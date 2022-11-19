<script setup lang="ts">
import Vditor from "vditor";
import { onMounted, ref } from "vue";
import "vditor/dist/index.css";

const props = withDefaults(
    defineProps<{
        id: string;
        options?: Record<string, any>;
    }>(),
    { id: "vditor" }
);

const vditor = ref<Vditor | null>(null);

onMounted(() => {
    vditor.value = new Vditor(props.id, {
        after: () => {
            // vditor.value is a instance of Vditor now and thus can be safely used here
            vditor.value!.setValue(
                "Vue Composition API + Vditor + TypeScript Minimal Example"
            );
        },
        ...props.options,
    });
});
</script>

<template>
    <div :id="props.id" />
</template>
