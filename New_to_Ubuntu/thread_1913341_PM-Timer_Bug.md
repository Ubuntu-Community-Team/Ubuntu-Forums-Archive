---
title: "PM-Timer Bug"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by deadlytackler on 2012-01-22
I am getting problem logging in to my machine. Its Intel(R) Pentium(R) 4 CPU 2.40 GHz, using Ubuntu 10.04 (Lucid), Kernel Linux 2.6.32-37-generic,
GNOME 2.30.2.
After many restarts logged on to system this is extract from log files:-
"[B] Jan 22 19:36:53 deadlytackler kernel: [    0.142315] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jan 22 19:36:53 deadlytackler kernel: [    0.142318] * this clock source is slow. If you are sure your timer does not have
Jan 22 19:36:53 deadlytackler kernel: [    0.142319] * this bug, please use "acpi_pm_good" to disable the workaround"[/B]

---

### Post by deadlytackler on 2012-01-22
Here is the complete Log:-

```

Jan 22 19:36:53 deadlytackler kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 22 19:36:53 deadlytackler rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="652" x-info="http://www.rsyslog.com"] (re)start
Jan 22 19:36:53 deadlytackler rsyslogd: rsyslogd's groupid changed to 103
Jan 22 19:36:53 deadlytackler rsyslogd: rsyslogd's userid changed to 101
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Linux version 2.6.32-37-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 (Ubuntu 2.6.32-37.81-generic 2.6.32.49+drm33.21)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] KERNEL supported cpus:
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   Intel GenuineIntel
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   AMD AuthenticAMD
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   NSC Geode by NSC
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   Cyrix CyrixInstead
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   Centaur CentaurHauls
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   Transmeta GenuineTMx86
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   Transmeta TransmetaCPU
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   UMC UMC UMC UMC
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7f0000 (usable)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 000000002f7f0000 - 000000002f7f3000 (ACPI NVS)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 000000002f7f3000 - 000000002f800000 (ACPI data)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] DMI 2.2 present.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] last_pfn = 0x2f7f0 max_arch_pfn = 0x100000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] modified physical RAM map:
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 0000000000100000 - 000000002f7f0000 (usable)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 000000002f7f0000 - 000000002f7f3000 (ACPI NVS)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 000000002f7f3000 - 000000002f800000 (ACPI data)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000002f7f0000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] RAMDISK: 23293000 - 23a33509
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: RSDP 000f6cd0 00014 (v00 IntelR)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: RSDT 2f7f3000 0002C (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: FACP 2f7f3040 00074 (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: DSDT 2f7f30c0 03C4A (v01 INTELR AWRDACPI 00001000 MSFT 0100000C)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: FACS 2f7f0000 00040
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: APIC 2f7f6d40 00054 (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] 0MB HIGHMEM available.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] 759MB LOWMEM available.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   mapped low ram: 0 - 2f7f0000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   low ram: 0 - 2f7f0000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   node 0 low ram: 00000000 - 2f7f0000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   node 0 bootmap 00011000 - 00016f00
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002f7f0000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #3 [0000100000 - 00008e0f18]    TEXT DATA BSS ==> [0000100000 - 00008e0f18]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #4 [0023293000 - 0023a33509]          RAMDISK ==> [0023293000 - 0023a33509]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #6 [00008e1000 - 00008e4072]              BRK ==> [00008e1000 - 00008e4072]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   #8 [0000011000 - 0000017000]          BOOTMAP ==> [0000011000 - 0000017000]
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] found SMP MP-table at [c00f5350] f5350
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Zone PFN ranges:
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   Normal   0x00001000 -> 0x0002f7f0
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]   HighMem  0x0002f7f0 -> 0x0002f7f0
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Movable zone start PFN for each node
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]     0: 0x00000100 -> 0x0002f7f0
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Using APIC driver default
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Allocating PCI resources starting at 2f800000 (gap: 2f800000:cf400000)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36312 r0 d21032 u4194304
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] pcpu-alloc: s36312 r0 d21032 u4194304 alloc=1*4194304
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] pcpu-alloc: [0] 0 
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192911
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-37-generic root=UUID=9191a08d-5473-43ee-99d8-dd64bdefed9e ro quiet splash
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Initializing CPU#0
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] allocated 3890560 bytes of page_cgroup
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Memory: 750740k/778176k available (4680k kernel code, 26668k reserved, 2122k data, 668k init, 0k highmem)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] virtual kernel memory layout:
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]     vmalloc : 0xefff0000 - 0xff7fe000   ( 248 MB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xef7f0000   ( 759 MB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]       .data : 0xc0592207 - 0xc07a4dc8   (2122 kB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000]       .text : 0xc0100000 - 0xc0592207   (4680 kB)
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Hierarchical RCU implementation.
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Console: colour VGA+ 80x25
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] console [tty0] enabled
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Fast TSC calibration using PIT
Jan 22 19:36:53 deadlytackler kernel: [    0.000000] Detected 2393.724 MHz processor.
Jan 22 19:36:53 deadlytackler kernel: [    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.44 BogoMIPS (lpj=9574896)
Jan 22 19:36:53 deadlytackler kernel: [    0.004037] Security Framework initialized
Jan 22 19:36:53 deadlytackler kernel: [    0.004069] AppArmor: AppArmor initialized
Jan 22 19:36:53 deadlytackler kernel: [    0.004083] Mount-cache hash table entries: 512
Jan 22 19:36:53 deadlytackler kernel: [    0.004275] Initializing cgroup subsys ns
Jan 22 19:36:53 deadlytackler kernel: [    0.004282] Initializing cgroup subsys cpuacct
Jan 22 19:36:53 deadlytackler kernel: [    0.004288] Initializing cgroup subsys memory
Jan 22 19:36:53 deadlytackler kernel: [    0.004302] Initializing cgroup subsys devices
Jan 22 19:36:53 deadlytackler kernel: [    0.004306] Initializing cgroup subsys freezer
Jan 22 19:36:53 deadlytackler kernel: [    0.004310] Initializing cgroup subsys net_cls
Jan 22 19:36:53 deadlytackler kernel: [    0.004349] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jan 22 19:36:53 deadlytackler kernel: [    0.004355] CPU: L2 cache: 1024K
Jan 22 19:36:53 deadlytackler kernel: [    0.004359] CPU: Hyper-Threading is disabled
Jan 22 19:36:53 deadlytackler kernel: [    0.004364] mce: CPU supports 4 MCE banks
Jan 22 19:36:53 deadlytackler kernel: [    0.004372] Disabling lock debugging due to kernel taint
Jan 22 19:36:53 deadlytackler kernel: [    0.004387] CPU0: Thermal monitoring enabled (TM1)
Jan 22 19:36:53 deadlytackler kernel: [    0.004395] using mwait in idle threads.
Jan 22 19:36:53 deadlytackler kernel: [    0.004404] Performance Events: no PMU driver, software events only.
Jan 22 19:36:53 deadlytackler kernel: [    0.004415] Checking 'hlt' instruction... OK.
Jan 22 19:36:53 deadlytackler kernel: [    0.021400] SMP alternatives: switching to UP code
Jan 22 19:36:53 deadlytackler kernel: [    0.037000] Freeing SMP alternatives: 19k freed
Jan 22 19:36:53 deadlytackler kernel: [    0.037032] ACPI: Core revision 20090903
Jan 22 19:36:53 deadlytackler kernel: [    0.048015] ftrace: converting mcount calls to 0f 1f 44 00 00
Jan 22 19:36:53 deadlytackler kernel: [    0.048025] ftrace: allocating 21734 entries in 43 pages
Jan 22 19:36:53 deadlytackler kernel: [    0.056108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 22 19:36:53 deadlytackler kernel: [    0.056417] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 22 19:36:53 deadlytackler kernel: [    0.096104] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 01
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] Brought up 1 CPUs
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] Total of 1 processors activated (4787.44 BogoMIPS).
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] devtmpfs: initialized
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] regulator: core version 0.5
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] Time: 14:06:35  Date: 01/22/12
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] NET: Registered protocol family 16
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] EISA bus registered
Jan 22 19:36:53 deadlytackler kernel: [    0.100001] ACPI: bus type pci registered
Jan 22 19:36:53 deadlytackler kernel: [    0.126745] PCI: PCI BIOS revision 2.10 entry at 0xfb4c0, last bus=1
Jan 22 19:36:53 deadlytackler kernel: [    0.126749] PCI: Using configuration type 1 for base access
Jan 22 19:36:53 deadlytackler kernel: [    0.128163] bio: create slab <bio-0> at 0
Jan 22 19:36:53 deadlytackler kernel: [    0.135657] ACPI: Interpreter enabled
Jan 22 19:36:53 deadlytackler kernel: [    0.135663] ACPI: (supports S0 S1 S4 S5)
Jan 22 19:36:53 deadlytackler kernel: [    0.135701] ACPI: Using IOAPIC for interrupt routing
Jan 22 19:36:53 deadlytackler kernel: [    0.141534] ACPI: No dock devices found.
Jan 22 19:36:53 deadlytackler kernel: [    0.141685] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 22 19:36:53 deadlytackler kernel: [    0.142246] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 22 19:36:53 deadlytackler kernel: [    0.142253] pci 0000:00:1d.7: PME# disabled
Jan 22 19:36:53 deadlytackler kernel: [    0.142315] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jan 22 19:36:53 deadlytackler kernel: [    0.142318] * this clock source is slow. If you are sure your timer does not have
Jan 22 19:36:53 deadlytackler kernel: [    0.142319] * this bug, please use "acpi_pm_good" to disable the workaround
Jan 22 19:36:53 deadlytackler kernel: [    0.142636] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jan 22 19:36:53 deadlytackler kernel: [    0.142642] pci 0000:00:1f.5: PME# disabled
Jan 22 19:36:53 deadlytackler kernel: [    0.142769] pci 0000:01:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 22 19:36:53 deadlytackler kernel: [    0.142775] pci 0000:01:06.0: PME# disabled
Jan 22 19:36:53 deadlytackler kernel: [    0.142817] pci 0000:00:1e.0: transparent bridge
Jan 22 19:36:53 deadlytackler kernel: [    0.151663] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jan 22 19:36:53 deadlytackler kernel: [    0.151822] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Jan 22 19:36:53 deadlytackler kernel: [    0.151979] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jan 22 19:36:53 deadlytackler kernel: [    0.152149] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jan 22 19:36:53 deadlytackler kernel: [    0.152306] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jan 22 19:36:53 deadlytackler kernel: [    0.152462] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jan 22 19:36:53 deadlytackler kernel: [    0.152619] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jan 22 19:36:53 deadlytackler kernel: [    0.152781] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jan 22 19:36:53 deadlytackler kernel: [    0.152946] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan 22 19:36:53 deadlytackler kernel: [    0.152956] vgaarb: loaded
Jan 22 19:36:53 deadlytackler kernel: [    0.153165] SCSI subsystem initialized
Jan 22 19:36:53 deadlytackler kernel: [    0.153359] usbcore: registered new interface driver usbfs
Jan 22 19:36:53 deadlytackler kernel: [    0.153382] usbcore: registered new interface driver hub
Jan 22 19:36:53 deadlytackler kernel: [    0.153426] usbcore: registered new device driver usb
Jan 22 19:36:53 deadlytackler kernel: [    0.153618] ACPI: WMI: Mapper loaded
Jan 22 19:36:53 deadlytackler kernel: [    0.153621] PCI: Using ACPI for IRQ routing
Jan 22 19:36:53 deadlytackler kernel: [    0.153809] NetLabel: Initializing
Jan 22 19:36:53 deadlytackler kernel: [    0.153813] NetLabel:  domain hash size = 128
Jan 22 19:36:53 deadlytackler kernel: [    0.153816] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 22 19:36:53 deadlytackler kernel: [    0.153838] NetLabel:  unlabeled traffic allowed by default
Jan 22 19:36:53 deadlytackler kernel: [    0.153895] Switching to clocksource tsc
Jan 22 19:36:53 deadlytackler kernel: [    0.155999] AppArmor: AppArmor Filesystem Enabled
Jan 22 19:36:53 deadlytackler kernel: [    0.155999] pnp: PnP ACPI init
Jan 22 19:36:53 deadlytackler kernel: [    0.155999] ACPI: bus type pnp registered
Jan 22 19:36:53 deadlytackler kernel: [    0.159086] pnp: PnP ACPI: found 14 devices
Jan 22 19:36:53 deadlytackler kernel: [    0.159090] ACPI: ACPI bus type pnp unregistered
Jan 22 19:36:53 deadlytackler kernel: [    0.159098] PnPBIOS: Disabled by ACPI PNP
Jan 22 19:36:53 deadlytackler kernel: [    0.159116] system 00:01: ioport range 0xb78-0xb7b has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159121] system 00:01: ioport range 0xf78-0xf7b has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159127] system 00:01: ioport range 0xa78-0xa7b has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159132] system 00:01: ioport range 0xe78-0xe7b has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159136] system 00:01: ioport range 0xbbc-0xbbf has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159143] system 00:01: ioport range 0xfbc-0xfbf has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159147] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159153] system 00:01: ioport range 0x294-0x297 has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159158] system 00:01: ioport range 0x800-0x805 has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.159178] system 00:0b: ioport range 0x400-0x4bf has been reserved
Jan 22 19:36:53 deadlytackler kernel: [    0.194028] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Jan 22 19:36:53 deadlytackler kernel: [    0.194034] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Jan 22 19:36:53 deadlytackler kernel: [    0.194041] pci 0000:00:1e.0:   MEM window: 0xe0000000-0xe1ffffff
Jan 22 19:36:53 deadlytackler kernel: [    0.194070] pci 0000:00:1e.0:   PREFETCH window: 0x30000000-0x300fffff
Jan 22 19:36:53 deadlytackler kernel: [    0.194183] NET: Registered protocol family 2
Jan 22 19:36:53 deadlytackler kernel: [    0.194333] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.194930] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.196100] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.197016] TCP: Hash tables configured (established 131072 bind 65536)
Jan 22 19:36:53 deadlytackler kernel: [    0.197021] TCP reno registered
Jan 22 19:36:53 deadlytackler kernel: [    0.197253] NET: Registered protocol family 1
Jan 22 19:36:53 deadlytackler kernel: [    0.197787] cpufreq-nforce2: No nForce2 chipset.
Jan 22 19:36:53 deadlytackler kernel: [    0.197837] Scanning for low memory corruption every 60 seconds
Jan 22 19:36:53 deadlytackler kernel: [    0.197997] audit: initializing netlink socket (disabled)
Jan 22 19:36:53 deadlytackler kernel: [    0.198018] type=2000 audit(1327241194.194:1): initialized
Jan 22 19:36:53 deadlytackler kernel: [    0.209300] Trying to unpack rootfs image as initramfs...
Jan 22 19:36:53 deadlytackler kernel: [    0.222677] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 22 19:36:53 deadlytackler kernel: [    0.230333] VFS: Disk quotas dquot_6.5.2
Jan 22 19:36:53 deadlytackler kernel: [    0.230447] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 22 19:36:53 deadlytackler kernel: [    0.231392] fuse init (API version 7.13)
Jan 22 19:36:53 deadlytackler kernel: [    0.231527] msgmni has been set to 1466
Jan 22 19:36:53 deadlytackler kernel: [    0.231858] alg: No test for stdrng (krng)
Jan 22 19:36:53 deadlytackler kernel: [    0.231948] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan 22 19:36:53 deadlytackler kernel: [    0.231954] io scheduler noop registered
Jan 22 19:36:53 deadlytackler kernel: [    0.231958] io scheduler anticipatory registered
Jan 22 19:36:53 deadlytackler kernel: [    0.231961] io scheduler deadline registered
Jan 22 19:36:53 deadlytackler kernel: [    0.232026] io scheduler cfq registered (default)
Jan 22 19:36:53 deadlytackler kernel: [    0.232189] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 22 19:36:53 deadlytackler kernel: [    0.232228] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 22 19:36:53 deadlytackler kernel: [    0.232380] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jan 22 19:36:53 deadlytackler kernel: [    0.232387] ACPI: Power Button [PWRB]
Jan 22 19:36:53 deadlytackler kernel: [    0.232466] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Jan 22 19:36:53 deadlytackler kernel: [    0.232478] ACPI: Sleep Button [SLPB]
Jan 22 19:36:53 deadlytackler kernel: [    0.232556] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 22 19:36:53 deadlytackler kernel: [    0.232560] ACPI: Power Button [PWRF]
Jan 22 19:36:53 deadlytackler kernel: [    0.232634] fan PNP0C0B:00: registered as cooling_device0
Jan 22 19:36:53 deadlytackler kernel: [    0.232643] ACPI: Fan [FAN] (on)
Jan 22 19:36:53 deadlytackler kernel: [    0.232966] processor LNXCPU:00: registered as cooling_device1
Jan 22 19:36:53 deadlytackler kernel: [    0.236450] thermal LNXTHERM:01: registered as thermal_zone0
Jan 22 19:36:53 deadlytackler kernel: [    0.236462] ACPI: Thermal Zone [THRM] (59 C)
Jan 22 19:36:53 deadlytackler kernel: [    0.242551] isapnp: Scanning for PnP cards...
Jan 22 19:36:53 deadlytackler kernel: [    0.250438] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jan 22 19:36:53 deadlytackler kernel: [    0.250562] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 22 19:36:53 deadlytackler kernel: [    0.251062] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 22 19:36:53 deadlytackler kernel: [    0.252726] brd: module loaded
Jan 22 19:36:53 deadlytackler kernel: [    0.253437] loop: module loaded
Jan 22 19:36:53 deadlytackler kernel: [    0.253573] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Jan 22 19:36:53 deadlytackler kernel: [    0.253776] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 22 19:36:53 deadlytackler kernel: [    0.302276] scsi0 : ata_piix
Jan 22 19:36:53 deadlytackler kernel: [    0.302450] scsi1 : ata_piix
Jan 22 19:36:53 deadlytackler kernel: [    0.303770] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jan 22 19:36:53 deadlytackler kernel: [    0.303776] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jan 22 19:36:53 deadlytackler kernel: [    0.304369] Fixed MDIO Bus: probed
Jan 22 19:36:53 deadlytackler kernel: [    0.304427] PPP generic driver version 2.4.2
Jan 22 19:36:53 deadlytackler kernel: [    0.304536] tun: Universal TUN/TAP device driver, 1.6
Jan 22 19:36:53 deadlytackler kernel: [    0.304541] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 22 19:36:53 deadlytackler kernel: [    0.304702] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 22 19:36:53 deadlytackler kernel: [    0.304756] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jan 22 19:36:53 deadlytackler kernel: [    0.304791] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 22 19:36:53 deadlytackler kernel: [    0.304844] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan 22 19:36:53 deadlytackler kernel: [    0.314593] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe2080000
Jan 22 19:36:53 deadlytackler kernel: [    0.334246] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan 22 19:36:53 deadlytackler kernel: [    0.334494] usb usb1: configuration #1 chosen from 1 choice
Jan 22 19:36:53 deadlytackler kernel: [    0.334544] hub 1-0:1.0: USB hub found
Jan 22 19:36:53 deadlytackler kernel: [    0.334567] hub 1-0:1.0: 6 ports detected
Jan 22 19:36:53 deadlytackler kernel: [    0.334672] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 22 19:36:53 deadlytackler kernel: [    0.334701] uhci_hcd: USB Universal Host Controller Interface driver
Jan 22 19:36:53 deadlytackler kernel: [    0.334812] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 22 19:36:53 deadlytackler kernel: [    0.334832] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 22 19:36:53 deadlytackler kernel: [    0.334887] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan 22 19:36:53 deadlytackler kernel: [    0.334931] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Jan 22 19:36:53 deadlytackler kernel: [    0.335075] usb usb2: configuration #1 chosen from 1 choice
Jan 22 19:36:53 deadlytackler kernel: [    0.335117] hub 2-0:1.0: USB hub found
Jan 22 19:36:53 deadlytackler kernel: [    0.335130] hub 2-0:1.0: 2 ports detected
Jan 22 19:36:53 deadlytackler kernel: [    0.335211] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 22 19:36:53 deadlytackler kernel: [    0.335224] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 22 19:36:53 deadlytackler kernel: [    0.335271] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan 22 19:36:53 deadlytackler kernel: [    0.335305] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Jan 22 19:36:53 deadlytackler kernel: [    0.335451] usb usb3: configuration #1 chosen from 1 choice
Jan 22 19:36:53 deadlytackler kernel: [    0.335498] hub 3-0:1.0: USB hub found
Jan 22 19:36:53 deadlytackler kernel: [    0.335513] hub 3-0:1.0: 2 ports detected
Jan 22 19:36:53 deadlytackler kernel: [    0.335574] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 22 19:36:53 deadlytackler kernel: [    0.335589] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 22 19:36:53 deadlytackler kernel: [    0.335635] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan 22 19:36:53 deadlytackler kernel: [    0.335668] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Jan 22 19:36:53 deadlytackler kernel: [    0.335818] usb usb4: configuration #1 chosen from 1 choice
Jan 22 19:36:53 deadlytackler kernel: [    0.335865] hub 4-0:1.0: USB hub found
Jan 22 19:36:53 deadlytackler kernel: [    0.335879] hub 4-0:1.0: 2 ports detected
Jan 22 19:36:53 deadlytackler kernel: [    0.336026] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 22 19:36:53 deadlytackler kernel: [    0.342971] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 22 19:36:53 deadlytackler kernel: [    0.342985] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 22 19:36:53 deadlytackler kernel: [    0.343228] mice: PS/2 mouse device common for all mice
Jan 22 19:36:53 deadlytackler kernel: [    0.343447] rtc_cmos 00:03: RTC can wake from S4
Jan 22 19:36:53 deadlytackler kernel: [    0.343517] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jan 22 19:36:53 deadlytackler kernel: [    0.343542] rtc0: alarms up to one month, 242 bytes nvram
Jan 22 19:36:53 deadlytackler kernel: [    0.343738] device-mapper: uevent: version 1.0.3
Jan 22 19:36:53 deadlytackler kernel: [    0.343933] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jan 22 19:36:53 deadlytackler kernel: [    0.346575] device-mapper: multipath: version 1.1.0 loaded
Jan 22 19:36:53 deadlytackler kernel: [    0.346581] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan 22 19:36:53 deadlytackler kernel: [    0.346798] EISA: Probing bus 0 at eisa.0
Jan 22 19:36:53 deadlytackler kernel: [    0.346842] EISA: Detected 0 cards.
Jan 22 19:36:53 deadlytackler kernel: [    0.349039] cpuidle: using governor ladder
Jan 22 19:36:53 deadlytackler kernel: [    0.349044] cpuidle: using governor menu
Jan 22 19:36:53 deadlytackler kernel: [    0.349667] TCP cubic registered
Jan 22 19:36:53 deadlytackler kernel: [    0.349888] NET: Registered protocol family 10
Jan 22 19:36:53 deadlytackler kernel: [    0.351007] NET: Registered protocol family 17
Jan 22 19:36:53 deadlytackler kernel: [    0.351092] Using IPI No-Shortcut mode
Jan 22 19:36:53 deadlytackler kernel: [    0.351272] registered taskstats version 1
Jan 22 19:36:53 deadlytackler kernel: [    0.351488]   Magic number: 12:171:132
Jan 22 19:36:53 deadlytackler kernel: [    0.351574] acpi device:07: hash matches
Jan 22 19:36:53 deadlytackler kernel: [    0.351616] rtc_cmos 00:03: setting system clock to 2012-01-22 14:06:35 UTC (1327241195)
Jan 22 19:36:53 deadlytackler kernel: [    0.351621] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 22 19:36:53 deadlytackler kernel: [    0.351625] EDD information not available.
Jan 22 19:36:53 deadlytackler kernel: [    0.409669] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jan 22 19:36:53 deadlytackler kernel: [    0.503041] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
Jan 22 19:36:53 deadlytackler kernel: [    0.503049] ata1.00: 156301488 sectors, multi 16: LBA48 
Jan 22 19:36:53 deadlytackler kernel: [    0.510545] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.02, max UDMA/66
Jan 22 19:36:53 deadlytackler kernel: [    0.510605] ata2.01: ATAPI: HL-DT-ST GCE-8525B, 1.03, max UDMA/33
Jan 22 19:36:53 deadlytackler kernel: [    0.510646] ata2.00: limited to UDMA/33 due to 40-wire cable
Jan 22 19:36:53 deadlytackler kernel: [    0.518683] ata1.00: configured for UDMA/100
Jan 22 19:36:53 deadlytackler kernel: [    0.526592] ata2.00: configured for UDMA/33
Jan 22 19:36:53 deadlytackler kernel: [    0.534565] ata2.01: configured for UDMA/33
Jan 22 19:36:53 deadlytackler kernel: [    0.670203] usb 1-2: new high speed USB device using ehci_hcd and address 2
Jan 22 19:36:53 deadlytackler kernel: [    0.870054] usb 1-2: configuration #1 chosen from 1 choice
Jan 22 19:36:53 deadlytackler kernel: [    0.870848] hub 1-2:1.0: USB hub found
Jan 22 19:36:53 deadlytackler kernel: [    0.871543] hub 1-2:1.0: 4 ports detected
Jan 22 19:36:53 deadlytackler kernel: [    0.873710] Freeing initrd memory: 7809k freed
Jan 22 19:36:53 deadlytackler kernel: [    0.933173] isapnp: No Plug & Play device found
Jan 22 19:36:53 deadlytackler kernel: [    0.933600] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
Jan 22 19:36:53 deadlytackler kernel: [    0.933904] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 22 19:36:53 deadlytackler kernel: [    0.934181] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan 22 19:36:53 deadlytackler kernel: [    0.934265] sd 0:0:0:0: [sda] Write Protect is off
Jan 22 19:36:53 deadlytackler kernel: [    0.934313] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 22 19:36:53 deadlytackler kernel: [    0.934592]  sda:
Jan 22 19:36:53 deadlytackler kernel: [    0.935509] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.02 PQ: 0 ANSI: 5
Jan 22 19:36:53 deadlytackler kernel: [    0.939809] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 22 19:36:53 deadlytackler kernel: [    0.939815] Uniform CD-ROM driver Revision: 3.20
Jan 22 19:36:53 deadlytackler kernel: [    0.940025] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan 22 19:36:53 deadlytackler kernel: [    0.940366] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8525B  1.03 PQ: 0 ANSI: 5
Jan 22 19:36:53 deadlytackler kernel: [    0.943409] sr1: scsi3-mmc drive: 40x/52x writer cd/rw xa/form2 cdda tray
Jan 22 19:36:53 deadlytackler kernel: [    0.943586] sr 1:0:1:0: Attached scsi generic sg2 type 5
Jan 22 19:36:53 deadlytackler kernel: [    0.945990]  sda1 sda2 sda3 sda4 < sda5 >
Jan 22 19:36:53 deadlytackler kernel: [    0.979789] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 22 19:36:53 deadlytackler kernel: [    0.979815] Freeing unused kernel memory: 668k freed
Jan 22 19:36:53 deadlytackler kernel: [    0.980977] Write protecting the kernel text: 4684k
Jan 22 19:36:53 deadlytackler kernel: [    0.981014] Write protecting the kernel read-only data: 1844k
Jan 22 19:36:53 deadlytackler kernel: [    1.009919] udev: starting version 151
Jan 22 19:36:53 deadlytackler kernel: [    1.042290] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jan 22 19:36:53 deadlytackler kernel: [    1.205019] usb 1-4: configuration #1 chosen from 1 choice
Jan 22 19:36:53 deadlytackler kernel: [    1.293878] Floppy drive(s): fd0 is 1.44M
Jan 22 19:36:53 deadlytackler kernel: [    1.313997] FDC 0 is a post-1991 82077
Jan 22 19:36:53 deadlytackler kernel: [    1.337823] sis900.c: v1.08.10 Apr. 2 2006
Jan 22 19:36:53 deadlytackler kernel: [    1.337908] sis900 0000:01:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jan 22 19:36:53 deadlytackler kernel: [    1.339592] 0000:01:06.0: SiS 900 Internal MII PHY transceiver found at address 1.
Jan 22 19:36:53 deadlytackler kernel: [    1.352463] 0000:01:06.0: Using transceiver found at address 1 as default
Jan 22 19:36:53 deadlytackler kernel: [    1.602119] EXT4-fs (sda3): mounted filesystem with ordered data mode
Jan 22 19:36:53 deadlytackler kernel: [    2.977877] eth0: SiS 900 PCI Fast Ethernet at 0xc000, IRQ 21, 00:11:5b:57:01:bb
Jan 22 19:36:53 deadlytackler kernel: [   14.419139] udev: starting version 151
Jan 22 19:36:53 deadlytackler kernel: [   14.655466] Adding 1952760k swap on /dev/sda2.  Priority:-1 extents:1 across:1952760k 
Jan 22 19:36:53 deadlytackler kernel: [   14.781493] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 22 19:36:53 deadlytackler kernel: [   14.974564] Linux video capture interface: v2.00
Jan 22 19:36:53 deadlytackler kernel: [   15.053699] lp: driver loaded but no devices found
Jan 22 19:36:53 deadlytackler kernel: [   15.065156] Linux agpgart interface v0.103
Jan 22 19:36:53 deadlytackler kernel: [   15.089983] intel_rng: FWH not detected
Jan 22 19:36:53 deadlytackler kernel: [   15.133167] parport_pc 00:08: reported by Plug and Play ACPI
Jan 22 19:36:53 deadlytackler kernel: [   15.133276] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jan 22 19:36:53 deadlytackler kernel: [   15.197674] gspca: main v2.7.0 registered
Jan 22 19:36:53 deadlytackler kernel: [   15.197960] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Jan 22 19:36:53 deadlytackler kernel: [   15.198297] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
Jan 22 19:36:53 deadlytackler kernel: [   15.203357] type=1505 audit(1327241210.348:2):  operation="profile_load" pid=476 name="/sbin/dhclient3"
Jan 22 19:36:53 deadlytackler kernel: [   15.204330] type=1505 audit(1327241210.352:3):  operation="profile_load" pid=476 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan 22 19:36:53 deadlytackler kernel: [   15.204833] type=1505 audit(1327241210.352:4):  operation="profile_load" pid=476 name="/usr/lib/connman/scripts/dhclient-script"
Jan 22 19:36:53 deadlytackler kernel: [   15.208167] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Jan 22 19:36:53 deadlytackler kernel: [   15.228313] lp0: using parport0 (interrupt-driven).
Jan 22 19:36:53 deadlytackler kernel: [   15.237107] ppdev: user-space parallel port driver
Jan 22 19:36:53 deadlytackler kernel: [   15.443341] gspca: probing 0ac8:0323
Jan 22 19:36:53 deadlytackler kernel: [   15.443964] vc032x: check sensor header 20
Jan 22 19:36:53 deadlytackler kernel: [   15.444969] [drm] Initialized drm 1.1.0 20060810
Jan 22 19:36:53 deadlytackler kernel: [   15.448360] vc032x: Sensor ID 7673 (0)
Jan 22 19:36:53 deadlytackler kernel: [   15.448364] vc032x: Find Sensor OV7670
Jan 22 19:36:53 deadlytackler kernel: [   15.448654] gspca: probe ok
Jan 22 19:36:53 deadlytackler kernel: [   15.448691] usbcore: registered new interface driver vc032x
Jan 22 19:36:53 deadlytackler kernel: [   15.449612] vc032x: registered
Jan 22 19:36:53 deadlytackler kernel: [   15.752769] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jan 22 19:36:53 deadlytackler kernel: [   15.771766] [drm] i915 disabling kernel modesetting for known bad device.
Jan 22 19:36:53 deadlytackler kernel: [   15.771803] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 22 19:36:53 deadlytackler kernel: [   15.791741] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan 22 19:36:53 deadlytackler kernel: [   15.983240] vga16fb: mapped to 0xc00a0000
Jan 22 19:36:53 deadlytackler kernel: [   15.983468] fb0: VGA16 VGA frame buffer device
Jan 22 19:36:53 deadlytackler kernel: [   16.194007] Console: switching to colour frame buffer device 80x30
Jan 22 19:36:53 deadlytackler kernel: [   16.515926] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan 22 19:36:53 deadlytackler kernel: [   16.718583] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jan 22 19:36:53 deadlytackler kernel: [   16.840025] intel8x0_measure_ac97_clock: measured 54597 usecs (2630 samples)
Jan 22 19:36:53 deadlytackler kernel: [   16.840031] intel8x0: clocking to 48000
Jan 22 19:36:53 deadlytackler kernel: [   17.055565] EXT4-fs (sda5): mounted filesystem with ordered data mode
Jan 22 19:36:53 deadlytackler kernel: [   18.299805] type=1505 audit(1327241213.444:5):  operation="profile_load" pid=674 name="/usr/share/gdm/guest-session/Xsession"
Jan 22 19:36:53 deadlytackler kernel: [   18.304518] type=1505 audit(1327241213.452:6):  operation="profile_replace" pid=675 name="/sbin/dhclient3"
Jan 22 19:36:53 deadlytackler kernel: [   18.305481] type=1505 audit(1327241213.452:7):  operation="profile_replace" pid=675 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan 22 19:36:53 deadlytackler kernel: [   18.306006] type=1505 audit(1327241213.452:8):  operation="profile_replace" pid=675 name="/usr/lib/connman/scripts/dhclient-script"
Jan 22 19:36:53 deadlytackler kernel: [   18.325573] type=1505 audit(1327241213.472:9):  operation="profile_load" pid=676 name="/usr/bin/evince"
Jan 22 19:36:53 deadlytackler kernel: [   18.337811] type=1505 audit(1327241213.484:10):  operation="profile_load" pid=676 name="/usr/bin/evince-previewer"
Jan 22 19:36:53 deadlytackler kernel: [   18.345060] type=1505 audit(1327241213.492:11):  operation="profile_load" pid=676 name="/usr/bin/evince-thumbnailer"
Jan 22 19:36:55 deadlytackler kernel: [   20.576836] eth0: Media Link On 100mbps full-duplex 
Jan 22 19:37:02 deadlytackler pulseaudio[1018]: ratelimit.c: 5 events suppressed
Jan 22 19:37:04 deadlytackler kernel: [   29.218334] *pde = 1f7bc067 *pte = 00000000 
Jan 22 19:37:04 deadlytackler kernel: [   29.218353] Modules linked in: binfmt_misc snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi fbcon tileblit font snd_rawmidi snd_seq_midi_event bitblit softcursor snd_seq vga16fb vgastate snd_timer snd_seq_device i915 drm_kms_helper gspca_vc032x drm i2c_algo_bit snd video ppdev gspca_main intel_agp soundcore parport_pc snd_page_alloc output psmouse agpgart videodev v4l1_compat shpchp serio_raw lp parport sis900 mii floppy
Jan 22 19:37:04 deadlytackler kernel: [   29.218408] 
Jan 22 19:37:04 deadlytackler kernel: [   29.218415] Pid: 1123, comm: udev-acl.ck Tainted: G   M       (2.6.32-37-generic #81-Ubuntu)  
Jan 22 19:37:04 deadlytackler kernel: [   29.218420] EIP: 0060:[<c03e79fd>] EFLAGS: 00010202 CPU: 0
Jan 22 19:37:04 deadlytackler kernel: [   29.218426] EIP is at show_uevent+0x2d/0x100
Jan 22 19:37:04 deadlytackler kernel: [   29.218430] EAX: 00000001 EBX: c078a440 ECX: eb857000 EDX: c078a440
Jan 22 19:37:04 deadlytackler kernel: [   29.218435] ESI: ef003010 EDI: e00497a8 EBP: e0843f0c ESP: e0843ee8
Jan 22 19:37:04 deadlytackler kernel: [   29.218439]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 22 19:37:04 deadlytackler kernel: [   29.218452]  c079ad00 00000000 00000000 000080d0 eb857000 c079ad00 c078a440 fffffffb
Jan 22 19:37:04 deadlytackler kernel: [   29.218463] <0> c03e79d0 e0843f20 c03e6f39 df667900 e0baba50 c078a454 e0843f3c c0260772
Jan 22 19:37:04 deadlytackler kernel: [   29.218473] <0> df623a80 e00497a8 df667900 e0843f98 df623a80 e0843f64 c026085a b7721000
Jan 22 19:37:04 deadlytackler kernel: [   29.218494]  [<c03e79d0>] ? show_uevent+0x0/0x100
Jan 22 19:37:04 deadlytackler kernel: [   29.218499]  [<c03e6f39>] ? dev_attr_show+0x29/0x50
Jan 22 19:37:04 deadlytackler kernel: [   29.218507]  [<c0260772>] ? fill_read_buffer+0x52/0xc0
Jan 22 19:37:04 deadlytackler kernel: [   29.218514]  [<c026085a>] ? sysfs_read_file+0x7a/0x90
Jan 22 19:37:04 deadlytackler kernel: [   29.218523]  [<c020a98f>] ? vfs_read+0x9f/0x1a0
Jan 22 19:37:04 deadlytackler kernel: [   29.218531]  [<c02607e0>] ? sysfs_read_file+0x0/0x90
Jan 22 19:37:04 deadlytackler kernel: [   29.218536]  [<c020ab42>] ? sys_read+0x42/0x70
Jan 22 19:37:04 deadlytackler kernel: [   29.218544]  [<c01033ec>] ? syscall_call+0x7/0xb
Jan 22 19:37:04 deadlytackler kernel: [   29.218552]  [<c0590000>] ? show_kprobe_addr+0xf0/0x100
Jan 22 19:37:04 deadlytackler kernel: [   29.218623] ---[ end trace c8dbd61911c7a0f3 ]---
Jan 22 19:37:04 deadlytackler kernel: [   29.309957] *pde = 00000000 
Jan 22 19:37:04 deadlytackler kernel: [   29.309976] Modules linked in: binfmt_misc snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi fbcon tileblit font snd_rawmidi snd_seq_midi_event bitblit softcursor snd_seq vga16fb vgastate snd_timer snd_seq_device i915 drm_kms_helper gspca_vc032x drm i2c_algo_bit snd video ppdev gspca_main intel_agp soundcore parport_pc snd_page_alloc output psmouse agpgart videodev v4l1_compat shpchp serio_raw lp parport sis900 mii floppy
Jan 22 19:37:04 deadlytackler kernel: [   29.310030] 
Jan 22 19:37:04 deadlytackler kernel: [   29.310037] Pid: 1131, comm: udev-acl.ck Tainted: G   M  D    (2.6.32-37-generic #81-Ubuntu)  
Jan 22 19:37:04 deadlytackler kernel: [   29.310042] EIP: 0060:[<c03e79fd>] EFLAGS: 00010202 CPU: 0
Jan 22 19:37:04 deadlytackler kernel: [   29.310049] EIP is at show_uevent+0x2d/0x100
Jan 22 19:37:04 deadlytackler kernel: [   29.310053] EAX: 00000001 EBX: c078a440 ECX: dd410000 EDX: c078a440
Jan 22 19:37:04 deadlytackler kernel: [   29.310057] ESI: ef003010 EDI: e00497a8 EBP: df7a7f0c ESP: df7a7ee8
Jan 22 19:37:04 deadlytackler kernel: [   29.310062]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 22 19:37:04 deadlytackler kernel: [   29.310075]  c079ad00 00000000 00000000 000080d0 dd410000 c079ad00 c078a440 fffffffb
Jan 22 19:37:04 deadlytackler kernel: [   29.310085] <0> c03e79d0 df7a7f20 c03e6f39 df72f5c0 e0baba50 c078a454 df7a7f3c c0260772
Jan 22 19:37:04 deadlytackler kernel: [   29.310096] <0> eb8f8780 e00497a8 df72f5c0 df7a7f98 eb8f8780 df7a7f64 c026085a b78bb000
Jan 22 19:37:04 deadlytackler kernel: [   29.310116]  [<c03e79d0>] ? show_uevent+0x0/0x100
Jan 22 19:37:04 deadlytackler kernel: [   29.310122]  [<c03e6f39>] ? dev_attr_show+0x29/0x50
Jan 22 19:37:04 deadlytackler kernel: [   29.310131]  [<c0260772>] ? fill_read_buffer+0x52/0xc0
Jan 22 19:37:04 deadlytackler kernel: [   29.310136]  [<c026085a>] ? sysfs_read_file+0x7a/0x90
Jan 22 19:37:04 deadlytackler kernel: [   29.310146]  [<c020a98f>] ? vfs_read+0x9f/0x1a0
Jan 22 19:37:04 deadlytackler kernel: [   29.310151]  [<c02607e0>] ? sysfs_read_file+0x0/0x90
Jan 22 19:37:04 deadlytackler kernel: [   29.310158]  [<c020ab42>] ? sys_read+0x42/0x70
Jan 22 19:37:04 deadlytackler kernel: [   29.310166]  [<c01033ec>] ? syscall_call+0x7/0xb
Jan 22 19:37:04 deadlytackler kernel: [   29.310178]  [<c0590000>] ? show_kprobe_addr+0xf0/0x100
Jan 22 19:37:04 deadlytackler kernel: [   29.310251] ---[ end trace c8dbd61911c7a0f4 ]---
Jan 22 19:41:35 deadlytackler kernel: [  300.004053] Machine check events logged


```

---

### Post by deadlytackler on 2012-01-23
> **deadlytackler said:**
> I am getting problem logging in to my machine. Its Intel(R) Pentium(R) 4 CPU 2.40 GHz, using Ubuntu 10.04 (Lucid), Kernel Linux 2.6.32-37-generic,
GNOME 2.30.2.
After many restarts logged on to system this is extract from log files:-
"[B] Jan 22 19:36:53 deadlytackler kernel: [    0.142315] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jan 22 19:36:53 deadlytackler kernel: [    0.142318] * this clock source is slow. If you are sure your timer does not have
Jan 22 19:36:53 deadlytackler kernel: [    0.142319] * this bug, please use "acpi_pm_good" to disable the workaround"[/B]

[COLOR="Navy"]How to add "acpi_pm_good" to kernel?[/COLOR]:confused:

---

