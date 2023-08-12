<script setup>
import { ref, onMounted, onBeforeUnmount, nextTick} from 'vue';

const items = ref([
  'https://images.unsplash.com/photo-1691294416061-a6a3ba9a63de?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80',
  'https://images.unsplash.com/photo-1681841607480-d3063d52b83b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80',
  'https://images.unsplash.com/photo-1691751676730-188d67b7c238?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80'
])

let carousel = null
const newItem =  ref('https://images.unsplash.com/photo-1691394790591-b1ce2093b045?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80')

function updateCarousel(){
    items.value.push(newItem)
}
onMounted(() =>{
    carousel = new Flickity('#carousel', {});
})
onBeforeUnmount(() => {
    carousel.destroy()
})

</script>


<template>
<div class="mx-auto items" id="carousel">
  <div :style="`background-image: url(${item})`" class="item" v-for="(item,index) in items" :key="index">
  </div>
</div>
</template>

<style scoped>
  .items{
    width: 1000px;
    height:400px;
}

.item{
    width: 1000px;
    height: 400px;
    background-color: gray;
    background-size: cover;
}
</style>