<script setup>
//import
import { ref } from "vue";


//ตัวแปร
const travellist = ref([
  {name:'i-love-coffe', price:50  , img:"/img/i_love_coffe2.jpg"}, 
  {name:'cafe', price:120 ,  img:"/img/คาเฟ่.jpg"},
  {name:'paizz', price:80 ,  img:"/img/ร้านพิซซ่า.jpg"},
  {name:'cat cafe', price:60 ,  img:"/img/คาเฟ่แมว.jpg"},
  {name:'dog cafe', price:100 ,img:"/img/คาเฟ่หมา.jpg"},
]);
//เก็บข้อมูลการจองร้าน
const bookinglist=ref([
  
]);
//จำนวนโต๊ะ
const teble=ref([]);
const telphon=ref([]);
const costomer=ref([]);
const time=ref([]);
const date=ref([]);
//function
function booking_control(name,price , tableQuantity){
//name--> +.bookinglist[]
  const totalPrice = price * tableQuantity;
  const box = {
    name: name,
    price: totalPrice,
    tableQuantity: tableQuantity,
    
  };
  bookinglist.value.push(box);

}

</script>


<template>

<h1 class="nameapp">Restaurants selected for you!</h1>
  <div class="container_text-center" >
    <div class="row">
      <div class="col" v-for=" (i,index) in travellist" :key="index" >
        <div class="card">
          <img :src="i.img" class="card-img-top" >
          <div class="card-body">
            <h5 class="card-title">{{ i.name }}</h5>
            <p class="card-price">{{ i.price }}</p>
            <p class="namecostomer">ชื่อผู้จอง <br>
              <input type="text" v-model="costomer[index]">
            </p>
            <p class="card-text">จำนวนโต๊ะ <br>
              <input type="number" class="input_value" v-model="teble[index]">
            </p>  
            <p class="card-text">เวลา<br>
              <input type="time" class="input_value" v-model="time[index]">
            </p> 
            <p class="card-text">วันที่<br>
              <input type="date" class="input_value" v-model="date[index]">
            </p> 
            <p class="card-text">เบอร์โทร <br>
              <input type="number" class="input_value" v-model="telphon[index]">
            </p> 
            <a class="btn btn-primary" @click="booking_control(i.name,i.price,teble[index],telphon[index],costomer[index],time[index],date[index])">จองเลย</a> 
          </div>
        </div>
      </div>
    </div>
  </div>

  <hr>
  <table class="table table-dark teble-striped" v-if="bookinglist.length > 0">
  <thead>
    <tr>
      <th scope="col">ลำดับ</th>
      <th scope="col">รายชื่อร้านที่จอง</th>
      <th scope="col">ราคา</th>
      <th scope="col">ชื่อผู้จอง</th>
      <th scope="col">จำนวนโต๊ะ</th>
      <th scope="col">เวลา</th>
      <th scope="col">วันที่</th>
      <th scope="col">เบอร์โทร</th>

    </tr>
  </thead>
  <tbody>
    <tr v-for="(i,index) in bookinglist" :key="index">
      <th scope="row">{{ index+1 }}</th>
      <td>{{ i.name }}</td>
      <td>{{ i.price }}</td>
      <td>{{ costomer[index] }}</td>
      <td>{{ teble[index] }} </td>
      <td>{{ time[index] }}</td>
      <td>{{ date[index] }}</td>
      <td>{{ telphon[index] }}</td>
    </tr>
  </tbody>
</table>

</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Lora:ital,wght@1,500&family=Noto+Serif+Display:wght@200&family=Noto+Serif:ital,wght@0,300;1,400&family=Playfair+Display:ital,wght@1,500&display=swap');

*{
  padding: 10px;
  font-family: 'Dancing Script', cursive;
  font-family: 'Lora', serif;
  font-family: 'Noto Serif', serif;
  font-family: 'Noto Serif Display', serif;
  font-family: 'Playfair Display', serif;
}
.card-img-top{
  height: 15rem;
  width: 10rem;

}
.input_value{
  width: 13rem;
}
.card{
  box-shadow:  0 30px 50px rgba(0,0,0,.2);
  border-radius: 25px;
  height: 50rem;
  width: 20rem;
}


</style>