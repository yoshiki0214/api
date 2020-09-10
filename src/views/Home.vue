<template>
  <div class="home">
    <input type="text" v-model="zipcode">
    <button @click="addressButton">住所自動入力</button>
    <p>Address:{{addressData}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      zipcode:"",
      addressData:{}
    };
  },
  methods:{
    addressButton(){
      let url =
        `https://apis.postcode-jp.com/api/v4/postcodes/${this.zipcode}?apiKey=wbUgCJJ0VYndDL2Sv7GVPwBxLrx7jFvuyp4LrR9`
      axios.get(url).then((res) => {
        this.addressData = res.data[0].allAddress;
      });
  }
      
}
};
</script>

