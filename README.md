# b85n-phoenix-hackintosh 简明教程
[GA-B85N Phoenix](https://www.gigabyte.cn/Motherboard/GA-B85N-Phoenix-rev-11) Hackintosh MacOS High Sierra 10.13.6 (17G8030)
> 由于 NVIDIA Drivers 目前最高只支持 MacOS High Sierra 10.13.6，HD4600 核显又带不动 4K，所以就没有升级 Mojave/Catalina。
* [tonymacx86.com](https://www.tonymacx86.com/)
* [黑果小兵](https://blog.daliansky.net/)


## 硬件配置参考，购买之前可以去这个网站看看 [Buyer's Guide](https://www.tonymacx86.com/buyersguide/building-a-customac-hackintosh-the-ultimate-buyers-guide/)
| 硬件 | 型号 | 参考价格 | 购买途径 | 购买日期 |
| ----- | ----- | ----- | ----- | ----- |
| 主板 | B85N PHOENIX-CF (F6) | 599 | 淘宝 | 2014-10-31 |
| CPU | i5 4590 | 1079 | 淘宝 | 2014-10-31 |
| GPU | Intel HD Graphics 4600 | 0 | CPU | 2014-10-31 |
| GPU | ASUS GTX960-MOC-2GD5 | 1449 | 京东 | 2016-04-17 |
| Audio | Realtek ALC898 | 0 | B85N | 2014-10-31 |
| 有线网卡 | Intel(R) Ethernet Connection I217-V | 0 | B85N | 2014-10-31 |
| 无线网卡+蓝牙 | 博通 BCM94352HMB | 156 | 淘宝 | 2014-11-03 |
| 无线天线 | 卡王 KW-5204 2.4G/5.8G高增益两用天线 | 39 | 京东 | 2014-11-10 | 
| 内存 | Corsair 8G 1600MHz | 479 | 淘宝 | 2014-10-31 | 
| 内存 | Corsair 8G 1600MHz | 229 | 京东 | 2016-04-17 | 
| SSD | PLEXTOR M6M 128G (PX-128M6M) | 599 | 亚马逊 | 2014-12-23 |
| SSD | 闪迪(SanDisk) 加强版 240G | 269 | 京东 | 2019-01-15 |
| 硬盘 | 东芝 2TB 7200转 64M SATA3 | 519 | 京东 | 2015-01-10 |
| 电源 | 海韵半模组 520W | 469 | 淘宝 | 2014-10-31 |
| 机箱 | 乔思伯 U2 | 299 | 淘宝 | 2014-10-31 |
| 散热 | 九州风神冰凌400 | 139 | 淘宝 | 2014-10-31 |
| 显示器 | 飞利浦 25英寸 2.5K高分 AH-IPS面板 258B6QJEB | 2149 | 京东 | 2016-04-03 |
| 显示器 | LG 27英寸 4K超高清 HDR400 sRGB99% 27UL650 | 2684 | 京东 | 2019-09-12 |
| 键盘 | 雷柏 V500 RGB幻彩背光 电竞机械键盘 茶轴 | 299 | 京东 | 2016-04-18 |
| 鼠标 | 双飞燕（A4TECH） N-810FX | 49.9 | 京东 | 2015-02-27 |

* Device: 1002 67DF Model: Radeon RX 580 (2304SP) **免驱**
* Device: 1002 6FDF Model: Radeon RX 580 (2048SP) **无法驱动**


## 硬件准备
* 1 个 16G 大小的 U 盘
* BIOS 设置
    * 快速启动 ---> 关闭
    * Windows 8/10 Features ---> Windows 8/10
    * CSM Support ---> Enable
        * 如果显卡支持纯 UEFI，这项可以关闭（我的 GTX 960 打了 DP 补丁），如果不打补丁这个选项不能关闭，不然看不到 Clover 启动界面。
        * [NVIDIA GRAPHICS FIRMWARE UPDATE TOOL FOR DISPLAYPORT 1.3 AND 1.4 DISPLAYS](https://www.nvidia.com/en-us/drivers/nv-uefi-update-x64/)
    * LAN PXE Boot Option ROM ---> Disabled
    * Legacy USB Support ---> Enabled
    * XHCI Hand-off ---> Enabled
    * SATA and RST Configuration ---> AHCI
    * Chipset --- VT-d ---> Disabled or Clover (dart=0) 


## 软件准备
* 引导工具：Clover
    * [Desktop Guide](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/config.plist-per-hardware/haswell)
    * [OS-X-Clover-Laptop-Config](https://github.com/RehabMan/OS-X-Clover-Laptop-Config)
* 必备驱动：[FakeSMC](https://bitbucket.org/RehabMan/os-x-fakesmc-kozlek/downloads/) or [VirtualSMC](https://github.com/acidanthera/VirtualSMC)

### 原版苹果官方镜像
* 找个白苹果用 App Store 下载
* 使用虚拟机安装一个黑苹果，再用 App Store 下载
* 使用大神制作的，如 [黑果小兵](https://blog.daliansky.net/)


### 制作启动优盘
* [如何创建可引导的 macOS 安装器](https://support.apple.com/zh-cn/HT201372)
* **High Sierra** `sudo /Applications/Install\ macOS\ High\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`
* 使用工具 [balenaEtcher](https://www.balena.io/etcher/)

### 安装
* 开机按 `F12` 选择 U 盘启动
* 进入 Clover 引导界面
* 选择 Boot macOS install from Install High Sierra
* 进入 macOS 使用工具页面
* 选择磁盘工具，选择你要安装系统的硬盘或分区（事先准备好，可以在 WindowsPE 下操作），点击抹掉，名称为 `High Sierra`，格式选择 `APFS`
* 关掉磁盘工具，选择刚刚抹掉的盘，安装
* 系统会重启，和第一步一样，选择 U 盘启动，进入 Clover 界面
* 这里要注意选择刚刚安装系统的硬盘，`Boot macOS Install from High Sierra`
* 等待安装，中间应该会有多次重启，依然选择 U 盘启动，再选择 `Boot macOS Install from High Sierra`
* 大功告成！！！


## 安装后的配置
### [Clover](https://sourceforge.net/projects/cloverefiboot/) 安装、配置、驱动
macOS 安装成功，下载 Clover 安装到硬盘 EFI/ESP 分区，BIOS 添加 Clover 启动项需要借助小工具 bootice，这个工具需要系统在 UEFI 下启动的（Windows 10 or Windows 10 PE)
* 必备：VirtualSMC.kext + (SMCLightSensor.kext, SMCProcessor.kext, SMCSuperIO.kext) [VirtualSMC](https://github.com/acidanthera/VirtualSMC)
* 必备驱动框架：Lilu.kext [Lilu](https://github.com/acidanthera/Lilu)
* 显卡：WhateverGreen.kext [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
* 声卡：AppleALC.kext [AppleALC](https://github.com/acidanthera/AppleALC)
* 有线网卡：IntelMausiEthernet.kext [OS-X-intel-network](https://bitbucket.org/RehabMan/os-x-intel-network/downloads/)
* 无线网卡：AirportBrcmFixup.kext [AirportBrcmFixup](https://github.com/acidanthera/AirportBrcmFixup)
* 蓝牙：BrcmFirmwareData.kext + BrcmPatchRAM2.kext [OS-X-BrcmPatchRAM](https://bitbucket.org/RehabMan/os-x-brcmpatchram/downloads/)
* CPU 变频：CPUFriend.kext + CPUFriendDataProvider.kext [CPUFriend](https://github.com/acidanthera/CPUFriend)
    * `ioreg -lw0 | grep -i "board-id" | sed -e '/[^<]*</s///; s/\"//g; s/\>//'`
    * `cp /System/Library/Extensions/IOPlatformPluginFamily.kext/Contents/PlugIns/X86PlatformPlugin.kext/Contents/Resources/Mac-27ADBB7B4CEE8E61.plist .`
    * [ResourceConverter.sh](https://github.com/acidanthera/CPUFriend/raw/master/Tools/ResourceConverter.sh) -k Mac-27ADBB7B4CEE8E61.plist
* USB：USBPorts.kext
    > 使用 Hackintool 定制
* HD4600: Clover - Devices, PciRoot(0x0)/Pci(0x2,0x0)
    * AAPL,ig-platform-id    0300220D    DATA
    * AAPL,slot-name    Built-In    String

### 开启原生电源管理
Clover - acpi - Fixes(AddDTGP, FakeLPC) 

### 开启 HiDPI


###  Hackintosh 禁用休眠
```bash
sudo pmset -a hibernatemode 0
sudo rm /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```

### 重装缓存
```bash
sudo kextcache -i /
```


## 高级进阶
### DSDT & SSDT


