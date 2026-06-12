---
title: "Help &amp; driver for XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by 58apache on 2011-11-08
New to Ubuntu, need help with getting the right display  configuration, possibly the right display/adapter driver for my server.

I recently installed Ubuntu 11.1 on my server, and noticed that I can  not control the resolution or settings under the Display Settings tool.   I have very low resolution and want to bump it up a bit.  I have  searched multiple forum threads, and many of them refer to the xorg.conf  file, but it is not where the threads say it should be, and I can't  find it anywhere.  Based on what I have read so far this is the file I  would need to edit to chnage things like refresh rate, and other display  settings.  Nothing I have tried so far has made any difference at all.   Need help . . .

Here is the output fro the lspci command:

lspci -vv
00:00.0 Host bridge: Intel Corporation E7230/3000/3010 Memory Controller Hub (rev 81)
    Subsystem: Tyan Computer Device 5160
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: i3000_edac
    Kernel modules: i3000_edac

00:01.0 PCI bridge: Intel Corporation E7230/3000/3010 PCI Express Root Port (rev 81) (prog-if 00 [Normal decode])
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 80400000-805fffff
    Prefetchable memory behind bridge: 0000000080600000-00000000807fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: dc200000-dc2fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: dc300000-dc3fffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at 3000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 3020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 3040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at 3060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at dc600000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: dc000000-dc1fffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000dbffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 30a0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at 30e8 [size=8]
    Region 1: I/O ports at 30dc [size=4]
    Region 2: I/O ports at 30e0 [size=8]
    Region 3: I/O ports at 30d8 [size=4]
    Region 4: I/O ports at 30b0 [size=16]
    Region 5: Memory at dc600400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Tyan Computer Device 5160
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 10
    Region 4: I/O ports at 1100 [size=32]
    Kernel modules: i2c-i801

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
    Subsystem: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at dc200000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
    Subsystem: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at dc300000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

0a:01.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics  Innovation) Z7/Z9 (XG20 core) (prog-if 00 [VGA controller])
    Subsystem: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    BIST result: 00
    Region 0: Memory at d8000000 (32-bit, prefetchable) [size=64M]
    Region 1: Memory at dc100000 (32-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 4000 [size=128]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: xgifb
    Kernel modules: xgifb, sisfb

0a:03.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
    Subsystem: Voyetra Technologies Santa Cruz
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (1000ns min, 6000ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at dc140000 (32-bit, non-prefetchable) [size=4K]
    Region 1: Memory at dc000000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: Sound Fusion CS46xx
    Kernel modules: snd-cs46xx

From the above I am guessing what is relevant is this part:

0a:01.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics   Innovation) Z7/Z9 (XG20 core) (prog-if 00 [VGA controller])
    Subsystem: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    BIST result: 00
    Region 0: Memory at d8000000 (32-bit, prefetchable) [size=64M]
    Region 1: Memory at dc100000 (32-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 4000 [size=128]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: xgifb
    Kernel modules: xgifb, sisfb

I'm running a Samsung SyncMaster 2494 display

When I run the "System Info" and click on Graphics, it indicates  "Driver: Unknown" and "Experience: Standard".  I'm guessing that this  plain vanilla driver is the source  of the limited video capabilities I  am getting.  The "Displays" tool doesn't let me change anything, and  won't even respond when I click on "Detect Displays".

Would greatly appreciate the proper steps specific to 11.10 for  configuring/tweaking the video and display.  Also, if anyone can tell me  what and where all the configuration files are for the video adapter  are, as well as the display, and the xserver related config files; this  must have changed drastically from older versions of Ubuntu since none  of the guidance on things like the location or existence of the  xorg.conf file seems to be valid anymore.  I've been doing a lot of this  the past 3 or 4 days >>>  ](*,)

By the way, I've been in the IT industry for over 25 years (yes, an old  guy) I have worked with various flavors of UNIX on Sun systems, AIX fro  IBM, and played with Linux from time to time.  I have decided I need to  get serious about learning Linux, and things like PHP, Python, and  expand my knowledge on HTTP.  I am finding that this is becoming a  required skill/knowledge even for non-programmers.  I mention this  because getting server up is key to my learning what I need to know.   Thank you in advance for your help on this.

---

### Post by Mark Phelps on 2011-11-08
Did you do a Google search based on your motherboard make and model?

Asking because I did a quick one for your video chipset and found a bunch of motherboards from Super Micro that offer Linux driver downloads -- problem is, they all referred to SUSE Enterprise versions, not to Ubuntu.

---

