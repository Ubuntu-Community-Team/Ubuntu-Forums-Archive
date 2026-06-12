---
title: "4 in 1 memory card reader not working"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by oaridus on 2011-09-26
Hi all, I have an issue which is quite urgent. My laptop is Thinkpad T61 + Ubuntu system + WinXP. I have the Ricoh 4 in 1 card reader exactly the way it is shown in this photo

[http://forum.notebookreview.com/lenovo-ibm/198140-looking-photo-sd-card-reader-t61-14-a.html](http://forum.notebookreview.com/lenovo-ibm/198140-looking-photo-sd-card-reader-t61-14-a.html)

But this does not seem to work. I inserted MMC card into it without knowing and the card is stuck. So my question is to how to activate this card reader permanently. I also checked this site 

[http://ubuntuforums.org/showthread.php?t=788334](http://ubuntuforums.org/showthread.php?t=788334)

My card reader comes out to be disabled in the dmesg command. But I did not try their fix.. Could any one please help me quickly

Thanks

---

### Post by oaridus on 2011-09-26
I typed lspci -v and here is the result

-------------

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Lenovo Device 20b1
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
	Subsystem: Lenovo Device 20b9
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at fe200000 (32-bit, non-prefetchable) [size=128K]
	Memory at fe225000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 20ab
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20ac
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc100000-df2fffff
	Prefetchable memory behind bridge: 00000000dfd00000-00000000dfdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d4000000-d7dfffff
	Prefetchable memory behind bridge: 00000000dfa00000-00000000dfafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000df700000-00000000df7fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: cc000000-cdffffff
	Prefetchable memory behind bridge: 00000000df400000-00000000df4fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 18c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 20ab
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: f8100000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: Lenovo Device 20b6
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo Device 20a6
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1830 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Lenovo Device 20a7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 31
	I/O ports at 1c48 [size=8]
	I/O ports at 1c1c [size=4]
	I/O ports at 1c40 [size=8]
	I/O ports at 1c18 [size=4]
	I/O ports at 1c20 [size=32]
	Memory at fe226000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo Device 20a9
	Flags: medium devsel, IRQ 11
	Memory at fe227400 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c60 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
	Subsystem: Lenovo Device 20d8
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-173, nvidia-current, nvidiafb, nouveau

02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
	Subsystem: Intel Corporation Turbo Memory Controller
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at df2ffc00 (32-bit, non-prefetchable) [size=1K]
	I/O ports at 3000 [size=128]
	[virtual] Expansion ROM at dfd00000 [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1110
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at d7dfe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Lenovo Device 20c6
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at f8100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: f4000000-f7fff000 (prefetchable)
	Memory window 1: 40000000-43fff000
	I/O window 0: 00008000-000080ff
	I/O window 1: 00008400-000084ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10)
	Subsystem: Lenovo Device 20c7
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f8101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
	Subsystem: Lenovo Device 20c8
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f8101800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
	Subsystem: Lenovo Device 20ca
	Flags: medium devsel, IRQ 11
	Memory at f8102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
	Subsystem: Lenovo Device 20cb
	Flags: medium devsel, IRQ 11
	Memory at f8102400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
-------------------

As you can see the Ricoh mmc host says "unknown header type 7f". It seems only the mmc is not working.. and unfortunately this is exactly what I put in. Could anyone tell me how to fix this header..

Thanks

---

### Post by oaridus on 2011-09-26
since I found the id of the device from the previous post, I typed the following as given in other sites

sudo setpci -s 15:00.1 0xCA=0x57
sudo setpci -s 15:00.1 0xCB=0x02
sudo setpci -s 15:00.1 0xCA=0x00

But nothing seems to happen. Do I have to do anything else. I rebooted the system as well. One thing I noticed that when rebooting the LED near the reader slot blinked. It seems to be accessed at boot time I guess.

Please could anyone help quickly..

Thanks

---

### Post by oaridus on 2011-09-27
I haven't got any reply yet.. Just crossing my fingers. please help

---

### Post by oaridus on 2011-09-28
Any help please 

> **oaridus said:**
> I haven't got any reply yet.. Just crossing my fingers. please help

---

### Post by anewguy on 2011-09-28
There is a bug report for this on launchpad you can view at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490")

Some say they can work with SDHC cards but not xD cards.

Supposedly, you can blacklist ricoh-mmx and load sm_ftl to get xD *only* support.

Just be aware that this is a known bug that affects many laptops of varying brands, and right now the problem is looked at as an added feature.  It appears that starting in Maverick the sm_ftl module became available.

Dave ;)

---

