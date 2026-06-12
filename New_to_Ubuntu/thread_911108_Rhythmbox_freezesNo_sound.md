---
title: "Rhythmbox freezes/No sound"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by iamthemicrowave on 2008-09-05
Hi everyone. I just installed Hardy on my Dell Laptop, and I am having some audio problems. I can stream sound and video from the internet, but anything on my hard drive is having playback problems.

None of my music in Rhythmbox will play, and when I try Rhythmbox it freezes and I have to quit the application. Movies in VLC play fine, but there is no audio.

I have installed all codecs and plugins as mentioned in the sticky. I enabled crossfading in Rythmbox as well, to no avail. I got the ALSA drivers from a fresh kernel, as it says in the sticky, and this fixed the problem, UNTIL I restarted my computer. Now I am music-less again...please help!

This problem cant be very hard to solve, because I used to have gutsy on this laptop, and everything played fine.

Thanks any and all for your help!!

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ed000000-efefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: ecf00000-ecffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: ece00000-ecefffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: medium devsel, IRQ 3
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at ef000000 [disabled] [size=128K]
	Capabilities: <access denied>

03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 18
	Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at ecef0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ecffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

---

### Post by iamthemicrowave on 2008-09-06
Help please?

---

