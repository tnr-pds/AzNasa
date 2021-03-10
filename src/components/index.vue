<template>
<div>
  
  <b-jumbotron bg-variant="dark" text-variant="warning" border-variant="dark">
      <b-img thumbnail fluid src="https://media3.giphy.com/media/sdcIxdTkFD0g8/200.gif" alt="Image 2" width="300"></b-img>-
      <b-img thumbnail fluid src="https://thumbs.gfycat.com/NecessaryCompetentIndri-max-1mb.gif" alt="Image 2" width="650"></b-img>-
      <b-img thumbnail fluid src="https://i.pinimg.com/originals/b5/11/79/b51179b9f68e94e38047eab97935ffc0.gif" alt="Image 2" width="300"></b-img>
      
    <template #header >NASA WSA+EnlilSimulation</template>
    <hr class="my-1">
      <b-button variant="outline-warning" @click="loadUser" >ข้อมูลเพิ่มเติม</b-button>
      <b-card class="ms-1"
        border-variant="warning"
        header="ข้อมูล"
        header-bg-variant="dark"
        header-text-variant="warning"
        v-for="(data,index) in dataList" :key="index"
        tag="article"
        style="max-width: 200rem;" >
    
        <h1 align="center"> {{data.catalog}}</h1>
        <b-card-text >
        <h3 > ID : {{data.simulationID}}</h3> 
        <br>
        <b-row class="">
    <b-col cols="2" md="auto"></b-col>
    <b-col col lg="4"> <h3>เวลา : {{data.modelCompletionTime}}</h3></b-col>
    </b-row>
        <div v-for="i in data.instruments" :key="i">
          ชื่อ : {{i.displayName}}
        </div >
       </b-card-text>
        <a :href="data.link" target="_blank">ข้อมูลเพิ่มเติม</a>
   </b-card>
  </b-jumbotron>
</div>
</template>

<script>
import axios from"axios"; 
export default {
    data(){
        return{
        dataList:null,
         url:"https://api.nasa.gov/DONKI/WSAEnlilSimulations?startDate=2011-09-19&endDate=2011-09-20&api_key=DEMO_KEY"
        };
    },
     methods:{
        loadUser(){
            axios.get(this.url)
            .then( response=>{ this.dataList = response.data;
            } )
            .catch(err => { console.log(err) } )
        },
     }
};
</script>