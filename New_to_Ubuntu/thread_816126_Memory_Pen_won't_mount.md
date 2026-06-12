---
title: "Memory Pen won't mount"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by takuhii on 2008-06-02
Ever since the recent upgrade, my memory pen won't mount, it worked before, but now it just comes up with some random error, any advice on getting a memory pen to mount successfully would be great...

I am using Hardy Heron (8.04)

---

### Post by Quintin Riis on 2008-06-03
Please run dmesg, look at the output, plug your pen in, run dmesg again, and look at the output.

Then paste here the relevant info.

---

### Post by takuhii on 2008-06-03
My Memory stick/pen is a Kingston Data traveller, the output of DMESG is below;

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-17-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 14:31:33 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f55f0
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6D00 checksum 0
[    0.000000] ACPI: RSDP 000F6D00, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 3474 (r1 AWARD  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF6540, 0068 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=81bc3e02-39f2-4beb-912b-9c68cdbc866a ro splash quiet rootflags=data=writeback
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2799.735 MHz processor.
[   11.483903] Console: colour VGA+ 80x25
[   11.483908] console [tty0] enabled
[   11.484263] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.484580] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.495566] Memory: 507652k/524224k available (2176k kernel code, 15956k reserved, 1007k data, 368k init, 0k highmem)
[   11.495575] virtual kernel memory layout:
[   11.495576]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   11.495577]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.495578]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   11.495579]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   11.495580]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   11.495581]       .data : 0xc0320134 - 0xc041bdc4   (1007 kB)
[   11.495582]       .text : 0xc0100000 - 0xc0320134   (2176 kB)
[   11.495585] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.495625] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   11.575486] Calibrating delay using timer specific routine.. 5604.46 BogoMIPS (lpj=11208928)
[   11.575512] Security Framework initialized
[   11.575519] SELinux:  Disabled at boot.
[   11.575532] AppArmor: AppArmor initialized
[   11.575537] Failure registering capabilities with primary security module.
[   11.575545] Mount-cache hash table entries: 512
[   11.575681] Initializing cgroup subsys ns
[   11.575685] Initializing cgroup subsys cpuacct
[   11.575697] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   11.575710] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   11.575713] CPU: L2 cache: 512K
[   11.575715] CPU: Hyper-Threading is disabled
[   11.575718] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   11.575731] Compat vDSO mapped to ffffe000.
[   11.575744] Checking 'hlt' instruction... OK.
[   11.591843] SMP alternatives: switching to UP code
[   11.593414] Freeing SMP alternatives: 11k freed
[   11.593553] Early unpacking initramfs... done
[   11.893656] ACPI: Core revision 20070126
[   11.893716] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.897037] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   11.897080] Total of 1 processors activated (5604.46 BogoMIPS).
[   11.897188] ENABLING IO-APIC IRQs
[   11.897367] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.042608] Brought up 1 CPUs
[   12.042632] CPU0 attaching sched-domain:
[   12.042635]  domain 0: span 01
[   12.042637]   groups: 01
[   12.042844] net_namespace: 64 bytes
[   12.042852] Booting paravirtualized kernel on bare hardware
[   12.043399] Time: 16:29:24  Date: 06/03/08
[   12.043431] NET: Registered protocol family 16
[   12.043658] EISA bus registered
[   12.043683] ACPI: bus type pci registered
[   12.085591] PCI: PCI BIOS revision 2.10 entry at 0xfbaa0, last bus=1
[   12.085594] PCI: Using configuration type 1
[   12.085596] Setting up standard PCI resources
[   12.093275] ACPI: EC: Look up EC in DSDT
[   12.095961] ACPI: Interpreter enabled
[   12.095964] ACPI: (supports S0 S1 S4 S5)
[   12.095978] ACPI: Using IOAPIC for interrupt routing
[   12.099590] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.099807] Enabling SiS 96x SMBus.
[   12.100586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.113825] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[   12.113918] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[   12.114006] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   12.114094] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[   12.114183] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[   12.114275] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[   12.114365] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   12.114462] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   12.114583] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.114618] pnp: PnP ACPI init
[   12.114627] ACPI: bus type pnp registered
[   12.116768] pnp: PnP ACPI: found 10 devices
[   12.116771] ACPI: ACPI bus type pnp unregistered
[   12.116776] PnPBIOS: Disabled by ACPI PNP
[   12.117035] PCI: Using ACPI for IRQ routing
[   12.117038] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.130428] NET: Registered protocol family 8
[   12.130431] NET: Registered protocol family 20
[   12.130512] AppArmor: AppArmor Filesystem Enabled
[   12.134374] Time: tsc clocksource has been installed.
[   12.142401] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   12.142405] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   12.142407] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   12.142410] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   12.142413] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[   12.142416] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   12.142418] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   12.142421] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[   12.142424] system 00:00: iomem range 0xffee0000-0xffefffff could not be reserved
[   12.142427] system 00:00: iomem range 0xfffe0000-0xfffeffff could not be reserved
[   12.142429] system 00:00: iomem range 0xfec00000-0xfecfffff could not be reserved
[   12.142432] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[   12.142440] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   12.142442] system 00:02: ioport range 0x294-0x297 has been reserved
[   12.172859] PCI: Bridge: 0000:00:01.0
[   12.172861]   IO window: disabled.
[   12.172869]   MEM window: ec000000-edffffff
[   12.172874]   PREFETCH window: e0000000-e7ffffff
[   12.172899] NET: Registered protocol family 2
[   12.210319] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   12.210561] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   12.210655] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   12.210751] TCP: Hash tables configured (established 16384 bind 16384)
[   12.210753] TCP reno registered
[   12.222357] checking if image is initramfs... it is
[   12.673298] Switched to high resolution mode on CPU 0
[   12.812671] Freeing initrd memory: 7316k freed
[   12.813336] audit: initializing netlink socket (disabled)
[   12.813355] audit(1212510564.216:1): initialized
[   12.815556] VFS: Disk quotas dquot_6.5.1
[   12.815645] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.815802] io scheduler noop registered
[   12.815804] io scheduler anticipatory registered
[   12.815806] io scheduler deadline registered
[   12.815818] io scheduler cfq registered (default)
[   12.896783] Boot video device is 0000:01:00.0
[   12.897086] isapnp: Scanning for PnP cards...
[   13.250292] isapnp: No Plug & Play device found
[   13.282908] Real Time Clock Driver v1.12ac
[   13.283016] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.283143] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.283993] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.284839] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.284913] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   13.285081] PNP: No PS/2 controller found. Probing ports directly.
[   13.285374] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.285380] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.292122] mice: PS/2 mouse device common for all mice
[   13.292252] EISA: Probing bus 0 at eisa.0
[   13.292260] Cannot allocate resource for EISA slot 1
[   13.292269] Cannot allocate resource for EISA slot 4
[   13.292284] EISA: Detected 0 cards.
[   13.292288] cpuidle: using governor ladder
[   13.292290] cpuidle: using governor menu
[   13.292392] NET: Registered protocol family 1
[   13.292422] Using IPI No-Shortcut mode
[   13.292461] registered taskstats version 1
[   13.292551]   Magic number: 12:845:488
[   13.292688] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   13.292690] EDD information not available.
[   13.293129] Freeing unused kernel memory: 368k freed
[   14.526764] fuse init (API version 7.9)
[   14.550337] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   14.550358] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   15.092443] SCSI subsystem initialized
[   15.156151] usbcore: registered new interface driver usbfs
[   15.156184] usbcore: registered new interface driver hub
[   15.168121] ACPI: PCI Interrupt 0000:00:02.3[B] -> GSI 17 (level, low) -> IRQ 16
[   15.219844] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[ef000000-ef0007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[   15.232259] libata version 3.00 loaded.
[   15.239591] usbcore: registered new device driver usb
[   15.258083] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   15.266005] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.289296] 8139cp 0000:00:0e.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   15.289303] 8139cp 0000:00:0e.0: Try the "8139too" driver instead.
[   15.291083] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17
[   15.291147] ACPI: PCI interrupt for device 0000:00:02.5 disabled
[   15.291185] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 18
[   15.291198] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   15.291553] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   15.291575] ohci_hcd 0000:00:03.0: irq 18, io mem 0xef001000
[   15.297944] 8139too Fast Ethernet driver 0.9.28
[   15.345782] usb usb1: configuration #1 chosen from 1 choice
[   15.345812] hub 1-0:1.0: USB hub found
[   15.345821] hub 1-0:1.0: 2 ports detected
[   15.353302] FDC 0 is a post-1991 82077
[   15.447560] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 19
[   15.447581] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   15.447608] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   15.447625] ohci_hcd 0000:00:03.1: irq 19, io mem 0xef002000
[   15.505436] usb usb2: configuration #1 chosen from 1 choice
[   15.505467] hub 2-0:1.0: USB hub found
[   15.505476] hub 2-0:1.0: 2 ports detected
[   15.607199] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 20
[   15.607219] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   15.607247] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   15.607263] ohci_hcd 0000:00:03.2: irq 20, io mem 0xef003000
[   15.665083] usb usb3: configuration #1 chosen from 1 choice
[   15.665112] hub 3-0:1.0: USB hub found
[   15.665121] hub 3-0:1.0: 2 ports detected
[   15.750782] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   15.766998] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 21
[   15.767015] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   15.767049] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   15.767088] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   15.767099] ehci_hcd 0000:00:03.3: irq 21, io mem 0xef004000
[   15.938409] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.938578] usb usb4: configuration #1 chosen from 1 choice
[   15.938608] hub 4-0:1.0: USB hub found
[   15.938616] hub 4-0:1.0: 6 ports detected
[   16.042714] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 18 (level, low) -> IRQ 22
[   16.043360] eth0: RealTek RTL8139 at 0xe800, 00:0c:76:63:a6:d5, IRQ 22
[   16.043363] eth0:  Identified 8139 chip type 'RTL-8101'
[   16.048289] pata_sis 0000:00:02.5: version 0.5.2
[   16.048329] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 17
[   16.048982] scsi0 : pata_sis
[   16.049678] scsi1 : pata_sis
[   16.050294] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
[   16.050297] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
[   16.253891] ata1.00: HPA unlocked: 313798656 -> 320173056, native 320173056
[   16.253899] ata1.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   16.253902] ata1.00: 320173056 sectors, multi 16: LBA48 
[   16.270049] ata1.00: configured for UDMA/133
[   16.333536] usb 1-1: device not accepting address 2, error -62
[   16.557186] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000010dc00366577]
[   16.589254] ata2.00: ATAPI: SONY    DVD RW DW-Q28A, KYS1, max UDMA/66
[   16.589271] ata2.00: limited to UDMA/33 due to 40-wire cable
[   16.760881] ata2.00: configured for UDMA/33
[   16.761033] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[   16.762195] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DW-Q28A   KYS1 PQ: 0 ANSI: 5
[   16.772727] Driver 'sd' needs updating - please use bus_type methods
[   16.772831] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   16.772846] sd 0:0:0:0: [sda] Write Protect is off
[   16.772849] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.772871] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.772928] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   16.772940] sd 0:0:0:0: [sda] Write Protect is off
[   16.772943] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.772962] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.772967]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.792583]  sda1 sda2 < sda5 >
[   16.814410] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.821031] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.821057] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   16.825257] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   16.825265] Uniform CD-ROM driver Revision: 3.20
[   16.825330] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   17.037223] Attempting manual resume
[   17.037228] swsusp: Resume From Partition 8:5
[   17.037230] PM: Checking swsusp image.
[   17.037558] PM: Resume from disk failed.
[   17.072301] kjournald starting.  Commit interval 5 seconds
[   17.072320] EXT3-fs: mounted filesystem with writeback data mode.
[   17.738582] usb 1-1: new low speed USB device using ohci_hcd and address 4
[   17.953227] usb 1-1: configuration #1 chosen from 1 choice
[   18.257487] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   18.482111] usb 3-1: configuration #1 chosen from 1 choice
[   18.788357] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   19.004012] usb 2-2: configuration #1 chosen from 1 choice
[   26.193725] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.258479] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   27.023030] Linux agpgart interface v0.102
[   27.076426] agpgart: Detected SiS chipset - id:1617
[   27.080591] agpgart: AGP aperture is 64M @ 0xe8000000
[   27.130832] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.202762] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.407764] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x10c0
[   27.530846] input: Power Button (FF) as /devices/virtual/input/input1
[   27.541928] ACPI: Power Button (FF) [PWRF]
[   27.542073] input: Power Button (CM) as /devices/virtual/input/input2
[   27.557878] ACPI: Power Button (CM) [PWRB]
[   28.403749] nvidia: module license 'NVIDIA' taints kernel.
[   29.183402] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   29.512525] usbcore: registered new interface driver hiddev
[   29.522290] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:03.0/usb1/1-1/1-1:1.0/input/input3
[   29.533981] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:03.0-1
[   29.545092] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:03.0/usb1/1-1/1-1:1.1/input/input4
[   29.573916] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:03.0-1
[   29.573945] usbcore: registered new interface driver usbhid
[   29.573949] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.596041] usbcore: registered new interface driver libusual
[   29.633718] Initializing USB Mass Storage driver...
[   29.673711] scsi2 : SCSI emulation for USB Mass Storage devices
[   29.678757] usb-storage: device found at 2
[   29.678762] usb-storage: waiting for device to settle before scanning
[   29.684316] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB202
[   29.695010] scsi3 : SCSI emulation for USB Mass Storage devices
[   29.703132] usbcore: registered new interface driver usb-storage
[   29.703140] USB Mass Storage support registered.
[   29.703256] usbcore: registered new interface driver usblp
[   29.703712] usb-storage: device found at 2
[   29.703714] usb-storage: waiting for device to settle before scanning
[   29.781540] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   30.008731] intel8x0_measure_ac97_clock: measured 55459 usecs
[   30.008736] intel8x0: clocking to 48000
[   30.335252] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   30.335571] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   30.368727] parport_pc 00:09: reported by Plug and Play ACPI
[   30.368836] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   32.059642] lp0: using parport0 (interrupt-driven).
[   32.147508] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   32.707879] EXT3 FS on sda1, internal journal
[   34.217828] No dock devices found.
[   34.668786] usb-storage: device scan complete
[   34.680670] scsi 2:0:0:0: Direct-Access     HP       photosmart 7600  1.00 PQ: 0 ANSI: 2
[   34.700659] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   34.700712] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   34.744765] usb-storage: device scan complete
[   34.840349] scsi scan: INQUIRY result too short (5), using 36
[   34.840359] scsi 3:0:0:0: Direct-Access     OEI-USB  CompactFlash     1.02 PQ: 0 ANSI: 0
[   35.462986] scsi scan: INQUIRY result too short (5), using 36
[   35.462997] scsi 3:0:0:1: Direct-Access     OEI-USB  SM/MS/SD         1.02 PQ: 0 ANSI: 0
[   35.482006] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[   35.482063] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   35.493000] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[   35.493058] sd 3:0:0:1: Attached scsi generic sg4 type 0
[   36.140209] ppdev: user-space parallel port driver
[   36.354585] audit(1212510588.437:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4910 profile="/usr/sbin/cupsd" namespace="default"
[   36.396974] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   36.396981] apm: overridden by ACPI.
[   40.686826] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   40.958107] Bluetooth: Core ver 2.11
[   40.958919] NET: Registered protocol family 31
[   40.958924] Bluetooth: HCI device and connection manager initialized
[   40.958929] Bluetooth: HCI socket layer initialized
[   41.000547] Bluetooth: L2CAP ver 2.9
[   41.000553] Bluetooth: L2CAP socket layer initialized
[   41.050877] Bluetooth: RFCOMM socket layer initialized
[   41.051155] Bluetooth: RFCOMM TTY layer initialized
[   41.051160] Bluetooth: RFCOMM ver 1.8
[   43.896216] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   43.896239] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   43.896288] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   45.033144] NET: Registered protocol family 17
[   56.832049] NET: Registered protocol family 10
[   56.832723] lo: Disabled Privacy Extensions
[   67.186303] eth0: no IPv6 routers present
[   80.047191] eth0: no IPv6 routers present
[  134.185045] usb 4-4: new high speed USB device using ehci_hcd and address 5
[  134.319774] usb 4-4: configuration #1 chosen from 1 choice
[  134.337575] scsi4 : SCSI emulation for USB Mass Storage devices
[  134.341085] usb-storage: device found at 5
[  134.341091] usb-storage: waiting for device to settle before scanning
[  139.338170] usb-storage: device scan complete
[  139.338904] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  139.342007] sd 4:0:0:0: [sde] 3901952 512-byte hardware sectors (1998 MB)
[  139.342867] sd 4:0:0:0: [sde] Write Protect is off
[  139.342872] sd 4:0:0:0: [sde] Mode Sense: 03 00 00 00
[  139.342874] sd 4:0:0:0: [sde] Assuming drive cache: write through
[  139.345738] sd 4:0:0:0: [sde] 3901952 512-byte hardware sectors (1998 MB)
[  139.346487] sd 4:0:0:0: [sde] Write Protect is off
[  139.346492] sd 4:0:0:0: [sde] Mode Sense: 03 00 00 00
[  139.346495] sd 4:0:0:0: [sde] Assuming drive cache: write through
[  139.346503]  sde: unknown partition table
[  139.348924] sd 4:0:0:0: [sde] Attached SCSI removable disk
[  139.348978] sd 4:0:0:0: Attached scsi generic sg5 type 0
[  181.684035] usb 4-4: USB disconnect, address 5
[  214.060624] usb 4-4: new high speed USB device using ehci_hcd and address 6
[  214.195272] usb 4-4: configuration #1 chosen from 1 choice
[  214.211000] scsi5 : SCSI emulation for USB Mass Storage devices
[  214.216453] usb-storage: device found at 6
[  214.216459] usb-storage: waiting for device to settle before scanning
[  219.206185] usb-storage: device scan complete
[  219.206799] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  219.218147] sd 5:0:0:0: [sde] 3901952 512-byte hardware sectors (1998 MB)
[  219.219140] sd 5:0:0:0: [sde] Write Protect is off
[  219.219148] sd 5:0:0:0: [sde] Mode Sense: 03 00 00 00
[  219.219150] sd 5:0:0:0: [sde] Assuming drive cache: write through
[  219.222242] sd 5:0:0:0: [sde] 3901952 512-byte hardware sectors (1998 MB)
[  219.223112] sd 5:0:0:0: [sde] Write Protect is off
[  219.223118] sd 5:0:0:0: [sde] Mode Sense: 03 00 00 00
[  219.223121] sd 5:0:0:0: [sde] Assuming drive cache: write through
[  219.223129]  sde: unknown partition table
[  219.225547] sd 5:0:0:0: [sde] Attached SCSI removable disk
[  219.225611] sd 5:0:0:0: Attached scsi generic sg5 type 0

---

### Post by spiderbatdad on 2008-06-03
```
usb-storage: device scan complete
[ 139.338904] scsi 4:0:0:0: Direct-Access Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 139.342007] sd 4:0:0:0: [sde] 3901952 512-byte hardware sectors (1998 MB)
[ 139.342867] sd 4:0:0:0: [sde] Write Protect is off
[ 139.342872] sd 4:0:0:0: [sde] Mode Sense: 03 00 00 00
[ 139.342874] sd 4:0:0:0: [sde] Assuming drive cache: write through
[ 139.345738] sd 4:0:0:0: [sde] 3901952 512-byte hardware sectors (1998 MB)
[ 139.346487] sd 4:0:0:0: [sde] Write Protect is off
[ 139.346492] sd 4:0:0:0: [sde] Mode Sense: 03 00 00 00
[ 139.346495] sd 4:0:0:0: [sde] Assuming drive cache: write through
[ 139.346503] sde:** unknown partition table**
```

Take a look at  sudo fdisk -l

You could also try running sudo apt-get update && sudo apt-get upgrade
If that fails, perhaps check to see if usbmount from synaptic will help..

---

### Post by GoodPanos on 2008-06-03
I am experiencing the same problem; almost.  But I am not sure mine happened after the upgrade.  It just happened all of a sudden.

Now I have to unplug the USB pen, plug it back in and then after 5-7 minutes it will mount :confused:

I am confused as to what is going on here.  I installed usbmount which I shouldn't have to, but still no change.

---

### Post by takuhii on 2008-06-04
sudo fdisk -l produces this...

Disk /dev/sde: 1997 MB, 1997799424 bytes
62 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   ?      202429      499388   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(202428, 43, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(499387, 30, 51)
Partition 1 does not end on cylinder boundary.
/dev/sde2   ?       43884      547534   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43883, 52, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(547533, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sde3   ?      486442      990091   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(486441, 36, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(990090, 59, 39)
Partition 3 does not end on cylinder boundary.
/dev/sde4   ?      750698      750712       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(750697, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(750711, 57, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


ALSO, when I plug the memory pen/stick in, I get this popup
CANNOT MOUNT VOLUME.
Invalid mount option when attempting to mount the volume.

Using GParted to "re-format" the pen causes an error, but only with FAT drives (16 and 32). It's almost as though FAT interaction is disabled. All other formats seem fine EXT3, REISERFS, etc. the drive has to be compatible with Windows though (NTFS support is disabled for some reason (NTFS-3G is installed)).

The FAT formatted drive works find in Windows...

---

### Post by takuhii on 2008-06-05
anyone?

---

### Post by novatotal on 2008-06-24
could you run fdisk-l one more time? but just like that, with out anything else:
sudo fdisk-l and post it? with your pendrive attached ofcourse, had a problem like yours and did work it out, but need to chek the whole out put of fdisk-l to be sure.
if it is the exact same problem, you need to edit fstab and add three lines of code, wich I did and my pendrives all mount like magic.
Obviously the UUID would not be the same in your machine, but here they are so you can try it.

add this to the end of fstab

# Mount usb
UUID= 0x000a745d
#/dev/sdf1 /media/usb vfat users,exec,noauto,noatime,rw 0 0

now the last line must have 5 spaces beetwen sdfl and /media in order to work


also, don't know if it's related but, afterwards my grub got messed up so I had to install startup manager and fix it.

before doing anything, you could copy and paste the grub to Oo and then compare it before restarting your machine

---

