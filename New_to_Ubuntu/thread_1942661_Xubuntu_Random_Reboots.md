---
title: "Xubuntu Random Reboots"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by manilaph on 2012-03-18
Recently, I have experienced random reboots on my Xubuntu 11.10

I wonder what is wrong. I brought my computer to the shop and they said there is nothing wrong with the hardware.

could you experts identify the problem:

```
sgo@sgo:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
[    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f69e000 - 000000007f6d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6de000 (reserved)
[    0.000000]  BIOS-e820: 000000007f6e0000 - 000000007f700000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/P5KPL-AM EPU, BIOS 0415    02/04/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f690 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365ea000 - 372ed000
[    0.000000] ACPI: RSDP 000fb7f0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7f690000 0003C (v01 A_M_I_ OEMRSDT  02001004 MSFT 00000097)
[    0.000000] ACPI: FACP 7f690200 00084 (v02 A_M_I_ OEMFACP  02001004 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f6905c0 08A54 (v01  A1350 A1350000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 7f69e000 00040
[    0.000000] ACPI: APIC 7f690390 0006C (v01 A_M_I_ OEMAPIC  02001004 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f690400 0003C (v01 A_M_I_ OEMMCFG  02001004 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f69e040 00080 (v01 A_M_I_ AMI_OEM  02001004 MSFT 00000097)
[    0.000000] ACPI: HPET 7f699020 00038 (v01 A_M_I_ OEMHPET  02001004 MSFT 00000097)
[    0.000000] ACPI: GSCI 7f69e0c0 02024 (v01 A_M_I_ GMCHSCI  02001004 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f690
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f690
[    0.000000] On node 0 totalpages: 521759
[    0.000000] free_area_init_node: node 0, pgdat c17b54c0, node_mem_map f55fa200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292244 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f700000 (gap: 7f700000:7f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5000000 s26240 r0 d22912 u1048576
[    0.000000] pcpu-alloc: s26240 r0 d22912 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517681
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=0a3a2f1a-f527-428c-b460-e28f060d0acf ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 8349696 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f690)
[    0.000000] Memory: 2038640k/2087488k available (5340k kernel code, 48396k reserved, 2596k data, 696k init, 1178184k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc1537104 - 0xc17c0140   (2596 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1537104   (5340 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f440a000 soft=f440c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2699.979 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.95 BogoMIPS (lpj=10799916)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004028] Security Framework initialized
[    0.004042] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004091] Mount-cache hash table entries: 512
[    0.004211] Initializing cgroup subsys cpuacct
[    0.004216] Initializing cgroup subsys memory
[    0.004222] Initializing cgroup subsys devices
[    0.004224] Initializing cgroup subsys freezer
[    0.004226] Initializing cgroup subsys net_cls
[    0.004228] Initializing cgroup subsys blkio
[    0.004234] Initializing cgroup subsys perf_event
[    0.004262] CPU: Physical Processor ID: 0
[    0.004263] CPU: Processor Core ID: 0
[    0.004266] mce: CPU supports 6 MCE banks
[    0.004274] CPU0: Thermal monitoring enabled (TM2)
[    0.004277] using mwait in idle threads.
[    0.006025] ACPI: Core revision 20110413
[    0.012011] ftrace: allocating 24901 entries in 49 pages
[    0.016047] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016403] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059565] CPU0: Intel Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz stepping 0a
[    0.060003] APIC calibration not consistent with PM-Timer: 115ms instead of 100ms
[    0.060003] APIC delta adjusted to PM-Timer: 1249997 (1449981)
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f44cc000 soft=f44ce000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148022] Brought up 2 CPUs
[    0.148025] Total of 2 processors activated (10799.88 BogoMIPS).
[    0.148925] devtmpfs: initialized
[    0.148925] PM: Registering ACPI NVS region at 7f69e000 (204800 bytes)
[    0.149634] print_constraints: dummy: 
[    0.149656] Time:  6:05:06  Date: 03/18/12
[    0.149689] NET: Registered protocol family 16
[    0.149713] Trying to unpack rootfs image as initramfs...
[    0.149795] EISA bus registered
[    0.149802] ACPI: bus type pci registered
[    0.149854] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.149856] PCI: not using MMCONFIG
[    0.150005] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.150007] PCI: Using configuration type 1 for base access
[    0.164086] bio: create slab <bio-0> at 0
[    0.165363] ACPI: EC: Look up EC in DSDT
[    0.166709] ACPI: Executed 1 blocks of module-level executable AML code
[    0.188775] ACPI: SSDT 7f6a00f0 00256 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.189076] ACPI: Dynamic OEM Table Load:
[    0.189079] ACPI: SSDT   (null) 00256 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.189230] ACPI: SSDT 7f6a0350 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.189519] ACPI: Dynamic OEM Table Load:
[    0.189521] ACPI: SSDT   (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.189740] ACPI: Interpreter enabled
[    0.189747] ACPI: (supports S0 S1 S3 S4 S5)
[    0.189768] ACPI: Using IOAPIC for interrupt routing
[    0.189793] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.190809] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in ACPI motherboard resources
[    0.190811] PCI: Using MMCONFIG for extended config space
[    0.195580] ACPI: No dock devices found.
[    0.195584] HEST: Table not found.
[    0.195588] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.195645] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.195758] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.195761] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.195763] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.195765] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.195767] pci_root PNP0A08:00: host bridge window [mem 0x7f700000-0xffffffff]
[    0.195782] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
[    0.195828] pci 0000:00:02.0: [8086:29c2] type 0 class 0x000300
[    0.195838] pci 0000:00:02.0: reg 10: [mem 0xfea80000-0xfeafffff]
[    0.195844] pci 0000:00:02.0: reg 14: [io  0xdc00-0xdc07]
[    0.195849] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff pref]
[    0.195854] pci 0000:00:02.0: reg 1c: [mem 0xfe900000-0xfe9fffff]
[    0.195917] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.195931] pci 0000:00:1b.0: reg 10: [mem 0xfea78000-0xfea7bfff 64bit]
[    0.195996] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.196000] pci 0000:00:1b.0: PME# disabled
[    0.196025] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.196090] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.196093] pci 0000:00:1c.0: PME# disabled
[    0.196113] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.196181] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.196184] pci 0000:00:1c.1: PME# disabled
[    0.196206] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.196243] pci 0000:00:1d.0: reg 20: [io  0xd400-0xd41f]
[    0.196272] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.196309] pci 0000:00:1d.1: reg 20: [io  0xd480-0xd49f]
[    0.196338] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.196378] pci 0000:00:1d.2: reg 20: [io  0xd800-0xd81f]
[    0.196407] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.196444] pci 0000:00:1d.3: reg 20: [io  0xd880-0xd89f]
[    0.196481] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.196499] pci 0000:00:1d.7: reg 10: [mem 0xfea77c00-0xfea77fff]
[    0.196577] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.196581] pci 0000:00:1d.7: PME# disabled
[    0.196596] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.196657] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.196735] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.196778] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.196790] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.196799] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.196807] pci 0000:00:1f.1: reg 18: [io  0x08f0-0x08f7]
[    0.196816] pci 0000:00:1f.1: reg 1c: [io  0x08f8-0x08fb]
[    0.196824] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.196857] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.196870] pci 0000:00:1f.2: reg 10: [io  0xd080-0xd087]
[    0.196877] pci 0000:00:1f.2: reg 14: [io  0xd000-0xd003]
[    0.196885] pci 0000:00:1f.2: reg 18: [io  0xcc00-0xcc07]
[    0.196892] pci 0000:00:1f.2: reg 1c: [io  0xc880-0xc883]
[    0.196899] pci 0000:00:1f.2: reg 20: [io  0xc800-0xc80f]
[    0.196932] pci 0000:00:1f.2: PME# supported from D3hot
[    0.196935] pci 0000:00:1f.2: PME# disabled
[    0.196947] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.196998] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.197066] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.197070] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.197074] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.197080] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.197134] pci 0000:01:00.0: [1969:1026] type 0 class 0x000200
[    0.197156] pci 0000:01:00.0: reg 10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.197168] pci 0000:01:00.0: reg 18: [io  0xec00-0xec7f]
[    0.197263] pci 0000:01:00.0: PME# supported from D3hot D3cold
[    0.197268] pci 0000:01:00.0: PME# disabled
[    0.197288] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.197299] pci 0000:00:1c.1: PCI bridge to [bus 01-01]
[    0.197303] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.197307] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.197312] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.197372] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.197375] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.197379] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.197385] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.197387] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.197389] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.197391] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.197394] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.197396] pci 0000:00:1e.0:   bridge window [mem 0x7f700000-0xffffffff] (subtractive decode)
[    0.197409] pci_bus 0000:00: on NUMA node 0
[    0.197413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.197516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.197579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.197611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.197654]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.197657]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.197658] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.202141] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.202184] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.202225] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.202265] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.202306] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.202348] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.202389] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.202430] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.202519] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.202527] vgaarb: loaded
[    0.202529] vgaarb: bridge control possible 0000:00:02.0
[    0.202723] SCSI subsystem initialized
[    0.202784] libata version 3.00 loaded.
[    0.202827] usbcore: registered new interface driver usbfs
[    0.202840] usbcore: registered new interface driver hub
[    0.202864] usbcore: registered new device driver usb
[    0.202938] PCI: Using ACPI for IRQ routing
[    0.202942] PCI: pci_cache_line_size set to 64 bytes
[    0.202998] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.203000] reserve RAM buffer: 000000007f690000 - 000000007fffffff 
[    0.203087] NetLabel: Initializing
[    0.203089] NetLabel:  domain hash size = 128
[    0.203090] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.203100] NetLabel:  unlabeled traffic allowed by default
[    0.203134] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.203138] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.203142] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212076] Switching to clocksource hpet
[    0.215879] Switched to NOHz mode on CPU #0
[    0.215904] Switched to NOHz mode on CPU #1
[    0.218665] AppArmor: AppArmor Filesystem Enabled
[    0.218696] pnp: PnP ACPI init
[    0.218713] ACPI: bus type pnp registered
[    0.218806] pnp 00:00: [bus 00-ff]
[    0.218809] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.218811] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.218813] pnp 00:00: [io  0x0d00-0xffff window]
[    0.218815] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.218817] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.218819] pnp 00:00: [mem 0x7f700000-0xffffffff window]
[    0.218880] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.218889] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.218936] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.218939] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218969] pnp 00:02: [dma 4]
[    0.218970] pnp 00:02: [io  0x0000-0x000f]
[    0.218972] pnp 00:02: [io  0x0081-0x0083]
[    0.218974] pnp 00:02: [io  0x0087]
[    0.218976] pnp 00:02: [io  0x0089-0x008b]
[    0.218977] pnp 00:02: [io  0x008f]
[    0.218979] pnp 00:02: [io  0x00c0-0x00df]
[    0.219000] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.219009] pnp 00:03: [io  0x0070-0x0071]
[    0.219020] pnp 00:03: [irq 8]
[    0.219042] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.219049] pnp 00:04: [io  0x0061]
[    0.219071] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.219079] pnp 00:05: [io  0x00f0-0x00ff]
[    0.219083] pnp 00:05: [irq 13]
[    0.219108] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.219432] pnp 00:06: [irq 7]
[    0.219434] pnp 00:06: [dma 3]
[    0.219435] pnp 00:06: [io  0x0378-0x037f]
[    0.219437] pnp 00:06: [io  0x0778-0x077f]
[    0.219563] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.219589] pnp 00:07: [io  0x0000-0xffffffff disabled]
[    0.219591] pnp 00:07: [io  0x0000-0xffffffff disabled]
[    0.219593] pnp 00:07: [io  0x0290-0x0297]
[    0.219628] system 00:07: [io  0x0290-0x0297] has been reserved
[    0.219631] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.219715] pnp 00:08: [io  0x0010-0x001f]
[    0.219717] pnp 00:08: [io  0x0022-0x003f]
[    0.219718] pnp 00:08: [io  0x0044-0x005f]
[    0.219720] pnp 00:08: [io  0x0062-0x0063]
[    0.219722] pnp 00:08: [io  0x0065-0x006f]
[    0.219723] pnp 00:08: [io  0x0072-0x007f]
[    0.219725] pnp 00:08: [io  0x0080]
[    0.219727] pnp 00:08: [io  0x0084-0x0086]
[    0.219728] pnp 00:08: [io  0x0088]
[    0.219730] pnp 00:08: [io  0x008c-0x008e]
[    0.219732] pnp 00:08: [io  0x0090-0x009f]
[    0.219733] pnp 00:08: [io  0x00a2-0x00bf]
[    0.219735] pnp 00:08: [io  0x00e0-0x00ef]
[    0.219737] pnp 00:08: [io  0x04d0-0x04d1]
[    0.219738] pnp 00:08: [io  0x0800-0x087f]
[    0.219740] pnp 00:08: [io  0x0400-0x03ff disabled]
[    0.219742] pnp 00:08: [io  0x0480-0x04bf]
[    0.219744] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.219746] pnp 00:08: [mem 0xfed20000-0xfed8ffff]
[    0.219791] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.219794] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.219796] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.219798] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.219801] system 00:08: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.219803] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.219859] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.219883] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.219928] pnp 00:0a: [mem 0xffb00000-0xffbfffff]
[    0.219930] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.219955] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.219989] pnp 00:0b: [mem 0xffc00000-0xffefffff]
[    0.220056] system 00:0b: [mem 0xffc00000-0xffefffff] has been reserved
[    0.220059] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.220097] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.220099] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.220138] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.220141] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.220144] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.220168] pnp 00:0d: [io  0x0060]
[    0.220170] pnp 00:0d: [io  0x0064]
[    0.220174] pnp 00:0d: [irq 1]
[    0.220208] pnp 00:0d: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.220438] pnp 00:0e: [irq 4]
[    0.220440] pnp 00:0e: [dma 0 disabled]
[    0.220442] pnp 00:0e: [io  0x03f8-0x03ff]
[    0.220505] pnp 00:0e: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.220534] pnp 00:0f: [mem 0xf0000000-0xf3ffffff]
[    0.220570] system 00:0f: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.220573] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.220712] pnp 00:10: [mem 0x00000000-0x0009ffff]
[    0.220714] pnp 00:10: [mem 0x000c0000-0x000cffff]
[    0.220716] pnp 00:10: [mem 0x000e0000-0x000fffff]
[    0.220718] pnp 00:10: [mem 0x00100000-0x7f6fffff]
[    0.220720] pnp 00:10: [mem 0x00000000-0xffffffff disabled]
[    0.220767] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.220769] system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.220772] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.220774] system 00:10: [mem 0x00100000-0x7f6fffff] could not be reserved
[    0.220777] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.220892] pnp: PnP ACPI: found 17 devices
[    0.220894] ACPI: ACPI bus type pnp unregistered
[    0.220897] PnPBIOS: Disabled by ACPI PNP
[    0.256763] PCI: max bus depth: 1 pci_try_num: 2
[    0.256805] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7f700000-0x7f8fffff 64bit pref]
[    0.256808] pci 0000:00:1c.0: BAR 14: assigned [mem 0x7f900000-0x7fafffff]
[    0.256811] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7fb00000-0x7fcfffff 64bit pref]
[    0.256815] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.256817] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.256820] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.256824] pci 0000:00:1c.0:   bridge window [mem 0x7f900000-0x7fafffff]
[    0.256828] pci 0000:00:1c.0:   bridge window [mem 0x7fb00000-0x7fcfffff 64bit pref]
[    0.256834] pci 0000:00:1c.1: PCI bridge to [bus 01-01]
[    0.256836] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.256841] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.256845] pci 0000:00:1c.1:   bridge window [mem 0x7f700000-0x7f8fffff 64bit pref]
[    0.256850] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.256852] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.256856] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.256859] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.256870] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.256887] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.256892] pci 0000:00:1c.0: setting latency timer to 64
[    0.256901] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.256904] pci 0000:00:1c.1: setting latency timer to 64
[    0.256910] pci 0000:00:1e.0: setting latency timer to 64
[    0.256914] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.256916] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.256918] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.256920] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.256922] pci_bus 0000:00: resource 8 [mem 0x7f700000-0xffffffff]
[    0.256924] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.256927] pci_bus 0000:02: resource 1 [mem 0x7f900000-0x7fafffff]
[    0.256929] pci_bus 0000:02: resource 2 [mem 0x7fb00000-0x7fcfffff 64bit pref]
[    0.256931] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.256933] pci_bus 0000:01: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.256935] pci_bus 0000:01: resource 2 [mem 0x7f700000-0x7f8fffff 64bit pref]
[    0.256938] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.256940] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.256942] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.256944] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.256946] pci_bus 0000:03: resource 8 [mem 0x7f700000-0xffffffff]
[    0.256989] NET: Registered protocol family 2
[    0.257062] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.257279] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.257762] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.258004] TCP: Hash tables configured (established 131072 bind 65536)
[    0.258006] TCP reno registered
[    0.258008] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.258016] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.258119] NET: Registered protocol family 1
[    0.258136] pci 0000:00:02.0: Boot video device
[    0.258233] PCI: CLS 32 bytes, default 64
[    0.258555] audit: initializing netlink socket (disabled)
[    0.258565] type=2000 audit(1332050706.252:1): initialized
[    0.278724] highmem bounce pool size: 64 pages
[    0.278730] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.287395] VFS: Disk quotas dquot_6.5.2
[    0.287462] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.288081] fuse init (API version 7.16)
[    0.288165] msgmni has been set to 1680
[    0.288448] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.288470] io scheduler noop registered
[    0.288472] io scheduler deadline registered
[    0.288484] io scheduler cfq registered (default)
[    0.288582] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.288621] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.288676] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.288710] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.288777] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.288797] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.288856] intel_idle: MWAIT substates: 0x22220
[    0.288858] intel_idle: does not run on family 6 model 23
[    0.288931] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.288936] ACPI: Power Button [PWRB]
[    0.288972] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.288975] ACPI: Power Button [PWRF]
[    0.289000] ACPI: acpi_idle registered with cpuidle
[    0.290602] ERST: Table is not found!
[    0.290662] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.300124] isapnp: Scanning for PnP cards...
[    0.311019] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.409373] Freeing initrd memory: 13324k freed
[    0.652978] isapnp: No Plug & Play device found
[    0.708688] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.708954] Linux agpgart interface v0.103
[    0.709030] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.709084] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.709677] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.709785] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.710830] brd: module loaded
[    0.711324] loop: module loaded
[    0.711450] ata_piix 0000:00:1f.1: version 2.13
[    0.711470] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.711499] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.711755] scsi0 : ata_piix
[    0.711826] scsi1 : ata_piix
[    0.712750] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.712753] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.712780] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.712785] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.712819] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.713052] scsi2 : ata_piix
[    0.713103] scsi3 : ata_piix
[    0.714166] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 23
[    0.714168] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 23
[    0.714472] Fixed MDIO Bus: probed
[    0.714492] PPP generic driver version 2.4.2
[    0.714528] tun: Universal TUN/TAP device driver, 1.6
[    0.714529] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.714596] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.714609] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.714621] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.714624] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.714656] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.714670] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.714680] ehci_hcd 0000:00:1d.7: debug port 1
[    0.718557] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.718562] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea77c00
[    0.732019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.732216] hub 1-0:1.0: USB hub found
[    0.732220] hub 1-0:1.0: 8 ports detected
[    0.732284] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732295] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732315] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.732320] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.732323] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.732355] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.732377] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    0.732473] hub 2-0:1.0: USB hub found
[    0.732476] hub 2-0:1.0: 2 ports detected
[    0.732532] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.732538] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.732541] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.732570] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.732598] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    0.732692] hub 3-0:1.0: USB hub found
[    0.732695] hub 3-0:1.0: 2 ports detected
[    0.732744] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.732749] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.732752] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.732778] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.732808] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.732908] hub 4-0:1.0: USB hub found
[    0.732911] hub 4-0:1.0: 2 ports detected
[    0.732959] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.732964] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.732967] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.732993] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.733021] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    0.733117] hub 5-0:1.0: USB hub found
[    0.733120] hub 5-0:1.0: 2 ports detected
[    0.733220] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.733221] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.733722] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.733800] mousedev: PS/2 mouse device common for all mice
[    0.733902] rtc_cmos 00:03: RTC can wake from S4
[    0.733980] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.734002] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.734077] device-mapper: uevent: version 1.0.3
[    0.734137] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.734161] EISA: Probing bus 0 at eisa.0
[    0.734163] EISA: Cannot allocate resource for mainboard
[    0.734165] Cannot allocate resource for EISA slot 1
[    0.734167] Cannot allocate resource for EISA slot 2
[    0.734168] Cannot allocate resource for EISA slot 3
[    0.734170] Cannot allocate resource for EISA slot 4
[    0.734171] Cannot allocate resource for EISA slot 5
[    0.734173] Cannot allocate resource for EISA slot 6
[    0.734174] Cannot allocate resource for EISA slot 7
[    0.734176] Cannot allocate resource for EISA slot 8
[    0.734177] EISA: Detected 0 cards.
[    0.734185] cpufreq-nforce2: No nForce2 chipset.
[    0.734187] cpuidle: using governor ladder
[    0.734189] cpuidle: using governor menu
[    0.734190] EFI Variables Facility v0.08 2004-May-17
[    0.734440] TCP cubic registered
[    0.734559] NET: Registered protocol family 10
[    0.735062] NET: Registered protocol family 17
[    0.735074] Registering the dns_resolver key type
[    0.735094] Using IPI No-Shortcut mode
[    0.735155] PM: Hibernation image not present or could not be loaded.
[    0.735165] registered taskstats version 1
[    0.743698]   Magic number: 4:480:64
[    0.743784] rtc_cmos 00:03: setting system clock to 2012-03-18 06:05:07 UTC (1332050707)
[    0.744248] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.744250] EDD information not available.
[    0.764132] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.879259] ata3.00: ATA-8: ST3250318AS, CC38, max UDMA/133
[    0.879265] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.884134] ata4.01: ATAPI: ATAPI   iHAS224   Y, ZL0W, max UDMA/100
[    0.892344] ata3.00: configured for UDMA/133
[    0.892520] scsi 2:0:0:0: Direct-Access     ATA      ST3250318AS      CC38 PQ: 0 ANSI: 5
[    0.892675] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.892698] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.892716] sd 2:0:0:0: [sda] Write Protect is off
[    0.892719] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.892737] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.900139] ata4.01: configured for UDMA/100
[    0.902022] scsi 3:0:1:0: CD-ROM            ATAPI    iHAS224   Y      ZL0W PQ: 0 ANSI: 5
[    0.904291] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.904294] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.904369] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    0.904408] sr 3:0:1:0: Attached scsi generic sg1 type 5
[    0.923961]  sda: sda1 sda2 < sda5 >
[    0.924292] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.924324] Freeing unused kernel memory: 696k freed
[    0.924540] Write protecting the kernel text: 5344k
[    0.924578] Write protecting the kernel read-only data: 2188k
[    0.937553] udevd[88]: starting version 173
[    0.991109] ATL1E 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.991122] ATL1E 0000:01:00.0: setting latency timer to 64
[    1.044046] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.169659] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.169663] EXT4-fs (sda1): write access will be enabled during recovery
[    1.177881] hub 1-2:1.0: USB hub found
[    1.178218] hub 1-2:1.0: 4 ports detected
[    1.256018] Refined TSC clocksource calibration: 2699.999 MHz.
[    1.256026] Switching to clocksource tsc
[    1.448378] usb 1-2.1: new low speed USB device number 3 using ehci_hcd
[    1.549717] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1:1.0/input/input3
[    1.549815] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.7-2.1/input0
[    1.549827] usbcore: registered new interface driver usbhid
[    1.549829] usbhid: USB HID core driver
[    2.076133] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.076142] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7604184
[    2.076165] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6427179
[    2.076209] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7604181
[    2.076221] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603965
[    2.076233] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603952
[    2.076245] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603951
[    2.076256] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603949
[    2.076267] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603794
[    2.076279] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603725
[    2.076291] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603718
[    2.076303] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603573
[    2.076315] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603534
[    2.076326] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7603521
[    2.076338] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7602907
[    2.076351] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5373965
[    2.076363] EXT4-fs (sda1): 15 orphan inodes deleted
[    2.076364] EXT4-fs (sda1): recovery complete
[    2.388114] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.658209] udevd[300]: starting version 173
[    9.682157] lp: driver loaded but no devices found
[    9.715410] [drm] Initialized drm 1.1.0 20060810
[    9.717358] Adding 2085884k swap on /dev/sda5.  Priority:-1 extents:1 across:2085884k 
[    9.771857] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.771863] i915 0000:00:02.0: setting latency timer to 64
[    9.772970] parport_pc 00:06: reported by Plug and Play ACPI
[    9.773078] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    9.807411] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    9.807420] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.807422] [drm] Driver supports precise vblank timestamp query.
[    9.807620] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.862592] intel_rng: FWH not detected
[    9.876543] type=1400 audit(1332050716.628:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=516 comm="apparmor_parser"
[    9.876874] type=1400 audit(1332050716.628:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=516 comm="apparmor_parser"
[    9.877084] type=1400 audit(1332050716.628:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=516 comm="apparmor_parser"
[    9.878025] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.878147] leds_ss4200: no LED devices found
[    9.886041] lp0: using parport0 (interrupt-driven).
[    9.896170] [drm] initialized overlay support
[   10.009247] init: failsafe main process (601) killed by TERM signal
[   10.018720] fbcon: inteldrmfb (fb0) is primary device
[   10.018808] Console: switching to colour frame buffer device 180x56
[   10.018837] fb0: inteldrmfb frame buffer device
[   10.018839] drm: registered panic notifier
[   10.018851] No ACPI video bus found
[   10.018924] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.098550] type=1400 audit(1332050716.848:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=699 comm="apparmor_parser"
[   10.104127] type=1400 audit(1332050716.856:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=700 comm="apparmor_parser"
[   10.112441] type=1400 audit(1332050716.864:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=700 comm="apparmor_parser"
[   10.112654] type=1400 audit(1332050716.864:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=700 comm="apparmor_parser"
[   10.125472] type=1400 audit(1332050716.876:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=702 comm="apparmor_parser"
[   10.150027] type=1400 audit(1332050716.900:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=708 comm="apparmor_parser"
[   10.152538] type=1400 audit(1332050716.904:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=708 comm="apparmor_parser"
[   10.220313] ppdev: user-space parallel port driver
[   10.220777] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.220828] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   10.220854] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.299054] ATL1E 0000:01:00.0: irq 44 for MSI/MSI-X
[   10.299180] ATL1E 0000:01:00.0: eth0: NIC Link is Up <100 Mbps Full Duplex>
[   10.299515] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.299638] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.564072] init: apport pre-start process (889) terminated with status 1
[   16.578541] init: apport post-stop process (940) terminated with status 1
[   16.832536] Bluetooth: Core ver 2.16
[   16.832559] NET: Registered protocol family 31
[   16.832560] Bluetooth: HCI device and connection manager initialized
[   16.832563] Bluetooth: HCI socket layer initialized
[   16.832564] Bluetooth: L2CAP socket layer initialized
[   16.832735] Bluetooth: SCO socket layer initialized
[   16.834440] Bluetooth: RFCOMM TTY layer initialized
[   16.834444] Bluetooth: RFCOMM socket layer initialized
[   16.834445] Bluetooth: RFCOMM ver 1.11
[   16.854663] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.854666] Bluetooth: BNEP filters: protocol multicast
[   16.977182] init: plymouth-upstart-bridge main process (658) killed by TERM signal
[   17.515684] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   17.705384] init: plymouth-stop pre-start process (1194) terminated with status 1
[   19.281148] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.008009] eth0: no IPv6 routers present

```

---

### Post by 2F4U on 2012-03-18
Did you 
- look into the system log files for error messages?
- run memtest over some iterations?
- identify a pattern behind the reboots (e.g. happens during the use of particular programs)?

---

### Post by Rodney9 on 2012-03-18
View log files in Ubuntu Linux
by VIVEK GITE 

Q. Can you explain me log files in Ubuntu Linux and how do I view logs?

A. All logs are stored in /var/log directory under Ubuntu (and other Linux distro).

Linux Log files and usage

=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

To view log files at shell prompt

Use tail, more, less and grep command.
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot

---

### Post by manilaph on 2012-03-18
Thank you for your kind replies.

This is what is found in my boot.log:

```
fsck from util-linux 2.19.1
/dev/sda1: clean, 188536/15138816 files, 6028352/60527616 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       ?[180G 
?[174G[ OK ]
 * Starting Userspace bootsplash?[174G[ OK ]
 * Stopping cold plug devices?[174G[ OK ]
 * Stopping log initial device creation?[174G[ OK ]
 * Starting configure network device security?[174G[ OK ]
 * Starting configure virtual network devices?[174G[ OK ]
 * Stopping configure virtual network devices?[174G[ OK ]
 * Stopping Userspace bootsplash?[174G[ OK ]
 * Setting sensors limits       ?[180G 
?[174G[ OK ]
 * Stopping System V initialisation compatibility?[174G[ OK ]
 * Starting System V runlevel compatibility?[174G[ OK ]
 * Stopping automatic crash report generation?[174G[?[31mfail?[39;49m]
 * Starting CPU interrupts balancing daemon?[174G[ OK ]
 * Starting LightDM Display Manager?[174G[ OK ]
 * Starting ACPI daemon?[174G[ OK ]
 * Starting anac(h)ronistic cron?[174G[ OK ]
 * Starting save kernel messages?[174G[ OK ]
```

does anything seem wrong with it?

---

### Post by manilaph on 2012-03-18
here is another one from the boot.log:

```
fsck from util-linux 2.19.1
/dev/sda1: clean, 187123/15138816 files, 6145665/60527616 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       [180G 
[174G[ OK ]
 * Stopping cold plug devices[174G[ OK ]
 * Stopping log initial device creation[174G[ OK ]
 * Starting configure network device security[174G[ OK ]
 * Stopping Userspace bootsplash[174G[ OK ]
 * Starting CUPS printing spooler/server[174G[ OK ]
 * Setting sensors limits       [180G 
[174G[ OK ]
 * Stopping System V initialisation compatibility[174G[ OK ]
 * Starting System V runlevel compatibility[174G[ OK ]
 * Stopping automatic crash report generation[174G[[31mfail[39;49m]
 * Starting deferred execution scheduler[174G[ OK ]
 * Starting regular background program processing daemon[174G[ OK ]
 * Starting LightDM Display Manager[174G[ OK ]
 * Starting ACPI daemon[174G[ OK ]
 * Starting anac(h)ronistic cron[174G[ OK ]
 * Starting save kernel messages[174G[ OK ]
 * Starting CPU interrupts balancing daemon[174G[ OK ]
 * Stopping anac(h)ronistic cron[174G[ OK ]
 * Stopping save kernel messages[174G[ OK ]

```

it just keeps rebooting randomly.

---

### Post by manilaph on 2012-03-18
this is from the powersave.log:

```
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

```

---

### Post by Elfy on 2012-03-18
First I would think about all of the questions in post #2 not just some logs.

Then I would be ready to look in the logs immediately _after_ one of these random reboots - I'd start with syslog, I'd also have a look at your .xsession-errors in your home.

---

