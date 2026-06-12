---
title: "No sound."
date: 2014-01-02
forum: New to Ubuntu
---

### Post by PataloraCR on 2014-01-02
This is what I got when I used "~$ lspci -v" on terminal

0:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: fast devsel
    Capabilities: <access denied>

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: fast devsel, IRQ 72
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port C) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fe800000-fe8fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    Memory at feb0b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb0a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb09000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb08000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb07000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_acpi, pata_atiixp

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Micro-Star International Co., Ltd. Device d693
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb06000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe700000-fe7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb05000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb04000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
    Flags: fast devsel
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
    Flags: fast devsel

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited / Sapphire Technology Cedar [Radeon HD 5450]
    Flags: bus master, fast devsel, latency 0, IRQ 83
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fea20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
    Subsystem: PC Partner Limited / Sapphire Technology Device aa68
    Flags: bus master, fast devsel, latency 0, IRQ 81
    Memory at fea40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited / Sapphire Technology Cedar [Radeon HD 5450]
    Flags: bus master, fast devsel, latency 0, IRQ 84
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe920000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at fe900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
    Subsystem: PC Partner Limited / Sapphire Technology Device aa68
    Flags: bus master, fast devsel, latency 0, IRQ 82
    Memory at fe940000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe800000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device 7693
    Flags: bus master, fast devsel, latency 0, IRQ 80
    I/O ports at c000 [size=256]
    Memory at fe704000 (64-bit, prefetchable) [size=4K]
    Memory at fe700000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by conversationjames on 2014-01-02
> [COLOR=#000000]00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)[/COLOR]
[COLOR=#000000]Subsystem: Micro-Star International Co., Ltd. Device d693[/COLOR]
[COLOR=#000000]Flags: bus master, slow devsel, latency 32, IRQ 16[/COLOR]
[COLOR=#000000]Memory at feb00000 (64-bit, non-prefetchable) [size=16K][/COLOR]
[COLOR=#000000]Capabilities: <access denied>[/COLOR]
[COLOR=#000000]Kernel driver in use: snd_hda_intel[/COLOR]
[COLOR=#000000]Kernel modules: snd-hda-intel
[/COLOR]

AND 

> [COLOR=#000000]01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series][/COLOR]
[COLOR=#000000]Subsystem: PC Partner Limited / Sapphire Technology Device aa68[/COLOR]
[COLOR=#000000]Flags: bus master, fast devsel, latency 0, IRQ 81[/COLOR]
[COLOR=#000000]Memory at fea40000 (64-bit, non-prefetchable) [size=16K][/COLOR]
[COLOR=#000000]Capabilities: <access denied>[/COLOR]
[COLOR=#000000]Kernel driver in use: snd_hda_intel[/COLOR]
[COLOR=#000000]Kernel modules: snd-hda-intel[/COLOR]

are your audio devices... Have you tried right-clicking the speaker on the top-right of your screen, left-click "Sound settings" and change the "Play sound through" devices? Mine was set to Analog Output, but I'm hooked up via optical through a receiver so had to change to "Digital Output"...

---

### Post by mörgæs on 2014-01-02
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by chkneater on 2014-01-02
open terminal and type 'alsamixer' to see if anything is muted.  "Master" and "PCM" should both be on.  You may have extra options also that may need to be unmuted like "4 channel" and stuff like that, but the main things are Master and PCM both unmuted and turned up.  You'll have to use your keyboard to change the levels.

---

