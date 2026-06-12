---
title: "Ubuntu doesn't detect my ipod"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by gjoellee on 2008-07-26
Ubuntu doesn't detect my ipod nano 8gb. It did detect it before but now it doesn't, down anyone know whats going on and how to fix it?:confused:

---

### Post by ejpyle on 2008-07-26
> **gjoellee said:**
> Ubuntu doesn't detect my ipod nano 8gb. It did detect it before but now it doesn't, down anyone know whats going on and how to fix it?:confused:

which gen nano are you running?

what software r u using? r u using gtkpod?

---

### Post by gjoellee on 2008-07-27
I use Amarok to sync my music, and it is 5th generation

---

### Post by frank002 on 2008-07-27
There is a program called gtkpod that might help. You can find it in Synaptic.

---

### Post by gjoellee on 2008-07-27
I installed it, but i didn't help much. The problem is that Ubuntu doesn't detect my ipod anymore. I is more like HAL detection or something like that

---

### Post by durand on 2008-07-27
Plug it in and post the output of dmesg and lsusb, from the terminal (Applications > Accessories > Terminal)

EDIT: Read comment #7 on this thread: [http://ubuntuforums.org/showthread.php?t=862930](http://ubuntuforums.org/showthread.php?t=862930)

---

### Post by gjoellee on 2008-07-27
DMESG:
[   14.152328]   PREFETCH window: e3600000-f35fffff
[   14.152339] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   14.152353] NET: Registered protocol family 2
[   14.189864] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   14.190092] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   14.190274] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   14.190451] TCP: Hash tables configured (established 16384 bind 16384)
[   14.190453] TCP reno registered
[   14.201891] checking if image is initramfs... it is
[   14.653343] Switched to high resolution mode on CPU 0
[   14.772531] Freeing initrd memory: 7322k freed
[   14.773265] audit: initializing netlink socket (disabled)
[   14.773281] audit(1217170788.160:1): initialized
[   14.775300] VFS: Disk quotas dquot_6.5.1
[   14.775373] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.775514] io scheduler noop registered
[   14.775517] io scheduler anticipatory registered
[   14.775519] io scheduler deadline registered
[   14.775529] io scheduler cfq registered (default)
[   17.106761] 0000:00:02.0 OHCI: BIOS handoff failed (BIOS bug ?) 000007b4
[   17.106827] Boot video device is 0000:01:00.0
[   17.107106] isapnp: Scanning for PnP cards...
[   17.461246] isapnp: No Plug & Play device found
[   17.491101] Real Time Clock Driver v1.12ac
[   17.491211] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.491346] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.492026] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.492844] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.492924] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.493031] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[   17.494954] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.494959] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.498606] mice: PS/2 mouse device common for all mice
[   17.498728] EISA: Probing bus 0 at eisa.0
[   17.498749] Cannot allocate resource for EISA slot 4
[   17.498767] EISA: Detected 0 cards.
[   17.498771] cpuidle: using governor ladder
[   17.498772] cpuidle: using governor menu
[   17.498916] NET: Registered protocol family 1
[   17.498944] Using IPI No-Shortcut mode
[   17.498978] registered taskstats version 1
[   17.499079]   Magic number: 0:961:991
[   17.499090]   hash matches device ttyd4
[   17.499244] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.499246] EDD information not available.
[   17.499641] Freeing unused kernel memory: 368k freed
[   17.526352] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.588940] vesafb: framebuffer at 0xe8000000, mapped to 0xe0880000, using 600k, total 131072k
[   17.588946] vesafb: mode is 640x480x8, linelength=640, pages=10
[   17.588948] vesafb: protected mode interface info at c000:f160
[   17.588951] vesafb: pmi: set display start = c00cf196, set palette = c00cf200
[   17.588953] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[   17.588962] vesafb: scrolling: redraw
[   17.588967] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[   17.589089] Console: switching to colour frame buffer device 80x30
[   17.596076] fb0: VESA VGA frame buffer device
[   18.720401] fuse init (API version 7.9)
[   19.376958] usbcore: registered new interface driver usbfs
[   19.376984] usbcore: registered new interface driver hub
[   19.388467] usbcore: registered new device driver usb
[   19.398512] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   19.398811] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 22
[   19.398819] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LKLN] -> GSI 22 (level, high) -> IRQ 16
[   19.398827] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.412645] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.459377] SCSI subsystem initialized
[   19.508327] libata version 3.00 loaded.
[   19.609243] Floppy drive(s): fd0 is 1.44M
[   19.632026] FDC 0 is a post-1991 82077
[   19.916265] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:0c:6e:e2:1f:5e
[   19.916271] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[   19.916680] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[   19.916689] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, high) -> IRQ 17
[   19.916703] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.916706] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   19.916991] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   19.917010] ohci_hcd 0000:00:02.0: irq 17, io mem 0xfe900000
[   19.973942] usb usb1: configuration #1 chosen from 1 choice
[   19.973969] hub 1-0:1.0: USB hub found
[   19.973978] hub 1-0:1.0: 3 ports detected
[   20.076111] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[   20.076121] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 20 (level, high) -> IRQ 18
[   20.076137] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   20.076140] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   20.076171] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   20.076189] ohci_hcd 0000:00:02.1: irq 18, io mem 0xfea00000
[   20.133733] usb usb2: configuration #1 chosen from 1 choice
[   20.133758] hub 2-0:1.0: USB hub found
[   20.133767] hub 2-0:1.0: 3 ports detected
[   20.236156] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   20.236161] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 16
[   20.236173] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   20.236176] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   20.236217] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   20.236251] ehci_hcd 0000:00:02.2: debug port 1
[   20.236256] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   20.236271] ehci_hcd 0000:00:02.2: irq 16, io mem 0xfeb00000
[   20.379385] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   20.391368] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.391493] usb usb3: configuration #1 chosen from 1 choice
[   20.391517] hub 3-0:1.0: USB hub found
[   20.391524] hub 3-0:1.0: 6 ports detected
[   20.498726] ACPI: PCI Interrupt Link [LFWR] enabled at IRQ 21
[   20.498732] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LFWR] -> GSI 21 (level, high) -> IRQ 17
[   20.498740] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   20.550473] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fe500000-fe5007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.575246] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   20.579111] pata_amd 0000:00:09.0: version 0.3.10
[   20.579196] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   20.580106] scsi0 : pata_amd
[   20.580400] scsi1 : pata_amd
[   20.581969] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   20.581973] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   20.744439] ata1.00: ATA-6: WDC WD1200BB-00DWA0, 15.05R15, max UDMA/100
[   20.744444] ata1.00: 234441648 sectors, multi 16: LBA48 
[   20.760325] ata1.00: configured for UDMA/100
[   21.162571] usb 1-3: new full speed USB device using ohci_hcd and address 3
[   21.242859] ata2.00: ATAPI: IDE-DVD ROM 16x, HD09, max UDMA/33
[   21.242876] ata2.01: ATAPI: HP      DVD Writer 300c, 7H29, max UDMA/33
[   21.378308] usb 1-3: configuration #1 chosen from 1 choice
[   21.394025] usbcore: registered new interface driver libusual
[   21.400449] Initializing USB Mass Storage driver...
[   21.401155] scsi2 : SCSI emulation for USB Mass Storage devices
[   21.401722] usbcore: registered new interface driver usb-storage
[   21.401726] USB Mass Storage support registered.
[   21.401820] usb-storage: device found at 3
[   21.401822] usb-storage: waiting for device to settle before scanning
[   21.414613] ata2.00: configured for UDMA/33
[   21.680449] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[   21.686553] ata2.01: configured for UDMA/33
[   21.686678] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BB-00D 15.0 PQ: 0 ANSI: 5
[   21.687392] scsi 1:0:0:0: CD-ROM            IDE-DVD  ROM 16x          HD09 PQ: 0 ANSI: 5
[   21.689919] scsi 1:0:1:0: CD-ROM            HP       DVD Writer 300c  7H29 PQ: 0 ANSI: 5
[   21.698491] Driver 'sd' needs updating - please use bus_type methods
[   21.698599] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.698613] sd 0:0:0:0: [sda] Write Protect is off
[   21.698616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.698634] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.698684] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.698695] sd 0:0:0:0: [sda] Write Protect is off
[   21.698697] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.698713] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.698717]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.722150]  sda1 sda2 < sda5 >
[   21.741920] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.747888] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.747908] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.747926] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   21.750480] sr0: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[   21.750486] Uniform CD-ROM driver Revision: 3.20
[   21.750541] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.763366] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   21.763418] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   21.949892] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[003dabe700e01800]
[   22.018382] Attempting manual resume
[   22.018386] swsusp: Resume From Partition 8:5
[   22.018388] PM: Checking swsusp image.
[   22.018571] PM: Resume from disk failed.
[   22.031888] EXT3-fs: INFO: recovery required on readonly filesystem.
[   22.031893] EXT3-fs: write access will be enabled during recovery.
[   22.669622] kjournald starting.  Commit interval 5 seconds
[   22.669640] EXT3-fs: sda1: orphan cleanup on readonly fs
[   22.669646] ext3_orphan_cleanup: deleting unreferenced inode 1286169
[   22.669672] EXT3-fs: sda1: 1 orphan inode deleted
[   22.669674] EXT3-fs: recovery complete.
[   22.803344] EXT3-fs: mounted filesystem with ordered data mode.
[   26.394491] usb-storage: device scan complete
[   26.401466] scsi 2:0:0:0: Direct-Access     Generic  CF Reader        1.01 PQ: 0 ANSI: 0
[   26.408491] scsi 2:0:0:1: Direct-Access     Generic  SM/SD/MS Reader  1.00 PQ: 0 ANSI: 0
[   26.455439] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   26.455469] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   26.502359] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   26.502387] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   33.326049] Linux agpgart interface v0.102
[   33.434044] agpgart: Detected NVIDIA nForce2 chipset
[   33.438205] agpgart: AGP aperture is 64M @ 0xf4000000
[   33.633929] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4300
[   33.633963] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4340
[   33.906182] input: Power Button (FF) as /devices/virtual/input/input2
[   33.921410] ACPI: Power Button (FF) [PWRF]
[   33.921548] input: Power Button (CM) as /devices/virtual/input/input3
[   33.933387] ACPI: Power Button (CM) [PWRB]
[   35.719521] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.747072] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.847792] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   36.824146] nvidia: module license 'NVIDIA' taints kernel.
[   36.991206] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   37.405919] parport_pc 00:06: reported by Plug and Play ACPI
[   37.406005] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.614149] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[   37.614159] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 16 (level, high) -> IRQ 19
[   37.614581] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   37.645098] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[   37.645109] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKD] -> GSI 19 (level, high) -> IRQ 20
[   37.650307] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 [Unknown]
[   39.574481] lp0: using parport0 (interrupt-driven).
[   39.656178] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   39.661828] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   39.662293] EXT3 FS on sda1, internal journal
[   41.404078] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.965051] No dock devices found.
[   43.263941] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.263948] apm: overridden by ACPI.
[   43.971900] ppdev: user-space parallel port driver
[   44.140619] audit(1217170818.711:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5075 profile="/usr/sbin/cupsd" namespace="default"
[   45.841538] Bluetooth: Core ver 2.11
[   45.842286] NET: Registered protocol family 31
[   45.842291] Bluetooth: HCI device and connection manager initialized
[   45.842296] Bluetooth: HCI socket layer initialized
[   45.885074] Bluetooth: L2CAP ver 2.9
[   45.885080] Bluetooth: L2CAP socket layer initialized
[   45.999277] Bluetooth: RFCOMM socket layer initialized
[   45.999297] Bluetooth: RFCOMM TTY layer initialized
[   45.999299] Bluetooth: RFCOMM ver 1.8
[   46.815562] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   46.815577] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   46.815628] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   49.914341] NET: Registered protocol family 17
[   51.696318] NET: Registered protocol family 10
[   51.696529] lo: Disabled Privacy Extensions
[   62.595767] eth0: no IPv6 routers present
[ 1379.651136] usb 3-6: new high speed USB device using ehci_hcd and address 3
[ 1379.784410] usb 3-6: configuration #1 chosen from 2 choices
[ 1379.805399] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1379.805647] usb-storage: device found at 3
[ 1379.805650] usb-storage: waiting for device to settle before scanning
[ 1384.797950] usb-storage: device scan complete
[ 1384.813168] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1384.835499] sd 3:0:0:0: [sdd] Spinning up disk.....................................................................................................not responding...
[ 1677.728399] sd 3:0:0:0: [sdd] READ CAPACITY failed
[ 1677.728407] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1677.728411] sd 3:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 1677.728414] sd 3:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 1677.729380] sd 3:0:0:0: [sdd] Write Protect is off
[ 1677.729384] sd 3:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 1677.729387] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[ 1677.729451] sd 3:0:0:0: [sdd] Attached SCSI removable disk
[ 1677.729491] sd 3:0:0:0: Attached scsi generic sg5 type 0
[ 1677.868968] sd 3:0:0:0: [sdd] Spinning up disk.....................................................................................................not responding...
[ 1970.869899] sd 3:0:0:0: [sdd] READ CAPACITY failed
[ 1970.869907] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1970.869911] sd 3:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 1970.869915] sd 3:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 1970.870876] sd 3:0:0:0: [sdd] Write Protect is off
[ 1970.870880] sd 3:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 1970.870882] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[ 1978.930948] sd 3:0:0:0: [sdd] Spinning up disk.....................................................................................................not responding...
[ 2271.907656] sd 3:0:0:0: [sdd] READ CAPACITY failed
[ 2271.907664] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2271.907668] sd 3:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 2271.907672] sd 3:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 2271.908634] sd 3:0:0:0: [sdd] Write Protect is off
[ 2271.908638] sd 3:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 2271.908641] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[ 5196.275501] usb 3-6: USB disconnect, address 3
[ 5200.395953] usb 3-6: new high speed USB device using ehci_hcd and address 4
[ 5200.529208] usb 3-6: configuration #1 chosen from 2 choices
[ 5200.563792] scsi4 : SCSI emulation for USB Mass Storage devices
[ 5200.564635] usb-storage: device found at 4
[ 5200.564639] usb-storage: waiting for device to settle before scanning
[ 5202.985919] usb 3-6: USB disconnect, address 4
[ 5206.241914] usb 3-6: new high speed USB device using ehci_hcd and address 5
[ 5206.375178] usb 3-6: configuration #1 chosen from 2 choices
[ 5206.404831] scsi5 : SCSI emulation for USB Mass Storage devices
[ 5206.414086] usb-storage: device found at 5
[ 5206.414092] usb-storage: waiting for device to settle before scanning
[ 5207.005136] usb 3-6: USB disconnect, address 5
[ 5210.089941] usb 3-6: new high speed USB device using ehci_hcd and address 6
[ 5210.223177] usb 3-6: configuration #1 chosen from 2 choices
[ 5210.257778] scsi6 : SCSI emulation for USB Mass Storage devices
[ 5210.258617] usb-storage: device found at 6
[ 5210.258621] usb-storage: waiting for device to settle before scanning
[ 5215.257021] usb-storage: device scan complete
[ 5215.272832] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5215.305637] sd 6:0:0:0: [sdd] Spinning up disk......................................................................................................not responding...
[ 5509.117945] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 5509.117953] sd 6:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5509.117957] sd 6:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 5509.117960] sd 6:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 5509.118687] sd 6:0:0:0: [sdd] Write Protect is off
[ 5509.118691] sd 6:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 5509.118693] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 5509.118758] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[ 5509.118804] sd 6:0:0:0: Attached scsi generic sg5 type 0
[ 5509.167876] sd 6:0:0:0: [sdd] Spinning up disk......................................................................................................not responding...
[ 5802.928634] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 5802.928642] sd 6:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 5802.928646] sd 6:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 5802.928650] sd 6:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 5802.929615] sd 6:0:0:0: [sdd] Write Protect is off
[ 5802.929619] sd 6:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 5802.929621] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 5810.989684] sd 6:0:0:0: [sdd] Spinning up disk......................................................................................................not responding...
[ 6104.759058] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 6104.759065] sd 6:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6104.759069] sd 6:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 6104.759073] sd 6:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 6104.760287] sd 6:0:0:0: [sdd] Write Protect is off
[ 6104.760290] sd 6:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 6104.760293] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 6507.475984] usb 3-6: USB disconnect, address 6
[ 6566.648497] usb 3-6: new high speed USB device using ehci_hcd and address 7
[ 6566.781684] usb 3-6: configuration #1 chosen from 2 choices
[ 6566.816328] scsi7 : SCSI emulation for USB Mass Storage devices
[ 6566.817743] usb-storage: device found at 7
[ 6566.817747] usb-storage: waiting for device to settle before scanning
[ 6571.811338] usb-storage: device scan complete
[ 6571.826678] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 6571.856125] sd 7:0:0:0: [sdd] Spinning up disk...<6>usb 3-6: USB disconnect, address 7
[ 6574.584286] .ready
[ 6574.584403] sd 7:0:0:0: [sdd] READ CAPACITY failed
[ 6574.584405] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6574.584410] sd 7:0:0:0: [sdd] Sense not available.
[ 6574.584420] sd 7:0:0:0: [sdd] Write Protect is off
[ 6574.584423] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
[ 6574.584425] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 6574.584491] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[ 6574.584534] sd 7:0:0:0: Attached scsi generic sg5 type 0
[ 6575.886942] usb 3-6: new high speed USB device using ehci_hcd and address 8
[ 6576.020078] usb 3-6: configuration #1 chosen from 2 choices
[ 6576.054785] scsi8 : SCSI emulation for USB Mass Storage devices
[ 6576.055631] usb-storage: device found at 8
[ 6576.055635] usb-storage: waiting for device to settle before scanning
[ 6581.049730] usb-storage: device scan complete
[ 6586.655823] usb 3-6: reset high speed USB device using ehci_hcd and address 8
[ 6586.835646] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 6586.864452] sd 8:0:0:0: [sdd] Spinning up disk.....................................................................................................not responding...
[ 6879.851620] sd 8:0:0:0: [sdd] READ CAPACITY failed
[ 6879.851628] sd 8:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6879.851633] sd 8:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 6879.851636] sd 8:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 6879.852597] sd 8:0:0:0: [sdd] Write Protect is off
[ 6879.852601] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 6879.852603] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 6879.852668] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[ 6879.852713] sd 8:0:0:0: Attached scsi generic sg5 type 0
[ 6879.906034] sd 8:0:0:0: [sdd] Spinning up disk.....................................................................................................not responding...
[ 7172.839996] sd 8:0:0:0: [sdd] READ CAPACITY failed
[ 7172.840004] sd 8:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 7172.840008] sd 8:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 7172.840012] sd 8:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 7172.840973] sd 8:0:0:0: [sdd] Write Protect is off
[ 7172.840977] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 7172.840980] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 7180.899923] sd 8:0:0:0: [sdd] Spinning up disk.....................................................................................................not responding...
[ 7473.789529] sd 8:0:0:0: [sdd] READ CAPACITY failed
[ 7473.789537] sd 8:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 7473.789542] sd 8:0:0:0: [sdd] Sense Key : Not Ready [current] 
[ 7473.789545] sd 8:0:0:0: [sdd] Add. Sense: Logical unit is in process of becoming ready
[ 7473.790513] sd 8:0:0:0: [sdd] Write Protect is off
[ 7473.790517] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 7473.790520] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[10878.435245] ehci_hcd 0000:00:02.2: remove, state 1
[10878.435261] usb usb3: USB disconnect, address 1
[10878.435263] usb 3-6: USB disconnect, address 8
[10878.437727] ehci_hcd 0000:00:02.2: USB bus 3 deregistered
[10878.437774] ACPI: PCI interrupt for device 0000:00:02.2 disabled
[10878.495349] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 16
[10878.495380] PCI: Setting latency timer of device 0000:00:02.2 to 64
[10878.495383] ehci_hcd 0000:00:02.2: EHCI Host Controller
[10878.495417] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[10878.495450] ehci_hcd 0000:00:02.2: debug port 1
[10878.495455] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[10878.495463] ehci_hcd 0000:00:02.2: irq 16, io mem 0xfeb00000
[10878.495968] usb 1-3: USB disconnect, address 3
[10878.506319] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[10878.506460] usb usb3: configuration #1 chosen from 1 choice
[10878.506487] hub 3-0:1.0: USB hub found
[10878.506495] hub 3-0:1.0: 6 ports detected
[10879.233193] usb 3-6: new high speed USB device using ehci_hcd and address 3
[10879.366328] usb 3-6: configuration #1 chosen from 2 choices
[10879.401033] scsi9 : SCSI emulation for USB Mass Storage devices
[10879.401888] usb-storage: device found at 3
[10879.401892] usb-storage: waiting for device to settle before scanning
[10879.704718] usb 1-3: new full speed USB device using ohci_hcd and address 4
[10879.919875] usb 1-3: configuration #1 chosen from 1 choice
[10879.948466] scsi10 : SCSI emulation for USB Mass Storage devices
[10879.949149] usb-storage: device found at 4
[10879.949152] usb-storage: waiting for device to settle before scanning
[10884.395981] usb-storage: device scan complete
[10884.411077] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[10884.440521] sd 9:0:0:0: [sdb] Spinning up disk...<7>usb-storage: device scan complete
[10884.952008] scsi 10:0:0:0: Direct-Access     Generic  CF Reader        1.01 PQ: 0 ANSI: 0
[10884.958988] scsi 10:0:0:1: Direct-Access     Generic  SM/SD/MS Reader  1.00 PQ: 0 ANSI: 0
[10898.513343] usb 3-6: USB disconnect, address 3
[10899.516235] .ready
[10899.516342] sd 9:0:0:0: [sdb] READ CAPACITY failed
[10899.516344] sd 9:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[10899.516348] sd 9:0:0:0: [sdb] Sense not available.
[10899.516359] sd 9:0:0:0: [sdb] Write Protect is off
[10899.516361] sd 9:0:0:0: [sdb] Mode Sense: 00 00 00 00
[10899.516364] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[10899.516432] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[10899.516476] sd 9:0:0:0: Attached scsi generic sg3 type 0
[10899.564543] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[10899.564654] sd 10:0:0:0: Attached scsi generic sg3 type 0
[10899.613381] sd 10:0:0:1: [sdc] Attached SCSI removable disk
[10899.613429] sd 10:0:0:1: Attached scsi generic sg4 type 0
[10904.571017] usb 3-6: new high speed USB device using ehci_hcd and address 4
[10904.704294] usb 3-6: configuration #1 chosen from 2 choices
[10904.735017] scsi11 : SCSI emulation for USB Mass Storage devices
[10904.743155] usb-storage: device found at 4
[10904.743160] usb-storage: waiting for device to settle before scanning
[10909.737806] usb-storage: device scan complete
[10909.752781] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[10909.770620] sd 11:0:0:0: [sdd] Spinning up disk...

LSUSB
ubuntu@ubuntu-desktop:~$ lsusb
Bus 003 Device 004: ID 05ac:1262 Apple Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:9361 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by durand on 2008-07-27
Well, it's being detected, I only needed the last part of dmesg.

> [10904.571017] usb 3-6: new high speed USB device using ehci_hcd and address 4
[10904.704294] usb 3-6: configuration #1 chosen from 2 choices
[10904.735017] scsi11 : SCSI emulation for USB Mass Storage devices
[10904.743155] usb-storage: device found at 4
[10904.743160] usb-storage: waiting for device to settle before scanning
[10909.737806] usb-storage: device scan complete
[10909.752781] scsi 11:0:0:0: Direct-Access Apple iPod 1.62 PQ: 0 ANSI: 0
[10909.770620] sd 11:0:0:0: [sdd] Spinning up disk...

Are you sure it's not showing up in the Computer as  removable device? Did you read [http://ubuntuforums.org/showthread.php?t=862930](http://ubuntuforums.org/showthread.php?t=862930) ?

---

### Post by gjoellee on 2008-07-27
yes I did....however the computer shows no sign of the ipod getting connected and also the ipod does not seam to get connected either. I just think this is some kind of weird because it wasnt a problem before

---

### Post by AegisTalons on 2008-07-27
I'm getting the same thing. I have nano and it used to work, and now its not. Before, I was using exaile, and everytime I plug in my Ipod, rhythmbox fires up. Now when I plug it in, nothing. My computer doesn't even see it.

---

### Post by AegisTalons on 2008-07-27
Ok, so I think I might have just figured it out. Looks like it might be the ipod not being happy. Note: Running 8.04 64-bit. I use Rhythmbox and it just detected it.

Try hard resetting your ipod. Hold down both the Menu button and the center button (select/enter). Just keep holding it till a splash screen of the Apple logo pops up. Then just let it reset itself. Afterwards plug it in; hopefully it will be seen.

Hope that solves your problem. If not, let us know, and we'll try to help you out.

---

### Post by gjoellee on 2008-07-29
no, doesn't help....

i tried to charge up the ipod on my Windows, but Windows doesn't detect my ipod either so it is something weird going to in my ipod....if I have synced it in Ubuntu do i loose the warranties?

---

### Post by AegisTalons on 2008-07-29
Apple in general is very fickle. But I would argue that no matter what you do to the Ipod in software, as long as it can be reset to original state, you do not breach the warrenty. 

Considering the fact the neither Windows nor Ubuntu can see the Ipod, that it is something related to the ipod definately, whether it is a hardware or software problem is another question. 

Is the outside of the ipod physically ok? Did you drop it recently? Can you still listen to music on it?

Did the ipod also go into a reset? Try the reset again. (hold the menu and middle button). If that still doesn't work, you can try some ipod diagonistics. [http://www.methodshop.com/gadgets/ipodsupport/diagnosticmode/index.shtml]("http://www.methodshop.com/gadgets/ipodsupport/diagnosticmode/index.shtml")

Let us know whats up.

---

### Post by gjoellee on 2008-07-29
the ipod seams to have fixed itself! I am very glad now!

---

