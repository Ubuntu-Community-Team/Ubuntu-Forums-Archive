---
title: "Cannot log on properly 12.04"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by pegasusgr on 2012-10-07
Hi there,

I am using Ubuntu 12.04 and recently (for about 10 days now) my computer started giving me a purple screen instead of the normal log on screen (where you input username and password). It still plays the short bongo sound. I think that I can normally put my password and continue but the screen never changes from the purple one I get. 

Note that this does not happen always. I just switch the laptop off and back on again and usually things work fine. Sometimes I need to do that more than once.

Could anybody help me with that?

Thanks!

---

### Post by 2F4U on 2012-10-07
Can you give more details about your hardware and the graphics card you have? What graphics driver do you use? Is this an upgrade or fresh install?

---

### Post by pegasusgr on 2012-10-07
Thank you for your answer.

This is what ```
lspci -v
``` gave me. I am not sure how to get the version of the graphics card driver. I use the one that was automatically installed with 12.04. I run an upgrade but it worked fine since April. It only started giving me this problem now. Maybe some driver update gave the problem?

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
	Subsystem: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
	Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=256]
	Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 4118 [size=8]
	I/O ports at 4124 [size=4]
	I/O ports at 4110 [size=8]
	I/O ports at 4120 [size=4]
	I/O ports at 4100 [size=16]
	Memory at f034e000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f034d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at f034c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f034b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at f034a000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Toshiba America Info Systems Device fd53
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0100000-f01fffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f0349000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at f0348000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
	Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
	Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
	Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
	Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
	Flags: fast devsel

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Lite-On Communications Inc Device 6613
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

06:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
	Subsystem: Toshiba America Info Systems Device fd52
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at f0100000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

---

