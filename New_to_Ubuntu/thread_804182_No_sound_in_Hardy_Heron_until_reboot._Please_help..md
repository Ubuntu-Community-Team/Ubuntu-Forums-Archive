---
title: "No sound in Hardy Heron until reboot. Please help..."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Ballistixx on 2008-05-22
Hello Guys,

I installed Hardy Heron (full blown install) on a usb external 2.5"drive two days ago. This is my first go 'round with any distribution of Linux ever. 

Before I get to my problem I want to give props to the Ubuntu programming community! To be able to stick the live cd in the drive of almost any computer system and have most of the hardware work is simply amazing!
Try that with Windows. Thanks!

On to one of my small problems... When I boot into Hardy the sound usually won't work. If I restart the system the sound usually works fine. 

The system is a Gateway 7508gx laptop w/ a Conexant sound card. The sound card model is AC '97 2.3 I believe.

I have done a bit of searching here and on the web in general with no luck! 

I also want to get all my Logitech mx610 mouse buttons working, then the wireless card. I am fairly certain everything else on the notebook is working properly with Ubuntu 8.04.

If any body can help I will be very grateful.

Regards,
Jason

---

### Post by Master Grah on 2008-05-22
Maybe if you enable the restricted driver? That's my only guess.

---

### Post by Ballistixx on 2008-05-22
In System/Administration/Hardware Drivers there is no driver listed for the sond card.

Thanks for the reply though.

Jason

---

### Post by yochaigal on 2008-05-22
This is always in the same machine, or any machine?
What is your output of 
sudo lspci -v

Also, try going to System > Preferences > Sound 
And changing the output from the default pulseaudio to ALSA.

---

### Post by Ballistixx on 2008-05-22
Hi,

It is on the same laptop Gateway 7508gx.
I will try changing the audio setting from auto detect (which is what is normally on) to alsa


Here is the log (taken while sound  was working)...

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
	Subsystem: Gateway 2000 Unknown device 0605
	Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0000000-c00fffff
	Prefetchable memory behind bridge: c8000000-cfffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [b0] Subsystem: Gateway 2000 Unknown device 0506
	Capabilities: [b8] HyperTransport: MSI Mapping

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0100000-c01fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [b0] Subsystem: ATI Technologies Inc Unknown device 5951
	Capabilities: [b8] HyperTransport: MSI Mapping

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0500000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0501000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0502000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at c0503000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: c0200000-c02fffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at c0503400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at c0503800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600] (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0020000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, fast devsel, latency 0, IRQ 221
	Memory at c0100000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at c0202000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 0000b400-0000b4ff
	I/O window 1: 0000b800-0000b8ff
	16-bit legacy interface ports at 0001

03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Broadcom Corporation Gateway 7510GX
	Flags: bus master, fast devsel, latency 64, IRQ 16
	Memory at c0200000 (32-bit, non-prefetchable) [size=8K]

03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0506
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at c0203000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at b000 [size=128]
	Capabilities: [50] Power Management version 2

Any ideas???

Thanks,
Jason

---

### Post by Ballistixx on 2008-05-22
I also ran aplay -l output here is what came up.

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Jason

---

### Post by Ballistixx on 2008-05-23
I got the wireless card working.

I also got all the buttons on my Logitech mx610 mouse working using instructions in this link.

[http://locoteam.ubuntuforums.org/showthread.php?t=485175](http://locoteam.ubuntuforums.org/showthread.php?t=485175)

I  still can only get the sound to work on reboot not on the initial start up.
Which is very anoying...Who wants to turn on thier PC, only to have restart it once again. Ugggh!

Is there any body out theeerrrrreeeeeee?????        errrrrrreeee

No soup for me??

Jason

---

