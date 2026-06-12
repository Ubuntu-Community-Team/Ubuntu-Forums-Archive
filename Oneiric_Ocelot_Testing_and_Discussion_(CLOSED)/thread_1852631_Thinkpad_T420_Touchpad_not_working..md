---
title: "Thinkpad T420 Touchpad not working."
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-09-30
Hello,

I did a new system install and after updating touchpad stopped working. Trackpoint is working fine.

Here is dmesg log.

Thanks.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #19-Ubuntu SMP Fri Sep 23 21:23:39 UTC 2011 (Ubuntu 3.0.0-12.19-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-12-generic root=/dev/sda5 ro rootflags=subvol=@ quiet splash pcie_aspm=force i915.i915_enable_rc6=1 vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000ba99f000 (usable)
[    0.000000]  BIOS-e820: 00000000ba99f000 - 00000000bae9f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae9f000 - 00000000baf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000baf9f000 - 00000000bafff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bafff000 - 00000000bb000000 (usable)
[    0.000000]  BIOS-e820: 00000000bb000000 - 00000000bfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed08000 - 00000000fed09000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd20000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000023e600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: LENOVO 4177CTO/4177CTO, BIOS 83ET60WW (1.30 ) 06/16/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x23e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   3 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   4 base 100000000 mask F00000000 write-back
[    0.000000]   5 base 200000000 mask FC0000000 write-back
[    0.000000]   6 base 23F000000 mask FFF000000 uncachable
[    0.000000]   7 base 23E800000 mask FFF800000 uncachable
[    0.000000]   8 base 23E600000 mask FFFE00000 uncachable
[    0.000000]   9 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb000000
[    0.000000]  0000000000 - 00bb000000 page 2M
[    0.000000] kernel direct mapping tables up to bb000000 @ ba99b000-ba99f000
[    0.000000] init_memory_mapping: 0000000100000000-000000023e600000
[    0.000000]  0100000000 - 023e600000 page 2M
[    0.000000] kernel direct mapping tables up to 23e600000 @ 23e5f6000-23e600000
[    0.000000] RAMDISK: 365ae000 - 372cf000
[    0.000000] ACPI: RSDP 00000000000f00e0 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000baffe120 000AC (v01 LENOVO TP-83    00001300 PTEC 00000002)
[    0.000000] ACPI: FACP 00000000bafe9000 000F4 (v04 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000bafec000 0DFA4 (v01 LENOVO TP-83    00001300 INTL 20061109)
[    0.000000] ACPI: FACS 00000000baf2d000 00040
[    0.000000] ACPI: SLIC 00000000baffd000 00176 (v01 LENOVO TP-83    00001300 PTEC 00000001)
[    0.000000] ACPI: SSDT 00000000baffc000 00249 (v01 LENOVO TP-SSDT2 00000200 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000baffb000 00033 (v01 LENOVO TP-SSDT1 00000100 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000baffa000 00797 (v01 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: HPET 00000000bafe8000 00038 (v01 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: APIC 00000000bafe7000 00098 (v01 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000bafe6000 0003C (v01 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: ECDT 00000000bafe5000 00052 (v01 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: ASF! 00000000bafeb000 000A5 (v32 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: TCPA 00000000bafe4000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT 00000000bafe3000 00A69 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafe2000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: DMAR 00000000bafe1000 000E8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 00000000bafe0000 0003E (v01 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafdf000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000bafde000 0027E (v01 LENOVO TP-83    00001300 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000023e600000
[    0.000000] Initmem setup node 0 0000000000000000-000000023e600000
[    0.000000]   NODE_DATA [000000023e5fb000 - 000000023e5fffff]
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880235c00000-ffff88023cbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0023e600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000ba99f
[    0.000000]     0: 0x000bafff -> 0x000bb000
[    0.000000]     0: 0x00100000 -> 0x0023e600
[    0.000000] On node 0 totalpages: 2068269
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 745944 pages, LIFO batch:31
[    0.000000]   Normal zone: 17829 pages used for memmap
[    0.000000]   Normal zone: 1286235 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
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
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000ba99f000 - 00000000bae9f000
[    0.000000] PM: Registered nosave memory: 00000000bae9f000 - 00000000baf9f000
[    0.000000] PM: Registered nosave memory: 00000000baf9f000 - 00000000bafff000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed08000
[    0.000000] PM: Registered nosave memory: 00000000fed08000 - 00000000fed09000
[    0.000000] PM: Registered nosave memory: 00000000fed09000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd20000
[    0.000000] PM: Registered nosave memory: 00000000ffd20000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:38600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88023e200000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2036099
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-12-generic root=/dev/sda5 ro rootflags=subvol=@ quiet splash pcie_aspm=force i915.i915_enable_rc6=1 vt.handoff=7
[    0.000000] PCIe ASPM is forcedly enabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.000000] Memory: 8064440k/9410560k available (6104k kernel code, 1137484k absent, 208636k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2691.509 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5383.01 BogoMIPS (lpj=10766036)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000024] Security Framework initialized
[    0.000035] AppArmor: AppArmor initialized
[    0.000036] Yama: becoming mindful.
[    0.000699] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002254] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002881] Mount-cache hash table entries: 256
[    0.002968] Initializing cgroup subsys cpuacct
[    0.002971] Initializing cgroup subsys memory
[    0.002976] Initializing cgroup subsys devices
[    0.002978] Initializing cgroup subsys freezer
[    0.002979] Initializing cgroup subsys net_cls
[    0.002981] Initializing cgroup subsys blkio
[    0.002985] Initializing cgroup subsys perf_event
[    0.003006] Disabled fast string operations
[    0.003008] CPU: Physical Processor ID: 0
[    0.003009] CPU: Processor Core ID: 0
[    0.003013] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003014] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003016] mce: CPU supports 7 MCE banks
[    0.003026] CPU0: Thermal monitoring enabled (TM1)
[    0.003031] using mwait in idle threads.
[    0.004620] ACPI: Core revision 20110413
[    0.011012] ftrace: allocating 25651 entries in 101 pages
[    0.017964] DMAR: Host address width 36
[    0.017966] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.017971] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.017973] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.017977] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.017978] DMAR: RMRR base: 0x000000bacd5000 end: 0x000000bacebfff
[    0.017979] DMAR: RMRR base: 0x000000bb800000 end: 0x000000bf9fffff
[    0.017981] DMAR: No ATSR found
[    0.018051] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.018052] HPET id 0 under DRHD base 0xfed91000
[    0.018053] HPET id 0 under DRHD base 0xfed91000
[    0.018054] HPET id 0 under DRHD base 0xfed91000
[    0.018055] HPET id 0 under DRHD base 0xfed91000
[    0.018056] HPET id 0 under DRHD base 0xfed91000
[    0.018057] HPET id 0 under DRHD base 0xfed91000
[    0.018058] HPET id 0 under DRHD base 0xfed91000
[    0.018059] HPET id 0 under DRHD base 0xfed91000
[    0.018260] Enabled IRQ remapping in x2apic mode
[    0.018261] Enabling x2apic
[    0.018262] Enabled x2apic
[    0.018267] Switched APIC routing to cluster x2apic.
[    0.018637] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058273] CPU0: Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz stepping 07
[    0.163955] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.163960] ... version:                3
[    0.163961] ... bit width:              48
[    0.163962] ... generic registers:      4
[    0.163963] ... value mask:             0000ffffffffffff
[    0.163964] ... max period:             000000007fffffff
[    0.163965] ... fixed-purpose events:   3
[    0.163966] ... event mask:             000000070000000f
[    0.164295] Booting Node   0, Processors  #1
[    0.164297] smpboot cpu 1: start_ip = 98000
[    0.251846] Disabled fast string operations
[    0.271975]  #2
[    0.271977] smpboot cpu 2: start_ip = 98000
[    0.359702] Disabled fast string operations
[    0.379852]  #3
[    0.379854] smpboot cpu 3: start_ip = 98000
[    0.467558] Disabled fast string operations
[    0.487674] Brought up 4 CPUs
[    0.487676] Total of 4 processors activated (21529.99 BogoMIPS).
[    0.490262] devtmpfs: initialized
[    0.490363] PM: Registering ACPI NVS region at bae9f000 (1048576 bytes)
[    0.491449] print_constraints: dummy: 
[    0.491474] Time: 11:34:40  Date: 09/30/11
[    0.491499] NET: Registered protocol family 16
[    0.491575] Trying to unpack rootfs image as initramfs...
[    0.491586] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.491588] ACPI: bus type pci registered
[    0.491798] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.491801] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.500582] PCI: Using configuration type 1 for base access
[    0.501104] bio: create slab <bio-0> at 0
[    0.502503] ACPI: EC: EC description table is found, configuring boot EC
[    0.506189] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.584085] ACPI: SSDT 00000000bae8c018 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.584428] ACPI: Dynamic OEM Table Load:
[    0.584430] ACPI: SSDT           (null) 008C0 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.607571] ACPI: SSDT 00000000bae8da98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.607937] ACPI: Dynamic OEM Table Load:
[    0.607939] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.639419] ACPI: SSDT 00000000bae8bd98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.639766] ACPI: Dynamic OEM Table Load:
[    0.639767] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.655773] ACPI: Interpreter enabled
[    0.655776] ACPI: (supports S0 S3 S4 S5)
[    0.655792] ACPI: Using IOAPIC for interrupt routing
[    0.687612] ACPI: Power Resource [PUBS] (on)
[    0.688734] Freeing initrd memory: 13444k freed
[    0.689922] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.690653] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.690656] HEST: Table not found.
[    0.690658] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.690750] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.690792] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.690794] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.690795] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.690798] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xfebfffff]
[    0.690799] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed4bfff]
[    0.690811] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    0.690840] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.690862] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.690864] pci 0000:00:01.0: PME# disabled
[    0.690880] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    0.690889] pci 0000:00:02.0: reg 10: [mem 0xf1400000-0xf17fffff 64bit]
[    0.690894] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.690898] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    0.690944] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.690967] pci 0000:00:16.0: reg 10: [mem 0xf2905000-0xf290500f 64bit]
[    0.691027] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.691031] pci 0000:00:16.0: PME# disabled
[    0.691061] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.691081] pci 0000:00:1a.0: reg 10: [mem 0xf290a000-0xf290a3ff]
[    0.691152] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.691156] pci 0000:00:1a.0: PME# disabled
[    0.691178] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.691193] pci 0000:00:1b.0: reg 10: [mem 0xf2900000-0xf2903fff 64bit]
[    0.691246] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.691256] pci 0000:00:1b.0: PME# disabled
[    0.691279] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.691381] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.691386] pci 0000:00:1c.0: PME# disabled
[    0.691421] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.691519] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.691524] pci 0000:00:1c.1: PME# disabled
[    0.691558] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    0.691659] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.691663] pci 0000:00:1c.4: PME# disabled
[    0.691700] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.691720] pci 0000:00:1d.0: reg 10: [mem 0xf2909000-0xf29093ff]
[    0.691791] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.691795] pci 0000:00:1d.0: PME# disabled
[    0.691818] pci 0000:00:1f.0: [8086:1c4f] type 0 class 0x000601
[    0.691929] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    0.691946] pci 0000:00:1f.2: reg 10: [io  0x5088-0x508f]
[    0.691954] pci 0000:00:1f.2: reg 14: [io  0x509c-0x509f]
[    0.691961] pci 0000:00:1f.2: reg 18: [io  0x5080-0x5087]
[    0.691969] pci 0000:00:1f.2: reg 1c: [io  0x5098-0x509b]
[    0.691977] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    0.691985] pci 0000:00:1f.2: reg 24: [mem 0xf2908000-0xf29087ff]
[    0.692016] pci 0000:00:1f.2: PME# supported from D3hot
[    0.692020] pci 0000:00:1f.2: PME# disabled
[    0.692036] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.692050] pci 0000:00:1f.3: reg 10: [mem 0xf2904000-0xf29040ff 64bit]
[    0.692071] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    0.692127] pci 0000:01:00.0: [10de:1057] type 0 class 0x000300
[    0.692140] pci 0000:01:00.0: reg 10: [mem 0xf0000000-0xf0ffffff]
[    0.692155] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.692169] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.692179] pci 0000:01:00.0: reg 24: [io  0x4000-0x407f]
[    0.692189] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    0.699267] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.699274] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.699281] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.699291] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.699395] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.699401] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.699406] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.699415] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.699638] pci 0000:03:00.0: [8086:0084] type 0 class 0x000280
[    0.699786] pci 0000:03:00.0: reg 10: [mem 0xf2800000-0xf2801fff 64bit]
[    0.700346] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.700381] pci 0000:03:00.0: PME# disabled
[    0.707380] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.707385] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.707390] pci 0000:00:1c.1:   bridge window [mem 0xf2800000-0xf28fffff]
[    0.707399] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.707501] pci 0000:0d:00.0: [1180:e823] type 0 class 0x000805
[    0.707529] pci 0000:0d:00.0: reg 10: [mem 0xf2000000-0xf20000ff]
[    0.707691] pci 0000:0d:00.0: supports D1 D2
[    0.707693] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.707698] pci 0000:0d:00.0: PME# disabled
[    0.715254] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.715264] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.715274] pci 0000:00:1c.4:   bridge window [mem 0xf2000000-0xf27fffff]
[    0.715289] pci 0000:00:1c.4:   bridge window [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.715337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.715411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[    0.715431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.715449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.715468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.715563]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.715680]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.715681] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.717035] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.717083] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11)
[    0.717126] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.717167] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.717209] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11)
[    0.717244] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.717286] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11)
[    0.717326] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11)
[    0.717398] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.717404] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.717406] vgaarb: loaded
[    0.717406] vgaarb: bridge control possible 0000:01:00.0
[    0.717407] vgaarb: bridge control possible 0000:00:02.0
[    0.717524] SCSI subsystem initialized
[    0.717566] libata version 3.00 loaded.
[    0.717594] usbcore: registered new interface driver usbfs
[    0.717600] usbcore: registered new interface driver hub
[    0.717619] usbcore: registered new device driver usb
[    0.717669] PCI: Using ACPI for IRQ routing
[    0.719116] PCI: pci_cache_line_size set to 64 bytes
[    0.719242] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.719244] reserve RAM buffer: 00000000ba99f000 - 00000000bbffffff 
[    0.719246] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
[    0.719247] reserve RAM buffer: 000000023e600000 - 000000023fffffff 
[    0.719308] NetLabel: Initializing
[    0.719309] NetLabel:  domain hash size = 128
[    0.719310] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.719319] NetLabel:  unlabeled traffic allowed by default
[    0.719349] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.719354] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.721364] Switching to clocksource hpet
[    0.723217] Switched to NOHz mode on CPU #0
[    0.723323] Switched to NOHz mode on CPU #1
[    0.723346] Switched to NOHz mode on CPU #2
[    0.723366] Switched to NOHz mode on CPU #3
[    0.724992] AppArmor: AppArmor Filesystem Enabled
[    0.725011] pnp: PnP ACPI init
[    0.725020] ACPI: bus type pnp registered
[    0.725294] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.725296] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    0.725297] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    0.725298] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    0.725299] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.725301] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    0.725302] pnp 00:00: [mem 0x000d4000-0x000d7fff]
[    0.725303] pnp 00:00: [mem 0x000d8000-0x000dbfff]
[    0.725304] pnp 00:00: [mem 0x000dc000-0x000dffff]
[    0.725305] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    0.725307] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    0.725308] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    0.725309] pnp 00:00: [mem 0x000ec000-0x000effff]
[    0.725310] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.725312] pnp 00:00: [mem 0x00100000-0xbf9fffff]
[    0.725313] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    0.725314] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    0.725364] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.725366] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.725368] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.725369] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.725371] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.725373] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.725376] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    0.725377] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    0.725379] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    0.725381] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.725382] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.725384] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.725386] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.725387] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.725389] system 00:00: [mem 0x00100000-0xbf9fffff] could not be reserved
[    0.725391] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.725393] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.725396] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.725411] pnp 00:01: [bus 00-fe]
[    0.725412] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.725414] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.725415] pnp 00:01: [io  0x0d00-0xffff window]
[    0.725416] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.725418] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    0.725419] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    0.725421] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    0.725422] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    0.725423] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    0.725425] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    0.725426] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    0.725427] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    0.725429] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    0.725430] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    0.725431] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    0.725433] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    0.725434] pnp 00:01: [mem 0xbfa00000-0xfebfffff window]
[    0.725436] pnp 00:01: [mem 0xfed40000-0xfed4bfff window]
[    0.725474] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.725521] pnp 00:02: [io  0x0010-0x001f]
[    0.725523] pnp 00:02: [io  0x0090-0x009f]
[    0.725524] pnp 00:02: [io  0x0024-0x0025]
[    0.725525] pnp 00:02: [io  0x0028-0x0029]
[    0.725526] pnp 00:02: [io  0x002c-0x002d]
[    0.725527] pnp 00:02: [io  0x0030-0x0031]
[    0.725528] pnp 00:02: [io  0x0034-0x0035]
[    0.725529] pnp 00:02: [io  0x0038-0x0039]
[    0.725530] pnp 00:02: [io  0x003c-0x003d]
[    0.725532] pnp 00:02: [io  0x00a4-0x00a5]
[    0.725533] pnp 00:02: [io  0x00a8-0x00a9]
[    0.725534] pnp 00:02: [io  0x00ac-0x00ad]
[    0.725535] pnp 00:02: [io  0x00b0-0x00b5]
[    0.725536] pnp 00:02: [io  0x00b8-0x00b9]
[    0.725537] pnp 00:02: [io  0x00bc-0x00bd]
[    0.725538] pnp 00:02: [io  0x0050-0x0053]
[    0.725539] pnp 00:02: [io  0x0072-0x0077]
[    0.725541] pnp 00:02: [io  0x0400-0x047f]
[    0.725542] pnp 00:02: [io  0x0500-0x057f]
[    0.725543] pnp 00:02: [io  0x0800-0x080f]
[    0.725544] pnp 00:02: [io  0x15e0-0x15ef]
[    0.725545] pnp 00:02: [io  0x1600-0x167f]
[    0.725547] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    0.725548] pnp 00:02: [mem 0x00000000-0x00000fff]
[    0.725549] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    0.725550] pnp 00:02: [mem 0xfed10000-0xfed13fff]
[    0.725552] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.725553] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.725554] pnp 00:02: [mem 0xfed45000-0xfed4bfff]
[    0.725592] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.725593] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.725595] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.725597] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.725598] system 00:02: [io  0x1600-0x167f] has been reserved
[    0.725600] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.725602] system 00:02: [mem 0x00000000-0x00000fff] could not be reserved
[    0.725604] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.725605] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.725607] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.725609] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.725610] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.725613] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.725644] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.725660] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.725667] pnp 00:04: [io  0x0000-0x000f]
[    0.725668] pnp 00:04: [io  0x0080-0x008f]
[    0.725669] pnp 00:04: [io  0x00c0-0x00df]
[    0.725670] pnp 00:04: [dma 4]
[    0.725685] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.725691] pnp 00:05: [io  0x0061]
[    0.725707] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.725713] pnp 00:06: [io  0x00f0]
[    0.725723] pnp 00:06: [irq 13]
[    0.725739] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.725745] pnp 00:07: [io  0x0070-0x0071]
[    0.725750] pnp 00:07: [irq 8]
[    0.725765] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.725771] pnp 00:08: [io  0x0060]
[    0.725772] pnp 00:08: [io  0x0064]
[    0.725777] pnp 00:08: [irq 1]
[    0.725794] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.725806] pnp 00:09: [irq 12]
[    0.725822] pnp 00:09: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.725846] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.725865] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.726251] pnp: PnP ACPI: found 11 devices
[    0.726252] ACPI: ACPI bus type pnp unregistered
[    0.731558] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.731562] PCI: max bus depth: 1 pci_try_num: 2
[    0.731603] pci 0000:01:00.0: BAR 6: assigned [mem 0xf1000000-0xf107ffff pref]
[    0.731605] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.731607] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.731610] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.731612] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.731615] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.731616] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.731623] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.731628] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.731636] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.731637] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.731644] pci 0000:00:1c.1:   bridge window [mem 0xf2800000-0xf28fffff]
[    0.731648] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.731657] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.731660] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.731667] pci 0000:00:1c.4:   bridge window [mem 0xf2000000-0xf27fffff]
[    0.731672] pci 0000:00:1c.4:   bridge window [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.731689] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.731692] pci 0000:00:01.0: setting latency timer to 64
[    0.731699] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.731706] pci 0000:00:1c.0: setting latency timer to 64
[    0.731716] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.731721] pci 0000:00:1c.1: setting latency timer to 64
[    0.731728] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.731732] pci 0000:00:1c.4: setting latency timer to 64
[    0.731736] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.731738] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.731739] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.731741] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfebfffff]
[    0.731742] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff]
[    0.731744] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.731745] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf10fffff]
[    0.731747] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.731748] pci_bus 0000:03: resource 1 [mem 0xf2800000-0xf28fffff]
[    0.731750] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff]
[    0.731751] pci_bus 0000:0d: resource 1 [mem 0xf2000000-0xf27fffff]
[    0.731753] pci_bus 0000:0d: resource 2 [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.731773] NET: Registered protocol family 2
[    0.731964] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.733538] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.734658] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.734779] TCP: Hash tables configured (established 524288 bind 65536)
[    0.734780] TCP reno registered
[    0.734793] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.734823] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.734909] NET: Registered protocol family 1
[    0.734921] pci 0000:00:02.0: Boot video device
[    0.735043] PCI: CLS 64 bytes, default 64
[    0.735047] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.735049] Placing 64MB software IO TLB between ffff8800b699b000 - ffff8800ba99b000
[    0.735050] software IO TLB at phys 0xb699b000 - 0xba99b000
[    0.735372] audit: initializing netlink socket (disabled)
[    0.735378] type=2000 audit(1317382480.576:1): initialized
[    0.759612] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.775607] VFS: Disk quotas dquot_6.5.2
[    0.775645] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.776036] fuse init (API version 7.16)
[    0.776092] msgmni has been set to 15777
[    0.776367] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.776391] io scheduler noop registered
[    0.776392] io scheduler deadline registered
[    0.776418] io scheduler cfq registered (default)
[    0.776480] pcieport 0000:00:01.0: setting latency timer to 64
[    0.776505] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    0.776743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.776759] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.776783] intel_idle: MWAIT substates: 0x21120
[    0.776784] intel_idle: v0.4 model 0x2A
[    0.776785] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.777136] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.777396] ACPI: AC Adapter [AC] (on-line)
[    0.777467] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.777784] ACPI: Lid Switch [LID]
[    0.777826] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.777829] ACPI: Sleep Button [SLPB]
[    0.777905] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.777907] ACPI: Power Button [PWRF]
[    0.777945] ACPI: acpi_idle yielding to intel_idle
[    0.780128] thermal LNXTHERM:00: registered as thermal_zone0
[    0.780130] ACPI: Thermal Zone [THM0] (66 C)
[    0.780142] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.780154] ERST: Table is not found!
[    0.780203] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.794817] ACPI: Battery Slot [BAT0] (battery present)
[    1.005243] Linux agpgart interface v0.103
[    1.005297] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.005385] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.006488] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.006580] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.007196] brd: module loaded
[    1.007475] loop: module loaded
[    1.007735] Fixed MDIO Bus: probed
[    1.007748] PPP generic driver version 2.4.2
[    1.007769] tun: Universal TUN/TAP device driver, 1.6
[    1.007770] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.007812] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.007825] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.007828] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.007836] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.007851] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.007854] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.007876] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.007900] ehci_hcd 0000:00:1a.0: debug port 2
[    1.011788] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.011803] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf290a000
[    1.024970] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.025118] hub 1-0:1.0: USB hub found
[    1.025121] hub 1-0:1.0: 3 ports detected
[    1.025162] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.025166] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.025178] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.025188] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.025191] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.025215] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.025235] ehci_hcd 0000:00:1d.0: debug port 2
[    1.029101] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.029110] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf2909000
[    1.044946] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.045080] hub 2-0:1.0: USB hub found
[    1.045084] hub 2-0:1.0: 3 ports detected
[    1.045120] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.045127] uhci_hcd: USB Universal Host Controller Interface driver
[    1.045163] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.048333] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.048338] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.048421] mousedev: PS/2 mouse device common for all mice
[    1.048503] rtc_cmos 00:07: RTC can wake from S4
[    1.048582] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.048607] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.048669] device-mapper: uevent: version 1.0.3
[    1.048712] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.048786] cpuidle: using governor ladder
[    1.048908] cpuidle: using governor menu
[    1.048910] EFI Variables Facility v0.08 2004-May-17
[    1.049069] TCP cubic registered
[    1.049157] NET: Registered protocol family 10
[    1.049435] NET: Registered protocol family 17
[    1.049444] Registering the dns_resolver key type
[    1.049497] PM: Hibernation image not present or could not be loaded.
[    1.049504] registered taskstats version 1
[    1.058991] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.061889]   Magic number: 11:468:581
[    1.061912] pci_bus 0000:02: hash matches
[    1.061964] rtc_cmos 00:07: setting system clock to 2011-09-30 11:34:41 UTC (1317382481)
[    1.067189] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.067196] EDD information not available.
[    1.068814] Freeing unused kernel memory: 984k freed
[    1.068924] Write protecting the kernel read-only data: 10240k
[    1.069159] Freeing unused kernel memory: 20k freed
[    1.071880] Freeing unused kernel memory: 1400k freed
[    1.081697] udevd[86]: starting version 173
[    1.100610] Btrfs loaded
[    1.105173] ahci 0000:00:1f.2: version 3.0
[    1.105200] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.105249] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.105303] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    1.105306] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.105311] ahci 0000:00:1f.2: setting latency timer to 64
[    1.110663] sdhci: Secure Digital Host Controller Interface driver
[    1.110665] sdhci: Copyright(c) Pierre Ossman
[    1.110872] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e823] (rev 5)
[    1.110896] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.110936] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    1.110948] mmc0: no vmmc regulator found
[    1.110979] Registered led device: mmc0::
[    1.111145] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    1.113878] scsi0 : ahci
[    1.114656] scsi1 : ahci
[    1.114993] scsi2 : ahci
[    1.116287] scsi3 : ahci
[    1.116934] scsi4 : ahci
[    1.117118] scsi5 : ahci
[    1.117867] ata1: SATA max UDMA/133 abar m2048@0xf2908000 port 0xf2908100 irq 43
[    1.117872] ata2: SATA max UDMA/133 abar m2048@0xf2908000 port 0xf2908180 irq 43
[    1.117873] ata3: DUMMY
[    1.117875] ata4: DUMMY
[    1.117876] ata5: DUMMY
[    1.117877] ata6: DUMMY
[    1.336668] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.436540] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.436587] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.438649] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.438652] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.438654] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.438918] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.439180] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.439191] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.440287] ata1.00: ATA-8: ST9500420AS, 0003LVM1, max UDMA/100
[    1.440296] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.440752] ata2.00: ATAPI: HL-DT-STDVDRAM GT33N, LT20, max UDMA/66
[    1.443081] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.443083] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.443085] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.443257] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.443442] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.443449] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.444711] ata1.00: configured for UDMA/100
[    1.444947] ata2.00: configured for UDMA/66
[    1.444950] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0003 PQ: 0 ANSI: 5
[    1.445075] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.445087] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.445109] sd 0:0:0:0: [sda] Write Protect is off
[    1.445110] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.445121] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.453923] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT33N     LT20 PQ: 0 ANSI: 5
[    1.456909] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.456918] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.457046] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.457073] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.469321] hub 1-1:1.0: USB hub found
[    1.469393] hub 1-1:1.0: 6 ports detected
[    1.531205]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    1.531536] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.580360] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.712709] hub 2-1:1.0: USB hub found
[    1.712817] hub 2-1:1.0: 8 ports detected
[    1.732063] Refined TSC clocksource calibration: 2691.258 MHz.
[    1.732072] Switching to clocksource tsc
[    1.788120] usb 1-1.3: new full speed USB device number 3 using ehci_hcd
[    1.959910] usb 1-1.6: new high speed USB device number 4 using ehci_hcd
[    2.127686] usb 2-1.1: new high speed USB device number 3 using ehci_hcd
[    2.220080] hub 2-1.1:1.0: USB hub found
[    2.220158] hub 2-1.1:1.0: 2 ports detected
[    2.455342] device fsid fcef771c-65c9-4a82-a87e-6a0da4ed0ef2 devid 1 transid 709 /dev/sda8
[    2.491390] usb 2-1.1.1: new high speed USB device number 4 using ehci_hcd
[    2.494085] device fsid aed03164-f0da-4880-a7ec-40d6c387acbc devid 1 transid 9684 /dev/sda5
[    2.622956] device fsid aed03164-f0da-4880-a7ec-40d6c387acbc devid 1 transid 9684 /dev/sda5
[    2.675171] usb 2-1.1.2: new high speed USB device number 5 using ehci_hcd
[    2.767489] hub 2-1.1.2:1.0: USB hub found
[    2.767574] hub 2-1.1.2:1.0: 4 ports detected
[    4.942202] udevd[366]: starting version 173
[    5.130633] Adding 19998716k swap on /dev/sda7.  Priority:-1 extents:1 across:19998716k 
[    6.929513] type=1400 audit(1317404087.372:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=532 comm="apparmor_parser"
[    6.929760] type=1400 audit(1317404087.372:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=532 comm="apparmor_parser"
[    6.929919] type=1400 audit(1317404087.372:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=532 comm="apparmor_parser"
[    7.549215] wmi: Mapper loaded
[    7.673210] Linux video capture interface: v2.00
[    7.726859] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    7.727058] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.727065] mei 0000:00:16.0: setting latency timer to 64
[    7.747100] cfg80211: Calling CRDA to update world regulatory domain
[    7.817346] Non-volatile memory driver v1.3
[    7.852675] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b221)
[    7.854131] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input4
[    7.854189] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
[    7.854597] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    7.855251] input: Monitor Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/input/input5
[    7.855299] usbcore: registered new interface driver uvcvideo
[    7.855301] USB Video Class driver (v1.1.0)
[    7.879366] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
[    7.904809] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[    7.904822] serio: Synaptics pass-through port at isa0060/serio1/input0
[    7.958204] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    8.004364] lp: driver loaded but no devices found
[    8.426697] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    8.426700] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    8.426805] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.426814] iwlagn 0000:03:00.0: setting latency timer to 64
[    8.426840] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    8.448006] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    8.448008] iwlagn 0000:03:00.0: Device SKU: 0X9
[    8.448009] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    8.448016] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    8.448101] iwlagn 0000:03:00.0: irq 44 for MSI/MSI-X
[    8.915389] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[    8.915495] Registered led device: phy0-led
[    8.915519] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.925106] coretemp coretemp.0: TjMax is 100 C.
[    8.925120] coretemp coretemp.0: TjMax is 100 C.
[    9.116928] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.228529] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[    9.228531] thinkpad_acpi: http://ibm-acpi.sf.net/
[    9.228533] thinkpad_acpi: ThinkPad BIOS 83ET60WW (1.30 ), EC unknown
[    9.228534] thinkpad_acpi: Lenovo ThinkPad T420, model 4177CTO
[    9.228864] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[    9.229071] thinkpad_acpi: radio switch found; radios are enabled
[    9.230183] Registered led device: tpacpi::thinklight
[    9.230199] Registered led device: tpacpi::power
[    9.230207] Registered led device: tpacpi::standby
[    9.230217] Registered led device: tpacpi::thinkvantage
[    9.230270] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[    9.230332] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[    9.231236] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[    9.326777] [drm] Initialized drm 1.1.0 20060810
[    9.392061] usbcore: registered new interface driver snd-usb-audio
[    9.595761] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.595815] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    9.595837] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.865366] nouveau 0000:01:00.0: power state changed by ACPI to D0
[    9.865371] nouveau 0000:01:00.0: power state changed by ACPI to D0
[    9.865375] nouveau 0000:01:00.0: enabling device (0000 -> 0003)
[    9.865380] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.865386] nouveau 0000:01:00.0: setting latency timer to 64
[    9.866603] [drm] nouveau 0000:01:00.0: Unsupported chipset 0x0d9170a1
[    9.867173] nouveau 0000:01:00.0: PCI INT A disabled
[    9.867177] nouveau: probe of 0000:01:00.0 failed with error -22
[    9.933412] i915 0000:00:02.0: power state changed by ACPI to D0
[    9.933417] i915 0000:00:02.0: power state changed by ACPI to D0
[    9.933423] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.933426] i915 0000:00:02.0: setting latency timer to 64
[    9.940028] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    9.940031] cfg80211: World regulatory domain updated:
[    9.940032] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.940034] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.940035] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.940036] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.940038] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.940039] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.968990] mtrr: no more MTRRs available
[    9.968993] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    9.969268] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    9.969272] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.969274] [drm] Driver supports precise vblank timestamp query.
[    9.969377] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[    9.969394] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.969395] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   10.185525] fbcon: inteldrmfb (fb0) is primary device
[   10.186010] Console: switching to colour frame buffer device 170x48
[   10.186025] fb0: inteldrmfb frame buffer device
[   10.186027] drm: registered panic notifier
[   10.206168] acpi device:01: registered as cooling_device4
[   10.206290] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   10.206330] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   10.207906] acpi device:0b: registered as cooling_device5
[   10.208396] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input9
[   10.208486] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[   10.208598] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.010587] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   15.291890] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input10
[   32.928566] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   33.050965] device fsid fcef771c-65c9-4a82-a87e-6a0da4ed0ef2 devid 1 transid 709 /dev/sda8
[   34.391050] ppdev: user-space parallel port driver
[   34.545017] type=1400 audit(1317404115.020:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1040 comm="apparmor_parser"
[   34.545317] type=1400 audit(1317404115.020:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1040 comm="apparmor_parser"
[   35.545358] type=1400 audit(1317404116.024:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1065 comm="apparmor_parser"
[   35.545604] type=1400 audit(1317404116.024:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1065 comm="apparmor_parser"
[   35.545759] type=1400 audit(1317404116.024:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1065 comm="apparmor_parser"
[   35.546364] type=1400 audit(1317404116.024:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1069 comm="apparmor_parser"
[   35.546729] type=1400 audit(1317404116.024:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1069 comm="apparmor_parser"
[   35.577262] type=1400 audit(1317404116.056:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1070 comm="apparmor_parser"
[   35.605093] type=1400 audit(1317404116.084:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1068 comm="apparmor_parser"
[   35.605339] type=1400 audit(1317404116.084:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1068 comm="apparmor_parser"
[   36.013027] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.407566] wlan0: authenticate with 00:21:91:fe:1d:eb (try 1)
[   38.411989] wlan0: authenticated
[   38.418101] wlan0: associate with 00:21:91:fe:1d:eb (try 1)
[   38.423026] wlan0: RX AssocResp from 00:21:91:fe:1d:eb (capab=0x431 status=0 aid=4)
[   38.423035] wlan0: associated
[   38.427085] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.713653] Bluetooth: Core ver 2.16
[   38.713668] NET: Registered protocol family 31
[   38.713669] Bluetooth: HCI device and connection manager initialized
[   38.713670] Bluetooth: HCI socket layer initialized
[   38.713671] Bluetooth: L2CAP socket layer initialized
[   38.713701] Bluetooth: SCO socket layer initialized
[   38.716032] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.716034] Bluetooth: BNEP filters: protocol multicast
[   38.737546] Bluetooth: RFCOMM TTY layer initialized
[   38.737550] Bluetooth: RFCOMM socket layer initialized
[   38.737551] Bluetooth: RFCOMM ver 1.11
[   42.522508] EXT4-fs (sda6): re-mounted. Opts: commit=15
[   43.223116] init: plymouth-stop pre-start process (1630) terminated with status 1
[   46.614595] EXT4-fs (sda6): re-mounted. Opts: commit=15
[   49.849861] wlan0: no IPv6 routers present
[ 1173.931200] [drm:pch_irq_handler] *ERROR* PCH poison interrupt
[ 1211.131481] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 1211.131486] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 1217.024585] [drm:pch_irq_handler] *ERROR* PCH poison interrupt
[ 1220.544225] thinkpad_acpi: unknown possible thermal alarm or keyboard event received
[ 1220.544234] thinkpad_acpi: unhandled HKEY event 0x6040
[ 1220.544239] thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel@lists.sourceforge.net
[ 1220.544969] thinkpad_acpi: EC reports that Thermal Table has changed
[ 1222.692956] EXT4-fs (sda6): re-mounted. Opts: commit=60
[ 1246.687953] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 1246.688048] ehci_hcd 0000:00:1d.0: PME# enabled
[ 1246.702184] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D3
[ 1248.497658] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1248.497753] ehci_hcd 0000:00:1a.0: PME# enabled
[ 1248.511755] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
[ 1254.778123] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1254.791702] ehci_hcd 0000:00:1a.0: BAR 0: set to [mem 0xf290a000-0xf290a3ff] (PCI address [0xf290a000-0xf290a3ff])
[ 1254.791728] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1254.791760] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1254.791801] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1254.791855] ehci_hcd 0000:00:1a.0: PME# disabled
[ 1254.791867] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1254.791875] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1254.791893] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1254.791906] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1254.791952] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1254.792021] ehci_hcd 0000:00:1a.0: PME# enabled
[ 1254.792069] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1254.807695] ehci_hcd 0000:00:1d.0: BAR 0: set to [mem 0xf2909000-0xf29093ff] (PCI address [0xf2909000-0xf29093ff])
[ 1254.807721] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1254.807753] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 1254.807795] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1254.807849] ehci_hcd 0000:00:1d.0: PME# disabled
[ 1254.807861] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1254.807870] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1254.807888] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1254.807902] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1254.807946] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
[ 1254.955620] usb 2-1.1: USB disconnect, device number 3
[ 1254.955629] usb 2-1.1.1: USB disconnect, device number 4
[ 1255.088065] usb 2-1.1.2: USB disconnect, device number 5
[ 1259.237949] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 1259.238041] ehci_hcd 0000:00:1d.0: PME# enabled
[ 1259.253959] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D3
[ 1264.382801] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.395273] ehci_hcd 0000:00:1a.0: BAR 0: set to [mem 0xf290a000-0xf290a3ff] (PCI address [0xf290a000-0xf290a3ff])
[ 1264.395298] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.395332] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1264.395373] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1264.395426] ehci_hcd 0000:00:1a.0: PME# disabled
[ 1264.395438] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.395446] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.395464] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1264.395477] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1264.395524] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1264.395593] ehci_hcd 0000:00:1a.0: PME# enabled
[ 1264.395640] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1264.411298] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
[ 1264.411340] ehci_hcd 0000:00:1d.0: BAR 0: set to [mem 0xf2909000-0xf29093ff] (PCI address [0xf2909000-0xf29093ff])
[ 1264.411353] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1264.411384] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 1264.411425] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1264.411476] ehci_hcd 0000:00:1d.0: PME# disabled
[ 1264.411488] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1264.411496] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[ 1264.411514] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1264.411527] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1264.631170] usb 2-1.1: new low speed USB device number 6 using ehci_hcd
[ 1264.733440] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.746829] ehci_hcd 0000:00:1a.0: BAR 0: set to [mem 0xf290a000-0xf290a3ff] (PCI address [0xf290a000-0xf290a3ff])
[ 1264.746856] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.746887] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1264.746927] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1264.746986] ehci_hcd 0000:00:1a.0: PME# disabled
[ 1264.746999] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.747009] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[ 1264.747027] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1264.747040] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1265.089752] usbcore: registered new interface driver usbhid
[ 1265.089759] usbhid: USB HID core driver
[ 1265.125054] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input11
[ 1265.125389] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input0
[ 1265.130326] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[ 1265.132097] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input12
[ 1265.132606] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input1
[ 1271.258325] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1271.258420] ehci_hcd 0000:00:1a.0: PME# enabled
[ 1271.274302] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D3
```

---

### Post by donniezazen on 2011-10-02
It worked once when i pressed the hardware switch but notification bubble is empty and i can't see any message. I have xf86-input-synaptic installed.

---

### Post by tista on 2011-10-03
> **donniezazen said:**
> It worked once when i pressed the hardware switch but notification bubble is empty and i can't see any message. I have xf86-input-synaptic installed.

Hi donniezazen,

So did you already try "gpointing-device-settings" ? it might be more useful than mouse config in "system settings"... ;)

cheers.

---

