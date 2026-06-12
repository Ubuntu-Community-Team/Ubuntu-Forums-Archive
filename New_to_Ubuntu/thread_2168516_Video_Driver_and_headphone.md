---
title: "Video Driver and headphone"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by SupermanNC21 on 2013-08-18
Need help installing right video driver i did lspci and heres driver info and also how do i keep sound from play throw my speaker when i have headphone plugged in. I installed alsa sound driver if u need info about that 

superman@supermanNC21-Ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P AGP Bridge (rev 02)
00:03.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350/M10 [Mobility Radeon 9600 PRO Turbo]
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
03:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by SupermanNC21 on 2013-08-20
bump....

---

### Post by Mark Phelps on 2013-08-21
From that output, it appears you have one of the OLD (very old, in fact) ATI 9xxx series video chipsets.  AMD (who bought out ATI) dropped restriced Linux driver support for those cards YEARS ago.  To install the restricted AMD driver, you would probably have to go back to Ubuntu 9.x.

Today, the only drivers that work (and maybe not well, at that) are the default Radeon drivers that are automatically installed during initial setup.

If you download other drivers and try to install them, that will only trash your display -- and then, you would have a LOT of work ahead of you to remove those -- and end up back with the same drivers you have now.

---

