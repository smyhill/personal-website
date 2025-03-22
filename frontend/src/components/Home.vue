<template>
    <div>
        <h1>{{ message }}</h1>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';

export default defineComponent({
    name: 'Home',
    setup() {
        const message = ref('Loading');

        onMounted(async () => {
            const response = await fetch('http://localhost:8080/my-name');
            const data = await response.json();
            message.value = data.message;
        });

        return { message};
    }
});

</script>