---
title: "screen stay black after suspending"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by guldberg72 on 2013-10-06
hello. when i close my lid my computer is going to suspend (sleep) but when i will open the lid again, can i hear my pc is working but the screen stay black ?


in ubuntu 13.04 there was no problem but after i updated to 13.10 it started. btw. i am using gnome 3.10

---

### Post by whitesmith on 2013-10-06
Hi **guldberg72** and welcome to the forum. Did the problem begin after you updated, either to Ubuntu 13.10 or Gnome 3.1? Please post as much information as you can about your computer. The more we know the more accurate our suggestions will be. In the meantime, try this on the black screen: hit ctrl+alt+F2. Then login and enter ```
startx
``` Let us know what that does.

---

### Post by guldberg72 on 2013-10-07
thx for the reply. i will try to use the startx next time it happends


> 00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
daniel@daniel-K53BR:~$ 




---

### Post by guldberg72 on 2013-10-07
i just tried to use alt-f2 but nothing happends :S but the screen isnt jsut black there is no power.

---

### Post by guldberg72 on 2013-10-08
Nope.. ctrl-alt-f2 defintley dosnt work.

---

