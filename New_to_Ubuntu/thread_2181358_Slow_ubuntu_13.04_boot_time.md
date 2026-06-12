---
title: "Slow ubuntu 13.04 boot time"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by Rui_Madaleno on 2013-10-17
I all !

i'd like your help to understant why my ubuntu is sooooo slow to boot.

here is my dmesg

```


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@aatxe) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 (Ubuntu 3.8.0-31.46-generic 3.8.13.8)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009b7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009b800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfecffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfed0000-0x00000000bfee2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfee3000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite A200/ISKAA, BIOS V2.00 01/09/2008
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbfed0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 3071M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000f71a0-0x000f71af] mapped at [c00f71a0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0097000] 97000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x37083000-0x37feffff]
[    0.000000] Allocated new RAMDISK: [mem 0x36116000-0x37082380]
[    0.000000] Move RAMDISK from [mem 0x37083000-0x37fef380] to [mem 0x36116000-0x37082380]
[    0.000000] ACPI: RSDP 000f7120 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT bfed7a5a 00094 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfedfb60 000F4 (v03 TOSCPL CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfed8e1a 06CD2 (v02 TOSCPL CRESTLNE 06040000 INTL 20060608)
[    0.000000] ACPI: FACS bfee2fc0 00040
[    0.000000] ACPI: APIC bfedfc54 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bfedfcbc 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfedfcf4 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA bfedfd30 00032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR bfedfd62 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC bfedfd88 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: OSFR bfedfefe 00072 (v01 TOSHIB A+2nd ID 06040000 TASM 04010000)
[    0.000000] ACPI: APIC bfedff70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfedffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT bfed8b6d 002AD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed807a 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed7fd4 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed7aee 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2178MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xbfecffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xbfecffff]
[    0.000000] On node 0 totalpages: 786011
[    0.000000] free_area_init_node: node 0, pgdat c18f7f00, node_mem_map f4916200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4358 pages used for memmap
[    0.000000]   HighMem zone: 553420 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34944 r0 d22400 u57344
[    0.000000] pcpu-alloc: s34944 r0 d22400 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779869
[    0.000000] Kernel command line: root=UUID=1114658d-a9e8-4088-b6f8-5eaa916db8e9 ro vga=771 quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6288896 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bfed0)
[    0.000000] Memory: 3085544k/3144512k available (6259k kernel code, 58500k reserved, 2973k data, 788k init, 2231112k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1905000 - 0xc19ca000   ( 788 kB)
[    0.000000]       .data : 0xc161cd30 - 0xc1904240   (2973 kB)
[    0.000000]       .text : 0xc1000000 - 0xc161cd30   (6259 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2394.075 MHz processor
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.15 BogoMIPS (lpj=9576300)
[    0.004004] pid_max: default: 32768 minimum: 301
[    0.004030] Security Framework initialized
[    0.004038] AppArmor: AppArmor initialized
[    0.004040] Yama: becoming mindful.
[    0.004081] Mount-cache hash table entries: 512
[    0.004262] Initializing cgroup subsys cpuacct
[    0.004264] Initializing cgroup subsys memory
[    0.004271] Initializing cgroup subsys devices
[    0.004273] Initializing cgroup subsys freezer
[    0.004275] Initializing cgroup subsys blkio
[    0.004277] Initializing cgroup subsys perf_event
[    0.004279] Initializing cgroup subsys hugetlb
[    0.004305] CPU: Physical Processor ID: 0
[    0.004306] CPU: Processor Core ID: 0
[    0.004309] mce: CPU supports 6 MCE banks
[    0.004314] CPU0: Thermal monitoring handled by SMI
[    0.004317] process: using mwait in idle threads
[    0.004324] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004324] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004324] tlb_flushall_shift: -1
[    0.004566] Freeing SMP alternatives: 24k freed
[    0.006334] ACPI: Core revision 20121018
[    0.006336] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.006392] ACPI: Forced DSDT copy: length 0x06CD2 copied locally, original unmapped
[    0.012010] ftrace: allocating 26139 entries in 52 pages
[    0.020085] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020505] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062982] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz (fam: 06, model: 17, stepping: 06)
[    0.064000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.064000] ... version:                2
[    0.064000] ... bit width:              40
[    0.064000] ... generic registers:      2
[    0.064000] ... value mask:             000000ffffffffff
[    0.064000] ... max period:             000000007fffffff
[    0.064000] ... fixed-purpose events:   3
[    0.064000] ... event mask:             0000000700000003
[    0.064000] CPU 1 irqstacks, hard=f44e0000 soft=f44e2000
[    0.064000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.074151] Brought up 2 CPUs
[    0.074156] smpboot: Total of 2 processors activated (9576.30 BogoMIPS)
[    0.074254] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076081] devtmpfs: initialized
[    0.076203] EVM: security.selinux
[    0.076205] EVM: security.SMACK64
[    0.076207] EVM: security.capability
[    0.076222] PM: Registering ACPI NVS region [mem 0xbfed0000-0xbfee2fff] (77824 bytes)
[    0.077041] regulator-dummy: no parameters
[    0.077095] NET: Registered protocol family 16
[    0.077227] EISA bus registered
[    0.077310] ACPI: bus type pci registered
[    0.077373] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.077376] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.077378] PCI: Using MMCONFIG for extended config space
[    0.077379] PCI: Using configuration type 1 for base access
[    0.078389] bio: create slab <bio-0> at 0
[    0.078389] ACPI: Added _OSI(Module Device)
[    0.078389] ACPI: Added _OSI(Processor Device)
[    0.078389] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.078389] ACPI: Added _OSI(Processor Aggregator Device)
[    0.078389] ACPI: EC: Look up EC in DSDT
[    0.080018] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.080544] ACPI: SSDT bfed87e9 002BC (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.080890] ACPI: Dynamic OEM Table Load:
[    0.080893] ACPI: SSDT   (null) 002BC (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.081013] ACPI: SSDT bfed82d9 0048B (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.081342] ACPI: Dynamic OEM Table Load:
[    0.081345] ACPI: SSDT   (null) 0048B (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.081568] ACPI: SSDT bfed8aa5 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.081906] ACPI: Dynamic OEM Table Load:
[    0.081909] ACPI: SSDT   (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.082004] ACPI: SSDT bfed8764 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.084233] ACPI: Dynamic OEM Table Load:
[    0.084236] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.084563] ACPI: Interpreter enabled
[    0.084571] ACPI: (supports S0 S3 S4 S5)
[    0.084588] ACPI: Using IOAPIC for interrupt routing
[    0.092025] ACPI: EC: GPE storm detected(12 GPEs), transactions will use polling mode
[    0.164663] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.164785] ACPI: No dock devices found.
[    0.164790] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.165108] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.165111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.165899] PCI host bridge to bus 0000:00
[    0.165903] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.165905] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.165908] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.165910] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.165912] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.165915] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.165917] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff]
[    0.165919] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.165930] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.165979] pci 0000:00:01.0: [8086:2a01] type 01 class 0x060400
[    0.166025] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.166081] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.166140] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.166184] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.166242] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.166301] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.166327] pci 0000:00:1a.7: reg 10: [mem 0xfc404800-0xfc404bff]
[    0.166438] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.166472] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.166496] pci 0000:00:1b.0: reg 10: [mem 0xfc400000-0xfc403fff 64bit]
[    0.166605] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.166637] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.166751] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.166786] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.166900] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.166935] pci 0000:00:1c.2: [8086:2843] type 01 class 0x060400
[    0.167049] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.167084] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.167196] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.167232] pci 0000:00:1c.4: [8086:2847] type 01 class 0x060400
[    0.167344] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.167379] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.167435] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.167478] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.167536] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.167580] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.167639] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.167699] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.167724] pci 0000:00:1d.7: reg 10: [mem 0xfc404c00-0xfc404fff]
[    0.167839] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.167867] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.167967] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.168087] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.168093] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.168097] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.168101] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.168160] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.168178] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.168190] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.168203] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.168216] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.168229] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.168285] pci 0000:00:1f.2: [8086:2829] type 00 class 0x010601
[    0.168313] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.168325] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.168338] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.168350] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.168362] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.168375] pci 0000:00:1f.2: reg 24: [mem 0xfc404000-0xfc4047ff]
[    0.168441] pci 0000:00:1f.2: PME# supported from D3hot
[    0.168466] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.168483] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.168527] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.168612] pci 0000:01:00.0: [1002:9581] type 00 class 0x030000
[    0.168630] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.168642] pci 0000:01:00.0: reg 14: [io  0x2000-0x20ff]
[    0.168654] pci 0000:01:00.0: reg 18: [mem 0xfc000000-0xfc00ffff]
[    0.168697] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.168753] pci 0000:01:00.0: supports D1 D2
[    0.168785] pci 0000:01:00.1: [1002:aa08] type 00 class 0x040300
[    0.168803] pci 0000:01:00.1: reg 10: [mem 0xfc010000-0xfc013fff]
[    0.168918] pci 0000:01:00.1: supports D1 D2
[    0.176014] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.176018] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.176021] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.176026] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.176089] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.176094] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.176099] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf3ffffff]
[    0.176107] pci 0000:00:1c.0:   bridge window [mem 0xce000000-0xcfffffff 64bit pref]
[    0.176201] pci 0000:04:00.0: [10ec:8136] type 00 class 0x020000
[    0.176226] pci 0000:04:00.0: reg 10: [io  0x4000-0x40ff]
[    0.176267] pci 0000:04:00.0: reg 18: [mem 0xf4000000-0xf4000fff 64bit]
[    0.176315] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.176425] pci 0000:04:00.0: supports D1 D2
[    0.176427] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.176461] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.176473] pci 0000:00:1c.1: PCI bridge to [bus 04]
[    0.176479] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.176484] pci 0000:00:1c.1:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.176492] pci 0000:00:1c.1:   bridge window [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.176616] pci 0000:05:00.0: [8086:4229] type 00 class 0x028000
[    0.176665] pci 0000:05:00.0: reg 10: [mem 0xf8000000-0xf8001fff 64bit]
[    0.176888] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.184043] pci 0000:00:1c.2: PCI bridge to [bus 05]
[    0.184048] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.184053] pci 0000:00:1c.2:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.184061] pci 0000:00:1c.2:   bridge window [mem 0xca000000-0xcbffffff 64bit pref]
[    0.184155] pci 0000:06:00.0: [8086:444e] type 00 class 0x058000
[    0.184182] pci 0000:06:00.0: reg 10: [mem 0xc4000000-0xc40003ff]
[    0.184219] pci 0000:06:00.0: reg 18: [io  0x6000-0x607f]
[    0.184290] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.192019] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.192024] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
[    0.192029] pci 0000:00:1c.3:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.192037] pci 0000:00:1c.3:   bridge window [mem 0xc8000000-0xc9ffffff 64bit pref]
[    0.192101] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.192167] pci 0000:0c:04.0: [104c:8039] type 02 class 0x060700
[    0.192192] pci 0000:0c:04.0: reg 10: [mem 0xfc100000-0xfc100fff]
[    0.192235] pci 0000:0c:04.0: supports D1 D2
[    0.192237] pci 0000:0c:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192264] pci 0000:0c:04.1: [104c:803a] type 00 class 0x0c0010
[    0.192289] pci 0000:0c:04.1: reg 10: [mem 0xfc102000-0xfc1027ff]
[    0.192303] pci 0000:0c:04.1: reg 14: [mem 0xfc104000-0xfc107fff]
[    0.192408] pci 0000:0c:04.1: supports D1 D2
[    0.192410] pci 0000:0c:04.1: PME# supported from D0 D1 D2 D3hot
[    0.192437] pci 0000:0c:04.2: [104c:803b] type 00 class 0x018000
[    0.192461] pci 0000:0c:04.2: reg 10: [mem 0xfc101000-0xfc101fff]
[    0.192572] pci 0000:0c:04.2: supports D1 D2
[    0.192575] pci 0000:0c:04.2: PME# supported from D0 D1 D2 D3hot
[    0.192600] pci 0000:0c:04.3: [104c:803c] type 00 class 0x080501
[    0.192625] pci 0000:0c:04.3: reg 10: [mem 0xfc102800-0xfc1028ff]
[    0.192737] pci 0000:0c:04.3: supports D1 D2
[    0.192739] pci 0000:0c:04.3: PME# supported from D0 D1 D2 D3hot
[    0.192805] pci 0000:00:1e.0: PCI bridge to [bus 0c-0d] (subtractive decode)
[    0.192813] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.192821] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.192823] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.192826] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.192828] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.192830] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.192833] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.192835] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.192882] pci_bus 0000:0d: busn_res: can not insert [bus 0d-ff] under [bus 0c-0d] (conflicts with (null) [bus 0c-0d])
[    0.192887] pci_bus 0000:0d: busn_res: [bus 0d-ff] end is updated to 10
[    0.192890] pci_bus 0000:0d: busn_res: can not insert [bus 0d-10] under [bus 0c-0d] (conflicts with (null) [bus 0c-0d])
[    0.192894] pci_bus 0000:0d: [bus 0d-10] partially hidden behind transparent bridge 0000:0c [bus 0c-0d]
[    0.192937] pci_bus 0000:00: on NUMA node 0
[    0.192950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.193008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.193056] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.193104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.193152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.193200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.193273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.193333]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.193336]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.194624] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.194674] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.194721] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.194768] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.194815] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.194865] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.194912] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.194958] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.196021] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.196025] vgaarb: loaded
[    0.196027] vgaarb: bridge control possible 0000:01:00.0
[    0.196242] SCSI subsystem initialized
[    0.196245] ACPI: bus type scsi registered
[    0.196253] libata version 3.00 loaded.
[    0.196253] ACPI: bus type usb registered
[    0.196253] usbcore: registered new interface driver usbfs
[    0.196253] usbcore: registered new interface driver hub
[    0.196253] usbcore: registered new device driver usb
[    0.196253] PCI: Using ACPI for IRQ routing
[    0.206554] PCI: pci_cache_line_size set to 64 bytes
[    0.206706] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
[    0.206708] e820: reserve RAM buffer [mem 0xbfed0000-0xbfffffff]
[    0.206795] NetLabel: Initializing
[    0.206797] NetLabel:  domain hash size = 128
[    0.206799] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206810] NetLabel:  unlabeled traffic allowed by default
[    0.208069] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.208075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.208079] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.208079] Switching to clocksource hpet
[    0.215634] AppArmor: AppArmor Filesystem Enabled
[    0.215668] pnp: PnP ACPI init
[    0.215683] ACPI: bus type pnp registered
[    0.215877] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.215880] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.215883] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.215886] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.215889] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.215891] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.215894] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.215897] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.215901] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.216132] pnp 00:01: [dma 4]
[    0.216162] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.216193] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.216295] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.216299] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.216345] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.216410] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.216413] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.216416] system 00:05: [io  0x1000-0x107f] has been reserved
[    0.216418] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.216423] system 00:05: [io  0xfe00] has been reserved
[    0.216426] system 00:05: [io  0xff00-0xff7f] has been reserved
[    0.216429] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.216468] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.252059] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.252100] pnp 00:08: Plug and Play ACPI device, IDs SYN0705 SYN0700 SYN0002 PNP0f13 (active)
[    0.252137] pnp: PnP ACPI: found 9 devices
[    0.252139] ACPI: ACPI bus type pnp unregistered
[    0.252142] PnPBIOS: Disabled by ACPI PNP
[    0.288825] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 09] add_size 1000
[    0.288830] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 09] add_size 200000
[    0.288833] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 09] add_size 200000
[    0.288853] pci 0000:0c:04.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.288856] pci 0000:0c:04.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.288859] pci 0000:00:1e.0: bridge window [io  0x1000-0x0fff] to [bus 0c-0d] add_size 1000
[    0.288862] pci 0000:0c:04.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.288865] pci 0000:00:1e.0: bridge window [mem 0x04000000-0x03ffffff pref] to [bus 0c-0d] add_size 4000000
[    0.288872] pci 0000:00:1e.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.288875] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.288878] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.288880] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.288883] pci 0000:00:1e.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.288890] pci 0000:00:1e.0: BAR 15: assigned [mem 0xc0000000-0xc3ffffff pref]
[    0.288893] pci 0000:00:1c.4: BAR 14: assigned [mem 0xfc200000-0xfc3fffff]
[    0.288897] pci 0000:00:1c.4: BAR 15: assigned [mem 0xfc500000-0xfc6fffff 64bit pref]
[    0.288901] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
[    0.288904] pci 0000:00:1e.0: BAR 13: assigned [io  0x8000-0x8fff]
[    0.288908] pci 0000:00:1f.3: BAR 0: assigned [mem 0xfc405000-0xfc4050ff]
[    0.288916] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc020000-0xfc03ffff pref]
[    0.288919] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.288921] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.288925] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.288929] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.288934] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.288937] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.288943] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf3ffffff]
[    0.288949] pci 0000:00:1c.0:   bridge window [mem 0xce000000-0xcfffffff 64bit pref]
[    0.288957] pci 0000:04:00.0: BAR 6: assigned [mem 0xcc000000-0xcc01ffff pref]
[    0.288960] pci 0000:00:1c.1: PCI bridge to [bus 04]
[    0.288963] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.288970] pci 0000:00:1c.1:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.288975] pci 0000:00:1c.1:   bridge window [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.288983] pci 0000:00:1c.2: PCI bridge to [bus 05]
[    0.288986] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.288993] pci 0000:00:1c.2:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.288997] pci 0000:00:1c.2:   bridge window [mem 0xca000000-0xcbffffff 64bit pref]
[    0.289006] pci 0000:06:00.0: BAR 6: assigned [mem 0xc8000000-0xc800ffff pref]
[    0.289008] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.289011] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
[    0.289017] pci 0000:00:1c.3:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.289022] pci 0000:00:1c.3:   bridge window [mem 0xc8000000-0xc9ffffff 64bit pref]
[    0.289030] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.289033] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
[    0.289040] pci 0000:00:1c.4:   bridge window [mem 0xfc200000-0xfc3fffff]
[    0.289045] pci 0000:00:1c.4:   bridge window [mem 0xfc500000-0xfc6fffff 64bit pref]
[    0.289054] pci 0000:0c:04.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.289057] pci 0000:0c:04.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.289059] pci 0000:0c:04.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.289062] pci 0000:0c:04.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.289065] pci 0000:0c:04.0: BAR 15: assigned [mem 0xc0000000-0xc3ffffff pref]
[    0.289070] pci 0000:0c:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.289073] pci 0000:0c:04.0: BAR 13: assigned [io  0x8000-0x80ff]
[    0.289076] pci 0000:0c:04.0: BAR 14: assigned [io  0x8400-0x84ff]
[    0.289081] pci 0000:0c:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.289084] pci 0000:0c:04.0: BAR 15: assigned [mem 0xc0000000-0xc3ffffff pref]
[    0.289086] pci 0000:0c:04.0: BAR 14: assigned [io  0x8000-0x80ff]
[    0.289089] pci 0000:0c:04.0: BAR 13: assigned [io  0x8400-0x84ff]
[    0.289091] pci 0000:0c:04.0: CardBus bridge to [bus 0d-10]
[    0.289094] pci 0000:0c:04.0:   bridge window [io  0x8400-0x84ff]
[    0.289099] pci 0000:0c:04.0:   bridge window [io  0x8000-0x80ff]
[    0.289105] pci 0000:0c:04.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[    0.289110] pci 0000:00:1e.0: PCI bridge to [bus 0c-0d]
[    0.289113] pci 0000:00:1e.0:   bridge window [io  0x8000-0x8fff]
[    0.289119] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.289124] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[    0.289181] pci 0000:00:1e.0: setting latency timer to 64
[    0.289193] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.289196] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.289198] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.289200] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.289203] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.289205] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xdfffffff]
[    0.289207] pci_bus 0000:00: resource 10 [mem 0xf0000000-0xfebfffff]
[    0.289210] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.289212] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfc0fffff]
[    0.289215] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.289217] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.289219] pci_bus 0000:02: resource 1 [mem 0xf0000000-0xf3ffffff]
[    0.289222] pci_bus 0000:02: resource 2 [mem 0xce000000-0xcfffffff 64bit pref]
[    0.289224] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.289227] pci_bus 0000:04: resource 1 [mem 0xf4000000-0xf7ffffff]
[    0.289229] pci_bus 0000:04: resource 2 [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.289231] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.289234] pci_bus 0000:05: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.289236] pci_bus 0000:05: resource 2 [mem 0xca000000-0xcbffffff 64bit pref]
[    0.289238] pci_bus 0000:06: resource 0 [io  0x6000-0x6fff]
[    0.289241] pci_bus 0000:06: resource 1 [mem 0xc4000000-0xc7ffffff]
[    0.289243] pci_bus 0000:06: resource 2 [mem 0xc8000000-0xc9ffffff 64bit pref]
[    0.289245] pci_bus 0000:09: resource 0 [io  0x7000-0x7fff]
[    0.289247] pci_bus 0000:09: resource 1 [mem 0xfc200000-0xfc3fffff]
[    0.289250] pci_bus 0000:09: resource 2 [mem 0xfc500000-0xfc6fffff 64bit pref]
[    0.289252] pci_bus 0000:0c: resource 0 [io  0x8000-0x8fff]
[    0.289255] pci_bus 0000:0c: resource 1 [mem 0xfc100000-0xfc1fffff]
[    0.289257] pci_bus 0000:0c: resource 2 [mem 0xc0000000-0xc3ffffff pref]
[    0.289259] pci_bus 0000:0c: resource 4 [io  0x0000-0x0cf7]
[    0.289261] pci_bus 0000:0c: resource 5 [io  0x0d00-0xffff]
[    0.289264] pci_bus 0000:0c: resource 6 [mem 0x000a0000-0x000bffff]
[    0.289266] pci_bus 0000:0c: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.289268] pci_bus 0000:0c: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.289270] pci_bus 0000:0c: resource 9 [mem 0xc0000000-0xdfffffff]
[    0.289273] pci_bus 0000:0c: resource 10 [mem 0xf0000000-0xfebfffff]
[    0.289275] pci_bus 0000:0d: resource 0 [io  0x8400-0x84ff]
[    0.289277] pci_bus 0000:0d: resource 1 [io  0x8000-0x80ff]
[    0.289280] pci_bus 0000:0d: resource 2 [mem 0xc0000000-0xc3ffffff pref]
[    0.289315] NET: Registered protocol family 2
[    0.289465] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.289496] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.289531] TCP: Hash tables configured (established 8192 bind 8192)
[    0.289565] TCP: reno registered
[    0.289567] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.289576] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.289631] NET: Registered protocol family 1
[    0.289839] pci 0000:01:00.0: Boot video device
[    0.289888] PCI: CLS 64 bytes, default 64
[    0.289927] Trying to unpack rootfs image as initramfs...
[    0.586012] Freeing initrd memory: 15796k freed
[    0.594150] Simple Boot Flag at 0x36 set to 0x1
[    0.594480] Initialise module verification
[    0.594527] audit: initializing netlink socket (disabled)
[    0.594546] type=2000 audit(1382037875.592:1): initialized
[    0.615493] bounce pool size: 64 pages
[    0.615507] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.617119] VFS: Disk quotas dquot_6.5.2
[    0.617170] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.617723] fuse init (API version 7.20)
[    0.617810] msgmni has been set to 1699
[    0.618259] Key type asymmetric registered
[    0.618262] Asymmetric key parser 'x509' registered
[    0.618297] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.618326] io scheduler noop registered
[    0.618328] io scheduler deadline registered (default)
[    0.618335] io scheduler cfq registered
[    0.618492] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.618590] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.618713] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.618837] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.618959] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.619080] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.619174] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.619191] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.619250] intel_idle: does not run on family 6 model 23
[    0.619369] ACPI: AC Adapter [ACAD] (on-line)
[    0.619423] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.619440] ACPI: Lid Switch [LID0]
[    0.619476] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.619480] ACPI: Power Button [PWRB]
[    0.619526] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.619529] ACPI: Power Button [PWRF]
[    0.619602] ACPI: Requesting acpi_cpufreq
[    0.621655] Monitor-Mwait will be used to enter C-1 state
[    0.621661] Monitor-Mwait will be used to enter C-2 state
[    0.621665] Monitor-Mwait will be used to enter C-3 state
[    0.621668] tsc: Marking TSC unstable due to TSC halts in idle
[    0.621678] ACPI: acpi_idle registered with cpuidle
[    0.696195] GHES: HEST is not enabled!
[    0.696252] isapnp: Scanning for PnP cards...
[    0.700073] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.920112] ACPI: Battery Slot [BAT1] (battery present)
[    0.920205] Linux agpgart interface v0.103
[    0.921612] brd: module loaded
[    0.922279] loop: module loaded
[    0.922388] ata_piix 0000:00:1f.1: version 2.13
[    0.922432] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.922668] scsi0 : ata_piix
[    0.922999] scsi1 : ata_piix
[    0.923042] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.923044] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.923323] libphy: Fixed MDIO Bus: probed
[    0.923396] tun: Universal TUN/TAP device driver, 1.6
[    0.923398] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.923452] PPP generic driver version 2.4.2
[    0.923487] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.923489] ehci-pci: EHCI PCI platform driver
[    0.923512] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    0.923516] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.923522] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.923537] ehci-pci 0000:00:1a.7: debug port 1
[    0.927454] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.927470] ehci-pci 0000:00:1a.7: irq 18, io mem 0xfc404800
[    0.936020] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.936053] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.936056] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.936059] usb usb1: Product: EHCI Host Controller
[    0.936061] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    0.936063] usb usb1: SerialNumber: 0000:00:1a.7
[    0.936157] hub 1-0:1.0: USB hub found
[    0.936162] hub 1-0:1.0: 4 ports detected
[    0.936302] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.936306] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.936311] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.936326] ehci-pci 0000:00:1d.7: debug port 1
[    0.940216] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.940234] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    0.952019] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.952034] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.952036] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.952039] usb usb2: Product: EHCI Host Controller
[    0.952041] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    0.952043] usb usb2: SerialNumber: 0000:00:1d.7
[    0.952130] hub 2-0:1.0: USB hub found
[    0.952134] hub 2-0:1.0: 6 ports detected
[    0.952303] ehci-platform: EHCI generic platform driver
[    0.952311] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.952329] uhci_hcd: USB Universal Host Controller Interface driver
[    0.952348] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.952351] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.952356] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.952393] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.952423] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.952426] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.952428] usb usb3: Product: UHCI Host Controller
[    0.952430] usb usb3: Manufacturer: Linux 3.8.0-31-generic uhci_hcd
[    0.952432] usb usb3: SerialNumber: 0000:00:1a.0
[    0.952509] hub 3-0:1.0: USB hub found
[    0.952513] hub 3-0:1.0: 2 ports detected
[    0.952589] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.952593] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.952598] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.952634] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.952664] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.952666] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.952668] usb usb4: Product: UHCI Host Controller
[    0.952671] usb usb4: Manufacturer: Linux 3.8.0-31-generic uhci_hcd
[    0.952673] usb usb4: SerialNumber: 0000:00:1a.1
[    0.952748] hub 4-0:1.0: USB hub found
[    0.952752] hub 4-0:1.0: 2 ports detected
[    0.952830] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.952834] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.952838] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.952865] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.952896] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.952898] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.952901] usb usb5: Product: UHCI Host Controller
[    0.952903] usb usb5: Manufacturer: Linux 3.8.0-31-generic uhci_hcd
[    0.952905] usb usb5: SerialNumber: 0000:00:1d.0
[    0.952982] hub 5-0:1.0: USB hub found
[    0.952986] hub 5-0:1.0: 2 ports detected
[    0.953063] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.953067] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.953071] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.953106] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.953139] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.953142] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.953144] usb usb6: Product: UHCI Host Controller
[    0.953146] usb usb6: Manufacturer: Linux 3.8.0-31-generic uhci_hcd
[    0.953148] usb usb6: SerialNumber: 0000:00:1d.1
[    0.953225] hub 6-0:1.0: USB hub found
[    0.953228] hub 6-0:1.0: 2 ports detected
[    0.953306] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.953309] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.953314] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.953340] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.953371] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.953374] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.953376] usb usb7: Product: UHCI Host Controller
[    0.953378] usb usb7: Manufacturer: Linux 3.8.0-31-generic uhci_hcd
[    0.953380] usb usb7: SerialNumber: 0000:00:1d.2
[    0.953457] hub 7-0:1.0: USB hub found
[    0.953461] hub 7-0:1.0: 2 ports detected
[    0.953593] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.983093] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.983098] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.983194] mousedev: PS/2 mouse device common for all mice
[    0.986045] rtc_cmos 00:06: RTC can wake from S4
[    0.986171] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.986202] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.986291] device-mapper: uevent: version 1.0.3
[    0.986345] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.986361] EISA: Probing bus 0 at eisa.0
[    0.986363] EISA: Cannot allocate resource for mainboard
[    0.986365] Cannot allocate resource for EISA slot 1
[    0.986366] Cannot allocate resource for EISA slot 2
[    0.986368] Cannot allocate resource for EISA slot 3
[    0.986370] Cannot allocate resource for EISA slot 4
[    0.986371] Cannot allocate resource for EISA slot 5
[    0.986373] Cannot allocate resource for EISA slot 6
[    0.986374] Cannot allocate resource for EISA slot 7
[    0.986376] Cannot allocate resource for EISA slot 8
[    0.986377] EISA: Detected 0 cards.
[    0.986386] cpufreq-nforce2: No nForce2 chipset.
[    0.986424] cpuidle: using governor ladder
[    0.986475] cpuidle: using governor menu
[    0.986478] ledtrig-cpu: registered to indicate activity on CPUs
[    0.986480] EFI Variables Facility v0.08 2004-May-17
[    0.986618] ashmem: initialized
[    0.986733] TCP: cubic registered
[    0.986833] NET: Registered protocol family 10
[    0.987017] NET: Registered protocol family 17
[    0.987027] Key type dns_resolver registered
[    0.987162] Using IPI No-Shortcut mode
[    0.987228] Loading module verification certificates
[    0.991115] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: be06a87ed5dd6bd2e94b82fbc0aa607728b7aeda'
[    0.991127] registered taskstats version 1
[    0.993572] Key type trusted registered
[    0.995575] Key type encrypted registered
[    0.998171] rtc_cmos 00:06: setting system clock to 2013-10-17 19:24:36 UTC (1382037876)
[    0.998627] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.998629] EDD information not available.
[    1.008931] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.050346] isapnp: No Plug & Play device found
[    1.091313] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.40, max UDMA/33
[    1.104392] ata1.00: configured for UDMA/33
[    1.107275] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.40 PQ: 0 ANSI: 5
[    1.109748] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.109752] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.109930] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.110049] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.110214] Freeing unused kernel memory: 788k freed
[    1.110531] Write protecting the kernel text: 6260k
[    1.110599] Write protecting the kernel read-only data: 2436k
[    1.110601] NX-protecting the kernel data: 3980k
[    1.131124] udevd[115]: starting version 175
[    1.184706] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.184951] r8169 0000:04:00.0: irq 46 for MSI/MSI-X
[    1.185134] r8169 0000:04:00.0 eth0: RTL8101e at 0xf8412000, 00:1e:ec:01:67:cd, XID 94200000 IRQ 46
[    1.222564] Disabling lock debugging due to kernel taint
[    1.223174] ahci 0000:00:1f.2: version 3.0
[    1.223248] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.223323] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.223327] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.223332] ahci 0000:00:1f.2: setting latency timer to 64
[    1.225028] sdhci: Secure Digital Host Controller Interface driver
[    1.225030] sdhci: Copyright(c) Pierre Ossman
[    1.229397] scsi2 : ahci
[    1.229900] sdhci-pci 0000:0c:04.3: SDHCI controller found [104c:803c] (rev 0)
[    1.229944] mmc0: no vqmmc regulator found
[    1.229946] mmc0: no vmmc regulator found
[    1.230020] scsi3 : ahci
[    1.230156] scsi4 : ahci
[    1.230225] ata3: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 47
[    1.230229] ata4: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 47
[    1.230232] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404200 irq 47
[    1.248453] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.264071] mmc0: SDHCI controller on PCI [0000:0c:04.3] using DMA
[    1.320194] firewire_ohci 0000:0c:04.1: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.394053] usb 1-3: New USB device found, idVendor=04f2, idProduct=b008
[    1.394060] usb 1-3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.394065] usb 1-3: Product: Chicony USB 2.0 Camera
[    1.394070] usb 1-3: Manufacturer: Chicony Electronics Co., Ltd.
[    1.394074] usb 1-3: SerialNumber: SN0001
[    1.548142] ata4: SATA link down (SStatus 0 SControl 300)
[    1.548177] ata5: SATA link down (SStatus 0 SControl 300)
[    1.820160] firewire_core 0000:0c:04.1: created device fw0: GUID 00023f81ad4257b9, S400
[    1.884122] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.884714] ata3.00: unexpected _GTF length (8)
[    1.896055] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    2.078172] usb 7-1: New USB device found, idVendor=045e, idProduct=0039
[    2.078179] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.078183] usb 7-1: Product: Microsoft IntelliMouse\xffffffc2\xffffffae\xffffffae Optical
[    2.078188] usb 7-1: Manufacturer: Microsoft
[    2.110259] usbcore: registered new interface driver usbhid
[    2.110264] usbhid: USB HID core driver
[    2.116399] input: Microsoft Microsoft IntelliMouse\xffffffc2\xffffffae\xffffffae Optical as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input4
[    2.116534] hid-generic 0003:045E:0039.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse\xffffffc2\xffffffae\xffffffae Optical] on usb-0000:00:1d.2-1/input0
[    2.244594] ata3.00: ATA-8: TOSHIBA MK2546GSX, LB013M, max UDMA/100
[    2.244599] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.245528] ata3.00: unexpected _GTF length (8)
[    2.245778] ata3.00: configured for UDMA/100
[    2.246020] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2546GS LB01 PQ: 0 ANSI: 5
[    2.246185] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.246251] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.246368] sd 2:0:0:0: [sda] Write Protect is off
[    2.246372] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.246436] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.341345]  sda: sda3 sda4 < sda5 sda6 >
[    2.341843] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.768439] kjournald starting.  Commit interval 5 seconds
[    2.768514] EXT3-fs (sda5): mounted filesystem with ordered data mode
[    6.322501] Adding 2192836k swap on /dev/sda6.  Priority:-1 extents:1 across:2192836k 
[    8.373217] EXT3-fs (sda5): using internal journal
[   10.690193] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.483293] udevd[427]: starting version 175
[   12.947539] lp: driver loaded but no devices found
[   15.207305] wmi: Mapper loaded
[   15.208274] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   15.208303] acpi device:03: registered as cooling_device2
[   15.224097] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.224196] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[   15.234935] yenta_cardbus 0000:0c:04.0: CardBus bridge found [1179:ff00]
[   15.234964] yenta_cardbus 0000:0c:04.0: CardBus bridge to [bus 0d-10]
[   15.234968] yenta_cardbus 0000:0c:04.0:   bridge window [io  0x8400-0x84ff]
[   15.234973] yenta_cardbus 0000:0c:04.0:   bridge window [io  0x8000-0x80ff]
[   15.234979] yenta_cardbus 0000:0c:04.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[   15.234984] yenta_cardbus 0000:0c:04.0:   bridge window [mem 0xfc800000-0xfcbfffff]
[   15.234992] yenta_cardbus 0000:0c:04.0: Enabling burst memory read transactions
[   15.234997] yenta_cardbus 0000:0c:04.0: Using CSCINT to route CSC interrupts to PCI
[   15.234999] yenta_cardbus 0000:0c:04.0: Routing CardBus interrupts to PCI
[   15.235005] yenta_cardbus 0000:0c:04.0: TI: mfunc 0x10a01b22, devctl 0x64
[   15.268078] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   15.274729] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   15.275377] input: Toshiba input device as /devices/virtual/input/input6
[   15.291201] microcode: CPU0 sig=0x10676, pf=0x80, revision=0x607
[   15.379563] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   15.379570] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.379575] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   15.379578] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.379580] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   15.379584] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.379585] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.386706] microcode: CPU1 sig=0x10676, pf=0x80, revision=0x607
[   15.388706] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.464836] yenta_cardbus 0000:0c:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   15.464842] yenta_cardbus 0000:0c:04.0: Socket status: 30000006
[   15.464846] pci_bus 0000:0c: Raising subordinate bus# of parent bus (#0c) from #0d to #10
[   15.464856] yenta_cardbus 0000:0c:04.0: pcmcia: parent PCI bridge window: [io  0x8000-0x8fff]
[   15.464859] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x8000-0x8fff:
[   15.466276]  excluding 0x8000-0x80ff 0x8400-0x84ff
[   15.471552] yenta_cardbus 0000:0c:04.0: pcmcia: parent PCI bridge window: [mem 0xfc100000-0xfc1fffff]
[   15.471555] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc100000-0xfc1fffff:
[   15.471559]  excluding 0xfc100000-0xfc10ffff
[   15.471570] yenta_cardbus 0000:0c:04.0: pcmcia: parent PCI bridge window: [mem 0xc0000000-0xc3ffffff pref]
[   15.471573] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0000000-0xc3ffffff:
[   15.471585]  excluding 0xc0000000-0xc3ffffff
[   15.504577] cfg80211: Calling CRDA to update world regulatory domain
[   15.625508] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   16.060892] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.061985] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.062376] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.062453] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   16.080464] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   16.109374] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   16.110465]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   16.111329] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   16.111719]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   16.112270] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   16.112914]  clean.
[   16.112930] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   16.113641]  clean.
[   16.113660] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   16.113665]  excluding 0xc0000-0xd3fff 0xdc000-0xfffff
[   16.113690] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   16.113700]  excluding 0xa0000000-0xa0ffffff
[   16.113717] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   16.113728]  excluding 0x60000000-0x60ffffff
[   16.113745] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   16.114476]  clean.
[   16.132031] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[   16.147588] [drm] Initialized drm 1.1.0 20060810
[   16.185800] kvm: disabled by bios
[   16.314320] usb 3-2: New USB device found, idVendor=0930, idProduct=0508
[   16.314328] usb 3-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   16.511152] [drm] radeon defaulting to kernel modesetting.
[   16.511156] [drm] radeon kernel modesetting enabled.
[   16.511569] [drm] initializing kernel modesetting (RV630 0x1002:0x9581 0x1179:0xFF00).
[   16.511589] [drm] register mmio base: 0xFC000000
[   16.511591] [drm] register mmio size: 65536
[   16.511695] ATOM BIOS: ISRAA
[   16.511719] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[   16.511722] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[   16.513332] [drm] Detected VRAM RAM=256M, BAR=256M
[   16.513335] [drm] RAM width 128bits DDR
[   16.513405] [TTM] Zone  kernel: Available graphics memory: 435520 kiB
[   16.513407] [TTM] Zone highmem: Available graphics memory: 1551076 kiB
[   16.513409] [TTM] Initializing pool allocator
[   16.513414] [TTM] Initializing DMA pool allocator
[   16.513440] [drm] radeon: 256M of VRAM memory ready
[   16.513442] [drm] radeon: 512M of GTT memory ready.
[   16.513461] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   16.514208] [drm] probing gen 2 caps for device 8086:2a01 = 1/0
[   16.514265] [drm] Loading RV630 Microcode
[   16.578537] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.5, id: 0x82e0b1, caps: 0xb04711/0xe0440d/0x0, board id: 3655, fw id: 316507
[   16.578543] psmouse serio1: synaptics: Toshiba Satellite A200 detected, limiting rate to 40pps.
[   16.677330] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   16.690024] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   16.690028] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   16.690158] iwl4965 0000:05:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   16.732554] iwl4965 0000:05:00.0: device EEPROM VER=0x36, CALIB=0x5
[   16.732572] iwl4965 0000:05:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   16.732710] iwl4965 0000:05:00.0: irq 50 for MSI/MSI-X
[   16.991254] Bluetooth: Core ver 2.16
[   16.991302] NET: Registered protocol family 31
[   16.991304] Bluetooth: HCI device and connection manager initialized
[   16.991902] Bluetooth: HCI socket layer initialized
[   16.991906] Bluetooth: L2CAP socket layer initialized
[   16.991913] Bluetooth: SCO socket layer initialized
[   17.167603] iwl4965 0000:05:00.0: loaded firmware version 228.61.2.24
[   17.236598] usbcore: registered new interface driver btusb
[   17.257209] cfg80211: World regulatory domain updated:
[   17.257213] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.257215] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.257217] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.257219] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.257221] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.257223] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.263351] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   17.582872] type=1400 audit(1382034293.083:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=758 comm="apparmor_parser"
[   17.582882] type=1400 audit(1382034293.083:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=695 comm="apparmor_parser"
[   17.583310] type=1400 audit(1382034293.083:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=758 comm="apparmor_parser"
[   17.583319] type=1400 audit(1382034293.083:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[   17.583541] type=1400 audit(1382034293.083:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=758 comm="apparmor_parser"
[   17.583552] type=1400 audit(1382034293.083:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[   17.584382] type=1400 audit(1382034293.083:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
[   17.584804] type=1400 audit(1382034293.083:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   17.585039] type=1400 audit(1382034293.083:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
[   17.735353] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   17.735412] radeon 0000:01:00.0: WB enabled
[   17.735416] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000c00 and cpu addr 0xffc13c00
[   17.735419] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000010000c0c and cpu addr 0xffc13c0c
[   17.735422] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.735424] [drm] Driver supports precise vblank timestamp query.
[   17.735483] radeon 0000:01:00.0: irq 51 for MSI/MSI-X
[   17.735501] radeon 0000:01:00.0: radeon: using MSI.
[   17.735531] [drm] radeon: irq initialized.
[   17.766939] [drm] ring test on 0 succeeded in 1 usecs
[   17.766999] [drm] ring test on 3 succeeded in 1 usecs
[   17.767157] [drm] ib test on ring 0 succeeded in 0 usecs
[   17.767172] [drm] ib test on ring 3 succeeded in 0 usecs
[   17.767833] [drm] Radeon Display Connectors
[   17.767835] [drm] Connector 0:
[   17.767837] [drm]   VGA-1
[   17.767839] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   17.767840] [drm]   Encoders:
[   17.767842] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   17.767843] [drm] Connector 1:
[   17.767845] [drm]   HDMI-A-1
[   17.767846] [drm]   HPD1
[   17.767848] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   17.767850] [drm]   Encoders:
[   17.767851] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   17.767852] [drm] Connector 2:
[   17.767854] [drm]   DIN-1
[   17.767855] [drm]   Encoders:
[   17.767857] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   17.767858] [drm] Connector 3:
[   17.767860] [drm]   LVDS-1
[   17.767862] [drm]   DDC: 0xac0 0xac0 0xac4 0xac4 0xac8 0xac8 0xacc 0xacc
[   17.767863] [drm]   Encoders:
[   17.767864] [drm]     LCD1: INTERNAL_LVTM1
[   17.767900] [drm] Internal thermal controller without fan control
[   17.767961] [drm] radeon: power management initialized
[   18.448503] Linux video capture interface: v2.00
[   18.456305] [drm] fb mappable at 0xD0142000
[   18.456308] [drm] vram apper at 0xD0000000
[   18.456309] [drm] size 4096000
[   18.456311] [drm] fb depth is 24
[   18.456312] [drm]    pitch is 5120
[   18.456407] fbcon: radeondrmfb (fb0) is primary device
[   18.696183] Console: switching to colour frame buffer device 160x50
[   18.699893] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   18.699895] radeon 0000:01:00.0: registered panic notifier
[   18.699911] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0
[   18.976390] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   18.979582] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input11
[   18.979752] usbcore: registered new interface driver uvcvideo
[   18.979754] USB Video Class driver (1.1.1)
[   19.115814] init: failsafe main process (780) killed by TERM signal
[   25.410819] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.410824] Bluetooth: BNEP filters: protocol multicast
[   25.410833] Bluetooth: BNEP socket layer initialized
[   25.718125] init: avahi-cups-reload main process (890) terminated with status 1
[   25.789001] Bluetooth: RFCOMM TTY layer initialized
[   25.789016] Bluetooth: RFCOMM socket layer initialized
[   25.789018] Bluetooth: RFCOMM ver 1.11
[   26.022476] ppdev: user-space parallel port driver
[   27.164660] type=1400 audit(1382034302.663:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=908 comm="apparmor_parser"
[   27.165119] type=1400 audit(1382034302.663:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=908 comm="apparmor_parser"
[   33.217193] r8169 0000:04:00.0 eth0: link down
[   33.217220] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.217518] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.466424] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.466753] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.985169] type=1400 audit(1382034311.483:13): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1017 comm="apparmor_parser"
[   36.003764] type=1400 audit(1382034311.499:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1018 comm="apparmor_parser"
[   36.004132] type=1400 audit(1382034311.503:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1018 comm="apparmor_parser"
[   36.059295] type=1400 audit(1382034311.559:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1020 comm="apparmor_parser"
[   36.059631] type=1400 audit(1382034311.559:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1020 comm="apparmor_parser"
[   36.062871] type=1400 audit(1382034311.559:18): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1023 comm="apparmor_parser"
[   36.063337] type=1400 audit(1382034311.559:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1023 comm="apparmor_parser"
[   36.063606] type=1400 audit(1382034311.559:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1023 comm="apparmor_parser"
[   36.241541] type=1400 audit(1382034311.739:21): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1022 comm="apparmor_parser"
[   36.241858] type=1400 audit(1382034311.739:22): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1022 comm="apparmor_parser"
[   37.855623] init: gdm main process (1170) killed by TERM signal
[   57.394502] init: plymouth-stop pre-start process (1768) terminated with status 1
[   61.400107] wlan0: authenticate with 00:05:ca:ba:98:18
[   61.431154] wlan0: send auth to 00:05:ca:ba:98:18 (try 1/3)
[   61.432405] wlan0: authenticated
[   61.436020] wlan0: associate with 00:05:ca:ba:98:18 (try 1/3)
[   61.443211] wlan0: RX AssocResp from 00:05:ca:ba:98:18 (capab=0xc31 status=0 aid=1)
[   61.469679] wlan0: associated
[   61.469707] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   94.212833] wlan0: deauthenticated from 00:05:ca:ba:98:18 (Reason: 2)
[   94.258294] cfg80211: Calling CRDA to update world regulatory domain
[   94.262580] cfg80211: World regulatory domain updated:
[   94.262584] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   94.262586] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   94.262588] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   94.262590] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   94.262592] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   94.262594] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   96.550900] wlan0: authenticate with 00:05:ca:ba:98:18
[   96.574514] wlan0: send auth to 00:05:ca:ba:98:18 (try 1/3)
[   96.575715] wlan0: authenticated
[   96.576097] wlan0: associate with 00:05:ca:ba:98:18 (try 1/3)
[   96.587635] wlan0: RX AssocResp from 00:05:ca:ba:98:18 (capab=0xc31 status=0 aid=1)
[   96.612258] wlan0: associated
[  724.872601] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)

```

best regards

Rui Madaleno

---

### Post by Petro Dawg on 2013-10-17
> ```
[  724.872601] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
```

Are you trying to run 64bit Ubuntu with a 32bit virtual box?  I expect the warning message above might be a clue to whatever the issue is.

Also looks like you have some connectivity issues...

> ```
 [   94.212833] wlan0: deauthenticated from 00:05:ca:ba:98:18 (Reason: 2)
```

---

### Post by Rui_Madaleno on 2013-10-17
Hi Petro,

thank you for your response. I'd like to investigate further the wlan deauthenticated issue.

can you point me some directions ?

best regards

Rui Madaleno

---

