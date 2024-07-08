<script setup>
import { ref,computed } from "vue";
const name = 'vue dinamico'
const counter = ref(0)
const arrayFavorite = ref([])
const increment = () => counter.value ++
const decrement = () => counter.value --  
const reset = () => counter.value = (0)
const add = () =>{
  arrayFavorite.value.push(counter.value)
};
const bloquearBtnAdd = computed(()=>{
  const numSearch = arrayFavorite.value.find((num) => num === counter.value);
  console.log(numSearch);
  // if(numSearch === 0) return true
  // return numSearch ? true : false ;
  return numSearch || numSearch === 0
});

const classCounter = computed(()=>{
  if(counter.value === 0){
    return 'zero'
  }
  if (counter.value > 0){
     return 'positive'
  }
  if(counter.value < 0){
    return 'negative'
  }
 
});
</script>

<template>
  <div class="container text-center">
  <h1>Hola {{ name.toUpperCase() }}!</h1>
  <h2 :class="classCounter">{{ counter }}</h2>
  <div class="btn-group" role="group">
      <button @click="increment" class="btn btn-success">aumentar  contador</button>
      <button @click="decrement" class="btn btn-danger">disminuir contador</button>
      <button @click="reset" class="btn btn-secondary">contador en 0</button>
      <button @click="reset" class="btn btn-success">contador en 0</button>
      <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary" >Add</button>

  </div>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="(num, index) in arrayFavorite" :key="index">
      {{ num }}

    </li>
  </ul>
  
  </div>
  
</template> 
<style>
h1{
  color: brown;
  
}
.container{
  align-content: center;
  width: 700px;
  margin-left:250px ;
}
.positive{
  color: green;
}
.negative{
  color : red;
}
.zero{
  color: peru;
}

</style>