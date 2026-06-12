---
title: "cayman"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-09-25
this morning I was downloading skype,whilst downloading my screen turned off I got an error message when rebooting the error report wouldnt load it said something to do with cayman and it wanted to also send report to kernel oopss.org here is my dmesg can anyone see whats happening here
```
[    0.786431] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.786433] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.786438] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.786442] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.786465] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.786469] pci 0000:00:02.0: setting latency timer to 64
[    0.786474] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.786477] pci 0000:00:06.0: setting latency timer to 64
[    0.786485] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.786487] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.786489] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.786492] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.786494] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.786496] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.786499] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.786501] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.786503] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.786505] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.786508] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.786510] pci_bus 0000:02: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.786513] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.786515] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.786517] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.786519] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.786522] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.786524] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.786562] NET: Registered protocol family 2
[    0.786796] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.788705] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.792360] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.792829] TCP: Hash tables configured (established 524288 bind 65536)
[    0.792832] TCP reno registered
[    0.792850] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.792927] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.793110] NET: Registered protocol family 1
[    0.980033] pci 0000:01:00.0: Boot video device
[    0.980041] PCI: CLS 64 bytes, default 64
[    0.981175] PCI-DMA: Disabling AGP.
[    0.981266] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.981267] PCI-DMA: using GART IOMMU.
[    0.981271] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.984298] audit: initializing netlink socket (disabled)
[    0.984311] type=2000 audit(1316933089.980:1): initialized
[    1.029741] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.082473] VFS: Disk quotas dquot_6.5.2
[    1.082535] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.083187] fuse init (API version 7.16)
[    1.083301] msgmni has been set to 15998
[    1.083762] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.083805] io scheduler noop registered
[    1.083807] io scheduler deadline registered
[    1.083858] io scheduler cfq registered (default)
[    1.084011] pcieport 0000:00:02.0: setting latency timer to 64
[    1.084045] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.084136] pcieport 0000:00:06.0: setting latency timer to 64
[    1.084162] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    1.084238] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.084262] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.084389] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.084394] ACPI: Power Button [PWRB]
[    1.084439] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.084442] ACPI: Power Button [PWRF]
[    1.084471] ACPI: acpi_idle registered with cpuidle
[    1.190362] ERST: Table is not found!
[    1.190440] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.211112] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.252016] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.252302] Linux agpgart interface v0.103
[    1.253445] brd: module loaded
[    1.253994] loop: module loaded
[    1.254266] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.254300] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.254688] Fixed MDIO Bus: probed
[    1.254711] PPP generic driver version 2.4.2
[    1.254753] tun: Universal TUN/TAP device driver, 1.6
[    1.254755] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.254839] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.254898] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.254925] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.254982] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.254996] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.255021] QUIRK: Enable AMD PLL fix
[    1.255024] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.255038] ehci_hcd 0000:00:12.2: debug port 1
[    1.255062] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbdff000
[    1.270024] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.270137] hub 1-0:1.0: USB hub found
[    1.270142] hub 1-0:1.0: 6 ports detected
[    1.270283] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.270297] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.270337] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.270353] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.270367] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.270381] ehci_hcd 0000:00:13.2: debug port 1
[    1.270399] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbdfa800
[    1.290024] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.290117] hub 2-0:1.0: USB hub found
[    1.290120] hub 2-0:1.0: 6 ports detected
[    1.290203] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.290249] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.290262] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.290302] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.290333] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbdfe000
[    1.354113] hub 3-0:1.0: USB hub found
[    1.354123] hub 3-0:1.0: 3 ports detected
[    1.354234] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.354246] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.354286] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.354309] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbdfd000
[    1.414110] hub 4-0:1.0: USB hub found
[    1.414120] hub 4-0:1.0: 3 ports detected
[    1.414232] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.414244] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.414282] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.414317] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbdfc000
[    1.474116] hub 5-0:1.0: USB hub found
[    1.474126] hub 5-0:1.0: 3 ports detected
[    1.474235] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.474247] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.474294] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.474314] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbdfb000
[    1.534110] hub 6-0:1.0: USB hub found
[    1.534120] hub 6-0:1.0: 3 ports detected
[    1.534232] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.534244] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.534282] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.534308] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbdf9000
[    1.590031] usb 1-3: new high speed USB device number 2 using ehci_hcd
[    1.594109] hub 7-0:1.0: USB hub found
[    1.594119] hub 7-0:1.0: 2 ports detected
[    1.594195] uhci_hcd: USB Universal Host Controller Interface driver
[    1.594276] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.594662] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.594667] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.594737] mousedev: PS/2 mouse device common for all mice
[    1.594840] rtc_cmos 00:03: RTC can wake from S4
[    1.594938] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.594965] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.595067] device-mapper: uevent: version 1.0.3
[    1.595144] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.595156] cpuidle: using governor ladder
[    1.595157] cpuidle: using governor menu
[    1.595159] EFI Variables Facility v0.08 2004-May-17
[    1.595404] TCP cubic registered
[    1.595533] NET: Registered protocol family 10
[    1.595995] NET: Registered protocol family 17
[    1.596013] Registering the dns_resolver key type
[    1.596115] PM: Hibernation image not present or could not be loaded.
[    1.596134] registered taskstats version 1
[    1.628176]   Magic number: 11:216:722
[    1.628190] block loop2: hash matches
[    1.628272] rtc_cmos 00:03: setting system clock to 2011-09-25 06:44:50 UTC (1316933090)
[    1.628280] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ (2 cpu cores) (version 2.20.00)
[    1.628317] powernow-k8: fid 0x12 (2600 MHz), vid 0xc
[    1.628319] powernow-k8: fid 0x10 (2400 MHz), vid 0xe
[    1.628320] powernow-k8: fid 0xe (2200 MHz), vid 0x10
[    1.628322] powernow-k8: fid 0xc (2000 MHz), vid 0x10
[    1.628323] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    1.628325] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.628595] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.628596] EDD information not available.
[    1.630359] Freeing unused kernel memory: 984k freed
[    1.630748] Write protecting the kernel read-only data: 10240k
[    1.630955] Freeing unused kernel memory: 20k freed
[    1.635450] Freeing unused kernel memory: 1400k freed
[    1.656405] udevd[114]: starting version 173
[    1.744439] scsi0 : pata_atiixp
[    1.746692] scsi1 : pata_atiixp
[    1.747312] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.747315] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.750912] ahci 0000:00:11.0: version 3.0
[    1.750941] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.751063] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.751067] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.753216] scsi2 : ahci
[    1.755765] scsi3 : ahci
[    1.758913] scsi4 : ahci
[    1.761454] scsi5 : ahci
[    1.761597] ata3: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdff900 irq 22
[    1.761601] ata4: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdff980 irq 22
[    1.761605] ata5: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdffa00 irq 22
[    1.761608] ata6: SATA max UDMA/133 abar m1024@0xfbdff800 port 0xfbdffa80 irq 22
[    1.768470] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.768499] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.768541] r8169 0000:02:00.0: setting latency timer to 64
[    1.768587] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.769012] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000c72000, 00:24:8c:d6:ab:ef, XID 1c4000c0 IRQ 42
[    1.775982] Floppy drive(s): fd0 is 1.44M
[    1.793862] FDC 0 is a post-1991 82077
[    1.950379] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100
[    1.950385] ata2.01: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    1.990388] ata2.00: configured for UDMA/100
[    2.030382] ata2.01: configured for UDMA/100
[    2.040561] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
[    2.049692] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.049694] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.049815] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.049886] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    2.054280] scsi 1:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    2.057552] sr1: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.057646] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.057707] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    2.080035] usb 1-4: new high speed USB device number 3 using ehci_hcd
[    2.310028] ata4: softreset failed (device not ready)
[    2.310033] ata4: applying SB600 PMP SRST workaround and retrying
[    2.310052] ata6: softreset failed (device not ready)
[    2.310057] ata6: applying SB600 PMP SRST workaround and retrying
[    2.310074] ata3: softreset failed (device not ready)
[    2.310077] ata3: applying SB600 PMP SRST workaround and retrying
[    2.310094] ata5: softreset failed (device not ready)
[    2.310097] ata5: applying SB600 PMP SRST workaround and retrying
[    2.510038] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.510064] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.510090] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.510110] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.511051] ata3.00: ATA-8: ST3250312AS, JC45, max UDMA/133
[    2.511054] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.511348] ata5.00: ATA-8: WDC WD10EARS-003BB1, 80.00A80, max UDMA/133
[    2.511351] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.512058] ata4.00: ATA-8: WDC WD10EARS-003BB1, 80.00A80, max UDMA/133
[    2.512061] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.512152] ata6.00: ATA-8: WDC WD10EARS-003BB1, 80.00A80, max UDMA/133
[    2.512155] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.512262] ata3.00: configured for UDMA/133
[    2.512406] scsi 2:0:0:0: Direct-Access     ATA      ST3250312AS      JC45 PQ: 0 ANSI: 5
[    2.512550] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.512573] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.512598] sd 2:0:0:0: [sda] Write Protect is off
[    2.512601] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.512622] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.512730] ata5.00: configured for UDMA/133
[    2.514431] ata4.00: configured for UDMA/133
[    2.514543] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EARS-003 80.0 PQ: 0 ANSI: 5
[    2.514660] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.514676] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.514704] sd 3:0:0:0: [sdb] Write Protect is off
[    2.514707] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.514725] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.514770] scsi 4:0:0:0: Direct-Access     ATA      WDC WD10EARS-003 80.0 PQ: 0 ANSI: 5
[    2.514900] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    2.514957] sd 4:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.515004] sd 4:0:0:0: [sdc] Write Protect is off
[    2.515007] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.515027] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.515162] ata6.00: configured for UDMA/133
[    2.515265] scsi 5:0:0:0: Direct-Access     ATA      WDC WD10EARS-003 80.0 PQ: 0 ANSI: 5
[    2.515393] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    2.515463] sd 5:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.515506] sd 5:0:0:0: [sdd] Write Protect is off
[    2.515509] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.515527] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.523168]  sda: sda1 sda2
[    2.523473] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.549582]  sdb: sdb1 sdb2 < sdb5 >
[    2.549859] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.573029]  sdd: sdd1 sdd2 < sdd5 sdd6 sdd7 >
[    2.573339] sd 5:0:0:0: [sdd] Attached SCSI disk
[    2.800026] usb 5-3: new full speed USB device number 2 using ohci_hcd
[    2.956761]  sdc: sdc1 sdc2 < sdc5 >
[    2.957056] sd 4:0:0:0: [sdc] Attached SCSI disk
[    3.009377] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input2
[    3.009475] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-3/input0
[    3.014633] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.1/input/input3
[    3.014796] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3/input1
[    3.023457] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3/input2
[    3.023477] usbcore: registered new interface driver usbhid
[    3.023479] usbhid: USB HID core driver
[    3.330040] usb 6-1: new full speed USB device number 2 using ohci_hcd
[    3.535349] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input4
[    3.535461] generic-usb 0003:046D:C526.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1/input0
[    3.543187] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input5
[    3.543306] generic-usb 0003:046D:C526.0005: input,hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.1-1/input1
[    3.739263] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   15.644424] udevd[407]: starting version 173
[   15.703213] Adding 8386556k swap on /dev/sdb5.  Priority:-1 extents:1 across:8386556k 
[   15.704960] lp: driver loaded but no devices found
[   15.729809] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.730348] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   15.730467] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   15.764878] [drm] Initialized drm 1.1.0 20060810
[   15.792181] type=1400 audit(1316933104.652:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=508 comm="apparmor_parser"
[   15.792596] type=1400 audit(1316933104.652:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   15.792854] type=1400 audit(1316933104.652:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   15.946337] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.984203] MCE: In-kernel MCE decoding enabled.
[   15.988766] [drm] radeon defaulting to kernel modesetting.
[   15.988771] [drm] radeon kernel modesetting enabled.
[   15.988940] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.989178] EDAC MC: Ver: 2.1.0
[   15.993064] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.993071] radeon 0000:01:00.0: setting latency timer to 64
[   15.993403] [drm] initializing kernel modesetting (CAYMAN 0x1002:0x6719 0x1043:0x03BA).
[   15.993446] [drm] register mmio base: 0xFBEE0000
[   15.993448] [drm] register mmio size: 131072
[   15.994048] ATOM BIOS: 6719.13.8.0.9.AS01
[   15.994086] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   15.994089] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[   15.994245] [drm] Detected VRAM RAM=2048M, BAR=256M
[   15.994249] [drm] RAM width 256bits DDR
[   15.994835] AMD64 EDAC driver v3.4.0
[   15.995135] [TTM] Zone  kernel: Available graphics memory: 4096718 kiB.
[   15.995137] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[   15.995138] [TTM] Initializing pool allocator.
[   15.995166] [drm] radeon: 2048M of VRAM memory ready
[   15.995168] [drm] radeon: 512M of GTT memory ready.
[   15.995184] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.995186] [drm] Driver supports precise vblank timestamp query.
[   15.995233] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[   15.995241] radeon 0000:01:00.0: radeon: using MSI.
[   15.995281] [drm] radeon: irq initialized.
[   15.995286] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.996723] [drm] Loading CAYMAN Microcode
[   16.034850] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   16.037043] EDAC amd64: DRAM ECC disabled.
[   16.037052] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   16.037053]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   16.037054]  (Note that use of the override may cause unknown side effects.)
[   16.060282] lp0: using parport0 (interrupt-driven).
[   16.196229] ppdev: user-space parallel port driver
[   16.220307] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   16.224606] Linux video capture interface: v2.00
[   16.225311] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0809)
[   16.257550] input: UVC Camera (046d:0809) as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input6
[   16.257664] usbcore: registered new interface driver uvcvideo
[   16.257666] USB Video Class driver (v1.1.0)
[   16.299625] radeon 0000:01:00.0: WB enabled
[   16.318042] [drm] ring test succeeded in 3 usecs
[   16.318159] [drm] radeon: ib pool ready.
[   16.318231] [drm] ib test succeeded in 0 usecs
[   16.318237] failed to evaluate ATIF got AE_BAD_PARAMETER
[   16.318736] [drm] Radeon Display Connectors
[   16.318737] [drm] Connector 0:
[   16.318739] [drm]   DisplayPort
[   16.318740] [drm]   HPD5
[   16.318742] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   16.318743] [drm]   Encoders:
[   16.318745] [drm]     DFP1: INTERNAL_UNIPHY2
[   16.318746] [drm] Connector 1:
[   16.318747] [drm]   DisplayPort
[   16.318748] [drm]   HPD4
[   16.318750] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   16.318752] [drm]   Encoders:
[   16.318753] [drm]     DFP2: INTERNAL_UNIPHY2
[   16.318754] [drm] Connector 2:
[   16.318755] [drm]   HDMI-A
[   16.318756] [drm]   HPD6
[   16.318758] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   16.318759] [drm]   Encoders:
[   16.318761] [drm]     DFP3: INTERNAL_UNIPHY1
[   16.318762] [drm] Connector 3:
[   16.318763] [drm]   DVI-D
[   16.318764] [drm]   HPD1
[   16.318766] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[   16.318767] [drm]   Encoders:
[   16.318768] [drm]     DFP4: INTERNAL_UNIPHY1
[   16.318770] [drm] Connector 4:
[   16.318771] [drm]   DVI-I
[   16.318772] [drm]   HPD3
[   16.318773] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[   16.318775] [drm]   Encoders:
[   16.318776] [drm]     DFP5: INTERNAL_UNIPHY
[   16.318777] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   16.556513] type=1400 audit(1316933105.412:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=999 comm="apparmor_parser"
[   16.556948] type=1400 audit(1316933105.412:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=999 comm="apparmor_parser"
[   16.557211] type=1400 audit(1316933105.412:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=999 comm="apparmor_parser"
[   16.565526] type=1400 audit(1316933105.422:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1000 comm="apparmor_parser"
[   16.568834] type=1400 audit(1316933105.422:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1002 comm="apparmor_parser"
[   16.569278] type=1400 audit(1316933105.422:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1002 comm="apparmor_parser"
[   16.575536] type=1400 audit(1316933105.432:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1000 comm="apparmor_parser"
[   16.662186] set resolution quirk: cval->res = 384
[   16.662376] usbcore: registered new interface driver snd-usb-audio
[   16.759057] r8169 0000:02:00.0: eth0: link down
[   16.759067] r8169 0000:02:00.0: eth0: link down
[   16.760957] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.163379] Bluetooth: Core ver 2.16
[   17.163447] NET: Registered protocol family 31
[   17.163449] Bluetooth: HCI device and connection manager initialized
[   17.163452] Bluetooth: HCI socket layer initialized
[   17.163454] Bluetooth: L2CAP socket layer initialized
[   17.164106] Bluetooth: SCO socket layer initialized
[   17.166749] Bluetooth: RFCOMM TTY layer initialized
[   17.166756] Bluetooth: RFCOMM socket layer initialized
[   17.166758] Bluetooth: RFCOMM ver 1.11
[   17.175156] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.175161] Bluetooth: BNEP filters: protocol multicast
[   17.523964] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   17.540052] [drm] Radeon display connector DP-1: No monitor connected or invalid EDID
[   18.740048] [drm] Radeon display connector DP-2: No monitor connected or invalid EDID
[   18.750930] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[   18.761718] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
[   18.820584] [drm] Radeon display connector DVI-I-1: Found valid EDID
[   18.820647] [drm] Internal thermal controller with fan control
[   18.822007] [drm] radeon: power management initialized
[   18.823763] r8169 0000:02:00.0: eth0: link up
[   18.824706] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.934738] [drm] fb mappable at 0xD0141000
[   18.934741] [drm] vram apper at 0xD0000000
[   18.934743] [drm] size 8294400
[   18.934744] [drm] fb depth is 24
[   18.934745] [drm]    pitch is 7680
[   18.934843] fbcon: radeondrmfb (fb0) is primary device
[   18.935095] Console: switching to colour frame buffer device 240x67
[   18.935133] fb0: radeondrmfb frame buffer device
[   18.935135] drm: registered panic notifier
[   18.935144] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
[   18.944351] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   18.944431] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
[   18.944455] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.952379] init: plymouth-splash main process (1290) terminated with status 1
[   18.986334] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   18.986463] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input7
[   19.386667] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[   21.960547] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   29.290014] eth0: no IPv6 routers present

```

---

### Post by dino99 on 2011-09-25
why dont you use pae kernel instead of 64 bits ?

---

### Post by rbrick49 on 2011-09-25
Dino I had pae kernel when it came available also 64 bits someone told me to get rid of pae so what is the advantage with pae kernel over 64 bits
regards ron

---

### Post by dino99 on 2011-09-25
here it is

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by rbrick49 on 2011-09-25
what is the code for that kernel Dino I did a fresh install last week and it didnt come in the updates I used the alternative cd 
regards Ron

---

### Post by cariboo on 2011-09-25
There is no pae kernel for 64-bit, dino99 has some sort of problem with 64-bit, so at every opportunity, he posts an anti 64-bit comment

---

### Post by effenberg0x0 on 2011-09-25
Hey rbrick49, 

As you are probably aware, CAYMAN is the GPU series of some RADEON cards. I see it on your dmesg at:

[drm] initializing kernel modesetting (CAYMAN 0x1002:0x6719 0x1043:0x03BA).
[   15.996723] [drm] Loading CAYMAN Microcode

They're supposed to be supported OK, as far as I can tell from some browsing. I could find no report of a serious kernel crash related to it. 
 
Unfortunately I don't have ATI hardware to test right now, only NVidia. Others here will probably be able to give you more insight on ATI support in beta 2. However, at the risk of saying the obvious, I would try removing / purging / reinstalling ATI-related packages if you continue to see weird behaviors like the one you reported. The following commands usually have helped putting an ATI based PC to work.

```

sudo apt-get remove --purge nvidia* 
sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx 
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati 
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core 
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Regards,
Effenberg

---

### Post by rbrick49 on 2011-09-26
> **cariboo907 said:**
> There is no pae kernel for 64-bit, dino99 has some sort of problem with 64-bit, so at every opportunity, he posts an anti 64-bit comment
thanks mate

---

### Post by rbrick49 on 2011-09-26
> **effenberg0x0 said:**
> Hey rbrick49, 

As you are probably aware, CAYMAN is the GPU series of some RADEON cards. I see it on your dmesg at:

[drm] initializing kernel modesetting (CAYMAN 0x1002:0x6719 0x1043:0x03BA).
[   15.996723] [drm] Loading CAYMAN Microcode

They're supposed to be supported OK, as far as I can tell from some browsing. I could find no report of a serious kernel crash related to it. 
 
Unfortunately I don't have ATI hardware to test right now, only NVidia. Others here will probably be able to give you more insight on ATI support in beta 2. However, at the risk of saying the obvious, I would try removing / purging / reinstalling ATI-related packages if you continue to see weird behaviors like the one you reported. The following commands usually have helped putting an ATI based PC to work.

```

sudo apt-get remove --purge nvidia* 
sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx 
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati 
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core 
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Regards,
Effenberg thanks Effenberg I have a ati 6950 graphics card fglrx is not up to speed october they are saying but I did a purge to see what happened there was some nvidia stuff installed but its gone now so will just keep on testing with mesa, its working ok gnome-shell works great with it
thanks again regards ron

---

