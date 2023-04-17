<script setup lang="ts">
import { useDark, useToggle } from "@vueuse/core";
import { VueFlow  } from '@vue-flow/core'
import { ref } from 'vue'

const isDark = useDark();
const toggleDark = useToggle(isDark);


const elements = ref([
  // Nodes
  // An input node, specified by using `type: 'input'`
  { id: '1', type: 'input', label: 'Node 1', position: { x: 250, y: 5 } },

  // Default nodes, you can omit `type: 'default'`
  { id: '2', label: 'Node 2', position: { x: 100, y: 100 }, },
  { id: '3', label: 'Node 3', position: { x: 400, y: 100 } },

  // An output node, specified by using `type: 'output'`
  { id: '4', type: 'output', label: 'Node 4', position: { x: 400, y: 200 } },

  // Edges
  // Most basic edge, only consists of an id, source-id and target-id
  { id: 'e1-3', source: '1', target: '3' },

  // An animated edge
  { id: 'e1-2', source: '1', target: '2', animated: true },
])
</script>

<template>
  <h1 class="text-green-700 dark:text-green-300">Hello</h1>
  <button class="text-black dark:text-white rounded shadow-sm ring-1 ring-inset ring-gray-300 dark:ring-slate-700 hover:bg-gray-100 dark:hover:bg-slate-950 p-4" @click="toggleDark()">
    Dark: {{ isDark }} , click to change
  </button>
  <span class="block classic-apply">this is the target of an @apply rule</span>
  <div class="wrapper">
    <div class="w-[1400px] h-[1000px]" >
      <VueFlow v-model="elements" />
    </div>
  </div>
</template>

<style scoped>
.classic-apply {
  @apply text-xl text-orange-700 dark:text-white
}

.wrapper :deep(.vue-flow__node){
  @apply cursor-pointer bg-green-100 dark:text-red-100 dark:bg-red-700
}
</style>
