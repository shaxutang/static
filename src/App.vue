<script setup lang="ts">
const images = import.meta.glob<string>("./images/**", {
  eager: true,
  as: "url",
});

const imgs = Object.values(images).map((img) => img);

function onCopy(img: string) {
  navigator.clipboard.writeText(`${location.origin}${img}`);
  alert("复制地址成功");
}
</script>

<template>
  <div class="columns-3">
    <div class="cursor-pointer" v-for="img in imgs" @click="onCopy(img)">
      <img :src="img" alt="" />
    </div>
  </div>
</template>
