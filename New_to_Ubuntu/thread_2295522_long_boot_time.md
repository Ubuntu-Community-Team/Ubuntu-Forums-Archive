---
title: "long boot time"
date: 2015-09-19
forum: New to Ubuntu
---

### Post by martreb on 2015-09-19
Im new to Linux and i feel like my boot time is way to long for such a light distro can you guys help me figure out what the issue is?
dmesg
```
    0.000000] BIOS-e820: [mem 0x000000007eb0b000-0x000000007ef53fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007ef54000-0x000000007effefff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007efff000-0x000000007effffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000047f3fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI 2.0=0x7eaca000  ACPI=0x7eaca000  SMBIOS=0x7ef52418 
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUSTeK COMPUTER INC. G751JT/G751JT, BIOS G751JT.205 10/29/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x47f400 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7F80000000 write-back
[    0.000000]   2 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   3 base 007FC00000 mask 7FFFC00000 uncachable
[    0.000000]   4 base 047F800000 mask 7FFF800000 uncachable
[    0.000000]   5 base 047F400000 mask 7FFFC00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 2GB, type UC
[    0.000000] reg 3, base: 2044MB, range: 4MB, type UC
[    0.000000] reg 4, base: 18424MB, range: 8MB, type UC
[    0.000000] reg 5, base: 18420MB, range: 4MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2044MB, range: 4MB, type UC
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8GB, range: 8GB, type WB
[    0.000000] reg 4, base: 16GB, range: 2GB, type WB
[    0.000000] reg 5, base: 18420MB, range: 4MB, type UC
[    0.000000] reg 6, base: 18424MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0x7fc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x7f000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE
[    0.000000] BRK [0x02fe6000, 0x02fe6fff] PGTABLE
[    0.000000] BRK [0x02fe7000, 0x02fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x47f200000-0x47f3fffff]
[    0.000000]  [mem 0x47f200000-0x47f3fffff] page 2M
[    0.000000] BRK [0x02fe8000, 0x02fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x460000000-0x47f1fffff]
[    0.000000]  [mem 0x460000000-0x47f1fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x440000000-0x45fffffff]
[    0.000000]  [mem 0x440000000-0x45fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x6d98dfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x6d7fffff] page 2M
[    0.000000]  [mem 0x6d800000-0x6d98dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x6d995000-0x6e203fff]
[    0.000000]  [mem 0x6d995000-0x6d9fffff] page 4k
[    0.000000]  [mem 0x6da00000-0x6e1fffff] page 2M
[    0.000000]  [mem 0x6e200000-0x6e203fff] page 4k
[    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x6e499000-0x7d8a9fff]
[    0.000000]  [mem 0x6e499000-0x6e5fffff] page 4k
[    0.000000]  [mem 0x6e600000-0x7d7fffff] page 2M
[    0.000000]  [mem 0x7d800000-0x7d8a9fff] page 4k
[    0.000000] BRK [0x02fea000, 0x02feafff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7dab4000-0x7de22fff]
[    0.000000]  [mem 0x7dab4000-0x7dbfffff] page 4k
[    0.000000]  [mem 0x7dc00000-0x7ddfffff] page 2M
[    0.000000]  [mem 0x7de00000-0x7de22fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x7efff000-0x7effffff]
[    0.000000]  [mem 0x7efff000-0x7effffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x43fffffff]
[    0.000000]  [mem 0x100000000-0x43fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x3583e000-0x36c16fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000007EACA000 000024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 0x000000007EACA090 0000AC (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x000000007EADEC50 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x000000007EACA258 0149F4 (v02 _ASUS_ Notebook 00000012 INTL 20120711)
[    0.000000] ACPI: FACS 0x000000007EB08F80 000040
[    0.000000] ACPI: APIC 0x000000007EADED60 000092 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x000000007EADEDF8 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT 0x000000007EADEE40 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x000000007EADEF08 00019D (v01 Intel  zpodd    00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x000000007EADF0A8 000539 (v01 PmRef  Cpu0Ist  00003000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x000000007EADF5E8 000AD8 (v01 PmRef  CpuPm    00003000 INTL 20120711)
[    0.000000] ACPI: MCFG 0x000000007EAE00C0 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x000000007EAE0100 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x000000007EAE0138 000298 (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x000000007EAE03D0 005955 (v01 SaSsdt SaSsdt   00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x000000007EAE5D28 000393 (v01 CppcTa CppcTabl 00001000 INTL 20120711)
[    0.000000] ACPI: PCCT 0x000000007EAE60C0 00006E (v05 PcctTa PcctTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x000000007EAE6130 000AC4 (v01 Cpc_Ta Cpc_Tabl 00001000 INTL 20120711)
[    0.000000] ACPI: BGRT 0x000000007EAE6BF8 000038 (v00 _ASUS_ Notebook 01072009 ASUS 00010013)
[    0.000000] ACPI: DMAR 0x000000007EAE6C30 000080 (v01 INTEL  HSW      00000001 INTL 00000001)
[    0.000000] ACPI: MSDM 0x000000007DAB2E18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000047f3fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x47f3f5000-0x47f3f9fff]
[    0.000000]  [ffffea0000000000-ffffea0011ffffff] PMD -> [ffff88046ea00000-ffff88047e9fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x47f3fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00057fff]
[    0.000000]   node   0: [mem 0x00059000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0x6d98dfff]
[    0.000000]   node   0: [mem 0x6d995000-0x6e203fff]
[    0.000000]   node   0: [mem 0x6e499000-0x7d8a9fff]
[    0.000000]   node   0: [mem 0x7dab4000-0x7de22fff]
[    0.000000]   node   0: [mem 0x7efff000-0x7effffff]
[    0.000000]   node   0: [mem 0x100000000-0x47f3fffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x47f3fffff]
[    0.000000] On node 0 totalpages: 4181274
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7974 pages used for memmap
[    0.000000]   DMA32 zone: 510334 pages, LIFO batch:31
[    0.000000]   Normal zone: 57296 pages used for memmap
[    0.000000]   Normal zone: 3666944 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x6d98e000-0x6d994fff]
[    0.000000] PM: Registered nosave memory: [mem 0x6e204000-0x6e498fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7d8aa000-0x7dab3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7de23000-0x7eb0afff]
[    0.000000] PM: Registered nosave memory: [mem 0x7eb0b000-0x7ef53fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7ef54000-0x7effefff]
[    0.000000] PM: Registered nosave memory: [mem 0x7f000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x7f000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88047f000000 s87104 r8192 d31680 u262144
[    0.000000] pcpu-alloc: s87104 r8192 d31680 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4115918
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-28-generic.efi.signed root=UUID=410f7e48-b06a-4880-884f-4e5f17bfca4d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16320464K/16725096K available (8002K kernel code, 1234K rwdata, 3764K rodata, 1408K init, 1300K bss, 404632K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] tsc: Detected 2494.225 MHz processor
[    0.000027] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.45 BogoMIPS (lpj=9976900)
[    0.000030] pid_max: default: 32768 minimum: 301
[    0.000034] ACPI: Core revision 20141107
[    0.019921] ACPI: All ACPI Tables successfully acquired
[    0.021023] Security Framework initialized
[    0.021039] AppArmor: AppArmor initialized
[    0.021040] Yama: becoming mindful.
[    0.021956] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.024721] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.025888] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.025903] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.026119] Initializing cgroup subsys memory
[    0.026124] Initializing cgroup subsys devices
[    0.026126] Initializing cgroup subsys freezer
[    0.026128] Initializing cgroup subsys net_cls
[    0.026130] Initializing cgroup subsys blkio
[    0.026132] Initializing cgroup subsys perf_event
[    0.026133] Initializing cgroup subsys net_prio
[    0.026135] Initializing cgroup subsys hugetlb
[    0.026156] CPU: Physical Processor ID: 0
[    0.026157] CPU: Processor Core ID: 0
[    0.026160] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.027060] mce: CPU supports 9 MCE banks
[    0.027073] CPU0: Thermal monitoring enabled (TM1)
[    0.027082] process: using mwait in idle threads
[    0.027085] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.027183] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
[    0.029381] Ignoring BGRT: invalid status 0 (expected 1)
[    0.030394] ftrace: allocating 30112 entries in 118 pages
[    0.042122] dmar: Host address width 39
[    0.042124] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.042131] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.042132] dmar: RMRR base: 0x0000007da4a000 end: 0x0000007da56fff
[    0.042244] IOAPIC id 8 under DRHD base  0xfed90000 IOMMU 0
[    0.042244] HPET id 0 under DRHD base 0xfed90000
[    0.042245] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.042318] Enabled IRQ remapping in x2apic mode
[    0.042320] Enabling x2apic
[    0.042320] Enabled x2apic
[    0.042325] Switched APIC routing to cluster x2apic.
[    0.042873] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082601] smpboot: CPU0: Intel(R) Core(TM) i7-4710HQ CPU @ 2.50GHz (fam: 06, model: 3c, stepping: 03)
[    0.082607] TSC deadline timer enabled
[    0.082630] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.082649] ... version:                3
[    0.082650] ... bit width:              48
[    0.082650] ... generic registers:      4
[    0.082651] ... value mask:             0000ffffffffffff
[    0.082652] ... max period:             0000ffffffffffff
[    0.082652] ... fixed-purpose events:   3
[    0.082653] ... event mask:             000000070000000f
[    0.083418] x86: Booting SMP configuration:
[    0.083420] .... node  #0, CPUs:      #1
[    0.097429] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.097507]  #2 #3 #4 #5 #6 #7
[    0.181627] x86: Booted up 1 node, 8 CPUs
[    0.181631] smpboot: Total of 8 processors activated (39907.60 BogoMIPS)
[    0.189152] devtmpfs: initialized
[    0.191750] evm: security.selinux
[    0.191751] evm: security.SMACK64
[    0.191751] evm: security.SMACK64EXEC
[    0.191752] evm: security.SMACK64TRANSMUTE
[    0.191753] evm: security.SMACK64MMAP
[    0.191754] evm: security.ima
[    0.191754] evm: security.capability
[    0.191797] PM: Registering ACPI NVS region [mem 0x6d98e000-0x6d994fff] (28672 bytes)
[    0.191799] PM: Registering ACPI NVS region [mem 0x7de23000-0x7eb0afff] (13533184 bytes)
[    0.192070] pinctrl core: initialized pinctrl subsystem
[    0.192160] RTC time: 16:36:34, date: 09/19/15
[    0.192257] NET: Registered protocol family 16
[    0.193002] cpuidle: using governor ladder
[    0.197006] cpuidle: using governor menu
[    0.197052] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.197053] ACPI: bus type PCI registered
[    0.197055] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.197117] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.197119] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.197256] PCI: Using configuration type 1 for base access
[    0.201360] ACPI: Added _OSI(Module Device)
[    0.201362] ACPI: Added _OSI(Processor Device)
[    0.201363] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.201364] ACPI: Added _OSI(Processor Aggregator Device)
[    0.203572] ACPI : EC: EC description table is found, configuring boot EC
[    0.205867] ACPI: Executed 2 blocks of module-level executable AML code
[    0.208789] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.211285] ACPI: Dynamic OEM Table Load:
[    0.211292] ACPI: SSDT 0xFFFF88046C0D4800 0003D3 (v01 PmRef  Cpu0Cst  00003001 INTL 20120711)
[    0.212031] ACPI: Dynamic OEM Table Load:
[    0.212036] ACPI: SSDT 0xFFFF88046C0CA800 0005AA (v01 PmRef  ApIst    00003000 INTL 20120711)
[    0.212814] ACPI: Dynamic OEM Table Load:
[    0.212818] ACPI: SSDT 0xFFFF88046C0DB400 000119 (v01 PmRef  ApCst    00003000 INTL 20120711)
[    0.214525] ACPI: Interpreter enabled
[    0.214534] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.214540] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.214558] ACPI: (supports S0 S3 S4 S5)
[    0.214559] ACPI: Using IOAPIC for interrupt routing
[    0.214582] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.222787] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.222792] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.223050] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.223211] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.223212] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.223564] PCI host bridge to bus 0000:00
[    0.223566] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.223568] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.223569] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.223571] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.223572] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.223573] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.223574] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.223575] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.223576] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.223578] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.223579] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.223580] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.223581] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.223582] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.223583] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.223585] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.223586] pci_bus 0000:00: root bus resource [mem 0x7fc00000-0xfeafffff]
[    0.223592] pci 0000:00:00.0: [8086:0c04] type 00 class 0x060000
[    0.223667] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.223701] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.223739] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.223812] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.223842] pci 0000:00:14.0: reg 0x10: [mem 0xed300000-0xed30ffff 64bit]
[    0.223941] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.223975] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.224012] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.224041] pci 0000:00:16.0: reg 0x10: [mem 0xed31a000-0xed31a00f 64bit]
[    0.224139] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.224222] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.224248] pci 0000:00:1a.0: reg 0x10: [mem 0xed318000-0xed3183ff]
[    0.224366] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.224411] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.224450] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.224474] pci 0000:00:1b.0: reg 0x10: [mem 0xed310000-0xed313fff 64bit]
[    0.224589] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.224627] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.224660] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.224775] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.224816] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.224852] pci 0000:00:1c.2: [8086:8c14] type 01 class 0x060400
[    0.224967] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.225008] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.225041] pci 0000:00:1c.3: [8086:8c16] type 01 class 0x060400
[    0.225161] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.225202] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.225245] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.225271] pci 0000:00:1d.0: reg 0x10: [mem 0xed317000-0xed3173ff]
[    0.225390] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.225435] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.225469] pci 0000:00:1f.0: [8086:8c4b] type 00 class 0x060100
[    0.225642] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    0.225668] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.225679] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.225691] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.225702] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.225713] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.225725] pci 0000:00:1f.2: reg 0x24: [mem 0xed316000-0xed3167ff]
[    0.225791] pci 0000:00:1f.2: PME# supported from D3hot
[    0.225852] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.225874] pci 0000:00:1f.3: reg 0x10: [mem 0xed315000-0xed3150ff 64bit]
[    0.225906] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.226026] pci 0000:01:00.0: [10de:13d8] type 00 class 0x030000
[    0.226037] pci 0000:01:00.0: reg 0x10: [mem 0xec000000-0xecffffff]
[    0.226047] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.226057] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.226064] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.226071] pci 0000:01:00.0: reg 0x30: [mem 0xed000000-0xed07ffff pref]
[    0.226129] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.226162] pci 0000:01:00.1: [10de:0fbb] type 00 class 0x040300
[    0.226172] pci 0000:01:00.1: reg 0x10: [mem 0xed080000-0xed083fff]
[    0.233087] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.233089] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.233091] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xed0fffff]
[    0.233094] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.233192] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.233200] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xebffffff]
[    0.233207] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0xbfffffff 64bit pref]
[    0.233305] acpiphp: Slot [1] registered
[    0.233449] pci 0000:3b:00.0: [8086:08b1] type 00 class 0x028000
[    0.233508] pci 0000:3b:00.0: reg 0x10: [mem 0xed200000-0xed201fff 64bit]
[    0.233780] pci 0000:3b:00.0: PME# supported from D0 D3hot D3cold
[    0.241118] pci 0000:00:1c.2: PCI bridge to [bus 3b]
[    0.241125] pci 0000:00:1c.2:   bridge window [mem 0xed200000-0xed2fffff]
[    0.241251] pci 0000:3c:00.0: [10ec:8168] type 00 class 0x020000
[    0.241272] pci 0000:3c:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.241305] pci 0000:3c:00.0: reg 0x18: [mem 0xed104000-0xed104fff 64bit]
[    0.241325] pci 0000:3c:00.0: reg 0x20: [mem 0xed100000-0xed103fff 64bit]
[    0.241437] pci 0000:3c:00.0: supports D1 D2
[    0.241438] pci 0000:3c:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.249114] pci 0000:00:1c.3: PCI bridge to [bus 3c]
[    0.249119] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.249123] pci 0000:00:1c.3:   bridge window [mem 0xed100000-0xed1fffff]
[    0.249818] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    0.249856] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.249891] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.249926] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.249960] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.249995] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.250029] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.250063] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.250318] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.250381] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.250457] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.250459] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.250460] vgaarb: loaded
[    0.250461] vgaarb: bridge control possible 0000:01:00.0
[    0.250628] SCSI subsystem initialized
[    0.250659] libata version 3.00 loaded.
[    0.250677] ACPI: bus type USB registered
[    0.250691] usbcore: registered new interface driver usbfs
[    0.250698] usbcore: registered new interface driver hub
[    0.250715] usbcore: registered new device driver usb
[    0.250851] PCI: Using ACPI for IRQ routing
[    0.256174] PCI: pci_cache_line_size set to 64 bytes
[    0.256247] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.256248] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.256249] e820: reserve RAM buffer [mem 0x6d98e000-0x6fffffff]
[    0.256250] e820: reserve RAM buffer [mem 0x6e204000-0x6fffffff]
[    0.256251] e820: reserve RAM buffer [mem 0x7d8aa000-0x7fffffff]
[    0.256253] e820: reserve RAM buffer [mem 0x7de23000-0x7fffffff]
[    0.256254] e820: reserve RAM buffer [mem 0x7f000000-0x7fffffff]
[    0.256255] e820: reserve RAM buffer [mem 0x47f400000-0x47fffffff]
[    0.256345] NetLabel: Initializing
[    0.256346] NetLabel:  domain hash size = 128
[    0.256347] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.256356] NetLabel:  unlabeled traffic allowed by default
[    0.256413] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.256418] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.258459] Switched to clocksource hpet
[    0.263310] AppArmor: AppArmor Filesystem Enabled
[    0.263358] pnp: PnP ACPI init
[    0.263425] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.263428] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.263623] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.263625] system 00:01: [io  0xffff] has been reserved
[    0.263626] system 00:01: [io  0xffff] has been reserved
[    0.263627] system 00:01: [io  0xffff] has been reserved
[    0.263629] system 00:01: [io  0x1c00-0x1cfe] has been reserved
[    0.263630] system 00:01: [io  0x1d00-0x1dfe] has been reserved
[    0.263631] system 00:01: [io  0x1e00-0x1efe] has been reserved
[    0.263633] system 00:01: [io  0x1f00-0x1ffe] has been reserved
[    0.263634] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.263636] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.263637] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.263662] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.263698] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.263700] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.263737] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.263738] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.263763] system 00:05: [io  0x0240-0x0259] has been reserved
[    0.263764] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.263811] pnp 00:06: Plug and Play ACPI device, IDs ETD010d SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 ETD0000 (active)
[    0.263843] pnp 00:07: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.264134] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.264135] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.264137] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.264138] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.264140] system 00:08: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.264141] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.264143] system 00:08: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.264144] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.264146] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
[    0.264147] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.264149] system 00:08: [mem 0xeffdf000-0xeffdffff] has been reserved
[    0.264150] system 00:08: [mem 0xeffe0000-0xeffeffff] has been reserved
[    0.264152] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.264208] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.264415] pnp: PnP ACPI: found 10 devices
[    0.270619] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-3a] add_size 1000
[    0.270630] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 3b] add_size 1000
[    0.270632] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 3b] add_size 200000
[    0.270645] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.270646] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.270647] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.270657] pci 0000:00:1c.2: BAR 15: assigned [mem 0x7fc00000-0x7fdfffff 64bit pref]
[    0.270659] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.270661] pci 0000:00:1c.2: BAR 13: assigned [io  0x3000-0x3fff]
[    0.270663] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.270665] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.270668] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xed0fffff]
[    0.270670] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.270673] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.270676] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.270682] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xebffffff]
[    0.270686] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0xbfffffff 64bit pref]
[    0.270693] pci 0000:00:1c.2: PCI bridge to [bus 3b]
[    0.270696] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.270701] pci 0000:00:1c.2:   bridge window [mem 0xed200000-0xed2fffff]
[    0.270706] pci 0000:00:1c.2:   bridge window [mem 0x7fc00000-0x7fdfffff 64bit pref]
[    0.270713] pci 0000:00:1c.3: PCI bridge to [bus 3c]
[    0.270715] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.270721] pci 0000:00:1c.3:   bridge window [mem 0xed100000-0xed1fffff]
[    0.270732] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.270733] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.270734] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.270735] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.270737] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.270738] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.270739] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.270740] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.270742] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.270743] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.270744] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.270745] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.270746] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.270748] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.270749] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.270750] pci_bus 0000:00: resource 19 [mem 0x7fc00000-0xfeafffff]
[    0.270751] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.270753] pci_bus 0000:01: resource 1 [mem 0xec000000-0xed0fffff]
[    0.270754] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.270755] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.270756] pci_bus 0000:02: resource 1 [mem 0xd4000000-0xebffffff]
[    0.270758] pci_bus 0000:02: resource 2 [mem 0x90000000-0xbfffffff 64bit pref]
[    0.270759] pci_bus 0000:3b: resource 0 [io  0x3000-0x3fff]
[    0.270760] pci_bus 0000:3b: resource 1 [mem 0xed200000-0xed2fffff]
[    0.270761] pci_bus 0000:3b: resource 2 [mem 0x7fc00000-0x7fdfffff 64bit pref]
[    0.270763] pci_bus 0000:3c: resource 0 [io  0xd000-0xdfff]
[    0.270764] pci_bus 0000:3c: resource 1 [mem 0xed100000-0xed1fffff]
[    0.270786] NET: Registered protocol family 2
[    0.270962] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.271141] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.271244] TCP: Hash tables configured (established 131072 bind 65536)
[    0.271258] TCP: reno registered
[    0.271274] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.271317] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.271381] NET: Registered protocol family 1
[    0.271664] PCI: CLS mismatch (64 != 128), using 64 bytes
[    0.271785] pci 0000:01:00.0: Video device with shadowed ROM
[    0.271834] Trying to unpack rootfs image as initramfs...
[    0.557568] Freeing initrd memory: 20324K (ffff88003583e000 - ffff880036c17000)
[    0.557589] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.557592] software IO TLB [mem 0x771b5000-0x7b1b5000] (64MB) mapped at [ffff8800771b5000-ffff88007b1b4fff]
[    0.557846] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.557895] microcode: CPU0 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557902] microcode: CPU1 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557910] microcode: CPU2 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557917] microcode: CPU3 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557924] microcode: CPU4 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557932] microcode: CPU5 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557938] microcode: CPU6 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557944] microcode: CPU7 sig=0x306c3, pf=0x20, revision=0x1c
[    0.557984] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.558007] Scanning for low memory corruption every 60 seconds
[    0.558309] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.558325] Initialise system trusted keyring
[    0.558341] audit: initializing netlink subsys (disabled)
[    0.558351] audit: type=2000 audit(1442680594.548:1): initialized
[    0.558662] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.559881] zpool: loaded
[    0.559883] zbud: loaded
[    0.560031] VFS: Disk quotas dquot_6.5.2
[    0.560060] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.560440] fuse init (API version 7.23)
[    0.560553] Key type big_key registered
[    0.561004] Key type asymmetric registered
[    0.561007] Asymmetric key parser 'x509' registered
[    0.561036] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.561104] io scheduler noop registered
[    0.561107] io scheduler deadline registered (default)
[    0.561132] io scheduler cfq registered
[    0.561666] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.561680] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.561713] efifb: probing for efifb
[    0.561733] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90009c00000, using 8640k, total 8640k
[    0.561735] efifb: mode is 1920x1080x32, linelength=8192, pages=1
[    0.561735] efifb: scrolling: redraw
[    0.561737] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.561818] Console: switching to colour frame buffer device 240x67
[    0.561837] fb0: EFI VGA frame buffer device
[    0.561845] intel_idle: MWAIT substates: 0x42120
[    0.561846] intel_idle: v0.4 model 0x3C
[    0.561847] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.562181] ACPI: AC Adapter [AC0] (on-line)
[    0.562272] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.564052] ACPI: Lid Switch [LID]
[    0.564088] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.564090] ACPI: Sleep Button [SLPB]
[    0.564119] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.564121] ACPI: Power Button [PWRF]
[    0.564833] thermal LNXTHERM:00: registered as thermal_zone0
[    0.564835] ACPI: Thermal Zone [THRM] (46 C)
[    0.564865] GHES: HEST is not enabled!
[    0.564962] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.567513] Linux agpgart interface v0.103
[    0.569026] brd: module loaded
[    0.569794] loop: module loaded
[    0.569967] libphy: Fixed MDIO Bus: probed
[    0.569970] tun: Universal TUN/TAP device driver, 1.6
[    0.569970] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.570026] PPP generic driver version 2.4.2
[    0.570177] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.570184] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.570298] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.570383] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.570384] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.570386] usb usb1: Product: xHCI Host Controller
[    0.570387] usb usb1: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.570388] usb usb1: SerialNumber: 0000:00:14.0
[    0.570497] hub 1-0:1.0: USB hub found
[    0.570520] hub 1-0:1.0: 14 ports detected
[    0.575367] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.575372] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.575404] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.575405] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.575406] usb usb2: Product: xHCI Host Controller
[    0.575408] usb usb2: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
[    0.575409] usb usb2: SerialNumber: 0000:00:14.0
[    0.575537] hub 2-0:1.0: USB hub found
[    0.575552] hub 2-0:1.0: 6 ports detected
[    0.577462] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.577471] ehci-pci: EHCI PCI platform driver
[    0.577593] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.577599] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.577622] ehci-pci 0000:00:1a.0: debug port 2
[    0.581525] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.581539] ehci-pci 0000:00:1a.0: irq 16, io mem 0xed318000
[    0.588556] ACPI: Battery Slot [BAT0] (battery present)
[    0.590837] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.591012] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.591013] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.591014] usb usb3: Product: EHCI Host Controller
[    0.591016] usb usb3: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
[    0.591017] usb usb3: SerialNumber: 0000:00:1a.0
[    0.591157] hub 3-0:1.0: USB hub found
[    0.591187] hub 3-0:1.0: 2 ports detected
[    0.591465] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.591471] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    0.591492] ehci-pci 0000:00:1d.0: debug port 2
[    0.595395] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.595407] ehci-pci 0000:00:1d.0: irq 23, io mem 0xed317000
[    0.606875] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.606986] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.606988] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.606990] usb usb4: Product: EHCI Host Controller
[    0.606991] usb usb4: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
[    0.606992] usb usb4: SerialNumber: 0000:00:1d.0
[    0.607149] hub 4-0:1.0: USB hub found
[    0.607154] hub 4-0:1.0: 2 ports detected
[    0.607254] ehci-platform: EHCI generic platform driver
[    0.607263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.607268] ohci-pci: OHCI PCI platform driver
[    0.607277] ohci-platform: OHCI generic platform driver
[    0.607284] uhci_hcd: USB Universal Host Controller Interface driver
[    0.607332] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.611068] i8042: Detected active multiplexing controller, rev 1.1
[    0.612267] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.612270] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.612291] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.612309] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.612324] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.612583] mousedev: PS/2 mouse device common for all mice
[    0.612898] rtc_cmos 00:02: RTC can wake from S4
[    0.613038] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.613067] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.613084] i2c /dev entries driver
[    0.613134] device-mapper: uevent: version 1.0.3
[    0.613212] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.613231] Intel P-state driver initializing.
[    0.613449] Consider also installing thermald for improved thermal control.
[    0.613456] ledtrig-cpu: registered to indicate activity on CPUs
[    0.613461] EFI Variables Facility v0.08 2004-May-17
[    0.617056] Error parsing PCC subspaces from PCCT
[    0.617057] ACPI PCC probe failed.
[    0.617116] TCP: cubic registered
[    0.617174] NET: Registered protocol family 10
[    0.617457] NET: Registered protocol family 17
[    0.617467] Key type dns_resolver registered
[    0.617943] Loading compiled-in X.509 certificates
[    0.618701] Loaded X.509 cert 'Magrathea: Glacier signing key: 99112ef1a6ba85be992582e9fef3a23f1a888175'
[    0.618713] registered taskstats version 1
[    0.620463] Key type trusted registered
[    0.623684] Key type encrypted registered
[    0.623690] AppArmor: AppArmor sha1 policy hashing enabled
[    0.623693] ima: No TPM chip found, activating TPM-bypass!
[    0.623714] evm: HMAC attrs: 0x1
[    0.624252]   Magic number: 15:723:641
[    0.624397] rtc_cmos 00:02: setting system clock to 2015-09-19 16:36:34 UTC (1442680594)
[    0.624491] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.624492] EDD information not available.
[    0.624567] PM: Hibernation image not present or could not be loaded.
[    0.624901] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
[    0.624902] Write protecting the kernel read-only data: 12288k
[    0.625214] Freeing unused kernel memory: 176K (ffff8800027d4000 - ffff880002800000)
[    0.625344] Freeing unused kernel memory: 332K (ffff880002bad000 - ffff880002c00000)
[    0.633319] random: systemd-udevd urandom read with 9 bits of entropy available
[    0.651092] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.651101] r8169 0000:3c:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.651271] ahci 0000:00:1f.2: version 3.0
[    0.651403] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    0.651458] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x5 impl SATA mode
[    0.651461] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    0.654627] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.659505] scsi host0: ahci
[    0.659649] scsi host1: ahci
[    0.659796] scsi host2: ahci
[    0.659980] r8169 0000:3c:00.0 eth0: RTL8168g/8111g at 0xffffc900018e0000, 08:62:66:51:07:04, XID 10900800 IRQ 28
[    0.659982] r8169 0000:3c:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.660003] scsi host3: ahci
[    0.660073] ata1: SATA max UDMA/133 abar m2048@0xed316000 port 0xed316100 irq 27
[    0.660075] ata2: DUMMY
[    0.660079] ata3: SATA max UDMA/133 abar m2048@0xed316000 port 0xed316200 irq 27
[    0.660080] ata4: DUMMY
[    0.887192] usb 1-5: new full-speed USB device number 2 using xhci_hcd
[    0.903221] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    0.919266] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    0.979349] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.980729] ata1.00: ATA-8: HGST HTS721010A9E630, JB0OA3J0, max UDMA/133
[    0.980732] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.982252] ata1.00: configured for UDMA/133
[    0.982409] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS721010A9 A3J0 PQ: 0 ANSI: 5
[    0.982641] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.982644] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    0.982672] sd 0:0:0:0: [sda] Write Protect is off
[    0.982674] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.982683] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.982686] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.016513] usb 1-5: New USB device found, idVendor=8087, idProduct=07dc
[    1.016516] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.035739] usb 3-1: New USB device found, idVendor=8087, idProduct=8008
[    1.035741] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.036007] hub 3-1:1.0: USB hub found
[    1.036103] hub 3-1:1.0: 6 ports detected
[    1.051784] usb 4-1: New USB device found, idVendor=8087, idProduct=8000
[    1.051787] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.051798]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    1.052010] hub 4-1:1.0: USB hub found
[    1.052125] hub 4-1:1.0: 8 ports detected
[    1.052392] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.183555] usb 1-7: new high-speed USB device number 3 using xhci_hcd
[    1.299699] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.301890] ata3.00: ATAPI: HL-DT-ST DVDRAM GUC0N, AS01, max UDMA/133
[    1.304823] ata3.00: configured for UDMA/133
[    1.311221] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GUC0N     AS01 PQ: 0 ANSI: 5
[    1.331730] sr 2:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.331734] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.331897] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.331979] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.343874] usb 1-7: New USB device found, idVendor=04f2, idProduct=b414
[    1.343877] usb 1-7: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.343879] usb 1-7: Product: USB2.0 HD UVC WebCam
[    1.343880] usb 1-7: Manufacturer: Chicony Electronics Co.,Ltd.
[    1.343881] usb 1-7: SerialNumber: 0x0001
[    1.423013] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x360f06)
[    1.438594] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x16, 0x0c.
[    1.511882] usb 1-10: new full-speed USB device number 4 using xhci_hcd
[    1.513431] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
[    1.555903] tsc: Refined TSC clocksource calibration: 2494.224 MHz
[    1.709480] usb 1-10: New USB device found, idVendor=0b05, idProduct=17fd
[    1.709483] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.709485] usb 1-10: Product: ASUS ROG Macrokey
[    1.709486] usb 1-10: Manufacturer: ASUS
[    1.714507] hidraw: raw HID events driver (C) Jiri Kosina
[    1.725089] hid (null): usage index exceeded
[    2.100089] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.557299] Switched to clocksource tsc
[   11.737576] usbcore: registered new interface driver usbhid
[   11.737579] usbhid: USB HID core driver
[   11.850283] random: nonblocking pool is initialized
[   12.232242] systemd[1]: RTC configured in localtime, applying delta of 120 minutes to system time.
[   12.424983] systemd[1]: Inserted module 'autofs4'
[   12.514080] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   12.514230] systemd[1]: Detected architecture x86-64.
[   12.525546] systemd[1]: Set hostname to <martreb-G751JT>.
[   13.515265] systemd[1]: Created slice Root Slice.
[   13.515277] systemd[1]: Starting Root Slice.
[   13.515304] systemd[1]: Listening on Journal Socket (/dev/log).
[   13.515310] systemd[1]: Starting Journal Socket (/dev/log).
[   13.515329] systemd[1]: Listening on udev Control Socket.
[   13.515334] systemd[1]: Starting udev Control Socket.
[   13.515397] systemd[1]: Listening on Journal Audit Socket.
[   13.515404] systemd[1]: Starting Journal Audit Socket.
[   13.515411] systemd[1]: Reached target Encrypted Volumes.
[   13.515416] systemd[1]: Starting Encrypted Volumes.
[   13.515432] systemd[1]: Listening on udev Kernel Socket.
[   13.515437] systemd[1]: Starting udev Kernel Socket.
[   13.515463] systemd[1]: Listening on Journal Socket.
[   13.515472] systemd[1]: Starting Journal Socket.
[   13.515487] systemd[1]: Listening on fsck to fsckd communication Socket.
[   13.515492] systemd[1]: Starting fsck to fsckd communication Socket.
[   13.515517] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   13.515523] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[   13.515529] systemd[1]: Reached target Remote File Systems (Pre).
[   13.515534] systemd[1]: Starting Remote File Systems (Pre).
[   13.515672] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   13.515680] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[   13.515703] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   13.515709] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[   13.515774] systemd[1]: Created slice System Slice.
[   13.515785] systemd[1]: Starting System Slice.
[   13.516064] systemd[1]: Mounting POSIX Message Queue File System...
[   13.516338] systemd[1]: Starting Increase datagram queue length...
[   13.516632] systemd[1]: Starting Uncomplicated firewall...
[   13.516937] systemd[1]: Mounting Huge Pages File System...
[   13.517268] systemd[1]: Mounting Debug File System...
[   13.517337] systemd[1]: Created slice system-getty.slice.
[   13.517346] systemd[1]: Starting system-getty.slice.
[   13.600523] systemd[1]: Started Set Up Additional Binary Formats.
[   13.600965] systemd[1]: Started Read required files in advance.
[   13.601103] systemd[1]: Starting Read required files in advance...
[   13.664605] systemd[1]: Starting Load Kernel Modules...
[   13.664979] systemd[1]: Starting udev Coldplug all Devices...
[   13.665354] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   13.665635] systemd[1]: Starting Nameserver information manager...
[   13.665697] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   13.665715] systemd[1]: Starting system-systemd\x2dfsck.slice.
[   13.665969] systemd[1]: Starting Setup Virtual Console...
[   13.666014] systemd[1]: Listening on Delayed Shutdown Socket.
[   13.666023] systemd[1]: Starting Delayed Shutdown Socket.
[   13.666088] systemd[1]: Created slice User and Session Slice.
[   13.666094] systemd[1]: Starting User and Session Slice.
[   13.666100] systemd[1]: Reached target Slices.
[   13.666104] systemd[1]: Starting Slices.
[   13.706720] systemd[1]: Started Uncomplicated firewall.
[   13.797918] systemd[1]: Started Setup Virtual Console.
[   13.875871] systemd[1]: Started udev Coldplug all Devices.
[   13.876224] systemd[1]: Starting udev Wait for Complete Device Initialization...
[   13.890665] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   13.891095] systemd[1]: Starting Create Static Device Nodes in /dev...
[   14.022264] systemd[1]: Mounted POSIX Message Queue File System.
[   14.022306] systemd[1]: Mounted Debug File System.
[   14.022331] systemd[1]: Mounted Huge Pages File System.
[   14.022580] systemd[1]: Started Increase datagram queue length.
[   14.027900] systemd[1]: Listening on Syslog Socket.
[   14.027908] systemd[1]: Starting Syslog Socket.
[   14.028210] systemd[1]: Starting Journal Service...
[   14.029571] systemd[1]: Started Nameserver information manager.
[   14.207927] lp: driver loaded but no devices found
[   14.210142] ppdev: user-space parallel port driver
[   14.291996] systemd[1]: Started Load Kernel Modules.
[   14.292467] systemd[1]: Starting Apply Kernel Variables...
[   14.292774] systemd[1]: Mounting FUSE Control File System...
[   14.292829] systemd[1]: Mounted Configuration File System.
[   14.294191] systemd[1]: Mounted FUSE Control File System.
[   14.344629] systemd[1]: Started Create Static Device Nodes in /dev.
[   14.345068] systemd[1]: Starting udev Kernel Device Manager...
[   14.405709] systemd[1]: Started Apply Kernel Variables.
[   14.519158] systemd[1]: Started Journal Service.
[   15.532025] wmi: Mapper loaded
[   15.564103] EDAC MC: Ver: 3.0.0
[   15.653726] EDAC ie31200: No ECC support
[   15.656075] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   15.662040] acpi device:63: registered as cooling_device8
[   15.664162] acpi device:66: registered as cooling_device9
[   15.664207] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:60/LNXVIDEO:00/input/input12
[   15.681667] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.923978] [drm] Initialized drm 1.1.0 20060810
[   15.959380] Bluetooth: Core ver 2.20
[   15.959389] NET: Registered protocol family 31
[   15.959390] Bluetooth: HCI device and connection manager initialized
[   15.959392] Bluetooth: HCI socket layer initialized
[   15.959394] Bluetooth: L2CAP socket layer initialized
[   15.959397] Bluetooth: SCO socket layer initialized
[   16.053200] cfg80211: Calling CRDA to update world regulatory domain
[   16.234764] usbcore: registered new interface driver btusb
[   16.247154] Bluetooth: hci0: read Intel version: 3707100180012d0d00
[   16.256367] AVX2 version of gcm_enc/dec engaged.
[   16.256369] AES CTR mode by8 optimization enabled
[   16.325090] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   16.325092] Copyright(c) 2003- 2014 Intel Corporation
[   16.399495] asus_wmi: ASUS WMI generic driver loaded
[   16.435370] asus_wmi: Initialization: 0x1
[   16.435411] asus_wmi: BIOS WMI version: 7.9
[   16.435440] asus_wmi: SFUN value: 0x4a0877
[   16.436002] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input13
[   16.443511] asus_wmi: Backlight controlled by ACPI video driver
[   16.448206] iwlwifi 0000:3b:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[   16.576367] snd_hda_intel 0000:01:00.1: Disabling MSI
[   16.576372] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.641697] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[   16.747898] sound hdaudioC0D0: autoconfig: line_outs=1 (0x15/0x0/0x0/0x0/0x0) type:line
[   16.747902] sound hdaudioC0D0:    speaker_outs=2 (0x14/0x1a/0x0/0x0/0x0)
[   16.747903] sound hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.747904] sound hdaudioC0D0:    mono: mono_out=0x0
[   16.747905] sound hdaudioC0D0:    dig-out=0x1e/0x0
[   16.747905] sound hdaudioC0D0:    inputs:
[   16.747907] sound hdaudioC0D0:      Mic=0x18
[   16.747908] sound hdaudioC0D0:      Internal Mic=0x12
[   16.749690] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   16.757077] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.757120] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   16.792160] iwlwifi 0000:3b:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   16.792234] iwlwifi 0000:3b:00.0: L1 Enabled - LTR Enabled
[   16.792507] iwlwifi 0000:3b:00.0: L1 Enabled - LTR Enabled
[   16.976883] media: Linux media interface: v0.10
[   16.995148] Linux video capture interface: v2.00
[   17.016455] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.072559] input: ASUS ASUS ROG Macrokey as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/0003:0B05:17FD.0001/input/input17
[   17.089320] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[   17.106623] intel_rapl: Found RAPL domain package
[   17.106626] intel_rapl: Found RAPL domain core
[   17.106630] intel_rapl: Found RAPL domain dram
[   17.125206] hid-generic 0003:0B05:17FD.0001: input,hidraw0: USB HID v1.10 Keyboard [ASUS ASUS ROG Macrokey] on usb-0000:00:14.0-10/input0
[   17.125218] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[   17.125312] hid-generic 0003:0B05:17FD.0002: usage index exceeded
[   17.125314] hid-generic 0003:0B05:17FD.0002: item 0 2 2 2 parsing failed
[   17.125322] hid-generic: probe of 0003:0B05:17FD.0002 failed with error -22
[   17.167903] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (04f2:b414)
[   17.168931] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input19
[   17.168994] usbcore: registered new interface driver uvcvideo
[   17.168995] USB Video Class driver (1.1.1)
[   17.744095] cfg80211: World regulatory domain updated:
[   17.744098] cfg80211:  DFS Master region: unset
[   17.744099] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   17.744101] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   17.744103] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   17.744104] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   17.744106] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   17.744107] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   17.744108] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   17.744109] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   17.744111] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   18.221856] nvidia: module license 'NVIDIA' taints kernel.
[   18.221859] Disabling lock debugging due to kernel taint
[   18.223808] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   18.226445] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.226677] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[   18.226680] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.59  Tue Mar 31 14:10:31 PDT 2015
[   18.817927] Adding 16724988k swap on /dev/sda8.  Priority:-1 extents:1 across:16724988k FS
[   27.136143] hid-generic 0003:0B05:17FD.0003: usb_submit_urb(ctrl) failed: -1
[   27.136164] hid-generic 0003:0B05:17FD.0003: timeout initializing reports
[   27.136331] hid-generic 0003:0B05:17FD.0003: hiddev0,hidraw1: USB HID v1.10 Device [ASUS ASUS ROG Macrokey] on usb-0000:00:14.0-10/input2
[   27.316609] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   27.348407] systemd-journald[276]: Received request to flush runtime journal from PID 1
[   28.048191] audit: type=1400 audit(1442673421.887:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=569 comm="apparmor_parser"
[   28.048206] audit: type=1400 audit(1442673421.887:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=569 comm="apparmor_parser"
[   28.049320] audit: type=1400 audit(1442673421.891:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=569 comm="apparmor_parser"
[   28.049335] audit: type=1400 audit(1442673421.891:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=569 comm="apparmor_parser"
[   28.049337] audit: type=1400 audit(1442673421.891:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=569 comm="apparmor_parser"
[   28.049340] audit: type=1400 audit(1442673421.891:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=569 comm="apparmor_parser"
[   28.054300] audit: type=1400 audit(1442673421.895:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=569 comm="apparmor_parser"
[   28.054314] audit: type=1400 audit(1442673421.895:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=569 comm="apparmor_parser"
[   28.054317] audit: type=1400 audit(1442673421.895:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=569 comm="apparmor_parser"
[   28.054320] audit: type=1400 audit(1442673421.895:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=569 comm="apparmor_parser"
[   28.435312] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.435314] Bluetooth: BNEP filters: protocol multicast
[   28.435316] Bluetooth: BNEP socket layer initialized
[   28.437593] Bluetooth: RFCOMM TTY layer initialized
[   28.437596] Bluetooth: RFCOMM socket layer initialized
[   28.437599] Bluetooth: RFCOMM ver 1.11
[   29.668951] r8169 0000:3c:00.0 eth0: link down
[   29.670651] iwlwifi 0000:3b:00.0: L1 Enabled - LTR Enabled
[   29.670966] iwlwifi 0000:3b:00.0: L1 Enabled - LTR Enabled
[   30.664846] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664881] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664901] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664910] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664918] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664932] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664941] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.664949] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   30.991091] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[   33.049140] wlan0: authenticate with d4:21:22:db:83:9d
[   33.053055] wlan0: send auth to d4:21:22:db:83:9d (try 1/3)
[   33.053848] wlan0: authenticated
[   33.054507] wlan0: associate with d4:21:22:db:83:9d (try 1/3)
[   33.056049] wlan0: RX AssocResp from d4:21:22:db:83:9d (capab=0x11 status=0 aid=1)
[   33.065696] wlan0: associated
[   33.065755] cfg80211: Calling CRDA for country: DE
[   33.083250] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by d4:21:22:db:83:9d
[   33.094668] cfg80211: Regulatory domain changed to country: DE
[   33.094671] cfg80211:  DFS Master region: ETSI
[   33.094673] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   33.094674] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   33.094676] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   33.094677] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   33.094679] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[   33.094680] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)


```
It seems like its hanging a couple of times but i have no idea where to even start.

Thanks for any help

---

### Post by mikewhatever on 2015-09-19
Perhaps start with your expectations. How fast do you expect it to boot?

---

### Post by martreb on 2015-09-19
I see no reason on why such a lightweight build would take 30 seconds i can boot into win 7 faster then that.=/
Just trying to optimize boot time no real goal on how long it should take.

---

### Post by Bucky Ball on 2015-09-19
Welcome. Windows 7 is probably set to hibernate, which means it doesn't actually shutdown or close the partition and that's why you can boot to that in less than 30 seconds. It's still running even. Boot to Windows, switch hibernation off, then do a comparison.

---

### Post by mikewhatever on 2015-09-19
> **martreb said:**
> I see no reason on why such a lightweight build would take 30 seconds i can boot into win 7 faster then that.=/
Just trying to optimize boot time no real goal on how long it should take.

Depends on the hardware, but seriously, 30 seconds in not so bad for a very wide range of machines.

---

### Post by Bucky Ball on 2015-09-19
Mine takes around 30 seconds, or just under. 4Gb or RAM, i3 processor, hard drives, not SSD. My HP Stream with 2Gb and an eMMC card, not a hard drive, boots in about half that, just under 15 seconds. eMMC is very fast. 

What does your machine have? Do you have Windows and Ubuntu both installed on a HDD or SSD?

---

### Post by martreb on 2015-09-19
It is an Asus g751JT, core i7 2.5 ghz, 16 gigs of ram and a gtx 970m.
All around it is a pretty solid laptop. I almost always do a full shutdown with windows not just hibernate 
I could be wrong but i just feel like it is getting hung up a few times during boot with ~10 second delays or so.

But like i said i am new and could just be expecting too much.

---

### Post by QIII on 2015-09-19
What would really be diagnostic is if you could get a good average time to GUI from a fully shut-down Windows (do it several times for an average) and the same for Ubuntu.  Compare from power button press to GUI both ways so you are comparing apples to apples.

But you really must be sure that you are not getting skewed results if your Windows is using the fast-boot/BIOS-UEFI shortcuts.

---

### Post by martreb on 2015-09-19
> **QIII said:**
> What would really be diagnostic is if you could get a good average time to GUI from a fully shut-down Windows (do it several times for an average) and the same for Ubuntu.  Compare from power button press to GUI both ways so you are comparing apples to apples.

But you really must be sure that you are not getting skewed results if your Windows is using the fast-boot/BIOS-UEFI shortcuts.

After 3 boots on each side W/ Fast-boot disabled in bios i am getting a 28 second boot time into Windows and a 32 second load time into Lubuntu.
Neither of these boot times are slow or that bad really but i was still expecting to get a little bit more out of the much lighter system.

Once again all help is much appreciated =)

---

### Post by QIII on 2015-09-19
That difference is negligible, but it would be nice to improve it.

What processes do you have set to run at startup?

---

### Post by martreb on 2015-09-19
> **QIII said:**
> That difference is negligible, but it would be nice to improve it.

What processes do you have set to run at startup?

The difference is not really that bad , but faster is always better.
Is there an easy way to check startup services. Once again i am pretty new =/

---

### Post by mystics on 2015-09-20
I'm not sure about Lubuntu in particular, but you should have something in your settings/preferences that allows you to manage the startup applications. Just make sure you know what the application does before you decide to not allow it to automatically start.

---

### Post by deadflowr on 2015-09-20
I find boot time remains similar regardless of desktop session running.

Better to look at how fast you can actually get your first major application running over how fast you get to a desktop screen. IMHO.
Example, see how long it takes you to get from hitting the power button to getting to this page.

---

### Post by Bucky Ball on 2015-09-20
Install the OS on an SSD or an eMMC card and see if it makes a difference. ;)

But seriously, is it installed on a regular hard drive? Not sure if you said ...

---

### Post by oldfred on 2015-09-20
Are you booting with Intel video or nVidia? And then is correct nVidia driver installed. Either incorrect nVidia driver or no nVidia driver can cause other seemingly unrelated issues. Or you may need other boot parameters.

Large gaps in time stamp are things to review.

> 
[    2.557299] Switched to clocksource tsc
[   11.737576] usbcore: registered new interface driver usbhid

[   18.817927] Adding 16724988k swap on /dev/sda8.  Priority:-1 extents:1 across:16724988k FS
[   27.136143] hid-generic 0003:0B05:17FD.0003: usb_submit_urb(ctrl) failed: -1


And potentially some of the other entries with a couple of seconds gap. 
Do not know about issues with clocksource or usbhid. (not sure if time stamp is one before or after)
How large is swap? With that much RAM is should only be  2GB or perhaps none?

ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

Just saw this in another thread.
 USB port issues: Under "Advanced CPU"  found another boot setting called "Boot performance mode"
[https://bbs.archlinux.org/viewtopic.php?id=198460](https://bbs.archlinux.org/viewtopic.php?id=198460)

---

### Post by buzzingrobot on 2015-09-20
Does Lubuntu use Systemd?  "systemd-analyze blame"  generates a roster of the boot processes and the time each took.

---

