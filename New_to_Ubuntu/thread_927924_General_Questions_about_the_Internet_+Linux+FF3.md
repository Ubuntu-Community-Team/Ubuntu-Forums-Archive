---
title: "General Questions about the Internet +Linux+FF3"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by spiritsongtress on 2008-09-23
I can't tell if the webpages I go to sometimes are misaligned for Linux or Fire fox 3? (Sometimes things  overlap)

I've also not been able to change the screen resolution for my screen I have no idea what its at currently.

I am running 8.04 Ubuntu.

---

### Post by Titan8990 on 2008-09-23
It sounds like you having issue with your graphics drivers. Post the output of the following command:


lspci

---

### Post by spiritsongtress on 2008-09-23
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Also I'd like to know if anyone knows a good webcam that's linux compatible?

---

### Post by Tatty on 2008-09-23
To find out your current screen resolution and to change it go to "System->Preferences->Screen Resolution"

---

### Post by RequinB4 on 2008-09-23
See if there is anything in system - admin - hardware drivers, may need to check something.

On the long shot this is an internet problem and the resolution is seperate, are you on wireless and how did you get your broadcom working?

---

### Post by Zieg30CT on 2008-09-23
My Gateway Integrated Webcam on my laptop works pretty well. I just had to install the drivers via EasyCam2 and install a program called Cheese in order to start using it.

I'm not to sure about any other webcams though.

---

### Post by spiritsongtress on 2008-09-24
When I do that I get: 
 " The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

---

