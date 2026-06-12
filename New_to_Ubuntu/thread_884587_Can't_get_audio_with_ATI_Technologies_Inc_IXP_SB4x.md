---
title: "Can't get audio with ATI Technologies Inc IXP SB4x0 High Definition Audio Controller"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by anarchybomb88 on 2008-08-09
Hey everyone,

So I have just made the jump over to Ubuntu and am liking it thus far apart from a few issues. I first couldn't get on the internet, but thanks to some great posts on these forums i figured that one out. 

However my sound isn't working yet, and I can't seem to fix this problem. I have included the output of lspci below, any help would be greatly appreciated.

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Thanks in advance,

---

### Post by ruisu on 2008-08-14
thats odd, i have almost the same hardware, but the generic kernel does the job (although i dont know what things is selected because im making miself a custom kernel and audio its not available):

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by martinwguy on 2009-09-27
Hi! I had the same thing until I tried fiddling with alsamixer in a terminal window - when I unmuted the "Surround" column ("m") and turned it up (up-arrow) thesound came out ok.
Dunno what they've done in this laptop - connected the main speakers to the surround sound output???  ANyway, give it a try and let us know

    M

---

