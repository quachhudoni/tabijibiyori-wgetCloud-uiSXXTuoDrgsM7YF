# iOS 有线投屏开源了：Windows 直连采集 iPhone 屏幕与音频的完整方案

项目地址：
[https://github.com/chotgpt/quicktime\_video\_hack\_windows](https://github.com)

---

## 一、前言

过去在 Windows 上想要录制或展示 iPhone 屏幕，几乎只能依靠 AirPlay 或无线方案，这不仅存在延迟高、画质压缩严重的问题，还容易受到网络环境影响。
现在，这个问题有了开源解决方案——quicktime\_video\_hack\_windows 项目正式发布。
它可以让 Windows 电脑直接通过数据线采集 iOS 设备的视频和音频流，真正实现低延迟的有线投屏。

这意味着，你可以：

* 实现有线低延迟投屏
* 将 iPhone 画面推流到 OBS、VLC、直播软件
* 用于 QA 自动化测试、应用演示、录屏分析等场景

---

## 二、项目简介

quicktime\_video\_hack\_windows 是一个基于 QuickTime 协议逆向实现的 C++ 版 iOS 视频捕获工具。
项目参考了 Daniel Paulus 的 quicktime\_video\_hack（Go 语言实现），并针对 Windows 环境重写了 USB 通信与协议解析逻辑。

仓库提供：

* 命令行工具（用于快速验证）
* Qt 图形界面程序（可实时预览）
* 完整源码，便于二次开发和自定义集成
  ![image]()

---

## 三、主要功能

* 通过 Lightning / Type-C 数据线获取 iOS 屏幕内容
* 支持音视频双流采集
* 提供回调接口，可直接整合进你的项目
* 支持多设备同时采集
* 带 Qt 界面，可实时预览画面
* 开源协议为 MIT，可自由修改和分发

---

## 四、快速上手

以下步骤 5 分钟即可上手测试：

1. 克隆仓库
   git clone [https://github.com/chotgpt/quicktime\_video\_hack\_windows.git](https://github.com)
2. 安装驱动

   * 安装 libusb 驱动；
   * 注意：会与 Apple 官方驱动冲突，需要卸载 Apple Mobile Device Support；
   * 连接 iPhone 后，首次需在手机上点击 “信任此电脑”。
3. 启动 USB 服务
   tool\usbmuxd.exe
   该服务会监听 37015 端口，检测到设备后自动启用 QuickTime 模式。
4. 运行示例程序

   * 命令行版：release\test\_x64Debug.exe
   * Qt 界面版：release\qt\_ios\_line\_cast\_screen.exe
5. 开始投屏
   如果一切正常，窗口会出现 iPhone 实时画面，延迟非常低。

---

## 五、效果展示

Qt 示例版支持直接显示来自 iOS 的实时视频流。

(示例截图链接：[https://i.hd-r.cn/bdf8336f-a24c-4f30-bddf-89287f76e3db.jpg](https://github.com):[CMESPEED-楚门加速器](https://cmnspeed.com))

---

## 六、应用场景与扩展方向

quicktime\_video\_hack\_windows 不仅是投屏工具，更是一套完整的 iOS 音视频采集底层方案。

你可以：

* 集成到 OBS / FFmpeg 实现有线直播采集；
* 应用于自动化 UI 测试、性能录制；
* 构建自定义录制器、屏幕同步系统；
* 在企业 QA 环境中实现多机并行录制，效率极高。

如果你熟悉多媒体开发，还可以进一步扩展：

* 增加 H.264 / AAC 硬件解码；
* 接入 WebRTC、RTMP、或本地播放器；
* 改写成 Unity、Qt、C# 插件使用；
* 做成本地控制台或后台录屏服务。

---

## 七、开源协议与致谢

* 开源协议：MIT
* 原始参考项目：danielpaulus/quicktime\_video\_hack
* C++ 实现与 Windows 适配：chotgpt/quicktime\_video\_hack\_windows

感谢原作者对 QuickTime 协议的研究，为 Windows 平台提供了可靠的有线采集方案。

---

## 八、总结

这款工具让 iOS 有线投屏在 Windows 上成为现实。
不再依赖 Wi-Fi、不再卡顿，稳定、低延迟、开源自由。

如果你正在寻找一款能让 iPhone “插上线就能显示”的解决方案，
那它几乎是当前最轻量、最灵活的选择之一。

项目主页：
[https://github.com/chotgpt/quicktime\_video\_hack\_windows](https://github.com)
