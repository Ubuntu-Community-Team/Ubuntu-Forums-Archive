---
title: "How can I get a USB wireless dongle to work with Ubuntu?"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by Nevan_Blaisdell on 2013-09-03
I have the latest version of Ubuntu on my Gateway FX desktop and I've been using it with the ethernet so far and it's been working fine. However, I'd like to try and move the computer to a place where I don't have access to the ethernet cable, so I tried to use my Netgear USB wireless dongle that I use to run Windows 8 on the same desktop.


Unfortunately, Ubuntu would not recognize this device and I couldn't figure out how to get it to work with the OS, if it is even possible. Could anyone offer any help?

---

### Post by eternal243 on 2013-09-03
I'm assuming you are missing the drivers for it, try connecting it to your PC and open a terminal, then use the command **"lsusb"** and post back the result.
It would help us determine if your dongle is recognized by the system or if it is just an "unidentified" device.

---

### Post by cmcanulty on 2013-09-03
also  just go to system settings-additional drivers or go to system settings-network and be sure airplane mode is off

---

### Post by Nevan_Blaisdell on 2013-09-03
Hmm, looks like it is being recognized:

This was one of the lines when I entered "lsusb":

Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

That's it, of course. But even so, the computer isn't doing anything with it.

---

### Post by khelben1979 on 2013-09-03
To be more precise, it means that your Ubuntu Linux kernel recognizes the hardware but having a suitable driver for it is a different story, it seems. When they at Ubuntu decided to configure up and then package the Linux kernel they decided for you if the driver is going to get loaded by module (which means it autoloads when ever needed on newer Linux systems) or if it is compiled inside the Linux kernel (gets loaded during bootup and are available all the time as long as it is plugged in and working). It is possible to download the driver if it is Linux supported Netgear hardware in this case. You can go to their official website to see if it is supported there, then just download the driver and look for README fie or specific instructions on their webpage to get it working.

I have no experience with that specific hardware, but from my experience, often a bit older hardware which has been around for a while is often better supported on a Linux system then just brand new, which also are only supported on Windows and/or MacOS systems.

---

### Post by chili555 on 2013-09-04
Please see: [https://www.google.com/search?q=WNDA3100v2+chili555+site:ubuntuforums.org&safe=off&client=ubuntu&hs=K9D&channel=fs&biw=1013&bih=566](https://www.google.com/search?q=WNDA3100v2+chili555+site:ubuntuforums.org&safe=off&client=ubuntu&hs=K9D&channel=fs&biw=1013&bih=566)

Especially see here: [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)

It isn't easy.

---

### Post by Nevan_Blaisdell on 2013-09-04
Yeesh. Well, thanks anyway, guys. Driver issues seem to be my biggest problem with running Ubuntu, but I will just stick with the Ethernet cable for now until I can figure something else out. I remember once having a PCI wireless card that worked with Ubuntu without me having to search for drivers, but I can't seem to find it anywhere...

---

### Post by kurt18947 on 2013-09-04
> **Nevan_Blaisdell said:**
> Yeesh. Well, thanks anyway, guys. Driver issues seem to be my biggest problem with running Ubuntu, but I will just stick with the Ethernet cable for now until I can figure something else out. I remember once having a PCI wireless card that worked with Ubuntu without me having to search for drivers, but I can't seem to find it anywhere...

From what I've read - I don't have one - if you searched for the most difficult wifi device to get to work with Ubuntu, your Netgear would certainly be a finalist.  If you want an N300+ dual frequency adapter, I don't have a suggestion.  If you're happy with a bit less, I'd suggest an adapter using the RTL-8192SU chipset - TrendNet TEW-649UB is one.  I've seen it advertized as 300 mb./sec. down, 150 mb./sec. up.  I find the Netgear WNA1100 is also plug 'n' play though I'm pretty sure it's limited to 150 mb./sec.  

A potential gotcha with recommending adapters that work out of the box with linux is that manufacturers sometimes change chipsets in a model and just give it a different version designator.  Model X ver. 1 may work great with Linux, Model X ver. 2 may be a real problem. The version designator  is generally not on the box.  D-Link seems to be good at this.

---

