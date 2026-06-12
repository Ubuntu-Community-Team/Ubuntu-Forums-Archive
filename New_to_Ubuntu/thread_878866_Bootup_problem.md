---
title: "Bootup problem"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Shippou on 2008-08-03
Hello guys.

I just switched (again) to Mint. 

Well, I thought that maybe reformatting the hard drive or deleting all of the system files in a drive will fix this problem, but it doesn't.

I do think this problem started when I hibernated my Windows session. Then after that, every reboot there will be fail messages that prompts me to run fsck manually. I tried that one time when I am still Kubuntu, but it only messed up my hard drive.

As of now, I have freshly reformatted my Linux partition with Mint 3.0 (this is my latest CD), but the problem still remains, though it is lessened by three to four lines.

My Windows partition is still fine.

Please help.

---

### Post by jamesrfla on 2008-08-03
Looks like you need to point your Grub or whatever you use to your windows partition when you boot.

---

### Post by Shippou on 2008-08-03
I can boot up fine in both Linux and Windows.

What my problem is that there are error messages that appear evem after reformatting my partitions. If it helps, this is my dmesg output:
```

root@Shippou:/home# dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000097ee0000 end: 0000000097fe0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000097fe0000 size: 0000000000003000 end: 0000000097fe3000 type: 4
[    0.000000] copy_e820_map() start: 0000000097fe3000 size: 000000000000d000 end: 0000000097ff0000 type: 3
[    0.000000] copy_e820_map() start: 0000000097ff0000 size: 0000000000010000 end: 0000000098000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
[    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1535MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3c80
[    0.000000] Entering add_active_range(0, 0, 622560) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   622560
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   622560
[    0.000000] On node 0 totalpages: 622560
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3071 pages used for memmap
[    0.000000]   HighMem zone: 390113 pages, LIFO batch:31
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP (v002 RS690                                 ) @ 0x000f7b80
[    0.000000] ACPI: RSDT (v001 RS690  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x97fe3040
[    0.000000] ACPI: FADT (v001 RS690  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x97fe30c0
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x97fe7dc0
[    0.000000] ACPI: HPET (v001 RS690  AWRDACPI 0x42302e31 AWRD 0x00000098) @ 0x97fe7f00
[    0.000000] ACPI: MCFG (v001 RS690  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x97fe7f80
[    0.000000] ACPI: MADT (v001 RS690  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x97fe7d00
[    0.000000] ACPI: DSDT (v001 RS690  AWRDACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
[    0.000000] Detected 1799.941 MHz processor.
[   10.641490] Built 1 zonelists.  Total pages: 617697
[   10.641494] Kernel command line: root=UUID=4254b483-9468-46fb-a0b8-87ea369d8cae ro quiet splash
[   10.641630] mapped APIC to ffffd000 (fee00000)
[   10.641632] mapped IOAPIC to ffffc000 (fec00000)
[   10.641635] Enabling fast FPU save and restore... done.
[   10.641638] Enabling unmasked SIMD FPU exception support... done.
[   10.641644] Initializing CPU#0
[   10.641688] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   10.642384] Console: colour VGA+ 80x25
[   10.642636] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.643078] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.733874] Memory: 2458024k/2490240k available (1992k kernel code, 30976k reserved, 893k data, 328k init, 1572736k highmem)
[   10.733886] virtual kernel memory layout:
[   10.733887]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   10.733888]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.733889]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.733891]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.733892]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   10.733893]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   10.733895]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   10.733898] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.734042] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   10.734047] hpet0: 4 32-bit timers, 14318180 Hz
[   10.735054] Using HPET for base-timer
[   10.814144] Calibrating delay using timer specific routine.. 3707.95 BogoMIPS (lpj=7415905)
[   10.814199] Security Framework v1.0.0 initialized
[   10.814204] SELinux:  Disabled at boot.
[   10.814218] Mount-cache hash table entries: 512
[   10.814330] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d
[   10.814338] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.814340] CPU: L2 Cache: 512K (64 bytes/line)
[   10.814343] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001d
[   10.814352] Compat vDSO mapped to ffffe000.
[   10.814355] Remapping vsyscall page to ffffe000
[   10.814364] Checking 'hlt' instruction... OK.
[   10.830223] SMP alternatives: switching to UP code
[   10.830365] Freeing SMP alternatives: 11k freed
[   10.830546] Early unpacking initramfs... done
[   11.180132] ACPI: Core revision 20060707
[   11.180722] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.188611] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[   11.188631] Total of 1 processors activated (3707.95 BogoMIPS).
[   11.188921] ENABLING IO-APIC IRQs
[   11.189151] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.337058] Brought up 1 CPUs
[   11.337277] Booting paravirtualized kernel on bare hardware
[   11.337350] Time: 23:18:28  Date: 07/03/108
[   11.337373] NET: Registered protocol family 16
[   11.337443] EISA bus registered
[   11.337446] ACPI: bus type pci registered
[   11.338538] PCI: PCI BIOS revision 3.00 entry at 0xfa020, last bus=2
[   11.338540] PCI: Using configuration type 1
[   11.338542] Setting up standard PCI resources
[   11.346216] ACPI: Interpreter enabled
[   11.346221] ACPI: Using IOAPIC for interrupt routing
[   11.346804] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.346809] PCI: Probing PCI hardware (bus 00)
[   11.346877] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   11.347719] Boot video device is 0000:01:05.0
[   11.347872] PCI: Transparent bridge - 0000:00:14.4
[   11.347897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.373317] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.373530] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.373743] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.373957] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.374169] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.374382] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.374596] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.374811] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   11.375331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   11.378075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.378343] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.378354] pnp: PnP ACPI init
[   11.381848] pnp: PnP ACPI: found 15 devices
[   11.381852] PnPBIOS: Disabled by ACPI PNP
[   11.381897] PCI: Using ACPI for IRQ routing
[   11.381899] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.428867] NET: Registered protocol family 8
[   11.428869] NET: Registered protocol family 20
[   11.429241] pnp: 00:01: ioport range 0x4100-0x411f has been reserved
[   11.429244] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   11.429247] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   11.429249] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   11.429252] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   11.429255] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   11.429257] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   11.429260] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   11.429470] PCI: Ignore bogus resource 6 [0:0] of 0000:01:05.0
[   11.429473] PCI: Bridge: 0000:00:01.0
[   11.429475]   IO window: e000-efff
[   11.429479]   MEM window: fdd00000-fdefffff
[   11.429481]   PREFETCH window: d8000000-dfffffff
[   11.429486] PCI: Bridge: 0000:00:14.4
[   11.429489]   IO window: d000-dfff
[   11.429494]   MEM window: fdc00000-fdcfffff
[   11.429499]   PREFETCH window: fdf00000-fdffffff
[   11.429539] NET: Registered protocol family 2
[   11.468877] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.469033] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.469990] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.470512] TCP: Hash tables configured (established 131072 bind 65536)
[   11.470514] TCP reno registered
[   11.480910] checking if image is initramfs... it is
[   12.112380] Freeing initrd memory: 7007k freed
[   12.112756] audit: initializing netlink socket (disabled)
[   12.112769] audit(1217805509.464:1): initialized
[   12.112822] highmem bounce pool size: 64 pages
[   12.112874] VFS: Disk quotas dquot_6.5.1
[   12.112890] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.112934] io scheduler noop registered
[   12.112936] io scheduler anticipatory registered
[   12.112939] io scheduler deadline registered
[   12.112946] io scheduler cfq registered (default)
[   12.271706] isapnp: Scanning for PnP cards...
[   12.635325] isapnp: No Plug & Play device found
[   12.656694] Real Time Clock Driver v1.12ac
[   12.656840] hpet_resources: 0xfed00000 is busy
[   12.656855] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.656989] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.657628] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.657832] mice: PS/2 mouse device common for all mice
[   12.658260] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.658455] input: Macintosh mouse button emulation as /class/input/input0
[   12.658484] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.658487] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.658696] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.658966] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.658969] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.659061] EISA: Probing bus 0 at eisa.0
[   12.659080] Cannot allocate resource for EISA slot 4
[   12.659097] EISA: Detected 0 cards.
[   12.689230] TCP cubic registered
[   12.689241] NET: Registered protocol family 1
[   12.689258] Using IPI No-Shortcut mode
[   12.689315] ACPI: (supports S0 S3 S4 S5)
[   12.689360]   Magic number: 4:947:351
[   12.689732] Freeing unused kernel memory: 328k freed
[   12.690767] Time: tsc clocksource has been installed.
[   12.702660] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.927286] Capability LSM initialized
[   13.962110] ACPI: Fan [FAN] (on)
[   13.965376] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   13.966482] ACPI: Thermal Zone [THRM] (40 C)
[   14.464941] SCSI subsystem initialized
[   14.469201] libata version 2.20 loaded.
[   14.470376] ahci 0000:00:12.0: version 2.1
[   14.470407] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.481828] usbcore: registered new interface driver usbfs
[   14.481848] usbcore: registered new interface driver hub
[   14.481867] usbcore: registered new device driver usb
[   14.482487] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.701956] Floppy drive(s): fd0 is 1.44M
[   14.758592] FDC 0 is a post-1991 82077
[   15.474115] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   15.474120] ahci 0000:00:12.0: flags: 64bit ncq ilck pm led clo pmp pio slum part 
[   15.474238] ata1: SATA max UDMA/133 cmd 0xf8830100 ctl 0x00000000 bmdma 0x00000000 irq 16
[   15.474332] ata2: SATA max UDMA/133 cmd 0xf8830180 ctl 0x00000000 bmdma 0x00000000 irq 16
[   15.474427] ata3: SATA max UDMA/133 cmd 0xf8830200 ctl 0x00000000 bmdma 0x00000000 irq 16
[   15.474522] ata4: SATA max UDMA/133 cmd 0xf8830280 ctl 0x00000000 bmdma 0x00000000 irq 16
[   15.474535] scsi0 : ahci
[   15.961264] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.006691] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   16.006697] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
[   16.006699] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   16.064898] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   16.064903] ata1.00: configured for UDMA/133
[   16.064911] scsi1 : ahci
[   16.376551] ata2: SATA link down (SStatus 0 SControl 300)
[   16.376563] scsi2 : ahci
[   16.692022] ata3: SATA link down (SStatus 0 SControl 300)
[   16.692033] scsi3 : ahci
[   17.007488] ata4: SATA link down (SStatus 0 SControl 300)
[   17.007587] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
[   17.009465] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.009479] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   17.009698] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   17.009715] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[   17.019030] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   17.019041] sda: Write Protect is off
[   17.019044] sda: Mode Sense: 00 3a 00 00
[   17.019055] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.019100] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   17.019107] sda: Write Protect is off
[   17.019109] sda: Mode Sense: 00 3a 00 00
[   17.019120] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.019125]  sda: sda1 sda2 sda3 sda4
[   17.071574] usb usb1: configuration #1 chosen from 1 choice
[   17.071596] hub 1-0:1.0: USB hub found
[   17.071607] hub 1-0:1.0: 2 ports detected
[   17.073286] sd 0:0:0:0: Attached scsi disk sda
[   17.077701] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.179314] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   17.179330] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.179349] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   17.179369] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[   17.243290] usb usb2: configuration #1 chosen from 1 choice
[   17.243316] hub 2-0:1.0: USB hub found
[   17.243327] hub 2-0:1.0: 2 ports detected
[   17.351027] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.351043] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   17.351064] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   17.351084] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[   17.396756] Attempting manual resume
[   17.396760] swsusp: Resume From Partition 8:3
[   17.396761] PM: Checking swsusp image.
[   17.414990] usb usb3: configuration #1 chosen from 1 choice
[   17.415013] hub 3-0:1.0: USB hub found
[   17.415024] hub 3-0:1.0: 2 ports detected
[   17.422066] PM: Resume from disk failed.
[   17.466506] kjournald starting.  Commit interval 5 seconds
[   17.466516] EXT3-fs: mounted filesystem with ordered data mode.
[   17.522732] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   17.522749] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   17.522773] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   17.522788] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[   17.586706] usb usb4: configuration #1 chosen from 1 choice
[   17.586729] hub 4-0:1.0: USB hub found
[   17.586740] hub 4-0:1.0: 2 ports detected
[   17.694420] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   17.694435] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   17.694456] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   17.694472] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[   17.758393] usb usb5: configuration #1 chosen from 1 choice
[   17.758413] hub 5-0:1.0: USB hub found
[   17.758423] hub 5-0:1.0: 2 ports detected
[   17.866265] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   17.866278] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   17.866300] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   17.866337] ehci_hcd 0000:00:13.5: debug port 1
[   17.866355] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[   17.866365] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.866420] usb usb6: configuration #1 chosen from 1 choice
[   17.866441] hub 6-0:1.0: USB hub found
[   17.866448] hub 6-0:1.0: 10 ports detected
[   17.974089] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.974122] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
[   17.974292] eth0: RTL8169sc/8110sc at 0xf8852000, 00:19:21:21:21:b5, IRQ 20
[   24.297961] r8169: eth0: link up
[   25.547149] NET: Registered protocol family 17
[   25.727492] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.745184] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.577919] Linux agpgart interface v0.102 (c) Dave Jones
[   26.600445] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[   26.600457] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   26.600468] SB600_PATA: chipset revision 0
[   26.600471] SB600_PATA: not 100% native mode: will probe irqs later
[   26.600479]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
[   26.600491] Probing IDE interface ide0...
[   26.915535] input: PC Speaker as /class/input/input2
[   26.975222] parport: PnPBIOS parport detected.
[   26.975280] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   27.533011] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input3
[   27.633950] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[   27.693899] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.709976] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   27.913135] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   28.099684] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   28.099692] Uniform CD-ROM driver Revision: 3.20
[   28.341501] fuse init (API version 7.8)
[   28.369519] lp0: using parport0 (interrupt-driven).
[   28.518437] Adding 289160k swap on /dev/disk/by-uuid/c4aa3413-6241-4c6d-bd41-1e16d20f5072.  Priority:-1 extents:1 across:289160k
[   28.660269] EXT3 FS on sda2, internal journal
[  114.861443] kjournald starting.  Commit interval 5 seconds
[  114.861452] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[  114.861644] EXT3 FS on sda4, internal journal
[  114.861649] EXT3-fs: mounted filesystem with ordered data mode.
[  114.897829] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  114.960658] NTFS volume version 3.1.
[  120.120135] Using specific hotkey driver
[  120.207306] input: Power Button (FF) as /class/input/input4
[  120.211842] ACPI: Power Button (FF) [PWRF]
[  120.243860] input: Power Button (CM) as /class/input/input5
[  120.248396] ACPI: Power Button (CM) [PWRB]
[  120.378151] ibm_acpi: ec object not found
[  120.434400] No dock devices found.
[  120.582128] pcc_acpi: loading...
[  120.786463] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[  120.786496] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[  120.786499] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[  125.235043] ppdev: user-space parallel port driver
[  126.174086] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  126.174092] apm: overridden by ACPI.
[  126.326470] Bluetooth: Core ver 2.11
[  126.326521] NET: Registered protocol family 31
[  126.326524] Bluetooth: HCI device and connection manager initialized
[  126.326528] Bluetooth: HCI socket layer initialized
[  126.361312] Bluetooth: L2CAP ver 2.8
[  126.361315] Bluetooth: L2CAP socket layer initialized
[  126.785152] Bluetooth: RFCOMM socket layer initialized
[  126.785165] Bluetooth: RFCOMM TTY layer initialized
[  126.785167] Bluetooth: RFCOMM ver 1.8
[  116.224000] Time: hpet clocksource has been installed.
[  124.524000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  758.324000] r8169: eth0: link up
[  770.172000] r8169: eth0: link up
[ 1626.548000] EXT3-fs error (device sda4): ext3_new_block: Allocating block in system zone - blocks from 2097152, length 1
[ 2983.092000] EXT3-fs error (device sda4): ext3_free_blocks: Freeing blocks in system zones - Block = 4587704, count = 1

```

---

