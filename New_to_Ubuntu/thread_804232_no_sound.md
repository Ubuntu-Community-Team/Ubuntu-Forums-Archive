---
title: "no sound"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by jinjuriki on 2008-05-22
I have no sound after installing Ubuntu for the first time on my Toshiba Satellite L45 S2416 which = piece of crap with vista installed on it.I have tried changing the autodetect to ALSA and the testing goes on forever. Try anything else and it gives the error of 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

here is what sudo lspci ran
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, fast devsel, latency 0
	Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff40
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ff200000-ff2fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff40
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff40
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at e800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e480 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ff63bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ff300000-ff3fffff
	Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff40

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [70] Power Management version 2

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7128
	Flags: fast devsel, IRQ 17
	Memory at ff2f0000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint IRQ 0
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 44000000-47fff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Unknown device ff40
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at d800 [size=256]
	Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

---

### Post by kansasnoob on 2008-05-23
The Medibuntu repository includes some "non-free" alsa-firmware.

You can install the Medibuntu repo by following the steps here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE: Remember to add the GPG key!

Then while you're in Synaptic installing "alsa-firmware" and/or "alsa-firmware-loaders", I'd also add either "alsamixergui" or "gnome-alsamixer" so you can make individual adjustments to the various "toggles".

---

