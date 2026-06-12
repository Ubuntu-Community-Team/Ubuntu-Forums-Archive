---
title: "Timidity won't start/install (Hardy, Dell Inspiron 1520)"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by demios on 2008-08-18
so I tried to install the ubuntu studio suite thing in synaptic, and everything installed (more or less) except Timidity and ubuntustudio-audio, which depends on timidity. So I figured I knew where to start at least. Every time a package manager installs anything, I get this error (or similar):
```

errors encountered:
timidity
ubuntustudio-audio

ALSA lib pcm_dmix.c:1008 (snd_pcm_dmix_open) unable to open slave
invoke-rc.d: initscript timidity, action "start" failed
dpkg: error processing timidity (--configure):
  subprocess post-installation script returned error exist status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:, depends on timidity
```

Any help or pointers even are greatly appreciated. Thanks.

```
handicaptain@handicaptain:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
handicaptain@handicaptain:~$ sudo lspci -v
[sudo] password for handicaptain: 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: [88] Subsystem: Dell Unknown device 01f1
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Unknown device 01f1
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: f9f00000-f9ffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Unknown device 01f1
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f9c00000-f9efffff
	Prefetchable memory behind bridge: 00000000f8100000-00000000f83fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Unknown device 01f1
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: f9b00000-f9bfffff
	Capabilities: [50] Subsystem: Dell Unknown device 01f1

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 6eb0 [size=8]
	I/O ports at 6eb8 [size=4]
	I/O ports at 6ec0 [size=8]
	I/O ports at 6ec8 [size=4]
	I/O ports at 6ee0 [size=32]
	Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 01f1
	Flags: medium devsel, IRQ 10
	Memory at febfb700 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f4000000 (64-bit, prefetchable) [size=64M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Unknown device 01f1
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Memory at f8000000 (64-bit, prefetchable) [size=1M]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] Vendor Specific Information
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint IRQ 0

```

---

### Post by markbuntu on 2008-08-18
I also had this problem installing Ubuntustudio i386. I just removed timidity and ubuntustudio-desktop I think, or whatever synaptic wanted to remove with timidity and then reinstalled that other thing and it was OK. There is a bug at launchpad about this, it has been confirmed.

I had no problems like this installing ubuntustudio amd64 version which I did at about the same time.

---

