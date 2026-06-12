---
title: "Missing wirless firmware"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Mashai on 2011-09-14
Hello, Ubuntu community.

I recently installed a new hard drive. Unfourtunatly, when I try to use wireless, it tells me I lack the firmware to do so. How can I figure out what I need to download? And no, 'additional drivers' in system/administration doesn't find it.

---

### Post by walt.smith1960 on 2011-09-14
What kind of wireless adapter, internal (PCI) or USB?  If you could post the output of lspci or lsusb as appropriate, that might be a good place to start.  Missing firmware is a not-uncommon situation. There might also be useful messages in dmesg.

---

### Post by Dragonbite on 2011-09-14
If you have a NIC, plug it in and depending on your wireless you may be able to add the drivers.

For example, I have a Broadcom wireless adapter so every time I install Ubuntu I have to, while connected to the internet over wire, go into the Software Center and search for "b43".  Once I find the right one and install it, I have wireless again.

It's a pain, that's for sure, but it beats Windows!  Installing Windows XP and it can't use the NIC!  So first I have to install the NIC (or the wireless) before I can run updates to get the other drivers that are missing (like video)!

---

### Post by Mashai on 2011-09-17
> **walt.smith1960 said:**
> What kind of wireless adapter, internal (PCI) or USB?  If you could post the output of lspci or lsusb as appropriate, that might be a good place to start.  Missing firmware is a not-uncommon situation. There might also be useful messages in dmesg.

Okay, so here's what I got:
> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
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
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by wildmanne39 on 2011-09-18
Hi, there is a bug in the install firmware in natty for that card here is the easy way to do it.

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then unplug your wired connection. Open a terminal and do these commands one at a time:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thank you

---

