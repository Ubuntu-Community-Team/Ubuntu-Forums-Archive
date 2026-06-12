---
title: "Given these specs, is there a way to tweak them so battery doesn't run out so fast?"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by KayeNg on 2013-01-01
Hi guys. I'm on Lubuntu 12.10 .

Some specs on my Samsung laptop:

Processor: Intel Core i3 , M 380 @ 2.53GHz  2.53 GHz

RAM: 2.00 GB

System type:  64-bit Operating System

Video Adapter:  ATI Mobility Radeon HD 5470

Monitor:  Generic PnP Monitor [NoDB]

Audio Adapter:	High Definition Audio Controller [NoDB]

IDE Controller:	Intel(R) 5 Series 4 Port SATA AHCI Controller

Disk Drive:	TOSHIBA MK5065GSX  (465 GB, IDE)

Optical Drive:	Slimtype DVD A DS8A5SH

Network Adapter:	Broadcom 802.11n Network Adapter

Network Adapter:	HUAWEI Mobile Connect - 3G Network Card  (10.140.102.161)

Network Adapter:	Marvell Yukon 88E8040 Family PCI-E Fast Ethernet Controller

Battery	Microsoft ACPI-Compliant Control Method Battery

Video Adapter Properties
Chip Type:	ATI display adapter (0x68E0)
DAC Type:	Internal DAC(400MHz)

The laptop also has "Realtek High Definition Audio Speakers" according to SRS Premium Sound, located on the task bar when I'm running Windows.

Are there ways to tweak these so I can get better battery life while using Lubuntu? Or do I just have to wait for Ubuntu to come up with something? I haven't really timed it, but it feels like I only get half the time in Lubuntu than I do in Windows. Like if I get two hours on Windows, it'll be like 45 to 60 minutes only in Lubuntu. 

By the way, I think there's a driver for ATI Mobility Radeon HD 5470 specifically for Linux x86, should I install it in my Lubuntu partition?

Thank you guys!

---

### Post by Paqman on 2013-01-01
I'd definitely advise installing [Jupiter applet]("http://jupiter.sourceforge.net/downloads.html"), it should eke out a bit more battery life. Apart from that just the usual stuff like not having your backlight up any brighter than you need and turning off anything like Bluetooth that your aren't using.

---

### Post by mamamia88 on 2013-01-01
like he said the less stuff running eating battery the better your battery will be.    personally i wouldn't worry about it too much and just buy an extra battery for the rare case you need it

---

### Post by AstroLlama on 2013-01-01
> **mamamia88 said:**
> like he said the less stuff running eating battery the better your battery will be.    personally i wouldn't worry about it too much and just buy an extra battery for the rare case you need it

+1 

extra battery is the most practical answer. 

Aside from that, keep a low brightness and install the cpu frequency scaling applet. Slower speed with help a little bit with battery life. Few programs open will also help, as will disabling the wifi antenna.

Doing all this, however, will make you less productive!

---

### Post by mysteriousdarren on 2013-01-07
There are a few things that can be done hardware wise: adding a larger battery, undervolting the computer, turning down the back-light, and allowing spin downs on the hard drive.

I would install the boot-up manager, and stop all but essential programs and processes. Check out your task manager when nothing is running, and check and remove more unessential processes. Be warned do not remove too much, otherwise it could cause kernel panic.

I installed bleachbit and removed GBs of unneeded programs and old kernels. 

Use smaller versions of programs such as using Abiword in place of Libreoffice. This would only be if you do not need all the extras. Remove all extra programs via synaptic or lubuntu package manager. I myself did all of these thing except undervolting and increased my battery life tremendously on my netbook. 

I installed Jupiter and Xfce4 power manager. Depending on the specific computer Jupiter maybe enough or both may help.

Good luck in whatever path you choose. Give updates as well.

---

### Post by Impavidus on 2013-01-07
Sub optimal video drivers can cause your graphics card to run full speed all the time, consuming a lot of energy. If other drivers are available you should definitely give it a try. Dimming the screen and disabling all wireless stuff can save a lot, other techniques may save a bit more, but not very impressive.

And something I found out by precisely monitoring my laptop's power consumption: the cooling fans actually draw significant power. Disabling cooling will destroy your hardware, but sitting in a cold room/in the park in winter helps.
:lolflag:

---

### Post by fyfe54 on 2013-01-07
Check this out too.  While surfing around,  I'm down to between 8 and 11 watts on a Dell Inspiron 1545.  Naturally, heavier usage uses more power and empties the battery faster,  but Powertop has made a big difference in my battery life.

[http://www.webupd8.org/2012/08/install-powertop-21-in-ubuntu-1204.html](http://www.webupd8.org/2012/08/install-powertop-21-in-ubuntu-1204.html)

---

