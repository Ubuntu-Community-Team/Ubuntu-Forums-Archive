---
title: "Having trouble w/ Broadcom on Hardy?  Give this a shot"
date: 2008-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by superm1 on 2008-08-04
Hi Everyone:

Broadcom has released a driver that supports recent A/B/G/N adapters.  The intention of this driver was to support current Dell platforms with Broadcom adapters, but as advertised on their site, it operates with a variety of non-Dell hardware too.  This means the **4311**, **4312**, **4321**, **4322**, and **4328** adapters. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The Broadcom 4306 has been verified** to not work with this.**

If you are having trouble w/ b43, or trouble with ndiswrapper please give this driver a try:

To enable it:

1) Fully update your 8.04.1 install.

2) Deactivate any ndiswrapper installed drivers.  There should be a remove option for ndiswrapper.

3) Click System->Administration->Hardware Drivers

4) Click the "Broadcom STA wireless driver" in the Hardware Drivers tool.
[IMG]http://home.eng.iastate.edu/%7Esuperm1/jockey.png[/IMG]

5) Reboot
Things should work on this next boot.    If you have troubles, please open up *another* forum post rather than looking for support in this thread.

--------
If this doesn't work for you and you want to revert back:

1) Open up Hardware drivers again, and "uncheck" the checkbox for "Broadcom STA wireless driver"

**Known issues:**
1) If you have an ethernet driver supported by ssb/b44, you will not be able to use this

---

### Post by Ayuthia on 2008-08-07
**Worked: **Yes
**uname -a:** Linux allen-fieldhouse 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
**lspci -vv -nn:** (For those who don't want to read through the info: 14e4:4311 rev 01 Subvendor:103c:1363)
```
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b4000000-b5ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: b6000000-b7ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: I/O ports at 1d00 [size=128]

00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 16
	Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device [f03c:30b7]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 3080 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 30c0 [size=8]
	Region 1: I/O ports at 30b4 [size=4]
	Region 2: I/O ports at 30b8 [size=8]
	Region 3: I/O ports at 30b0 [size=4]
	Region 4: I/O ports at 3090 [size=16]
	Region 5: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
	Memory behind bridge: b8000000-b80fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at b0008000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 30e0 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device [103c:1363]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at b6000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max)
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin B routed to IRQ 7
	Region 0: Memory at b8000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at b8000c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at b8001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff) (prog-if ff)
	!!! Unknown header type 7f

```

**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels

```

**Laptop:** HP Pavilion dv6338se
**Encryption:** None, WEP
**Range:**Around 35 meters.  Signal strength is shown as n/5 where n would be any number between 0 to 5.  This differs from the n/100 scale.

**Comments:**
The wl driver worked really well, but I have not tested encryption on it yet.  I did have to load the module manually though:
```
sudo modprobe wl
```so I have added it to /etc/modules:
```
echo wl|sudo tee -a /etc/modules
```When I ran lshw -C network before loading the wl driver, the wireless card showed up, but no driver was listed.  The other change that occurred was that the logical name of the card changed from wlan0 to eth1.

Just to make sure that it was the wl driver that was working, I also removed the firmware from /lib/firmware/b43 and /lib/firmware/b43legacy.

The only caution that I want to add is with the blacklisting of ssb.  The Broadcom 44xx series ethernet cards (the wired card) use the b44 driver and that needs the ssb driver if I understand correctly.  If ssb is blacklisted, I am not for sure if ssb will still load for it and if it does, I am guessing that it might be loaded before the wl driver.  I am going to be testing this out shortly on my other laptop.

---

### Post by pytheas22 on 2008-08-07
I'm trying to test this for a 4306 card on Gutsy (this is my only computer with a Broadcom chipsest and it needs to keep running Gutsy for the time being).  Since I'm on Gutsy, I'm trying to build the kernel module using the source and directions given on Broadcom's site, instead of following the instructions to install it via the repositories.  However I can't get it to build:

```
$ sudo make -C /lib/modules/2.6.22-14-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** No rule to make target `linux'.  Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
```

This is probably just a simple issue with make, but I'm not sure how to solve it.  If you have time and want to suggest a solution, I'll continue trying to build the module and see if I can get it to drive my card.

EDIT: my card is also a 4306 14e4:4320, which Ayuthia tests below and confirms not to be supported, so I won't bother compiling this module.

---

### Post by Ayuthia on 2008-08-07
**Worked:** No
**uname -a: ** Linux ubuntu 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
**lspci -vv -nn:** (Broadcom 4306 14e4:4320 rev 03 Subvendor  1028:0003)
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:01.0 PCI bridge [0604]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller [8086:3581] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at bf80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 18
        Region 4: I/O ports at bf40 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 19
        Region 4: I/O ports at bf20 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 20
        Region 0: Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at bfa0 [size=16]
        Region 5: Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at b800 [size=256]
        Region 1: I/O ports at bc40 [size=64]
        Region 2: Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01) (prog-if 00 [Generic])
        Subsystem: Broadcom Corporation Unknown device [14e4:4d64]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at b400 [size=256]
        Region 1: I/O ports at b080 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34M [GeForce FX Go5200 64M] [10de:0324] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
        Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at faffc000 (32-bit, non-prefetchable) [size=8K]

02:04.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 34000000-37fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

02:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029] (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at faffb800 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at faff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```
**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels

```

**Laptop:** Dell Inspiron 5150

**Comments: **No surprise.  This card did not work with the wl module.  Even though I did blacklist the ssb module, it did come back again when the b44 module loaded.  Most likely a script will be needed like what was done for ndiswrapper so that the ssb module is loaded after the wl module (modified script based on [https://help.ubuntu.com/community/WifiDocs/Drive/bcm43xx/Feisty_No-Fluff#Version](https://help.ubuntu.com/community/WifiDocs/Drive/bcm43xx/Feisty_No-Fluff#Version) 0.3):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```This script was not tested because the wl module does not work for this card.

---

### Post by superm1 on 2008-08-07
> **Ayuthia said:**
> **Worked:** No
**uname -a: ** Linux ubuntu 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
[b]lspci -vv -nn: (Broadcom 4306 14e4:4320 rev 03 Subvendor  1028:0003)
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:01.0 PCI bridge [0604]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller [8086:3581] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at bf80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 18
        Region 4: I/O ports at bf40 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 19
        Region 4: I/O ports at bf20 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 20
        Region 0: Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at bfa0 [size=16]
        Region 5: Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at b800 [size=256]
        Region 1: I/O ports at bc40 [size=64]
        Region 2: Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01) (prog-if 00 [Generic])
        Subsystem: Broadcom Corporation Unknown device [14e4:4d64]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at b400 [size=256]
        Region 1: I/O ports at b080 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34M [GeForce FX Go5200 64M] [10de:0324] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
        Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at faffc000 (32-bit, non-prefetchable) [size=8K]

02:04.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 34000000-37fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

02:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029] (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device [1028:015f]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at faffb800 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at faff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels

```**Laptop:** Dell Inspiron 5150

**Comments: **No surprise.  This card did not work with the wl module.  Even though I did blacklist the ssb module, it did come back again when the b44 module loaded.  Most likely a script will be needed like what was done for ndiswrapper so that the ssb module is loaded after the wl module (modified script based on [https://help.ubuntu.com/community/WifiDocs/Drive/bcm43xx/Feisty_No-Fluff#Version](https://help.ubuntu.com/community/WifiDocs/Drive/bcm43xx/Feisty_No-Fluff#Version) 0.3):
```
echo -e '#ssb workaround, added `date`\ninstall wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```This script was not tested because the wl module does not work for this card.
Kind of surprising the 4320 wouldn't work.  If you rmmod ssb and modprobe wl, any more luck?

---

### Post by Ayuthia on 2008-08-07
> **superm1 said:**
> Kind of surprising the 4320 wouldn't work.  If you rmmod ssb and modprobe wl, any more luck?
Well, the 4320 card is labeled as a 4306 and it is an older card.  I removed all the possible modules (b43, b43legacy, b44, ssb, ndiswrapper, wl) and then I loaded wl.  No luck.  The module was there, but the driver would not work.  lshw -C network did not show any drivers and dmesg had nothing to report.

---

### Post by Ayuthia on 2008-08-07
> **pytheas22 said:**
> I'm trying to test this for a 4306 card on Gutsy (this is my only computer with a Broadcom chipsest and it needs to keep running Gutsy for the time being).  Since I'm on Gutsy, I'm trying to build the kernel module using the source and directions given on Broadcom's site, instead of following the instructions to install it via the repositories.  However I can't get it to build:

```
$ sudo make -C /lib/modules/2.6.22-14-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** No rule to make target `linux'.  Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
```

This is probably just a simple issue with make, but I'm not sure how to solve it.  If you have time and want to suggest a solution, I'll continue trying to build the module and see if I can get it to drive my card.This message almost looks like you were not in the directory where the Makefile is located. From the "No rule to make target `linux`.  Stop" message, it looks like you were in /usr/src/linux-headers-2.6.22-14-generic instead of hybrid_wl.

---

### Post by swordphsh on 2008-08-07
**Worked:** yes
**uname -a:** Linux 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
**lspci -vv -nn:** 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [88] Subsystem: Dell Unknown device [1028:01fe]
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: fee0300c  Data: 41c1
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 2
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x16
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise-
		Slot: Number 1, PowerLimit 75.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at 6f20 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 6f00 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 0: Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 2, PowerLimit 6.500000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: fee0300c  Data: 41c9
	Capabilities: [90] Subsystem: Dell Unknown device [1028:01fe]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: f9f00000-f9ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM L0s Enabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 3, PowerLimit 6.500000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: fee0300c  Data: 41d1
	Capabilities: [90] Subsystem: Dell Unknown device [1028:01fe]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f9c00000-f9efffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 4
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x0
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 5, PowerLimit 6.500000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: fee0300c  Data: 41d9
	Capabilities: [90] Subsystem: Dell Unknown device [1028:01fe]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: f9b00000-f9bfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 6
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 3, PowerLimit 6.500000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: fee0300c  Data: 41e1
	Capabilities: [90] Subsystem: Dell Unknown device [1028:01fe]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at 6f80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 6f60 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 4: I/O ports at 6f40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Memory behind bridge: f9a00000-f9afffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: [50] Subsystem: Dell Unknown device [1028:01fe]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 6fa0 [size=16]

00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 6eb0 [size=8]
	Region 1: I/O ports at 6eb8 [size=4]
	Region 2: I/O ports at 6ec0 [size=8]
	Region 3: I/O ports at 6ec8 [size=4]
	Region 4: I/O ports at 6ee0 [size=16]
	Region 5: I/O ports at eff0 [size=16]
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at febfbf00 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 135M [10de:042b] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at df00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <512ns, L1 <4us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM L0s L1 Enabled RCB 128 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x16

03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f9a00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f9aff000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at f9afe800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
	Subsystem: Dell Unknown device [1028:01fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 218
	Region 0: Memory at f9bf0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Vendor Specific Information
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 414a
	Capabilities: [d0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 4096 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM L0s Enabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM L0s Enabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
```

**dpkg -l|grep linux-restricted:**
```

rc  linux-restricted-modules-2.6.22-14-386     2.6.22.4-14.10                                             Non-free Linux 2.6.22 modules on 386
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-20.46                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                                               Restricted Linux modules for generic kernels
```

**Laptop:** Dell Latitude D830

**Comments:** It seems to be working, but disconnects me every so often. I was formally using the b43 drivers and had terrible signal strength; these new drivers give excellent strength.

---

### Post by tedarmitage on 2008-08-08
It worked on hp pavilion 6408ca

Linux ted-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels


I was a little confused by "Open up Synaptic", being a Ubuntu beginner, but eventually realised it wasn't a package name.  And since it was my first time I could only mark the linux package for install (not UPDATE).

Packages automatically selected were:
linux-generic (version 2.6.24.19.21) will be upgraded to version 2.6.24.20.22
linux-image-generic (version 2.6.24.19.21) will be upgraded to version 2.6.24.20.22
linux-restricted-modules-generic (version 2.6.24.19.21) will be upgraded to version 2.6.24.20.22
linux (version 2.6.24.20.22) will be installed
linux-image (version 2.6.24.20.22) will be installed
linux-image-2.6.24-20-generic (version 2.6.24-20.38) will be installed
linux-restricted-modules (version 2.6.24.20.22) will be installed
linux-restricted-modules-2.6.24-20-generic (version 2.6.24.14-20.46) will be installed
linux-ubuntu-modules-2.6.24-20-generic (version 2.6.24-20.29) will be installed   


Many thanks. Now I can delete Windows Vista.

---

### Post by tedarmitage on 2008-08-08
.... oops, file did not upload. 

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1374]

---

### Post by superm1 on 2008-08-08
> **tedarmitage said:**
> It worked on hp pavilion 6408ca

Linux ted-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels


I was a little confused by "Open up Synaptic", being a Ubuntu beginner, but eventually realised it wasn't a package name.  And since it was my first time I could only mark the linux package for install (not UPDATE).

Packages automatically selected were:
linux-generic (version 2.6.24.19.21) will be upgraded to version 2.6.24.20.22
linux-image-generic (version 2.6.24.19.21) will be upgraded to version 2.6.24.20.22
linux-restricted-modules-generic (version 2.6.24.19.21) will be upgraded to version 2.6.24.20.22
linux (version 2.6.24.20.22) will be installed
linux-image (version 2.6.24.20.22) will be installed
linux-image-2.6.24-20-generic (version 2.6.24-20.38) will be installed
linux-restricted-modules (version 2.6.24.20.22) will be installed
linux-restricted-modules-2.6.24-20-generic (version 2.6.24.14-20.46) will be installed
linux-ubuntu-modules-2.6.24-20-generic (version 2.6.24-20.29) will be installed   


Many thanks. Now I can delete Windows Vista.
Ted, please add in the information about lspci -nn.

Much thanks!

---

### Post by richs360 on 2008-08-08
please help!!! Im new to ubuntu and cant get wireless to work... ive tried everything but dont realy understand what im supposed to do. if anyone can help in simpl terms please... please... please 
 *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:83:8b:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-2 ip=192.168.1.4 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

this is my wireless device

---

### Post by pytheas22 on 2008-08-08
@richs360

You should probably start a new thread for your issue, as it's not really on the same topic as this one.  Please post the URL of your new thread and we can help you there.  I think that the solution is simple; you'll just need to revert to the bcm43xx driver, which should support your card, according to [this]("http://ubuntuforums.org/showthread.php?t=434946").

You could also follow the instructions in the first post here to see if Broadcom's driver will support your card, even though it's not advertised to--that was the original intent of this thread, to figure out which wireless cards are supported by this new driver.

EDIT: to save some time and avoid extraneous posts, I figured I would write out here the commands that you should use to make your card work using the bcm43xx driver (make sure you are plugged into the Internet via ethernet before running these commands; if that's impossible, let us know and we can work around it):

```
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

After running this last command, you should be asked whether you want to download firmware automatically; say yes.  Then reboot and your wireless should be working.  If not, please post in your new thread the output of:

```

iwlist scan
lshw -C Network
cat /etc/modprobe.d/blacklist
lspci -nn | grep -i broadcom
dmesg | grep -e bcm -e eth1
```

---

### Post by richs360 on 2008-08-08
[http://ubuntuforums.org/showthread.php?t=884111](http://ubuntuforums.org/showthread.php?t=884111)

Thanks

---

### Post by ThaRabbit on 2008-08-09
**Laptop:**
HP Compaq 6720s

**WiFi module:**
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

**Diagnosis:**
Sweet! Same speeds as ndiswrapper! Good range too.

**DPKG:**
```
ii  linux-restricted-modules                   2.6.24.20.22                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                                         Restricted Linux modules for generic kernels
```

**LSPCI:**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub [8086:2a10] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a13] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562GT 10/100 Network Connection [8086:10c4] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
```

**UNAME:**
```
Linux lapsteef 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
```

However, I sadly still suffer the NetworkManager problem with WiFi and WEP. It refuses to connect to WEP encrypted access points, though this is unrelated to this driver. 

I am able to connect to my access point using iwconfig.

This being hardy-proposed, am I to understand that these will eventually enter hardy via a kernell update?

Sidenote: it's created under "eth1" leaving all the network monitor applet confused about the connection, saying it's disconnected. I am able to connect to access points with no encryption via NetworkManager. No WPA access points here to test.

Final note: blacklisting ssb, which seems to be a requirement of the driver, disables my wired interface?

Extra Final note: I've tried compiling the driver from source against the latest stable hardy repository kernell - no joy.

---

### Post by tjwilli on 2008-08-09
YES!!! thank you! thank you! thank you!

Is it safe to apply the updates now? (17 available right now.)

tim@linux-loft:~$ uname -a
Linux linux-loft 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
tim@linux-loft:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] [1106:3099]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] [1106:b099]
00:08.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:08.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:08.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:08.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)
00:08.4 FireWire (IEEE 1394) [0c00]: ALi Corporation M5253 P1394 OHCI 1.1 Controller [10b9:5253]
00:09.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
00:0a.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
00:0b.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7890] (rev 02)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233 PCI to ISA Bridge [1106:3074]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.4 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL AGP 2X [1002:474d] (rev 27)
tim@linux-loft:~$ uname -a
Linux linux-loft 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
tim@linux-loft:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] [1106:3099]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] [1106:b099]
00:08.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:08.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:08.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:08.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)
00:08.4 FireWire (IEEE 1394) [0c00]: ALi Corporation M5253 P1394 OHCI 1.1 Controller [10b9:5253]
00:09.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
00:0a.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
00:0b.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7890] (rev 02)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233 PCI to ISA Bridge [1106:3074]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.4 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1b)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL AGP 2X [1002:474d] (rev 27)
tim@linux-loft:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels
tim@linux-loft:~$

---

### Post by tjwilli on 2008-08-09
One thing I forgot to mention is that I needed to refer to my wireless as eth1 instead of wlan0.

---

### Post by Ayuthia on 2008-08-09
> **ThaRabbit said:**
> 
**LSPCI:**
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82562GT 10/100 Network Connection [8086:10c4] (rev 03)
```


Final note: blacklisting ssb, which seems to be a requirement of the driver, disables my wired interface?
As far as I know, the ssb rule is no different than the ndiswrapper rule.  It just can't be loaded before the wl driver.  However, I don't think that the Intel card uses ssb either.  You can check lshw -C network and see what driver your wired card uses, remove the driver, then load it back along with ssb just to see if it works.

---

### Post by B.C. on 2008-08-10
Does this allow for monitor mode on Broadcom cards? I have a Broadcom BCM4322  802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

It seems to work fine connecting to my wireless network in managed mode, but when attempting to set monitor mode I get the following error: 
> 
$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

Doing a "sudo iwconfig eth1" shows the following:

> eth1      IEEE 802.11abgn  ESSID:"XXXXXX"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-41 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


---

### Post by jinksys on 2008-08-11
**Working:**[COLOR="Red"]NO[/COLOR]

I did the steps you outlined, but no wireless modules were loaded.

**LSCPI -NN**
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
05:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
05:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
05:09.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
```

---

### Post by dhega on 2008-08-11
Linux sebzombie-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

```

00:00.0 RAM memory [0500]: nVidia Corporation MCP65 Memory Controller [10de:0444] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP65 LPC Bridge [10de:0442] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP65 SMBus [10de:0446] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP65 SMU [10de:0447] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0454] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0455] (rev a3)
00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
00:07.0 Audio device [0403]: nVidia Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP65 IDE [10de:0448] (rev a1)
00:0a.0 IDE interface [0101]: nVidia Corporation MCP65 SATA Controller [10de:045d] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:045b] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:045a] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0458] (rev a1)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0459] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)


```

```
ii  linux-restricted-modules                   2.6.24.20.22                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-17-generic 2.6.24.12-17.36                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                                         Restricted Linux modules for generic kernels

```


Worked for me on a HP 6540 laptop, with WPA-PERSONAL
I did a TPtest with the b43 driver and the results were:  10mbit down 6mbit up.

With WL driver i got 10mbit down 10mbit up.

My connection should give about 23-24mbit down so there is still a little way to go!

---

### Post by rizitis on 2008-08-11
**tjwilli**> 00:09.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

Bravo!!!

 Its the first time that bcm 4329 works with out ndiswrapper

[http://ubuntuforums.org/showthread.php?p=5031396#post5031396](http://ubuntuforums.org/showthread.php?p=5031396#post5031396)
[http://ubuntu.opengr.net/viewtopic.php?f=9&t=773](http://ubuntu.opengr.net/viewtopic.php?f=9&t=773)

---

### Post by funnypanks on 2008-08-11
worked here
thanks so much:guitar:
ii  linux-restricted-modules                   2.6.24.20.22                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                                         Restricted Linux modules for generic kernels

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux

additional note: the card is the dell 1490

---

### Post by antm88 on 2008-08-11
Using:
Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

It worked seemingly OK for me, I can connect to the internet and network etc. but now I can't connect to either VNC or SSH :(

Can anyone else confirm if this is not just me or otherwise please!

when I connect to a freshly installed openssh-server with a freshly installed openssh-client on my network i get prompted for a password and then it just hangs...

---

### Post by funnypanks on 2008-08-12
> **antm88 said:**
> Using:
Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

It worked seemingly OK for me, I can connect to the internet and network etc. but now I can't connect to either VNC or SSH :(

Can anyone else confirm if this is not just me or otherwise please!

when I connect to a freshly installed openssh-server with a freshly installed openssh-client on my network i get prompted for a password and then it just hangs...

well i just checked and i can't seem to get samba working either, it doesn't see any workgroups now

---

### Post by Ayuthia on 2008-08-12
> **funnypanks said:**
> well i just checked and i can't seem to get samba working either, it doesn't see any workgroups nowAre you able to ping the workgroup?  Samba seems to be fine on mine.

---

### Post by iliadav on 2008-08-12
worked well, thanks a lot!

Linux cartman 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels

---

### Post by dorea on 2008-08-13
WOrked.
THANK YOU! I have been trying to fix this for a couple of weeks!

Linux dorea-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
07:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 01)
08:04.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
08:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
```

```
ii  linux-restricted-modules                   2.6.24.20.22                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.20.22                             Restricted Linux modules for generic kernels

```

---

### Post by funnypanks on 2008-08-13
> **Ayuthia said:**
> Are you able to ping the workgroup?  Samba seems to be fine on mine.

despite rebooting both the windows machine and ubuntu machine twice yesterday it didnt work, today i boot up and i can see the vista machine from my laptop. woohoo... this driver works amazingly well. ndiswrapper used to take like 30seconds to connect, this takes like 1

---

### Post by balaji.ramasubramanian on 2008-08-13
Hi superm1,

I have a weird problem and I have been trying to get this fixed for a very long while now.

I have a HP Compaq Preseario V 6102AU and it ran Hardy and Wireless perfectly till about two weeks back. One of the problems in the sleep/wireless issues has driven me finally to the point that I reinstall Hardy from scratch. Now, when I do this, even lspci is not detecting my Broadcom Wireless adapater. It used to do so earlier.

I tried your steps above and tried installing the next kernel version, but it is not working. Earlier the wireless adapater was listed in the Restricted drivers list that comes up.

In fact it screwed my resolutions so bad that I decided to re-install Hardy again. I have reinstalled Hardy two times today. What is really wrong. It worked with Wireless access just two weeks back.

Thanks,
Balaji

---

### Post by Beltic on 2008-08-15
I have my Dell Precision M-90 (Broadcom 43xx) working with ndiswrapper. Works great except for - I cant seem to get the system to remember/save my network settings for a WPA-Enterprise SSID. 

We have 2 networks via wireless here, one public (no security) and a WPA Enterprise (peap/tkip). If I manually add the secured SSID, it will work, but if I reboot, i loose those settings and have to re-add them manually.

Any fix, or am i missing something?

(ubuntu hardy, gnome, using nm-applet 0.6.6)
thanks!

---

### Post by Ayuthia on 2008-08-15
> **Beltic said:**
> I have my Dell Precision M-90 (Broadcom 43xx) working with ndiswrapper. Works great except for - I cant seem to get the system to remember/save my network settings for a WPA-Enterprise SSID. 

We have 2 networks via wireless here, one public (no security) and a WPA Enterprise (peap/tkip). If I manually add the secured SSID, it will work, but if I reboot, i loose those settings and have to re-add them manually.

Any fix, or am i missing something?

(ubuntu hardy, gnome, using nm-applet 0.6.6)
thanks!

You should create another thread for this one since your issue is with ndiswrapper instead of the wl driver that is being tested in this thread.  You might get better responses there.

---

### Post by Beltic on 2008-08-15
> **Ayuthia said:**
> You should create another thread for this one since your issue is with ndiswrapper instead of the wl driver that is being tested in this thread.  You might get better responses there.

Thanks. Ill do that.

---

### Post by Ayuthia on 2008-08-15
> **balaji.ramasubramanian said:**
> Hi superm1,

I have a weird problem and I have been trying to get this fixed for a very long while now.

I have a HP Compaq Preseario V 6102AU and it ran Hardy and Wireless perfectly till about two weeks back. One of the problems in the sleep/wireless issues has driven me finally to the point that I reinstall Hardy from scratch. Now, when I do this, even lspci is not detecting my Broadcom Wireless adapater. It used to do so earlier.

I tried your steps above and tried installing the next kernel version, but it is not working. Earlier the wireless adapater was listed in the Restricted drivers list that comes up.

In fact it screwed my resolutions so bad that I decided to re-install Hardy again. I have reinstalled Hardy two times today. What is really wrong. It worked with Wireless access just two weeks back.

Thanks,
Balaji

If lspci is no longer showing your wireless card, you might have a hardware problem.  I know that HP is having some problems with the motherboard on their laptops.  One of the symptoms is that the wireless card is no longer detected.  You might check out this link:
[http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1179013)

---

### Post by olingern on 2008-08-16
Hey, Thanks so much for the post I've been at this for days. This worked great on my Dell D830 which was sporting a Broadcom 4312
    
**Worked:** Yes
**uname-a:**Linux comp 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
**lspci -nn**
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 140M [10de:0429] (rev a1)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

```

**dpkg -l | grep linux-restricted**
```
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.47                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

```

Thx again!

---

### Post by johnnyresponsible on 2008-08-16
Worked: no

Admittedly, I might have messed up on step #2, deactivating ndiswrapper drivers.  But I don't think I had any active to begin with.

Thanks anyway!

Requested info:

Linux 7Eleven 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux

00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
02:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)

00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
02:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)

---

### Post by crazybilly on 2008-08-17
Unfortunately, I can't use ssh or vnc, either, on my Acer Extensa 4420. But my wireless worked before I tried this, with the same problems. 

**Uname: **

Linux jakeslaptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux

**lspci: **

```
Linux jakeslaptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
jaket@jakeslaptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0b:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller [1217:7136] (rev 01)
0b:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0b:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
0b:06.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)

```

**Linux:**

```
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.47                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
```

---

### Post by cycleguy on 2008-08-17
HP Pavilion dv6436nr, Broadcomm bcm4311 rev2.  This seems to work very well for me.  I was having problems with the b43 driver; the connection with my WAP (across the room) was very slow and the connection would frequently go numb, forcing me to disable/enable wireless to get things going again.  I've not seen any problems since installing the new support and my speed is very good now.

uname:
Linux faramir 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux

lspci:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a
2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa
] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe
] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8
] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9
] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a
2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f
] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e
] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc]
 (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd]
 (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 G
o] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev
 a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev 
a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026
d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026
e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10
de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev 
a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10d
e:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] 
(rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] H
yperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] A
ddress Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] D
RAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] M
iscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [
14e4:4311] (rev 02)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1
180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host
 Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:
0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adap
ter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:
0852] (rev ff)

restricted drivers:
ii  linux-restricted-modules                   2.6.24.21.23                     
        Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                  
        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                  
        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                  
        Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                     
        Restricted Linux modules for generic kernels

---

### Post by funnypanks on 2008-08-18
just wondering if this driver will be integrated into intrepid. this is so much better than b43 & ndiswrapper on my laptop

---

### Post by wtgee on 2008-08-18
Also having problems with ssh connection...

---

### Post by jreikes on 2008-08-18
<never mind...  I think my problem was due to forgetting the blacklist...>

---

### Post by xavi1337 on 2008-08-18
Laptop: Dell XPS M1530, should have paid the extra $10 for the Intel car :)

Worked: YES!!! Nothing else would, i've spent hours on this. Touchpad needs work again though

UName -a:Linux alice 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux

lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)



dpkg -l | grep linux-restricted:
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

---

### Post by Mike Schafir on 2008-08-19
This test did not work for me.  I don't get wireless on my Dell Studio 1535 laptop.  I have the Dell 
Wireless-N card with the bcm4322 chip in it.  This card does work with NDISwrapper installed and the bcmwl5.inf driver.

I am not sure, but I think the system might be trying to use some other driver.  

Here are the particulars for this test.  Synaptic did
download the 2.6.24-21 kernel instead of the -20 kernel indicated in the instructions:

uname -a

Linux schafir-laptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]
01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


dpkg -l | grep linux-restricted

ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

Below is also my lsmod results if that helps:

Module                  Size  Used by
hci_usb                16540  3 
rfcomm                 41744  4 
hidp                   20480  2 
l2cap                  25728  14 rfcomm,hidp
bluetooth              61156  10 hci_usb,rfcomm,hidp,l2cap
ipv6                  267780  12 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
uinput                 10240  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_seq_dummy           4868  0 
snd_hda_intel         344728  2 
fglrx                1555468  27 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_pcm_oss            42144  0 
ndiswrapper           192920  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_rawmidi            25760  1 snd_seq_midi
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                  4736  1 video
snd_timer              24836  2 snd_pcm,snd_seq
sdhci                  19076  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
wmi_acer                9644  0 
mmc_core               51460  1 sdhci
snd                    56996  15 snd_seq_dummy,snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
battery                14212  0 
intel_agp              25492  0 
ac                      6916  0 
agpgart                34760  2 fglrx,intel_agp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  9 
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 32128  0 
hid                    38784  2 hidp,usbhid
ahci                   28548  2 
libata                159344  1 ahci
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  7 hci_usb,uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by matthewbpt on 2008-08-19
Any idea if this is in the intrepid kernel? I'm running intrepid at the mo, how can I test this out in intrepid?

---

### Post by Ayuthia on 2008-08-19
> **matthewbpt said:**
> Any idea if this is in the intrepid kernel? I'm running intrepid at the mo, how can I test this out in intrepid?

I was unable to find it in the intrepid kernel (alpha 4 live CD).  :(

EDIT:
I take back what I said.  It is there.  I found the info in a bug report in launchpad (forgot to keep the link), but you need to do the following to get it started:
sudo /etc/init.d/linux-restricted-modules-common start
sudo depmod -a
modprobe wl

The report says that you only have to do it once and then the system will take care of itself.

---

### Post by Ayuthia on 2008-08-19
> **Mike Schafir said:**
> This test did not work for me.  I don't get wireless on my Dell Studio 1535 laptop.  I have the Dell 
Wireless-N card with the bcm4322 chip in it.  This card does work with NDISwrapper installed and the bcmwl5.inf driver.

I am not sure, but I think the system might be trying to use some other driver.  

Here are the particulars for this test.  Synaptic did
download the 2.6.24-21 kernel instead of the -20 kernel indicated in the instructions:

uname -a

Linux schafir-laptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]
01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


dpkg -l | grep linux-restricted

ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

Below is also my lsmod results if that helps:

Module                  Size  Used by
hci_usb                16540  3 
rfcomm                 41744  4 
hidp                   20480  2 
l2cap                  25728  14 rfcomm,hidp
bluetooth              61156  10 hci_usb,rfcomm,hidp,l2cap
ipv6                  267780  12 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
uinput                 10240  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_seq_dummy           4868  0 
snd_hda_intel         344728  2 
fglrx                1555468  27 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_pcm_oss            42144  0 
ndiswrapper           192920  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_rawmidi            25760  1 snd_seq_midi
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                  4736  1 video
snd_timer              24836  2 snd_pcm,snd_seq
sdhci                  19076  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
wmi_acer                9644  0 
mmc_core               51460  1 sdhci
snd                    56996  15 snd_seq_dummy,snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
battery                14212  0 
intel_agp              25492  0 
ac                      6916  0 
agpgart                34760  2 fglrx,intel_agp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  9 
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 32128  0 
hid                    38784  2 hidp,usbhid
ahci                   28548  2 
libata                159344  1 ahci
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  7 hci_usb,uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

Can we see lsmod and lshw -C network with the wl driver installed?

---

### Post by wtgee on 2008-08-19
> **Ayuthia said:**
> Can we see lsmod and lshw -C network with the wl driver installed?

Everything seems to be fine with my wl driver except I can't ssh to remote networks.  Local networks work fine.

lsmod:

Module                  Size  Used by
nfs                   295728  1 
lockd                  80464  1 nfs
nfs_acl                11904  1 nfs
sunrpc                223208  11 nfs,lockd,nfs_acl
tun                    19332  1 
michael_mic            11008  4 
arc4                   10368  4 
ecb                    11520  4 
crypto_blkcipher       27652  1 ecb
ipv6                  311016  10 
af_packet              28288  4 
binfmt_misc            18444  1 
hci_usb                24476  2 
rfcomm                 49696  2 
l2cap                  31104  9 rfcomm
bluetooth              65956  7 hci_usb,rfcomm,l2cap
ipt_MASQUERADE         11520  1 
iptable_nat            14480  1 
nf_nat                 29080  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      24472  4 iptable_nat,nf_nat
xt_state               10752  1 
nf_conntrack           81296  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             11904  2 
xt_tcpudp              11776  4 
bridge                 64424  0 
kvm                   156904  0 
ppdev                  16648  0 
acpi_cpufreq           16400  1 
cpufreq_powersave      10496  0 
cpufreq_stats          14624  0 
cpufreq_ondemand       16528  1 
freq_table             13952  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      13316  0 
cpufreq_conservative    16392  0 
sbs                    22160  0 
container              12416  0 
sbshc                  14592  1 sbs
iptable_filter         11520  1 
ip_tables              28432  2 iptable_nat,iptable_filter
x_tables               31624  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
sbp2                   31884  0 
parport_pc             43688  0 
lp                     19460  0 
parport                49456  3 ppdev,parport_pc,lp
joydev                 20480  0 
uvcvideo               67592  0 
psmouse                51228  0 
serio_raw              14468  0 
compat_ioctl32         18304  1 uvcvideo
videodev               43648  2 uvcvideo,compat_ioctl32
sdhci                  25348  0 
snd_seq_dummy          11652  0 
v4l1_compat            24452  2 uvcvideo,videodev
ieee80211_crypt_tkip    18048  0 
mmc_core               61920  1 sdhci
snd_seq_oss            41856  0 
wl                   1084736  0 
iTCO_wdt               20560  0 
iTCO_vendor_support    12548  1 iTCO_wdt
snd_seq_midi           15872  0 
snd_rawmidi            33664  1 snd_seq_midi
snd_seq_midi_event     16640  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt        14724  2 ieee80211_crypt_tkip,wl
snd_hda_intel         470328  3 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fglrx                2027444  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                97160  2 snd_hda_intel,snd_pcm_oss
snd_timer              33552  2 snd_seq,snd_pcm
snd                    77896  15 snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore              16544  1 snd
snd_page_alloc         17808  2 snd_hda_intel,snd_pcm
shpchp                 42400  0 
pci_hotplug            38584  1 shpchp
intel_agp              38256  0 
wmi_acer               16964  0 
video                  28692  0 
output                 12032  1 video
button                 15904  0 
battery                21128  0 
ac                     13576  0 
dcdbas                 16688  0 
evdev                  19712  18 
ext3                  147856  1 
jbd                    62504  1 ext3
mbcache                17668  1 ext3
usbhid                 39776  0 
hid                    57152  1 usbhid
sg                     45024  0 
sr_mod                 24516  0 
cdrom                  48808  1 sr_mod
sd_mod                 36928  3 
tg3                   135300  0 
ahci                   38792  2 
ohci1394               40756  0 
ieee1394              109560  2 sbp2,ohci1394
libata                193376  1 ahci
scsi_mod              180088  5 sbp2,sg,sr_mod,sd_mod,libata
dock                   18208  1 libata
ehci_hcd               48268  0 
uhci_hcd               33696  0 
usbcore               170648  6 hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
dm_mirror              27904  0 
dm_log                 19204  1 dm_mirror
dm_snapshot            25416  0 
dm_mod                 71280  3 dm_mirror,dm_log,dm_snapshot
thermal                27040  0 
processor              48320  4 acpi_cpufreq,thermal
fan                    13448  0 
fbcon                  50944  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
uvesafb                37800  0 
cn                     17068  1 uvesafb
fuse                   64448  3 


lshw -C network:

  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:a8:38:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.114 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

---

### Post by crazybilly on 2008-08-19
anybody got any resources/links/alternate solutions or anything yet on the ssh problem?

---

### Post by zggame on 2008-08-20
It works for me. Acer Extensa 5620-4025 Broadcom BCM94311MCG.  It seems to work better than nidiswrapper (gives me higher percentage in nm-applet's "connection information") And it seems more stable.  (ndiswrapper gave me lots of trouble, dropping out, long time to connect, refusing to connect, etc.)

Here is the information

```
Linux tigger-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux

```
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

```
```
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                                         Restricted Linux modules for generic kernels

```

---

### Post by Ayuthia on 2008-08-20
> **crazybilly said:**
> anybody got any resources/links/alternate solutions or anything yet on the ssh problem?

I have created a bug report for it:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/259800](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/259800)

I did try it out on Arch by downloading the wl module from the Broadcom site and it still hangs when you use ssh.  Works fine with the b43 module though.

EDIT:
Mine has been marked as a duplicate so the new link is:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816)

---

### Post by 3dAnim8d on 2008-08-20
Well, I tried it out, and yes it does work, and yet, no it doesn't.  It works in that the driver got my card working.  It senses and picks up the networks that are around and available.  And it allows me to connect to a network (Trying with both the network tools that come on the OS as well as with wifi-radar).

The problem is that it doesn't really allow me to connect to the network.  If I try going to the internet or to the package manager, it doesn't work.  It doesn't really seem to keep me connected to the network, either.  The wireless network I have here at the house requires a password to get on, and when I try using it, it'll bring up the password window every 15-20 seconds or so.  So it seems like it's constantly kicking me off and trying to log me back on.  Also, when I try using wifi-radar to connect, it'll search for the IP address, but it'll bring back none.  I've tried putting that information in manually (as copied over from Windows Vista), but it still doesn't get me anywhere.

I've been working on this problem for a few days now, so any help would be appreciated.  Quite possibly this isn't a problem with the driver, but with something else.  But, I'm new to Linux so I really don't know.

My computer is a Dell Studio 17.
My wifi card is a Broadcom BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Thanks in advance.

---

### Post by tymek666 on 2008-08-20
**Worked**: No
Laptop : HP 2570US
Output:
Linux kuba-laptop 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux

00:00.0 Host bridge [0600]: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] [1002:cbb2] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 340M] [1002:7010]
00:06.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Modem [0703]: ALi Corporation M5457 AC'97 Modem Controller [10b9:5457]
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
00:0a.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
00:0b.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:0b.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:0b.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 51)
00:0c.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon IGP 330M/340M/350M [1002:4337]

ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-386     2.6.24.14-20.46                          Non-free Linux 2.6.24 modules on 386
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                             Restricted Linux modules for generic kernels

---

### Post by TheBlackNoodle on 2008-08-21
**Worked:** Yes
**Laptop:** HP Pavilion dv9700us
**Card:** BCM4328
**Comments:** This worked wonderfully for me, as long as I don't put the laptop to sleep or switch off the wireless antenna. I noticed that switching it off and back on freezes everything, and I need to hard boot.

uname -a
```
Linux schnum-laptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux
```

lspci -nn
```
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```

dpkg -l | grep linux-restricted
```
ii  linux-restricted-modules                   2.6.24.21.23                                               Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.47                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.47                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                               Restricted Linux modules for generic kernels
```

---

### Post by crazybilly on 2008-08-21
just to update...I was having ssh/vnc problems. For a variety of reasons I don't want to go into (for the sake of my pride ;)), I ended up reinstalling Hardy.  I installed all the updates on the first boot without enabling any extra repos. 

Then rebooted. The restricted driver manager installed the wl driver. And this time around, it worked out of the box.  

Unfortunately, I don't have any advice about why it worked this time or what anybody else might do besides reinstalling. 

Here's the 2nd time around:

```
Linux jakeslaptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
  
```

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0b:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller [1217:7136] (rev 01)
0b:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0b:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
0b:06.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)

```

```
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                                         Restricted Linux modules for generic kernels

```

---

### Post by balaji.s on 2008-08-22
Hi

do this

#apt-get install b43-fwcutter


then restart your network.

---

### Post by cjtenny on 2008-08-22
Thanks!  It worked.

uname -a
```

Linux blueberry 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux

```

lspci -nn
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```

dpkg -l | grep linux-restricted
```

ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.44                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.44                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

---

### Post by jarome on 2008-08-22
> **superm1 said:**
> Hi Everyone:

In an effort to get an idea how a new driver that is being introduced to hardy is working out, I'd like to make a small call for testing.


It failed for me, if I made the broadcom drivers properly. Their instructions were a little obscure.

Here is the data you asked for:

root@jarhp:/home/jar# uname -a
Linux jarhp 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
root@jarhp:/home/jar# lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:0364]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:1364]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:2364]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:3364]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:4364]
00:00.5 PIC [0800]: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller [1106:5364]
00:00.6 Host bridge [0600]: VIA Technologies, Inc. P4M900 Security Device [1106:6364]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:7364]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198]
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller [1106:a364] (rev 80)
00:03.0 PCI bridge [0604]: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller [1106:c364] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. Unknown device [1106:5372]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 90)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237S PCI to ISA Bridge [1106:3372]
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e]
00:13.0 Host bridge [0600]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a]
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. Chrome9 HC IGP [1106:3371] (rev 01)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
07:03.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
80:01.0 Audio device [0403]: VIA Technologies, Inc. VIA High Definition Audio Controller [1106:3288] (rev 10)
root@jarhp:/home/jar# dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                                               Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                               Restricted Linux modules for generic kernels

---

### Post by XxLeekxX on 2008-08-23
Worked: Yes and No
**EDIT** Now it works.  This doesn't make much sense but I'll state it anyway.  I restarted my computer again and I toggled the wi-fi catcher. Hopefully I won't be bothered anymore by broadcom.  Thank you so much!
Laptop : Dell Studio 17
Network Card: BCM4322 

My driver is now detected, but each time I enter my wep key the connection just hangs.  It always says *Waiting for Network Key for wireless network*.  It does this for a while and then asks me to enter the wep key once again.  Forgive me if I can't realize a simple solution for this.  This is my first time using Linux, meaning I'm completely  newb.

**uname -a**

```
Linux andrew-laptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
```

**lspci -nn**

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3650 [1002:9591]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
```
[B]
dpkg -l | grep linux-restricted[/B]

```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
```

---

### Post by dkronst on 2008-08-23
Laptop: Dell INSPIRON 630m
Working: No :(
Card: BCM4318

lshw -C networking:
```
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:63:41:4d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.89 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
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
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vnet0
       serial: ca:2e:a4:3d:cf:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes

```
lspci -nn:
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
02:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
02:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
02:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```
uname -a:
```
Linux wolf 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
```
dpkg -l | grep linux-restricted:
```
ii  linux-restricted-modules                   2.6.24.21.23                       Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-17-generic 2.6.24.12-17.36                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                       Restricted Linux modules for generic kernels

```

---

### Post by jarome on 2008-08-23
> **superm1 said:**
> Hi Everyone:
ee how things are working.

--------
If this doesn't work for you and you want to revert back, follow these steps.
1) Boot into the old kernel.
At the screen "PRESS ESC to open boot menu", press escape.  select your old kernel.

2) Open up synaptic.
Remove linux-image-2.6.24-20-generic

3) Remove /etc/modprobe.d/blacklist-bcm43
```
sudo rm -rf /etc/modprobe.d/blacklist-bcm43
```4) Update your initramfs
```
sudo update-initramfs -u
```------
**Known issues:**
1) SSH via NAT appears to not be working.  Please see this bug for more information: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816)
2) If you have an ethernet driver supported by ssb/b44, you may run into issues.

I tried to remove this, but the startup menu still lists the .21 kernel which is the default. How do I fix this in Ubuntu?

---

### Post by cascagrossa on 2008-08-24
**worked:** yes
**uname -a:** Linux cerebro 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
**lspci -nn:**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```

**dpkg -l | grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.21.23    Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48 Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48 Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23    Restricted Linux modules for generic kernels

```

**Laptop:** HP Pavilion dv2240br
**encription:** WPA-PSK (WPA-1)
**Range:** dont have exact mesures, but much better than b43 or ndiswrapper

**Comments:**
Using Kubuntu, upgraded from gusty
Interface name changed from wlan0 to eth1(persistent net rules automactically updated)
knetworkmanager conects faster than when using ndiswrapper
Didnt test suspend/resume, will edit post when tested
Modules not needed for machine to run: b44, ssb
SSH not tested.
Home network, internet access only (NAT)

**EDIT:**
Suspend/resume works

**dmesg | grep wl:**
```
[   24.447393] wl: module license 'unspecified' taints kernel.
```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
```

**iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
```

---

### Post by zggame on 2008-08-27
I am using this with ubuntu 2.6.24-20/21.  It works just fine with my WPA network at home, as well as the normal insecure network.  But it does not work with **WPA2** in my school.  "nm-applet" keeps connecting by default. Then  I try to force the connection by left-click the wpa2 connection in the nm-applet.  A windows will pop up for the key, after I enter it, **the laptop freezes in a few seconds. ** I have to reboot.  This happens both in 2.6.24-20 or 21.  

I am using Ubuntu 8.0.4 on Acer Extensa 5620Z (broadcom BCM 94311MCG).  ( I did exactly as the first posts says.)

---

### Post by superm1 on 2008-08-27
> **zggame said:**
> I am using this with ubuntu 2.6.24-20/21.  It works just fine with my WPA network at home, as well as the normal insecure network.  But it does not work with **WPA2** in my school.  "nm-applet" keeps connecting by default. Then  I try to force the connection by left-click the wpa2 connection in the nm-applet.  A windows will pop up for the key, after I enter it, **the laptop freezes in a few seconds. ** I have to reboot.  This happens both in 2.6.24-20 or 21.  

I am using Ubuntu 8.0.4 on Acer Extensa 5620Z (broadcom BCM 94311MCG).  ( I did exactly as the first posts says.)
Would you mind elaborating on this freeze?  WPA2 w/ what type of access point and what kind of encryption.  I'm suspecting a bug here.  Can you enter one into launchpad?

---

### Post by smalldog on 2008-08-28
> **cascagrossa said:**
> **worked:** yes
**uname -a:** Linux cerebro 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
**lspci -nn:**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

```

**dpkg -l | grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.21.23    Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48 Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48 Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23    Restricted Linux modules for generic kernels

```

**Laptop:** HP Pavilion dv2240br
**encription:** WPA-PSK (WPA-1)
**Range:** dont have exact mesures, but much better than b43 or ndiswrapper

**Comments:**
Using Kubuntu, upgraded from gusty
Interface name changed from wlan0 to eth1(persistent net rules automactically updated)
knetworkmanager conects faster than when using ndiswrapper
Didnt test suspend/resume, will edit post when tested
Modules not needed for machine to run: b44, ssb
SSH not tested.
Home network, internet access only (NAT)

**EDIT:**
Suspend/resume works

**dmesg | grep wl:**
```
[   24.447393] wl: module license 'unspecified' taints kernel.
```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
```

**iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
```

Run all command under privilege mode i.e. root user. In addition, try ssh connect with putty instead of native ssh-client. Good luck

---

### Post by smalldog on 2008-08-28
> **zggame said:**
> I am using this with ubuntu 2.6.24-20/21.  It works just fine with my WPA network at home, as well as the normal insecure network.  But it does not work with **WPA2** in my school.  "nm-applet" keeps connecting by default. Then  I try to force the connection by left-click the wpa2 connection in the nm-applet.  A windows will pop up for the key, after I enter it, **the laptop freezes in a few seconds. ** I have to reboot.  This happens both in 2.6.24-20 or 21.  

I am using Ubuntu 8.0.4 on Acer Extensa 5620Z (broadcom BCM 94311MCG).  ( I did exactly as the first posts says.)

You have more luck than me. I can setup my the wireless connection with WPA enabled. The mostly that I have done is using WEP to protect my connection with hidden SSID. Is it necessary disable the hidden SSID on the wireless router? The laptop freeze in a few seconds is due to trying change the wireless connection in progress, you can monitor the wireless transition with command **iwevent**. If the machine stroke during changing wireless configuration, you can restart the NetworkManager manually as "/etc/dbus-1/event.d/25NetworkManager stop & /etc/dbus-1/event.d/26NetworkManagerDispatcher stop" then start it again. Good luck

---

### Post by smalldog on 2008-08-28
It work for me:guitar:

root@king-laptop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:c6:4d:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.42 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:08:cb:f9
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair
root@king-laptop:~# 

root@king-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"MIMO"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:31:B3:59:B0   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:28  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:0   Missed beacon:0

root@king-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:08:cb:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:c6:4d:4c  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62317 errors:0 dropped:0 overruns:0 frame:45102
          TX packets:35576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90746610 (86.5 MB)  TX bytes:3288484 (3.1 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)

root@king-laptop:~#

---

### Post by zggame on 2008-08-28
> **superm1 said:**
> Would you mind elaborating on this freeze?  WPA2 w/ what type of access point and what kind of encryption.  I'm suspecting a bug here.  Can you enter one into launchpad?


I am not sure how to file bugs in launchpad.  And I am not that familiar with all the details in wpa2.  Here is the link for its setup. [http://www.cites.uiuc.edu/wireless/wpa2/index.html]("http://www.cites.uiuc.edu/wireless/wpa2/index.html")   It is a campus-wide network.  I have used it successfully with ndiswrapper before although ndiswrapper works not irregularly recently.

---

### Post by zggame on 2008-08-28
It freezes up the whole system, keyboard, screen and the HD light does not blink any more.  I have to power it down to get back the control.  But yes, it might relate to the change of network.  It just keeps this rotating sigh for "connecting".  Then it freezes after I click the wpa2 in the nm-applet list  and enter the password again.  

> **smalldog said:**
> You have more luck than me. I can setup my the wireless connection with WPA enabled. The mostly that I have done is using WEP to protect my connection with hidden SSID. Is it necessary disable the hidden SSID on the wireless router? The laptop freeze in a few seconds is due to trying change the wireless connection in progress, you can monitor the wireless transition with command **iwevent**. If the machine stroke during changing wireless configuration, you can restart the NetworkManager manually as "/etc/dbus-1/event.d/25NetworkManager stop & /etc/dbus-1/event.d/26NetworkManagerDispatcher stop" then start it again. Good luck

---

### Post by matthewbpt on 2008-08-28
**Worked:**Yes, but only after some tweaking. 
**uname -a:** Linux matthew-laptop 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux
**lspci -nn:**
```
matthew@matthew-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f7] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
05:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce Go 7600] [10de:0398] (rev a1)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
```

**dpkg -l | grep linux-restricted:**
```
matthew@matthew-laptop:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels
```

**Notes:**
I'm happy to say i finally got it to work on my HP Pavillion dv9225us laptop with the 4312 card, but only after some tweaking. Even after following the instructions here and blacklisting, the b43 and ssb modules would load and running "lshw -C network" would show the card using the b43 driver instead of the wl driver. In the end what I did was add the following to the "/etc/rc.local" file:

```
rmmod b43
rmmod ssb
rmmod wl
modprobe wl
```

After doing this and rebooting wireless worked perfectly connecting to a WEP connection, but I think that this issue will have to be solved so that it's automatic, without having to do any editing of system files. I haven't tested it with WPA at all.

---

### Post by cascagrossa on 2008-08-28
> **smalldog said:**
> Run all command under privilege mode i.e. root user. In addition, try ssh connect with putty instead of native ssh-client. Good luck

You are right smalldog, running iwlist and iwconfig using sudo presents all the informations correctly.
But it sounds strange to me, I've never seen a driver that creates a network interface that can only be read by the super user.
About ssh, I can't test it cause I don't have it in my network.

Thank you for the information.

---

### Post by XxLeekxX on 2008-08-30
Is there any way I can have my BCM4322 identified in my dell studio 17 without upgrading kernel?  If I do upgrade to that kernel, my ati driver conflicts with it.

---

### Post by vishalrao on 2008-08-30
***_[COLOR="Purple"]Worked? YES![/COLOR]_*** (on Hardy amd64 with BC 4312!) I could not figure out manual IP but enabling DHCP on my wireless router worked with WPA2 Personal! Too bad I missed this thread for 3 weeks... I am now going to wipe Hardy and test Intrepid with kernel .27 to see how the wireless works there...

uname -a : Linux silverbird 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

lspci -nn:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

dpkg -l | grep linux-restricted:

ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

---

### Post by crazybilly on 2008-08-30
One more update:  I reinstalled Hardy (again), this time from the .iso I downloaded last night, rather than from the cd I recieved via ShipIt.  

My wireless seems to be working fine using the restricted wl driver. On the first install, it worked, but couldn't ssh. On the second install, it worked just fine. This time around, it also seems fine.

Interestingly, where dmesg saw it as a 4312 before, now it's being recognized as a 4315:

```
eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
```

No clue ;)

---

### Post by Yaja on 2008-08-30
I have no idea how or why. but after weeks of my broadcom card randomly not being detected on vista ( one of the reasons i tried to use ubuntu) and days of following a couple of tutorials over and over again and not getting anything to work i uninstalled comodo firewall in vista . guess what? wireless suddenly works fine on both vista and ubuntu. maybe i did something else but i have no idea what it might have been. oh well im happy. :)

---

### Post by jimmgunnz on 2008-08-31
i've definitely been having severe issues with my wireless setup.  broadcom 4311, tried using the b43 driver with the fw cutter, which was disastrous. totally bricked my system. i went through your steps and the blacklisting helped. still have zero wireless though. anyway, here's my output after following your outlined steps....

uname -a
Linux 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

dpkg -l | grep linux-restricted
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

---

### Post by Halbarad on 2008-08-31
The fix works with ASUS Z53H, **but** there are no **kernel headers** for 2.6.24-21-generic. If I try to install them:
```
$ sudo apt-get install build-essential linux-headers-$(uname -r)
```

I get the message:

```
E: Couldn't find package linux-headers-2.6.24-21-generic
```
Perhaps I make some trivial mistake? The kernel headers are important for compiling packages such as alsa-driver etc.
@ Superm1: are the headers going to be released soon?

Sorry, I forgot to post the data you required, here it is:

```

$ uname -a
Linux traveller 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
05:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
05:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)

$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

---

### Post by barlaventoexpert on 2008-09-01
> **Halbarad said:**
> The fix works with ASUS Z53H, **but** there are no more **kernel headers** for 2.6.24-21-generic. If I try to install them I get the message:
```
E: Couldn't find package linux-headers-2.6.24-21-generic
```
Perhaps I make some trivial mistake? The kernel headers are important for compiling packages such as alsa-driver etc.
@ Superm1: are the headers going to be released soon?

I am having similiar problems with my installation and running into the same problems as above.

I upgraded from Gutsy to Hardy last Friday.

I am running 8.0.4 64 bit version. I had months of problems getting my broadcom wifi installation to work properly on Gutsy...Now its happened again! Will probably have to revert to a usb wifi stick. I only use Ubuntu and need my machine for work. However, this problem with wifi drivers for Broadcom is driving me insane.

I tried to follow the instructions for the new driver at the head of this topic but found that linux-headers-2.6.24-21-generic were already installed according to synaptic.

When I tried to run the Makefile from root/superuser as indicated I get the following output:

root@cgkhmobile:~/hybrid_wl# make -C /lib/modules/2.6.24-21-generic/build M=302972
make: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.24-21-generic/302972/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.24-21-generic/302972/Makefile'. Stop.
make: *** [_module_302972] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'

I have posted relevant details of this problem on my blog here:

[http://barlaventositblog.blogspot.com/2008/08/ubuntu-804-hardy-broadcom-wifi-problem.html]("http://barlaventositblog.blogspot.com/2008/08/ubuntu-804-hardy-broadcom-wifi-problem.html")

I would appreciate any advice (Please make it clear and understandable).

Many thanks.

---

### Post by RadioMirchi on 2008-09-01
thanks for the info

---

### Post by revidnus on 2008-09-01
Thanks this worked out very painless. 

I just installed new hard drive and ubuntu Hardy on HP Pavilion 9610us with a BCM4312 802.11a/b/g.

My wireless didn't work right after install as I expected see driver configurations before and after.
Before fix;
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


After fix;
*-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:b8:d1:82
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.220 latency=0 module=wl multicast=yes wireless=IEEE 802.11

Thanks, Philip

---

### Post by Kopiermeister on 2008-09-01
Hello.
Kernel 2.6.24-20 and -21 are in the proposed software-sources. So normally, you should not use it at the moment.
Is there Any Chance to get the wl-driver working with the -19 kernel? wl is not shown in the "restricted driver manager", so i don't know how to install it.

Pls help!

Regards,
Kopiermeister

---

### Post by Ayuthia on 2008-09-02
> **Kopiermeister said:**
> Hello.
Kernel 2.6.24-20 and -21 are in the proposed software-sources. So normally, you should not use it at the moment.
Is there Any Chance to get the wl-driver working with the -19 kernel? wl is not shown in the "restricted driver manager", so i don't know how to install it.

Pls help!

Regards,
Kopiermeister
The wl driver does not work with your card (If I recall correctly, you have a 4312 rev 02) in the -19 kernel.  If you want to try it out, you will need to download the driver from:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
There is a link in there for the readme on how to install the driver.  If you have any problems, you can open another thread and PM me.  I'll try to respond over there.  I say this because this thread is for superm1's testing of the wl driver in linux-restricted-modules and I don't want to confuse others on it unintentionally.

---

### Post by khayden39005 on 2008-09-02
i followed the instructions in this post. the blue light for my wireless card turns on, but my wireless isnt working. im new to linux and think i might not be missing something simple or not doing it right. here is the requested info. please help.
uname-a:
Linux ubuntu 2.6.24-21-rt #1 SMP PREEMPT RT Mon Aug 25 18:23:02 UTC 2008 x86_64 GNU/Linux

lspci -nn:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

dpkg -l | grep linux-restricted:
ii  linux-restricted-modules-2.6.24-19-rt 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-rt 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common       2.6.24.14-21.48                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-rt           2.6.24.21.23                             Restricted Linux modules for rt kernels

---

### Post by falcon61102 on 2008-09-02
What's the results of:
```
sudo lshw -C network
```

---

### Post by Happibun on 2008-09-03
Just followed this on a fresh hardy install on my friend's laptop. Thank you very much, Mwah mwah xx

> mattas@mattas-laptop:~$ uname -a
Linux mattas-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
mattas@mattas-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
mattas@mattas-laptop:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels


---

### Post by falcon61102 on 2008-09-03
Glad it worked for you.

---

### Post by ctopkelly on 2008-09-04
This worked for me.... here is the information you requested
thank you so much

HP DV9925UA
```


@Nebuchadnezzar:~$ uname -a
Linux Nebuchadnezzar 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

@Nebuchadnezzar:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

@Nebuchadnezzar:~$ dpkg -l |grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                       Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.44                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.44                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                       Restricted Linux modules for generic kernels
@Nebuchadnezzar:~$ 


```

---

### Post by joshbrown40 on 2008-09-05
**Working:** Yes
**Laptop;** Dell XPS M1530
**Wireless Card:** Broadcom BCM4310
**Encyption:** WPA with PSK (using Apple Airport Extreme router)

**uname -a**
Linux fire 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

**lspci 0nn**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)
```

**dpkg -l | grep linux-restricted**
```
ii  linux-restricted-modules                   2.6.24.21.23                       Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.44                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.44                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                       Restricted Linux modules for generic kernels
```


Thanks for all your hard work.

---

### Post by khayden39005 on 2008-09-05
this is the output for sudo lshw -C network....

 *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:7f:58:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by rickzoll on 2008-09-07
Worked: No  :confused:

rickpcos@sun:~$ uname -a
Linux sun 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
rickpcos@sun:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
rickpcos@sun:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
rickpcos@sun:~$

---

### Post by Ayuthia on 2008-09-07
> **rickzoll said:**
> Worked: No  :confused:

rickpcos@sun:~$ uname -a
Linux sun 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
rickpcos@sun:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
rickpcos@sun:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
rickpcos@sun:~$

From the Terminal, can you post the results of:
```
lshw -C network
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e wl
```

---

### Post by rickzoll on 2008-09-07
Laptop: dv9620us

rickpcos@sun:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:c6:7b:31
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.100 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
rickpcos@sun:~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e wl
ndiswrapper           192920  0 
usbcore               146412  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,ohci_hcd
rickpcos@sun:~$

---

### Post by Ayuthia on 2008-09-07
> **rickzoll said:**
> Laptop: dv9620us

rickpcos@sun:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:c6:7b:31
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.100 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
rickpcos@sun:~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper -e wl
ndiswrapper           192920  0 
usbcore               146412  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,ohci_hcd
rickpcos@sun:~$

Have you already tried:```

sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
It looks like your wireless card is currently UNCLAIMED so I am guessing that ndiswrapper is not working at the time either.  This set of commands will unload all the possible conflicting modules and load the wl driver and then scan for wireless networks.

---

### Post by muanis on 2008-09-07
Anyone had any look using the new driver with 4318?

---

### Post by outfaller on 2008-09-07
Worked: Yes
uname -a:Linux Compaq 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
lspci -nn
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

```
dpkg -l | grep linux-restricted
```
ii  linux-restricted-modules                   2.6.24.21.23                                Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                             Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                             Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                             Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                             Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                Restricted Linux modules for generic kernels

```

Laptop: Compaq 6210US

Had to load the module manually. Works great other than that. I'm getting faster speeds with this than i ever did with b43 or ndiswrapper.

---

### Post by rickzoll on 2008-09-08
Hi Ayuthia - Your suggestion worked.  The first time I tried to connect it hung and I had to power-off.  After restarting, I applied the commands again and it prompted me quickly for the WPA passphrase and then it connected.  I'm now running wireless :) but I'm not sure how to make the commands you suggested permanent.  Specifically:
[INDENT]sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan[/INDENT]
Thanks, rickzoll

---

### Post by Ayuthia on 2008-09-08
> **rickzoll said:**
> Hi Ayuthia - Your suggestion worked.  The first time I tried to connect it hung and I had to power-off.  After restarting, I applied the commands again and it prompted me quickly for the WPA passphrase and then it connected.  I'm now running wireless :) but I'm not sure how to make the commands you suggested permanent.  Specifically:
[INDENT]sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan[/INDENT]
Thanks, rickzoll

Since ndiswrapper was loaded, you will need to blacklist it:
```
echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist
```
I did not see that the b43, ssb, bcm43xx modules loaded so I am guessing that they are blacklisted.

It also looked like the wl module did not load.  You could try the following to have it load:
```
echo wl | sudo tee -a /etc/modules
```
Hopefully, that is all you need.  If it does not work, please post the results of the following:
```
cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
cat /etc/modules | grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
```

If you are using a script to make ndiswrapper load, you might need to find that script and comment out the commands in them.  Some guides say to use /etc/rc.local and some have a script in /etc/init.d with the name of something like wire.sh.

---

### Post by Sam Lars on 2008-09-08
Wow, this worked!  And I didn't even know it!
I had changed my settings according to the guide, and forgot, until I noticed this:
```
iwconfig
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```
Because my Conky wasn't showing the correct settings, I assumed my interface name had changed.  Sure enough, it did, but it appears to also show the wrong stuff here.
Here's the info you wanted:
```
uname -a
Linux inspiron 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```

```
lspci -nn
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

```
dpkg -l | grep linux-restricted
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48                                        Non-free Linux 2.6.24 modules helper script

```

Connected with no encryption.
Looks like it's detected correctly, and other than the iwconfig it seems to work fine.  I can test it at home later, with some heavier network transfers...

---

### Post by dakjawa on 2008-09-08
Already success install broadcom wireless.. but..

Broadcom wireless speed low 2-5 mb/s.
My laptop Compaq Presario V3753AU and using ubuntu hardy 64bit 8.04 LTS.
My broadcom wireless 54mb/s that built in my laptop working but speed very slow around 2-5 mb/s.

Any method or tweak would help?

---

### Post by gerryl7 on 2008-09-08
all working on dell vistro 1500

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions)

Step 2d: R151517 Driver Download/Extraction

note:-bcmwl6 released...will try later

Big Thanks to all...:popcorn:

---

### Post by Sam Lars on 2008-09-08
I've got more info now... it works great at home with WPA2, same results as before.
While Conky can't get a value for its bar, Network Manager reports a more sane quality, but it's way higher than it was with Ndiswrapper.  It gives me 80% in my room where before it was 50%, and 100% where before I got 60 maybe 80%.
Also, where I used to get maybe 2700 k/s as reported via Conky, it now says about 1800 k/s... Nautilus ends up at 2 MB/s.  But there's no process using a bit of CPU like there was before (ntos_wq?).


Edit: Transmission is not transmitting.
Another Edit: I've updated to Intrepid by now, and somewhere along the way, Transmission started working again.

---

### Post by dakjawa on 2008-09-09
I already install Ndiswrapper. problem is when signal down below than 80% internet will disconnected.Also speed 5mb/s still connected but when 2mb/s it disconneted. is it ok or can we fix it? :confused:

---

### Post by superm1 on 2008-09-09
I'll remind people on this page;

This thread is ***not*** for support. [SIZE=4] 

If your device doesn't work, provide the asked for information, and please open another thread.[/SIZE]

---

### Post by Sam Lars on 2008-09-09
Apologies if this has already been asked/answered, but will this also be included in Intrepid?  I loaded Intrepid, and it didn't "just work."  I had to load Ndiswrapper.  Maybe I missed something?

---

### Post by dontunderstand on 2008-09-10
Works: YES :cool: , thanks a lot :-D!

uname -a: Linux laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

lspci -nn:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

dpkg -l | grep linux-restricted:
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

Computer: HP tx1250eo

---

### Post by hajk on 2008-09-11
I'll be installing Ubuntu 8.10 soon, right now I'm running Debian testing (Lenny) on my MacBook Pro 4,1 (Penryn) with Broadcom 4328 a/b/g/n (rev 05) wireless that wouldn't work with Ndiswrapper together with WPA2 Personal security (it would also not work with Hardy). 

Glad to say that everything works with the wl-driver, including ssh/scp that some are having problems with. The *reported* rated throughput varies between 1-54Mbps, even when I'm downloading at close to the rated speed of my ADSL2+ connection.

The nm-applet disconnects spontaneously after 5-10 minutes of inactivity, but then quickly connects again when traffic resumes -- could this be a battery-saving feature, I wonder? I have it working with the AP (Apple Airport Extreme Base Station) in mixed b/g/n mode in the 2.4GHz band; it also works in pure 802.11n (draft) mode, and in the 5GHz band as well. Yet, the rated speed in the output of "iwconfig"is never above 54Mbps. 

```

henk@mbp:~/setup$ uname -a
Linux mbp 2.6.26-1-amd64 #1 SMP Thu Aug 28 11:13:42 UTC 2008 x86_64 GNU/Linux
```
```

henk@mbp:~/setup$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
0c:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
0d:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 02)
```
```

henk@mbp:~/setup$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 05
       serial: 00:1e:c2:c5:6c:53
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=10.0.1.195 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1f:5b:f7:e8:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.21 firmware=N/A latency=0 module=sky2 multicast=yes
```
```

henk@mbp:~/setup$ lsmod
Module                  Size  Used by
sg                     36448  0 
coretemp               11008  0 
binfmt_misc            13580  1 
nvidia               8105072  26 
rfcomm                 38176  2 
hidp                   19072  3 
l2cap                  23936  18 rfcomm,hidp
ppdev                  11656  0 
parport_pc             31016  0 
lp                     14724  0 
parport                41776  3 ppdev,parport_pc,lp
ipv6                  288200  24 
acpi_cpufreq           11792  1 
cpufreq_userspace       8452  0 
cpufreq_stats           9120  0 
cpufreq_powersave       6400  0 
cpufreq_ondemand       11792  1 
freq_table              9344  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    11784  0 
loop                   19468  0 
snd_pcsp               14588  0 
snd_hda_intel         434776  2 
snd_pcm_oss            41760  0 
snd_pcm                81800  3 snd_pcsp,snd_hda_intel,snd_pcm_oss
snd_mixer_oss          18816  1 snd_pcm_oss
snd_seq_dummy           7428  0 
snd_seq_oss            33152  0 
snd_seq_midi           11072  0 
snd_rawmidi            26784  1 snd_seq_midi
snd_seq_midi_event     11904  2 snd_seq_oss,snd_seq_midi
snd_seq                54304  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25744  2 snd_pcm,snd_seq
snd_seq_device         11668  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55432  0 
ieee80211_crypt_tkip    13184  0 
i2c_i801               13596  0 
compat_ioctl32         12288  1 uvcvideo
snd                    63688  14 snd_pcsp,snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1074624  0 
videodev               35840  2 uvcvideo,compat_ioctl32
hci_usb                18460  3 
ieee80211_crypt        10244  2 ieee80211_crypt_tkip,wl
v4l1_compat            17284  2 uvcvideo,videodev
i2c_core               27936  2 nvidia,i2c_i801
soundcore              12064  1 snd
iTCO_wdt               15696  0 
snd_page_alloc         13072  2 snd_hda_intel,snd_pcm
bluetooth              57124  8 rfcomm,hidp,l2cap,hci_usb
video                  24084  4 
output                  7808  1 video
button                 11680  0 
ac                      9352  0 
battery                16904  0 
intel_agp              31728  0 
evdev                  14208  10 
jfs                   157904  1 
nls_base               12932  1 jfs
usbhid                 45792  0 
hid                    41792  2 hidp,usbhid
ff_memless              9224  1 usbhid
ide_cd_mod             36360  0 
cdrom                  37928  1 ide_cd_mod
sd_mod                 29376  3 
piix                   12424  0 [permanent]
ide_pci_generic         9220  0 [permanent]
ide_core              128284  3 ide_cd_mod,piix,ide_pci_generic
ata_piix               22660  3 
ohci1394               32564  0 
ieee1394               93816  1 ohci1394
ata_generic            10116  0 
libata                165472  2 ata_piix,ata_generic
scsi_mod              160760  3 sg,sd_mod,libata
dock                   14112  1 libata
sky2                   48004  0 
uhci_hcd               25760  0 
ehci_hcd               36108  0 
thermal                22688  0 
processor              42304  4 acpi_cpufreq,thermal
fan                     9352  0 
thermal_sys            17728  4 video,thermal,processor,fan
```
Glad I found this thread, am looking forward to installing Intrepid Ibex with the wl-module!

---

### Post by Metaleks on 2008-09-11
**Working:** Yes.

**Comments:** Works perfectly. However, I get the feeling that this is pretty unstable. Maybe it's just me. On the reboot, after logging in not a whole two minutes had passed and my entire system locked up. The numslock and capslock LEDs were flashing in unison. Everything just froze. After another reboot (forced, this time) I haven't experienced any problems. I'll update this post if this happens again. Other than that, so far it's been smooth sailin'! Keep up the great work!

**uname -a**
```
Linux kingdom 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```

**lspci -nn**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```

**dpkg -l | grep linux-restricted**
```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.49                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
```

---

### Post by thomasio on 2008-09-12
Working : **YES**

Thanks very much for your advice.

Report :

Machine : **HP 6735s**
Wifi model : BCM4322 ( a/b/g/n )

**uname -a**
```
Linux johnny-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```

**lspci -nn**
```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4) [1022:9608]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:4357] (rev 10)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
```

**dpkg -l | grep linux-restricted**
```
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                             Restricted Linux modules for generic kernels
```

---

### Post by EDH1981 on 2008-09-12
Same Problem Here

---

### Post by bwainscott on 2008-09-12
Works with really good signal strength!  Thanks

uname -a Linux bob-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

bob@bob-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)


bob@bob-laptop:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.49                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

---

### Post by MiLoX on 2008-09-13
IT IS WORKING

Linux MiLuXuNTu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
milox@MiLuXuNTu:~/Desktop$ sudo lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro HostAdapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
milox@MiLuXuNTu:~/Desktop$ dpkg -l|grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23          Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.49          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23          Restricted Linux modules for generic kernels

---

### Post by Halbarad on 2008-09-13
Since this thread is **not for support**, I propose to open a new one for discussing freely any trouble, fixes etc. one might have with the Broadcom wireless and with the new driver.
To begin with, I have given my answer to Lars' question about Intrepid.
The thread is:
[http://ubuntuforums.org/showthread.php?p=5782446](http://ubuntuforums.org/showthread.php?p=5782446)

---

### Post by AndrewZorn on 2008-09-13
**Dell XPS M1330**
Works!  BETTER!

```
andrew@lappy:~$ uname -a
Linux lappy 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
andrew@lappy:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
andrew@lappy:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                                               Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.48                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.48                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                               Restricted Linux modules for generic kernels
```

---

### Post by eanbowman on 2008-09-16
Hello, you asked that I post whether or not it's working and what I have.

Dell XPS M1530 with 0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

**NOT WORKING**

I followed your instructions and nothing really seems to have changed functionally. Too bad. This is one of my final barriers to a fully functioning laptop. :|

I had to gzip two of the requested outputs because they were too long for .txt files.

---

### Post by RavUn on 2008-09-16
Thanks!  I was able to detect networks but could not connect to WPA networks, only open networks.  This worked very well:

```
kwatson@rav:~$ uname -a
Linux rav 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

kwatson@rav:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

kwatson@rav:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

---

### Post by Artemis3 on 2008-09-16
Seems to be working on MacBook Santa Rosa 4.1

```
Linux laptop 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
04:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 61)
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

---

### Post by terrypen on 2008-09-17
My Broadcom 4318 wireless is working but when I go to connection information it shows that it is xmitting at 2Mbs and I'm only about 20feet from the AP. How can I tell if it is using the 802.11g instead of b? and if it is using g, how can I speed up the connection?
BTW I am a supernewb with Linux, so go easy on me please.

---

### Post by Sam Lars on 2008-09-17
I've been noticing some problems with my card now.
I still have the weird issue with it dropping the connection at school, and I have to reconnect to get it to work.  It may be related to signal strength, I'm not sure.  I think I had the same thing happen at home at least once.
Also, sometimes when I try reconnecting through Network-Manager, the computer freezes with the caps and scroll lock lights blinking.  I didn't see anything special in syslog or dmesg about it.

---

### Post by Tanisaint on 2008-09-17
**It worked!**
I have a Dell Inspiron E1505 with a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01).  I had tried every single variation of ndiswrapper with every driver I could find.  I could always see the networks but I could *never* connect to a protected network.  I use WPA2 Personal on my router and my laptop had worked great under Windows XP.  However, ndiswrapper would always attempt to make a connection to the router but would never get an IP address. 

I spent hours a night for almost a month on this issue until I found this forum post.  I followed the OP's steps and amazingly it worked and I am able to connect to my router with WPA2 Personal still enabled.  The only oddity is that it shows up as 'eth1' in ifconfig.  But who cares?  It works!  Praise the Ubuntu gods I can finally reclaim the power that Windows XP was stifling for so long.

---

### Post by SwaroopKunduru on 2008-09-17
Please check the info.

It donot work for me?

swaroop@swaroop-desktop:~$ uname -a
Linux swaroop-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

swaroop@swaroop-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
01:05.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)
01:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020]
01:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
01:0b.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7897] (rev 02)


swaroop@swaroop-desktop:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.44                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.44                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                       Restricted Linux modules for generic kernels

---

### Post by rizitis on 2008-09-18
**Worked:Yes**

**uname -a:**
 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-17-generic 2.6.24.12-17.36                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-17-rt      2.6.24.12-17.36                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-18-rt      2.6.24.13-18.41                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-rt      2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-rt      2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels
ii  linux-restricted-modules-rt                2.6.24.21.23                                         Restricted Linux modules for rt kernels

```

**lspci -vv -nn:**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at eff8 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at 6f20 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 6f00 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 0: Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe600000-fe7fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at 6f80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 6f60 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 4: I/O ports at 6f40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: fe500000-fe5fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 220
	Region 0: I/O ports at 6eb0 [size=8]
	Region 1: I/O ports at 6eb8 [size=4]
	Region 2: I/O ports at 6ec0 [size=8]
	Region 3: I/O ports at 6ec8 [size=4]
	Region 4: I/O ports at 6ee0 [size=32]
	Region 5: Memory at fe9fb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe9fb700 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 10c0 [size=32]

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe5fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Dell Unknown device [1028:0229]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at fe5fd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```
 
**Laptop:**Dell Vostro 1700
**Encryption**:WPA2

[COLOR="Red"]**but it works only when I did what**[/COLOR] [**Ayuthia** _say_]("http://ubuntuforums.org/showpost.php?p=5543284&postcount=2") :

> Comments:
The wl driver worked really well, but I have not tested encryption on it yet. I did have to load the module manually though:
Code:

sudo modprobe wl

so I have added it to /etc/modules:
Code:

echo wl|sudo tee -a /etc/modules



---

### Post by muanis on 2008-09-19
HP Compaq 6515b 

Worked here, but authenticating in a WPA2 Enteprise Wifi freezes computer

muanis@muanis-laptop:~$ uname -a
```

Linux muanis-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
```

muanis@muanis-laptop:~$ dpkg -l | grep restricted

```
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels
ii  ubuntu-restricted-extras                   15.2                                                 Commonly used restricted packages

```

muanis@muanis-laptop:~$ lspci -vv -nn
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 64

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d0400000-d05fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c7ffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:04.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7914] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	Memory behind bridge: d0000000-d00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
	I/O behind bridge: 00002000-00003fff
	Memory behind bridge: cc000000-cfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=30, subordinate=30, sec-latency=0
	Memory behind bridge: c8100000-c81fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000c80fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
	Subsystem: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 9000 [size=8]
	Region 1: I/O ports at 9008 [size=4]
	Region 2: I/O ports at 9010 [size=8]
	Region 3: I/O ports at 5018 [size=4]
	Region 4: I/O ports at 5020 [size=16]
	Region 5: Memory at d0609000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d0601000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at d0602000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 19
	Region 0: Memory at d0603000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at d0604000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 19
	Region 0: Memory at d0605000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 18
	Region 0: Memory at d0606000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Region 0: I/O ports at 8200 [size=16]
	Capabilities: <access denied>

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 82 [Master PriP])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 5040 [size=16]

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin ? routed to IRQ 17
	Region 0: Memory at c8200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
	Memory behind bridge: d0100000-d03fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at c0000000 (64-bit, prefetchable) [size=128M]
	Region 2: Memory at d0400000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at 4000 [size=256]
	Region 5: Memory at d0500000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: d4000000-d7fff000 (prefetchable)
	Memory window 1: d8000000-dbfff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at d0101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30c2]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 220
	Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

30:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Hewlett-Packard Company BCM4321 802.11a/b/g/n Wireless LAN Controller [103c:1367]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at c8100000 (64-bit, non-prefetchable) [size=16K]
	Region 2: Memory at c8000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

```

---

### Post by daemen on 2008-09-19
**Working:** No.
**uname -a:** Linux daemen 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
**lspci -nn:** ```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
08:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

```
**dpkg -l | grep linux-restricted:**```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-amd64-generic     2.6.24.21.23                             Upgrade dummy package. Can be removed
ii  linux-restricted-modules-common            2.6.24.14-21.50                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23  

```

Help anyone?

---

### Post by avinash_destiny on 2008-09-21
Its working fine ..
compaq presario v3425au

Linux Avi 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux




lscpi:
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
05:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
05:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
05:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)


ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

---

### Post by metz2112 on 2008-09-22
I've been having a problem getting my wireless working. I tried what was said in this sticky, but it doesn't yet work :confused:
for some reason there is no wlan0 at all - (probably a completely unrelated problem, but please help me out)
**iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

**lshw -C network**
>   *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a5:af:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.103 latency=64 module=ssb multicast=yes

**uname -a**
> Linux metz2112 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

**lspci -vv -nn**(05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01))
> 00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort+ >SERR- <PERR-
	Latency: 64

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37] (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	Memory behind bridge: c0200000-c02fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at 8438 [size=8]
	Region 1: I/O ports at 8454 [size=4]
	Region 2: I/O ports at 8430 [size=8]
	Region 3: I/O ports at 8450 [size=4]
	Region 4: I/O ports at 8400 [size=16]
	Region 5: Memory at c0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at c0005000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at c0006000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at c0007000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at c0008000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at c0009000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at c0004400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Region 0: I/O ports at 8410 [size=16]
	Region 1: Memory at c0004800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 8420 [size=16]

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
	Memory behind bridge: c0300000-c03fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975] (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 255 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 9000 [size=256]
	Region 2: Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at c0300000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at c0302000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
	Subsystem: Dell Unknown device [1028:022a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 9
	Region 0: Memory at c0302400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

**dpkg -l | grep linux-restricted**
> ii  linux-restricted-modules                   2.6.24.21.23                                               Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                               Restricted Linux modules for generic kernels

**Laptop:** Dell Vostro 1000

---

### Post by millz123 on 2008-09-23
well im kinda having the same problem m a newbe at ubuntu like i just installed it on my computer to day well my problem is i can fig out how to work the terminals so that leads to my other problem i have a netgear 54 Mbps wireless usb abapter my problem with it is i got to keep unpluging it or disconnecting it cuz  it will only be online for a lil over 5 mins then it says its online but when i get on foxfire and type in something it wont go there at all it goeas to a grey screen in foxfire where the web site is suspost 2 b and it says its done loading is there any better way of getting a better connection for my usb wireless adapter

---

### Post by ludu900 on 2008-09-23
Hi 
I've been running linux for about 15 minutes and I have no clue what im doing. All i know is that a have the bcm4328 network card and i cannot get on the internet. Can anyone break down some of this stuff in like super noob terms???
THANKS

---

### Post by hajk on 2008-09-23
The recipe is in the very first post of this thread, just start at the beginning and work your way to the end without skipping a step...

Now, if some of the instructions aren't clear to you, why don't you start a new thread, and I'm sure there are enough folks (like myself) who will take the time to walk you through it. But remember, we aren't mind readers, so be specific as to what (part of a) step you don't understand. In the end your 4328 will work, it did on my laptop, so keep at it.

---

### Post by viper77 on 2008-09-23
It worked like a charm for me on latest Intrepid Alpha6, and best of all automatically, but then i had to go back to Hardy because Ati restricted drivers (fglrx) are not working yet at the moment, so i can't manage to get both things working at the same time (yet)...

> **matthewbpt said:**
> Any idea if this is in the intrepid kernel? I'm running intrepid at the mo, how can I test this out in intrepid?

---

### Post by yosemite610 on 2008-09-23
Product: Netgear **WN311B**
Worked: **Yes**
uname -a : Linux homer 2.6.26.5-yosemite #1 SMP PREEMPT Sun Sep 14 16:44:51 EDT 2008 i686 GNU/Linux
lspci -nn (relevant): 02:0b.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

Note: With 2.6.24.21-rt The Broadcom drivers (linked in OP, version 5.10.27.6) worked fine. Followed instructions in README. 

Upgrading to 2.6.26.5 I found the wl module would not load until I manually did a [FONT="Courier New"]insmod wl.ko[/FONT] manually. This is required after every boot (currently) so I've added the command to rc.local and everything seems fine.

---

### Post by viper77 on 2008-09-23
Worked: No
Chipset: 4320SKBG
Model: WIfi MaxG USB adapter (USR5421)
[IMG]http://www.ciudadwireless.com/images/USR805421CW.jpg[/IMG]

Was anyone able to make this dongle work with Hardy?
I already tried everything on this thread but no luck.
It worked perfectly on Intrepid but i had to go back to Hardy for the time being because of fglrx (Ati driver) that is not working yet.
If it worked with Intrepid i guess it should work with these workarounds on Hardy as well, if there's no way then i guess that ndiswrapper will be my only choice for the moment...:(

uname -a: Linux ubuntu 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

lspci -nn:
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] [1106:0305] (rev 03)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] [1106:8305]
00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 40)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1a)
00:07.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 1a)
00:07.4 Bridge [0680]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 40)
00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 50)
00:0e.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AS [Radeon 9550] [1002:4153]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary) [1002:4173]

dpkg -l | grep linux-restricted:
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

lsusb: (just in case)
Bus 001 Device 002: ID 0baf:011b U.S. Robotics

Thanks!
Sebastian

> **superm1 said:**
> Hi Everyone:

In an effort to get an idea how a new driver that is being introduced to hardy is working out, I'd like to make a small call for testing.

This driver is being introduced in hardy, but the GUI to enable it in Jockey is not yet ready.  It should support recent Broadcom A/B/G/N adapters.  As advertised on their site, this means the **4311**, **4312**, **4321**, **4322**, and **4328** adapters. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The Broadcom 4306 has been verified to not work with this.

If you are having trouble w/ b43, or trouble with ndiswrapper please give this a shot.  The more feedback, the better. 


---

### Post by aaamos on 2008-09-25
Wow, after trying out quite a few things in various posts, this one actually worked for me... :)

**System**: Dell Studio 17 with Broadcom BCM4322
```
lspci | grep Broadcom
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```
Chipset:
```
lspci -n | grep '14e4:43'
0c:00.0 0280: 14e4:432b (rev 01)

```

**uname -a**: Linux dingo 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

[B]lspci -nn[B]:
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3650 [1002:9591]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
0d:00.0 Multimedia controller [0480]: Philips Semiconductors Unknown device [1131:7160] (rev 03)

```

**dpkg -l | grep linux-restricted**:
```

ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

---

### Post by rubic on 2008-09-26
Great instructions.  Thanks.  I got everything working on my Acer TravelMate 2480.  Here are the particulars.

jbauer@pico:~$ uname -a
Linux pico 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
jbauer@pico:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
0a:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
jbauer@pico:~$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                                               Generic Linux restricted modules.
rc  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20                                             Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-2.6.20-16-generic 2.6.20.6-16.30                                             Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.10                                             Non-free Linux 2.6.22 modules on x86/x86_64
ii  linux-restricted-modules-2.6.22-15-generic 2.6.22.4-15.11                                             Non-free Linux 2.6.22 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                               Restricted Linux modules for generic kernels

---

### Post by Modax42 on 2008-09-26
Hi there.  This thread helped me tremendously, but I now have a question to ask which will require a long explanation, so please bear with me!  

I first tried out Hardy a month ago on the live CD.  I used an Ethernet connection to get the drivers for my Broadcom 4318 card.  After a lot of fiddling and head scratching, I was able to connect wirelessly.

Now the strange part.  Although it worked on the live CD, when I wiped my windows XP install and installed Ubuntu, it was no longer able to find and install the Broadcom drivers.  I got a glitch where it would continually prompt me to restart my computer, but nothing would change and nothing worked.  So I used the method described in this thread and now my wireless works beautifully.  But why did it work out of the box on the live CD but not the installed version?  Has anyone had a similar experience?

---

### Post by PearlStreet on 2008-09-28
**Worked:** No
**Laptop:** Acer Aspire 3680

```
Linux travis-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

```

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.9                            Non-free Linux 2.6.22 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

Basically I'm not seeing any wireless networks in network manager.  I had to load the wl module manually, and now this is what is shown in lshw -C network:

```
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:19:7e:65:58:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

And just for kicks, here's lsmod:

```
af_packet              23812  2 
ipv6                  267780  8 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ieee80211_crypt_tkip    11648  0 
wl                   1073940  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
sky2                   47620  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
container               5632  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0 
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_7xx1               8576  0 
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                40336  0 
battery                14212  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
button                  9232  0 
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
wmi_acer                9644  1 acer_acpi
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
pcspkr                  4224  0 
evdev                  13056  7 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  2 
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

```

Any thoughts?

---

### Post by ferdaus98 on 2008-09-29
> **superm1 said:**
> Hi Everyone:

In an effort to get an idea how a new driver that is being introduced to hardy is working out, I'd like to make a small call for testing.

This driver is being introduced in hardy, but the GUI to enable it in Jockey is not yet ready.  It should support recent Broadcom A/B/G/N adapters.  As advertised on their site, this means the **4311**, **4312**, **4321**, **4322**, and **4328** adapters. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The Broadcom 4306 has been verified to not work with this.

If you are having trouble w/ b43, or trouble with ndiswrapper please give this a shot.  The more feedback, the better. 

To enable it:

1) Create a blacklist file, /etc/modprobe.d/blacklist-bcm43.  In this file, have these contents:
```
blacklist b43
blacklist ssb
blacklist b43legacy
```2) Deactivate any ndiswrapper installed drivers.  There should be a remove option for ndiswrapper.

3) Update your initramfs
```
sudo update-initramfs -u
```4) Activate Hardy proposed.
Select System->Administration->Software sources.  Check the box for proposed updates.  Hit close and let it refresh.

5) Open up Synaptic.  Search for the package entitled "linux" and mark it for update.  This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.  Perform the updates.

6) Deactivate hardy proposed.
Uncheck that box from Software sources.  Let it reload the sources.  You don't need any of the other updates, and you don't want to risk stability of your system.  

7) Reboot
Things should work on this next boot.  Please report back some feedback.  To be consistent and have good data, please be sure to post the following information with your posts:

[LIST]
[*]uname -a
[*]lspci -nn
[*]dpkg -l | grep linux-restricted
[/LIST]
The GUI to activate isn't ready, and this won't be copied over to hardy-updates until ready, so this is more of an early look for support to see how things are working.

--------
If this doesn't work for you and you want to revert back, follow these steps.
1) Boot into the old kernel.
At the screen "PRESS ESC to open boot menu", press escape.  select your old kernel.

2) Open up synaptic.
Remove linux-image-2.6.24-21-generic

3) Remove /etc/modprobe.d/blacklist-bcm43
```
sudo rm -rf /etc/modprobe.d/blacklist-bcm43
```4) Update your initramfs
```
sudo update-initramfs -u
```------
**Known issues:**
1) SSH via NAT appears to not be working.  Please see this bug for more information: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816)
2) If you have an ethernet driver supported by ssb/b44, you may run into issues.

> **superm1 said:**
> Hi Everyone:

In an effort to get an idea how a new driver that is being introduced to hardy is working out, I'd like to make a small call for testing.

This driver is being introduced in hardy, but the GUI to enable it in Jockey is not yet ready.  It should support recent Broadcom A/B/G/N adapters.  As advertised on their site, this means the **4311**, **4312**, **4321**, **4322**, and **4328** adapters. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The Broadcom 4306 has been verified to not work with this.

If you are having trouble w/ b43, or trouble with ndiswrapper please give this a shot.  The more feedback, the better. 

To enable it:

1) Create a blacklist file, /etc/modprobe.d/blacklist-bcm43.  In this file, have these contents:
```
blacklist b43
blacklist ssb
blacklist b43legacy
```2) Deactivate any ndiswrapper installed drivers.  There should be a remove option for ndiswrapper.

3) Update your initramfs
```
sudo update-initramfs -u
```4) Activate Hardy proposed.
Select System->Administration->Software sources.  Check the box for proposed updates.  Hit close and let it refresh.

5) Open up Synaptic.  Search for the package entitled "linux" and mark it for update.  This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.  Perform the updates.

6) Deactivate hardy proposed.
Uncheck that box from Software sources.  Let it reload the sources.  You don't need any of the other updates, and you don't want to risk stability of your system.  

7) Reboot
Things should work on this next boot.  Please report back some feedback.  To be consistent and have good data, please be sure to post the following information with your posts:

[LIST]
[*]uname -a
[*]lspci -nn
[*]dpkg -l | grep linux-restricted
[/LIST]
The GUI to activate isn't ready, and this won't be copied over to hardy-updates until ready, so this is more of an early look for support to see how things are working.

--------
If this doesn't work for you and you want to revert back, follow these steps.
1) Boot into the old kernel.
At the screen "PRESS ESC to open boot menu", press escape.  select your old kernel.

2) Open up synaptic.
Remove linux-image-2.6.24-21-generic

3) Remove /etc/modprobe.d/blacklist-bcm43
```
sudo rm -rf /etc/modprobe.d/blacklist-bcm43
```4) Update your initramfs
```
sudo update-initramfs -u
```------
**Known issues:**
1) SSH via NAT appears to not be working.  Please see this bug for more information: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816)
2) If you have an ethernet driver supported by ssb/b44, you may run into issues.

Hi
This is Ferdaus
I did this following your article, in HP Pavilion TX1000
[I][COLOR="SeaGreen"]Create a blacklist file, /etc/modprobe.d/blacklist-bcm43. In this file, have these contents:
Code:

blacklist b43
blacklist ssb
blacklist b43legacy[/COLOR][/I]

then I also did the following:-

[I][COLOR="SeaGreen"]Update your initramfs
Code:

sudo update-initramfs -u[/COLOR][/I]

Then I rebooted but no wireless,
After that I decided that the files  "ndisgtk", "ndiswrapper-common" and " ndiswrapper-util 1.9" be installed via **System--> Administration--> Synaptic Application Manager.**
This installed the workaround for windows wireless driver. This can be seen as [B]System-->Administration--> Windows Wireless Driver
[/B]
Download the Windows Broadcom driver for the wireless network card.
Most likely this site [COLOR="SeaGreen"]**[http://h18007.www1.hp.com/support/files/hpcpqnk/us/download/23995.html](http://h18007.www1.hp.com/support/files/hpcpqnk/us/download/23995.html)**[/COLOR]
for 64 bit processor. This site also has 32 bit driver
Then just load the **[COLOR="Red"].inf[/COLOR]** file via [B]System-->Administration--> Windows Wireless Driver
[/B] and reboot the computer to Ubuntu Linux
Let me know at ferdaus98 at netzero dot net

---

### Post by roro100 on 2008-09-29
7) Reboot
Things should work on this next boot.  Please report back some feedback.  To be consistent and have good data, please be sure to post the following information with your posts:

[LIST]
[*]uname -a
[*]lspci -nn
[*]dpkg -l | grep linux-restricted
[/LIST]
======================================

It worked. I just bought Dell Studio 15 from Dell. Installed Hardy. The wireless did not work at first, but after I followed your instructions it worked magically. Thank you very much! 
here are the outputs:

uname -a:
Linux ubl 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 
GNU/Linux

lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]
01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

---

### Post by roro100 on 2008-09-29
minor correction to my previos post: 
the wireless worked at first, i.e. I could see all routers (secured and unsecured). But I could not connect to my WPA secured. Then I followed your instructions and could connect to my WPA-enabled router.

---

### Post by davidaw06 on 2008-09-30
> **superm1 said:**
> Hi Everyone:

In an effort to get an idea how a new driver that is being introduced to hardy is working out, I'd like to make a small call for testing.

This driver is being introduced in hardy, but the GUI to enable it in Jockey is not yet ready.  It should support recent Broadcom A/B/G/N adapters.  As advertised on their site, this means the **4311**, **4312**, **4321**, **4322**, and **4328** adapters. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The Broadcom 4306 has been verified to not work with this.

If you are having trouble w/ b43, or trouble with ndiswrapper please give this a shot.  The more feedback, the better. 

To enable it:

1) Create a blacklist file, /etc/modprobe.d/blacklist-bcm43.  In this file, have these contents:
```
blacklist b43
blacklist ssb
blacklist b43legacy
```2) Deactivate any ndiswrapper installed drivers.  There should be a remove option for ndiswrapper.

3) Update your initramfs
```
sudo update-initramfs -u
```4) Activate Hardy proposed.
Select System->Administration->Software sources.  Check the box for proposed updates.  Hit close and let it refresh.

5) Open up Synaptic.  Search for the package entitled "linux" and mark it for update.  This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.  Perform the updates.

6) Deactivate hardy proposed.
Uncheck that box from Software sources.  Let it reload the sources.  You don't need any of the other updates, and you don't want to risk stability of your system.  

7) Reboot
Things should work on this next boot.  Please report back some feedback.  To be consistent and have good data, please be sure to post the following information with your posts:

[LIST]
[*]uname -a
[*]lspci -nn
[*]dpkg -l | grep linux-restricted
[/LIST]
The GUI to activate isn't ready, and this won't be copied over to hardy-updates until ready, so this is more of an early look for support to see how things are working.

--------
If this doesn't work for you and you want to revert back, follow these steps.
1) Boot into the old kernel.
At the screen "PRESS ESC to open boot menu", press escape.  select your old kernel.

2) Open up synaptic.
Remove linux-image-2.6.24-21-generic

3) Remove /etc/modprobe.d/blacklist-bcm43
```
sudo rm -rf /etc/modprobe.d/blacklist-bcm43
```4) Update your initramfs
```
sudo update-initramfs -u
```------
**Known issues:**
1) SSH via NAT appears to not be working.  Please see this bug for more information: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/259816)
2) If you have an ethernet driver supported by ssb/b44, you may run into issues.

Could someone PLEASE decipher this into something a total Linux newbie can follow?!  I am trying to get WiFi running on Hardy using the Broadcom chipset so this looks like it will work for me but I cannot follow it!!!

---

### Post by Osee on 2008-09-30
First of all i just want to say thank you for the great tutorial.
it work perfect, but now i'm trying to get it to work with wap and aircrack-ng. I cant get it to inject. Please somebody help me, I'm really new when it comes to Linux. 
Thank you, /O

**uname -a**
```
Linux osee-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU
```
**lspci -nn**
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 
```
**dpkg -l | grep linux-restricted**
```
linux-restricted-modules 2.6.24.21.23
linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45
linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50
linux-restricted-modules-common            2.6.24.13-19.45
linux-restricted-modules-generic           2.6.24.21.23
```

---

### Post by keyshawn on 2008-10-01
worked: no 
uname: 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
lspci ```
Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

```dpkg -l | grep linux-restricted: ```
 ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                             Restricted Linux modules for generic kernels

```

---

### Post by sevta on 2008-10-02
Oh man, the same thing happened to me the other day. Same problem, but still no solution. I am pretty desperate, as I really need my Broadcom. I am technically dependent of it workwise. I tried asking around over the Internet, I contacted a tech-frak pal of mine from Germany on a German [portal]("http://www.imedo.de/group/topics/show/58453-wann-habt-ihr-das-erste-mal-davon-gehoert-oder-gelesen"), nothing.. zero... Nobody seems to be able to fix my problem.

---

### Post by carra on 2008-10-02
A huge Thank You.
My Hp Pavilion Tx 1250el (tx1000 series) goes wireless like a charm (chipset "bcm4328").
It would be interesting to know a bit more about this workaround.
Keep up the good work.

carra from Italy


uname -a
```
Linux michele-laptopHP 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```

lspci -nn
```
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```

dpkg -l | grep linux-restricted
```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
```

---

### Post by dunlaphw on 2008-10-02
Did not work:
D800
Data below
dunlaphw@dunlaphw-laptop:~$ uname -a
Linux dunlaphw-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
dunlaphw@dunlaphw-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] [10de:0286] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
02:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
02:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
dunlaphw@dunlaphw-laptop:~$ dpkg -l|grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels


Any other advice???

---

### Post by superm1 on 2008-10-02
> **dunlaphw said:**
> Did not work:
D800
Data below
dunlaphw@dunlaphw-laptop:~$ uname -a
Linux dunlaphw-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
dunlaphw@dunlaphw-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] [10de:0286] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
02:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
02:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
dunlaphw@dunlaphw-laptop:~$ dpkg -l|grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels


Any other advice???
4306 is *NOT* supported.

---

### Post by RedAE102 on 2008-10-02
Worked spectacularly!
System: Acer Extensa 4420-5963, Broadcom 4312 (see notes at bottom)

1) uname -a
```
Linux Tyler9311 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```
2) lspci -nn
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0b:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller [1217:7136] (rev 01)
0b:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0b:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
0b:06.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
```
3) dpkg -l | grep linux-restricted
```
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels
```

Notes: In the old kernel (2.6.24-19), this 4312 card was mistakenly identified as a 4310. lspci | grep Broadcom\ Corporation would return BCM4310 USB, and this wasn't a problem unique to Ubuntu. This laptop originally came with Vista, and Device Manager also identified it as a BCM4310 USB, as does XP, which I am now dual-booting with Hardy. This made it very difficult to obtain drivers. bcm43xx wouldn't work, so I was going to use ndiswrapper, but even then, I couldn't, because I didn't have working drivers for XP for the 4310 USB that it claimed to be. I finally turned the laptop over, and lo and behold, there was a sticker that said it's equipped with BCM94312MCG, and opening it up corroborated this. The most annoying part is that I had to go searching for another laptop model that said it had 4312 to get XP drivers, since neither Acer USA nor Acer EU's driver site has working 4312 drivers available on my laptop's download page.

---

### Post by Big_Kahunaca on 2008-10-03
Works!

HP Pavilion DV6404ca 

uname -a 
```
Linux The-Black-Pearl 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
```

lspci -nn
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
```

dpkg -l | grep linux-restricted
```

ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

Many thanks! Now I don't have to use ndiswrapper!

---

### Post by mistry on 2008-10-07
Kubuntu Dell Studio 15, got the linux_sta driver directly from Broadcom, compiled it, and ran well.  My only issue is connecting to a WPA2 Enterprise access point.  Sometimes I get a kernel panic with the caps lock flashing.  Other times the machine freezes for a few seconds and then becomes responsive again.
[B]
uname -a:[/B]
```
Linux <computer name removed> 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

**lspci -nn**
...
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```
...

**dpkg -l | grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.19.21                                               Generic Linux restricted modules.
rc  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                            Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-16-rt      2.6.24.12-16.34                                            Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                                            Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-18-rt      2.6.24.13-18.41                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-19-rt      2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                                            Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.19.21                                               Restricted Linux modules for generic kernels
```

---

### Post by carra on 2008-10-08
At the moment, upgrading my laptop to 8.10beta breaks support for bcm4328.
Anyone experiencing this problem?
I will step back to 8.04.1 patched as described above...

carra from Italy

---

### Post by matthewbpt on 2008-10-08
Does anyone else have trouble going into suspend after using this driver? Everytime I try suspending i get stuck in a console ending in "Suspending Console(s)."
Also any idea when this will be in the main kernel and no longer just 'proposed'?

---

### Post by alex_kent_18 on 2008-10-08
Hi,

Thanks for the great post.

According to your post, I installed the following packages:
**_linux-image-2.6.24-21-generic_**, **_linux-ubuntu-modules-2.6.24-21-generic_**, and **_linux-restricted-modules-2.6.24-21-generic_** (I didn't select the ubuntu-backports. Would it be the problem?)

However, "Broadcom STA wireless driver" doesn't show up. Please refer to the following screen shot:

[IMG]http://lh4.ggpht.com/alexanderfuture/SO1yxs10i-I/AAAAAAAAALo/zvqWW9Vs-nU/Screenshot-Hardware%20Drivers.jpg[/IMG]

Followings are the details, as requested:

========================================================================
**uname -a**
Linux alexkent-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
========================================================================

**lspci -nn**
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
05:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

========================================================================

**dpkg -l | grep linux-restricted**
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

========================================================================

Please help me figure out the problem. Thank you in advance. 

Anyway, this is a great post and also a great news to Broadcom users. Hope to free from wires and ndiswrappers in the near future.You did a brilliant job! Keep up the good work! :)

I'll be expecting your reply. :)

Best regards,
Alex

---

### Post by superm1 on 2008-10-08
> **alex_kent_18 said:**
> Hi,

Thanks for the great post.

According to your post, I installed the following packages:
**_linux-image-2.6.24-21-generic_**, **_linux-ubuntu-modules-2.6.24-21-generic_**, and **_linux-restricted-modules-2.6.24-21-generic_** (I didn't select the ubuntu-backports. Would it be the problem?)

However, "Broadcom STA wireless driver" doesn't show up. Please refer to the following screen shot:

[IMG]http://lh4.ggpht.com/alexanderfuture/SO1yxs10i-I/AAAAAAAAALo/zvqWW9Vs-nU/Screenshot-Hardware%20Drivers.jpg[/IMG]

Followings are the details, as requested:

========================================================================
**uname -a**
Linux alexkent-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
========================================================================

**lspci -nn**
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
05:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

========================================================================

**dpkg -l | grep linux-restricted**
ii  linux-restricted-modules                   2.6.24.21.23                                         Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-20-generic 2.6.24.14-20.46                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.50                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

========================================================================

Please help me figure out the problem. Thank you in advance. 

Anyway, this is a great post and also a great news to Broadcom users. Hope to free from wires and ndiswrappers in the near future.You did a brilliant job! Keep up the good work! :)

I'll be expecting your reply. :)

Best regards,
Alex
Hi Alex:

This means you haven't updated your version of Jockey.  Please update jockey from -proposed too.

---

### Post by alex_kent_18 on 2008-10-08
> **superm1 said:**
> Hi Alex:

This means you haven't updated your version of Jockey.  Please update jockey from -proposed too.

Hi, 

I did "checked" 'em, **_Jockey-common_** and **_Jockey-gtk_**, for upgrade just now. If it is different from what i am doing, may i know what's the procedure to update it?

Right now, the version of Jockey-common and Jockey-gtk is "**_0.3.3-0ubuntu8.1_**";

Please suggest.

best regards,
alex

---

### Post by jearod on 2008-10-09
Hello all,
I upgraded from 8.04.1 to 8.10 on my Dell Mini 9 last night and then tried this driver today and it works great!
My only issue that is on reboot, there is no wireless card detected and when I go into hardware drivers, it shows Broadcom STA is **activated but not in use**. If I deactivate it and the activate it again, everything is great and it even remembers my AP password.

So I guess my question is how do I set the Broadcom driver to load on boot? 
Thanks

---

### Post by NealCCM on 2008-10-09
Hello All :)
Thanking for this wonderful tutorial.
Before I saw this post, I had downloaded the actual driver from Broadcom & had tested it. It did work well for me.

I tried your way & that also WORKS PERFECTLY.

Here is my Laptop Specs:

Model : HP Compaq 6720s
Memory : 3 GB

uname -a
Linux laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub [8086:2a10] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a13] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562GT 10/100 Network Connection [8086:10c4] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23       Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.50    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23       Restricted Linux modules for generic kernels

once again, thank you so much.

---

### Post by elj4176 on 2008-10-09
> **alex_kent_18 said:**
> Hi, 

I did "checked" 'em, **_Jockey-common_** and **_Jockey-gtk_**, for upgrade just now. If it is different from what i am doing, may i know what's the procedure to update it?

Right now, the version of Jockey-common and Jockey-gtk is "**_0.3.3-0ubuntu8.1_**";

Please suggest.

best regards,
alex

I'm having the same issue. Proposed is checked, linux was updated and so were both jockey packages. Rebooted and no STA in hardware drivers.

---

### Post by bwaslo on 2008-10-09
Worked great for me, thanks Superm1.  I (newbie) was about ready to give up on the WPA issue, maybe now I can get back to figuring out Ubuntu.

---

### Post by tamalatamala on 2008-10-10
I am a total newbie on Kubuntu (I know a bit more about SUSE which I used) so I have a couple of questions regarding the procedure.

I have a broadcom 4322 adapter, Kubuntu 8.04 KDE4 Remix (HP compaq 6735b, AMD Turion). Hopefully the procedure should work for me.

It sais:

1) Deactivate any ndiswrapper installed drivers. There should be a remove option for ndiswrapper.

Should I use Adept to do this? If I open Adept and type ndiswrapper, I get three things, all not installed.

2) Activate Hardy proposed.
Select System->Administration->Software sources. Check the box for proposed updates. Hit close and let it refresh.

How do I select System? Where is that? I can only find System Settings, there is Computer Administration but no Software sources.
Or, I have Applications -> System and no Administration.


3) Open up Synaptic. Search for the package entitled "linux" and mark it for update. This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.

Should I use Adept instead of Synaptic?

4) Search for the package entitled "jockey" and mark it for update. Perform the updates.

All the packages with jockey?

5) Reboot your machine

6) Click System->Administration->Hardware Drivers

I have Applications -> System -> Hardware Drivers Manager which so far has only one device listed (ATI).

7) Click the "Broadcom STA wireless driver" in the Hardware Drivers tool.


I would really appreciate the help to get things started.

---

### Post by superm1 on 2008-10-10
> **tamalatamala said:**
> I am a total newbie on Kubuntu (I know a bit more about SUSE which I used) so I have a couple of questions regarding the procedure.

I have a broadcom 4322 adapter, Kubuntu 8.04 KDE4 Remix (HP compaq 6735b, AMD Turion). Hopefully the procedure should work for me.

It sais:

1) Deactivate any ndiswrapper installed drivers. There should be a remove option for ndiswrapper.

Should I use Adept to do this? If I open Adept and type ndiswrapper, I get three things, all not installed.

2) Activate Hardy proposed.
Select System->Administration->Software sources. Check the box for proposed updates. Hit close and let it refresh.

How do I select System? Where is that? I can only find System Settings, there is Computer Administration but no Software sources.
Or, I have Applications -> System and no Administration.


3) Open up Synaptic. Search for the package entitled "linux" and mark it for update. This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.

Should I use Adept instead of Synaptic?

4) Search for the package entitled "jockey" and mark it for update. Perform the updates.

All the packages with jockey?

5) Reboot your machine

6) Click System->Administration->Hardware Drivers

I have Applications -> System -> Hardware Drivers Manager which so far has only one device listed (ATI).

7) Click the "Broadcom STA wireless driver" in the Hardware Drivers tool.


I would really appreciate the help to get things started.
Sure, using adept is fine.  Make sure you mark the right kernel packages and upgrade the appropriate jockey packages.  You won't see the driver listed UNTIL you are booted in the right kernel package & jockey version

---

### Post by tamalatamala on 2008-10-10
Ok, I managed to get things right.

Adept Manager:
1) Deactivate any ndiswrapper installed drivers. There should be a remove option for ndiswrapper.

2) In Adept Manager's menu, Adept-> Manage Repositories: I selected all under Kubuntu Software and Third-party Software, as well as Pre-release and unsuported updates under Updates

3) In Adept Manager - Search for the package entitled "linux" and mark it for update. This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.

4) Search for the package entitled "jockey" and mark it for update. Perform the updates.

5) Reboot your machine

6) Click Application->System->Hardware Drivers Manager

7) Click the "Broadcom STA wireless driver" in the Hardware Drivers tool.

8 ) Deactivate everything you did in 2) 

9) Reboot

Note that this procedure destroyed my ATI configuration so I had to do it again (cause now we have 2.6.24-21 instead of 2.6.24-19)

---

### Post by tamalatamala on 2008-10-10
**Worked:** Yes
**uname -a:** Linux PrenosnikIrena 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
**lspci -vv -nn:** 

```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI toPCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI toPCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI toPCI bridge (PCIE port 1) [1022:9605]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI toPCI bridge (PCIE port 3) [1022:9607]
00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI toPCI bridge (PCIE port 4) [1022:9608]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC hostcontroller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
09:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
0a:06.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811](rev 70)
```

**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.21.23                      Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.51                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                      Restricted Linux modules for generic kernels
```

**Laptop:** HP compaq 6735b AMD
**Encryption:** WPA

Thanks!

---

### Post by toocer on 2008-10-10
**Worked:** Yes
**uname -a:** Linux ulha-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
**lspci -nn:** 

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

```

**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.50                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.50                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

```

**Laptop:** HP compaq 6715s AMD
**Encryption:** WPA

Thanks!

---

### Post by ytsestef on 2008-10-11
> **yosemite610 said:**
> Product: Netgear **WN311B**
Worked: **Yes**
uname -a : Linux homer 2.6.26.5-yosemite #1 SMP PREEMPT Sun Sep 14 16:44:51 EDT 2008 i686 GNU/Linux
lspci -nn (relevant): 02:0b.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

Note: With 2.6.24.21-rt The Broadcom drivers (linked in OP, version 5.10.27.6) worked fine. Followed instructions in README. 

Upgrading to 2.6.26.5 I found the wl module would not load until I manually did a [FONT="Courier New"]insmod wl.ko[/FONT] manually. This is required after every boot (currently) so I've added the command to rc.local and everything seems fine.

Hey mate, I have the EXACT same wireless adapter and I can't get it working in Interpid Ibex Beta. I used to get it working easily using ndiswrapper in Hardy, but now ndiswrapper reports an alternate driver is used (wl) even if I unload the wl module... Any ideas? Thanks a lot

---

### Post by vanishikawa on 2008-10-11
**Worked: **No
**uname -a:** Linux domenic-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
**lspci -vv -nn:**   0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 4: I/O ports at 6f20 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at 6f00 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 22
	Region 0: Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: f9f00000-f9ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f9c00000-f9efffff
	Prefetchable memory behind bridge: 00000000f0100000-00000000f03fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: f9b00000-f9bfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 4: I/O ports at 6f80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at 6f60 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 22
	Region 4: I/O ports at 6f40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: f9a00000-f9afffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 506
	Region 0: I/O ports at 6eb0 [size=8]
	Region 1: I/O ports at 6eb8 [size=4]
	Region 2: I/O ports at 6ec0 [size=8]
	Region 3: I/O ports at 6ec8 [size=4]
	Region 4: I/O ports at 6ee0 [size=32]
	Region 5: Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at febfb700 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f9aff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at f9aff500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at f9aff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Dell Unknown device [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at f9aff700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Dell XPS M1330 [1028:0209]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 505
	Region 0: Memory at f9bf0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Region 2: Memory at f0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

```

**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.21.23                          Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                       Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                       Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                       Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                          Restricted Linux modules for generic kernels


```

**Laptop:** Dell XPS M1330
**Encryption:** None needed for the connection I use
**Comments:**  I've tried this technique before with two different versions of Ubuntu, actually.  I have the 32 and 64 bit versions installed on separate partitions, because I didn't know which one would be best for my comp. (I have a Core 2 Duo, but the version of Vista I previously used was 32-bit from the factory.)  

I first tried this with the 32 bit, and although the wireless card functioned, numerous other problems developed with both the new and old kernals.  

The above info is from my attempt to do this with the 64-bit version.  The driver does not even show up in the hardware drivers menu, and unlike the 32 bit install, they new kernal is nowhere to be found in GRUB.  It looks like it didn't even install, but the packages are all checked...

Even if no one can help me out, I hope it helps out you Ubuntu guys :)

EDIT:  added wireless card info to top, so you don't have to plow through all that code.  the very last line in that hardware's section says "<access denied>".  probably not important, but just in case

---

### Post by superm1 on 2008-10-11
> **vanishikawa said:**
> **Worked: **No
**uname -a:** Linux domenic-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
**lspci -vv -nn:**   0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
    Latency: 0
    Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-feafffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 20
    Region 4: I/O ports at 6f20 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at 6f00 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin C routed to IRQ 22
    Region 0: Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
    Capabilities: <access denied>

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: f9f00000-f9ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
    Capabilities: <access denied>

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f9c00000-f9efffff
    Prefetchable memory behind bridge: 00000000f0100000-00000000f03fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
    Capabilities: <access denied>

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: f9b00000-f9bfffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
    Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 20
    Region 4: I/O ports at 6f80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at 6f60 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin C routed to IRQ 22
    Region 4: I/O ports at 6f40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: f9a00000-f9afffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin B routed to IRQ 506
    Region 0: I/O ports at 6eb0 [size=8]
    Region 1: I/O ports at 6eb8 [size=4]
    Region 2: I/O ports at 6ec0 [size=8]
    Region 3: I/O ports at 6ec8 [size=4]
    Region 4: I/O ports at 6ee0 [size=32]
    Region 5: Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Interrupt: pin B routed to IRQ 10
    Region 0: Memory at febfb700 (32-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at ef00 [size=128]
    [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
    Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f9aff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 18
    Region 0: Memory at f9aff500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 4
    Region 0: Memory at f9aff600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
    Subsystem: Dell Unknown device [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 4
    Region 0: Memory at f9aff700 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Dell XPS M1330 [1028:0209]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 505
    Region 0: Memory at f9bf0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
    Region 2: Memory at f0000000 (64-bit, prefetchable) [size=1M]
    Capabilities: <access denied>

```**dpkg -l|grep linux-restricted:**
```
ii  linux-restricted-modules                   2.6.24.21.23                          Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                       Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                       Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                       Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                          Restricted Linux modules for generic kernels


```**Laptop:** Dell XPS M1330
**Encryption:** None needed for the connection I use
**Comments:**  I've tried this technique before with two different versions of Ubuntu, actually.  I have the 32 and 64 bit versions installed on separate partitions, because I didn't know which one would be best for my comp. (I have a Core 2 Duo, but the version of Vista I previously used was 32-bit from the factory.)  

I first tried this with the 32 bit, and although the wireless card functioned, numerous other problems developed with both the new and old kernals.  

The above info is from my attempt to do this with the 64-bit version.  The driver does not even show up in the hardware drivers menu, and unlike the 32 bit install, they new kernal is nowhere to be found in GRUB.  It looks like it didn't even install, but the packages are all checked...

Even if no one can help me out, I hope it helps out you Ubuntu guys :)

EDIT:  added wireless card info to top, so you don't have to plow through all that code.  the very last line in that hardware's section says "<access denied>".  probably not important, but just in case
You appear to not be "booted" into the kernel that adds support.  Make sure you boot into it.  It's the -21 kernel.

---

### Post by vanishikawa on 2008-10-11
> **superm1 said:**
> You appear to not be "booted" into the kernel that adds support.  Make sure you boot into it.  It's the -21 kernel.

There's no other option to boot from that kernal for this partition.

My boot options (from GRUB):
2.6.24-21 (for 32 bit version)
2.6.24-19 (32 bit)
Vista/Longhorn
2.6.24.19 (on separate partition, the one I'm running now)

the previous -21 kernal was from when I tried to correct the wireless in the 32 bit version.  It is not the same as the version of Hardy I'm using now.

---

### Post by superm1 on 2008-10-11
> **vanishikawa said:**
> There's no other option to boot from that kernal for this partition.

My boot options (from GRUB):
2.6.24-21 (for 32 bit version)
2.6.24-19 (32 bit)
Vista/Longhorn
2.6.24.19 (on separate partition, the one I'm running now)

the previous -21 kernal was from when I tried to correct the wireless in the 32 bit version.  It is not the same as the version of Hardy I'm using now.
You'll have to hand modify your grub conf to add the extra kernel.  Side effect of the way you are doing this.  If you don't get it working, open up another thread for support.

---

### Post by ludu900 on 2008-10-12
Worked-sort of
Uname-Dont know what that is
dpkg-dont know what that is

Im a complete noob if u can't tell. I followed the instructions and established a wireless connection. It shows the bars and says I am connected to the internet. However, no websites other than google work. Can anyone explain this?

---

### Post by vanishikawa on 2008-10-12
> **superm1 said:**
> You'll have to hand modify your grub conf to add the extra kernel.  Side effect of the way you are doing this.  If you don't get it working, open up another thread for support.

UPDATE:  I fixed the grub menu.lst.  Turns out the grub from the 32 bit install was overriding the 64 bit one, and the 32 bit didn't get the memo about the new kernal.  did a quick sudo gedit and rebooted into the -24 kernal for the 64 bit.

Wireless now works, although I have to go into hardware drivers every time I reboot and re-enable the driver to get it to work.  Luckily, it appears my ethernet still works, which it did not in the 32 bit attempt.

I'm still running in low-graphics mode, so I will look around for help on that.  I'm guessing the kernal upgrade doesn't like my graphics card, go figure.  I'll look around for help or post a new thread for that.

---

### Post by wdaim on 2008-10-13
thank you so much! it worked fine

---

### Post by ARMissel on 2008-10-14
Hey there...

I just installed Kubuntu 8.04 on my new Dell Studio 17 laptop.  After installation (and updating the packages that needed updating), I immediately followed the advice given in this thread, and wireless is now fully functional.  In fact, pretty much everything is working perfectly, which is a pleasant surprise: I've had some trouble in the past with Linux (Debian and OpenSUSE).  There are only two things not working, as far as I can tell, and, although they seem to be common problems, I can't seem to locate solutions that are known to work with my particular hardware.  Since I think--though I certainly don't know this for a fact--that some of the problems may be stemming from using this kernel, and since I'm only booted into this kernel because of the advice given on this thread, I thought I'd post here.  First, though, the requested outputs:

```
uname -a
Linux armissel-LinuxPC 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3650 [1002:9591]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.24.21.23                             Generic Linux restricted modules.
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.45                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels


```

Now for the problems:

1) If I shutdown or restart, everything works fine, but if I try to logout, the system hangs.

2) Sound doesn't work.

Again, these seem to be common problems, so hopefully someone can help me out.  Thanks!

---

### Post by mistry on 2008-10-15
**Worked**: Partially, but UI freezes for a few seconds on WPA2 connect.  Sometimes it results in a kernel panic as Caps Lock LED flashes upon after the UI freeze.
**uname -a**: Linux [computerName] 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
**sudo lspci -vv -nn**: 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
**Laptop model**: Dell Studio 1535
**Comments**: The Broadcom driver I compiled from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .  After continual freezes upon connection to a WPA2 network, I reverted to ndiswrapper with bcmwl5.  Such prevents any freeze of my UI, but at times it cannot connect to an encrypted network.

Kubuntu 8.0.4.1, KDE 3.5.9


```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f6d00000-f6efffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: [88] Subsystem: Dell Unknown device [1028:0254]
        Capabilities: [80] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0300c  Data: 41c1
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 2
                Link: Latency L0s <256ns, L1 <4us
                Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x16
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise-
                Slot: Number 1, PowerLimit 75.000000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
                Slot: AttnInd Off, PwrInd On, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 4: I/O ports at 6f60 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 21
        Region 4: I/O ports at 6f80 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 19
        Region 0: Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x0
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 2, PowerLimit 6.500000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0300c  Data: 41c9
        Capabilities: [90] Subsystem: Dell Unknown device [1028:0254]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f6c00000-f6cfffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
                Link: Latency L0s <256ns, L1 <4us
                Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 3, PowerLimit 6.500000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0300c  Data: 41d1
        Capabilities: [90] Subsystem: Dell Unknown device [1028:0254]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f6a00000-f6bfffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM unknown, Port 4
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x0
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 5, PowerLimit 6.500000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0300c  Data: 41d9
        Capabilities: [90] Subsystem: Dell Unknown device [1028:0254]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        Memory behind bridge: f6900000-f69fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 6
                Link: Latency L0s <256ns, L1 <4us
                Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 3, PowerLimit 6.500000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0300c  Data: 41e1
        Capabilities: [90] Subsystem: Dell Unknown device [1028:0254]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 4: I/O ports at 6f00 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 21
        Region 4: I/O ports at 6f20 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 19
        Region 4: I/O ports at 6f40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f6800000-f68fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [50] Subsystem: Dell Unknown device [1028:0254]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 218
        Region 0: I/O ports at 6e70 [size=8]
        Region 1: I/O ports at 6e78 [size=4]
        Region 2: I/O ports at 6e80 [size=8]
        Region 3: I/O ports at 6e88 [size=4]
        Region 4: I/O ports at 6ea0 [size=32]
        Region 5: Memory at f6ffb800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
                Address: fee0300c  Data: 4142
        Capabilities: [70] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a8] #12 [0010]

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at f6ffb700 (32-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4] (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at ee00 [size=256]
        Region 2: Memory at f6df0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at f6d00000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x16
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000

01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at f6dec000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x16
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f68ff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME+

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at f68ff500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 3
        Region 0: Memory at f68ff600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 3
        Region 0: Memory at f68ff700 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
        Subsystem: Dell Unknown device [1028:0254]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 217
        Region 0: Memory at f69f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [40] Vital Product Data
        Capabilities: [60] Vendor Specific Information
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0300c  Data: 4152
        Capabilities: [cc] Express Endpoint IRQ 0
                Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 4096 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <1us, L1 <64us
                Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
        Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f6cfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [d0] Express Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <4us, L1 <64us
                Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

```

---

### Post by mozart_ar on 2008-10-16
**worked:** yes

**uname -a:** Linux ubuntu 2.6.24-21-server #1 SMP Mon Aug 25 17:28:54 UTC 2008 x86_64 GNU/Linux

**lspci -vv -nn:** 03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
Subsystem: Hewlett-Packard Company BCM4321 802.11a/b/g/n Wireless LAN Controller [103c:1366]

```

00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0

00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 10
	Region 0: I/O ports at 3080 [size=64]
	Region 4: I/O ports at 3040 [size=64]
	Region 5: I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at f2300000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f2586000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at f2589000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f2587000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at f2589400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device [f03c:30cf]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 30c0 [size=16]
	Capabilities: <access denied>

00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f2580000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: f2100000-f21fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 2301
	Region 0: I/O ports at 30f0 [size=8]
	Region 1: I/O ports at 30e4 [size=4]
	Region 2: I/O ports at 30e8 [size=8]
	Region 3: I/O ports at 30e0 [size=4]
	Region 4: I/O ports at 30d0 [size=16]
	Region 5: Memory at f2584000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 2300
	Region 0: Memory at f2588000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 30f8 [size=8]
	Region 2: Memory at f2589c00 (32-bit, non-prefetchable) [size=256]
	Region 3: Memory at f2589800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f2200000-f22fffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f20fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f3000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f2380000 [disabled] [size=128K]
	Capabilities: <access denied>

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at f2100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 7
	Region 0: Memory at f2100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at f2100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at f2101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30cf]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 248, Cache Line Size: 1020 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at f2101400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Hewlett-Packard Company BCM4321 802.11a/b/g/n Wireless LAN Controller [103c:1366]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f2200000 (64-bit, non-prefetchable) [size=16K]
	Region 2: Memory at f2000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

```

**dpkg -l|grep linux-restricted:**
```

rc  linux-restricted-modules-2.6.22-14-xen     2.6.22.4-14.10                                       Non-free Linux 2.6.22 modules on Xen
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.51                                      Non-free Linux 2.6.24 modules helper script

```

**Laptop:** HP Pavilion DV9925NR

Thanks!!

---

### Post by zaleksf on 2008-10-17
I believe you are mistaken about support for the 4328 card. The Broadcom website (your link) indicates support only for the BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware. I attempted to use this restricted driver with my 4328 card with no success. I'm successfully using ndiswrapper. Hopefully support is expanded to other Broadcom cards soon.

Cheers

---

### Post by Ayuthia on 2008-10-17
> **zaleksf said:**
> I believe you are mistaken about support for the 4328 card. The Broadcom website (your link) indicates support only for the BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware. I attempted to use this restricted driver with my 4328 card with no success. I'm successfully using ndiswrapper. Hopefully support is expanded to other Broadcom cards soon.

Cheers

See post #171.  It is a 4328 card.  You might check lspci -nn and see what [14e4:43xx]shows.

---

### Post by zaleksf on 2008-10-17
Worked: Yes - with a slight mod (per comments of post #2) to force auto load=>
    sudo modprobe wl
    echo wl|sudo tee -a /etc/modules

Failure to force this load resulted in the driver indicating it was 'Enabled' but not 'In Use' upon startup

uname -a: Linux zaleksf-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

lspci -vv -nn:
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at 6f20 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 6f00 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 0: Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: f9f00000-f9ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f9c00000-f9efffff
	Prefetchable memory behind bridge: 00000000f0100000-00000000f03fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: f9b00000-f9bfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at 6f80 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 6f60 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 21
	Region 4: I/O ports at 6f40 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: f9a00000-f9afffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device [1028:01f3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 218
	Region 0: I/O ports at 6eb0 [size=8]
	Region 1: I/O ports at 6eb8 [size=4]
	Region 2: I/O ports at 6ec0 [size=8]
	Region 3: I/O ports at 6ec8 [size=4]
	Region 4: I/O ports at 6ee0 [size=32]
	Region 5: Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at febfb700 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device [1028:01f3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f9aff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at f9aff500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Dell Unknown device [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at f9aff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Dell Unknown device [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 4
	Region 0: Memory at f9aff700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 217
	Region 0: Memory at f9bf0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Region 2: Memory at f0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>

dpkg -l|grep linux-restricted:
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                          Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.51                          Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                             Restricted Linux modules for generic kernels

---

### Post by pointfive on 2008-10-17
EDIT: I'm having problems installing this driver. When I follow the instructions in the readme, I get a slew of errors when trying to build the driver.

Calling this: ~/hybrid_wl$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd`

Produces this: 

```
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/pointfive/hybrid_wl/src/wl/sys/wl_iw.o
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c: In function &#8216;wl_iw_get_scan&#8217;:
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
make[1]: *** [/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/pointfive/hybrid_wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

```

I'm a newbie, so I appreciate any insight. Thanks!

This is with the 64-bit download.

---

### Post by superm1 on 2008-10-18
> **pointfive said:**
> EDIT: I'm having problems installing this driver. When I follow the instructions in the readme, I get a slew of errors when trying to build the driver.

Calling this: ~/hybrid_wl$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd`

Produces this: 

```
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/pointfive/hybrid_wl/src/wl/sys/wl_iw.o
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c: In function ‘wl_iw_get_scan’:
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:934: error: too few arguments to function ‘iwe_stream_add_event’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:939: error: too few arguments to function ‘iwe_stream_add_point’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:947: error: too few arguments to function ‘iwe_stream_add_event’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:955: error: too few arguments to function ‘iwe_stream_add_event’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:961: error: too few arguments to function ‘iwe_stream_add_event’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:973: error: too few arguments to function ‘iwe_stream_add_point’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:981: error: too few arguments to function ‘iwe_stream_add_point’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:992: error: too few arguments to function ‘iwe_stream_add_point’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1006: error: too few arguments to function ‘iwe_stream_add_point’
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.c:1016: error: too few arguments to function ‘iwe_stream_add_value’
make[1]: *** [/home/pointfive/hybrid_wl/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/pointfive/hybrid_wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

```I'm a newbie, so I appreciate any insight. Thanks!

This is with the 64-bit download.
This driver is *included* in linux-restricted-modules.  You don't need to manually compile it.

---

### Post by pointfive on 2008-10-18
> **superm1 said:**
> This driver is *included* in linux-restricted-modules.  You don't need to manually compile it.

Ah, thanks superm1. Still getting the hang of all this.

---

### Post by zwon on 2008-10-18
I've updated today driver to STA and found one issue. I use Dell XPS M1330, ubuntu 8.04, amd64, uname -a: Linux xps 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux. 

Driver works fine, actually I'm using it now. But problem with Network Manager. Icon, that shows strength of signal constantly switch between 100% and 0%. So it shows 100% for 10 sec - 1 min, when network icon goes gray for 5-10 sec, and tooltip says it 0%. iwconfig also shows that connection is down. When it shows connection 100% again. But actually network connection is up all time, as downloading speed the same when this happens. So I doesn't experience any network problems, it's just indication.

Any ideas?

---

### Post by phmadore on 2008-10-18
Should this work for the Linksys WPC54GS series PCMCIA cards? I am still getting the updates, but I would appreciate knowing if this is the right direction to go in. I'm tired of sitting on the floor with my new linux box next to my friggin router. Thanks.

---

### Post by Ayuthia on 2008-10-18
> **phmadore said:**
> Should this work for the Linksys WPC54GS series PCMCIA cards? I am still getting the updates, but I would appreciate knowing if this is the right direction to go in. I'm tired of sitting on the floor with my new linux box next to my friggin router. Thanks.

You will need to go into the Terminal and check the results of lspci -nn.  You will have to compare the results with the cards in the first post to see if it is in there.

If I recall correctly the Linksys cards are generally 4306 or 4318.  Neither work with this option.

---

### Post by nicktheninja27 on 2008-10-18
im new to ubuntu and im not sure about installing this.. help?

---

### Post by zwon on 2008-10-19
> **nicktheninja27 said:**
> im new to ubuntu and im not sure about installing this.. help?

My opinion: if your wifi works without it, do not install.

---

### Post by hndaklr8480 on 2008-10-19
hey new ubuntu fam.  I loaded this STA driver and it worked fine for me just little weird FYI i discovered that light on my wifi bottom was on which i thought meant that the card was on but i was wrong for some reason when the light is on the card is actually off and visa versa just something to keep in mind

---

### Post by sergiom99 on 2008-10-19
how can I be sure that I am using the new driver and not the old ndiswrapper driver??
B/c in the restricted driver manager it appears unchecked. I check it an reboot and still unchecked. Any way to tell for sure?

[[IMG]http://img169.imagevenue.com/loc1094/th_59040_snap7_122_1094lo.jpg[/IMG]](http://img169.imagevenue.com/img.php?image=59040_snap7_122_1094lo.jpg)
Linux kubuntu 2.6.24-21-generic
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by sliverman69 on 2008-10-20
I am having a strange problem...maybe I blacklisted the wrong things, but I have been trying to get rid of the b44 ssb whatever and nothing is working...in fact, the STA driver shows up and looks like it will install but after every reboot it won't install.  now, the checkbox won't check for the driver, but it says I need to reboot...my ethernet is not broadcom, so I shouldn't need the b44 driver...also, I have to rmmod the b44 driver and the wl driver before the STA driver will show up in the list of drivers to install with jockey.  Any ideas?

Best regards,
Sliverman69

Edit: card is a bcm4312 rev01

---

### Post by sergiom99 on 2008-10-20
> **sergiom99 said:**
> how can I be sure that I am using the new driver and not the old ndiswrapper driver??
B/c in the restricted driver manager it appears unchecked. I check it an reboot and still unchecked. Any way to tell for sure?

[[IMG]http://img169.imagevenue.com/loc1094/th_59040_snap7_122_1094lo.jpg[/IMG]](http://img169.imagevenue.com/img.php?image=59040_snap7_122_1094lo.jpg)
Linux kubuntu 2.6.24-21-generic
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

also forgot to mention that my wifi network is WPA2 encrypted so if I am using STA and not ndiswrapper I can connect just fine.

---

### Post by ThaRabbit on 2008-10-21
just a quick note:

The latest normal update brought the .21 kernell to stable 8.04. I've removed the ndiswrapper version I had installed and referred to the STA driver... which is working awesomely :D

lspci:
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

---

### Post by _Q_ on 2008-10-22
I found some problems using this driver. Please read about it here:
[http://ubuntuforums.org/showthread.php?p=6011780]("http://ubuntuforums.org/showthread.php?p=6011780")

---

### Post by chamus on 2008-10-25
Hi, i have a compaq f505 and for the last 3 months my card was not working, so y really forget about that problem, but today y start my notebook and Ubuntu tells my that i have some new hardware to install, and there were this two, so i installed them and my card light came blue, yes!! it works! So then i have to reboot, but when i do this, it does not work any longer. I have read that for this compac model it usually have problems in their mother and this put the card out of work, how can i know if it is a hardware or a software problem? How can i know if it is the mother or the card?
Everything else is working perfectly in my notebook, so it would by really fantastic to fix this and have Ubuntu working perfectly!

---

### Post by lswest on 2008-10-25
I have the driver installed and working for a Broadcom BCM4311 (rev 02).  The only issue I have is that I cannot connect to a WPA network (using ndiswrapper it does connect).  I've tried manually to connect using wpa_supplicant, but that also failed.  Anyone have it working with a WPA (TKIP) network?

*UPDATE* Randomly decided to keep connecting a few times using nm-applet, and it now connected (full signal strength too), but it's not the first time it's taken a number of tries to connect (I'm happy it's working at all atm though).

---

### Post by tracey__ on 2008-10-26
I DID have the same problem.. but I got an update through a wired connection for the broadcom.

---

### Post by texas.chef94 on 2008-10-29
I am reluctant to be too short on supplied information as being a newbie I am challenged in number of areas so here goes.
My laptop an hp ze4935wm has wireless capability, but I have no interest in going wireless.
In attempting to explore my file system having just partitioned all the way to extended I attempted to access graphical via ctrl+alt+f2. Got as far as it accepting my username and only 2 characters in PW untill all hell broke loose with direction to linuxwireless.org and filmware version 4.
So for whatever reason it detected my chip without the filmware.
Contacted HP and was told bcm4303 802.11b-only chip, that my unit has uses b43legacy.
Please bear in mind when responding that I do not give a hoot about reasons only some specific steps and solutions. This stance of mine is not an attempt to be a smart A-- merely a 76 year old crying for help that he can understand and effectively utilize.

I will stick with this until it solved and appreciate to no end any and all assistance. Oh by way running ubuntu 8.04 with kubuntu desktop if that is an issue



Thank you so much

Allen

---

### Post by knotphunnie on 2008-10-30
I upgraded to Ibex today. Solved my Broadcom problem. Maybe you will have the same luck as me.

---

### Post by texas.chef94 on 2008-10-31
After reading all the replies after my #192 post I need to thank and extend my question. am adding this after reading all the informative replied and now I want to amend my initial statement _I am interested in going wireless_
because after installing film ware driver 43B and being able to access virtual text my original reason for posting prompts me with extending my capability. Went to XP only because did not know how to do it in linux clicked on connections, clicked on 2 wire and recorded that number under my router and after a few other moves says I am connected 802.11b/g WLAN.
So help the old out one more time. What must I get or do at this point to be fully connected. Because when I remove that blue cabel that connects me to router I realize I am not connected. Oh while in windows and connections I clicked on repair wireless and got something about clearing DNS cache if that means anything. Thanks and anxiously awaiting my next move from this great cast of resource chatacters:lolflag:

Allen

---

### Post by TerryP on 2008-11-08
**Worked:** Yes
**uname -a:** Linux terryp-laptop64X2 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux
**lspci -vv -nn:** 01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
	Region 2: Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 30d0 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at 91100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30d9]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 92400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 91300000-923fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 21
	Region 4: I/O ports at 3080 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at 3060 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 19
	Region 4: I/O ports at 3040 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at 92404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 91200000-912fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 30a0 [size=16]

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 510
	Region 0: I/O ports at 30b8 [size=8]
	Region 1: I/O ports at 30dc [size=4]
	Region 2: I/O ports at 30b0 [size=8]
	Region 3: I/O ports at 30d8 [size=4]
	Region 4: I/O ports at 3020 [size=32]
	Region 5: Memory at 92404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
	Subsystem: Hewlett-Packard Company Presario C700 [103c:30d9]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin D routed to IRQ 11
	Region 0: Memory at 92404c00 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 3000 [size=32]

01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1374]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 91300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device [103c:30d9]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 1000 [size=256]
	Region 1: Memory at 91200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


```

**dpkg -l|grep linux-restricted:**
```
rc  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                                      Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-21.51                                      Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.21.23                                         Restricted Linux modules for generic kernels

```


**lshw -C network:**
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:96:a2:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.0.104 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:83:f8:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

```


**iwconfig:**
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:223  Noise level:158
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```


**Laptop:** HP CompaqC714NR
**Encryption:** WPA
[B]
Comments:[/B]

A great improvement in comparison to using the Broadcom drivers with NDISWrapper.  Wireless connections to my router are now almost instantaneous and the signal strength is much higher.  Wired ethernet also works.        :)


My only concerns are that my wireless interface changed from wlan1 to eth1 -- in conky, I can no longer monitor signal quality, ESSID, and other parameters associated with the wireless interface.  Is there a way to correct this?  Also, iwconfig output above appears to be incorrect/strange.  Can this be safely ingored?

Update:  after using this driver for awhile, like mocho in the following post, I noticed that it sometimes takes awhile for web pages to respond.

---

### Post by mocho on 2008-11-09
hi

for me this driver works and i can but i have some problems 

my laptop is an hp tx1000 with broadcom 4321 abgn mini pci-express

i can connect to wpa2 with no problem but it seems i cant define some or any options 

my big problems is despite i'm in europe i should get 13 channels in b/g band but i only get 11 

**sudo iwlist channel**

> eth1      20 channels in total; available frequencies :
          [COLOR="Red"]Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz[/COLOR]
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Channel:1


despite i've added 

> 
options cfg80211 ieee80211_regdom=EU

to /etc/modprobe.d/options

other problem is 

**sudo iwlist txpower**

> eth1      [COLOR="Blue"]2 available transmit-powers[/COLOR] :
	  [COLOR="Green"]0 dBm  	(1 mW)
	  25 dBm  	(255 mW)[/COLOR]
          [COLOR="Red"]Current Tx-Power:32 dBm  	(1496 mW)[/COLOR]

 
i suspect this is causing another problem that after some time i've been using wireles is sometimes it takes a lot of time to respond when i'm trying to see a web page or for example using synaptics

is there some form i can configure my card and driver to use european channels and set the txpower?

is there any work being done in this driver so we can hope see any improvements in near future ?


regards 
the

---

### Post by mocho on 2008-11-10
the channels issue is defnitly a driver bug maybe caused by adapter bind with eth1 instead of wlan0 

i've tried a pen with realtek RTL8187vB chip and i can see 14 channels 

**iwlist channel**

> wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.472 GHz (Channel 13)

---

### Post by TerryP on 2008-11-10
I'm also having trouble with samba shares.  Think I will try a USB NIC and see if that changes anything.

---

### Post by ZanexGt on 2008-11-27
Thanks!

This driver seems to work great for my Compaq F730US on Intrepid. I have previously run Gutsy/Hardy with the NDISWRAPPER solution for the BCM4311 wifi chipset.

This solution is so much easier!

---

### Post by manij on 2008-11-29
I have a dell vostro 1000 with broadcom 4310 G card

I have Hardy heron and it has been working well with ndiswrapper.

Just one problem. If I try to switch access points I have trouble geting it to connect.

At home I have have Linksys wrt54g and it works fine with that router. 
If I try any other router, all hell breaks loose.

I have tried  a couple of public access points. I have tried an Airlink router at home. no luck with those. I'm able to connect to the Linksys I set this up with no problem!

Does anyone have a solution for this?

Is there a way to monitor signal strength and status in real time?

Also I have btter lluck in ubuntu rather than the knetwork manager. Why is this?

---

### Post by r0t on 2008-12-18
I'm at step 4 and 5 in the readme.txt saying:
```
On the target machine, and cd'ed to the directory that contains the Makefile (fragment)

4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`
```

But here I get a long list of warning messages ending with:
```

make[1]: *** [/home/asa/Desktop/hybrid_wl/src/wl/sys/wl_iw.o] Error 1
make: *** [_module_/home/asa/Desktop/hybrid_wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
```

I'm writing this from another computer (for obvious reasons), so I hope I got it all right.

Thankful for any suggestions about what might have gone wrong.

---

### Post by superm1 on 2008-12-18
There is no need to build it yourself on 8.04.1 or 8.10.  It comes in linux-restricted-modules.

---

### Post by arthurema on 2009-01-20
Worked: yes WEP, not working with WPA/WPA2
uname -a: Linux laptop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
lspci -vv -nn (Broadcom BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01))
code:

```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022
:9600]
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge 
(int gfx) [1022:9602]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 96300000-964fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge 
(PCIE port 0) [1022:9604]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 95200000-962fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge 
(PCIE port 1) [1022:9605]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 94200000-951fffff
	Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge 
(PCIE port 3) [1022:9607]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=06, subordinate=08, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 93200000-941fffff
	Prefetchable memory behind bridge: 0000000092000000-0000000092ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge 
(PCIE port 4) [1022:9608]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: 93100000-931fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller
 [AHCI mode] [1002:4391] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at 6018 [size=8]
	Region 1: I/O ports at 6024 [size=4]
	Region 2: I/O ports at 6010 [size=8]
	Region 3: I/O ports at 6020 [size=4]
	Region 4: I/O ports at 6000 [size=16]
	Region 5: Memory at 96509000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Contro
ller [1002:4397] (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 96508000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [
1002:4398] (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 96507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Control
ler [1002:4396] (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at 96509500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Contro
ller [1002:4397] (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 96506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [
1002:4398] (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 96505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Control
ler [1002:4396] (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at 96509400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (r
ev 3a)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
+ <MAbort- >SERR+ <PERR+ INTx-
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002
:4383]
	Subsystem: Hewlett-Packard Company Device [103c:30ee]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at 96500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller 
[1002:439d]
	Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller [1002:43
9d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:43
84] (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=64
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 93000000-930fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Contro
ller [1002:4399] (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at 96504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTranspo
rt Configuration [1022:1300] (rev 40)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map 
[1022:1301]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Control
ler [1022:1302]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneou
s Control [1022:1303]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control
 [1022:1304]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [R
adeon HD 3200 Graphics] [1002:9612]
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at 80000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 5000 [size=256]
	Region 2: Memory at 96400000 (32-bit, non-prefetchable) [size=64K]
	Region 5: Memory at 96300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabi
t Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 2299
	Region 0: Memory at 95200000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

09:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wi
reless LAN Controller [14e4:432b] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- 
<MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 93100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

0a:06.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 70) (p
rog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:30e3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B+ DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 93000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

```

dpkg -l|grep linux-restricted

```

ii  linux-restricted-modules                  2.6.27.9.13                             Generic Linux restricted modules.
rc  linux-restricted-modules-2.6.27-7-generic 2.6.27-7.12                             Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13                             Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common           2.6.27-9.13                             Non-free Linux 2.6.27 modules helper script
ii  linux-restricted-modules-generic          2.6.27.9.13                             Restricted Linux modules for generic kernels

```

iwevent with WEP
```

00:46:49.016631   eth1     Set Mode:Managed
00:46:53.640362   eth1     New Access Point/Cell address:00:13:10:2B:A1:21
00:46:53.724504   eth1     Registered node:00:13:10:2B:A1:21
00:46:53.724646   eth1     Custom driver event:Conn Success 00 00

```

iwevent with WPA/WPA2
```
00:45:41.895930   eth1     Set Mode:Managed
00:45:46.428768   eth1     Custom driver event:Conn RsnMismatch 00 08
00:45:46.428909   eth1     Custom driver event:Conn ConfigMismatch 01 00

```

---

### Post by jrwagz on 2009-06-06
> **ayuthia said:**
> this message almost looks like you were not in the directory where the makefile is located. From the "no rule to make target `linux`.  Stop" message, it looks like you were in /usr/src/linux-headers-2.6.22-14-generic instead of hybrid_wl.
I am having a similar issue, however I am running the command from the directory containing the Makefile.  And ideas?  Here is the results I get:

root@justin-laptop:/home/justin/hybrid_wl# ls
hybrid-portsrc-x86_32-v5_10_91_9.tar.gz  lib  Makefile  src
root@justin-laptop:/home/justin/hybrid_wl# make -C /lib/modules/2.6.28-11-generi/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
root@justin-laptop:/home/justin/hybrid_wl# 

I am very new to Ubuntu so I may be making some idiotic beginner mistake, but I don't know what that is!

Thanks

---

### Post by pxwpxw on 2009-06-06
> **jrwagz said:**
> I am having a similar issue, however I am running the command from the directory containing the Makefile.  And ideas?  Here is the results I get:

root@justin-laptop:/home/justin/hybrid_wl# ls
hybrid-portsrc-x86_32-v5_10_91_9.tar.gz  lib  Makefile  src
root@justin-laptop:/home/justin/hybrid_wl# make -C /lib/modules/2.6.28-11-generi/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
root@justin-laptop:/home/justin/hybrid_wl# 

I am very new to Ubuntu so I may be making some idiotic beginner mistake, but I don't know what that is!

Thanks

In here - 
```

# make -C /lib/modules/2.6.28-11-generi/build M='pwd'

should be 

# make -C /lib/modules/2.6.28-11-generi/build M=`pwd`

```

The ` ` backward leaning quotes give the output of the pwd command.

---

### Post by jrwagz on 2009-06-08
> **pxwpxw said:**
> In here - 
```

# make -C /lib/modules/2.6.28-11-generi/build M='pwd'

should be 

# make -C /lib/modules/2.6.28-11-generi/build M=`pwd`

```The ` ` backward leaning quotes give the output of the pwd command.

Thanks for your help!  That resolved that issue.  I am having another issue as shown in this post [http://ubuntuforums.org/showthread.php?p=7424140#post7424140 ]("http://ubuntuforums.org/showthread.php?p=7424140#post7424140")

I felt this topic was more related to that thread.  I appreciate your help!

---

