---
title: "blank screen after splash but harddisk still working"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-11-12
This has happened several times this month. After the splash screen finished, the screen went blank but the harddrive activity LED was still on. I hard reset the computer several times and it could finally show up the x. Is the harddrive having problem? it dual boots with xp and seems there's no problem with the harddrive.
It just happened again and here's is the dmesg:

```
dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002feea000 (usable)
[    0.000000]  BIOS-e820: 000000002feea000 - 000000002feed000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002feed000 - 000000002fefd000 (reserved)
[    0.000000]  BIOS-e820: 000000002fefd000 - 000000002fefe000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fefe000 - 000000002ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 766MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196330) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196330
[    0.000000]   HighMem    196330 ->   196330
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196330
[    0.000000] On node 0 totalpages: 196330
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1501 pages used for memmap
[    0.000000]   Normal zone: 190733 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5360 checksum 0
[    0.000000] ACPI: RSDP 000F5360, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 2FEEA000, 0030 (r1 ASUS   P4GE-V   42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 2FEEA0C0, 0074 (r1 ASUS   P4GE-V   42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 2FEEA134, 2A67 (r1   ASUS P4GE-V       1000 MSFT  100000B)
[    0.000000] ACPI: FACS 2FEFD000, 0040
[    0.000000] ACPI: BOOT 2FEEA030, 0028 (r1 ASUS   P4GE-V   42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 2FEEA058, 005A (r1 ASUS   P4GE-V   42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
[    0.000000] Built 1 zonelists.  Total pages: 194797
[    0.000000] Kernel command line: root=UUID=238e764e-81b6-48d8-84da-71f4d8e4b9ba ro splash vga=normal
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1804.158 MHz processor.
[    8.597126] Console: colour VGA+ 80x25
[    8.600521] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.601527] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.623519] Memory: 766860k/785320k available (2015k kernel code, 17892k reserved, 915k data, 364k init, 0k highmem)
[    8.623607] virtual kernel memory layout:
[    8.623609]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    8.623612]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.623614]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[    8.623615]     lowmem  : 0xc0000000 - 0xefeea000   ( 766 MB)
[    8.623617]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    8.623619]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    8.623620]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    8.624038] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.624194] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.704208] Calibrating delay using timer specific routine.. 3612.02 BogoMIPS (lpj=7224048)
[    8.704344] Security Framework v1.0.0 initialized
[    8.704406] SELinux:  Disabled at boot.
[    8.704476] Mount-cache hash table entries: 512
[    8.704724] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[    8.704742] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    8.704835] CPU: L2 cache: 512K
[    8.704887] CPU: Hyper-Threading is disabled
[    8.704942] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[    8.704958] Compat vDSO mapped to ffffe000.
[    8.705028] Checking 'hlt' instruction... OK.
[    8.720398] SMP alternatives: switching to UP code
[    8.720706] Freeing SMP alternatives: 11k freed
[    8.721176] Early unpacking initramfs... done
[    9.161346] ACPI: Core revision 20070126
[    9.161477] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.163237] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 07
[    9.163417] Total of 1 processors activated (3612.02 BogoMIPS).
[    9.163618] ENABLING IO-APIC IRQs
[    9.163910] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.307677] Brought up 1 CPUs
[    9.307905] Booting paravirtualized kernel on bare hardware
[    9.308045] Time:  9:00:42  Date: 10/13/108
[    9.308133] NET: Registered protocol family 16
[    9.308333] EISA bus registered
[    9.308402] ACPI: bus type pci registered
[    9.310474] PCI: PCI BIOS revision 2.10 entry at 0xf1e60, last bus=2
[    9.310531] PCI: Using configuration type 1
[    9.310584] Setting up standard PCI resources
[    9.315297] ACPI: EC: Look up EC in DSDT
[    9.323328] ACPI: Interpreter enabled
[    9.323388] ACPI: (supports S0 S1 S3 S4 S5)
[    9.323678] ACPI: Using IOAPIC for interrupt routing
[    9.342269] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.342346] PCI: Probing PCI hardware (bus 00)
[    9.342905] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    9.342907] * this clock source is slow. If you are sure your timer does not have
[    9.342909] * this bug, please use "acpi_pm_good" to disable the workaround
[    9.343147] PCI: Enabled i801 SMBus device
[    9.343205] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[    9.343263] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[    9.343713] PCI: Transparent bridge - 0000:00:1e.0
[    9.343796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.343939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    9.428788] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    9.429428] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.430061] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.430694] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.431327] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.431954] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.432644] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.433350] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    9.433995] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.434067] pnp: PnP ACPI init
[    9.434131] ACPI: bus type pnp registered
[    9.441087] pnp: PnP ACPI: found 16 devices
[    9.441144] ACPI: ACPI bus type pnp unregistered
[    9.441202] PnPBIOS: Disabled by ACPI PNP
[    9.441346] PCI: Using ACPI for IRQ routing
[    9.441401] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.449189] NET: Registered protocol family 8
[    9.449243] NET: Registered protocol family 20
[    9.449392] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    9.449451] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    9.449510] pnp: 00:00: iomem range 0x100000-0x2fefffff could not be reserved
[    9.449568] pnp: 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[    9.449642] pnp: 00:02: ioport range 0xe400-0xe47f has been reserved
[    9.449698] pnp: 00:02: ioport range 0xe800-0xe81f has been reserved
[    9.449754] pnp: 00:02: ioport range 0xec00-0xec3f has been reserved
[    9.449810] pnp: 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    9.449867] pnp: 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    9.449935] pnp: 00:02: iomem range 0xffb80000-0xffbfffff has been reserved
[    9.450008] pnp: 00:0f: ioport range 0x3f0-0x3f1 has been reserved
[    9.451482] Time: tsc clocksource has been installed.
[    9.480536] PCI: Bridge: 0000:00:1e.0
[    9.480589]   IO window: disabled.
[    9.480644]   MEM window: ee800000-eeffffff
[    9.480699]   PREFETCH window: disabled.
[    9.480767] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.480788] NET: Registered protocol family 2
[    9.519488] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.519770] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    9.521939] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.522871] TCP: Hash tables configured (established 131072 bind 65536)
[    9.522939] TCP reno registered
[    9.531667] checking if image is initramfs... it is
[    9.982969] Switched to high resolution mode on CPU 0
[   10.407991] Freeing initrd memory: 7073k freed
[   10.408239] Simple Boot Flag at 0x3a set to 0x1
[   10.408658] audit: initializing netlink socket (disabled)
[   10.408734] audit(1226566842.224:1): initialized
[   10.411987] VFS: Disk quotas dquot_6.5.1
[   10.412127] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.412331] io scheduler noop registered
[   10.412385] io scheduler anticipatory registered
[   10.412439] io scheduler deadline registered
[   10.412515] io scheduler cfq registered (default)
[   10.412586] Boot video device is 0000:00:02.0
[   10.412881] isapnp: Scanning for PnP cards...
[   10.766976] isapnp: No Plug & Play device found
[   10.806905] Real Time Clock Driver v1.12ac
[   10.807101] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.807293] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.807626] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   10.808636] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.809108] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   10.810403] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.810798] input: Macintosh mouse button emulation as /class/input/input0
[   10.810992] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.814922] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.814988] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.815344] mice: PS/2 mouse device common for all mice
[   10.815568] EISA: Probing bus 0 at eisa.0
[   10.815661] EISA: Detected 0 cards.
[   10.815860] TCP cubic registered
[   10.815926] NET: Registered protocol family 1
[   10.816010] Using IPI No-Shortcut mode
[   10.816280]   Magic number: 0:920:19
[   10.818055] Freeing unused kernel memory: 364k freed
[   10.854060] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.150218] AppArmor: AppArmor initialized<5>audit(1226566844.224:2):  type=1505 info="AppArmor initialized" pid=1186
[   12.162810] fuse init (API version 7.8)
[   12.169938] Failure registering capabilities with primary security module.
[   12.189724] ACPI: Invalid PBLK length [5]
[   12.189778] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   13.036240] usbcore: registered new interface driver usbfs
[   13.036286] usbcore: registered new interface driver hub
[   13.036321] usbcore: registered new device driver usb
[   13.037690] USB Universal Host Controller Interface driver v3.0
[   13.037788] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.037805] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.037811] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.038031] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.038066] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   13.038246] usb usb1: configuration #1 chosen from 1 choice
[   13.038288] hub 1-0:1.0: USB hub found
[   13.038302] hub 1-0:1.0: 2 ports detected
[   13.139737] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   13.139758] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.139763] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.139800] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.139834] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d400
[   13.139993] usb usb2: configuration #1 chosen from 1 choice
[   13.140034] hub 2-0:1.0: USB hub found
[   13.140048] hub 2-0:1.0: 2 ports detected
[   13.154218] SCSI subsystem initialized
[   13.162531] libata version 2.21 loaded.
[   13.243614] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.243634] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.243640] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.243676] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.243711] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[   13.243862] usb usb3: configuration #1 chosen from 1 choice
[   13.243904] hub 3-0:1.0: USB hub found
[   13.243916] hub 3-0:1.0: 2 ports detected
[   13.346003] Floppy drive(s): fd0 is 1.44M
[   13.347856] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   13.347876] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.347882] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.347926] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.347975] ehci_hcd 0000:00:1d.7: debug port 1
[   13.347985] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   13.347998] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xef000000
[   13.351880] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.352014] usb usb4: configuration #1 chosen from 1 choice
[   13.352057] hub 4-0:1.0: USB hub found
[   13.352071] hub 4-0:1.0: 6 ports detected
[   13.420292] FDC 0 is a post-1991 82077
[   13.458985] ata_piix 0000:00:1f.1: version 2.11
[   13.459010] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   13.459067] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.459231] scsi0 : ata_piix
[   13.459298] scsi1 : ata_piix
[   13.459456] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   13.459461] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   13.639406] ata1.00: ATA-6: IC35L090AVV207-0, V23OA63A, max UDMA/100
[   13.639415] ata1.00: 160836480 sectors, multi 16: LBA48 
[   13.679050] ata1.01: ATA-7: ST3160812A, 3.AAJ, max UDMA/100
[   13.679057] ata1.01: 312581808 sectors, multi 16: LBA48 
[   13.703335] ata1.00: configured for UDMA/100
[   13.762181] ata1.01: configured for UDMA/100
[   14.078728] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4082B, A208, max UDMA/66
[   14.250562] ata2.00: configured for UDMA/66
[   14.251908] scsi 0:0:0:0: Direct-Access     ATA      IC35L090AVV207-0 V23O PQ: 0 ANSI: 5
[   14.252552] scsi 0:0:1:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
[   14.258160] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082B A208 PQ: 0 ANSI: 5
[   14.258750] b44.c:v1.01 (Jun 16, 2006)
[   14.258782] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[   14.262543] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0c:6e:1a:85:a6
[   14.290229] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   14.290284] sd 0:0:0:0: [sda] Write Protect is off
[   14.290288] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.290317] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.290409] sd 0:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[   14.290426] sd 0:0:0:0: [sda] Write Protect is off
[   14.290429] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.290456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.290463]  sda: sda1 sda2 < sda5 sda6 sda7 >
[   14.337511] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.338758] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   14.338779] sd 0:0:1:0: [sdb] Write Protect is off
[   14.338784] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   14.338812] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.338888] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   14.338905] sd 0:0:1:0: [sdb] Write Protect is off
[   14.338909] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   14.338935] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.338940]  sdb: sdb1 < sdb5 sdb6 sdb7 sdb8 > sdb2
[   14.417109] sd 0:0:1:0: [sdb] Attached SCSI disk
[   14.423112] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.423146] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   14.423176] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   14.472043] sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.472054] Uniform CD-ROM driver Revision: 3.20
[   14.472442] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   15.189231] Attempting manual resume
[   15.189238] swsusp: Resume From Partition 8:18
[   15.189241] PM: Checking swsusp image.
[   15.198363] PM: Resume from disk failed.
[   15.254131] kjournald starting.  Commit interval 5 seconds
[   15.254150] EXT3-fs: mounted filesystem with writeback data mode.
[   23.791010] Linux agpgart interface v0.102 (c) Dave Jones
[   23.804653] NET: Registered protocol family 17
[   24.074525] agpgart: Detected an Intel 830M Chipset.
[   24.074670] agpgart: Detected 892K stolen memory.
[   24.092446] agpgart: AGP aperture is 128M @ 0xf0000000
[   24.255231] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   24.455492] b44: eth0: Link is up at 100 Mbps, full duplex.
[   24.455500] b44: eth0: Flow control is off for TX and off for RX.
[   24.459927] iTCO_vendor_support: vendor-support=0
[   24.465438] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   24.465548] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0xe460)
[   24.465607] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.479292] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.489649] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.876331] intel_rng: FWH not detected
[   25.456376] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   25.458969] parport_pc 00:09: reported by Plug and Play ACPI
[   25.459027] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   25.490720] input: PC Speaker as /class/input/input3
[   25.588459] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   25.588488] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   26.009658] intel8x0_measure_ac97_clock: measured 52014 usecs
[   26.009666] intel8x0: clocking to 48000
[   27.098866] lp0: using parport0 (interrupt-driven).
[   27.120626] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 17 (level, low) -> IRQ 21
[   27.357415] Adding 1461904k swap on /dev/sdb2.  Priority:-1 extents:1 across:1461904k
[   27.872892] EXT3 FS on sdb7, internal journal
[   28.466364] NET: Registered protocol family 10
[   28.466498] lo: Disabled Privacy Extensions
[   29.566027] kjournald starting.  Commit interval 5 seconds
[   29.566172] EXT3 FS on sdb8, internal journal
[   29.566178] EXT3-fs: mounted filesystem with writeback data mode.
[   29.608936] kjournald starting.  Commit interval 5 seconds
[   29.609176] EXT3 FS on sdb6, internal journal
[   29.609182] EXT3-fs: mounted filesystem with writeback data mode.
[   29.627272] kjournald starting.  Commit interval 5 seconds
[   29.627455] EXT3 FS on sdb5, internal journal
[   29.627461] EXT3-fs: mounted filesystem with writeback data mode.
[   33.506550] No dock devices found.
[   33.713974] input: Power Button (FF) as /class/input/input4
[   33.720339] ACPI: Power Button (FF) [PWRF]
[   33.767952] input: Power Button (CM) as /class/input/input5
[   33.774210] ACPI: Power Button (CM) [PWRB]
[   35.541333] Failure registering capabilities with primary security module.
[   35.957536] ppdev: user-space parallel port driver
[   36.417503] audit(1226538069.012:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4949 profile="/usr/sbin/cupsd"
[   36.485785] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   36.485793] apm: overridden by ACPI.
[   36.884303] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   37.011198] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   37.019815] NFSD: starting 90-second grace period
[   37.948683] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   37.948691] vboxdrv: Successfully done.
[   38.422514] Bluetooth: Core ver 2.11
[   38.422693] NET: Registered protocol family 31
[   38.422697] Bluetooth: HCI device and connection manager initialized
[   38.422702] Bluetooth: HCI socket layer initialized
[   38.451429] Bluetooth: L2CAP ver 2.8
[   38.451435] Bluetooth: L2CAP socket layer initialized
[   38.512563] Bluetooth: RFCOMM socket layer initialized
[   38.512721] Bluetooth: RFCOMM TTY layer initialized
[   38.512725] Bluetooth: RFCOMM ver 1.8
[   38.987486] eth0: no IPv6 routers present
[   40.754128] [drm] Initialized drm 1.1.0 20060810
[   40.776178] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   40.780066] [drm] Initialized i915 1.6.0 20060119 on minor 0

```
The OS is Ubuntu 7.10
Thanks!

---

### Post by afeasfaerw23231233 on 2008-11-13
bump

---

### Post by thehellboy on 2008-11-13
i have this same problem.. i use hardy

---

