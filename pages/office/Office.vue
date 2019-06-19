<template>
  <!-- <OfficeTest/> -->
  <list class="list">
    <template v-for="(item, index) in longList">
      <cell class="card-cell" v-if="item.type === 'card'" :key="index">
        <div class="card">
          <div class="row" style="padding-bottom:18upx">
            <div class="card-side">
              <image class="card-poster" :src="item.poster"></image>
            </div>
            <div class="card-message">
              <text class="card-title">{{item.title}}</text>
              <div class="card-line row">
                <image class="card-icon" src="//ossgw.alicdn.com/img/upload/0a4946e164acd1f81e97ddbc048afcc5/Group13-69-69.png@22w_22h_80Q.png"></image>
                <text class="card-subtitle">{{item.subtitle1}}</text>
              </div>
              <div class="card-line row">
                <image class="card-icon" src="//ossgw.alicdn.com/img/upload/0a4946e164acd1f81e97ddbc048afcc5/Group13-69-69.png@22w_22h_80Q.png"></image>
                <text class="card-subtitle">{{item.subtitle2}}</text>
              </div>
              <div class="card-progress row">
                <div class="card-progress-inner" :style="{ width: item.progress * 230 / 100 }"></div>
                <text class="card-got">已抢 {{item.got}} 件</text>
                <text class="card-remain">{{item.progress}} %</text>
              </div>
              <div class="card-info row">
                <text class="card-price">¥ {{item.price.real}}</text>
                <text class="card-sale-price">¥ {{item.price.sale}}</text>
                <div class="card-btn">
                  <text class="card-btn-text">马上抢</text>
                </div>
              </div>
            </div>
          </div>
        </div>
      </cell>
    </template>
  </list>
</template>

<script>
const dataset = {
  card: [
    {
      type: 'card',
      poster: 'http://gw.alicdn.com/tps/i4/1611893164/TB2t4mtXJqUQKJjSZFIXXcOkFXa_!!0-juitemmedia.jpg_320x320q80s150.jpg',
      title: '澳洲牛排10份装送刀叉酱料黄油',
      subtitle1: '送平底锅前3000仅78',
      subtitle2: '私厨经典 镇店套餐',
      got: 173,
      progress: 35,
      price: { real: 108, sale: 240.00 }
    }, {
      type: 'card',
      poster: 'http://gw.alicdn.com/tps/i2/2838892713/TB2ma39aqmgSKJjSsphXXcy1VXa_!!0-juitemmedia.jpg_320x320q80s150.jpg',
      title: 'HUAWEI P10',
      subtitle1: '买赠好礼6期免息',
      subtitle2: '6期免息',
      got: 996,
      progress: 89,
      price: { real: 3488, sale: 3488.00 }
    }, {
      type: 'card',
      poster: 'http://gw.alicdn.com/tps/i3/902257410/TB2pzypfU3IL1JjSZFMXXajrFXa_!!0-juitemmedia.jpg_320x320q80s150.jpg',
      title: '海宁真皮皮衣男绵羊皮夹克外套',
      subtitle1: '店内领券下单438',
      subtitle2: '限送500双皮手套',
      got: 296,
      progress: 16,
      price: { real: 538, sale: 3080.00 }
    }, {
      type: 'card',
      poster: 'https://gw.alicdn.com/tps/i4/0/TB2Mx3Jg4TI8KJjSspiXXbM4FXa_!!0-juitemmedia.jpg_320x320q80s150.jpg',
      title: '玛丽黛佳元气风动三色腮红正品',
      subtitle1: '满108领券立减10元',
      subtitle2: '宛若天生粉红好气色',
      got: 1457,
      progress: 61,
      price: { real: 49, sale: 69.80 }
    }, {
      type: 'card',
      poster: 'https://gw.alicdn.com/tps/i2/0/TB2i25DgN6I8KJjSszfXXaZVXXa_!!0-juitemmedia.jpg_320x320q80s150.jpg',
      title: '王小二高山脐橙，酸甜如初恋',
      subtitle1: '前3分钟半价',
      subtitle2: 'VC仓库，酸甜如初恋',
      got: 598,
      progress: 42,
      price: { real: 29.8, sale: 56.10 }
    }
  ]
}
// generate list data
function createListData (order) {
  var array = []
  var list = order.split(/[\s,]+/)
  for (var i = 0; i < list.length; ++i) {
    var candidates = dataset[list[i]]
    if (candidates) {
      var idx = Math.floor(Math.random() * candidates.length)
      array.push(candidates[idx])
    }
  }
  return array
}

import OfficeTest from './Office_test'
export default {
  components: {
    OfficeTest,
  },
  data () {
    const order = 'tab,banner,apps,apps,banner,card,floor,floor' +
       ',tab,apps,apps,banner,card,card,banner,floor,floor,floor' +
       ',tab,banner,card,apps,banner,card,floor,floor,floor,floor,floor' +
       ',tab,apps,banner,card,banner,floor,floor,floor' +
       ',tab,apps,apps,card,floor,card,banner,floor,floor' +
       ',tab,banner,card,apps,banner,card,floor,floor,floor,floor' +
       ',tab,apps,banner,card,card,apps,floor,floor,floor'
    return {
      longList: createListData(order)
    }
  }
}
</script>

<style scoped>
  .list {
    width: 100%;
    background-color: #EFEFEF;
  }
  .row {
    flex-direction: column;
  }

  .tab-cell {
    justify-content: stretch;
    background-color: #f51438;
  }
  .tab {
    height: 120uupx;
    width: 150uupx;
    justify-content: center;
    align-items: center;
  }
  .tab-icon {
    width: 45upx;
    height: 45upx;
  }
  .tab-title {
    font-size: 28upx;
    color: #FFF;
    margin-top: 10upx;
  }

  .banner-image {
    width: 750upx;
    height: 235upx;
  }

  .app-cell { background-color: #FFF; }
  .app-box {
    width: 180upx;
    padding-top: 15upx;
    padding-bottom: 15upx;
    padding-left: 15upx;
    padding-right: 15upx;
  }
  .app-title {
    width: 180upx;
    font-size: 30upx;
    text-align: center;
    padding-top: 15upx;
    color: #999999;
  }
  .app-icon {
    width: 140upx;
    height: 140upx;
    margin-left: 20upx;
  }

  .card {
    width: 710upx;
    margin: 20upx;
    background-color: #FFFFFF;
    border-radius: 15upx;
  }
  .card-banner {
    width: 222upx;
    height: 60upx;
  }
  .card-side {
    padding: 20upx;
  }
  .card-poster {
    width: 230upx;
    height: 230upx;
    margin-right: 20upx;
  }
  .card-title {
    font-size: 26upx;
    color: #666666;
    margin-top: 10upx;
    padding-bottom: 6upx;
  }
  .card-line {
    align-items: center;
    padding-top: 5upx;
    padding-bottom: 5upx;
  }
  .card-icon {
    width: 36upx;
    height: 36upx;
    margin-right: 8upx;
  }
  .card-subtitle {
    font-size: 28upx;
    color: #07152a;
  }
  .card-progress {
    flex-direction: row;
    align-items: center;
    width: 230upx;
    height: 30upx;
    background-color: #FEC1C1;
    border-radius: 20upx;
    margin-top: 10upx;
    margin-bottom: 10upx;
  }
  .card-progress-inner {
    position: absolute;
    height: 30upx;
    left: 0;
    border-radius: 20upx;
    background-color: #ff3c32;
  }
  .card-got {
    position: absolute;
    left: 8upx;
    line-height: 30upx;
    color: #FFFFFF;
    font-size: 22upx
  }
  .card-remain {
    position: absolute;
    right: 8upx;
    line-height: 30upx;
    color: #FFFFFF;
    font-size: 22upx;
  }
  .card-info {
    width: 400upx;
    flex-direction: row;
    align-items: flex-end;
  }
  .card-price {
    font-size: 52upx;
    color: #ff3c32;
    margin-bottom: -10upx;
    margin-top: 10upx;
    margin-right: 8upx;
  }
  .card-sale-price {
    font-size: 28upx;
    color: #999999;
    text-decoration: line-through;
  }
  .card-btn {
    position: absolute;
    right: 0;
    bottom: 0;
    background-color: #ff5d62;
    border-radius: 8upx;
    width: 125upx;
    height: 52upx;
    justify-content: center;
  }
  .card-btn-text {
    color: #FFFFFF;
    font-size: 32upx;
    text-align: center;
  }

  .floor {
    margin-bottom: 15upx;
    background-color: #FFF;
  }
  .floor-title {
    font-size: 40upx;
    text-align: center;
    padding-top: 35upx;
    padding-bottom: 25upx;
  }
  .floor-desc {
    lines: 2;
    color: #999;
    font-size: 30upx;
    padding-left: 30upx;
    padding-right: 30upx;
  }
  .floor-image-box {
    flex-direction: row;
    justify-content: space-between;
    margin-top: 20upx;
  }
  .floor-image {
    width: 245upx;
    height: 245upx;
  }
  .floor-comment {
    color: #52bfe6;
    font-size: 32upx;
    text-align: right;
    padding-right: 50upx;
    margin-top: 25upx;
    margin-bottom: 20upx;
  }
</style>
