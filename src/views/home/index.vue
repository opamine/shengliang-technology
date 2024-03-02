<template>
  <div class="container">
    <!-- <div>{{ innerWidth > 886 ? 'pc' : '移动' }}</div> -->
    <div class="top-nav">
      <div class="logo-container" @click="scrollTopTo(0)">
        <img src="../../assets/logo.png" alt="" class="logo-img" />
        <img src="../../assets/logo-text.png" class="logo-text" />
      </div>
      <!-- PC端 -->
      <div v-if="innerWidth > 886" class="menu-container">
        <div class="menus">
          <div class="menu-item" @click="scrollTopTo(0)">首页</div>
          <div class="menu-item" @click="scrollTopTo(innerHeight - 70)">平台优势</div>
          <div class="menu-item" @click="scrollTopTo(innerHeight - 70 + 963)">产品服务</div>
          <div class="menu-item" @click="scrollTopTo(innerHeight - 70 + 963 + 903)"
            >合作流程</div
          >
          <div class="menu-item" @click="scrollTopTo(innerHeight - 70 + 963 + 903 + 1296)"
            >联系我们</div
          >
          <div class="menu-item" @click="scrollTopTo(innerHeight - 70 + 963 + 903 + 1296)"
            >技术文档</div
          >
          <!-- <div class="menu-item">
            <div class="menu-item-content">
              <span style="margin-right: 4px">技术文档</span>
              <i class="iconfont icon-xia_line" style="font-size: 10px; font-weight: 600"></i>
            </div>
            <div class="menu-item-childs">
              <div class="menu-item-child-item">文档链接1</div>
              <div class="menu-item-child-item">文档链接2</div>
            </div>
          </div> -->
        </div>
      </div>
      <!-- 移动端 -->
      <template v-else>
        <div style="height: 24px" @click="handleMobileMenuExpand">
          <i class="iconfont icon-gengduo2_line" style="font-size: 24px; color: #6c6c6c"></i>
        </div>
        <div class="mobile-menu-modal" :class="{ expand: mobileMenuExpand }">
          <div class="modal-content">
            <div class="menus">
              <div
                v-for="(item, index) in menusData"
                class="menu-item"
                @click="mobileMenuClick(index)"
                >{{ item.title }}</div
              >
            </div>
          </div>
        </div>
      </template>
    </div>
    <div class="hero" :style="innerWidth > 886 ? { height: innerHeight - 70 + 'px' } : {}">
      <div class="slide1">
        <div class="art">
          <div class="art-title">携手开发者，共赢未来</div>
          <div class="art-sub-title">专注于为移动应用开发者提供便捷高效的流量变现解决方案。</div>
          <div class="art-sub-title"
            >助力开发者构建完善的商业化运营体系，提升变现能力，实现媒体商业价值。</div
          >
        </div>
      </div>
    </div>
    <div class="platform-advantages">
      <div class="title">平台优势</div>
      <div class="advantages">
        <div v-for="(item, index) in advantagesData" :key="index" class="advantage-item">
          <div class="icon-container">
            <img :src="item.icon" alt="" />
          </div>
          <div class="advantage-title">{{ item.title }}</div>
          <div class="advantage-desc">{{ item.desc }}</div>
        </div>
      </div>
    </div>
    <div class="product-service">
      <div class="title">产品服务</div>
      <div class="service">
        <div class="tabs">
          <div
            v-for="(item, index) in serviceTabsData"
            :key="index"
            class="tab-item"
            :class="{ active: currentTabIndex === index }"
            @click="onTabClick(index)"
            >{{ item.title }}</div
          >
        </div>
        <div class="phone-preview">
          <div class="preview-img"><img :src="serviceTabsData[currentTabIndex].img" alt="" /></div>
          <div class="phone"></div>
        </div>
      </div>
    </div>
    <div class="cooperation-process">
      <div class="title"> 合作流程 </div>
      <div class="process">
        <template v-if="innerWidth > 886">
          <div class="index-num">
            <svg
              width="86"
              height="1002"
              viewBox="0 0 86 1002"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="43" cy="43" r="38.5" fill="white" stroke="#8CB5FD" stroke-width="9" />
              <path
                d="M37.6559 53C37.2359 53 36.9059 52.88 36.6659 52.64C36.4259 52.4 36.3059 52.08 36.3059 51.68C36.3059 51.26 36.4259 50.94 36.6659 50.72C36.9059 50.5 37.2359 50.39 37.6559 50.39H41.3159V34.43H42.8759L38.4959 37.22C38.1759 37.4 37.8759 37.47 37.5959 37.43C37.3359 37.39 37.1059 37.28 36.9059 37.1C36.7259 36.92 36.5959 36.7 36.5159 36.44C36.4559 36.18 36.4759 35.91 36.5759 35.63C36.6959 35.35 36.9059 35.12 37.2059 34.94L41.3459 32.33C41.6859 32.13 42.0059 31.97 42.3059 31.85C42.6259 31.71 42.9259 31.64 43.2059 31.64C43.5459 31.64 43.8259 31.74 44.0459 31.94C44.2859 32.12 44.4059 32.43 44.4059 32.87V50.39H47.7659C48.2059 50.39 48.5459 50.5 48.7859 50.72C49.0259 50.94 49.1459 51.26 49.1459 51.68C49.1459 52.1 49.0259 52.43 48.7859 52.67C48.5459 52.89 48.2059 53 47.7659 53H37.6559Z"
                fill="#292930"
              />
              <circle
                cx="43"
                cy="348.333"
                r="38.5"
                fill="white"
                stroke="#8CB5FD"
                stroke-width="9"
              />
              <path
                d="M36.9359 358.667C36.3959 358.667 36.0059 358.547 35.7659 358.307C35.5259 358.047 35.4059 357.697 35.4059 357.257C35.4059 356.977 35.4759 356.707 35.6159 356.447C35.7559 356.187 35.9559 355.917 36.2159 355.637L42.6059 348.797C43.5859 347.757 44.2859 346.807 44.7059 345.947C45.1459 345.067 45.3659 344.187 45.3659 343.307C45.3659 342.187 45.0259 341.337 44.3459 340.757C43.6659 340.177 42.6659 339.887 41.3459 339.887C40.5459 339.887 39.7759 340.007 39.0359 340.247C38.2959 340.487 37.5559 340.877 36.8159 341.417C36.5159 341.617 36.2359 341.707 35.9759 341.687C35.7159 341.667 35.4859 341.567 35.2859 341.387C35.1059 341.207 34.9859 340.987 34.9259 340.727C34.8659 340.467 34.8759 340.197 34.9559 339.917C35.0359 339.637 35.2259 339.397 35.5259 339.197C36.3459 338.577 37.2959 338.097 38.3759 337.757C39.4559 337.417 40.5559 337.247 41.6759 337.247C43.1359 337.247 44.3659 337.477 45.3659 337.937C46.3859 338.377 47.1559 339.027 47.6759 339.887C48.1959 340.747 48.4559 341.797 48.4559 343.037C48.4559 343.877 48.3159 344.697 48.0359 345.497C47.7759 346.297 47.3659 347.117 46.8059 347.957C46.2659 348.777 45.5559 349.647 44.6759 350.567L38.6159 356.927V356.057H48.1559C48.5959 356.057 48.9359 356.167 49.1759 356.387C49.4159 356.607 49.5359 356.927 49.5359 357.347C49.5359 357.767 49.4159 358.097 49.1759 358.337C48.9359 358.557 48.5959 358.667 48.1559 358.667H36.9359Z"
                fill="#292930"
              />
              <circle
                cx="43"
                cy="653.667"
                r="38.5"
                fill="white"
                stroke="#8CB5FD"
                stroke-width="9"
              />
              <path
                d="M41.6759 663.937C40.5559 663.937 39.4159 663.787 38.2559 663.487C37.0959 663.167 36.0859 662.697 35.2259 662.077C34.9059 661.877 34.6859 661.637 34.5659 661.357C34.4659 661.057 34.4459 660.787 34.5059 660.547C34.5659 660.287 34.6859 660.067 34.8659 659.887C35.0659 659.707 35.3059 659.607 35.5859 659.587C35.8659 659.547 36.1759 659.627 36.5159 659.827C37.3759 660.347 38.2159 660.727 39.0359 660.967C39.8559 661.187 40.7059 661.297 41.5859 661.297C42.5459 661.297 43.3559 661.157 44.0159 660.877C44.6759 660.597 45.1659 660.187 45.4859 659.647C45.8259 659.107 45.9959 658.457 45.9959 657.697C45.9959 656.557 45.6159 655.707 44.8559 655.147C44.1159 654.567 43.0359 654.277 41.6159 654.277H39.5759C39.1159 654.277 38.7659 654.167 38.5259 653.947C38.2859 653.707 38.1659 653.377 38.1659 652.957C38.1659 652.557 38.2859 652.247 38.5259 652.027C38.7659 651.787 39.1159 651.667 39.5759 651.667H41.3159C42.1759 651.667 42.9059 651.527 43.5059 651.247C44.1059 650.947 44.5659 650.537 44.8859 650.017C45.2259 649.477 45.3959 648.827 45.3959 648.067C45.3959 647.047 45.0559 646.267 44.3759 645.727C43.7159 645.167 42.7459 644.887 41.4659 644.887C40.6459 644.887 39.8659 644.997 39.1259 645.217C38.4059 645.437 37.6559 645.827 36.8759 646.387C36.5759 646.587 36.2859 646.677 36.0059 646.657C35.7459 646.617 35.5159 646.517 35.3159 646.357C35.1359 646.177 35.0059 645.957 34.9259 645.697C34.8659 645.437 34.8859 645.167 34.9859 644.887C35.0859 644.607 35.2859 644.367 35.5859 644.167C36.4259 643.547 37.3759 643.077 38.4359 642.757C39.4959 642.417 40.5859 642.247 41.7059 642.247C43.1059 642.247 44.3059 642.467 45.3059 642.907C46.3259 643.347 47.0959 643.977 47.6159 644.797C48.1559 645.617 48.4259 646.597 48.4259 647.737C48.4259 648.597 48.2659 649.377 47.9459 650.077C47.6259 650.777 47.1659 651.377 46.5659 651.877C45.9859 652.357 45.2759 652.697 44.4359 652.897V652.567C45.8959 652.807 47.0259 653.407 47.8259 654.367C48.6259 655.307 49.0259 656.487 49.0259 657.907C49.0259 659.147 48.7259 660.227 48.1259 661.147C47.5459 662.047 46.7059 662.737 45.6059 663.217C44.5059 663.697 43.1959 663.937 41.6759 663.937Z"
                fill="#292930"
              />
              <circle cx="43" cy="959" r="38.5" fill="white" stroke="#8CB5FD" stroke-width="9" />
              <path
                d="M45.4859 969.21C45.0059 969.21 44.6259 969.08 44.3459 968.82C44.0659 968.54 43.9259 968.16 43.9259 967.68V964.71H35.8859C35.3859 964.71 34.9859 964.6 34.6859 964.38C34.3859 964.16 34.2359 963.82 34.2359 963.36C34.2359 963.1 34.2959 962.82 34.4159 962.52C34.5559 962.22 34.7959 961.83 35.1359 961.35L43.8659 948.66C44.0859 948.32 44.3359 948.07 44.6159 947.91C44.8959 947.73 45.2159 947.64 45.5759 947.64C45.9959 947.64 46.3359 947.77 46.5959 948.03C46.8759 948.27 47.0159 948.65 47.0159 949.17V962.1H48.9059C49.3859 962.1 49.7359 962.21 49.9559 962.43C50.1959 962.65 50.3159 962.97 50.3159 963.39C50.3159 963.83 50.1959 964.16 49.9559 964.38C49.7359 964.6 49.3859 964.71 48.9059 964.71H47.0159V967.68C47.0159 968.16 46.8759 968.54 46.5959 968.82C46.3359 969.08 45.9659 969.21 45.4859 969.21ZM43.9259 962.1V951.51H44.7359L36.9059 962.94V962.1H43.9259Z"
                fill="#292930"
              />
            </svg>
          </div>
          <div class="line">
            <svg
              width="2"
              height="942"
              viewBox="0 0 2 942"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <line
                x1="0.749817"
                y1="0.946533"
                x2="0.749776"
                y2="942"
                stroke="#3674E2"
                stroke-width="1.5"
                stroke-dasharray="5 5"
              />
            </svg>
          </div>
        </template>
        <template v-else>
          <div class="index-num">
            <div class="index">1</div>
            <div class="index">2</div>
            <div class="index">3</div>
            <div class="index">4</div>
          </div>
          <div class="line">
            <svg
              width="2"
              height="700"
              viewBox="0 0 2 700"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <line
                x1="0.749817"
                y1="0.946533"
                x2="0.749776"
                y2="700"
                stroke="#3674E2"
                stroke-width="1.5"
                stroke-dasharray="5 5"
              />
            </svg>
          </div>
        </template>
        <div class="steps">
          <div class="step">
            <div class="img"><img src="../../assets/step-1.png" /></div>
            <div class="step-title">联系我们</div>
          </div>
          <div class="step">
            <div class="step-title">创建对接小组</div>
            <div class="img">
              <div><img src="../../assets/step-2-01.png" alt="" /></div>
              <div><img src="../../assets/step-2-01.png" alt="" /></div>
              <div><img src="../../assets/step-2-02.png" alt="" /></div>
            </div>
          </div>
          <div class="step">
            <div class="img"><img src="../../assets/step-3.png" /></div>
            <div class="step-title">接入 SDK</div>
          </div>
          <div class="step">
            <div class="step-title">上线收益</div>
            <div class="img">
              <img src="../../assets/step-4.png" />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="contact-us"
    >
      <div class="title">联系我们</div>
      <div class="detail">
        <div class="address">
          <div>微信：SlowButSure_li</div>
          <div>QQ：1980678623</div>
        </div>
        <div class="qrcode">
          <img src="../../assets//weixin01.png" alt="" />
          <img src="../../assets//weixin02.png" alt="" />
        </div>
      </div>
    </div>
    <div class="copyright">
      <div>Copyright@ 2024 北京升量科技有限公司 版权所有</div>
      <div><a style="text-decoration: none;color: inherit;" href="https://beian.miit.gov.cn">京ICP备2024046777号</a></div>
    </div>
  </div>
</template>
<script setup>
  import { ref, onMounted, onUnmounted } from 'vue';

  // 菜单列表
  const menusData = [
    { title: '首页', external: false },
    { title: '平台优势', external: false },
    { title: '产品服务', external: false },
    { title: '合作流程', external: false },
    { title: '联系我们', external: false },
    { title: '技术文档', external: false },
  ];

  // 平台优势
  const advantagesData = [
    {
      title: '数据真实',
      desc: '数据公开透明，开发者可实时查看数据、流量、收益',
      icon: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/advantage-01.png',
    },
    {
      title: '高填充、高收益',
      desc: '智能算法引擎，高效自动化，填充率接近100%，收益至少提高30%',
      icon: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/advantage-02.png',
    },
    {
      title: '对接门槛低',
      desc: '支持个人开发者/无需上架/无需软著',
      icon: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/advantage-03.png',
    },
    {
      title: '广告资源',
      desc: '集成穿山甲、优量汇等多个大平台以及丰富的广告类型',
      icon: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/advantage-04.png',
    },
    {
      title: '定期广告优化',
      desc: '广告调优指导，免费咨询广告调优策略， 帮助开发者广告收益最大化',
      icon: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/advantage-05.png',
    },
    {
      title: '7*24h服务',
      desc: '数据公开透明，开发者可实时查看数据、流量、收益',
      icon: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/advantage-06.png',
    },
  ];

  // 产品服务
  const serviceTabsData = [
    {
      title: '开屏广告',
      img: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/service01.png',
    },
    {
      title: '激励视频',
      img: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/service02.png',
    },
    {
      title: '插屏',
      img: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/service03.png',
    },
    {
      title: 'Banner',
      img: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/service04.png',
    },
    {
      title: '信息流',
      img: 'https://zzh-assets.oss-cn-hangzhou.aliyuncs.com/shengliang-technology/service05.png',
    },
  ];

  const currentTabIndex = ref(0);

  const onTabClick = (index) => {
    currentTabIndex.value = index;
  };

  let timer = null;

  const scrollTopTo = (y) => {
    window.scrollTo({
      top: y,
      left: 0,
      behavior: 'smooth',
    });
  };

  // 视图区域宽高，用于定义响应式
  const innerWidth = ref(window.innerWidth);
  const innerHeight = ref(window.innerHeight);

  // 移动端菜单是否展开
  const mobileMenuExpand = ref(false);

  const handleMobileMenuExpand = () => {
    mobileMenuExpand.value = !mobileMenuExpand.value;
  };

  const mobileMenuClick = (index) => {
    mobileMenuExpand.value = false;
    switch (index) {
      case 0:
        scrollTopTo(0);
        break;
      case 1:
        scrollTopTo(354);
        break;
      case 2:
        scrollTopTo(1728);
        break;
      case 3:
        scrollTopTo(2482);
        break;
      case 4:
        scrollTopTo(2930);
        break;
      case 5:
        scrollTopTo(2930);
        break;
      default:
        break;
    }
    console.log(index);
  };

  onMounted(() => {
    window.onresize = (e) => {
      innerWidth.value = e.target.innerWidth;
      innerHeight.value = e.target.innerHeight;
    };

    timer = setInterval(() => {
      if (currentTabIndex.value === serviceTabsData.length - 1) {
        currentTabIndex.value = 0;
      } else {
        currentTabIndex.value = currentTabIndex.value + 1;
      }
    }, 3000);
  });

  onUnmounted(() => {
    timer && clearInterval(timer);
    timer = null;
  });
</script>
<style lang="less" scoped>
  // pc 样式
  @media screen and (min-width: 886px) {
    .container {
      padding-top: 70px;
      .top-nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        position: fixed;
        left: 0;
        top: 0;
        width: 100%;
        padding: 15px 80px;
        box-sizing: border-box;
        box-shadow: 0 5px 6px -5px rgba(133, 133, 133, 0.6);
        background-color: #fff;
        z-index: 9999;

        .logo-container {
          display: flex;
          align-items: center;
          cursor: pointer;
          .logo-img {
            width: 40px;
            margin-right: 6px;
          }
          .logo-text {
            height: 24px;
          }
        }
        .menu-container {
          .menus {
            display: flex;
            font-size: 16px;
            .menu-item {
              position: relative;
              margin-right: 32px;
              cursor: pointer;
              &:hover {
                color: #408cfd;
                .menu-item-childs {
                  height: 74px;
                }
              }
              .menu-item-content {
                display: flex;
                align-items: center;
              }
              .menu-item-childs {
                position: absolute;
                top: 30px;
                width: 100px;
                height: 0px;
                border-radius: 4px;
                box-shadow: 0 12px 32px rgba(0, 0, 0, 0.1), 0 2px 6px rgba(0, 0, 0, 0.08);
                color: #000;
                font-size: 14px;
                text-align: center;
                transition: all 0.3s;
                overflow: hidden;
                background-color: #fff;
                z-index: 999;
                .menu-item-child-item {
                  margin-top: 12px;
                  margin-bottom: 12px;
                }
              }
              &:last-of-type {
                margin-right: 0;
              }
            }
          }
        }
      }
      .hero {
        position: relative;
        height: 600px;
        box-sizing: border-box;
        .slide1 {
          position: relative;
          height: 100%;
          background: url('../../assets/back-pc.png');
          background-size: 100% 100%;
          .art {
            position: absolute;
            top: 315px;
            left: 80px;
            .art-title {
              margin-bottom: 8px;
              color: #444;
              font-size: 48px;
              font-weight: 700;
              line-height: normal;
              letter-spacing: 3.84px;
            }
            .art-sub-title {
              color: #666;
              font-size: 20px;
              font-weight: 400;
              line-height: normal;
            }
          }
        }
      }
      .platform-advantages {
        margin-top: 30px;
        padding: 0 80px 80px;
        .title {
          color: #3674e2;
          font-size: 40px;
          font-weight: 400;
        }
        .advantages {
          display: flex;
          flex-wrap: wrap;
          gap: 40px;
          margin-top: 48px;
          .advantage-item {
            width: calc((100% - 80px) / 3);
            height: 354.5px;
            padding: 56px 32px;
            text-align: center;
            box-shadow: 0px 4px 28.600000381469727px rgba(54, 116, 226, 0.08);
            border-radius: 12px;
            box-sizing: border-box;
            .icon-container {
              img {
                width: 100px;
              }
            }
            .advantage-title {
              margin-top: 48px;
              color: #111;
              font-size: 20px;
            }
            .advantage-desc {
              margin-top: 16px;
              color: rgba(0, 0, 0, 0.6);
              font-size: 16px;
            }
          }
        }
      }
      .product-service {
        padding: 40px 80px;
        background: url('../../assets/back-service-pc.png');
        background-size: 100% 100%;
        .title {
          color: #3674e2;
          font-size: 40px;
          font-weight: 400;
        }
        .service {
          .tabs {
            display: flex;
            width: 521px;
            height: 48px;
            margin: 48px auto 0;
            padding: 4px;
            border-radius: 48px;
            background-color: #c8dcff;
            box-shadow: 0px 4px 7.3px 0px rgba(0, 0, 0, 0.25);
            box-sizing: border-box;
            .tab-item {
              width: 20%;
              height: 40px;
              border-radius: 40px;
              text-align: center;
              line-height: 40px;
              color: #111;
              font-size: 16px;
              cursor: pointer;
              transition: all 0.2s;
              &.active {
                color: #fff;
                background-color: #4d74de;
              }
            }
          }
          .phone-preview {
            position: relative;
            margin-top: 20px;
            margin-left: auto;
            margin-right: auto;
            width: 325px;
            height: 651px;
            .preview-img {
              position: absolute;
              width: 310px;
              height: 651px;
              z-index: 0;
              img {
                position: absolute;
                left: 53%;
                transform: translateX(-50%);
                width: 310px;
                height: 651px;
              }
            }
            .phone {
              position: absolute;
              width: 325px;
              height: 651px;
              margin: 0 auto;
              background: url('../../assets/iphone.png');
              background-size: 100% 100%;
              z-index: 1;
            }
          }
        }
      }
      .cooperation-process {
        padding: 40px 80px;
        .title {
          color: #3674e2;
          font-size: 40px;
          font-weight: 400;
        }
        .process {
          position: relative;
          height: 1080px;
          .index-num {
            position: absolute;
            top: 36px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 999;
          }
          .line {
            position: absolute;
            top: 36px;
            left: 50%;
            transform: translateX(-50%);
          }
          .steps {
            .step {
              display: flex;
              align-items: center;
              justify-content: center;
              margin-top: 80px;
              .img {
                width: 250px;
                img {
                  width: 100%;
                }
              }
              .step-title {
                color: #111;
                font-size: 20px;
                font-weight: 600;
                width: 250px;
              }
              &:nth-of-type(1),
              &:nth-of-type(3) {
                .img {
                  margin-right: 143px;
                }
              }
              &:nth-of-type(2),
              &:nth-of-type(4) {
                .step-title {
                  margin-right: 143px;
                  text-align: right;
                }
              }
              &:nth-of-type(2) {
                margin-top: 108px;
              }
              &:nth-of-type(3) {
                margin-top: 67px;
              }
              &:nth-of-type(4) {
                margin-top: 99px;
              }
            }
          }
        }
      }
      .contact-us {
        padding: 40px 80px 72px;
        background-color: #e8f0fe;
        box-sizing: border-box;
        .title {
          color: #3674e2;
          font-size: 40px;
          font-weight: 400;
        }
        .detail {
          margin-top: 48px;
          .address {
            font-size: 14px;
            color: #111;
          }
          .qrcode {
            margin-top: 48px;
            img {
              width: 250px;
              margin-right: 48px;
            }
          }
        }
      }
      .copyright {
        padding: 24px 0;
        text-align: center;
        font-size: 14px;
        color: rgba(0, 0, 0, 0.4);
        background-color: #e8f0fe;
      }
    }
  }

  // 移动端样式
  @media screen and (max-width: 886px) {
    .container {
      padding-top: 48px;
      .top-nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        height: 48px;
        padding: 12px 20px;
        box-sizing: border-box;
        box-shadow: 0 5px 6px -5px rgba(133, 133, 133, 0.6);
        background-color: #fff;
        position: fixed;
        left: 0;
        top: 0;
        z-index: 9999;

        .logo-container {
          display: flex;
          align-items: center;
          cursor: pointer;
          .logo-img {
            width: 24px;
            margin-right: 6px;
          }
          .logo-text {
            height: 16px;
          }
        }
        .mobile-menu-modal {
          position: fixed;
          top: 48px;
          right: 0;
          box-shadow: 0 12px 32px rgba(0, 0, 0, 0.1), 0 2px 6px rgba(0, 0, 0, 0.08);
          color: #000;
          font-size: 14px;
          height: 0;
          overflow: hidden;
          transition: all 0.3s;
          &.expand {
            height: 204px;
          }
          .modal-content {
            padding: 6px 0;
            background-color: #fff;
            .menus {
              .menu-item {
                padding: 6px 32px;
                cursor: pointer;
              }
            }
          }
        }
      }
      .hero {
        position: relative;
        height: 352px;
        .slide1 {
          position: relative;
          height: 100%;
          background: url('../../assets/back-mobile.png');
          background-size: 100% 100%;
          .art {
            position: absolute;
            top: 74px;
            left: 24px;
            text-align: center;
            .art-title {
              margin-bottom: 8px;
              color: #444;
              font-size: 36px;
              font-weight: 700;
              line-height: normal;
              letter-spacing: 2.88px;
            }
            .art-sub-title {
              color: #666;
              font-size: 16px;
              font-weight: 400;
              line-height: normal;
            }
          }
        }
      }
      .platform-advantages {
        margin-top: 48px;
        padding: 0 20px;
        .title {
          color: #3674e2;
          font-size: 24px;
          font-weight: 400;
        }
        .advantages {
          display: block;
          .advantage-item {
            margin-top: 20px;
            padding: 16px;
            text-align: center;
            border-radius: 4px;
            background: #fff;
            box-shadow: 0px 4px 19.5px 0px rgba(54, 116, 226, 0.08);
            height: 195px;
            box-sizing: border-box;
            .icon-container {
              img {
                width: 50px;
              }
            }
            .advantage-title {
              margin-top: 16px;
              color: #111;
              font-size: 20px;
            }
            .advantage-desc {
              margin-top: 16px;
              color: rgba(0, 0, 0, 0.6);
              font-size: 16px;
            }
          }
        }
      }
      .product-service {
        padding: 32px 20px;
        background: url('../../assets/back-service-pc.png');
        background-size: 100% 100%;
        .title {
          color: #3674e2;
          font-size: 24px;
          font-weight: 400;
        }
        .service {
          .tabs {
            display: flex;
            width: 330px;
            height: 34px;
            margin: 24px auto 0;
            padding: 4px;
            border-radius: 34px;
            background-color: #c8dcff;
            box-shadow: 0px 4px 7.3px 0px rgba(0, 0, 0, 0.25);
            box-sizing: border-box;

            .tab-item {
              width: 20%;
              height: 26px;
              border-radius: 26px;
              text-align: center;
              line-height: 26px;
              color: #111;
              font-size: 12px;
              cursor: pointer;
              transition: all 0.2s;
              &.active {
                color: #fff;
                background-color: #4d74de;
              }
            }
          }
          .phone-preview {
            position: relative;
            margin-top: 24px;
            margin-left: auto;
            margin-right: auto;
            width: 292px;
            height: 569px;
            .preview-img {
              position: absolute;
              width: 277px;
              height: 569px;
              z-index: 0;
              img {
                position: absolute;
                left: 53%;
                transform: translateX(-50%);
                width: 277px;
                height: 569px;
              }
            }
            .phone {
              position: absolute;
              width: 292px;
              height: 569px;
              margin: 0 auto;
              background: url('../../assets/iphone.png');
              background-size: 100% 100%;
              z-index: 1;
            }
          }
        }
      }
      .cooperation-process {
        padding: 32px 20px;
        .title {
          color: #3674e2;
          font-size: 24px;
          font-weight: 400;
        }
        .process {
          position: relative;
          margin-top: 28px;
          .index-num {
            position: absolute;
            top: 36px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 999;
            .index {
              border: 2px solid #8cb5fd;
              width: 32px;
              height: 32px;
              margin-top: 124px;
              text-align: center;
              line-height: 32px;
              border-radius: 50%;
              background-color: #fff;
              &:nth-of-type(1) {
                margin-top: -13px;
              }
              &:nth-of-type(2) {
                margin-top: 195px;
              }
              &:nth-of-type(3) {
                margin-top: 214px;
              }
              &:nth-of-type(4) {
                margin-top: 192px;
              }
            }
          }
          .line {
            position: absolute;
            top: 36px;
            left: 50%;
            transform: translateX(-50%);
          }
          .steps {
            .step {
              display: flex;
              align-items: center;
              justify-content: center;
              margin-top: 123px;
              .img {
                width: 126px;
                img {
                  width: 100%;
                }
              }
              .step-title {
                color: #111;
                font-size: 12px;
                font-weight: 600;
                width: 126px;
              }
              &:nth-of-type(1) {
                margin-top: 0;
              }
              &:nth-of-type(1),
              &:nth-of-type(3) {
                .img {
                  margin-right: 66px;
                }
              }
              &:nth-of-type(2),
              &:nth-of-type(4) {
                .step-title {
                  margin-right: 66px;
                  text-align: right;
                }
              }
              // &:nth-of-type(2) {
              //   margin-top: 108px;
              // }
              // &:nth-of-type(3) {
              //   margin-top: 67px;
              // }
              // &:nth-of-type(4) {
              //   margin-top: 99px;
              // }
            }
          }
        }
      }
      .contact-us {
        padding: 32px 20px 30px;
        background-color: #e8f0fe;
        box-sizing: border-box;
        .title {
          color: #3674e2;
          font-size: 24px;
          font-weight: 400;
        }
        .detail {
          margin-top: 20px;
          .address {
            font-size: 14px;
            color: #111;
          }
          .qrcode {
            margin-top: 20px;
            img {
              width: 125px;
              margin-right: 12px;
            }
          }
        }
      }
      .copyright {
        padding: 24px 0;
        border-top: 1px solid rgba(0, 0, 0, 0.2);
        text-align: center;
        font-size: 12px;
        color: rgba(0, 0, 0, 0.4);
        background-color: #e8f0fe;
        box-sizing: border-box;
      }
    }
  }
</style>
