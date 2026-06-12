---
title: "microphone not working,sound card, hardy 8.04"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-17
i have a dell xps 1210 laptop
sounds works on the laptop
head phones work correctly
but the microphone does not work

as i understand it the sound card fully works, IF it is configured correctly
as there are MANY different variants of the sound card and ubuntu will not likely find just the right settings automagicly.

here is what information i have

@linuxtop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


linuxtop:~$ sudo lspci -v
[sudo] password for XXXXXXXXXX: 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ed000000-efefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Dell Unknown device 01d7
	Capabilities: [80] Power Management version 2
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Dell Unknown device 01d7
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Memory behind bridge: ecf00000-ecffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e00fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Dell Unknown device 01d7
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ecc00000-ecefffff
	Prefetchable memory behind bridge: 00000000e0100000-00000000e03fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Dell Unknown device 01d7
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: ecb00000-ecbfffff
	Capabilities: [50] Subsystem: Dell Unknown device 01d7

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Unknown device 01d7
	Flags: medium devsel, IRQ 5
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at ef000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at ecbfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at ecbfd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Unknown device 01d7
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at ecbfd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
	Subsystem: Dell Unknown device 01d7
	Flags: medium devsel, IRQ 9
	Memory at ecbfd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: Dell Unknown device 01d7
	Flags: medium devsel, IRQ 9
	Memory at ecbfd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: Dell Unknown device 01d7
	Flags: medium devsel, IRQ 9
	Memory at ecbfd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at ecffc000 (64-bit, non-prefetchable) [size=16K]
	Memory at e0000000 (64-bit, prefetchable) [size=1M]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] Vendor Specific Information
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint IRQ 0


thanks for any help

nutz

---

### Post by nutpants on 2008-05-18
found the answer here
[http://ubuntuforums.org/showthread.php?t=616845&highlight=9221](http://ubuntuforums.org/showthread.php?t=616845&highlight=9221)

there needs to be a wiki for information about what hardware and what settings need to be changed for newbies for laptops and prebuilt systems..

the forums are the next best thing

---

