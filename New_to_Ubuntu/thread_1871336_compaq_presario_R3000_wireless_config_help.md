---
title: "compaq presario R3000 wireless config help"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2011-10-28
ok. so i have a compaq presario r300 computer. it has 512 megabytes of ram and i havent modified it at all. i want to know how to configure wireless settings, but i just dont know how. i enabled the additional drivers thing but it says i need a "kernel driver". i have absoululty no idea what that is. nor do i know how to get one. so can someone please help me get my wireless working?

---

### Post by wolfen69 on 2011-10-28
Open a terminal and do
```
lspci
```
copy and paste the output here.

---

### Post by ilikelinuxitisthebest on 2011-10-30
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

---

