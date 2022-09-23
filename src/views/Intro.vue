<template>
  <div>
    <h1>Say! {{greeting2}}</h1>
    <!-- v-model -> input값의 value역할 value 값을 넣어주는 부분 -->
    <input type="text" v-model="input1"/>
    <!-- @click -> button에서 onclick 역할   -->
    <button type="button" @click="getData" >얍</button>
    <button type="button" @click="setData" >요</button>

    <!-- select의 기본값 설정 시 v-model을 통해서 artist데이터가 twoway 방식으로 binding -->
    <select class="form-control" v-model="artist">
      <!--  임의로 d - data, i - index  -->
      <!--  v-for -> for문 (배열 처리시 사용)  -->
      <!--  v-for in data변수명     -->
      <!--  :key -> 유일한 고유값 부여    -->
      <!-- {{d.t}}  d -> 한줄 데이터 값, t: 해당 value값     -->
      <!-- :value="d.v"  데이터의 value 값 할당     -->
      <option :key="i" :value="d.v" v-for="(d,i) in options">{{d.t}}</option>
    </select>
  </div>
</template>

<script>
export default {
  //기존 html 에서 data 가져올때 getElementById 이용해서 input 내에 있는 id나 선택자에 접근해 value 뺴오는 방식
  //twoway binding -> data()에서 선언 후 삽입, 갖고오기 (get.setData) 가능

  data(){
    return{
      greeting1: "Halo!",
      greeting2: "bonjour!",
      greeting3: "안녕!",
      input1: "put down",
      //화면상에 테이블 형태로 데이터 뿌리는 형식일때 (데이터가 배열 형식인 경우)
      options: [
        {v:"1",t:"IAN"},
        {v:"2",t:"ZIOR"},
        {v:"3",t:"redZeplean"},
      ],
      artist: "2"
    };
  },
  watch: {
    //data명으로 function형식 작성
    //input형 데이터가 변경될때 catch해서 사용가능
    input1(){
      console.log(this.input1);
    }
  },
  //실제 데이터에서 메소드안에서 접근하려면 this.변수명(해당data) 입력
  methods:{
    getData(){
      alert(this.input1)
    },
    setData(){
      this.input1 = "jot down";
    }
  }
};
</script>

<style scoped>

</style>