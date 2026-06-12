---
title: "Internet - 1395 WLAN minicard Broadcom BCM4312 802.11b/g"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by AtomicRobot on 2011-12-24
Trying to connect to the internet. I actually got this the first time I installed Ubuntu, and got props from a computer science dude when I told him. Then, I reformatted my hard drive and couldn't figure out how to get this tihs working like I did last time. After going through a ton of sights, hours of frustration I finally gave in and decided to make a post to see if I could get some help. 

Here is my terminal info. I got the stuff working, tried everything I could and the internet connection will work sometimes then disconnect after a minute, and sometimes not work at all:

milo@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
milo@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Dell Device 022f
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at eff8 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Dell Device 022f
    Flags: bus master, fast devsel, latency 0
    Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000a01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fe700000-fe7fffff
    Prefetchable memory behind bridge: 00000000a0200000-00000000a03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe400000-fe6fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6f40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    Memory behind bridge: fe300000-fe3fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 6fa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 022f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 6eb0 [size=8]
    I/O ports at 6eb8 [size=4]
    I/O ports at 6ec0 [size=8]
    I/O ports at 6ec8 [size=4]
    I/O ports at 6ee0 [size=32]
    Memory at fe9fb800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 022f
    Flags: medium devsel, IRQ 10
    Memory at fe9fb700 (32-bit, non-prefetchable) [size=256]
    I/O ports at 10c0 [size=32]
    Kernel modules: i2c-i801

02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at fe3ff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394

02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe3ff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at fe3ff600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Dell Device 022f
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe3ff700 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852
    Kernel modules: r852

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
    Subsystem: Dell Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at de00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

---

### Post by gandaran on 2011-12-24
> 0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

