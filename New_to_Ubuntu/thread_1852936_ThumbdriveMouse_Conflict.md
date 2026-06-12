---
title: "Thumbdrive/Mouse Conflict"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by haggar47 on 2011-10-01
I just started using Ubuntu!  When I plug in a USB thumbdrive the mouse freezes.  I have tried both a USB and PS/2 mouse.  Any suggestions, please!  Thank you!

---

### Post by cameronedwards on 2011-10-01
Open the update manager. 
(Menu-System-Adimistration-Update Manager)
If there are any updates, install them. If not, try to google your mouse model, with words like 'ubuntu' and 'driver'.
Most likely it's a driver problem, but there's a chance that the system isn't reacting to usb input correctly.
If that doesn't work try pluging two usb's into the computer at once, and see what happens.

---

### Post by ubudog on 2011-10-01
Hi there!

Can you please post the output of:
```
dmesg
```

After plugging in the thumb drive?
(you run that command in a terminal)

And also, have you done any updates yet?

---

### Post by haggar47 on 2011-10-01
```

[    0.012458] Initializing cgroup subsys blkio
[    0.012510] tseg: 0000000000
[    0.012533] mce: CPU supports 5 MCE banks
[    0.012587] SMP alternatives: switching to UP code
[    0.027443] Freeing SMP alternatives: 20k freed
[    0.027470] ACPI: Core revision 20110112
[    0.029752] ftrace: allocating 24328 entries in 96 pages
[    0.038461] Setting APIC routing to flat
[    0.039285] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.139305] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[    0.140000] Performance Events: AMD PMU driver.
[    0.140000] ... version:                0
[    0.140000] ... bit width:              48
[    0.140000] ... generic registers:      4
[    0.140000] ... value mask:             0000ffffffffffff
[    0.140000] ... max period:             00007fffffffffff
[    0.140000] ... fixed-purpose events:   0
[    0.140000] ... event mask:             000000000000000f
[    0.140000] Brought up 1 CPUs
[    0.140000] Total of 1 processors activated (4000.08 BogoMIPS).
[    0.140000] devtmpfs: initialized
[    0.140000] print_constraints: dummy: 
[    0.140000] Time:  7:17:30  Date: 10/01/11
[    0.140000] NET: Registered protocol family 16
[    0.140000] node 0 link 0: io port [1000, ffffff]
[    0.140000] TOM: 0000000040000000 aka 1024M
[    0.140000] node 0 link 0: mmio [a0000, bffff]
[    0.140000] node 0 link 0: mmio [40000000, ffffffff]
[    0.140000] bus: [00, ff] on node 0 link 0
[    0.140000] bus: 00 index 0 [io  0x0000-0xffff]
[    0.140000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.140000] bus: 00 index 2 [mem 0x40000000-0xfcffffffff]
[    0.140000] ACPI: bus type pci registered
[    0.140000] PCI: Using configuration type 1 for base access
[    0.140000] bio: create slab <bio-0> at 0
[    0.140000] ACPI: EC: Look up EC in DSDT
[    0.140000] ACPI: Actual Package length (266) is larger than NumElements field (2), truncated
[    0.140000] 
[    0.140000] ACPI: Interpreter enabled
[    0.140000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.140000] ACPI: Using IOAPIC for interrupt routing
[    0.140000] ACPI: Power Resource [URP1] (off)
[    0.140000] ACPI: Power Resource [URP2] (off)
[    0.140000] ACPI: Power Resource [FDDP] (off)
[    0.140000] ACPI: Power Resource [LPTP] (off)
[    0.141760] ACPI: No dock devices found.
[    0.141762] HEST: Table not found.
[    0.141766] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.141984] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.142099] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.142102] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.142105] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.142108] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.142111] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffdfffff] (ignored)
[    0.142114] pci_root PNP0A03:00: host bridge window [mem 0xfee01000-0xffdfffff] (ignored)
[    0.142133] pci 0000:00:00.0: [1106:0204] type 0 class 0x000600
[    0.142143] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.142202] pci 0000:00:00.1: [1106:1204] type 0 class 0x000600
[    0.142241] pci 0000:00:00.2: [1106:2204] type 0 class 0x000600
[    0.142276] pci 0000:00:00.3: [1106:3204] type 0 class 0x000600
[    0.142310] pci 0000:00:00.4: [1106:4204] type 0 class 0x000600
[    0.142347] pci 0000:00:00.7: [1106:7204] type 0 class 0x000600
[    0.142385] pci 0000:00:01.0: [1106:b188] type 1 class 0x000604
[    0.142417] pci 0000:00:01.0: supports D1
[    0.142447] pci 0000:00:0f.0: [1106:3149] type 0 class 0x000104
[    0.142462] pci 0000:00:0f.0: reg 10: [io  0xec00-0xec07]
[    0.142470] pci 0000:00:0f.0: reg 14: [io  0xe800-0xe803]
[    0.142479] pci 0000:00:0f.0: reg 18: [io  0xe400-0xe407]
[    0.142488] pci 0000:00:0f.0: reg 1c: [io  0xe000-0xe003]
[    0.142497] pci 0000:00:0f.0: reg 20: [io  0xdc00-0xdc0f]
[    0.142506] pci 0000:00:0f.0: reg 24: [io  0xd800-0xd8ff]
[    0.142544] pci 0000:00:0f.1: [1106:0571] type 0 class 0x000101
[    0.142583] pci 0000:00:0f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.142634] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.142669] pci 0000:00:10.0: reg 20: [io  0xc800-0xc81f]
[    0.142696] pci 0000:00:10.0: supports D1 D2
[    0.142699] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.142703] pci 0000:00:10.0: PME# disabled
[    0.142723] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.142759] pci 0000:00:10.1: reg 20: [io  0xcc00-0xcc1f]
[    0.142786] pci 0000:00:10.1: supports D1 D2
[    0.142789] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.142793] pci 0000:00:10.1: PME# disabled
[    0.142809] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.142846] pci 0000:00:10.2: reg 20: [io  0xd000-0xd01f]
[    0.142873] pci 0000:00:10.2: supports D1 D2
[    0.142875] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.142879] pci 0000:00:10.2: PME# disabled
[    0.142897] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.142933] pci 0000:00:10.3: reg 20: [io  0xd400-0xd41f]
[    0.142960] pci 0000:00:10.3: supports D1 D2
[    0.142962] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.142966] pci 0000:00:10.3: PME# disabled
[    0.142984] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.143584] pci 0000:00:10.4: reg 10: [mem 0xcfffbe00-0xcfffbeff]
[    0.145963] pci 0000:00:10.4: supports D1 D2
[    0.145965] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145969] pci 0000:00:10.4: PME# disabled
[    0.145991] pci 0000:00:11.0: [1106:3227] type 0 class 0x000601
[    0.146042] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.146078] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
[    0.146093] pci 0000:00:11.5: reg 10: [io  0xc400-0xc4ff]
[    0.146145] pci 0000:00:11.5: supports D1 D2
[    0.146166] pci 0000:00:12.0: [1106:3065] type 0 class 0x000200
[    0.146180] pci 0000:00:12.0: reg 10: [io  0xc000-0xc0ff]
[    0.146188] pci 0000:00:12.0: reg 14: [mem 0xcfffbd00-0xcfffbdff]
[    0.146233] pci 0000:00:12.0: supports D1 D2
[    0.146236] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.146240] pci 0000:00:12.0: PME# disabled
[    0.146259] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.146280] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.146297] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.146314] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.146335] PCI: peer root bus 00 res updated from pci conf
[    0.146370] pci 0000:01:00.0: [1106:3108] type 0 class 0x000300
[    0.146380] pci 0000:01:00.0: reg 10: [mem 0xc8000000-0xcbffffff pref]
[    0.146386] pci 0000:01:00.0: reg 14: [mem 0xce000000-0xceffffff]
[    0.146406] pci 0000:01:00.0: reg 30: [mem 0xcfef0000-0xcfefffff pref]
[    0.146420] pci 0000:01:00.0: supports D1 D2
[    0.146444] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.146449] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.146453] pci 0000:00:01.0:   bridge window [mem 0xcde00000-0xcfefffff]
[    0.146457] pci 0000:00:01.0:   bridge window [mem 0xc5d00000-0xcdcfffff pref]
[    0.146466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.159446] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.159495] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.159542] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.159589] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.159636] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.159684] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.159733] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.159781] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.159925] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.159928] vgaarb: loaded
[    0.160202] SCSI subsystem initialized
[    0.160312] libata version 3.00 loaded.
[    0.160377] usbcore: registered new interface driver usbfs
[    0.160390] usbcore: registered new interface driver hub
[    0.160423] usbcore: registered new device driver usb
[    0.160545] wmi: Mapper loaded
[    0.160547] PCI: Using ACPI for IRQ routing
[    0.160551] PCI: pci_cache_line_size set to 64 bytes
[    0.160562] pci 0000:00:00.0: address space collision: [mem 0xd0000000-0xd7ffffff pref] conflicts with GART [mem 0xd0000000-0xd7ffffff]
[    0.160632] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.160635] reserve RAM buffer: 000000003bff0000 - 000000003bffffff 
[    0.160773] NetLabel: Initializing
[    0.160776] NetLabel:  domain hash size = 128
[    0.160777] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.160795] NetLabel:  unlabeled traffic allowed by default
[    0.171801] AppArmor: AppArmor Filesystem Enabled
[    0.171854] pnp: PnP ACPI init
[    0.171883] ACPI: bus type pnp registered
[    0.172033] pnp 00:00: [bus 00-ff]
[    0.172036] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.172039] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.172042] pnp 00:00: [io  0x0d00-0xffff window]
[    0.172045] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.172048] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.172050] pnp 00:00: [mem 0x40000000-0xffdfffff window]
[    0.172053] pnp 00:00: [mem 0xfee01000-0xffdfffff window]
[    0.172114] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.172195] pnp 00:01: [io  0x03f2-0x03f3]
[    0.172197] pnp 00:01: [io  0x03f4-0x03f5]
[    0.172199] pnp 00:01: [io  0x03f7]
[    0.172216] pnp 00:01: [irq 6]
[    0.172219] pnp 00:01: [dma 2]
[    0.172272] pnp 00:01: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.172442] pnp 00:02: [io  0x03f8-0x03ff]
[    0.172448] pnp 00:02: [irq 4]
[    0.172505] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.172802] pnp 00:03: [io  0x0378-0x037f]
[    0.172805] pnp 00:03: [io  0x0778-0x077b]
[    0.172810] pnp 00:03: [irq 7]
[    0.172812] pnp 00:03: [dma 3]
[    0.172894] pnp 00:03: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.173042] pnp 00:04: [io  0x0010-0x001f]
[    0.173044] pnp 00:04: [io  0x0022-0x003f]
[    0.173047] pnp 00:04: [io  0x0044-0x005f]
[    0.173049] pnp 00:04: [io  0x0062-0x0063]
[    0.173051] pnp 00:04: [io  0x0065-0x006f]
[    0.173054] pnp 00:04: [io  0x0072-0x007f]
[    0.173056] pnp 00:04: [io  0x0080]
[    0.173058] pnp 00:04: [io  0x0084-0x0086]
[    0.173060] pnp 00:04: [io  0x0088]
[    0.173062] pnp 00:04: [io  0x008c-0x008e]
[    0.173064] pnp 00:04: [io  0x0090-0x009f]
[    0.173067] pnp 00:04: [io  0x00a2-0x00bf]
[    0.173069] pnp 00:04: [io  0x00e0-0x00ef]
[    0.173071] pnp 00:04: [io  0x0290-0x0297]
[    0.173073] pnp 00:04: [io  0x03f0-0x03f1]
[    0.173075] pnp 00:04: [io  0x04d0-0x04d1]
[    0.173078] pnp 00:04: [io  0x0400-0x040f]
[    0.173080] pnp 00:04: [io  0x0000-0xffffffffffffffff disabled]
[    0.173083] pnp 00:04: [io  0x0820-0x0821]
[    0.173085] pnp 00:04: [mem 0xfee00000-0xfee00fff]
[    0.173178] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.173182] system 00:04: [io  0x03f0-0x03f1] has been reserved
[    0.173185] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.173188] system 00:04: [io  0x0400-0x040f] has been reserved
[    0.173191] system 00:04: [io  0x0820-0x0821] has been reserved
[    0.173195] system 00:04: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.173199] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.173220] pnp 00:05: [dma 4]
[    0.173223] pnp 00:05: [io  0x0000-0x000f]
[    0.173225] pnp 00:05: [io  0x0081-0x0083]
[    0.173227] pnp 00:05: [io  0x0087]
[    0.173229] pnp 00:05: [io  0x0089-0x008b]
[    0.173231] pnp 00:05: [io  0x008f]
[    0.173234] pnp 00:05: [io  0x00c0-0x00df]
[    0.173272] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.173283] pnp 00:06: [io  0x0070-0x0071]
[    0.173289] pnp 00:06: [irq 8]
[    0.173330] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.173339] pnp 00:07: [io  0x0061]
[    0.173373] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.173385] pnp 00:08: [io  0x00f0-0x00ff]
[    0.173391] pnp 00:08: [irq 13]
[    0.173427] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.173458] pnp 00:09: [io  0x0060]
[    0.173460] pnp 00:09: [io  0x0064]
[    0.173465] pnp 00:09: [irq 12]
[    0.173500] pnp 00:09: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.173672] pnp: PnP ACPI: found 10 devices
[    0.173674] ACPI: ACPI bus type pnp unregistered
[    0.180247] Switching to clocksource acpi_pm
[    0.180298] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.180301] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.180308] pci 0000:00:01.0:   bridge window [mem 0xcde00000-0xcfefffff]
[    0.180312] pci 0000:00:01.0:   bridge window [mem 0xc5d00000-0xcdcfffff pref]
[    0.180325] pci 0000:00:01.0: setting latency timer to 64
[    0.180329] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.180332] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.180335] pci_bus 0000:00: resource 6 [mem 0x40000000-0xfcffffffff]
[    0.180339] pci_bus 0000:01: resource 1 [mem 0xcde00000-0xcfefffff]
[    0.180341] pci_bus 0000:01: resource 2 [mem 0xc5d00000-0xcdcfffff pref]
[    0.180401] NET: Registered protocol family 2
[    0.180512] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.181326] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.183772] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.185018] TCP: Hash tables configured (established 131072 bind 65536)
[    0.185021] TCP reno registered
[    0.185034] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.185066] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.185208] NET: Registered protocol family 1
[    0.185225] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.185244] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.189760] Switched to NOHz mode on CPU #0
[    2.180010] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    2.180124] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    2.180146] pci 0000:01:00.0: Boot video device
[    2.180149] PCI: CLS 32 bytes, default 64
[    2.180291] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
[    2.186779] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[    2.187189] audit: initializing netlink socket (disabled)
[    2.187205] type=2000 audit(1317453452.179:1): initialized
[    2.203463] Trying to unpack rootfs image as initramfs...
[    2.230689] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.232784] VFS: Disk quotas dquot_6.5.2
[    2.232852] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.233614] fuse init (API version 7.16)
[    2.233718] msgmni has been set to 1839
[    2.240548] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.250400] io scheduler noop registered
[    2.250406] io scheduler deadline registered
[    2.250534] io scheduler cfq registered (default)
[    2.250782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.250815] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.250988] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.250996] ACPI: Power Button [PWRB]
[    2.251061] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.251065] ACPI: Power Button [PWRF]
[    2.251204] ACPI: acpi_idle registered with cpuidle
[    2.252471] ERST: Table is not found!
[    2.252596] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.273094] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.311888] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.330692] Linux agpgart interface v0.103
[    2.332181] brd: module loaded
[    2.332864] loop: module loaded
[    2.333011] i2c-core: driver [adp5520] using legacy suspend method
[    2.333013] i2c-core: driver [adp5520] using legacy resume method
[    2.340141] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.340224] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    2.340763] Fixed MDIO Bus: probed
[    2.340813] PPP generic driver version 2.4.2
[    2.340917] tun: Universal TUN/TAP device driver, 1.6
[    2.340919] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.341032] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.341092] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.341114] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.341162] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.341247] ehci_hcd 0000:00:10.4: irq 21, io mem 0xcfffbe00
[    2.360142] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.360402] hub 1-0:1.0: USB hub found
[    2.360409] hub 1-0:1.0: 8 ports detected
[    2.360557] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.360582] uhci_hcd: USB Universal Host Controller Interface driver
[    2.370143] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.370161] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.370288] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.370326] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c800
[    2.370531] hub 2-0:1.0: USB hub found
[    2.370537] hub 2-0:1.0: 2 ports detected
[    2.370712] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.370718] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.370768] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.370790] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000cc00
[    2.370959] hub 3-0:1.0: USB hub found
[    2.370963] hub 3-0:1.0: 2 ports detected
[    2.371073] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.371079] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.371145] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.371168] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d000
[    2.371323] hub 4-0:1.0: USB hub found
[    2.371328] hub 4-0:1.0: 2 ports detected
[    2.371435] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.371442] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.371491] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.371516] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[    2.371670] hub 5-0:1.0: USB hub found
[    2.371674] hub 5-0:1.0: 2 ports detected
[    2.371809] i8042: PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    2.371812] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    2.372307] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.372315] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.372416] mousedev: PS/2 mouse device common for all mice
[    2.372546] rtc_cmos 00:06: RTC can wake from S4
[    2.372619] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.372670] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.372837] device-mapper: uevent: version 1.0.3
[    2.372927] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    2.380101] device-mapper: multipath: version 1.2.0 loaded
[    2.380107] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.380364] cpuidle: using governor ladder
[    2.380366] cpuidle: using governor menu
[    2.380684] TCP cubic registered
[    2.380842] NET: Registered protocol family 10
[    2.381408] NET: Registered protocol family 17
[    2.381436] Registering the dns_resolver key type
[    2.381461] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ (1 cpu cores) (version 2.20.00)
[    2.381536] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
[    2.381538] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[    2.381758] PM: Hibernation image not present or could not be loaded.
[    2.381774] registered taskstats version 1
[    2.382033]   Magic number: 15:557:267
[    2.382172] rtc_cmos 00:06: setting system clock to 2011-10-01 07:17:32 UTC (1317453452)
[    2.382176] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.382178] EDD information not available.
[    2.597690] Freeing initrd memory: 12864k freed
[    2.615438] Freeing unused kernel memory: 956k freed
[    2.616583] Write protecting the kernel read-only data: 10240k
[    2.617493] Freeing unused kernel memory: 184k freed
[    2.623718] Freeing unused kernel memory: 1440k freed
[    2.655364] <30>udev[68]: starting version 167
[    2.865757] via-rhine.c:v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    2.869452] pata_via 0000:00:0f.1: version 0.3.4
[    2.869474] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.873796] Floppy drive(s): fd0 is 1.44M
[    2.874772] scsi0 : pata_via
[    2.874967] scsi1 : pata_via
[    2.876398] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.876402] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.878736] sata_via 0000:00:0f.0: version 2.6
[    2.878758] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.878810] sata_via 0000:00:0f.0: routed to hard irq line 10
[    2.880812] scsi2 : sata_via
[    2.882114] scsi3 : sata_via
[    2.882176] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 20
[    2.882179] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 20
[    2.889222] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.889805] eth0: VIA Rhine II at 0xcfffbd00, 00:11:09:84:f1:f8, IRQ 23.
[    2.890534] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 4de1.
[    2.900090] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    2.916082] FDC 0 is a post-1991 82077
[    3.070876] ata1.00: ATA-8: WDC WD1600AAJB-00J3A0, 01.03E01, max UDMA/133
[    3.070882] ata1.00: 312581808 sectors, multi 16: LBA48 
[    3.090015] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.120925] ata1.00: configured for UDMA/133
[    3.121078] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJB-0 01.0 PQ: 0 ANSI: 5
[    3.121295] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.121598] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.121655] sd 0:0:0:0: [sda] Write Protect is off
[    3.121660] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.121685] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.132871]  sda: sda1
[    3.133201] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.155882] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.3/usb5/5-2/5-2:1.0/input/input2
[    3.156075] generic-usb 0003:046D:C31C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:10.3-2/input0
[    3.196583] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.3/usb5/5-2/5-2:1.1/input/input3
[    3.196738] generic-usb 0003:046D:C31C.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:10.3-2/input1
[    3.196993] usbcore: registered new interface driver usbhid
[    3.196996] usbhid: USB HID core driver
[    3.210018] Refined TSC clocksource calibration: 2000.068 MHz.
[    3.210025] Switching to clocksource tsc
[    3.490012] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.075398] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[   14.946582] <30>udev[315]: starting version 167
[   15.041771] lp: driver loaded but no devices found
[   15.568655] parport_pc 00:03: reported by Plug and Play ACPI
[   15.568766] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   15.578819] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.689268] <30>udev[346]: renamed network interface eth0 to eth1
[   15.699081] ACPI: resource vt596_smbus [io  0x0400-0x0407] conflicts with ACPI region SMOV [io 0x400-0x406]
[   15.699086] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.699641] lp0: using parport0 (interrupt-driven).
[   15.795336] MCE: In-kernel MCE decoding enabled.
[   15.863328] type=1400 audit(1317467865.972:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
[   15.863822] type=1400 audit(1317467865.972:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
[   15.864132] type=1400 audit(1317467865.972:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
[   15.969638] EDAC MC: Ver: 2.1.0 Sep 12 2011
[   16.141738] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input4
[   16.142065] EDAC amd64_edac: v3.3.0
[   16.145948] EDAC amd64: DRAM ECC disabled.
[   16.145958] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   16.145959]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   16.145961]  (Note that use of the override may cause unknown side effects.)
[   16.480609] ppdev: user-space parallel port driver
[   17.079632] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   17.079800] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   17.433344] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   17.547466] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   18.259480] type=1400 audit(1317467868.362:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=685 comm="apparmor_parser"
[   18.263351] type=1400 audit(1317467868.372:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[   18.263811] type=1400 audit(1317467868.372:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   18.264090] type=1400 audit(1317467868.372:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[   18.450744] type=1400 audit(1317467868.562:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=687 comm="apparmor_parser"
[   18.454779] type=1400 audit(1317467868.562:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=706 comm="apparmor_parser"
[   18.484292] type=1400 audit(1317467868.592:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=706 comm="apparmor_parser"
[   18.742954] eth1: link up, 100Mbps, full-duplex, lpa 0x4DE1
[   19.872326] [drm] Initialized drm 1.1.0 20060810
[   19.899250] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.904675] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   19.904682] [drm] No driver support for vblank timestamp query.
[   19.904687] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   19.907408] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   19.907431] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   19.907495] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   20.032077] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   24.016475] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   29.700009] eth1: no IPv6 routers present
[   80.540235] Marking TSC unstable due to cpufreq changes
[   80.540302] Switching to clocksource acpi_pm
[ 5176.127679] powernow-k8: Hardware error - pending bit very stuck - no further pstate changes possible
[ 5176.128559] powernow-k8: transition frequency failed
[ 5176.230042] powernow-k8: failing targ, change pending bit set
[10151.330056] powernow-k8: error - out of sync, fix 0xa 0xc, vid 0x1 0x1
[10151.330068] powernow-k8: ph2 null fid transition 0xc

```

---

### Post by haggar47 on 2011-10-01
What do I do with the updated dmesg??

---

### Post by ubudog on 2011-10-01
Nothing changed, I just put the output in code brackets to make it look nicer.

Anyway, do you see anything in Additional Drivers?  

In 11.04 and up: Search for "Drivers"
In 10.10 and down: System>Administration>Additional Drivers

---

### Post by haggar47 on 2011-10-01
> **ubudog said:**
> Nothing changed, I just put the output in code brackets to make it look nicer.

Anyway, do you see anything in Additional Drivers?  

In 11.04 and up: Search for "Drivers"
In 10.10 and down: System>Administration>Additional Drivers

Nothing appears under the search for drivers.

The latest dmesg, with the usb drive in:  powernow-k8:failing targ, change pending bit set (10.5 pages of this error).  

powernow-k8: error-out of sync, fix 0xc 0xa, vid 0x2 0x2

powernow-k8:  ph2 null fid transition 0xa

hub 1-1:1.0: unable to enumerate USB device on port 7

I also downloaded the MSI K8M Neo-V drivers:  VIA K8M800 + zchipset 8237, but I don't believe they installed properly.

Thank you very much for trying to solve this problem!

---

### Post by ubudog on 2011-10-01
Hmm... are you using a USB extension?  (a dongle that provides like 4 extra ports)

---

### Post by haggar47 on 2011-10-01
No, I am putting the thumbdrive into an onboard USB port.  Nothing I plug into the onboard USB ports will work, but it does stop my mouse from working.

---

### Post by ubudog on 2011-10-01
This is a desktop computer, right?

PS: [This]("http://ubuntuforums.org/showthread.php?t=1695464") thread might help.

---

### Post by haggar47 on 2011-10-05
Yes.  I should have said a USB device (keyboard, mouse), not a thumbdrive.  Sorry!
 
I have a new post "Unable to Install from CD"  Would you please read it and see if might be able to help?
 
I did not understand the first reply.
 
Is there a Ubuntu format driver to down load?
 
Thanks for your reply!

---

