---
title: "after upgrade 10.04 to 12.04 lts my ubuntu becam crash"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by dikyiwan on 2013-12-17
i upgrade it with download  it from update manager after finisihing installing and restart it i can go insert  my ubuntu with my new kernel 3.2  but still work with my old kernel 2.6... i try  run it in recovery mode but stuck too....( i find some eroro on cannot allocated resource from esia slot1-8
it my demsg.txt i run from kernel 2.6 witch still work but crash if i open with kernel 3.2
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-50-generic (buildd@akateko) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #112-Ubuntu SMP Tue Jul 9 20:29:14 UTC 2013 (Ubuntu 2.6.32-50.112-generic 2.6.32.61+drm33.26)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffb8000 (usable)
[    0.000000]  BIOS-e820: 00000000bffb8000 - 00000000bffc0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffb8 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffb8000 (usable)
[    0.000000]  modified: 00000000bffb8000 - 00000000bffc0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  modified: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 36186000 - 370ba3d4
[    0.000000] ACPI: RSDP 000f9be0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bffc0000 0004C (v01 060209 RSDT1047 20090602 MSFT 00000097)
[    0.000000] ACPI: FACP bffc0200 00084 (v01 060209 FACP1047 20090602 MSFT 00000097)
[    0.000000] ACPI: DSDT bffc0690 094EE (v01  F83Se F83Se001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS bffce000 00040
[    0.000000] ACPI: APIC bffc0390 0006C (v01 060209 APIC1047 20090602 MSFT 00000097)
[    0.000000] ACPI: MCFG bffc0440 0003C (v01 060209 OEMMCFG  20090602 MSFT 00000097)
[    0.000000] ACPI: OEMX bffc0480 00176 (v01 060209 OEMX1047 20090602 MSFT 00000097)
[    0.000000] ACPI: ECDT bffc0630 00055 (v01 060209 OEMECDT  20090602 MSFT 00000097)
[    0.000000] ACPI: DBGP bffc0400 00034 (v01 060209 DBGP1047 20090602 MSFT 00000097)
[    0.000000] ACPI: BOOT bffc0600 00028 (v01 060209 BOOT1047 20090602 MSFT 00000097)
[    0.000000] ACPI: OEMB bffce040 00071 (v01 060209 OEMB1047 20090602 MSFT 00000097)
[    0.000000] ACPI: HPET bffc9b80 00038 (v01 060209 OEMHPET  20090602 MSFT 00000097)
[    0.000000] ACPI: SSDT bffced10 004E6 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2183MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e7ef8]    TEXT DATA BSS ==> [0000100000 - 00008e7ef8]
[    0.000000]   #4 [0036186000 - 00370ba3d4]          RAMDISK ==> [0036186000 - 00370ba3d4]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008e8000 - 00008eb15d]              BRK ==> [00008e8000 - 00008eb15d]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bffb8
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffb8
[    0.000000] On node 0 totalpages: 786247
[    0.000000] free_area_init_node: node 0, pgdat c07a2800, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4368 pages used for memmap
[    0.000000]   HighMem zone: 554666 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780103
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-50-generic root=UUID=b6810acf-f8e2-45a0-b2ba-e7620cb17ef1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15726880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bffb8)
[    0.000000] Memory: 3079112k/3145440k available (4704k kernel code, 64732k reserved, 2130k data, 664k init, 2236136k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07ad000 - 0xc0853000   ( 664 kB)
[    0.000000]       .data : 0xc0598337 - 0xc07acdc8   (2130 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0598337   (4704 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches HPET. 1 loops
[    0.000000] Detected 2532.608 MHz processor.
[    0.008008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5065.21 BogoMIPS (lpj=10130432)
[    0.008031] Security Framework initialized
[    0.008065] AppArmor: AppArmor initialized
[    0.008073] Mount-cache hash table entries: 512
[    0.008268] Initializing cgroup subsys ns
[    0.008273] Initializing cgroup subsys cpuacct
[    0.008277] Initializing cgroup subsys memory
[    0.008286] Initializing cgroup subsys devices
[    0.008289] Initializing cgroup subsys freezer
[    0.008291] Initializing cgroup subsys net_cls
[    0.008322] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008324] CPU: L2 cache: 3072K
[    0.008327] CPU: Physical Processor ID: 0
[    0.008328] CPU: Processor Core ID: 0
[    0.008333] mce: CPU supports 6 MCE banks
[    0.008344] CPU0: Thermal monitoring handled by SMI
[    0.008348] using mwait in idle threads.
[    0.008361] Performance Events: Core2 events, Intel PMU driver.
[    0.008369] ... version:                2
[    0.008370] ... bit width:              40
[    0.008372] ... generic registers:      2
[    0.008374] ... value mask:             000000ffffffffff
[    0.008375] ... max period:             000000007fffffff
[    0.008377] ... fixed-purpose events:   3
[    0.008378] ... event mask:             0000000700000003
[    0.008387] Checking 'hlt' instruction... OK.
[    0.026874] ACPI: Core revision 20090903
[    0.044009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044016] ftrace: allocating 21851 entries in 43 pages
[    0.048121] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048364] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.089734] CPU0: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.092005] Booting processor 1 APIC 0x1 ip 0x6000
[    0.012000] Initializing CPU#1
[    0.012000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.012000] CPU: L2 cache: 3072K
[    0.012000] CPU: Physical Processor ID: 0
[    0.012000] CPU: Processor Core ID: 1
[    0.012000] CPU1: Thermal monitoring handled by SMI
[    0.176131] CPU1: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.176137] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.180036] Brought up 2 CPUs
[    0.180038] Total of 2 processors activated (10130.32 BogoMIPS).
[    0.181257] CPU0 attaching sched-domain:
[    0.181262]  domain 0: span 0-1 level MC
[    0.181264]   groups: 0 1
[    0.181269] CPU1 attaching sched-domain:
[    0.181271]  domain 0: span 0-1 level MC
[    0.181273]   groups: 1 0
[    0.181335] devtmpfs: initialized
[    0.181335] regulator: core version 0.5
[    0.181335] Time: 14:04:28  Date: 12/17/13
[    0.181335] NET: Registered protocol family 16
[    0.181335] Trying to unpack rootfs image as initramfs...
[    0.181335] EISA bus registered
[    0.181335] ACPI: bus type pci registered
[    0.181335] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.181335] PCI: Not using MMCONFIG.
[    0.181335] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.181335] PCI: Using configuration type 1 for base access
[    0.188098] bio: create slab <bio-0> at 0
[    0.188947] ACPI: EC: EC description table is found, configuring boot EC
[    0.190035] ACPI: Executed 1 blocks of module-level executable AML code
[    0.198561] ACPI: Interpreter enabled
[    0.198567] ACPI: (supports S0 S3 S4 S5)
[    0.198589] ACPI: Using IOAPIC for interrupt routing
[    0.200504] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.202942] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.202944] PCI: Using MMCONFIG for extended config space
[    0.208298] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.208564] ACPI: No dock devices found.
[    0.208888] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.209031] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.209035] pci 0000:00:01.0: PME# disabled
[    0.209150] pci 0000:00:02.5: reg 20 io port: [0xfff0-0xffff]
[    0.209186] pci 0000:00:02.5: PME# supported from D3cold
[    0.209190] pci 0000:00:02.5: PME# disabled
[    0.209213] pci 0000:00:03.0: reg 10 32bit mmio: [0xfddff000-0xfddfffff]
[    0.209263] pci 0000:00:03.1: reg 10 32bit mmio: [0xfddfe000-0xfddfefff]
[    0.209323] pci 0000:00:03.3: reg 10 32bit mmio: [0xfddfd000-0xfddfdfff]
[    0.209383] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.209386] pci 0000:00:03.3: PME# disabled
[    0.209421] pci 0000:00:04.0: reg 10 32bit mmio: [0xfddfcc00-0xfddfcc7f]
[    0.209427] pci 0000:00:04.0: reg 14 io port: [0xcc00-0xcc7f]
[    0.209473] pci 0000:00:04.0: supports D1 D2
[    0.209474] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.209478] pci 0000:00:04.0: PME# disabled
[    0.209512] pci 0000:00:05.0: reg 10 io port: [0xc800-0xc807]
[    0.209518] pci 0000:00:05.0: reg 14 io port: [0xc400-0xc403]
[    0.209524] pci 0000:00:05.0: reg 18 io port: [0xc000-0xc007]
[    0.209530] pci 0000:00:05.0: reg 1c io port: [0xbc00-0xbc03]
[    0.209537] pci 0000:00:05.0: reg 20 io port: [0xb800-0xb80f]
[    0.209543] pci 0000:00:05.0: reg 24 io port: [0xb400-0xb47f]
[    0.209573] pci 0000:00:05.0: PME# supported from D3cold
[    0.209577] pci 0000:00:05.0: PME# disabled
[    0.209676] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.209681] pci 0000:00:06.0: PME# disabled
[    0.209789] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.209793] pci 0000:00:07.0: PME# disabled
[    0.209839] pci 0000:00:0f.0: reg 10 32bit mmio: [0xfddf4000-0xfddf7fff]
[    0.209890] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.209893] pci 0000:00:0f.0: PME# disabled
[    0.209951] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.209957] pci 0000:01:00.0: reg 14 io port: [0xd800-0xd8ff]
[    0.209964] pci 0000:01:00.0: reg 18 32bit mmio: [0xfdef0000-0xfdefffff]
[    0.209992] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfdec0000-0xfdedffff]
[    0.210034] pci 0000:01:00.0: supports D1 D2
[    0.210071] pci 0000:01:00.1: reg 10 32bit mmio: [0xfdeec000-0xfdeeffff]
[    0.210139] pci 0000:01:00.1: supports D1 D2
[    0.210189] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.210193] pci 0000:00:01.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.210199] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.210261] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdff0000-0xfdffffff]
[    0.210374] pci 0000:02:00.0: supports D1
[    0.210375] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.210381] pci 0000:02:00.0: PME# disabled
[    0.210453] pci 0000:00:06.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.210508] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.210512] pci 0000:00:07.0: bridge 32bit mmio: [0xfe000000-0xfebfffff]
[    0.210518] pci 0000:00:07.0: bridge 64bit mmio pref: [0xfa000000-0xfcffffff]
[    0.210533] pci_bus 0000:00: on NUMA node 0
[    0.210538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.217111] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.217238] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.217357] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14 15)
[    0.217476] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.217598] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.217717] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.217843] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.217962] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.218092] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.218095] vgaarb: loaded
[    0.218238] SCSI subsystem initialized
[    0.218350] libata version 3.00 loaded.
[    0.218416] usbcore: registered new interface driver usbfs
[    0.218427] usbcore: registered new interface driver hub
[    0.218577] usbcore: registered new device driver usb
[    0.218577] ACPI: WMI: Mapper loaded
[    0.218578] PCI: Using ACPI for IRQ routing
[    0.218839] NetLabel: Initializing
[    0.218841] NetLabel:  domain hash size = 128
[    0.218842] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.218855] NetLabel:  unlabeled traffic allowed by default
[    0.218884] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.218889] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.218893] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.224095] Switching to clocksource tsc
[    0.226080] AppArmor: AppArmor Filesystem Enabled
[    0.226095] pnp: PnP ACPI init
[    0.226111] ACPI: bus type pnp registered
[    0.228438] pnp: PnP ACPI: found 12 devices
[    0.228440] ACPI: ACPI bus type pnp unregistered
[    0.228444] PnPBIOS: Disabled by ACPI PNP
[    0.228459] system 00:06: ioport range 0x290-0x297 has been reserved
[    0.228461] system 00:06: ioport range 0xc00-0xc05 has been reserved
[    0.228464] system 00:06: ioport range 0xd00-0xd05 has been reserved
[    0.228466] system 00:06: ioport range 0x480-0x48f has been reserved
[    0.228468] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.228470] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.228473] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.228475] system 00:06: ioport range 0xc00-0xc7f could not be reserved
[    0.228478] system 00:06: ioport range 0x2000-0x20fe has been reserved
[    0.228481] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
[    0.228483] system 00:06: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.228486] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
[    0.228488] system 00:06: iomem range 0xfed10000-0xfed3ffff has been reserved
[    0.228494] system 00:09: ioport range 0x250-0x253 has been reserved
[    0.228496] system 00:09: ioport range 0x256-0x25f has been reserved
[    0.228499] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.228501] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.228506] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.228511] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.228514] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.228516] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.228518] system 00:0b: iomem range 0x100000-0xbfffffff could not be reserved
[    0.228521] system 00:0b: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.263236] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.263244] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.263250] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdefffff
[    0.263256] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.263264] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.263266] pci 0000:00:06.0:   IO window: disabled
[    0.263271] pci 0000:00:06.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.263275] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.263281] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.263284] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.263289] pci 0000:00:07.0:   MEM window: 0xfe000000-0xfebfffff
[    0.263294] pci 0000:00:07.0:   PREFETCH window: 0x000000fa000000-0x000000fcffffff
[    0.263319] pci 0000:00:01.0: setting latency timer to 64
[    0.263329] pci 0000:00:06.0: setting latency timer to 64
[    0.263339] pci 0000:00:07.0: setting latency timer to 64
[    0.263343] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.263345] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.263348] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.263350] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.263352] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.263354] pci_bus 0000:02: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.263357] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.263359] pci_bus 0000:03: resource 1 mem: [0xfe000000-0xfebfffff]
[    0.263361] pci_bus 0000:03: resource 2 pref mem [0xfa000000-0xfcffffff]
[    0.263414] NET: Registered protocol family 2
[    0.263538] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.263945] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.265020] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.265541] TCP: Hash tables configured (established 131072 bind 65536)
[    0.265543] TCP reno registered
[    0.265657] NET: Registered protocol family 1
[    0.265693]   alloc irq_desc for 20 on node -1
[    0.265695]   alloc kstat_irqs on node -1
[    0.265705] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.323757] pci 0000:00:03.0: PCI INT A disabled
[    0.323776]   alloc irq_desc for 21 on node -1
[    0.323778]   alloc kstat_irqs on node -1
[    0.323785] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.347741] pci 0000:00:03.1: PCI INT B disabled
[    0.347762]   alloc irq_desc for 22 on node -1
[    0.347763]   alloc kstat_irqs on node -1
[    0.347769] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.347786] pci 0000:00:03.3: PCI INT C disabled
[    0.347797] pci 0000:01:00.0: Boot video device
[    0.347836] Simple Boot Flag at 0x71 set to 0x1
[    0.348018] cpufreq-nforce2: No nForce2 chipset.
[    0.348046] Scanning for low memory corruption every 60 seconds
[    0.348168] audit: initializing netlink socket (disabled)
[    0.348186] type=2000 audit(1387289067.347:1): initialized
[    0.356719] highmem bounce pool size: 64 pages
[    0.356727] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.358090] VFS: Disk quotas dquot_6.5.2
[    0.358146] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.358658] fuse init (API version 7.13)
[    0.358731] msgmni has been set to 1648
[    0.358948] alg: No test for stdrng (krng)
[    0.358996] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.358999] io scheduler noop registered
[    0.359000] io scheduler anticipatory registered
[    0.359002] io scheduler deadline registered
[    0.359034] io scheduler cfq registered (default)
[    0.359168]   alloc irq_desc for 24 on node -1
[    0.359170]   alloc kstat_irqs on node -1
[    0.359181] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.359190] pcieport 0000:00:01.0: setting latency timer to 64
[    0.359301]   alloc irq_desc for 25 on node -1
[    0.359303]   alloc kstat_irqs on node -1
[    0.359310] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.359318] pcieport 0000:00:06.0: setting latency timer to 64
[    0.359444]   alloc irq_desc for 26 on node -1
[    0.359446]   alloc kstat_irqs on node -1
[    0.359453] pcieport 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.359461] pcieport 0000:00:07.0: setting latency timer to 64
[    0.359535] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.359563] Firmware did not grant requested _OSC control
[    0.359597] Firmware did not grant requested _OSC control
[    0.359612] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.359782] ACPI: AC Adapter [AC0] (on-line)
[    0.359850] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.359855] ACPI: Power Button [PWRB]
[    0.359890] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.359897] ACPI: Sleep Button [SLPB]
[    0.359932] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.361103] ACPI: Lid Switch [LID]
[    0.361142] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.361145] ACPI: Power Button [PWRF]
[    0.361777] ACPI: SSDT bffce390 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.362361] ACPI: SSDT bffce630 006DC (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.362820] Monitor-Mwait will be used to enter C-1 state
[    0.371641] Monitor-Mwait will be used to enter C-2 state
[    0.371652] Marking TSC unstable due to TSC halts in idle
[    0.371715] processor LNXCPU:00: registered as cooling_device0
[    0.372107] ACPI: SSDT bffce2c0 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.372455] ACPI: SSDT bffce5a0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.372976] processor LNXCPU:01: registered as cooling_device1
[    0.374600] Switching to clocksource hpet
[    0.376637] thermal LNXTHERM:01: registered as thermal_zone0
[    0.376647] ACPI: Thermal Zone [THRM] (52 C)
[    0.378028] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.379279] brd: module loaded
[    0.379702] loop: module loaded
[    0.379777] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.379897] pata_sis 0000:00:02.5: version 0.5.2
[    0.380011] scsi0 : pata_sis
[    0.380075] scsi1 : pata_sis
[    0.380624] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    0.380626] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    0.380663]   alloc irq_desc for 17 on node -1
[    0.380665]   alloc kstat_irqs on node -1
[    0.380672] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.380707] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.380959] Fixed MDIO Bus: probed
[    0.380991] PPP generic driver version 2.4.2
[    0.381019] tun: Universal TUN/TAP device driver, 1.6
[    0.381021] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.381106] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.381118] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.381131] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.381173] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.381230] ehci_hcd 0000:00:03.3: irq 22, io mem 0xfddfd000
[    0.381269] isapnp: Scanning for PnP cards...
[    0.430698] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.430874] usb usb1: configuration #1 chosen from 1 choice
[    0.430903] hub 1-0:1.0: USB hub found
[    0.430914] hub 1-0:1.0: 8 ports detected
[    0.430982] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.431009] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.431035] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.431074] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.431102] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfddff000
[    0.431252] ACPI: Battery Slot [BAT0] (battery present)
[    0.520532] usb usb2: configuration #1 chosen from 1 choice
[    0.520562] hub 2-0:1.0: USB hub found
[    0.520575] hub 2-0:1.0: 4 ports detected
[    0.520638] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.520668] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.520707] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.520755] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfddfe000
[    0.584306] Freeing initrd memory: 15568k freed
[    0.610108] usb usb3: configuration #1 chosen from 1 choice
[    0.610144] hub 3-0:1.0: USB hub found
[    0.610164] hub 3-0:1.0: 4 ports detected
[    0.610244] uhci_hcd: USB Universal Host Controller Interface driver
[    0.610390] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.613490] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.615348] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.615354] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.615379] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.615397] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.615420] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.615526] mice: PS/2 mouse device common for all mice
[    0.615699] rtc_cmos 00:08: RTC can wake from S4
[    0.615745] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.615765] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    0.615858] device-mapper: uevent: version 1.0.3
[    0.616001] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.616071] device-mapper: multipath: version 1.1.0 loaded
[    0.616074] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.616182] EISA: Probing bus 0 at eisa.0
[    0.616192] Cannot allocate resource for EISA slot 2
[    0.616212] EISA: Detected 0 cards.
[    0.616341] cpuidle: using governor ladder
[    0.616418] cpuidle: using governor menu
[    0.616833] TCP cubic registered
[    0.616973] NET: Registered protocol family 10
[    0.617755] NET: Registered protocol family 17
[    0.618285] Using IPI No-Shortcut mode
[    0.618359] PM: Resume from disk failed.
[    0.618376] registered taskstats version 1
[    0.618670]   Magic number: 9:312:81
[    0.618783] rtc_cmos 00:08: setting system clock to 2013-12-17 14:04:28 UTC (1387289068)
[    0.618786] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.618788] EDD information not available.
[    0.651900] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.744015] isapnp: No Plug & Play device found
[    0.744077] ata2: port disabled. ignoring.
[    0.744109] Freeing unused kernel memory: 664k freed
[    0.744738] Write protecting the kernel text: 4708k
[    0.744773] Write protecting the kernel read-only data: 1848k
[    0.760225] <30>udevd[92]: starting version 175
[    0.812043] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.824204] sis190 Gigabit Ethernet driver 1.3 loaded.
[    0.824233]   alloc irq_desc for 19 on node -1
[    0.824235]   alloc kstat_irqs on node -1
[    0.824242] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.824260] sis190 0000:00:04.0: setting latency timer to 64
[    0.824278] 0000:00:04.0: Read MAC address from EEPROM
[    0.824280] 0000:00:04.0: Error EEPROM read 0.
[    0.824283] 0000:00:04.0: Read MAC address from APC.
[    0.826844] vga16fb: initializing
[    0.826847] vga16fb: mapped to 0xc00a0000
[    0.826905] fb0: VGA16 VGA frame buffer device
[    0.827106] Linux agpgart interface v0.103
[    0.866727] acpi device:17: registered as cooling_device2
[    0.866821] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:14/LNXVIDEO:00/input/input6
[    0.866872] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    0.872187] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[    0.988340] usb 1-2: configuration #1 chosen from 1 choice
[    0.992919] Console: switching to colour frame buffer device 80x30
[    1.348020] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.368017] 0000:00:04.0: Using transceiver at address 1 as default.
[    1.400576] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8086c00 (IRQ: 19), 90:e6:ba:19:da:fb
[    1.400578] eth0: GMII mode.
[    1.400583] eth0: Enabling Auto-negotiation.
[    1.432039] sata_sis 0000:00:05.0: version 1.0
[    1.432059] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.432066] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.432239] scsi2 : sata_sis
[    1.432308] scsi3 : sata_sis
[    1.432851] ata3: PATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb800 irq 17
[    1.432854] ata4: PATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb808 irq 17
[    1.560490] usb 2-2: configuration #1 chosen from 1 choice
[    1.596626] ata3.00: ATA-8: ST9500325AS, 0002SDM1, max UDMA/133
[    1.596631] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.612663] ata3.00: configured for UDMA/133
[    1.612810] scsi 2:0:0:0: Direct-Access     ATA      ST9500325AS      0002 PQ: 0 ANSI: 5
[    1.612917] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.612936] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.612958] sd 2:0:0:0: [sda] Write Protect is off
[    1.612960] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.612985] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.613116]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.688563] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.776736] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RR09, max UDMA/133
[    1.792255] ata4.00: configured for UDMA/133
[    1.797666] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RR09 PQ: 0 ANSI: 5
[    1.808876] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.808880] Uniform CD-ROM driver Revision: 3.20
[    1.808996] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.809036] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.812876] usbcore: registered new interface driver hiddev
[    1.818593] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input7
[    1.818677] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:03.0-2/input0
[    1.818701] usbcore: registered new interface driver usbhid
[    1.818703] usbhid: v2.6:USB HID core driver
[    3.839693] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.839696] EXT3-fs: write access will be enabled during recovery.
[    8.544327] kjournald starting.  Commit interval 5 seconds
[    8.544360] EXT3-fs: recovery complete.
[    8.550788] EXT3-fs: mounted filesystem with ordered data mode.
[   28.984272] Adding 1951856k swap on /dev/sda6.  Priority:-1 extents:1 across:1951856k 
[   29.037144] <30>udevd[506]: starting version 175
[   29.090328] lp: driver loaded but no devices found
[   29.238727] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   29.238732] Disabling lock debugging due to kernel taint
[   29.413114] [fglrx] Maximum main memory to use for locked dma buffers: 2877 MBytes.
[   29.413432] [fglrx]   vendor: 1002 device: 9553 count: 1
[   29.414306] [fglrx] ioport: bar 1, base 0xd800, size: 0x100
[   29.414327]   alloc irq_desc for 16 on node -1
[   29.414329]   alloc kstat_irqs on node -1
[   29.414337] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.414342] pci 0000:01:00.0: setting latency timer to 64
[   29.414546] [fglrx] Kernel PAT support is enabled
[   29.414568] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   29.427084] cfg80211: Calling CRDA to update world regulatory domain
[   29.428263] asus_laptop: Asus Laptop Support version 0.42
[   29.434971] asus_laptop:   F83Se model detected
[   29.442201] cfg80211: World regulatory domain updated:
[   29.442204]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.442206]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.442208]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.442210]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.442212]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.442214]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.449052] Linux video capture interface: v2.00
[   29.455458] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.455473] ath9k 0000:02:00.0: setting latency timer to 64
[   29.458926] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   29.483677] input: CNF7129 as /devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2:1.0/input/input8
[   29.483728] usbcore: registered new interface driver uvcvideo
[   29.483730] USB Video Class driver (v0.1.0)
[   29.505181] ath: EEPROM regdomain: 0x60
[   29.505184] ath: EEPROM indicates we should expect a direct regpair map
[   29.505188] ath: Country alpha2 being used: 00
[   29.505189] ath: Regpair used: 0x60
[   29.506928] input: Asus Laptop extra buttons as /devices/virtual/input/input9
[   29.508400] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   29.530106]   alloc irq_desc for 18 on node -1
[   29.530109]   alloc kstat_irqs on node -1
[   29.530117] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   29.530153] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   29.531320] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   29.531962] Registered led device: ath9k-phy0::radio
[   29.531977] Registered led device: ath9k-phy0::assoc
[   29.531991] Registered led device: ath9k-phy0::tx
[   29.532062] Registered led device: ath9k-phy0::rx
[   29.532076] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8ae0000, irq=16
[   29.613136] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:0f.0/input/input10
[   29.622141] HDA Intel 0000:01:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[   29.622203] HDA Intel 0000:01:00.1: setting latency timer to 64
[   29.826336] type=1505 audit(1387263897.705:2):  operation="profile_load" pid=761 name="/sbin/dhclient"
[   29.826366] type=1505 audit(1387263897.705:3):  operation="profile_replace" pid=702 name="/sbin/dhclient"
[   29.826735] type=1505 audit(1387263897.705:4):  operation="profile_load" pid=761 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.826768] type=1505 audit(1387263897.705:5):  operation="profile_replace" pid=702 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.826959] type=1505 audit(1387263897.705:6):  operation="profile_load" pid=761 name="/usr/lib/connman/scripts/dhclient-script"
[   29.826997] type=1505 audit(1387263897.705:7):  operation="profile_replace" pid=702 name="/usr/lib/connman/scripts/dhclient-script"
[   29.828354] type=1505 audit(1387263897.705:8):  operation="profile_replace" pid=655 name="/sbin/dhclient"
[   29.828764] type=1505 audit(1387263897.709:9):  operation="profile_replace" pid=655 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.828999] type=1505 audit(1387263897.709:10):  operation="profile_replace" pid=655 name="/usr/lib/connman/scripts/dhclient-script"
[   30.007497] EXT3 FS on sda7, internal journal
[   30.124756] init: failsafe main process (851) killed by TERM signal
[   30.147260] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   30.185429] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   30.213438] type=1505 audit(1387263898.093:11):  operation="profile_load" pid=921 name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper"
[   30.226730] Bluetooth: Core ver 2.15
[   30.236649] NET: Registered protocol family 31
[   30.236654] Bluetooth: HCI device and connection manager initialized
[   30.236660] Bluetooth: HCI socket layer initialized
[   30.260395] Bluetooth: L2CAP ver 2.14
[   30.260397] Bluetooth: L2CAP socket layer initialized
[   30.274010] ppdev: user-space parallel port driver
[   30.275675] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.275677] Bluetooth: BNEP filters: protocol multicast
[   30.279446] Bluetooth: SCO (Voice Link) ver 0.6
[   30.279448] Bluetooth: SCO socket layer initialized
[   30.554945] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.610173] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.622173] init: gdm main process (1103) killed by TERM signal
[   31.144682]   alloc irq_desc for 27 on node -1
[   31.144685]   alloc kstat_irqs on node -1
[   31.144698] fglrx_pci 0000:01:00.0: irq 27 for MSI/MSI-X
[   31.145681] [fglrx] Firegl kernel thread PID: 1252
[   31.145782] [fglrx] Firegl kernel thread PID: 1253
[   31.145879] [fglrx] Firegl kernel thread PID: 1254
[   31.146036] [fglrx] IRQ 27 Enabled
[   31.198202] CPU0 attaching NULL sched-domain.
[   31.198209] CPU1 attaching NULL sched-domain.
[   31.248575] CPU0 attaching sched-domain:
[   31.248578]  domain 0: span 0-1 level MC
[   31.248580]   groups: 0 1
[   31.248585] CPU1 attaching sched-domain:
[   31.248586]  domain 0: span 0-1 level MC
[   31.248588]   groups: 1 0
[   31.436440] [fglrx] Gart USWC size:944 M.
[   31.436444] [fglrx] Gart cacheable size:373 M.
[   31.436449] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   31.436451] [fglrx] Reserved FB block: Unshared offset:fd0b000, size:2f5000 
[   31.436453] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   34.153814] CPU0 attaching NULL sched-domain.
[   34.153819] CPU1 attaching NULL sched-domain.
[   34.176106] CPU0 attaching sched-domain:
[   34.176111]  domain 0: span 0-1 level MC
[   34.176115]   groups: 0 1
[   34.176128] CPU1 attaching sched-domain:
[   34.176129]  domain 0: span 0-1 level MC
[   34.176131]   groups: 1 0
[   36.131136] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   36.274559] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   40.584021] eth0: mii ext = 0000.
[   40.608019] eth0: mii lpa=c5e1 adv=01e1 exp=0001.
[   40.624017] eth0: link on unknown mode.
[   40.656019] eth0: mii ext = 0000.
[   40.680019] eth0: mii lpa=c5e1 adv=01e1 exp=0001.
[   40.696019] eth0: link on unknown mode.
[   40.696214] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   47.354506] wlan0: direct probe to AP f8:1a:67:f5:16:da (try 1)
[   47.359597] wlan0: direct probe responded
[   47.359602] wlan0: authenticate with AP f8:1a:67:f5:16:da (try 1)
[   47.369081] wlan0: authenticated
[   47.369368] wlan0: associate with AP f8:1a:67:f5:16:da (try 1)
[   47.373475] wlan0: RX AssocResp from f8:1a:67:f5:16:da (capab=0x411 status=0 aid=1)
[   47.373482] wlan0: associated
[   47.383114] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.384450] cfg80211: Calling CRDA for country: US
[   47.388955] cfg80211: Received country IE:
[   47.388959] cfg80211: Regulatory domain: US
[   47.388960]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.388963]     (2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   47.388964] cfg80211: CRDA thinks this should applied:
[   47.388965] cfg80211: Regulatory domain: US
[   47.388967]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.388969]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   47.388971]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   47.388973]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.388975]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.388976]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.388978]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   47.388980] cfg80211: We intersect both of these and get:
[   47.388981] cfg80211: Regulatory domain: 98
[   47.388982]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.388984]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   47.388989] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   47.388990] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   47.388992] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   47.388997] cfg80211: Current regulatory domain updated by AP to: US
[   47.388998]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.389001]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   47.800690] padlock: VIA PadLock not detected.
[   51.140020] eth0: no IPv6 routers present
[   57.944511] wlan0: no IPv6 routers present
```

---

### Post by monkeybrain20122 on 2013-12-17
It is probably a bad upgrade. The upgrade manager method for upgrading may have improved in recent releases, but definitely full of issues back in 10.04. Make a live usb of 12.04 and see if it works on your computer. If yes, then save your data and do a fresh install. There has been so much change going from 10.04 to 12.04 it would be daunting to try to fix a bad upgrade and even if someone (not me. :)) manages to help you get it to work for now, who knows what other problems may be hidden and shows up later as strange undiagnosable issues.

---

