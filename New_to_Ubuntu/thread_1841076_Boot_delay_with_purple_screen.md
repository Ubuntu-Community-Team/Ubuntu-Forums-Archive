---
title: "Boot delay with purple screen"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by pappusarkar on 2011-09-08
My system takes 40-45 seconds to boot natty.
When I select 11.04 ( Ubuntu & Windows 7) in GRUB2,I get a purple screen.it is really annoying.Can I speed up my boot if not then how do I get rid of that purple stuff?

BIOS Setup-
ACPI = OFF
APIC = OFF
USB LEGACY = OFF

Tweaks in ubuntu-
Uninstalled softwares like Gwibber,Unneeded fonts etc.

My config is 
AMD Phenom 2 X4 955 BE 3.2 Ghz
M4N68T-M
4 GB DDR3
ATI 5770
500 WD Green (1 Ext4 = 200 GB, 1 Ext3 = 50 GB, 1 NTFS = 200GB)

I'm new to linux and do not understand the lines.sort this out for me! 
dmesg.log file says

[    0.161501] pci 0000:01:07.0: PME# supported from D1 D2 D3hot
[    0.161504] pci 0000:01:07.0: PME# disabled
[    0.161527] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.161530] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.161532] pci 0000:00:04.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.161534] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.161536] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.161538] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.161539] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.161541] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.161543] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.161545] pci 0000:00:04.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.161566] pci 0000:02:00.0: [1002:68b8] type 0 class 0x000300
[    0.161576] pci 0000:02:00.0: reg 10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.161583] pci 0000:02:00.0: reg 18: [mem 0xdffe0000-0xdfffffff 64bit]
[    0.161588] pci 0000:02:00.0: reg 20: [io  0xe800-0xe8ff]
[    0.161596] pci 0000:02:00.0: reg 30: [mem 0xdffc0000-0xdffdffff pref]
[    0.161608] pci 0000:02:00.0: supports D1 D2
[    0.161623] pci 0000:02:00.1: [1002:aa58] type 0 class 0x000403
[    0.161632] pci 0000:02:00.1: reg 10: [mem 0xdffbc000-0xdffbffff 64bit]
[    0.161661] pci 0000:02:00.1: supports D1 D2
[    0.180014] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.180017] pci 0000:00:09.0:   bridge window [io  0xe000-0xefff]
[    0.180019] pci 0000:00:09.0:   bridge window [mem 0xdff00000-0xdfffffff]
[    0.180022] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.180040] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.180043] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.180045] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.180047] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180063] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.180066] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.180068] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.180070] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.180190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.180208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.180225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.180303]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.183071] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183103] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 *10 11 14)
[    0.183133] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183163] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183193] ACPI: PCI Interrupt Link [LNEA] (IRQs *5 7 10 11 14)
[    0.183224] ACPI: PCI Interrupt Link [LNEB] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183254] ACPI: PCI Interrupt Link [LNEC] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183284] ACPI: PCI Interrupt Link [LNED] (IRQs 5 7 10 *11 14)
[    0.183313] ACPI: PCI Interrupt Link [LUB0] (IRQs *5 7 10 11 14)
[    0.183343] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 10 *11 14)
[    0.183372] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 10 11 14)
[    0.183402] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 *10 11 14)
[    0.183431] ACPI: PCI Interrupt Link [LMC9] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183461] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 *10 11 14)
[    0.183491] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183521] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 10 *11 14)
[    0.183550] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 10 *11 14)
[    0.183587] ACPI: PCI Interrupt Link [LATA] (IRQs 5 7 10 11 14) *0, disabled.
[    0.183646] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.183648] vgaarb: loaded
[    0.183747] SCSI subsystem initialized
[    0.183777] libata version 3.00 loaded.
[    0.183806] usbcore: registered new interface driver usbfs
[    0.183812] usbcore: registered new interface driver hub
[    0.183826] usbcore: registered new device driver usb
[    0.183885] wmi: Mapper loaded
[    0.183887] PCI: Using ACPI for IRQ routing
[    0.183888] PCI: pci_cache_line_size set to 64 bytes
[    0.183924] reserve RAM buffer: 000000000009b400 - 000000000009ffff 
[    0.183926] reserve RAM buffer: 00000000bffa0000 - 00000000bfffffff 
[    0.183981] NetLabel: Initializing
[    0.183983] NetLabel:  domain hash size = 128
[    0.183984] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.183991] NetLabel:  unlabeled traffic allowed by default
[    0.184011] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.184016] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.184019] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.190036] Switching to clocksource hpet
[    0.193912] AppArmor: AppArmor Filesystem Enabled
[    0.193930] pnp: PnP ACPI init
[    0.193939] ACPI: bus type pnp registered
[    0.194005] pnp 00:00: [bus 00-ff]
[    0.194007] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.194008] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.194010] pnp 00:00: [io  0x0d00-0xffff window]
[    0.194012] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.194013] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.194015] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.194016] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.194043] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.194062] pnp 00:01: [dma 4]
[    0.194063] pnp 00:01: [io  0x0000-0x000f]
[    0.194065] pnp 00:01: [io  0x0081-0x0083]
[    0.194066] pnp 00:01: [io  0x0087]
[    0.194067] pnp 00:01: [io  0x0089-0x008b]
[    0.194068] pnp 00:01: [io  0x008f]
[    0.194069] pnp 00:01: [io  0x00c0-0x00df]
[    0.194084] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.194090] pnp 00:02: [io  0x0070-0x0071]
[    0.194092] pnp 00:02: [irq 8]
[    0.194105] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.194111] pnp 00:03: [io  0x0061]
[    0.194124] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.194130] pnp 00:04: [io  0x00f0-0x00ff]
[    0.194131] pnp 00:04: [irq 13]
[    0.194143] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.194625] pnp 00:05: [io  0x0378-0x037f]
[    0.194626] pnp 00:05: [irq 7]
[    0.194628] pnp 00:05: [dma 0 disabled]
[    0.194794] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.195028] pnp 00:06: [mem 0x000d0000-0x000d3fff window]
[    0.195029] pnp 00:06: [mem 0x000d4000-0x000d7fff window]
[    0.195031] pnp 00:06: [mem 0x000de000-0x000dffff window]
[    0.195032] pnp 00:06: [io  0x0010-0x001f]
[    0.195034] pnp 00:06: [io  0x0022-0x003f]
[    0.195035] pnp 00:06: [io  0x0044-0x004d]
[    0.195036] pnp 00:06: [io  0x0050-0x005f]
[    0.195037] pnp 00:06: [io  0x0062-0x0063]
[    0.195038] pnp 00:06: [io  0x0065-0x006f]
[    0.195039] pnp 00:06: [io  0x0072-0x007f]
[    0.195041] pnp 00:06: [io  0x0080]
[    0.195042] pnp 00:06: [io  0x0084-0x0086]
[    0.195043] pnp 00:06: [io  0x0088]
[    0.195044] pnp 00:06: [io  0x008c-0x008e]
[    0.195045] pnp 00:06: [io  0x0090-0x009f]
[    0.195046] pnp 00:06: [io  0x00a2-0x00bf]
[    0.195048] pnp 00:06: [io  0x00e0-0x00ef]
[    0.195049] pnp 00:06: [io  0x04d0-0x04d1]
[    0.195050] pnp 00:06: [io  0x0800-0x080f]
[    0.195051] pnp 00:06: [io  0x0500-0x057f]
[    0.195052] pnp 00:06: [io  0x0580-0x05ff]
[    0.195053] pnp 00:06: [io  0x0800-0x087f]
[    0.195055] pnp 00:06: [io  0x0880-0x08ff]
[    0.195056] pnp 00:06: [io  0x0d00-0x0d7f]
[    0.195057] pnp 00:06: [io  0x0d80-0x0dff]
[    0.195058] pnp 00:06: [io  0x0900-0x097f]
[    0.195059] pnp 00:06: [io  0x0980-0x09ff]
[    0.195061] pnp 00:06: [io  0x1100-0x117f]
[    0.195062] pnp 00:06: [io  0x1180-0x11ff]
[    0.195063] pnp 00:06: [mem 0xfec80000-0x1fd93ffff]
[    0.195065] pnp 00:06: [mem 0xfefe0000-0xfefe01ff]
[    0.195066] pnp 00:06: [mem 0xfefe1000-0xfefe1fff]
[    0.195067] pnp 00:06: [mem 0xfee01000-0xfeefffff]
[    0.195072] pnp 00:06: disabling [io  0x0900-0x097f] because it overlaps 0000:00:01.0 BAR 0 [io  0x0900-0x09ff]
[    0.195074] pnp 00:06: disabling [io  0x0980-0x09ff] because it overlaps 0000:00:01.0 BAR 0 [io  0x0900-0x09ff]
[    0.195128] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.195130] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.195132] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.195134] system 00:06: [io  0x0580-0x05ff] has been reserved
[    0.195135] system 00:06: [io  0x0800-0x087f] could not be reserved
[    0.195137] system 00:06: [io  0x0880-0x08ff] has been reserved
[    0.195139] system 00:06: [io  0x0d00-0x0d7f] has been reserved
[    0.195140] system 00:06: [io  0x0d80-0x0dff] has been reserved
[    0.195142] system 00:06: [io  0x1100-0x117f] has been reserved
[    0.195144] system 00:06: [io  0x1180-0x11ff] has been reserved
[    0.195146] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.195148] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.195149] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved
[    0.195151] system 00:06: [mem 0xfec80000-0x1fd93ffff] could not be reserved
[    0.195153] system 00:06: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.195155] system 00:06: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.195157] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.195159] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.195202] pnp 00:07: [mem 0xfed00000-0xfed00fff]
[    0.195217] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.195255] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.195256] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.195257] pnp 00:08: [mem 0xc0000000-0xbfffffff disabled]
[    0.195281] system 00:08: [mem 0xfec00000-0xfec00fff] has been reserved
[    0.195283] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.195285] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.195301] pnp 00:09: [io  0x0060]
[    0.195302] pnp 00:09: [io  0x0064]
[    0.195304] pnp 00:09: [irq 1]
[    0.195320] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.195418] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.195419] pnp 00:0a: [io  0x0230-0x023f]
[    0.195421] pnp 00:0a: [io  0x0290-0x029f]
[    0.195422] pnp 00:0a: [io  0x0a00-0x0a0f]
[    0.195423] pnp 00:0a: [io  0x0a30-0x0a3f]
[    0.195448] system 00:0a: [io  0x0230-0x023f] has been reserved
[    0.195450] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.195452] system 00:0a: [io  0x0a00-0x0a0f] has been reserved
[    0.195454] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.195455] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.195799] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.195800] pnp 00:0b: [irq 4]
[    0.195801] pnp 00:0b: [dma 0 disabled]
[    0.195848] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.195874] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.195897] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.195899] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.195975] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.195977] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.195978] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.195980] pnp 00:0d: [mem 0x00100000-0xbfffffff]
[    0.195981] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.196008] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.196010] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    0.196012] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.196014] system 00:0d: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.196016] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.196017] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.196195] pnp: PnP ACPI: found 14 devices
[    0.196196] ACPI: ACPI bus type pnp unregistered
[    0.199963] Switched to NOHz mode on CPU #0
[    0.201672] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.201674] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.201677] pci 0000:00:04.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.201679] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.201683] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.201685] pci 0000:00:09.0:   bridge window [io  0xe000-0xefff]
[    0.201687] pci 0000:00:09.0:   bridge window [mem 0xdff00000-0xdfffffff]
[    0.201689] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.201692] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.201693] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.201695] pci 0000:00:0b.0:   bridge window [mem disabled]
[    0.201697] pci 0000:00:0b.0:   bridge window [mem pref disabled]
[    0.201699] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.201700] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.201702] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.201704] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.201709] pci 0000:00:04.0: setting latency timer to 64
[    0.201712] pci 0000:00:09.0: setting latency timer to 64
[    0.201715] pci 0000:00:0b.0: setting latency timer to 64
[    0.201718] pci 0000:00:0c.0: setting latency timer to 64
[    0.201721] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.201722] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.201724] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.201725] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.201727] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.201729] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.201730] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.201732] pci_bus 0000:01: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.201733] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.201735] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.201737] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.201738] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.201740] pci_bus 0000:01: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.201742] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.201743] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.201745] pci_bus 0000:02: resource 1 [mem 0xdff00000-0xdfffffff]
[    0.201747] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.201769] NET: Registered protocol family 2
[    0.201855] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.202620] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.204841] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.205116] TCP: Hash tables configured (established 524288 bind 65536)
[    0.205118] TCP reno registered
[    0.205125] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.205151] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.205222] NET: Registered protocol family 1
[    0.205327] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205371] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205422] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205472] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205522] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205575] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205632] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205691] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.205702] pci 0000:02:00.0: Boot video device
[    0.205706] PCI: CLS 64 bytes, default 64
[    0.205848] Trying to unpack rootfs image as initramfs...
[    0.250053] PCI-DMA: Disabling AGP.
[    0.252406] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    0.252407] PCI-DMA: using GART IOMMU.
[    0.252409] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.255371] audit: initializing netlink socket (disabled)
[    0.255379] type=2000 audit(1315535564.250:1): initialized
[    0.270286] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.281178] VFS: Disk quotas dquot_6.5.2
[    0.281212] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.281592] fuse init (API version 7.16)
[    0.281645] msgmni has been set to 7898
[    0.290183] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.290203] io scheduler noop registered
[    0.290205] io scheduler deadline registered
[    0.290229] io scheduler cfq registered (default)
[    0.290310] pcieport 0000:00:09.0: setting latency timer to 64
[    0.290331] pcieport 0000:00:09.0: irq 16 for MSI/MSI-X
[    0.290372] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.290386] pcieport 0000:00:0b.0: irq 17 for MSI/MSI-X
[    0.290421] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.290434] pcieport 0000:00:0c.0: irq 18 for MSI/MSI-X
[    0.290474] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.290488] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.290576] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.290579] ACPI: Power Button [PWRB]
[    0.290608] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.290610] ACPI: Power Button [PWRF]
[    0.290690] ACPI: acpi_idle registered with cpuidle
[    0.291974] ERST: Table is not found!
[    0.292015] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.312506] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.361075] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.380350] Linux agpgart interface v0.103
[    0.381001] brd: module loaded
[    0.381300] loop: module loaded
[    0.381359] i2c-core: driver [adp5520] using legacy suspend method
[    0.381360] i2c-core: driver [adp5520] using legacy resume method
[    0.381491] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.381588] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 11
[    0.381589] PCI: setting IRQ 11 as level-triggered
[    0.381593] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 11 (level, low) -> IRQ 11
[    0.381608] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.381612] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.381673] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 11
[    0.381675] pata_acpi 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 11 (level, low) -> IRQ 11
[    0.381684] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.381688] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.390254] Fixed MDIO Bus: probed
[    0.390273] PPP generic driver version 2.4.2
[    0.390304] tun: Universal TUN/TAP device driver, 1.6
[    0.390305] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.390353] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.390432] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
[    0.390434] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 11 (level, low) -> IRQ 11
[    0.390446] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.390448] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.390470] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.390490] ehci_hcd 0000:00:02.1: debug port 1
[    0.390496] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.390504] ehci_hcd 0000:00:02.1: irq 11, io mem 0xdfdfac00
[    0.410022] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.410139] hub 1-0:1.0: USB hub found
[    0.410142] hub 1-0:1.0: 10 ports detected
[    0.410211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.420280] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 5
[    0.420283] PCI: setting IRQ 5 as level-triggered
[    0.420287] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 5 (level, low) -> IRQ 5
[    0.420303] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.420306] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.420342] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.420357] ohci_hcd 0000:00:02.0: irq 5, io mem 0xdfdfb000
[    0.441196] Freeing initrd memory: 12864k freed
[    0.482145] hub 2-0:1.0: USB hub found
[    0.482150] hub 2-0:1.0: 10 ports detected
[    0.482213] uhci_hcd: USB Universal Host Controller Interface driver
[    0.482289] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.482291] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.482415] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.482462] mousedev: PS/2 mouse device common for all mice
[    0.482530] rtc_cmos 00:02: RTC can wake from S4
[    0.482559] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.482584] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.482641] device-mapper: uevent: version 1.0.3
[    0.482683] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.482754] device-mapper: multipath: version 1.2.0 loaded
[    0.482756] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.482816] cpuidle: using governor ladder
[    0.482817] cpuidle: using governor menu
[    0.482959] TCP cubic registered
[    0.483031] NET: Registered protocol family 10
[    0.483306] NET: Registered protocol family 17
[    0.483315] Registering the dns_resolver key type
[    0.483329] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (1 cpu cores) (version 2.20.00)
[    0.483357] powernow-k8:    0 : pstate 0 (3200 MHz)
[    0.483358] powernow-k8:    1 : pstate 1 (2500 MHz)
[    0.483359] powernow-k8:    2 : pstate 2 (2100 MHz)
[    0.483360] powernow-k8:    3 : pstate 3 (800 MHz)
[    0.483434] PM: Hibernation image not present or could not be loaded.
[    0.483443] registered taskstats version 1
[    0.483593]   Magic number: 11:380:510
[    0.483622] pci 0000:00:01.2: hash matches
[    0.483666] rtc_cmos 00:02: setting system clock to 2011-09-09 02:32:44 UTC (1315535564)
[    0.483668] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.483669] EDD information not available.
[    0.484815] Freeing unused kernel memory: 956k freed
[    0.485075] Write protecting the kernel read-only data: 10240k
[    0.485602] Freeing unused kernel memory: 184k freed
[    0.489066] Freeing unused kernel memory: 1440k freed
[    0.500346] <30>udev[93]: starting version 167
[    0.503588] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.593810] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.607461] sata_nv 0000:00:08.0: version 3.5
[    0.607470] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 11 (level, low) -> IRQ 11
[    0.607501] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.609905] scsi0 : sata_nv
[    0.611641] scsi1 : sata_nv
[    0.611726] ata1: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 11
[    0.611728] ata2: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 11
[    0.614372] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 11 (level, low) -> IRQ 11
[    0.614394] sata_nv 0000:00:08.1: setting latency timer to 64
[    0.616361] scsi2 : sata_nv
[    0.617665] scsi3 : sata_nv
[    0.617740] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb000 irq 11
[    0.617742] ata4: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xb008 irq 11
[    0.619759] pata_amd 0000:00:06.0: version 0.4.1
[    0.619780] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.621224] scsi4 : pata_amd
[    0.622188] 8139cp 0000:01:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.622278] scsi5 : pata_amd
[    0.622553] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.622555] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.622695] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.622761] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 5
[    0.622764] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 5 (level, low) -> IRQ 5
[    0.622766] forcedeth 0000:00:07.0: setting latency timer to 64
[    0.701015] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 20:cf:30:c8:b3:0c
[    0.701017] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    0.950411] ata1: SATA link down (SStatus 0 SControl 300)
[    1.010026] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.100043] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.120824] ata3.00: ATA-8: WDC WD5000AAKX-001CA0, 15.01H15, max UDMA/133
[    1.120826] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.160858] ata3.00: configured for UDMA/133
[    1.250025] Refined TSC clocksource calibration: 3214.619 MHz.
[    1.250029] Switching to clocksource tsc
[    1.290323] ata2: SATA link down (SStatus 0 SControl 300)
[    1.290404] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    1.290491] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.290610] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.290635] sd 2:0:0:0: [sda] Write Protect is off
[    1.290637] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.290648] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.307921]  sda: sda1 sda2 sda3
[    1.308124] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.780036] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.800114] ata4.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    1.840114] ata4.00: configured for UDMA/100
[    1.848700] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    1.857137] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.857139] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.857201] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.857233] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.857271] ata6: port disabled. ignoring.
[    1.858834] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.862655] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    1.862657] PCI: setting IRQ 10 as level-triggered
[    1.862662] 8139too 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    1.863292] 8139too 0000:01:07.0: eth1: RealTek RTL8139 at 0xd800, 00:e0:1c:3d:ca:c2, IRQ 10
[    1.874176] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
[    1.874256] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2/input0
[    1.874265] usbcore: registered new interface driver usbhid
[    1.874266] usbhid: USB HID core driver
[    7.197446] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    9.195571] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    9.786957] <30>udev[436]: starting version 167
[   10.829285] <30>udev[507]: renamed network interface eth1 to eth2
[   10.932185] lp: driver loaded but no devices found
[   10.946526] parport_pc 00:05: reported by Plug and Play ACPI
[   10.946567] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.020121] lp0: using parport0 (interrupt-driven).
[   11.090195] ACPI: resource nForce2_smbus [io  0x0600-0x063f] conflicts with ACPI region SMRG [io 0x600-0x6ff]
[   11.090197] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.090263] i2c i2c-0: nForce2 SMBus adapter at 0x700
[   11.134002] ppdev: user-space parallel port driver
[   11.196260] MCE: In-kernel MCE decoding enabled.
[   11.213854] EDAC MC: Ver: 2.1.0 Jul 29 2011
[   11.254220] EDAC amd64_edac: v3.3.0
[   11.254716] EDAC amd64: DRAM ECC disabled.
[   11.254719] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   11.254720]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   11.254721]  (Note that use of the override may cause unknown side effects.)
[   11.351258] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.351261] Disabling lock debugging due to kernel taint
[   11.389520] [fglrx] Maximum main memory to use for locked dma buffers: 3802 MBytes.
[   11.389559] [fglrx]   vendor: 1002 device: 68b8 count: 1
[   11.389725] [fglrx] ioport: bar 4, base 0xe800, size: 0x100
[   11.389808] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 11
[   11.389811] pci 0000:02:00.0: PCI INT A -> Link[LNED] -> GSI 11 (level, low) -> IRQ 11
[   11.389815] pci 0000:02:00.0: setting latency timer to 64
[   11.389969] [fglrx] Kernel PAT support is enabled
[   11.389982] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   11.707831] type=1400 audit(1315515775.717:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=687 comm="apparmor_parser"
[   11.708074] type=1400 audit(1315515775.717:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=687 comm="apparmor_parser"
[   11.708234] type=1400 audit(1315515775.717:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=687 comm="apparmor_parser"
[   11.708532] type=1400 audit(1315515775.717:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=688 comm="apparmor_parser"
[   11.708774] type=1400 audit(1315515775.717:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=688 comm="apparmor_parser"
[   11.708932] type=1400 audit(1315515775.717:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=688 comm="apparmor_parser"
[   11.709224] type=1400 audit(1315515775.717:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=752 comm="apparmor_parser"
[   11.709463] type=1400 audit(1315515775.717:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=752 comm="apparmor_parser"
[   11.709620] type=1400 audit(1315515775.717:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=752 comm="apparmor_parser"
[   12.342086] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   12.342091] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 10 (level, low) -> IRQ 10
[   12.342093] hda_intel: Disable MSI for Nvidia chipset
[   12.342112] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.507687] type=1400 audit(1315515777.507:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=904 comm="apparmor_parser"
[   14.460436] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 5
[   14.460440] HDA Intel 0000:02:00.1: PCI INT B -> Link[LNEA] -> GSI 5 (level, low) -> IRQ 5
[   14.460487] HDA Intel 0000:02:00.1: irq 19 for MSI/MSI-X
[   14.460502] HDA Intel 0000:02:00.1: setting latency timer to 64
[   14.503147] hda-intel: Enable sync_write for AMD chipset
[   14.952556] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[   15.266302] forcedeth 0000:00:07.0: irq 20 for MSI/MSI-X
[   15.266482] forcedeth 0000:00:07.0: eth0: no link during initialization
[   15.268718] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.598057] vboxdrv: Found 1 processor cores.
[   15.600196] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.600198] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   18.738623] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   20.223384] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90012a80000, using 3904k, total 3904k
[   20.223387] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[   20.223388] vesafb: scrolling: redraw
[   20.223390] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   20.223503] Console: switching to colour frame buffer device 144x54
[   20.223519] fb0: VESA VGA frame buffer device
[   20.263831] audit_printk_skb: 33 callbacks suppressed
[   20.263833] type=1400 audit(1315515784.267:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1338 comm="apparmor_parser"
[   20.264141] type=1400 audit(1315515784.267:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1338 comm="apparmor_parser"
[   21.655523] fglrx_pci 0000:02:00.0: irq 21 for MSI/MSI-X
[   21.655959] [fglrx] Firegl kernel thread PID: 1419
[   21.655990] [fglrx] Firegl kernel thread PID: 1420
[   21.656018] [fglrx] Firegl kernel thread PID: 1421
[   21.656189] [fglrx] IRQ 21 Enabled
[   21.889129] [fglrx] Gart USWC size:1240 M.
[   21.889131] [fglrx] Gart cacheable size:491 M.
[   21.889135] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   21.889136] [fglrx] Reserved FB block: Unshared offset:f91d000, size:3e3000 
[   21.889138] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   37.361968] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   43.138482] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0

---

### Post by snip3r8 on 2011-09-08
I also get the purple screen and the delay ,but not as long as 45 seconds

---

### Post by aura7 on 2011-09-08
Install Startup-manager and you can customize your boot screen as you want.

---

### Post by Mark Phelps on 2011-09-09
> **aura7 said:**
> Install Startup-manager and you can customize your boot screen as you want.

Startup-manager does not work well with the more recent versions of GRUB2, specifically, v1.99RC.  If you want to customize GUB, would do better using Grub-customizer.

---

