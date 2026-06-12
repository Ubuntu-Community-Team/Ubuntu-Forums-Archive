---
title: "Ubuntu 12.10 freezes briefly when launching application"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by HatoExB on 2013-01-09
Hi,

Whenever I launch a program (or something starts automatically) or unlock my screen, my laptop lags for about 1-2 secs.  It's not too much of a big deal, but it can be annoying especially when watching a video or looking at a website.  When I listen to the hard disk it seems to sleep and wake itself frequently.

My computer: Dell Studio 1535, 3gb of ram, Intel® Core™2 Duo CPU T5800 @ 2.00GHz × 2 75 Gb filesystem size, Ubuntu 12.10 32 bit. 

Any suggestion would be appreciated .  Thanks in advanced.

---

### Post by leviteo on 2013-01-09
Hey,

Please get a kernel log and send it here. Let us see if there is some clue on that.

To get kernel log, after the screen freeze, go to terminal and:

dmesg > freeze.txt

:)
BR

---

### Post by HatoExB on 2013-01-10
Information is cut off when I run dmesg freeze.txt in the terminal.  Is there a way to find the file by nautilus?

---

### Post by leviteo on 2013-01-11
You must redirect the output of dmesg to a file.

Example: 
levi@levinTu:/home/levi$ dmesg > freeze.txt

---

### Post by HatoExB on 2013-01-24
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.7.2-030702-generic (root@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201301111424 SMP Fri Jan 11 19:34:48 UTC 2013
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
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf65c7ff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf65c800-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed1bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feda0000-0x00000000feda5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Dell Inc. Studio 1535                     /0H279K, BIOS A06 12/04/2008
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbf65c max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   3 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3064MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3063MB, range: 1MB, type UC
[    0.000000] total RAM covered: 3063M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 3, base: 3064MB, range: 8MB, type UC
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x3651a000-0x37284fff]
[    0.000000] ACPI: RSDP 000fbaf0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT bf65e200 00064 (v01 DELL    M09     27D80C04 ASL  00000061)
[    0.000000] ACPI: FACP bf65e09c 000F4 (v04 DELL    M09     27D80C04 ASL  00000061)
[    0.000000] ACPI: DSDT bf65e800 0521C (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS bf66d000 00040
[    0.000000] ACPI: HPET bf65e300 00038 (v01 DELL    M09     00000001 ASL  00000061)
[    0.000000] ACPI: APIC bf65e400 00068 (v01 DELL    M09     27D80C04 ASL  00000047)
[    0.000000] ACPI: MCFG bf65e3c0 0003E (v16 DELL    M09     27D80C04 ASL  00000061)
[    0.000000] ACPI: SLIC bf65e49c 00176 (v01 DELL    M09     27D80C04 ASL  00000061)
[    0.000000] ACPI: OSFR bf65da00 00086 (v01 DELL    M09     27D80C04 ASL  00000061)
[    0.000000] ACPI: BOOT bf65dfc0 00028 (v01 DELL    M09     27D80C04 ASL  00000061)
[    0.000000] ACPI: SSDT bf65ca3c 004D4 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2170MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xbf65bfff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbf65bfff]
[    0.000000] On node 0 totalpages: 783851
[    0.000000] free_area_init_node: node 0, pgdat c18fa980, node_mem_map f4d2a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4341 pages used for memmap
[    0.000000]   HighMem zone: 551273 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] e820: [mem 0xc0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34880 r0 d22464 u57344
[    0.000000] pcpu-alloc: s34880 r0 d22464 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777726
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.2-030702-generic root=UUID=a722021b-12af-43ce-b4dd-830892866ee7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6271584 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bf65c)
[    0.000000] Memory: 3079032k/3135856k available (6210k kernel code, 56372k reserved, 3041k data, 784k init, 2222456k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1909000 - 0xc19cd000   ( 784 kB)
[    0.000000]       .data : 0xc16108cf - 0xc1908dc0   (3041 kB)
[    0.000000]       .text : 0xc1000000 - 0xc16108cf   (6210 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4808000 soft=f480a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1995.168 MHz processor
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.33 BogoMIPS (lpj=7980672)
[    0.004005] pid_max: default: 32768 minimum: 301
[    0.004036] Security Framework initialized
[    0.004044] AppArmor: AppArmor initialized
[    0.004046] Yama: becoming mindful.
[    0.004100] Mount-cache hash table entries: 512
[    0.004354] Initializing cgroup subsys cpuacct
[    0.004357] Initializing cgroup subsys memory
[    0.004365] Initializing cgroup subsys devices
[    0.004367] Initializing cgroup subsys freezer
[    0.004369] Initializing cgroup subsys blkio
[    0.004371] Initializing cgroup subsys perf_event
[    0.004375] Initializing cgroup subsys hugetlb
[    0.004406] CPU: Physical Processor ID: 0
[    0.004408] CPU: Processor Core ID: 0
[    0.004411] mce: CPU supports 6 MCE banks
[    0.004419] CPU0: Thermal monitoring enabled (TM2)
[    0.004422] process: using mwait in idle threads
[    0.004431] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004431] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004431] tlb_flushall_shift: -1
[    0.004704] Freeing SMP alternatives: 24k freed
[    0.008269] ACPI: Core revision 20120913
[    0.012011] ftrace: allocating 27960 entries in 55 pages
[    0.024074] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024549] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066346] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz (fam: 06, model: 0f, stepping: 0d)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] perf_event_intel: PEBS disabled due to CPU errata
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.068000] CPU 1 irqstacks, hard=f48d2000 soft=f48d4000
[    0.068000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.078421] Brought up 2 CPUs
[    0.078426] smpboot: Total of 2 processors activated (7980.67 BogoMIPS)
[    0.078531] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080054] devtmpfs: initialized
[    0.080249] EVM: security.selinux
[    0.080251] EVM: security.SMACK64
[    0.080253] EVM: security.capability
[    0.081285] regulator-dummy: no parameters
[    0.081352] NET: Registered protocol family 16
[    0.081530] EISA bus registered
[    0.081637] ACPI: bus type pci registered
[    0.081704] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.081708] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.081710] PCI: Using MMCONFIG for extended config space
[    0.081712] PCI: Using configuration type 1 for base access
[    0.081725] dmi type 0xB1 record - unknown flag
[    0.081725] bio: create slab <bio-0> at 0
[    0.081725] ACPI: Added _OSI(Module Device)
[    0.081725] ACPI: Added _OSI(Processor Device)
[    0.081725] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.081725] ACPI: Added _OSI(Processor Aggregator Device)
[    0.085002] ACPI: EC: Look up EC in DSDT
[    0.100786] ACPI: SSDT bf66d080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.101123] ACPI: Dynamic OEM Table Load:
[    0.101126] ACPI: SSDT   (null) 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.101443] ACPI: SSDT bf65d57a 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.101798] ACPI: Dynamic OEM Table Load:
[    0.101801] ACPI: SSDT   (null) 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.101957] ACPI: SSDT bf65cf10 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.102291] ACPI: Dynamic OEM Table Load:
[    0.102294] ACPI: SSDT   (null) 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.102565] ACPI: SSDT bf65d77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.102913] ACPI: Dynamic OEM Table Load:
[    0.102917] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.103037] ACPI: SSDT bf65d4f5 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.103373] ACPI: Dynamic OEM Table Load:
[    0.103377] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.103602] ACPI: Interpreter enabled
[    0.103612] ACPI: (supports S0 S3 S4 S5)
[    0.103631] ACPI: Using IOAPIC for interrupt routing
[    0.164021] ACPI: No dock devices found.
[    0.164021] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.179837] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.201178] pci_root PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.201225] PCI host bridge to bus 0000:00
[    0.201229] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.201232] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.201235] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.201238] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.201241] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.201244] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xf7ffffff]
[    0.201247] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfebfffff]
[    0.201250] pci_bus 0000:00: root bus resource [mem 0xfec10000-0xfecfffff]
[    0.201253] pci_bus 0000:00: root bus resource [mem 0xfed1c000-0xfed1ffff]
[    0.201255] pci_bus 0000:00: root bus resource [mem 0xfed90000-0xfed9ffff]
[    0.201258] pci_bus 0000:00: root bus resource [mem 0xfeda7000-0xfedfffff]
[    0.201261] pci_bus 0000:00: root bus resource [mem 0xfee10000-0xff9fffff]
[    0.201264] pci_bus 0000:00: root bus resource [mem 0xffc00000-0xffdfffff]
[    0.201277] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.201336] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.201353] pci 0000:00:02.0: reg 10: [mem 0xf6e00000-0xf6efffff 64bit]
[    0.201363] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.201371] pci 0000:00:02.0: reg 20: [io  0xeff8-0xefff]
[    0.201418] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.201432] pci 0000:00:02.1: reg 10: [mem 0xf6f00000-0xf6ffffff 64bit]
[    0.201535] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.201597] pci 0000:00:1a.0: reg 20: [io  0x6f60-0x6f7f]
[    0.201645] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.201707] pci 0000:00:1a.1: reg 20: [io  0x6f80-0x6f9f]
[    0.201771] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.201799] pci 0000:00:1a.7: reg 10: [mem 0xfed1c400-0xfed1c7ff]
[    0.201917] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.201956] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.201981] pci 0000:00:1b.0: reg 10: [mem 0xf6dfc000-0xf6dfffff 64bit]
[    0.202097] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.202133] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.202254] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.202294] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.202416] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.202457] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.202577] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.202618] pci 0000:00:1c.5: [8086:2849] type 01 class 0x060400
[    0.202740] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.202776] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.202837] pci 0000:00:1d.0: reg 20: [io  0x6f00-0x6f1f]
[    0.202885] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.202947] pci 0000:00:1d.1: reg 20: [io  0x6f20-0x6f3f]
[    0.202995] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.203057] pci 0000:00:1d.2: reg 20: [io  0x6f40-0x6f5f]
[    0.203121] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.203148] pci 0000:00:1d.7: reg 10: [mem 0xfed1c000-0xfed1c3ff]
[    0.203266] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.203296] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.203405] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.203528] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.203535] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.203540] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.203547] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.203552] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0300 (mask 003f)
[    0.203627] pci 0000:00:1f.2: [8086:2829] type 00 class 0x010601
[    0.203656] pci 0000:00:1f.2: reg 10: [io  0x6e70-0x6e77]
[    0.203670] pci 0000:00:1f.2: reg 14: [io  0x6e78-0x6e7b]
[    0.203684] pci 0000:00:1f.2: reg 18: [io  0x6e80-0x6e87]
[    0.203697] pci 0000:00:1f.2: reg 1c: [io  0x6e88-0x6e8b]
[    0.203711] pci 0000:00:1f.2: reg 20: [io  0x6ea0-0x6ebf]
[    0.203725] pci 0000:00:1f.2: reg 24: [mem 0xf6dfb800-0xf6dfbfff]
[    0.203798] pci 0000:00:1f.2: PME# supported from D3hot
[    0.203826] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.203845] pci 0000:00:1f.3: reg 10: [mem 0xf6dfb700-0xf6dfb7ff]
[    0.203891] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.204005] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.204190] pci 0000:0c:00.0: [14e4:4315] type 00 class 0x028000
[    0.204263] pci 0000:0c:00.0: reg 10: [mem 0xf6cfc000-0xf6cfffff 64bit]
[    0.204659] pci 0000:0c:00.0: supports D1 D2
[    0.204662] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.204858] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.204867] pci 0000:00:1c.1:   bridge window [mem 0xf6c00000-0xf6cfffff]
[    0.204942] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.204947] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.204953] pci 0000:00:1c.3:   bridge window [mem 0xf6a00000-0xf6bfffff]
[    0.204963] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.205086] pci 0000:09:00.0: [14e4:1698] type 00 class 0x020000
[    0.205137] pci 0000:09:00.0: reg 10: [mem 0xf69f0000-0xf69fffff 64bit]
[    0.205436] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.212029] pci 0000:00:1c.5: PCI bridge to [bus 09]
[    0.212039] pci 0000:00:1c.5:   bridge window [mem 0xf6900000-0xf69fffff]
[    0.212098] pci 0000:03:01.0: [1180:0832] type 00 class 0x0c0010
[    0.212117] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.212119] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
[    0.212138] pci 0000:03:01.0: reg 10: [mem 0xf68ff800-0xf68fffff]
[    0.212248] pci 0000:03:01.0: supports D1 D2
[    0.212251] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212279] pci 0000:03:01.1: [1180:0822] type 00 class 0x080501
[    0.212304] pci 0000:03:01.1: reg 10: [mem 0xf68ff400-0xf68ff4ff]
[    0.212415] pci 0000:03:01.1: supports D1 D2
[    0.212418] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212445] pci 0000:03:01.2: [1180:0592] type 00 class 0x088000
[    0.212470] pci 0000:03:01.2: reg 10: [mem 0xf68ff600-0xf68ff6ff]
[    0.212581] pci 0000:03:01.2: supports D1 D2
[    0.212584] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212612] pci 0000:03:01.3: [1180:0852] type 00 class 0x088000
[    0.212637] pci 0000:03:01.3: reg 10: [mem 0xf68ff700-0xf68ff7ff]
[    0.212749] pci 0000:03:01.3: supports D1 D2
[    0.212752] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212832] pci 0000:00:1e.0: PCI bridge to [bus 03] (subtractive decode)
[    0.212841] pci 0000:00:1e.0:   bridge window [mem 0xf6800000-0xf68fffff]
[    0.212850] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.212853] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.212856] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.212859] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.212862] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xf7ffffff] (subtractive decode)
[    0.212865] pci 0000:00:1e.0:   bridge window [mem 0xfc000000-0xfebfffff] (subtractive decode)
[    0.212868] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.212871] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.212874] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.212877] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.212880] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.212883] pci 0000:00:1e.0:   bridge window [mem 0xffc00000-0xffdfffff] (subtractive decode)
[    0.212920] pci_bus 0000:00: on NUMA node 0
[    0.212924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.213242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.213365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.213425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.213487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.213547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.213604]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.213606]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.224419] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    0.224501] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.224580] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *3
[    0.224646] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.
[    0.224728] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.224812] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.224894] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.224964] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.225072] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.225072] vgaarb: loaded
[    0.225072] vgaarb: bridge control possible 0000:00:02.0
[    0.225072] SCSI subsystem initialized
[    0.225072] ACPI: bus type scsi registered
[    0.225072] libata version 3.00 loaded.
[    0.225072] ACPI: bus type usb registered
[    0.225072] usbcore: registered new interface driver usbfs
[    0.225072] usbcore: registered new interface driver hub
[    0.225072] usbcore: registered new device driver usb
[    0.228034] PCI: Using ACPI for IRQ routing
[    0.230763] PCI: pci_cache_line_size set to 64 bytes
[    0.230954] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.230957] e820: reserve RAM buffer [mem 0xbf65c800-0xbfffffff]
[    0.231070] NetLabel: Initializing
[    0.231072] NetLabel:  domain hash size = 128
[    0.231074] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.231087] NetLabel:  unlabeled traffic allowed by default
[    0.231102] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.231102] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.231102] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.233014] Switching to clocksource hpet
[    0.241074] AppArmor: AppArmor Filesystem Enabled
[    0.241111] pnp: PnP ACPI init
[    0.241130] ACPI: bus type pnp registered
[    0.251467] pnp 00:00: [bus 00-ff]
[    0.251472] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.251475] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.251478] pnp 00:00: [io  0x0d00-0xffff window]
[    0.251481] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.251484] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.251488] pnp 00:00: [mem 0xc0000000-0xf7ffffff window]
[    0.251491] pnp 00:00: [mem 0xfc000000-0xfebfffff window]
[    0.251493] pnp 00:00: [mem 0xfec10000-0xfecfffff window]
[    0.251496] pnp 00:00: [mem 0xfed1c000-0xfed1ffff window]
[    0.251499] pnp 00:00: [mem 0xfed90000-0xfed9ffff window]
[    0.251502] pnp 00:00: [mem 0xfeda7000-0xfedfffff window]
[    0.251505] pnp 00:00: [mem 0xfee10000-0xff9fffff window]
[    0.251508] pnp 00:00: [mem 0xffc00000-0xffdfffff window]
[    0.251564] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.251599] pnp 00:01: [irq 12]
[    0.251623] pnp 00:01: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.251642] pnp 00:02: [io  0x0300-0x0307]
[    0.251650] pnp 00:02: [irq 10]
[    0.251676] pnp 00:02: Plug and Play ACPI device, IDs ITE8708 (active)
[    0.251695] pnp 00:03: [io  0x0060]
[    0.251698] pnp 00:03: [io  0x0064]
[    0.251700] pnp 00:03: [io  0x0062]
[    0.251703] pnp 00:03: [io  0x0066]
[    0.251710] pnp 00:03: [irq 1]
[    0.251732] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.251751] pnp 00:04: [io  0x0070-0x0071]
[    0.251757] pnp 00:04: [irq 8]
[    0.251760] pnp 00:04: [io  0x0072-0x0077]
[    0.251783] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.251804] pnp 00:05: [io  0x0061]
[    0.251807] pnp 00:05: [io  0x0063]
[    0.251809] pnp 00:05: [io  0x0065]
[    0.251812] pnp 00:05: [io  0x0067]
[    0.251838] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.251855] pnp 00:06: [io  0x0c80-0x0cff]
[    0.251910] system 00:06: [io  0x0c80-0x0cff] could not be reserved
[    0.251915] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.251936] pnp 00:07: [dma 4]
[    0.251939] pnp 00:07: [io  0x0000-0x000f]
[    0.251942] pnp 00:07: [io  0x0080-0x0085]
[    0.251945] pnp 00:07: [io  0x0087-0x008f]
[    0.251948] pnp 00:07: [io  0x00c0-0x00df]
[    0.251950] pnp 00:07: [io  0x0010-0x001f]
[    0.251953] pnp 00:07: [io  0x0090-0x0091]
[    0.251956] pnp 00:07: [io  0x0093-0x009f]
[    0.251980] pnp 00:07: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.251997] pnp 00:08: [io  0x00f0-0x00ff]
[    0.252016] pnp 00:08: [irq 13]
[    0.252040] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.252087] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.252130] system 00:09: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.252135] system 00:09: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.252284] pnp 00:0a: [io  0x0900-0x097f]
[    0.252287] pnp 00:0a: [io  0x0092]
[    0.252290] pnp 00:0a: [io  0x00b2-0x00b3]
[    0.252293] pnp 00:0a: [io  0x0020-0x0021]
[    0.252295] pnp 00:0a: [io  0x00a0-0x00a1]
[    0.252298] pnp 00:0a: [irq 0 disabled]
[    0.252301] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.252304] pnp 00:0a: [io  0x1000-0x1005]
[    0.252306] pnp 00:0a: [io  0x1008-0x100f]
[    0.252322] pnp 00:0a: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.252325] pnp 00:0a: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.252366] system 00:0a: [io  0x0900-0x097f] has been reserved
[    0.252370] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.252374] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.252394] pnp 00:0b: [io  0xf400-0xf4fe]
[    0.252396] pnp 00:0b: [io  0x0086]
[    0.252399] pnp 00:0b: [io  0x1006-0x1007]
[    0.252402] pnp 00:0b: [io  0x100a-0x1059]
[    0.252405] pnp 00:0b: [io  0x1060-0x107f]
[    0.252407] pnp 00:0b: [io  0x1080-0x10bf]
[    0.252410] pnp 00:0b: [io  0x10c0-0x10df]
[    0.252412] pnp 00:0b: [io  0x1010-0x102f]
[    0.252415] pnp 00:0b: [io  0x0809]
[    0.252430] pnp 00:0b: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.252433] pnp 00:0b: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.252437] pnp 00:0b: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.252440] pnp 00:0b: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.252486] system 00:0b: [io  0xf400-0xf4fe] has been reserved
[    0.252490] system 00:0b: [io  0x1080-0x10bf] has been reserved
[    0.252494] system 00:0b: [io  0x10c0-0x10df] has been reserved
[    0.252497] system 00:0b: [io  0x0809] has been reserved
[    0.252501] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264210] pnp 00:0c: [mem 0x00000000-0x0009efff]
[    0.264213] pnp 00:0c: [mem 0x0009f000-0x0009ffff]
[    0.264216] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.264219] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.264222] pnp 00:0c: [mem 0x00100000-0xbf65c7ff]
[    0.264225] pnp 00:0c: [mem 0xbf65c800-0xbf6fffff]
[    0.264228] pnp 00:0c: [mem 0xbf700000-0xbf7fffff]
[    0.264231] pnp 00:0c: [mem 0xffe00000-0xffffffff]
[    0.264233] pnp 00:0c: [mem 0xffa00000-0xffbfffff]
[    0.264236] pnp 00:0c: [mem 0xfec00000-0xfec0ffff]
[    0.264239] pnp 00:0c: [mem 0xfee00000-0xfee0ffff]
[    0.264242] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
[    0.264244] pnp 00:0c: [mem 0xfeda0000-0xfeda3fff]
[    0.264247] pnp 00:0c: [mem 0xfeda4000-0xfeda4fff]
[    0.264250] pnp 00:0c: [mem 0xfeda5000-0xfeda5fff]
[    0.264253] pnp 00:0c: [mem 0xfeda6000-0xfeda6fff]
[    0.264256] pnp 00:0c: [mem 0xfed18000-0xfed1bfff]
[    0.264258] pnp 00:0c: [mem 0xf8000000-0xfbffffff]
[    0.264327] system 00:0c: [mem 0x00000000-0x0009efff] could not be reserved
[    0.264331] system 00:0c: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.264335] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.264338] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.264341] system 00:0c: [mem 0x00100000-0xbf65c7ff] could not be reserved
[    0.264345] system 00:0c: [mem 0xbf65c800-0xbf6fffff] has been reserved
[    0.264348] system 00:0c: [mem 0xbf700000-0xbf7fffff] has been reserved
[    0.264352] system 00:0c: [mem 0xffe00000-0xffffffff] has been reserved
[    0.264355] system 00:0c: [mem 0xffa00000-0xffbfffff] has been reserved
[    0.264358] system 00:0c: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.264362] system 00:0c: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.264365] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.264369] system 00:0c: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.264372] system 00:0c: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.264376] system 00:0c: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.264379] system 00:0c: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.264382] system 00:0c: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.264386] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.264390] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264457] pnp: PnP ACPI: found 13 devices
[    0.264459] ACPI: ACPI bus type pnp unregistered
[    0.264464] PnPBIOS: Disabled by ACPI PNP
[    0.301618] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b] add_size 1000
[    0.301625] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b] add_size 200000
[    0.301629] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 0b] add_size 200000
[    0.301642] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 0c] add_size 1000
[    0.301646] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0c] add_size 200000
[    0.301809] pci 0000:00:1c.5: bridge window [io  0x1000-0x0fff] to [bus 09] add_size 1000
[    0.301813] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 09] add_size 200000
[    0.301833] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.301836] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.301840] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.301843] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.301846] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.301849] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.301990] pci 0000:00:1c.5: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.301996] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.302001] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.302005] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.302010] pci 0000:00:1c.5: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.302014] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.302018] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.302022] pci 0000:00:1c.5: BAR 13: assigned [io  0x4000-0x4fff]
[    0.302026] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.303974] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.303982] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.303988] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.303999] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.304018] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.304025] pci 0000:00:1c.1:   bridge window [mem 0xf6c00000-0xf6cfffff]
[    0.304031] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.304040] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.304045] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.304052] pci 0000:00:1c.3:   bridge window [mem 0xf6a00000-0xf6bfffff]
[    0.304058] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.304206] pci 0000:00:1c.5: PCI bridge to [bus 09]
[    0.304211] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.304218] pci 0000:00:1c.5:   bridge window [mem 0xf6900000-0xf69fffff]
[    0.304225] pci 0000:00:1c.5:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.304235] pci 0000:00:1e.0: PCI bridge to [bus 03]
[    0.304243] pci 0000:00:1e.0:   bridge window [mem 0xf6800000-0xf68fffff]
[    0.304440] pci 0000:00:1e.0: setting latency timer to 64
[    0.304445] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.304449] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.304452] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.304455] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.304458] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xf7ffffff]
[    0.304461] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.304464] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.304467] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.304470] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.304472] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.304475] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.304478] pci_bus 0000:00: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.304482] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.304485] pci_bus 0000:0b: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.304488] pci_bus 0000:0b: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.304491] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.304494] pci_bus 0000:0c: resource 1 [mem 0xf6c00000-0xf6cfffff]
[    0.304497] pci_bus 0000:0c: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.304500] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.304503] pci_bus 0000:0d: resource 1 [mem 0xf6a00000-0xf6bfffff]
[    0.304506] pci_bus 0000:0d: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.304509] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.304512] pci_bus 0000:09: resource 1 [mem 0xf6900000-0xf69fffff]
[    0.304515] pci_bus 0000:09: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.304519] pci_bus 0000:03: resource 1 [mem 0xf6800000-0xf68fffff]
[    0.308010] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.309339] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.309342] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.309345] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.309348] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xf7ffffff]
[    0.309351] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.309354] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.309356] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.309359] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.309362] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.309365] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.309368] pci_bus 0000:03: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.309414] NET: Registered protocol family 2
[    0.309598] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.310080] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.310280] TCP: Hash tables configured (established 131072 bind 65536)
[    0.310309] TCP: reno registered
[    0.310312] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.310323] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.310388] NET: Registered protocol family 1
[    0.310405] pci 0000:00:02.0: Boot video device
[    0.310711] PCI: CLS 64 bytes, default 64
[    0.310777] Trying to unpack rootfs image as initramfs...
[    0.647747] Freeing initrd memory: 13740k freed
[    0.654705] Simple Boot Flag at 0x79 set to 0x1
[    0.655069] Initialise module verification
[    0.655124] audit: initializing netlink socket (disabled)
[    0.655142] type=2000 audit(1358980175.652:1): initialized
[    0.681526] bounce pool size: 64 pages
[    0.681540] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.683614] VFS: Disk quotas dquot_6.5.2
[    0.683672] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.684336] fuse init (API version 7.20)
[    0.684445] msgmni has been set to 1699
[    0.684915] Key type asymmetric registered
[    0.684918] Asymmetric key parser 'x509' registered
[    0.684963] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.684996] io scheduler noop registered
[    0.685000] io scheduler deadline registered (default)
[    0.685008] io scheduler cfq registered
[    0.685208] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.685355] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.685497] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.685636] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.685745] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.685769] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.685844] intel_idle: does not run on family 6 model 15
[    0.685958] ACPI: AC Adapter [AC] (off-line)
[    0.686038] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.687468] ACPI: Lid Switch [LID]
[    0.687518] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.687523] ACPI: Power Button [PBTN]
[    0.687566] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.687570] ACPI: Sleep Button [SBTN]
[    0.687649] ACPI: Requesting acpi_cpufreq
[    0.687880] Monitor-Mwait will be used to enter C-1 state
[    0.687886] Monitor-Mwait will be used to enter C-2 state
[    0.687891] Monitor-Mwait will be used to enter C-3 state
[    0.687894] tsc: Marking TSC unstable due to TSC halts in idle
[    0.687906] ACPI: acpi_idle registered with cpuidle
[    0.703379] thermal LNXTHERM:00: registered as thermal_zone0
[    0.703382] ACPI: Thermal Zone [THM] (34 C)
[    0.703425] GHES: HEST is not enabled!
[    0.703438] isapnp: Scanning for PnP cards...
[    0.726064] ACPI: Battery Slot [BAT0] (battery present)
[    1.062270] isapnp: No Plug & Play device found
[    1.062372] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.063984] Linux agpgart interface v0.103
[    1.064116] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    1.064163] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.064632] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.064778] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.066459] brd: module loaded
[    1.067321] loop: module loaded
[    1.067465] ahci 0000:00:1f.2: version 3.0
[    1.067533] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.067615] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.067620] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.067626] ahci 0000:00:1f.2: setting latency timer to 64
[    1.080335] scsi0 : ahci
[    1.080433] scsi1 : ahci
[    1.080513] scsi2 : ahci
[    1.080563] ata1: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb900 irq 44
[    1.080566] ata2: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfb980 irq 44
[    1.080570] ata3: SATA max UDMA/133 abar m2048@0xf6dfb800 port 0xf6dfba00 irq 44
[    1.080994] libphy: Fixed MDIO Bus: probed
[    1.081076] tun: Universal TUN/TAP device driver, 1.6
[    1.081078] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.081140] PPP generic driver version 2.4.2
[    1.081202] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.081239] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.081244] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.081252] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.085160] ehci_hcd 0000:00:1a.7: debug port 1
[    1.085171] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.085189] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.096021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.096045] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.096048] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.096051] usb usb1: Product: EHCI Host Controller
[    1.096054] usb usb1: Manufacturer: Linux 3.7.2-030702-generic ehci_hcd
[    1.096057] usb usb1: SerialNumber: 0000:00:1a.7
[    1.096201] hub 1-0:1.0: USB hub found
[    1.096207] hub 1-0:1.0: 4 ports detected
[    1.096508] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.096513] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.096519] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.100420] ehci_hcd 0000:00:1d.7: debug port 1
[    1.100429] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.100447] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.112022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.112040] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.112043] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.112046] usb usb2: Product: EHCI Host Controller
[    1.112049] usb usb2: Manufacturer: Linux 3.7.2-030702-generic ehci_hcd
[    1.112051] usb usb2: SerialNumber: 0000:00:1d.7
[    1.112178] hub 2-0:1.0: USB hub found
[    1.112183] hub 2-0:1.0: 6 ports detected
[    1.112706] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.112728] uhci_hcd: USB Universal Host Controller Interface driver
[    1.112751] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.112756] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.112762] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.112792] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    1.112831] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.112834] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.112837] usb usb3: Product: UHCI Host Controller
[    1.112840] usb usb3: Manufacturer: Linux 3.7.2-030702-generic uhci_hcd
[    1.112843] usb usb3: SerialNumber: 0000:00:1a.0
[    1.112973] hub 3-0:1.0: USB hub found
[    1.112978] hub 3-0:1.0: 2 ports detected
[    1.113119] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.113124] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.113130] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.113170] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    1.113206] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.113209] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.113212] usb usb4: Product: UHCI Host Controller
[    1.113215] usb usb4: Manufacturer: Linux 3.7.2-030702-generic uhci_hcd
[    1.113218] usb usb4: SerialNumber: 0000:00:1a.1
[    1.113344] hub 4-0:1.0: USB hub found
[    1.113349] hub 4-0:1.0: 2 ports detected
[    1.113486] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.113491] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.113497] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.113526] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    1.113562] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.113565] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.113568] usb usb5: Product: UHCI Host Controller
[    1.113571] usb usb5: Manufacturer: Linux 3.7.2-030702-generic uhci_hcd
[    1.113573] usb usb5: SerialNumber: 0000:00:1d.0
[    1.113696] hub 5-0:1.0: USB hub found
[    1.113700] hub 5-0:1.0: 2 ports detected
[    1.113839] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.113844] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.113850] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.113879] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    1.113915] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.113918] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.113921] usb usb6: Product: UHCI Host Controller
[    1.113924] usb usb6: Manufacturer: Linux 3.7.2-030702-generic uhci_hcd
[    1.113926] usb usb6: SerialNumber: 0000:00:1d.1
[    1.114044] hub 6-0:1.0: USB hub found
[    1.114048] hub 6-0:1.0: 2 ports detected
[    1.114185] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.114189] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.114195] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.114224] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.114260] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.114263] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.114266] usb usb7: Product: UHCI Host Controller
[    1.114269] usb usb7: Manufacturer: Linux 3.7.2-030702-generic uhci_hcd
[    1.114272] usb usb7: SerialNumber: 0000:00:1d.2
[    1.114389] hub 7-0:1.0: USB hub found
[    1.114393] hub 7-0:1.0: 2 ports detected
[    1.114611] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.121675] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.121682] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.121814] mousedev: PS/2 mouse device common for all mice
[    1.122011] rtc_cmos 00:04: RTC can wake from S4
[    1.122174] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.122212] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.122300] device-mapper: uevent: version 1.0.3
[    1.122385] device-mapper: ioctl: 4.23.0-ioctl (2012-07-25) initialised: dm-devel@redhat.com
[    1.122425] EISA: Probing bus 0 at eisa.0
[    1.122428] EISA: Cannot allocate resource for mainboard
[    1.122430] Cannot allocate resource for EISA slot 1
[    1.122432] Cannot allocate resource for EISA slot 2
[    1.122434] Cannot allocate resource for EISA slot 3
[    1.122436] Cannot allocate resource for EISA slot 4
[    1.122438] Cannot allocate resource for EISA slot 5
[    1.122440] Cannot allocate resource for EISA slot 6
[    1.122442] Cannot allocate resource for EISA slot 7
[    1.122444] Cannot allocate resource for EISA slot 8
[    1.122446] EISA: Detected 0 cards.
[    1.122457] cpufreq-nforce2: No nForce2 chipset.
[    1.122508] cpuidle: using governor ladder
[    1.122588] cpuidle: using governor menu
[    1.122593] ledtrig-cpu: registered to indicate activity on CPUs
[    1.122595] EFI Variables Facility v0.08 2004-May-17
[    1.122855] ashmem: initialized
[    1.123019] TCP: cubic registered
[    1.123147] NET: Registered protocol family 10
[    1.123368] NET: Registered protocol family 17
[    1.123382] Key type dns_resolver registered
[    1.123616] Using IPI No-Shortcut mode
[    1.123785] Loading module verification certificates
[    1.124532] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.128439] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: fa6ffa91b0374744aff7e35a470868639be353b9'
[    1.128454] registered taskstats version 1
[    1.131409] Key type trusted registered
[    1.134498] Key type encrypted registered
[    1.137607] rtc_cmos 00:04: setting system clock to 2013-01-23 22:29:37 UTC (1358980177)
[    1.138546] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.138549] EDD information not available.
[    1.400217] ata3: SATA link down (SStatus 0 SControl 300)
[    1.408213] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.421426] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, D300, max UDMA/100
[    1.421433] ata2.00: applying bridge limits
[    1.424082] usb 2-5: new high-speed USB device number 2 using ehci_hcd
[    1.435304] ata2.00: configured for UDMA/100
[    1.628064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.635272] usb 2-5: New USB device found, idVendor=0c45, idProduct=63fa
[    1.635278] usb 2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.635283] usb 2-5: Product: Laptop_Integrated_Webcam_2M
[    1.635288] usb 2-5: Manufacturer: SONiX Technology Inc.
[    1.635293] usb 2-5: SerialNumber: CN0TX6137248789RCNCG
[    1.657060] ata1.00: ATA-8: WDC WD2500BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.657066] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    1.657270] ata1.00: failed to get Identify Device Data, Emask 0x1
[    1.659423] ata1.00: failed to get Identify Device Data, Emask 0x1
[    1.659430] ata1.00: configured for UDMA/133
[    1.659646] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.659829] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.659847] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.659886] sd 0:0:0:0: [sda] Write Protect is off
[    1.659890] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.659915] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.662432] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D300 PQ: 0 ANSI: 5
[    1.666507] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.666512] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.666694] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.666777] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.706255]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.707033] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.707129] Freeing unused kernel memory: 784k freed
[    1.707443] Write protecting the kernel text: 6212k
[    1.707538] Write protecting the kernel read-only data: 2516k
[    1.707539] NX-protecting the kernel data: 4028k
[    1.736397] udevd[116]: starting version 175
[    1.850756] tg3.c:v3.125 (September 26, 2012)
[    1.912961] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:dd:e9:ca
[    1.912968] tg3 0000:09:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.912972] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.912975] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.919664] sdhci: Secure Digital Host Controller Interface driver
[    1.919668] sdhci: Copyright(c) Pierre Ossman
[    1.984152] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.984431] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.985484] mmc0: no vqmmc regulator found
[    1.985486] mmc0: no vmmc regulator found
[    1.986534] Registered led device: mmc0::
[    2.016056] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.245300] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.245305] EXT4-fs (sda5): write access will be enabled during recovery
[    2.484221] firewire_core 0000:03:01.0: created device fw0: GUID 314fc0002cff49e1, S400
[    4.373256] EXT4-fs (sda5): recovery complete
[    4.401703] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    6.087204] init: ureadahead main process (300) terminated with status 5
[    7.619732] Adding 3133436k swap on /dev/sda6.  Priority:-1 extents:1 across:3133436k 
[    8.779370] udevd[390]: starting version 175
[    9.316043] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    9.748679] lp: driver loaded but no devices found
[   13.524042] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa3
[   13.712587] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa3
[   13.714743] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   13.968594] lib80211: common routines for IEEE802.11 drivers
[   13.968599] lib80211_crypt: registered algorithm 'NULL'
[   14.230387] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.323574] r592: driver successfully loaded
[   14.361708] wmi: Mapper loaded
[   15.016441] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   15.060823] r852: driver loaded successfully
[   15.075978] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   15.239267] [drm] Initialized drm 1.1.0 20060810
[   15.279490] ite_cir: Auto-detected model: ITE8708 CIR transceiver
[   15.279495] ite_cir: Using model: ITE8708 CIR transceiver
[   15.279498] ite_cir: TX-capable: 1
[   15.279500] ite_cir: Sample period (ns): 8680
[   15.279501] ite_cir: TX carrier frequency (Hz): 38000
[   15.279504] ite_cir: TX duty cycle (%): 33
[   15.279505] ite_cir: RX low carrier frequency (Hz): 0
[   15.279507] ite_cir: RX high carrier frequency (Hz): 0
[   15.331366] Linux video capture interface: v2.00
[   15.431435] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.512038] Registered IR keymap rc-rc6-mce
[   15.512153] input: ITE8708 CIR transceiver as /devices/virtual/rc/rc0/input5
[   15.513382] rc0: ITE8708 CIR transceiver as /devices/virtual/rc/rc0
[   15.514000] ite_cir: driver has been successfully loaded
[   15.558135] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   15.558321] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.626932] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   15.650684] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   15.663409] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.663414] Disabling lock debugging due to kernel taint
[   15.702243] IR NEC protocol handler initialized
[   15.802870] lib80211_crypt: registered algorithm 'TKIP'
[   15.839512] IR RC5(x) protocol handler initialized
[   15.853356] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63fa)
[   15.858297] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input10
[   15.859244] usbcore: registered new interface driver uvcvideo
[   15.859247] USB Video Class driver (1.1.1)
[   15.902397] i915 0000:00:02.0: setting latency timer to 64
[   15.903119] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   15.903131] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.903133] [drm] Driver supports precise vblank timestamp query.
[   15.903215] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.052731] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.112
[   16.142886] [drm] initialized overlay support
[   16.181350] fbcon: inteldrmfb (fb0) is primary device
[   16.346956] IR RC6 protocol handler initialized
[   16.391511] IR JVC protocol handler initialized
[   16.553947] IR Sony protocol handler initialized
[   16.676986] IR SANYO protocol handler initialized
[   16.725157] input: MCE IR Keyboard/Mouse (ite-cir) as /devices/virtual/input/input11
[   16.725252] IR MCE Keyboard/mouse protocol handler initialized
[   16.856092] lirc_dev: IR Remote Control driver registered, major 250 
[   16.909616] rc rc0: lirc_dev: driver ir-lirc-codec (ite-cir) registered at minor = 0
[   16.909618] IR LIRC bridge handler initialized
[   17.059237] Console: switching to colour frame buffer device 160x50
[   17.063757] fb0: inteldrmfb frame buffer device
[   17.063758] drm: registered panic notifier
[   17.068229] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.072703] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input12
[   17.073398] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   17.073917] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.442275] ppdev: user-space parallel port driver
[   17.494477] type=1400 audit(1359008993.854:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=729 comm="apparmor_parser"
[   17.494489] type=1400 audit(1359008993.854:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=730 comm="apparmor_parser"
[   17.494961] type=1400 audit(1359008993.854:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=729 comm="apparmor_parser"
[   17.494972] type=1400 audit(1359008993.854:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=730 comm="apparmor_parser"
[   17.495231] type=1400 audit(1359008993.854:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=729 comm="apparmor_parser"
[   17.495244] type=1400 audit(1359008993.854:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=730 comm="apparmor_parser"
[   17.495876] type=1400 audit(1359008993.854:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=810 comm="apparmor_parser"
[   17.496382] type=1400 audit(1359008993.858:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=810 comm="apparmor_parser"
[   17.496657] type=1400 audit(1359008993.858:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=810 comm="apparmor_parser"
[   18.075852] Bluetooth: Core ver 2.16
[   18.075881] NET: Registered protocol family 31
[   18.075883] Bluetooth: HCI device and connection manager initialized
[   18.076169] Bluetooth: HCI socket layer initialized
[   18.076173] Bluetooth: L2CAP socket layer initialized
[   18.076182] Bluetooth: SCO socket layer initialized
[   18.128330] type=1400 audit(1359008994.490:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1104 comm="apparmor_parser"
[   18.429196] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.429201] Bluetooth: BNEP filters: protocol multicast
[   18.429211] Bluetooth: BNEP socket layer initialized
[   18.431865] Bluetooth: RFCOMM TTY layer initialized
[   18.431877] Bluetooth: RFCOMM socket layer initialized
[   18.431879] Bluetooth: RFCOMM ver 1.11
[   18.855216] init: failsafe main process (1123) killed by TERM signal
[   22.054184] init: smbd main process (1173) killed by HUP signal
[   22.054216] init: smbd main process ended, respawning
[   26.487054] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[   26.581557] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.557949] audit_printk_skb: 3 callbacks suppressed
[   28.557954] type=1400 audit(1359009004.918:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1296 comm="apparmor_parser"
[   28.558354] type=1400 audit(1359009004.918:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1296 comm="apparmor_parser"
[   28.598227] type=1400 audit(1359009004.958:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1298 comm="apparmor_parser"
[   28.598627] type=1400 audit(1359009004.958:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1298 comm="apparmor_parser"
[   28.601930] type=1400 audit(1359009004.962:17): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1299 comm="apparmor_parser"
[   28.602435] type=1400 audit(1359009004.962:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1299 comm="apparmor_parser"
[   28.602712] type=1400 audit(1359009004.962:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1299 comm="apparmor_parser"
[   28.618436] type=1400 audit(1359009004.978:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1297 comm="apparmor_parser"
[   28.618841] type=1400 audit(1359009004.978:21): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1297 comm="apparmor_parser"
[   28.920838] type=1400 audit(1359009005.282:22): apparmor="STATUS" operation="profile_load" name="system_tor" pid=1300 comm="apparmor_parser"
[   31.094897] init: gdm main process (1419) killed by TERM signal
[   49.231397] init: anacron main process (1417) killed by TERM signal
[   59.297999] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   59.396395] init: plymouth-stop pre-start process (2894) terminated with status 1
[  600.061705] init: anacron main process (5943) killed by TERM signal
[  600.879835] PM: Syncing filesystems ... done.
[  601.136627] Freezing user space processes ... (elapsed 0.01 seconds) done.
[  601.152402] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[  601.168319] Suspending console(s) (use no_console_suspend to debug)
[  601.177246] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[  601.184304] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[  601.205459] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[  601.241729] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  601.248788] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  601.254838] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  601.277026] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  601.277373] sd 0:0:0:0: [sda] Stopping disk
[  601.608273] PM: suspend of devices complete after 331.019 msecs
[  601.608474] PM: late suspend of devices complete after 0.196 msecs
[  601.651972] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
[  601.674018] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
[  601.686117] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
[  601.711813] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[  601.723430] ehci_hcd 0000:00:1a.7: wake-up capability enabled by ACPI
[  601.749632] uhci_hcd 0000:00:1a.1: wake-up capability enabled by ACPI
[  601.761726] uhci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
[  601.761784] PM: noirq suspend of devices complete after 153.306 msecs
[  601.762009] ACPI: Preparing to enter system sleep state S3
[  601.783360] PM: Saving platform NVS memory
[  601.783362] Disabling non-boot CPUs ...
[  601.784646] smpboot: CPU 1 is now offline
[  601.785110] Extended CMOS year: 2000
[  601.785110] ACPI: Low-level resume complete
[  601.785110] PM: Restoring platform NVS memory
[  601.785110] Extended CMOS year: 2000
[  601.785110] Enabling non-boot CPUs ...
[  601.785110] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  601.784637] Initializing CPU#1
[  601.796836] CPU1 is up
[  601.798081] ACPI: Waking up from system sleep state S3
[  601.852646] uhci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
[  601.859592] uhci_hcd 0000:00:1a.1: wake-up capability disabled by ACPI
[  601.875692] ehci_hcd 0000:00:1a.7: wake-up capability disabled by ACPI
[  601.892837] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[  601.898886] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[  601.905944] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[  601.927106] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[  601.988069] firewire_ohci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
[  601.988071] firewire_ohci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
[  602.036204] PM: noirq resume of devices complete after 200.810 msecs
[  602.038617] PM: early resume of devices complete after 2.373 msecs
[  602.038644] i915 0000:00:02.0: setting latency timer to 64
[  602.038697] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[  602.038727] usb usb3: root hub lost power or was reset
[  602.038745] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[  602.038773] usb usb4: root hub lost power or was reset
[  602.038792] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[  602.038869] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[  602.039007] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  602.039035] usb usb5: root hub lost power or was reset
[  602.039051] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  602.039079] usb usb6: root hub lost power or was reset
[  602.039095] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  602.039124] usb usb7: root hub lost power or was reset
[  602.039142] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  602.039164] pci 0000:00:1e.0: setting latency timer to 64
[  602.039178] ahci 0000:00:1f.2: setting latency timer to 64
[  602.300207] usb 2-5: reset high-speed USB device number 2 using ehci_hcd
[  602.504057] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  602.508058] ata3: SATA link down (SStatus 0 SControl 300)
[  602.531234] ata2.00: configured for UDMA/100
[  602.584221] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  602.615441] ata1.00: failed to get Identify Device Data, Emask 0x1
[  602.617621] ata1.00: failed to get Identify Device Data, Emask 0x1
[  602.617626] ata1.00: configured for UDMA/133
[  602.632215] firewire_core 0000:03:01.0: rediscovered device fw0
[  602.632234] sd 0:0:0:0: [sda] Starting disk
[  602.633642] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  603.016913] PM: resume of devices complete after 978.290 msecs
[  603.017205] Restarting tasks ... done.
[  603.035492] video LNXVIDEO:01: Restoring backlight state
[  603.907232] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[  603.958273] init: anacron main process (6276) killed by TERM signal
[  604.114522] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[  604.208098] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by deadcenter on 2013-04-23
I have the same computer and I don't even have hdmi option in my sound settings.  How did you do it?  What additional drivers did you install.  It says that my ubuntu 12.10 software is updated.

---

