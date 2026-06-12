---
title: "Screen Flickering"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by xecure on 2008-11-27
After opening my laptop lid all the applets icons, the icons on the notification area and my main window (the window all the way on top) flickers for a minute or two. At first I didn't mind it but it gets very annoying after a while and applications become somewhat unresponsive for that minute or two. Would installing a video driver resolve this?

btw, if it of any help, i run a Dell inspiron 6400 and this is what lspci out puts: ```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

---

### Post by xecure on 2008-11-28
bump..

---

### Post by hessiess on 2008-11-28
If you are using compiz(desktop effects) try shutting that off first.

---

### Post by xecure on 2008-11-28
I am using Compiz, but I would like to continue using compiz (It was mainly why I switched over to linux). 

Any way to solve this without disabling compiz?

---

### Post by xecure on 2008-12-01
bump..

---

### Post by Cryp71c on 2008-12-01
Intel - in general - has very poor linux driver support.

My laptop uses the G965/GL960 and I experience poorer graphics performance in linux than I did in windows. Disabling compiz would be the first step  just to see if it goes away.

Also could check for restricted drivers.

---

### Post by Kellemora on 2008-12-02
Hi xecure

I don't want to sound dumb here, but may I ask what features of Compiz you like?

The reason I ask is I have Compiz on one machine and not on another machine, both of which I use all day long.

I like the way the screen flips and have changed some setting so when I close a window it does some interesting things.
But for the most part, I only show the CUBE effect to Doze users so they can ooh and aah, hi hi.........

But for doing my daily work, having Compiz turned on seems to slow things down considerably in some cases.

In any case, I was just curious is all, because perhaps I'm missing something useful!

TTUL
Gary

---

### Post by xecure on 2008-12-11
I mainly use the cube feature (cylinder actually) the wobbly windows and the application switcher (I think its called the ring switcher)

---

### Post by HavocXphere on 2008-12-11
I fixed some very weird flickering by disabling the "Detecting RANDR monitor changes". Admittedly, the circumstances were very different, but who knows. (Just remember to re-enable it if it doesn't make a difference)

The other thing I'd check is the refresh rate. Some LCD screen do crazy weird stuff if you select more Refresh Hz than the screen can handle.

---

### Post by xecure on 2009-01-12
Do i disable the "detecting RANDR monitor changes" on Compiz configuration?

---

