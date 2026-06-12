---
title: "openGL problem!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by sabti on 2008-05-29
I'm trying to run catia v5R18 under wine and when i do it gives me the error " no certified opengl library found check installation" what do i do? i have an ati card and the output of lspci is:

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


thanks for the help in advance~!

---

### Post by iaculallad on 2008-05-29
Try appending **--enable-opengl** on your command.

---

### Post by sabti on 2008-05-29
this is my command now

env WINEPREFIX="/home/sabti/.wine" wine "C:\Program Files\Dassault Systemes\B18\intel_a\code\bin\catstart.exe"  -run "CNEXT.exe" -env CATIA.V5R18.B18 -direnv "C:\windows\profiles\All Users\Application Data\DassaultSystemes\CATEnv" -nowindow -enable-opengl


and still a problem!

---

### Post by iaculallad on 2008-05-29
Try looking at WineHQ Bugzilla's - [Bug 10490]("http://bugs.winehq.org/show_bug.cgi?id=10490"). I don't know if this applies with your v5R18.

---

### Post by sabti on 2008-05-29
i went to the link you provided above and still no help... what is it thats making it not work!
i really need it i have an assignment due tomorw!!! i don't want to install windowss... nooooooooooooooooooooooo

---

### Post by iaculallad on 2008-05-29
> **sabti said:**
> i went to the link you provided above and still no help... what is it thats making it not work!
i really need it i have an assignment due tomorw!!! i don't want to install windowss... nooooooooooooooooooooooo

After doing some research (Engineering Forum), and for you not wanting to install windoze, you still have some options. You can try using one of the following:

*Windoze
Solaris
AIX
IRIX
HP-UX

w/c, according to them could execute Catia.

---

### Post by xenocide13 on 2008-05-29
Are you sure that all of your drivers are up to date?
what version of ubuntu are you running?

---

### Post by sabti on 2008-05-29
i'm running ubuntu 8.04

---

### Post by sabti on 2008-06-01
bump i need help still!! i don't want to install another system

---

