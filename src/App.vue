<script setup>
import {ref} from "vue";

let messages = ref([]),
    currentMessage = ref("สวัสดีครับ"),
    response = ["เหมียว", "แม๊ว", "แง่ว", "โฮ่ง ๆ", "Mondayleftmebroken😢", "Ano ano wilkum🍓🍓🍓", "We live We love We lie🐌🐌🐌", "Sowakemeupwhenitsallover😔😔😔", "cat"]

function processData() {
  console.log(currentMessage.value)
  messages.value.push({
    type: "user",
    message: currentMessage.value,
  });
  messages.value.push({
    type: "bot",
    message: response[Math.floor(Math.random() * response.length)],
  });

  currentMessage.value = "";
}

processData()

</script>

<template>
  <center class="mb-6 text-white">
    <a href="https://tinarskii.com">Website of <span class="underline">Tinarskii</span></a>
  </center>
  <div class="grid md:grid-cols-2 grid-cols-1 gap-8 min-h-screen">
    <div class="flex flex-col md:col-span-2 gap-2 w-full items-center">
      <h1 class="font-black text-white sm:text-6xl text-5xl text-center">
        Chat Meow
      </h1>
      <p class="font-extrabold text-slate-300 italic text-center">
        Talk with our cutting edge AI technology, trained from the best cat!
      </p>
      <div class="flex flex-col gap-6 max-w-xl w-full">
        <div class="flex flex-col" v-for="(msg, idx) in messages" :key="idx">
          <div v-if="msg.type === 'user'" class="chat chat-end">
            <div class="chat-bubble bg-blue-600">
              {{ msg.message }}
            </div>
          </div>
          <div v-if="msg.type === 'bot'" class="chat chat-start">
            <div class="chat-bubble bg-white text-black">
              {{ msg.message }}
            </div>
          </div>
        </div>
        <div class="flex flex-row gap-2">
          <input v-model="currentMessage" type="text" class="w-full p-2 rounded-lg border border-white" placeholder="Ask something..." />
          <button class="w-1/4 p-2 rounded-lg bg-blue-600 text-white font-bold" @click="processData()">Send</button>
        </div>
      </div>
    </div>
  </div>
</template>
