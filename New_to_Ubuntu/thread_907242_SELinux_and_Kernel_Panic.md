---
title: "SELinux and Kernel Panic"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Shippou on 2008-09-01
Hello...

I recently installed SELinux because I heard and read that it is a great program in order to increase security of a Linux box (this is currently used by Fedora 9).

So the installation went smoothly, until it asked me if I want to keep or replace menu.lst. I said I will replace it. The installation requires a reboot. When I rebooted in normal mode, it only showed CLI after a few seconds, with (initramfs) (if I'm not mistaken with the spelling) showing. When I type exit, the kernel panics.

(For those who do not know, Kernel panic is the alternative of BSoD in Linux and Mac systems.)

I was able to circumvent this by booting using the recovery mode.

Does anyone know how to fix this? 

And here is my kernel log for yesterday:
```

Aug 31 07:27:45 Shippou kernel: [19592.756510] r8169: eth0: link up
Aug 31 07:28:18 Shippou kernel: [19626.358012] r8169: eth0: link down
Aug 31 07:28:37 Shippou kernel: [19644.758045] r8169: eth0: link up
Aug 31 07:28:49 Shippou kernel: [19656.752545] r8169: eth0: link down
Aug 31 07:28:50 Shippou kernel: [19658.376289] r8169: eth0: link up
Aug 31 07:28:52 Shippou kernel: [19659.986512] r8169: eth0: link down
Aug 31 07:28:54 Shippou kernel: [19661.657683] r8169: eth0: link up
Aug 31 07:28:56 Shippou kernel: [19663.473573] r8169: eth0: link down
Aug 31 07:28:58 Shippou kernel: [19665.683125] r8169: eth0: link up
Aug 31 07:28:58 Shippou kernel: [19665.868399] r8169: eth0: link down
Aug 31 07:29:02 Shippou kernel: [19670.002701] r8169: eth0: link up
Aug 31 07:29:02 Shippou kernel: [19670.095331] r8169: eth0: link down
Aug 31 07:29:18 Shippou kernel: [19685.520637] r8169: eth0: link up
Aug 31 07:29:44 Shippou kernel: [19711.840330] r8169: eth0: link down
Aug 31 07:29:47 Shippou kernel: [19714.833247] r8169: eth0: link up
Aug 31 07:30:34 Shippou kernel: [10961.723367] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 31 07:30:49 Shippou kernel: [10977.107524] UDF-fs: No VRS found
Aug 31 07:30:49 Shippou kernel: [10977.195879] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 31 07:30:49 Shippou kernel: [10977.196995] ISOFS: changing to secondary root
Aug 31 07:32:57 Shippou kernel: [19948.435786] r8169: eth0: link up
Aug 31 07:33:45 Shippou kernel: [20006.351622] r8169: eth0: link up
Aug 31 12:26:46 Shippou kernel: [27684.040348] r8169: eth0: link down
Aug 31 12:36:23 Shippou kernel: [28246.630749] r8169: eth0: link up
Aug 31 12:36:26 Shippou kernel: [28249.408980] r8169: eth0: link down
Aug 31 12:36:27 Shippou kernel: [28251.058165] r8169: eth0: link up
Aug 31 12:36:28 Shippou kernel: [28251.884466] r8169: eth0: link down
Aug 31 12:36:30 Shippou kernel: [28253.580999] r8169: eth0: link up
Aug 31 12:36:31 Shippou kernel: [50937.109539] r8169: eth0: link down
Aug 31 12:36:32 Shippou kernel: [28255.458062] r8169: eth0: link up
Aug 31 12:36:36 Shippou kernel: [28259.199501] r8169: eth0: link down
Aug 31 12:36:44 Shippou kernel: [28267.227535] r8169: eth0: link up
Aug 31 12:36:44 Shippou kernel: [28267.481458] r8169: eth0: link down
Aug 31 12:36:47 Shippou kernel: [28270.143161] r8169: eth0: link up
Aug 31 12:36:52 Shippou kernel: [28275.511699] r8169: eth0: link down
Aug 31 12:36:56 Shippou kernel: [28279.573807] r8169: eth0: link up
Aug 31 12:36:56 Shippou kernel: [28279.654516] r8169: eth0: link down
Aug 31 12:36:59 Shippou kernel: [28282.056649] r8169: eth0: link up
Aug 31 12:37:00 Shippou kernel: [28282.889820] r8169: eth0: link down
Aug 31 12:37:01 Shippou kernel: [28284.757111] r8169: eth0: link up
Aug 31 12:37:08 Shippou kernel: [51003.679662] r8169: eth0: link down
Aug 31 12:37:13 Shippou kernel: [28295.394799] r8169: eth0: link up
Aug 31 12:37:24 Shippou kernel: [28306.252797] r8169: eth0: link down
Aug 31 12:37:26 Shippou kernel: [28307.999627] r8169: eth0: link up
Aug 31 12:37:27 Shippou kernel: [28308.872543] r8169: eth0: link down
Aug 31 12:37:28 Shippou kernel: [51038.654467] r8169: eth0: link up
Aug 31 12:37:31 Shippou kernel: [28312.031656] r8169: eth0: link down
Aug 31 12:37:33 Shippou kernel: [28314.162198] r8169: eth0: link up
Aug 31 12:37:34 Shippou kernel: [28314.989482] r8169: eth0: link down
Aug 31 12:37:41 Shippou kernel: [51056.702737] r8169: eth0: link up
Aug 31 12:37:41 Shippou kernel: [28321.362695] r8169: eth0: link down
Aug 31 14:35:16 Shippou kernel: [35339.581508] nautilus[29917]: segfault at e1000018 eip b76c62d6 esp bfe30810 error 5
Aug 31 14:35:21 Shippou kernel: [63718.885172] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 31 17:30:15 Shippou kernel: Inspecting /boot/System.map-2.6.24-16-generic
Aug 31 17:30:15 Shippou kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Aug 31 17:30:15 Shippou kernel: Symbols match kernel version 2.6.24.
Aug 31 17:30:15 Shippou kernel: Loaded 15856 symbols from 78 modules.
Aug 31 17:30:15 Shippou kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Aug 31 17:30:15 Shippou kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097fe0000 (usable)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe0000 - 0000000097fe3000 (ACPI NVS)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 0000000097fe3000 - 0000000097ff0000 (ACPI data)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 0000000097ff0000 - 0000000098000000 (reserved)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 31 17:30:15 Shippou kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 31 17:30:15 Shippou kernel: [    0.000000] 1535MB HIGHMEM available.
Aug 31 17:30:15 Shippou kernel: [    0.000000] 896MB LOWMEM available.
Aug 31 17:30:15 Shippou kernel: [    0.000000] found SMP MP-table at 000f3c80
Aug 31 17:30:15 Shippou kernel: [    0.000000] Entering add_active_range(0, 0, 622560) 0 entries of 256 used
Aug 31 17:30:15 Shippou kernel: [    0.000000] Zone PFN ranges:
Aug 31 17:30:15 Shippou kernel: [    0.000000]   DMA             0 ->     4096
Aug 31 17:30:15 Shippou kernel: [    0.000000]   Normal       4096 ->   229376
Aug 31 17:30:15 Shippou kernel: [    0.000000]   HighMem    229376 ->   622560
Aug 31 17:30:15 Shippou kernel: [    0.000000] Movable zone start PFN for each node
Aug 31 17:30:15 Shippou kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 31 17:30:15 Shippou kernel: [    0.000000]     0:        0 ->   622560
Aug 31 17:30:15 Shippou kernel: [    0.000000] On node 0 totalpages: 622560
Aug 31 17:30:15 Shippou kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 31 17:30:15 Shippou kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 31 17:30:15 Shippou kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 31 17:30:15 Shippou kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 31 17:30:15 Shippou kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 31 17:30:15 Shippou kernel: [    0.000000]   HighMem zone: 3071 pages used for memmap
Aug 31 17:30:15 Shippou kernel: [    0.000000]   HighMem zone: 390113 pages, LIFO batch:31
Aug 31 17:30:15 Shippou kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 31 17:30:15 Shippou kernel: [    0.000000] DMI 2.5 present.
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7B80 checksum 0
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: RSDP 000F7B80, 0024 (r2 RS690 )
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: RSDT 97FE3040, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: FACP 97FE30C0, 0074 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: DSDT 97FE3180, 4B0B (r1 RS690  AWRDACPI     1000 MSFT  3000000)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: FACS 97FE0000, 0040
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: SSDT 97FE7DC0, 00D3 (r1 PTLTD  POWERNOW        1  LTP        1)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: HPET 97FE7F00, 0038 (r1 RS690  AWRDACPI 42302E31 AWRD       98)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: MCFG 97FE7F80, 003C (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: APIC 97FE7D00, 0068 (r1 RS690  AWRDACPI 42302E31 AWRD        0)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 31 17:30:15 Shippou kernel: [    0.000000] Processor #0 15:15 APIC version 16
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 31 17:30:15 Shippou kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 31 17:30:15 Shippou kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 31 17:30:15 Shippou kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Aug 31 17:30:15 Shippou kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 31 17:30:15 Shippou kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 98000000:48000000)
Aug 31 17:30:15 Shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 31 17:30:15 Shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 31 17:30:15 Shippou kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 31 17:30:15 Shippou kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 617697
Aug 31 17:30:15 Shippou kernel: [    0.000000] Kernel command line: root=UUID=29666169-1fdf-40ff-9495-00fb9010ea09 ro single
Aug 31 17:30:15 Shippou kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 31 17:30:15 Shippou kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 31 17:30:15 Shippou kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 31 17:30:15 Shippou kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 31 17:30:15 Shippou kernel: [    0.000000] Initializing CPU#0
Aug 31 17:30:15 Shippou kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 31 17:30:15 Shippou kernel: [    0.000000] Detected 1799.874 MHz processor.
Aug 31 17:30:15 Shippou kernel: [   11.541726] Console: colour VGA+ 80x25
Aug 31 17:30:15 Shippou kernel: [   11.541729] console [tty0] enabled
Aug 31 17:30:15 Shippou kernel: [   11.544010] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 31 17:30:15 Shippou kernel: [   11.544471] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 31 17:30:15 Shippou kernel: [   11.662869] Memory: 2456460k/2490240k available (2157k kernel code, 32544k reserved, 998k data, 364k init, 1572736k highmem)
Aug 31 17:30:15 Shippou kernel: [   11.662924] virtual kernel memory layout:
Aug 31 17:30:15 Shippou kernel: [   11.662925]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 31 17:30:15 Shippou kernel: [   11.662927]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 31 17:30:15 Shippou kernel: [   11.662928]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 31 17:30:15 Shippou kernel: [   11.662929]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 31 17:30:15 Shippou kernel: [   11.662930]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Aug 31 17:30:15 Shippou kernel: [   11.662931]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Aug 31 17:30:15 Shippou kernel: [   11.662933]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Aug 31 17:30:15 Shippou kernel: [   11.663212] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 31 17:30:15 Shippou kernel: [   11.663319] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug 31 17:30:15 Shippou kernel: [   11.663839] hpet clockevent registered
Aug 31 17:30:15 Shippou kernel: [   11.743942] Calibrating delay using timer specific routine.. 3709.47 BogoMIPS (lpj=7418958)
Aug 31 17:30:15 Shippou kernel: [   11.744046] Security Framework initialized
Aug 31 17:30:15 Shippou kernel: [   11.744085] SELinux:  Disabled at boot.
Aug 31 17:30:15 Shippou kernel: [   11.744133] AppArmor: AppArmor initialized
Aug 31 17:30:15 Shippou kernel: [   11.744171] Failure registering capabilities with primary security module.
Aug 31 17:30:15 Shippou kernel: [   11.744214] Mount-cache hash table entries: 512
Aug 31 17:30:15 Shippou kernel: [   11.744356] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d 00000000
Aug 31 17:30:15 Shippou kernel: [   11.744364] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Aug 31 17:30:15 Shippou kernel: [   11.744402] CPU: L2 Cache: 512K (64 bytes/line)
Aug 31 17:30:15 Shippou kernel: [   11.744439] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001d 00000000
Aug 31 17:30:15 Shippou kernel: [   11.744447] Compat vDSO mapped to ffffe000.
Aug 31 17:30:15 Shippou kernel: [   11.744491] Checking 'hlt' instruction... OK.
Aug 31 17:30:15 Shippou kernel: [   11.760210] SMP alternatives: switching to UP code
Aug 31 17:30:15 Shippou kernel: [   11.761292] Freeing SMP alternatives: 11k freed
Aug 31 17:30:15 Shippou kernel: [   11.761444] Early unpacking initramfs... done
Aug 31 17:30:15 Shippou kernel: [   12.150869] ACPI: Core revision 20070126
Aug 31 17:30:15 Shippou kernel: [   12.150959] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 31 17:30:15 Shippou kernel: [   12.159095] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
Aug 31 17:30:15 Shippou kernel: [   12.159212] Total of 1 processors activated (3709.47 BogoMIPS).
Aug 31 17:30:15 Shippou kernel: [   12.159536] ENABLING IO-APIC IRQs
Aug 31 17:30:15 Shippou kernel: [   12.159792] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 31 17:30:15 Shippou kernel: [   12.306797] Brought up 1 CPUs
Aug 31 17:30:15 Shippou kernel: [   12.306879] CPU0 attaching sched-domain:
Aug 31 17:30:15 Shippou kernel: [   12.306881]  domain 0: span 01
Aug 31 17:30:15 Shippou kernel: [   12.306883]   groups: 01
Aug 31 17:30:15 Shippou kernel: [   12.307039] net_namespace: 64 bytes
Aug 31 17:30:15 Shippou kernel: [   12.307078] Booting paravirtualized kernel on bare hardware
Aug 31 17:30:15 Shippou kernel: [   12.307565] Time: 17:29:15  Date: 08/31/08
Aug 31 17:30:15 Shippou kernel: [   12.307622] NET: Registered protocol family 16
Aug 31 17:30:15 Shippou kernel: [   12.307813] EISA bus registered
Aug 31 17:30:15 Shippou kernel: [   12.307851] ACPI: bus type pci registered
Aug 31 17:30:15 Shippou kernel: [   12.309037] PCI: PCI BIOS revision 3.00 entry at 0xfa020, last bus=2
Aug 31 17:30:15 Shippou kernel: [   12.309074] PCI: Using configuration type 1
Aug 31 17:30:15 Shippou kernel: [   12.309109] Setting up standard PCI resources
Aug 31 17:30:15 Shippou kernel: [   12.312549] ACPI: EC: Look up EC in DSDT
Aug 31 17:30:15 Shippou kernel: [   12.317586] ACPI: Interpreter enabled
Aug 31 17:30:15 Shippou kernel: [   12.317630] ACPI: (supports S0 S3 S4 S5)
Aug 31 17:30:15 Shippou kernel: [   12.317797] ACPI: Using IOAPIC for interrupt routing
Aug 31 17:30:15 Shippou kernel: [   12.322640] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 31 17:30:15 Shippou kernel: [   12.322832] pci 0000:00:12.0: set SATA to AHCI mode
Aug 31 17:30:15 Shippou kernel: [   12.323658] PCI: Transparent bridge - 0000:00:14.4
Aug 31 17:30:15 Shippou kernel: [   12.323715] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 31 17:30:15 Shippou kernel: [   12.323926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Aug 31 17:30:15 Shippou kernel: [   12.324051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Aug 31 17:30:15 Shippou kernel: [   12.343351] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.343818] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.344282] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.344746] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.345210] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.345674] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.346138] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.346602] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Aug 31 17:30:15 Shippou kernel: [   12.347079] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 31 17:30:15 Shippou kernel: [   12.347138] pnp: PnP ACPI init
Aug 31 17:30:15 Shippou kernel: [   12.347178] ACPI: bus type pnp registered
Aug 31 17:30:15 Shippou kernel: [   12.350003] pnp: PnP ACPI: found 14 devices
Aug 31 17:30:15 Shippou kernel: [   12.350039] ACPI: ACPI bus type pnp unregistered
Aug 31 17:30:15 Shippou kernel: [   12.350076] PnPBIOS: Disabled by ACPI PNP
Aug 31 17:30:15 Shippou kernel: [   12.350288] PCI: Using ACPI for IRQ routing
Aug 31 17:30:15 Shippou kernel: [   12.350325] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 31 17:30:15 Shippou kernel: [   12.402621] NET: Registered protocol family 8
Aug 31 17:30:15 Shippou kernel: [   12.402657] NET: Registered protocol family 20
Aug 31 17:30:15 Shippou kernel: [   12.402722] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 31 17:30:15 Shippou kernel: [   12.402909] hpet0: 4 32-bit timers, 14318180 Hz
Aug 31 17:30:15 Shippou kernel: [   12.403984] AppArmor: AppArmor Filesystem Enabled
Aug 31 17:30:15 Shippou kernel: [   12.406589] Time: tsc clocksource has been installed.
Aug 31 17:30:15 Shippou kernel: [   12.406636] Switched to high resolution mode on CPU 0
Aug 31 17:30:15 Shippou kernel: [   12.414569] system 00:01: ioport range 0x4100-0x411f has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414607] system 00:01: ioport range 0x228-0x22f has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414645] system 00:01: ioport range 0x40b-0x40b has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414682] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414720] system 00:01: ioport range 0xc00-0xc01 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414758] system 00:01: ioport range 0xc14-0xc14 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414795] system 00:01: ioport range 0xc50-0xc52 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414832] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414873] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414911] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414948] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.414985] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415023] system 00:01: ioport range 0x4000-0x40fe has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415061] system 00:01: ioport range 0x4210-0x4217 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415098] system 00:01: ioport range 0xb10-0xb1f has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415140] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415177] system 00:07: ioport range 0x220-0x225 has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415214] system 00:07: ioport range 0xb00-0xb0f has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415256] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415300] system 00:0d: iomem range 0xf0000-0xfffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415338] system 00:0d: iomem range 0xfed00000-0xfed000ff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415379] system 00:0d: iomem range 0x97fe0000-0x97ffffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415420] system 00:0d: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415461] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415499] system 00:0d: iomem range 0x100000-0x97fdffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415540] system 00:0d: iomem range 0x98000000-0x9fffffff has been reserved
Aug 31 17:30:15 Shippou kernel: [   12.415578] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415619] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.415660] system 00:0d: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 31 17:30:15 Shippou kernel: [   12.445984] PCI: Bridge: 0000:00:01.0
Aug 31 17:30:15 Shippou kernel: [   12.446772]   IO window: e000-efff
Aug 31 17:30:15 Shippou kernel: [   12.446809]   MEM window: fdd00000-fdefffff
Aug 31 17:30:15 Shippou kernel: [   12.446845]   PREFETCH window: d8000000-dfffffff
Aug 31 17:30:15 Shippou kernel: [   12.446884] PCI: Bridge: 0000:00:14.4
Aug 31 17:30:15 Shippou kernel: [   12.446920]   IO window: d000-dfff
Aug 31 17:30:15 Shippou kernel: [   12.446958]   MEM window: fdc00000-fdcfffff
Aug 31 17:30:15 Shippou kernel: [   12.446996]   PREFETCH window: fdf00000-fdffffff
Aug 31 17:30:15 Shippou kernel: [   12.447055] NET: Registered protocol family 2
Aug 31 17:30:15 Shippou kernel: [   12.486501] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 31 17:30:15 Shippou kernel: [   12.486827] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 31 17:30:15 Shippou kernel: [   12.487823] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 31 17:30:15 Shippou kernel: [   12.488367] TCP: Hash tables configured (established 131072 bind 65536)
Aug 31 17:30:15 Shippou kernel: [   12.488405] TCP reno registered
Aug 31 17:30:15 Shippou kernel: [   12.498543] checking if image is initramfs... it is
Aug 31 17:30:15 Shippou kernel: [   13.191957] Freeing initrd memory: 8158k freed
Aug 31 17:30:15 Shippou kernel: [   13.192528] audit: initializing netlink socket (disabled)
Aug 31 17:30:15 Shippou kernel: [   13.192576] audit(1220203756.420:1): initialized
Aug 31 17:30:15 Shippou kernel: [   13.192776] highmem bounce pool size: 64 pages
Aug 31 17:30:15 Shippou kernel: [   13.194368] VFS: Disk quotas dquot_6.5.1
Aug 31 17:30:15 Shippou kernel: [   13.194469] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 31 17:30:15 Shippou kernel: [   13.194643] io scheduler noop registered
Aug 31 17:30:15 Shippou kernel: [   13.194680] io scheduler anticipatory registered
Aug 31 17:30:15 Shippou kernel: [   13.194716] io scheduler deadline registered
Aug 31 17:30:15 Shippou kernel: [   13.194761] io scheduler cfq registered (default)
Aug 31 17:30:15 Shippou kernel: [   13.333046] Boot video device is 0000:01:05.0
Aug 31 17:30:15 Shippou kernel: [   13.333318] isapnp: Scanning for PnP cards...
Aug 31 17:30:15 Shippou kernel: [   13.697118] isapnp: No Plug & Play device found
Aug 31 17:30:15 Shippou kernel: [   13.721012] Real Time Clock Driver v1.12ac
Aug 31 17:30:15 Shippou kernel: [   13.721227] hpet_resources: 0xfed00000 is busy
Aug 31 17:30:15 Shippou kernel: [   13.721255] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 31 17:30:15 Shippou kernel: [   13.721429] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 31 17:30:15 Shippou kernel: [   13.722077] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug 31 17:30:15 Shippou kernel: [   13.722765] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 31 17:30:15 Shippou kernel: [   13.722872] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 31 17:30:15 Shippou kernel: [   13.722993] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 31 17:30:15 Shippou kernel: [   13.723032] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 31 17:30:15 Shippou kernel: [   13.723169] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 31 17:30:15 Shippou kernel: [   13.728626] mice: PS/2 mouse device common for all mice
Aug 31 17:30:15 Shippou kernel: [   13.728758] EISA: Probing bus 0 at eisa.0
Aug 31 17:30:15 Shippou kernel: [   13.728811] Cannot allocate resource for EISA slot 4
Aug 31 17:30:15 Shippou kernel: [   13.728862] EISA: Detected 0 cards.
Aug 31 17:30:15 Shippou kernel: [   13.728898] cpuidle: using governor ladder
Aug 31 17:30:15 Shippou kernel: [   13.728934] cpuidle: using governor menu
Aug 31 17:30:15 Shippou kernel: [   13.729051] NET: Registered protocol family 1
Aug 31 17:30:15 Shippou kernel: [   13.729110] Using IPI No-Shortcut mode
Aug 31 17:30:15 Shippou kernel: [   13.729173] registered taskstats version 1
Aug 31 17:30:15 Shippou kernel: [   13.729303]   Magic number: 4:73:493
Aug 31 17:30:15 Shippou kernel: [   13.729520] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 31 17:30:15 Shippou kernel: [   13.729556] EDD information not available.
Aug 31 17:30:15 Shippou kernel: [   13.729836] Freeing unused kernel memory: 364k freed
Aug 31 17:30:15 Shippou kernel: [   13.756338] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 31 17:30:15 Shippou kernel: [   13.930193] fuse init (API version 7.9)
Aug 31 17:30:15 Shippou kernel: [   13.945991] ACPI: Fan [FAN] (on)
Aug 31 17:30:15 Shippou kernel: [   13.952004] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 31 17:30:15 Shippou kernel: [   13.953386] ACPI: Thermal Zone [THRM] (40 C)
Aug 31 17:30:15 Shippou kernel: [   14.599272] usbcore: registered new interface driver usbfs
Aug 31 17:30:15 Shippou kernel: [   14.599333] usbcore: registered new interface driver hub
Aug 31 17:30:15 Shippou kernel: [   14.611168] SCSI subsystem initialized
Aug 31 17:30:15 Shippou kernel: [   14.626899] usbcore: registered new device driver usb
Aug 31 17:30:15 Shippou kernel: [   14.662812] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 31 17:30:15 Shippou kernel: [   14.662863] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 31 17:30:15 Shippou kernel: [   14.662949] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 31 17:30:15 Shippou kernel: [   14.663246] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug 31 17:30:15 Shippou kernel: [   14.663305] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Aug 31 17:30:15 Shippou kernel: [   14.678749] libata version 3.00 loaded.
Aug 31 17:30:15 Shippou kernel: [   14.722901] usb usb1: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   14.722963] hub 1-0:1.0: USB hub found
Aug 31 17:30:15 Shippou kernel: [   14.723006] hub 1-0:1.0: 2 ports detected
Aug 31 17:30:15 Shippou kernel: [   14.723076] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 31 17:30:15 Shippou kernel: [   14.723115] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 31 17:30:15 Shippou kernel: [   14.826598] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Aug 31 17:30:15 Shippou kernel: [   14.826684] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 31 17:30:15 Shippou kernel: [   14.826744] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug 31 17:30:15 Shippou kernel: [   14.826803] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Aug 31 17:30:15 Shippou kernel: [   14.886628] usb usb2: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   14.886690] hub 2-0:1.0: USB hub found
Aug 31 17:30:15 Shippou kernel: [   14.886734] hub 2-0:1.0: 2 ports detected
Aug 31 17:30:15 Shippou kernel: [   14.906422] Floppy drive(s): fd0 is 1.44M
Aug 31 17:30:15 Shippou kernel: [   14.928264] FDC 0 is a post-1991 82077
Aug 31 17:30:15 Shippou kernel: [   14.990320] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug 31 17:30:15 Shippou kernel: [   14.990409] ohci_hcd 0000:00:13.2: OHCI Host Controller
Aug 31 17:30:15 Shippou kernel: [   14.990468] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug 31 17:30:15 Shippou kernel: [   14.990528] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Aug 31 17:30:15 Shippou kernel: [   15.050333] usb usb3: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   15.050395] hub 3-0:1.0: USB hub found
Aug 31 17:30:15 Shippou kernel: [   15.050438] hub 3-0:1.0: 2 ports detected
Aug 31 17:30:15 Shippou kernel: [   15.154034] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Aug 31 17:30:15 Shippou kernel: [   15.154122] ohci_hcd 0000:00:13.3: OHCI Host Controller
Aug 31 17:30:15 Shippou kernel: [   15.154179] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Aug 31 17:30:15 Shippou kernel: [   15.154232] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Aug 31 17:30:15 Shippou kernel: [   15.214078] usb usb4: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   15.214141] hub 4-0:1.0: USB hub found
Aug 31 17:30:15 Shippou kernel: [   15.214183] hub 4-0:1.0: 2 ports detected
Aug 31 17:30:15 Shippou kernel: [   15.301707] usb 2-1: new low speed USB device using ohci_hcd and address 2
Aug 31 17:30:15 Shippou kernel: [   15.317783] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Aug 31 17:30:15 Shippou kernel: [   15.317870] ohci_hcd 0000:00:13.4: OHCI Host Controller
Aug 31 17:30:15 Shippou kernel: [   15.317924] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Aug 31 17:30:15 Shippou kernel: [   15.317978] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Aug 31 17:30:15 Shippou kernel: [   15.377798] usb usb5: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   15.377860] hub 5-0:1.0: USB hub found
Aug 31 17:30:15 Shippou kernel: [   15.377902] hub 5-0:1.0: 2 ports detected
Aug 31 17:30:15 Shippou kernel: [   15.481677] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Aug 31 17:30:15 Shippou kernel: [   15.481763] ehci_hcd 0000:00:13.5: EHCI Host Controller
Aug 31 17:30:15 Shippou kernel: [   15.481822] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Aug 31 17:30:15 Shippou kernel: [   15.481901] ehci_hcd 0000:00:13.5: debug port 1
Aug 31 17:30:15 Shippou kernel: [   15.481952] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Aug 31 17:30:15 Shippou kernel: [   15.501364] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 31 17:30:15 Shippou kernel: [   15.501534] usb usb6: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   15.501599] hub 6-0:1.0: USB hub found
Aug 31 17:30:15 Shippou kernel: [   15.501639] hub 6-0:1.0: 10 ports detected
Aug 31 17:30:15 Shippou kernel: [   15.605507] ahci 0000:00:12.0: version 3.0
Aug 31 17:30:15 Shippou kernel: [   15.605536] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 31 17:30:15 Shippou kernel: [   15.605627] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Aug 31 17:30:15 Shippou kernel: [   15.605665] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Aug 31 17:30:15 Shippou kernel: [   15.896678] usb 2-1: device not accepting address 2, error -62
Aug 31 17:30:15 Shippou kernel: [   16.451741] usb 2-1: new low speed USB device using ohci_hcd and address 4
Aug 31 17:30:15 Shippou kernel: [   16.607514] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Aug 31 17:30:15 Shippou kernel: [   16.607557] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Aug 31 17:30:15 Shippou kernel: [   16.607946] scsi0 : ahci
Aug 31 17:30:15 Shippou kernel: [   16.608259] scsi1 : ahci
Aug 31 17:30:15 Shippou kernel: [   16.608418] scsi2 : ahci
Aug 31 17:30:15 Shippou kernel: [   16.608575] scsi3 : ahci
Aug 31 17:30:15 Shippou kernel: [   16.608691] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 16
Aug 31 17:30:15 Shippou kernel: [   16.608733] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 16
Aug 31 17:30:15 Shippou kernel: [   16.608776] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 16
Aug 31 17:30:15 Shippou kernel: [   16.608818] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 16
Aug 31 17:30:15 Shippou kernel: [   16.672502] usb 2-1: configuration #1 chosen from 1 choice
Aug 31 17:30:15 Shippou kernel: [   16.690644] usbcore: registered new interface driver hiddev
Aug 31 17:30:15 Shippou kernel: [   16.694550] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb2/2-1/2-1:1.0/input/input2
Aug 31 17:30:15 Shippou kernel: [   16.707340] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.1-1
Aug 31 17:30:15 Shippou kernel: [   16.707513] usbcore: registered new interface driver usbhid
Aug 31 17:30:15 Shippou kernel: [   16.707551] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 31 17:30:15 Shippou kernel: [   17.082683] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 31 17:30:15 Shippou kernel: [   17.124821] ata1.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
Aug 31 17:30:15 Shippou kernel: [   17.124860] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug 31 17:30:15 Shippou kernel: [   17.183033] ata1.00: configured for UDMA/133
Aug 31 17:30:15 Shippou kernel: [   17.493982] ata2: SATA link down (SStatus 0 SControl 300)
Aug 31 17:30:15 Shippou kernel: [   17.805455] ata3: SATA link down (SStatus 0 SControl 300)
Aug 31 17:30:15 Shippou kernel: [   18.116927] ata4: SATA link down (SStatus 0 SControl 300)
Aug 31 17:30:15 Shippou kernel: [   18.117067] scsi 0:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
Aug 31 17:30:15 Shippou kernel: [   18.119085] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Aug 31 17:30:15 Shippou kernel: [   18.119138] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 31 17:30:15 Shippou kernel: [   18.119214] SB600_PATA: not 100% native mode: will probe irqs later
Aug 31 17:30:15 Shippou kernel: [   18.120007]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:DMA
Aug 31 17:30:15 Shippou kernel: [   18.120114] Probing IDE interface ide0...
Aug 31 17:30:15 Shippou kernel: [   18.134614] Driver 'sd' needs updating - please use bus_type methods
Aug 31 17:30:15 Shippou kernel: [   18.134732] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Aug 31 17:30:15 Shippou kernel: [   18.134780] sd 0:0:0:0: [sda] Write Protect is off
Aug 31 17:30:15 Shippou kernel: [   18.134817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 31 17:30:15 Shippou kernel: [   18.134833] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 31 17:30:15 Shippou kernel: [   18.134914] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Aug 31 17:30:15 Shippou kernel: [   18.134958] sd 0:0:0:0: [sda] Write Protect is off
Aug 31 17:30:15 Shippou kernel: [   18.134995] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 31 17:30:15 Shippou kernel: [   18.135008] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 31 17:30:15 Shippou kernel: [   18.135051]  sda: sda1 sda2 sda3 < sda5 sda6 >
Aug 31 17:30:15 Shippou kernel: [   18.170387] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 31 17:30:15 Shippou kernel: [   18.175905] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 31 17:30:15 Shippou kernel: [   18.907918] hdb: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
Aug 31 17:30:15 Shippou kernel: [   19.187114] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 31 17:30:15 Shippou kernel: [   19.187451] hdb: UDMA/66 mode selected
Aug 31 17:30:15 Shippou kernel: [   19.187852] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Aug 31 17:30:15 Shippou kernel: [   19.203578] r8169 Gigabit Ethernet driver 2.2LK loaded
Aug 31 17:30:15 Shippou kernel: [   19.203647] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
Aug 31 17:30:15 Shippou kernel: [   19.203955] eth0: RTL8169sc/8110sc at 0xf882c000, 00:19:21:21:21:b5, XID 18000000 IRQ 20
Aug 31 17:30:15 Shippou kernel: [   19.226773] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Aug 31 17:30:15 Shippou kernel: [   19.226995] Uniform CD-ROM driver Revision: 3.20
Aug 31 17:30:15 Shippou kernel: [   19.491333] Attempting manual resume
Aug 31 17:30:15 Shippou kernel: [   19.491371] swsusp: Resume From Partition 8:5
Aug 31 17:30:15 Shippou kernel: [   19.491373] PM: Checking swsusp image.
Aug 31 17:30:15 Shippou kernel: [   19.491536] PM: Resume from disk failed.
Aug 31 17:30:15 Shippou kernel: [   19.526553] kjournald starting.  Commit interval 5 seconds
Aug 31 17:30:15 Shippou kernel: [   19.526602] EXT3-fs: mounted filesystem with ordered data mode.
Aug 31 17:30:15 Shippou kernel: [   26.279212] input: PC Speaker as /devices/platform/pcspkr/input/input3
Aug 31 17:30:15 Shippou kernel: [   26.722414] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 31 17:30:15 Shippou kernel: [   26.758425] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 31 17:30:15 Shippou kernel: [   26.798263] Linux agpgart interface v0.102
Aug 31 17:30:15 Shippou kernel: [   26.988088] parport_pc 00:0a: reported by Plug and Play ACPI
Aug 31 17:30:15 Shippou kernel: [   26.988184] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Aug 31 17:30:15 Shippou kernel: [   27.025907] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 31 17:30:15 Shippou kernel: [   27.294489] input: Power Button (FF) as /devices/virtual/input/input4
Aug 31 17:30:15 Shippou kernel: [   27.305384] ACPI: Power Button (FF) [PWRF]
Aug 31 17:30:15 Shippou kernel: [   27.305492] input: Power Button (CM) as /devices/virtual/input/input5
Aug 31 17:30:15 Shippou kernel: [   27.321356] ACPI: Power Button (CM) [PWRB]
Aug 31 17:30:15 Shippou kernel: [   28.124087] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Aug 31 17:30:15 Shippou kernel: [   28.149818] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Aug 31 17:30:15 Shippou kernel: [   28.895325] udev: renamed network interface eth0 to eth1
Aug 31 17:30:15 Shippou kernel: [   30.957934] lp0: using parport0 (interrupt-driven).
Aug 31 17:30:15 Shippou kernel: [   31.020182] Adding 497972k swap on /dev/sda5.  Priority:-1 extents:1 across:497972k
Aug 31 17:30:15 Shippou kernel: [   57.021447] EXT3 FS on sda2, internal journal
Aug 31 17:30:15 Shippou kernel: [   57.483048] kjournald starting.  Commit interval 5 seconds
Aug 31 17:30:15 Shippou kernel: [   57.483289] EXT3 FS on sda6, internal journal
Aug 31 17:30:15 Shippou kernel: [   57.483294] EXT3-fs: mounted filesystem with ordered data mode.
Aug 31 17:30:15 Shippou kernel: [   57.651092] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 31 17:30:15 Shippou kernel: [   71.524902] No dock devices found.
Aug 31 17:30:15 Shippou kernel: [   71.910263] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Aug 31 17:30:15 Shippou kernel: [   71.910294] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Aug 31 17:30:15 Shippou kernel: [   71.910297] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Aug 31 17:30:16 Shippou kernel: [   72.847861] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 31 17:30:16 Shippou kernel: [   72.847866] apm: overridden by ACPI.
Aug 31 17:30:19 Shippou kernel: [  136.695690] Marking TSC unstable due to: cpufreq changes.
Aug 31 17:30:19 Shippou kernel: [  136.893638] Time: hpet clocksource has been installed.
Aug 31 17:30:19 Shippou kernel: [  137.123523] Clocksource tsc unstable (delta = -190233661 ns)
Aug 31 17:30:21 Shippou kernel: [  139.232101] r8169: eth1: link down
Aug 31 17:30:22 Shippou kernel: [  140.139239] [drm] Initialized drm 1.1.0 20060810
Aug 31 17:30:41 Shippou kernel: [   89.720063] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 31 17:30:53 Shippou kernel: [  100.241895] UDF-fs: No VRS found
Aug 31 17:30:53 Shippou kernel: [  100.349732] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 31 17:30:53 Shippou kernel: [  100.350829] ISOFS: changing to secondary root
Aug 31 17:33:54 Shippou kernel: [  396.783664] r8169: eth1: link down
Aug 31 17:34:39 Shippou kernel: [  449.596026] r8169: eth1: link down
Aug 31 17:41:14 Shippou kernel: [  628.087804] UDF-fs: No VRS found
Aug 31 17:41:14 Shippou kernel: [  628.150303] ISO 9660 Extensions: RRIP_1991A
Aug 31 17:46:06 Shippou kernel: [  920.012767] cdrom: This disc doesn't have any tracks I recognize!
Aug 31 17:50:48 Shippou kernel: [ 1201.047382] UDF-fs: No VRS found
Aug 31 17:50:48 Shippou kernel: [ 1201.084153] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 31 17:50:48 Shippou kernel: [ 1201.086921] ISO 9660 Extensions: RRIP_1991A
Aug 31 17:53:41 Shippou kernel: [ 1374.036647] cdrom: This disc doesn't have any tracks I recognize!
Aug 31 17:57:14 Shippou kernel: [ 1586.567746] UDF-fs: No VRS found
Aug 31 18:10:17 Shippou kernel: [ 4237.033345] hdb: irq timeout: status=0xd0 { Busy }
Aug 31 18:10:17 Shippou kernel: [ 4237.033355] ide: failed opcode was: unknown
Aug 31 18:10:33 Shippou kernel: [ 4253.306571] hdb: irq timeout: status=0xd0 { Busy }
Aug 31 18:10:33 Shippou kernel: [ 4253.306580] ide: failed opcode was: unknown
Aug 31 18:10:53 Shippou kernel: [ 2372.619943] ip6_tables: (C) 2000-2006 Netfilter Core Team

```

Hope anyone knows a fix.

---

### Post by Shippou on 2008-09-01
bump!

---

### Post by louis442122 on 2008-10-21
I have the same problem.

---

### Post by bodhi.zazen on 2008-10-21
Edit: Duplicate post / forums hiccup.

---

### Post by bodhi.zazen on 2008-10-21
To be honest, if you wish to use selinux I would suggest a distro with selinux already enabled (Fedora, Centos, EnGarde).

Don't get me wrong, I am a fan of SELinux and I use it on EnGarde and Centos.

I too have had problems installing it on Ubuntu and I advise you file a bug report on Launchpad.

If you would like help here, can you tell us more information please. How did you install selinux ? Version of Ubuntu ?

Otherwise, Ubuntu uses AppArmor and , when in Rome ...

Why not try AppArmor ?

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

---

### Post by Shippou on 2008-10-22
Wow, an old post got revived!

Well, I have fixed the problem by uninstalling SELinux (purge). Also, I have restored grub - replaced by SELinux.

Thanks for mentioning apparmor. I'll try it sometime. But now I have to fix my VirtualBox problem.

Thanks again! :)

---

