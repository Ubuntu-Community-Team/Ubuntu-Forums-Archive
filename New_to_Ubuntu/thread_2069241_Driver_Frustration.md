---
title: "Driver Frustration"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by ALinuxWindowsBalance on 2012-10-10
I don't hate linux, but it's ticking me off right now.
I started with Ubuntu about two years ago, with Oneiric, and had zero problems with the wifi, or sound on a D610 laptop. I _loved_ it. No problems, and, it was free! The only thing not totally amazing was the fact that it would crash if I tried to install 12.04. But, hey, 11.10 was fine. So, I kept going along until the laptop died. Now, I decide to use Ubuntu on an a6257c HP Pavilion.
Everything went smoothly, except for the fact that the sound doesn't work, and numerous others.

   I have a Creative SoundBlaster PCI (model CA0106) internal sound card. Does not play sound.
   
   I have a Netgear Wireless Adapter PCI (model WG311v3) internal wireless. Ubuntu says no network devices available.

   I have an onboard LSI Corp. 1394 (model FW322), which, also does nothing under Ubuntu.

   I have a generic onboard Ethernet Controller. Ubuntu says no network devices available.

See, I know the little tricks and quirks of Ubuntu. I can get stuff working from the command line. 
But, for this particular issue, i'm frazzled. Usually, the ethernet drivers are there, and I can hook it up to use my Mac's ICS. This is dead in the water. The only connections it has to the outside world is a couple of flash drives. 

I've tried building NDISwrapper from source, but the GCC and all that have endless dependencies that aren't available to me. I used BuildEssentials.deb or something like that, but the Install in the ubuntu app store is grayed out. Same if i use a pre-built version of NDISwrapper. The install button is not available.

Hm. I love Ubuntu. I **HATE** the drivers.

Basically, my problem is that there is no connections to the outside world. 
See, If there was an ethernet driver, I'd be fine. But, there isn't.

I hope someone knows more than I do on this. Ironically, I'm only useful when there is a connection. (Web Dev)

**EDIT**
I'm continuing to work on this as you type.

Good Luck solving this,
 ALinuxWindowsBalance

---

### Post by ortermagic on 2012-10-10
I have had some problems with wifi set ups myself. It might be helpful if you had a look at this excellent thread...which worked for me!

[http://ubuntuforums.org/showthread.php?t=2053179](http://ubuntuforums.org/showthread.php?t=2053179)

---

### Post by chili555 on 2012-10-10
I suggest you move your networking issue to Networking and Wireless and include:```
lspci -nn | grep-e 0200 -e 0280
```I'll be happy to help.

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by ALinuxWindowsBalance on 2012-10-10
```
02:05.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
```
Marvell or Netgear?
Wierd.

---

### Post by chili555 on 2012-10-10
> **ALinuxWindowsBalance said:**
> ```
02:05.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
```
Marvell or Netgear?
Wierd.Please post in Networking and Wireless.

---

### Post by ALinuxWindowsBalance on 2012-10-10
I don't hate linux, but it's ticking me off right now.
I started with Ubuntu about two years ago, with Oneiric, and had zero problems with the wifi, or sound on a D610 laptop. I loved it. No problems, and, it was free! The only thing not totally amazing was the fact that it would crash if I tried to install 12.04. But, hey, 11.10 was fine. So, I kept going along until the laptop died. Now, I decide to use Ubuntu on an a6257c HP Pavilion.
Everything went smoothly, except for the fact that the sound doesn't work, and numerous others.

I have a Creative SoundBlaster PCI (model CA0106) internal sound card. Does not play sound.

I have a Netgear Wireless Adapter PCI (model WG311v3) internal wireless. Ubuntu says no network devices available.

I have an onboard LSI Corp. 1394 (model FW322), which, also does nothing under Ubuntu.

I have a generic onboard Ethernet Controller. Ubuntu says no network devices available.

See, I know the little tricks and quirks of Ubuntu. I can get stuff working from the command line. 
But, for this particular issue, i'm frazzled. Usually, the ethernet drivers are there, and I can hook it up to use my Mac's ICS. This is dead in the water. The only connections it has to the outside world is a couple of flash drives. 

I've tried building NDISwrapper from source, but the GCC and all that have endless dependencies that aren't available to me. I used BuildEssentials.deb or something like that, but the Install in the ubuntu app store is grayed out. Same if i use a pre-built version of NDISwrapper. The install button is not available.

Hm. I love Ubuntu. I HATE the drivers.

Basically, my problem is that there is no connections to the outside world. 
See, If there was an ethernet driver, I'd be fine. But, there isn't.

I hope someone knows more than I do on this. Ironically, I'm only useful when there is a connection. (Web Dev)

**EDIT**
I'm continuing to work on this as you type.

Good Luck solving this,
ALinuxWindowsBalance

NOTE: Moved from Absolute Beginner.

Exact lspci -nn result 02:05.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

---

### Post by ALinuxWindowsBalance on 2012-10-10
I've also installed a wireless subsystem, I'm hoping that will work.
If it does, I'll give a report on here about it.

---

### Post by oldos2er on 2012-10-10
Threads merged. Please don't open more than one thread per question. Thanks.

---

### Post by Lyfang on 2012-10-13
I rather have too many drivers than missing the correct Linux driver. But the Linux kernel needs to balance the supported hardware and Linux kernel growth. Linus Torvalds said the kernel has become 'bloated and huge'. Or what about upgrading or compiling the kernel to add a piece of hardware?

---

### Post by cdoebbler on 2012-10-13
Does anyone know how to get the Netgear A6200 (450/450) wifi usb stick working with Ubuntu 12.04 LTS? IT seems there are no drivers available. This is an new generation ac speed modem.

---

