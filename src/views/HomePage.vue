<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="dark">
        <ion-title>Ejercicios Basicos </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <h1> Las cuatro operaciones </h1>
      <ion-item>
        <p>Suma: {{ a + b }}</p>
        <p>Resta: {{ a - b }}</p>
        <p>Multiplicacion: {{ a * b }}</p>
        <p>Division:{{ a/b }}</p>
      </ion-item>
      <ion-item>
        <ion-input label="Ingrese a:" type="number" v-model.number="a" />
        <ion-input label="Ingrese b:" type="number" v-model.number="b" />
        <br>
        <ion-item>  
      <ion-input label="Ingrese nombre:" placeholder="Ingrese un nombre"type="text" v-model.number="nombre" />
      <ion-input label="Ingrese edad:"  placeholder="Ingrese edad" type="number" v-model.number="edad" />
      </ion-item>
      </ion-item>
      <ion-item>
        <ion-button color="danger"@click="AdicionarEst()">
          Adicionar Estudiante
        </ion-button>
        <ion-button color="warning" @click="addStudent">
          Adicionar Estudiante
        </ion-button>
      </ion-item>
      <ion-item v-if="a===0">
        <p>a debe ser diferente de cero.</p>
      </ion-item>
      <ion-item v-if="b===0">
        <p>b debe ser diferente de cero.</p>
      </ion-item>
      <h1>Lista de Estudiantes</h1>
      <ion-list>
        <ion-item v-for="(est,index) in estudiantes" :key=" est.nombre">
          <p>{{ index+1 }}</p> 
          <p>{{ est.nombre }}</p>
           <p>Edad: {{ est.edad }}</p>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonInput, IonItem } from '@ionic/vue';
import { ref } from 'vue';

const a = ref(15);
const b = ref(3);
const estudiantes = ref([
  {nombre: "Juan",edad:244},
  {nombre: "Maria",edad:22},
  {nombre: "Pedro",edad:19},
]);
const nombre = ref("");
const edad = ref(0);
const addStudent=()=>{
 estudiantes.value.push(
  {
    nombre: nombre.value,
    edad: edad.value,
  }
 );
 nombre.value = "";
 edad.value = 0;
}
function AdicionarEst()
{
  alert("Adicionando estudiante2");
}
const index=prompt("Ingrese a eliminar (1 a" + estudiantes.value.length)
if(index !== null){
  const idx = parseInt(index) -1;
  if (idx >=0 && idx <estudiantes.value.length){
    estudiantes.value.splice(idx, 1);
  }else{
    alert("Indice invalido. entre 1 y " + estudiantes.value.length)
  }
}
</script>

<style scoped>
</style>
