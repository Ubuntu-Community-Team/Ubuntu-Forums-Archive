---
title: "very slow booting"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Pulka on 2012-02-21
Hi.


for quite some time i've been having very slow boot on my ubuntu 11.10. Sometimes it takes more than 3 minutes. Have no idea what's causing this.
Here's my

**dmesg**

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@palmer) (gcc version 4.6.1 (Ubuntu/
Linaro 4.6.1-9ubuntu3) ) #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 (Ubuntu 3.0.0-16.28-
generic 3.0.17)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@palmer) (gcc version 4.6.1 (Ubuntu/
Linaro 4.6.1-9ubuntu3) ) #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 (Ubuntu 3.0.0-16.28-
generic 3.0.17)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@palmer) (gcc version 4.6.1 (Ubuntu/
Linaro 4.6.1-9ubuntu3) ) #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 (Ubuntu 3.0.0-16.28-
generic 3.0.17)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: System manufacturer System Product Name/P5GC-MX/1333, BIOS 0413    03/13/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365ec000 - 372ee000
[    0.000000] ACPI: RSDP 000fb030 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffa0000 00038 (v01 A_M_I_ OEMRSDT  03000913 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffa0200 00084 (v02 A_M_I_ OEMFACP  03000913 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffa05c0 06909 (v01  A0798 A0798000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7ffae000 00040
[    0.000000] ACPI: APIC 7ffa0390 0006C (v01 A_M_I_ OEMAPIC  03000913 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffa0400 0003C (v01 A_M_I_ OEMMCFG  03000913 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffae040 00080 (v01 A_M_I_ AMI_OEM  03000913 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffa6ed0 00038 (v01 A_M_I_ OEMHPET  03000913 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffa0
[    0.000000] On node 0 totalpages: 524079
[    0.000000] free_area_init_node: node 0, pgdat c17b5480, node_mem_map f55ec200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294546 pages, LIFO batch:31
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
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5000000 s26240 r0 d22912 u1048576
[    0.000000] pcpu-alloc: s26240 r0 d22912 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519983
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=UUID=d5b66bd9-920a-4459-9a78-dbd6287bbf67 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 8386816 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffa0)
[    0.000000] Memory: 2047824k/2096768k available (5338k kernel code, 48492k reserved, 2597k data, 696k init, 1187464k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc1536944 - 0xc17c0100   (2597 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1536944   (5338 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f440a000 soft=f440c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2999.969 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.93 BogoMIPS (lpj=11999876)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004040] AppArmor: AppArmor initialized
[    0.004041] Yama: becoming mindful.
[    0.004089] Mount-cache hash table entries: 512
[    0.004209] Initializing cgroup subsys cpuacct
[    0.004214] Initializing cgroup subsys memory
[    0.004219] Initializing cgroup subsys devices
[    0.004221] Initializing cgroup subsys freezer
[    0.004223] Initializing cgroup subsys net_cls
[    0.004225] Initializing cgroup subsys blkio
[    0.004230] Initializing cgroup subsys perf_event
[    0.004257] CPU: Physical Processor ID: 0
[    0.004258] CPU: Processor Core ID: 0
[    0.004261] mce: CPU supports 6 MCE banks
[    0.004269] CPU0: Thermal monitoring enabled (TM2)
[    0.004272] using mwait in idle threads.
[    0.008062] ACPI: Core revision 20110413
[    0.012010] ftrace: allocating 24891 entries in 49 pages
[    0.016050] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016408] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058060] CPU0: Intel Pentium(R) Dual-Core  CPU      E5700  @ 3.00GHz stepping 0a
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f44ac000 soft=f44ae000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148021] Brought up 2 CPUs
[    0.148024] Total of 2 processors activated (11999.73 BogoMIPS).
[    0.148868] devtmpfs: initialized
[    0.148868] PM: Registering ACPI NVS region at 7ffae000 (204800 bytes)
[    0.149488] print_constraints: dummy: 
[    0.149510] Time: 15:08:29  Date: 02/21/12
[    0.149541] NET: Registered protocol family 16
[    0.149563] Trying to unpack rootfs image as initramfs...
[    0.149638] EISA bus registered
[    0.149645] ACPI: bus type pci registered
[    0.149694] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.149696] PCI: not using MMCONFIG
[    0.149985] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[    0.149986] PCI: Using configuration type 1 for base access
[    0.164144] bio: create slab <bio-0> at 0
[    0.165127] ACPI: EC: Look up EC in DSDT
[    0.166226] ACPI: Executed 1 blocks of module-level executable AML code
[    0.168201] ACPI: SSDT 7ffae0c0 00298 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.168430] ACPI: Dynamic OEM Table Load:
[    0.168433] ACPI: SSDT   (null) 00298 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.168567] ACPI: SSDT 7ffae360 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.168791] ACPI: Dynamic OEM Table Load:
[    0.168794] ACPI: SSDT   (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.168988] ACPI: Interpreter enabled
[    0.168994] ACPI: (supports S0 S1 S3 S4 S5)
[    0.169013] ACPI: Using IOAPIC for interrupt routing
[    0.169037] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.169965] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in ACPI motherboard resources
[    0.169967] PCI: Using MMCONFIG for extended config space
[    0.174249] ACPI: No dock devices found.
[    0.174252] HEST: Table not found.
[    0.174256] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.174299] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.174383] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.174385] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.174387] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.174389] pci_root PNP0A08:00: host bridge window [mem 0x80010000-0xffffffff]
[    0.174402] pci 0000:00:00.0: [8086:2770] type 0 class 0x000600
[    0.174439] pci 0000:00:01.0: [8086:2771] type 1 class 0x000604
[    0.174468] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.174472] pci 0000:00:01.0: PME# disabled
[    0.174514] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.174528] pci 0000:00:1b.0: reg 10: [mem 0xe3df8000-0xe3dfbfff 64bit]
[    0.174579] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.174583] pci 0000:00:1b.0: PME# disabled
[    0.174601] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.174653] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.174656] pci 0000:00:1c.0: PME# disabled
[    0.174675] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.174726] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.174730] pci 0000:00:1c.1: PME# disabled
[    0.174753] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.174790] pci 0000:00:1d.0: reg 20: [io  0x8000-0x801f]
[    0.174817] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.174855] pci 0000:00:1d.1: reg 20: [io  0x8400-0x841f]
[    0.174882] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.174920] pci 0000:00:1d.2: reg 20: [io  0x8800-0x881f]
[    0.174948] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.174986] pci 0000:00:1d.3: reg 20: [io  0x9000-0x901f]
[    0.175021] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.175039] pci 0000:00:1d.7: reg 10: [mem 0xe3dffc00-0xe3dfffff]
[    0.175104] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.175108] pci 0000:00:1d.7: PME# disabled
[    0.175124] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.175176] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.175256] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
[    0.175287] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.175298] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.175307] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.175316] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.175324] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.175333] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.175365] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.175378] pci 0000:00:1f.2: reg 10: [io  0xa800-0xa807]
[    0.175385] pci 0000:00:1f.2: reg 14: [io  0xa400-0xa403]
[    0.175393] pci 0000:00:1f.2: reg 18: [io  0xa000-0xa007]
[    0.175400] pci 0000:00:1f.2: reg 1c: [io  0x9800-0x9803]
[    0.175408] pci 0000:00:1f.2: reg 20: [io  0x9400-0x940f]
[    0.175436] pci 0000:00:1f.2: PME# supported from D3hot
[    0.175439] pci 0000:00:1f.2: PME# disabled
[    0.175451] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.175500] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.175565] pci 0000:04:00.0: [10de:1040] type 0 class 0x000300
[    0.175574] pci 0000:04:00.0: reg 10: [mem 0xe4000000-0xe4ffffff]
[    0.175585] pci 0000:04:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
[    0.175595] pci 0000:04:00.0: reg 1c: [mem 0xe6000000-0xe7ffffff 64bit pref]
[    0.175602] pci 0000:04:00.0: reg 24: [io  0xe800-0xe87f]
[    0.175609] pci 0000:04:00.0: reg 30: [mem 0xe5f00000-0xe5f7ffff pref]
[    0.175650] pci 0000:04:00.1: [10de:0e08] type 0 class 0x000403
[    0.175659] pci 0000:04:00.1: reg 10: [mem 0xe5ffc000-0xe5ffffff]
[    0.180030] pci 0000:00:01.0: PCI bridge to [bus 04-04]
[    0.180034] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.180037] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe5ffffff]
[    0.180041] pci 0000:00:01.0:   bridge window [mem 0xe6000000-0xefffffff 64bit pref]
[    0.180083] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.180086] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.180090] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.180095] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180148] pci 0000:02:00.0: [1969:2048] type 0 class 0x000200
[    0.180170] pci 0000:02:00.0: reg 10: [mem 0xe3fc0000-0xe3ffffff 64bit]
[    0.180222] pci 0000:02:00.0: reg 30: [mem 0xe3fa0000-0xe3fbffff pref]
[    0.180256] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.180261] pci 0000:02:00.0: PME# disabled
[    0.180279] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.180289] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.180292] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.180296] pci 0000:00:1c.1:   bridge window [mem 0xe3f00000-0xe3ffffff]
[    0.180301] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180334] pci 0000:01:01.0: [168c:0023] type 0 class 0x000280
[    0.180353] pci 0000:01:01.0: reg 10: [mem 0xe3ef0000-0xe3efffff]
[    0.180468] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.180472] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.180475] pci 0000:00:1e.0:   bridge window [mem 0xe3e00000-0xe3efffff]
[    0.180480] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180482] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.180484] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.180486] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.180488] pci 0000:00:1e.0:   bridge window [mem 0x80010000-0xffffffff] (subtractive decode)
[    0.180504] pci_bus 0000:00: on NUMA node 0
[    0.180510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180633] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.180664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.180714] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.180744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.180803]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.180806]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.180807] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.183365] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.183406] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.183444] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.183481] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.183518] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.183555] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.183592] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.183631] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.183728] vgaarb: device added: PCI:0000:04:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.183731] vgaarb: loaded
[    0.183732] vgaarb: bridge control possible 0000:04:00.0
[    0.183921] SCSI subsystem initialized
[    0.184011] libata version 3.00 loaded.
[    0.184038] usbcore: registered new interface driver usbfs
[    0.184048] usbcore: registered new interface driver hub
[    0.184073] usbcore: registered new device driver usb
[    0.184142] PCI: Using ACPI for IRQ routing
[    0.184145] PCI: pci_cache_line_size set to 64 bytes
[    0.184213] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.184215] reserve RAM buffer: 000000007ffa0000 - 000000007fffffff 
[    0.184302] NetLabel: Initializing
[    0.184304] NetLabel:  domain hash size = 128
[    0.184305] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184314] NetLabel:  unlabeled traffic allowed by default
[    0.184346] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.184350] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.184354] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.192075] Switching to clocksource hpet
[    0.195866] Switched to NOHz mode on CPU #0
[    0.195940] Switched to NOHz mode on CPU #1
[    0.198246] AppArmor: AppArmor Filesystem Enabled
[    0.198281] pnp: PnP ACPI init
[    0.198298] ACPI: bus type pnp registered
[    0.198381] pnp 00:00: [bus 00-ff]
[    0.198384] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.198385] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.198387] pnp 00:00: [io  0x0d00-0xffff window]
[    0.198389] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.198391] pnp 00:00: [mem 0x80010000-0xffffffff window]
[    0.198451] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.198459] pnp 00:01: [mem 0xfed13000-0xfed19fff]
[    0.198513] system 00:01: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.198515] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.198538] pnp 00:02: [dma 4]
[    0.198540] pnp 00:02: [io  0x0000-0x000f]
[    0.198542] pnp 00:02: [io  0x0081-0x0083]
[    0.198543] pnp 00:02: [io  0x0087]
[    0.198545] pnp 00:02: [io  0x0089-0x008b]
[    0.198546] pnp 00:02: [io  0x008f]
[    0.198548] pnp 00:02: [io  0x00c0-0x00df]
[    0.198568] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.198576] pnp 00:03: [io  0x0070-0x0071]
[    0.198589] pnp 00:03: [irq 8]
[    0.198612] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.198619] pnp 00:04: [io  0x0061]
[    0.198641] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.198648] pnp 00:05: [io  0x00f0-0x00ff]
[    0.198652] pnp 00:05: [irq 13]
[    0.198673] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.198915] pnp 00:06: [irq 6]
[    0.198917] pnp 00:06: [dma 2]
[    0.198919] pnp 00:06: [io  0x03f0-0x03f5]
[    0.198921] pnp 00:06: [io  0x03f7]
[    0.198965] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.199255] pnp 00:07: [irq 7]
[    0.199257] pnp 00:07: [dma 3]
[    0.199259] pnp 00:07: [io  0x0378-0x037f]
[    0.199260] pnp 00:07: [io  0x0778-0x077f]
[    0.199374] pnp 00:07: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.199398] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    0.199400] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    0.199401] pnp 00:08: [io  0x0290-0x0297]
[    0.199438] system 00:08: [io  0x0290-0x0297] has been reserved
[    0.199440] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199524] pnp 00:09: [io  0x0010-0x001f]
[    0.199526] pnp 00:09: [io  0x0022-0x003f]
[    0.199528] pnp 00:09: [io  0x0044-0x005f]
[    0.199529] pnp 00:09: [io  0x0062-0x0063]
[    0.199531] pnp 00:09: [io  0x0065-0x006f]
[    0.199532] pnp 00:09: [io  0x0072-0x007f]
[    0.199534] pnp 00:09: [io  0x0080]
[    0.199535] pnp 00:09: [io  0x0084-0x0086]
[    0.199536] pnp 00:09: [io  0x0088]
[    0.199538] pnp 00:09: [io  0x008c-0x008e]
[    0.199539] pnp 00:09: [io  0x0090-0x009f]
[    0.199541] pnp 00:09: [io  0x00a2-0x00bf]
[    0.199542] pnp 00:09: [io  0x00e0-0x00ef]
[    0.199544] pnp 00:09: [io  0x04d0-0x04d1]
[    0.199546] pnp 00:09: [io  0x0800-0x087f]
[    0.199547] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    0.199549] pnp 00:09: [io  0x0480-0x04bf]
[    0.199550] pnp 00:09: [io  0x0900-0x091f]
[    0.199552] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.199554] pnp 00:09: [mem 0xfed20000-0xfed8ffff]
[    0.199555] pnp 00:09: [mem 0xffb00000-0xffbfffff]
[    0.199557] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.199610] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.199612] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.199614] system 00:09: [io  0x0480-0x04bf] has been reserved
[    0.199616] system 00:09: [io  0x0900-0x091f] has been reserved
[    0.199618] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.199621] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.199623] system 00:09: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.199625] system 00:09: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.199628] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199703] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.199727] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.199758] pnp 00:0b: [io  0x0060]
[    0.199760] pnp 00:0b: [io  0x0064]
[    0.199764] pnp 00:0b: [irq 1]
[    0.199795] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.199842] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.199844] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.199883] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.199885] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.199888] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200122] pnp 00:0d: [irq 4]
[    0.200124] pnp 00:0d: [dma 0 disabled]
[    0.200126] pnp 00:0d: [io  0x03f8-0x03ff]
[    0.200178] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.200217] pnp 00:0e: [mem 0xffb80000-0xffbfffff]
[    0.200219] pnp 00:0e: [mem 0xfff80000-0xffffffff]
[    0.200243] pnp 00:0e: Plug and Play ACPI device, IDs INT0800 (active)
[    0.200277] pnp 00:0f: [mem 0xffc00000-0xfff7ffff]
[    0.200313] system 00:0f: [mem 0xffc00000-0xfff7ffff] has been reserved
[    0.200316] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200339] pnp 00:10: [mem 0xf0000000-0xf3ffffff]
[    0.200378] system 00:10: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.200380] system 00:10: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200496] pnp 00:11: [mem 0x00000000-0x0009ffff]
[    0.200498] pnp 00:11: [mem 0x000c0000-0x000dffff]
[    0.200499] pnp 00:11: [mem 0x000e0000-0x000fffff]
[    0.200501] pnp 00:11: [mem 0x00100000-0x7fffffff]
[    0.200503] pnp 00:11: [mem 0x00000000-0xffffffff disabled]
[    0.200546] system 00:11: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.200548] system 00:11: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.200550] system 00:11: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.200553] system 00:11: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.200555] system 00:11: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200658] pnp: PnP ACPI: found 18 devices
[    0.200659] ACPI: ACPI bus type pnp unregistered
[    0.200662] PnPBIOS: Disabled by ACPI PNP
[    0.236448] PCI: max bus depth: 1 pci_try_num: 2
[    0.236487] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80100000-0x802fffff]
[    0.236490] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80300000-0x804fffff 64bit pref]
[    0.236493] pci 0000:00:01.0: PCI bridge to [bus 04-04]
[    0.236495] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.236499] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe5ffffff]
[    0.236502] pci 0000:00:01.0:   bridge window [mem 0xe6000000-0xefffffff 64bit pref]
[    0.236505] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.236508] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.236512] pci 0000:00:1c.0:   bridge window [mem 0x80100000-0x802fffff]
[    0.236516] pci 0000:00:1c.0:   bridge window [mem 0x80300000-0x804fffff 64bit pref]
[    0.236521] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.236523] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.236528] pci 0000:00:1c.1:   bridge window [mem 0xe3f00000-0xe3ffffff]
[    0.236531] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.236536] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.236539] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.236543] pci 0000:00:1e.0:   bridge window [mem 0xe3e00000-0xe3efffff]
[    0.236546] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.236572] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.236576] pci 0000:00:01.0: setting latency timer to 64
[    0.236582] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.236585] pci 0000:00:1c.0: setting latency timer to 64
[    0.236593] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.236597] pci 0000:00:1c.1: setting latency timer to 64
[    0.236603] pci 0000:00:1e.0: setting latency timer to 64
[    0.236606] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.236608] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.236609] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.236611] pci_bus 0000:00: resource 7 [mem 0x80010000-0xffffffff]
[    0.236613] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.236615] pci_bus 0000:04: resource 1 [mem 0xe4000000-0xe5ffffff]
[    0.236617] pci_bus 0000:04: resource 2 [mem 0xe6000000-0xefffffff 64bit pref]
[    0.236619] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.236621] pci_bus 0000:03: resource 1 [mem 0x80100000-0x802fffff]
[    0.236623] pci_bus 0000:03: resource 2 [mem 0x80300000-0x804fffff 64bit pref]
[    0.236625] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.236627] pci_bus 0000:02: resource 1 [mem 0xe3f00000-0xe3ffffff]
[    0.236629] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.236631] pci_bus 0000:01: resource 1 [mem 0xe3e00000-0xe3efffff]
[    0.236632] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.236634] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.236636] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.236638] pci_bus 0000:01: resource 7 [mem 0x80010000-0xffffffff]
[    0.236687] NET: Registered protocol family 2
[    0.236755] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.236963] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.237482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.237735] TCP: Hash tables configured (established 131072 bind 65536)
[    0.237737] TCP reno registered
[    0.237740] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.237754] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.237854] NET: Registered protocol family 1
[    0.237977] pci 0000:04:00.0: Boot video device
[    0.237994] PCI: CLS 16 bytes, default 64
[    0.238301] audit: initializing netlink socket (disabled)
[    0.238311] type=2000 audit(1329836909.232:1): initialized
[    0.257729] highmem bounce pool size: 64 pages
[    0.257735] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.266778] VFS: Disk quotas dquot_6.5.2
[    0.266841] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.267393] fuse init (API version 7.16)
[    0.267468] msgmni has been set to 1680
[    0.267736] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.267757] io scheduler noop registered
[    0.267758] io scheduler deadline registered
[    0.267769] io scheduler cfq registered (default)
[    0.267866] pcieport 0000:00:01.0: setting latency timer to 64
[    0.267899] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.267938] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.267971] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.268039] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.268072] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.268138] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.268157] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.268211] intel_idle: MWAIT substates: 0x22220
[    0.268212] intel_idle: does not run on family 6 model 23
[    0.268280] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.268284] ACPI: Power Button [PWRB]
[    0.268319] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.268321] ACPI: Power Button [PWRF]
[    0.268343] ACPI: acpi_idle registered with cpuidle
[    0.269961] ERST: Table is not found!
[    0.270025] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.290412] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.290728] isapnp: Scanning for PnP cards...
[    0.374835] Freeing initrd memory: 13320k freed
[    0.643585] isapnp: No Plug & Play device found
[    0.696637] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.696918] Linux agpgart interface v0.103
[    0.698022] brd: module loaded
[    0.698479] loop: module loaded
[    0.698605] ata_piix 0000:00:1f.1: version 2.13
[    0.698629] ata_piix 0000:00:1f.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.698664] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.698925] scsi0 : ata_piix
[    0.698996] scsi1 : ata_piix
[    0.699967] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.699969] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.699996] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.700011] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.700054] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.700271] scsi2 : ata_piix
[    0.698996] scsi1 : ata_piix
[    0.699967] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.699969] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.699996] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.700011] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.700054] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.700271] scsi2 : ata_piix
[    0.700323] scsi3 : ata_piix
[    0.701281] ata3: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0x9400 irq 23
[    0.701283] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x9408 irq 23
[    0.701574] Fixed MDIO Bus: probed
[    0.701596] PPP generic driver version 2.4.2
[    0.701630] tun: Universal TUN/TAP device driver, 1.6
[    0.701631] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.701693] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.701709] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.701719] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.701722] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.701755] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.701773] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.701782] ehci_hcd 0000:00:1d.7: debug port 1
[    0.705657] ehci_hcd 0000:00:1d.7: cache line size of 16 is not supported
[    0.705668] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe3dffc00
[    0.720018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.720219] hub 1-0:1.0: USB hub found
[    0.720223] hub 1-0:1.0: 8 ports detected
[    0.720283] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.720293] uhci_hcd: USB Universal Host Controller Interface driver
[    0.720312] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.720317] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.720319] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.720345] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.720366] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008000
[    0.720457] hub 2-0:1.0: USB hub found
[    0.720460] hub 2-0:1.0: 2 ports detected
[    0.720509] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.720514] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.720517] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.720541] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.720571] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00008400
[    0.720664] hub 3-0:1.0: USB hub found
[    0.720667] hub 3-0:1.0: 2 ports detected
[    0.720715] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.720719] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.720722] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.720749] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.720776] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008800
[    0.720866] hub 4-0:1.0: USB hub found
[    0.720869] hub 4-0:1.0: 2 ports detected
[    0.720919] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.720923] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.720926] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.720950] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.720978] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009000
[    0.721066] hub 5-0:1.0: USB hub found
[    0.721071] hub 5-0:1.0: 2 ports detected
[    0.721168] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.721170] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.721762] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.721836] mousedev: PS/2 mouse device common for all mice
[    0.721938] rtc_cmos 00:03: RTC can wake from S4
[    0.722015] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.722037] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.722105] device-mapper: uevent: version 1.0.3
[    0.722162] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.722184] EISA: Probing bus 0 at eisa.0
[    0.722186] EISA: Cannot allocate resource for mainboard
[    0.722188] Cannot allocate resource for EISA slot 1
[    0.722190] Cannot allocate resource for EISA slot 2
[    0.722191] Cannot allocate resource for EISA slot 3
[    0.722192] Cannot allocate resource for EISA slot 4
[    0.722194] Cannot allocate resource for EISA slot 5
[    0.722195] Cannot allocate resource for EISA slot 6
[    0.722196] Cannot allocate resource for EISA slot 7
[    0.722198] Cannot allocate resource for EISA slot 8
[    0.722199] EISA: Detected 0 cards.
[    0.722207] cpufreq-nforce2: No nForce2 chipset.
[    0.722209] cpuidle: using governor ladder
[    0.722211] cpuidle: using governor menu
[    0.722212] EFI Variables Facility v0.08 2004-May-17
[    0.722441] TCP cubic registered
[    0.722550] NET: Registered protocol family 10
[    0.723012] NET: Registered protocol family 17
[    0.723024] Registering the dns_resolver key type
[    0.723040] Using IPI No-Shortcut mode
[    0.723096] PM: Hibernation image not present or could not be loaded.
[    0.723107] registered taskstats version 1
[    0.731642]   Magic number: 0:209:134
[    0.731701] acpi device:09: hash matches
[    0.731733] rtc_cmos 00:03: setting system clock to 2012-02-21 15:08:30 UTC (1329836910)
[    0.732236] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.732237] EDD information not available.
[    0.872397] ata1.00: ATAPI: _NEC DVD_RW ND-3520A, 1.04, max UDMA/33
[    0.872402] ata1.01: ATAPI: TSSTcorpDVD-ROM TS-H352A, TS03, max UDMA/33
[    0.872495] ata3.00: ATA-7: SAMSUNG SP1603C, VL100-50, max UDMA7
[    0.872497] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.888220] ata1.00: configured for UDMA/33
[    0.896350] ata1.01: configured for UDMA/33
[    0.898628] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520A  1.04 PQ: 0 ANSI: 5
[    0.900145] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.900150] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.900326] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.900380] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.901378] scsi 0:0:1:0: CD-ROM            TSSTcorp DVD-ROM TS-H352A TS03 PQ: 0 ANSI: 5
[    0.902260] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    0.902413] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    0.902467] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.904259] ata3.00: configured for UDMA/133
[    0.904393] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP1603C  VL10 PQ: 0 ANSI: 5
[    0.904580] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.904607] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    0.904630] sd 2:0:0:0: [sda] Write Protect is off
[    0.904632] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.904659] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.954206]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    0.954581] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.984367] ata4.00: ATA-6: ST380013AS, 3.18, max UDMA/133
[    0.984372] ata4.00: 156301488 sectors, multi 16: LBA48 
[    1.000357] ata4.00: configured for UDMA/133
[    1.000489] scsi 3:0:0:0: Direct-Access     ATA      ST380013AS       3.18 PQ: 0 ANSI: 5
[    1.000643] sd 3:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.000659] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.000679] sd 3:0:0:0: [sdb] Write Protect is off
[    1.000681] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.000707] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.236020] Refined TSC clocksource calibration: 2999.963 MHz.
[    1.236027] Switching to clocksource tsc
[    1.272016] usb 3-1: new low speed USB device number 2 using uhci_hcd
[    1.768014] usb 3-2: new low speed USB device number 3 using uhci_hcd
[    2.299883]  sdb: sdb1 < sdb5 >
[    2.300164] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.300193] Freeing unused kernel memory: 696k freed
[    2.300413] Write protecting the kernel text: 5340k
[    2.300446] Write protecting the kernel read-only data: 2192k
[    2.312269] udevd[89]: starting version 173
[    2.386595] Atheros(R) L2 Ethernet Driver - version 2.2.3
[    2.386598] Copyright (c) 2007 Atheros Corporation.
[    2.386632] atl2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.386641] atl2 0000:02:00.0: setting latency timer to 64
[    2.394328] Floppy drive(s): fd0 is 1.44M
[    2.411805] FDC 0 is a post-1991 82077
[    2.442106] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[    2.442184] generic-usb 0003:04D9:1503.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-1/input0
[    2.531761] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input3
[    2.531864] generic-usb 0003:04D9:1503.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-1/input1
[    2.545018] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    2.545085] generic-usb 0003:046D:C03E.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
[    2.545096] usbcore: registered new interface driver usbhid
[    2.545098] usbhid: USB HID core driver
[    2.657840] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   22.860411] udevd[318]: starting version 173
[   22.894810] lp: driver loaded but no devices found
[   22.909771] intel_rng: FWH not detected
[   22.938474] leds_ss4200: no LED devices found
[   22.968887] cfg80211: Calling CRDA to update world regulatory domain
[   22.981994] type=1400 audit(1329836932.745:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=426 comm="apparmor_parser"
[   22.982313] type=1400 audit(1329836932.745:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[   22.982514] type=1400 audit(1329836932.745:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[   22.983843] Adding 2144672k swap on /dev/sda2.  Priority:-1 extents:1 across:2144672k 
[   22.997464] nvidia: module license 'NVIDIA' taints kernel.
[   22.997468] Disabling lock debugging due to kernel taint
[   23.127386] parport_pc 00:07: reported by Plug and Play ACPI
[   23.127489] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   23.330425] lp0: using parport0 (interrupt-driven).
[   23.334592] ath9k 0000:01:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   23.840679] ppdev: user-space parallel port driver
[   23.851621] ath: EEPROM regdomain: 0x30
[   23.851623] ath: EEPROM indicates we should expect a direct regpair map
[   23.851625] ath: Country alpha2 being used: AM
[   23.851626] ath: Regpair used: 0x30
[   23.851629] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   23.851631] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851633] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   23.851635] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851637] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   23.851639] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851640] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   23.851642] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851644] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   23.851646] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851647] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   23.851649] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851651] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   23.851653] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851655] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   23.851657] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851658] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   23.851660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851662] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.851664] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851666] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.851668] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851669] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851671] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851673] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.887368] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.893039] cfg80211: World regulatory domain updated:
[   23.893042] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.893044] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893046] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893048] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893050] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893052] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893504] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width ch[   23.851660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851662] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.851664] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851666] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.851668] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851669] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851671] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851673] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.887368] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.893039] cfg80211: World regulatory domain updated:
[   23.893042] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.893044] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893046] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893048] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893050] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893052] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893504] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width ch[   23.851660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851662] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.851664] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851666] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.851668] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851669] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851671] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851673] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.887368] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.893039] cfg80211: World regulatory domain updated:
[   23.893042] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.893044] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893046] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893048] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893050] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893052] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893504] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width ch[   23.851660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851662] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.851664] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851666] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.851668] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.851669] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851671] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.851673] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   23.887368] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.893039] cfg80211: World regulatory domain updated:
[   23.893042] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.893044] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893046] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893048] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.893050] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893052] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.893504] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   23.893506] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893508] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   23.893510] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893512] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   23.893514] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893515] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   23.893517] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893519] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   23.893521] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893523] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   23.893525] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893526] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   23.893528] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893530] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   23.893532] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893534] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   23.893536] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893537] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.893539] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893541] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.893543] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893545] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   23.893547] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893548] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   23.893550] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.893552] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   23.893554] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.907721] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   23.907771] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   23.907793] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.926696] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.931094] nvidia 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.931103] nvidia 0000:04:00.0: setting latency timer to 64
[   23.931108] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes
=none:owns=io+mem
[   23.931253] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
[   23.942046] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   23.942743] Registered led device: ath9k-phy0
[   23.942748] ieee80211 phy0: Atheros AR5416 MAC/BB Rev:2 AR2133 RF Rev:81 mem=0xf8cc0000, irq=21
[   23.943105] cfg80211: Calling CRDA for country: AM
[   23.964609] HDA Intel 0000:04:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   23.964614] hda_intel: Disabling MSI
[   23.964645] HDA Intel 0000:04:00.1: setting latency timer to 64
[   23.968601] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   23.968605] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968607] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   23.968609] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968610] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   23.968612] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968614] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   23.968616] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968618] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   23.968620] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968621] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   23.968623] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968625] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   23.968627] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968629] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   23.968631] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968632] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   23.968634] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968636] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   23.968638] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968640] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   23.968642] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968643] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   23.968645] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968647] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   23.968649] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   23.968651] cfg80211: Disabling freq 2484 MHz
[   23.968654] cfg80211: Regulatory domain changed to country: AM
[   23.968655] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.968657] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   23.968659] cfg80211:     (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   23.968661] cfg80211:     (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   24.388016] HDMI status: Pin=4 Presence_Detect=0 ELD_Valid=0
[   24.412016] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   24.428160] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:04:00.1/sound/card1/input5
[   24.428265] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:04:00.1/sound/card1/input6
[   24.436594] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   24.752974] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   24.804594] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   27.056324] type=1400 audit(1329836936.821:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=979 comm="apparmor_parser"
[   27.057746] type=1400 audit(1329836936.821:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=978 comm="apparmor_parser"
[   27.058410] type=1400 audit(1329836936.821:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser
place" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser"
[   27.058608] type=1400 audit(1329836936.821:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser"
[   27.074268] type=1400 audit(1329836936.837:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=985 comm="apparmor_parser"
[   27.074980] type=1400 audit(1329836936.837:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=980 comm="apparmor_parser"
[   27.079472] type=1400 audit(1329836936.841:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=980 comm="apparmor_parser"
[   27.195777] atl2 0000:02:00.0: irq 44 for MSI/MSI-X
[   27.195949] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.237457] init: failsafe main process (928) killed by TERM signal
[   27.238668] init: apport pre-start process (1064) terminated with status 1
[   27.249785] init: apport post-stop process (1089) terminated with status 1
[   27.400592] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   27.400712] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.011049] Bluetooth: Core ver 2.16
[   28.011103] NET: Registered protocol family 31
[   28.011105] Bluetooth: HCI device and connection manager initialized
[   28.011107] Bluetooth: HCI socket layer initialized
[   28.011109] Bluetooth: L2CAP socket layer initialized
[   28.011132] Bluetooth: SCO socket layer initialized
[   28.014116] Bluetooth: RFCOMM TTY layer initialized
[   28.014121] Bluetooth: RFCOMM socket layer initialized
[   28.014122] Bluetooth: RFCOMM ver 1.11
[   28.014335] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.014337] Bluetooth: BNEP filters: protocol multicast
[   29.388612] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   29.514427] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   29.592273] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   38.136009] eth0: no IPv6 routers present
[   61.833417] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   61.833420] vesafb: scrolling: redraw
[   61.833422] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   61.834013] vesafb: framebuffer at 0xe7000000, mapped to 0xfa680000, using 1216k, total 1216k
[   61.834176] Console: switching to colour frame buffer device 80x30
[   61.834187] fb0: VESA VGA frame buffer device
[   61.849862] init: plymouth-splash main process (1748) terminated with status 1
[   61.859217] audit_printk_skb: 21 callbacks suppressed
[   61.859220] type=1400 audit(1329836970.645:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1765 comm="apparmor_parser"
[   61.859641] type=1400 audit(1329836970.645:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1765 comm="apparmor_parser"
[   63.889175] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   63.891566] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   63.893760] EXT4-fs (sda6): re-mounted. Opts: commit=0

```

---

### Post by che47audio on 2012-02-22
I'm experiencing pretty much exactly the same issue:

[http://ubuntuforums.org/showthread.php?t=1921305&highlight=che47audio]("http://ubuntuforums.org/showthread.php?t=1921305&highlight=che47audio")

Please let me know if you get anywhere, I will do the same.

---

### Post by alegomaster on 2012-02-22
You seem to have three items which take a while to initialize. 

The first is udevd which is a daemon that I believe you shouldn't tamper with.

The second is your ethernet connection which can't find an ipv6 router.

The third one is your graphics driver which is for intel boxes.

I am wondering if you did any modifications to any of these which may have caused a slowdown

---

### Post by wildmanne39 on 2012-02-22
Hi, for the ipv6 issue you can click on your network settings, edit connections, wireless ipv6 and set it to ignore that should take care of that issue.
Thanks

---

### Post by Pulka on 2012-03-09
Thank u for your replies.

Already deactivated IPV6 but it remains the same. 
Udevd? can i turn it off? How? What will it do if i turn it off?

About the graphic card, i made some changes in my hardware. I upgraded my cpu and graphic card. I'm not sure, but i think the problem existed before that upgrade.

---

### Post by Pulka on 2012-03-13
my computer takes about 4 minutes to boot. :mad:

---

### Post by gacb on 2012-11-10
Mine, at least the 32 bit version of 12.10 hangs for a full minute at nf-conntrack, but only for 5 seconds on my 64 bit version of Quantal.

Any ideas why this is happening?

---

### Post by rdsmith12 on 2012-12-25
I ran across this on one of my Ububoxes awhile back. 4 or 5 mins. to boot. I think it was looking at the 250Gb external USB hard drive for something to boot from or was at least reading the file system on it.

If I remember right, I even went into the bios and set the boot order for usb last but that didn't work.

After that I tried to remember to unplug all the USB drive before rebooting.

This was in your dmesg:
[    1.272016] usb 3-1: new low speed USB device number 2 using uhci_hcd
[    1.768014] usb 3-2: new low speed USB device number 3 using uhci_hcd
[    2.299883]  sdb: sdb1 < sdb5 >

Hope this is relevant.

---

