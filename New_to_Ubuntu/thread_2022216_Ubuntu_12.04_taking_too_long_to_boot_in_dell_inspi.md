---
title: "Ubuntu 12.04 taking too long to boot in dell inspiron N5010"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by manuganji on 2012-07-10
I previously posted this in a solved thread and got no replies. So, reposting it here. Thanks in advance for your time. :)

this is my dmesg output

> [ 0.634807] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[ 0.634893] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[ 0.634936] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[ 0.634938] pnp 00:01: [mem 0xe0000000-0xefffffff]
[ 0.634940] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[ 0.634942] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[ 0.634943] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[ 0.634998] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[ 0.635001] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[ 0.635003] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[ 0.635006] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[ 0.635008] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[ 0.635011] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[ 0.635041] pnp 00:02: [dma 4]
[ 0.635043] pnp 00:02: [io 0x0000-0x000f]
[ 0.635045] pnp 00:02: [io 0x0081-0x0083]
[ 0.635046] pnp 00:02: [io 0x0087]
[ 0.635048] pnp 00:02: [io 0x0089-0x008b]
[ 0.635049] pnp 00:02: [io 0x008f]
[ 0.635051] pnp 00:02: [io 0x00c0-0x00df]
[ 0.635075] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[ 0.635084] pnp 00:03: [io 0x0070-0x0071]
[ 0.635096] pnp 00:03: [irq 8]
[ 0.635117] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[ 0.635127] pnp 00:04: [io 0x0061]
[ 0.635149] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[ 0.635157] pnp 00:05: [io 0x00f0-0x00ff]
[ 0.635163] pnp 00:05: [irq 13]
[ 0.635188] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[ 0.635204] pnp 00:06: [io 0x0010-0x001f]
[ 0.635206] pnp 00:06: [io 0x0022-0x003f]
[ 0.635208] pnp 00:06: [io 0x0044-0x005f]
[ 0.635209] pnp 00:06: [io 0x0068-0x006f]
[ 0.635211] pnp 00:06: [io 0x0072-0x007f]
[ 0.635212] pnp 00:06: [io 0x0080]
[ 0.635214] pnp 00:06: [io 0x0084-0x0086]
[ 0.635215] pnp 00:06: [io 0x0088]
[ 0.635217] pnp 00:06: [io 0x008c-0x008e]
[ 0.635219] pnp 00:06: [io 0x0090-0x009f]
[ 0.635220] pnp 00:06: [io 0x00a2-0x00bf]
[ 0.635222] pnp 00:06: [io 0x00e0-0x00ef]
[ 0.635223] pnp 00:06: [io 0x04d0-0x04d1]
[ 0.635225] pnp 00:06: [mem 0xfe800000-0xfe8001ff]
[ 0.635268] system 00:06: [io 0x04d0-0x04d1] has been reserved
[ 0.635271] system 00:06: [mem 0xfe800000-0xfe8001ff] has been reserved
[ 0.635274] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.635291] pnp 00:07: [irq 12]
[ 0.635320] pnp 00:07: Plug and Play ACPI device, IDs DLL0447 SYN0600 SYN0002 PNP0f13 (active)
[ 0.635334] pnp 00:08: [io 0x0060]
[ 0.635336] pnp 00:08: [io 0x0064]
[ 0.635338] pnp 00:08: [io 0x0062]
[ 0.635339] pnp 00:08: [io 0x0066]
[ 0.635345] pnp 00:08: [irq 1]
[ 0.635369] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[ 0.635494] pnp 00:09: [io 0x0400-0x047f]
[ 0.635496] pnp 00:09: [io 0x1180-0x119f]
[ 0.635498] pnp 00:09: [io 0x0500-0x057f]
[ 0.635500] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[ 0.635502] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[ 0.635503] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[ 0.635505] pnp 00:09: [mem 0xff000000-0xffffffff]
[ 0.635546] system 00:09: [io 0x0400-0x047f] has been reserved
[ 0.635548] system 00:09: [io 0x1180-0x119f] has been reserved
[ 0.635550] system 00:09: [io 0x0500-0x057f] has been reserved
[ 0.635553] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[ 0.635556] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[ 0.635558] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[ 0.635561] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[ 0.635564] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[ 0.635645] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[ 0.635679] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[ 0.635877] pnp: PnP ACPI: found 11 devices
[ 0.635878] ACPI: ACPI bus type pnp unregistered
[ 0.643457] PCI: max bus depth: 1 pci_try_num: 2
[ 0.643518] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd1600000-0xd17fffff 64bit pref]
[ 0.643522] pci 0000:00:1c.1: BAR 13: assigned [io 0x2000-0x2fff]
[ 0.643525] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd1800000-0xd19fffff]
[ 0.643528] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd1a00000-0xd1bfffff 64bit pref]
[ 0.643531] pci 0000:00:1c.0: BAR 13: assigned [io 0x3000-0x3fff]
[ 0.643534] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[ 0.643536] pci 0000:00:01.0: bridge window [io 0xe000-0xefff]
[ 0.643540] pci 0000:00:01.0: bridge window [mem 0xfbe00000-0xfbefffff]
[ 0.643543] pci 0000:00:01.0: bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[ 0.643547] pci 0000:00:1c.0: PCI bridge to [bus 11-11]
[ 0.643550] pci 0000:00:1c.0: bridge window [io 0x3000-0x3fff]
[ 0.643556] pci 0000:00:1c.0: bridge window [mem 0xd1800000-0xd19fffff]
[ 0.643561] pci 0000:00:1c.0: bridge window [mem 0xd1a00000-0xd1bfffff 64bit pref]
[ 0.643569] pci 0000:00:1c.1: PCI bridge to [bus 12-12]
[ 0.643572] pci 0000:00:1c.1: bridge window [io 0x2000-0x2fff]
[ 0.643578] pci 0000:00:1c.1: bridge window [mem 0xfbd00000-0xfbdfffff]
[ 0.643583] pci 0000:00:1c.1: bridge window [mem 0xd1600000-0xd17fffff 64bit pref]
[ 0.643592] pci 0000:00:1c.2: PCI bridge to [bus 13-13]
[ 0.643595] pci 0000:00:1c.2: bridge window [io 0xd000-0xdfff]
[ 0.643602] pci 0000:00:1c.2: bridge window [mem 0xfb300000-0xfbcfffff]
[ 0.643607] pci 0000:00:1c.2: bridge window [mem 0xd0c00000-0xd15fffff 64bit pref]
[ 0.643615] pci 0000:00:1c.4: PCI bridge to [bus 15-15]
[ 0.643618] pci 0000:00:1c.4: bridge window [io 0xc000-0xcfff]
[ 0.643625] pci 0000:00:1c.4: bridge window [mem 0xfa900000-0xfb2fffff]
[ 0.643630] pci 0000:00:1c.4: bridge window [mem 0xd0100000-0xd0afffff 64bit pref]
[ 0.643638] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[ 0.643670] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.643674] pci 0000:00:01.0: setting latency timer to 64
[ 0.643685] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 0.643690] pci 0000:00:1c.0: setting latency timer to 64
[ 0.643699] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[ 0.643704] pci 0000:00:1c.1: setting latency timer to 64
[ 0.643717] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 0.643722] pci 0000:00:1c.2: setting latency timer to 64
[ 0.643730] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 0.643735] pci 0000:00:1c.4: setting latency timer to 64
[ 0.643743] pci 0000:00:1e.0: setting latency timer to 64
[ 0.643748] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7]
[ 0.643750] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff]
[ 0.643752] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[ 0.643755] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[ 0.643757] pci_bus 0000:01: resource 0 [io 0xe000-0xefff]
[ 0.643759] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[ 0.643761] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[ 0.643764] pci_bus 0000:11: resource 0 [io 0x3000-0x3fff]
[ 0.643766] pci_bus 0000:11: resource 1 [mem 0xd1800000-0xd19fffff]
[ 0.643768] pci_bus 0000:11: resource 2 [mem 0xd1a00000-0xd1bfffff 64bit pref]
[ 0.643771] pci_bus 0000:12: resource 0 [io 0x2000-0x2fff]
[ 0.643773] pci_bus 0000:12: resource 1 [mem 0xfbd00000-0xfbdfffff]
[ 0.643775] pci_bus 0000:12: resource 2 [mem 0xd1600000-0xd17fffff 64bit pref]
[ 0.643778] pci_bus 0000:13: resource 0 [io 0xd000-0xdfff]
[ 0.643780] pci_bus 0000:13: resource 1 [mem 0xfb300000-0xfbcfffff]
[ 0.643782] pci_bus 0000:13: resource 2 [mem 0xd0c00000-0xd15fffff 64bit pref]
[ 0.643784] pci_bus 0000:15: resource 0 [io 0xc000-0xcfff]
[ 0.643787] pci_bus 0000:15: resource 1 [mem 0xfa900000-0xfb2fffff]
[ 0.643789] pci_bus 0000:15: resource 2 [mem 0xd0100000-0xd0afffff 64bit pref]
[ 0.643791] pci_bus 0000:20: resource 4 [io 0x0000-0x0cf7]
[ 0.643793] pci_bus 0000:20: resource 5 [io 0x0d00-0xffff]
[ 0.643796] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[ 0.643798] pci_bus 0000:20: resource 7 [mem 0xc0000000-0xffffffff]
[ 0.643801] pci_bus 0000:ff: resource 0 [io 0x0000-0xffff]
[ 0.643803] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[ 0.643842] NET: Registered protocol family 2
[ 0.643990] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.644961] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[ 0.647700] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[ 0.648031] TCP: Hash tables configured (established 524288 bind 65536)
[ 0.648034] TCP reno registered
[ 0.648046] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[ 0.648083] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[ 0.648199] NET: Registered protocol family 1
[ 0.648233] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.772229] pci 0000:00:1a.0: PCI INT A disabled
[ 0.772274] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 0.899973] pci 0000:00:1d.0: PCI INT A disabled
[ 0.899999] pci 0000:01:00.0: Boot video device
[ 0.900028] PCI: CLS 64 bytes, default 64
[ 0.900030] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[ 0.900033] Placing 64MB software IO TLB between ffff8800bb5a6000 - ffff8800bf5a6000
[ 0.900035] software IO TLB at phys 0xbb5a6000 - 0xbf5a6000
[ 0.900568] audit: initializing netlink socket (disabled)
[ 0.900580] type=2000 audit(1341306922.732:1): initialized
[ 0.931973] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[ 0.951363] VFS: Disk quotas dquot_6.5.2
[ 0.951417] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[ 0.951955] fuse init (API version 7.17)
[ 0.952052] msgmni has been set to 7605
[ 0.952511] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.952547] io scheduler noop registered
[ 0.952549] io scheduler deadline registered
[ 0.952582] io scheduler cfq registered (default)
[ 0.952695] pcieport 0000:00:01.0: setting latency timer to 64
[ 0.952725] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[ 0.952777] pcieport 0000:00:1c.0: setting latency timer to 64
[ 0.952827] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[ 0.952910] pcieport 0000:00:1c.1: setting latency timer to 64
[ 0.952960] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[ 0.953040] pcieport 0000:00:1c.2: setting latency timer to 64
[ 0.953091] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[ 0.953173] pcieport 0000:00:1c.4: setting latency timer to 64
[ 0.953223] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[ 0.953314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.953434] pciehp: Using ACPI for slot detection.
[ 0.953499] pciehp 0000:00:1c.4cie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[ 0.953535] pciehp 0000:00:1c.4cie04: service driver pciehp loaded
[ 0.953541] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.953591] intel_idle: MWAIT substates: 0x1120
[ 0.953593] intel_idle: v0.4 model 0x25
[ 0.953594] intel_idle: lapic_timer_reliable_states 0xffffffff
[ 0.953677] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.953723] ACPI: AC Adapter [AC] (off-line)
[ 0.953821] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[ 0.953826] ACPI: Power Button [PWRB]
[ 0.953865] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[ 0.955418] ACPI: Lid Switch [LID0]
[ 0.955458] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[ 0.955462] ACPI: Sleep Button [SBTN]
[ 0.955497] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[ 0.955500] ACPI: Power Button [PWRF]
[ 0.967676] thermal LNXTHERM:00: registered as thermal_zone0
[ 0.967680] ACPI: Thermal Zone [THM] (59 C)
[ 0.967712] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.967724] ACPI: Battery Slot [BAT0] (battery present)
[ 0.967759] ERST: Table is not found!
[ 0.967761] GHES: HEST is not enabled!
[ 0.967886] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[ 0.980196] ACPI: Battery Slot [BAT0] (battery present)
[ 1.031086] Freeing initrd memory: 13836k freed
[ 1.191756] Linux agpgart interface v0.103
[ 1.193385] brd: module loaded
[ 1.194194] loop: module loaded
[ 1.194319] ahci 0000:00:1f.2: version 3.0
[ 1.194343] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1.194399] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[ 1.194485] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[ 1.194489] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[ 1.194494] ahci 0000:00:1f.2: setting latency timer to 64
[ 1.207822] scsi0 : ahci
[ 1.207912] scsi1 : ahci
[ 1.207992] scsi2 : ahci
[ 1.208069] scsi3 : ahci
[ 1.208147] scsi4 : ahci
[ 1.208221] scsi5 : ahci
[ 1.208350] ata1: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06100 irq 45
[ 1.208354] ata2: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06180 irq 45
[ 1.208356] ata3: DUMMY
[ 1.208357] ata4: DUMMY
[ 1.208360] ata5: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06300 irq 45
[ 1.208362] ata6: DUMMY
[ 1.208750] Fixed MDIO Bus: probed
[ 1.208766] tun: Universal TUN/TAP device driver, 1.6
[ 1.208767] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1.208833] PPP generic driver version 2.4.2
[ 1.208943] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.208960] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.208977] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1.208981] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[ 1.209042] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[ 1.209078] ehci_hcd 0000:00:1a.0: debug port 2
[ 1.213033] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[ 1.213048] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbf08000
[ 1.227302] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[ 1.227454] hub 1-0:1.0: USB hub found
[ 1.227459] hub 1-0:1.0: 2 ports detected
[ 1.227526] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1.227541] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1.227545] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[ 1.227594] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1.227623] ehci_hcd 0000:00:1d.0: debug port 2
[ 1.231595] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[ 1.231612] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbf07000
[ 1.247261] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[ 1.247401] hub 2-0:1.0: USB hub found
[ 1.247404] hub 2-0:1.0: 2 ports detected
[ 1.247461] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.247471] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.247515] usbcore: registered new interface driver libusual
[ 1.247547] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13S2] at 0x60,0x64 irq 1,12
[ 1.272294] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.272301] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.272438] mousedev: PS/2 mouse device common for all mice
[ 1.273551] rtc_cmos 00:03: RTC can wake from S4
[ 1.273674] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[ 1.273707] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[ 1.273781] device-mapper: uevent: version 1.0.3
[ 1.273858] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[ 1.273951] cpuidle: using governor ladder
[ 1.274089] cpuidle: using governor menu
[ 1.274090] EFI Variables Facility v0.08 2004-May-17
[ 1.274306] TCP cubic registered
[ 1.274399] NET: Registered protocol family 10
[ 1.274845] NET: Registered protocol family 17
[ 1.274858] Registering the dns_resolver key type
[ 1.275033] PM: Hibernation image not present or could not be loaded.
[ 1.275050] registered taskstats version 1
[ 1.291495] Magic number: 4:901:271
[ 1.291690] rtc_cmos 00:03: setting system clock to 2012-07-03 09:15:23 UTC (1341306923)
[ 1.292888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.292890] EDD information not available.
[ 1.302020] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 1.526808] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1.526850] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.526887] ata5: SATA link down (SStatus 0 SControl 300)
[ 1.538757] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[ 1.545384] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633C, DW40, max UDMA/100
[ 1.545390] ata2.00: applying bridge limits
[ 1.565854] ata2.00: configured for UDMA/100
[ 1.572511] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ002D, max UDMA/100
[ 1.572517] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[ 1.573570] ata1.00: configured for UDMA/100
[ 1.573904] scsi 0:0:0:0: Direct-Access ATA TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
[ 1.574139] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.574195] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 1.574429] sd 0:0:0:0: [sda] Write Protect is off
[ 1.574432] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.574579] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.576088] scsi 1:0:0:0: CD-ROM TSSTcorp DVD+-RW TS-L633C DW40 PQ: 0 ANSI: 5
[ 1.583264] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1.583270] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 1.583583] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1.583720] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 1.671552] hub 1-1:1.0: USB hub found
[ 1.671768] hub 1-1:1.0: 6 ports detected
[ 1.704029] sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 >
[ 1.706288] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.707736] Freeing unused kernel memory: 920k freed
[ 1.707879] Write protecting the kernel read-only data: 12288k
[ 1.712585] Freeing unused kernel memory: 1604k freed
[ 1.716256] Freeing unused kernel memory: 1196k freed
[ 1.735193] udevd[106]: starting version 175
[ 1.777770] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.777818] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.777859] r8169 0000:13:00.0: setting latency timer to 64
[ 1.777928] r8169 0000:13:00.0: irq 46 for MSI/MSI-X
[ 1.778614] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc9000064e000, a4:ba:db:b8:70:ba, XID 04e00000 IRQ 46
[ 1.782225] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[ 1.898072] Refined TSC clocksource calibration: 2261.000 MHz.
[ 1.898080] Switching to clocksource tsc
[ 1.914786] hub 2-1:1.0: USB hub found
[ 1.914822] hub 2-1:1.0: 8 ports detected
[ 1.985981] usb 1-1.6: new full-speed USB device number 3 using ehci_hcd
[ 2.129743] usb 1-1.6: new high-speed USB device number 4 using ehci_hcd
[ 2.337286] usb 2-1.6: new full-speed USB device number 3 using ehci_hcd
[ 2.431748] hub 2-1.6:1.0: USB hub found
[ 2.431947] hub 2-1.6:1.0: 3 ports detected
[ 2.700565] usb 2-1.6.1: new full-speed USB device number 4 using ehci_hcd
[ 2.799522] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input5
[ 2.799685] generic-usb 0003:413C:8161.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[ 2.799710] usbcore: registered new interface driver usbhid
[ 2.799714] usbhid: USB HID core driver
[ 2.864258] usb 2-1.6.2: new full-speed USB device number 5 using ehci_hcd
[ 2.966485] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input6
[ 2.966702] generic-usb 0003:413C:8162.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[ 2.998093] EXT4-fs (sda: mounted filesystem with ordered data mode. Opts: (null)
[ 42.025119] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 43.353109] Adding 5957628k swap on /dev/sda9. Priority:-1 extents:1 across:5957628k 
[ 43.388353] udevd[445]: starting version 175
[ 43.421391] mei: module is from the staging directory, the quality is unknown, you have been warned.
[ 43.421756] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 43.421766] mei 0000:00:16.0: setting latency timer to 64
[ 43.421844] mei 0000:00:16.0: irq 47 for MSI/MSI-X
[ 43.422861] lib80211: common routines for IEEE802.11 drivers
[ 43.422864] lib80211_crypt: registered algorithm 'NULL'
[ 43.428383] lp: driver loaded but no devices found
[ 43.428900] wl: module license 'MIXED/Proprietary' taints kernel.
[ 43.428905] Disabling lock debugging due to kernel taint
[ 43.437254] wl 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 43.437264] wl 0000:12:00.0: setting latency timer to 64
[ 43.438986] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[ 43.439000] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 43.439456] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[ 43.450629] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[ 43.479802] lib80211_crypt: registered algorithm 'TKIP'
[ 43.487809] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[ 43.498629] acpi device:03: registered as cooling_device4
[ 43.498840] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[ 43.498925] ACPI: Video Device [PEGP] (multi-head: yes rom: no post: no)
[ 43.512344] [fglrx] Maximum main memory to use for locked dma buffers: 3659 MBytes.
[ 43.512633] [fglrx] vendor: 1002 device: 68e0 count: 1
[ 43.513146] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[ 43.513166] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 43.513176] pci 0000:01:00.0: setting latency timer to 64
[ 43.513423] [fglrx] Kernel PAT support is enabled
[ 43.513447] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[ 43.558148] type=1400 audit(1341287165.843:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
[ 43.558567] type=1400 audit(1341287165.843:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[ 43.558805] type=1400 audit(1341287165.843:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
[ 43.562495] wmi: Mapper loaded
[ 43.562780] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[ 43.568040] Linux video capture interface: v2.00
[ 43.568689] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6461)
[ 43.573433] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 43.573505] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[ 43.573541] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 43.593278] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[ 43.652705] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[ 43.654191] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[ 43.654463] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 43.654552] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[ 43.654582] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[ 43.675194] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[ 43.675295] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[ 43.684648] input: Dell WMI hotkeys as /devices/virtual/input/input11
[ 43.715612] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input12
[ 43.715699] usbcore: registered new interface driver uvcvideo
[ 43.715702] USB Video Class driver (1.1.1)
[ 43.933935] EXT4-fs (sda: re-mounted. Opts: (null)
[ 44.383305] init: failsafe main process (795) killed by TERM signal
[ 44.629030] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[ 44.671155] ppdev: user-space parallel port driver
[ 44.703374] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[ 44.716631] Bluetooth: Core ver 2.16
[ 44.716661] NET: Registered protocol family 31
[ 44.716663] Bluetooth: HCI device and connection manager initialized
[ 44.716667] Bluetooth: HCI socket layer initialized
[ 44.716669] Bluetooth: L2CAP socket layer initialized
[ 44.716930] Bluetooth: SCO socket layer initialized
[ 44.721826] Bluetooth: RFCOMM TTY layer initialized
[ 44.721833] Bluetooth: RFCOMM socket layer initialized
[ 44.721836] Bluetooth: RFCOMM ver 1.11
[ 44.722134] type=1400 audit(1341287167.011:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=863 comm="apparmor_parser"
[ 44.723539] type=1400 audit(1341287167.011:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=863 comm="apparmor_parser"
[ 44.728079] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 44.728083] Bluetooth: BNEP filters: protocol multicast
[ 44.749249] type=1400 audit(1341287167.039:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=900 comm="apparmor_parser"
[ 44.749262] type=1400 audit(1341287167.039:: apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=901 comm="apparmor_parser"
[ 44.749840] type=1400 audit(1341287167.039:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=902 comm="apparmor_parser"
[ 44.750264] type=1400 audit(1341287167.039:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
[ 44.750519] type=1400 audit(1341287167.039:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
[ 44.789954] r8169 0000:13:00.0: eth0: link down
[ 44.790306] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 44.790612] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 45.740359] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[ 45.740363] vesafb: scrolling: redraw
[ 45.740366] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[ 45.742414] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90011400000, using 3072k, total 3072k
[ 45.743325] Console: switching to colour frame buffer device 128x48
[ 45.743354] fb0: VESA VGA frame buffer device
[ 45.759609] init: gdm main process (1072) killed by TERM signal
[ 46.125341] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[ 46.126014] [fglrx] Firegl kernel thread PID: 1088
[ 46.126108] [fglrx] Firegl kernel thread PID: 1089
[ 46.126170] [fglrx] Firegl kernel thread PID: 1090
[ 46.126270] [fglrx] IRQ 50 Enabled
[ 46.254527] [fglrx] Gart USWC size:1196 M.
[ 46.254530] [fglrx] Gart cacheable size:473 M.
[ 46.254535] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[ 46.254537] [fglrx] Reserved FB block: Unshared offset:f941000, size:3bf000 
[ 46.254539] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[ 48.200875] init: anacron main process (974) killed by TERM signal
[ 76.869234] eth1: no IPv6 routers present
[ 112.690723] init: plymouth-stop pre-start process (2205) terminated with status 1

I connect through wi-fi. And I can't see the files etc/modprobe.d/blacklist-ethernet.conf or /usr/sbin/ethtool in my  system. So, I couldn't try the solutions given in some of the threads. My laptop runs win-7 and ubuntu 12.04. I upgraded from 11.10 to 12.04 instead of doing a fresh install.  Please help. Please let me know if you need any further details.

---

### Post by Redblade20XX on 2012-07-10
> **manuganji said:**
> I upgraded from 11.10 to 12.04 instead of doing a fresh install.  Please help. Please let me know if you need any further details.

Was your boot time normal under 11.10? If it was, then probably a configuration file got carried over during the upgrade and is messing up your system. Your better off ( it will be much quicker)  doing a clean install instead of searching for the problem.

- Red

---

### Post by manuganji on 2012-07-10
> **Redblade20XX said:**
> Was your boot time normal under 11.10? If it was, then probably a configuration file got carried over during the upgrade and is messing up your system. Your better off ( it will be much quicker)  doing a clean install instead of searching for the problem.

- Red

In one of 11.04 or 11.10 the boot time was normal. Like around 10 seconds. I had upgraded from 11.04 to 11.10 and to 12.04 when it was released. I think in the log, the problem is at 
> [ 42.025119] ADDRCONF(NETDEV_UP): eth0: link is not ready

This step is taking somewhere like 40 seconds to get completed. If there is no other option I will try the fresh install.

---

### Post by manuganji on 2012-07-10
```
sudo lspci | grep Broadcom
``` gives this
> 12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)


---

