---
title: "Boot Problem, dmesg Analysis Enclosed"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by C64Threepwood on 2008-04-27
I installed Ubuntu 8.04 on two separate systems this weekend, and on the second system, I'm experiencing very slow boot times to the tune of 4+ minutes.  Specs are:

[INDENT]Intel 3.2GHz Prescott
Asus P5W DH Deluxe
2GB Crucial Ballistix DDR2-800
Gigabyte 7600GT
Lite-On SOHD-167T IDE (upgraded firmware)
Seagate 80GB Barracuda 7200.9 SATA[/INDENT]

Partitions are configured as follows:
[INDENT]60GB (XP)
19GB (Ubuntu)
1GB (swap)[/INDENT]

I've searched through other threads regarding slow boot times and, as a result, have:

[INDENT]Updated optical drive's firmware
Deleted splash screen from startup
Changed *ro quiet splash* to *ro lapic pci=routeirq*[/INDENT]

Here are the contents of dmesg:
```
[   40.982092] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   40.982235] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  D0, should be C7 [20070126]
[   40.982245] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.982280] pnp: PnP ACPI init
[   40.982288] ACPI: bus type pnp registered
[   40.985777] pnp: PnP ACPI: found 14 devices
[   40.985779] ACPI: ACPI bus type pnp unregistered
[   40.986067] PCI: Using ACPI for IRQ routing
[   40.986070] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   40.999242] NET: Registered protocol family 8
[   40.999244] NET: Registered protocol family 20
[   40.999282] PCI-GART: No AMD northbridge found.
[   40.999287] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   40.999292] hpet0: 3 64-bit timers, 14318180 Hz
[   41.000327] AppArmor: AppArmor Filesystem Enabled
[   41.003196] Time: tsc clocksource has been installed.
[   41.003207] Switched to high resolution mode on CPU 0
[   41.006316] Switched to high resolution mode on CPU 1
[   41.011185] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   41.011194] system 00:07: ioport range 0x290-0x297 has been reserved
[   41.011200] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   41.011202] system 00:08: ioport range 0x800-0x87f has been reserved
[   41.011205] system 00:08: ioport range 0x400-0x41f has been reserved
[   41.011207] system 00:08: ioport range 0x480-0x4bf has been reserved
[   41.011209] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   41.011212] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   41.011214] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   41.011216] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   41.011219] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   41.011225] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   41.011227] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   41.011233] system 00:0c: iomem range 0xf0000000-0xf3ffffff has been reserved
[   41.011238] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   41.011241] system 00:0d: iomem range 0xc0000-0xdffff has been reserved
[   41.011243] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   41.011245] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[   41.011247] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   41.011729] PCI: Bridge: 0000:00:01.0
[   41.011732]   IO window: c000-cfff
[   41.011736]   MEM window: faa00000-feafffff
[   41.011739]   PREFETCH window: cff00000-efefffff
[   41.011742] PCI: Bridge: 0000:00:1c.0
[   41.011743]   IO window: disabled.
[   41.011747]   MEM window: disabled.
[   41.011750]   PREFETCH window: cfe00000-cfefffff
[   41.011755] PCI: Bridge: 0000:00:1c.3
[   41.011757]   IO window: b000-bfff
[   41.011761]   MEM window: fa900000-fa9fffff
[   41.011764]   PREFETCH window: disabled.
[   41.011769] PCI: Bridge: 0000:00:1c.4
[   41.011771]   IO window: a000-afff
[   41.011775]   MEM window: fa800000-fa8fffff
[   41.011778]   PREFETCH window: disabled.
[   41.011783] PCI: Bridge: 0000:00:1e.0
[   41.011784]   IO window: disabled.
[   41.011788]   MEM window: fa700000-fa7fffff
[   41.011791]   PREFETCH window: disabled.
[   41.011807] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.011813] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   41.011830] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.011834] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   41.011852] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   41.011856] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   41.011873] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   41.011877] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   41.011887] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   41.011896] NET: Registered protocol family 2
[   41.047171] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   41.048025] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   41.049956] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   41.050497] TCP: Hash tables configured (established 262144 bind 65536)
[   41.050499] TCP reno registered
[   41.059190] checking if image is initramfs... it is
[   41.642543] Freeing initrd memory: 7507k freed
[   41.647440] audit: initializing netlink socket (disabled)
[   41.647457] audit(1209330803.244:1): initialized
[   41.649968] VFS: Disk quotas dquot_6.5.1
[   41.650048] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   41.650176] io scheduler noop registered
[   41.650179] io scheduler anticipatory registered
[   41.650181] io scheduler deadline registered
[   41.650301] io scheduler cfq registered (default)
[   41.651648] Boot video device is 0000:05:00.0
[   41.651807] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   41.651843] assign_interrupt_mode Found MSI capability
[   41.651873] Allocate Port Service[0000:00:01.0:pcie00]
[   41.651960] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   41.652000] assign_interrupt_mode Found MSI capability
[   41.652032] Allocate Port Service[0000:00:1c.0:pcie00]
[   41.652074] Allocate Port Service[0000:00:1c.0:pcie02]
[   41.652165] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   41.652204] assign_interrupt_mode Found MSI capability
[   41.652236] Allocate Port Service[0000:00:1c.3:pcie00]
[   41.652323] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   41.652362] assign_interrupt_mode Found MSI capability
[   41.652394] Allocate Port Service[0000:00:1c.4:pcie00]
[   41.684111] Real Time Clock Driver v1.12ac
[   41.684314] hpet_resources: 0xfed00000 is busy
[   41.684343] Linux agpgart interface v0.102
[   41.684345] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   41.684474] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.685126] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   41.686200] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   41.686275] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   41.686449] PNP: No PS/2 controller found. Probing ports directly.
[   41.689144] serio: i8042 KBD port at 0x60,0x64 irq 1
[   41.689150] serio: i8042 AUX port at 0x60,0x64 irq 12
[   41.701362] mice: PS/2 mouse device common for all mice
[   41.701405] cpuidle: using governor ladder
[   41.701407] cpuidle: using governor menu
[   41.701486] NET: Registered protocol family 1
[   41.701538] registered taskstats version 1
[   41.701637]   Magic number: 4:413:248
[   41.701654]   hash matches device ttyw4
[   41.701720] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   41.701723] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   41.701724] EDD information not available.
[   41.701731] Freeing unused kernel memory: 316k freed
[   42.905420] fuse init (API version 7.9)
[   42.923793] ACPI: Processor [CPU1] (supports 8 throttling states)
[   42.924254] ACPI: Processor [CPU2] (supports 8 throttling states)
[   42.924273] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   42.924285] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   43.387525] usbcore: registered new interface driver usbfs
[   43.387561] usbcore: registered new interface driver hub
[   43.388573] usbcore: registered new device driver usb
[   43.400577] USB Universal Host Controller Interface driver v3.0
[   43.400641] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   43.400655] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   43.400659] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   43.400920] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   43.400953] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e480
[   43.401129] usb usb1: configuration #1 chosen from 1 choice
[   43.401167] hub 1-0:1.0: USB hub found
[   43.401175] hub 1-0:1.0: 2 ports detected
[   43.504392] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   43.504406] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   43.504411] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   43.504440] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   43.504470] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e800
[   43.504611] usb usb2: configuration #1 chosen from 1 choice
[   43.504644] hub 2-0:1.0: USB hub found
[   43.504652] hub 2-0:1.0: 2 ports detected
[   43.513668] SCSI subsystem initialized
[   43.561855] Floppy drive(s): fd0 is 1.44M
[   43.564361] libata version 3.00 loaded.
[   43.586921] FDC 0 is a post-1991 82077
[   43.608084] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   43.608103] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   43.608108] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   43.608143] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   43.608177] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
[   43.608351] usb usb3: configuration #1 chosen from 1 choice
[   43.608391] hub 3-0:1.0: USB hub found
[   43.608401] hub 3-0:1.0: 2 ports detected
[   43.711790] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[   43.711806] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   43.711812] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   43.711849] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   43.711880] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000ec00
[   43.712051] usb usb4: configuration #1 chosen from 1 choice
[   43.712096] hub 4-0:1.0: USB hub found
[   43.712108] hub 4-0:1.0: 2 ports detected
[   43.743581] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   43.815537] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[   43.815567] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   43.816204] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   43.816212] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   43.816296] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   43.820206] ehci_hcd 0000:00:1d.7: debug port 1
[   43.820213] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   43.820222] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfebfbc00
[   43.835313] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.835436] usb usb5: configuration #1 chosen from 1 choice
[   43.835468] hub 5-0:1.0: USB hub found
[   43.835476] hub 5-0:1.0: 8 ports detected
[   43.866264] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fa7ff800-fa7fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   43.939312] ata_piix 0000:00:1f.1: version 2.12
[   43.939343] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[   43.939389] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   43.939723] scsi0 : ata_piix
[   43.939783] scsi1 : ata_piix
[   43.941037] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   43.941040] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   44.250598] ata1.00: ATAPI: LITE-ON DVD SOHD-167T, 9S1B, max UDMA/33
[   44.406089] ata1.00: configured for UDMA/33
[   44.572665] scsi 0:0:0:0: CD-ROM            LITE-ON  DVD SOHD-167T    9S1B PQ: 0 ANSI: 5
[   44.572737] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   44.724858] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23
[   44.724890] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   44.724932] scsi2 : ata_piix
[   44.725172] scsi3 : ata_piix
[   44.725204] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 23
[   44.725206] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 23
[   44.808603] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   44.921703] ata3.00: ATA-7: ST3808110AS, 2AAA, max UDMA/133
[   44.921706] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   44.941531] usb 5-7: configuration #1 chosen from 1 choice
[   44.942340] hub 5-7:1.0: USB hub found
[   44.942576] hub 5-7:1.0: 4 ports detected
[   44.988169] ata3.00: configured for UDMA/133
[   45.135778] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000ded331]
[   45.283282] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   45.590759] ata4.00: ATA-6: Config  Disk, RGL10364, max UDMA/133
[   45.590762] ata4.00: 640 sectors, multi 1: LBA 
[   45.590767] ata4.00: Drive reports diagnostics failure. This may indicate a drive
[   45.590769] ata4.00: fault or invalid emulation. Contact drive vendor for information.
[   45.590772] ata4.00: device is on DMA blacklist, disabling DMA
[   45.591133] ata4.00: configured for PIO4
[   45.591237] scsi 2:0:0:0: Direct-Access     ATA      ST3808110AS      2AAA PQ: 0 ANSI: 5
[   45.591724] scsi 3:0:0:0: Direct-Access     ATA      Config  Disk     RGL1 PQ: 0 ANSI: 5
[   45.642699] Driver 'sd' needs updating - please use bus_type methods
[   45.642827] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   45.642852] sd 2:0:0:0: [sda] Write Protect is off
[   45.642857] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   45.643014] usb 1-1: configuration #1 chosen from 1 choice
[   45.643050] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.643134] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   45.643153] sd 2:0:0:0: [sda] Write Protect is off
[   45.643157] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   45.643188] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.643194]  sda: sda1 sda2 sda3
[   45.659223] Driver 'sr' needs updating - please use bus_type methods
[   45.663376] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   45.663381] Uniform CD-ROM driver Revision: 3.20
[   45.663443] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   45.683696] sd 2:0:0:0: [sda] Attached SCSI disk
[   45.683792] sd 3:0:0:0: [sdb] 640 512-byte hardware sectors (0 MB)
[   45.683817] sd 3:0:0:0: [sdb] Write Protect is off
[   45.683822] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   45.683863] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   45.683941] sd 3:0:0:0: [sdb] 640 512-byte hardware sectors (0 MB)
[   45.683962] sd 3:0:0:0: [sdb] Write Protect is off
[   45.683965] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   45.684002] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   45.684008]  sdb:<6>usb 1-2: new full speed USB device using uhci_hcd and address 4
[   46.072792] usb 1-2: configuration #1 chosen from 1 choice
[   46.075727] hub 1-2:1.0: USB hub found
[   46.077701] hub 1-2:1.0: 3 ports detected
[   46.384519] usb 5-7.3: new high speed USB device using ehci_hcd and address 5
[   46.482463] usb 5-7.3: configuration #1 chosen from 1 choice
[   46.685038] usb 1-2.1: new full speed USB device using uhci_hcd and address 5
[   46.826741] usb 1-2.1: configuration #1 chosen from 1 choice
[   46.835663] usbcore: registered new interface driver hiddev
[   46.851837] input: Razer Razer 1600dpi Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   46.883365] input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi Mouse] on usb-0000:00:1d.0-1
[   46.885698] input: ORTEK USB Hub/Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.1/1-2.1:1.0/input/input2
[   46.894817] input,hidraw1: USB HID v1.00 Keyboard [ORTEK USB Hub/Keyboard] on usb-0000:00:1d.0-2.1
[   46.899516] input: ORTEK USB Hub/Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.1/1-2.1:1.1/input/input3
[   46.926722] input,hidraw2: USB HID v1.00 Device [ORTEK USB Hub/Keyboard] on usb-0000:00:1d.0-2.1
[   46.926744] usbcore: registered new interface driver usbhid
[   46.926750] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   75.602857] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   75.602867] ata4.00: cmd c4/00:08:00:00:00/00:00:00:00:00/e0 tag 0 pio 4096 in
[   75.602868]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   75.602871] ata4.00: status: { DRDY }
[   75.602880] ata4: soft resetting link
[   75.941619] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   75.941623] ata4.00: revalidation failed (errno=-5)
[   75.941625] ata4: failed to recover some devices, retrying in 5 secs
[   80.928018] ata4: soft resetting link
[   81.270744] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   81.270750] ata4.00: revalidation failed (errno=-5)
[   81.270755] ata4: failed to recover some devices, retrying in 5 secs
[   86.257172] ata4: soft resetting link
[   91.442730] ata4: port is slow to respond, please be patient (Status 0xd0)
[   96.249343] ata4: SRST failed (errno=-16)
[   96.249348] ata4: soft resetting link
[  101.430909] ata4: port is slow to respond, please be patient (Status 0xd0)
[  106.237526] ata4: SRST failed (errno=-16)
[  106.237531] ata4: soft resetting link
[  111.423085] ata4: port is slow to respond, please be patient (Status 0xd0)
[  141.144314] ata4: SRST failed (errno=-16)
[  141.144318] ata4: soft resetting link
[  146.158358] ata4: SRST failed (errno=-16)
[  146.158363] ata4: reset failed, giving up
[  146.158366] ata4.00: disabled
[  151.184349] ata4: port is slow to respond, please be patient (Status 0xd0)
[  156.154509] ata4: device not ready (errno=-16), forcing hardreset
[  156.154512] ata4: soft resetting link
[  161.336082] ata4: port is slow to respond, please be patient (Status 0xd0)
[  166.138703] ata4: SRST failed (errno=-16)
[  166.138707] ata4: soft resetting link
[  171.320282] ata4: port is slow to respond, please be patient (Status 0xd0)
[  176.122898] ata4: SRST failed (errno=-16)
[  176.122902] ata4: soft resetting link
[  181.304470] ata4: port is slow to respond, please be patient (Status 0xd0)
[  211.077557] ata4: SRST failed (errno=-16)
[  211.077562] ata4: soft resetting link
[  216.091593] ata4: SRST failed (errno=-16)
[  216.091598] ata4: reset failed, giving up
[  216.091611] ata4: EH complete
[  216.091629] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091633] end_request: I/O error, dev sdb, sector 0
[  216.091637] Buffer I/O error on device sdb, logical block 0
[  216.091672] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091676] end_request: I/O error, dev sdb, sector 0
[  216.091678] Buffer I/O error on device sdb, logical block 0
[  216.091699] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091702] end_request: I/O error, dev sdb, sector 0
[  216.091704] Buffer I/O error on device sdb, logical block 0
[  216.091722] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091725] end_request: I/O error, dev sdb, sector 0
[  216.091727] Buffer I/O error on device sdb, logical block 0
[  216.091744] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091747] end_request: I/O error, dev sdb, sector 0
[  216.091749] Buffer I/O error on device sdb, logical block 0
[  216.091757] ldm_validate_partition_table(): Disk read failed.
[  216.091770] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091773] end_request: I/O error, dev sdb, sector 0
[  216.091775] Buffer I/O error on device sdb, logical block 0
[  216.091792] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091795] end_request: I/O error, dev sdb, sector 0
[  216.091797] Buffer I/O error on device sdb, logical block 0
[  216.091814] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091817] end_request: I/O error, dev sdb, sector 0
[  216.091819] Buffer I/O error on device sdb, logical block 0
[  216.091835] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091839] end_request: I/O error, dev sdb, sector 0
[  216.091841] Buffer I/O error on device sdb, logical block 0
[  216.091849] Dev sdb: unable to read RDB block 0
[  216.091860] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091863] end_request: I/O error, dev sdb, sector 0
[  216.091865] Buffer I/O error on device sdb, logical block 0
[  216.091882] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091885] end_request: I/O error, dev sdb, sector 0
[  216.091906] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091909] end_request: I/O error, dev sdb, sector 24
[  216.091925] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091928] end_request: I/O error, dev sdb, sector 24
[  216.091945] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091948] end_request: I/O error, dev sdb, sector 0
[  216.091964] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.091968] end_request: I/O error, dev sdb, sector 0
[  216.091975]  unable to read partition table
[  216.092044] sd 3:0:0:0: [sdb] Attached SCSI disk
[  216.104952] sr 0:0:0:0: Attached scsi generic sg0 type 5
[  216.104976] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  216.104996] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  216.166412] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.166418] end_request: I/O error, dev sdb, sector 0
[  216.166444] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  216.166447] end_request: I/O error, dev sdb, sector 0
[  216.391851] Attempting manual resume
[  216.391855] swsusp: Resume From Partition 8:3
[  216.391857] PM: Checking swsusp image.
[  216.392028] PM: Resume from disk failed.
[  216.439925] kjournald starting.  Commit interval 5 seconds
[  216.439938] EXT3-fs: mounted filesystem with ordered data mode.
[  224.104549] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  224.104557] end_request: I/O error, dev sdb, sector 0
[  224.104561] printk: 10 messages suppressed.
[  224.104565] Buffer I/O error on device sdb, logical block 0
[  224.104602] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  224.104608] end_request: I/O error, dev sdb, sector 0
[  225.130595] EDAC MC: Ver: 2.1.0 Apr 10 2008
[  225.351456] input: PC Speaker as /devices/platform/pcspkr/input/input4
[  225.402456] EDAC i82975x: ECC disabled on both channels.
[  225.425782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  225.457706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  225.630474] intel_rng: FWH not detected
[  225.868490] iTCO_vendor_support: vendor-support=0
[  225.904996] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  225.905095] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[  225.905133] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  226.020192] input: Power Button (FF) as /devices/virtual/input/input5
[  226.035925] ACPI: Power Button (FF) [PWRF]
[  226.036050] input: Power Button (CM) as /devices/virtual/input/input6
[  226.067819] ACPI: Power Button (CM) [PWRB]
[  227.026745] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19
[  227.027379] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  227.384333] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  227.384352] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  227.385015] sky2 0000:03:00.0: v1.20 addr 0xfa9fc000 irq 19 Yukon-EC (0xb6) rev 2
[  227.386178] sky2 eth0: addr 00:18:f3:62:c8:bc
[  227.386217] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  227.386239] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  227.386886] sky2 0000:02:00.0: v1.20 addr 0xfa8fc000 irq 16 Yukon-EC (0xb6) rev 2
[  227.387679] sky2 eth1: addr 00:18:f3:62:bb:74
[  228.243217] phy0: Selected rate control algorithm 'simple'
[  228.372961] phy0: hwaddr 00:15:af:09:b6:87, rtl8187 V1 + rtl8225z2
[  228.372990] usbcore: registered new interface driver rtl8187
[  229.891501] loop: module loaded
[  229.924480] lp: driver loaded but no devices found
[  230.137148] Adding 1044216k swap on /dev/sda3.  Priority:-1 extents:1 across:1044216k
[  230.675372] EXT3 FS on sda2, internal journal
[  231.823658] ip_tables: (C) 2000-2006 Netfilter Core Team
[  232.240527] No dock devices found.
[  233.338457] ppdev: user-space parallel port driver
[  233.483375] audit(1209345396.663:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=10206 profile="/usr/sbin/cupsd" namespace="default"
[  234.436166] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  234.436177] end_request: I/O error, dev sdb, sector 0
[  234.436181] printk: 4 messages suppressed.
[  234.436185] Buffer I/O error on device sdb, logical block 0
[  234.436192] Buffer I/O error on device sdb, logical block 1
[  234.436222] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  234.436229] end_request: I/O error, dev sdb, sector 0
[  234.539966] Bluetooth: Core ver 2.11
[  234.540083] NET: Registered protocol family 31
[  234.540086] Bluetooth: HCI device and connection manager initialized
[  234.540091] Bluetooth: HCI socket layer initialized
[  234.580791] Bluetooth: L2CAP ver 2.9
[  234.580797] Bluetooth: L2CAP socket layer initialized
[  234.619386] Bluetooth: RFCOMM socket layer initialized
[  234.619400] Bluetooth: RFCOMM TTY layer initialized
[  234.619403] Bluetooth: RFCOMM ver 1.8
[  243.005622] sky2 eth1: enabling interface
[  243.071119] sky2 eth0: enabling interface
[  244.224409] NET: Registered protocol family 17
[  244.752566] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  252.069562] NET: Registered protocol family 10
[  252.069960] lo: Disabled Privacy Extensions
[  252.072309] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  252.073226] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  262.497744] eth0: no IPv6 routers present
ubuntu@dualboot:~$
```

Any/all help would be greatly appreciated.

---

### Post by C64Threepwood on 2008-04-27
Since posting, I've also tried to the following (to no avail):

[LIST]
[*]Unhooking optical and floppy drive
[*]adding *noprobe=ata4* to menu.lst
[/LIST]

---

### Post by C64Threepwood on 2008-04-27
W00t!  After nearly going cross-eyed from reading threads regarding slow boots and almost falling into a gDepression over failed Google search results, I was able to solve my own problem.  For anyone else that may be suffering similar symptoms, here's what I did:

[LIST=1]
[*]Enter BIOS
[*]Navigate to ***IDE Configuration*** under ***Main*** menu
[*]Change ***Standard IDE*** to ***ACHI*** under ***Configure SATA As***
[/LIST]See attached pics for a visual.  By applying the above, boot time was reduced from 4+ minutes (conservative estimate) to well under 1 minute. \\:D/

---

### Post by arch0njw on 2008-08-07
C64Threepwood: You're awesome!  This just worked for me too.  Thanks!  You should mark this thread as solved.

---

### Post by foundbobby on 2008-09-10
Oh wow. thanks for replying on how to fix. For me it was making sata mode from IDE -> "RAID" without actually creating a raid... seems to have worked.  Thanks the advice on changing SATA settings! you rock

---

