---
title: "Sony mp3 won't work"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by telltommy on 2008-09-28
Hi folks,
I'm thrilled I got Ubuntu working, printer, scanner, my email all working it's great to say good by to Windows. Now the next problem to solve. I plug in my sony NWZ-B105F Black MP3 Player and nothing. I went to applications and terminal and entered some suggestions from an earlier post but it didn't work and i'm not very skilled at programing. I'm new so any help step by step (don't leave anything out) would be great.:confused: thanks.

---

### Post by victorbrca on 2008-09-28
First thing is we need to find out if your computer recognized the player. 

Open a terminal, connect the player (in this order) and issue the following commands:

```
dmesg
lsusb
```

Copy the output here.

Also, check if your player has a HD option.


Vic.

---

### Post by telltommy on 2008-09-29
20.827972]  domain 0: span 03
[   20.827974]   groups: 01 02
[   20.827978]   domain 1: span 03
[   20.827980]    groups: 03
[   20.827982] CPU1 attaching sched-domain:
[   20.827984]  domain 0: span 03
[   20.827986]   groups: 02 01
[   20.827988]   domain 1: span 03
[   20.827990]    groups: 03
[   20.828258] net_namespace: 64 bytes
[   20.828267] Booting paravirtualized kernel on bare hardware
[   20.828792] Time: 13:03:21  Date: 09/28/08
[   20.828816] NET: Registered protocol family 16
[   20.829078] EISA bus registered
[   20.829084] ACPI: bus type pci registered
[   20.853240] PCI: PCI BIOS revision 3.00 entry at 0xf1ea0, last bus=1
[   20.853242] PCI: Using configuration type 1
[   20.853256] Setting up standard PCI resources
[   20.865395] ACPI: EC: Look up EC in DSDT
[   20.870237] ACPI: Interpreter enabled
[   20.870245] ACPI: (supports S0 S1 S3 S4 S5)
[   20.870264] ACPI: Using IOAPIC for interrupt routing
[   20.875529] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.876598] PCI: Transparent bridge - 0000:00:1e.0
[   20.876622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.876810] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   20.888353] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   20.888476] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   20.888598] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   20.888718] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   20.888837] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   20.888957] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   20.889077] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   20.889201] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[   20.889362] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.889404] pnp: PnP ACPI init
[   20.889414] ACPI: bus type pnp registered
[   20.891706] pnpacpi: exceeded the max number of mem resources: 12
[   20.891784] pnp: PnP ACPI: found 14 devices
[   20.891786] ACPI: ACPI bus type pnp unregistered
[   20.891791] PnPBIOS: Disabled by ACPI PNP
[   20.892103] PCI: Using ACPI for IRQ routing
[   20.892106] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.927510] NET: Registered protocol family 8
[   20.927513] NET: Registered protocol family 20
[   20.927570] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.927577] hpet0: 3 64-bit timers, 14318180 Hz
[   20.928616] AppArmor: AppArmor Filesystem Enabled
[   20.931493] Time: tsc clocksource has been installed.
[   20.931511] Switched to high resolution mode on CPU 0
[   20.931649] Switched to high resolution mode on CPU 1
[   20.947482] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   20.947487] system 00:01: ioport range 0x800-0x87f has been reserved
[   20.947490] system 00:01: ioport range 0x294-0x297 has been reserved
[   20.947493] system 00:01: ioport range 0x880-0x88f has been reserved
[   20.947513] system 00:0a: ioport range 0x400-0x4bf has been reserved
[   20.947519] system 00:0c: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   20.947525] system 00:0d: iomem range 0xd0800-0xd3fff has been reserved
[   20.947528] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   20.947531] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   20.947533] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   20.947536] system 00:0d: iomem range 0xfed00000-0xfed000ff could not be reserved
[   20.947539] system 00:0d: iomem range 0x3f6e0000-0x3f6fffff could not be reserved
[   20.947541] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   20.947544] system 00:0d: iomem range 0x100000-0x3f6dffff could not be reserved
[   20.947546] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   20.947549] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[   20.947552] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.947554] system 00:0d: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   20.978029] PCI: Bridge: 0000:00:1e.0
[   20.978033]   IO window: e000-efff
[   20.978038]   MEM window: fde00000-fdefffff
[   20.978042]   PREFETCH window: disabled.
[   20.978058] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.978070] NET: Registered protocol family 2
[   21.015313] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.015588] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.016139] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.016419] TCP: Hash tables configured (established 131072 bind 65536)
[   21.016422] TCP reno registered
[   21.027364] checking if image is initramfs... it is
[   21.574038] Freeing initrd memory: 7325k freed
[   21.574932] audit: initializing netlink socket (disabled)
[   21.574949] audit(1222607001.265:1): initialized
[   21.575146] highmem bounce pool size: 64 pages
[   21.577503] VFS: Disk quotas dquot_6.5.1
[   21.577596] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.577738] io scheduler noop registered
[   21.577741] io scheduler anticipatory registered
[   21.577743] io scheduler deadline registered
[   21.577754] io scheduler cfq registered (default)
[   21.577765] Boot video device is 0000:00:02.0
[   21.577845] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   21.578174] isapnp: Scanning for PnP cards...
[   21.928811] isapnp: No Plug & Play device found
[   21.964857] Real Time Clock Driver v1.12ac
[   21.965101] hpet_resources: 0xfed00000 is busy
[   21.965137] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.966655] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.966735] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.966863] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.969225] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.969234] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.988656] mice: PS/2 mouse device common for all mice
[   21.988805] EISA: Probing bus 0 at eisa.0
[   21.988834] EISA: Detected 0 cards.
[   21.988838] cpuidle: using governor ladder
[   21.988840] cpuidle: using governor menu
[   21.988917] NET: Registered protocol family 1
[   21.988945] Using IPI No-Shortcut mode
[   21.988975] registered taskstats version 1
[   21.989068]   Magic number: 8:15:80
[   21.989169] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.989171] EDD information not available.
[   21.989362] Freeing unused kernel memory: 368k freed
[   22.006366] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.207389] fuse init (API version 7.9)
[   23.222011] ACPI: Fan [FAN] (on)
[   23.227238] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PDC] (Node f7c500d8), AE_ALREADY_EXISTS
[   23.227247] ACPI: Marking method _PDC as Serialized
[   23.227447] ACPI: SSDT 3F6E8410, 00CE (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[   23.227621] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.227633] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.229035] ACPI: Thermal Zone [THRM] (-269 C)
[   23.381455] usbcore: registered new interface driver usbfs
[   23.381491] usbcore: registered new interface driver hub
[   23.389120] usbcore: registered new device driver usb
[   23.398976] USB Universal Host Controller Interface driver v3.0
[   23.399047] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 16
[   23.399064] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.399070] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.399308] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.399343] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000fe00
[   23.399532] usb usb1: configuration #1 chosen from 1 choice
[   23.399574] hub 1-0:1.0: USB hub found
[   23.399583] hub 1-0:1.0: 2 ports detected
[   23.500369] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   23.500385] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.500390] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.500424] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.500456] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000fd00
[   23.500618] usb usb2: configuration #1 chosen from 1 choice
[   23.500656] hub 2-0:1.0: USB hub found
[   23.500664] hub 2-0:1.0: 2 ports detected
[   23.604018] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.604034] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.604039] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.604073] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.604104] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[   23.604258] usb usb3: configuration #1 chosen from 1 choice
[   23.604296] hub 3-0:1.0: USB hub found
[   23.604306] hub 3-0:1.0: 2 ports detected
[   23.707743] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 19
[   23.707758] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.707764] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.707798] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.707829] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000fb00
[   23.707991] usb usb4: configuration #1 chosen from 1 choice
[   23.708029] hub 4-0:1.0: USB hub found
[   23.708037] hub 4-0:1.0: 2 ports detected
[   23.739519] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   23.789737] SCSI subsystem initialized
[   23.811468] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 16
[   23.811486] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.811492] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.811524] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.815425] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   23.815435] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xfdfff000
[   23.828430] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   23.828436] e100: Copyright(c) 1999-2006 Intel Corporation
[   23.843219] libata version 3.00 loaded.
[   23.887093] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.887249] usb usb5: configuration #1 chosen from 1 choice
[   23.887287] hub 5-0:1.0: USB hub found
[   23.887297] hub 5-0:1.0: 8 ports detected
[   23.939299] Floppy drive(s): fd0 is 1.44M
[   23.959576] FDC 0 is a post-1991 82077
[   23.991049] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.042739] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[   24.050573] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.074217] e100: eth0: e100_probe: addr 0xfdefd000, irq 20, MAC addr 00:1a:92:c4:4c:85
[   24.074255] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   24.126857] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fdefe000-fdefe7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[   24.133825] ohci1394: fw-host1: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[   24.133911] ata_piix 0000:00:1f.1: version 2.12
[   24.133933] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   24.133980] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.134715] scsi0 : ata_piix
[   24.134791] scsi1 : ata_piix
[   24.135181] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[   24.135184] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[   24.281970] usb 1-1: device not accepting address 2, error -71
[   24.454867] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-H652M, 0414, max UDMA/33
[   24.625281] ata1.00: configured for UDMA/33
[   24.625333] ata2: port disabled. ignoring.
[   24.626285] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H652M 0414 PQ: 0 ANSI: 5
[   24.626688] ahci 0000:00:1f.2: version 3.0
[   24.626717] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   25.183414] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   25.316199] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000137ed65]
[   25.398940] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[a30600000000e332]
[   25.626163] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[   25.626169] ahci 0000:00:1f.2: flags: 64bit ncq led clo 
[   25.626175] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   25.626437] scsi2 : ahci
[   25.626624] scsi3 : ahci
[   25.626774] scsi4 : ahci
[   25.626921] scsi5 : ahci
[   25.627044] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 223
[   25.627049] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 223
[   25.627054] ata5: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 223
[   25.627058] ata6: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 223
[   25.644201] usb 1-1: configuration #1 chosen from 1 choice
[   25.885413] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   26.056439] usb 2-1: configuration #1 chosen from 1 choice
[   26.069348] usbcore: registered new interface driver libusual
[   26.075564] Initializing USB Mass Storage driver...
[   26.075650] scsi6 : SCSI emulation for USB Mass Storage devices
[   26.075741] usbcore: registered new interface driver usb-storage
[   26.075746] USB Mass Storage support registered.
[   26.075867] usb-storage: device found at 2
[   26.075870] usb-storage: waiting for device to settle before scanning
[   26.100798] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.150699] ata3.00: ATA-7: ST3160811AS, 3.AAE, max UDMA/133
[   26.150706] ata3.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   26.208843] ata3.00: configured for UDMA/133
[   26.519603] ata4: SATA link down (SStatus 0 SControl 300)
[   26.994264] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.994986] ata5.00: ATA-7: ST3160812AS, 3.AHL, max UDMA/100
[   26.994990] ata5.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   26.995899] ata5.00: configured for UDMA/100
[   27.309366] ata6: SATA link down (SStatus 0 SControl 300)
[   27.309508] scsi 2:0:0:0: Direct-Access     ATA      ST3160811AS      3.AA PQ: 0 ANSI: 5
[   27.309689] scsi 4:0:0:0: Direct-Access     ATA      ST3160812AS      3.AH PQ: 0 ANSI: 5
[   27.321723] Driver 'sd' needs updating - please use bus_type methods
[   27.321830] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   27.321850] sd 2:0:0:0: [sda] Write Protect is off
[   27.321854] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.321887] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.321961] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   27.321982] sd 2:0:0:0: [sda] Write Protect is off
[   27.321986] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.322016] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.322022]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   27.336350] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   27.336355] Uniform CD-ROM driver Revision: 3.20
[   27.336431] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   27.344795]  sda1 sda2 < sda5 >
[   27.371985] sd 2:0:0:0: [sda] Attached SCSI disk
[   27.372065] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   27.372086] sd 4:0:0:0: [sdb] Write Protect is off
[   27.372090] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.372120] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.372186] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   27.372204] sd 4:0:0:0: [sdb] Write Protect is off
[   27.372208] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.372237] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.372243]  sdb: sdb1 sdb2
[   27.390889] sd 4:0:0:0: [sdb] Attached SCSI disk
[   27.395775] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   27.395810] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   27.395841] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   27.723368] Attempting manual resume
[   27.723373] swsusp: Resume From Partition 8:5
[   27.723374] PM: Checking swsusp image.
[   27.723523] PM: Resume from disk failed.
[   27.759611] kjournald starting.  Commit interval 5 seconds
[   27.759620] EXT3-fs: mounted filesystem with ordered data mode.
[   31.058726] usb-storage: device scan complete
[   31.058831] scsi 6:0:0:0: Direct-Access     Datafab  MDCFE-B USB CF R 0012 PQ: 0 ANSI: 0 CCS
[   31.058881] scsi 6:0:0:1: Direct-Access     Datafab  MDCFE-B USB CF R 0012 PQ: 0 ANSI: 0 CCS
[   31.254133] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   35.371616] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.419393] Linux agpgart interface v0.102
[   35.618872] agpgart: Detected an Intel 945G Chipset.
[   35.620197] agpgart: Detected 7932K stolen memory.
[   35.635375] agpgart: AGP aperture is 256M @ 0xe0000000
[   35.969221] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   36.068653] input: Power Button (FF) as /devices/virtual/input/input4
[   36.136336] ACPI: Power Button (FF) [PWRF]
[   36.136450] input: Power Button (CM) as /devices/virtual/input/input5
[   36.192143] ACPI: Power Button (CM) [PWRB]
[   37.788672] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 19
[   37.788695] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   37.821306] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   38.066145] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x000D
[   38.066173] usbcore: registered new interface driver usblp
[   39.033867] lp: driver loaded but no devices found
[   39.185213] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   39.740766] EXT3 FS on sda1, internal journal
[   40.922108] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.336919] No dock devices found.
[   42.484778] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   42.484787] apm: disabled - APM is not SMP safe.
[   42.647598] ppdev: user-space parallel port driver
[   42.880592] audit(1222607022.988:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5042 profile="/usr/sbin/cupsd" namespace="default"
[   44.205423] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   44.471449] Bluetooth: Core ver 2.11
[   44.471949] NET: Registered protocol family 31
[   44.471957] Bluetooth: HCI device and connection manager initialized
[   44.471965] Bluetooth: HCI socket layer initialized
[   44.562722] Bluetooth: L2CAP ver 2.9
[   44.562730] Bluetooth: L2CAP socket layer initialized
[   44.719025] Bluetooth: RFCOMM socket layer initialized
[   44.719046] Bluetooth: RFCOMM TTY layer initialized
[   44.719050] Bluetooth: RFCOMM ver 1.8
[   47.534627] NET: Registered protocol family 17
[   47.627134] [drm] Initialized drm 1.1.0 20060810
[   47.630368] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[   47.630381] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   47.630463] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   50.343116] NET: Registered protocol family 10
[   50.343587] lo: Disabled Privacy Extensions
[   60.482987] eth0: no IPv6 routers present
[   61.428307] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   71.659202] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   87.873086] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   88.132342] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   98.363259] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   98.512166] sd 6:0:0:0: Device offlined - not ready after error recovery
[   98.512200] sd 6:0:0:0: rejecting I/O to offline device
[   98.512215] sd 6:0:0:0: rejecting I/O to offline device
[   98.512227] sd 6:0:0:0: rejecting I/O to offline device
[   98.512236] sd 6:0:0:0: [sdc] READ CAPACITY failed
[   98.512272] sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   98.512281] sd 6:0:0:0: [sdc] Sense not available.
[   98.512291] sd 6:0:0:0: rejecting I/O to offline device
[   98.512330] sd 6:0:0:0: [sdc] Write Protect is off
[   98.512336] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   98.512342] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   98.512442] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   98.512520] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  128.538432] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[  138.780297] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[  154.998151] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[  155.257416] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[  165.488317] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[  165.637047] sd 6:0:0:1: Device offlined - not ready after error recovery
[  165.637097] sd 6:0:0:1: rejecting I/O to offline device
[  165.637113] sd 6:0:0:1: rejecting I/O to offline device
[  165.637125] sd 6:0:0:1: rejecting I/O to offline device
[  165.637134] sd 6:0:0:1: [sdd] READ CAPACITY failed
[  165.637140] sd 6:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  165.637150] sd 6:0:0:1: [sdd] Sense not available.
[  165.637190] sd 6:0:0:1: rejecting I/O to offline device
[  165.637199] sd 6:0:0:1: [sdd] Write Protect is off
[  165.637205] sd 6:0:0:1: [sdd] Mode Sense: 00 00 00 00
[  165.637211] sd 6:0:0:1: [sdd] Assuming drive cache: write through
[  165.637342] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[  165.637421] sd 6:0:0:1: Attached scsi generic sg4 type 0
[ 4389.079084] audit(1222611382.240:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6580 profile="/usr/sbin/cupsd" namespace="default"
[24247.724028] audit(1222631297.372:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=12219 profile="/usr/sbin/cupsd" namespace="default"
[24610.370233] audit(1222631661.048:5): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=12309 profile="/usr/sbin/cupsd" namespace="default"
[24652.691623] audit(1222631703.492:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=12334 profile="/usr/sbin/cupsd" namespace="default"
[26840.517393] audit(1222633897.540:7): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=12963 profile="/usr/sbin/cupsd" namespace="default"
[38062.115935] usb 5-5: new high speed USB device using ehci_hcd and address 4
[38062.251665] usb 5-5: configuration #1 chosen from 1 choice
[38062.252257] scsi7 : SCSI emulation for USB Mass Storage devices
[38062.252833] usb-storage: device found at 4
[38062.252840] usb-storage: waiting for device to settle before scanning
[38067.237468] usb-storage: device scan complete
[38067.238007] scsi 7:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[38068.947498] sd 7:0:0:0: [sde] 4028416 512-byte hardware sectors (2063 MB)
[38068.948501] sd 7:0:0:0: [sde] Write Protect is off
[38068.948507] sd 7:0:0:0: [sde] Mode Sense: 23 00 00 00
[38068.948536] sd 7:0:0:0: [sde] Assuming drive cache: write through
[38068.951359] sd 7:0:0:0: [sde] 4028416 512-byte hardware sectors (2063 MB)
[38068.952107] sd 7:0:0:0: [sde] Write Protect is off
[38068.952113] sd 7:0:0:0: [sde] Mode Sense: 23 00 00 00
[38068.952118] sd 7:0:0:0: [sde] Assuming drive cache: write through
[38068.952124]  sde: sde1
[38068.953328] sd 7:0:0:0: [sde] Attached SCSI removable disk
[38068.953397] sd 7:0:0:0: Attached scsi generic sg5 type 0
[38680.243178] usb 5-5: USB disconnect, address 4
[38688.857169] usb 5-5: new high speed USB device using ehci_hcd and address 5
[38688.991601] usb 5-5: configuration #1 chosen from 1 choice
[38688.992878] scsi8 : SCSI emulation for USB Mass Storage devices
[38688.993275] usb-storage: device found at 5
[38688.993281] usb-storage: waiting for device to settle before scanning
[38693.978791] usb-storage: device scan complete
[38693.979374] scsi 8:0:0:0: Direct-Access     SONY     WALKMAN          0100 PQ: 0 ANSI: 4
[38693.981890] sd 8:0:0:0: [sde] 949760 2048-byte hardware sectors (1945 MB)
[38693.987600] sd 8:0:0:0: [sde] Write Protect is off
[38693.987610] sd 8:0:0:0: [sde] Mode Sense: 3e 00 00 00
[38693.987615] sd 8:0:0:0: [sde] Assuming drive cache: write through
[38693.989980] sd 8:0:0:0: [sde] 949760 2048-byte hardware sectors (1945 MB)
[38693.990477] sd 8:0:0:0: [sde] Write Protect is off
[38693.990485] sd 8:0:0:0: [sde] Mode Sense: 3e 00 00 00
[38693.990489] sd 8:0:0:0: [sde] Assuming drive cache: write through
[38693.990496]  sde: sde1
[38693.991917] sd 8:0:0:0: [sde] Attached SCSI removable disk
[38693.992005] sd 8:0:0:0: Attached scsi generic sg5 type 0
[38706.758274] usb 5-5: USB disconnect, address 5
[73679.103947] usb 5-5: new high speed USB device using ehci_hcd and address 6
[73679.238327] usb 5-5: configuration #1 chosen from 1 choice
[73679.239741] scsi9 : SCSI emulation for USB Mass Storage devices
[73679.240141] usb-storage: device found at 6
[73679.240147] usb-storage: waiting for device to settle before scanning
[73684.225644] usb-storage: device scan complete
[73684.226143] scsi 9:0:0:0: Direct-Access     SONY     WALKMAN          0100 PQ: 0 ANSI: 4
[73684.227989] sd 9:0:0:0: [sde] 949760 2048-byte hardware sectors (1945 MB)
[73684.228741] sd 9:0:0:0: [sde] Write Protect is off
[73684.228749] sd 9:0:0:0: [sde] Mode Sense: 3e 00 00 00
[73684.228752] sd 9:0:0:0: [sde] Assuming drive cache: write through
[73684.231104] sd 9:0:0:0: [sde] 949760 2048-byte hardware sectors (1945 MB)
[73684.231852] sd 9:0:0:0: [sde] Write Protect is off
[73684.231860] sd 9:0:0:0: [sde] Mode Sense: 3e 00 00 00
[73684.231867] sd 9:0:0:0: [sde] Assuming drive cache: write through
[73684.231875]  sde: sde1
[73684.233908] sd 9:0:0:0: [sde] Attached SCSI removable disk
[73684.233991] sd 9:0:0:0: Attached scsi generic sg5 type 0
[73725.919662] usb 5-5: USB disconnect, address 6
[73744.087102] usb 5-5: new high speed USB device using ehci_hcd and address 7
[73744.221426] usb 5-5: configuration #1 chosen from 1 choice
[73744.222786] scsi10 : SCSI emulation for USB Mass Storage devices
[73744.223186] usb-storage: device found at 7
[73744.223194] usb-storage: waiting for device to settle before scanning
[73746.003397] usb 5-5: USB disconnect, address 7
tom@tom-desktop:~$ lsusb

---

### Post by Tom--d on 2008-09-29
Seems to detect it alright.

What happens when you put it in (wait a few seconds first) and does anything appear on the Desktop?

---

### Post by victorbrca on 2008-09-29
You can also check under the Computer folder. Mounts might be disabled on your desktop.


Vic.

---

### Post by telltommy on 2008-09-29
nothing happens when i plug it into the usb port. If I plug in flash media it shows.

---

### Post by victorbrca on 2008-09-29
Did you *"lsusb"* command return anything? Was it blank?

---

### Post by telltommy on 2008-09-29
here it is
tom@tom-desktop:~$ lsusb
Bus 005 Device 013: ID 054c:031b Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 07c4:a000 Datafab Systems, Inc. CompactFlash Card Reader
Bus 001 Device 001: ID 0000:0000  
tom@tom-desktop:~$

---

### Post by victorbrca on 2008-09-29
Looks like this device does not get mounted automatically.

If you are confident, take a look at these two links:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=866297](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=866297)
[http://www.secondbestblog.com/2008/08/sony-walkman-nwz-b105f-on-ubuntu.html](http://www.secondbestblog.com/2008/08/sony-walkman-nwz-b105f-on-ubuntu.html)


Otherwise try running these two commands with the device plugged in and paste the results:

```
df -h
sudo fdisk -l
```


Vic.

---

### Post by telltommy on 2008-09-29
result:
tom@tom-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  2.9G  135G   3% /
varrun                502M  104K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   76K  501M   1% /dev
devshm                502M   12K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      146G  2.9G  135G   3% /home/tom/.gvfs
tom@tom-desktop:~$ sudo fdisk -l

---

### Post by victorbrca on 2008-09-29
Try the sudo fdisk again. The last letter is a lower case "L" (as in LIMA).

```
sudo fdisk -l
```

Remember to type in your password when it asks you.


Vic.

---

### Post by telltommy on 2008-09-30
tom@tom-desktop:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f59bae8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa15cf37a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18533   148866291    7  HPFS/NTFS
/dev/sdb2           18534       19457     7422030    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sde: 1945 MB, 1945108480 bytes
212 heads, 56 sectors/track, 80 cylinders
Units = cylinders of 11872 * 2048 = 24313856 bytes
Disk identifier: 0xb6eda5aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          80     1899408    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 56) logical=(0, 1, 1)
tom@tom-desktop:~$

---

### Post by wilsong on 2008-09-30
Some MP3 players have different modes (i had one that had a slider switch on it) and when it was in one position it would charge, and it wouldnt mount or show on a PC when it was in that mode, then you would slide it to the other position, and then it was readable like a Flash Thumb Drive, and would show up as a hard drive style device.  Might be a long shot, but just a thought.

---

### Post by victorbrca on 2008-09-30
Try this...

1- Right click on your panel (same as taskbar from Windows), and select "Add to Panel"
2- Look for something called "Disk Mounter" or "Drive Mount" and add it
3- Insert the player and click on that new icon. It should display your player. Click on it and you should now be able to the player on your desktop.

---

### Post by telltommy on 2008-09-30
i now have mount disk on the task bar with three disk icons. one states floppy drive not mounted, one states Compaq not mounted and last states Recovery not mounted. Still no sign of the Sony player.

---

### Post by victorbrca on 2008-09-30
Looks like that might not work. What I'm going to show you now is the manual way. Make sure you enter the commands in the same sequence:

Create a mount folder (only the first time):
```
sudo mkdir /media/sony
```


Install pmount:
```
sudo apt-get install pmount
```


Insert the device and manually mount the player:
```
pmount /dev/sde1 /media/sony
```


Before removing the device make sure you unmount it:
```
pumount /media/sony
```


Vic.

---

### Post by telltommy on 2008-09-30
tom@tom-desktop:~$ sudo mkdir /media/sony
mkdir: cannot create directory `/media/sony': File exists
tom@tom-desktop:~$ sudo apt-get install pmount
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pmount is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tom@tom-desktop:~$ pmount /dev/sde1 /media/sony
Error: device /dev/sde1 does not exist
tom@tom-desktop:~$ pumount /media/sony
Error: device /dev/sde1 does not exist
tom@tom-desktop:~$

---

### Post by victorbrca on 2008-09-30
Was the device plugged in? Can you run these two commands again?

```
sudo fdisk -l
df -h
```


Vic.

---

### Post by telltommy on 2008-10-01
tom@tom-desktop:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f59bae8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa15cf37a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18533   148866291    7  HPFS/NTFS
/dev/sdb2           18534       19457     7422030    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sdf: 1945 MB, 1945108480 bytes
212 heads, 56 sectors/track, 80 cylinders
Units = cylinders of 11872 * 2048 = 24313856 bytes
Disk identifier: 0xb6eda5aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          80     1899408    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 56) logical=(0, 1, 1)
tom@tom-desktop:~$ 

Sony icon is on the desktop but it doesn't work.

---

### Post by sub2007 on 2008-10-01
If you get an icon on the Desktop, can you right click on it and choose "Mount Device"? That's what I have to do to mount my Sony player. Then to unmount it close all windows (that are related to the Walkman, so any Nautilus windows, terminal windows that you have been using to navigate the player files  etc) and choose "Unmount Device".

---

### Post by telltommy on 2008-10-01
i right click on the player and it shows it is mounted, but when i choose unmount i get this message.
Error org.freedesktop.DBus.Error.UnknownMethod

---

### Post by eddietours on 2008-10-01
hm l have the same sony mp it work off the bat just for the hell of it try with a live cd

---

### Post by telltommy on 2008-10-02
I thought of that too, but it doesn't work with the live cd. Also tried it on my other computer with only a fresh install of ubuntu and it will not work. Doesn't show the player at all.

---

### Post by victorbrca on 2008-10-02
Did you unplug that device from a Windows machine without properly removing it? I've had that problem on my BlackBerry once.

Try inserting your device and then run this code:

```
ls /dev/disk/by-label -lah
```


Vic.

---

### Post by telltommy on 2008-10-02
tried that but it still doesn't mount. I'm going to give up for now. I just realized i have a partition that is holding a recovery file for windows, this may be causing problems.

---

