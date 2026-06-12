---
title: "Howto:"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by kelvinq on 2005-04-13
Hi.

Would just like to share with all the poor atmel usb wireless adapters users here my success with D-Link DWL-120E.

I've tried using ndiswrapper as suggested on this forum, Driver loaded correctly but refused to work when I turn WEP on. No success with the sourceforge atmel drivers either.

First of all, I'm using the latest drivers from at76503c, available at [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)

Note: All other versions, 0.11 and before, DO NOT WORK.

Run make, make install.

If make gives you an error about not finding the kernel build directory, use Synaptic Package Manager to install linux-headers (search under 'linux). You can use apt-get for this too (duh!).

(Re-)Plugin your wireless card. Hotplug should load the respective drivers. dmesg should give you:

==
usb 1-2: new full speed USB device using ohci_hcd and address 5
/home/kelvinq/Desktop/stuff/at76/at76c503a/at76c503-fw_skel.c: using compiled-in firmware
/home/kelvinq/Desktop/stuff/at76/at76c503a/at76c503.c: $Id: at76c503.c,v 1.74 2005/03/08 01:33:14 jal2 Exp $ compiled Apr 13 2005 06:28:55
/home/kelvinq/Desktop/stuff/at76/at76c503a/at76c503.c: firmware version 1.101.5 #84 (fcs_len 4)
/home/kelvinq/Desktop/stuff/at76/at76c503a/at76c503.c: device's MAC 00:##:##:##:##:69, regulatory domain ETSI (Europe - (Spain+France) (id 48)
/home/kelvinq/Desktop/stuff/at76/at76c503a/at76c503.c: registered wlan0
==

Then use System>Administration>Networking to key in your essid, wep key, gateway and all.

Alternatively you may use iwconfig and route for these settings.

Good luck.

Kelvin Quee

---

