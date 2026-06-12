---
title: "card reader does not work"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by ccl4 on 2008-09-21
what should i do so ubuntu can read my sd card?
thanks

---

### Post by dhtseany on 2008-09-21
Is the card reader built into your computer or an external one (Like USB or Firewire)?

Peace
Sean

---

### Post by ccl4 on 2008-09-21
it is built in

---

### Post by dhtseany on 2008-09-21
Ok, I believe this is the command you use to show what devices are recognized on your system (And I welcome someone else to step in and correct me if I'm wrong):

```
lspci -v
```

Post the output of that.

Also post the output from the following:
```
lsusb
```

Peace
Sean

---

### Post by ccl4 on 2008-09-21
does not work

---

### Post by Sycron on 2008-09-21
Go to Applications-->Accesories-->Terminal then type: ```
lspci -v
```. You will get some text's around there. Copy them here. Do the same with ```
lsusb
```

---

### Post by ccl4 on 2008-09-21
**lspci -v**
> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: dc700000-dc7fffff
	Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dc800000-dcffffff
	Prefetchable memory behind bridge: 00000000be000000-00000000bfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: dd000000-dfefffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at dc6be000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at dc6bfc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c800 [size=8]
	I/O ports at c480 [size=4]
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=16]
	Memory at dc6bd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	Memory behind bridge: dff00000-dfffffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1339
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at dc6b8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1385
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at dc6bc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Atheros Communications Inc. AR5006EG 802.11bg NIC (2.4GHz, PCI Express)
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at dc7f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1322
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at dfee0000 [disabled] [size=128K]
	Capabilities: <access denied>

05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at dfffe800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: medium devsel, IRQ 17
	Memory at dffff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: medium devsel, IRQ 10
	Memory at dffff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

05:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1387
	Flags: medium devsel, IRQ 10
	Memory at dffffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>



**lusb**
> Bus 002 Device 004: ID 046d:c045 Logitech, Inc. 
Bus 002 Device 005: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 05e1:0501 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

---

### Post by dtl on 2008-11-15
Hi, 
May I join in ? My 5in one card reader acts strangely. The usb slot in it works fine but the other ones for my camera cards works only when it feels like it. Sometimes it comes on many hours after insertion. But mostly not at all.
My outputs are :

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: d0000000-d7ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Unknown device a102
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: d8000000-d80fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at b400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology Unknown device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d8304000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d8100000-d81fffff
	Prefetchable memory behind bridge: 00000000d8200000-00000000d82fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Giga-byte Technology Unknown device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Giga-byte Technology Unknown device 5001
	Flags: medium devsel, IRQ 11
	I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81dc
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at d5000000 [disabled] [size=128K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
	Subsystem: Giga-byte Technology Unknown device e000
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

04:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Twinhan Technology Co. Ltd VisionPlus DVB card
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at d8200000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

04:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Twinhan Technology Co. Ltd VisionPlus DVB Card
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at d8201000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

04:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
	Subsystem: Conexant Unknown device 2000
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at d8100000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at a000 [size=8]
	Capabilities: <access denied>


and :  
Bus 005 Device 003: ID 1307:0163 Transcend Information, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 

Hope somebody can help us .
Thanks

---

