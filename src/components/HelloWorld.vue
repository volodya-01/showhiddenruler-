<template>
    <div id="main">
         <div class="koutbox1"><img id="slidingImg" src="~@/assets/img/时间刻度_10.png" alt=""></div> 
           <div class="eoutbox" v-show="isshowh">
              <div class="eoutleftbox">
                <div class="hidden"  @click="show1">隐藏</div>
              </div>
              <div class="eoutrightbox">
                <div id="slidingImgline"></div>
              </div>
         </div>
          <!-- 隐藏部分 -->
           <div class="toutbox" v-show="isshoww">
              <div class="toutleftbox">
                <div class="show" @click="show2">显示</div>
              </div>
              <div class="toutrightbox">
                <div id="tslidingImgline"></div>
              </div>
         </div>
      
          <div class="koutbox2"><img  id="slidingImg2" src="~@/assets/img/时间刻度_10.png" alt=""></div> 
    </div>
</template>
<script>
let moment = require("moment");
export default {
  name: "HelloWorld",
  data() {
    return {
      isshowh: false,
      isshoww: true
    };
  },
  mounted() {
    let that = this;
    that.LopTime();
    setInterval(function() {
      var mindata = new Date().getHours() * 60 + new Date().getMinutes();
      if (mindata % 15 == 0) {
        that.LopTime();
        console.log(mindata);
      }
    }, 60000); //在生命周期中调用LopTime（）方法
  },
  props: [""],
  computed: {},
  methods: {
    LopTime() {
      let timer = new Date();
      let hours = timer.getHours();
      let min = timer.getMinutes();
      let total = hours * 60 + min;
      let localnum = parseInt(total / 15);
      let Insetlinelocation = -234 + localnum * parseFloat(760 / 96);
      let Insetlinelocationline = 74 + localnum * parseFloat(760 / 96);
        console.log(localnum);
      document.getElementById("slidingImg").style.left = Insetlinelocation + "px";
      document.getElementById("slidingImg2").style.left = Insetlinelocation + "px";
      document.getElementById("slidingImgline").style.left =Insetlinelocationline + "px";
      document.getElementById("tslidingImgline").style.left =Insetlinelocationline + "px";
   
    },
    show1() {
      this.isshowh = false;
      this.isshoww = true;
    },
    show2() {
      this.isshowh = true;
      this.isshoww = false;
     
    }
  }
};
</script>
<style  scoped>
#main {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;
  width: 1128px;
  /*  height: 210px; */
  border: 1px #e4e4ec solid;
  margin: 50px auto;
  position: relative;
}
.koutbox1 {
  width: 1128px;
  height: 28px;
  border-bottom: 1px #e4e4ec solid;
  background-image: url("~@/assets/img/刻度02_03.png");
  background-repeat: no-repeat;
  background-position: 0px 3px;
  position: relative;
}
.koutbox2 {
  width: 1128px;
  height: 28px;
  border-top: 1px #e4e4ec solid;
  background-image: url("~@/assets/img/刻度02_03.png");
  background-repeat: no-repeat;
  background-position: 0px 3px;
}
#slidingImg {
  position: relative;
  left: -234px;
}
#slidingImg2 {
  position: relative;
  left: -234px;
}
.eoutbox {
  width: 1128px;
  height: 154px;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;
}
.eoutleftbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  width: 254px;
  height: 154px;
  border-right: 1px #e4e4ec solid;
}
.hidden {
  width: 42px;
  height: 42px;
  color: #fff;
  font-size: 14px;
  font-family: "微软雅黑";
  background-color: rgba(126, 136, 1, 0.8);
  line-height: 42px;
  text-align: center;
}
.eoutrightbox {
  width: calc(100%-254px);
  height: 154px;
  position: relative;
}
#slidingImgline{
  width: 1px;
  height: 154px;
  background-color: red;
  position: relative;
  left: 74px;
}
/* 隐藏部分 */

.toutbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;
    width: 1128px;
  height: 40px;
}
.toutleftbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  width: 254px;
  height: 40px;
  border-right: 1px #e4e4ec solid;
}
.show {
  width: 24px;
  height: 24px;
  color: #fff;
  font-size: 14px;
  font-family: "微软雅黑";
  background-color: rgba(126, 136, 1, 0.8);
  line-height: 24px;
  text-align: center;
}
.toutrightbox {
  width: calc(100%-254px);
  height: 40px;
  position: relative;
}
#tslidingImgline {
  width: 1px;
  height: 40px;
  background-color: red;
  position: relative;
  left: 74px;
}
</style>


