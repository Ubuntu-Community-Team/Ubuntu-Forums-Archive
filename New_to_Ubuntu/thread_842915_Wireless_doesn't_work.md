---
title: "Wireless doesn't work"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by vettexl on 2008-06-27
I am using a Compaq Presario V500 and I just installed Ubuntu (I also have it on my desktop computer), but I am having issues 
with my wireless connection. It is built in to the notebook, and I don't think Ubuntu can detect it. Is there anyway to get it working?

---

### Post by avtolle on 2008-06-27
From the terminal (Applications>>Accessories>>Terminal)```
lspci
```and post the results. We need to see what wireless card you have to make relevant suggestions.

---

### Post by phidia on 2008-06-27
At a terminal type lspci -v (or copy and paste that). You can look throught that out put to find your network device or post the output here.
Once the wireless card is IDed then it can probably be configured.

---

### Post by vettexl on 2008-06-27
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

administrator@adam-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
administrator@adam-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30ae
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
	Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
	Subsystem: Hewlett-Packard Company Unknown device 30ae
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30ae
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30ae
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 16
	Memory at c0003400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company Unknown device 30ae
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 16
	Memory at c0003800 (32-bit, non-prefetchable) [size=256]
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

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30ae
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 16
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 1355
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at c0200000 (32-bit, non-prefetchable) [size=8K]

06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device 30a4
	Flags: bus master, medium devsel, latency 128, IRQ 20
	I/O ports at a000 [size=256]
	Memory at c0202000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
```

---

### Post by vettexl on 2008-06-27
Sorry for the double post but I need to get this solved within the next 15 minutes.

Thanks

---

### Post by avtolle on 2008-06-27
Looks like you have a Broadcom BCM4318 as your wireless card. That shuts me out for any further assistance here, turning you over to the Broadcom users (or those more familiar with wireless generally than I).

---

### Post by vettexl on 2008-06-27
Is Broadcom incompatable with Ubuntu?

---

### Post by avtolle on 2008-06-27
No, but there's a bit of work to be done to get it up and working. If you wish, do a forum search, put in Broadcom 4318 in the search bar, and see what threads it finds.

---

### Post by vettexl on 2008-06-27
I got this: [http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+4318)

Do I try that?

---

### Post by avtolle on 2008-06-27
You may; since your card is a 4318 not a 4312, be sure to do the part in red under Step 1. Good luck.

---

### Post by vettexl on 2008-06-27
I just took a look at that, and have no idea what I'm doing.

---

