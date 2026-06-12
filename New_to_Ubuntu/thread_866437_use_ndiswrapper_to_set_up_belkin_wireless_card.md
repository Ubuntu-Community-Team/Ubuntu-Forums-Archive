---
title: "use ndiswrapper to set up belkin wireless card"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by beeman1266 on 2008-07-21
First, I'll get the formal declaration of newbiness out of the way. I just installed ubuntu 8.04. It seems nice except for the fact that I can't use my wireless card... not even getting any nice flashing lights. I know I'm supposed to download ndiswrapper which I've done (from cd) and now I'm supposed to download the driver for the card. How do I find out what my "chip set" is and how do I use this to get the driver I need. I'm using a Belkin G F5D7010v7 card. And lspci gives: Ethernet controller: Belkin Unknown device 701f (rev 20). Sorry if this question has been asked/is stupid. I've been searching around trying to find it but came up empty. Thanks for any help you can give.

---

### Post by phidia on 2008-07-21
You could try lspci -v and/or sudo lshw -C network post the results.
The community docs [here]("https://help.ubuntu.com/community/WifiDocs") have several wireless guides that could be helpful too.

---

### Post by beeman1266 on 2008-07-21
ben@fun-mobile-2:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 0149
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at f6f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf40 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at f6f7fc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 0000d000-0000efff
	Memory behind bridge: f8000000-fdffffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Unknown device 24c0
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0149
	Flags: bus master, medium devsel, latency 0, IRQ 7
	I/O ports at c800 [size=256]
	I/O ports at cc40 [size=64]
	Memory at f6f7f800 (32-bit, non-prefetchable) [size=512]
	Memory at f6f7f400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Broadcom Corporation Unknown device 4d64
	Flags: medium devsel, IRQ 7
	I/O ports at c400 [size=256]
	I/O ports at c080 [size=128]
	Capabilities: <access denied>

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
	Subsystem: Unknown device 4401:1028
	Flags: bus master, fast devsel, latency 32, IRQ 7
	Memory at fcffe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Dell Unknown device 0149
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at fc000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: f8000000-fbfff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001

---

### Post by beeman1266 on 2008-07-21
ben@fun-mobile-2:~$ sudo lshw -C network
[sudo] password for ben: 
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:aa:ce:8e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

---

### Post by beeman1266 on 2008-07-22
I'm still trying to get my wireless card working. I followed a step by step process by another guy who had the same wireless card as I do. But when I do: ndiswrapper -l, I get: net8185 driver installed, but no output about the hardware. And still no flashing lights... Any ideas?

---

