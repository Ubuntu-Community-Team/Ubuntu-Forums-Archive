---
title: "Ubuntu freezes randomly, nothing works"
date: 2015-07-28
forum: New to Ubuntu
---

### Post by ragheed2 on 2015-07-28
[COLOR=#111111][FONT=Ubuntu]It has been a month now with this problem and my life is hell.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I had ubutnu 5 months ago or so and I changed to windows after a mistake that cleared out all my HDD, and about a month ago I got back to ubutnu 15.04, I had the problem that all of the system freezes (mouse, keyboard, etc..) until I use the (SysRq+RESUIB) trick which results in a whole system reboot and the loss of my data, I moved to 14.04 LTS and I had the problem again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I did a memtest and it showed no errors, I tried to run only on my intel integrated GPU but nothing hapenned and the problem still exists, I asked around and saw the previous posts but nothing helped. Here's the output of lspci -v :

[/FONT][/COLOR]
 00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, fast devsel, latency 0, IRQ 65
    Memory at b3000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, fast devsel, latency 0, IRQ 66
    Memory at b3810000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04) (prog-if 30 [XHCI])
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, medium devsel, latency 0, IRQ 60
    Memory at b3800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, fast devsel, latency 0, IRQ 64
    Memory at b381b000 (64-bit, non-prefetchable) [size=32]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, fast devsel, latency 64, IRQ 67
    Memory at b3814000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: b2000000-b2ffffff
    Prefetchable memory behind bridge: 00000000b1000000-00000000b1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: b3700000-b37fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: b3600000-b36fffff
    Prefetchable memory behind bridge: 00000000b3400000-00000000b34fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b3500000-b35fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000b01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b3819000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 62
    I/O ports at 6088 [size=8]
    I/O ports at 6094 [size=4]
    I/O ports at 6080 [size=8]
    I/O ports at 6090 [size=4]
    I/O ports at 6060 [size=32]
    Memory at b3818000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: medium devsel, IRQ 255
    Memory at b381a000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 6040 [size=32]

01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
    Subsystem: Toshiba America Info Systems Device f920
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 61
    Memory at b2000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci

07:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160
    Flags: bus master, fast devsel, latency 0, IRQ 68
    Memory at b3700000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: Toshiba America Info Systems Device f920
    Flags: bus master, fast devsel, latency 0, IRQ 63
    I/O ports at 4000 [size=256]
    Memory at b3600000 (64-bit, non-prefetchable) [size=4K]
    Memory at b3400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

---

### Post by dino99 on 2015-07-28
as its a toshiba hardware, start to read some links below
[https://duckduckgo.com/?q=ubuntu+toshiba+install](https://duckduckgo.com/?q=ubuntu+toshiba+install)

---

