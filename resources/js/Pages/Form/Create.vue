<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Create Form
            </h2>
        </template>

        <div>
            <div class="max-w-7xl mx-auto py-10 sm:px-6 lg:px-8">
                <form @submit.prevent="submit">
                    <label for="name">Name:</label>
                    <input id="name" v-model="form.name" />
                    <div v-if="errors.name">{{ errors.name }}</div>

                    <label for="email">Email:</label>
                    <input id="email" v-model="form.email" />
                    <div v-if="errors.email">{{ errors.email }}</div>

                    <button type="submit">Submit</button>
                </form>
            </div>
        </div>
    </app-layout>
</template>

<script>
import AppLayout from '@/Layouts/AppLayout'

export default {
    components: {
        AppLayout,
    },
    props: {
        errors: Object,
    },
    data() {
        return {
            form: {
                name: null,
                email: null,
            },
        }
    },
    methods: {
        submit() {
            this.$inertia.post('/form', this.form)
        },
    },
}
</script>
