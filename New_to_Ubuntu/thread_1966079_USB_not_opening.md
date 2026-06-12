---
title: "USB not opening"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by ssdt on 2012-04-26
I got this one USB drive that does not open, doesn't show me a message. It virtually does nothing in any computer that I try. I have tried it in Windows and Ubuntu. I have tried different ports for it and still it doesn't work.

Does anyone know a possible way to solve the problem?

---

### Post by calavier62 on 2012-04-27
It sounds like the drive could be dead. One thing to check would be to crack it open and see if any of the four contacts near the usb plug on the end have broken/become unsoldered. If so, it's an easy 5 minute fix to simply re solder the pins on the drive.

If that's not the case, then there's not too much you can do. USB drives are built using nanotechnology, and it's basically impossible for a human to work on.

---

### Post by lechien73 on 2012-04-27
Depending on the make of the drive, there may be something you can to do fix it. Sometimes a drive may fail to appear or mount in Ubuntu because the size is being misreported.

Could you plug in the drive, open a terminal window and run:

```
lsusb
```

Please post the output here. Additionally, runnning:

```
dmesg
```

will likely give more debugging information.

---

### Post by garvinrick4 on 2012-04-27
Sometimes they just die. If they are used as a linux install and used a lot they die even quicker.
Good thing they are getting dead cheap nowadays. Sorry I could not help but If you can put it in a USB port
and then open gparted and if you can select it in upper right and format it to fat32 maybe it can be saved
only if it has no format right now.
If no gparted:
```
sudo apt-get install gparted
```
It is a powerfull partitioning tool go slow and be carefull. Need to hit green apply arrow before it does what you specify.

---

### Post by ssdt on 2012-04-29
Here's the output of lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 005 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000

```

for dmseg:
```
[    0.171166]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.171169]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.171171] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.180642] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.180690] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.180736] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.180781] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.180829] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.180874] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.180919] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.180964] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.181079] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.181090] vgaarb: loaded
[    0.181091] vgaarb: bridge control possible 0000:00:02.0
[    0.181209] i2c-core: driver [aat2870] using legacy suspend method
[    0.181210] i2c-core: driver [aat2870] using legacy resume method
[    0.181294] SCSI subsystem initialized
[    0.184259] libata version 3.00 loaded.
[    0.184259] usbcore: registered new interface driver usbfs
[    0.184259] usbcore: registered new interface driver hub
[    0.184259] usbcore: registered new device driver usb
[    0.184265] PCI: Using ACPI for IRQ routing
[    0.190367] PCI: pci_cache_line_size set to 64 bytes
[    0.190437] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.190440] reserve RAM buffer: 000000007f590000 - 000000007fffffff 
[    0.190554] NetLabel: Initializing
[    0.190556] NetLabel:  domain hash size = 128
[    0.190557] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.190568] NetLabel:  unlabeled traffic allowed by default
[    0.190623] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.190628] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.190633] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.200081] Switching to clocksource hpet
[    0.207821] AppArmor: AppArmor Filesystem Enabled
[    0.207860] pnp: PnP ACPI init
[    0.207879] ACPI: bus type pnp registered
[    0.207974] pnp 00:00: [bus 00-ff]
[    0.207977] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.207980] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.207982] pnp 00:00: [io  0x0d00-0xffff window]
[    0.207984] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.207986] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.207988] pnp 00:00: [mem 0x7f600000-0xfebfffff window]
[    0.208082] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.208143] pnp 00:01: [io  0x0010-0x001f]
[    0.208145] pnp 00:01: [io  0x0022-0x003f]
[    0.208147] pnp 00:01: [io  0x0044-0x005f]
[    0.208149] pnp 00:01: [io  0x0060]
[    0.208150] pnp 00:01: [io  0x0064]
[    0.208152] pnp 00:01: [io  0x0062-0x0063]
[    0.208154] pnp 00:01: [io  0x0065-0x006f]
[    0.208156] pnp 00:01: [io  0x0074-0x007f]
[    0.208157] pnp 00:01: [io  0x0091-0x0093]
[    0.208159] pnp 00:01: [io  0x00a2-0x00bf]
[    0.208161] pnp 00:01: [io  0x00e0-0x00ef]
[    0.208163] pnp 00:01: [io  0x04d0-0x04d1]
[    0.208164] pnp 00:01: [io  0x0800-0x087f]
[    0.208166] pnp 00:01: [io  0x0290-0x0297]
[    0.208168] pnp 00:01: [io  0x0880-0x088f]
[    0.208231] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.208234] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.208236] system 00:01: [io  0x0290-0x0297] has been reserved
[    0.208239] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.208242] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.208253] pnp 00:02: [dma 4]
[    0.208255] pnp 00:02: [io  0x0000-0x000f]
[    0.208257] pnp 00:02: [io  0x0080-0x0090]
[    0.208261] pnp 00:02: [io  0x0094-0x009f]
[    0.208263] pnp 00:02: [io  0x00c0-0x00df]
[    0.208290] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.208339] pnp 00:03: [irq 0 disabled]
[    0.208350] pnp 00:03: [irq 8]
[    0.208352] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.208385] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.208410] pnp 00:04: [io  0x0070-0x0073]
[    0.208438] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.208447] pnp 00:05: [io  0x0061]
[    0.208474] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.208483] pnp 00:06: [io  0x00f0-0x00ff]
[    0.208488] pnp 00:06: [irq 13]
[    0.208523] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.208652] pnp 00:07: [io  0x03f0-0x03f5]
[    0.208654] pnp 00:07: [io  0x03f7]
[    0.208659] pnp 00:07: [irq 6]
[    0.208661] pnp 00:07: [dma 2]
[    0.208702] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.208752] pnp 00:08: [io  0x0400-0x04bf]
[    0.208797] system 00:08: [io  0x0400-0x04bf] has been reserved
[    0.208800] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.208817] pnp 00:09: [mem 0xffb80000-0xffbfffff]
[    0.208851] pnp 00:09: Plug and Play ACPI device, IDs INT0800 (active)
[    0.209029] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.209082] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.209085] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.209146] pnp 00:0b: [mem 0x000f0000-0x000fffff]
[    0.209149] pnp 00:0b: [mem 0x7f600000-0x7f6fffff]
[    0.209151] pnp 00:0b: [mem 0xfed00000-0xfed000ff]
[    0.209153] pnp 00:0b: [mem 0x7f590000-0x7f5fffff]
[    0.209154] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.209156] pnp 00:0b: [mem 0x00100000-0x7f58ffff]
[    0.209158] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.209160] pnp 00:0b: [mem 0xfed14000-0xfed1dfff]
[    0.209162] pnp 00:0b: [mem 0xfed20000-0xfed9ffff]
[    0.209164] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.209166] pnp 00:0b: [mem 0xffb00000-0xffb7ffff]
[    0.209168] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.209170] pnp 00:0b: [mem 0x000e0000-0x000effff]
[    0.209232] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.209235] system 00:0b: [mem 0x7f600000-0x7f6fffff] has been reserved
[    0.209237] system 00:0b: [mem 0xfed00000-0xfed000ff] has been reserved
[    0.209240] system 00:0b: [mem 0x7f590000-0x7f5fffff] could not be reserved
[    0.209242] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.209245] system 00:0b: [mem 0x00100000-0x7f58ffff] could not be reserved
[    0.209247] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.209250] system 00:0b: [mem 0xfed14000-0xfed1dfff] has been reserved
[    0.209252] system 00:0b: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.209255] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.209257] system 00:0b: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.209260] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.209262] system 00:0b: [mem 0x000e0000-0x000effff] has been reserved
[    0.209266] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.209274] pnp: PnP ACPI: found 12 devices
[    0.209275] ACPI: ACPI bus type pnp unregistered
[    0.209279] PnPBIOS: Disabled by ACPI PNP
[    0.245576] PCI: max bus depth: 1 pci_try_num: 2
[    0.245600] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.245604] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.245608] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.245611] pci 0000:00:01.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.245616] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.245619] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.245623] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.245627] pci 0000:00:1e.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.245652] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.245657] pci 0000:00:01.0: setting latency timer to 64
[    0.245664] pci 0000:00:1e.0: setting latency timer to 64
[    0.245668] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.245670] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.245672] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.245674] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.245677] pci_bus 0000:00: resource 8 [mem 0x7f600000-0xfebfffff]
[    0.245679] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.245681] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.245683] pci_bus 0000:01: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.245686] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.245688] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.245690] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.245692] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.245694] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.245697] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.245699] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000dffff]
[    0.245701] pci_bus 0000:02: resource 8 [mem 0x7f600000-0xfebfffff]
[    0.245747] NET: Registered protocol family 2
[    0.245824] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.246053] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.246493] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.246715] TCP: Hash tables configured (established 131072 bind 65536)
[    0.246717] TCP reno registered
[    0.246719] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.246729] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.246823] NET: Registered protocol family 1
[    0.246848] pci 0000:00:02.0: Boot video device
[    0.246864] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.246881] pci 0000:00:1a.0: PCI INT A disabled
[    0.246898] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.246914] pci 0000:00:1a.1: PCI INT B disabled
[    0.246923] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.246939] pci 0000:00:1a.2: PCI INT D disabled
[    0.246949] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.246975] pci 0000:00:1a.7: PCI INT C disabled
[    0.246987] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.247002] pci 0000:00:1d.0: PCI INT A disabled
[    0.247009] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.247024] pci 0000:00:1d.1: PCI INT B disabled
[    0.247031] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.247046] pci 0000:00:1d.2: PCI INT C disabled
[    0.247053] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.247066] pci 0000:00:1d.7: PCI INT A disabled
[    0.247080] PCI: CLS 64 bytes, default 64
[    0.247463] audit: initializing netlink socket (disabled)
[    0.247473] type=2000 audit(1335689476.240:1): initialized
[    0.270714] highmem bounce pool size: 64 pages
[    0.270720] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.279557] VFS: Disk quotas dquot_6.5.2
[    0.279628] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.280177] fuse init (API version 7.17)
[    0.280265] msgmni has been set to 1678
[    0.280561] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.280584] io scheduler noop registered
[    0.280586] io scheduler deadline registered
[    0.280593] io scheduler cfq registered (default)
[    0.280702] pcieport 0000:00:01.0: setting latency timer to 64
[    0.280734] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.280802] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.280827] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.280891] intel_idle: MWAIT substates: 0x22220
[    0.280893] intel_idle: does not run on family 6 model 23
[    0.280964] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.280969] ACPI: Power Button [PWRB]
[    0.281020] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.281023] ACPI: Power Button [PWRF]
[    0.281073] ACPI: Fan [FAN] (on)
[    0.282323] thermal LNXTHERM:00: registered as thermal_zone0
[    0.282326] ACPI: Thermal Zone [THRM] (40 C)
[    0.282365] ERST: Table is not found!
[    0.282366] GHES: HEST is not enabled!
[    0.282442] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.282562] isapnp: Scanning for PnP cards...
[    0.432681] Freeing initrd memory: 13788k freed
[    0.635458] isapnp: No Plug & Play device found
[    0.688493] Linux agpgart interface v0.103
[    0.688581] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.688639] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.689263] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.689384] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.690871] brd: module loaded
[    0.691629] loop: module loaded
[    0.691770] ata_piix 0000:00:1f.2: version 2.13
[    0.691784] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.691788] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.691824] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.692128] scsi0 : ata_piix
[    0.692206] scsi1 : ata_piix
[    0.692692] ata1: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    0.692697] ata2: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    0.692721] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.692726] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.692758] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.692959] scsi2 : ata_piix
[    0.693025] scsi3 : ata_piix
[    0.693233] ata3: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xec00 irq 19
[    0.693237] ata4: SATA max UDMA/133 cmd 0xee00 ctl 0xed00 bmdma 0xec08 irq 19
[    0.693597] Fixed MDIO Bus: probed
[    0.693618] tun: Universal TUN/TAP device driver, 1.6
[    0.693619] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.693673] PPP generic driver version 2.4.2
[    0.693779] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.693794] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.693808] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.693811] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.693852] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.693876] ehci_hcd 0000:00:1a.7: debug port 1
[    0.697746] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.697761] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdffe000
[    0.712021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.712164] hub 1-0:1.0: USB hub found
[    0.712169] hub 1-0:1.0: 6 ports detected
[    0.712236] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.712246] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.712249] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.712294] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.712315] ehci_hcd 0000:00:1d.7: debug port 1
[    0.716211] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.716224] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffd000
[    0.732020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.732151] hub 2-0:1.0: USB hub found
[    0.732155] hub 2-0:1.0: 6 ports detected
[    0.732222] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732234] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732250] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.732257] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.732260] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.732302] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.732333] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fd00
[    0.732448] hub 3-0:1.0: USB hub found
[    0.732452] hub 3-0:1.0: 2 ports detected
[    0.732514] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.732520] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.732523] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.732568] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.732597] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fc00
[    0.732709] hub 4-0:1.0: USB hub found
[    0.732712] hub 4-0:1.0: 2 ports detected
[    0.732770] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.732776] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.732779] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.732821] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.732842] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fb00
[    0.732957] hub 5-0:1.0: USB hub found
[    0.732961] hub 5-0:1.0: 2 ports detected
[    0.733019] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.733026] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.733028] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.733068] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.733088] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fa00
[    0.733203] hub 6-0:1.0: USB hub found
[    0.733207] hub 6-0:1.0: 2 ports detected
[    0.733263] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.733270] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.733273] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.733314] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.733335] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f900
[    0.733458] hub 7-0:1.0: USB hub found
[    0.733462] hub 7-0:1.0: 2 ports detected
[    0.733524] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.733530] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.733533] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.733575] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.733596] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f800
[    0.733711] hub 8-0:1.0: USB hub found
[    0.733714] hub 8-0:1.0: 2 ports detected
[    0.733829] usbcore: registered new interface driver libusual
[    0.733879] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.734230] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.734236] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.734358] mousedev: PS/2 mouse device common for all mice
[    0.734492] rtc_cmos 00:04: RTC can wake from S4
[    0.734586] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.734608] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.734674] device-mapper: uevent: version 1.0.3
[    0.734739] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.734769] EISA: Probing bus 0 at eisa.0
[    0.734773] EISA: Cannot allocate resource for mainboard
[    0.734775] Cannot allocate resource for EISA slot 1
[    0.734776] Cannot allocate resource for EISA slot 2
[    0.734778] Cannot allocate resource for EISA slot 3
[    0.734780] Cannot allocate resource for EISA slot 4
[    0.734781] Cannot allocate resource for EISA slot 5
[    0.734783] Cannot allocate resource for EISA slot 6
[    0.734785] Cannot allocate resource for EISA slot 7
[    0.734786] Cannot allocate resource for EISA slot 8
[    0.734788] EISA: Detected 0 cards.
[    0.734796] cpufreq-nforce2: No nForce2 chipset.
[    0.734798] cpuidle: using governor ladder
[    0.734800] cpuidle: using governor menu
[    0.734801] EFI Variables Facility v0.08 2004-May-17
[    0.735047] TCP cubic registered
[    0.735162] NET: Registered protocol family 10
[    0.735716] NET: Registered protocol family 17
[    0.735730] Registering the dns_resolver key type
[    0.735753] Using IPI No-Shortcut mode
[    0.735845] PM: Hibernation image not present or could not be loaded.
[    0.735858] registered taskstats version 1
[    0.744931]   Magic number: 8:353:878
[    0.745021] rtc_cmos 00:04: setting system clock to 2012-04-29 08:51:17 UTC (1335689477)
[    0.745470] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.745472] EDD information not available.
[    1.022585] ata3: SATA link down (SStatus 0 SControl 300)
[    1.033169] ata4: SATA link down (SStatus 0 SControl 300)
[    1.244017] Refined TSC clocksource calibration: 2493.749 MHz.
[    1.244024] Switching to clocksource tsc
[    1.384017] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[    1.488069] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.488079] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.488190] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.488202] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.488212] ata2.01: link offline, clearing class 3 to NONE
[    1.496251] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7200S, 102A, max UDMA/100
[    1.497173] ata1.00: ATA-8: WDC WD3200AAKS-75L9A0, 01.03E01, max UDMA/133
[    1.497179] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.512250] ata2.00: configured for UDMA/100
[    1.513181] ata1.00: configured for UDMA/133
[    1.513313] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-7 01.0 PQ: 0 ANSI: 5
[    1.513429] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.513467] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.513474] sd 0:0:0:0: [sda] Write Protect is off
[    1.513477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.513498] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.515190] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7200S 102A PQ: 0 ANSI: 5
[    1.517476] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.517481] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.517597] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.517711] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.561650]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.562054] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.562074] Freeing unused kernel memory: 712k freed
[    1.562317] Write protecting the kernel text: 5628k
[    1.562359] Write protecting the kernel read-only data: 2324k
[    1.576675] udevd[92]: starting version 175
[    1.598938] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.598941] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.599115] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.599126] e1000e 0000:00:19.0: setting latency timer to 64
[    1.599221] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    1.664151] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2
[    1.664284] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1a.1-1/input0
[    1.664302] usbcore: registered new interface driver usbhid
[    1.664304] usbhid: USB HID core driver
[    1.667820] FDC 0 is a post-1991 82077
[    1.788106] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:21:9b:2b:56:0e
[    1.788109] e1000e 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    1.788131] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 7, PBA No: FFFFFF-0FF
[    1.800021] usb 4-2: new low-speed USB device number 3 using uhci_hcd
[    1.992049] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3
[    1.992151] generic-usb 0003:413C:3012.0002: input,hidraw1: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1a.1-2/input0
[    2.097001] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.097004] EXT4-fs (sda6): write access will be enabled during recovery
[    2.232021] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    5.671982] EXT4-fs (sda6): recovery complete
[    5.672411] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   19.422417] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.435393] udevd[308]: starting version 175
[   19.475152] lp: driver loaded but no devices found
[   19.480351] [drm] Initialized drm 1.1.0 20060810
[   19.491366] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.491371] i915 0000:00:02.0: setting latency timer to 64
[   19.510840] Adding 2085884k swap on /dev/sda5.  Priority:-1 extents:1 across:2085884k 
[   19.528469] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   19.528475] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   19.528477] [drm] Driver supports precise vblank timestamp query.
[   19.556323] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   19.568178] [drm] initialized overlay support
[   19.616027] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   19.643490] fbcon: inteldrmfb (fb0) is primary device
[   19.643546] Console: switching to colour frame buffer device 180x56
[   19.643577] fb0: inteldrmfb frame buffer device
[   19.643579] drm: registered panic notifier
[   19.643591] No ACPI video bus found
[   19.643633] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.722402] Linux video capture interface: v2.00
[   19.726625] gspca_main: v2.14.0 registered
[   19.726966] gspca_main: sonixj-2.14.0 probing 045e:00f5
[   19.734005] input: sonixj as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/input/input4
[   19.734203] usbcore: registered new interface driver sonixj
[   19.796662] Bluetooth: Core ver 2.16
[   19.796684] NET: Registered protocol family 31
[   19.796686] Bluetooth: HCI device and connection manager initialized
[   19.796689] Bluetooth: HCI socket layer initialized
[   19.796691] Bluetooth: L2CAP socket layer initialized
[   19.796698] Bluetooth: SCO socket layer initialized
[   19.799108] ppdev: user-space parallel port driver
[   19.809323] type=1400 audit(1335703896.559:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=569 comm="apparmor_parser"
[   19.809715] type=1400 audit(1335703896.559:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=569 comm="apparmor_parser"
[   19.809935] type=1400 audit(1335703896.559:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=569 comm="apparmor_parser"
[   19.818108] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.818111] Bluetooth: BNEP filters: protocol multicast
[   19.857850] Bluetooth: RFCOMM TTY layer initialized
[   19.857860] Bluetooth: RFCOMM socket layer initialized
[   19.857862] Bluetooth: RFCOMM ver 1.11
[   19.901164] type=1400 audit(1335703896.651:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=646 comm="apparmor_parser"
[   19.901634] type=1400 audit(1335703896.651:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=646 comm="apparmor_parser"
[   19.935608] usbcore: registered new interface driver snd-usb-audio
[   19.956868] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.957003] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   19.957027] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.064220] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   20.082347] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.120088] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   20.120299] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.120621] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.149758] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.150052] init: failsafe main process (714) killed by TERM signal
[   20.230352] type=1400 audit(1335703896.979:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=934 comm="apparmor_parser"
[   20.230756] type=1400 audit(1335703896.979:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=934 comm="apparmor_parser"
[   20.230981] type=1400 audit(1335703896.979:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=934 comm="apparmor_parser"
[   20.445372] type=1400 audit(1335703897.195:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=933 comm="apparmor_parser"
[   20.468175] type=1400 audit(1335703897.219:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=937 comm="apparmor_parser"
[   20.639322] init: gdm main process (1069) killed by TERM signal
[   21.572766] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   21.572771] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   21.572928] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.807285] init: plymouth-stop pre-start process (1272) terminated with status 1
[   31.680015] eth0: no IPv6 routers present

```

---

### Post by ssdt on 2012-06-08
I formatted the usb with gparted and now for lsusb I get this message:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 005 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 002 Device 005: ID 0718:0611 Imation Corp. 

```

for dmesg i get this:
```

[    0.196233] pnp 00:02: [io  0x0094-0x009f]
[    0.196234] pnp 00:02: [io  0x00c0-0x00df]
[    0.196263] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.196309] pnp 00:03: [irq 0 disabled]
[    0.196321] pnp 00:03: [irq 8]
[    0.196323] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.196354] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.196379] pnp 00:04: [io  0x0070-0x0073]
[    0.196408] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.196416] pnp 00:05: [io  0x0061]
[    0.196448] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.196457] pnp 00:06: [io  0x00f0-0x00ff]
[    0.196462] pnp 00:06: [irq 13]
[    0.196498] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.196628] pnp 00:07: [io  0x03f0-0x03f5]
[    0.196631] pnp 00:07: [io  0x03f7]
[    0.196635] pnp 00:07: [irq 6]
[    0.196637] pnp 00:07: [dma 2]
[    0.196678] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.196731] pnp 00:08: [io  0x0400-0x04bf]
[    0.196779] system 00:08: [io  0x0400-0x04bf] has been reserved
[    0.196782] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.196799] pnp 00:09: [mem 0xffb80000-0xffbfffff]
[    0.196829] pnp 00:09: Plug and Play ACPI device, IDs INT0800 (active)
[    0.197004] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.197062] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.197065] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.197127] pnp 00:0b: [mem 0x000f0000-0x000fffff]
[    0.197129] pnp 00:0b: [mem 0x7f600000-0x7f6fffff]
[    0.197131] pnp 00:0b: [mem 0xfed00000-0xfed000ff]
[    0.197133] pnp 00:0b: [mem 0x7f590000-0x7f5fffff]
[    0.197135] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.197137] pnp 00:0b: [mem 0x00100000-0x7f58ffff]
[    0.197139] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.197141] pnp 00:0b: [mem 0xfed14000-0xfed1dfff]
[    0.197143] pnp 00:0b: [mem 0xfed20000-0xfed9ffff]
[    0.197145] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.197147] pnp 00:0b: [mem 0xffb00000-0xffb7ffff]
[    0.197149] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.197151] pnp 00:0b: [mem 0x000e0000-0x000effff]
[    0.197211] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.197214] system 00:0b: [mem 0x7f600000-0x7f6fffff] has been reserved
[    0.197216] system 00:0b: [mem 0xfed00000-0xfed000ff] has been reserved
[    0.197219] system 00:0b: [mem 0x7f590000-0x7f5fffff] could not be reserved
[    0.197222] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.197224] system 00:0b: [mem 0x00100000-0x7f58ffff] could not be reserved
[    0.197227] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.197229] system 00:0b: [mem 0xfed14000-0xfed1dfff] has been reserved
[    0.197232] system 00:0b: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.197234] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.197237] system 00:0b: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.197239] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.197242] system 00:0b: [mem 0x000e0000-0x000effff] has been reserved
[    0.197245] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.197253] pnp: PnP ACPI: found 12 devices
[    0.197255] ACPI: ACPI bus type pnp unregistered
[    0.197258] PnPBIOS: Disabled by ACPI PNP
[    0.233602] PCI: max bus depth: 1 pci_try_num: 2
[    0.233630] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.233634] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.233638] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.233641] pci 0000:00:01.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.233646] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.233649] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.233654] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.233658] pci 0000:00:1e.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.233683] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.233688] pci 0000:00:01.0: setting latency timer to 64
[    0.233696] pci 0000:00:1e.0: setting latency timer to 64
[    0.233700] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.233702] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.233704] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.233707] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.233709] pci_bus 0000:00: resource 8 [mem 0x7f600000-0xfebfffff]
[    0.233711] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.233714] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.233716] pci_bus 0000:01: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.233719] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.233721] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.233723] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.233725] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.233727] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.233730] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.233732] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000dffff]
[    0.233734] pci_bus 0000:02: resource 8 [mem 0x7f600000-0xfebfffff]
[    0.233780] NET: Registered protocol family 2
[    0.233854] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.234079] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.234529] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.234748] TCP: Hash tables configured (established 131072 bind 65536)
[    0.234750] TCP reno registered
[    0.234753] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.234762] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.234848] NET: Registered protocol family 1
[    0.234868] pci 0000:00:02.0: Boot video device
[    0.234885] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.234901] pci 0000:00:1a.0: PCI INT A disabled
[    0.234917] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.234933] pci 0000:00:1a.1: PCI INT B disabled
[    0.234942] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.234959] pci 0000:00:1a.2: PCI INT D disabled
[    0.234972] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.234997] pci 0000:00:1a.7: PCI INT C disabled
[    0.235010] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.235025] pci 0000:00:1d.0: PCI INT A disabled
[    0.235032] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.235047] pci 0000:00:1d.1: PCI INT B disabled
[    0.235054] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.235070] pci 0000:00:1d.2: PCI INT C disabled
[    0.235077] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.235090] pci 0000:00:1d.7: PCI INT A disabled
[    0.235104] PCI: CLS 64 bytes, default 64
[    0.235480] audit: initializing netlink socket (disabled)
[    0.235490] type=2000 audit(1339181110.228:1): initialized
[    0.258688] highmem bounce pool size: 64 pages
[    0.258694] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.267580] VFS: Disk quotas dquot_6.5.2
[    0.267650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.268203] fuse init (API version 7.17)
[    0.268289] msgmni has been set to 1678
[    0.268585] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.268610] io scheduler noop registered
[    0.268612] io scheduler deadline registered
[    0.268618] io scheduler cfq registered (default)
[    0.268729] pcieport 0000:00:01.0: setting latency timer to 64
[    0.268762] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.268829] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.268852] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.268916] intel_idle: MWAIT substates: 0x22220
[    0.268918] intel_idle: does not run on family 6 model 23
[    0.268994] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.268999] ACPI: Power Button [PWRB]
[    0.269051] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.269054] ACPI: Power Button [PWRF]
[    0.269101] ACPI: Fan [FAN] (on)
[    0.270345] thermal LNXTHERM:00: registered as thermal_zone0
[    0.270347] ACPI: Thermal Zone [THRM] (40 C)
[    0.270386] ERST: Table is not found!
[    0.270388] GHES: HEST is not enabled!
[    0.270464] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.270586] isapnp: Scanning for PnP cards...
[    0.424503] Freeing initrd memory: 13792k freed
[    0.623469] isapnp: No Plug & Play device found
[    0.676495] Linux agpgart interface v0.103
[    0.676583] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.676642] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.677263] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.677386] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.678849] brd: module loaded
[    0.679592] loop: module loaded
[    0.679732] ata_piix 0000:00:1f.2: version 2.13
[    0.679747] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.679751] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.679787] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.680096] scsi0 : ata_piix
[    0.680173] scsi1 : ata_piix
[    0.680657] ata1: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    0.680662] ata2: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    0.680686] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.680691] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.680723] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.680923] scsi2 : ata_piix
[    0.680990] scsi3 : ata_piix
[    0.681196] ata3: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xec00 irq 19
[    0.681200] ata4: SATA max UDMA/133 cmd 0xee00 ctl 0xed00 bmdma 0xec08 irq 19
[    0.681564] Fixed MDIO Bus: probed
[    0.681585] tun: Universal TUN/TAP device driver, 1.6
[    0.681586] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.681638] PPP generic driver version 2.4.2
[    0.681747] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.681761] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.681775] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.681778] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.681821] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.681847] ehci_hcd 0000:00:1a.7: debug port 1
[    0.685737] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.685751] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdffe000
[    0.700021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.700173] hub 1-0:1.0: USB hub found
[    0.700177] hub 1-0:1.0: 6 ports detected
[    0.700248] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.700258] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.700261] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.700305] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.700327] ehci_hcd 0000:00:1d.7: debug port 1
[    0.704202] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.704215] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffd000
[    0.720021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.720153] hub 2-0:1.0: USB hub found
[    0.720157] hub 2-0:1.0: 6 ports detected
[    0.720225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.720237] uhci_hcd: USB Universal Host Controller Interface driver
[    0.720253] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.720260] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.720263] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.720303] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.720338] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fd00
[    0.720453] hub 3-0:1.0: USB hub found
[    0.720457] hub 3-0:1.0: 2 ports detected
[    0.720516] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.720522] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.720525] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.720571] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.720599] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fc00
[    0.720712] hub 4-0:1.0: USB hub found
[    0.720716] hub 4-0:1.0: 2 ports detected
[    0.720774] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.720780] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.720783] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.720824] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.720845] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fb00
[    0.720957] hub 5-0:1.0: USB hub found
[    0.720960] hub 5-0:1.0: 2 ports detected
[    0.721019] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.721026] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.721029] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.721071] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.721092] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fa00
[    0.721212] hub 6-0:1.0: USB hub found
[    0.721215] hub 6-0:1.0: 2 ports detected
[    0.721274] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.721280] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.721283] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.721324] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.721345] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f900
[    0.721468] hub 7-0:1.0: USB hub found
[    0.721471] hub 7-0:1.0: 2 ports detected
[    0.721529] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.721535] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.721538] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.721580] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.721601] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f800
[    0.721714] hub 8-0:1.0: USB hub found
[    0.721718] hub 8-0:1.0: 2 ports detected
[    0.721832] usbcore: registered new interface driver libusual
[    0.721881] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.722224] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.722230] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.722352] mousedev: PS/2 mouse device common for all mice
[    0.722490] rtc_cmos 00:04: RTC can wake from S4
[    0.722587] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.722610] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.722675] device-mapper: uevent: version 1.0.3
[    0.722746] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.722778] EISA: Probing bus 0 at eisa.0
[    0.722780] EISA: Cannot allocate resource for mainboard
[    0.722782] Cannot allocate resource for EISA slot 1
[    0.722783] Cannot allocate resource for EISA slot 2
[    0.722785] Cannot allocate resource for EISA slot 3
[    0.722787] Cannot allocate resource for EISA slot 4
[    0.722788] Cannot allocate resource for EISA slot 5
[    0.722790] Cannot allocate resource for EISA slot 6
[    0.722792] Cannot allocate resource for EISA slot 7
[    0.722793] Cannot allocate resource for EISA slot 8
[    0.722795] EISA: Detected 0 cards.
[    0.722803] cpufreq-nforce2: No nForce2 chipset.
[    0.722804] cpuidle: using governor ladder
[    0.722806] cpuidle: using governor menu
[    0.722808] EFI Variables Facility v0.08 2004-May-17
[    0.723052] TCP cubic registered
[    0.723166] NET: Registered protocol family 10
[    0.723717] NET: Registered protocol family 17
[    0.723732] Registering the dns_resolver key type
[    0.723750] Using IPI No-Shortcut mode
[    0.723853] PM: Hibernation image not present or could not be loaded.
[    0.723863] registered taskstats version 1
[    0.733042]   Magic number: 0:745:796
[    0.733132] rtc_cmos 00:04: setting system clock to 2012-06-08 18:45:11 UTC (1339181111)
[    0.733584] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.733586] EDD information not available.
[    1.010585] ata3: SATA link down (SStatus 0 SControl 300)
[    1.021164] ata4: SATA link down (SStatus 0 SControl 300)
[    1.232019] Refined TSC clocksource calibration: 2493.749 MHz.
[    1.232026] Switching to clocksource tsc
[    1.364018] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[    1.476066] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.476077] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.476188] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.476201] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.476211] ata2.01: link offline, clearing class 3 to NONE
[    1.484206] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7200S, 102A, max UDMA/100
[    1.484819] ata1.00: ATA-8: WDC WD3200AAKS-75L9A0, 01.03E01, max UDMA/133
[    1.484825] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.492846] ata1.00: configured for UDMA/133
[    1.492978] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-7 01.0 PQ: 0 ANSI: 5
[    1.493095] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.493142] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.493153] sd 0:0:0:0: [sda] Write Protect is off
[    1.493156] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.493186] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.500130] ata2.00: configured for UDMA/100
[    1.502409] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7200S 102A PQ: 0 ANSI: 5
[    1.504759] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.504764] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.504882] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.504984] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.541076]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.541485] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.541505] Freeing unused kernel memory: 712k freed
[    1.541759] Write protecting the kernel text: 5632k
[    1.541801] Write protecting the kernel read-only data: 2324k
[    1.556064] udevd[93]: starting version 175
[    1.608785] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.608788] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.608833] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.608845] e1000e 0000:00:19.0: setting latency timer to 64
[    1.608935] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    1.643855] FDC 0 is a post-1991 82077
[    1.654143] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2
[    1.654292] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1a.1-1/input0
[    1.654309] usbcore: registered new interface driver usbhid
[    1.654311] usbhid: USB HID core driver
[    1.780039] usb 4-2: new low-speed USB device number 3 using uhci_hcd
[    1.780185] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:21:9b:2b:56:0e
[    1.780188] e1000e 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    1.780210] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 7, PBA No: FFFFFF-0FF
[    1.972053] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3
[    1.972209] generic-usb 0003:413C:3012.0002: input,hidraw1: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1a.1-2/input0
[    2.085427] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.212025] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[   18.352897] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.373126] udevd[395]: starting version 175
[   18.386880] Adding 2085884k swap on /dev/sda5.  Priority:-1 extents:1 across:2085884k 
[   18.410758] lp: driver loaded but no devices found
[   18.474838] type=1400 audit(1339195529.236:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[   18.475239] type=1400 audit(1339195529.236:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[   18.475461] type=1400 audit(1339195529.236:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[   18.495538] [drm] Initialized drm 1.1.0 20060810
[   18.496112] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   18.541943] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.541949] i915 0000:00:02.0: setting latency timer to 64
[   18.562932] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   18.562939] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.562940] [drm] Driver supports precise vblank timestamp query.
[   18.601270] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.625014] Linux video capture interface: v2.00
[   18.634139] [drm] initialized overlay support
[   18.672238] gspca_main: v2.14.0 registered
[   18.672526] gspca_main: sonixj-2.14.0 probing 045e:00f5
[   18.681029] ppdev: user-space parallel port driver
[   18.684124] Bluetooth: Core ver 2.16
[   18.684143] NET: Registered protocol family 31
[   18.684145] Bluetooth: HCI device and connection manager initialized
[   18.684148] Bluetooth: HCI socket layer initialized
[   18.684150] Bluetooth: L2CAP socket layer initialized
[   18.684155] Bluetooth: SCO socket layer initialized
[   18.695459] input: sonixj as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/input/input4
[   18.710151] type=1400 audit(1339195529.472:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=608 comm="apparmor_parser"
[   18.711000] type=1400 audit(1339195529.472:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=608 comm="apparmor_parser"
[   18.738328] usbcore: registered new interface driver sonixj
[   18.738416] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.738419] Bluetooth: BNEP filters: protocol multicast
[   18.740870] Bluetooth: RFCOMM TTY layer initialized
[   18.740876] Bluetooth: RFCOMM socket layer initialized
[   18.740878] Bluetooth: RFCOMM ver 1.11
[   18.782003] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.869628] fbcon: inteldrmfb (fb0) is primary device
[   18.870642] Console: switching to colour frame buffer device 180x56
[   18.870678] fb0: inteldrmfb frame buffer device
[   18.870679] drm: registered panic notifier
[   18.893347] No ACPI video bus found
[   18.893457] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.898000] init: failsafe main process (657) killed by TERM signal
[   18.931963] usbcore: registered new interface driver snd-usb-audio
[   18.945467] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.945517] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   18.945542] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   19.152218] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   19.179297] type=1400 audit(1339195529.940:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=789 comm="apparmor_parser"
[   19.182779] type=1400 audit(1339195529.944:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=790 comm="apparmor_parser"
[   19.183180] type=1400 audit(1339195529.944:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=790 comm="apparmor_parser"
[   19.183405] type=1400 audit(1339195529.944:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=790 comm="apparmor_parser"
[   19.196962] type=1400 audit(1339195529.960:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=807 comm="apparmor_parser"
[   19.208092] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   19.208316] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.208647] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.619482] init: gdm main process (905) killed by TERM signal
[   20.612165] init: plymouth-stop pre-start process (1211) terminated with status 1
[   20.660762] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   20.660767] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   20.660925] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.408093] eth0: no IPv6 routers present
[  146.056050] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[  146.222238] Initializing USB Mass Storage driver...
[  146.222377] scsi4 : usb-storage 2-1:1.0
[  146.222457] usbcore: registered new interface driver usb-storage
[  146.222458] USB Mass Storage support registered.
[  146.231735] usbcore: registered new interface driver uas
[  147.256915] scsi 4:0:0:0: Direct-Access     Memorex  Mini             PMAP PQ: 0 ANSI: 0 CCS
[  147.257925] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  148.803168] sd 4:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[  148.803652] sd 4:0:0:0: [sdb] Write Protect is off
[  148.803658] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  148.804160] sd 4:0:0:0: [sdb] No Caching mode page present
[  148.804166] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  148.808090] sd 4:0:0:0: [sdb] No Caching mode page present
[  148.808101] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  148.835151]  sdb: sdb1
[  148.837670] sd 4:0:0:0: [sdb] No Caching mode page present
[  148.837676] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  148.837682] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  385.770809] usb 2-1: USB disconnect, device number 2
[  387.760031] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[  387.898545] scsi5 : usb-storage 2-1:1.0
[  388.933024] scsi 5:0:0:0: Direct-Access     Memorex  Mini             PMAP PQ: 0 ANSI: 0 CCS
[  388.934067] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  389.650491] sd 5:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[  389.650978] sd 5:0:0:0: [sdb] Write Protect is off
[  389.650984] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  389.651478] sd 5:0:0:0: [sdb] No Caching mode page present
[  389.651483] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  389.654977] sd 5:0:0:0: [sdb] No Caching mode page present
[  389.654983] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  389.682972]  sdb:
[  389.685613] sd 5:0:0:0: [sdb] No Caching mode page present
[  389.685617] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  389.685620] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  413.198771] usb 2-1: USB disconnect, device number 3
[  414.808030] usb 2-4: new high-speed USB device number 4 using ehci_hcd
[  414.946563] scsi6 : usb-storage 2-4:1.0
[  415.980924] scsi 6:0:0:0: Direct-Access     Memorex  Mini             PMAP PQ: 0 ANSI: 0 CCS
[  415.981987] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  416.689010] sd 6:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[  416.689498] sd 6:0:0:0: [sdb] Write Protect is off
[  416.689503] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  416.689998] sd 6:0:0:0: [sdb] No Caching mode page present
[  416.690003] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  416.699502] sd 6:0:0:0: [sdb] No Caching mode page present
[  416.699508] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  416.726999]  sdb:
[  416.730151] sd 6:0:0:0: [sdb] No Caching mode page present
[  416.730158] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  416.730163] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  467.618742] usb 2-4: USB disconnect, device number 4
[  536.936051] usb 2-3: new high-speed USB device number 5 using ehci_hcd
[  537.074508] scsi7 : usb-storage 2-3:1.0
[  538.108990] scsi 7:0:0:0: Direct-Access     Memorex  Mini             PMAP PQ: 0 ANSI: 0 CCS
[  538.109999] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  538.815827] sd 7:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[  538.816319] sd 7:0:0:0: [sdb] Write Protect is off
[  538.816325] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  538.816813] sd 7:0:0:0: [sdb] No Caching mode page present
[  538.816819] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  538.820815] sd 7:0:0:0: [sdb] No Caching mode page present
[  538.820822] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  538.848299]  sdb:
[  538.850960] sd 7:0:0:0: [sdb] No Caching mode page present
[  538.850966] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  538.850972] sd 7:0:0:0: [sdb] Attached SCSI removable disk

```


Please someone help. I need this USB.

---

### Post by wilee-nilee on 2012-06-08
If you have reformatted it and it does not work I would think it is just broken.

Have you googled the model and Linux to see if there are any known problems with this model.

---

### Post by jtarin on 2012-06-08
Try formatting it on a Windows machine as FAT32. Use the long method....not Quick method.

---

