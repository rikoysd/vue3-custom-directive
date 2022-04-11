<script setup lang="ts">
import { ref } from "vue";

const props = defineProps(["modelValue"]);
const emits = defineEmits(["update:modelValue"]);

const isActiveButton = ref(props.modelValue);
const onClick = (buttonType: string) => {
  isActiveButton.value = buttonType;
  emits(isActiveButton.value);
};
</script>

<template>
  <ul>
    <li>
      <button
        type="button"
        :class="{ active: isActiveButton === 'bad' }"
        @click="onClick('bad')"
      >
        Bad
      </button>
    </li>
    <li>
      <button
        type="button"
        :class="{ active: isActiveButton === 'average' }"
        @click="onClick('average')"
      >
        Average
      </button>
    </li>
    <li>
      <button
        type="button"
        :class="{ active: isActiveButton === 'great' }"
        @click="onClick('great')"
      >
        Great
      </button>
    </li>
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: solid 1px gray;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}

.active {
  color: rgb(224, 94, 116);
}
</style>
