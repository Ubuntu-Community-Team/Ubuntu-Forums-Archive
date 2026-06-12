---
title: "Can't mount dvdrom drive"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by hurstja on 2008-11-13
Dvd rom drive used to mount and now does not.  I have an Acer Aspire 5100.  I can still load bootable discs but once in Ubuntu (8.10) I can not mount the drive.  So I know drive works.

dmesg replies

```
[    0.772288] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:04.0 BAR 8 (0x0-0xfffff), disabling

[    0.772288] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:04.0 BAR 9 (0x0-0xfffff), disabling

[    0.772288] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:04.0 BAR 9 (0x0-0xfffff), disabling

[    0.772288] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:05.0 BAR 8 (0x0-0xfffff), disabling

[    0.772288] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:05.0 BAR 8 (0x0-0xfffff), disabling

[    0.772288] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:12.0 BAR 6 (0x0-0x7ffff), disabling

[    0.772290] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling

[    0.808402] pnp: PnP ACPI: found 10 devices

[    0.808406] ACPI: ACPI bus type pnp unregistered

[    0.812102] PCI: Using ACPI for IRQ routing

[    0.812102] pci 0000:00:04.0: BAR 7: can't allocate resource

[    0.812102] pci 0000:00:04.0: BAR 8: can't allocate resource

[    0.812102] pci 0000:00:04.0: BAR 9: can't allocate resource

[    0.812102] pci 0000:00:05.0: BAR 7: can't allocate resource

[    0.812102] pci 0000:00:05.0: BAR 8: can't allocate resource

[    0.824066] NET: Registered protocol family 8

[    0.824068] NET: Registered protocol family 20

[    0.828056] NetLabel: Initializing

[    0.828058] NetLabel:  domain hash size = 128

[    0.828060] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.828078] NetLabel:  unlabeled traffic allowed by default

[    0.829717] tracer: 1286 pages allocated for 65536 entries of 80 bytes

[    0.829721]    actual entries 65586

[    0.829884] AppArmor: AppArmor Filesystem Enabled

[    0.829915] ACPI: RTC can wake from S4

[    0.840075] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved

[    0.840079] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved

[    0.840094] system 00:08: ioport range 0x1080-0x1080 has been reserved

[    0.840099] system 00:08: ioport range 0x8000-0x805f has been reserved

[    0.840107] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved

[    0.847100] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01

[    0.847100] pci 0000:00:01.0:   IO window: 0x9000-0x9fff

[    0.847100] pci 0000:00:01.0:   MEM window: 0xf0200000-0xf02fffff

[    0.847100] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff

[    0.847100] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02

[    0.847100] pci 0000:00:04.0:   IO window: disabled

[    0.847100] pci 0000:00:04.0:   MEM window: disabled

[    0.847100] pci 0000:00:04.0:   PREFETCH window: disabled

[    0.847100] pci 0000:00:05.0: PCI bridge, secondary bus 0000:04

[    0.847100] pci 0000:00:05.0:   IO window: disabled

[    0.847100] pci 0000:00:05.0:   MEM window: disabled

[    0.847100] pci 0000:00:05.0:   PREFETCH window: disabled

[    0.847100] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07

[    0.847100] pci 0000:06:04.0:   IO window: 0x00a400-0x00a4ff

[    0.847100] pci 0000:06:04.0:   IO window: 0x00a800-0x00a8ff

[    0.847100] pci 0000:06:04.0:   PREFETCH window: 0x50000000-0x53ffffff

[    0.847100] pci 0000:06:04.0:   MEM window: 0x58000000-0x5bffffff

[    0.847100] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06

[    0.847100] pci 0000:00:14.4:   IO window: 0xa000-0xafff

[    0.847100] pci 0000:00:14.4:   MEM window: 0xf0300000-0xf03fffff

[    0.847100] pci 0000:00:14.4:   PREFETCH window: 0x00000050000000-0x00000053ffffff

[    0.847100] pci 0000:00:04.0: setting latency timer to 64

[    0.847100] pci 0000:00:05.0: setting latency timer to 64

[    0.847100] pci 0000:06:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20

[    0.847100] bus: 00 index 0 io port: [0, ffff]

[    0.847100] bus: 00 index 1 mmio: [0, ffffffffffffffff]

[    0.847100] bus: 01 index 0 io port: [9000, 9fff]

[    0.847100] bus: 01 index 1 mmio: [f0200000, f02fffff]

[    0.847100] bus: 01 index 2 mmio: [d0000000, dfffffff]

[    0.847100] bus: 01 index 3 mmio: [0, 0]

[    0.847100] bus: 02 index 0 mmio: [0, fff]

[    0.847100] bus: 02 index 1 mmio: [0, fffff]

[    0.847100] bus: 02 index 2 mmio: [0, fffff]

[    0.847100] bus: 02 index 3 mmio: [0, 0]

[    0.847100] bus: 04 index 0 mmio: [0, fff]

[    0.847100] bus: 04 index 1 mmio: [0, fffff]

[    0.847100] bus: 04 index 2 mmio: [0, 0]

[    0.847100] bus: 04 index 3 mmio: [0, 0]

[    0.847100] bus: 06 index 0 io port: [a000, afff]

[    0.847100] bus: 06 index 1 mmio: [f0300000, f03fffff]

[    0.847100] bus: 06 index 2 mmio: [50000000, 53ffffff]

[    0.847100] bus: 06 index 3 io port: [0, ffff]

[    0.847100] bus: 06 index 4 mmio: [0, ffffffffffffffff]

[    0.847100] bus: 07 index 0 io port: [a400, a4ff]

[    0.847100] bus: 07 index 1 io port: [a800, a8ff]

[    0.847100] bus: 07 index 2 mmio: [50000000, 53ffffff]

[    0.847100] bus: 07 index 3 mmio: [58000000, 5bffffff]

[    0.847100] NET: Registered protocol family 2

[    0.852063] Switched to high resolution mode on CPU 0

[    0.852095] Switched to high resolution mode on CPU 1

[    0.885147] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)

[    0.885815] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)

[    0.887110] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)

[    0.887705] TCP: Hash tables configured (established 131072 bind 65536)

[    0.887708] TCP reno registered

[    0.897149] NET: Registered protocol family 1

[    0.897300] checking if image is initramfs... it is

[    1.907004] Freeing initrd memory: 9120k freed

[    1.914602] audit: initializing netlink socket (disabled)

[    1.914621] type=2000 audit(1226611670.912:1): initialized

[    1.921603] HugeTLB registered 2 MB page size, pre-allocated 0 pages

[    1.925962] VFS: Disk quotas dquot_6.5.1

[    1.926111] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)

[    1.926271] msgmni has been set to 1494

[    1.926462] io scheduler noop registered

[    1.926464] io scheduler anticipatory registered

[    1.926467] io scheduler deadline registered

[    1.926675] io scheduler cfq registered (default)

[    1.926686] pci 0000:00:00.0: MSI quirk detected; MSI disabled

[    1.926774] pci 0000:01:05.0: Boot video device

[    1.926953] pcieport-driver 0000:00:04.0: setting latency timer to 64

[    1.926977] pcieport-driver 0000:00:04.0: found MSI capability

[    1.926981] pci_express 0000:00:04.0:pcie00: allocate port service

[    1.927066] pci_express 0000:00:04.0:pcie02: allocate port service

[    1.927174] pcieport-driver 0000:00:05.0: setting latency timer to 64

[    1.927195] pcieport-driver 0000:00:05.0: found MSI capability

[    1.927199] pci_express 0000:00:05.0:pcie00: allocate port service

[    1.927276] pci_express 0000:00:05.0:pcie02: allocate port service

[    1.991975] Linux agpgart interface v0.103

[    1.991983] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

[    1.995964] brd: module loaded

[    1.996108] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[    1.996306] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12

[    1.996768] i8042.c: Detected active multiplexing controller, rev 1.1.

[    1.996863] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.996875] serio: i8042 AUX0 port at 0x60,0x64 irq 12

[    1.996878] serio: i8042 AUX1 port at 0x60,0x64 irq 12

[    1.996881] serio: i8042 AUX2 port at 0x60,0x64 irq 12

[    1.996883] serio: i8042 AUX3 port at 0x60,0x64 irq 12

[    2.016368] mice: PS/2 mouse device common for all mice

[    2.016631] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0

[    2.016664] rtc0: alarms up to one month

[    2.016745] cpuidle: using governor ladder

[    2.016747] cpuidle: using governor menu

[    2.017207] TCP cubic registered

[    2.017621] registered taskstats version 1

[    2.017808]   Magic number: 0:163:500

[    2.017981] rtc_cmos 00:04: setting system clock to 2008-11-13 21:27:51 UTC (1226611671)

[    2.017985] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    2.017987] EDD information not available.

[    2.018054] Freeing unused kernel memory: 536k freed

[    2.018368] Write protecting the kernel read-only data: 4348k

[    2.019130] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

[    2.172263] fuse init (API version 7.9)

[    2.364124] ACPI: processor limited to max C-state 1

[    2.364258] processor ACPI0007:00: registered as cooling_device0

[    2.364379] processor ACPI0007:01: registered as cooling_device1

[    2.430330] thermal LNXTHERM:01: registered as thermal_zone0

[    2.489604] ACPI: Thermal Zone [THRM] (47 C)

[    2.845131] No dock devices found.

[    2.885695] usbcore: registered new interface driver usbfs

[    2.885726] usbcore: registered new interface driver hub

[    2.892032] usbcore: registered new device driver usb

[    2.913798] SCSI subsystem initialized

[    2.917582] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[    2.917605] ehci_hcd 0000:00:13.2: EHCI Host Controller

[    2.917677] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1

[    2.917754] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf0406000

[    2.922295] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver

[    2.928102] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[    2.928312] usb usb1: configuration #1 chosen from 1 choice

[    2.928347] hub 1-0:1.0: USB hub found

[    2.928358] hub 1-0:1.0: 8 ports detected

[    2.956742] libata version 3.00 loaded.

[    2.959790] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

[    3.032703] pata_acpi 0000:00:12.0: enabling device (0005 -> 0007)

[    3.032717] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

[    3.032847] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[    3.032872] ohci_hcd 0000:00:13.0: OHCI Host Controller

[    3.032937] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2

[    3.032961] ohci_hcd 0000:00:13.0: irq 19, io mem 0xf0404000

[    3.089448] usb usb2: configuration #1 chosen from 1 choice

[    3.089488] hub 2-0:1.0: USB hub found

[    3.089503] hub 2-0:1.0: 4 ports detected

[    3.193606] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[    3.193629] ohci_hcd 0000:00:13.1: OHCI Host Controller

[    3.193676] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3

[    3.193701] ohci_hcd 0000:00:13.1: irq 19, io mem 0xf0405000

[    3.249300] usb usb3: configuration #1 chosen from 1 choice

[    3.249336] hub 3-0:1.0: USB hub found

[    3.249350] hub 3-0:1.0: 4 ports detected

[    3.354344] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    3.354393] pata_acpi 0000:00:14.1: setting latency timer to 64

[    3.354729] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

[    3.354779] 8139cp 0000:06:01.0: Try the "8139too" driver instead.

[    3.362213] sata_sil 0000:00:12.0: version 2.3

[    3.365556] scsi0 : sata_sil

[    3.365695] 8139too Fast Ethernet driver 0.9.28

[    3.367644] scsi1 : sata_sil

[    3.368209] ata1: SATA max UDMA/100 mmio m512@0xf0407000 tf 0xf0407080 irq 22

[    3.368215] ata2: SATA max UDMA/100 mmio m512@0xf0407000 tf 0xf04070c0 irq 22

[    3.688098] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)

[    3.698208] ata1.00: ATA-7: ST98823AS, 3.06, max UDMA/133

[    3.698213] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)

[    3.712986] ata1.00: configured for UDMA/100

[    4.032085] ata2: SATA link down (SStatus 0 SControl 310)

[    4.032159] isa bounce pool size: 16 pages

[    4.032268] scsi 0:0:0:0: Direct-Access     ATA      ST98823AS        3.06 PQ: 0 ANSI: 5

[    4.033148] scsi2 : pata_atiixp

[    4.033285] scsi3 : pata_atiixp

[    4.784469] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14

[    4.784475] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15

[    4.948738] ata3.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.20, max UDMA/33

[    4.964685] ata3.00: configured for UDMA/33

[    5.123026] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.20 PQ: 0 ANSI: 5

[    5.123469] 8139too 0000:06:01.0: power state changed by ACPI to D0

[    5.123487] 8139too 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21

[    5.124779] eth0: RealTek RTL8139 at 0xa000, 00:16:d4:67:2a:54, IRQ 21

[    5.124781] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

[    5.138154] scsi 0:0:0:0: Attached scsi generic sg0 type 0

[    5.138212] scsi 2:0:0:0: Attached scsi generic sg1 type 5

[    5.161231] Driver 'sr' needs updating - please use bus_type methods

[    5.166437] Driver 'sd' needs updating - please use bus_type methods

[    5.166714] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[    5.166747] sd 0:0:0:0: [sda] Write Protect is off

[    5.166750] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    5.166802] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    5.166919] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[    5.166946] sd 0:0:0:0: [sda] Write Protect is off

[    5.166949] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    5.167040] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    5.167045]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

[    5.169554] Uniform CD-ROM driver Revision: 3.20

[    5.169698] sr 2:0:0:0: Attached scsi CD-ROM sr0

[    5.248173]  sda1 sda2 sda3

[    5.266038] sd 0:0:0:0: [sda] Attached SCSI disk

[    5.669433] PM: Starting manual resume from disk

[    5.669438] PM: Resume from partition 8:3

[    5.669440] PM: Checking hibernation image.

[    5.669684] PM: Resume from disk failed.

[    5.712465] kjournald starting.  Commit interval 5 seconds

[    5.712489] EXT3-fs: mounted filesystem with ordered data mode.

[   14.464197] udevd version 124 started

[   14.808218] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   14.836156] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   14.952101] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2

[   14.981047] ACPI: Power Button (FF) [PWRF]

[   14.981185] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3

[   14.981313] ACPI: Lid Switch [LID]

[   14.981382] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4

[   15.013087] ACPI: Power Button (CM) [PWRB]

[   15.013234] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5

[   15.041048] ACPI: Sleep Button (CM) [SLPB]

[   15.041454] ACPI: WMI: Mapper loaded

[   15.104907] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.

[   15.198236] [fglrx] Maximum main memory to use for locked dma buffers: 670 MBytes.

[   15.198293] [fglrx]   vendor: 1002 device: 5975 count: 1

[   15.199130] [fglrx] ioport: bar 1, base 0x9000, size: 0x100

[   15.199155] pci 0000:01:05.0: power state changed by ACPI to D0

[   15.199169] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[   15.200208] [fglrx] PAT is enabled successfully!

[   15.200257] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors

[   15.252328] ACPI: AC Adapter [ACAD] (on-line)

[   15.809603] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0

[   15.832892] ACPI: Battery Slot [BAT1] (battery present)

[   15.846445] acpi device:27: registered as cooling_device2

[   15.846997] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:24/device:25/input/input6

[   15.868081] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

[   15.868127] proc_dir_entry 'video/VGA' already registered

[   15.868133] Pid: 2535, comm: modprobe Tainted: P          2.6.27-7-generic #1

[   15.868136] 

[   15.868136] Call Trace:

[   15.868147]  [<ffffffff8033dea8>] proc_register+0x1e8/0x220

[   15.868151]  [<ffffffff8033e102>] proc_mkdir_mode+0x42/0x60

[   15.868155]  [<ffffffff8033e136>] proc_mkdir+0x16/0x20

[   15.868163]  [<ffffffffa03d0e99>] acpi_video_bus_add_fs+0x2d/0x199 [video]

[   15.868168]  [<ffffffffa03d2251>] acpi_video_bus_add+0xe8/0x2f7 [video]

[   15.868182]  [<ffffffff803ee550>] acpi_device_probe+0x4e/0x91

[   15.868188]  [<ffffffff80430552>] really_probe+0x72/0x1a0

[   15.868193]  [<ffffffff804306d0>] driver_probe_device+0x50/0x60

[   15.868197]  [<ffffffff8043076b>] __driver_attach+0x8b/0x90

[   15.868201]  [<ffffffff804306e0>] ? __driver_attach+0x0/0x90

[   15.868204]  [<ffffffff8042fcdb>] bus_for_each_dev+0x6b/0xa0

[   15.868209]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0

[   15.868214]  [<ffffffffa0081000>] ? acpi_video_init+0x0/0x63 [video]

[   15.868218]  [<ffffffff804303b1>] driver_attach+0x21/0x30

[   15.868221]  [<ffffffff8042f548>] bus_add_driver+0x1f8/0x270

[   15.868226]  [<ffffffffa0081000>] ? acpi_video_init+0x0/0x63 [video]

[   15.868230]  [<ffffffff80430965>] driver_register+0x75/0x170

[   15.868235]  [<ffffffffa0081000>] ? acpi_video_init+0x0/0x63 [video]

[   15.868239]  [<ffffffff803ee8a6>] acpi_bus_register_driver+0x43/0x45

[   15.868244]  [<ffffffffa0081041>] acpi_video_init+0x41/0x63 [video]

[   15.868248]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170

[   15.868253]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90

[   15.868258]  [<ffffffff8027d085>] sys_init_module+0xb5/0x1f0

[   15.868264]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b

[   15.868266] 

[   15.879473] acpi device:2c: registered as cooling_device3

[   15.879861] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:29/device:2a/input/input7

[   15.889032] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

[   16.056526] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

[   16.082675] sdhci: Secure Digital Host Controller Interface driver

[   16.082680] sdhci: Copyright(c) Pierre Ossman

[   16.090493] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)

[   16.090523] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23

[   16.090651] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO

[   16.090673] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)

[   16.090688] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)

[   16.090694] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 23 (level, low) -> IRQ 23

[   16.090747] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO

[   16.126780] Yenta: CardBus bridge found at 0000:06:04.0 [1025:009f]

[   16.126812] Yenta: Using CSCINT to route CSC interrupts to PCI

[   16.126815] Yenta: Routing CardBus interrupts to PCI

[   16.126822] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44

[   16.128089] input: PC Speaker as /devices/platform/pcspkr/input/input8

[   16.154454] wlan: 0.9.4

[   16.349698] ath_pci: 0.9.4

[   16.358273] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20

[   16.358280] Socket status: 30000006

[   16.358285] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff

[   16.358290] pcmcia: parent PCI bridge Memory window: 0xf0300000 - 0xf03fffff

[   16.358293] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff

[   16.361167] ath_pci 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

[   16.702059] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000

[   16.733674] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9

[   17.086736] ath_rate_sample: 1.2 (0.9.4)

[   17.127085] acer-wmi: Acer Laptop ACPI-WMI Extras

[   17.129128] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps

[   17.129137] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

[   17.129148] wifi0: H/W encryption support: WEP AES AES_CCM TKIP

[   17.129153] wifi0: mac 7.8 phy 4.5 radio 5.6

[   17.129161] wifi0: Use hw queue 1 for WME_AC_BE traffic

[   17.129163] wifi0: Use hw queue 0 for WME_AC_BK traffic

[   17.129165] wifi0: Use hw queue 2 for WME_AC_VI traffic

[   17.129167] wifi0: Use hw queue 3 for WME_AC_VO traffic

[   17.129170] wifi0: Use hw queue 8 for CAB traffic

[   17.129171] wifi0: Use hw queue 9 for beacons

[   17.134838] wifi0: Atheros 5212: mem=0xf0310000, irq=22

[   17.356597] Registered led device: acer-wmi::mail

[   17.489801] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[   19.485079] lp: driver loaded but no devices found

[   19.796269] Adding 1333384k swap on /dev/sda3.  Priority:-1 extents:1 across:1333384k

[   20.231086] EXT3 FS on sda1, internal journal

[   20.878820] type=1505 audit(1226611690.616:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4206

[   21.088273] type=1505 audit(1226611690.828:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4211

[   21.088564] type=1505 audit(1226611690.828:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4211

[   21.275561] ip_tables: (C) 2000-2006 Netfilter Core Team

[   22.081944] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (2 cpu cores) (version 2.20.00)

[   22.082033] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13

[   22.082038] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14

[   22.082041] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a

[   23.774048] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)

[   24.310490] ppdev: user-space parallel port driver

[   24.849063] Clocksource tsc unstable (delta = -186944099 ns)

[   30.352485] Bluetooth: Core ver 2.13

[   30.356257] NET: Registered protocol family 31

[   30.356272] Bluetooth: HCI device and connection manager initialized

[   30.356283] Bluetooth: HCI socket layer initialized

[   30.414733] Bluetooth: L2CAP ver 2.11

[   30.414764] Bluetooth: L2CAP socket layer initialized

[   30.490196] Bluetooth: SCO (Voice Link) ver 0.6

[   30.490229] Bluetooth: SCO socket layer initialized

[   30.550589] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[   30.550605] Bluetooth: BNEP filters: protocol multicast

[   30.582172] Bluetooth: RFCOMM socket layer initialized

[   30.585238] Bluetooth: RFCOMM TTY layer initialized

[   30.585264] Bluetooth: RFCOMM ver 1.10

[   30.621503] Bridge firewalling registered

[   30.623784] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.

[   34.373078] [fglrx] GART Table is not in FRAME_BUFFER range 

[   34.380304] [fglrx] CMM init INV FB MC:0x38000000, length:0x8000000

[   34.380327] [fglrx] Reserved FB block: Shared offset:0, size:40000 

[   34.812629] eth0: link down

[   34.893692] NET: Registered protocol family 17

[   42.210446] hda-intel: Invalid position buffer, using LPIB read method instead.

[   84.941797] NET: Registered protocol family 10

[   84.944137] lo: Disabled Privacy Extensions

[   84.945843] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   88.798474] CPU0 attaching NULL sched-domain.

[   88.798516] CPU1 attaching NULL sched-domain.

[   88.816194] CPU0 attaching sched-domain:

[   88.816207]  domain 0: span 0-1 level CPU

[   88.816213]   groups: 0 1

[   88.816226]   domain 1: span 0-1 level NODE

[   88.816231]    groups: 0-1

[   88.816240] CPU1 attaching sched-domain:

[   88.816244]  domain 0: span 0-1 level CPU

[   88.816248]   groups: 1 0

[   88.816255]   domain 1: span 0-1 level NODE

[   88.816259]    groups: 0-1

[   95.037043] ath0: no IPv6 routers present

[  545.261368] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

[  545.261389] ata3.00: ST_FIRST: !(DRQ|ERR|DF)

[  545.261407] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0

[  545.261410]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00

[  545.261414]          res 50/50:50:50:50:50/00:00:00:00:00/50 Emask 0x2 (HSM violation)

[  545.261422] ata3.00: status: { DRDY }

[  545.261470] ata3: soft resetting link

[  545.417326] ata3.00: NODEV after polling detection

[  545.417343] ata3.00: revalidation failed (errno=-2)

[  550.417112] ata3: soft resetting link

[  550.572331] ata3.00: NODEV after polling detection

[  550.572348] ata3.00: revalidation failed (errno=-2)

[  555.572135] ata3: soft resetting link

[  555.752738] ata3.00: configured for UDMA/33

[  555.752803] ata3: EH complete

[ 3616.265351] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

[ 3616.265371] ata3.00: ST_FIRST: !(DRQ|ERR|DF)

[ 3616.265388] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0

[ 3616.265391]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00

[ 3616.265395]          res 50/50:50:50:50:50/00:00:00:00:00/50 Emask 0x2 (HSM violation)

[ 3616.265403] ata3.00: status: { DRDY }

[ 3616.265452] ata3: soft resetting link

[ 3616.420375] ata3.00: NODEV after polling detection

[ 3616.420391] ata3.00: revalidation failed (errno=-2)

[ 3621.421116] ata3: soft resetting link

[ 3621.600742] ata3.00: configured for UDMA/33

[ 3621.600803] ata3: EH complete

[ 4310.265385] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

[ 4310.265405] ata3.00: ST_FIRST: !(DRQ|ERR|DF)

[ 4310.265424] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0

[ 4310.265427]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00

[ 4310.265430]          res 50/50:50:50:50:50/00:00:00:00:00/50 Emask 0x2 (HSM violation)

[ 4310.265439] ata3.00: status: { DRDY }

[ 4310.265487] ata3: soft resetting link

[ 4310.421322] ata3.00: NODEV after polling detection

[ 4310.421338] ata3.00: revalidation failed (errno=-2)

[ 4315.420113] ata3: soft resetting link

[ 4315.601793] ata3.00: configured for UDMA/33

[ 4315.601860] ata3: EH complete

[ 7064.264360] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

[ 7064.264379] ata3.00: ST_FIRST: !(DRQ|ERR|DF)

[ 7064.264396] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0

[ 7064.264399]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00

[ 7064.264403]          res 50/50:50:50:50:50/00:00:00:00:00/50 Emask 0x2 (HSM violation)

[ 7064.264411] ata3.00: status: { DRDY }

[ 7064.264457] ata3: soft resetting link

[ 7064.421322] ata3.00: NODEV after polling detection

[ 7064.421339] ata3.00: revalidation failed (errno=-2)

[ 7069.420124] ata3: soft resetting link

[ 7069.577333] ata3.00: NODEV after polling detection

[ 7069.577350] ata3.00: revalidation failed (errno=-2)

[ 7074.576112] ata3: soft resetting link

[ 7074.733328] ata3.00: NODEV after polling detection

[ 7074.733345] ata3.00: revalidation failed (errno=-2)

[ 7074.733354] ata3.00: disabled

[ 7074.733427] ata3: soft resetting link

[ 7074.889180] ata3: EH complete

[19157.872109] usb 1-1: new high speed USB device using ehci_hcd and address 2

[19158.114620] usb 1-1: configuration #1 chosen from 1 choice

[19158.546707] usbcore: registered new interface driver libusual

[19158.596598] Initializing USB Mass Storage driver...

[19158.599272] scsi4 : SCSI emulation for USB Mass Storage devices

[19158.602058] usb-storage: device found at 2

[19158.602078] usb-storage: waiting for device to settle before scanning

[19158.602093] usbcore: registered new interface driver usb-storage

[19158.608853] USB Mass Storage support registered.

[19163.600549] usb-storage: device scan complete

[19163.602430] scsi 4:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS

[19164.916562] sd 4:0:0:0: [sdb] 7831552 512-byte hardware sectors (4010 MB)

[19164.920585] sd 4:0:0:0: [sdb] Write Protect is off

[19164.920603] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00

[19164.920610] sd 4:0:0:0: [sdb] Assuming drive cache: write through

[19164.931954] sd 4:0:0:0: [sdb] 7831552 512-byte hardware sectors (4010 MB)

[19164.933965] sd 4:0:0:0: [sdb] Write Protect is off

[19164.933986] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00

[19164.933993] sd 4:0:0:0: [sdb] Assuming drive cache: write through

[19164.935111]  sdb: sdb1

[19164.937564] sd 4:0:0:0: [sdb] Attached SCSI removable disk

[19164.940037] sd 4:0:0:0: Attached scsi generic sg2 type 0

[19563.873185] usb 1-1: USB disconnect, address 2
```

jim@jim-laptop:~$

---

### Post by sisco311 on 2008-11-13
post:
```
lshw -C disk
```
and ```
cat /etc/fstab
```

---

### Post by hurstja on 2008-11-14
lshw -C disk replies:```
 *-disk                  
       description: ATA Disk
       product: ST98823AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.06
       serial: 5PK2XN72
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=870b83b4

```

cat /etc/fstab replies:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=628d507f-9fcf-4496-a470-f47198bac724 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=85084ee2-6243-458f-840c-5f75e1c1d761 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jim@jim-laptop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=628d507f-9fcf-4496-a470-f47198bac724 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=85084ee2-6243-458f-840c-5f75e1c1d761 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jim@jim-laptop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=628d507f-9fcf-4496-a470-f47198bac724 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=85084ee2-6243-458f-840c-5f75e1c1d761 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
doesn't recognize.

I appreciate your help.

---

### Post by hurstja on 2008-11-21
Works now.

---

### Post by kahping on 2009-05-02
> **hurstja said:**
> Works now.

how did you get it to detect the drive? i'm having similar problems right now

---

### Post by _FR0D0 on 2009-05-28
I'm having the same problem

---

### Post by Knyte on 2009-05-31
Would like to see a solution to this as well..

---

### Post by Malta paul on 2009-06-01
At the risk of stating the obvious, 
1) have you set your BIOS to detect the CD drive?
2) Have you set your drive to 'master' if you are using only one?
Ubuntu should then detect your drive ;)

---

### Post by Knyte on 2009-06-07
> **Malta paul said:**
> At the risk of stating the obvious, 
1) have you set your BIOS to detect the CD drive?
2) Have you set your drive to 'master' if you are using only one?
Ubuntu should then detect your drive ;)

yes all that was done on my end with no joy.. ](*,)

My issue turned out to be the drive (LG HSA-H55N/L) failing in the dvd reading dept. Once I replaced it with a Samsung SH-S222A I have no issue with blank dvd media.. Now if I can get a proper veiwer to watch dvd movies I will be happy..

---

