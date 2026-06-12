---
title: "Sound issue?"
date: 2008-11-26
forum: Philippine Team
---

### Post by killer_d76 on 2008-11-26
sound works okey when i'm playing video/mp3 on rythmbox, Movie Player,Totem, Real Player and Youtube!.. then i tried running Sound Recorder.. and here's what happened..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94224&d=1227681833[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94225&d=1227681833[/IMG]



i tried installing Skype and when i did a test call here's what i got...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94226&d=1227681833[/IMG]


how can i fix this issue?

---

### Post by loell on 2008-11-26
is this in Hardy? or Intrepid?

---

### Post by killer_d76 on 2008-11-26
Intrepid bossing..

---

### Post by loell on 2008-11-26
i'm having a feeling that this is an intel sound device :)

(nag kuro-kuro na naman ako, heheh)

can you post your **dmesg**?

---

### Post by killer_d76 on 2008-11-26
eto bossing..

[PHP][    0.524590] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    0.525029] pnp: PnP ACPI: found 10 devices
[    0.525031] ACPI: ACPI bus type pnp unregistered
[    0.525036] PnPBIOS: Disabled by ACPI PNP
[    0.525435] PCI: Using ACPI for IRQ routing
[    0.525441] pci 0000:00:1c.3: BAR 7: can't allocate resource
[    0.525444] pci 0000:00:1c.3: BAR 8: can't allocate resource
[    0.525607] NET: Registered protocol family 8
[    0.525607] NET: Registered protocol family 20
[    0.525607] NetLabel: Initializing
[    0.525607] NetLabel:  domain hash size = 128
[    0.525607] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.525607] NetLabel:  unlabeled traffic allowed by default
[    0.525607] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.525607] hpet0: 3 64-bit timers, 14318180 Hz
[    0.525684] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.525687]    actual entries 65620
[    0.525803] AppArmor: AppArmor Filesystem Enabled
[    0.525835] ACPI: RTC can wake from S4
[    0.525846] system 00:01: ioport range 0xfe00-0xfe7f has been reserved
[    0.525846] system 00:01: ioport range 0xfe80-0xfeff has been reserved
[    0.525846] system 00:01: ioport range 0xff00-0xff7f has been reserved
[    0.525846] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    0.525846] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.525846] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    0.525846] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.525846] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.528046] Switched to high resolution mode on CPU 0
[    0.562758] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.562761] pci 0000:00:1c.0:   IO window: disabled
[    0.562769] pci 0000:00:1c.0:   MEM window: 0xd0000000-0xd00fffff
[    0.562774] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.562784] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.562788] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    0.562795] pci 0000:00:1c.2:   MEM window: 0xd0200000-0xd02fffff
[    0.562801] pci 0000:00:1c.2:   PREFETCH window: 0x0000006c000000-0x0000006c0fffff
[    0.562810] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.562813] pci 0000:00:1c.3:   IO window: disabled
[    0.562819] pci 0000:00:1c.3:   MEM window: disabled
[    0.562825] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.562840] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.562843] pci 0000:06:04.0:   IO window: 0x003000-0x0030ff
[    0.562849] pci 0000:06:04.0:   IO window: 0x003400-0x0034ff
[    0.562856] pci 0000:06:04.0:   PREFETCH window: 0x68000000-0x6bffffff
[    0.562862] pci 0000:06:04.0:   MEM window: 0x70000000-0x73ffffff
[    0.562868] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.562872] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.562879] pci 0000:00:1e.0:   MEM window: 0xd0100000-0xd01fffff
[    0.562885] pci 0000:00:1e.0:   PREFETCH window: 0x00000068000000-0x0000006bffffff
[    0.562908] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.562915] pci 0000:00:1c.0: setting latency timer to 64
[    0.562925] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.562931] pci 0000:00:1c.2: setting latency timer to 64
[    0.562942] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.562949] pci 0000:00:1c.3: setting latency timer to 64
[    0.562955] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.562962] pci 0000:00:1e.0: setting latency timer to 64
[    0.562974] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.562981] bus: 00 index 0 io port: [0, ffff]
[    0.562984] bus: 00 index 1 mmio: [0, ffffffff]
[    0.562986] bus: 02 index 0 mmio: [0, 0]
[    0.562988] bus: 02 index 1 mmio: [d0000000, d00fffff]
[    0.562990] bus: 02 index 2 mmio: [0, 0]
[    0.562992] bus: 02 index 3 mmio: [0, 0]
[    0.562994] bus: 04 index 0 io port: [2000, 2fff]
[    0.562997] bus: 04 index 1 mmio: [d0200000, d02fffff]
[    0.562999] bus: 04 index 2 mmio: [6c000000, 6c0fffff]
[    0.563001] bus: 04 index 3 mmio: [0, 0]
[    0.563003] bus: 05 index 0 mmio: [0, fff]
[    0.563005] bus: 05 index 1 mmio: [0, fffff]
[    0.563007] bus: 05 index 2 mmio: [0, 0]
[    0.563009] bus: 05 index 3 mmio: [0, 0]
[    0.563011] bus: 06 index 0 io port: [3000, 3fff]
[    0.563014] bus: 06 index 1 mmio: [d0100000, d01fffff]
[    0.563016] bus: 06 index 2 mmio: [68000000, 6bffffff]
[    0.563018] bus: 06 index 3 io port: [0, ffff]
[    0.563020] bus: 06 index 4 mmio: [0, ffffffff]
[    0.563023] bus: 07 index 0 io port: [3000, 30ff]
[    0.563025] bus: 07 index 1 io port: [3400, 34ff]
[    0.563027] bus: 07 index 2 mmio: [68000000, 6bffffff]
[    0.563029] bus: 07 index 3 mmio: [70000000, 73ffffff]
[    0.563040] NET: Registered protocol family 2
[    0.563187] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.563451] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.564091] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.564493] TCP: Hash tables configured (established 131072 bind 65536)
[    0.564497] TCP reno registered
[    0.564649] NET: Registered protocol family 1
[    0.564788] checking if image is initramfs... it is
[    0.990408] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.445379] Freeing initrd memory: 8312k freed
[    1.445605] Simple Boot Flag at 0x36 set to 0x1
[    1.446294] audit: initializing netlink socket (disabled)
[    1.446315] type=2000 audit(1227723761.444:1): initialized
[    1.453877] highmem bounce pool size: 64 pages
[    1.453884] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.464507] VFS: Disk quotas dquot_6.5.1
[    1.464607] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.464716] msgmni has been set to 1753
[    1.464846] io scheduler noop registered
[    1.464849] io scheduler anticipatory registered
[    1.464853] io scheduler deadline registered
[    1.464866] io scheduler cfq registered (default)
[    1.464883] pci 0000:00:02.0: Boot video device
[    1.465110] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.465164] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.465219] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.465270] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.465316] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.465437] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.465490] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.465540] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.465586] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.465631] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.465750] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.465803] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.465854] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.465899] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.465943] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.466315] isapnp: Scanning for PnP cards...
[    1.820331] isapnp: No Plug & Play device found
[    1.868465] hpet_resources: 0xfed00000 is busy
[    1.868536] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.871036] brd: module loaded
[    1.871122] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.871257] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.894460] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.912281] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.912290] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.912293] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.912295] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.912298] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.912793] mice: PS/2 mouse device common for all mice
[    1.913630] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.913663] rtc0: alarms up to one month, y3k, hpet irqs
[    1.913800] EISA: Probing bus 0 at eisa.0
[    1.913808] Cannot allocate resource for EISA slot 1
[    1.913811] Cannot allocate resource for EISA slot 2
[    1.913813] Cannot allocate resource for EISA slot 3
[    1.913836] EISA: Detected 0 cards.
[    1.913839] cpuidle: using governor ladder
[    1.913842] cpuidle: using governor menu
[    1.914353] TCP cubic registered
[    1.914386] Using IPI No-Shortcut mode
[    1.914611] registered taskstats version 1
[    1.914726]   Magic number: 0:717:393
[    1.914884] rtc_cmos 00:07: setting system clock to 2008-11-26 18:22:42 UTC (1227723762)
[    1.914888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.914890] EDD information not available.
[    1.915131] Freeing unused kernel memory: 424k freed
[    1.915175] Write protecting the kernel text: 2576k
[    1.915210] Write protecting the kernel read-only data: 936k
[    1.930987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.125091] fuse init (API version 7.9)
[    2.392721] Monitor-Mwait will be used to enter C-1 state
[    2.392726] Monitor-Mwait will be used to enter C-2 state
[    2.392729] Monitor-Mwait will be used to enter C-3 state
[    2.412803] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.416837] processor ACPI0007:00: registered as cooling_device0
[    2.416842] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.002866] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.002889] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.002910] r8169 0000:04:00.0: setting latency timer to 64
[    3.003288] eth0: RTL8168b/8111b at 0xf884e000, 00:16:d4:d5:03:9d, XID 38000000 IRQ 220
[    3.096291] usbcore: registered new interface driver usbfs
[    3.096318] usbcore: registered new interface driver hub
[    3.096366] usbcore: registered new device driver usb
[    3.099534] USB Universal Host Controller Interface driver v3.0
[    3.102723] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.102733] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.102738] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.102792] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.102834] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    3.102994] usb usb1: configuration #1 chosen from 1 choice
[    3.103023] hub 1-0:1.0: USB hub found
[    3.103031] hub 1-0:1.0: 2 ports detected
[    3.162376] No dock devices found.
[    3.196956] SCSI subsystem initialized
[    3.217512] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.217523] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.217528] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.217555] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.217596] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.217705] usb usb2: configuration #1 chosen from 1 choice
[    3.217734] hub 2-0:1.0: USB hub found
[    3.217741] hub 2-0:1.0: 2 ports detected
[    3.268726] libata version 3.00 loaded.
[    3.424261] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.424272] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.424277] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.424304] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.424344] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.424453] usb usb3: configuration #1 chosen from 1 choice
[    3.424483] hub 3-0:1.0: USB hub found
[    3.424491] hub 3-0:1.0: 2 ports detected
[    3.528361] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.528372] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.528377] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.528403] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.528443] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.528546] usb usb4: configuration #1 chosen from 1 choice
[    3.528576] hub 4-0:1.0: USB hub found
[    3.528584] hub 4-0:1.0: 2 ports detected
[    3.536031] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.632352] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.632372] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.632376] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.632405] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.636330] ehci_hcd 0000:00:1d.7: debug port 1
[    3.636338] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.636347] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0644000
[    3.664027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.664216] usb usb5: configuration #1 chosen from 1 choice
[    3.664250] hub 5-0:1.0: USB hub found
[    3.664259] hub 5-0:1.0: 8 ports detected
[    3.872320] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.872356] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.872371] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.881139] ata_piix 0000:00:1f.2: version 2.12
[    3.881152] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.881157] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.902886] Marking TSC unstable due to TSC halts in idle
[    4.000090] Clocksource tsc unstable (delta = -76724876 ns)
[    4.036111] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.036198] scsi0 : ata_piix
[    4.036593] scsi1 : ata_piix
[    4.037890] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    4.037894] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    4.060092] usb 2-2: device not accepting address 2, error -71
[    4.116125] hub 2-0:1.0: unable to enumerate USB device on port 2
[    4.200650] ata1.00: ATA-8: FUJITSU MHW2080BH, 0000001C, max UDMA/100
[    4.200653] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.216668] ata1.00: configured for UDMA/100
[    4.228100] usb 5-4: new high speed USB device using ehci_hcd and address 2
[    4.363465] usb 5-4: configuration #1 chosen from 1 choice
[    4.396539] ata2.00: ATAPI: Slimtype DVDRW SSM-8515S, GSL1, max UDMA/33
[    4.428516] ata2.00: configured for UDMA/33
[    4.428653] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[    4.430107] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GSL1 PQ: 0 ANSI: 5
[    4.440876] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.440918] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.459147] Driver 'sd' needs updating - please use bus_type methods
[    4.459274] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.459302] sd 0:0:0:0: [sda] Write Protect is off
[    4.459305] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.459352] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.459445] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.459471] sd 0:0:0:0: [sda] Write Protect is off
[    4.459475] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.459522] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.459528]  sda: sda1 sda2 < sda5 >
[    4.460161] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.483001] Driver 'sr' needs updating - please use bus_type methods
[    4.489153] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.489158] Uniform CD-ROM driver Revision: 3.20
[    4.489260] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.797657] kjournald starting.  Commit interval 5 seconds
[    4.797673] EXT3-fs: mounted filesystem with ordered data mode.
[   11.805099] udevd version 124 started
[   12.735168] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.801347] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.853620] Linux agpgart interface v0.103
[   12.896774] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   12.896974] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   12.949288] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   12.961058] iTCO_vendor_support: vendor-support=0
[   13.014506] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.014638] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   13.014772] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.097190] intel_rng: FWH not detected
[   13.137327] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.157217] ACPI: Power Button (FF) [PWRF]
[   13.157350] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   13.157428] ACPI: Lid Switch [LID0]
[   13.157508] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   13.172042] ACPI: Power Button (CM) [PWRB]
[   13.340262] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.770748] acpi device:04: registered as cooling_device1
[   13.771147] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   13.780046] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.795900] acpi device:0a: registered as cooling_device2
[   13.796125] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input7
[   13.812044] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.812964] ACPI: AC Adapter [ACAD] (on-line)
[   14.165759] ACPI: Battery Slot [BAT1] (battery present)
[   14.471005] ieee80211_crypt: registered algorithm 'NULL'
[   14.503015] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.527899] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.527908] wl 0000:02:00.0: setting latency timer to 64
[   14.580926] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.580958] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.613940] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.631200] ieee80211_crypt: registered algorithm 'TKIP'
[   14.631346] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.6
[   14.851421] Yenta: CardBus bridge found at 0000:06:04.0 [14c0:0020]
[   14.851449] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.851452] Yenta: Routing CardBus interrupts to PCI
[   14.851459] Yenta TI: socket 0000:06:04.0, mfunc 0x88501212, devctl 0x44
[   14.869937] sdhci: Secure Digital Host Controller Interface driver
[   14.869941] sdhci: Copyright(c) Pierre Ossman
[   15.080811] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   15.080817] Socket status: 30000006
[   15.080820] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   15.080828] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   15.080832] cs: IO port probe 0x3000-0x3fff: clean.
[   15.081065] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   15.081068] pcmcia: parent PCI bridge Memory window: 0x68000000 - 0x6bffffff
[   15.107013] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[   15.107029] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
[   15.107038] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.107128] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   15.110133] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[   15.110147] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[   15.110153] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.110195] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[   15.441075] Linux video capture interface: v2.00
[   15.464983] microdia: Microdia USB 2.0 webcam driver loaded
[   15.465020] microdia: Microdia USB 2.0 Webcam - 0C45:624F plugged-in.
[   15.466762] microdia: Microdia USB 2.0 Webcam is now controlling video device /dev/video0
[   15.466812] usbcore: registered new interface driver usb_microdia_driver
[   15.466836] microdia: v2008.10 : Microdia USB 2.0 Webcam Driver
[   15.852309] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
[   17.426796] cs: IO port probe 0x100-0x3af: clean.
[   17.428896] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.429769] cs: IO port probe 0x820-0x8ff: clean.
[   17.430481] cs: IO port probe 0xc00-0xcf7: clean.
[   17.431367] cs: IO port probe 0xa00-0xaff: clean.
[   17.804491] lp: driver loaded but no devices found
[   18.624873] EXT3 FS on sda5, internal journal
[   19.908216] type=1505 audit(1227694980.366:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4081
[   20.113057] type=1505 audit(1227694980.570:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4086
[   20.113297] type=1505 audit(1227694980.570:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4086
[   20.272295] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.127986] ACPI: WMI: Mapper loaded
[   22.163613] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.266395] apm: BIOS not found.
[   22.463042] ppdev: user-space parallel port driver
[   28.244929] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.244938] vboxdrv: Successfully done.
[   28.244940] vboxdrv: Found 1 processor cores.
[   28.245652] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.245659] vboxdrv: Successfully loaded version 2.0.4 (interface 0x00090000).
[   30.217514] Bluetooth: Core ver 2.13
[   30.219458] NET: Registered protocol family 31
[   30.219466] Bluetooth: HCI device and connection manager initialized
[   30.219469] Bluetooth: HCI socket layer initialized
[   30.244298] Bluetooth: L2CAP ver 2.11
[   30.244306] Bluetooth: L2CAP socket layer initialized
[   30.263724] Bluetooth: SCO (Voice Link) ver 0.6
[   30.263732] Bluetooth: SCO socket layer initialized
[   30.282592] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.282600] Bluetooth: BNEP filters: protocol multicast
[   30.318314] Bridge firewalling registered
[   30.319245] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   30.381345] Bluetooth: RFCOMM socket layer initialized
[   30.381628] Bluetooth: RFCOMM TTY layer initialized
[   30.381635] Bluetooth: RFCOMM ver 1.10
[   33.491071] [drm] Initialized drm 1.1.0 20060810
[   33.499769] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   33.499781] pci 0000:00:02.0: setting latency timer to 64
[   33.502126] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   34.504900] r8169: eth0: link down
[   34.547793] NET: Registered protocol family 17
[   40.164059] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   40.347503] usb 1-1: configuration #1 chosen from 1 choice
[   40.588165] usbcore: registered new interface driver hiddev
[   40.603214] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input9
[   40.613074] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[   40.613447] usbcore: registered new interface driver usbhid
[   40.613650] usbhid: v2.6:USB HID core driver
[   49.659499] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   54.660616] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660628] Buffer I/O error on device sr0, logical block 1024
[   54.660639] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660642] Buffer I/O error on device sr0, logical block 1025
[   54.660650] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660653] Buffer I/O error on device sr0, logical block 1026
[   54.660660] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660663] Buffer I/O error on device sr0, logical block 1027
[   54.660670] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660673] Buffer I/O error on device sr0, logical block 1028
[   54.660680] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660683] Buffer I/O error on device sr0, logical block 1029
[   54.660690] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660693] Buffer I/O error on device sr0, logical block 1030
[   54.660700] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660703] Buffer I/O error on device sr0, logical block 1031
[   54.660711] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660715] Buffer I/O error on device sr0, logical block 1024
[   54.660722] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660725] Buffer I/O error on device sr0, logical block 1025
[   54.660731] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660738] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660746] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660753] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660760] sr 1:0:0:0: [sr0] unaligned transfer
[   54.660767] sr 1:0:0:0: [sr0] unaligned transfer
[   54.688991] sr 1:0:0:0: [sr0] unaligned transfer
[   54.689898] sr 1:0:0:0: [sr0] unaligned transfer
[   54.690866] sr 1:0:0:0: [sr0] unaligned transfer
[   54.691649] sr 1:0:0:0: [sr0] unaligned transfer
[   54.694713] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695648] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695663] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695671] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695681] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695688] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695695] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695703] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695710] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695717] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695724] sr 1:0:0:0: [sr0] unaligned transfer
[   54.695732] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712709] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712767] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712776] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712783] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712791] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712798] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712805] sr 1:0:0:0: [sr0] unaligned transfer
[   54.712812] sr 1:0:0:0: [sr0] unaligned transfer
[   87.548806] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=ee1d8b40
[  140.244764] UDF-fs: Partition marked readonly; forcing readonly mount
[  140.276427] UDF-fs INFO UDF: Mounting volume 'NEW', timestamp 2008/11/11 17:44 (11e0)
[  141.834092] __ratelimit: 30 callbacks suppressed
[  141.834101] type=1503 audit(1227695102.290:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6395/net/" pid=6395 profile="/usr/sbin/cupsd"
[  142.886505] type=1503 audit(1227695103.342:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6403/net/" pid=6403 profile="/usr/sbin/cupsd"
[  142.961519] NET: Registered protocol family 10
[  142.963411] lo: Disabled Privacy Extensions
[  142.964841] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  142.966382] type=1503 audit(1227695103.422:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966394] type=1503 audit(1227695103.422:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966402] type=1503 audit(1227695103.422:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966409] type=1503 audit(1227695103.422:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966416] type=1503 audit(1227695103.422:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966423] type=1503 audit(1227695103.422:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966430] type=1503 audit(1227695103.422:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[  142.966437] type=1503 audit(1227695103.422:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6403 profile="/usr/sbin/cupsd"
[/PHP]

---

### Post by killer_d76 on 2008-11-26
it was working fine with Hardy?

---

### Post by loell on 2008-11-26
ba't hindi ko makita? :D

try mo din ang **lspci**

---

### Post by killer_d76 on 2008-11-26
here you go.. ;)

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
[COLOR="Red"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)


---

### Post by loell on 2008-11-26
blame **pulseaudio**!! :lolflag:

yeah, this is a well know bug, my intel sound can record but has very low volume. they say jaunty jackalope has fix this already, by packaging the newer pulseaudio. ;)


heto na muna ang solution

[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html]("http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html")

---

### Post by killer_d76 on 2008-11-26
hehehe guess what?... it's working now.. on MS Sound Recorder! :lolflag:

not on Sound Recorder :confused: ..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94246&d=1227704731[/IMG]

---

### Post by killer_d76 on 2008-11-26
i boot up my laptop early this morning and i was greeted with this error! :shock:

> etc/gdm/Xsession: Beginning session setup:
Setting IM through im-switch for locale=en_PH.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinput.d/default.

Couldn't exec /usr/bin/pulse-session: No such file or directory 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94323&d=1227741447[/IMG]

---

### Post by loell on 2008-11-26
in menus **System -> Preferences -> Sessions)**

uncheck **pulseaudio session management**

---

### Post by killer_d76 on 2008-11-27
loell i can't seem to find > pulseaudio session management on my session list here.. seems like i have deleted it somehow :confused:

---

### Post by loell on 2008-11-27
hmmm,.. ok, lets view your xsession.

```
cat /etc/gdm/Xsession
```

---

### Post by killer_d76 on 2008-11-27
eto bossing! ;)

> #!/bin/sh
#
# This is SORT OF LIKE an X session, but not quite.  You get a command as the
# first argument (it could be multiple words, so run it with "eval").  As a
# special case, the command can be:
#  failsafe - Run an xterm only
#  default - Run the appropriate Xclients startup (see the code below)
#  custom - Run ~/.xsession and if that's not available run 'default'
#
# (Note that other arguments could also follow, but only the command one is
# right now relevant and supported)
#
# The output is ALREADY redirected to .xsession-errors in GDM.  This way
# .xsession-errors actually gets more output such as if the PreSession script
# is failing.  This also prevents DoS attacks if some app in the users session
# can be prodded to dump lots of stuff on the stdout/stderr.  We wish to be
# robust don't we?  In case you wish to use an existing script for other DM's,
# you can just not redirect when GDMSESSION is set.  GDMSESSION will always
# be set from gdm.
#
# Also note that this is not run as a login shell, this is just executed.
#
# based on:
# $XConsortium: Xsession /main/10 1995/12/18 18:21:28 gildea $

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"xfree86-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

run_parts () {
  # until run-parts --noexec is implemented
  if [ -z "$1" ]; then
    internal_errormsg "run_parts() called without an argument."
  fi
  if [ ! -d "$1" ]; then
    internal_errormsg "run_parts() called, but \"$1\" does not exist or is" \
                      "not a directory."
  fi
  for F in $(ls $1); do
    if expr "$F" : '[[:alnum:]_-]\+$' > /dev/null 2>&1; then
      if [ -f "$1/$F" ]; then
        echo "$1/$F"
      fi
    fi
  done
}
# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession

# this will go into the .xsession-errors along with all other echo's
# good for debugging where things went wrong
echo "$0: Beginning session setup..."

# First read /etc/profile and .profile
test -f /etc/profile && . /etc/profile
test -f "$HOME/.profile" && . "$HOME/.profile"
# Second read /etc/xprofile and .xprofile for X specific setup
test -f /etc/xprofile && . /etc/xprofile
test -f "$HOME/.xprofile" && . "$HOME/.xprofile"

# Translation stuff
if [ -x "/usr/lib/gdm/gdmtranslate" ] ; then
  gdmtranslate="/usr/lib/gdm/gdmtranslate"
else
  gdmtranslate=
fi

# Note that this should only go to zenity dialogs which always expect utf8
gettextfunc () {
  if [ "x$gdmtranslate" != "x" ] ; then
    "$gdmtranslate" --utf8 "$1"
  else
    echo "$1"
  fi
}

zenity=`which zenity 2>/dev/null`
xmessage=`which xmessage 2>/dev/null`

command="$1"

if [ -z "$command" ] ; then
  command=failsafe
fi

if [ x"$command" = xfailsafe ] ; then
  if [ -n "$zenity" ] ; then
    "$zenity" --info --text "`gettextfunc "This is the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner"`"
  else
    echo "$0: Starting the failsafe xterm session."
  fi
  exec xterm -geometry 80x24+0+0
fi

# clean up after xbanner
freetemp=`which freetemp 2>/dev/null`
if [ -n "$freetemp" ] ; then
        "$freetemp"
fi

usermodmap="$HOME/.Xmodmap"
userxkbmap="$HOME/.Xkbmap"

if [ -f "$userxkbmap" ]; then
    setxkbmap `cat "$userxkbmap"`
    XKB_IN_USE=yes
fi

# xkb and xmodmap don't play nice together
if [ -z "$XKB_IN_USE" ]; then
    if [ -f "$usermodmap" ]; then
       xmodmap "$usermodmap"
    fi
fi

unset XKB_IN_USE

# if GDM_LANG isn't first in LANGUAGE, then unset it.
if [ -n "$GDM_LANG" ]; then
    if [ -n "$LANGUAGE" ]; then
        if echo "$LANGUAGE" | grep -q -- "^$GDM_LANG"; then
           :
        else
           unset LANGUAGE
        fi
    fi
fi

# The default Debian session runs xsession first, so we just do that for
# "custom"
if [ "x$command" = "xcustom" ] ; then
  shift
  set default $*
fi

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run_parts $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
fi

echo "$0: Executing $command failed, will try to run x-terminal-emulator"

if [ -n "$zenity" ] ; then
        "$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner"`"
fi

exec x-terminal-emulator -geometry 80x24+0+0


---

### Post by killer_d76 on 2008-11-27
... i've re-installed pulseaudio for the meantime.

---

### Post by killer_d76 on 2008-11-28
boss loell.. any luck on finding the fix on my sound issue?.. i'd love to have the recording back, it's my daughters favorite app!.. she love to record and listen to her song eh. :(

---

### Post by loell on 2008-11-28
hala, pasensya na  busy kasi kahapon sa trabaho,

comment mo lang pala ang **/etc/X11/Xsession.d/70pulseaudio**

```
sudo gedit /etc/X11/Xsession.d/70pulseaudio
```

you know **#** , at prepend sa lahat nang linya. tapos save.

---

### Post by killer_d76 on 2008-11-29
thanks for the reply Loell... which one are you referring to that i would comment?

> # If we are loading a GNOME session, load pulseaudio.

if [ "$BASESTARTUP" = gnome-session -o \
	\( "$BASESTARTUP" = x-session-manager -a \
	"`readlink /etc/alternatives/x-session-manager`" = \
		/usr/bin/gnome-session \) ]; then
  STARTUP="/usr/bin/pulse-session $STARTUP"
fi

---

### Post by loell on 2008-11-29
> **killer_d76 said:**
> thanks for the reply Loell... which one are you referring to that i would comment?

yep, like this :)

> 
# If we are loading a GNOME session, load pulseaudio.

#if [ "$BASESTARTUP" = gnome-session -o \
#\( "$BASESTARTUP" = x-session-manager -a \
#"`readlink /etc/alternatives/x-session-manager`" = \
#/usr/bin/gnome-session \) ]; then
#STARTUP="/usr/bin/pulse-session $STARTUP"
#fi 


---

### Post by randytan on 2008-12-22
Hi All!

I'm having the same issues but only with Skype.

All videos play with audio though I haven't tried audio only.

Audio for programs like Pidgin works.

No sound from Skype though. Normally you'd have log in sounds, sounds when you get and send an IM I just noticed now that I don't.

Can anyone help? Am using Intrepid but the Skype I'm using is for Hardy since that was the only version available at the wesite.

Thanks in advance and Happy Holidays! :)

---

### Post by randytan on 2009-01-02
Up ko lang kasi baka kailanganin na yung Skype sa trabaho.

Thanks!

---

