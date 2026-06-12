---
title: "Lubuntu 14.04.1 slow boot up on Samsung R-25P"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by Urkosh on 2014-12-16
Hi,
could you please help me to speed up Lubuntu boot on my laptop (Samsung R-25P)? Althought it's quite old (and noisy) the boot time is too long. I know it is a frequent topic but the solutions suggested in previous threads differ depending on the case (hardware configuration and software version). Here is my case:

**dsmeg**
```
[    0.000000] ACPI: FACP 3fe99cce 0000F4 (v03 SEC    HAINAN3  06040000 SEC  000F4240)
[    0.000000] ACPI: DSDT 3fe92b4f 00710B (v01    ATI    SB600 06040000 INTL 20050228)
[    0.000000] ACPI: FACS 3fe9bfc0 000040
[    0.000000] ACPI: APIC 3fe99dc2 000054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 3fe99e16 00003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 3fe99e52 000038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 3fe99e8a 000176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 3fe919e3 00025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 3fe9193d 0000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 3fe90538 001405 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 130MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b97000, 0x01b97fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3fe8ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x3fe8ffff]
[    0.000000] On node 0 totalpages: 261676
[    0.000000] free_area_init_node: node 0, pgdat c199d580, node_mem_map f73fe020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 262 pages used for memmap
[    0.000000]   HighMem zone: 33426 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538310 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73db000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259892
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=d108174f-80e2-43a0-ad5b-179be08a4907 ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2094200 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003fe90)
[    0.000000] Memory: 1005248K/1046704K available (6546K kernel code, 640K rwdata, 2764K rodata, 876K init, 924K bss, 41456K reserved, 133704K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19bb000 - 0xc1a96000   ( 876 kB)
[    0.000000]       .data : 0xc1664ef4 - 0xc19ba3c0   (3413 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1664ef4   (6547 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1596.057 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.11 BogoMIPS (lpj=6384228)
[    0.004024] pid_max: default: 32768 minimum: 301
[    0.004110] Security Framework initialized
[    0.004157] AppArmor: AppArmor initialized
[    0.004167] Yama: becoming mindful.
[    0.004300] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004315] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.008086] Initializing cgroup subsys memory
[    0.008111] Initializing cgroup subsys devices
[    0.008122] Initializing cgroup subsys freezer
[    0.008133] Initializing cgroup subsys blkio
[    0.008144] Initializing cgroup subsys perf_event
[    0.008157] Initializing cgroup subsys hugetlb
[    0.008234] CPU: Physical Processor ID: 0
[    0.008244] CPU: Processor Core ID: 0
[    0.008257] mce: CPU supports 6 MCE banks
[    0.008280] CPU0: Thermal monitoring enabled (TM2)
[    0.008309] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.008309] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.008309] tlb_flushall_shift: -1
[    0.009133] Freeing SMP alternatives memory: 32K (c1a96000 - c1a9e000)
[    0.011940] ACPI: Core revision 20131115
[    0.023629] ACPI: All ACPI Tables successfully acquired
[    0.024024] ftrace: allocating 27840 entries in 55 pages
[    0.044208] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048408] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.052000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.052000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.052000] ..... (found apic 0 pin 0) ...
[    0.091850] ....... works.
[    0.091858] smpboot: CPU0: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz (fam: 06, model: 0f, stepping: 0d)
[    0.092000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.092000] perf_event_intel: PEBS disabled due to CPU errata
[    0.092000] ... version:                2
[    0.092000] ... bit width:              40
[    0.092000] ... generic registers:      2
[    0.092000] ... value mask:             000000ffffffffff
[    0.092000] ... max period:             000000007fffffff
[    0.092000] ... fixed-purpose events:   3
[    0.092000] ... event mask:             0000000700000003
[    0.093633] CPU 1 irqstacks, hard=f58ec000 soft=f58ee000
[    0.093640] x86: Booting SMP configuration:
[    0.008000] Initializing CPU#1
[    0.093655] .... node  #0, CPUs:      #1
[    0.106803] x86: Booted up 1 node, 2 CPUs
[    0.106828] smpboot: Total of 2 processors activated (6384.22 BogoMIPS)
[    0.106983] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.108255] devtmpfs: initialized
[    0.108571] EVM: security.selinux
[    0.108582] EVM: security.SMACK64
[    0.108590] EVM: security.ima
[    0.108598] EVM: security.capability
[    0.108681] PM: Registering ACPI NVS region [mem 0x3fe9a000-0x3fe9bfff] (8192 bytes)
[    0.110808] pinctrl core: initialized pinctrl subsystem
[    0.111044] regulator-dummy: no parameters
[    0.111117] RTC time:  0:31:10, date: 12/17/14
[    0.111248] NET: Registered protocol family 16
[    0.111659] EISA bus registered
[    0.111670] cpuidle: using governor ladder
[    0.111680] cpuidle: using governor menu
[    0.111831] ACPI: bus type PCI registered
[    0.111845] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.112067] PCI: MMCONFIG for domain 0000 [bus 00-0c] at [mem 0xe0000000-0xe0cfffff] (base 0xe0000000)
[    0.112086] PCI: MMCONFIG at [mem 0xe0000000-0xe0cfffff] reserved in E820
[    0.112096] PCI: Using MMCONFIG for extended config space
[    0.112106] PCI: Using configuration type 1 for base access
[    0.116189] bio: create slab <bio-0> at 0
[    0.116210] ACPI: Added _OSI(Module Device)
[    0.116224] ACPI: Added _OSI(Processor Device)
[    0.116235] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.116245] ACPI: Added _OSI(Processor Aggregator Device)
[    0.136211] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.145100] ACPI: SSDT 3fe92366 0002E6 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.145973] ACPI: Dynamic OEM Table Load:
[    0.145988] ACPI: SSDT   (null) 0002E6 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.146949] ACPI: SSDT 3fe91c42 00069F (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.148602] ACPI: Dynamic OEM Table Load:
[    0.148617] ACPI: SSDT   (null) 00069F (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.149428] ACPI: SSDT 3fe9264c 0000AA (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.150284] ACPI: Dynamic OEM Table Load:
[    0.150297] ACPI: SSDT   (null) 0000AA (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.150629] ACPI: SSDT 3fe922e1 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.151462] ACPI: Dynamic OEM Table Load:
[    0.151475] ACPI: SSDT   (null) 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.164103] ACPI: Interpreter enabled
[    0.164174] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.164197] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.164251] ACPI: (supports S0 S3 S4 S5)
[    0.164260] ACPI: Using IOAPIC for interrupt routing
[    0.164462] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.164881] ACPI: No dock devices found.
[    0.168918] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.168977] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.181252] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.181330] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.182040] ACPI: Power Resource [FN00] (off)
[    0.184874] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.184900] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.184927] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.187780] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-0c] only partially covers this bridge
[    0.188422] PCI host bridge to bus 0000:00
[    0.188439] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.188452] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.188464] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.188477] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.188489] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.188501] pci_bus 0000:00: root bus resource [mem 0x40000000-0xdfffffff]
[    0.188514] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff]
[    0.188526] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.188537] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.188565] pci 0000:00:00.0: [1002:7930] type 00 class 0x060000
[    0.188853] pci 0000:00:02.0: [1002:7933] type 01 class 0x060400
[    0.188986] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.189147] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.189268] pci 0000:00:05.0: [1002:7935] type 01 class 0x060400
[    0.189390] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.189548] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.189664] pci 0000:00:06.0: [1002:7936] type 01 class 0x060400
[    0.189786] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.189945] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.190059] pci 0000:00:07.0: [1002:7937] type 01 class 0x060400
[    0.190189] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.190348] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.190489] pci 0000:00:12.0: [1002:4380] type 00 class 0x01018f
[    0.190531] pci 0000:00:12.0: reg 0x10: [io  0x8438-0x843f]
[    0.190554] pci 0000:00:12.0: reg 0x14: [io  0x8444-0x8447]
[    0.190578] pci 0000:00:12.0: reg 0x18: [io  0x8430-0x8437]
[    0.190601] pci 0000:00:12.0: reg 0x1c: [io  0x8440-0x8443]
[    0.190624] pci 0000:00:12.0: reg 0x20: [io  0x8400-0x840f]
[    0.190648] pci 0000:00:12.0: reg 0x24: [mem 0xf8509000-0xf85093ff]
[    0.190694] pci 0000:00:12.0: set SATA to AHCI mode
[    0.190972] pci 0000:00:13.0: [1002:4387] type 00 class 0x0c0310
[    0.191005] pci 0000:00:13.0: reg 0x10: [mem 0xf8504000-0xf8504fff]
[    0.191331] pci 0000:00:13.1: [1002:4388] type 00 class 0x0c0310
[    0.191364] pci 0000:00:13.1: reg 0x10: [mem 0xf8505000-0xf8505fff]
[    0.191695] pci 0000:00:13.2: [1002:4389] type 00 class 0x0c0310
[    0.191728] pci 0000:00:13.2: reg 0x10: [mem 0xf8506000-0xf8506fff]
[    0.192064] pci 0000:00:13.3: [1002:438a] type 00 class 0x0c0310
[    0.192096] pci 0000:00:13.3: reg 0x10: [mem 0xf8507000-0xf8507fff]
[    0.192429] pci 0000:00:13.4: [1002:438b] type 00 class 0x0c0310
[    0.192461] pci 0000:00:13.4: reg 0x10: [mem 0xf8508000-0xf8508fff]
[    0.192806] pci 0000:00:13.5: [1002:4386] type 00 class 0x0c0320
[    0.192850] pci 0000:00:13.5: reg 0x10: [mem 0xf8509400-0xf85094ff]
[    0.193029] pci 0000:00:13.5: supports D1 D2
[    0.193036] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.193288] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.193328] pci 0000:00:14.0: reg 0x10: [io  0x8410-0x841f]
[    0.193658] pci 0000:00:14.1: [1002:438c] type 00 class 0x01018a
[    0.193690] pci 0000:00:14.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.193714] pci 0000:00:14.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.193737] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.193760] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.193783] pci 0000:00:14.1: reg 0x20: [io  0x8420-0x842f]
[    0.194054] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.194103] pci 0000:00:14.2: reg 0x10: [mem 0xf8500000-0xf8503fff 64bit]
[    0.194248] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.194403] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.194516] pci 0000:00:14.3: [1002:438d] type 00 class 0x060100
[    0.194864] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.195073] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.195388] pci 0000:01:00.0: [1002:7188] type 00 class 0x030000
[    0.195418] pci 0000:01:00.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
[    0.195439] pci 0000:01:00.0: reg 0x14: [io  0x9000-0x90ff]
[    0.195459] pci 0000:01:00.0: reg 0x18: [mem 0xf8000000-0xf800ffff]
[    0.195518] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.195596] pci 0000:01:00.0: supports D1 D2
[    0.195712] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.195743] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.195761] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.195772] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xf80fffff]
[    0.195786] pci 0000:00:02.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.196010] acpiphp: Slot [1] registered
[    0.196035] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    0.196053] pci 0000:00:05.0:   bridge window [io  0x0000-0x0fff]
[    0.196063] pci 0000:00:05.0:   bridge window [mem 0x00000000-0x000fffff]
[    0.196272] acpiphp: Slot [1-1] registered
[    0.196295] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    0.196314] pci 0000:00:06.0:   bridge window [io  0x0000-0x0fff]
[    0.196324] pci 0000:00:06.0:   bridge window [mem 0x00000000-0x000fffff]
[    0.196530] acpiphp: Slot [1-2] registered
[    0.196584] pci 0000:08:00.0: [168c:001c] type 00 class 0x020000
[    0.196626] pci 0000:08:00.0: reg 0x10: [mem 0xf8100000-0xf810ffff 64bit]
[    0.196809] pci 0000:08:00.0: PME# supported from D3hot
[    0.196946] pci 0000:08:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.196977] pci 0000:00:07.0: PCI bridge to [bus 08-0a]
[    0.196999] pci 0000:00:07.0:   bridge window [mem 0xf8100000-0xf81fffff]
[    0.197162] pci 0000:0b:05.0: [10ec:8139] type 00 class 0x020000
[    0.197207] pci 0000:0b:05.0: reg 0x10: [io  0xa000-0xa0ff]
[    0.197234] pci 0000:0b:05.0: reg 0x14: [mem 0xf8200000-0xf82000ff]
[    0.197400] pci 0000:0b:05.0: supports D1 D2
[    0.197407] pci 0000:0b:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.197460] pci 0000:0b:05.0: System wakeup disabled by ACPI
[    0.197630] pci 0000:00:14.4: PCI bridge to [bus 0b-0d] (subtractive decode)
[    0.197649] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.197660] pci 0000:00:14.4:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.197673] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.197680] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.197687] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.197694] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.197701] pci 0000:00:14.4:   bridge window [mem 0x40000000-0xdfffffff] (subtractive decode)
[    0.197709] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.197722] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.197729] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.197787] pci_bus 0000:00: on NUMA node 0
[    0.199127] ACPI: PCI Interrupt Link [LNKA] (IRQs 11) *0, disabled.
[    0.199319] ACPI: PCI Interrupt Link [LNKB] (IRQs 10) *0, disabled.
[    0.199503] ACPI: PCI Interrupt Link [LNKC] (IRQs 5) *0, disabled.
[    0.199684] ACPI: PCI Interrupt Link [LNKD] (IRQs 5) *0, disabled.
[    0.199866] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.200057] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    0.200240] ACPI: PCI Interrupt Link [LNKG] (IRQs 5) *0, disabled.
[    0.200422] ACPI: PCI Interrupt Link [LNKH] (IRQs 5) *0, disabled.
[    0.201310] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.201348] ACPI: \_SB_.PCI0: notify handler is installed
[    0.201473] Found 1 acpi root devices
[    0.201671] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.201704] ACPI : EC: 0 stale EC events cleared
[    0.201704] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.201704] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.201704] vgaarb: loaded
[    0.201704] vgaarb: bridge control possible 0000:01:00.0
[    0.201704] SCSI subsystem initialized
[    0.201704] libata version 3.00 loaded.
[    0.201704] ACPI: bus type USB registered
[    0.201704] usbcore: registered new interface driver usbfs
[    0.201704] usbcore: registered new interface driver hub
[    0.201704] usbcore: registered new device driver usb
[    0.201704] PCI: Using ACPI for IRQ routing
[    0.201704] PCI: pci_cache_line_size set to 64 bytes
[    0.204138] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    0.204145] e820: reserve RAM buffer [mem 0x3fe90000-0x3fffffff]
[    0.204416] NetLabel: Initializing
[    0.204427] NetLabel:  domain hash size = 128
[    0.204435] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204472] NetLabel:  unlabeled traffic allowed by default
[    0.204518] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.204518] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.206312] Switched to clocksource hpet
[    0.228082] AppArmor: AppArmor Filesystem Enabled
[    0.228172] pnp: PnP ACPI init
[    0.228220] ACPI: bus type PNP registered
[    0.229076] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.229095] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.229114] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.230165] pnp 00:01: [dma 4]
[    0.230250] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.230380] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.230620] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.230721] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.230841] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.230956] pnp 00:06: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.231184] system 00:07: [io  0x0220-0x022f] has been reserved
[    0.231201] system 00:07: [io  0x040b] has been reserved
[    0.231215] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.231229] system 00:07: [io  0x04d6] has been reserved
[    0.231242] system 00:07: [io  0x0530-0x0537] has been reserved
[    0.231256] system 00:07: [io  0x0c00-0x0c01] has been reserved
[    0.231269] system 00:07: [io  0x0c14] has been reserved
[    0.231282] system 00:07: [io  0x0c50-0x0c52] has been reserved
[    0.231295] system 00:07: [io  0x0c6c] has been reserved
[    0.231307] system 00:07: [io  0x0c6f] has been reserved
[    0.231320] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
[    0.231334] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
[    0.231347] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
[    0.231360] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
[    0.231373] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
[    0.231387] system 00:07: [io  0x8000-0x805f] could not be reserved
[    0.231401] system 00:07: [io  0x8100-0x81ff window] has been reserved
[    0.231414] system 00:07: [io  0x8210-0x821f] has been reserved
[    0.231427] system 00:07: [io  0x0f40-0x0f47] has been reserved
[    0.231440] system 00:07: [io  0x0280-0x0293] has been reserved
[    0.231453] system 00:07: [io  0x087f] has been reserved
[    0.231468] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.231749] system 00:08: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.231767] system 00:08: [mem 0xffb83020-0xffb8401f] has been reserved
[    0.231782] system 00:08: [mem 0xfff00000-0xffffffff] has been reserved
[    0.231798] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.232292] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.232374] pnp: PnP ACPI: found 10 devices
[    0.232385] ACPI: bus type PNP unregistered
[    0.232401] PnPBIOS: Disabled by ACPI PNP
[    0.273314] pci 0000:01:00.0: BAR 6: assigned [mem 0xf8020000-0xf803ffff pref]
[    0.273336] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.273350] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.273366] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xf80fffff]
[    0.273382] pci 0000:00:02.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.273402] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    0.273427] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    0.273451] pci 0000:00:07.0: PCI bridge to [bus 08-0a]
[    0.273466] pci 0000:00:07.0:   bridge window [mem 0xf8100000-0xf81fffff]
[    0.273488] pci 0000:00:14.4: PCI bridge to [bus 0b-0d]
[    0.273505] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.273523] pci 0000:00:14.4:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.273551] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff]
[    0.273558] pci_bus 0000:00: resource 5 [mem 0x000d0000-0x000d3fff]
[    0.273565] pci_bus 0000:00: resource 6 [mem 0x000d4000-0x000d7fff]
[    0.273571] pci_bus 0000:00: resource 7 [mem 0x000d8000-0x000dbfff]
[    0.273578] pci_bus 0000:00: resource 8 [mem 0x40000000-0xdfffffff]
[    0.273585] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
[    0.273592] pci_bus 0000:00: resource 10 [io  0x0000-0x0cf7]
[    0.273599] pci_bus 0000:00: resource 11 [io  0x0d00-0xffff]
[    0.273606] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.273613] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xf80fffff]
[    0.273620] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.273627] pci_bus 0000:08: resource 1 [mem 0xf8100000-0xf81fffff]
[    0.273634] pci_bus 0000:0b: resource 0 [io  0xa000-0xafff]
[    0.273641] pci_bus 0000:0b: resource 1 [mem 0xf8200000-0xf82fffff]
[    0.273647] pci_bus 0000:0b: resource 4 [mem 0x000a0000-0x000bffff]
[    0.273654] pci_bus 0000:0b: resource 5 [mem 0x000d0000-0x000d3fff]
[    0.273660] pci_bus 0000:0b: resource 6 [mem 0x000d4000-0x000d7fff]
[    0.273667] pci_bus 0000:0b: resource 7 [mem 0x000d8000-0x000dbfff]
[    0.273673] pci_bus 0000:0b: resource 8 [mem 0x40000000-0xdfffffff]
[    0.273680] pci_bus 0000:0b: resource 9 [mem 0xf0000000-0xffffffff]
[    0.273686] pci_bus 0000:0b: resource 10 [io  0x0000-0x0cf7]
[    0.273693] pci_bus 0000:0b: resource 11 [io  0x0d00-0xffff]
[    0.273796] NET: Registered protocol family 2
[    0.274418] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.274466] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.274526] TCP: Hash tables configured (established 8192 bind 8192)
[    0.274596] TCP: reno registered
[    0.274608] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.274632] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.274789] NET: Registered protocol family 1
[    0.277400] pci 0000:01:00.0: Video device with shadowed ROM
[    0.277420] PCI: CLS 32 bytes, default 64
[    0.277549] Trying to unpack rootfs image as initramfs...
[    1.315304] Freeing initrd memory: 18332K (f5c22000 - f6e09000)
[    1.315940] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[    1.315963] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[    1.316174] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.316191] Scanning for low memory corruption every 60 seconds
[    1.316909] Initialise system trusted keyring
[    1.317033] audit: initializing netlink socket (disabled)
[    1.317067] type=2000 audit(1418776269.316:1): initialized
[    1.385306] bounce pool size: 64 pages
[    1.385347] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.389459] zbud: loaded
[    1.389657] VFS: Disk quotas dquot_6.5.2
[    1.389813] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.391336] fuse init (API version 7.22)
[    1.391612] msgmni has been set to 1738
[    1.391799] Key type big_key registered
[    1.392784] Key type asymmetric registered
[    1.392799] Asymmetric key parser 'x509' registered
[    1.392912] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.393008] io scheduler noop registered
[    1.393020] io scheduler deadline registered (default)
[    1.393116] io scheduler cfq registered
[    1.393446] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.393616] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.393777] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    1.393930] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    1.394125] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.394182] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.394328] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.394339] vesafb: scrolling: redraw
[    1.394350] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.394843] vesafb: framebuffer at 0xf0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    1.460826] Console: switching to colour frame buffer device 128x48
[    1.526869] fb0: VESA VGA frame buffer device
[    1.527465] intel_idle: does not run on family 6 model 15
[    1.527485] ipmi message handler version 39.2
[    1.528348] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.529882] ACPI: AC Adapter [ADP1] (on-line)
[    1.530966] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.531994] ACPI: Power Button [PWRB]
[    1.532607] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.533637] ACPI: Lid Switch [LID0]
[    1.534187] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.535207] ACPI: Sleep Button [SLPB]
[    1.535805] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.536758] ACPI: Power Button [PWRF]
[    1.537382] ACPI: Fan [FAN0] (off)
[    1.541570] Monitor-Mwait will be used to enter C-1 state
[    1.541587] Monitor-Mwait will be used to enter C-2 state
[    1.541596] tsc: Marking TSC unstable due to TSC halts in idle
[    1.542331] ACPI: acpi_idle registered with cpuidle
[    1.544678] thermal LNXTHERM:00: registered as thermal_zone0
[    1.545392] ACPI: Thermal Zone [TZ00] (25 C)
[    1.547224] thermal LNXTHERM:01: registered as thermal_zone1
[    1.547934] ACPI: Thermal Zone [TZ01] (25 C)
[    1.548586] GHES: HEST is not enabled!
[    1.549390] isapnp: Scanning for PnP cards...
[    1.550513] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.554708] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.556078] ACPI: Battery Slot [BAT1] (battery present)
[    1.590233] Linux agpgart interface v0.103
[    1.625067] brd: module loaded
[    1.657352] loop: module loaded
[    1.688445] libphy: Fixed MDIO Bus: probed
[    1.718365] tun: Universal TUN/TAP device driver, 1.6
[    1.748227] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.778297] PPP generic driver version 2.4.2
[    1.807685] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.837955] ehci-pci: EHCI PCI platform driver
[    1.864086] isapnp: No Plug & Play device found
[    1.898476] ehci-pci 0000:00:13.5: EHCI Host Controller
[    1.928549] ehci-pci 0000:00:13.5: new USB bus registered, assigned bus number 1
[    1.958693] ehci-pci 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    1.988677] ehci-pci 0000:00:13.5: debug port 1
[    2.018462] ehci-pci 0000:00:13.5: irq 19, io mem 0xf8509400
[    2.060051] ehci-pci 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    2.090027] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.120142] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.150198] usb usb1: Product: EHCI Host Controller
[    2.179974] usb usb1: Manufacturer: Linux 3.13.0-43-generic ehci_hcd
[    2.209971] usb usb1: SerialNumber: 0000:00:13.5
[    2.240164] hub 1-0:1.0: USB hub found
[    2.269724] hub 1-0:1.0: 10 ports detected
[    2.299386] ehci-platform: EHCI generic platform driver
[    2.328414] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.357481] ohci-pci: OHCI PCI platform driver
[    2.386777] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    2.415567] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.444031] ohci-pci 0000:00:13.0: irq 16, io mem 0xf8504000
[    2.524165] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    2.551955] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.579445] usb usb2: Product: OHCI PCI host controller
[    2.606504] usb usb2: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    2.633353] usb usb2: SerialNumber: 0000:00:13.0
[    2.659949] hub 2-0:1.0: USB hub found
[    2.685809] hub 2-0:1.0: 2 ports detected
[    2.711165] usb 1-6: new high-speed USB device number 3 using ehci-pci
[    2.712357] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    2.712376] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.712433] ohci-pci 0000:00:13.1: irq 17, io mem 0xf8505000
[    2.768603] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    2.768608] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.768612] usb usb3: Product: OHCI PCI host controller
[    2.768617] usb usb3: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    2.768620] usb usb3: SerialNumber: 0000:00:13.1
[    2.768918] hub 3-0:1.0: USB hub found
[    2.768943] hub 3-0:1.0: 2 ports detected
[    2.769880] ohci-pci 0000:00:13.2: OHCI PCI host controller
[    2.769894] ohci-pci 0000:00:13.2: new USB bus registered, assigned bus number 4
[    2.769945] ohci-pci 0000:00:13.2: irq 18, io mem 0xf8506000
[    2.824209] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.824214] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.824218] usb usb4: Product: OHCI PCI host controller
[    2.824222] usb usb4: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    2.824226] usb usb4: SerialNumber: 0000:00:13.2
[    2.824502] hub 4-0:1.0: USB hub found
[    2.824526] hub 4-0:1.0: 2 ports detected
[    2.825319] ohci-pci 0000:00:13.3: OHCI PCI host controller
[    2.825333] ohci-pci 0000:00:13.3: new USB bus registered, assigned bus number 5
[    2.825361] ohci-pci 0000:00:13.3: irq 17, io mem 0xf8507000
[    2.880306] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.880311] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.880315] usb usb5: Product: OHCI PCI host controller
[    2.880319] usb usb5: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    2.880323] usb usb5: SerialNumber: 0000:00:13.3
[    2.880621] hub 5-0:1.0: USB hub found
[    2.880649] hub 5-0:1.0: 2 ports detected
[    2.881578] ohci-pci 0000:00:13.4: OHCI PCI host controller
[    2.881592] ohci-pci 0000:00:13.4: new USB bus registered, assigned bus number 6
[    2.881621] ohci-pci 0000:00:13.4: irq 18, io mem 0xf8508000
[    2.936300] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.936305] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.936309] usb usb6: Product: OHCI PCI host controller
[    2.936313] usb usb6: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    2.936317] usb usb6: SerialNumber: 0000:00:13.4
[    2.936600] hub 6-0:1.0: USB hub found
[    2.936628] hub 6-0:1.0: 2 ports detected
[    2.936901] ohci-platform: OHCI generic platform driver
[    2.936931] uhci_hcd: USB Universal Host Controller Interface driver
[    2.937165] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.940292] i8042: Detected active multiplexing controller, rev 1.1
[    2.942101] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.942114] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.942194] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.942257] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.942324] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.942629] mousedev: PS/2 mouse device common for all mice
[    2.943348] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.943395] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.943619] device-mapper: uevent: version 1.0.3
[    2.943813] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.943876] platform eisa.0: Probing EISA bus 0
[    2.943881] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    2.943886] platform eisa.0: Cannot allocate resource for EISA slot 1
[    2.943891] platform eisa.0: Cannot allocate resource for EISA slot 2
[    2.943895] platform eisa.0: Cannot allocate resource for EISA slot 3
[    2.943899] platform eisa.0: Cannot allocate resource for EISA slot 4
[    2.943903] platform eisa.0: Cannot allocate resource for EISA slot 5
[    2.943908] platform eisa.0: Cannot allocate resource for EISA slot 6
[    2.943912] platform eisa.0: Cannot allocate resource for EISA slot 7
[    2.943917] platform eisa.0: Cannot allocate resource for EISA slot 8
[    2.943920] platform eisa.0: EISA: Detected 0 cards
[    2.943938] cpufreq-nforce2: No nForce2 chipset.
[    2.943946] ledtrig-cpu: registered to indicate activity on CPUs
[    2.944384] TCP: cubic registered
[    2.944694] NET: Registered protocol family 10
[    2.945270] NET: Registered protocol family 17
[    2.945299] Key type dns_resolver registered
[    2.945712] Using IPI No-Shortcut mode
[    2.945930] Loading compiled-in X.509 certificates
[    2.956936] Loaded X.509 cert 'Magrathea: Glacier signing key: 3c74d8789caa5ecb12ddd1aac215e12c62fcaca5'
[    2.956970] registered taskstats version 1
[    2.973415] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.975631] Key type trusted registered
[    2.991068] Key type encrypted registered
[    3.007080] AppArmor: AppArmor sha1 policy hashing enabled
[    3.007084] IMA: No TPM chip found, activating TPM-bypass!
[    3.015927] regulator-dummy: disabling
[    3.016042]   Magic number: 10:787:506
[    4.692408] rtc_cmos 00:03: setting system clock to 2014-12-17 00:31:13 UTC (1418776273)
[    4.715343] [sched_delayed] sched: RT throttling activated
[    4.728385] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.740894] EDD information not available.
[    4.753335] PM: Hibernation image not present or could not be loaded.
[    4.754013] Freeing unused kernel memory: 876K (c19bb000 - c1a96000)
[    4.766887] Write protecting the kernel text: 6548k
[    4.779858] Write protecting the kernel read-only data: 2772k
[    4.792508] NX-protecting the kernel data: 5740k
[    4.855594] systemd-udevd[112]: starting version 204
[    4.870069] usb 1-6: New USB device found, idVendor=058f, idProduct=6366
[    4.883159] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.896229] usb 1-6: Product: Mass Storage Device
[    4.911041] usb 1-6: Manufacturer: Generic
[    4.924824] usb 1-6: SerialNumber: 058F0O1111B
[    4.956937] usb-storage 1-6:1.0: USB Mass Storage device detected
[    4.957039] scsi0 : usb-storage 1-6:1.0
[    4.957169] usbcore: registered new interface driver usb-storage
[    5.019254] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.019298] 8139cp 0000:0b:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    5.061603] 8139too: 8139too Fast Ethernet driver 0.9.28
[    5.079037] 8139too 0000:0b:05.0 eth0: RealTek RTL8139 at 0x0001a000, 00:13:77:69:52:5b, IRQ 22
[    5.095480] ahci 0000:00:12.0: version 3.0
[    5.095687] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.121757] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.121761] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    5.168173] scsi1 : ahci
[    5.191263] scsi2 : ahci
[    5.210519] scsi3 : ahci
[    5.227629] scsi4 : ahci
[    5.243560] ata1: SATA max UDMA/133 abar m1024@0xf8509000 port 0xf8509100 irq 22
[    5.248059] usb 3-1: new low-speed USB device number 2 using ohci-pci
[    5.275865] ata2: SATA max UDMA/133 abar m1024@0xf8509000 port 0xf8509180 irq 22
[    5.292597] ata3: SATA max UDMA/133 abar m1024@0xf8509000 port 0xf8509200 irq 22
[    5.309058] ata4: SATA max UDMA/133 abar m1024@0xf8509000 port 0xf8509280 irq 22
[    5.326804] scsi5 : pata_atiixp
[    5.343077] scsi6 : pata_atiixp
[    5.358912] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    5.374812] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    5.430103] usb 3-1: New USB device found, idVendor=15d9, idProduct=0a4e
[    5.445305] usb 3-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    5.460710] usb 3-1: Product:  USB OPTICAL MOUSE
[    5.489007] hidraw: raw HID events driver (C) Jiri Kosina
[    5.517786] usbcore: registered new interface driver usbhid
[    5.533172] usbhid: USB HID core driver
[    5.555766] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input13
[    5.572250] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L632H, SC03, max UDMA/33
[    5.572423] hid-generic 0003:15D9:0A4E.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:13.1-1/input0
[    5.636499] ata5.00: configured for UDMA/33
[    5.652711] ata3: SATA link down (SStatus 0 SControl 300)
[    5.669077] ata4: SATA link down (SStatus 0 SControl 300)
[    5.685582] ata2: SATA link down (SStatus 0 SControl 300)
[    5.864047] ata1: softreset failed (device not ready)
[    5.880245] ata1: applying PMP SRST workaround and retrying
[    5.885341] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x200000/0x0, board id: 3655, fw id: 131143
[    5.929508] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[    5.957007] scsi 0:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[    5.975936] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.997363] sd 0:0:0:0: [sda] Attached SCSI removable disk
[    6.108062] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.131227] ata1.00: ATA-8: SAMSUNG HM121HI, LZ100-06, max UDMA7
[    6.148310] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.165534] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    6.188842] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    6.205561] ata1.00: configured for UDMA/133
[    6.222302] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HM121HI  LZ10 PQ: 0 ANSI: 5
[    6.239083] sd 1:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    6.255699] sd 1:0:0:0: [sdb] Write Protect is off
[    6.257157] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    6.287578] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.287630] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.303645] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  SC03 PQ: 0 ANSI: 5
[    6.330868] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.346840] cdrom: Uniform CD-ROM driver Revision: 3.20
[    6.352424]  sdb: sdb2 sdb3 sdb4 < sdb5 sdb6 >
[    6.353258] sd 1:0:0:0: [sdb] Attached SCSI disk
[    6.396370] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    6.396475] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    7.140373] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[    7.648471] random: nonblocking pool is initialized
[    8.463691] init: plymouth-upstart-bridge main process (177) terminated with status 1
[    8.481349] init: plymouth-upstart-bridge main process ended, respawning
[    8.503260] init: plymouth-upstart-bridge main process (188) terminated with status 1
[    8.521841] init: plymouth-upstart-bridge main process ended, respawning
[   18.956267] Adding 714748k swap on /dev/sdb5.  Priority:-1 extents:1 across:714748k FS
[   19.065554] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.250331] systemd-udevd[291]: starting version 204
[   19.567373] lp: driver loaded but no devices found
[   19.579840] ppdev: user-space parallel port driver
[   20.018607] ACPI: Video Device [PEGD] (multi-head: yes  rom: no  post: no)
[   20.018638] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   20.021755] acpi device:03: registered as cooling_device3
[   20.021944] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input14
[   20.169967] [drm] Initialized drm 1.1.0 20060810
[   20.209358] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   20.209526] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0x8050
[   20.220374] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   20.220597] sp5100_tco: PCI Revision ID: 0x14
[   20.220628] sp5100_tco: failed to find MMIO address, giving up.
[   20.378352] cfg80211: Calling CRDA to update world regulatory domain
[   20.439945] [drm] radeon kernel modesetting enabled.
[   20.440114] checking generic (f0000000 300000) vs hw (f0000000 8000000)
[   20.440118] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   20.440166] Console: switching to colour dummy device 80x25
[   20.441039] [drm] initializing kernel modesetting (RV515 0x1002:0x7188 0x144D:0xC515).
[   20.441068] [drm] register mmio base: 0xF8000000
[   20.441070] [drm] register mmio size: 65536
[   20.441220] ATOM BIOS: SAMSUNG
[   20.441248] [drm] Generation 2 PCI interface, using max accessible memory
[   20.441257] radeon 0000:01:00.0: VRAM: 128M 0x0000000000000000 - 0x0000000007FFFFFF (128M used)
[   20.441261] radeon 0000:01:00.0: GTT: 512M 0x0000000008000000 - 0x0000000027FFFFFF
[   20.441290] [drm] Detected VRAM RAM=128M, BAR=128M
[   20.441292] [drm] RAM width 64bits DDR
[   20.447824] [TTM] Zone  kernel: Available graphics memory: 445392 kiB
[   20.447830] [TTM] Zone highmem: Available graphics memory: 512244 kiB
[   20.447832] [TTM] Initializing pool allocator
[   20.447951] [TTM] Initializing DMA pool allocator
[   20.447995] [drm] radeon: 128M of VRAM memory ready
[   20.447998] [drm] radeon: 512M of GTT memory ready.
[   20.448072] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   20.455833] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   20.457718] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   20.457778] radeon 0000:01:00.0: WB enabled
[   20.457785] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000008000000 and cpu addr 0xf6382000
[   20.457790] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   20.457792] [drm] Driver supports precise vblank timestamp query.
[   20.457812] [drm] radeon: irq initialized.
[   20.457836] [drm] Loading R500 Microcode
[   20.501074] ath5k 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[   20.501264] ath5k 0000:08:00.0: registered as 'phy0'
[   20.569702] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro
[   20.775978] hda-intel 0000:00:14.2: Using LPIB position fix
[   20.784927] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   20.804968] type=1400 audit(1418769091.287:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=389 comm="apparmor_parser"
[   20.804981] type=1400 audit(1418769091.287:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=389 comm="apparmor_parser"
[   20.804990] type=1400 audit(1418769091.287:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=389 comm="apparmor_parser"
[   20.805863] type=1400 audit(1418769091.287:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=389 comm="apparmor_parser"
[   20.805876] type=1400 audit(1418769091.287:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=389 comm="apparmor_parser"
[   20.806316] type=1400 audit(1418769091.287:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=389 comm="apparmor_parser"
[   20.812046] type=1400 audit(1418769091.291:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=416 comm="apparmor_parser"
[   20.813968] [drm] radeon: ring at 0x0000000008001000
[   20.814013] [drm] ring test succeeded in 7 usecs
[   20.815930] [drm] ib test succeeded in 0 usecs
[   20.833575] [drm] radeon atom DIG backlight initialized
[   20.833585] [drm] Radeon Display Connectors
[   20.833588] [drm] Connector 0:
[   20.833592] [drm]   VGA-1
[   20.833596] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   20.833598] [drm]   Encoders:
[   20.833601] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   20.833603] [drm] Connector 1:
[   20.833605] [drm]   LVDS-1
[   20.833609] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   20.833611] [drm]   Encoders:
[   20.833613] [drm]     LCD1: INTERNAL_LVTM1
[   20.886478] autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   20.886484]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.886487]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.886489]    mono: mono_out=0x0
[   20.886491]    inputs:
[   20.927242] SKU: Nid=0x1d sku_cfg=0x4014820d
[   20.927247] SKU: port_connectivity=0x1
[   20.927249] SKU: enable_pcbeep=0x1
[   20.927251] SKU: check_sum=0x00000004
[   20.927254] SKU: customization=0x00000082
[   20.927256] SKU: external_amp=0x1
[   20.927258] SKU: platform_type=0x1
[   20.927260] SKU: swap=0x0
[   20.927262] SKU: override=0x1
[   20.927454] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   20.927458]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.927460]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   20.927462]    mono: mono_out=0x0
[   20.927464]    inputs:
[   20.927468]      Mic=0x18
[   20.927470] realtek: No valid SSID, checking pincfg 0x4014820d for NID 0x1d
[   20.927473] realtek: Enabling init ASM_ID=0x820d CODEC_ID=10ec0262
[   21.071032] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input16
[   21.079512] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input15
[   21.318162] [drm] fb mappable at 0xF00C0000
[   21.318168] [drm] vram apper at 0xF0000000
[   21.318179] [drm] size 4096000
[   21.318182] [drm] fb depth is 24
[   21.318184] [drm]    pitch is 5120
[   21.318795] fbcon: radeondrmfb (fb0) is primary device
[   21.376627] cfg80211: World regulatory domain updated:
[   21.376628] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.376631] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.376633] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.376634] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.376636] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.376637] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.628195] Console: switching to colour frame buffer device 160x50
[   21.637455] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   21.637458] radeon 0000:01:00.0: registered panic notifier
[   21.637481] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   21.779935] ath: EEPROM regdomain: 0x65
[   21.779940] ath: EEPROM indicates we should expect a direct regpair map
[   21.779945] ath: Country alpha2 being used: 00
[   21.779947] ath: Regpair used: 0x65
[   21.826454] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   21.827221] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.845057] init: failsafe main process (555) killed by TERM signal
[   22.408705] type=1400 audit(1418769092.891:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=634 comm="apparmor_parser"
[   22.408719] type=1400 audit(1418769092.891:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=634 comm="apparmor_parser"
[   22.409971] type=1400 audit(1418769092.891:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=634 comm="apparmor_parser"
[   22.468223] Bluetooth: Core ver 2.17
[   22.468314] NET: Registered protocol family 31
[   22.468317] Bluetooth: HCI device and connection manager initialized
[   22.468331] Bluetooth: HCI socket layer initialized
[   22.468336] Bluetooth: L2CAP socket layer initialized
[   22.468344] Bluetooth: SCO socket layer initialized
[   22.528877] Bluetooth: RFCOMM TTY layer initialized
[   22.528896] Bluetooth: RFCOMM socket layer initialized
[   22.528911] Bluetooth: RFCOMM ver 1.11
[   22.537442] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.537448] Bluetooth: BNEP filters: protocol multicast
[   22.537466] Bluetooth: BNEP socket layer initialized
[   24.067097] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.067660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.088490] 8139too 0000:0b:05.0 eth0: link down
[   24.088586] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.089132] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.097860] wlan0: authenticate with 8c:a9:82:56:cc:1f
[   25.102097] wlan0: send auth to 8c:a9:82:56:cc:1f (try 1/3)
[   25.103756] wlan0: authenticated
[   25.108045] wlan0: associate with 8c:a9:82:56:cc:1f (try 1/3)
[   25.110012] wlan0: RX AssocResp from 8c:a9:82:56:cc:1f (capab=0x431 status=0 aid=1)
[   25.110377] wlan0: associated
[   25.110416] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.858010] init: plymouth-upstart-bridge main process ended, respawning
[   25.877822] init: plymouth-upstart-bridge main process (1108) terminated with status 1
[   25.877855] init: plymouth-upstart-bridge main process ended, respawning
[  113.493323] perf samples too long (2538 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  185.053437] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  185.113030] JFS: nTxBlock = 8003, nTxLock = 64030
[  185.183448] NTFS driver 2.1.30 [Flags: R/O MODULE].
[  185.302145] QNX4 filesystem 0.2.3 registered.
[  185.372727] xor: measuring software checksum speed
[  185.412019]    pIII_sse  :  5735.000 MB/sec
[  185.452016]    prefetch64-sse:  6486.000 MB/sec
[  185.452020] xor: using function: prefetch64-sse (6486.000 MB/sec)
[  185.544036] raid6: mmxx1     2083 MB/s
[  185.612046] raid6: mmxx2     2381 MB/s
[  185.680055] raid6: sse1x1    1375 MB/s
[  185.748029] raid6: sse1x2    1740 MB/s
[  185.816021] raid6: sse2x1    2416 MB/s
[  185.884018] raid6: sse2x2    2787 MB/s
[  185.884021] raid6: using algorithm sse2x2 (2787 MB/s)
[  185.884024] raid6: using ssse3x1 recovery algorithm
[  185.962909] bio: create slab <bio-1> at 1
[  185.965127] Btrfs loaded
[  358.724741] perf samples too long (5008 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
```

**bootchart**
[ATTACH=CONFIG]258650[/ATTACH]
Thanks in advance!

---

### Post by DuckHook on 2014-12-16
Hi Urkosh and welcome to the forums.

What do you mean by too long? This is a subjective term that means different things to different people. Please give approximate time.

The R-25P is not actually that old. I only briefly looked over a summary of the specs (hard to find proper specs for some reason), but based on it being a dual-core, it shouldn't qualify as ancient. Therefore, it shouldn't boot up with too much elapsed time either.

Your reference to noisy is not a good sign. This often indicates a dying HDD. Next time you get it running, please go to Accessories>Disks. Click on the "gear" icon at upper right corner and choose "SMART Data & Self-Tests". See what condition the HDD is in. Your long startups may be due to lots of bad sectors and/or missing partition tables, bad inodes, etc. Be careful with the *Disks* utility. It is very powerful and could wipe your system.

It is a good idea to do a data backup RIGHT AWAY. Backups never hurt and if your HDD is going, it could be a lifesaver. It will also save your skin if you inadvertently hit "format disk" while monkeying around with disk utilities.

You did good posting *dmesg* output, but your bootchart is far too small to make out and the most important info is your HW configuration. You can either just tell us your HW specs if you know them, or you can post back the results of:```
sudo lshw -short
```One further thing to try: you can make the splash screen go away by hitting <Esc> when it comes on. Then you will see all of the services and modules as they load. You should be able to see whichever module/service that the system is waiting for before timing out. It could be anything, but waiting for a network or a NFS share is a common problem.

---

