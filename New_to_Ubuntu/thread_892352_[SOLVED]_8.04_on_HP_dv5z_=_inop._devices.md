---
title: "[SOLVED] 8.04 on HP dv5z = inop. devices"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Sava8420 on 2008-08-17
So where to start?  I suppose a list of my hardware would be the first step.
HP dv5z 
-AMD Turion X2 ZM-80 2.1ghz
-ATI Radeon Mobility HD 3450 256mb
-Hitachi 250GB 5400rpm SATA
-3GB DDR2 System Memory
-Wireless LAN 802.11a/b/g/n and Bluetooth
-15.4" WSXGA+ (1680x1050)
-Imprint Finish + Mic. + Webcam + Fingerprint Reader

So I pretty painlessly shrunk the vista partion and got dual-booted with 8.04 64bit was pretty simple all good.  I have all repos on DVD 2 mains and 4 multi/uni. Added them to synaptics and figured I'd get Compiz up and running well nope that is not gonna happen cause the restricted driver ATI FireGL is enabled but not in use?  Tried manual remove and install but nothing changed, tried using ATI's driver package with no luck.  

So figured try to get Bluetooth to work umm nope.  Maybe wireless ummm nope.  Fingerprint reader haven't even tried cause no point.  Used my cell for internet but with WVDial says my USB port is a low power usb port so it can't recognize my modem? (Vista has no problems)  

What really sucks is I love my 7.10 on my desktop and talk about a difference in ease of configuration between 7.10 and 8.04!  You can't even view hardware info with out installing something.
Now I'm sure if my terminal skills were at a level I'd call functional I wouldn't have near the problems I am,  so I'm not trying to sound like I'm here to complain as I am aware that it is my own ignorance that is the real problem.  Oh yeah, worst thing of all when I shut down my system or restart with Ubuntu it acts like a surge of power goes through my system and the speakers scratch and screen flash/glitches, I'm really not liking that one at all.  I guess if there is any advice out there let it be known.  If your advice consists of criticism save your breath cause I am aware of my own faults.

---

### Post by 3rdalbum on 2008-08-17
You need to tell us what wireless chipset you have, and the make of your Bluetooth chipset. Hopefully your computer's manual should tell you; alternatively, the output of the commands "lspci" and "lsusb" could be enough to tell us.

---

### Post by Sava8420 on 2008-08-17
Bluetooth dev. is Broadcom or HP Integrated Module with Bluetooth 2.0
Wireless is Atheros AR5009 802.11a/g/n WiFi Adapter

---

### Post by stijngysemans on 2008-08-17
the wireless adapter, it this working using the live cd?

---

### Post by Sava8420 on 2008-08-17
> **stijngysemans said:**
> the wireless adapter, it this working using the live cd?
No sir it is not working with the live cd.

---

### Post by Sava8420 on 2008-08-19
Let's just call this one "SOLVED" as I must have answered my own question.  No the hardware does not work yet but ohh well I'll figure it out myself. ](*,)

---

### Post by gt1fan on 2008-08-19
I have the same computer with the Atheros 242x Wireless Chip and I have not been able to get it working....any help would be appreciated.  Really want to not use Vista.

---

### Post by Sava8420 on 2008-08-20
> **gt1fan said:**
> I have the same computer with the Atheros 242x Wireless Chip and I have not been able to get it working....any help would be appreciated.  Really want to not use Vista.

So see if this helps you out I think it just might: ubuntuforums.org/showthread.php?t=816780&highlight=atheros+amd64

---

### Post by highlandsun on 2008-08-22
For the AR5009 you need the ath9k driver, and you're going to have to compile it yourself because it's still very new. I have it working fine on my dv5z; I also compiled 2.6.26.3 for myself. I may write this up in the Laptop forum...

---

