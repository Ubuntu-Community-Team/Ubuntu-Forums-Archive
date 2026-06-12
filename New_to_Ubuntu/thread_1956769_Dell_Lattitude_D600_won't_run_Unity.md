---
title: "Dell Lattitude D600 won't run Unity"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by gmgj on 2012-04-11
my dell latitude d600 video is not capable of running unity.  I have been searching for an option to update the laptop with a pcmia card or usb device that would replace/ augment / whatever the video so that I could easily update with no luck.  Before I give up, I thought I would ask here.  BTW, my luck with opening up laptops is not so good.  I can put in memory and other easy stuff, but anything more advanced is probably out of the question:confused:   
Currently running 11.04 NN, with gnome.

---

### Post by idoitprone on 2012-04-11
> **gmgj said:**
> my dell latitude d600 video is not capable of running unity.  I have been searching for an option to update the laptop with a pcmia card or usb device that would replace/ augment / whatever the video so that I could easily update with no luck.  Before I give up, I thought I would ask here.  BTW, my luck with opening up laptops is not so good.  I can put in memory and other easy stuff, but anything more advanced is probably out of the question:confused:   
Currently running 11.04 NN, with gnome.

dell latitude d600 is a little old for unity 3d?

Unity 2d should be fine

do you have a graphic card?

```
lspci
```

---

### Post by gmgj on 2012-04-12
My memory is foggy, but my best recollection is that when I first installed the first version with unity, I had to go through around 5 or six iterations to get any kind of desktop.  I would like to upgrade, if I don't have to spend a day trying to get a working desktop back.


ubugj@ubugj-D600:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

BTW, bunny is my new electronic signature; do as 
the Bunny says, or else.

---

### Post by idoitprone on 2012-04-12
> **gmgj said:**
> My memory is foggy, but my best recollection is that when I first installed the first version with unity, I had to go through around 5 or six iterations to get any kind of desktop.  I would like to upgrade, if I don't have to spend a day trying to get a working desktop back.


ubugj@ubugj-D600:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)



i believe your card is little slow, so i might say get a lighter desktop

btw, that is not convincing 
> BTW, bunny is my new electronic signature; do as 
the Bunny says, or else

this is
[http://www.youtube.com/watch?v=pmu5sRIizdw](http://www.youtube.com/watch?v=pmu5sRIizdw)

---

### Post by cortman on 2012-04-12
If you're wanting to change/upgrade your operating system, I would recommend [Lubuntu]("http://lubuntu.net/") for your old machine- Lubuntu is a very lightweight Ubuntu based distro, and runs beautifully fast on low-spec or older machines.

---

### Post by SuperMau on 2012-11-08
I had the same problem and gave up on Unity. I am running Linux Mint Maya (Ubuntu 12.04) based with Mate and Compiz with desktop effects and it runs wonderful in my D600... I am very happy with its performance and it is a LTS!!!

---

