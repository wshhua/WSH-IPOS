<template>
  <div class="header" id="header">
    <div class="logoAndInfo">
      <div class="left">
        <div class="logoWaymap"></div>
        <div class="logoClient"></div>
        <input class="searchHeader" v-bind:placeholder="this.Gbl.LangFun(chinaOrEnglish.inputText1, this.Gbl.wayMapUserLang)"
          disabled="disabled" />
      </div>
      <div class="right">
        <div class="userInfo">
          <p class="p1">{{this.Gbl.wayMapUserName}}</p>
          <p class="p2">{{this.Gbl.wayMapLocationName}}-{{this.Gbl.wayMapRoleName}}</p>
        </div>
        <div class="personList">
          <div v-for="(personItem,index) in personListData"
          v-on:click.stop="exitClick"
          v-bind:class="personItem.className"
          v-bind:key="'index'+index">{{this.Gbl.LangFun(personItem.name, this.Gbl.wayMapUserLang)}}</div>
          <div class="shopList">
            <div v-for="(item,index) in shopListData" v-bind:key="'item'+index" class="shopItem" v-on:click.stop="shopItemClick(index)">{{item.name}}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="menuRow">
      <div class="menuBox">
        <div class="pageGroup" v-for="(group,fIndex) in menuData"
        v-if="group.display" v-bind:key="'FI'+fIndex" v-bind:class="group.active">
          <div class="groupName" v-on:click.stop="groupNameClick(fIndex)">{{this.Gbl.LangFun(group.name, this.Gbl.wayMapUserLang)}}</div>
          <div class="groupList" v-show="group.listDir">
            <div class="aBox">
              <a class="groupItem" v-bind:class="item.className"
              v-for="(item,iIndex) in group.data"
              v-bind:key="'Item'+iIndex"
              v-show="item.display"
              v-bind:href="item.url">{{this.Gbl.LangFun(item.name, this.Gbl.wayMapUserLang)}}</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'headerCpt',
  data () {
    return {
      headerData: wayMapHeadDisplay,
      chinaOrEnglish: {
        inputText1: ['此功能暂不可用', 'Temporarily Unavailable']
      },
      menuData: [{
          active: '',
          name: newLGCom.pageHeader.menu1Text,
          className: 'goHome',
          display: false,
          dataLen: 0,
          listDir: false,
          data: []
        },
        {
          active: '',
          name: newLGCom.pageHeader.menu2Text,
          className: 'goCashier',
          display: false,
          dataLen: 8,
          listDir: false,
          data: [
            {
              name: newLGCom.pageHeader.menu23Text,
              className: 'gCItem9',
              display: true,
              url: 'cashier9.html'
            },
            {
              name: newLGCom.pageHeader.menu21Text,
              className: 'gCItem6',
              display: false,
              url: 'cashier6.html'
            },
            {
              name: newLGCom.pageHeader.menu22Text,
              className: 'gCItem7',
              display: false,
              url: 'cashier7.html'
            },
            {
              name: newLGCom.pageHeader.menu23Text,
              className: 'gCItem1',
              display: false,
              url: 'cashier1.html'
            },
            {
              name: newLGCom.pageHeader.menu24Text,
              className: 'gCItem2',
              display: true,
              url: 'cashier2.html'
            },
            {
              name: newLGCom.pageHeader.menu25Text,
              className: 'gCItem3',
              display: true,
              url: 'cashier3.html'
            },
            {
              name: newLGCom.pageHeader.menu26Text,
              className: 'gCItem8',
              display: true,
              url: 'cashier8.html'
            },
            {
              name: newLGCom.pageHeader.menu27Text,
              className: 'gCItem5',
              display: true,
              url: 'cashier5.html'
            },
            {
              name: newLGCom.pageHeader.menu28Text,
              className: 'gCItem10',
              display: true,
              url: 'cashier10.html'
            }
          ]
        },
        {
          active: '',
          name: newLGCom.pageHeader.menu3Text,
          className: 'goStockProcess',
          display: false,
          dataLen: 4,
          listDir: false,
          data: [{
              name: newLGCom.pageHeader.menu31Text,
              className: 'gSPItem1',
              display: true,
              url: 'goStockProcessItem1.html'
            },
            {
              name: newLGCom.pageHeader.menu32Text,
              className: 'gSPItem2',
              display: true,
              url: 'goStockProcessItem2.html'
            },
            {
              name: newLGCom.pageHeader.menu33Text,
              className: 'gSPItem3',
              display: true,
              url: 'goStockProcessItem3.html'
            },
            {
              name: newLGCom.pageHeader.menu34Text,
              className: 'gSPItem4',
              display: true,
              url: 'goStockProcessItem4.html'
            }
          ]
        },
        {
          active: '',
          name: newLGCom.pageHeader.menu4Text,
          className: 'goReportFile',
          display: false,
          dataLen: 9,
          listDir: false,
          data: [{
              name: newLGCom.pageHeader.menu41Text,
              className: 'gRFItem1',
              display: true,
              url: 'gRFItem1.html'
            },
            {
              name: newLGCom.pageHeader.menu42Text,
              className: 'gRFItem2',
              display: true,
              url: 'gRFItem2.html'
            },
            {
              name: newLGCom.pageHeader.menu43Text,
              className: 'gRFItem3',
              display: true,
              url: 'gRFItem3.html'
            },
            {
              name: newLGCom.pageHeader.menu44Text,
              className: 'gRFItem5',
              display: true,
              url: 'gRFItem5.html'
            },
            {
              name: newLGCom.pageHeader.menu45Text,
              className: 'gRFItem6',
              display: true,
              url: 'gRFItem6.html'
            },
            {
              name: newLGCom.pageHeader.menu46Text,
              className: 'gRFItem8',
              display: false,
              url: 'gRFItem8.html'
            },
            {
              name: newLGCom.pageHeader.menu47Text,
              className: 'gRFItem9',
              display: false,
              url: 'gRFItem9.html'
            },
            {
              name: newLGCom.pageHeader.menu48Text,
              className: 'gRFItem10',
              display: true,
              url: 'gRFItem10.html'
            },
            {
              name: newLGCom.pageHeader.menu49Text,
              className: 'gRFItem11',
              display: true,
              url: 'gRFItem11.html'
            },
            {
              name: newLGCom.pageHeader.menu410Text,
              className: 'gRFItem12',
              display: true,
              url: 'gRFItem12.html'
            }
          ]
        },
        {
          active: '',
          name: newLGCom.pageHeader.menu5Text,
          className: 'goPersonSet',
          display: false,
          dataLen: 4,
          listDir: false,
          data: [{
              name: newLGCom.pageHeader.menu51Text,
              className: 'gPSItem1',
              display: true,
              url: 'gPSItem1.html'
            },
            {
              name: newLGCom.pageHeader.menu52Text,
              className: 'gPSItem2',
              display: true,
              url: 'gPSItem2.html'
            },
            {
              name: newLGCom.pageHeader.menu53Text,
              className: 'gPSItem3',
              display: true,
              url: 'gPSItem3.html'
            },
            {
              name: newLGCom.pageHeader.menu54Text,
              className: 'gPSItem4',
              display: true,
              url: 'gPSItem4.html'
            },
            {
              name: newLGCom.pageHeader.menu55Text,
              className: 'gPSItem5',
              display: true,
              url: 'gPSItem5.html'
            }
          ]
        }
      ],
      personListData: [{
        name: newLGCom.pageHeader.personListText1,
        className: 'exitLoading'
      }],
      shopListData: []
    }
  },
  props: ['message'],
  methods: {
    exitClick (event) {
      if (event.target.className === 'exitLoading') {
        this.router.push('/')
      }
    },
    groupNameClick (val) {
      if (val === 0) {
        this.router.push('/home')
      } else {
        if (this.menuData[val].listDir) {
          this.menuData[val].listDir = false
        } else {
          this.menuData[val].listDir = true
        }
        if (val === 1) {
          this.menuData[2].listDir = false
          this.menuData[3].listDir = false
          this.menuData[4].listDir = false
        } else if (val === 2) {
          this.menuData[1].listDir = false
          this.menuData[3].listDir = false
          this.menuData[4].listDir = false
        } else if (val === 3) {
          this.menuData[1].listDir = false
          this.menuData[2].listDir = false
          this.menuData[4].listDir = false
        } else if (val === 4) {
          this.menuData[1].listDir = false
          this.menuData[2].listDir = false
          this.menuData[3].listDir = false
        }
      }
    },
    shopItemClick (val) {
      console.log(this.shopListData[val].name)
    }
  },
  watch: {},
  filters: {},
  mounted () {
    var dataLen = this.menuData.length;
    var urlString = window.location.href;
    if (urlString.indexOf('home.html') > 0) {
      this.menuData[0].active = 'active';
    }
    for (var i = 0; i < dataLen; i++) {
      var dataPageLen = this.menuData[i].data.length;
      for (var j = 0; j < dataPageLen; j++) {
        if (urlString.indexOf(this.menuData[i].data[j].url) > 0) {
          this.menuData[i].active = 'active';
          break;
        } else if (j === dataPageLen - 1) {
          this.menuData[i].active = '';
        }
      }
    }
    // menuDisplay
    var menuListDisplay = wayMapHeadDisplay.split(',');
    for (var i = 0; i < menuListDisplay.length; i++) {
      this.menuData[(menuListDisplay[i] - 1)].display = true;
    }
  }
}
</script>

<style scoped>
  /*页面公共头部样式*/
  .header {
    width: 100%;
    height: auto;
  }
  
  .header>.logoAndInfo {
    width: 100%;
    height: 60px;
    background-color: #eaf1f9;
    display: -webkit-flex;
    /* Safari */
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .header>.menuRow {
    width: 100%;
    height: auto;
    background-color: #2745ea;
    display: -webkit-flex;
    /* Safari */
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .header>.menuRow>.menuBox {
    width: 94%;
    height: 52px;
    display: -webkit-flex;
    /* Safari */
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .header>.logoAndInfo>.left {
    width: auto;
    height: 100%;
    display: -webkit-flex;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-left: 3%;
  }
  
  .header>.logoAndInfo>.left>.logoWaymap {
    display: none;
    width: 150px;
    height: 52px;
    background-image: url(../../../static/img/logo6.png);
    background-position: left center;
    background-size: 90% auto;
    background-repeat: no-repeat;
    margin-right: 5px;
  }
  
  .header>.logoAndInfo>.left>.logoClient {
    width: 150px;
    height: 52px;
    background-image: url(../../../static/img/logo.png);
    background-position: left center;
    background-size: 90% auto;
    background-repeat: no-repeat;
    margin-right: 5px;
  }
  
  .header>.logoAndInfo>.left>.searchHeader {
    width: 250px;
    height: 30px;
    background-image: url(../img/searchPic.png);
    background-position: 90% center;
    background-size: auto 60%;
    background-repeat: no-repeat;
    margin-right: 5px;
    outline: none;
    border: 1px solid #b5b8bd;
    border-radius: 3px;
  }
  
  .header>.menuRow>.menuBox>.pageGroup {
    width: auto;
    height: 52px;
    cursor: pointer;
    position: relative;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupName {
    width: auto;
    height: 52px;
    line-height: 52px;
    color: #FFFFFF;
    background-color: #2745ea;
    padding: 0 30px;
    font-size: 20px;
  }
  
  .header>.menuRow>.menuBox>.pageGroup.active>.groupName,
  .header>.menuRow>.menuBox>.pageGroup:hover>.groupName {
    background-color: #215acc;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList {
    display: none;
    width: auto;
    height: auto;
    position: absolute;
    left: 0;
    top: 50px;
    background-color: rgba(0, 0, 0, 0);
    border-top: 2px solid transparent;
    z-index: 100;
  }
  .header>.menuRow>.menuBox>.pageGroup:last-child>.groupList {
    display: none;
    width: auto;
    height: auto;
    position: absolute;
    right: 0;
    left: auto;
    top: 50px;
    background-color: rgba(0, 0, 0, 0);
    border-top: 2px solid transparent;
    z-index: 100;
  }
  .header>.menuRow>.menuBox>.pageGroup>.groupList>.aBox {
    width: auto;
    height: auto;
    margin-top: 2px;
    border-radius: 5px;
    box-shadow: 0 0 5px #686868;
    overflow: hidden;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList .groupItem {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    width: 200px;
    height: 38px;
    line-height: 38px;
    font-size: 15px;
    color: #a0a0a0;
    cursor: pointer;
    padding: 0 10px;
    text-align: left;
    background-color: #FFFFFF;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList.goCashier .groupItem {
    width: 190px;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList.goStockProcess .groupItem {
    width: 190px;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList.goReportFile .groupItem {
    width: 230px;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList.goPersonSet .groupItem {
    width: 179px;
  }
  
  .header>.menuRow>.menuBox>.pageGroup>.groupList .groupItem:hover {
    color: #FFFFFF;
    background-color: #2c4194;
  }
  
  .header>.logoAndInfo>.right {
    width: auto;
    height: 52px;
    cursor: pointer;
    position: relative;
    margin-right: 3%;
  }
  
  .header>.logoAndInfo>.right>.userInfo {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    width: auto;
    height: 52px;
    line-height: 52px;
    background-image: url(../img/personPic.png);
    background-repeat: no-repeat;
    background-position: left center;
    background-size: 45px auto;
    padding-left: 50px;
    border-top: 1px solid transparent;
  }
  
  .header>.logoAndInfo>.right>.userInfo p {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    width: auto;
    height: 14px;
    line-height: 14px;
    font-size: 12px;
    color: #909090;
  }
  
  .header>.logoAndInfo>.right>.userInfo p.p1 {
    margin-top: 10px;
  }
  
  .header>.logoAndInfo>.right>.personList {
    display: none;
    width: auto;
    min-width: 100%;
    height: auto;
    position: absolute;
    right: 0;
    top: 50px;
    border-top: 2px solid transparent;
    z-index: 10;
  }
  
  .header>.logoAndInfo>.right:hover>.personList {
    display: block;
  }
  
  .header>.logoAndInfo>.right>.personList>div {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    width: auto;
    min-width: 100%;
    height: 52px;
    line-height: 52px;
    font-size: 18px;
    color: #a0a0a0;
    background-color: #FFFFFF;
    margin-top: 2px;
    box-shadow: 0 0 5px #686868;
    border-radius: 5px;
  }
  .header>.logoAndInfo>.right>.personList .shopList {
    width: auto;
    min-width: 100%;
    height: auto;
    max-height: 200px;
    overflow-y: scroll;
  }
  .header>.logoAndInfo>.right>.personList .shopList .shopItem {
    width: 100%;
    height: 50px;
    line-height: 50px;
    font-size: 18px;
    color: #a0a0a0;
    text-align: left;
  }
  .header>.logoAndInfo>.right>.personList .shopList .shopItem:hover {
    color: #05146f;
  }
  .header>.logoAndInfo>.right>.personList>.exitLoading {
    background-image: url(../img/exitPic1.png);
    background-repeat: no-repeat;
    background-position: 19px center;
    padding-left: 52px;
  }
  
  .header>.logoAndInfo>.right>.personList>.exitLoading:hover {
    background-image: url(../img/exitPic3.png);
    color: #05146f;
  }
</style>
