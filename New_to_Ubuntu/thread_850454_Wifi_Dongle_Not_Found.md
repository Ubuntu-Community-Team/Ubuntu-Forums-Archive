---
title: "Wifi Dongle Not Found"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by s.fox on 2008-07-05
Can anybody help me get this wireless dongle working on Ubuntu?  

When i hover over the network connection it says something like no wireless devices found but lsub gives:

```
lsusb
Bus 005 Device 005: ID 0cde:001a Z-Com 
ashley@ashley-desktop:~$ 
```

Thanks to anybody who can help.

---

### Post by s.fox on 2008-07-05
Can anybody help me get this wireless dongle working on Ubuntu?  

When i hover over the network connection icon it says something like no wireless devices found but lsub gives:

```
lsusb
Bus 005 Device 005: ID 0cde:001a Z-Com 
ashley@ashley-desktop:~$ 
```

Thanks to anybody who can help.

---

### Post by bodhi.zazen on 2008-07-05
I know mistakes happen, but please try not to double post :)

---

### Post by s.fox on 2008-07-05
My Firefox went really odd.  It double posted for me.  Didn't know who to contact to remove it.  Sorry

---

### Post by bodhi.zazen on 2008-07-05
> **Ash R said:**
> My Firefox went really odd.  It double posted for me.  Didn't know who to contact to remove it.  Sorry

np, it happens :)

---

### Post by freak42 on 2008-07-05
Maybe you can post the exact brand and name of the dongle.

If it isn't supported by Ubuntu maybe you can use ndiswrapper ([ndiswrapper.sourceforge.net/]("ndiswrapper.sourceforge.net/")). 
It helped me a couple of times with unsupported wifi-hardware

---

### Post by s.fox on 2008-07-06
Thanks for the help everyone.

The dongle is an eTEC XG-762N.  I appear to have the same dongle as this person:[http://ubuntuforums.org/archive/index.php/t-326459.html]("http://ubuntuforums.org/archive/index.php/t-326459.html")

Unfortunately I don't have the driver disc :(

Thank you for all the help

---

### Post by kamitsukai on 2008-07-06
> **Ash R said:**
> Thanks for the help everyone.

The dongle is an eTEC XG-762N.  I appear to have the same dongle as this person:[http://ubuntuforums.org/archive/index.php/t-326459.html]("http://ubuntuforums.org/archive/index.php/t-326459.html")

Unfortunately I don't have the driver disc :(

Thank you for all the help

you can download the driver form there website [http://www.etec-components.co.uk/download.html](http://www.etec-components.co.uk/download.html)

---

### Post by s.fox on 2008-07-06
UPDATE:  I think i have just downloaded the correct WIndows drivers from
 
[http://www.etec-components.co.uk/download.html]("http://www.etec-components.co.uk/download.html")

This ndiswrapper thing is a little confusing to me.  From what i understand its a way of using windows drivers on linux.  Is my understanding correct?  CAn anybody give me a step by step in  how to use it to setup my dongle?

Thanks once again

---

### Post by kamitsukai on 2008-07-06
Yep thats exactley what nidswrapper is :D also if you go here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) it should tell you all you need to know. make sure you try the other options before ndiswrapper!

---

### Post by s.fox on 2008-07-06
> **kamitsukai said:**
> Yep thats exactley what nidswrapper is :D also if you go here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) it should tell you all you need to know. make sure you try the other options before ndiswrapper!

What are the other options?

Thanks for the fast reply!

---

### Post by kamitsukai on 2008-07-06
In the introduction to that page it lists a couple of ways to use native linux drivers but only on certain chip sstes (the stuff insidde he dongle)

---

### Post by s.fox on 2008-07-06
Ok.  I just ran lspci and lspci -v.  Now I don't know how to proceed.  The help on the webpage looks like it will only work if you have a Broadcom wireless chip set.  

```
ashley@ashley-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
ashley@ashley-desktop:~$ 

```

```
ashley@ashley-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff900000-ff9fffff
	Prefetchable memory behind bridge: cff00000-efefffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at eec0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ef00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ef20 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ef40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffaffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fc00 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
	Flags: medium devsel
	I/O ports at 0400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 810d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at e800 [size=256]
	I/O ports at ee80 [size=64]
	Memory at ffaff800 (32-bit, non-prefetchable) [size=512]
	Memory at ffaff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 004c
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at d000 [size=256]
	Memory at ff9f0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at ff9c0000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 004d
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Memory at ff9e0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

ashley@ashley-desktop:~$ 

```

Thanks for all your help

---

### Post by freak42 on 2008-07-06
I cannot detect anything that resembles a wlan chipset in your output above (but I am no expert), did you execute the lspci commands while your dongle was attached to the system?

(I also think it is strange that there is no ethernet controller whatsoever (do you have an ethernet port on your computer?)

---

### Post by freak42 on 2008-07-06
DISREGARD MY ABOVE POST please.

since you are using a usb dongle you need to use the lsusb command: 
in the tutorial it is written here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#USB%20Wireless%20Adapter]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#USB%20Wireless%20Adapter")

---

