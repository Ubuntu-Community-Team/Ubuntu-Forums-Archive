---
title: "wireless error"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by sutibun on 2012-07-18
i just installed linux ubuntu with dual boot with win 7. in win 7 i use wireless internet and works fine. ubuntu does not find any wireless connections tho and i cant use a wired internet.there is any way to download the drivers through win 7 and install them in ubuntu? please explain to me what i should do, i am new to ubuntu

---

### Post by NikTh on 2012-07-18
Hi , 
i am sure that you must provide more info . 
Boot to Ubuntu and open a terminal (ctrl+alt+t) , copy-paste these commands (one at time  , one line=one command) . 
```
dmesg > dmesg.txt 
lsmod > lsmod.txt 
lspci -nnk | grep -iA2 net > lspci.txt
```Then you will find 3 files dmesg.txt , lsmod.txt , lspci.txt at your home directory. Move these files somewhere so you can access them from windows later. 
Boot to windows , open these files (with wordpad) and post back here the content. 

**Please put the content inside [CODE] tags , by highlighting the text and click at[SIZE=3] # [/SIZE]symbol on top of message pane.**
Thanks

---

### Post by sutibun on 2012-07-18
dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Acer            Extensa 5220                   /Columbia                       , BIOS V1.32           02/01/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] total RAM covered: 1015M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f7d60] f7d60
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365f2000 - 372f1000
[    0.000000] ACPI: RSDP 000f7bf0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 3f6d1f1d 0009C (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP 3f6dcbe5 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 3f6d3bc9 08FA8 (v02 INTEL  CRESTLNE 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 3f6dffc0 00040
[    0.000000] ACPI: HPET 3f6dccd9 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 3f6dcd11 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 3f6dcd4d 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 3f6dcd7f 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 3f6dcda5 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: ASF! 3f6dcf1b 00063 (v32 OEMID  OEMTBL   06040000 PTL  00000001)
[    0.000000] ACPI: APIC 3f6dcf7e 0005A (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f6dcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f6d357a 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d2ee8 00692 (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d2d1d 001CB (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d26fe 0061F (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d249f 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d1fb9 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f6d0
[    0.000000] On node 0 totalpages: 259679
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f5e02200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32212 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5800000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257649
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=150ca18f-30f2-4024-9abb-54514b90fa6f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4156416 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d0)
[    0.000000] Memory: 1002812k/1039168k available (5329k kernel code, 35904k reserved, 2589k data, 696k init, 129864k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5408000 soft=f540a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.024 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.04 BogoMIPS (lpj=7980096)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004034] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004055] Yama: becoming mindful.
[    0.004120] Mount-cache hash table entries: 512
[    0.004270] Initializing cgroup subsys cpuacct
[    0.004277] Initializing cgroup subsys memory
[    0.004287] Initializing cgroup subsys devices
[    0.004289] Initializing cgroup subsys freezer
[    0.004292] Initializing cgroup subsys net_cls
[    0.004294] Initializing cgroup subsys blkio
[    0.004302] Initializing cgroup subsys perf_event
[    0.004340] mce: CPU supports 6 MCE banks
[    0.004350] CPU0: Thermal monitoring handled by SMI
[    0.004355] using mwait in idle threads.
[    0.004591] SMP alternatives: switching to UP code
[    0.014297] Freeing SMP alternatives: 24k freed
[    0.014312] ACPI: Core revision 20110413
[    0.024017] ftrace: allocating 24885 entries in 49 pages
[    0.028068] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028444] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068418] CPU0: Intel(R) Celeron(R) CPU          550  @ 2.00GHz stepping 01
[    0.072003] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (3990.04 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] PM: Registering ACPI NVS region at 3f6d0000 (65536 bytes)
[    0.072003] print_constraints: dummy: 
[    0.072003] Time:  0:36:49  Date: 07/19/12
[    0.072003] NET: Registered protocol family 16
[    0.072003] EISA bus registered
[    0.072003] ACPI: bus type pci registered
[    0.072003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.072003] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.072003] PCI: Using MMCONFIG for extended config space
[    0.072003] PCI: Using configuration type 1 for base access
[    0.072634] bio: create slab <bio-0> at 0
[    0.074085] ACPI: EC: Look up EC in DSDT
[    0.077051] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.077549] ACPI: Extensa 5220 detected - disabling mwait for CPU C-states
[    0.084113] ACPI: Interpreter enabled
[    0.084113] ACPI: (supports S0 S3 S4 S5)
[    0.084128] ACPI: Using IOAPIC for interrupt routing
[    0.496649] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.496835] ACPI: No dock devices found.
[    0.496838] HEST: Table not found.
[    0.496842] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.497209] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.497913] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.497916] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.497919] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.497922] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.497925] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.497928] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.497930] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.497934] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xdfffffff]
[    0.497936] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.497954] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.498008] pci 0000:00:02.0: [8086:2a02] type 0 class 0x000300
[    0.498025] pci 0000:00:02.0: reg 10: [mem 0xfc000000-0xfc0fffff 64bit]
[    0.498035] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.498043] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.498083] pci 0000:00:02.1: [8086:2a03] type 0 class 0x000380
[    0.498097] pci 0000:00:02.1: reg 10: [mem 0xfc100000-0xfc1fffff 64bit]
[    0.498197] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.498259] pci 0000:00:1a.0: reg 20: [io  0x1820-0x183f]
[    0.498302] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.498365] pci 0000:00:1a.1: reg 20: [io  0x1840-0x185f]
[    0.498424] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.498451] pci 0000:00:1a.7: reg 10: [mem 0xfc504000-0xfc5043ff]
[    0.498549] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.498556] pci 0000:00:1a.7: PME# disabled
[    0.498587] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.498612] pci 0000:00:1b.0: reg 10: [mem 0xfc300000-0xfc303fff 64bit]
[    0.498704] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.498709] pci 0000:00:1b.0: PME# disabled
[    0.498740] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.498835] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.498841] pci 0000:00:1c.0: PME# disabled
[    0.498874] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.498971] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.498976] pci 0000:00:1c.1: PME# disabled
[    0.499010] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
[    0.499105] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.499111] pci 0000:00:1c.2: PME# disabled
[    0.499148] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.499211] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.499256] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.499318] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.499361] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.499424] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.499484] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.499510] pci 0000:00:1d.7: reg 10: [mem 0xfc504400-0xfc5047ff]
[    0.499609] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.499614] pci 0000:00:1d.7: PME# disabled
[    0.499640] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.499734] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.499856] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.499863] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.499870] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0068 (mask 0007)
[    0.499919] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.499937] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.499951] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.499964] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.499977] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.499990] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.500046] pci 0000:00:1f.2: [8086:2828] type 0 class 0x000101
[    0.500070] pci 0000:00:1f.2: reg 10: [io  0x1c00-0x1c07]
[    0.500083] pci 0000:00:1f.2: reg 14: [io  0x18f4-0x18f7]
[    0.500096] pci 0000:00:1f.2: reg 18: [io  0x18f8-0x18ff]
[    0.500109] pci 0000:00:1f.2: reg 1c: [io  0x18f0-0x18f3]
[    0.500122] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ef]
[    0.500136] pci 0000:00:1f.2: reg 24: [io  0x18d0-0x18df]
[    0.500174] pci 0000:00:1f.2: PME# supported from D3hot
[    0.500179] pci 0000:00:1f.2: PME# disabled
[    0.500196] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.500215] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.500261] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
[    0.500441] pci 0000:02:00.0: [14e4:1693] type 0 class 0x000200
[    0.500476] pci 0000:02:00.0: reg 10: [mem 0xf6000000-0xf600ffff 64bit]
[    0.500623] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.500630] pci 0000:02:00.0: PME# disabled
[    0.508091] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.508097] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.508103] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.508112] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.508206] pci 0000:04:00.0: [14e4:4311] type 0 class 0x000280
[    0.508231] pci 0000:04:00.0: reg 10: [mem 0xf8000000-0xf8003fff]
[    0.508376] pci 0000:04:00.0: supports D1 D2
[    0.508406] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.508422] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.508427] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.508433] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.508442] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.508510] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.508515] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.508521] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.508530] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.508594] pci 0000:0f:06.0: [104c:8039] type 2 class 0x000607
[    0.508623] pci 0000:0f:06.0: reg 10: [mem 0xfc204000-0xfc204fff]
[    0.508654] pci 0000:0f:06.0: supports D1 D2
[    0.508656] pci 0000:0f:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508662] pci 0000:0f:06.0: PME# disabled
[    0.508689] pci 0000:0f:06.1: [104c:803a] type 0 class 0x000c00
[    0.508717] pci 0000:0f:06.1: reg 10: [mem 0xfc206000-0xfc2067ff]
[    0.508733] pci 0000:0f:06.1: reg 14: [mem 0xfc200000-0xfc203fff]
[    0.508831] pci 0000:0f:06.1: supports D1 D2
[    0.508833] pci 0000:0f:06.1: PME# supported from D0 D1 D2 D3hot
[    0.508839] pci 0000:0f:06.1: PME# disabled
[    0.508865] pci 0000:0f:06.2: [104c:803b] type 0 class 0x000180
[    0.508892] pci 0000:0f:06.2: reg 10: [mem 0xfc205000-0xfc205fff]
[    0.508998] pci 0000:0f:06.2: supports D1 D2
[    0.509000] pci 0000:0f:06.2: PME# supported from D0 D1 D2 D3hot
[    0.509006] pci 0000:0f:06.2: PME# disabled
[    0.509031] pci 0000:0f:06.3: [104c:803c] type 0 class 0x000805
[    0.509057] pci 0000:0f:06.3: reg 10: [mem 0xfc206800-0xfc2068ff]
[    0.509164] pci 0000:0f:06.3: supports D1 D2
[    0.509166] pci 0000:0f:06.3: PME# supported from D0 D1 D2 D3hot
[    0.509172] pci 0000:0f:06.3: PME# disabled
[    0.509241] pci 0000:00:1e.0: PCI bridge to [bus 0f-10] (subtractive decode)
[    0.509247] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.509253] pci 0000:00:1e.0:   bridge window [mem 0xfc200000-0xfc2fffff]
[    0.509262] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.509265] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.509268] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.509271] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.509273] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.509276] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.509279] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.509282] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.509284] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xdfffffff] (subtractive decode)
[    0.509287] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.509344] pci_bus 0000:10: [bus 10-13] partially hidden behind transparent bridge 0000:0f [bus 0f-10]
[    0.509376] pci_bus 0000:00: on NUMA node 0
[    0.509380] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.509574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.509635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.509694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.509782] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.509850]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.509854]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.509856] ACPI _OSC control for PCIe not granted, disabling ASPM
[    4.308687] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    4.308739] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[    4.308789] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    4.308839] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[    4.308888] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[    4.308937] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 *11)
[    4.308986] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[    4.309035] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    4.309131] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    4.309142] vgaarb: loaded
[    4.309143] vgaarb: bridge control possible 0000:00:02.0
[    4.309378] SCSI subsystem initialized
[    4.309441] libata version 3.00 loaded.
[    4.309489] usbcore: registered new interface driver usbfs
[    4.309502] usbcore: registered new interface driver hub
[    4.309529] usbcore: registered new device driver usb
[    4.309618] PCI: Using ACPI for IRQ routing
[    4.321848] PCI: pci_cache_line_size set to 64 bytes
[    4.322037] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    4.322040] reserve RAM buffer: 000000003f6d0000 - 000000003fffffff 
[    4.322149] NetLabel: Initializing
[    4.322152] NetLabel:  domain hash size = 128
[    4.322153] NetLabel:  protocols = UNLABELED CIPSOv4
[    4.322163] NetLabel:  unlabeled traffic allowed by default
[    4.322210] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    4.322218] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    4.322223] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    4.324311] Switching to clocksource hpet
[    4.328259] Switched to NOHz mode on CPU #0
[    4.330970] AppArmor: AppArmor Filesystem Enabled
[    4.331016] pnp: PnP ACPI init
[    4.331037] ACPI: bus type pnp registered
[    4.331455] pnp 00:00: [bus 00-ff]
[    4.331459] pnp 00:00: [io  0x0000-0x0cf7 window]
[    4.331461] pnp 00:00: [io  0x0cf8-0x0cff]
[    4.331463] pnp 00:00: [io  0x0d00-0xffff window]
[    4.331466] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    4.331469] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    4.331471] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    4.331474] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    4.331476] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    4.331479] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    4.331481] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    4.331484] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    4.331486] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    4.331488] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    4.331491] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    4.331493] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    4.331496] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    4.331498] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    4.331501] pnp 00:00: [mem 0x40000000-0xdfffffff window]
[    4.331503] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    4.331506] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    4.331589] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    4.331685] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    4.331687] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    4.331690] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    4.331692] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    4.331694] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    4.331697] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    4.331699] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    4.331763] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    4.331767] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    4.331769] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    4.331772] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    4.331775] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    4.331778] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    4.331781] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    4.331785] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.334395] pnp 00:02: [io  0x0060]
[    4.334397] pnp 00:02: [io  0x0064]
[    4.334410] pnp 00:02: [irq 1]
[    4.334452] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    4.334467] pnp 00:03: [irq 12]
[    4.334506] pnp 00:03: Plug and Play ACPI device, IDs SYN0302 SYN0300 SYN0002 PNP0f13 (active)
[    4.334517] pnp 00:04: [io  0x0000-0x001f]
[    4.334519] pnp 00:04: [io  0x0081-0x0091]
[    4.334521] pnp 00:04: [io  0x0093-0x009f]
[    4.334523] pnp 00:04: [io  0x00c0-0x00df]
[    4.334526] pnp 00:04: [dma 4]
[    4.334568] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    4.334578] pnp 00:05: [mem 0xff000000-0xffffffff]
[    4.334615] pnp 00:05: Plug and Play ACPI device, IDs INT0800 (active)
[    4.334693] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    4.334749] system 00:06: [mem 0xfed00000-0xfed003ff] has been reserved
[    4.334753] system 00:06: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    4.334765] pnp 00:07: [io  0x00f0]
[    4.334771] pnp 00:07: [irq 13]
[    4.334810] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    4.334823] pnp 00:08: [io  0x002e-0x002f]
[    4.334825] pnp 00:08: [io  0x004e-0x004f]
[    4.334827] pnp 00:08: [io  0x0061]
[    4.334829] pnp 00:08: [io  0x0063]
[    4.334831] pnp 00:08: [io  0x0065]
[    4.334833] pnp 00:08: [io  0x0067]
[    4.334835] pnp 00:08: [io  0x0080]
[    4.334837] pnp 00:08: [io  0x0092]
[    4.334839] pnp 00:08: [io  0x00b2-0x00b3]
[    4.334841] pnp 00:08: [io  0x0068-0x006f]
[    4.334843] pnp 00:08: [io  0x0800-0x080f]
[    4.334845] pnp 00:08: [io  0x1000-0x107f]
[    4.334847] pnp 00:08: [io  0x1180-0x11bf]
[    4.334849] pnp 00:08: [io  0xfe00]
[    4.334854] pnp 00:08: [mem 0xff800000-0xff800fff]
[    4.334923] system 00:08: [io  0x0800-0x080f] has been reserved
[    4.334926] system 00:08: [io  0x1000-0x107f] has been reserved
[    4.334929] system 00:08: [io  0x1180-0x11bf] has been reserved
[    4.334932] system 00:08: [io  0xfe00] has been reserved
[    4.334935] system 00:08: [mem 0xff800000-0xff800fff] has been reserved
[    4.334939] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.334949] pnp 00:09: [io  0x0070-0x0077]
[    4.334955] pnp 00:09: [irq 8]
[    4.334994] pnp 00:09: Plug and Play ACPI device, IDs PNP0b00 (active)
[    4.335109] pnp 00:0a: Plug and Play ACPI device, IDs NSC6001 (disabled)
[    4.532041] pnp: PnP ACPI: found 11 devices
[    4.532043] ACPI: ACPI bus type pnp unregistered
[    4.532048] PnPBIOS: Disabled by ACPI PNP
[    4.568190] PCI: max bus depth: 2 pci_try_num: 3
[    4.568248] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    4.568253] pci 0000:00:1e.0: BAR 13: assigned [io  0x5000-0x5fff]
[    4.568257] pci 0000:00:1f.3: BAR 0: assigned [mem 0x44000000-0x440000ff]
[    4.568263] pci 0000:00:1f.3: BAR 0: set to [mem 0x44000000-0x440000ff] (PCI address [0x44000000-0x440000ff])
[    4.568267] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    4.568271] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    4.568279] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    4.568284] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    4.568293] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    4.568297] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    4.568304] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    4.568310] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    4.568319] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    4.568323] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    4.568330] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    4.568336] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    4.568346] pci 0000:0f:06.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    4.568350] pci 0000:0f:06.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    4.568353] pci 0000:0f:06.0: BAR 13: assigned [io  0x5000-0x50ff]
[    4.568355] pci 0000:0f:06.0: BAR 14: assigned [io  0x5400-0x54ff]
[    4.568358] pci 0000:0f:06.0: CardBus bridge to [bus 10-13]
[    4.568360] pci 0000:0f:06.0:   bridge window [io  0x5000-0x50ff]
[    4.568366] pci 0000:0f:06.0:   bridge window [io  0x5400-0x54ff]
[    4.568372] pci 0000:0f:06.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    4.568379] pci 0000:0f:06.0:   bridge window [mem 0x48000000-0x4bffffff]
[    4.568385] pci 0000:00:1e.0: PCI bridge to [bus 0f-10]
[    4.568388] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    4.568396] pci 0000:00:1e.0:   bridge window [mem 0xfc200000-0xfc2fffff]
[    4.568401] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    4.568428] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.568435] pci 0000:00:1c.0: setting latency timer to 64
[    4.568446] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.568451] pci 0000:00:1c.1: setting latency timer to 64
[    4.568463] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.568468] pci 0000:00:1c.2: setting latency timer to 64
[    4.568478] pci 0000:00:1e.0: setting latency timer to 64
[    4.568490] pci 0000:0f:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.568498] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    4.568500] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    4.568503] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    4.568505] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    4.568508] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    4.568511] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    4.568513] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    4.568516] pci_bus 0000:00: resource 11 [mem 0x40000000-0xdfffffff]
[    4.568518] pci_bus 0000:00: resource 12 [mem 0xf0000000-0xfebfffff]
[    4.568521] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    4.568524] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    4.568526] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    4.568529] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    4.568532] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    4.568534] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    4.568537] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    4.568540] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    4.568542] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    4.568545] pci_bus 0000:0f: resource 0 [io  0x5000-0x5fff]
[    4.568548] pci_bus 0000:0f: resource 1 [mem 0xfc200000-0xfc2fffff]
[    4.568550] pci_bus 0000:0f: resource 2 [mem 0x40000000-0x43ffffff pref]
[    4.568553] pci_bus 0000:0f: resource 4 [io  0x0000-0x0cf7]
[    4.568555] pci_bus 0000:0f: resource 5 [io  0x0d00-0xffff]
[    4.568558] pci_bus 0000:0f: resource 6 [mem 0x000a0000-0x000bffff]
[    4.568560] pci_bus 0000:0f: resource 7 [mem 0x000d0000-0x000d3fff]
[    4.568563] pci_bus 0000:0f: resource 8 [mem 0x000d4000-0x000d7fff]
[    4.568565] pci_bus 0000:0f: resource 9 [mem 0x000d8000-0x000dbfff]
[    4.568568] pci_bus 0000:0f: resource 10 [mem 0x000dc000-0x000dffff]
[    4.568570] pci_bus 0000:0f: resource 11 [mem 0x40000000-0xdfffffff]
[    4.568573] pci_bus 0000:0f: resource 12 [mem 0xf0000000-0xfebfffff]
[    4.568576] pci_bus 0000:10: resource 0 [io  0x5000-0x50ff]
[    4.568578] pci_bus 0000:10: resource 1 [io  0x5400-0x54ff]
[    4.568581] pci_bus 0000:10: resource 2 [mem 0x40000000-0x43ffffff pref]
[    4.568583] pci_bus 0000:10: resource 3 [mem 0x48000000-0x4bffffff]
[    4.568630] NET: Registered protocol family 2
[    4.568690] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.568937] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    4.569442] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.569782] TCP: Hash tables configured (established 131072 bind 65536)
[    4.569785] TCP reno registered
[    4.569788] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    4.569801] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    4.569932] NET: Registered protocol family 1
[    4.569958] pci 0000:00:02.0: Boot video device
[    4.570191] PCI: CLS 64 bytes, default 64
[    4.570280] Simple Boot Flag at 0x36 set to 0x1
[    4.570596] audit: initializing netlink socket (disabled)
[    4.570610] type=2000 audit(1342658213.564:1): initialized
[    4.593400] Trying to unpack rootfs image as initramfs...
[    4.628100] highmem bounce pool size: 64 pages
[    4.628107] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.640294] VFS: Disk quotas dquot_6.5.2
[    4.640376] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.641133] fuse init (API version 7.16)
[    4.641239] msgmni has been set to 1705
[    4.652243] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.656331] io scheduler noop registered
[    4.656334] io scheduler deadline registered
[    4.656372] io scheduler cfq registered (default)
[    4.656530] pcieport 0000:00:1c.0: setting latency timer to 64
[    4.656600] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    4.656691] pcieport 0000:00:1c.1: setting latency timer to 64
[    4.656752] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    4.656835] pcieport 0000:00:1c.2: setting latency timer to 64
[    4.656895] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    4.657003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.657029] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.658538] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.659555] ACPI: AC Adapter [ADP1] (on-line)
[    4.659629] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    4.660688] ACPI: Lid Switch [LID0]
[    4.660738] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    4.660743] ACPI: Sleep Button [SLPB]
[    4.660799] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.660803] ACPI: Power Button [PWRF]
[    4.660831] ACPI: acpi_idle registered with cpuidle
[    4.663602] Marking TSC unstable due to TSC halts in idle
[    4.876883] thermal LNXTHERM:00: registered as thermal_zone0
[    4.876886] ACPI: Thermal Zone [TZS0] (80 C)
[    4.882337] thermal LNXTHERM:01: registered as thermal_zone1
[    4.882340] ACPI: Thermal Zone [TZS1] (76 C)
[    4.882381] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.882410] ERST: Table is not found!
[    4.882506] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.883917] Linux agpgart interface v0.103
[    4.883988] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    4.884079] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    4.884284] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    4.884406] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    4.885642] brd: module loaded
[    4.886222] loop: module loaded
[    4.886373] ata_piix 0000:00:1f.1: version 2.13
[    4.886400] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.886440] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.892193] scsi0 : ata_piix
[    4.892343] isapnp: Scanning for PnP cards...
[    4.941522] scsi1 : ata_piix
[    4.941968] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    4.941971] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    4.942004] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.942011] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.990001] Freeing initrd memory: 13308k freed
[    5.129829] ata_piix 0000:00:1f.2: setting latency timer to 64
[    5.141945] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[    5.229403] scsi2 : ata_piix
[    5.229476] scsi3 : ata_piix
[    5.230341] ata3: SATA max UDMA/133 cmd 0x1c00 ctl 0x18f4 bmdma 0x18e0 irq 19
[    5.230350] ata4: SATA max UDMA/133 cmd 0x18f8 ctl 0x18f0 bmdma 0x18e8 irq 19
[    5.230874] Fixed MDIO Bus: probed
[    5.230904] PPP generic driver version 2.4.2
[    5.231049] tun: Universal TUN/TAP device driver, 1.6
[    5.231051] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.231144] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.231184] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    5.231210] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.231215] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.231251] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.231288] ehci_hcd 0000:00:1a.7: debug port 1
[    5.235178] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    5.235211] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc504000
[    5.239396] ata1.00: configured for UDMA/33
[    5.283000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.283131] hub 1-0:1.0: USB hub found
[    5.283136] hub 1-0:1.0: 4 ports detected
[    5.283214] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.283290] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.283294] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.283337] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.283370] ehci_hcd 0000:00:1d.7: debug port 1
[    5.287274] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    5.287291] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504400
[    5.334870] isapnp: No Plug & Play device found
[    5.338433] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[    5.343268] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.343272] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.343385] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.343513] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.344021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.344192] hub 2-0:1.0: USB hub found
[    5.344196] hub 2-0:1.0: 6 ports detected
[    5.344300] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.344318] uhci_hcd: USB Universal Host Controller Interface driver
[    5.344366] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.344377] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.344381] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.344420] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.344453] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001820
[    5.344579] hub 3-0:1.0: USB hub found
[    5.344584] hub 3-0:1.0: 2 ports detected
[    5.344657] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.344665] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.344668] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.344703] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.344747] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    5.344869] hub 4-0:1.0: USB hub found
[    5.344873] hub 4-0:1.0: 2 ports detected
[    5.344997] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.345005] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.345009] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.345050] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.345082] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    5.345214] hub 5-0:1.0: USB hub found
[    5.345218] hub 5-0:1.0: 2 ports detected
[    5.345276] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.345283] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.345287] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.345322] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.345365] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
[    5.345486] hub 6-0:1.0: USB hub found
[    5.345490] hub 6-0:1.0: 2 ports detected
[    5.345552] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.345560] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.345564] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.345599] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.345640] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    5.345764] hub 7-0:1.0: USB hub found
[    5.345768] hub 7-0:1.0: 2 ports detected
[    5.345890] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.355030] i8042: Detected active multiplexing controller, rev 1.1
[    5.363872] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.363877] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    5.363907] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    5.363931] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    5.363958] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    5.364082] mousedev: PS/2 mouse device common for all mice
[    5.364445] rtc_cmos 00:09: RTC can wake from S4
[    5.364568] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    5.364602] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    5.364709] device-mapper: uevent: version 1.0.3
[    5.364795] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    5.364825] EISA: Probing bus 0 at eisa.0
[    5.364828] EISA: Cannot allocate resource for mainboard
[    5.364830] Cannot allocate resource for EISA slot 1
[    5.364832] Cannot allocate resource for EISA slot 2
[    5.364834] Cannot allocate resource for EISA slot 3
[    5.364836] Cannot allocate resource for EISA slot 4
[    5.364838] Cannot allocate resource for EISA slot 5
[    5.364840] Cannot allocate resource for EISA slot 6
[    5.364842] Cannot allocate resource for EISA slot 7
[    5.364844] Cannot allocate resource for EISA slot 8
[    5.364846] EISA: Detected 0 cards.
[    5.364857] cpufreq-nforce2: No nForce2 chipset.
[    5.364892] cpuidle: using governor ladder
[    5.364942] cpuidle: using governor menu
[    5.364944] EFI Variables Facility v0.08 2004-May-17
[    5.365193] TCP cubic registered
[    5.365341] NET: Registered protocol family 10
[    5.365839] NET: Registered protocol family 17
[    5.365859] Registering the dns_resolver key type
[    5.365879] Using IPI No-Shortcut mode
[    5.365963] PM: Hibernation image not present or could not be loaded.
[    5.365974] registered taskstats version 1
[    5.376378]   Magic number: 4:12:608
[    5.376499] rtc_cmos 00:09: setting system clock to 2012-07-19 00:36:54 UTC (1342658214)
[    5.376517] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.376518] EDD information not available.
[    5.391472] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.712462] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    5.795380] ACPI: Battery Slot [BAT0] (battery present)
[    6.040132] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.040151] ata3.01: SATA link down (SStatus 0 SControl 300)
[    6.048429] ata3.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
[    6.048432] ata3.00: 234441648 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    6.064418] ata3.00: configured for UDMA/100
[    6.064538] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    6.064684] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.064753] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    6.064805] sd 2:0:0:0: [sda] Write Protect is off
[    6.064808] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.064831] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.503253]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    6.503611] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.732055] ata4.01: failed to resume link (SControl 0)
[    6.743250] ata4.00: SATA link down (SStatus 0 SControl 300)
[    6.743270] ata4.01: SATA link down (SStatus 0 SControl 0)
[    6.743328] Freeing unused kernel memory: 696k freed
[    6.743611] Write protecting the kernel text: 5332k
[    6.743641] Write protecting the kernel read-only data: 2188k
[    6.764474] udevd[86]: starting version 173
[    6.960334] tg3.c:v3.119 (May 18, 2011)
[    6.960393] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.960405] tg3 0000:02:00.0: setting latency timer to 64
[    6.983726] sdhci: Secure Digital Host Controller Interface driver
[    6.983729] sdhci: Copyright(c) Pierre Ossman
[    6.983983] sdhci-pci 0000:0f:06.3: SDHCI controller found [104c:803c] (rev 0)
[    6.984033] sdhci-pci 0000:0f:06.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.008283] mmc0: no vmmc regulator found
[    7.008447] Registered led device: mmc0::
[    7.008500] mmc0: SDHCI controller on PCI [0000:0f:06.3] using PIO
[    7.023550] firewire_ohci 0000:0f:06.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.025992] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95787m) rev b002] (PCI Express) MAC address 00:1d:72:28:df:b9
[    7.025997] tg3 0000:02:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    7.026001] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    7.026004] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    7.079138] firewire_ohci: Added fw-ohci device 0000:0f:06.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    7.576134] firewire_core: created device fw0: GUID 001d72ffff28dfb9, S400
[    7.671542] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   19.348047] udevd[304]: starting version 173
[   19.385177] lp: driver loaded but no devices found
[   19.456547] Adding 1037308k swap on /dev/sda6.  Priority:-1 extents:1 across:1037308k 
[   19.571475] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   19.676129] wmi: Mapper loaded
[   19.769493] type=1400 audit(1342647428.889:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=486 comm="apparmor_parser"
[   19.769975] type=1400 audit(1342647428.889:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=486 comm="apparmor_parser"
[   19.770268] type=1400 audit(1342647428.889:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=486 comm="apparmor_parser"
[   20.052273] [drm] Initialized drm 1.1.0 20060810
[   20.164232] irda_init()
[   20.164248] NET: Registered protocol family 23
[   20.195588] lib80211: common routines for IEEE802.11 drivers
[   20.195593] lib80211_crypt: registered algorithm 'NULL'
[   20.203252] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.203257] Disabling lock debugging due to kernel taint
[   20.221115] tg3 0000:02:00.0: irq 43 for MSI/MSI-X
[   20.255613] nsc-ircc 00:0a: [io  0x02f8-0x02ff]
[   20.255734] nsc-ircc 00:0a: [irq 3]
[   20.255738] nsc-ircc 00:0a: [dma 3]
[   20.262770] nsc-ircc 00:0a: activated
[   20.262777] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   20.264410] nsc-ircc, chip->init
[   20.264426] nsc-ircc, Found chip at base=0x02e
[   20.265034] nsc-ircc, driver loaded (Dag Brattli)
[   20.301337] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.339067] IrDA: Registered device irda0
[   20.339132] nsc-ircc, Found dongle: Supports SIR Mode only
[   20.343890] nsc-ircc, chip->init
[   20.343906] nsc-ircc, Found chip at base=0x02e
[   20.343948] nsc-ircc, driver loaded (Dag Brattli)
[   20.343959] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.345509] yenta_cardbus 0000:0f:06.0: CardBus bridge found [1025:011f]
[   20.345534] yenta_cardbus 0000:0f:06.0: Using CSCINT to route CSC interrupts to PCI
[   20.345537] yenta_cardbus 0000:0f:06.0: Routing CardBus interrupts to PCI
[   20.345544] yenta_cardbus 0000:0f:06.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   20.365733] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.365740] i915 0000:00:02.0: setting latency timer to 64
[   20.446666] type=1400 audit(1342647429.565:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=599 comm="apparmor_parser"
[   20.458733] type=1400 audit(1342647429.577:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=600 comm="apparmor_parser"
[   20.464542] type=1400 audit(1342647429.585:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
[   20.464839] type=1400 audit(1342647429.585:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
[   20.479481] type=1400 audit(1342647429.597:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=601 comm="apparmor_parser"
[   20.502638] type=1400 audit(1342647429.621:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=601 comm="apparmor_parser"
[   20.521151] type=1400 audit(1342647429.641:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=601 comm="apparmor_parser"
[   20.577028] yenta_cardbus 0000:0f:06.0: ISA IRQ mask 0x0cf0, PCI irq 22
[   20.577033] yenta_cardbus 0000:0f:06.0: Socket status: 30000006
[   20.577038] pci_bus 0000:0f: Raising subordinate bus# of parent bus (#0f) from #10 to #13
[   20.577049] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   20.577053] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: excluding 0x5000-0x50ff 0x5400-0x54ff
[   20.588919] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.588929] wl 0000:04:00.0: setting latency timer to 64
[   20.591381] malloc in abgphy done
[   20.591515] eth%d: 5.100.82.38 driver failed with code 21
[   20.757122] init: apport pre-start process (655) terminated with status 1
[   20.759656] init: alsa-restore main process (660) terminated with status 19
[   20.795751] init: apport post-stop process (684) terminated with status 1
[   20.844491] 
[   20.844498] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge window: [mem 0xfc200000-0xfc2fffff]
[   20.844503] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc200000-0xfc2fffff: excluding 0xfc200000-0xfc20ffff
[   20.844516] yenta_cardbus 0000:0f:06.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   20.844519] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   20.853295] Linux video capture interface: v2.00
[   20.862633] tifm_7xx1 0000:0f:06.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.931495] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   20.931503] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   20.931505] [drm] Driver supports precise vblank timestamp query.
[   20.931554] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   20.960357] uvcvideo: Found UVC 1.00 device Microsoft LifeCam-VX700  v2.0 (045e:0770)
[   20.972267] input: Microsoft LifeCam-VX700  v2.0 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input4
[   20.972442] usbcore: registered new interface driver uvcvideo
[   20.972445] USB Video Class driver (v1.1.0)
[   21.152543] fixme: max PWM is zero.
[   21.160345] Bluetooth: Core ver 2.16
[   21.160407] NET: Registered protocol family 31
[   21.160409] Bluetooth: HCI device and connection manager initialized
[   21.160412] Bluetooth: HCI socket layer initialized
[   21.160414] Bluetooth: L2CAP socket layer initialized
[   21.164429] Bluetooth: SCO socket layer initialized
[   21.173026] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.173030] Bluetooth: BNEP filters: protocol multicast
[   21.282154] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04711/0xa04000/0x0
[   21.336284] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
[   21.368550] 2:3:1: cannot get freq at ep 0x84
[   21.369743] usbcore: registered new interface driver snd-usb-audio
[   21.602028] [drm] initialized overlay support
[   21.713270] acer_wmi: Acer Laptop ACPI-WMI Extras
[   21.736082] acer_wmi: Brightness must be controlled by generic video driver
[   21.832787] fbcon: inteldrmfb (fb0) is primary device
[   21.833883] Console: switching to colour frame buffer device 160x50
[   21.833918] fb0: inteldrmfb frame buffer device
[   21.833920] drm: registered panic notifier
[   21.858398] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
[   21.860733] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   21.862028] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   21.863953] acpi device:04: registered as cooling_device1
[   21.865783] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   21.866465] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.866642] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   21.866732] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   21.866824] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   21.866860] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.962121]  clean.
[   21.962217] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   21.963044] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   21.963101] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   21.963154] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   21.963210] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   21.975849] hda_codec: ALC268: BIOS auto-probing.
[   21.976391]  clean.
[   22.001698] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   22.593784] ppdev: user-space parallel port driver
[   22.958255] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   25.400289] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[  141.325978] audit_printk_skb: 21 callbacks suppressed
[  141.325982] type=1400 audit(1342647550.445:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1848 comm="apparmor_parser"
[  141.329243] type=1400 audit(1342647550.449:20): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1849 comm="apparmor_parser"
[  141.329748] type=1400 audit(1342647550.449:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1849 comm="apparmor_parser"
[  141.330184] type=1400 audit(1342647550.449:22): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1849 comm="apparmor_parser"
[  141.339591] type=1400 audit(1342647550.457:23): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=1850 comm="apparmor_parser"
[  141.346712] type=1400 audit(1342647550.465:24): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=1850 comm="apparmor_parser"
[  141.350858] type=1400 audit(1342647550.469:25): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=1850 comm="apparmor_parser"
[  141.357739] type=1400 audit(1342647550.477:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=1852 comm="apparmor_parser"
[  141.358260] type=1400 audit(1342647550.477:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=1852 comm="apparmor_parser"
[  141.366983] type=1400 audit(1342647550.485:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1853 comm="apparmor_parser"
[  141.443834] init: apport pre-start process (1877) terminated with status 1
[  141.445425] init: alsa-restore main process (1881) terminated with status 99
[  141.466087] init: apport post-stop process (1894) terminated with status 1
[  141.601834] Bluetooth: RFCOMM TTY layer initialized
[  141.601841] Bluetooth: RFCOMM socket layer initialized
[  141.601843] Bluetooth: RFCOMM ver 1.11
[  141.786733] init: plymouth-stop pre-start process (1977) terminated with status 1
[  186.706311] show_signal_msg: 6 callbacks suppressed
[  186.706317] gvfsd-metadata[1430]: segfault at 8 ip 0804c7ca sp bf988880 error 4 in gvfsd-metadata[8048000+d000]
[  314.700385] gvfsd-metadata[2008]: segfault at 8 ip 0804c7ca sp bf8297f0 error 4 in gvfsd-metadata[8048000+d000]
[  376.689416] gvfsd-metadata[2040]: segfault at 8 ip 0804c7ca sp bfc23250 error 4 in gvfsd-metadata[8048000+d000]
[  479.748094] gvfsd-metadata[2385]: segfault at 8 ip 0804c7ca sp bff4db40 error 4 in gvfsd-metadata[8048000+d000]
[  540.692089] gvfsd-metadata[2461]: segfault at 8 ip 0804c7ca sp bf9cb320 error 4 in gvfsd-metadata[8048000+d000]

```


```
Module                  Size  Used by
rfcomm                 38408  0 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_intel          24262  0 
snd_usb_audio         100880  0 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                80468  3 snd_hda_intel,snd_usb_audio,snd_hda_codec
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24558  1 snd_usb_audio
uvcvideo               67271  0 
snd_seq_midi           13132  0 
pcmcia                 39822  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2646601  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
tifm_7xx1              12937  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
i915                  505108  3 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  11 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
nsc_ircc               23240  0 
lib80211               14570  1 wl
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
irda                  185428  1 nsc_ircc
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
crc_ccitt              12595  1 irda
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
tg3                   132972  0 

```

lspci dint have anything in it:/ pid=1853 comm=

---

### Post by NikTh on 2012-07-18
Ok ,
2 more commands , with the same way 
```
lspci -nnk > lspci.txt
lsusb > lsusb.txt
```
**Question:** Why you didn't install Ubuntu 12.04 LTS and you installed Ubuntu 11.10 ? 
Maybe newer version of ubuntu supports (out of the box) your wireless.
Thanks

---

### Post by sutibun on 2012-07-18
LSUSB```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0770 Microsoft Corp. 

```

LSPCI```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
	Subsystem: Acer Incorporated [ALI] Realtek ALC268 audio codec [1025:011f]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel modules: iTCO_wdt
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel modules: i2c-i801
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:011c]
	Kernel driver in use: tg3
	Kernel modules: tg3
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
	Kernel modules: wl, ssb
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
	Subsystem: Acer Incorporated [ALI] Device [1025:011f]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```


you are a greek too? :p 
to answer your question my friend i took the cd of ubuntu 11.10 from a friend couple of months ago if i am correct and i thought if i will fix the wireless problem i can upgrade it later to the newest version :) am i right?i can do this right? what you mean out of the box?

---

### Post by NikTh on 2012-07-18
Hi , 
ok this is your wireless card 
> **sutibun said:**
> 
```
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel modules: wl, ssb
```
I cannot see any driver in use. 
You can try few thinks from Ubuntu , without be necessary to have Internet connection. 

Open a terminal (ctrl+alt+t) and write 
```
sudo modprobe -r ssb
sudo modprobe wl
```wait few seconds and see if WiFi enabled. 
> **sutibun said:**
> you are a greek too? :p  
If you are a Greek , check my signature about GR Ubuntu Forums. 

> **sutibun said:**
> to answer your question my friend i took the cd of ubuntu 11.10 from a friend couple of months ago if i am correct and i thought if i will fix the wireless problem i can upgrade it later to the newest version :) am i right?i can do this right? what you mean out of the box?
By out of the box , i mean , maybe your wireless will work without to do anything or without to install anything. 
After all Ubuntu 12.04 LTS its a Long Term Support version. More stable (will be) and has support for 5 years. 
So you can download (from windows) the Ubuntu 12.04 LTS .iso image and burn it to Usb. Check a how to , here in **Greek Language** -> [http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=3899&http#p37282](http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=3899&http#p37282) , and boot from this Usb and "Try Ubuntu" , check if wireless works.
Thanks

---

### Post by sutibun on 2012-07-18
ok i installed ubunt 12.04 and i made it the only os in my pc. the card still is not active tho :/ i followed your steps

---

### Post by NikTh on 2012-07-19
> **sutibun said:**
> ok i installed ubunt 12.04 and i made it the only os in my pc. the card still is not active tho :/ i followed your steps

Do you have internet ? (ethernet) 
I think you must remove 1 package (if its installed) and install another one. 
You must open a terminal and run these 2 commands 
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```but you must have internet. 
I am not sure , but i believe that your wireless will enabled after you run 2 above commands.
Thanks

---

### Post by westie457 on 2012-07-19
Hi just adding to what NikTh has already suggested.

After those last 2 commands if wireless does not come to life ```
sudo modprobe b43
``` in a terminal should give it a kick.

Or you could just reboot and that should work as well.

@NikTh hope you do not mind the intrusion, only trying to help.

---

### Post by sutibun on 2012-07-19
> **NikTh said:**
> Do you have internet ? (ethernet) 
I think you must remove 1 package (if its installed) and install another one. 
You must open a terminal and run these 2 commands 
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```but you must have internet. 
I am not sure , but i believe that your wireless will enabled after you run 2 above commands.
Thanks

Hi. Thank you my friend for all of your help. I found out a way get internet only for a while and hit those commands i found from a person having the exact same problem with me with the exact same wireless card and it worked :) the commands you told me are the commands i used (if i remember correctly there was something more) and the internet now works fine :)

Thanks again!:)

---

### Post by NikTh on 2012-07-19
Glad you fixed it. 
Please mark this **thread as solved** from **thread tools** . 
Thanks

---

