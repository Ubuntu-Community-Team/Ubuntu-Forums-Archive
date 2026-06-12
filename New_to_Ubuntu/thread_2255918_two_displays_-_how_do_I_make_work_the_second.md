---
title: "two displays - how do I make work the second?"
date: 2014-12-08
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-12-08
Hi all, 

I have two displays - how do I make work the second?
Thanks ahead.

---

### Post by nerdtron on 2014-12-08
You can install "arandr". A nice utility for configuring screen and screen resolutions.

Install it from the software center or through the command line:
```
sudo apt-get install arandr
```

---

### Post by marchello_lippi2 on 2014-12-09
Ok, I installed "arandr", what next? The second display still doesn't work... Could you please kindly help to perform all required steps? 
Thanks ahead.

---

### Post by marchello_lippi2 on 2014-12-09
My hardware information is shown below. 
Any help? 

```

$ lspci -v | less

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: ASUSTeK Computer Inc. Device 84ca
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 84ca
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 44
        Memory at f7d00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at f7d1a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>
        Kernel driver in use: mei_me

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at f7d18000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. Device 84a8
        Flags: bus master, fast devsel, latency 0, IRQ 49
        Memory at f7d10000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f7c00000-f7cfffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f7d17000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
        I/O ports at f0b0 [size=8]
        I/O ports at f0a0 [size=4]
        I/O ports at f090 [size=8]
        I/O ports at f080 [size=4]
        I/O ports at f060 [size=32]
        Memory at f7d16000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: medium devsel, IRQ 11
        Memory at f7d15000 (64-bit, non-prefetchable) [size=256]
        I/O ports at f040 [size=32]

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device 84b5
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at e000 [size=256]
        Memory at f7c00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: rtl8192ce

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
        Subsystem: ASUSTeK Computer Inc. P8 series motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 45
        I/O ports at d000 [size=256]
        Memory at f0004000 (64-bit, prefetchable) [size=4K]
        Memory at f0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8169

05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=05, secondary=06, subordinate=06, sec-latency=32
        Capabilities: <access denied>

```

---

### Post by Rex Bouwense on 2014-12-10
> **marchello_lippi2 said:**
> Ok, I installed "arandr", what next? The second display still doesn't work... Could you please kindly help to perform all required steps? 
Thanks ahead.
See here
[http://lxlinux.com/#14](http://lxlinux.com/#14)

---

