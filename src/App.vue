<template>
  <div class="black-bg" v-if="isOpenModal">
    <div class="white-bg">
      <div class="text-btn">
        <a @click="openModal(false)" href="">× close</a>
      </div>
      <h4>detail</h4>
      <p>page</p>
    </div>
  </div>

  <div class="menu">
    <a @mouseover="openDropDown(true, i)" @mouseout="openDropDown(false)" v-for="(menu, i) in menus" :key="i" :href="i">{{ menu }}</a>
  </div>

  <div class="gray-dr" v-if="isOpenDropDown">
    <div class="white-dr">
      <p class="menu-dr" @mouseout="openDropDown(false)" v-for="(j, k) in dropDownMenus[this.currDropDown]" :key="k">
        {{ dropDownMenus[this.currDropDown][k] }}
      </p>
    </div>
  </div>

  <div v-for="(a, i) in items" :key="i">
    <img class="item-img" @click="openModal(true)" :src="itemImgUrl[i]" :style="itemImg">
    <!-- <h4 class="item-name" @click="isOpenModal = true">{{ a }}</h4> -->
    <div class="item-name">
      <p @click="openModal(true)" href="">{{ a }}</p>
    </div>
    <p>{{ prices[i] }} won</p>
    <button id="report" @click="countAdd(i)">신고</button>
    <span><b>신고수:</b> {{ cnt[i] }}</span>
  </div>
  
  <!-- <div>
    <h4 :style="style">{{ items[0] }}</h4>
    <p>{{ prices[0] }} won</p>
  </div>
  <div>
    <h4 :style="style">{{ items[1] }}</h4>
    <p>{{ prices[1] }} won</p>
  </div>
  <div>
    <h4 :style="style">{{ items[2] }}</h4>
    <p>{{ prices[2] }} won</p>
  </div> -->
</template>

<script>

export default {
  name: 'App',
  data(){
    return { // data 보관함, obj 자료형식으로 저장
      menus: ['Home', 'About', 'Products', 'Dashboard'],
      dropDownMenus: [['Home'], ['About1', 'About2'], ['Page1', 'Page2'], ['Dash1', 'Dash2', 'Dash3']],
      itemImgUrl: [require("./assets/img1.jpg"), require("./assets/img2.jpg"), require("./assets/img3.jpg")],
      itemImg: 'margin-top:30px',
      items: ['item1', 'item2', 'item3'],
      prices: [60, 70, 30],
      cnt: [0, 0, 0],
      isOpenModal: false,
      isOpenDropDown: false,
      currDropDown: -1,
    }
  },
  methods: {
    countAdd(i){
      this.cnt[i]++;
    },
    openModal(isOpen){
      this.isOpenModal = isOpen;
      this.currDropDown = -1;
    },
    openDropDown(isOpen, idx){
      this.isOpenDropDown = isOpen;
      this.currDropDown = idx;
      // console.log(this.dropDownMenus[idx]);
    }
    // imgUrl(i){
    //   const url = "./assets/img"+i+".jpg"
    //   console.log(url);
    //   return url;
    // }
  },
  components: {
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.menu{
  width: 100%;
  float:left;
  background: slategray;
  /* padding: 1px; */
  padding: 15px;
  /* border-radius: 5px; */
}
.menu a{
  color: white;
  font-weight: bold;
  padding: 10px;
  text-decoration: none !important
}
.gray-dr{
  width: 100px;
  background: slategray;
  position: fixed;
  margin-top: 48px;
  /* position: relative;
  left: 50%; */
}
.white-dr{
  /* border: 0.25px solid slategray; */
  /* width: 100px; */
  background: white;
  color: slategray;
}
.menu-dr{
  border: 1px solid slategray;
  /* width: 100px; */
  background: white;
  color: slategray;
  padding: 7px;
  margin: 0 auto;
  margin-top: -1px;
}
.menu-dr:hover{
  background: slategray;
  color: white;
}

.text-btn{
  color: cornflowerblue;
  text-align: right;
}
.text-btn a{
  text-decoration: none !important
}
.text-btn a:visited{
  color: cornflowerblue;
}

.item-name{
  color: blue;
  font-weight: bold;
}
.item-name a{
  text-decoration: none !important
}
.item-name a:visited{
  color: blue;
}

.item-img{
  width: 200px;
  height: 150px;
}

button{
  background: maroon;
  color: white;
  padding: 5px;
  border-radius: 5px;
  font-size: 0.1em;
  margin-right: 10px;
  border: none;
  outline: none;
}

</style>
