---
title: "help with wireless connection"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by huntis619 on 2008-05-04
Hi I recently upgraded to ubuntu 8.04 and now my wireless connection wont work. I have a hpzv5410us laptop. Please can anyone help me.

---

### Post by zaussome on 2008-05-04
z

---

### Post by huntis619 on 2008-05-04
Its an amd64 3200

---

### Post by sam_delta on 2008-05-04
i bet its a broadcom

confirm this by posting the output of 
```
lspci
```

sam

---

### Post by huntis619 on 2008-05-04
lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
steven@steven-laptop:~$

---

### Post by sam_delta on 2008-05-04
yeap, thats a broadcom BCM4306,

reinstalling b43 drivers might work
re-install b43-fwcutter drivers and see if it works

to do this, type the following into a terminal:

NOTE: you need internet connection to do this, so make sure you have your wired connection pugged in.

```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

NOTE: if it ask you to fetch a firmware, make sure you answer with "Y" for yes.

restart your pc, and check if it works, if not, go into system>administrator>hardware drivers, and enable broadcom drivers,

tell us how it goes
sam

---

### Post by huntis619 on 2008-05-04
Well the commands in the terminal didn't work. I had to go into system >administration >hardware drivers. I restarted computer but the wireless still isn't working. Could this be because I upgraded from 7.10 instead of a fresh install.

---

### Post by sam_delta on 2008-05-04
honeslty , i dont know if the upgrade could have mess something.

try
install ndiswrapper by carefully following the guide posted here:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

if you get stuck in any step, post here, and we'll help

tell us how it goes,
 sam

---

### Post by subzero316 on 2008-05-04
Try flicking the WIFI switch and see ...

---

