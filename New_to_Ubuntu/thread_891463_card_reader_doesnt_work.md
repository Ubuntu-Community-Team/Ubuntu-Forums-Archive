---
title: "card reader doesnt work"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by inter-m on 2008-08-16
My laptop comes with a built in card reader now i tried to put a memory stick duo but it does not read it... any help is appreciated... thanx in advance...

K.H.

---

### Post by Cypher on 2008-08-16
Show us the outpout of "lspci -v"

---

### Post by inter-m on 2008-08-19
this is what i got i hope it helps

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff04
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff04
	Flags: fast devsel
	Memory at 88000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b4000000-b7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d3ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b8000000-bbffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d7ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: bc000000-bc0fffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at b0040800 (32-bit, non-prefetchable) [size=512]
	Memory at b0040400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: medium devsel, IRQ 18
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 2090 [size=8]
	I/O ports at 2084 [size=4]
	I/O ports at 2088 [size=8]
	I/O ports at 2080 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at b0040c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: medium devsel, IRQ 20
	I/O ports at 20a0 [size=32]

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 5000 [size=256]
	Memory at bc006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2741
	Flags: bus master, medium devsel, latency 32, IRQ 23
	Memory at bc007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at bc008000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 8c000000-8ffff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00005400-000054ff
	I/O window 1: 00005800-000058ff
	16-bit legacy interface ports at 0001

06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at bc006800 (32-bit, non-prefetchable) [size=2K]
	Memory at bc000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
	Subsystem: Toshiba America Info Systems Unknown device ff05
	Flags: bus master, medium devsel, latency 57, IRQ 16
	Memory at bc004000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
	Subsystem: Toshiba America Info Systems Unknown device ff05
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at bc009400 (32-bit, non-prefetchable) [size=256]
	Memory at bc009000 (32-bit, non-prefetchable) [size=256]
	Memory at bc006400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

---

