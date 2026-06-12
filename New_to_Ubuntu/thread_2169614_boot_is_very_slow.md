---
title: "boot is very slow"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by pnaarmann on 2013-08-22
Hello Ubuntu forum, :)

I just installed Ubuntu 13.04 a few days ago and it is my first experience with a linux distribution.

Slowly I am starting to know the system, but encounter many difficulties.

Something I cannot figure out by searching google and forums is my slow boot time. It takes over a minute and my Windows 8 is up in about 15 seconds.

I looked in the dmesg-file and saw big gaps in the log, but did not find a good answer through searching for the lines.

So, here is the log:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-29-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 (Ubuntu 3.8.0-29.42-generic 3.8.13.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=cb79b948-f67b-4a77-99c5-17ece94ecbff ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009abff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ac00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cff7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cff80000-0x00000000cff97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cff98000-0x00000000cffbffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cffc0000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A87, BIOS 1402    11/15/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000022f000000 aka 8944M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000094000] 94000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcff7ffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcff7ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcff7ffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22effffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000]  [mem 0x200000000-0x22effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22effffff @ [mem 0xcff7e000-0xcff7ffff]
[    0.000000] RAMDISK: [mem 0x344be000-0x36256fff]
[    0.000000] ACPI: RSDP 00000000000fb850 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff80100 00054 (v01 111512 XSDT1057 20121115 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 111512 FACP1057 20121115 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff80460 0D051 (v01  A1866 A1866001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff98000 00040
[    0.000000] ACPI: APIC 00000000cff80390 0008C (v01 111512 APIC1057 20121115 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff80420 0003C (v01 111512 OEMMCFG  20121115 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 111512 OEMB1057 20121115 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff8f8b0 00038 (v01 111512 OEMHPET  20121115 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff8f8f0 01158 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22effffff]
[    0.000000]   NODE_DATA [mem 0x22effb000-0x22effffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226600000-ffff88022e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00099fff]
[    0.000000]   node   0: [mem 0x00100000-0xcff7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22effffff]
[    0.000000] On node 0 totalpages: 2092810
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3908 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13246 pages used for memmap
[    0.000000]   DMA32 zone: 834498 pages, LIFO batch:31
[    0.000000]   Normal zone: 19392 pages used for memmap
[    0.000000]   Normal zone: 1221696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x16] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 22, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
[    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffc0000
[    0.000000] PM: Registered nosave memory: 00000000cffc0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xff9fffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022ec00000 s85056 r8192 d21440 u262144
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2060102
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=cb79b948-f67b-4a77-99c5-17ece94ecbff ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 8061552k/9158656k available (7013k kernel code, 787416k absent, 309688k reserved, 6229k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3499.776 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6999.55 BogoMIPS (lpj=13999104)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000036] AppArmor: AppArmor initialized
[    0.000037] Yama: becoming mindful.
[    0.000507] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002365] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003163] Mount-cache hash table entries: 256
[    0.003305] Initializing cgroup subsys cpuacct
[    0.003307] Initializing cgroup subsys memory
[    0.003313] Initializing cgroup subsys devices
[    0.003315] Initializing cgroup subsys freezer
[    0.003316] Initializing cgroup subsys blkio
[    0.003317] Initializing cgroup subsys perf_event
[    0.003319] Initializing cgroup subsys hugetlb
[    0.003338] tseg: 0000000000
[    0.003346] CPU: Physical Processor ID: 0
[    0.003347] CPU: Processor Core ID: 0
[    0.003348] mce: CPU supports 7 MCE banks
[    0.003354] LVT offset 1 assigned for vector 0xf9
[    0.003359] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.003359] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.003359] tlb_flushall_shift: 5
[    0.003443] Freeing SMP alternatives: 24k freed
[    0.004778] ACPI: Core revision 20121018
[    0.010237] ftrace: allocating 26712 entries in 105 pages
[    0.018429] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058035] smpboot: CPU0: AMD FX(tm)-6300 Six-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.164767] Performance Events: 
[    0.164769] perf: AMD core performance counters detected
[    0.164771] AMD PMU driver.
[    0.164772] ... version:                0
[    0.164773] ... bit width:              48
[    0.164774] ... generic registers:      6
[    0.164775] ... value mask:             0000ffffffffffff
[    0.164776] ... max period:             00007fffffffffff
[    0.164777] ... fixed-purpose events:   0
[    0.164778] ... event mask:             000000000000003f
[    0.165677] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.165738] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5
[    0.231489] Brought up 6 CPUs
[    0.231492] smpboot: Total of 6 processors activated (41997.31 BogoMIPS)
[    0.239279] devtmpfs: initialized
[    0.240556] EVM: security.selinux
[    0.240558] EVM: security.SMACK64
[    0.240559] EVM: security.capability
[    0.240609] PM: Registering ACPI NVS region [mem 0xcff98000-0xcffbffff] (163840 bytes)
[    0.241293] regulator-dummy: no parameters
[    0.241334] NET: Registered protocol family 16
[    0.241490] ACPI: bus type pci registered
[    0.241534] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.241536] PCI: not using MMCONFIG
[    0.241537] PCI: Using configuration type 1 for base access
[    0.241538] PCI: Using configuration type 1 for extended access
[    0.241734] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.241735] mtrr: probably your BIOS does not setup all CPUs.
[    0.241736] mtrr: corrected configuration.
[    0.242491] bio: create slab <bio-0> at 0
[    0.242574] ACPI: Added _OSI(Module Device)
[    0.242575] ACPI: Added _OSI(Processor Device)
[    0.242577] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.242578] ACPI: Added _OSI(Processor Aggregator Device)
[    0.243875] ACPI: EC: Look up EC in DSDT
[    0.245409] ACPI: Executed 3 blocks of module-level executable AML code
[    0.344275] ACPI: Interpreter enabled
[    0.344279] ACPI: (supports S0 S1 S3 S4 S5)
[    0.344299] ACPI: Using IOAPIC for interrupt routing
[    0.344320] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.345117] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.361846] ACPI: No dock devices found.
[    0.361850] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.361937] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.361939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.362384] PCI host bridge to bus 0000:00
[    0.362387] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.362389] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.362391] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.362393] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.362394] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.362396] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.362397] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.362407] pci 0000:00:00.0: [1002:5957] type 00 class 0x060000
[    0.362451] pci 0000:00:02.0: [1002:5978] type 01 class 0x060400
[    0.362484] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.362498] pci 0000:00:04.0: [1002:597a] type 01 class 0x060400
[    0.362528] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.362543] pci 0000:00:07.0: [1002:597d] type 01 class 0x060400
[    0.362574] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.362588] pci 0000:00:0a.0: [1002:597f] type 01 class 0x060400
[    0.362618] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.362642] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.362660] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.362668] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.362676] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.362685] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.362693] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.362702] pci 0000:00:11.0: reg 24: [mem 0xf9fffc00-0xf9ffffff]
[    0.362755] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.362767] pci 0000:00:12.0: reg 10: [mem 0xf9ffe000-0xf9ffefff]
[    0.362831] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.362848] pci 0000:00:12.2: reg 10: [mem 0xf9fff800-0xf9fff8ff]
[    0.362922] pci 0000:00:12.2: supports D1 D2
[    0.362923] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.362945] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.362957] pci 0000:00:13.0: reg 10: [mem 0xf9ffd000-0xf9ffdfff]
[    0.363021] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.363038] pci 0000:00:13.2: reg 10: [mem 0xf9fff400-0xf9fff4ff]
[    0.363112] pci 0000:00:13.2: supports D1 D2
[    0.363113] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.363134] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.363204] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.363223] pci 0000:00:14.2: reg 10: [mem 0xf9ff4000-0xf9ff7fff 64bit]
[    0.363282] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.363295] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.363363] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.363401] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.363412] pci 0000:00:14.5: reg 10: [mem 0xf9ffc000-0xf9ffcfff]
[    0.363474] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.363485] pci 0000:00:16.0: reg 10: [mem 0xf9ff3000-0xf9ff3fff]
[    0.363550] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.363567] pci 0000:00:16.2: reg 10: [mem 0xf9fff000-0xf9fff0ff]
[    0.363641] pci 0000:00:16.2: supports D1 D2
[    0.363643] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.363662] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.363681] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.363695] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.363709] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.363727] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.363741] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.363791] pci 0000:01:00.0: [10de:1200] type 00 class 0x030000
[    0.363801] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfbffffff]
[    0.363810] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.363820] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.363827] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.363834] pci 0000:01:00.0: reg 30: [mem 0xfce80000-0xfcefffff pref]
[    0.363888] pci 0000:01:00.1: [10de:0e0c] type 00 class 0x040300
[    0.363898] pci 0000:01:00.1: reg 10: [mem 0xfce7c000-0xfce7ffff]
[    0.371936] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.371940] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.371942] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfcefffff]
[    0.371945] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.371982] pci 0000:02:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.371999] pci 0000:02:00.0: reg 10: [mem 0xfcff8000-0xfcffffff 64bit]
[    0.372082] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.379916] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.379920] pci 0000:00:04.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.379958] pci 0000:03:00.0: [1102:000b] type 00 class 0x040300
[    0.379977] pci 0000:03:00.0: reg 10: [mem 0xfebe0000-0xfebeffff 64bit]
[    0.379992] pci 0000:03:00.0: reg 18: [mem 0xfe800000-0xfe9fffff 64bit]
[    0.380007] pci 0000:03:00.0: reg 20: [mem 0xfd000000-0xfdffffff 64bit]
[    0.387900] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.387905] pci 0000:00:07.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.387940] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.387952] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.387972] pci 0000:04:00.0: reg 18: [mem 0xf8fff000-0xf8ffffff 64bit pref]
[    0.387985] pci 0000:04:00.0: reg 20: [mem 0xf8ff8000-0xf8ffbfff 64bit pref]
[    0.388038] pci 0000:04:00.0: supports D1 D2
[    0.388040] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.395887] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.395891] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.395895] pci 0000:00:0a.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.395950] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
[    0.395958] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.395960] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.395961] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.395963] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.395964] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.395966] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.395988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.396022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.396054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.396083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.396119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.396287]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.396448]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.397539] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 14 15)
[    0.397598] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 14 15)
[    0.397658] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 14 15)
[    0.397715] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 *10 11 14 15)
[    0.397760] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.397794] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.397828] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.397861] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.397947] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.397949] vgaarb: loaded
[    0.397950] vgaarb: bridge control possible 0000:01:00.0
[    0.398099] SCSI subsystem initialized
[    0.398101] ACPI: bus type scsi registered
[    0.398152] libata version 3.00 loaded.
[    0.398168] ACPI: bus type usb registered
[    0.398181] usbcore: registered new interface driver usbfs
[    0.398188] usbcore: registered new interface driver hub
[    0.398209] usbcore: registered new device driver usb
[    0.398288] PCI: Using ACPI for IRQ routing
[    0.405933] PCI: pci_cache_line_size set to 64 bytes
[    0.405992] e820: reserve RAM buffer [mem 0x0009ac00-0x0009ffff]
[    0.405994] e820: reserve RAM buffer [mem 0xcff80000-0xcfffffff]
[    0.405995] e820: reserve RAM buffer [mem 0x22f000000-0x22fffffff]
[    0.406063] NetLabel: Initializing
[    0.406065] NetLabel:  domain hash size = 128
[    0.406065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.406076] NetLabel:  unlabeled traffic allowed by default
[    0.406117] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.406120] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.408141] Switching to clocksource hpet
[    0.413307] AppArmor: AppArmor Filesystem Enabled
[    0.413320] pnp: PnP ACPI init
[    0.413328] ACPI: bus type pnp registered
[    0.413379] pnp 00:00: [dma 4]
[    0.413395] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.413422] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.413441] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.413460] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.413758] pnp 00:04: [dma 0 disabled]
[    0.413860] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.413935] system 00:05: [io  0x0290-0x029f] has been reserved
[    0.413937] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.413983] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.414040] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.414257] pnp 00:08: [dma 0 disabled]
[    0.414315] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.414414] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.414416] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.414418] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414629] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.414631] system 00:0a: [io  0x040b] has been reserved
[    0.414633] system 00:0a: [io  0x04d6] has been reserved
[    0.414635] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.414637] system 00:0a: [io  0x0c14] has been reserved
[    0.414638] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.414640] system 00:0a: [io  0x0c52] has been reserved
[    0.414642] system 00:0a: [io  0x0c6c] has been reserved
[    0.414643] system 00:0a: [io  0x0c6f] has been reserved
[    0.414645] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.414647] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.414649] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.414650] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.414652] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.414654] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.414656] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.414657] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
[    0.414659] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.414661] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.414663] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.414664] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.414667] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.414669] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.414670] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.414672] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.414675] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414725] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.414727] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414855] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.414858] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.414860] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.414861] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.414863] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.414865] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.414953] pnp: PnP ACPI: found 13 devices
[    0.414954] ACPI: ACPI bus type pnp unregistered
[    0.421179] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.421182] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.421185] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfcefffff]
[    0.421187] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.421190] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.421193] pci 0000:00:04.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.421197] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.421199] pci 0000:00:07.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.421203] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.421205] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.421208] pci 0000:00:0a.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.421211] pci 0000:00:14.4: PCI bridge to [bus 05]
[    0.421242] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.421244] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.421246] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421247] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421249] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.421250] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.421252] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.421253] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfcefffff]
[    0.421255] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.421257] pci_bus 0000:02: resource 1 [mem 0xfcf00000-0xfcffffff]
[    0.421258] pci_bus 0000:03: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.421260] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.421261] pci_bus 0000:04: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.421263] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.421264] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.421266] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421267] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421269] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.421270] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.421292] NET: Registered protocol family 2
[    0.421449] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421679] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421853] TCP: Hash tables configured (established 65536 bind 65536)
[    0.421878] TCP: reno registered
[    0.421890] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421923] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421990] NET: Registered protocol family 1
[    1.522036] pci 0000:01:00.0: Boot video device
[    1.522078] PCI: CLS 64 bytes, default 64
[    1.522113] Trying to unpack rootfs image as initramfs...
[    1.909449] Freeing initrd memory: 30308k freed
[    1.915458] PCI-DMA: Disabling AGP.
[    1.915538] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.915539] PCI-DMA: using GART IOMMU.
[    1.915542] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.919928] LVT offset 0 assigned for vector 0x400
[    1.919958] perf: AMD IBS detected (0x000000ff)
[    1.920165] Initialise module verification
[    1.920196] audit: initializing netlink socket (disabled)
[    1.920205] type=2000 audit(1377215301.808:1): initialized
[    1.941571] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.943008] VFS: Disk quotas dquot_6.5.2
[    1.943040] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.943446] fuse init (API version 7.20)
[    1.943506] msgmni has been set to 15933
[    1.943924] Key type asymmetric registered
[    1.943926] Asymmetric key parser 'x509' registered
[    1.943951] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.943976] io scheduler noop registered
[    1.943978] io scheduler deadline registered (default)
[    1.943982] io scheduler cfq registered
[    1.944082] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.944140] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.944195] pcieport 0000:00:07.0: irq 42 for MSI/MSI-X
[    1.944251] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
[    1.944305] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    1.944307] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.944309] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.944311] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    1.944321] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.944322] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.944324] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    1.944335] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    1.944337] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.944339] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    1.944348] pcieport 0000:00:0a.0: Signaling PME through PCIe PME interrupt
[    1.944350] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.944352] pcie_pme 0000:00:0a.0:pcie01: service driver pcie_pme loaded
[    1.944363] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.944376] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.944457] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.944461] ACPI: Power Button [PWRB]
[    1.944492] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.944494] ACPI: Power Button [PWRF]
[    1.944830] ACPI: acpi_idle registered with cpuidle
[    1.948634] GHES: HEST is not enabled!
[    1.948698] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.969117] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.970297] Linux agpgart interface v0.103
[    1.971354] brd: module loaded
[    1.971912] loop: module loaded
[    1.972175] libphy: Fixed MDIO Bus: probed
[    1.972222] tun: Universal TUN/TAP device driver, 1.6
[    1.972224] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.972257] PPP generic driver version 2.4.2
[    1.972291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.972292] ehci-pci: EHCI PCI platform driver
[    1.972328] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.972333] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.972341] QUIRK: Enable AMD PLL fix
[    1.972342] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.972352] ehci-pci 0000:00:12.2: debug port 1
[    1.972382] ehci-pci 0000:00:12.2: irq 17, io mem 0xf9fff800
[    1.981069] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.981085] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.981087] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.981088] usb usb1: Product: EHCI Host Controller
[    1.981090] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.981091] usb usb1: SerialNumber: 0000:00:12.2
[    1.981176] hub 1-0:1.0: USB hub found
[    1.981180] hub 1-0:1.0: 5 ports detected
[    1.981267] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.981270] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.981273] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.981283] ehci-pci 0000:00:13.2: debug port 1
[    1.981303] ehci-pci 0000:00:13.2: irq 17, io mem 0xf9fff400
[    1.993055] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.993067] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.993068] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.993070] usb usb2: Product: EHCI Host Controller
[    1.993071] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.993072] usb usb2: SerialNumber: 0000:00:13.2
[    1.993145] hub 2-0:1.0: USB hub found
[    1.993149] hub 2-0:1.0: 5 ports detected
[    1.993234] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.993239] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.993242] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.993252] ehci-pci 0000:00:16.2: debug port 1
[    1.993272] ehci-pci 0000:00:16.2: irq 17, io mem 0xf9fff000
[    2.005034] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.005047] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.005049] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.005050] usb usb3: Product: EHCI Host Controller
[    2.005052] usb usb3: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    2.005053] usb usb3: SerialNumber: 0000:00:16.2
[    2.005120] hub 3-0:1.0: USB hub found
[    2.005122] hub 3-0:1.0: 4 ports detected
[    2.005186] ehci-platform: EHCI generic platform driver
[    2.005192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.005213] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.005217] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.005235] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf9ffe000
[    2.064896] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.064898] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.064900] usb usb4: Product: OHCI Host Controller
[    2.064901] usb usb4: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.064902] usb usb4: SerialNumber: 0000:00:12.0
[    2.064981] hub 4-0:1.0: USB hub found
[    2.064986] hub 4-0:1.0: 5 ports detected
[    2.065059] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.065062] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.065073] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffd000
[    2.124791] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.124793] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.124794] usb usb5: Product: OHCI Host Controller
[    2.124796] usb usb5: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.124797] usb usb5: SerialNumber: 0000:00:13.0
[    2.124876] hub 5-0:1.0: USB hub found
[    2.124881] hub 5-0:1.0: 5 ports detected
[    2.124958] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.124962] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.124973] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ffc000
[    2.184663] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.184665] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.184667] usb usb6: Product: OHCI Host Controller
[    2.184668] usb usb6: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.184670] usb usb6: SerialNumber: 0000:00:14.5
[    2.184743] hub 6-0:1.0: USB hub found
[    2.184748] hub 6-0:1.0: 2 ports detected
[    2.184807] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.184811] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.184825] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf9ff3000
[    2.244541] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.244543] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.244545] usb usb7: Product: OHCI Host Controller
[    2.244546] usb usb7: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.244547] usb usb7: SerialNumber: 0000:00:16.0
[    2.244623] hub 7-0:1.0: USB hub found
[    2.244628] hub 7-0:1.0: 4 ports detected
[    2.244687] uhci_hcd: USB Universal Host Controller Interface driver
[    2.244719] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.244722] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    2.254339] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    2.254344] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    2.254349] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    2.254354] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    2.254359] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    2.254364] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    2.254369] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[    2.254448] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    2.254450] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254452] usb usb8: Product: xHCI Host Controller
[    2.254453] usb usb8: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    2.254454] usb usb8: SerialNumber: 0000:02:00.0
[    2.254511] xHCI xhci_add_endpoint called for root hub
[    2.254513] xHCI xhci_check_bandwidth called for root hub
[    2.254528] hub 8-0:1.0: USB hub found
[    2.254533] hub 8-0:1.0: 2 ports detected
[    2.254576] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.254579] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.254601] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    2.254603] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254604] usb usb9: Product: xHCI Host Controller
[    2.254605] usb usb9: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    2.254607] usb usb9: SerialNumber: 0000:02:00.0
[    2.254655] xHCI xhci_add_endpoint called for root hub
[    2.254656] xHCI xhci_check_bandwidth called for root hub
[    2.254669] hub 9-0:1.0: USB hub found
[    2.254674] hub 9-0:1.0: 2 ports detected
[    2.254807] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.254809] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.255289] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.255377] mousedev: PS/2 mouse device common for all mice
[    2.255481] rtc_cmos 00:01: RTC can wake from S4
[    2.255573] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.255594] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.255663] device-mapper: uevent: version 1.0.3
[    2.255715] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.255778] cpuidle: using governor ladder
[    2.255868] cpuidle: using governor menu
[    2.255871] ledtrig-cpu: registered to indicate activity on CPUs
[    2.255873] EFI Variables Facility v0.08 2004-May-17
[    2.256031] ashmem: initialized
[    2.256119] TCP: cubic registered
[    2.256191] NET: Registered protocol family 10
[    2.256315] NET: Registered protocol family 17
[    2.256321] Key type dns_resolver registered
[    2.256737] Loading module verification certificates
[    2.257479] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d8bc1516bb9827ccf9ced525fc4133574da45d40'
[    2.257486] registered taskstats version 1
[    2.259927] Key type trusted registered
[    2.261845] Key type encrypted registered
[    2.263786] rtc_cmos 00:01: setting system clock to 2013-08-22 23:48:22 UTC (1377215302)
[    2.263823] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    2.264720] acpi-cpufreq: overriding BIOS provided _PSD data
[    2.265256] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.265257] EDD information not available.
[    2.267521] Freeing unused kernel memory: 996k freed
[    2.267701] Write protecting the kernel read-only data: 12288k
[    2.272306] Freeing unused kernel memory: 1168k freed
[    2.276267] Freeing unused kernel memory: 1076k freed
[    2.287770] udevd[124]: starting version 175
[    2.291180] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.309598] Disabling lock debugging due to kernel taint
[    2.310196] ahci 0000:00:11.0: version 3.0
[    2.310321] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.310325] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.311457] scsi0 : ahci
[    2.311548] scsi1 : ahci
[    2.311623] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.311827] r8169 0000:04:00.0: irq 51 for MSI/MSI-X
[    2.311920] scsi2 : ahci
[    2.311979] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c7c000, f4:6d:04:cf:61:7c, XID 0c900800 IRQ 51
[    2.311981] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.312041] scsi3 : ahci
[    2.312117] scsi4 : ahci
[    2.312177] scsi5 : ahci
[    2.312223] ata1: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd00 irq 19
[    2.312226] ata2: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd80 irq 19
[    2.312229] ata3: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe00 irq 19
[    2.312231] ata4: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe80 irq 19
[    2.312234] ata5: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff00 irq 19
[    2.312236] ata6: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff80 irq 19
[    2.799524] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.799561] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.799592] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.800132] ata2.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    2.800135] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.800181] ata1.00: ATA-9: OCZ-AGILITY4, 1.4, max UDMA/133
[    2.800183] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.800972] ata1.00: configured for UDMA/133
[    2.800999] ata2.00: configured for UDMA/133
[    2.801131] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB06, max UDMA/66
[    2.801209] scsi 0:0:0:0: Direct-Access     ATA      OCZ-AGILITY4     1.4  PQ: 0 ANSI: 5
[    2.801340] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.801355] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.801468] sd 0:0:0:0: [sda] Write Protect is off
[    2.801470] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.801489] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    2.801507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.801578] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.801628] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.801638] sd 1:0:0:0: [sdb] Write Protect is off
[    2.801641] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.801659] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.801922]  sda: sda1
[    2.802191] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.803450] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.803521] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.803547] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.805911] ata4.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    2.805913] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.808099] ata4.00: configured for UDMA/133
[    2.809999] ata6.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    2.810006] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.811493] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.815174] ata5.00: ATA-8: KINGSTON SV300S37A120G, 505ABBF1, max UDMA/133
[    2.815181] ata5.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.816643] ata6.00: configured for UDMA/133
[    2.825043] ata5.00: configured for UDMA/133
[    2.826931]  sdb: sdb1
[    2.827343] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.915280] tsc: Refined TSC clocksource calibration: 3499.904 MHz
[    2.915289] Switching to clocksource tsc
[    2.943733] usb 2-1: New USB device found, idVendor=0409, idProduct=005a
[    2.943736] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.943925] hub 2-1:1.0: USB hub found
[    2.944024] hub 2-1:1.0: 4 ports detected
[    3.466178] usb 5-3: new full-speed USB device number 2 using ohci_hcd
[    3.600969] ata3.00: configured for UDMA/66
[    3.691771] usb 5-3: New USB device found, idVendor=0a12, idProduct=0001
[    3.691778] usb 5-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.084950] usb 4-2: new full-speed USB device number 2 using ohci_hcd
[    4.364432] usb 4-2: New USB device found, idVendor=0471, idProduct=0329
[    4.364439] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    4.364445] usb 4-2: SerialNumber: 01690000F54901B1
[    4.401394] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB06 PQ: 0 ANSI: 5
[    4.406464] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.406470] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.406670] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.406739] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    4.406867] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    4.406965] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.406982] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    4.407040] sd 3:0:0:0: [sdc] Write Protect is off
[    4.407042] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.407066] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.407097] scsi 4:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 505A PQ: 0 ANSI: 5
[    4.407253] sd 4:0:0:0: [sdd] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    4.407271] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    4.407306] sd 4:0:0:0: [sdd] Write Protect is off
[    4.407309] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.407329] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.407380] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    4.407496] sd 5:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.407529] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    4.407593] sd 5:0:0:0: [sde] Write Protect is off
[    4.407595] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.407621] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.409668]  sdd: sdd1 sdd2 < sdd5 >
[    4.410108] sd 4:0:0:0: [sdd] Attached SCSI disk
[    4.416474]  sde: sde1
[    4.416870] sd 5:0:0:0: [sde] Attached SCSI disk
[    4.423784]  sdc: sdc1
[    4.424160] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.627873] usb 4-5: new full-speed USB device number 3 using ohci_hcd
[    4.800562] usb 4-5: New USB device found, idVendor=046d, idProduct=c245
[    4.800569] usb 4-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.800574] usb 4-5: Product: Gaming Mouse G400
[    4.800578] usb 4-5: Manufacturer: Logitech
[    4.816639] usbcore: registered new interface driver usbhid
[    4.816645] usbhid: USB HID core driver
[    4.819003] input: Logitech Gaming Mouse G400 as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input3
[    4.819098] hid-generic 0003:046D:C245.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input0
[    4.821750] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input1
[   34.887829] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   34.887837] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   34.887847] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   34.887847]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   34.887853] ata3.00: status: { DRDY }
[   34.887860] ata3: hard resetting link
[   35.378860] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   36.180311] ata3.00: configured for PIO4
[   36.979455] ata3: EH complete
[   67.782599] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   67.782607] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   67.782616] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   67.782616]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   67.782622] ata3.00: status: { DRDY }
[   67.782628] ata3: hard resetting link
[   68.273581] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   69.074982] ata3.00: configured for PIO4
[   69.874099] ata3: EH complete
[   75.987368] EXT3-fs (sdd1): recovery required on readonly filesystem
[   75.987370] EXT3-fs (sdd1): write access will be enabled during recovery
[   76.112097] kjournald starting.  Commit interval 5 seconds
[   76.112913] EXT3-fs (sdd1): recovery complete
[   76.112916] EXT3-fs (sdd1): mounted filesystem with ordered data mode
[   76.263163] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.267197] init: bootchart main process (466) terminated with status 127
[   76.275109] udevd[480]: starting version 175
[   76.305805] lp: driver loaded but no devices found
[   76.311221] nvidia: module license 'NVIDIA' taints kernel.
[   76.312366] w83627ehf: Found NCT6776F chip at 0x290
[   76.312395] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SIOE 1 (20121018/utaddress-251)
[   76.312400] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.SIOR.HWRE 2 (20121018/utaddress-251)
[   76.312404] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   76.321211] EXT3-fs (sdd1): using internal journal
[   76.324671] wmi: Mapper loaded
[   76.331233] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   76.331380] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.44  Wed Mar 27 14:51:30 PDT 2013
[   76.342632] type=1400 audit(1377208176.723:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=558 comm="apparmor_parser"
[   76.342914] type=1400 audit(1377208176.723:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=558 comm="apparmor_parser"
[   76.343071] type=1400 audit(1377208176.723:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=558 comm="apparmor_parser"
[   76.394662] Linux video capture interface: v2.00
[   76.397232] init: bootchart post-stop process (477) terminated with status 127
[   76.402820] pwc: Philips SPC 900NC USB webcam detected.
[   76.403701] parport_pc 00:04: reported by Plug and Play ACPI
[   76.403750] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   76.417152] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input4
[   76.417259] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input5
[   76.417451] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
[   76.417575] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[   76.418235] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   76.422505] hda_intel: Disabling MSI
[   76.422513] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   76.446520] MCE: In-kernel MCE decoding enabled.
[   76.448661] EDAC MC: Ver: 3.0.0
[   76.452564] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20121018/utaddress-251)
[   76.452571] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 2 (20121018/utaddress-251)
[   76.452575] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   76.453744] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   76.453793] sp5100_tco: PCI Revision ID: 0x42
[   76.453829] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   76.453841] sp5100_tco: Last reboot was not triggered by watchdog.
[   76.454223] sp5100_tco: initialized (0xffffc90000c7eb00). heartbeat=60 sec (nowayout=0)
[   76.455977] AMD64 EDAC driver v3.4.0
[   76.456002] EDAC amd64: DRAM ECC disabled.
[   76.456013] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   76.456013]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   76.456013]  (Note that use of the override may cause unknown side effects.)
[   76.469078] microcode: CPU0: patch_level=0x0600081c
[   76.471274] microcode: CPU1: patch_level=0x0600081c
[   76.471418] microcode: CPU2: patch_level=0x0600081c
[   76.471424] microcode: CPU3: patch_level=0x0600081c
[   76.471431] microcode: CPU4: patch_level=0x0600081c
[   76.471439] microcode: CPU5: patch_level=0x0600081c
[   76.471487] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   76.487925] kvm: disabled by bios
[   76.493824] lp0: using parport0 (interrupt-driven).
[   76.531607] ppdev: user-space parallel port driver
[   76.555745] init: avahi-cups-reload main process (750) terminated with status 1
[   76.575604] type=1400 audit(1377208176.955:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=806 comm="apparmor_parser"
[   76.575956] type=1400 audit(1377208176.955:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=806 comm="apparmor_parser"
[   76.580883] Bluetooth: Core ver 2.16
[   76.580907] NET: Registered protocol family 31
[   76.580909] Bluetooth: HCI device and connection manager initialized
[   76.583587] Bluetooth: HCI socket layer initialized
[   76.583589] Bluetooth: L2CAP socket layer initialized
[   76.583594] Bluetooth: SCO socket layer initialized
[   76.591518] Bluetooth: RFCOMM TTY layer initialized
[   76.591526] Bluetooth: RFCOMM socket layer initialized
[   76.591528] Bluetooth: RFCOMM ver 1.11
[   76.592019] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   76.592021] Bluetooth: BNEP filters: protocol multicast
[   76.592055] Bluetooth: BNEP socket layer initialized
[   76.601145] usbcore: registered new interface driver btusb
[   76.633427] pwc: Registered as video0.
[   76.633472] input: PWC snapshot button as /devices/pci0000:00/0000:00:12.0/usb4/4-2/input/input9
[   76.634321] usbcore: registered new interface driver Philips webcam
[   76.674687] init: failsafe main process (848) killed by TERM signal
[   76.716893] usbcore: registered new interface driver snd-usb-audio
[   76.724859] type=1400 audit(1377208177.107:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=978 comm="apparmor_parser"
[   76.725111] type=1400 audit(1377208177.107:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=978 comm="apparmor_parser"
[   76.725353] type=1400 audit(1377208177.107:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=979 comm="apparmor_parser"
[   76.726946] type=1400 audit(1377208177.107:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=977 comm="apparmor_parser"
[   76.727180] type=1400 audit(1377208177.107:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=977 comm="apparmor_parser"

```

Does anyone have a clue what it is about? :confused:

Thank You!

---

### Post by Ikaru on 2013-08-23
From my experience, linux boots slowly. I too had that same experience with Windows 8 booting faster than my Ubuntu but that can be explained as Windows 8 uses some sort of hybrid hibernation when booting, thus making it faster.

I have a core 2 duo with 3GB RAM and ubuntu boot time has always been slow (up to a minute). I think it all depends on the specs of you PC and not by the simple fact that you are running linux. 
And if you think about it boot speed is not that important. What really is important is the speed within the OS, running applications and processes.

---

### Post by pnaarmann on 2013-08-23
I have a six core processor with 8GB RAM. Alos I am using a SSD. I think it should be a lot faster when there is nothing wrong.

What is worrying me, is that something is not installed correctly or some hardware damaged.

After I pick Ubuntu in the bootmanager, I have a black screen with a blinking line in the top left corner for about 30 seconds. (You can also see the gap in the log I posted in the first post)

Do you know what it means?

---

### Post by Ikaru on 2013-08-23
Well, I am no expert but I get the blank screen with blinking line too. So, I think it's normal. 
As for the boot time I think it should be faster in your case given the specs of your machine. The Ubuntu boot time in modern machines is around 8 to 10 seconds, i think.

Sorry I can't help your further, maybe someone with more experience can help you out and point you in the right direction.

---

### Post by pnaarmann on 2013-08-23
Thank you anyway!

Hopefully someone can tell me more about my log.

---

### Post by Andrew_Lucas on 2013-08-23
> **pnaarmann said:**
> Hello Ubuntu forum, :)

I just installed Ubuntu 13.04 a few days ago and it is my first experience with a linux distribution.

Slowly I am starting to know the system, but encounter many difficulties.

Something I cannot figure out by searching google and forums is my slow boot time. It takes over a minute and my Windows 8 is up in about 15 seconds.

I looked in the dmesg-file and saw big gaps in the log, but did not find a good answer through searching for the lines.

So, here is the log:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-29-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 (Ubuntu 3.8.0-29.42-generic 3.8.13.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=cb79b948-f67b-4a77-99c5-17ece94ecbff ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009abff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ac00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cff7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cff80000-0x00000000cff97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cff98000-0x00000000cffbffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cffc0000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A87, BIOS 1402    11/15/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000022f000000 aka 8944M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000094000] 94000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcff7ffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcff7ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcff7ffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22effffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000]  [mem 0x200000000-0x22effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22effffff @ [mem 0xcff7e000-0xcff7ffff]
[    0.000000] RAMDISK: [mem 0x344be000-0x36256fff]
[    0.000000] ACPI: RSDP 00000000000fb850 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff80100 00054 (v01 111512 XSDT1057 20121115 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 111512 FACP1057 20121115 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff80460 0D051 (v01  A1866 A1866001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff98000 00040
[    0.000000] ACPI: APIC 00000000cff80390 0008C (v01 111512 APIC1057 20121115 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff80420 0003C (v01 111512 OEMMCFG  20121115 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 111512 OEMB1057 20121115 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff8f8b0 00038 (v01 111512 OEMHPET  20121115 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff8f8f0 01158 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22effffff]
[    0.000000]   NODE_DATA [mem 0x22effb000-0x22effffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226600000-ffff88022e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00099fff]
[    0.000000]   node   0: [mem 0x00100000-0xcff7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22effffff]
[    0.000000] On node 0 totalpages: 2092810
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3908 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13246 pages used for memmap
[    0.000000]   DMA32 zone: 834498 pages, LIFO batch:31
[    0.000000]   Normal zone: 19392 pages used for memmap
[    0.000000]   Normal zone: 1221696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x16] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 22, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
[    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffc0000
[    0.000000] PM: Registered nosave memory: 00000000cffc0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xff9fffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022ec00000 s85056 r8192 d21440 u262144
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2060102
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=cb79b948-f67b-4a77-99c5-17ece94ecbff ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 8061552k/9158656k available (7013k kernel code, 787416k absent, 309688k reserved, 6229k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3499.776 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6999.55 BogoMIPS (lpj=13999104)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000036] AppArmor: AppArmor initialized
[    0.000037] Yama: becoming mindful.
[    0.000507] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002365] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003163] Mount-cache hash table entries: 256
[    0.003305] Initializing cgroup subsys cpuacct
[    0.003307] Initializing cgroup subsys memory
[    0.003313] Initializing cgroup subsys devices
[    0.003315] Initializing cgroup subsys freezer
[    0.003316] Initializing cgroup subsys blkio
[    0.003317] Initializing cgroup subsys perf_event
[    0.003319] Initializing cgroup subsys hugetlb
[    0.003338] tseg: 0000000000
[    0.003346] CPU: Physical Processor ID: 0
[    0.003347] CPU: Processor Core ID: 0
[    0.003348] mce: CPU supports 7 MCE banks
[    0.003354] LVT offset 1 assigned for vector 0xf9
[    0.003359] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.003359] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.003359] tlb_flushall_shift: 5
[    0.003443] Freeing SMP alternatives: 24k freed
[    0.004778] ACPI: Core revision 20121018
[    0.010237] ftrace: allocating 26712 entries in 105 pages
[    0.018429] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058035] smpboot: CPU0: AMD FX(tm)-6300 Six-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.164767] Performance Events: 
[    0.164769] perf: AMD core performance counters detected
[    0.164771] AMD PMU driver.
[    0.164772] ... version:                0
[    0.164773] ... bit width:              48
[    0.164774] ... generic registers:      6
[    0.164775] ... value mask:             0000ffffffffffff
[    0.164776] ... max period:             00007fffffffffff
[    0.164777] ... fixed-purpose events:   0
[    0.164778] ... event mask:             000000000000003f
[    0.165677] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.165738] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5
[    0.231489] Brought up 6 CPUs
[    0.231492] smpboot: Total of 6 processors activated (41997.31 BogoMIPS)
[    0.239279] devtmpfs: initialized
[    0.240556] EVM: security.selinux
[    0.240558] EVM: security.SMACK64
[    0.240559] EVM: security.capability
[    0.240609] PM: Registering ACPI NVS region [mem 0xcff98000-0xcffbffff] (163840 bytes)
[    0.241293] regulator-dummy: no parameters
[    0.241334] NET: Registered protocol family 16
[    0.241490] ACPI: bus type pci registered
[    0.241534] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.241536] PCI: not using MMCONFIG
[    0.241537] PCI: Using configuration type 1 for base access
[    0.241538] PCI: Using configuration type 1 for extended access
[    0.241734] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.241735] mtrr: probably your BIOS does not setup all CPUs.
[    0.241736] mtrr: corrected configuration.
[    0.242491] bio: create slab <bio-0> at 0
[    0.242574] ACPI: Added _OSI(Module Device)
[    0.242575] ACPI: Added _OSI(Processor Device)
[    0.242577] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.242578] ACPI: Added _OSI(Processor Aggregator Device)
[    0.243875] ACPI: EC: Look up EC in DSDT
[    0.245409] ACPI: Executed 3 blocks of module-level executable AML code
[    0.344275] ACPI: Interpreter enabled
[    0.344279] ACPI: (supports S0 S1 S3 S4 S5)
[    0.344299] ACPI: Using IOAPIC for interrupt routing
[    0.344320] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.345117] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.361846] ACPI: No dock devices found.
[    0.361850] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.361937] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.361939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.362384] PCI host bridge to bus 0000:00
[    0.362387] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.362389] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.362391] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.362393] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.362394] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.362396] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.362397] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.362407] pci 0000:00:00.0: [1002:5957] type 00 class 0x060000
[    0.362451] pci 0000:00:02.0: [1002:5978] type 01 class 0x060400
[    0.362484] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.362498] pci 0000:00:04.0: [1002:597a] type 01 class 0x060400
[    0.362528] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.362543] pci 0000:00:07.0: [1002:597d] type 01 class 0x060400
[    0.362574] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.362588] pci 0000:00:0a.0: [1002:597f] type 01 class 0x060400
[    0.362618] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.362642] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.362660] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.362668] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.362676] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.362685] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.362693] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.362702] pci 0000:00:11.0: reg 24: [mem 0xf9fffc00-0xf9ffffff]
[    0.362755] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.362767] pci 0000:00:12.0: reg 10: [mem 0xf9ffe000-0xf9ffefff]
[    0.362831] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.362848] pci 0000:00:12.2: reg 10: [mem 0xf9fff800-0xf9fff8ff]
[    0.362922] pci 0000:00:12.2: supports D1 D2
[    0.362923] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.362945] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.362957] pci 0000:00:13.0: reg 10: [mem 0xf9ffd000-0xf9ffdfff]
[    0.363021] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.363038] pci 0000:00:13.2: reg 10: [mem 0xf9fff400-0xf9fff4ff]
[    0.363112] pci 0000:00:13.2: supports D1 D2
[    0.363113] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.363134] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.363204] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.363223] pci 0000:00:14.2: reg 10: [mem 0xf9ff4000-0xf9ff7fff 64bit]
[    0.363282] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.363295] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.363363] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.363401] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.363412] pci 0000:00:14.5: reg 10: [mem 0xf9ffc000-0xf9ffcfff]
[    0.363474] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.363485] pci 0000:00:16.0: reg 10: [mem 0xf9ff3000-0xf9ff3fff]
[    0.363550] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.363567] pci 0000:00:16.2: reg 10: [mem 0xf9fff000-0xf9fff0ff]
[    0.363641] pci 0000:00:16.2: supports D1 D2
[    0.363643] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.363662] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.363681] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.363695] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.363709] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.363727] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.363741] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.363791] pci 0000:01:00.0: [10de:1200] type 00 class 0x030000
[    0.363801] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfbffffff]
[    0.363810] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.363820] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.363827] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.363834] pci 0000:01:00.0: reg 30: [mem 0xfce80000-0xfcefffff pref]
[    0.363888] pci 0000:01:00.1: [10de:0e0c] type 00 class 0x040300
[    0.363898] pci 0000:01:00.1: reg 10: [mem 0xfce7c000-0xfce7ffff]
[    0.371936] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.371940] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.371942] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfcefffff]
[    0.371945] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.371982] pci 0000:02:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.371999] pci 0000:02:00.0: reg 10: [mem 0xfcff8000-0xfcffffff 64bit]
[    0.372082] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.379916] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.379920] pci 0000:00:04.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.379958] pci 0000:03:00.0: [1102:000b] type 00 class 0x040300
[    0.379977] pci 0000:03:00.0: reg 10: [mem 0xfebe0000-0xfebeffff 64bit]
[    0.379992] pci 0000:03:00.0: reg 18: [mem 0xfe800000-0xfe9fffff 64bit]
[    0.380007] pci 0000:03:00.0: reg 20: [mem 0xfd000000-0xfdffffff 64bit]
[    0.387900] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.387905] pci 0000:00:07.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.387940] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.387952] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.387972] pci 0000:04:00.0: reg 18: [mem 0xf8fff000-0xf8ffffff 64bit pref]
[    0.387985] pci 0000:04:00.0: reg 20: [mem 0xf8ff8000-0xf8ffbfff 64bit pref]
[    0.388038] pci 0000:04:00.0: supports D1 D2
[    0.388040] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.395887] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.395891] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.395895] pci 0000:00:0a.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.395950] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
[    0.395958] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.395960] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.395961] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.395963] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.395964] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.395966] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.395988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.396022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.396054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.396083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.396119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.396287]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.396448]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.397539] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 14 15)
[    0.397598] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 14 15)
[    0.397658] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 14 15)
[    0.397715] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 *10 11 14 15)
[    0.397760] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.397794] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.397828] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.397861] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.397947] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.397949] vgaarb: loaded
[    0.397950] vgaarb: bridge control possible 0000:01:00.0
[    0.398099] SCSI subsystem initialized
[    0.398101] ACPI: bus type scsi registered
[    0.398152] libata version 3.00 loaded.
[    0.398168] ACPI: bus type usb registered
[    0.398181] usbcore: registered new interface driver usbfs
[    0.398188] usbcore: registered new interface driver hub
[    0.398209] usbcore: registered new device driver usb
[    0.398288] PCI: Using ACPI for IRQ routing
[    0.405933] PCI: pci_cache_line_size set to 64 bytes
[    0.405992] e820: reserve RAM buffer [mem 0x0009ac00-0x0009ffff]
[    0.405994] e820: reserve RAM buffer [mem 0xcff80000-0xcfffffff]
[    0.405995] e820: reserve RAM buffer [mem 0x22f000000-0x22fffffff]
[    0.406063] NetLabel: Initializing
[    0.406065] NetLabel:  domain hash size = 128
[    0.406065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.406076] NetLabel:  unlabeled traffic allowed by default
[    0.406117] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.406120] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.408141] Switching to clocksource hpet
[    0.413307] AppArmor: AppArmor Filesystem Enabled
[    0.413320] pnp: PnP ACPI init
[    0.413328] ACPI: bus type pnp registered
[    0.413379] pnp 00:00: [dma 4]
[    0.413395] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.413422] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.413441] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.413460] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.413758] pnp 00:04: [dma 0 disabled]
[    0.413860] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.413935] system 00:05: [io  0x0290-0x029f] has been reserved
[    0.413937] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.413983] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.414040] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.414257] pnp 00:08: [dma 0 disabled]
[    0.414315] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.414414] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.414416] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.414418] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414629] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.414631] system 00:0a: [io  0x040b] has been reserved
[    0.414633] system 00:0a: [io  0x04d6] has been reserved
[    0.414635] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.414637] system 00:0a: [io  0x0c14] has been reserved
[    0.414638] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.414640] system 00:0a: [io  0x0c52] has been reserved
[    0.414642] system 00:0a: [io  0x0c6c] has been reserved
[    0.414643] system 00:0a: [io  0x0c6f] has been reserved
[    0.414645] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.414647] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.414649] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.414650] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.414652] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.414654] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.414656] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.414657] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
[    0.414659] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.414661] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.414663] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.414664] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.414667] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.414669] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.414670] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.414672] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.414675] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414725] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.414727] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414855] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.414858] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.414860] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.414861] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.414863] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.414865] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.414953] pnp: PnP ACPI: found 13 devices
[    0.414954] ACPI: ACPI bus type pnp unregistered
[    0.421179] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.421182] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.421185] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfcefffff]
[    0.421187] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.421190] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.421193] pci 0000:00:04.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.421197] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.421199] pci 0000:00:07.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.421203] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.421205] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.421208] pci 0000:00:0a.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.421211] pci 0000:00:14.4: PCI bridge to [bus 05]
[    0.421242] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.421244] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.421246] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421247] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421249] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.421250] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.421252] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.421253] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfcefffff]
[    0.421255] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.421257] pci_bus 0000:02: resource 1 [mem 0xfcf00000-0xfcffffff]
[    0.421258] pci_bus 0000:03: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.421260] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.421261] pci_bus 0000:04: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.421263] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.421264] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.421266] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421267] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421269] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.421270] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.421292] NET: Registered protocol family 2
[    0.421449] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421679] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421853] TCP: Hash tables configured (established 65536 bind 65536)
[    0.421878] TCP: reno registered
[    0.421890] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421923] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421990] NET: Registered protocol family 1
[    1.522036] pci 0000:01:00.0: Boot video device
[    1.522078] PCI: CLS 64 bytes, default 64
[    1.522113] Trying to unpack rootfs image as initramfs...
[    1.909449] Freeing initrd memory: 30308k freed
[    1.915458] PCI-DMA: Disabling AGP.
[    1.915538] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.915539] PCI-DMA: using GART IOMMU.
[    1.915542] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.919928] LVT offset 0 assigned for vector 0x400
[    1.919958] perf: AMD IBS detected (0x000000ff)
[    1.920165] Initialise module verification
[    1.920196] audit: initializing netlink socket (disabled)
[    1.920205] type=2000 audit(1377215301.808:1): initialized
[    1.941571] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.943008] VFS: Disk quotas dquot_6.5.2
[    1.943040] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.943446] fuse init (API version 7.20)
[    1.943506] msgmni has been set to 15933
[    1.943924] Key type asymmetric registered
[    1.943926] Asymmetric key parser 'x509' registered
[    1.943951] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.943976] io scheduler noop registered
[    1.943978] io scheduler deadline registered (default)
[    1.943982] io scheduler cfq registered
[    1.944082] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.944140] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.944195] pcieport 0000:00:07.0: irq 42 for MSI/MSI-X
[    1.944251] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
[    1.944305] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    1.944307] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.944309] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.944311] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    1.944321] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.944322] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.944324] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    1.944335] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    1.944337] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.944339] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    1.944348] pcieport 0000:00:0a.0: Signaling PME through PCIe PME interrupt
[    1.944350] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.944352] pcie_pme 0000:00:0a.0:pcie01: service driver pcie_pme loaded
[    1.944363] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.944376] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.944457] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.944461] ACPI: Power Button [PWRB]
[    1.944492] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.944494] ACPI: Power Button [PWRF]
[    1.944830] ACPI: acpi_idle registered with cpuidle
[    1.948634] GHES: HEST is not enabled!
[    1.948698] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.969117] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.970297] Linux agpgart interface v0.103
[    1.971354] brd: module loaded
[    1.971912] loop: module loaded
[    1.972175] libphy: Fixed MDIO Bus: probed
[    1.972222] tun: Universal TUN/TAP device driver, 1.6
[    1.972224] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.972257] PPP generic driver version 2.4.2
[    1.972291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.972292] ehci-pci: EHCI PCI platform driver
[    1.972328] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.972333] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.972341] QUIRK: Enable AMD PLL fix
[    1.972342] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.972352] ehci-pci 0000:00:12.2: debug port 1
[    1.972382] ehci-pci 0000:00:12.2: irq 17, io mem 0xf9fff800
[    1.981069] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.981085] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.981087] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.981088] usb usb1: Product: EHCI Host Controller
[    1.981090] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.981091] usb usb1: SerialNumber: 0000:00:12.2
[    1.981176] hub 1-0:1.0: USB hub found
[    1.981180] hub 1-0:1.0: 5 ports detected
[    1.981267] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.981270] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.981273] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.981283] ehci-pci 0000:00:13.2: debug port 1
[    1.981303] ehci-pci 0000:00:13.2: irq 17, io mem 0xf9fff400
[    1.993055] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.993067] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.993068] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.993070] usb usb2: Product: EHCI Host Controller
[    1.993071] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.993072] usb usb2: SerialNumber: 0000:00:13.2
[    1.993145] hub 2-0:1.0: USB hub found
[    1.993149] hub 2-0:1.0: 5 ports detected
[    1.993234] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.993239] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.993242] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.993252] ehci-pci 0000:00:16.2: debug port 1
[    1.993272] ehci-pci 0000:00:16.2: irq 17, io mem 0xf9fff000
[    2.005034] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.005047] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.005049] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.005050] usb usb3: Product: EHCI Host Controller
[    2.005052] usb usb3: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    2.005053] usb usb3: SerialNumber: 0000:00:16.2
[    2.005120] hub 3-0:1.0: USB hub found
[    2.005122] hub 3-0:1.0: 4 ports detected
[    2.005186] ehci-platform: EHCI generic platform driver
[    2.005192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.005213] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.005217] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.005235] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf9ffe000
[    2.064896] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.064898] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.064900] usb usb4: Product: OHCI Host Controller
[    2.064901] usb usb4: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.064902] usb usb4: SerialNumber: 0000:00:12.0
[    2.064981] hub 4-0:1.0: USB hub found
[    2.064986] hub 4-0:1.0: 5 ports detected
[    2.065059] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.065062] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.065073] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffd000
[    2.124791] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.124793] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.124794] usb usb5: Product: OHCI Host Controller
[    2.124796] usb usb5: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.124797] usb usb5: SerialNumber: 0000:00:13.0
[    2.124876] hub 5-0:1.0: USB hub found
[    2.124881] hub 5-0:1.0: 5 ports detected
[    2.124958] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.124962] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.124973] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ffc000
[    2.184663] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.184665] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.184667] usb usb6: Product: OHCI Host Controller
[    2.184668] usb usb6: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.184670] usb usb6: SerialNumber: 0000:00:14.5
[    2.184743] hub 6-0:1.0: USB hub found
[    2.184748] hub 6-0:1.0: 2 ports detected
[    2.184807] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.184811] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.184825] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf9ff3000
[    2.244541] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.244543] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.244545] usb usb7: Product: OHCI Host Controller
[    2.244546] usb usb7: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.244547] usb usb7: SerialNumber: 0000:00:16.0
[    2.244623] hub 7-0:1.0: USB hub found
[    2.244628] hub 7-0:1.0: 4 ports detected
[    2.244687] uhci_hcd: USB Universal Host Controller Interface driver
[    2.244719] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.244722] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    2.254339] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    2.254344] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    2.254349] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    2.254354] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    2.254359] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    2.254364] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    2.254369] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[    2.254448] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    2.254450] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254452] usb usb8: Product: xHCI Host Controller
[    2.254453] usb usb8: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    2.254454] usb usb8: SerialNumber: 0000:02:00.0
[    2.254511] xHCI xhci_add_endpoint called for root hub
[    2.254513] xHCI xhci_check_bandwidth called for root hub
[    2.254528] hub 8-0:1.0: USB hub found
[    2.254533] hub 8-0:1.0: 2 ports detected
[    2.254576] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.254579] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.254601] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    2.254603] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254604] usb usb9: Product: xHCI Host Controller
[    2.254605] usb usb9: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    2.254607] usb usb9: SerialNumber: 0000:02:00.0
[    2.254655] xHCI xhci_add_endpoint called for root hub
[    2.254656] xHCI xhci_check_bandwidth called for root hub
[    2.254669] hub 9-0:1.0: USB hub found
[    2.254674] hub 9-0:1.0: 2 ports detected
[    2.254807] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.254809] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.255289] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.255377] mousedev: PS/2 mouse device common for all mice
[    2.255481] rtc_cmos 00:01: RTC can wake from S4
[    2.255573] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.255594] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.255663] device-mapper: uevent: version 1.0.3
[    2.255715] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.255778] cpuidle: using governor ladder
[    2.255868] cpuidle: using governor menu
[    2.255871] ledtrig-cpu: registered to indicate activity on CPUs
[    2.255873] EFI Variables Facility v0.08 2004-May-17
[    2.256031] ashmem: initialized
[    2.256119] TCP: cubic registered
[    2.256191] NET: Registered protocol family 10
[    2.256315] NET: Registered protocol family 17
[    2.256321] Key type dns_resolver registered
[    2.256737] Loading module verification certificates
[    2.257479] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d8bc1516bb9827ccf9ced525fc4133574da45d40'
[    2.257486] registered taskstats version 1
[    2.259927] Key type trusted registered
[    2.261845] Key type encrypted registered
[    2.263786] rtc_cmos 00:01: setting system clock to 2013-08-22 23:48:22 UTC (1377215302)
[    2.263823] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    2.264720] acpi-cpufreq: overriding BIOS provided _PSD data
[    2.265256] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.265257] EDD information not available.
[    2.267521] Freeing unused kernel memory: 996k freed
[    2.267701] Write protecting the kernel read-only data: 12288k
[    2.272306] Freeing unused kernel memory: 1168k freed
[    2.276267] Freeing unused kernel memory: 1076k freed
[    2.287770] udevd[124]: starting version 175
[    2.291180] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.309598] Disabling lock debugging due to kernel taint
[    2.310196] ahci 0000:00:11.0: version 3.0
[    2.310321] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.310325] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.311457] scsi0 : ahci
[    2.311548] scsi1 : ahci
[    2.311623] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.311827] r8169 0000:04:00.0: irq 51 for MSI/MSI-X
[    2.311920] scsi2 : ahci
[    2.311979] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c7c000, f4:6d:04:cf:61:7c, XID 0c900800 IRQ 51
[    2.311981] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.312041] scsi3 : ahci
[    2.312117] scsi4 : ahci
[    2.312177] scsi5 : ahci
[    2.312223] ata1: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd00 irq 19
[    2.312226] ata2: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd80 irq 19
[    2.312229] ata3: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe00 irq 19
[    2.312231] ata4: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe80 irq 19
[    2.312234] ata5: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff00 irq 19
[    2.312236] ata6: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff80 irq 19
[    2.799524] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.799561] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.799592] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.800132] ata2.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    2.800135] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.800181] ata1.00: ATA-9: OCZ-AGILITY4, 1.4, max UDMA/133
[    2.800183] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.800972] ata1.00: configured for UDMA/133
[    2.800999] ata2.00: configured for UDMA/133
[    2.801131] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB06, max UDMA/66
[    2.801209] scsi 0:0:0:0: Direct-Access     ATA      OCZ-AGILITY4     1.4  PQ: 0 ANSI: 5
[    2.801340] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.801355] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.801468] sd 0:0:0:0: [sda] Write Protect is off
[    2.801470] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.801489] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    2.801507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.801578] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.801628] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.801638] sd 1:0:0:0: [sdb] Write Protect is off
[    2.801641] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.801659] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.801922]  sda: sda1
[    2.802191] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.803450] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.803521] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.803547] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.805911] ata4.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    2.805913] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.808099] ata4.00: configured for UDMA/133
[    2.809999] ata6.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    2.810006] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.811493] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.815174] ata5.00: ATA-8: KINGSTON SV300S37A120G, 505ABBF1, max UDMA/133
[    2.815181] ata5.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.816643] ata6.00: configured for UDMA/133
[    2.825043] ata5.00: configured for UDMA/133
[    2.826931]  sdb: sdb1
[    2.827343] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.915280] tsc: Refined TSC clocksource calibration: 3499.904 MHz
[    2.915289] Switching to clocksource tsc
[    2.943733] usb 2-1: New USB device found, idVendor=0409, idProduct=005a
[    2.943736] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.943925] hub 2-1:1.0: USB hub found
[    2.944024] hub 2-1:1.0: 4 ports detected
[    3.466178] usb 5-3: new full-speed USB device number 2 using ohci_hcd
[    3.600969] ata3.00: configured for UDMA/66
[    3.691771] usb 5-3: New USB device found, idVendor=0a12, idProduct=0001
[    3.691778] usb 5-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.084950] usb 4-2: new full-speed USB device number 2 using ohci_hcd
[    4.364432] usb 4-2: New USB device found, idVendor=0471, idProduct=0329
[    4.364439] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    4.364445] usb 4-2: SerialNumber: 01690000F54901B1
[    4.401394] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB06 PQ: 0 ANSI: 5
[    4.406464] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.406470] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.406670] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.406739] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    4.406867] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    4.406965] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.406982] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    4.407040] sd 3:0:0:0: [sdc] Write Protect is off
[    4.407042] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.407066] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.407097] scsi 4:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 505A PQ: 0 ANSI: 5
[    4.407253] sd 4:0:0:0: [sdd] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    4.407271] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    4.407306] sd 4:0:0:0: [sdd] Write Protect is off
[    4.407309] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.407329] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.407380] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    4.407496] sd 5:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.407529] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    4.407593] sd 5:0:0:0: [sde] Write Protect is off
[    4.407595] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.407621] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.409668]  sdd: sdd1 sdd2 < sdd5 >
[    4.410108] sd 4:0:0:0: [sdd] Attached SCSI disk
[    4.416474]  sde: sde1
[    4.416870] sd 5:0:0:0: [sde] Attached SCSI disk
[    4.423784]  sdc: sdc1
[    4.424160] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.627873] usb 4-5: new full-speed USB device number 3 using ohci_hcd
[    4.800562] usb 4-5: New USB device found, idVendor=046d, idProduct=c245
[    4.800569] usb 4-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.800574] usb 4-5: Product: Gaming Mouse G400
[    4.800578] usb 4-5: Manufacturer: Logitech
[    4.816639] usbcore: registered new interface driver usbhid
[    4.816645] usbhid: USB HID core driver
[    4.819003] input: Logitech Gaming Mouse G400 as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input3
[    4.819098] hid-generic 0003:046D:C245.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input0
[    4.821750] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input1
[   34.887829] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   34.887837] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   34.887847] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   34.887847]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   34.887853] ata3.00: status: { DRDY }
[   34.887860] ata3: hard resetting link
[   35.378860] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   36.180311] ata3.00: configured for PIO4
[   36.979455] ata3: EH complete
[   67.782599] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   67.782607] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   67.782616] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   67.782616]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   67.782622] ata3.00: status: { DRDY }
[   67.782628] ata3: hard resetting link
[   68.273581] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   69.074982] ata3.00: configured for PIO4
[   69.874099] ata3: EH complete
[   75.987368] EXT3-fs (sdd1): recovery required on readonly filesystem
[   75.987370] EXT3-fs (sdd1): write access will be enabled during recovery
[   76.112097] kjournald starting.  Commit interval 5 seconds
[   76.112913] EXT3-fs (sdd1): recovery complete
[   76.112916] EXT3-fs (sdd1): mounted filesystem with ordered data mode
[   76.263163] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.267197] init: bootchart main process (466) terminated with status 127
[   76.275109] udevd[480]: starting version 175
[   76.305805] lp: driver loaded but no devices found
[   76.311221] nvidia: module license 'NVIDIA' taints kernel.
[   76.312366] w83627ehf: Found NCT6776F chip at 0x290
[   76.312395] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SIOE 1 (20121018/utaddress-251)
[   76.312400] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.SIOR.HWRE 2 (20121018/utaddress-251)
[   76.312404] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   76.321211] EXT3-fs (sdd1): using internal journal
[   76.324671] wmi: Mapper loaded
[   76.331233] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   76.331380] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.44  Wed Mar 27 14:51:30 PDT 2013
[   76.342632] type=1400 audit(1377208176.723:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=558 comm="apparmor_parser"
[   76.342914] type=1400 audit(1377208176.723:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=558 comm="apparmor_parser"
[   76.343071] type=1400 audit(1377208176.723:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=558 comm="apparmor_parser"
[   76.394662] Linux video capture interface: v2.00
[   76.397232] init: bootchart post-stop process (477) terminated with status 127
[   76.402820] pwc: Philips SPC 900NC USB webcam detected.
[   76.403701] parport_pc 00:04: reported by Plug and Play ACPI
[   76.403750] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   76.417152] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input4
[   76.417259] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input5
[   76.417451] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
[   76.417575] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[   76.418235] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   76.422505] hda_intel: Disabling MSI
[   76.422513] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   76.446520] MCE: In-kernel MCE decoding enabled.
[   76.448661] EDAC MC: Ver: 3.0.0
[   76.452564] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20121018/utaddress-251)
[   76.452571] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 2 (20121018/utaddress-251)
[   76.452575] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   76.453744] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   76.453793] sp5100_tco: PCI Revision ID: 0x42
[   76.453829] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   76.453841] sp5100_tco: Last reboot was not triggered by watchdog.
[   76.454223] sp5100_tco: initialized (0xffffc90000c7eb00). heartbeat=60 sec (nowayout=0)
[   76.455977] AMD64 EDAC driver v3.4.0
[   76.456002] EDAC amd64: DRAM ECC disabled.
[   76.456013] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   76.456013]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   76.456013]  (Note that use of the override may cause unknown side effects.)
[   76.469078] microcode: CPU0: patch_level=0x0600081c
[   76.471274] microcode: CPU1: patch_level=0x0600081c
[   76.471418] microcode: CPU2: patch_level=0x0600081c
[   76.471424] microcode: CPU3: patch_level=0x0600081c
[   76.471431] microcode: CPU4: patch_level=0x0600081c
[   76.471439] microcode: CPU5: patch_level=0x0600081c
[   76.471487] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   76.487925] kvm: disabled by bios
[   76.493824] lp0: using parport0 (interrupt-driven).
[   76.531607] ppdev: user-space parallel port driver
[   76.555745] init: avahi-cups-reload main process (750) terminated with status 1
[   76.575604] type=1400 audit(1377208176.955:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=806 comm="apparmor_parser"
[   76.575956] type=1400 audit(1377208176.955:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=806 comm="apparmor_parser"
[   76.580883] Bluetooth: Core ver 2.16
[   76.580907] NET: Registered protocol family 31
[   76.580909] Bluetooth: HCI device and connection manager initialized
[   76.583587] Bluetooth: HCI socket layer initialized
[   76.583589] Bluetooth: L2CAP socket layer initialized
[   76.583594] Bluetooth: SCO socket layer initialized
[   76.591518] Bluetooth: RFCOMM TTY layer initialized
[   76.591526] Bluetooth: RFCOMM socket layer initialized
[   76.591528] Bluetooth: RFCOMM ver 1.11
[   76.592019] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   76.592021] Bluetooth: BNEP filters: protocol multicast
[   76.592055] Bluetooth: BNEP socket layer initialized
[   76.601145] usbcore: registered new interface driver btusb
[   76.633427] pwc: Registered as video0.
[   76.633472] input: PWC snapshot button as /devices/pci0000:00/0000:00:12.0/usb4/4-2/input/input9
[   76.634321] usbcore: registered new interface driver Philips webcam
[   76.674687] init: failsafe main process (848) killed by TERM signal
[   76.716893] usbcore: registered new interface driver snd-usb-audio
[   76.724859] type=1400 audit(1377208177.107:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=978 comm="apparmor_parser"
[   76.725111] type=1400 audit(1377208177.107:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=978 comm="apparmor_parser"
[   76.725353] type=1400 audit(1377208177.107:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=979 comm="apparmor_parser"
[   76.726946] type=1400 audit(1377208177.107:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=977 comm="apparmor_parser"
[   76.727180] type=1400 audit(1377208177.107:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=977 comm="apparmor_parser"

```

Does anyone have a clue what it is about? :confused:

Thank You!

What spec is your computer? If you're using Unity, KDE or a GNOME fork, consider switching to another Ubuntu distro (Xubuntu, or Lubuntu, or Mint XFCE edition). Plus (IMHO) it doesn't have any of the ugliness of Unity (the default interface, the one you're using if you installed standard Ubuntu), nor does it have the Amazon-sponsored spyware. If you want to experiment a little more...Crunchbang (#!) is known for being snappy, as is just about any distro with XFCE (as in Xubuntu) or LXDE (as in Lubuntu).

---

### Post by Andrew_Lucas on 2013-08-23
> **Ikaru said:**
> From my experience, linux boots slowly. I too had that same experience with Windows 8 booting faster than my Ubuntu but that can be explained as Windows 8 uses some sort of hybrid hibernation when booting, thus making it faster.

I have a core 2 duo with 3GB RAM and ubuntu boot time has always been slow (up to a minute). I think it all depends on the specs of you PC and not by the simple fact that you are running linux. 
And if you think about it boot speed is not that important. What really is important is the speed within the OS, running applications and processes.

Simply not true. Certain distros might be bad on your hardware, but time  and time again Linux boots faster than any like for like system.  Especially if you use something a little more stripped down (which I  wouldn't recommend for OP's main desktop distro) like Puppy or  DamnSmallLinux (both of which I think run straight out of the RAM I  think - so MUST be faster than Windows or just about any other OS).

If OP think's it's a driver rather than performation issue, consider switching to a distro with more packages installed out of the box, e.g. Mint. Also, if OP didn't want to change distro - make sure you have the proprietrary drivers installed e.g. for the GPU. AMD are much better than Nvidia here but both companies produce a Linux driver.

I've been using Linux for ~2.5 years. On my current relatively lowpowered laptop, POSTing and BIOS flash screen are slower than my Xubuntu OS to load. I reckon boot time is <30 seconds, maybe <10/~10.

---

### Post by oldfred on 2013-08-23
Windows 8 cheats, it does not fully boot, but uses hibernation all the time to make it seem like it is booting. Most of the time that works since hardware configuration does not change, but it is not a full boot.

If dual booting you should turn off the fast boot anyway as that can cause dual boot issues and may be related to your boot time.

This is your issue:
 [    4.821750] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input1
[   34.887829] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 [COLOR=#ff0000]frozen[/COLOR]

   
[   36.979455] ata3: EH complete
[   67.782599] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 [COLOR=#ff0000]frozen[/COLOR]

That is 60 seconds of your boot.

Somewhere I saw info on the frozen setting, but did not save a link. 
Found some info - seems to be a BIOS setting.

I have this in my notes on boot issues also, post by another user:
 Though my drive was appearing in the bios and working for install it was actually "disabled"! 

More detailed info on frozen.
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)

---

### Post by Ikaru on 2013-08-23
> **Andrew_Lucas said:**
> Simply not true. Certain distros might be bad on your hardware, but time  and time again Linux boots faster than any like for like system.  Especially if you use something a little more stripped down (which I  wouldn't recommend for OP's main desktop distro) like Puppy or  DamnSmallLinux (both of which I think run straight out of the RAM I  think - so MUST be faster than Windows or just about any other OS).

If OP think's it's a driver rather than performation issue, consider switching to a distro with more packages installed out of the box, e.g. Mint. Also, if OP didn't want to change distro - make sure you have the proprietrary drivers installed e.g. for the GPU. AMD are much better than Nvidia here but both companies produce a Linux driver.

I've been using Linux for ~2.5 years. On my current relatively lowpowered laptop, POSTing and BIOS flash screen are slower than my Xubuntu OS to load. I reckon boot time is <30 seconds, maybe <10/~10.

If true then all distros are bad on my hardware. I've been using Linux since 2009 and never had a real fast boot distro. I think puppy was a little faster but I don't like puppy.

---

### Post by Jonathan Andrew Upton on 2013-08-24
Ubuntu boots slowly because of all the running processes to make the operating system work are starting up at specific periods of time. The reason why Windows 8 boots faster is because Windows NT/RT uses a different kernel which follows a different set of running processes. The same can be said for Mac OS X, despite being UNIX-based.

---

### Post by pnaarmann on 2013-08-24
Thank you for all the answers.

> [COLOR=#000000]Windows 8 cheats, it does not fully boot, but uses hibernation all the time to make it seem like it is booting. Most of the time that works since hardware configuration does not change, but it is not a full boot.[/COLOR]

[COLOR=#000000]If dual booting you should turn off the fast boot anyway as that can cause dual boot issues and may be related to your boot time.[/COLOR]

I turned fast boot off before installing Ubuntu.

> [COLOR=#000000]This is your issue:[/COLOR]
[COLOR=#000000][ 4.821750] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input1[/COLOR]
[COLOR=#000000][ 34.887829] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 [/COLOR][COLOR=#ff0000]frozen[/COLOR]


[COLOR=#000000][ 36.979455] ata3: EH complete[/COLOR]
[COLOR=#000000][ 67.782599] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 [/COLOR][COLOR=#ff0000]frozen[/COLOR]

[COLOR=#000000]That is 60 seconds of your boot.[/COLOR]

I googled that error message many times, but it doesn't seem to get me to the problem directly. I also changed the SATA cable - so that is not the problem.

> [COLOR=#000000]Somewhere I saw info on the frozen setting, but did not save a link. [/COLOR]
[COLOR=#000000]Found some info - seems to be a BIOS setting.[/COLOR]

[COLOR=#000000]I have this in my notes on boot issues also, post by another user:[/COLOR]
[COLOR=#000000]Though my drive was appearing in the bios and working for install it was actually "disabled"! [/COLOR]

What is it with the BIOS setting you are talking about? How can I check that?

> [COLOR=#000000]More detailed info on frozen.[/COLOR]
[https://wiki.archlinux.org/index.php..._Cell_Clearing]("https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing")

What I tried is:
```
$ sudo hdparm -I /dev/sdd1
```

It gave me this output:
```
/dev/sdd1:

ATA device, with non-removable media
    Model Number:       KINGSTON SV300S37A120G                  
    Serial Number:      50026B7237015973    
    Firmware Revision:  505ABBF1
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Used: unknown (minor revision code 0x0110) 
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  234441648
    LBA48  user addressable sectors:  234441648
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:      114473 MBytes
    device size with M = 1000*1000:      120034 MBytes (120 GB)
    cache/buffer size  = unknown
    Nominal Media Rotation Rate: Solid State Device
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
            Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
       *    48-bit Address feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
            Write-Read-Verify feature set
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    unknown 76[14]
       *    unknown 76[15]
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Data Tables (AC5)
       *    SET MAX SETPASSWORD/UNLOCK DMA commands
       *    Data Set Management TRIM supported (limit 1 block)
       *    Deterministic read data after TRIM
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
    not    supported: enhanced erase
    2min for SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50026b7237015973
    NAA        : 5
    IEEE OUI    : 0026b7
    Unique ID    : 237015973
Checksum: correct

```

Does this tell you anything?

I guess "not frozen" is the info you were after?

---

### Post by oldfred on 2013-08-24
That does say not frozen so that may not be issue. But still the 30 sec twice to try to mount or load that device is a problem. But I am not sure what it is doing as it is not a mount but seems to not be able to read some device.

I would still review BIOS settings. One user had no floppy drive but BIOS had floppy enabled and that caused issues. Another user still had a DVD in a drive and system somehow tried running fsck on it? Or it may take some investigation. Even disconnect things and see what is different or change settings.
Have not seen that issue or no one has posted a solution to make it easier that I know of.

---

### Post by pnaarmann on 2013-08-24
> **oldfred said:**
> That does say not frozen so that may not be issue. But still the 30 sec twice to try to mount or load that device is a problem. But I am not sure what it is doing as it is not a mount but seems to not be able to read some device.

I would still review BIOS settings. One user had no floppy drive but BIOS had floppy enabled and that caused issues. Another user still had a DVD in a drive and system somehow tried running fsck on it? Or it may take some investigation. Even disconnect things and see what is different or change settings.
Have not seen that issue or no one has posted a solution to make it easier that I know of.


Checked the BIOS, but everything seemed OK.

Then I unplugged the DVD drive and it booted in around 10 seconds. :D

This is the log:
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-29-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 (Ubuntu 3.8.0-29.42-generic 3.8.13.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=cb79b948-f67b-4a77-99c5-17ece94ecbff ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009abff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ac00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cff7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cff80000-0x00000000cff97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cff98000-0x00000000cffbffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cffc0000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A87, BIOS 1402    11/15/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000022f000000 aka 8944M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000094000] 94000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcff7ffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcff7ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcff7ffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22effffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000]  [mem 0x200000000-0x22effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22effffff @ [mem 0xcff7e000-0xcff7ffff]
[    0.000000] RAMDISK: [mem 0x344be000-0x36256fff]
[    0.000000] ACPI: RSDP 00000000000fb850 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff80100 00054 (v01 111512 XSDT1057 20121115 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 111512 FACP1057 20121115 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff80460 0D051 (v01  A1866 A1866001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff98000 00040
[    0.000000] ACPI: APIC 00000000cff80390 0008C (v01 111512 APIC1057 20121115 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff80420 0003C (v01 111512 OEMMCFG  20121115 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 111512 OEMB1057 20121115 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff8f8b0 00038 (v01 111512 OEMHPET  20121115 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff8f8f0 01158 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22effffff]
[    0.000000]   NODE_DATA [mem 0x22effb000-0x22effffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226600000-ffff88022e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00099fff]
[    0.000000]   node   0: [mem 0x00100000-0xcff7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22effffff]
[    0.000000] On node 0 totalpages: 2092810
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3908 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13246 pages used for memmap
[    0.000000]   DMA32 zone: 834498 pages, LIFO batch:31
[    0.000000]   Normal zone: 19392 pages used for memmap
[    0.000000]   Normal zone: 1221696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x16] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 22, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
[    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffc0000
[    0.000000] PM: Registered nosave memory: 00000000cffc0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xff9fffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022ec00000 s85056 r8192 d21440 u262144
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2060102
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=cb79b948-f67b-4a77-99c5-17ece94ecbff ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 8061552k/9158656k available (7013k kernel code, 787416k absent, 309688k reserved, 6229k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3500.178 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 7000.35 BogoMIPS (lpj=14000712)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000508] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002356] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003160] Mount-cache hash table entries: 256
[    0.003303] Initializing cgroup subsys cpuacct
[    0.003305] Initializing cgroup subsys memory
[    0.003311] Initializing cgroup subsys devices
[    0.003312] Initializing cgroup subsys freezer
[    0.003314] Initializing cgroup subsys blkio
[    0.003315] Initializing cgroup subsys perf_event
[    0.003317] Initializing cgroup subsys hugetlb
[    0.003336] tseg: 0000000000
[    0.003344] CPU: Physical Processor ID: 0
[    0.003345] CPU: Processor Core ID: 0
[    0.003346] mce: CPU supports 7 MCE banks
[    0.003352] LVT offset 1 assigned for vector 0xf9
[    0.003357] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.003357] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.003357] tlb_flushall_shift: 5
[    0.003442] Freeing SMP alternatives: 24k freed
[    0.004777] ACPI: Core revision 20121018
[    0.010243] ftrace: allocating 26712 entries in 105 pages
[    0.018443] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058053] smpboot: CPU0: AMD FX(tm)-6300 Six-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.164767] Performance Events: 
[    0.164768] perf: AMD core performance counters detected
[    0.164770] AMD PMU driver.
[    0.164771] ... version:                0
[    0.164772] ... bit width:              48
[    0.164773] ... generic registers:      6
[    0.164774] ... value mask:             0000ffffffffffff
[    0.164775] ... max period:             00007fffffffffff
[    0.164776] ... fixed-purpose events:   0
[    0.164777] ... event mask:             000000000000003f
[    0.165679] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.165740] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5
[    0.231502] Brought up 6 CPUs
[    0.231505] smpboot: Total of 6 processors activated (42002.13 BogoMIPS)
[    0.239271] devtmpfs: initialized
[    0.240551] EVM: security.selinux
[    0.240552] EVM: security.SMACK64
[    0.240553] EVM: security.capability
[    0.240603] PM: Registering ACPI NVS region [mem 0xcff98000-0xcffbffff] (163840 bytes)
[    0.241281] regulator-dummy: no parameters
[    0.241327] NET: Registered protocol family 16
[    0.241481] ACPI: bus type pci registered
[    0.241526] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.241528] PCI: not using MMCONFIG
[    0.241529] PCI: Using configuration type 1 for base access
[    0.241530] PCI: Using configuration type 1 for extended access
[    0.241726] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.241727] mtrr: probably your BIOS does not setup all CPUs.
[    0.241728] mtrr: corrected configuration.
[    0.242482] bio: create slab <bio-0> at 0
[    0.242564] ACPI: Added _OSI(Module Device)
[    0.242566] ACPI: Added _OSI(Processor Device)
[    0.242567] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.242568] ACPI: Added _OSI(Processor Aggregator Device)
[    0.243862] ACPI: EC: Look up EC in DSDT
[    0.245391] ACPI: Executed 3 blocks of module-level executable AML code
[    0.344281] ACPI: Interpreter enabled
[    0.344285] ACPI: (supports S0 S1 S3 S4 S5)
[    0.344305] ACPI: Using IOAPIC for interrupt routing
[    0.344326] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.345125] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.361847] ACPI: No dock devices found.
[    0.361850] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.361938] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.361940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.362382] PCI host bridge to bus 0000:00
[    0.362385] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.362387] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.362388] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.362390] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.362392] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.362393] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.362395] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.362404] pci 0000:00:00.0: [1002:5957] type 00 class 0x060000
[    0.362449] pci 0000:00:02.0: [1002:5978] type 01 class 0x060400
[    0.362481] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.362495] pci 0000:00:04.0: [1002:597a] type 01 class 0x060400
[    0.362526] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.362541] pci 0000:00:07.0: [1002:597d] type 01 class 0x060400
[    0.362572] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.362586] pci 0000:00:0a.0: [1002:597f] type 01 class 0x060400
[    0.362617] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.362641] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.362659] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.362667] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.362676] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.362684] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.362693] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.362701] pci 0000:00:11.0: reg 24: [mem 0xf9fffc00-0xf9ffffff]
[    0.362755] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.362767] pci 0000:00:12.0: reg 10: [mem 0xf9ffe000-0xf9ffefff]
[    0.362832] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.362849] pci 0000:00:12.2: reg 10: [mem 0xf9fff800-0xf9fff8ff]
[    0.362923] pci 0000:00:12.2: supports D1 D2
[    0.362925] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.362947] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.362959] pci 0000:00:13.0: reg 10: [mem 0xf9ffd000-0xf9ffdfff]
[    0.363023] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.363040] pci 0000:00:13.2: reg 10: [mem 0xf9fff400-0xf9fff4ff]
[    0.363114] pci 0000:00:13.2: supports D1 D2
[    0.363116] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.363136] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.363206] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.363226] pci 0000:00:14.2: reg 10: [mem 0xf9ff4000-0xf9ff7fff 64bit]
[    0.363285] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.363299] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.363367] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.363405] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.363417] pci 0000:00:14.5: reg 10: [mem 0xf9ffc000-0xf9ffcfff]
[    0.363479] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.363491] pci 0000:00:16.0: reg 10: [mem 0xf9ff3000-0xf9ff3fff]
[    0.363556] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.363573] pci 0000:00:16.2: reg 10: [mem 0xf9fff000-0xf9fff0ff]
[    0.363648] pci 0000:00:16.2: supports D1 D2
[    0.363649] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.363669] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.363687] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.363701] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.363716] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.363734] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.363748] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.363799] pci 0000:01:00.0: [10de:1200] type 00 class 0x030000
[    0.363808] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfbffffff]
[    0.363818] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.363828] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.363835] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.363841] pci 0000:01:00.0: reg 30: [mem 0xfce80000-0xfcefffff pref]
[    0.363897] pci 0000:01:00.1: [10de:0e0c] type 00 class 0x040300
[    0.363906] pci 0000:01:00.1: reg 10: [mem 0xfce7c000-0xfce7ffff]
[    0.371940] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.371943] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.371946] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfcefffff]
[    0.371949] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.371987] pci 0000:02:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.372004] pci 0000:02:00.0: reg 10: [mem 0xfcff8000-0xfcffffff 64bit]
[    0.372090] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.379920] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.379924] pci 0000:00:04.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.379962] pci 0000:03:00.0: [1102:000b] type 00 class 0x040300
[    0.379981] pci 0000:03:00.0: reg 10: [mem 0xfebe0000-0xfebeffff 64bit]
[    0.379996] pci 0000:03:00.0: reg 18: [mem 0xfe800000-0xfe9fffff 64bit]
[    0.380011] pci 0000:03:00.0: reg 20: [mem 0xfd000000-0xfdffffff 64bit]
[    0.387904] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.387908] pci 0000:00:07.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.387944] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.387956] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.387975] pci 0000:04:00.0: reg 18: [mem 0xf8fff000-0xf8ffffff 64bit pref]
[    0.387988] pci 0000:04:00.0: reg 20: [mem 0xf8ff8000-0xf8ffbfff 64bit pref]
[    0.388041] pci 0000:04:00.0: supports D1 D2
[    0.388043] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.395891] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.395894] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.395898] pci 0000:00:0a.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.395954] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
[    0.395962] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.395964] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.395965] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.395967] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.395968] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.395970] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.395992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.396027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.396058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.396087] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.396123] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.396291]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.396452]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.397538] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 14 15)
[    0.397597] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 14 15)
[    0.397656] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 14 15)
[    0.397715] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 *10 11 14 15)
[    0.397761] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.397795] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.397829] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.397863] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.397949] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.397951] vgaarb: loaded
[    0.397952] vgaarb: bridge control possible 0000:01:00.0
[    0.398102] SCSI subsystem initialized
[    0.398104] ACPI: bus type scsi registered
[    0.398155] libata version 3.00 loaded.
[    0.398171] ACPI: bus type usb registered
[    0.398183] usbcore: registered new interface driver usbfs
[    0.398190] usbcore: registered new interface driver hub
[    0.398212] usbcore: registered new device driver usb
[    0.398291] PCI: Using ACPI for IRQ routing
[    0.405942] PCI: pci_cache_line_size set to 64 bytes
[    0.406002] e820: reserve RAM buffer [mem 0x0009ac00-0x0009ffff]
[    0.406003] e820: reserve RAM buffer [mem 0xcff80000-0xcfffffff]
[    0.406005] e820: reserve RAM buffer [mem 0x22f000000-0x22fffffff]
[    0.406074] NetLabel: Initializing
[    0.406075] NetLabel:  domain hash size = 128
[    0.406076] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.406087] NetLabel:  unlabeled traffic allowed by default
[    0.406128] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.406131] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.408152] Switching to clocksource hpet
[    0.413312] AppArmor: AppArmor Filesystem Enabled
[    0.413325] pnp: PnP ACPI init
[    0.413334] ACPI: bus type pnp registered
[    0.413384] pnp 00:00: [dma 4]
[    0.413400] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.413427] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.413446] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.413466] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.413762] pnp 00:04: [dma 0 disabled]
[    0.413865] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.413940] system 00:05: [io  0x0290-0x029f] has been reserved
[    0.413942] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.413987] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.414045] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.414264] pnp 00:08: [dma 0 disabled]
[    0.414321] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.414419] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.414421] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.414424] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414634] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.414636] system 00:0a: [io  0x040b] has been reserved
[    0.414638] system 00:0a: [io  0x04d6] has been reserved
[    0.414640] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.414641] system 00:0a: [io  0x0c14] has been reserved
[    0.414643] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.414645] system 00:0a: [io  0x0c52] has been reserved
[    0.414646] system 00:0a: [io  0x0c6c] has been reserved
[    0.414648] system 00:0a: [io  0x0c6f] has been reserved
[    0.414650] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.414652] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.414653] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.414655] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.414657] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.414658] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.414660] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.414662] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
[    0.414664] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.414665] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.414667] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.414669] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.414671] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.414673] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.414674] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.414676] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.414679] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414728] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.414731] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414860] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.414862] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.414864] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.414866] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.414868] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.414870] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.414957] pnp: PnP ACPI: found 13 devices
[    0.414958] ACPI: ACPI bus type pnp unregistered
[    0.421180] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.421183] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.421186] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfcefffff]
[    0.421189] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.421192] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.421194] pci 0000:00:04.0:   bridge window [mem 0xfcf00000-0xfcffffff]
[    0.421198] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.421200] pci 0000:00:07.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.421204] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.421206] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.421209] pci 0000:00:0a.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.421212] pci 0000:00:14.4: PCI bridge to [bus 05]
[    0.421244] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.421246] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.421247] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421249] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421250] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.421252] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.421253] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.421255] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfcefffff]
[    0.421256] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.421258] pci_bus 0000:02: resource 1 [mem 0xfcf00000-0xfcffffff]
[    0.421260] pci_bus 0000:03: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.421261] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.421263] pci_bus 0000:04: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.421264] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.421266] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.421267] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421269] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421270] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.421271] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.421293] NET: Registered protocol family 2
[    0.421451] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421681] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.421856] TCP: Hash tables configured (established 65536 bind 65536)
[    0.421881] TCP: reno registered
[    0.421892] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421926] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.421993] NET: Registered protocol family 1
[    1.522047] pci 0000:01:00.0: Boot video device
[    1.522089] PCI: CLS 64 bytes, default 64
[    1.522124] Trying to unpack rootfs image as initramfs...
[    1.909427] Freeing initrd memory: 30308k freed
[    1.915408] PCI-DMA: Disabling AGP.
[    1.915489] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.915490] PCI-DMA: using GART IOMMU.
[    1.915492] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.919880] LVT offset 0 assigned for vector 0x400
[    1.919910] perf: AMD IBS detected (0x000000ff)
[    1.920118] Initialise module verification
[    1.920152] audit: initializing netlink socket (disabled)
[    1.920161] type=2000 audit(1377363624.812:1): initialized
[    1.941519] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.942952] VFS: Disk quotas dquot_6.5.2
[    1.942985] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.943391] fuse init (API version 7.20)
[    1.943451] msgmni has been set to 15933
[    1.943883] Key type asymmetric registered
[    1.943885] Asymmetric key parser 'x509' registered
[    1.943909] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.943936] io scheduler noop registered
[    1.943937] io scheduler deadline registered (default)
[    1.943941] io scheduler cfq registered
[    1.944040] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.944098] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.944153] pcieport 0000:00:07.0: irq 42 for MSI/MSI-X
[    1.944209] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
[    1.944263] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    1.944265] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.944266] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.944268] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    1.944278] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.944279] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.944282] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    1.944292] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    1.944294] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.944296] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    1.944306] pcieport 0000:00:0a.0: Signaling PME through PCIe PME interrupt
[    1.944307] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.944309] pcie_pme 0000:00:0a.0:pcie01: service driver pcie_pme loaded
[    1.944321] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.944333] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.944414] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.944417] ACPI: Power Button [PWRB]
[    1.944448] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.944450] ACPI: Power Button [PWRF]
[    1.944782] ACPI: acpi_idle registered with cpuidle
[    1.948596] GHES: HEST is not enabled!
[    1.948659] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.969058] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.970250] Linux agpgart interface v0.103
[    1.971306] brd: module loaded
[    1.971866] loop: module loaded
[    1.972128] libphy: Fixed MDIO Bus: probed
[    1.972176] tun: Universal TUN/TAP device driver, 1.6
[    1.972177] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.972211] PPP generic driver version 2.4.2
[    1.972251] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.972252] ehci-pci: EHCI PCI platform driver
[    1.972285] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.972290] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.972298] QUIRK: Enable AMD PLL fix
[    1.972299] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.972310] ehci-pci 0000:00:12.2: debug port 1
[    1.972339] ehci-pci 0000:00:12.2: irq 17, io mem 0xf9fff800
[    1.981083] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.981104] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.981106] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.981107] usb usb1: Product: EHCI Host Controller
[    1.981108] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.981110] usb usb1: SerialNumber: 0000:00:12.2
[    1.981190] hub 1-0:1.0: USB hub found
[    1.981193] hub 1-0:1.0: 5 ports detected
[    1.981279] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.981283] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.981285] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.981296] ehci-pci 0000:00:13.2: debug port 1
[    1.981315] ehci-pci 0000:00:13.2: irq 17, io mem 0xf9fff400
[    1.993060] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.993072] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.993074] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.993075] usb usb2: Product: EHCI Host Controller
[    1.993077] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.993078] usb usb2: SerialNumber: 0000:00:13.2
[    1.993150] hub 2-0:1.0: USB hub found
[    1.993154] hub 2-0:1.0: 5 ports detected
[    1.993238] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.993243] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.993246] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.993256] ehci-pci 0000:00:16.2: debug port 1
[    1.993276] ehci-pci 0000:00:16.2: irq 17, io mem 0xf9fff000
[    2.005043] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.005057] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.005058] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.005060] usb usb3: Product: EHCI Host Controller
[    2.005061] usb usb3: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    2.005063] usb usb3: SerialNumber: 0000:00:16.2
[    2.005130] hub 3-0:1.0: USB hub found
[    2.005133] hub 3-0:1.0: 4 ports detected
[    2.005197] ehci-platform: EHCI generic platform driver
[    2.005202] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.005224] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.005228] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.005245] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf9ffe000
[    2.064907] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.064909] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.064911] usb usb4: Product: OHCI Host Controller
[    2.064912] usb usb4: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.064913] usb usb4: SerialNumber: 0000:00:12.0
[    2.064987] hub 4-0:1.0: USB hub found
[    2.064992] hub 4-0:1.0: 5 ports detected
[    2.065065] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.065068] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.065079] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffd000
[    2.124802] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.124804] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.124805] usb usb5: Product: OHCI Host Controller
[    2.124807] usb usb5: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.124808] usb usb5: SerialNumber: 0000:00:13.0
[    2.124886] hub 5-0:1.0: USB hub found
[    2.124891] hub 5-0:1.0: 5 ports detected
[    2.124969] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.124972] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.124984] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ffc000
[    2.184674] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.184676] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.184678] usb usb6: Product: OHCI Host Controller
[    2.184679] usb usb6: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.184680] usb usb6: SerialNumber: 0000:00:14.5
[    2.184755] hub 6-0:1.0: USB hub found
[    2.184760] hub 6-0:1.0: 2 ports detected
[    2.184818] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.184821] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.184836] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf9ff3000
[    2.244552] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.244554] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.244556] usb usb7: Product: OHCI Host Controller
[    2.244557] usb usb7: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    2.244558] usb usb7: SerialNumber: 0000:00:16.0
[    2.244634] hub 7-0:1.0: USB hub found
[    2.244639] hub 7-0:1.0: 4 ports detected
[    2.244698] uhci_hcd: USB Universal Host Controller Interface driver
[    2.244730] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.244733] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    2.254348] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    2.254354] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    2.254359] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    2.254364] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    2.254369] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    2.254373] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    2.254378] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[    2.254458] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    2.254460] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254461] usb usb8: Product: xHCI Host Controller
[    2.254463] usb usb8: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    2.254464] usb usb8: SerialNumber: 0000:02:00.0
[    2.254524] xHCI xhci_add_endpoint called for root hub
[    2.254525] xHCI xhci_check_bandwidth called for root hub
[    2.254540] hub 8-0:1.0: USB hub found
[    2.254545] hub 8-0:1.0: 2 ports detected
[    2.254588] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.254591] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.254613] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    2.254614] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.254616] usb usb9: Product: xHCI Host Controller
[    2.254617] usb usb9: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    2.254618] usb usb9: SerialNumber: 0000:02:00.0
[    2.254667] xHCI xhci_add_endpoint called for root hub
[    2.254668] xHCI xhci_check_bandwidth called for root hub
[    2.254681] hub 9-0:1.0: USB hub found
[    2.254685] hub 9-0:1.0: 2 ports detected
[    2.254817] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.254819] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.255299] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.255387] mousedev: PS/2 mouse device common for all mice
[    2.255483] rtc_cmos 00:01: RTC can wake from S4
[    2.255577] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.255599] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.255668] device-mapper: uevent: version 1.0.3
[    2.255722] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.255782] cpuidle: using governor ladder
[    2.255871] cpuidle: using governor menu
[    2.255874] ledtrig-cpu: registered to indicate activity on CPUs
[    2.255876] EFI Variables Facility v0.08 2004-May-17
[    2.256033] ashmem: initialized
[    2.256122] TCP: cubic registered
[    2.256192] NET: Registered protocol family 10
[    2.256316] NET: Registered protocol family 17
[    2.256322] Key type dns_resolver registered
[    2.256730] Loading module verification certificates
[    2.257471] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d8bc1516bb9827ccf9ced525fc4133574da45d40'
[    2.257479] registered taskstats version 1
[    2.260081] Key type trusted registered
[    2.261834] Key type encrypted registered
[    2.263872] rtc_cmos 00:01: setting system clock to 2013-08-24 17:00:26 UTC (1377363626)
[    2.263909] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    2.264821] acpi-cpufreq: overriding BIOS provided _PSD data
[    2.265365] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.265366] EDD information not available.
[    2.267581] Freeing unused kernel memory: 996k freed
[    2.267749] Write protecting the kernel read-only data: 12288k
[    2.272110] Freeing unused kernel memory: 1168k freed
[    2.276301] Freeing unused kernel memory: 1076k freed
[    2.288213] udevd[124]: starting version 175
[    2.300527] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.309598] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.309796] r8169 0000:04:00.0: irq 51 for MSI/MSI-X
[    2.309919] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c7a000, f4:6d:04:cf:61:7c, XID 0c900800 IRQ 51
[    2.309921] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.311104] Disabling lock debugging due to kernel taint
[    2.311668] ahci 0000:00:11.0: version 3.0
[    2.311777] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.311780] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.312324] scsi0 : ahci
[    2.312500] scsi1 : ahci
[    2.313119] scsi2 : ahci
[    2.313629] scsi3 : ahci
[    2.313746] scsi4 : ahci
[    2.313838] scsi5 : ahci
[    2.313880] ata1: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd00 irq 19
[    2.313883] ata2: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd80 irq 19
[    2.313886] ata3: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe00 irq 19
[    2.313888] ata4: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe80 irq 19
[    2.313892] ata5: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff00 irq 19
[    2.313895] ata6: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff80 irq 19
[    2.631934] ata3: SATA link down (SStatus 0 SControl 300)
[    2.803543] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.803582] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.803616] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.803649] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.803675] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.804132] ata1.00: ATA-9: OCZ-AGILITY4, 1.4, max UDMA/133
[    2.804134] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.804213] ata2.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    2.804215] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.804882] ata1.00: configured for UDMA/133
[    2.804943] ata2.00: configured for UDMA/133
[    2.805004] scsi 0:0:0:0: Direct-Access     ATA      OCZ-AGILITY4     1.4  PQ: 0 ANSI: 5
[    2.805136] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.805159] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.805258] sd 0:0:0:0: [sda] Write Protect is off
[    2.805261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.805302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.805313] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    2.805426] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.805468] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.805470] sd 1:0:0:0: [sdb] Write Protect is off
[    2.805473] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.805508] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.805949]  sda: sda1
[    2.806231] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.810140] ata6.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    2.810143] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.811499] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.813106] ata4.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    2.813113] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.815385] ata4.00: configured for UDMA/133
[    2.815393] ata5.00: ATA-8: KINGSTON SV300S37A120G, 505ABBF1, max UDMA/133
[    2.815395] ata5.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.815491] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    2.815614] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.815637] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.815712] sd 3:0:0:0: [sdc] Write Protect is off
[    2.815714] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.815750] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.816565] ata6.00: configured for UDMA/133
[    2.824122]  sdc: sdc1
[    2.824545] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.824948]  sdb: sdb1
[    2.825200] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.825329] ata5.00: configured for UDMA/133
[    2.825407] scsi 4:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 505A PQ: 0 ANSI: 5
[    2.825518] sd 4:0:0:0: [sdd] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.825543] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.825627] sd 4:0:0:0: [sdd] Write Protect is off
[    2.825629] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.825666] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.825677] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    2.825779] sd 5:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.825826] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    2.825831] sd 5:0:0:0: [sde] Write Protect is off
[    2.825834] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.825851] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.826205]  sdd: sdd1 sdd2 < sdd5 >
[    2.826549] sd 4:0:0:0: [sdd] Attached SCSI disk
[    2.829648]  sde: sde1
[    2.830108] sd 5:0:0:0: [sde] Attached SCSI disk
[    2.915235] tsc: Refined TSC clocksource calibration: 3499.907 MHz
[    2.915239] Switching to clocksource tsc
[    2.943623] usb 2-1: New USB device found, idVendor=0409, idProduct=005a
[    2.943625] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.943819] hub 2-1:1.0: USB hub found
[    2.943909] hub 2-1:1.0: 4 ports detected
[    3.334451] usb 4-2: new full-speed USB device number 2 using ohci_hcd
[    3.613937] usb 4-2: New USB device found, idVendor=0471, idProduct=0329
[    3.613944] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    3.613949] usb 4-2: SerialNumber: 01690000F54901B1
[    3.877373] usb 4-5: new full-speed USB device number 3 using ohci_hcd
[    4.050066] usb 4-5: New USB device found, idVendor=046d, idProduct=c245
[    4.050073] usb 4-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.050078] usb 4-5: Product: Gaming Mouse G400
[    4.050082] usb 4-5: Manufacturer: Logitech
[    4.066144] usbcore: registered new interface driver usbhid
[    4.066149] usbhid: USB HID core driver
[    4.068401] input: Logitech Gaming Mouse G400 as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input3
[    4.068515] hid-generic 0003:046D:C245.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input0
[    4.071291] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input1
[    9.207763] EXT3-fs (sdd1): recovery required on readonly filesystem
[    9.207765] EXT3-fs (sdd1): write access will be enabled during recovery
[    9.430935] kjournald starting.  Commit interval 5 seconds
[    9.431744] EXT3-fs (sdd1): recovery complete
[    9.431748] EXT3-fs (sdd1): mounted filesystem with ordered data mode
[    9.579666] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.585447] init: bootchart main process (461) terminated with status 127
[    9.587195] udevd[474]: starting version 175
[    9.626126] EXT3-fs (sdd1): using internal journal
[    9.630573] lp: driver loaded but no devices found
[    9.636465] w83627ehf: Found NCT6776F chip at 0x290
[    9.636494] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SIOE 1 (20121018/utaddress-251)
[    9.636500] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.SIOR.HWRE 2 (20121018/utaddress-251)
[    9.636504] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.647964] type=1400 audit(1377356433.895:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=549 comm="apparmor_parser"
[    9.648276] type=1400 audit(1377356433.895:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=549 comm="apparmor_parser"
[    9.648428] type=1400 audit(1377356433.895:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=549 comm="apparmor_parser"
[    9.650514] nvidia: module license 'NVIDIA' taints kernel.
[    9.668232] wmi: Mapper loaded
[    9.670309] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.670514] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.44  Wed Mar 27 14:51:30 PDT 2013
[    9.677776] parport_pc 00:04: reported by Plug and Play ACPI
[    9.677837] parport0: PC-style at 0x378, irq 7 [PCSPP]
[    9.690493] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20121018/utaddress-251)
[    9.690500] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 2 (20121018/utaddress-251)
[    9.690505] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.693008] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    9.693116] sp5100_tco: PCI Revision ID: 0x42
[    9.693157] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[    9.693170] sp5100_tco: Last reboot was not triggered by watchdog.
[    9.693681] sp5100_tco: initialized (0xffffc90000c7eb00). heartbeat=60 sec (nowayout=0)
[    9.707226] MCE: In-kernel MCE decoding enabled.
[    9.710318] EDAC MC: Ver: 3.0.0
[    9.713286] AMD64 EDAC driver v3.4.0
[    9.723471] init: bootchart post-stop process (472) terminated with status 127
[    9.729228] Linux video capture interface: v2.00
[    9.733850] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[    9.736021] pwc: Philips SPC 900NC USB webcam detected.
[    9.736682] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    9.736812] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    9.736905] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    9.737056] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    9.737453] hda_intel: Disabling MSI
[    9.737462] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    9.737819] EDAC amd64: DRAM ECC disabled.
[    9.737829] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    9.737829]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    9.737829]  (Note that use of the override may cause unknown side effects.)
[    9.742656] Bluetooth: Core ver 2.16
[    9.742674] NET: Registered protocol family 31
[    9.742676] Bluetooth: HCI device and connection manager initialized
[    9.742683] Bluetooth: HCI socket layer initialized
[    9.742686] Bluetooth: L2CAP socket layer initialized
[    9.742692] Bluetooth: SCO socket layer initialized
[    9.744301] microcode: CPU0: patch_level=0x0600081c
[    9.751544] Bluetooth: RFCOMM TTY layer initialized
[    9.751554] Bluetooth: RFCOMM socket layer initialized
[    9.751556] Bluetooth: RFCOMM ver 1.11
[    9.753219] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.753222] Bluetooth: BNEP filters: protocol multicast
[    9.753228] Bluetooth: BNEP socket layer initialized
[    9.779309] microcode: CPU1: patch_level=0x0600081c
[    9.779318] microcode: CPU2: patch_level=0x0600081c
[    9.779324] microcode: CPU3: patch_level=0x0600081c
[    9.779331] microcode: CPU4: patch_level=0x0600081c
[    9.779340] microcode: CPU5: patch_level=0x0600081c
[    9.779381] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.789653] lp0: using parport0 (interrupt-driven).
[    9.819661] kvm: disabled by bios
[    9.835856] ppdev: user-space parallel port driver
[    9.865405] init: avahi-cups-reload main process (794) terminated with status 1
[    9.903494] type=1400 audit(1377356434.151:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=896 comm="apparmor_parser"
[    9.903865] type=1400 audit(1377356434.151:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=896 comm="apparmor_parser"
[    9.923658] init: failsafe main process (866) killed by TERM signal
[    9.970267] pwc: Registered as video0.
[    9.970328] input: PWC snapshot button as /devices/pci0000:00/0000:00:12.0/usb4/4-2/input/input9
[    9.970530] usbcore: registered new interface driver Philips webcam
[    9.980024] type=1400 audit(1377356434.227:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=955 comm="apparmor_parser"
[    9.980274] type=1400 audit(1377356434.227:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=955 comm="apparmor_parser"
[    9.983900] type=1400 audit(1377356434.231:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=954 comm="apparmor_parser"
[    9.984159] type=1400 audit(1377356434.231:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=954 comm="apparmor_parser"
[    9.984460] type=1400 audit(1377356434.231:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
[   10.039946] usbcore: registered new interface driver snd-usb-audio
[   10.142928] r8169 0000:04:00.0 eth0: link down
[   10.142970] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.143265] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.144882] r8169 0000:04:00.0 eth0: link down
```

I checked the cables of the DVD drive if they are damaged, but that was not the cause.

How can I check my DVD drive for errors? Can it be driver related?

---

### Post by oldfred on 2013-08-24
Is DVD SATA2 and you have it in a SATA3 port? Or something similar. 
Do you have a SATA2 port to try with?

Did DVD seem to work correctly once booted? Or did it have issues?

---

### Post by pnaarmann on 2013-08-25
> **oldfred said:**
> Did DVD seem to work correctly once booted? Or did it have issues?

Yes it works fine, I even burned a CD with photos.


> **oldfred said:**
> Is DVD SATA2 and you have it in a SATA3 port? Or something similar. 
Do you have a SATA2 port to try with?

I checked the DVD drive [http://www.samsung.com/ph/consumer/monitor-peripherals-printer/optical-disc-drive/dvd-rw-drive/SH-S223C/RSBF-spec](http://www.samsung.com/ph/consumer/monitor-peripherals-printer/optical-disc-drive/dvd-rw-drive/SH-S223C/RSBF-spec)

It doesn't give me anything about SATA 2 or 3.

I checked the mainboard [http://www.asus.com/Motherboards/M5A87/#specifications](http://www.asus.com/Motherboards/M5A87/#specifications)

It has SATA 3 only.

Isn't SATA 3 downward compatible anyway?

---

### Post by oldfred on 2013-08-25
I think these were all older Asus motherboard, but users posted these as issues.

 Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.

---

### Post by pnaarmann on 2013-08-25
> **oldfred said:**
> I think these were all older Asus motherboard, but users posted these as issues.

 Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.

I found your last post from March regarding this bug a lot of ASUS motherboards are having issues with: [http://ubuntuforums.org/archive/index.php/t-2129374.html](http://ubuntuforums.org/archive/index.php/t-2129374.html)

After searching more and more I found, that this bug should have been fixed with kernel 2.6.38-10.46 (see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/802464](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/802464))

I have 3.8.0-29-generic updated two days ago, so this fix should be included?

Another fix was switching ACPI off in the BIOS. Isn't there another way?

---

### Post by oldfred on 2013-08-25
Older kernel fixes should be included in newer versions, although sometimes there are regressions. And most new UEFI systems are in AHCI mode automatically and that is the mode you really want.

While Asrock is different motherboard, they (or Linux) have issues with asmedia ports which somehow are different. And on  older systems we sometimes had issues with systems with added ports where some were Intel and some another vendor. Are all your ports the same?

---

### Post by jacob lastman on 2013-08-27
My suggestion after using ubuntu for some years but not being an expert, is use 12.04 LTS version.(it will be properly patched for years to come) I have had very little problem. Do a nice fresh install and use the correct file system (not NTS or FAT for windows).

---

### Post by jacob lastman on 2013-08-27
and use its 'suspend' option as long as you have battery or other backup to keep the PC alive

---

### Post by alesseon1 on 2014-04-09
I think that will have something with your hard drive, there is big waiting for something.. And few lines down is that too... But just guessing, i know small amout of informations about booting of linux...

> 
[    4.821750] hid-generic 0003:046D:C245.0002: hiddev0,hidraw1: USB HID v1.10 Device [Logitech Gaming Mouse G400] on usb-0000:00:12.0-5/input1
[   34.887829] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen


---

### Post by Coolgirl on 2014-04-09
t SSD have blazing boots speeds, if you can get your hands on one this will def increase your boots speed.. Hope this helps

---

