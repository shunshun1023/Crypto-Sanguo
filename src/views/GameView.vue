<!--<template>
  <div class="game-view">
    <div class="game-wrapper">
      <iframe height="740"
              width="1120"
              src="./static/cocos/index.html">
        <p>Your browser does not support iframes.</p>
      </iframe>
    </div>
  </div>
</template>

<script>
export default {
  components: {},

  created() {},
};
</script>

<style scoped>
.game-wrapper {
  height: 100vh;
}
</style>-->

<template> 
  <div class="game-view">
    <div class="columns">
      <div class="column">
        <ve-map height="100vh"
                :data="chartData"
                :legend-visible="legendVisible"
                :settings="chartSettings"
                :events="chartEvents"
                :extend="chartExtend"></ve-map>
      </div>
      <div class="tile is-parent">
        <div class="column">
          <article class="is-child notification is-primary">
            <div class="columns is-mobile">
              <div class="column has-text-left subtitle">
                城市
              </div>
              <div class="column has-text-right subtitle">
                {{selectedstatus.name}}<!--新野-->
              </div>
              <div class="column has-text-left subtitle">
                太守
              </div>
              <div class="column has-text-right subtitle">
                岛娘
              </div>
            </div>
            <div class="columns is-mobile">
              <div class="column has-text-left">
                金
              </div>
              <div class="column has-text-right">
                1000
              </div>
              <div class="column has-text-left">
                粮
              </div>
              <div class="column has-text-right">
                20000
              </div>
            </div>
            <div class="columns is-mobile">
              <div class="column has-text-left">
                农业
              </div>
              <div class="column has-text-right">
                940/1000
              </div>
              <div class="column has-text-left">
                商业
              </div>
              <div class="column has-text-right">
                460/800
              </div>
            </div>
            <div class="columns is-mobile">
              <div class="column has-text-left">
                兵力
              </div>
              <div class="column has-text-right">
                10000
              </div>
            </div>
            <div class="columns is-mobile">
              <div class="column has-text-left">
                武将
              </div>
              <div class="column has-text-right">
                5
              </div>
            </div>
            <div class="columns is-mobile">
              <div class="column has-text-left">
                城防
              </div>
              <div class="column has-text-right">
                1000/1000
              </div>
            </div>
          </article>
          <article class="is-child notification is-warning">
            <div class="columns is-mobile">
              <div class="column is-one-fifth"><a class="button">军事</a></div>
              <div class="column is-one-fifth"><a class="button">内政</a></div>
              <div class="column is-one-fifth"><a class="button">人事</a></div>
              <div class="column is-one-fifth"><a class="button">计谋</a></div>
              <div class="column is-one-fifth"><a class="button">外交</a></div>
              <!-- <a class="button">军事</a>
              <a class="button">内政</a>
              <a class="button">人事</a>
              <a class="button">计谋</a>
              <a class="button">外交</a> -->
            </div>
          </article>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VeMap from 'v-charts/lib/map';
export default {
  components: { VeMap },
  created() {
    this.chartData = {
      columns: ['位置', '势力', '兵力', '城防', '人口'],
      rows: [
        { 位置: '北平', 兵力: 11, 城防: 250, 势力: 999, 人口: 123 },
        { 位置: '襄平', 人口: 1223 },
        { 位置: '蓟', 人口: 321 },
        { 位置: '晋阳'},
        { 位置: '上党'},
        { 位置: '南皮'},
        { 位置: '兒'},
        { 位置: '北海'},
        { 位置: '陈留'},
        { 位置: '洛阳'},
        { 位置: '弘农'},
        { 位置: '长安'},
        { 位置: '天水'},
        { 位置: '武威'},
        { 位置: '酒泉'},
        { 位置: '下堰'},
        { 位置: '许昌'},
        { 位置: '寿春'},
        { 位置: '南阳'},
        { 位置: '襄阳'},
        { 位置: '长沙'},
        { 位置: '桂阳'},
        { 位置: '零陵'},
        { 位置: '建业'},
        { 位置: '会稽'},
        { 位置: '建安'},
        { 位置: '阜阳'},
        { 位置: '柴桑'},
        { 位置: '汉中'},
        { 位置: '武都'},
        { 位置: '永安'},
        { 位置: '江州'},
        { 位置: '成都'},
        { 位置: '朱提'},
        { 位置: '永昌'},
        { 位置: '建宁'},
        { 位置: '南海'},
        { 位置: '苍梧'},
        { 位置: '合浦'},
        { 位置: '郁林'},
        { 位置: '交趾'},
      ],
    };
    var theself = this;
    this.selectedstatus = {name : "wow"};
    this.legendVisible = false;
    this.chartSettings = {
      positionJsonLink: './static/gameGeo.json',
      position: 'world',
      beforeRegisterMap(json) {
        return json;
      },
      selectedMode: 'single',
      zoom: 1,
      roam: false,
      itemStyle: {
        normal: {
          borderColor: 'rgba(0, 0, 0, 0.2)',
        },
        emphasis: {
          areaColor: null,
          shadowOffsetX: 0,
          shadowOffsetY: 0,
          shadowBlur: 20,
          borderWidth: 0,
          shadowColor: 'rgba(0, 0, 0, 0.5)',
        },
      },
    };
    this.chartExtend = {
      series: {
        showLegendSymbol: false,
        nameMap: {
          XiangPing: '襄平',
          BeiPing: '北平',
          Ji: '蓟',
          JinYang: '晋阳',
          ShangDang: '上党',
          NanPi: '南皮',
          Er: '兒',
          BeiHai: '北海',
          ChenLiu: '陈留',
          LuoYang: '洛阳',
          HongNong: '弘农',
          ChangAn: '长安',
          TianShui: '天水',
          WuWei: '武威',
          JiuQuan: '酒泉',
          XiaYan: '下堰',
          XuChang: '许昌',
          ShouChun: '寿春',
          NanYang: '南阳',
          XiangYang: '襄阳',
          ChangSha: '长沙',
          GuiYang: '桂阳',
          LingLing: '零陵',
          JianYe: '建业',
          KuaiJi: '会稽',
          JianAn: '建安',
          FuYang: '阜阳',
          ChaiSang: '柴桑',
          HanZhong: '汉中',
          WuDu: '武都',
          YongAn: '永安',
          JiangZhou: '江州',
          ChengDu: '成都',
          ZhuTi: '朱提',
          YongChang: '永昌',
          JianNing: '建宁',
          NanHai: '南海',
          CangWu: '苍梧',
          HePu: '合浦',
          YuLin: '郁林',
          JiaoZhi: '交趾',
        },
      },
    };
    this.chartEvents = {
      click(e){
        theself.selectedstatus = e;
        theself.$forceUpdate();
        console.log(e);
        console.log(this);
        console.log(theself);
      },
      mouseover(e) {
        console.log(e.name);
      },
    };
  },
};
</script>