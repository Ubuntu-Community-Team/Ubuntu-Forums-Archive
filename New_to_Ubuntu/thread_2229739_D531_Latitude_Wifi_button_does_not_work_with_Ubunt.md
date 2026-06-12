---
title: "D531 Latitude Wifi button does not work with Ubuntu"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by finn2 on 2014-06-15
Hi all, Any advice please? I've been trying to solve this for ages but i'm just going round in circles.
I've got a Dell Latitude D531 - No OS was on it so i installed Ubuntu yesterday. **I can connect successfully online with a wire but the dedicated Wifi button on the keyboard does not work (no light appears when pressing).**
I accessed the BIOS and it looks like wifi and the switch are not turned off.
Tried numerous things - really dont know what the problem is. Below is the results of some commands, any help appreciated!

$ **sudo lshw -C network;lsb_release -a;uname -a;sudo rfkill list;dmesg|grep -i firm;sudo iwlist scan**

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:af:7d:65
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5755m-v3.29 ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fe7f0000-fe7fffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
Linux ellie-Latitude-D531 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux
[    0.000000] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.144344] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.232891] [Firmware Warn]: MTRR: CPU 1: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.626951] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**$ lspci -nnk | grep -iA2 net**
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:0206]
    Kernel driver in use: tg3
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl

**$ lspci -v**
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
    Subsystem: Dell Device 0206
    Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe900000-feafffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
    Capabilities: <access denied>

00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Memory behind bridge: fe800000-fe8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: fe700000-fe7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

...................(deleted some of the results i dont think are needed ) ..........................................

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
    Subsystem: Dell Device 0206
    Flags: 66MHz, medium devsel
    I/O ports at 10c0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus

03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
    Subsystem: O2 Micro, Inc. Firewire (IEEE 1394)
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at fe6ff000 (32-bit, non-prefetchable) [size=4K]
    Memory at fe6fe800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci

[B]09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
    Subsystem: Dell Device 0206
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fe7f0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl[/B]

**$ sudo iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
**no wlan0 ??????????**

---

### Post by finn2 on 2014-06-15
I've moved this to the Wireless and Networking thread - probably a more appropriate place - sorry!

---

### Post by Iowan on 2014-06-15
Duplicate closed.
[http://ubuntuforums.org/showthread.php?t=2229752&p=13050264#post13050264]("http://ubuntuforums.org/showthread.php?t=2229752&p=13050264#post13050264")

You can use the Report Post button at the bottom of each post to request to have a thread moved. :)

---

