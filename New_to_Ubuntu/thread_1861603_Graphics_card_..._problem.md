---
title: "Graphics card ... problem?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by BlackS3th on 2011-10-15
Ok so... I was thinking the other day if my lappy works properly
and i saw some forums... I found out that my card dosent make direct rending so i figured that this must be a problem. I will give some info about my lappy's graphic card (if you need more plz ask) and plz help me without going like... YoUr A NoOb plz :)



from lspci..


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


and lspci -v...


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Device 01f9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Latitude D630
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at efe8 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
	Subsystem: Dell Device 01f9
	Flags: bus master, fast devsel, latency 0
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f20 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f00 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Dell Latitude D630
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 84400000-845fffff
	Prefetchable memory behind bridge: 0000000084600000-00000000847fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 0000000084200000-00000000843fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: fe700000-fe7fffff
	Prefetchable memory behind bridge: 0000000084000000-00000000841fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6f40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fe600000-fe6fffff
	Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 01f9
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=16]
	I/O ports at eff0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Device 01f9
	Flags: medium devsel, IRQ 10
	Memory at fe9fbf00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
	Subsystem: Dell Device 01f9
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 19
	Memory at fe600000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 88000000-8bfff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Dell Device 01f9
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fe6ff000 (32-bit, non-prefetchable) [size=4K]
	Memory at fe6fe800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Dell Device 01f9
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fe7f0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1021
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

Also from system profile and benhmark i get this..

Resolution	1280x800 pixels
Vendor	The X.Org Foundation
Version	1.10.4
Monitors
Monitor 0	1280x800 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DOUBLE-BUFFER	
DPMS	
DRI2	
GLX	
Generic Event Extension	
GestureExtension	
MIT-SCREEN-SAVER	
MIT-SHM	
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-DGA	
XFree86-VidModeExtension	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
XVideo-MotionCompensation	
OpenGL
Vendor	Unknown
Renderer	Unknown
Version	Unknown
Direct Rendering	No


Begining to <3 ubuntu :P

---

### Post by BlackS3th on 2011-11-15
Yeah.. i solved it .. i just needed to upgrade and get mesa<--- ...

Dirext rending .. yes :)

---

