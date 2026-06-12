---
title: "Sudden Crash-- Anachronistic Cron Anacron?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by scathmandra on 2008-10-14
Running Ubuntu 8.04 on a Dell Inspiron 1501. I was watching a video when suddenly the screen went black and came back with something about Anachronistic Chron Anacron and boot things(I'm sorry, but I didn't manage to write down the message) and promptly stayed stuck there. Is this common? Is there something I can do to stop it?

---

### Post by sumguy231 on 2008-10-14
I'm not sure what caused the crash (the anacron message is probably a coincidence) but to help people on the forums find out you should post the results of typing the following in a terminal:
```
dmesg
```
and
```
cat /var/log/Xorg.0.log
```
That may contain helpful information about what went wrong.

---

### Post by scathmandra on 2008-10-14
Ah, okay. I didn't know that.

The result of dmesg was:
```

[   15.712429] pnp: PnP ACPI: found 10 devices
[   15.712432] ACPI: ACPI bus type pnp unregistered
[   15.712754] PCI: Using ACPI for IRQ routing
[   15.712757] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.712764] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   15.712767] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   15.730341] NET: Registered protocol family 8
[   15.730343] NET: Registered protocol family 20
[   15.730499] AppArmor: AppArmor Filesystem Enabled
[   15.750351] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.750355] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.750359] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.750370] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   15.750373] system 00:08: ioport range 0x220-0x22f has been reserved
[   15.750376] system 00:08: ioport range 0x40b-0x40b has been reserved
[   15.750380] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   15.750383] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   15.750386] system 00:08: ioport range 0x530-0x537 has been reserved
[   15.750389] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   15.750393] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   15.750396] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   15.750399] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   15.750402] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   15.750405] system 00:08: ioport range 0xcd0-0xcd3 has been reserved
[   15.750409] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   15.750412] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   15.750415] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   15.750418] system 00:08: ioport range 0x8000-0x805f has been reserved
[   15.750422] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   15.750425] system 00:08: ioport range 0x87f-0x87f has been reserved
[   15.750433] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   15.750437] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   15.750440] system 00:09: iomem range 0xc0004800-0xc0004bff has been reserved
[   15.750444] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   15.750448] system 00:09: iomem range 0x0-0xfff could not be reserved
[   15.750938] PCI: Bridge: 0000:00:01.0
[   15.750940]   IO window: 9000-9fff
[   15.750944]   MEM window: c0100000-c01fffff
[   15.750947]   PREFETCH window: c8000000-cfffffff
[   15.750950] PCI: Bridge: 0000:00:05.0
[   15.750951]   IO window: disabled.
[   15.750954]   MEM window: disabled.
[   15.750956]   PREFETCH window: disabled.
[   15.750959] PCI: Bridge: 0000:00:06.0
[   15.750960]   IO window: disabled.
[   15.750963]   MEM window: c0200000-c02fffff
[   15.750965]   PREFETCH window: disabled.
[   15.750969] PCI: Bridge: 0000:00:14.4
[   15.750971]   IO window: disabled.
[   15.750976]   MEM window: c0300000-c03fffff
[   15.750981]   PREFETCH window: disabled.
[   15.751004] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.751012] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   15.751077] NET: Registered protocol family 2
[   15.753799] Time: acpi_pm clocksource has been installed.
[   15.753806] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   15.753812] Could not switch to high resolution mode on CPU 0
[   15.754317] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   15.754322] Could not switch to high resolution mode on CPU 1
[   15.790360] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   15.790928] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   15.792224] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.792827] TCP: Hash tables configured (established 131072 bind 65536)
[   15.792832] TCP reno registered
[   15.806389] checking if image is initramfs... it is
[   16.253121] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
[   16.253623] Could not switch to high resolution mode on CPU 1
[   16.253136]  lapic is not functional.
[   16.253138] Could not switch to high resolution mode on CPU 0
[   16.514150] Freeing initrd memory: 7551k freed
[   16.519345] audit: initializing netlink socket (disabled)
[   16.519360] audit(1224034237.448:1): initialized
[   16.521622] VFS: Disk quotas dquot_6.5.1
[   16.521716] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.521868] io scheduler noop registered
[   16.521870] io scheduler anticipatory registered
[   16.521873] io scheduler deadline registered
[   16.521988] io scheduler cfq registered (default)
[   16.521996] PCI: MSI quirk detected. MSI deactivated.
[   16.523253] Boot video device is 0000:01:05.0
[   16.523468] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.523490] assign_interrupt_mode Found MSI capability
[   16.523493] Allocate Port Service[0000:00:05.0:pcie00]
[   16.523536] Allocate Port Service[0000:00:05.0:pcie02]
[   16.523598] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.523618] assign_interrupt_mode Found MSI capability
[   16.523621] Allocate Port Service[0000:00:06.0:pcie00]
[   16.523657] Allocate Port Service[0000:00:06.0:pcie02]
[   16.556472] Real Time Clock Driver v1.12ac
[   16.556579] Linux agpgart interface v0.102
[   16.556582] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.557811] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.557889] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.557999] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.561565] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.561576] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.577274] mice: PS/2 mouse device common for all mice
[   16.577329] cpuidle: using governor ladder
[   16.577331] cpuidle: using governor menu
[   16.577483] NET: Registered protocol family 1
[   16.577615] registered taskstats version 1
[   16.577758]   Magic number: 12:730:508
[   16.577878]   hash matches device 0000:00:01.0
[   16.577895] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.577899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.577901] EDD information not available.
[   16.577914] Freeing unused kernel memory: 320k freed
[   16.621129] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.869517] fuse init (API version 7.9)
[   17.920141] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.923575] ACPI: Thermal Zone [THRM] (55 C)
[   18.168018] SCSI subsystem initialized
[   18.237248] libata version 3.00 loaded.
[   18.268530] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   18.268546] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   18.287013] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   18.287025] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   18.287032] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   18.287040] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   18.301589] usbcore: registered new interface driver usbfs
[   18.301622] usbcore: registered new interface driver hub
[   18.326904] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   18.326509] ahci 0000:00:12.0: version 3.0
[   18.326548] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.326692] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   18.326699] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   18.326815] usbcore: registered new device driver usb
[   18.328701] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.329015] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   19.329021] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   19.330300] scsi0 : ahci
[   19.330730] scsi1 : ahci
[   19.330947] scsi2 : ahci
[   19.331148] scsi3 : ahci
[   19.331241] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 22
[   19.331246] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 22
[   19.331251] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 22
[   19.331256] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 22
[   19.804334] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.805684] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
[   19.805689] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   19.806685] ata1.00: configured for UDMA/133
[   20.115905] ata2: SATA link down (SStatus 0 SControl 300)
[   20.427478] ata3: SATA link down (SStatus 0 SControl 300)
[   20.739053] ata4: SATA link down (SStatus 0 SControl 300)
[   20.739191] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
[   20.740215] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.740351] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   20.740697] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   20.740726] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[   20.750046] Driver 'sd' needs updating - please use bus_type methods
[   20.755557] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   20.755573] sd 0:0:0:0: [sda] Write Protect is off
[   20.755576] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.755592] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.755670] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   20.755680] sd 0:0:0:0: [sda] Write Protect is off
[   20.755683] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.755697] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.755702]  sda: sda1 sda2 < sda5 >
[   20.794955] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.795189] usb usb1: configuration #1 chosen from 1 choice
[   20.795217] hub 1-0:1.0: USB hub found
[   20.795228] hub 1-0:1.0: 2 ports detected
[   20.800275] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.898945] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   20.899087] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   20.899159] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   20.899184] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[   20.954903] usb usb2: configuration #1 chosen from 1 choice
[   20.954930] hub 2-0:1.0: USB hub found
[   20.954941] hub 2-0:1.0: 2 ports detected
[   21.058717] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.058860] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   21.058930] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   21.058955] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[   21.114679] usb usb3: configuration #1 chosen from 1 choice
[   21.114706] hub 3-0:1.0: USB hub found
[   21.114716] hub 3-0:1.0: 2 ports detected
[   21.218494] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   21.218633] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   21.218711] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   21.218732] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[   21.274458] usb usb4: configuration #1 chosen from 1 choice
[   21.274487] hub 4-0:1.0: USB hub found
[   21.274497] hub 4-0:1.0: 2 ports detected
[   21.378284] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   21.378411] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   21.378478] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   21.378499] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[   21.434238] usb usb5: configuration #1 chosen from 1 choice
[   21.434264] hub 5-0:1.0: USB hub found
[   21.434275] hub 5-0:1.0: 2 ports detected
[   21.539034] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   21.539177] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   21.539250] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   21.539297] ehci_hcd 0000:00:13.5: debug port 1
[   21.539316] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[   21.550421] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.550570] usb usb6: configuration #1 chosen from 1 choice
[   21.550598] hub 6-0:1.0: USB hub found
[   21.550606] hub 6-0:1.0: 10 ports detected
[   21.656989] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   21.657164] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   21.657211] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   21.657271] scsi4 : pata_atiixp
[   21.657328] scsi5 : pata_atiixp
[   21.658056] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[   21.658059] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[   21.673906] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   21.673919] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   21.673927] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   21.717764] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   21.717791] b44.c:v2.0
[   21.738060] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:8d:89:28
[   21.977843] ata5.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A103, max UDMA/33
[   22.149571] ata5.00: configured for UDMA/33
[   22.309174] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5
[   22.309282] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   22.318560] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.318568] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.330524] Driver 'sr' needs updating - please use bus_type methods
[   22.348486] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   22.348490] Uniform CD-ROM driver Revision: 3.20
[   22.348540] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   22.562786] Attempting manual resume
[   22.562791] swsusp: Resume From Partition 8:5
[   22.562793] PM: Checking swsusp image.
[   22.562959] PM: Resume from disk failed.
[   22.578385] EXT3-fs: INFO: recovery required on readonly filesystem.
[   22.578391] EXT3-fs: write access will be enabled during recovery.
[   25.074984] kjournald starting.  Commit interval 5 seconds
[   25.075454] EXT3-fs: sda1: orphan cleanup on readonly fs
[   25.098405] ext3_orphan_cleanup: deleting unreferenced inode 2588963
[   25.098456] ext3_orphan_cleanup: deleting unreferenced inode 2187276
[   25.098464] EXT3-fs: sda1: 2 orphan inodes deleted
[   25.098465] EXT3-fs: recovery complete.
[   25.132321] EXT3-fs: mounted filesystem with ordered data mode.
[   35.335717] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.383252] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.459762] ACPI: AC Adapter [ACAD] (on-line)
[   35.509721] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   35.564631] input: Power Button (FF) as /devices/virtual/input/input2
[   35.583210] ACPI: Power Button (FF) [PWRF]
[   35.583305] input: Power Button (CM) as /devices/virtual/input/input3
[   35.587427] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   35.619165] ACPI: Power Button (CM) [PWRB]
[   35.619280] input: Sleep Button (CM) as /devices/virtual/input/input4
[   35.651152] ACPI: Sleep Button (CM) [SLPB]
[   35.651257] input: Lid Switch as /devices/virtual/input/input5
[   35.652484] ACPI: Lid Switch [LID]
[   35.759481] ricoh-mmc: Ricoh MMC Controller disabling driver
[   35.759486] ricoh-mmc: Copyright(c) Philip Langdale
[   35.759551] ricoh-mmc: Ricoh MMC controller found at 0000:08:01.1 [1180:0843] (rev 1)
[   35.759557] ricoh-mmc: Main firewire function not found. Cannot disable controller.
[   35.993366] sdhci: Secure Digital Host Controller Interface driver
[   35.993371] sdhci: Copyright(c) Pierre Ossman
[   35.993437] sdhci: SDHCI controller found at 0000:08:01.0 [1180:0822] (rev 19)
[   35.993467] ACPI: PCI Interrupt 0000:08:01.0[B] -> GSI 20 (level, low) -> IRQ 20
[   35.993721] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   35.993831] mmc0: SDHCI at 0xc0302800 irq 20 DMA
[   36.070694] ACPI: Battery Slot [BAT1] (battery present)
[   36.070812] ACPI: WMI-Acer: Mapper loaded
[   36.100688] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input6
[   36.162478] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   36.215785] ieee80211_crypt: registered algorithm 'NULL'
[   36.255740] wl: module license 'MIXED/Proprietary' taints kernel.
[   36.305948] [fglrx] Maximum main memory to use for locked dma buffers: 797 MBytes.
[   36.305985] [fglrx] ASYNCIO init succeed!
[   36.306187] [fglrx] PAT is enabled successfully!
[   36.306335] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   36.569375] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   36.605107] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   36.658102] b43-phy0: Broadcom 4311 WLAN found
[   36.685869] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   36.701679] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   36.701701] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   36.726207] phy0: Selected rate control algorithm 'simple'
[   38.386787] lp: driver loaded but no devices found
[   38.467012] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   38.554376] usbcore: registered new interface driver ndiswrapper
[   38.625691] Adding 2626588k swap on /dev/sda5.  Priority:-1 extents:1 across:2626588k
[   39.207276] EXT3 FS on sda1, internal journal
[   40.626567] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.187975] No dock devices found.
[   41.482213] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (2 cpu cores) (version 2.20.00)
[   41.481907] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13
[   41.481913] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   41.481916] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[   42.918759] ppdev: user-space parallel port driver
[   43.178784] NET: Registered protocol family 10
[   43.179088] lo: Disabled Privacy Extensions
[   43.646661] audit(1224034266.453:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5103 profile="/usr/sbin/cupsd" namespace="default"
[   44.064603] Clocksource tsc unstable (delta = -147013841 ns)
[   45.141624] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[   45.203934] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   45.228114] usbcore: deregistering interface driver ndiswrapper
[   45.258904] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   45.258918] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   45.267799] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   45.267813] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   45.267822] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   45.267829] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   45.286515] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   45.298694] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[   45.307271] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   45.307283] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   45.307289] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   45.326001] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   45.326031] b44.c:v2.0
[   45.335896] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:8d:89:28
[   45.356703] b43-phy0: Broadcom 4311 WLAN found
[   45.376347] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   45.376363] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   45.389645] phy0: Selected rate control algorithm 'simple'
[   46.418073] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.463444] input: b43-phy0 as /devices/virtual/input/input8
[   46.498498] Bluetooth: Core ver 2.11
[   46.498607] NET: Registered protocol family 31
[   46.498610] Bluetooth: HCI device and connection manager initialized
[   46.498616] Bluetooth: HCI socket layer initialized
[   46.516011] Bluetooth: L2CAP ver 2.9
[   46.516017] Bluetooth: L2CAP socket layer initialized
[   46.631445] Bluetooth: RFCOMM socket layer initialized
[   46.631464] Bluetooth: RFCOMM TTY layer initialized
[   46.631466] Bluetooth: RFCOMM ver 1.8
[   46.667140] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   47.705805] b43-phy0 debug: Chip initialized
[   47.706079] b43-phy0 debug: 32-bit DMA initialized
[   47.725886] Registered led device: b43-phy0:tx
[   47.725913] Registered led device: b43-phy0:rx
[   47.725935] Registered led device: b43-phy0:radio
[   47.725970] b43-phy0 debug: Wireless interface started
[   47.765460] b43-phy0 debug: Adding Interface type 2
[   47.767776] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.532687] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   48.813640] b44: eth0: Link is up at 100 Mbps, full duplex.
[   48.813646] b44: eth0: Flow control is off for TX and off for RX.
[   48.814752] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   49.718409] [fglrx] GART Table is not in FRAME_BUFFER range 
[   49.718420] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   49.718423] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[   49.830853] [fglrx] interrupt source 20008000 successfully enabled
[   49.830863] [fglrx] enable ID = 0x00000004
[   49.830873] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   50.434597] NET: Registered protocol family 17
[   54.808787] hda-intel: Invalid position buffer, using LPIB read method instead.
[   58.122110] eth0: no IPv6 routers present
[   80.059045] CPU0 attaching NULL sched-domain.
[   80.059057] CPU1 attaching NULL sched-domain.
[   80.068333] CPU0 attaching sched-domain:
[   80.068342]  domain 0: span 03
[   80.068345]   groups: 01 02
[   80.068348]   domain 1: span 03
[   80.068350]    groups: 03
[   80.068352] CPU1 attaching sched-domain:
[   80.068354]  domain 0: span 03
[   80.068356]   groups: 02 01
[   80.068358]   domain 1: span 03
[   80.068360]    groups: 03
[  249.561071] APIC error on CPU0: 00(40)
[  249.560312] APIC error on CPU1: 00(40)
[  480.379781] audit(1224034975.447:3): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=10148 profile="/usr/sbin/cupsd" namespace="default"
[  480.379851] audit(1224034975.447:4): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=10148 profile="/usr/sbin/cupsd" namespace="default"
[  480.849981] audit(1224034975.963:5): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=10148 profile="/usr/sbin/cupsd" namespace="default"
[  480.885045] audit(1224034976.035:6): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=10148 profile="/usr/sbin/cupsd" namespace="default"
[  480.885090] audit(1224034976.035:7): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=10148 profile="/usr/sbin/cupsd" namespace="default"
[  481.031820] audit(1224034976.347:8): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/run/samba/gencache.tdb" pid=10148 profile="/usr/sbin/cupsd" namespace="default"
[  955.478839] APIC error on CPU0: 40(40)
[  955.476018] APIC error on CPU1: 40(40)
[  986.933455] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[  986.933462] ACPI: EC: read timeout, command = 130
[ 1028.336207] b43-phy0 debug: Removing Interface type 2
[ 1028.368184] b43-phy0 debug: Wireless interface stopped
[ 1028.368284] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[ 1028.368340] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[ 1028.374956] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[ 1028.378672] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[ 1028.382476] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[ 1028.386193] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[ 1028.390432] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[ 1035.592799] input: b43-phy0 as /devices/virtual/input/input9
[ 1035.670059] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1036.829154] b43-phy0 debug: Chip initialized
[ 1036.829658] b43-phy0 debug: 32-bit DMA initialized
[ 1036.849408] Registered led device: b43-phy0:tx
[ 1036.849666] Registered led device: b43-phy0:rx
[ 1036.849837] Registered led device: b43-phy0:radio
[ 1036.849879] b43-phy0 debug: Wireless interface started
[ 1036.850130] b43-phy0 debug: Adding Interface type 2
[ 1036.852440] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1207.521784] APIC error on CPU0: 40(40)
[ 1207.518322] APIC error on CPU1: 40(40)
[ 1338.609222] APIC error on CPU0: 40(40)
[ 1338.605543] APIC error on CPU1: 40(40)
[ 1346.024222] APIC error on CPU0: 40(40)
[ 1346.020524] APIC error on CPU1: 40(40)
[ 1410.565020] APIC error on CPU1: 40(40)
[ 1410.568891] APIC error on CPU0: 40(40)
[ 2447.013751] APIC error on CPU1: 40(40)
[ 2447.019966] APIC error on CPU0: 40(40)
[ 2527.270379] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[ 2527.270388] ACPI: EC: read timeout, command = 128
[ 2527.270628] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
[ 2527.270639] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
[ 2527.270650] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT1._STA] (Node ffff8100355df5a0), AE_TIME
[ 2527.270704] ACPI Exception (battery-0306): AE_ERROR, Evaluating _STA [20070126]
[ 4339.661261] APIC error on CPU1: 40(40)
[ 4339.672144] APIC error on CPU0: 40(40)
```


Result of cat /var/log/Xorg.0.log was:

```
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0006af741c00000000
(II) fglrx(0): 	010f0103802115780aa7e599594f8c27
(II) fglrx(0): 	1d505400000001010101010101010101
(II) fglrx(0): 	010101010101c71b00a0502017301520
(II) fglrx(0): 	44004bcf10000018261700a050201730
(II) fglrx(0): 	152044004bcf10000000000000fe0046
(II) fglrx(0): 	463035390042313534455731000000fe
(II) fglrx(0): 	0030414d5778a4ccf801010a202000e9
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 401/401MHz @ 60Hz []
(II) fglrx(0):   2. 100/133MHz @ 60Hz [low voltage]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   71.11  1280 1296 1328 1440  800 804 808 823 (49.4 kHz)
(**) fglrx(0): *Mode "1280x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   71.11  1280 1296 1328 1440  768 788 792 823 (49.4 kHz)
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   71.11  1024 1168 1200 1440  768 788 792 823 (49.4 kHz)
(**) fglrx(0): *Mode "848x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   71.11  848 1080 1112 1440  480 644 648 823 (49.4 kHz)
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   71.11  800 1056 1088 1440  600 704 708 823 (49.4 kHz)
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   71.11  720 1016 1048 1440  480 644 648 823 (49.4 kHz)
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   71.11  640 976 1008 1440  480 644 648 823 (49.4 kHz)
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   71.11  640 976 1008 1440  400 604 608 823 (49.4 kHz)
(**) fglrx(0):  Default mode "640x350": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0   71.11  640 976 1008 1440  350 579 583 823 (49.4 kHz)
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   71.11  512 912 944 1440  384 596 600 823 (49.4 kHz)
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   71.11  400 856 888 1440  300 704 708 823 doublescan (49.4 kHz)
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   71.11  320 816 848 1440  240 644 648 823 doublescan (49.4 kHz)
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   71.11  320 816 848 1440  200 604 608 823 doublescan (49.4 kHz)
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   71.11  1280 1296 1328 1440  800 804 808 823 (49.4 kHz)
(**) fglrx(0): *Mode "1280x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   71.11  1280 1296 1328 1440  768 788 792 823 (49.4 kHz)
(**) fglrx(0): *Mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   71.11  1024 1168 1200 1440  768 788 792 823 (49.4 kHz)
(**) fglrx(0): *Mode "848x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"x60.0   71.11  848 1080 1112 1440  480 644 648 823 (49.4 kHz)
(**) fglrx(0): *Mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   71.11  800 1056 1088 1440  600 704 708 823 (49.4 kHz)
(**) fglrx(0): *Mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   71.11  720 1016 1048 1440  480 644 648 823 (49.4 kHz)
(**) fglrx(0): *Mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   71.11  640 976 1008 1440  480 644 648 823 (49.4 kHz)
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   71.11  640 976 1008 1440  400 604 608 823 (49.4 kHz)
(**) fglrx(0):  Default mode "640x350": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"x60.0   71.11  640 976 1008 1440  350 579 583 823 (49.4 kHz)
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   71.11  512 912 944 1440  384 596 600 823 (49.4 kHz)
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   71.11  400 856 888 1440  300 704 708 823 doublescan (49.4 kHz)
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   71.11  320 816 848 1440  240 644 648 823 doublescan (49.4 kHz)
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   71.11  320 816 848 1440  200 604 608 823 doublescan (49.4 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0302c00 - 0xc0302cff (0x100) MX[B]
	[7] -1	0	0xc0302800 - 0xc03028ff (0x100) MX[B]
	[8] -1	0	0xc0300000 - 0xc0301fff (0x2000) MX[B]
	[9] -1	0	0xc0200000 - 0xc0203fff (0x4000) MX[B]
	[10] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[11] -1	0	0xc0004800 - 0xc0004bff (0x400) MX[B]
	[12] -1	0	0xc0004400 - 0xc00044ff (0x100) MX[B]
	[13] -1	0	0xc0009000 - 0xc0009fff (0x1000) MX[B]
	[14] -1	0	0xc0008000 - 0xc0008fff (0x1000) MX[B]
	[15] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[16] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[17] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[18] -1	0	0xc0004000 - 0xc00043ff (0x400) MX[B]
	[19] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[20] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[24] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x00008420 - 0x0000842f (0x10) IX[B]
	[28] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[33] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[34] -1	0	0x00008450 - 0x00008453 (0x4) IX[B]
	[35] -1	0	0x00008430 - 0x00008437 (0x8) IX[B]
	[36] -1	0	0x00008454 - 0x00008457 (0x4) IX[B]
	[37] -1	0	0x00008438 - 0x0000843f (0x8) IX[B]
	[38] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [drm] installed DRM signal handler
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.47.3
(II) fglrx(0):     Date: Feb 25 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-21-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 17.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x005f0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1216)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 416
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 20008000
...dwIRQEnableId: 00000004
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ca"
(**) Generic Keyboard: XkbLayout: "ca"
(**) Option "XkbVariant" "fr-legacy"
(**) Generic Keyboard: XkbVariant: "fr-legacy"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
(II) XAA: Evicting pixmaps
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

It's gobbledegook to me--is there anyone who's able to spot where my computer's going wrong?

Thanks!

---

### Post by dontbotherdave on 2008-10-30
I've been having the same problem but can't really find a solution. Here is a post that explains the same symptoms but no one has responded: [_http://ubuntuforums.org/showthread.php?t=810184_]("http://ubuntuforums.org/showthread.php?t=810184"). I would also like to know the answer to this riddle...

---

### Post by rare HERO on 2008-11-18
via Synaptic Package Manager:
[INDENT]cron-like program that doesn't go by time 
Anacron (like `anac(h)ronistic') is a periodic command scheduler.  It
executes commands at intervals specified in days.  Unlike cron, it
does not assume that the system is running continuously.  It can
therefore be used to control the execution of daily, weekly and
monthly jobs (or anything with a period of n days), on systems that
don't run 24 hours a day.  When installed and configured properly,
Anacron will make sure that the commands are run at the specified
intervals as closely as machine-uptime permits.

This package is pre-configured to execute the daily jobs of the Debian
system. You should install this program if your system isn't powered on
24 hours a day to make sure the maintenance jobs of other Debian packages
are executed each day.[/INDENT]

For some reason this kept killing gnome, and I couldn't use my computer (because I need GUI). So I removed Anacron by typing the following into terminal
```
$ sudo apt-get remove anacron
```
If anyone knows what anacron is supposed to be used for, let me know.

---

