---
title: "Hardy Heron Crashes, Caps Lock lights flash, Using A Broadcom Wireless Car"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by lnajt on 2008-10-11
Hello,

I recently set up Ubuntu on my Dell Latitude D830 Laptop and, after wrestling with the wireless drivers for a while, I finally got everything up and running.

However, the success I achieved was doomed to be cut short - my computer now crashes randomly and when it does these things happen:

1. Everything locks up (The screen image remains the same though)
2. The Caps Lock and Scroll Lock buttons flash on and off at regular intervals
3. I am forced to hard reboot my computer.

I looked around on the forums here for a while, and I discovered that in many cases (that is, all of the ones I saw) this had to do with a wireless card from RaLink. My Wireless card is not from RaLink. It is from Broadcom, and here is the output of lspci | grep Network:

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I have installed the drivers for this device using Ndiswrapper.

Does anyone know how to overcome this particular problem?

Thanks

---

### Post by Sava8420 on 2008-10-12
Ok by any chance are you using a bluetooth mouse or keyboard?  The reason I ask is that I have a new HP dv5z and I use a bluetooth Microsoft mouse with Vista now since I haven't taken the time to configure the mouse if I have it turned on and try to use it it will cause the same problem.  I haven't attempted to look for reason since I haven't taken the time to properly configure device.  I would bet though that other bluetooth devices could cause the same problem.  If you don't have bluetooth ability in your laptop then obviously this is not the case, if you do try turning off all bluetooth devices around you and see what happens.

---

### Post by lnajt on 2008-10-15
I do use a bluetooth mouse, but my computer crashed even when the mouse was not plugged in.

Anyway, it hasn't happened for a few days so I'm guessing an update or something cleared it up.

Thanks anyway

---

### Post by lnajt on 2008-10-19
Update: Experimental evidence shows that it only crashes when I'm undocked.

---

### Post by rRNA on 2008-10-19
I also got the same thing on my dell inspiron 1420 with a broadcom 4311 chipset using the new STA drivers. I never had this problem with the older b43 so I will probably go back to that. After a bit of googling I also learned that the flashing caps lock meant a kernel panic? I'm not really sure what this means.

---

### Post by Suminus on 2008-10-20
I got the same problem. Every now and then my Hardy crashes with the efects mentioned here. In another forum I read that maybe a USB-Keyboard or USB-Mouse could cause the problem. I use a USB-Mouse. Bluetooth is deactivated in my system.

If my system crashs, it happens booting, logging in or directly after the login.

Anyone got a clue?

My System:
Ubuntu 8.04.1 
GNOME 2.22.3 (Ubuntu 2008-07-09)
Linux 2.6.24-21-generic
AMD Athlon(tm) XP 2800+
2026 MB DDR2-Ram
WLAN-Card is installed in my computer, but not in Ubuntu (I'm using cable)

Edit: See also this Thread: [http://ubuntuforums.org/showthread.php?t=832383&page=16]("http://ubuntuforums.org/showthread.php?t=832383&page=16")

---

### Post by tbar3 on 2008-11-15
same problem with my HP DV2715nr. It usually happens for me when it attempts to come out of suspend, although, tonight, i did have it crash when it was attempting to connect to my home wireless network, which leads me to believe it is the wireless driver messing it up...

at any rate, i'm still looking for a driver update or anything that will solve the issue... any other luck?

Thanks,
TBare

---

### Post by Elktro on 2008-11-26
Same thing with my Compal FL91 and Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express. Thought I only come across these crashes randomly usually after suspend. I'm not using any blue-tooth devices, but as I power up my wireless car with the switch on the front, it will power up my bluetooth device as well.

Does anyknow know what the flasing caps and scroll lock meanm?

---

### Post by Elktro on 2008-12-03
> **Elktro said:**
> 
Does anyknow know what the flasing caps and scroll lock meanm?

Okey so it seems that it is kernel panic. :(

Is there any a fix for this ones? Why would there be a kernel panic when network card is switched on?

---

### Post by Kellemora on 2008-12-03
Hi Gang

I may be wrong, but I think this latest Kernel upgrade has a few major flaws in it.
I have NOT had any issues at all with the caps key light until this most recent kernel upgrade.  Now the light don't work at all, or if something is amiss it will start flashing and I know a crash is forthcoming in a few seconds.

Rather than the light turning on, my boot screen now shows if the caps lock is on with red banner saying "you're caps lock is on"
never had that before either.

A lot of things keep crashing now since the newest kernel upgrade.  So I rolled back to the last one and most of the problems go away.  So that's what I'm back to using until the next one comes out.

TTUL
Gary

---

### Post by bumble bee man on 2008-12-13
Had same problem in 8.04...
Fresh install 8.10, no solution

Dell Inspiron 1720
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

~$ modinfo rt61pci
filename: /lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license: GPL
firmware: rt2661.bin
firmware: rt2561s.bin
firmware: rt2561.bin
description: Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version: 2.1.8
author: [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion: 8F4EE2C062AC0B948F1F3AD
alias: pci:v00001814d00000401sv*sd*bc*sc*i*
alias: pci:v00001814d00000302sv*sd*bc*sc*i*
alias: pci:v00001814d00000301sv*sd*bc*sc*i*
depends: rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
vermagic: 2.6.27-9-generic SMP mod_unload modversions 586

---

### Post by jarviw on 2008-12-17
The Broadcom STA wl driver is buggy... see bug report here:
[https://bugs.launchpad.net/bugs/292450](https://bugs.launchpad.net/bugs/292450)

It causes random kernel panic -- I am not exactly sure about the mechanism, but it has been plaguing us for a while.

They just released the bug fix into the hardy-proposed repository with linux-restricted-modules-2.6.24_2.6.24.15-23.55

According to the launchpad tracking, it doesn't seem to be ported to Intrepid as yet. But you might want to keep your proposed repository open for update.

Hope this helps.

---

### Post by h'bel h'balim on 2008-12-21
Folks,

I get the same problem with a different hardware configuration ...

Dell Inspiron 1420

*$ lspci | grep Network*
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

*$ modinfo rt61pci*
filename:       /lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.1.8
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     8F4EE2C062AC0B948F1F3AD
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
vermagic:       2.6.27-9-generic SMP mod_unload modversions

---

### Post by Minipalmer on 2008-12-30
Hey fellas, I have this problem too :(

I did NOT have this problem with 8.04. Only with the new 8.10 upgrade and new wireless drivers. Unfortunately, I don't think the old drivers work anymore.

I haven't narrowed the cause down to anything specific, I only know sometimes it will happen after several hours or several seconds.

Edit: I am on an Inspiron 1525.

---

### Post by Cha1ns on 2009-02-25
I also have a kernel panic in 8.10 that did not happen in 8.04 on the same hardware. The panic only happens on one Wireless network and no other time. Its a solid laptop 90% of the time on every wireless network I take it to. Yet, every time I bring it to my college, the kernel panics within 1 hour. 

I never had a problem prior to switching to 8.10, and I never have a problem when not connected to the wireless at college. Many other networks are fine.

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

dell b120 with a mini wlan adapter 1490

---

### Post by hadisen on 2009-06-03
Hello all !

In this thread people are talking about several problems all leading to a kernel panic, which is a very general symptom that can have different causes. I am experiencing kernel panics on my Sony Vaio VGN-TX laptop, running Ubuntu kernel 8.04: screen freezes, caps & scroll lock blinking. I have to pull out the battery to restart.
After four weeks of experimenting I can tell that this phenomenom only happens when I am using my Bluetooth mouse - but after random time intervals, not reproducible. It has nothing to do with WLAN in my case - compare bug #222859. It has something to do with the kernel and (what I found) there is no gurantee that Intrepid fixes the problem. I hope this contributes to the public confusion.

hadisen

---

### Post by jamaj on 2010-04-10
Today i was using my DELL inspiron 1525 at University Campus.

My kernel is Linux KAOS 2.6.27-17-generic #1 SMP Fri Mar 12 03:09:00 UTC 2010 i686 GNU/Linux

This was the first time this problem raised in this machine. Now i'm home, and using my wireless router this never happened, and the problem did not happen again.

So, i think something occurs only with my University wireless network. I already read that this simptom (caps and scroll lock leds blinking) means that kernel panic occurred.

But why only with some wireless networks? Do someone knows which program causes this kernel panic?

---

### Post by titotti32 on 2010-10-11
not only with broadcom wireless card, also happen in my ncomputing x550 server.

---

### Post by ibizatunes on 2010-10-11
This thread goes back to 2008, i presume that you run 10.04 or 10.10 for your desktops now?

---

### Post by titotti32 on 2011-02-01
> **ibizatunes said:**
> This thread goes back to 2008, i presume that you run 10.04 or 10.10 for your desktops now?
i'm sorry, but NComputing X550 must installed on Ubuntu 8.04 Hardy Heron :(

---

