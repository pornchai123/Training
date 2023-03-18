<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

defineProps<{ msg: string }>()
const count = ref(0)
const message = ref('')
const list = ref()
const getList = async function () {
  const {data} = await axios.get("https://gorest.co.in/public/v2/todos");
  list.value = data;
};
</script>
<template>
  <div
    class = "col-start-">
    <h1 class= "text-center">{{ msg+''+message }}</h1>
    <div class= "card text=center"></div>
  </div>
  <div v-for="(item,index) in list" key = "index">
  <div class="border-red-600 bg-white px-10 py-10 text-start my10 rounded-x1">
<h3 class="text-base font-semibold leading-6 text-gray-900">Title : {{ item["title"] }}</h3>
<h3 class="text-base font-semibold leading-6 text-gray-900">user-id : {{ item["user-id"] }}</h3>
<h3 class="text-base font-semibold leading-6 text-gray-900">status : {{ item["status"] }}</h3>
</div>
</div>
  <pre>{{ list }}</pre>
  <h1 class="text-3xl font-bold text-red-600"> Hello world!</h1>
  <div class="card">
    <input type="text" v-model='message'>
    <button type="button" @click="getList()"> Get List </button>
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
