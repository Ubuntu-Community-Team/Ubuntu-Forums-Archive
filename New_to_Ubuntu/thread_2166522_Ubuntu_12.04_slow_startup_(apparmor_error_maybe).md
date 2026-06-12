---
title: "Ubuntu 12.04 slow startup (apparmor error maybe?)"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by gonzalo2 on 2013-08-09
Hello,

My problem is about a slow start in Ubuntu 12.04, it takes almost 2 minutes to load since I select Ubuntu in the grub. 

I have a Vaio laptop (model VGN-NW170TJ) and have been looking for a solve in similar threads, but any of them actually has an answer that could help me.

This is the output after typing 'dmesg' in a terminal, the bolded part is what I think there's a problem (there is a delay of about 90 seconds):

> [    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-26-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #38~precise2-Ubuntu SMP Thu Jun 20 18:29:36 UTC 2013 (Ubuntu 3.8.0-26.38~precise2-generic 3.8.13.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=32c5f807-0242-49e8-8aa6-37e3069aee35 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009bc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b5ea3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b5ea4000-0x00000000b5ec8fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b5ec9000-0x00000000b5ecafff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b5ecb000-0x00000000b5ecdfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b5ece000-0x00000000b5edefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b5edf000-0x00000000b5edffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b5ee0000-0x00000000b5f06fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b5f07000-0x00000000b5f07fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b5f08000-0x00000000b5f08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b5f09000-0x00000000b5f13fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000b5f14000-0x00000000b5f19fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b5f1a000-0x00000000b5f38fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b5f39000-0x00000000b5ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Sony Corporation VGN-NW170TJ/VAIO, BIOS R0180Y4 08/27/2009
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   3 base 0B6000000 mask FFE000000 uncachable
[    0.000000]   4 base 100000000 mask FC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2912MB, range: 32MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] total RAM covered: 3936M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2912MB, range: 32MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xb6000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xb6000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd650-0x000fd65f] mapped at [ffff8800000fd650]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xb5ffffff]
[    0.000000]  [mem 0x00000000-0xb5ffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xb5ffffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x13fffffff]
[    0.000000]  [mem 0x100000000-0x13fffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x13fffffff @ [mem 0xb5ffe000-0xb5ffffff]
[    0.000000] RAMDISK: [mem 0x36172000-0x370b0fff]
[    0.000000] ACPI: RSDP 00000000000f03b0 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000b5f12f10 0005C (v01   Sony     VAIO 20090827 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000b5f07a90 000F4 (v04   Sony     VAIO 20090827 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20121018/tbfadt-394)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X FACS address mismatch in FADT - 0xB5F19E40/0x00000000B5F19D40, using 32 (20121018/tbfadt-521)
[    0.000000] ACPI: DSDT 00000000b5f09010 07B23 (v01   Sony     VAIO 20090827 INTL 20051117)
[    0.000000] ACPI: FACS 00000000b5f19e40 00040
[    0.000000] ACPI: APIC 00000000b5f11f10 0006C (v02   Sony     VAIO 20090827 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000b5f18c90 0003C (v01   Sony     VAIO 20090827 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000b5f18c10 00038 (v01   Sony     VAIO 20090827 MSFT 00010013)
[    0.000000] ACPI: SLIC 00000000b5f14c10 00176 (v01   Sony     VAIO 20090827 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000b5edf590 00505 (v01   Sony     VAIO 20090827 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000b5ec8c10 002E4 (v01   Sony     VAIO 20090827 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x13fffffff]
[    0.000000]   NODE_DATA [mem 0x13fffb000-0x13fffffff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b800000-ffff88013f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x13fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xb5ea3fff]
[    0.000000]   node   0: [mem 0xb5f39000-0xb5ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x13fffffff]
[    0.000000] On node 0 totalpages: 1007350
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3909 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11582 pages used for memmap
[    0.000000]   DMA32 zone: 729645 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b5ea4000 - 00000000b5ec9000
[    0.000000] PM: Registered nosave memory: 00000000b5ec9000 - 00000000b5ecb000
[    0.000000] PM: Registered nosave memory: 00000000b5ecb000 - 00000000b5ece000
[    0.000000] PM: Registered nosave memory: 00000000b5ece000 - 00000000b5edf000
[    0.000000] PM: Registered nosave memory: 00000000b5edf000 - 00000000b5ee0000
[    0.000000] PM: Registered nosave memory: 00000000b5ee0000 - 00000000b5f07000
[    0.000000] PM: Registered nosave memory: 00000000b5f07000 - 00000000b5f08000
[    0.000000] PM: Registered nosave memory: 00000000b5f08000 - 00000000b5f09000
[    0.000000] PM: Registered nosave memory: 00000000b5f09000 - 00000000b5f14000
[    0.000000] PM: Registered nosave memory: 00000000b5f14000 - 00000000b5f1a000
[    0.000000] PM: Registered nosave memory: 00000000b5f1a000 - 00000000b5f39000
[    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] e820: [mem 0xb6000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 991602
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=32c5f807-0242-49e8-8aa6-37e3069aee35 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3867956k/5242880k available (7167k kernel code, 1213480k absent, 161444k reserved, 6075k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16252928 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1993.677 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3987.35 BogoMIPS (lpj=7974708)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004043] Security Framework initialized
[    0.004060] AppArmor: AppArmor initialized
[    0.004062] Yama: becoming mindful.
[    0.004475] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009001] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.009990] Mount-cache hash table entries: 256
[    0.010256] Initializing cgroup subsys cpuacct
[    0.010262] Initializing cgroup subsys memory
[    0.010273] Initializing cgroup subsys devices
[    0.010275] Initializing cgroup subsys freezer
[    0.010277] Initializing cgroup subsys blkio
[    0.010279] Initializing cgroup subsys perf_event
[    0.010283] Initializing cgroup subsys hugetlb
[    0.010318] CPU: Physical Processor ID: 0
[    0.010320] CPU: Processor Core ID: 0
[    0.010322] mce: CPU supports 6 MCE banks
[    0.010332] CPU0: Thermal monitoring enabled (TM2)
[    0.010337] process: using mwait in idle threads
[    0.010343] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.010343] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.010343] tlb_flushall_shift: -1
[    0.010483] Freeing SMP alternatives: 24k freed
[    0.013716] ACPI: Core revision 20121018
[    0.020033] ftrace: allocating 29338 entries in 115 pages
[    0.032507] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.073627] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] smpboot: Booting Node   0, Processors  #1
[    0.086458] Brought up 2 CPUs
[    0.086463] smpboot: Total of 2 processors activated (7974.70 BogoMIPS)
[    0.086594] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088109] devtmpfs: initialized
[    0.089318] EVM: security.selinux
[    0.089320] EVM: security.SMACK64
[    0.089322] EVM: security.capability
[    0.089341] PM: Registering ACPI NVS region [mem 0xb5ea4000-0xb5ec8fff] (151552 bytes)
[    0.089341] PM: Registering ACPI NVS region [mem 0xb5ecb000-0xb5ecdfff] (12288 bytes)
[    0.089341] PM: Registering ACPI NVS region [mem 0xb5edf000-0xb5edffff] (4096 bytes)
[    0.089341] PM: Registering ACPI NVS region [mem 0xb5f07000-0xb5f07fff] (4096 bytes)
[    0.089341] PM: Registering ACPI NVS region [mem 0xb5f14000-0xb5f19fff] (24576 bytes)
[    0.089341] regulator-dummy: no parameters
[    0.089341] NET: Registered protocol family 16
[    0.089500] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.089503] ACPI: bus type pci registered
[    0.089584] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.089588] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.125798] PCI: Using configuration type 1 for base access
[    0.126909] bio: create slab <bio-0> at 0
[    0.126909] ACPI: Added _OSI(Module Device)
[    0.126909] ACPI: Added _OSI(Processor Device)
[    0.126909] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.126909] ACPI: Added _OSI(Processor Aggregator Device)
[    0.126909] ACPI: EC: Look up EC in DSDT
[    0.128070] ACPI: Executed 1 blocks of module-level executable AML code
[    0.132038] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.136422] ACPI: SSDT 00000000b5ee3c90 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.136837] ACPI: Dynamic OEM Table Load:
[    0.136840] ACPI: SSDT           (null) 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.136993] ACPI: SSDT 00000000b5ee1810 007A2 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.137389] ACPI: Dynamic OEM Table Load:
[    0.137393] ACPI: SSDT           (null) 007A2 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.144311] ACPI: SSDT 00000000b5ee2d90 000FD (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.144718] ACPI: Dynamic OEM Table Load:
[    0.144721] ACPI: SSDT           (null) 000FD (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.144735] ACPI: SSDT 00000000b5ee0f90 00047 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.144735] ACPI: Dynamic OEM Table Load:
[    0.144735] ACPI: SSDT           (null) 00047 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.848068] ACPI: Interpreter enabled
[    0.848074] ACPI: (supports S0 S3 S4 S5)
[    0.848095] ACPI: Using IOAPIC for interrupt routing
[    0.884474] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.884601] ACPI: No dock devices found.
[    0.884605] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.884854] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.884858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.888092] \_SB_.PCI0:_OSC invalid UUID
[    0.888094] _OSC request data:1 8 0 
[    0.888563] PCI host bridge to bus 0000:00
[    0.888567] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.888570] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.888573] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.888575] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.888578] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.888580] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.888583] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.888585] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.888588] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.888591] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.888593] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    0.888606] pci 0000:00:00.0: [8086:2a40] type 00 class 0x060000
[    0.888630] DMAR: Forcing write-buffer flush capability
[    0.888632] DMAR: Disabling IOMMU for graphics on this chipset
[    0.888662] pci 0000:00:02.0: [8086:2a42] type 00 class 0x030000
[    0.888677] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.888686] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.888693] pci 0000:00:02.0: reg 20: [io  0xe140-0xe147]
[    0.888735] pci 0000:00:02.1: [8086:2a43] type 00 class 0x038000
[    0.888748] pci 0000:00:02.1: reg 10: [mem 0xd0400000-0xd04fffff 64bit]
[    0.888846] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.888908] pci 0000:00:1a.0: reg 20: [io  0xe0e0-0xe0ff]
[    0.888984] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.889045] pci 0000:00:1a.1: reg 20: [io  0xe0c0-0xe0df]
[    0.889123] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.889185] pci 0000:00:1a.2: reg 20: [io  0xe0a0-0xe0bf]
[    0.889273] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.889301] pci 0000:00:1a.7: reg 10: [mem 0xd4e04c00-0xd4e04fff]
[    0.889423] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.889462] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.889485] pci 0000:00:1b.0: reg 10: [mem 0xd4e00000-0xd4e03fff 64bit]
[    0.889592] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.889627] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.889740] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.889777] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.889889] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.889926] pci 0000:00:1c.2: [8086:2944] type 01 class 0x060400
[    0.890037] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.890081] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.890144] pci 0000:00:1d.0: reg 20: [io  0xe080-0xe09f]
[    0.890220] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.890281] pci 0000:00:1d.1: reg 20: [io  0xe060-0xe07f]
[    0.890359] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.890421] pci 0000:00:1d.2: reg 20: [io  0xe040-0xe05f]
[    0.890510] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.890539] pci 0000:00:1d.7: reg 10: [mem 0xd4e04800-0xd4e04bff]
[    0.890661] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.890692] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.890793] pci 0000:00:1f.0: [8086:2919] type 00 class 0x060100
[    0.890973] pci 0000:00:1f.2: [8086:2929] type 00 class 0x010601
[    0.891004] pci 0000:00:1f.2: reg 10: [io  0xe130-0xe137]
[    0.891017] pci 0000:00:1f.2: reg 14: [io  0xe120-0xe123]
[    0.891029] pci 0000:00:1f.2: reg 18: [io  0xe110-0xe117]
[    0.891042] pci 0000:00:1f.2: reg 1c: [io  0xe100-0xe103]
[    0.891055] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    0.891067] pci 0000:00:1f.2: reg 24: [mem 0xd4e04000-0xd4e047ff]
[    0.891144] pci 0000:00:1f.2: PME# supported from D3hot
[    0.891174] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.891197] pci 0000:00:1f.3: reg 10: [mem 0xd4e05000-0xd4e050ff 64bit]
[    0.891230] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    0.891506] pci 0000:01:00.0: [11ab:4380] type 00 class 0x020000
[    0.891678] pci 0000:01:00.0: reg 10: [mem 0xd3920000-0xd3923fff 64bit]
[    0.891778] pci 0000:01:00.0: reg 18: [io  0xd000-0xd0ff]
[    0.892154] pci 0000:01:00.0: reg 30: [mem 0xd3900000-0xd391ffff pref]
[    0.892617] pci 0000:01:00.0: supports D1 D2
[    0.892619] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.892903] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.892909] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.892914] pci 0000:00:1c.0:   bridge window [mem 0xd3900000-0xd4cfffff]
[    0.893054] pci 0000:02:00.0: [8086:4232] type 00 class 0x028000
[    0.893128] pci 0000:02:00.0: reg 10: [mem 0xd2500000-0xd2501fff 64bit]
[    0.893433] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.893595] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.893600] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.893606] pci 0000:00:1c.1:   bridge window [mem 0xd2500000-0xd38fffff]
[    0.893675] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
[    0.893681] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.893687] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd24fffff]
[    0.893748] pci 0000:0b:03.0: [1180:0832] type 00 class 0x0c0010
[    0.893775] pci 0000:0b:03.0: reg 10: [mem 0xd4d00000-0xd4d007ff]
[    0.893880] pci 0000:0b:03.0: PME# supported from D0 D3hot D3cold
[    0.893906] pci 0000:0b:03.1: [1180:0822] type 00 class 0x080500
[    0.893929] pci 0000:0b:03.1: reg 10: [mem 0xd4d00900-0xd4d009ff]
[    0.894032] pci 0000:0b:03.1: supports D1 D2
[    0.894034] pci 0000:0b:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.894062] pci 0000:0b:03.2: [1180:0592] type 00 class 0x088000
[    0.894086] pci 0000:0b:03.2: reg 10: [mem 0xd4d00800-0xd4d008ff]
[    0.894188] pci 0000:0b:03.2: supports D1 D2
[    0.894191] pci 0000:0b:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.894264] pci 0000:00:1e.0: PCI bridge to [bus 0b] (subtractive decode)
[    0.894273] pci 0000:00:1e.0:   bridge window [mem 0xd4d00000-0xd4dfffff]
[    0.894282] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.894285] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.894287] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.894290] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.894293] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.894295] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.894298] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.894300] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.894303] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.894306] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.894383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.894411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.894446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.894482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.894609] \_SB_.PCI0:_OSC invalid UUID
[    0.894612] _OSC request data:1 1f 0 
[    0.894616]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.894618]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.895920] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.895973] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.896046] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.896096] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.896145] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.896200] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.896251] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.896309] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.896405] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.896405] vgaarb: loaded
[    0.896405] vgaarb: bridge control possible 0000:00:02.0
[    0.896405] SCSI subsystem initialized
[    0.896405] ACPI: bus type scsi registered
[    0.896405] libata version 3.00 loaded.
[    0.896405] ACPI: bus type usb registered
[    0.896405] usbcore: registered new interface driver usbfs
[    0.896405] usbcore: registered new interface driver hub
[    0.896405] usbcore: registered new device driver usb
[    0.896405] PCI: Using ACPI for IRQ routing
[    0.907809] PCI: pci_cache_line_size set to 64 bytes
[    0.907985] e820: reserve RAM buffer [mem 0x0009bc00-0x0009ffff]
[    0.907987] e820: reserve RAM buffer [mem 0xb5ea4000-0xb7ffffff]
[    0.907990] e820: reserve RAM buffer [mem 0xb6000000-0xb7ffffff]
[    0.908110] NetLabel: Initializing
[    0.908112] NetLabel:  domain hash size = 128
[    0.908113] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.908129] NetLabel:  unlabeled traffic allowed by default
[    0.908143] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.908143] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.908143] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.910079] Switching to clocksource hpet
[    0.916184] AppArmor: AppArmor Filesystem Enabled
[    0.916224] pnp: PnP ACPI init
[    0.916243] ACPI: bus type pnp registered
[    0.916294] pnp 00:00: [dma 4]
[    0.916320] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.916349] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.916505] system 00:02: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.916510] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.916554] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.916607] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.916611] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.916614] system 00:04: [io  0x0800-0x0803] has been reserved
[    0.916616] system 00:04: [io  0x0400-0x047f] has been reserved
[    0.916619] system 00:04: [io  0x0500-0x053f] has been reserved
[    0.916622] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.916626] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.916660] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.916693] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.916729] pnp 00:07: Plug and Play ACPI device, IDs SNY9001 PNP0f13 (active)
[    0.916974] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.916978] system 00:08: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.916981] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.916984] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.916987] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.916990] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.916993] system 00:08: [mem 0xfeb00000-0xfeb03fff] has been reserved
[    0.916996] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.917000] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.932626] pnp: PnP ACPI: found 9 devices
[    0.932628] ACPI: ACPI bus type pnp unregistered
[    0.939537] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.939550] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.939563] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03-0a] add_size 200000
[    0.939581] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.939584] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.939587] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.939595] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd4f00000-0xd50fffff 64bit pref]
[    0.939600] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd5100000-0xd52fffff 64bit pref]
[    0.939605] pci 0000:00:1c.2: BAR 15: assigned [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.939608] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.939613] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.939620] pci 0000:00:1c.0:   bridge window [mem 0xd3900000-0xd4cfffff]
[    0.939626] pci 0000:00:1c.0:   bridge window [mem 0xd4f00000-0xd50fffff 64bit pref]
[    0.939635] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.939639] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.939646] pci 0000:00:1c.1:   bridge window [mem 0xd2500000-0xd38fffff]
[    0.939651] pci 0000:00:1c.1:   bridge window [mem 0xd5100000-0xd52fffff 64bit pref]
[    0.939660] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
[    0.939664] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.939671] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd24fffff]
[    0.939676] pci 0000:00:1c.2:   bridge window [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.939685] pci 0000:00:1e.0: PCI bridge to [bus 0b]
[    0.939692] pci 0000:00:1e.0:   bridge window [mem 0xd4d00000-0xd4dfffff]
[    0.939740] pci 0000:00:1e.0: setting latency timer to 64
[    0.939745] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.939748] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.939751] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.939753] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.939756] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.939758] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.939761] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.939763] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.939766] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.939768] pci_bus 0000:00: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.939771] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.939774] pci_bus 0000:01: resource 1 [mem 0xd3900000-0xd4cfffff]
[    0.939776] pci_bus 0000:01: resource 2 [mem 0xd4f00000-0xd50fffff 64bit pref]
[    0.939779] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.939782] pci_bus 0000:02: resource 1 [mem 0xd2500000-0xd38fffff]
[    0.939784] pci_bus 0000:02: resource 2 [mem 0xd5100000-0xd52fffff 64bit pref]
[    0.939787] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.939790] pci_bus 0000:03: resource 1 [mem 0xd0500000-0xd24fffff]
[    0.939792] pci_bus 0000:03: resource 2 [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.939795] pci_bus 0000:0b: resource 1 [mem 0xd4d00000-0xd4dfffff]
[    0.939798] pci_bus 0000:0b: resource 4 [io  0x0000-0x0cf7]
[    0.939801] pci_bus 0000:0b: resource 5 [io  0x0d00-0xffff]
[    0.939803] pci_bus 0000:0b: resource 6 [mem 0x000a0000-0x000bffff]
[    0.939806] pci_bus 0000:0b: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.939808] pci_bus 0000:0b: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.939811] pci_bus 0000:0b: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.939814] pci_bus 0000:0b: resource 10 [mem 0x000dc000-0x000dffff]
[    0.939816] pci_bus 0000:0b: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.939819] pci_bus 0000:0b: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.939821] pci_bus 0000:0b: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.939864] NET: Registered protocol family 2
[    0.940088] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.940346] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.940545] TCP: Hash tables configured (established 32768 bind 32768)
[    0.940591] TCP: reno registered
[    0.940602] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.940635] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.940724] NET: Registered protocol family 1
[    0.940740] pci 0000:00:02.0: Boot video device
[    0.941255] PCI: CLS 64 bytes, default 64
[    0.941309] Trying to unpack rootfs image as initramfs...
[    1.272661] Freeing initrd memory: 15612k freed
[    1.280279] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.280288] software IO TLB [mem 0xb1ea4000-0xb5ea4000] (64MB) mapped at [ffff8800b1ea4000-ffff8800b5ea3fff]
[    1.280652] Initialise module verification
[    1.280712] audit: initializing netlink socket (disabled)
[    1.280728] type=2000 audit(1376067533.280:1): initialized
[    1.315942] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.317945] VFS: Disk quotas dquot_6.5.2
[    1.317999] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.318570] fuse init (API version 7.20)
[    1.318662] msgmni has been set to 7585
[    1.319151] Key type asymmetric registered
[    1.319154] Asymmetric key parser 'x509' registered
[    1.319195] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.319226] io scheduler noop registered
[    1.319229] io scheduler deadline registered (default)
[    1.319236] io scheduler cfq registered
[    1.319416] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.319550] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.319681] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.319780] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.319797] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.319853] intel_idle: does not run on family 6 model 23
[    1.321961] ACPI: AC Adapter [ADP1] (on-line)
[    1.322073] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.323816] ACPI: Lid Switch [LID0]
[    1.323861] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.323866] ACPI: Power Button [PWRB]
[    1.323935] ACPI: Requesting acpi_cpufreq
[    1.325923] Monitor-Mwait will be used to enter C-1 state
[    1.326549] Monitor-Mwait will be used to enter C-2 state
[    1.326555] Monitor-Mwait will be used to enter C-3 state
[    1.326558] tsc: Marking TSC unstable due to TSC halts in idle
[    1.326569] ACPI: acpi_idle registered with cpuidle
[    1.363348] thermal LNXTHERM:00: registered as thermal_zone0
[    1.363351] ACPI: Thermal Zone [TZ00] (41 C)
[    1.364269] ACPI: Invalid active0 threshold
[    1.366080] thermal LNXTHERM:01: registered as thermal_zone1
[    1.366083] ACPI: Thermal Zone [TZ01] (41 C)
[    1.366114] GHES: HEST is not enabled!
[    1.366214] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.368018] Linux agpgart interface v0.103
[    1.368111] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    1.368227] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.369167] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    1.369308] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.370813] brd: module loaded
[    1.371598] loop: module loaded
[    1.372048] libphy: Fixed MDIO Bus: probed
[    1.372122] tun: Universal TUN/TAP device driver, 1.6
[    1.372124] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.372175] PPP generic driver version 2.4.2
[    1.372227] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.372229] ehci-pci: EHCI PCI platform driver
[    1.372267] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    1.372272] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    1.372280] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.372297] ehci-pci 0000:00:1a.7: debug port 1
[    1.376207] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    1.376227] ehci-pci 0000:00:1a.7: irq 19, io mem 0xd4e04c00
[    1.380614] ACPI: Battery Slot [BAT0] (battery absent)
[    1.388021] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.388045] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.388048] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.388050] usb usb1: Product: EHCI Host Controller
[    1.388053] usb usb1: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
[    1.388055] usb usb1: SerialNumber: 0000:00:1a.7
[    1.388167] hub 1-0:1.0: USB hub found
[    1.388172] hub 1-0:1.0: 6 ports detected
[    1.388313] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.388318] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.388324] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.388339] ehci-pci 0000:00:1d.7: debug port 1
[    1.392258] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.392274] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd4e04800
[    1.404024] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.404062] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.404065] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.404067] usb usb2: Product: EHCI Host Controller
[    1.404070] usb usb2: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
[    1.404072] usb usb2: SerialNumber: 0000:00:1d.7
[    1.404211] hub 2-0:1.0: USB hub found
[    1.404216] hub 2-0:1.0: 6 ports detected
[    1.404402] ehci-platform: EHCI generic platform driver
[    1.404412] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.404431] uhci_hcd: USB Universal Host Controller Interface driver
[    1.404453] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.404457] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.404463] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.404501] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e0e0
[    1.404539] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.404542] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.404544] usb usb3: Product: UHCI Host Controller
[    1.404547] usb usb3: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
[    1.404549] usb usb3: SerialNumber: 0000:00:1a.0
[    1.404644] hub 3-0:1.0: USB hub found
[    1.404649] hub 3-0:1.0: 2 ports detected
[    1.404735] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.404739] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.404745] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.404785] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e0c0
[    1.404822] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.404826] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.404828] usb usb4: Product: UHCI Host Controller
[    1.404831] usb usb4: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
[    1.404833] usb usb4: SerialNumber: 0000:00:1a.1
[    1.404923] hub 4-0:1.0: USB hub found
[    1.404928] hub 4-0:1.0: 2 ports detected
[    1.405008] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.405012] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.405018] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.405047] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e0a0
[    1.405083] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.405086] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.405089] usb usb5: Product: UHCI Host Controller
[    1.405091] usb usb5: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
[    1.405094] usb usb5: SerialNumber: 0000:00:1a.2
[    1.405190] hub 5-0:1.0: USB hub found
[    1.405194] hub 5-0:1.0: 2 ports detected
[    1.405277] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.405281] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.405286] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.405314] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    1.405351] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.405354] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.405356] usb usb6: Product: UHCI Host Controller
[    1.405359] usb usb6: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
[    1.405361] usb usb6: SerialNumber: 0000:00:1d.0
[    1.405451] hub 6-0:1.0: USB hub found
[    1.405457] hub 6-0:1.0: 2 ports detected
[    1.405534] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.405538] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.405550] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.405579] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    1.405616] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.405619] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.405621] usb usb7: Product: UHCI Host Controller
[    1.405624] usb usb7: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
[    1.405627] usb usb7: SerialNumber: 0000:00:1d.1
[    1.405714] hub 7-0:1.0: USB hub found
[    1.405719] hub 7-0:1.0: 2 ports detected
[    1.405797] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.405801] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.405806] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.405844] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    1.405882] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.405885] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.405887] usb usb8: Product: UHCI Host Controller
[    1.405890] usb usb8: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
[    1.405892] usb usb8: SerialNumber: 0000:00:1d.2
[    1.405983] hub 8-0:1.0: USB hub found
[    1.405993] hub 8-0:1.0: 2 ports detected
[    1.406135] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.410907] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.410914] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.411051] mousedev: PS/2 mouse device common for all mice
[    1.411186] rtc_cmos 00:05: RTC can wake from S4
[    1.411340] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.411373] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.411477] device-mapper: uevent: version 1.0.3
[    1.411542] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.411591] cpuidle: using governor ladder
[    1.411645] cpuidle: using governor menu
[    1.411650] ledtrig-cpu: registered to indicate activity on CPUs
[    1.411652] EFI Variables Facility v0.08 2004-May-17
[    1.411869] ashmem: initialized
[    1.411998] TCP: cubic registered
[    1.412130] NET: Registered protocol family 10
[    1.412328] NET: Registered protocol family 17
[    1.412341] Key type dns_resolver registered
[    1.412641] Loading module verification certificates
[    1.413885] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 19c1a75513ecc6be610385ab1ca94044dc0b42c3'
[    1.413901] registered taskstats version 1
[    1.416586] Key type trusted registered
[    1.418722] Key type encrypted registered
[    1.421425] rtc_cmos 00:05: setting system clock to 2013-08-09 16:58:54 UTC (1376067534)
[    1.422901] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.422904] EDD information not available.
[    1.425028] Freeing unused kernel memory: 1012k freed
[    1.425360] Write protecting the kernel read-only data: 12288k
[    1.429279] Freeing unused kernel memory: 1012k freed
[    1.432062] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.433358] Freeing unused kernel memory: 1008k freed
[    1.451730] udevd[95]: starting version 175
[    1.498682] Disabling lock debugging due to kernel taint
[    1.499060] sky2: driver version 1.30
[    1.499277] sky2 0000:01:00.0: Yukon-2 UL 2 chip revision 0
[    1.499767] sky2 0000:01:00.0: irq 43 for MSI/MSI-X
[    1.500454] sky2 0000:01:00.0 eth0: addr 00:1d:ba:ee:15:5a
[    1.509193] ahci 0000:00:1f.2: version 3.0
[    1.509269] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.509347] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.509351] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.509357] ahci 0000:00:1f.2: setting latency timer to 64
[    1.517750] sdhci: Secure Digital Host Controller Interface driver
[    1.517754] sdhci: Copyright(c) Pierre Ossman
[    1.518368] sdhci-pci 0000:0b:03.1: SDHCI controller found [1180:0822] (rev 22)
[    1.518570] sdhci-pci 0000:0b:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.518579] mmc0: no vqmmc regulator found
[    1.518581] mmc0: no vmmc regulator found
[    1.525581] scsi0 : ahci
[    1.529141] scsi1 : ahci
[    1.531204] scsi2 : ahci
[    1.532116] scsi3 : ahci
[    1.532185] ata1: SATA max UDMA/133 abar m2048@0xd4e04000 port 0xd4e04100 irq 44
[    1.532190] ata2: SATA max UDMA/133 abar m2048@0xd4e04000 port 0xd4e04180 irq 44
[    1.532192] ata3: DUMMY
[    1.532194] ata4: DUMMY
[    1.552251] mmc0: SDHCI controller on PCI [0000:0b:03.1] using DMA
[    1.616116] firewire_ohci 0000:0b:03.0: added OHCI v1.0 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.700079] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    1.836416] usb 1-2: New USB device found, idVendor=04f2, idProduct=b14e
[    1.836419] usb 1-2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    1.836422] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
[    1.852054] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.852089] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.852815] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.853899] ata2.00: ATAPI: Optiarc BD ROM BC-5500S, 1.75, max UDMA/100
[    1.855845] ata2.00: configured for UDMA/100
[    1.889754] ata1.00: ATA-8: TOSHIBA MK4058GSX, FF012A, max UDMA/100
[    1.889757] ata1.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.890532] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.890536] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.890716] ata1.00: configured for UDMA/100
[    1.890880] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4058GS FF01 PQ: 0 ANSI: 5
[    1.891057] sd 0:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    1.891068] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.891123] sd 0:0:0:0: [sda] Write Protect is off
[    1.891127] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.891204] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.892075] scsi 1:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S  1.75 PQ: 0 ANSI: 5
[    1.893480] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.893483] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.893589] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.893658] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.965877]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.966430] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.116162] firewire_core 0000:0b:03.0: created device fw0: GUID 0800460302f8fafa, S400
[    2.336045] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    2.504083] usb 7-1: New USB device found, idVendor=045e, idProduct=0745
[    2.504088] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.504091] usb 7-1: Product: Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0
[    2.504093] usb 7-1: Manufacturer: Microsoft
[    2.526136] usbcore: registered new interface driver usbhid
[    2.526140] usbhid: USB HID core driver
[    2.529873] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3
[    2.530083] hid-generic 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0] on usb-0000:00:1d.1-1/input0
[    2.530988] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input4
[    2.532887] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0] on usb-0000:00:1d.1-1/input1
[    2.551266] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/input/input5
[    2.551472] hid-generic 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Nano Transceiver v2.0] on usb-0000:00:1d.1-1/input2
[    2.920301] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    4.428061] init: ureadahead main process (266) terminated with status 5
[    5.729302] Adding 2001916k swap on /dev/sda5.  Priority:-1 extents:1 across:2001916k 
[    6.163870] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.251853] udevd[342]: starting version 175
[    7.689280] lp: driver loaded but no devices found
[    7.936906] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    7.936915] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.936920] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    7.936924] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.936926] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    7.936930] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.936932] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.606913] sony_laptop: Sony Notebook Control Driver v0.6
[    8.607043] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input6
[    8.607722] input: Sony Vaio Jogdial as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input7
[    8.630150] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[    8.689097] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[    8.700429] [drm] Initialized drm 1.1.0 20060810
[    9.071703] r592: driver successfully loaded
[    9.225018] cfg80211: Calling CRDA to update world regulatory domain
[    9.294062] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[    9.296094] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.377899] Intel(R) Wireless WiFi driver for Linux, in-tree:
[    9.377904] Copyright(c) 2003-2012 Intel Corporation
[    9.378254] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[    9.447000] i915 0000:00:02.0: setting latency timer to 64
[    9.497914] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    9.497926] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.497928] [drm] Driver supports precise vblank timestamp query.
[    9.497967] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.578929] fbcon: inteldrmfb (fb0) is primary device
[    9.602021] Linux video capture interface: v2.00
[    9.650188] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[    9.668598] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[    9.714928] type=1400 audit(1376085542.790:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
[    9.714938] type=1400 audit(1376085542.790:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=559 comm="apparmor_parser"
[    9.715387] type=1400 audit(1376085542.790:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
[    9.715396] type=1400 audit(1376085542.790:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=559 comm="apparmor_parser"
[    9.715647] type=1400 audit(1376085542.790:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
[    9.715659] type=1400 audit(1376085542.790:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=559 comm="apparmor_parser"
[    9.921605] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   10.182927] uvcvideo: Found UVC 1.00 device <unnamed> (04f2:b14e)
[   10.184965] input: UVC Camera (04f2:b14e) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input10
[   10.185159] usbcore: registered new interface driver uvcvideo
[   10.185160] USB Video Class driver (1.1.1)
[   10.408123] Console: switching to colour frame buffer device 170x48
[   10.411149] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.411152] i915 0000:00:02.0: registered panic notifier
[   10.416522] acpi device:14: registered as cooling_device2
[   10.416606] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.417741] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11
[   10.419066] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.421475] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   10.459085] hda_codec: ALC262: SKU not ready 0x411111f0
[   10.471336] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.471342] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.471344] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.471347] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.471349] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.471353] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.471488] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   10.529521] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.529668] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.529757] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.575114] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.618331] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   13.274215] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.827732] init: failsafe main process (868) killed by TERM signal
[   15.306535] type=1400 audit(1376085548.382:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=932 comm="apparmor_parser"
[   15.307008] type=1400 audit(1376085548.382:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=932 comm="apparmor_parser"
[   15.307275] type=1400 audit(1376085548.382:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=932 comm="apparmor_parser"
[   15.412081] type=1400 audit(1376085548.490:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=931 comm="apparmor_parser"
[   15.412470] type=1400 audit(1376085548.490:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=931 comm="apparmor_parser"
[   15.446861] type=1400 audit(1376085548.522:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=933 comm="apparmor_parser"
[   15.452354] type=1400 audit(1376085548.530:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=933 comm="apparmor_parser"
[   15.453487] type=1400 audit(1376085548.530:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=933 comm="apparmor_parser"
[   15.454570] type=1400 audit(1376085548.530:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=933 comm="apparmor_parser"
[   15.457855] type=1400 audit(1376085548.534:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=933 comm="apparmor_parser"
[   16.007328] ppdev: user-space parallel port driver
[   17.066902] Bluetooth: Core ver 2.16
[   17.066929] NET: Registered protocol family 31
[   17.066931] Bluetooth: HCI device and connection manager initialized
[   17.066944] Bluetooth: HCI socket layer initialized
[   17.066947] Bluetooth: L2CAP socket layer initialized
[   17.066955] Bluetooth: SCO socket layer initialized
[   17.264662] Bluetooth: RFCOMM TTY layer initialized
[   17.264678] Bluetooth: RFCOMM socket layer initialized
[   17.264680] Bluetooth: RFCOMM ver 1.11
[   18.093245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.093250] Bluetooth: BNEP filters: protocol multicast
[   18.093264] Bluetooth: BNEP socket layer initialized
[   21.029814] sky2 0000:01:00.0 eth0: enabling interface
[   21.030182] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.031881] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.035806] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.039169] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   21.244609] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   21.247570] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   21.383187] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.384245] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.985702] wlan0: authenticate with 00:25:86:b9:3f:fe
[   28.989029] wlan0: send auth to 00:25:86:b9:3f:fe (try 1/3)
[   28.992780] wlan0: authenticated
[   28.992968] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   28.992972] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   28.996053] wlan0: associate with 00:25:86:b9:3f:fe (try 1/3)
[   29.000247] wlan0: RX AssocResp from 00:25:86:b9:3f:fe (capab=0x421 status=0 aid=1)
[   29.003828] wlan0: associated
[   29.003861] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
**[   41.763737] audit_printk_skb: 30 callbacks suppressed**
**[   41.763741] type=1400 audit(1376085574.834:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1011 comm="cupsd" pid=1011 comm="cupsd" capability=36  capname="block_suspend"**
**[  153.940812] CE: hpet increased min_delta_ns to 20113 nsec**

I appreciate any suggestion that would help me. Thanks!

---

### Post by DuckHook on 2013-08-09
Hi gonzalo2,

Welcome to Ubuntu and the forums.

*apparmor* is unlikely to be the problem. There are many causes of boot delays but some common ones are your boot process waiting for either of a network mapping or a network share. Does your setup involve any of these?

*dmesg* will generally not tell you if these are holding up your boot process. However, your *dmesg* does show a highly involved boot process involving significant initializations and therefore significant time. Therefore, what is the basis of your concern? Did your system boot up appreciably faster in the past? Did it slow down after a particular update/upgrade? If so, which one?

Also important to tell us more about your system:

1. Is it HDD-based and if so, do you have a slow HDD?
2. What CPU is installed?
3. How much system memory?

Your system may simply not have the horsepower to boot up fast.

The next time you boot your system, please hit the <Esc> key which should get rid of the overlaying boot screen and reveal each step of the boot process in all its gory detail. You might be able to see which process (if any) is causing the long wait time.

P.S. In future, please enclose output in {CODE}output{/CODE} marks (where square brackets are substituted for the parenthesis) instead of QUOTE marks for easier reading.

---

