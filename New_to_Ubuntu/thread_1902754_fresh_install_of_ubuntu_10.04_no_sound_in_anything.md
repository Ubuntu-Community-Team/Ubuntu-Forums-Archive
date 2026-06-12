---
title: "fresh install of ubuntu 10.04 no sound in anything"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by Crystlviper on 2011-12-31
yes i placed this thread here as it is an absolute beginners posting. the title says it all, no sound from youtube, no sound from hulu, no sound from anything. nothing is muted this much i know. please advise on how i fix this problem. if you are going to say how to do it please be advised that i know nothing of ubuntu so please be some what detailed and guiding if you can.

---

### Post by ilikelinuxitisthebest on 2011-12-31
hello crystalviper welcome to the fourums.
press ctrl-alt-t to open the terminal an type this code.```
sudo lspci -v
``` and copy/paste your output here.

---

### Post by Crystlviper on 2011-12-31
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0200000-d03fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1235
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: d0100000-d01fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 1444
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: b0000000-b00fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 1444
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4038 [size=8]
    I/O ports at 404c [size=4]
    I/O ports at 4030 [size=8]
    I/O ports at 4048 [size=4]
    I/O ports at 4010 [size=16]
    Memory at d0408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA <?>
    Capabilities: [a4] PCIe advanced features <?>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0408600 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d0408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at d0300000 (32-bit, non-prefetchable) [size=64K]
    Memory at d0200000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0310000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 3040
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d0100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1444
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at 2000 [size=256]
    Memory at d0010000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d0020000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
    Capabilities: [cc] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by ilikelinuxitisthebest on 2011-12-31
there is a great fourm that i found right here [http://ubuntuforums.org/showthread.php?t=1088978](http://ubuntuforums.org/showthread.php?t=1088978). the person who had the problem has the same sound card as you. look through it and see if you can figure it out. if you need help post back here and ill help you out.

---

### Post by Crystlviper on 2011-12-31
i read through that posting and it sitll isnt working. so any help woudl be appreciated

---

### Post by tuxy-love on 2012-01-01
It looks like the issue you are having has been around a while with no permanent fix. In my experience it is easier to replace hardware like that. [www.thinkpenguin.com](www.thinkpenguin.com) has a nice selection of accessories that are easy to install and just work. For the most part anyway. You could possibly run into a digital restriction issue. Although not in this case.

---

