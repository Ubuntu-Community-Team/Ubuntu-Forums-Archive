---
title: "Kogan Agora pro Atheros Bluetooth AR3011 not working {AMD64}"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Roo79x on 2011-07-19
Kogan Agora pro Atheros Bluetooth AR3011 not working {AMD64}

I've just installed Oneiric on my laptop{it originally came with Natty pre-installed} and I have lost the bluetooth. I'm not sure if it is a bug or not.

Is there anyone who could please help to get this fixed?

I'm new to all this so forgive me if I have given the wrong info
here is some information I have collected from terminal
```
ray@Agora:~$ sudo lsusb
[sudo] password for ray: 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 18e3:9512 Fitipower Integrated Technology Inc Webcam
Bus 003 Device 002: ID 0cf3:3000 Atheros Communications, Inc. AR3011
```

```
ray@Agora:~$ sudo dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-5-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-2ubuntu2) ) #6-Ubuntu SMP Tue Jul 12 05:21:50 UTC 2011 (Ubuntu 3.0.0-5.6-generic 3.0.0-rc7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-5-generic root=UUID=b9729248-335e-45b7-9248-0add8ee09b91 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dc80000 (usable)
[    0.000000]  BIOS-e820: 000000007dc80000 - 000000007dc8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dc8e000 - 000000007dcd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dcd0000 - 000000007dce0000 (reserved)
[    0.000000]  BIOS-e820: 000000007dcec000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Kogan                           Kogan Agora                    /Kogan Agora                    , BIOS 080016  05/05/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7dc80 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07DD00000 mask FFFF00000 uncachable
[    0.000000]   2 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 07E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000007dc80000
[    0.000000]  0000000000 - 007dc00000 page 2M
[    0.000000]  007dc00000 - 007dc80000 page 4k
[    0.000000] kernel direct mapping tables up to 7dc80000 @ 7dc7c000-7dc80000
[    0.000000] RAMDISK: 365d6000 - 372e3000
[    0.000000] ACPI: RSDP 00000000000f9a80 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 000000007dc80100 00074 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007dc80290 000F4 (v03 050511 FACP1430 20110505 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007dc805c0 0707D (v01  U200R U200R123 00000123 INTL 20051117)
[    0.000000] ACPI: FACS 000000007dc8e000 00040
[    0.000000] ACPI: APIC 000000007dc80390 0006C (v01 050511 APIC1430 20110505 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007dc80400 0003C (v01 050511 OEMMCFG  20110505 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007dc80440 00176 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007dc8e040 00073 (v01 050511 OEMB1430 20110505 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007dc8a5c0 00038 (v01 050511 OEMHPET  20110505 MSFT 00000097)
[    0.000000] ACPI: GSCI 000000007dc8e0c0 02024 (v01 050511 GMCHSCI  20110505 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000007dc900f0 00176 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90270 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90810 002D7 (v01  PmRef   CpuPm1 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dc80000
[    0.000000] Initmem setup node 0 0000000000000000-000000007dc80000
[    0.000000]   NODE_DATA [000000007dc77000 - 000000007dc7bfff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007b400000-ffff88007cffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0007dc80
[    0.000000] On node 0 totalpages: 515083
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3918 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6988 pages used for memmap
[    0.000000]   DMA32 zone: 504116 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7de00000 (gap: 7de00000:80f20000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88007da00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508034
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-5-generic root=UUID=b9729248-335e-45b7-9248-0add8ee09b91 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2004340k/2060800k available (6125k kernel code, 468k absent, 55992k reserved, 4862k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches HPET. 1 loops
[    0.000000] Detected 1300.042 MHz processor.
[    0.020004] Calibrating delay loop (skipped), value calculated using timer frequency.. 2600.08 BogoMIPS (lpj=13000420)
[    0.020011] pid_max: default: 32768 minimum: 301
[    0.020061] Security Framework initialized
[    0.020084] AppArmor: AppArmor initialized
[    0.020087] Yama: becoming mindful.
[    0.020466] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.021275] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.021986] Mount-cache hash table entries: 256
[    0.022199] Initializing cgroup subsys cpuacct
[    0.022209] Initializing cgroup subsys memory
[    0.022222] Initializing cgroup subsys devices
[    0.022225] Initializing cgroup subsys freezer
[    0.022228] Initializing cgroup subsys net_cls
[    0.022231] Initializing cgroup subsys blkio
[    0.022242] Initializing cgroup subsys perf_event
[    0.022291] mce: CPU supports 6 MCE banks
[    0.022303] CPU0: Thermal monitoring handled by SMI
[    0.022309] using mwait in idle threads.
[    0.022370] SMP alternatives: switching to UP code
[    0.043916] ACPI: Core revision 20110413
[    0.050038] ftrace: allocating 25882 entries in 102 pages
[    0.060441] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.161972] CPU0: Genuine Intel(R) CPU           U2700  @ 1.30GHz stepping 0a
[    0.170000] APIC calibration not consistent with PM-Timer: 109ms instead of 100ms
[    0.170000] APIC delta adjusted to PM-Timer: 1250042 (1375038)
[    0.170000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.170000] ... version:                2
[    0.170000] ... bit width:              40
[    0.170000] ... generic registers:      2
[    0.170000] ... value mask:             000000ffffffffff
[    0.170000] ... max period:             000000007fffffff
[    0.170000] ... fixed-purpose events:   3
[    0.170000] ... event mask:             0000000700000003
[    0.170000] Brought up 1 CPUs
[    0.170000] Total of 1 processors activated (2600.08 BogoMIPS).
[    0.170000] devtmpfs: initialized
[    0.170000] PM: Registering ACPI NVS region at 7dc8e000 (270336 bytes)
[    0.170000] print_constraints: dummy: 
[    0.170000] Time:  1:23:50  Date: 07/20/11
[    0.170000] NET: Registered protocol family 16
[    0.170000] ACPI: bus type pci registered
[    0.170000] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.170000] PCI: not using MMCONFIG
[    0.170000] PCI: Using configuration type 1 for base access
[    0.170000] bio: create slab <bio-0> at 0
[    0.170000] ACPI: EC: Look up EC in DSDT
[    0.170000] ACPI: Executed 1 blocks of module-level executable AML code
[    0.172457] ACPI Warning: Incorrect checksum in table [GSCI] - 0x8B, should be 0x33 (20110413/tbutils-314)
[    0.173167] ACPI: Interpreter enabled
[    0.173167] ACPI: (supports S0 S3 S4 S5)
[    0.173167] ACPI: Using IOAPIC for interrupt routing
[    0.173167] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.173167] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.236735] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.236969] ACPI: No dock devices found.
[    0.236972] HEST: Table not found.
[    0.236977] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.237104] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.237358] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.237363] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.237367] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.237371] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.237375] pci_root PNP0A08:00: host bridge window [mem 0x7de00000-0xdfffffff]
[    0.237379] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.237398] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.237429] DMAR: Forcing write-buffer flush capability
[    0.237431] DMAR: Disabling IOMMU for graphics on this chipset
[    0.237461] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.237479] pci 0000:00:02.0: reg 10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.237492] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.237501] pci 0000:00:02.0: reg 20: [io  0xcc00-0xcc07]
[    0.237544] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.237560] pci 0000:00:02.1: reg 10: [mem 0xfe800000-0xfe8fffff 64bit]
[    0.237667] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.237735] pci 0000:00:1a.0: reg 20: [io  0xd400-0xd41f]
[    0.237804] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.237871] pci 0000:00:1a.1: reg 20: [io  0xd080-0xd09f]
[    0.237940] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.238007] pci 0000:00:1a.2: reg 20: [io  0xd000-0xd01f]
[    0.238090] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.238121] pci 0000:00:1a.7: reg 10: [mem 0xfe9ff400-0xfe9ff7ff]
[    0.238229] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.238236] pci 0000:00:1a.7: PME# disabled
[    0.238276] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.238302] pci 0000:00:1b.0: reg 10: [mem 0xfe9f8000-0xfe9fbfff 64bit]
[    0.238395] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.238401] pci 0000:00:1b.0: PME# disabled
[    0.238434] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.238529] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.238535] pci 0000:00:1c.0: PME# disabled
[    0.238571] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.238667] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.238674] pci 0000:00:1c.1: PME# disabled
[    0.238720] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.238788] pci 0000:00:1d.0: reg 20: [io  0xd880-0xd89f]
[    0.238857] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.238924] pci 0000:00:1d.1: reg 20: [io  0xd800-0xd81f]
[    0.238994] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.239061] pci 0000:00:1d.2: reg 20: [io  0xd480-0xd49f]
[    0.239143] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.239174] pci 0000:00:1d.7: reg 10: [mem 0xfe9ff800-0xfe9ffbff]
[    0.239280] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.239287] pci 0000:00:1d.7: PME# disabled
[    0.239317] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.239415] pci 0000:00:1f.0: [8086:2917] type 0 class 0x000601
[    0.239585] pci 0000:00:1f.2: [8086:2928] type 0 class 0x000101
[    0.239612] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.239627] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.239641] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.239655] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.239670] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.239684] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.239749] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.239776] pci 0000:00:1f.3: reg 10: [mem 0xfe9ffc00-0xfe9ffcff 64bit]
[    0.239812] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.240005] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
[    0.240072] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.240190] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.240265] pci 0000:02:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.240313] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.240473] pci 0000:02:00.0: supports D1 D2
[    0.240476] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.240492] pci 0000:02:00.0: PME# disabled
[    0.240669] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.240676] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.240683] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.240693] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.240798] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.240839] pci 0000:03:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.240998] pci 0000:03:00.0: supports D1
[    0.241001] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.241011] pci 0000:03:00.0: PME# disabled
[    0.241094] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.241100] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.241107] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.241117] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.241220] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.241227] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.241234] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.241244] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.241249] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.241253] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.241257] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.241261] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.241265] pci 0000:00:1e.0:   bridge window [mem 0x7de00000-0xdfffffff] (subtractive decode)
[    0.241269] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.241296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.241448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.241599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.241644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.241706]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.241711]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.241714] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.253571] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.253642] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.253706] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.253774] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.253842] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.253911] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.253978] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.254046] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.254187] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.254199] vgaarb: loaded
[    0.254201] vgaarb: bridge control possible 0000:00:02.0
[    0.254466] SCSI subsystem initialized
[    0.254550] libata version 3.00 loaded.
[    0.254608] usbcore: registered new interface driver usbfs
[    0.254623] usbcore: registered new interface driver hub
[    0.254661] usbcore: registered new device driver usb
[    0.254803] wmi: Mapper loaded
[    0.254806] PCI: Using ACPI for IRQ routing
[    0.266695] PCI: pci_cache_line_size set to 64 bytes
[    0.266803] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.266807] reserve RAM buffer: 000000007dc80000 - 000000007fffffff 
[    0.266933] NetLabel: Initializing
[    0.266935] NetLabel:  domain hash size = 128
[    0.266938] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.266957] NetLabel:  unlabeled traffic allowed by default
[    0.267019] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.267027] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.267035] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.270051] Switching to clocksource hpet
[    0.278882] AppArmor: AppArmor Filesystem Enabled
[    0.278925] pnp: PnP ACPI init
[    0.278947] ACPI: bus type pnp registered
[    0.279119] pnp 00:00: [bus 00-ff]
[    0.279123] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.279133] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.279137] pnp 00:00: [io  0x0d00-0xffff window]
[    0.279141] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.279144] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.279148] pnp 00:00: [mem 0x7de00000-0xdfffffff window]
[    0.279151] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.279236] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.279251] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.279319] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.279324] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.279374] pnp 00:02: [dma 4]
[    0.279377] pnp 00:02: [io  0x0000-0x000f]
[    0.279381] pnp 00:02: [io  0x0081-0x0083]
[    0.279384] pnp 00:02: [io  0x0087]
[    0.279386] pnp 00:02: [io  0x0089-0x008b]
[    0.279389] pnp 00:02: [io  0x008f]
[    0.279392] pnp 00:02: [io  0x00c0-0x00df]
[    0.279425] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.279441] pnp 00:03: [io  0x0070-0x0071]
[    0.279458] pnp 00:03: [irq 8]
[    0.279490] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.279542] pnp 00:04: [io  0x0060]
[    0.279545] pnp 00:04: [io  0x0064]
[    0.279553] pnp 00:04: [irq 1]
[    0.279588] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.279655] pnp 00:05: [irq 12]
[    0.279691] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.279705] pnp 00:06: [io  0x0061]
[    0.279743] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.279757] pnp 00:07: [io  0x00f0-0x00ff]
[    0.279765] pnp 00:07: [irq 13]
[    0.279798] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.279970] Switched to NOHz mode on CPU #0
[    0.280032] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.280036] pnp 00:08: [io  0x0680-0x069f]
[    0.280091] system 00:08: [io  0x0680-0x069f] has been reserved
[    0.280097] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.280275] pnp 00:09: [io  0x0010-0x001f]
[    0.280278] pnp 00:09: [io  0x0022-0x003f]
[    0.280281] pnp 00:09: [io  0x0044-0x005f]
[    0.280284] pnp 00:09: [io  0x0063]
[    0.280287] pnp 00:09: [io  0x0065]
[    0.280289] pnp 00:09: [io  0x0067-0x006f]
[    0.280292] pnp 00:09: [io  0x0072-0x007f]
[    0.280295] pnp 00:09: [io  0x0080]
[    0.280298] pnp 00:09: [io  0x0084-0x0086]
[    0.280300] pnp 00:09: [io  0x0088]
[    0.280303] pnp 00:09: [io  0x008c-0x008e]
[    0.280307] pnp 00:09: [io  0x0090-0x009f]
[    0.280309] pnp 00:09: [io  0x00a2-0x00bf]
[    0.280312] pnp 00:09: [io  0x00e0-0x00ef]
[    0.280315] pnp 00:09: [io  0x04d0-0x04d1]
[    0.280318] pnp 00:09: [io  0x0800-0x087f]
[    0.280322] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.280328] pnp 00:09: [io  0x0500-0x057f]
[    0.280332] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.280335] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.280338] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.280415] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.280420] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.280424] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.280429] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.280434] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.280439] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.280444] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.280526] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.280563] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.280630] pnp 00:0b: [mem 0xff800000-0xffbfffff]
[    0.280633] pnp 00:0b: [mem 0xffc00000-0xffffffff]
[    0.280674] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.280735] pnp 00:0c: [mem 0xffc00000-0xffbfffff disabled]
[    0.280789] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.280902] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.280906] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.280959] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.280964] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.280969] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.281058] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.281117] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.281123] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.281387] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.281391] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.281395] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.281398] pnp 00:0f: [mem 0x00100000-0x7ddfffff]
[    0.281401] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.281474] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.281479] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.281484] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.281488] system 00:0f: [mem 0x00100000-0x7ddfffff] could not be reserved
[    0.281493] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.281498] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.281686] pnp: PnP ACPI: found 16 devices
[    0.281689] ACPI: ACPI bus type pnp unregistered
[    0.288461] PCI: max bus depth: 1 pci_try_num: 2
[    0.288509] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.288515] pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
[    0.288520] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
[    0.288525] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.288530] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.288539] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.288546] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.288556] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.288561] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.288569] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.288576] pci 0000:00:1c.1:   bridge window [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.288586] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.288589] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.288597] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.288603] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.288632] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.288639] pci 0000:00:1c.0: setting latency timer to 64
[    0.288649] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.288659] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.288666] pci 0000:00:1c.1: setting latency timer to 64
[    0.288677] pci 0000:00:1e.0: setting latency timer to 64
[    0.288683] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.288687] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.288690] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.288694] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.288698] pci_bus 0000:00: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.288701] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.288705] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.288709] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.288713] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.288717] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.288720] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.288724] pci_bus 0000:03: resource 2 [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.288728] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.288732] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.288735] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.288739] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.288743] pci_bus 0000:01: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.288746] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.288803] NET: Registered protocol family 2
[    0.288949] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.289840] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.292378] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.293064] TCP: Hash tables configured (established 262144 bind 65536)
[    0.293068] TCP reno registered
[    0.293078] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.293107] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.293296] NET: Registered protocol family 1
[    0.293327] pci 0000:00:02.0: Boot video device
[    0.293527] PCI: CLS 32 bytes, default 64
[    0.293977] audit: initializing netlink socket (disabled)
[    0.293991] type=2000 audit(1311125029.290:1): initialized
[    0.329571] Trying to unpack rootfs image as initramfs...
[    0.380458] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.410353] VFS: Disk quotas dquot_6.5.2
[    0.410436] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.411296] fuse init (API version 7.16)
[    0.411426] msgmni has been set to 3914
[    0.420400] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.420439] io scheduler noop registered
[    0.420442] io scheduler deadline registered
[    0.420503] io scheduler cfq registered (default)
[    0.420646] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.420719] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.420816] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.420879] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.420996] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.421029] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.421090] intel_idle: MWAIT substates: 0x22220
[    0.421093] intel_idle: does not run on family 6 model 23
[    0.423301] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.424823] ACPI: AC Adapter [AC] (on-line)
[    0.424923] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C09:00/PNP0C0D:00/input/input0
[    0.426218] ACPI: Lid Switch [LID]
[    0.426289] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.426296] ACPI: Sleep Button [SLPB]
[    0.426348] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.426353] ACPI: Power Button [PWRB]
[    0.426409] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.426414] ACPI: Power Button [PWRF]
[    0.426628] ACPI: acpi_idle registered with cpuidle
[    0.428969] Monitor-Mwait will be used to enter C-1 state
[    0.440058] Monitor-Mwait will be used to enter C-2 state
[    0.440110] Monitor-Mwait will be used to enter C-3 state
[    0.440119] Marking TSC unstable due to TSC halts in idle
[    0.442310] ACPI: Invalid active0 threshold
[    0.442456] thermal LNXTHERM:00: registered as thermal_zone0
[    0.442460] ACPI: Thermal Zone [TZ01] (42 C)
[    0.442487] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.442570] ERST: Table is not found!
[    0.442667] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.444521] Linux agpgart interface v0.103
[    0.444600] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.444744] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.445680] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.445815] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.447318] brd: module loaded
[    0.448007] loop: module loaded
[    0.448247] ata_piix 0000:00:1f.2: version 2.13
[    0.448275] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.448283] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.448333] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.448732] scsi0 : ata_piix
[    0.448840] scsi1 : ata_piix
[    0.450393] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.450400] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.450854] Fixed MDIO Bus: probed
[    0.450886] PPP generic driver version 2.4.2
[    0.450936] tun: Universal TUN/TAP device driver, 1.6
[    0.450939] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.451144] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.451172] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.451192] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.451197] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.451242] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.451285] ehci_hcd 0000:00:1a.7: debug port 1
[    0.455184] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.460334] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9ff400
[    0.475323] ACPI: Battery Slot [BAT0] (battery present)
[    0.480334] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.480539] hub 1-0:1.0: USB hub found
[    0.480546] hub 1-0:1.0: 6 ports detected
[    0.480657] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.480683] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.480688] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.480747] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.480788] ehci_hcd 0000:00:1d.7: debug port 1
[    0.484663] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.484691] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    0.500168] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.500361] hub 2-0:1.0: USB hub found
[    0.500368] hub 2-0:1.0: 6 ports detected
[    0.500468] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.500488] uhci_hcd: USB Universal Host Controller Interface driver
[    0.500539] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.500552] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.500558] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.500610] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.500663] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d400
[    0.500818] hub 3-0:1.0: USB hub found
[    0.500824] hub 3-0:1.0: 2 ports detected
[    0.500909] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.500918] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.500923] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.500967] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.501010] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d080
[    0.501169] hub 4-0:1.0: USB hub found
[    0.501177] hub 4-0:1.0: 2 ports detected
[    0.501253] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.501261] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.501266] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.501311] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.501354] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d000
[    0.501516] hub 5-0:1.0: USB hub found
[    0.501522] hub 5-0:1.0: 2 ports detected
[    0.501603] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.501612] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.501617] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.501660] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.501694] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.501860] hub 6-0:1.0: USB hub found
[    0.501866] hub 6-0:1.0: 2 ports detected
[    0.501939] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.501948] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.501953] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.502009] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.502044] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.502198] hub 7-0:1.0: USB hub found
[    0.502204] hub 7-0:1.0: 2 ports detected
[    0.502277] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.502286] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.502291] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.502340] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.502372] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.502530] hub 8-0:1.0: USB hub found
[    0.502536] hub 8-0:1.0: 2 ports detected
[    0.502696] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.509497] i8042: Detected active multiplexing controller, rev 1.1
[    0.530298] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.530313] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.530365] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.530398] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.530434] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.530604] mousedev: PS/2 mouse device common for all mice
[    0.530846] rtc_cmos 00:03: RTC can wake from S4
[    0.530984] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.531020] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.531191] device-mapper: uevent: version 1.0.3
[    0.531300] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.531388] device-mapper: multipath: version 1.3.0 loaded
[    0.531391] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.531529] cpuidle: using governor ladder
[    0.531589] cpuidle: using governor menu
[    0.531592] EFI Variables Facility v0.08 2004-May-17
[    0.531929] TCP cubic registered
[    0.532111] NET: Registered protocol family 10
[    0.532713] NET: Registered protocol family 17
[    0.532738] Registering the dns_resolver key type
[    0.532880] PM: Hibernation image not present or could not be loaded.
[    0.532895] registered taskstats version 1
[    0.541661]   Magic number: 3:434:357
[    0.541671] input event3: hash matches
[    0.541789] rtc_cmos 00:03: setting system clock to 2011-07-20 01:23:50 UTC (1311125030)
[    0.541940] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.541943] EDD information not available.
[    0.558266] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.821655] ata1: SATA link down (SStatus 0 SControl 300)
[    0.852750] Freeing initrd memory: 13364k freed
[    0.920138] usb 2-2: new high speed USB device number 2 using ehci_hcd
[    0.980089] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.000479] ata2.00: ATA-8: WDC WD5000BEVT-24A0RT0, 01.01A02, max UDMA/133
[    1.000485] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.040547] ata2.00: configured for UDMA/133
[    1.040746] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.040987] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.041096] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.041175] sd 1:0:0:0: [sda] Write Protect is off
[    1.041180] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.041215] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.105010]  sda: sda1 sda2 < sda5 >
[    1.105378] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.108322] Freeing unused kernel memory: 988k freed
[    1.108798] Write protecting the kernel read-only data: 10240k
[    1.117078] Freeing unused kernel memory: 1396k freed
[    1.142475] udevd[64]: starting version 172
[    1.346771] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.346804] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.346903] r8169 0000:02:00.0: setting latency timer to 64
[    1.347096] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.347674] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc9000033c000, 00:24:25:0d:50:d8, XID 04c00000 IRQ 42
[    1.490046] usb 3-2: new full speed USB device number 2 using uhci_hcd
[    1.585147] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.036405] udevd[265]: starting version 172
[    9.097253] lp: driver loaded but no devices found
[    9.128064] Adding 2058236k swap on /dev/sda5.  Priority:-1 extents:1 across:2058236k 
[    9.436577] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.544337] [drm] Initialized drm 1.1.0 20060810
[    9.572196] cfg80211: Calling CRDA to update world regulatory domain
[    9.723092] type=1400 audit(1311125039.671:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=489 comm="apparmor_parser"
[    9.724899] type=1400 audit(1311125039.671:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=489 comm="apparmor_parser"
[    9.725829] type=1400 audit(1311125039.671:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=489 comm="apparmor_parser"
[   10.106346] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.106355] i915 0000:00:02.0: setting latency timer to 64
[   10.375118] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.375136] ath9k 0000:03:00.0: setting latency timer to 64
[   10.437496] r8169 0000:02:00.0: eth0: link down
[   10.437864] Linux video capture interface: v2.00
[   10.440386] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.471356] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (18e3:9512)
[   10.488109] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input5
[   10.488270] usbcore: registered new interface driver uvcvideo
[   10.488273] USB Video Class driver (v1.1.0)
[   10.515488] ath: EEPROM regdomain: 0x60
[   10.515492] ath: EEPROM indicates we should expect a direct regpair map
[   10.515497] ath: Country alpha2 being used: 00
[   10.515500] ath: Regpair used: 0x60
[   10.527212] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.527219] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527223] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.527227] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527230] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.527235] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527238] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.527242] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527246] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.527250] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527253] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.527257] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527261] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.527265] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527268] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.527273] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527276] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.527280] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527284] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.527288] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527291] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.527296] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527299] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.527303] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527307] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.527311] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.527314] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.527319] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.587098] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   10.605753] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.801649] Registered led device: ath9k-phy0
[   10.801662] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90000360000, irq=17
[   10.842197] type=1400 audit(1311125040.791:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=687 comm="apparmor_parser"
[   10.855483] type=1400 audit(1311125040.801:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=687 comm="apparmor_parser"
[   10.856418] type=1400 audit(1311125040.801:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=687 comm="apparmor_parser"
[   10.885115] type=1400 audit(1311125040.831:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=689 comm="apparmor_parser"
[   10.948611] type=1400 audit(1311125040.891:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=689 comm="apparmor_parser"
[   10.981719] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
[   10.990053] type=1400 audit(1311125040.931:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=689 comm="apparmor_parser"
[   10.990559] usbcore: registered new interface driver snd-usb-audio
[   11.040417] type=1400 audit(1311125040.991:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=704 comm="apparmor_parser"
[   11.193368] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   11.193377] cfg80211: World regulatory domain updated:
[   11.193380] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.193385] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.193389] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.193393] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.193397] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.193401] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.254878] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   11.330100] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   11.371314] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
[   11.507337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.721394] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   11.721403] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.721406] [drm] Driver supports precise vblank timestamp query.
[   11.721460] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.196848] fbcon: inteldrmfb (fb0) is primary device
[   12.199877] Console: switching to colour frame buffer device 170x48
[   12.199916] fb0: inteldrmfb frame buffer device
[   12.199919] drm: registered panic notifier
[   12.208873] acpi device:2d: registered as cooling_device1
[   12.210372] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   12.210568] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.211367] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.211430] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.211508] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.211546] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.334942] hda_codec: ALC662 rev1: BIOS auto-probing.
[   12.345238] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   12.354597] input: HDA Intel HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.354852] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   13.550901] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   13.756006] init: plymouth-stop pre-start process (1102) terminated with status 1
[   14.679797] wlan0: authenticate with 00:26:44:98:e0:11 (try 1)
[   14.681793] wlan0: authenticated
[   14.682208] wlan0: associate with 00:26:44:98:e0:11 (try 1)
[   14.685003] wlan0: RX AssocResp from 00:26:44:98:e0:11 (capab=0x411 status=0 aid=2)
[   14.685008] wlan0: associated
[   14.685648] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.856399] Intel AES-NI instructions are not detected.
[   14.858587] padlock_aes: VIA PadLock not detected.
[   16.621734] ath3k_load_firmware: Can't change to loading configuration err
[   16.621774] ath3k: probe of 3-2:1.0 failed with error -110
[   16.621821] usbcore: registered new interface driver ath3k
[   16.963952] ppdev: user-space parallel port driver
[   17.353869] audit_printk_skb: 6 callbacks suppressed
[   17.353874] type=1400 audit(1311125047.301:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1176 comm="apparmor_parser"
[   17.355608] type=1400 audit(1311125047.301:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1176 comm="apparmor_parser"
[   19.869011] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.090021] wlan0: no IPv6 routers present
[  178.710170] usb 8-2: new low speed USB device number 2 using uhci_hcd
[  179.311101] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input10
[  179.311379] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:1d.2-2/input0
[  179.312155] usbcore: registered new interface driver usbhid
[  179.312159] usbhid: USB HID core driver
[ 3728.638287] exe (2269): /proc/2269/oom_adj is deprecated, please use /proc/2269/oom_score_adj instead.
[ 4144.790076] usb 8-2: USB disconnect, device number 2
```

```
ray@Agora:~$ sudo lspci
[sudo] password for ray: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

```
ray@Agora:~$ uname -a
Linux Agora 3.0.0-5-generic #6-Ubuntu SMP Tue Jul 12 05:21:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

if I should have given more information or different information please guide me and I will do my best to give it.
 
I'd just like to get my bluetooth working, also wifi works fine

some stuff I have found but I don't know if it's relevent or not to my problem

[http://www.mailrepository.com/ath9k-devel.lists.ath9k.org/msg/3546094/](http://www.mailrepository.com/ath9k-devel.lists.ath9k.org/msg/3546094/)

[http://www.kogan.com.au/shop/agora-pro-12-ultra-portable-laptop-computer/](http://www.kogan.com.au/shop/agora-pro-12-ultra-portable-laptop-computer/)

[http://www.qca.qualcomm.com/technology/technology.php?nav1=49&product=66](http://www.qca.qualcomm.com/technology/technology.php?nav1=49&product=66)

---

### Post by Roo79x on 2011-07-20
well seeing as no-one has replied yet I was looking through launchpad.net and I found this bug [https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/714862](https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/714862)

although they talk of a dell laptop I think it relates to this as well... can someone please confirm?

---

### Post by cariboo on 2011-07-20
Please don't bump your thread more than once every 24 hours, we are all volunteers here, and the person that may be able to answer your question may not have seen it yet.

---

### Post by Roo79x on 2011-07-20
> **cariboo907 said:**
> Please don't bump your thread more than once every 24 hours, we are all volunteers here, and the person that may be able to answer your question may not have seen it yet.

it wasn't a bump at all. Did I write bump I was looking to solve an issue and as no one had answered yet and I had been looking on launchpad.net and found a bug that I thought might be related I posted it here.

---

### Post by Roo79x on 2011-07-29
well it's been a week and a 130 views and still no answer?... top form people top form. so much for a community/forum to help hey!!!.
I'm dual booting into linux mint 11 now (at least they are not snobs). anyway I have some more information about this issue if anyone can be bothered to do more than just read and not help.

as I said I'm dual booting with linux mint 11 and ubuntu 11.10 now and I have found that if I first boot and login to linux mint 11 then reboot into ubuntu oneiric ocelot 11.10 the bluetooth works fine... but if I boot straight into ubuntu oneiric ocelot 11.10 the bluetooth does not work at all.

this is just to update what I've found here as I'm sure this thread will get the same attention it did before.

---

### Post by cariboo on 2011-07-29
What does dmesg say when you plug your device in while running Mint, as compared to Oneiric?

---

### Post by Roo79x on 2011-07-29
dmesg when booting straight into Linux Mint 11 is
```
~ $ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@yellow) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=47bba116-2bee-48b1-899d-9b161b440f9f ro splash vga=786 quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dc80000 (usable)
[    0.000000]  BIOS-e820: 000000007dc80000 - 000000007dc8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dc8e000 - 000000007dcd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dcd0000 - 000000007dce0000 (reserved)
[    0.000000]  BIOS-e820: 000000007dcec000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Kogan                           Kogan Agora                    /Kogan Agora                    , BIOS 080016  05/05/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7dc80 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07DD00000 mask FFFF00000 uncachable
[    0.000000]   2 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 07E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007dc80000
[    0.000000]  0000000000 - 007dc00000 page 2M
[    0.000000]  007dc00000 - 007dc80000 page 4k
[    0.000000] kernel direct mapping tables up to 7dc80000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 35ac2000 - 36d59000
[    0.000000] ACPI: RSDP 00000000000f9a80 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 000000007dc80100 00074 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007dc80290 000F4 (v03 050511 FACP1430 20110505 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007dc805c0 0707D (v01  U200R U200R123 00000123 INTL 20051117)
[    0.000000] ACPI: FACS 000000007dc8e000 00040
[    0.000000] ACPI: APIC 000000007dc80390 0006C (v01 050511 APIC1430 20110505 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007dc80400 0003C (v01 050511 OEMMCFG  20110505 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007dc80440 00176 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007dc8e040 00073 (v01 050511 OEMB1430 20110505 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007dc8a5c0 00038 (v01 050511 OEMHPET  20110505 MSFT 00000097)
[    0.000000] ACPI: GSCI 000000007dc8e0c0 02024 (v01 050511 GMCHSCI  20110505 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000007dc900f0 00176 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90270 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90810 002D7 (v01  PmRef   CpuPm1 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dc80000
[    0.000000] Initmem setup node 0 0000000000000000-000000007dc80000
[    0.000000]   NODE_DATA [000000007dc7b000 - 000000007dc7ffff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007b400000-ffff88007cffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0007dc80
[    0.000000] On node 0 totalpages: 515083
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3917 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6988 pages used for memmap
[    0.000000]   DMA32 zone: 504116 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7de00000 (gap: 7de00000:80f20000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007da00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508033
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=47bba116-2bee-48b1-899d-9b161b440f9f ro splash vga=786 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1998704k/2060800k available (5941k kernel code, 468k absent, 61628k reserved, 5016k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 20971520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1299.917 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2599.83 BogoMIPS (lpj=12999170)
[    0.010012] pid_max: default: 32768 minimum: 301
[    0.010052] Security Framework initialized
[    0.010076] AppArmor: AppArmor initialized
[    0.010079] Yama: becoming mindful.
[    0.010466] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011737] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012436] Mount-cache hash table entries: 256
[    0.012641] Initializing cgroup subsys ns
[    0.012648] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.012652] Initializing cgroup subsys cpuacct
[    0.012659] Initializing cgroup subsys memory
[    0.012672] Initializing cgroup subsys devices
[    0.012675] Initializing cgroup subsys freezer
[    0.012679] Initializing cgroup subsys net_cls
[    0.012682] Initializing cgroup subsys blkio
[    0.012736] mce: CPU supports 6 MCE banks
[    0.012748] CPU0: Thermal monitoring handled by SMI
[    0.012753] using mwait in idle threads.
[    0.012806] SMP alternatives: switching to UP code
[    0.033244] ACPI: Core revision 20110112
[    0.040036] ftrace: allocating 24323 entries in 96 pages
[    0.050070] Setting APIC routing to flat
[    0.050445] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.163008] CPU0: Genuine Intel(R) CPU           U2700  @ 1.30GHz stepping 0a
[    0.170000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.170000] ... version:                2
[    0.170000] ... bit width:              40
[    0.170000] ... generic registers:      2
[    0.170000] ... value mask:             000000ffffffffff
[    0.170000] ... max period:             000000007fffffff
[    0.170000] ... fixed-purpose events:   3
[    0.170000] ... event mask:             0000000700000003
[    0.170000] Brought up 1 CPUs
[    0.170000] Total of 1 processors activated (2599.83 BogoMIPS).
[    0.170000] devtmpfs: initialized
[    0.170000] print_constraints: dummy: 
[    0.170000] Time:  6:51:29  Date: 07/29/11
[    0.170000] NET: Registered protocol family 16
[    0.170000] ACPI: bus type pci registered
[    0.170000] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.170000] PCI: not using MMCONFIG
[    0.170000] PCI: Using configuration type 1 for base access
[    0.170000] bio: create slab <bio-0> at 0
[    0.170000] ACPI: EC: Look up EC in DSDT
[    0.170000] ACPI: Executed 1 blocks of module-level executable AML code
[    0.173492] ACPI Warning: Incorrect checksum in table [GSCI] - 0x8B, should be 0x6F (20110112/tbutils-314)
[    0.174268] ACPI: Interpreter enabled
[    0.174268] ACPI: (supports S0 S3 S4 S5)
[    0.174268] ACPI: Using IOAPIC for interrupt routing
[    0.174268] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.174268] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.235311] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.235559] ACPI: No dock devices found.
[    0.235562] HEST: Table not found.
[    0.235566] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.235702] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.235985] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.235989] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.235993] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.235997] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.236001] pci_root PNP0A08:00: host bridge window [mem 0x7de00000-0xdfffffff]
[    0.236005] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.236023] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.236055] DMAR: Forcing write-buffer flush capability
[    0.236057] DMAR: Disabling IOMMU for graphics on this chipset
[    0.236087] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.236106] pci 0000:00:02.0: reg 10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.236118] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.236127] pci 0000:00:02.0: reg 20: [io  0xcc00-0xcc07]
[    0.236172] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.236188] pci 0000:00:02.1: reg 10: [mem 0xfe800000-0xfe8fffff 64bit]
[    0.236296] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.236364] pci 0000:00:1a.0: reg 20: [io  0xd400-0xd41f]
[    0.236434] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.236503] pci 0000:00:1a.1: reg 20: [io  0xd080-0xd09f]
[    0.236573] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.236641] pci 0000:00:1a.2: reg 20: [io  0xd000-0xd01f]
[    0.236724] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.236755] pci 0000:00:1a.7: reg 10: [mem 0xfe9ff400-0xfe9ff7ff]
[    0.236862] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.236869] pci 0000:00:1a.7: PME# disabled
[    0.236909] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.236934] pci 0000:00:1b.0: reg 10: [mem 0xfe9f8000-0xfe9fbfff 64bit]
[    0.237028] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.237034] pci 0000:00:1b.0: PME# disabled
[    0.237068] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.237164] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.237170] pci 0000:00:1c.0: PME# disabled
[    0.237206] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.237303] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.237309] pci 0000:00:1c.1: PME# disabled
[    0.237356] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.237425] pci 0000:00:1d.0: reg 20: [io  0xd880-0xd89f]
[    0.237495] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.237563] pci 0000:00:1d.1: reg 20: [io  0xd800-0xd81f]
[    0.237633] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.237702] pci 0000:00:1d.2: reg 20: [io  0xd480-0xd49f]
[    0.237786] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.237817] pci 0000:00:1d.7: reg 10: [mem 0xfe9ff800-0xfe9ffbff]
[    0.237924] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.237931] pci 0000:00:1d.7: PME# disabled
[    0.237962] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.238061] pci 0000:00:1f.0: [8086:2917] type 0 class 0x000601
[    0.238231] pci 0000:00:1f.2: [8086:2928] type 0 class 0x000101
[    0.238259] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.238273] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.238288] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.238302] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.238316] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.238330] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.238396] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.238422] pci 0000:00:1f.3: reg 10: [mem 0xfe9ffc00-0xfe9ffcff 64bit]
[    0.238459] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.238642] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
[    0.238709] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.238824] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.238898] pci 0000:02:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.238947] pci 0000:02:00.0: reg 30: [mem 0xfeae0000-0xfeafffff pref]
[    0.239112] pci 0000:02:00.0: supports D1 D2
[    0.239115] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.239132] pci 0000:02:00.0: PME# disabled
[    0.239309] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.239316] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.239323] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.239333] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.239437] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.239481] pci 0000:03:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.239637] pci 0000:03:00.0: supports D1
[    0.239640] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.239650] pci 0000:03:00.0: PME# disabled
[    0.239734] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.239741] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.239748] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.239758] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.239861] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.239868] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.239875] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.239885] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.239889] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.239893] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.239897] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.239901] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.239905] pci 0000:00:1e.0:   bridge window [mem 0x7de00000-0xdfffffff] (subtractive decode)
[    0.239909] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.239936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.240137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.240312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.240362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.240428]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.253738] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.253814] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.253882] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.253955] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.254028] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.254103] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.254175] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.254248] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.254398] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.254410] vgaarb: loaded
[    0.254673] SCSI subsystem initialized
[    0.254755] libata version 3.00 loaded.
[    0.254818] usbcore: registered new interface driver usbfs
[    0.254836] usbcore: registered new interface driver hub
[    0.254871] usbcore: registered new device driver usb
[    0.255013] wmi: Mapper loaded
[    0.255015] PCI: Using ACPI for IRQ routing
[    0.255019] PCI: pci_cache_line_size set to 64 bytes
[    0.255147] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.255151] reserve RAM buffer: 000000007dc80000 - 000000007fffffff 
[    0.255285] NetLabel: Initializing
[    0.255288] NetLabel:  domain hash size = 128
[    0.255290] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.255308] NetLabel:  unlabeled traffic allowed by default
[    0.255359] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.255368] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.255375] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.260048] Switching to clocksource hpet
[    0.269974] Switched to NOHz mode on CPU #0
[    0.270062] AppArmor: AppArmor Filesystem Enabled
[    0.270103] pnp: PnP ACPI init
[    0.270126] ACPI: bus type pnp registered
[    0.270313] pnp 00:00: [bus 00-ff]
[    0.270321] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.270324] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.270328] pnp 00:00: [io  0x0d00-0xffff window]
[    0.270332] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.270335] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.270339] pnp 00:00: [mem 0x7de00000-0xdfffffff window]
[    0.270342] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.270430] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.270446] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.270516] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.270521] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270575] pnp 00:02: [dma 4]
[    0.270578] pnp 00:02: [io  0x0000-0x000f]
[    0.270581] pnp 00:02: [io  0x0081-0x0083]
[    0.270584] pnp 00:02: [io  0x0087]
[    0.270587] pnp 00:02: [io  0x0089-0x008b]
[    0.270589] pnp 00:02: [io  0x008f]
[    0.270592] pnp 00:02: [io  0x00c0-0x00df]
[    0.270634] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.270651] pnp 00:03: [io  0x0070-0x0071]
[    0.270665] pnp 00:03: [irq 8]
[    0.270702] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.270754] pnp 00:04: [io  0x0060]
[    0.270757] pnp 00:04: [io  0x0064]
[    0.270764] pnp 00:04: [irq 1]
[    0.270808] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.270881] pnp 00:05: [irq 12]
[    0.270921] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.270936] pnp 00:06: [io  0x0061]
[    0.270976] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.270991] pnp 00:07: [io  0x00f0-0x00ff]
[    0.270998] pnp 00:07: [irq 13]
[    0.271035] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.271269] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.271273] pnp 00:08: [io  0x0680-0x069f]
[    0.271334] system 00:08: [io  0x0680-0x069f] has been reserved
[    0.271339] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.271534] pnp 00:09: [io  0x0010-0x001f]
[    0.271537] pnp 00:09: [io  0x0022-0x003f]
[    0.271540] pnp 00:09: [io  0x0044-0x005f]
[    0.271543] pnp 00:09: [io  0x0063]
[    0.271545] pnp 00:09: [io  0x0065]
[    0.271548] pnp 00:09: [io  0x0067-0x006f]
[    0.271551] pnp 00:09: [io  0x0072-0x007f]
[    0.271554] pnp 00:09: [io  0x0080]
[    0.271556] pnp 00:09: [io  0x0084-0x0086]
[    0.271559] pnp 00:09: [io  0x0088]
[    0.271562] pnp 00:09: [io  0x008c-0x008e]
[    0.271565] pnp 00:09: [io  0x0090-0x009f]
[    0.271567] pnp 00:09: [io  0x00a2-0x00bf]
[    0.271570] pnp 00:09: [io  0x00e0-0x00ef]
[    0.271573] pnp 00:09: [io  0x04d0-0x04d1]
[    0.271576] pnp 00:09: [io  0x0800-0x087f]
[    0.271582] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.271586] pnp 00:09: [io  0x0500-0x057f]
[    0.271589] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.271592] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.271595] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.271683] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.271688] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.271692] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.271702] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.271706] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.271710] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.271715] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.271805] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.271846] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.271923] pnp 00:0b: [mem 0xff800000-0xffbfffff]
[    0.271927] pnp 00:0b: [mem 0xffc00000-0xffffffff]
[    0.271974] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.272041] pnp 00:0c: [mem 0xffc00000-0xffbfffff disabled]
[    0.272105] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.272234] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.272238] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.272303] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.272308] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.272313] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.272408] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.272470] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.272475] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.272767] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.272771] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.272774] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.272778] pnp 00:0f: [mem 0x00100000-0x7ddfffff]
[    0.272781] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.272861] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.272865] system 00:0f: [mem 0x000c0000-0x000cffff] has been reserved
[    0.272870] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.272874] system 00:0f: [mem 0x00100000-0x7ddfffff] could not be reserved
[    0.272878] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.272883] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.273085] pnp: PnP ACPI: found 16 devices
[    0.273088] ACPI: ACPI bus type pnp unregistered
[    0.280833] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.280842] pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
[    0.280846] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.280851] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.280860] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.280866] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.280876] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.280881] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.280889] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.280896] pci 0000:00:1c.1:   bridge window [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.280906] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.280909] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.280917] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.280923] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.280958] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.280966] pci 0000:00:1c.0: setting latency timer to 64
[    0.280975] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.280985] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.280992] pci 0000:00:1c.1: setting latency timer to 64
[    0.281003] pci 0000:00:1e.0: setting latency timer to 64
[    0.281009] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.281013] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.281016] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.281020] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.281024] pci_bus 0000:00: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.281028] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.281031] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.281035] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.281039] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.281043] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.281046] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.281050] pci_bus 0000:03: resource 2 [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.281054] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.281057] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.281061] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.281064] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.281068] pci_bus 0000:01: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.281071] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.281125] NET: Registered protocol family 2
[    0.281267] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.282052] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.284408] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.285102] TCP: Hash tables configured (established 262144 bind 65536)
[    0.285105] TCP reno registered
[    0.285117] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.285146] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.285325] NET: Registered protocol family 1
[    0.285351] pci 0000:00:02.0: Boot video device
[    0.285558] PCI: CLS 32 bytes, default 64
[    0.286049] audit: initializing netlink socket (disabled)
[    0.286063] type=2000 audit(1311922289.280:1): initialized
[    0.308220] Trying to unpack rootfs image as initramfs...
[    0.340871] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.343553] VFS: Disk quotas dquot_6.5.2
[    0.343630] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.344534] fuse init (API version 7.16)
[    0.344667] msgmni has been set to 3903
[    0.350276] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.360527] io scheduler noop registered
[    0.360531] io scheduler deadline registered
[    0.360607] io scheduler cfq registered (default)
[    0.360758] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.360832] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.360935] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.360999] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.361118] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.361151] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.361215] intel_idle: MWAIT substates: 0x22220
[    0.361218] intel_idle: does not run on family 6 model 23
[    0.362570] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.364295] ACPI: AC Adapter [AC] (on-line)
[    0.364403] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C09:00/PNP0C0D:00/input/input0
[    0.365613] ACPI: Lid Switch [LID]
[    0.365688] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.365695] ACPI: Sleep Button [SLPB]
[    0.365759] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.365764] ACPI: Power Button [PWRB]
[    0.365827] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.365832] ACPI: Power Button [PWRF]
[    0.366064] ACPI: acpi_idle registered with cpuidle
[    0.369810] Monitor-Mwait will be used to enter C-1 state
[    0.380083] Monitor-Mwait will be used to enter C-2 state
[    0.380129] Monitor-Mwait will be used to enter C-3 state
[    0.380137] Marking TSC unstable due to TSC halts in idle
[    0.382591] ACPI: Invalid active0 threshold
[    0.382752] thermal LNXTHERM:00: registered as thermal_zone0
[    0.382756] ACPI: Thermal Zone [TZ01] (43 C)
[    0.382837] ERST: Table is not found!
[    0.382948] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.384747] Linux agpgart interface v0.103
[    0.384832] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.384975] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.385907] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.386053] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.387694] brd: module loaded
[    0.388461] loop: module loaded
[    0.388581] i2c-core: driver [adp5520] using legacy suspend method
[    0.388585] i2c-core: driver [adp5520] using legacy resume method
[    0.388712] ata_piix 0000:00:1f.2: version 2.13
[    0.388741] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.388749] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.388800] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.389258] scsi0 : ata_piix
[    0.389375] scsi1 : ata_piix
[    0.391356] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.391363] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.392695] Fixed MDIO Bus: probed
[    0.392738] PPP generic driver version 2.4.2
[    0.392796] tun: Universal TUN/TAP device driver, 1.6
[    0.392799] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.392914] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.392944] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.392958] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.392963] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.393016] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.393065] ehci_hcd 0000:00:1a.7: debug port 1
[    0.396941] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.400191] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9ff400
[    0.419435] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.419448] ACPI: Battery Slot [BAT0] (battery present)
[    0.430045] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.430259] hub 1-0:1.0: USB hub found
[    0.430266] hub 1-0:1.0: 6 ports detected
[    0.430391] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.430416] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.430421] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.430479] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.430523] ehci_hcd 0000:00:1d.7: debug port 1
[    0.434419] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.434444] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    0.450234] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.450442] hub 2-0:1.0: USB hub found
[    0.450449] hub 2-0:1.0: 6 ports detected
[    0.450558] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.450578] uhci_hcd: USB Universal Host Controller Interface driver
[    0.450679] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.450690] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.450695] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.450751] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.450802] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d400
[    0.450966] hub 3-0:1.0: USB hub found
[    0.450972] hub 3-0:1.0: 2 ports detected
[    0.451067] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.451076] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.451081] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.451137] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.451180] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d080
[    0.451347] hub 4-0:1.0: USB hub found
[    0.451353] hub 4-0:1.0: 2 ports detected
[    0.451436] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.451445] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.451450] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.451514] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.451560] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d000
[    0.451731] hub 5-0:1.0: USB hub found
[    0.451737] hub 5-0:1.0: 2 ports detected
[    0.451821] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.451831] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.451836] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.451883] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.451915] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.452077] hub 6-0:1.0: USB hub found
[    0.452082] hub 6-0:1.0: 2 ports detected
[    0.452164] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.452173] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.452178] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.452230] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.452266] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.452427] hub 7-0:1.0: USB hub found
[    0.452433] hub 7-0:1.0: 2 ports detected
[    0.452517] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.452526] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.452531] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.452579] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.452611] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.452772] hub 8-0:1.0: USB hub found
[    0.452778] hub 8-0:1.0: 2 ports detected
[    0.452945] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.459647] i8042: Detected active multiplexing controller, rev 1.1
[    0.480327] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.480341] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.480395] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.480436] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.480471] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.480667] mousedev: PS/2 mouse device common for all mice
[    0.480928] rtc_cmos 00:03: RTC can wake from S4
[    0.480994] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.481029] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.481204] device-mapper: uevent: version 1.0.3
[    0.481322] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.481408] device-mapper: multipath: version 1.2.0 loaded
[    0.481412] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.483862] cpuidle: using governor ladder
[    0.483927] cpuidle: using governor menu
[    0.484245] TCP cubic registered
[    0.484420] NET: Registered protocol family 10
[    0.485068] NET: Registered protocol family 17
[    0.485091] Registering the dns_resolver key type
[    0.485399] PM: Hibernation image not present or could not be loaded.
[    0.485415] registered taskstats version 1
[    0.485848]   Magic number: 3:160:874
[    0.485978] rtc_cmos 00:03: setting system clock to 2011-07-29 06:51:29 UTC (1311922289)
[    0.485983] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.485985] EDD information not available.
[    0.503645] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.751350] ata1: SATA link down (SStatus 0 SControl 300)
[    0.880172] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    0.910391] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.931526] ata2.00: ATA-8: WDC WD5000BEVT-24A0RT0, 01.01A02, max UDMA/133
[    0.931532] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.971083] ata2.00: configured for UDMA/133
[    0.971242] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-2 01.0 PQ: 0 ANSI: 5
[    0.971472] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    0.971582] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.971664] sd 1:0:0:0: [sda] Write Protect is off
[    0.971669] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.971705] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.995928] Freeing initrd memory: 19036k freed
[    1.058973]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.059516] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.062492] Freeing unused kernel memory: 956k freed
[    1.062977] Write protecting the kernel read-only data: 10240k
[    1.064267] Freeing unused kernel memory: 184k freed
[    1.072919] Freeing unused kernel memory: 1440k freed
[    1.100070] <30>udev[69]: starting version 167
[    1.381793] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.381838] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.381891] r8169 0000:02:00.0: setting latency timer to 64
[    1.381971] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.382567] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc9000032a000, 00:24:25:0d:50:d8, XID 04c00000 IRQ 42
[    1.443185] [drm] Initialized drm 1.1.0 20060810
[    1.482424] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.482432] i915 0000:00:02.0: setting latency timer to 64
[    1.561537] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.564662] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    1.564671] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.564673] [drm] Driver supports precise vblank timestamp query.
[    1.660596] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.973305] fbcon: inteldrmfb (fb0) is primary device
[    1.973694] Console: switching to colour frame buffer device 170x48
[    1.973732] fb0: inteldrmfb frame buffer device
[    1.973734] drm: registered panic notifier
[    1.986394] acpi device:2d: registered as cooling_device1
[    1.986913] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    1.987028] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.987407] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.019228] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90021a80000, using 1216k, total 1216k
[    2.019234] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    2.019237] vesafb: scrolling: redraw
[    2.019241] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.021230] fb1: VESA VGA frame buffer device
[    2.030067] usb 8-2: new low speed USB device using uhci_hcd and address 2
[    2.238157] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input6
[    2.238419] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.238649] usbcore: registered new interface driver usbhid
[    2.238653] usbhid: USB HID core driver
[    2.406783] Btrfs loaded
[    2.414273] xor: automatically using best checksumming function: generic_sse
[    2.460012]    generic_sse:  4978.800 MB/sec
[    2.460015] xor: using function: generic_sse (4978.800 MB/sec)
[    2.464420] device-mapper: dm-raid45: initialized v0.2594b
[    2.919016] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.149087] <30>udev[361]: starting version 167
[   15.174419] Adding 2058236k swap on /dev/sda5.  Priority:-1 extents:1 across:2058236k 
[   15.206524] lp: driver loaded but no devices found
[   15.275858] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.055703] r8169 0000:02:00.0: eth0: link down
[   16.064396] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.837171] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   17.176458] cfg80211: Calling CRDA to update world regulatory domain
[   17.276021] Linux video capture interface: v2.00
[   17.280485] cfg80211: World regulatory domain updated:
[   17.280490] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.280495] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.280500] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.280504] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.280508] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.280512] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.299240] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (18e3:9512)
[   17.310479] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input7
[   17.310737] usbcore: registered new interface driver uvcvideo
[   17.310741] USB Video Class driver (v1.0.0)
[   17.408049] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.408068] ath9k 0000:03:00.0: setting latency timer to 64
[   17.479358] ath: EEPROM regdomain: 0x60
[   17.479363] ath: EEPROM indicates we should expect a direct regpair map
[   17.479368] ath: Country alpha2 being used: 00
[   17.479370] ath: Regpair used: 0x60
[   17.479375] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.479379] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479382] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.479387] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479390] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.479394] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479397] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.479401] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479404] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.479409] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479412] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.479416] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479419] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.479423] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479427] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.479431] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479434] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.479438] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479441] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.479445] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479448] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.479453] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479456] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.479460] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479464] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.479468] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.479471] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   17.479476] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.501554] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   17.547740] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.550448] Registered led device: ath9k-phy0::radio
[   17.550552] Registered led device: ath9k-phy0::assoc
[   17.550649] Registered led device: ath9k-phy0::tx
[   17.550744] Registered led device: ath9k-phy0::rx
[   17.550753] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90010a20000, irq=17
[   17.658182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.673852] usbcore: registered new interface driver snd-usb-audio
[   17.691187] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.691267] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   17.691305] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.825673] hda_codec: ALC662 rev1: BIOS auto-probing.
[   17.873921] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.929008] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   17.976379] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   18.005801] usbcore: registered new interface driver ath3k
[   18.040117] usb 3-2: USB disconnect, address 2
[   18.642137] ppdev: user-space parallel port driver
[   19.570062] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   19.866183] Bluetooth: Core ver 2.15
[   19.866225] NET: Registered protocol family 31
[   19.866228] Bluetooth: HCI device and connection manager initialized
[   19.866232] Bluetooth: HCI socket layer initialized
[   19.888925] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.893358] usbcore: registered new interface driver btusb
[   19.955575] Bluetooth: L2CAP ver 2.15
[   19.955580] Bluetooth: L2CAP socket layer initialized
[   19.981817] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.981823] Bluetooth: BNEP filters: protocol multicast
[   20.005858] Bluetooth: SCO (Voice Link) ver 0.6
[   20.005864] Bluetooth: SCO socket layer initialized
[   20.331081] wlan0: authenticate with 00:26:44:98:e0:11 (try 1)
[   20.333093] wlan0: authenticated
[   20.333122] wlan0: associate with 00:26:44:98:e0:11 (try 1)
[   20.336010] wlan0: RX AssocResp from 00:26:44:98:e0:11 (capab=0x411 status=0 aid=2)
[   20.336016] wlan0: associated
[   20.336935] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.090080] Bluetooth: RFCOMM TTY layer initialized
[   21.090088] Bluetooth: RFCOMM socket layer initialized
[   21.090091] Bluetooth: RFCOMM ver 1.11
[   21.286045] Intel AES-NI instructions are not detected.
[   21.310403] padlock_aes: VIA PadLock not detected.
[   21.599115] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   30.590163] wlan0: no IPv6 routers present
```

dmesg when booting straight into Ubuntu Oneiric 11.10 Alpha 2 without booting and logging into linux mint first
```
~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-7-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-4ubuntu2) ) #8-Ubuntu SMP Fri Jul 22 20:26:22 UTC 2011 (Ubuntu 3.0.0-7.8-generic 3.0.0)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=99b86718-bda1-4ecb-a1e8-a1ffc061470e ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dc80000 (usable)
[    0.000000]  BIOS-e820: 000000007dc80000 - 000000007dc8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dc8e000 - 000000007dcd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dcd0000 - 000000007dce0000 (reserved)
[    0.000000]  BIOS-e820: 000000007dcec000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Kogan                           Kogan Agora                    /Kogan Agora                    , BIOS 080016  05/05/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7dc80 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07DD00000 mask FFFF00000 uncachable
[    0.000000]   2 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 07E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000007dc80000
[    0.000000]  0000000000 - 007dc00000 page 2M
[    0.000000]  007dc00000 - 007dc80000 page 4k
[    0.000000] kernel direct mapping tables up to 7dc80000 @ 7dc7c000-7dc80000
[    0.000000] RAMDISK: 365c4000 - 372da000
[    0.000000] ACPI: RSDP 00000000000f9a80 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 000000007dc80100 00074 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007dc80290 000F4 (v03 050511 FACP1430 20110505 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007dc805c0 0707D (v01  U200R U200R123 00000123 INTL 20051117)
[    0.000000] ACPI: FACS 000000007dc8e000 00040
[    0.000000] ACPI: APIC 000000007dc80390 0006C (v01 050511 APIC1430 20110505 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007dc80400 0003C (v01 050511 OEMMCFG  20110505 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007dc80440 00176 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007dc8e040 00073 (v01 050511 OEMB1430 20110505 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007dc8a5c0 00038 (v01 050511 OEMHPET  20110505 MSFT 00000097)
[    0.000000] ACPI: GSCI 000000007dc8e0c0 02024 (v01 050511 GMCHSCI  20110505 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000007dc900f0 00176 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90270 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90810 002D7 (v01  PmRef   CpuPm1 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dc80000
[    0.000000] Initmem setup node 0 0000000000000000-000000007dc80000
[    0.000000]   NODE_DATA [000000007dc77000 - 000000007dc7bfff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007b400000-ffff88007cffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0007dc80
[    0.000000] On node 0 totalpages: 515083
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3918 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6988 pages used for memmap
[    0.000000]   DMA32 zone: 504116 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7de00000 (gap: 7de00000:80f20000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88007da00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508034
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=99b86718-bda1-4ecb-a1e8-a1ffc061470e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2004308k/2060800k available (6095k kernel code, 468k absent, 56024k reserved, 4889k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1300.060 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2600.12 BogoMIPS (lpj=13000600)
[    0.010012] pid_max: default: 32768 minimum: 301
[    0.010056] Security Framework initialized
[    0.010081] AppArmor: AppArmor initialized
[    0.010083] Yama: becoming mindful.
[    0.010464] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011734] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012443] Mount-cache hash table entries: 256
[    0.012654] Initializing cgroup subsys cpuacct
[    0.012663] Initializing cgroup subsys memory
[    0.012677] Initializing cgroup subsys devices
[    0.012680] Initializing cgroup subsys freezer
[    0.012683] Initializing cgroup subsys net_cls
[    0.012686] Initializing cgroup subsys blkio
[    0.012698] Initializing cgroup subsys perf_event
[    0.012745] mce: CPU supports 6 MCE banks
[    0.012758] CPU0: Thermal monitoring handled by SMI
[    0.012764] using mwait in idle threads.
[    0.012826] SMP alternatives: switching to UP code
[    0.033398] ACPI: Core revision 20110413
[    0.040037] ftrace: allocating 25748 entries in 101 pages
[    0.050441] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.151792] CPU0: Genuine Intel(R) CPU           U2700  @ 1.30GHz stepping 0a
[    0.160000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.160000] ... version:                2
[    0.160000] ... bit width:              40
[    0.160000] ... generic registers:      2
[    0.160000] ... value mask:             000000ffffffffff
[    0.160000] ... max period:             000000007fffffff
[    0.160000] ... fixed-purpose events:   3
[    0.160000] ... event mask:             0000000700000003
[    0.160000] Brought up 1 CPUs
[    0.160000] Total of 1 processors activated (2600.12 BogoMIPS).
[    0.160000] devtmpfs: initialized
[    0.160000] PM: Registering ACPI NVS region at 7dc8e000 (270336 bytes)
[    0.160000] print_constraints: dummy: 
[    0.160000] Time:  6:46:02  Date: 07/29/11
[    0.160000] NET: Registered protocol family 16
[    0.160000] ACPI: bus type pci registered
[    0.160000] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.160000] PCI: not using MMCONFIG
[    0.160000] PCI: Using configuration type 1 for base access
[    0.160000] bio: create slab <bio-0> at 0
[    0.160000] ACPI: EC: Look up EC in DSDT
[    0.160000] ACPI: Executed 1 blocks of module-level executable AML code
[    0.162422] ACPI Warning: Incorrect checksum in table [GSCI] - 0x8B, should be 0x1F (20110413/tbutils-314)
[    0.163129] ACPI: Interpreter enabled
[    0.163129] ACPI: (supports S0 S3 S4 S5)
[    0.163129] ACPI: Using IOAPIC for interrupt routing
[    0.163129] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.163129] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.226238] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.226468] ACPI: No dock devices found.
[    0.226471] HEST: Table not found.
[    0.226475] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.226599] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.226853] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.226857] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.226862] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.226866] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.226871] pci_root PNP0A08:00: host bridge window [mem 0x7de00000-0xdfffffff]
[    0.226874] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.226894] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.226925] DMAR: Forcing write-buffer flush capability
[    0.226928] DMAR: Disabling IOMMU for graphics on this chipset
[    0.226957] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.226977] pci 0000:00:02.0: reg 10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.226989] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.226998] pci 0000:00:02.0: reg 20: [io  0xcc00-0xcc07]
[    0.227042] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.227058] pci 0000:00:02.1: reg 10: [mem 0xfe800000-0xfe8fffff 64bit]
[    0.227165] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.227234] pci 0000:00:1a.0: reg 20: [io  0xd400-0xd41f]
[    0.227304] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.227372] pci 0000:00:1a.1: reg 20: [io  0xd080-0xd09f]
[    0.227442] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.227510] pci 0000:00:1a.2: reg 20: [io  0xd000-0xd01f]
[    0.227592] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.227624] pci 0000:00:1a.7: reg 10: [mem 0xfe9ff400-0xfe9ff7ff]
[    0.227731] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.227738] pci 0000:00:1a.7: PME# disabled
[    0.227779] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.227805] pci 0000:00:1b.0: reg 10: [mem 0xfe9f8000-0xfe9fbfff 64bit]
[    0.227899] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.227905] pci 0000:00:1b.0: PME# disabled
[    0.227939] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.228035] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.228041] pci 0000:00:1c.0: PME# disabled
[    0.228078] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.228175] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.228181] pci 0000:00:1c.1: PME# disabled
[    0.228228] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.228297] pci 0000:00:1d.0: reg 20: [io  0xd880-0xd89f]
[    0.228367] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.228436] pci 0000:00:1d.1: reg 20: [io  0xd800-0xd81f]
[    0.228505] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.228574] pci 0000:00:1d.2: reg 20: [io  0xd480-0xd49f]
[    0.228657] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.228689] pci 0000:00:1d.7: reg 10: [mem 0xfe9ff800-0xfe9ffbff]
[    0.228795] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.228802] pci 0000:00:1d.7: PME# disabled
[    0.228832] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.228931] pci 0000:00:1f.0: [8086:2917] type 0 class 0x000601
[    0.229102] pci 0000:00:1f.2: [8086:2928] type 0 class 0x000101
[    0.229130] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.229144] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.229159] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.229173] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.229187] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.229202] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.229267] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.229294] pci 0000:00:1f.3: reg 10: [mem 0xfe9ffc00-0xfe9ffcff 64bit]
[    0.229331] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.229513] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
[    0.229580] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.229699] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.229773] pci 0000:02:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.229822] pci 0000:02:00.0: reg 30: [mem 0xfeae0000-0xfeafffff pref]
[    0.229981] pci 0000:02:00.0: supports D1 D2
[    0.229985] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.230010] pci 0000:02:00.0: PME# disabled
[    0.230188] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.230195] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.230202] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.230212] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.230318] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.230361] pci 0000:03:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.230517] pci 0000:03:00.0: supports D1
[    0.230520] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.230530] pci 0000:03:00.0: PME# disabled
[    0.230615] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.230622] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.230629] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.230639] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.230748] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.230755] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.230762] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.230772] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.230776] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.230780] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.230785] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.230789] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.230793] pci 0000:00:1e.0:   bridge window [mem 0x7de00000-0xdfffffff] (subtractive decode)
[    0.230797] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.230825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.230975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.231124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.231169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.231230]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.231236]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.231239] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.242972] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.243044] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.243108] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.243177] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.243245] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.243315] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.243383] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.243451] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.243593] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.243605] vgaarb: loaded
[    0.243608] vgaarb: bridge control possible 0000:00:02.0
[    0.243872] SCSI subsystem initialized
[    0.243953] libata version 3.00 loaded.
[    0.244015] usbcore: registered new interface driver usbfs
[    0.244030] usbcore: registered new interface driver hub
[    0.244068] usbcore: registered new device driver usb
[    0.244188] PCI: Using ACPI for IRQ routing
[    0.256078] PCI: pci_cache_line_size set to 64 bytes
[    0.256192] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.256196] reserve RAM buffer: 000000007dc80000 - 000000007fffffff 
[    0.256322] NetLabel: Initializing
[    0.256325] NetLabel:  domain hash size = 128
[    0.256328] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.256346] NetLabel:  unlabeled traffic allowed by default
[    0.256403] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.256412] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.256420] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.260050] Switching to clocksource hpet
[    0.268877] AppArmor: AppArmor Filesystem Enabled
[    0.268921] pnp: PnP ACPI init
[    0.268948] ACPI: bus type pnp registered
[    0.269121] pnp 00:00: [bus 00-ff]
[    0.269125] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.269129] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.269133] pnp 00:00: [io  0x0d00-0xffff window]
[    0.269136] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.269140] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.269144] pnp 00:00: [mem 0x7de00000-0xdfffffff window]
[    0.269151] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.269238] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.269253] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.269318] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.269324] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269378] pnp 00:02: [dma 4]
[    0.269381] pnp 00:02: [io  0x0000-0x000f]
[    0.269385] pnp 00:02: [io  0x0081-0x0083]
[    0.269387] pnp 00:02: [io  0x0087]
[    0.269390] pnp 00:02: [io  0x0089-0x008b]
[    0.269393] pnp 00:02: [io  0x008f]
[    0.269396] pnp 00:02: [io  0x00c0-0x00df]
[    0.269430] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.269446] pnp 00:03: [io  0x0070-0x0071]
[    0.269463] pnp 00:03: [irq 8]
[    0.269496] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.269545] pnp 00:04: [io  0x0060]
[    0.269548] pnp 00:04: [io  0x0064]
[    0.269556] pnp 00:04: [irq 1]
[    0.269595] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.269663] pnp 00:05: [irq 12]
[    0.269699] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.269713] pnp 00:06: [io  0x0061]
[    0.269746] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.269760] pnp 00:07: [io  0x00f0-0x00ff]
[    0.269767] pnp 00:07: [irq 13]
[    0.269804] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.269970] Switched to NOHz mode on CPU #0
[    0.270038] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.270043] pnp 00:08: [io  0x0680-0x069f]
[    0.270096] system 00:08: [io  0x0680-0x069f] has been reserved
[    0.270102] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270274] pnp 00:09: [io  0x0010-0x001f]
[    0.270277] pnp 00:09: [io  0x0022-0x003f]
[    0.270281] pnp 00:09: [io  0x0044-0x005f]
[    0.270284] pnp 00:09: [io  0x0063]
[    0.270287] pnp 00:09: [io  0x0065]
[    0.270290] pnp 00:09: [io  0x0067-0x006f]
[    0.270293] pnp 00:09: [io  0x0072-0x007f]
[    0.270296] pnp 00:09: [io  0x0080]
[    0.270299] pnp 00:09: [io  0x0084-0x0086]
[    0.270302] pnp 00:09: [io  0x0088]
[    0.270305] pnp 00:09: [io  0x008c-0x008e]
[    0.270308] pnp 00:09: [io  0x0090-0x009f]
[    0.270312] pnp 00:09: [io  0x00a2-0x00bf]
[    0.270315] pnp 00:09: [io  0x00e0-0x00ef]
[    0.270318] pnp 00:09: [io  0x04d0-0x04d1]
[    0.270321] pnp 00:09: [io  0x0800-0x087f]
[    0.270325] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.270328] pnp 00:09: [io  0x0500-0x057f]
[    0.270332] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.270335] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.270338] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.270416] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.270421] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.270425] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.270430] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.270435] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.270439] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.270444] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270531] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.270569] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.270640] pnp 00:0b: [mem 0xff800000-0xffbfffff]
[    0.270644] pnp 00:0b: [mem 0xffc00000-0xffffffff]
[    0.270681] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.270742] pnp 00:0c: [mem 0xffc00000-0xffbfffff disabled]
[    0.270799] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270912] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.270916] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.270969] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.270974] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.270979] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.271067] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.271122] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.271127] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.271389] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.271393] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.271396] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.271400] pnp 00:0f: [mem 0x00100000-0x7ddfffff]
[    0.271403] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.271476] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.271480] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.271485] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.271489] system 00:0f: [mem 0x00100000-0x7ddfffff] could not be reserved
[    0.271494] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.271499] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.271685] pnp: PnP ACPI: found 16 devices
[    0.271688] ACPI: ACPI bus type pnp unregistered
[    0.278428] PCI: max bus depth: 1 pci_try_num: 2
[    0.278476] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.278483] pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
[    0.278487] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.278492] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.278500] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.278507] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.278518] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.278523] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.278531] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.278538] pci 0000:00:1c.1:   bridge window [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.278548] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.278551] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.278558] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.278564] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.278592] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.278600] pci 0000:00:1c.0: setting latency timer to 64
[    0.278610] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.278621] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.278627] pci 0000:00:1c.1: setting latency timer to 64
[    0.278638] pci 0000:00:1e.0: setting latency timer to 64
[    0.278644] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.278648] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.278652] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.278655] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.278659] pci_bus 0000:00: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.278663] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.278667] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.278671] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.278675] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.278679] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.278683] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.278687] pci_bus 0000:03: resource 2 [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.278691] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.278695] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.278699] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.278702] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.278706] pci_bus 0000:01: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.278710] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.278765] NET: Registered protocol family 2
[    0.278910] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.279818] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.282386] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.283073] TCP: Hash tables configured (established 262144 bind 65536)
[    0.283076] TCP reno registered
[    0.283086] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.283117] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.283308] NET: Registered protocol family 1
[    0.283333] pci 0000:00:02.0: Boot video device
[    0.283529] PCI: CLS 32 bytes, default 64
[    0.283982] audit: initializing netlink socket (disabled)
[    0.283996] type=2000 audit(1311921962.280:1): initialized
[    0.319524] Trying to unpack rootfs image as initramfs...
[    0.370260] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.400384] VFS: Disk quotas dquot_6.5.2
[    0.400472] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.401332] fuse init (API version 7.16)
[    0.401458] msgmni has been set to 3914
[    0.410367] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.410408] io scheduler noop registered
[    0.410411] io scheduler deadline registered
[    0.410476] io scheduler cfq registered (default)
[    0.410621] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.410694] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.410791] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.410855] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.410972] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.411007] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.411063] intel_idle: MWAIT substates: 0x22220
[    0.411066] intel_idle: does not run on family 6 model 23
[    0.412253] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.414612] ACPI: AC Adapter [AC] (on-line)
[    0.414708] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C09:00/PNP0C0D:00/input/input0
[    0.416583] ACPI: Lid Switch [LID]
[    0.416652] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.416659] ACPI: Sleep Button [SLPB]
[    0.416715] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.416721] ACPI: Power Button [PWRB]
[    0.416780] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.416785] ACPI: Power Button [PWRF]
[    0.416820] ACPI: acpi_idle registered with cpuidle
[    0.420050] Monitor-Mwait will be used to enter C-1 state
[    0.430108] Monitor-Mwait will be used to enter C-2 state
[    0.430169] Monitor-Mwait will be used to enter C-3 state
[    0.430177] Marking TSC unstable due to TSC halts in idle
[    0.432357] ACPI: Invalid active0 threshold
[    0.432501] thermal LNXTHERM:00: registered as thermal_zone0
[    0.432505] ACPI: Thermal Zone [TZ01] (42 C)
[    0.432532] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.432586] ERST: Table is not found!
[    0.432690] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.434515] Linux agpgart interface v0.103
[    0.434593] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.434738] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.435672] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.435811] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.437312] brd: module loaded
[    0.437993] loop: module loaded
[    0.438173] ata_piix 0000:00:1f.2: version 2.13
[    0.438201] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.438209] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.438262] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.438661] scsi0 : ata_piix
[    0.438775] scsi1 : ata_piix
[    0.440314] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.440321] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.440865] Fixed MDIO Bus: probed
[    0.440897] PPP generic driver version 2.4.2
[    0.440949] tun: Universal TUN/TAP device driver, 1.6
[    0.440952] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.441058] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.441086] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441107] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.441112] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.441169] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.441206] ehci_hcd 0000:00:1a.7: debug port 1
[    0.445091] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.446529] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9ff400
[    0.472201] ACPI: Battery Slot [BAT0] (battery present)
[    0.480122] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.480336] hub 1-0:1.0: USB hub found
[    0.480343] hub 1-0:1.0: 6 ports detected
[    0.480452] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.480479] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.480484] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.480550] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.480590] ehci_hcd 0000:00:1d.7: debug port 1
[    0.484489] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.484516] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    0.500261] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.500448] hub 2-0:1.0: USB hub found
[    0.500456] hub 2-0:1.0: 6 ports detected
[    0.500555] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.500575] uhci_hcd: USB Universal Host Controller Interface driver
[    0.500632] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.500643] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.500648] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.500712] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.500762] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d400
[    0.500919] hub 3-0:1.0: USB hub found
[    0.500925] hub 3-0:1.0: 2 ports detected
[    0.501009] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.501018] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.501024] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.501077] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.501124] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d080
[    0.501282] hub 4-0:1.0: USB hub found
[    0.501288] hub 4-0:1.0: 2 ports detected
[    0.501361] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.501370] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.501375] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.501418] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.501462] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d000
[    0.501621] hub 5-0:1.0: USB hub found
[    0.501627] hub 5-0:1.0: 2 ports detected
[    0.501704] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.501713] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.501718] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.501762] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.501795] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.501960] hub 6-0:1.0: USB hub found
[    0.501966] hub 6-0:1.0: 2 ports detected
[    0.502035] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.502044] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.502049] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.502106] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.502141] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.502291] hub 7-0:1.0: USB hub found
[    0.502297] hub 7-0:1.0: 2 ports detected
[    0.502370] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.502378] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.502383] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.502431] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.502466] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.502622] hub 8-0:1.0: USB hub found
[    0.502628] hub 8-0:1.0: 2 ports detected
[    0.502785] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.509637] i8042: Detected active multiplexing controller, rev 1.1
[    0.530298] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.530313] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.530364] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.530400] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.530432] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.530601] mousedev: PS/2 mouse device common for all mice
[    0.530835] rtc_cmos 00:03: RTC can wake from S4
[    0.530972] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.531008] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.531177] device-mapper: uevent: version 1.0.3
[    0.531278] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.531368] device-mapper: multipath: version 1.3.0 loaded
[    0.531372] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.531514] cpuidle: using governor ladder
[    0.531574] cpuidle: using governor menu
[    0.531577] EFI Variables Facility v0.08 2004-May-17
[    0.531924] TCP cubic registered
[    0.532105] NET: Registered protocol family 10
[    0.532728] NET: Registered protocol family 17
[    0.532752] Registering the dns_resolver key type
[    0.532894] PM: Hibernation image not present or could not be loaded.
[    0.532910] registered taskstats version 1
[    0.541795]   Magic number: 3:57:773
[    0.541813] hub 2-0:1.0: hash matches
[    0.541923] rtc_cmos 00:03: setting system clock to 2011-07-29 06:46:02 UTC (1311921962)
[    0.542077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.542080] EDD information not available.
[    0.560321] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.801438] ata1: SATA link down (SStatus 0 SControl 300)
[    0.844796] Freeing initrd memory: 13400k freed
[    0.920189] usb 2-2: new high speed USB device number 2 using ehci_hcd
[    0.970089] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.990386] ata2.00: ATA-8: WDC WD5000BEVT-24A0RT0, 01.01A02, max UDMA/133
[    0.990391] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.030527] ata2.00: configured for UDMA/133
[    1.030720] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.030966] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.031070] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.031150] sd 1:0:0:0: [sda] Write Protect is off
[    1.031155] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.031190] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.114940]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.115388] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.118319] Freeing unused kernel memory: 984k freed
[    1.118785] Write protecting the kernel read-only data: 10240k
[    1.119162] Freeing unused kernel memory: 32k freed
[    1.127385] Freeing unused kernel memory: 1412k freed
[    1.152759] udevd[64]: starting version 172
[    1.336884] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.336944] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.338393] r8169 0000:02:00.0: setting latency timer to 64
[    1.341185] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.347452] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc9000033c000, 00:24:25:0d:50:d8, XID 04c00000 IRQ 42
[    1.550040] usb 3-2: new full speed USB device number 2 using uhci_hcd
[    1.929565] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.980049] usb 8-2: new low speed USB device number 2 using uhci_hcd
[   10.643198] udevd[279]: starting version 172
[   10.693315] lp: driver loaded but no devices found
[   10.759862] Adding 2051068k swap on /dev/sda7.  Priority:-1 extents:1 across:2051068k 
[   10.931727] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   11.158683] [drm] Initialized drm 1.1.0 20060810
[   11.206108] type=1400 audit(1311921973.149:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=478 comm="apparmor_parser"
[   11.207585] type=1400 audit(1311921973.149:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[   11.208516] type=1400 audit(1311921973.149:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[   11.677876] r8169 0000:02:00.0: eth0: link down
[   11.680544] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.702354] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.702363] i915 0000:00:02.0: setting latency timer to 64
[   11.893461] cfg80211: Calling CRDA to update world regulatory domain
[   12.038362] Linux video capture interface: v2.00
[   12.176142] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (18e3:9512)
[   12.176246] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input5
[   12.176534] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:1d.2-2/input0
[   12.176592] usbcore: registered new interface driver usbhid
[   12.176596] usbhid: USB HID core driver
[   12.177623] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.177643] ath9k 0000:03:00.0: setting latency timer to 64
[   12.236939] ath: EEPROM regdomain: 0x60
[   12.236943] ath: EEPROM indicates we should expect a direct regpair map
[   12.236949] ath: Country alpha2 being used: 00
[   12.236951] ath: Regpair used: 0x60
[   12.236956] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.236962] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.236965] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.236970] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.236973] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.236977] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.236981] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.236985] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.236989] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.236993] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.236997] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.237001] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237004] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.237009] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237012] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.237017] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237020] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.237024] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237028] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.237032] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237036] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.237040] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237062] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.237067] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237070] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.237074] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.237078] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.237082] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.325677] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input6
[   12.327307] usbcore: registered new interface driver uvcvideo
[   12.327312] USB Video Class driver (v1.1.0)
[   12.359837] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   12.359847] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.359850] [drm] Driver supports precise vblank timestamp query.
[   12.359910] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.453321] type=1400 audit(1311921974.399:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=696 comm="apparmor_parser"
[   12.455142] type=1400 audit(1311921974.399:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=696 comm="apparmor_parser"
[   12.456072] type=1400 audit(1311921974.399:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=696 comm="apparmor_parser"
[   12.469272] type=1400 audit(1311921974.409:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=697 comm="apparmor_parser"
[   12.520616] type=1400 audit(1311921974.469:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=697 comm="apparmor_parser"
[   12.527598] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   12.566801] type=1400 audit(1311921974.509:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=697 comm="apparmor_parser"
[   12.569721] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.584876] Registered led device: ath9k-phy0
[   12.584890] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90000340000, irq=17
[   12.611778] type=1400 audit(1311921974.559:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=713 comm="apparmor_parser"
[   12.662859] usbcore: registered new interface driver snd-usb-audio
[   12.751828] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
[   12.806183] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   12.856940] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   13.074416] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   13.103347] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.103357] cfg80211: World regulatory domain updated:
[   13.103360] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.103365] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.103369] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.103373] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.103377] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.103382] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.355751] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.601324] Bluetooth: Core ver 2.16
[   13.601413] NET: Registered protocol family 31
[   13.601417] Bluetooth: HCI device and connection manager initialized
[   13.601421] Bluetooth: HCI socket layer initialized
[   13.601423] Bluetooth: L2CAP socket layer initialized
[   13.602030] Bluetooth: SCO socket layer initialized
[   13.605321] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.605326] Bluetooth: BNEP filters: protocol multicast
[   13.694865] fbcon: inteldrmfb (fb0) is primary device
[   13.696240] Console: switching to colour frame buffer device 170x48
[   13.696278] fb0: inteldrmfb frame buffer device
[   13.696280] drm: registered panic notifier
[   13.704481] Bluetooth: RFCOMM TTY layer initialized
[   13.704490] Bluetooth: RFCOMM socket layer initialized
[   13.704493] Bluetooth: RFCOMM ver 1.11
[   13.708036] acpi device:2d: registered as cooling_device1
[   13.709267] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   13.709465] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.711423] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.711489] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.711568] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.711607] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.833887] hda_codec: ALC662 rev1: BIOS auto-probing.
[   13.851911] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   13.911438] input: HDA Intel HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   13.912704] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.332244] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   15.852942] init: plymouth-stop pre-start process (1154) terminated with status 1
[   16.324479] wlan0: authenticate with 00:26:44:98:e0:11 (try 1)
[   16.337929] wlan0: authenticated
[   16.363194] wlan0: associate with 00:26:44:98:e0:11 (try 1)
[   16.384288] wlan0: RX AssocResp from 00:26:44:98:e0:11 (capab=0x411 status=0 aid=2)
[   16.384294] wlan0: associated
[   16.384975] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.598864] Intel AES-NI instructions are not detected.
[   16.602594] padlock_aes: VIA PadLock not detected.
[   17.369837] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   18.191875] ath3k_load_firmware: Can't change to loading configuration err
[   18.191926] ath3k: probe of 3-2:1.0 failed with error -110
[   18.191975] usbcore: registered new interface driver ath3k
[   18.236314] ppdev: user-space parallel port driver
[   18.254607] audit_printk_skb: 12 callbacks suppressed
[   18.254613] type=1400 audit(1311921980.199:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1265 comm="apparmor_parser"
[   18.262654] type=1400 audit(1311921980.209:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1265 comm="apparmor_parser"
[   26.670029] wlan0: no IPv6 routers present
```

then if I boot and login to Linux Mint 11 then do a reboot into Ubuntu Oneiric 11.10 Alpha 2 the dmesg I get is
```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-7-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-4ubuntu2) ) #8-Ubuntu SMP Fri Jul 22 20:26:22 UTC 2011 (Ubuntu 3.0.0-7.8-generic 3.0.0)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=99b86718-bda1-4ecb-a1e8-a1ffc061470e ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dc80000 (usable)
[    0.000000]  BIOS-e820: 000000007dc80000 - 000000007dc8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dc8e000 - 000000007dcd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dcd0000 - 000000007dce0000 (reserved)
[    0.000000]  BIOS-e820: 000000007dcec000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Kogan                           Kogan Agora                    /Kogan Agora                    , BIOS 080016  05/05/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7dc80 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07DD00000 mask FFFF00000 uncachable
[    0.000000]   2 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 07E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000007dc80000
[    0.000000]  0000000000 - 007dc00000 page 2M
[    0.000000]  007dc00000 - 007dc80000 page 4k
[    0.000000] kernel direct mapping tables up to 7dc80000 @ 7dc7c000-7dc80000
[    0.000000] RAMDISK: 365c4000 - 372da000
[    0.000000] ACPI: RSDP 00000000000f9a80 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 000000007dc80100 00074 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007dc80290 000F4 (v03 050511 FACP1430 20110505 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007dc805c0 0707D (v01  U200R U200R123 00000123 INTL 20051117)
[    0.000000] ACPI: FACS 000000007dc8e000 00040
[    0.000000] ACPI: APIC 000000007dc80390 0006C (v01 050511 APIC1430 20110505 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007dc80400 0003C (v01 050511 OEMMCFG  20110505 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000007dc80440 00176 (v01 NEC             20110505 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007dc8e040 00073 (v01 050511 OEMB1430 20110505 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007dc8a5c0 00038 (v01 050511 OEMHPET  20110505 MSFT 00000097)
[    0.000000] ACPI: GSCI 000000007dc8e0c0 02024 (v01 050511 GMCHSCI  20110505 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000007dc900f0 00176 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90270 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.000000] ACPI: SSDT 000000007dc90810 002D7 (v01  PmRef   CpuPm1 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dc80000
[    0.000000] Initmem setup node 0 0000000000000000-000000007dc80000
[    0.000000]   NODE_DATA [000000007dc77000 - 000000007dc7bfff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007b400000-ffff88007cffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0007dc80
[    0.000000] On node 0 totalpages: 515083
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3918 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6988 pages used for memmap
[    0.000000]   DMA32 zone: 504116 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7de00000 (gap: 7de00000:80f20000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88007da00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508034
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=99b86718-bda1-4ecb-a1e8-a1ffc061470e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2004308k/2060800k available (6095k kernel code, 468k absent, 56024k reserved, 4889k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1299.931 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2599.86 BogoMIPS (lpj=12999310)
[    0.010012] pid_max: default: 32768 minimum: 301
[    0.010058] Security Framework initialized
[    0.010083] AppArmor: AppArmor initialized
[    0.010085] Yama: becoming mindful.
[    0.010470] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011734] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012445] Mount-cache hash table entries: 256
[    0.012656] Initializing cgroup subsys cpuacct
[    0.012665] Initializing cgroup subsys memory
[    0.012679] Initializing cgroup subsys devices
[    0.012682] Initializing cgroup subsys freezer
[    0.012685] Initializing cgroup subsys net_cls
[    0.012688] Initializing cgroup subsys blkio
[    0.012699] Initializing cgroup subsys perf_event
[    0.012748] mce: CPU supports 6 MCE banks
[    0.012760] CPU0: Thermal monitoring handled by SMI
[    0.012767] using mwait in idle threads.
[    0.012828] SMP alternatives: switching to UP code
[    0.033401] ACPI: Core revision 20110413
[    0.040037] ftrace: allocating 25748 entries in 101 pages
[    0.050443] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.151308] CPU0: Genuine Intel(R) CPU           U2700  @ 1.30GHz stepping 0a
[    0.160000] APIC calibration not consistent with PM-Timer: 109ms instead of 100ms
[    0.160000] APIC delta adjusted to PM-Timer: 1250043 (1375047)
[    0.160000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.160000] ... version:                2
[    0.160000] ... bit width:              40
[    0.160000] ... generic registers:      2
[    0.160000] ... value mask:             000000ffffffffff
[    0.160000] ... max period:             000000007fffffff
[    0.160000] ... fixed-purpose events:   3
[    0.160000] ... event mask:             0000000700000003
[    0.160000] Brought up 1 CPUs
[    0.160000] Total of 1 processors activated (2599.86 BogoMIPS).
[    0.160000] devtmpfs: initialized
[    0.160000] PM: Registering ACPI NVS region at 7dc8e000 (270336 bytes)
[    0.160000] print_constraints: dummy: 
[    0.160000] Time:  4:58:30  Date: 07/29/11
[    0.160000] NET: Registered protocol family 16
[    0.160000] ACPI: bus type pci registered
[    0.160000] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.160000] PCI: not using MMCONFIG
[    0.160000] PCI: Using configuration type 1 for base access
[    0.160000] bio: create slab <bio-0> at 0
[    0.160000] ACPI: EC: Look up EC in DSDT
[    0.160000] ACPI: Executed 1 blocks of module-level executable AML code
[    0.162422] ACPI Warning: Incorrect checksum in table [GSCI] - 0x8B, should be 0x0B (20110413/tbutils-314)
[    0.163131] ACPI: Interpreter enabled
[    0.163131] ACPI: (supports S0 S3 S4 S5)
[    0.163131] ACPI: Using IOAPIC for interrupt routing
[    0.163131] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.163131] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.226135] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.226366] ACPI: No dock devices found.
[    0.226369] HEST: Table not found.
[    0.226373] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.226496] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.226749] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.226755] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.226759] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.226763] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.226767] pci_root PNP0A08:00: host bridge window [mem 0x7de00000-0xdfffffff]
[    0.226771] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.226790] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.226821] DMAR: Forcing write-buffer flush capability
[    0.226823] DMAR: Disabling IOMMU for graphics on this chipset
[    0.226854] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.226873] pci 0000:00:02.0: reg 10: [mem 0xfe400000-0xfe7fffff 64bit]
[    0.226885] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.226894] pci 0000:00:02.0: reg 20: [io  0xcc00-0xcc07]
[    0.226938] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.226954] pci 0000:00:02.1: reg 10: [mem 0xfe800000-0xfe8fffff 64bit]
[    0.227062] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.227131] pci 0000:00:1a.0: reg 20: [io  0xd400-0xd41f]
[    0.227200] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.227269] pci 0000:00:1a.1: reg 20: [io  0xd080-0xd09f]
[    0.227338] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.227407] pci 0000:00:1a.2: reg 20: [io  0xd000-0xd01f]
[    0.227489] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.227520] pci 0000:00:1a.7: reg 10: [mem 0xfe9ff400-0xfe9ff7ff]
[    0.227627] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.227635] pci 0000:00:1a.7: PME# disabled
[    0.227675] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.227701] pci 0000:00:1b.0: reg 10: [mem 0xfe9f8000-0xfe9fbfff 64bit]
[    0.227794] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.227801] pci 0000:00:1b.0: PME# disabled
[    0.227834] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.227931] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.227937] pci 0000:00:1c.0: PME# disabled
[    0.227973] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.228069] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.228076] pci 0000:00:1c.1: PME# disabled
[    0.228122] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.228190] pci 0000:00:1d.0: reg 20: [io  0xd880-0xd89f]
[    0.228260] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.228328] pci 0000:00:1d.1: reg 20: [io  0xd800-0xd81f]
[    0.228397] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.228466] pci 0000:00:1d.2: reg 20: [io  0xd480-0xd49f]
[    0.228548] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.228579] pci 0000:00:1d.7: reg 10: [mem 0xfe9ff800-0xfe9ffbff]
[    0.228685] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.228692] pci 0000:00:1d.7: PME# disabled
[    0.228723] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.228822] pci 0000:00:1f.0: [8086:2917] type 0 class 0x000601
[    0.228992] pci 0000:00:1f.2: [8086:2928] type 0 class 0x000101
[    0.229020] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.229035] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.229049] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.229063] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.229078] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.229092] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.229157] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.229184] pci 0000:00:1f.3: reg 10: [mem 0xfe9ffc00-0xfe9ffcff 64bit]
[    0.229220] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.229381] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
[    0.229448] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.229566] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.229640] pci 0000:02:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.229689] pci 0000:02:00.0: reg 30: [mem 0xfeae0000-0xfeafffff pref]
[    0.229853] pci 0000:02:00.0: supports D1 D2
[    0.229856] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.229872] pci 0000:02:00.0: PME# disabled
[    0.230051] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.230058] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.230065] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.230075] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.230180] pci 0000:03:00.0: [168c:002b] type 0 class 0x000280
[    0.230222] pci 0000:03:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.230378] pci 0000:03:00.0: supports D1
[    0.230381] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.230391] pci 0000:03:00.0: PME# disabled
[    0.230472] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.230479] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.230486] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.230496] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.230601] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.230608] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.230616] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.230626] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.230630] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.230634] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.230639] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.230643] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.230647] pci 0000:00:1e.0:   bridge window [mem 0x7de00000-0xdfffffff] (subtractive decode)
[    0.230651] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.230679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.230830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.230979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.231023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.231085]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.231090]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.231093] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.242816] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.242887] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.242951] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.243020] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.243088] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.243158] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.243226] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.243294] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.243437] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.243449] vgaarb: loaded
[    0.243451] vgaarb: bridge control possible 0000:00:02.0
[    0.243716] SCSI subsystem initialized
[    0.243796] libata version 3.00 loaded.
[    0.243859] usbcore: registered new interface driver usbfs
[    0.243873] usbcore: registered new interface driver hub
[    0.243911] usbcore: registered new device driver usb
[    0.244032] PCI: Using ACPI for IRQ routing
[    0.255911] PCI: pci_cache_line_size set to 64 bytes
[    0.256018] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.256022] reserve RAM buffer: 000000007dc80000 - 000000007fffffff 
[    0.256149] NetLabel: Initializing
[    0.256152] NetLabel:  domain hash size = 128
[    0.256154] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.256173] NetLabel:  unlabeled traffic allowed by default
[    0.256231] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.256240] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.256247] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.260050] Switching to clocksource hpet
[    0.268881] AppArmor: AppArmor Filesystem Enabled
[    0.268924] pnp: PnP ACPI init
[    0.268952] ACPI: bus type pnp registered
[    0.269124] pnp 00:00: [bus 00-ff]
[    0.269129] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.269133] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.269136] pnp 00:00: [io  0x0d00-0xffff window]
[    0.269140] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.269144] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.269148] pnp 00:00: [mem 0x7de00000-0xdfffffff window]
[    0.269155] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.269241] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.269256] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.269319] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.269324] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269379] pnp 00:02: [dma 4]
[    0.269383] pnp 00:02: [io  0x0000-0x000f]
[    0.269386] pnp 00:02: [io  0x0081-0x0083]
[    0.269389] pnp 00:02: [io  0x0087]
[    0.269391] pnp 00:02: [io  0x0089-0x008b]
[    0.269394] pnp 00:02: [io  0x008f]
[    0.269397] pnp 00:02: [io  0x00c0-0x00df]
[    0.269431] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.269447] pnp 00:03: [io  0x0070-0x0071]
[    0.269464] pnp 00:03: [irq 8]
[    0.269497] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.269545] pnp 00:04: [io  0x0060]
[    0.269548] pnp 00:04: [io  0x0064]
[    0.269556] pnp 00:04: [irq 1]
[    0.269596] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.269665] pnp 00:05: [irq 12]
[    0.269701] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.269716] pnp 00:06: [io  0x0061]
[    0.269748] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.269762] pnp 00:07: [io  0x00f0-0x00ff]
[    0.269770] pnp 00:07: [irq 13]
[    0.269807] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.269972] Switched to NOHz mode on CPU #0
[    0.270044] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.270048] pnp 00:08: [io  0x0680-0x069f]
[    0.270102] system 00:08: [io  0x0680-0x069f] has been reserved
[    0.270108] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270280] pnp 00:09: [io  0x0010-0x001f]
[    0.270284] pnp 00:09: [io  0x0022-0x003f]
[    0.270287] pnp 00:09: [io  0x0044-0x005f]
[    0.270290] pnp 00:09: [io  0x0063]
[    0.270293] pnp 00:09: [io  0x0065]
[    0.270296] pnp 00:09: [io  0x0067-0x006f]
[    0.270300] pnp 00:09: [io  0x0072-0x007f]
[    0.270303] pnp 00:09: [io  0x0080]
[    0.270306] pnp 00:09: [io  0x0084-0x0086]
[    0.270309] pnp 00:09: [io  0x0088]
[    0.270312] pnp 00:09: [io  0x008c-0x008e]
[    0.270315] pnp 00:09: [io  0x0090-0x009f]
[    0.270318] pnp 00:09: [io  0x00a2-0x00bf]
[    0.270321] pnp 00:09: [io  0x00e0-0x00ef]
[    0.270324] pnp 00:09: [io  0x04d0-0x04d1]
[    0.270327] pnp 00:09: [io  0x0800-0x087f]
[    0.270331] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.270334] pnp 00:09: [io  0x0500-0x057f]
[    0.270338] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.270341] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.270344] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.270421] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.270426] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.270430] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.270435] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.270440] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.270445] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.270450] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270537] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.270575] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.270646] pnp 00:0b: [mem 0xff800000-0xffbfffff]
[    0.270650] pnp 00:0b: [mem 0xffc00000-0xffffffff]
[    0.270687] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.270748] pnp 00:0c: [mem 0xffc00000-0xffbfffff disabled]
[    0.270805] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.270918] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.270922] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.270975] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.270980] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.270986] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.271074] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.271129] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.271135] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.271398] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.271402] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.271405] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.271409] pnp 00:0f: [mem 0x00100000-0x7ddfffff]
[    0.271412] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.271484] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.271489] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.271494] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.271498] system 00:0f: [mem 0x00100000-0x7ddfffff] could not be reserved
[    0.271503] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.271508] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.271694] pnp: PnP ACPI: found 16 devices
[    0.271697] ACPI: ACPI bus type pnp unregistered
[    0.278435] PCI: max bus depth: 1 pci_try_num: 2
[    0.278483] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.278489] pci 0000:00:1c.1: BAR 13: assigned [io  0x1000-0x1fff]
[    0.278494] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.278499] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.278507] pci 0000:00:1c.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.278514] pci 0000:00:1c.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.278524] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.278529] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.278537] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.278544] pci 0000:00:1c.1:   bridge window [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.278554] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.278557] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.278565] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.278571] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.278600] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.278607] pci 0000:00:1c.0: setting latency timer to 64
[    0.278617] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.278628] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.278634] pci 0000:00:1c.1: setting latency timer to 64
[    0.278645] pci 0000:00:1e.0: setting latency timer to 64
[    0.278651] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.278655] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.278659] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.278662] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.278666] pci_bus 0000:00: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.278670] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.278674] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.278678] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.278682] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.278686] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.278690] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.278694] pci_bus 0000:03: resource 2 [mem 0x7de00000-0x7dffffff 64bit pref]
[    0.278698] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.278702] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.278705] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.278709] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.278713] pci_bus 0000:01: resource 8 [mem 0x7de00000-0xdfffffff]
[    0.278717] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.278776] NET: Registered protocol family 2
[    0.278920] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.279830] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.282395] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.283081] TCP: Hash tables configured (established 262144 bind 65536)
[    0.283084] TCP reno registered
[    0.283095] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.283124] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.283315] NET: Registered protocol family 1
[    0.283340] pci 0000:00:02.0: Boot video device
[    0.283541] PCI: CLS 32 bytes, default 64
[    0.283995] audit: initializing netlink socket (disabled)
[    0.284010] type=2000 audit(1311915510.280:1): initialized
[    0.319537] Trying to unpack rootfs image as initramfs...
[    0.370281] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.400366] VFS: Disk quotas dquot_6.5.2
[    0.400453] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.401310] fuse init (API version 7.16)
[    0.401435] msgmni has been set to 3914
[    0.410342] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.410382] io scheduler noop registered
[    0.410385] io scheduler deadline registered
[    0.410449] io scheduler cfq registered (default)
[    0.410595] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.410668] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.410765] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.410828] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.410945] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.410980] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.411036] intel_idle: MWAIT substates: 0x22220
[    0.411039] intel_idle: does not run on family 6 model 23
[    0.413557] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.415712] ACPI: AC Adapter [AC] (on-line)
[    0.415811] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C09:00/PNP0C0D:00/input/input0
[    0.417052] ACPI: Lid Switch [LID]
[    0.417120] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.417127] ACPI: Sleep Button [SLPB]
[    0.417183] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.417189] ACPI: Power Button [PWRB]
[    0.417244] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.417249] ACPI: Power Button [PWRF]
[    0.417283] ACPI: acpi_idle registered with cpuidle
[    0.420048] Monitor-Mwait will be used to enter C-1 state
[    0.430119] Monitor-Mwait will be used to enter C-2 state
[    0.430177] Monitor-Mwait will be used to enter C-3 state
[    0.430185] Marking TSC unstable due to TSC halts in idle
[    0.432359] ACPI: Invalid active0 threshold
[    0.432504] thermal LNXTHERM:00: registered as thermal_zone0
[    0.432508] ACPI: Thermal Zone [TZ01] (43 C)
[    0.432535] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.432589] ERST: Table is not found!
[    0.432691] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.434520] Linux agpgart interface v0.103
[    0.434598] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.434744] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.435677] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.435815] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.437319] brd: module loaded
[    0.438000] loop: module loaded
[    0.438179] ata_piix 0000:00:1f.2: version 2.13
[    0.438208] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.438217] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.438268] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.438666] scsi0 : ata_piix
[    0.438779] scsi1 : ata_piix
[    0.440383] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.440390] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.440932] Fixed MDIO Bus: probed
[    0.440964] PPP generic driver version 2.4.2
[    0.441018] tun: Universal TUN/TAP device driver, 1.6
[    0.441021] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.441127] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.441155] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441175] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.441180] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.441237] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.441347] ehci_hcd 0000:00:1a.7: debug port 1
[    0.445241] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.450108] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9ff400
[    0.465996] ACPI: Battery Slot [BAT0] (battery present)
[    0.470490] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.470704] hub 1-0:1.0: USB hub found
[    0.470712] hub 1-0:1.0: 6 ports detected
[    0.470819] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.470844] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.470849] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.470912] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.470952] ehci_hcd 0000:00:1d.7: debug port 1
[    0.474843] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.474868] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    0.490210] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.490395] hub 2-0:1.0: USB hub found
[    0.490403] hub 2-0:1.0: 6 ports detected
[    0.490499] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.490518] uhci_hcd: USB Universal Host Controller Interface driver
[    0.490573] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.490584] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.490589] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.490644] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.490693] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d400
[    0.490852] hub 3-0:1.0: USB hub found
[    0.490858] hub 3-0:1.0: 2 ports detected
[    0.490944] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.490953] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.490958] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.491013] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.491055] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d080
[    0.491213] hub 4-0:1.0: USB hub found
[    0.491220] hub 4-0:1.0: 2 ports detected
[    0.491292] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.491301] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.491306] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.491361] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.491407] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d000
[    0.491561] hub 5-0:1.0: USB hub found
[    0.491567] hub 5-0:1.0: 2 ports detected
[    0.491644] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.491653] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.491658] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.491701] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.491734] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    0.491901] hub 6-0:1.0: USB hub found
[    0.491907] hub 6-0:1.0: 2 ports detected
[    0.491976] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.491985] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.491989] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.492046] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.492083] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.492232] hub 7-0:1.0: USB hub found
[    0.492241] hub 7-0:1.0: 2 ports detected
[    0.492313] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.492322] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.492327] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.492374] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.492407] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    0.492559] hub 8-0:1.0: USB hub found
[    0.492565] hub 8-0:1.0: 2 ports detected
[    0.492721] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.499476] i8042: Detected active multiplexing controller, rev 1.1
[    0.520431] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.520446] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.520497] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.520533] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.520565] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.520737] mousedev: PS/2 mouse device common for all mice
[    0.520970] rtc_cmos 00:03: RTC can wake from S4
[    0.521106] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.521140] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.521310] device-mapper: uevent: version 1.0.3
[    0.521415] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.521503] device-mapper: multipath: version 1.3.0 loaded
[    0.521507] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.521649] cpuidle: using governor ladder
[    0.521709] cpuidle: using governor menu
[    0.521712] EFI Variables Facility v0.08 2004-May-17
[    0.522058] TCP cubic registered
[    0.522240] NET: Registered protocol family 10
[    0.522865] NET: Registered protocol family 17
[    0.522892] Registering the dns_resolver key type
[    0.523038] PM: Hibernation image not present or could not be loaded.
[    0.523053] registered taskstats version 1
[    0.531724]   Magic number: 3:51:971
[    0.531847] rtc_cmos 00:03: setting system clock to 2011-07-29 04:58:30 UTC (1311915510)
[    0.532002] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.532005] EDD information not available.
[    0.549397] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.811679] ata1: SATA link down (SStatus 0 SControl 300)
[    0.845838] Freeing initrd memory: 13400k freed
[    0.910189] usb 2-2: new high speed USB device number 2 using ehci_hcd
[    0.970088] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.990520] ata2.00: ATA-8: WDC WD5000BEVT-24A0RT0, 01.01A02, max UDMA/133
[    0.990525] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.030517] ata2.00: configured for UDMA/133
[    1.030726] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.030962] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.031067] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.031147] sd 1:0:0:0: [sda] Write Protect is off
[    1.031152] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.031187] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.117320]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.117765] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.120714] Freeing unused kernel memory: 984k freed
[    1.121181] Write protecting the kernel read-only data: 10240k
[    1.121559] Freeing unused kernel memory: 32k freed
[    1.129748] Freeing unused kernel memory: 1412k freed
[    1.155065] udevd[64]: starting version 172
[    1.368091] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.368126] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.368229] r8169 0000:02:00.0: setting latency timer to 64
[    1.368424] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.369025] r8169 0000:02:00.0: eth0: RTL8102e at 0xffffc9000033c000, 00:24:25:0d:50:d8, XID 04c00000 IRQ 42
[    1.540150] usb 3-2: new full speed USB device number 2 using uhci_hcd
[    1.915109] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.980059] usb 8-2: new low speed USB device number 2 using uhci_hcd
[   10.645558] udevd[277]: starting version 172
[   10.702622] lp: driver loaded but no devices found
[   10.787450] Adding 2051068k swap on /dev/sda7.  Priority:-1 extents:1 across:2051068k 
[   10.978509] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   11.103127] [drm] Initialized drm 1.1.0 20060810
[   11.236649] type=1400 audit(1311915521.191:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=490 comm="apparmor_parser"
[   11.238384] type=1400 audit(1311915521.191:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 comm="apparmor_parser"
[   11.239314] type=1400 audit(1311915521.191:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm="apparmor_parser"
[   11.470152] r8169 0000:02:00.0: eth0: link down
[   11.473670] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.551132] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.551140] i915 0000:00:02.0: setting latency timer to 64
[   11.707548] cfg80211: Calling CRDA to update world regulatory domain
[   11.758367] Bluetooth: Core ver 2.16
[   11.758600] NET: Registered protocol family 31
[   11.758604] Bluetooth: HCI device and connection manager initialized
[   11.758607] Bluetooth: HCI socket layer initialized
[   11.758610] Bluetooth: L2CAP socket layer initialized
[   11.761223] Bluetooth: SCO socket layer initialized
[   11.778256] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.782660] usbcore: registered new interface driver btusb
[   12.022644] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.022667] ath9k 0000:03:00.0: setting latency timer to 64
[   12.186148] type=1400 audit(1311915522.141:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=668 comm="apparmor_parser"
[   12.189676] type=1400 audit(1311915522.141:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=668 comm="apparmor_parser"
[   12.190669] type=1400 audit(1311915522.151:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=668 comm="apparmor_parser"
[   12.210789] type=1400 audit(1311915522.171:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=670 comm="apparmor_parser"
[   12.213068] ath: EEPROM regdomain: 0x60
[   12.213071] ath: EEPROM indicates we should expect a direct regpair map
[   12.213077] ath: Country alpha2 being used: 00
[   12.213079] ath: Regpair used: 0x60
[   12.213084] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.213089] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213092] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.213097] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213100] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.213105] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213108] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.213112] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213116] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.213120] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213124] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.213128] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213131] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.213136] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213139] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.213144] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213147] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.213151] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213155] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.213159] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213163] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.213167] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213170] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.213175] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213178] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.213183] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.213186] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.213190] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   12.276289] type=1400 audit(1311915522.231:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=670 comm="apparmor_parser"
[   12.312738] type=1400 audit(1311915522.271:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=670 comm="apparmor_parser"
[   12.314012] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   12.314204] Linux video capture interface: v2.00
[   12.359705] type=1400 audit(1311915522.311:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=684 comm="apparmor_parser"
[   12.371774] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (18e3:9512)
[   12.372129] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input5
[   12.372507] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:1d.2-2/input0
[   12.372681] usbcore: registered new interface driver usbhid
[   12.372685] usbhid: USB HID core driver
[   12.389863] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input6
[   12.390249] usbcore: registered new interface driver uvcvideo
[   12.390253] USB Video Class driver (v1.1.0)
[   12.445155] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.446599] Registered led device: ath9k-phy0
[   12.446611] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90010920000, irq=17
[   12.596069] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   12.596078] cfg80211: World regulatory domain updated:
[   12.596081] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.596086] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.596090] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.596095] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.596099] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.596103] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.650531] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   12.699563] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   12.716035] usbcore: registered new interface driver snd-usb-audio
[   12.735331] init: alsa-restore main process (764) terminated with status 19
[   13.030073] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   13.030082] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.030085] [drm] Driver supports precise vblank timestamp query.
[   13.030142] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.103089] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.571536] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.571541] Bluetooth: BNEP filters: protocol multicast
[   13.580383] Bluetooth: RFCOMM TTY layer initialized
[   13.580391] Bluetooth: RFCOMM socket layer initialized
[   13.580394] Bluetooth: RFCOMM ver 1.11
[   13.642111] fbcon: inteldrmfb (fb0) is primary device
[   13.643788] Console: switching to colour frame buffer device 170x48
[   13.643825] fb0: inteldrmfb frame buffer device
[   13.643828] drm: registered panic notifier
[   13.654432] acpi device:2d: registered as cooling_device1
[   13.655171] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   13.656515] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.657387] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.657454] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.657534] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.657572] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.785310] hda_codec: ALC662 rev1: BIOS auto-probing.
[   13.795877] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   13.812941] input: HDA Intel HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   13.813207] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.976577] ppdev: user-space parallel port driver
[   15.072697] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   15.354147] init: plymouth-stop pre-start process (1145) terminated with status 1
[   16.059767] wlan0: authenticate with 00:26:44:98:e0:11 (try 1)
[   16.061867] wlan0: authenticated
[   16.062303] wlan0: associate with 00:26:44:98:e0:11 (try 1)
[   16.065098] wlan0: RX AssocResp from 00:26:44:98:e0:11 (capab=0x411 status=0 aid=2)
[   16.065103] wlan0: associated
[   16.065791] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.236697] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   16.286319] Intel AES-NI instructions are not detected.
[   16.289692] padlock_aes: VIA PadLock not detected.
[   26.460030] wlan0: no IPv6 routers present
[   79.650696] exe (1697): /proc/1697/oom_adj is deprecated, please use /proc/1697/oom_score_adj instead.
[ 1275.424186] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1275.424195] cfg80211: Restoring regulatory settings
[ 1275.424201] cfg80211: Calling CRDA to update world regulatory domain
[ 1275.429441] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1275.429450] cfg80211: World regulatory domain updated:
[ 1275.429452] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1275.429458] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1275.429462] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1275.429466] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1275.429470] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1275.429475] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1276.609778] wlan0: authenticate with 00:26:44:98:e0:11 (try 1)
[ 1276.611771] wlan0: authenticated
[ 1276.612356] wlan0: associate with 00:26:44:98:e0:11 (try 1)
[ 1276.615382] wlan0: RX ReassocResp from 00:26:44:98:e0:11 (capab=0x411 status=0 aid=2)
[ 1276.615388] wlan0: associated
```

if I boot mint then shutdown I get no bluetooth in oneiric, but if I reboot{restart} bluetooth is working fine in oneiric.

thanks for your time.

---

### Post by Roo79x on 2011-08-21
well it's been 3 ******* weeks and no one has answered? or even tried to give a clue as to what or how. and a place to try and get help, maybe an improvement in the forum ethos is needed!

---

### Post by cariboo on 2011-08-21
Keep in mind, we are all volunteers here. It could be that no one here has run into the same problem, or the person that can answer your question hasn't seen the problem yet. It also could be that your thread has dropped from view.

I'm not adverse to you bumping your thread once every 24 hours to keep it on the front page of the sub-forum.

---

### Post by karel.vacha on 2011-09-02
I had the problem with the same bluetooth chipset in Natty (kernel 2.6.38 ) and Arch Linux (kernel 3.0.5). I solved it by adding file bluetooth.conf to directory /etc/modprobe.d/ 

content of bluetooth.conf

```
install btusb [[ -z "$(lsusb | grep -E '13d3:3304')" ]] &&  modprobe ath3k &&  echo '13d3 3304'>/sys/module/ath3k/drivers/usb\:ath3k/new_id && modprobe -r ath3k;  modprobe -i btusb

```After you create the file **poweroff** your computer and start it again.
Judging from your lsusb output (same as mine in Arch Linux with 3.0.x kernels) only **rebooting won't work**.

If this does not work please post your dmesg, you can also try to bind ath3k driver without using the id.

Edit: 
I didn't remembered device id of my bt chipset correctly mine is 0cf3:3005 but yours seems to be 0cf3:3000, so we probably have different chipsets. Still it is worth a try.

---

### Post by Yfrwlf on 2011-09-13
From following this: [https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters](https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters)

What do you get when you do

```
hciconfig
```

Does it give you hci0?  If so, what does it say about it?  If it says "DOWN" then you need to put it up by doing

```
hciconfig hci0 up
```

I was searching through the forums for bluetooth issues because in Gnome 3's bluetooth settings window it shows bluetooth as being turned off until I perform the above.  It pops up with the bluetooth icon and everything upon inserting a bluetooth dongle, but isn't automatically turning it on for me.  What does it say in your bluetooth settings window?

---

### Post by Roo79x on 2011-09-13
> **Yfrwlf said:**
> From following this: [https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters](https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters)

What do you get when you do

```
hciconfig
```

Does it give you hci0?  If so, what does it say about it?  If it says "DOWN" then you need to put it up by doing

```
hciconfig hci0 up
```

I was searching through the forums for bluetooth issues because in Gnome 3's bluetooth settings window it shows bluetooth as being turned off until I perform the above.  It pops up with the bluetooth icon and everything upon inserting a bluetooth dongle, but isn't automatically turning it on for me.  What does it say in your bluetooth settings window?

Thanks for your time but I no longer have oneiric install as I can't be bothered to learn and contribute with ubuntu any more. linux mint is my main OS now and I'm playing with arch and elementary OS luna. it seems as far as ubuntu and kogan goes I've been left with a bad experience. and I personally do not like 11.10 and it's current direction, So thank you for trying to help, but I have moved on.

---

### Post by Yfrwlf on 2011-09-13
> **Roo79x said:**
> Thanks for your time but I no longer have oneiric install as I can't be bothered to learn and contribute with ubuntu any more. linux mint is my main OS now and I'm playing with arch and elementary OS luna. it seems as far as ubuntu and kogan goes I've been left with a bad experience. and I personally do not like 11.10 and it's current direction, So thank you for trying to help, but I have moved on.

I'd be happy if all distros were gotten rid of completely, and instead focus was directed towards individual Unix programs, the way things should be.  All we need for that to happen, and to get some true software freedom, is to have cross-distro package management like [Zero Install]("http://0install.net/") perhaps become a reality so you can install any desktop environment, any kernel, any driver, and any software any time.  Or, not even worry about making it work on other distros, and just focus on an intelligent package manager which can install anything, like Zero Install, instead of the crap managers that exist now.

With Ubuntu, since they have a lot of DEB packages available for them, you can install several other desktop environments, for example, if you don't like Unity.  However, you should be able to install Unity or any other DE on any other "distro" as well if you wanted to.  Currently that's far from easy, i.e. normal users can't, which isn't true software freedom at all.

---

### Post by acimmarusti on 2011-09-19
> **karel.vacha said:**
> I had the problem with the same bluetooth chipset in Natty (kernel 2.6.38 ) and Arch Linux (kernel 3.0.5). I solved it by adding file bluetooth.conf to directory /etc/modprobe.d/ 

content of bluetooth.conf

```
install btusb [[ -z "$(lsusb | grep -E '13d3:3304')" ]] &&  modprobe ath3k &&  echo '13d3 3304'>/sys/module/ath3k/drivers/usb\:ath3k/new_id && modprobe -r ath3k;  modprobe -i btusb

```After you create the file **poweroff** your computer and start it again.
Judging from your lsusb output (same as mine in Arch Linux with 3.0.x kernels) only **rebooting won't work**.

If this does not work please post your dmesg, you can also try to bind ath3k driver without using the id.

Edit: 
I didn't remembered device id of my bt chipset correctly mine is 0cf3:3005 but yours seems to be 0cf3:3000, so we probably have different chipsets. Still it is worth a try.

I have almost the exact same problem as the the owner of this thread. Except my laptop is a different brand that also came pre-installed with Ubuntu 11.04. However, I wanted to use Debian testing on the laptop. Kernel 3.0.x has issues with this bluetooth module. It fails to load the firmware (while Natty's kernel works fine).

could you tell me how you came up with this solution? also what is 13d3:3304? it seems like it's an address for a usb device. But I don't have such device listed.. can you please elaborate? I'm going to try it and report back, but I fear it will not work, because my device is ar3011 0cf3:3000.

Thanks

---

