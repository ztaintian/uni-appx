# 淘宝购物

基于 **uni-app x** 开发的淘宝风格购物 App 演示项目，使用 Vue 3 组合式 API 与 UTS 语言，支持 Android、iOS、Web 及小程序等多端运行。

## 功能概览

| 模块 | 说明 |
|------|------|
| 首页 | 搜索栏、轮播图、分类入口、限时秒杀、双列商品推荐 |
| 分类 | 左侧分类导航 + 右侧商品列表 |
| 购物车 | 商品勾选、数量加减、全选、合计金额、结算入口 |
| 我的 | 用户信息、订单状态入口、常用功能菜单 |
| 商品详情 | 商品图片、价格标签、店铺信息、加入购物车 / 立即购买 |

## 技术栈

- [uni-app x](https://doc.dcloud.net.cn/uni-app-x/) — 原生渲染的跨端框架
- Vue 3 `<script setup>` + UTS
- SCSS 样式（主题色 `#FF5000`）
- 本地 Storage 持久化购物车数据

## 项目结构

```text
.
├── components/          # 公共组件
│   ├── AppTabBar.uvue   # 底部导航（含购物车角标）
│   ├── ProductCard.uvue # 商品卡片
│   └── EmptyState.uvue  # 空状态
├── constants/           # 常量与模拟数据
│   ├── types.uts        # 类型定义
│   ├── products.uts     # 商品数据
│   ├── categories.uts   # 分类数据
│   └── tabbar.uts       # Tab 配置
├── pages/               # 页面
│   ├── home/            # 首页
│   ├── category/        # 分类
│   ├── cart/            # 购物车
│   ├── profile/         # 我的
│   └── product/         # 商品详情
├── styles/              # 样式资源
│   ├── theme.scss       # 主题变量（需同步至 uni.scss）
│   └── common.scss      # 公共样式类
├── utils/               # 工具方法
│   ├── cart.uts         # 购物车逻辑
│   └── format.uts       # 价格 / 销量格式化
├── App.uvue             # 应用入口
├── main.uts             # 主入口
├── pages.json           # 页面路由配置
├── manifest.json        # 应用配置
├── uni.scss             # 全局 SCSS 变量入口
└── AGENTS.md            # 项目开发约定
```

## 快速开始

### 环境要求

- [HBuilderX](https://www.dcloud.io/hbuilderx.html)（建议使用最新 Alpha 版，需支持 uni-app x）
- Android 模拟器 / 真机，或 Web 浏览器

### 运行项目

1. 使用 HBuilderX 打开本项目目录
2. 菜单选择 **运行 → 运行到手机或模拟器 → Android**
3. 或选择 **运行到浏览器** 进行 Web 预览

> 当前 `platformConfig.json` 默认目标平台为 `APP-ANDROID`，可按需在 HBuilderX 中切换运行平台。

## 页面路由

| 路径 | 页面 |
|------|------|
| `pages/home/home` | 首页（启动页） |
| `pages/category/category` | 分类 |
| `pages/cart/cart` | 购物车 |
| `pages/profile/profile` | 我的 |
| `pages/product/detail?id=xxx` | 商品详情 |

## 数据说明

当前版本使用 `constants/products.uts` 中的**模拟商品数据**，商品图片为网络占位图（picsum.photos）。购物车数据通过 `utils/cart.uts` 读写本地 Storage，键名为 `taobao_cart_items`。

## 主题定制

主题变量定义在 `styles/theme.scss`，由于 uni-app 会将 `uni.scss` 注入各页面样式，**修改主题时请同步更新 `uni.scss` 中的对应变量**。

主色调：

```scss
$color-primary: #ff5000;  // 淘宝橙
$color-bg: #f5f5f5;       // 页面背景
```

## 后续扩展

- [ ] 接入真实后端 API（`api/` 目录）
- [ ] 搜索页与搜索结果
- [ ] 用户登录与订单流程
- [ ] 替换 emoji 图标为 `static/` 图片资源
- [ ] 引入 Pinia 做全局状态管理

## 开发约定

项目遵循 [AGENTS.md](./AGENTS.md) 中的分层与编码规范，包括页面、组件、接口、工具方法的职责划分。

## License

MIT
