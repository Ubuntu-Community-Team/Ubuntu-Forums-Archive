---
title: "Problem booting: &quot;starting k display manager&quot; fail"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by rachellcb on 2013-03-29
I'm using Kubuntu 12.04, installed recently from usb.
Kubuntu crashed when I was using firefox and when I try to boot it gets stuck and on the boot log it says "starting k display manager" "ok" and then two lines down says "starting k display manager" "fail". This is the only line with a "fail" so that's my starting point to try and get the desktop back.
I did ctr + alt + F1 which prompted me to log in and got me to a command line but now I don't know what to do. I'm new at this, thanks for your help!! :(

---

### Post by kc1di on 2013-03-29
Hello rachellcb  and welcome to Linux and Ubuntu/Kubuntu.

Can you give us a little more information on your machine.  that might help. What make , model and especially what video card are you using?

This often is a video driver problem and can be fixed by installing the correct driver for your card.  if you do don't know the video card and you 
can get to a terminal type the following command and post the read out here.

```
lspci
```

---

### Post by rachellcb on 2013-03-30
Hi kc1di, I am using a DELL Latitude D340 laptop. I don't know about the video card so I typed in [COLOR=#b22222]lspci[/COLOR] and a whole bunch of stuff came up including:

00:00.0 Host Bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Mempry Controller Hub (rev 03)
00:02.0  VGA compatible controller: Intel Corporation Mobile 945GM/GMS,  943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio Device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7-Family) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:01.0 CardBus Bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C822 IEEE 1394 Controller (rev 09)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Hope that's the right information. Thank you!

---

