---
title: "All sorts of issues"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by ohchumanities on 2008-09-15
Hi everyone, 

I'm totally new to Ubuntu and really Linux in general.  I just made the switch over from Windows and I am having all sorts of issues adjusting.

First, I haven't been able to get my wireless network to show up.  I've seen several how-tos on how to correct this problem, but nothing seems to work.  

Connected to this, I can't seem to get anything I've downloaded to work either.  As I don't have internet on my pc, I've been downloading through windows, putting the downloads onto an external hardrive, and then uploading them in Ubuntu.  I've then tried to follow the command line instructions, but nothing seems to work.  Most often, I get a message like "No such file or directory".

I've also been trying to get LAMP and XAMPP to work (the main reason I switched to a linux based os), but again, nothing.  

I'm obviously doing some things wrong here- so any help would be great!  Thanks so much- I've heard such great things about Ubuntu and hope to keep working with it.

---

### Post by porchrat on 2008-09-15
it seems like most of your issues could be solved by getting your network working.

If you could post the ouput of this command here on the forum we could help you a little more:

```
lshw -C network
```

This will tell us what wireless module you are running.

Another thought:  Can't you just use an ethernet connection to the router in place of the wireless connection in the meantime?

---

### Post by ohchumanities on 2008-09-15
Ok, here's what I got.  (I'm on two computers now, one with internet, one running Ubuntu, so sorry if I make an errors re-typing)

Hardware LIster (lshw)-B.02.12.01
lshw [-format] [-options . . .]
lshw -version
-version print program version (B.02.12.01)

format can be 
-html output hardware tree as HTML
-xml output hardware tree as XML
-short output hardware paths
-businfo output bus information

options can be
-class CLASS only show a certain class of hardware
-C CLASS same as '-class CLASS'
-disable TEST disable a test (like pci, isapnp, cpuid, etc.)
-quiet don't display status
-sanitize samitize output (remove sensitive information like serial numbers, etc.)

Does this help at all?  Thanks for getting back to me!

---

### Post by ohchumanities on 2008-09-15
I didn't see your post about the ethernet connect- that's not a bad thought.  I would like to get my wireless working, and I still can't seem to get anything I download to work.  Is it because I'm transfering from an external hardrive?  Or do I not have these files in the right place?  If that makes sense.

---

### Post by phidia on 2008-09-15
It seems you didn't enter the command "lshw -C network" that porchrat provided correctly.
Open a terminal from Applications > Accessories and enter that command and also "lspci -v" as they appear-don't include the quotation marks.

To answer your last question: To use files you downloaded probably requires creating an external repo (your own repository) it's doable but requires more work than just plugging in your Ethernet or configuring wireless (hopefully).

---

### Post by ohchumanities on 2008-09-15
Hi sorry about the last mix up.

Here is the information you asked for:
Command: lshw -C network
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:73:f2:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:9c:ae:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Command: lspci -v:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfc00000-dfdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: dfb00000-dfbfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 01c9
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Dell Unknown device 0005
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]


Thanks again for all of the help!  I think I have the right information posted now.  Thanks again so much.

---

### Post by panhandle on 2008-09-15
You mentioned that you have followed howtos here on the boards. Did you follow this one?

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by porchrat on 2008-09-16
panhandle is right...that guide looks like it will work as this is your wireless module:

> product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation

This could be the problem though...seems like the wireless card is disabled:

> configuration: driver=b43-pci-bridge latency=64 module=ssb
_***-network DISABLED**_
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:16:cf:9c:ae:55

Does your machine have some sort of wireless switch and if so is it disabled or enabled?  If not then no worries, but if so it is a easy possible solution.

---

### Post by ohchumanities on 2008-09-16
Thanks for the help everyone, I will try to get this all fixed.  To make matters worse my internet is completely down at home right now, so as soon as I get a chance, I'll try your solutions.  I don't think my wireless card is disabled, as it still works when I boot Windows.  So, I'll try this fix and keep my fingers crossed.  Thanks again so much!

---

