---
title: "[SOLVED] cant load KDE 4.1"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by dineshs on 2008-11-13
I am unable to install  8.1 as the process freezes at step 1 .When tried to  upgrade from 8.04 , the login screen freezes after upgrade.Tried all options in recovery mode.At last I reinstalled 8.04 then  tried to install KDE4.1 . Now the loading just begins,then goes back to login screen again .(I can boot gdm and KDE).Can anyone help please?

---

### Post by dineshs on 2008-11-13
Kindly help .Is it a display driver problem .Is there no solution?

---

### Post by Crafty Kisses on 2008-11-13
I need some more information, what are your system specs?

---

### Post by dineshs on 2008-11-13
I have an asus A8V MX motherboard 64 bit AMD processor,and 512 RAM.Samsung 17 inch LCD monitor.

---

### Post by Viranh on 2008-11-13
Please tell us what graphics card you are using.

---

### Post by dineshs on 2008-11-14
I am not an expert .I dont use a separate card but the one integrated with motherboard.Can these links help ?
[http://www.driverstock.com/ASUS-A8V-MX-driver-download/6-9-10210/index.html](http://www.driverstock.com/ASUS-A8V-MX-driver-download/6-9-10210/index.html)
[http://www.asus.com/products.aspx?modelmenu=1&model=743&l1=3&l2=15&l3=224](http://www.asus.com/products.aspx?modelmenu=1&model=743&l1=3&l2=15&l3=224)
Thanks in advance

---

### Post by Crafty Kisses on 2008-11-14
Post the results of this command:
```
lspci
```

---

### Post by dineshs on 2008-11-14
At present I am in the office.I will reach home only after 5 hrs.I shall let you know

---

### Post by Ptero-4 on 2008-11-14
sounds like a VIA S3 unichrome (a POS card). Try and post the output of the lspci -v command to see if it's indeed an unichrome.

---

### Post by dineshs on 2008-11-14
This is what I get for lspci

dinesh@dinesh:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port


and for lspci -v

dinesh@dinesh:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 64
	Memory at dc000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: fca00000-feafffff
	Prefetchable memory behind bridge: cff00000-d7efffff
	Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
	Flags: bus master, medium devsel, latency 64, IRQ 221
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at e080 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at e000 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at d880 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at febef800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
	Subsystem: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
	Flags: medium devsel
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81b9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d400 [size=256]
	Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Subsystem: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Flags: bus master, medium devsel, latency 128
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at d000 [size=256]
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0

00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8129
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at d0000000 (32-bit, prefetchable) [size=64M]
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at fe9f0000 [disabled] [size=64K]
	Capabilities: <access denied>

02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

---

### Post by dineshs on 2008-11-14
I went throug the release notes

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Is it a bug (287488) as the note says.I dont understand how to solve

---

### Post by dineshs on 2008-11-14
pl help

---

### Post by dineshs on 2008-11-14
some one please I am not an expert

---

### Post by dineshs on 2008-11-15
I think I will have to give up

---

### Post by dineshs on 2008-11-16
At last I tried a kubuntu 8.1 cd with option start installation in safe graphics mode and could install .Still dont know how

---

