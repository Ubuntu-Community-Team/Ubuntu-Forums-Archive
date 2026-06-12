---
title: "Errors/Problems/Compatibility? Ubuntu Server 14.04.3 LTS"
date: 2016-02-15
forum: New to Ubuntu
---

### Post by kazz2 on 2016-02-15
EVGA 790i Ultra SLI motherboard
EVGA GeForce 8800GTX GPU

I'm trying to track down any drivers/compatibility issues I may have with this build. It's my first foray into Linux, let alone Ubuntu.  I've had it up and running with little-to-no load for testing but have encountered a couple of occasions when the system was unavailable remotely and a couple of times some kind of log/dump was on the server's display.  So I'm looking for a couple of pieces of help.

First, I just found an nVidia driver for the GPU. I didn't realize it might not be included with the installation. It's installing as I type this. I found a reference from nVidia that the nForce drivers for the motherboard *should* install with the current installation. So are there other drivers I should be looking for and how do I confirm versions of drivers for motherboard and GPU services?

Secondly, how do I check for recent errors, downtimes, reboots, etc.? There must be some logs, etc. I need to be going over.

Thanks!

---

### Post by sandyd on 2016-02-15
Hi, and welcome to Ubuntu.

For server installations, I generally do not recommend installing the proprietary graphics drivers. The default console that you see (tty) only works with the correct resolution when running with KMS that only the open source video drivers built into the kernel. The proprietary drivers do not support KMS, and as such cause the console to have an improper resolution which makes it only useful with a GUI.

To debug the issues, there are some logs in /var/log.

Check the following files, and post them here if you need help checking for errors:
/var/log/dmesg (same as running `dmesg` in terminal).
/var/log/syslog

If you have older entries, they may be in the format of *logfilename*.0 or *logfilename*.1.gz or similar. For the ones with extensions ending in .gz, you can extract them by using ```
gunzip -d *filename*
```

---

### Post by kazz2 on 2016-02-15
Thank you for the prompt reply.

As is apparently the norm these days, I went searching in Google. Read a thread talking about how systems could be finicky with certain GPUs and directed me to the driver I've installed. It's often unclear to me whether anyone's talking about server or desktop though what you've said makes sense.  I'll live with the new GPU drivers and go after the logs for now. The output of a dmesg on my console appears as follows:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-49-generic (buildd@lgw01-08) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 (Ubuntu 3.19.0-49.55~14.04.1-generic 3.19.8-ckt12)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009b7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009b800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfeeffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfef2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfef3000-0x00000000bfefffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI:  EVGA  132-CK-NF79/132-CK-NF79, BIOS   P10  12/30/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 8191M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 2M  num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbfef0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f3fd0-0x000f3fdf] mapped at [ffff8800000f3fd0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
[    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23fdfffff]
[    0.000000]  [mem 0x220000000-0x23fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfeeffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbfdfffff] page 2M
[    0.000000]  [mem 0xbfe00000-0xbfeeffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21fffffff]
[    0.000000]  [mem 0x100000000-0x21fffffff] page 2M
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x34dd2000-0x366e0fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7FA0 000014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 0x00000000BFEF3040 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 0x00000000BFEF30C0 000074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT 0x00000000BFEF3180 005447 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x00000000BFEF0000 000040
[    0.000000] ACPI: HPET 0x00000000BFEF8740 000038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: WDRT 0x00000000BFEF87C0 000047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: MCFG 0x00000000BFEF8880 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 0x00000000BFEF8640 000098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: OEMN 0x00000000BFEF8900 004AED (v01 NVIDIA NTUNEOEM 20302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23fff6000-0x23fffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xbfeeffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x23fffffff]
[    0.000000] On node 0 totalpages: 2096778
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3994 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12220 pages used for memmap
[    0.000000]   DMA32 zone: 782064 pages, LIFO batch:31
[    0.000000]   Normal zone: 20480 pages used for memmap
[    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef0000-0xbfef2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef3000-0xbfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xbff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88023fc00000 s86144 r8192 d32640 u524288
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2063993
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8147228K/8387112K available (7923K kernel code, 1174K rwdata, 3760K rodata, 1408K init, 1292K bss, 239884K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000]  Offload RCU callbacks from all CPUs
[    0.000000]  Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2999.708 MHz processor
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.41 BogoMIPS (lpj=11998832)
[    0.004254] pid_max: default: 32768 minimum: 301
[    0.004376] ACPI: Core revision 20141107
[    0.010801] ACPI: All ACPI Tables successfully acquired
[    0.011032] Security Framework initialized
[    0.011164] AppArmor: AppArmor initialized
[    0.011277] Yama: becoming mindful.
[    0.011906] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.015308] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.016960] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.017100] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.017583] Initializing cgroup subsys memory
[    0.017704] Initializing cgroup subsys devices
[    0.017822] Initializing cgroup subsys freezer
[    0.017939] Initializing cgroup subsys net_cls
[    0.018056] Initializing cgroup subsys blkio
[    0.018171] Initializing cgroup subsys perf_event
[    0.018290] Initializing cgroup subsys net_prio
[    0.018407] Initializing cgroup subsys hugetlb
[    0.018544] CPU: Physical Processor ID: 0
[    0.018657] CPU: Processor Core ID: 0
[    0.018768] mce: CPU supports 6 MCE banks
[    0.018885] CPU0: Thermal monitoring enabled (TM1)
[    0.019005] process: using mwait in idle threads
[    0.019125] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.019125] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.019410] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.023102] ftrace: allocating 30034 entries in 118 pages
[    0.032537] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075716] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.080000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.080000] ... version:                2
[    0.080000] ... bit width:              40
[    0.080000] ... generic registers:      2
[    0.080000] ... value mask:             000000ffffffffff
[    0.080000] ... max period:             000000007fffffff
[    0.080000] ... fixed-purpose events:   3
[    0.080000] ... event mask:             0000000700000003
[    0.080000] x86: Booting SMP configuration:
[    0.080000] .... node  #0, CPUs:      #1
[    0.091570] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.091941]  #2 #3
[    0.118233] x86: Booted up 1 node, 4 CPUs
[    0.118438] smpboot: Total of 4 processors activated (23997.66 BogoMIPS)
[    0.120123] devtmpfs: initialized
[    0.126975] evm: security.selinux
[    0.127085] evm: security.SMACK64
[    0.127193] evm: security.SMACK64EXEC
[    0.127303] evm: security.SMACK64TRANSMUTE
[    0.127416] evm: security.SMACK64MMAP
[    0.127536] evm: security.ima
[    0.127642] evm: security.capability
[    0.127767] PM: Registering ACPI NVS region [mem 0xbfef0000-0xbfef2fff] (12288 bytes)
[    0.128118] pinctrl core: initialized pinctrl subsystem
[    0.128272] RTC time: 21:25:14, date: 02/15/16
[    0.128486] NET: Registered protocol family 16
[    0.132007] cpuidle: using governor ladder
[    0.136007] cpuidle: using governor menu
[    0.136175] ACPI: bus type PCI registered
[    0.136288] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.136481] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.136670] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.137141] PCI: Using configuration type 1 for base access
[    0.144125] ACPI: Added _OSI(Module Device)
[    0.145940] ACPI: Added _OSI(Processor Device)
[    0.146055] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.146172] ACPI: Added _OSI(Processor Aggregator Device)
[    0.150617] ACPI: Interpreter enabled
[    0.150732] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.151012] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.151299] ACPI: (supports S0 S3 S4 S5)
[    0.151420] ACPI: Using IOAPIC for interrupt routing
[    0.151628] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.151767] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.156806] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.156935] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.157204] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug]
[    0.157418] acpi PNP0A08:00: _OSC: OS now controls [PME AER PCIeCapability]
[    0.157793] PCI host bridge to bus 0000:00
[    0.157908] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.158030] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.158157] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.158283] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.158413] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.158543] pci_bus 0000:00: root bus resource [mem 0xbff00000-0xfebfffff]
[    0.158681] pci 0000:00:00.0: [10de:0800] type 00 class 0x060000
[    0.158796] pci 0000:00:00.1: [10de:0808] type 00 class 0x050000
[    0.158907] pci 0000:00:00.2: [10de:0809] type 00 class 0x050000
[    0.159014] pci 0000:00:00.3: [10de:080a] type 00 class 0x050000
[    0.159134] pci 0000:00:00.4: [10de:080b] type 00 class 0x050000
[    0.159252] pci 0000:00:00.5: [10de:080c] type 00 class 0x050000
[    0.159361] pci 0000:00:00.6: [10de:080d] type 00 class 0x050000
[    0.159468] pci 0000:00:00.7: [10de:080e] type 00 class 0x050000
[    0.159576] pci 0000:00:01.0: [10de:080f] type 00 class 0x050000
[    0.159674] pci 0000:00:01.1: [10de:0810] type 00 class 0x050000
[    0.159773] pci 0000:00:01.2: [10de:0811] type 00 class 0x050000
[    0.159871] pci 0000:00:01.3: [10de:0812] type 00 class 0x050000
[    0.159969] pci 0000:00:01.4: [10de:0813] type 00 class 0x050000
[    0.160074] pci 0000:00:01.5: [10de:0814] type 00 class 0x050000
[    0.160172] pci 0000:00:01.6: [10de:081a] type 00 class 0x050000
[    0.160292] pci 0000:00:01.7: [10de:080e] type 00 class 0x050000
[    0.160411] pci 0000:00:02.0: [10de:0815] type 01 class 0x060400
[    0.160493] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160545] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.160727] pci 0000:00:04.0: [10de:0817] type 01 class 0x060400
[    0.160804] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160859] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.161057] pci 0000:00:09.0: [10de:0369] type 00 class 0x050000
[    0.161304] pci 0000:00:0a.0: [10de:0360] type 00 class 0x060100
[    0.161313] pci 0000:00:0a.0: reg 0x10: [io  0xfc00-0xfc7f]
[    0.161414] pci 0000:00:0a.1: [10de:0368] type 00 class 0x0c0500
[    0.161428] pci 0000:00:0a.1: reg 0x10: [io  0xf800-0xf83f]
[    0.161450] pci 0000:00:0a.1: reg 0x20: [io  0xf400-0xf43f]
[    0.161456] pci 0000:00:0a.1: reg 0x24: [io  0xf000-0xf03f]
[    0.161493] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.161580] pci 0000:00:0b.0: [10de:036c] type 00 class 0x0c0310
[    0.161591] pci 0000:00:0b.0: reg 0x10: [mem 0xdffff000-0xdfffffff]
[    0.161635] pci 0000:00:0b.0: supports D1 D2
[    0.161636] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.161678] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.161839] pci 0000:00:0b.1: [10de:036d] type 00 class 0x0c0320
[    0.161850] pci 0000:00:0b.1: reg 0x10: [mem 0xdfffe000-0xdfffe0ff]
[    0.161897] pci 0000:00:0b.1: supports D1 D2
[    0.161898] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.161953] pci 0000:00:0b.1: System wakeup disabled by ACPI
[    0.162122] pci 0000:00:0d.0: [10de:036e] type 00 class 0x01018a
[    0.162146] pci 0000:00:0d.0: reg 0x20: [io  0xec00-0xec0f]
[    0.162157] pci 0000:00:0d.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.162289] pci 0000:00:0d.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.162417] pci 0000:00:0d.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.162549] pci 0000:00:0d.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.162762] pci 0000:00:0e.0: [10de:037f] type 00 class 0x010185
[    0.162774] pci 0000:00:0e.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.162779] pci 0000:00:0e.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.162784] pci 0000:00:0e.0: reg 0x18: [io  0x0970-0x0977]
[    0.162790] pci 0000:00:0e.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.162795] pci 0000:00:0e.0: reg 0x20: [io  0xd800-0xd80f]
[    0.162801] pci 0000:00:0e.0: reg 0x24: [mem 0xdfffd000-0xdfffdfff]
[    0.162901] pci 0000:00:0e.1: [10de:037f] type 00 class 0x010185
[    0.162912] pci 0000:00:0e.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.162918] pci 0000:00:0e.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.162923] pci 0000:00:0e.1: reg 0x18: [io  0x0960-0x0967]
[    0.162929] pci 0000:00:0e.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.162934] pci 0000:00:0e.1: reg 0x20: [io  0xc400-0xc40f]
[    0.162940] pci 0000:00:0e.1: reg 0x24: [mem 0xdfffc000-0xdfffcfff]
[    0.163039] pci 0000:00:0e.2: [10de:037f] type 00 class 0x010185
[    0.163051] pci 0000:00:0e.2: reg 0x10: [io  0xc000-0xc007]
[    0.163056] pci 0000:00:0e.2: reg 0x14: [io  0xbc00-0xbc03]
[    0.163062] pci 0000:00:0e.2: reg 0x18: [io  0xb800-0xb807]
[    0.163067] pci 0000:00:0e.2: reg 0x1c: [io  0xb400-0xb403]
[    0.163073] pci 0000:00:0e.2: reg 0x20: [io  0xb000-0xb00f]
[    0.163078] pci 0000:00:0e.2: reg 0x24: [mem 0xdfffb000-0xdfffbfff]
[    0.163182] pci 0000:00:0f.0: [10de:0370] type 01 class 0x060401
[    0.163253] pci 0000:00:0f.0: System wakeup disabled by ACPI
[    0.163422] pci 0000:00:0f.1: [10de:0371] type 00 class 0x040300
[    0.163435] pci 0000:00:0f.1: reg 0x10: [mem 0xdfff0000-0xdfff3fff]
[    0.163488] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.163532] pci 0000:00:0f.1: System wakeup disabled by ACPI
[    0.163705] pci 0000:00:11.0: [10de:0373] type 00 class 0x068000
[    0.163719] pci 0000:00:11.0: reg 0x10: [mem 0xdfffa000-0xdfffafff]
[    0.163725] pci 0000:00:11.0: reg 0x14: [io  0xac00-0xac07]
[    0.163730] pci 0000:00:11.0: reg 0x18: [mem 0xdfff9000-0xdfff90ff]
[    0.163736] pci 0000:00:11.0: reg 0x1c: [mem 0xdfff8000-0xdfff800f]
[    0.163781] pci 0000:00:11.0: supports D1 D2
[    0.163783] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163829] pci 0000:00:11.0: System wakeup disabled by ACPI
[    0.163993] pci 0000:00:12.0: [10de:0373] type 00 class 0x068000
[    0.164013] pci 0000:00:12.0: reg 0x10: [mem 0xdfff7000-0xdfff7fff]
[    0.164019] pci 0000:00:12.0: reg 0x14: [io  0xa800-0xa807]
[    0.164024] pci 0000:00:12.0: reg 0x18: [mem 0xdfff6000-0xdfff60ff]
[    0.164030] pci 0000:00:12.0: reg 0x1c: [mem 0xdfff5000-0xdfff500f]
[    0.164075] pci 0000:00:12.0: supports D1 D2
[    0.164076] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164124] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.164290] pci 0000:00:15.0: [10de:0374] type 01 class 0x060400
[    0.164335] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164380] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.164612] pci 0000:01:00.0: [10de:0191] type 00 class 0x030000
[    0.164621] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.164629] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.164638] pci 0000:01:00.0: reg 0x1c: [mem 0xda000000-0xdbffffff 64bit]
[    0.164644] pci 0000:01:00.0: reg 0x24: [io  0x9c00-0x9c7f]
[    0.164650] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.164714] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.164913] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.165036] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.165039] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.165045] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.165106] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.165291] pci 0000:00:0f.0: PCI bridge to [bus 03] (subtractive decode)
[    0.165424] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.165426] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.165428] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.165430] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.165431] pci 0000:00:0f.0:   bridge window [mem 0xbff00000-0xfebfffff] (subtractive decode)
[    0.165486] pci 0000:04:00.0: [197b:2363] type 00 class 0x010601
[    0.165558] pci 0000:04:00.0: reg 0x24: [mem 0xdfefe000-0xdfefffff]
[    0.165614] pci 0000:04:00.0: PME# supported from D3hot
[    0.165670] pci 0000:04:00.1: [197b:2363] type 00 class 0x010185
[    0.165687] pci 0000:04:00.1: reg 0x10: [io  0x8c00-0x8c07]
[    0.165695] pci 0000:04:00.1: reg 0x14: [io  0x8800-0x8803]
[    0.165704] pci 0000:04:00.1: reg 0x18: [io  0x8400-0x8407]
[    0.165712] pci 0000:04:00.1: reg 0x1c: [io  0x8000-0x8003]
[    0.165720] pci 0000:04:00.1: reg 0x20: [io  0x7c00-0x7c0f]
[    0.165810] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.166008] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.166129] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
[    0.166132] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.166515] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.167229] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.167942] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.168642] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.169364] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
[    0.169936] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.170650] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 *11 14 15)
[    0.171223] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 *10 11 14 15)
[    0.171805] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.172363] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.172945] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.173524] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.174096] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.174810] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.175391] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.176129] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.176702] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.177288] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.177890] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.178306] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.178718] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.179131] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.179553] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0, disabled.
[    0.179966] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.180341] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.180754] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.181167] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0, disabled.
[    0.181627] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0, disabled.
[    0.182086] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0, disabled.
[    0.182545] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0, disabled.
[    0.183005] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[    0.183474] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[    0.184011] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[    0.184470] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0, disabled.
[    0.184939] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[    0.185398] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0, disabled.
[    0.185858] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0, disabled.
[    0.186317] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0, disabled.
[    0.186827] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.186827] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.186827] vgaarb: loaded
[    0.186827] vgaarb: bridge control possible 0000:01:00.0
[    0.186827] SCSI subsystem initialized
[    0.186827] libata version 3.00 loaded.
[    0.186827] ACPI: bus type USB registered
[    0.186827] usbcore: registered new interface driver usbfs
[    0.188012] usbcore: registered new interface driver hub
[    0.188160] usbcore: registered new device driver usb
[    0.188344] PCI: Using ACPI for IRQ routing
[    0.195214] PCI: pci_cache_line_size set to 64 bytes
[    0.195280] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
[    0.195282] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.195378] NetLabel: Initializing
[    0.195487] NetLabel:  domain hash size = 128
[    0.195602] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195732] NetLabel:  unlabeled traffic allowed by default
[    0.195879] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.196006] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.196306] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.198447] Switched to clocksource hpet
[    0.202505] AppArmor: AppArmor Filesystem Enabled
[    0.202689] pnp: PnP ACPI init
[    0.202885] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.203013] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.203138] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.203263] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.203388] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.203513] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.203639] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.203745] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.203870] system 00:01: [io  0x0295-0x0314] has been reserved
[    0.203995] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.204136] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.204191] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.204351] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.204817] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.204947] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.205071] system 00:05: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.205200] system 00:05: [mem 0x000d9000-0x000dbfff] has been reserved
[    0.205330] system 00:05: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.205461] system 00:05: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.205593] system 00:05: [mem 0xbfef0000-0xbfefffff] could not be reserved
[    0.205724] system 00:05: [mem 0xffff0000-0xffffffff] has been reserved
[    0.205853] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.205984] system 00:05: [mem 0x00100000-0xbfeeffff] could not be reserved
[    0.206115] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.206246] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.206375] system 00:05: [mem 0xfeff0000] has been reserved
[    0.206499] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.206506] pnp: PnP ACPI: found 6 devices
[    0.215330] pci 0000:01:00.0: BAR 6: assigned [mem 0xdd000000-0xdd01ffff pref]
[    0.215508] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.215629] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.215757] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.215889] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.216083] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.216211] pci 0000:00:0f.0: PCI bridge to [bus 03]
[    0.216335] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.216454] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
[    0.216582] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.216715] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.216716] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.216718] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.216720] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.216721] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.216723] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.216725] pci_bus 0000:01: resource 1 [mem 0xda000000-0xddffffff]
[    0.216727] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.216729] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.216730] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.216732] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.216733] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.216735] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.216737] pci_bus 0000:04: resource 0 [io  0x7000-0x8fff]
[    0.216738] pci_bus 0000:04: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.216764] NET: Registered protocol family 2
[    0.217089] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.217510] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.217988] TCP: Hash tables configured (established 65536 bind 65536)
[    0.218154] TCP: reno registered
[    0.218272] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.218447] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.218651] NET: Registered protocol family 1
[    0.219100] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    0.288354] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    0.288689] pci 0000:01:00.0: Video device with shadowed ROM
[    0.288693] pci 0000:04:00.0: async suspend disabled to avoid multi-function power-on ordering issue
[    0.288883] pci 0000:04:00.1: async suspend disabled to avoid multi-function power-on ordering issue
[    0.289072] PCI: CLS 64 bytes, default 64
[    0.289123] Trying to unpack rootfs image as initramfs...
[    0.662844] Freeing initrd memory: 25660K (ffff880034dd2000 - ffff8800366e1000)
[    0.663060] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.663188] software IO TLB [mem 0xbbef0000-0xbfef0000] (64MB) mapped at [ffff8800bbef0000-ffff8800bfeeffff]
[    0.663644] microcode: CPU0 sig=0x1067a, pf=0x10, revision=0xa07
[    0.663787] microcode: CPU1 sig=0x1067a, pf=0x10, revision=0xa07
[    0.663927] microcode: CPU2 sig=0x1067a, pf=0x10, revision=0xa07
[    0.664082] microcode: CPU3 sig=0x1067a, pf=0x10, revision=0xa07
[    0.664282] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.664512] Scanning for low memory corruption every 60 seconds
[    0.664917] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.665058] Initialise system trusted keyring
[    0.665190] audit: initializing netlink subsys (disabled)
[    0.665328] audit: type=2000 audit(1455571514.664:1): initialized
[    0.665761] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.667555] zpool: loaded
[    0.669368] zbud: loaded
[    0.669625] VFS: Disk quotas dquot_6.5.2
[    0.669771] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.670405] fuse init (API version 7.23)
[    0.670661] Key type big_key registered
[    0.671571] Key type asymmetric registered
[    0.671687] Asymmetric key parser 'x509' registered
[    0.671847] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.672126] io scheduler noop registered
[    0.672243] io scheduler deadline registered (default)
[    0.672391] io scheduler cfq registered
[    0.672803] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[    0.673196] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[    0.673492] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.673623] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.673754] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.673772] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    0.673905] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    0.673918] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.674049] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.674177] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.674306] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.674313] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.674449] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.674614] intel_idle: does not run on family 6 model 23
[    0.674684] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.674869] ACPI: Power Button [PWRB]
[    0.675028] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.675205] ACPI: Power Button [PWRF]
[    0.675638] GHES: HEST is not enabled!
[    0.675883] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.677834] Linux agpgart interface v0.103
[    0.679383] brd: module loaded
[    0.680222] loop: module loaded
[    0.680546] libphy: Fixed MDIO Bus: probed
[    0.680661] tun: Universal TUN/TAP device driver, 1.6
[    0.680780] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.680951] PPP generic driver version 2.4.2
[    0.681137] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.681268] ehci-pci: EHCI PCI platform driver
[    0.681511] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    0.681636] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.681819] ehci-pci 0000:00:0b.1: debug port 1
[    0.681957] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    0.681970] ehci-pci 0000:00:0b.1: irq 22, io mem 0xdfffe000
[    0.692022] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.692202] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.692332] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.692508] usb usb1: Product: EHCI Host Controller
[    0.692626] usb usb1: Manufacturer: Linux 3.19.0-49-generic ehci_hcd
[    0.692754] usb usb1: SerialNumber: 0000:00:0b.1
[    0.692976] hub 1-0:1.0: USB hub found
[    0.693093] hub 1-0:1.0: 10 ports detected
[    0.693392] ehci-platform: EHCI generic platform driver
[    0.693519] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.693647] ohci-pci: OHCI PCI platform driver
[    0.693877] ohci-pci 0000:00:0b.0: OHCI PCI host controller
[    0.694003] ohci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.694202] ohci-pci 0000:00:0b.0: irq 23, io mem 0xdffff000
[    0.750043] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.750173] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.750350] usb usb2: Product: OHCI PCI host controller
[    0.750470] usb usb2: Manufacturer: Linux 3.19.0-49-generic ohci_hcd
[    0.750597] usb usb2: SerialNumber: 0000:00:0b.0
[    0.750819] hub 2-0:1.0: USB hub found
[    0.750937] hub 2-0:1.0: 10 ports detected
[    0.751235] ohci-platform: OHCI generic platform driver
[    0.751364] uhci_hcd: USB Universal Host Controller Interface driver
[    0.751534] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.751664] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.752677] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.752910] mousedev: PS/2 mouse device common for all mice
[    0.753180] rtc_cmos 00:02: RTC can wake from S4
[    0.753435] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.753590] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.753774] i2c /dev entries driver
[    0.753944] device-mapper: uevent: version 1.0.3
[    0.754139] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.754334] ledtrig-cpu: registered to indicate activity on CPUs
[    0.754687] PCCT header not found.
[    0.754874] TCP: cubic registered
[    0.755085] NET: Registered protocol family 10
[    0.755418] NET: Registered protocol family 17
[    0.755542] Key type dns_resolver registered
[    0.756024] Loading compiled-in X.509 certificates
[    0.757008] Loaded X.509 cert 'Magrathea: Glacier signing key: a932dc237895a44d3959bf91a3566a20ee211f37'
[    0.757208] registered taskstats version 1
[    0.759095] Key type trusted registered
[    0.762207] Key type encrypted registered
[    0.762326] AppArmor: AppArmor sha1 policy hashing enabled
[    0.762449] ima: No TPM chip found, activating TPM-bypass!
[    0.762586] evm: HMAC attrs: 0x1
[    0.763059]   Magic number: 4:704:449
[    0.763270] rtc_cmos 00:02: setting system clock to 2016-02-15 21:25:15 UTC (1455571515)
[    0.763557] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.763682] EDD information not available.
[    0.763842] PM: Hibernation image not present or could not be loaded.
[    0.764357] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    0.764537] Write protecting the kernel read-only data: 12288k
[    0.764927] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
[    0.765267] Freeing unused kernel memory: 336K (ffff880001bac000 - ffff880001c00000)
[    0.774120] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.778498] systemd-udevd[119]: starting version 204
[    0.800480] pata_amd 0000:00:0d.0: version 0.4.1
[    0.801070] scsi host0: pata_amd
[    0.801295] scsi host1: pata_amd
[    0.801450] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    0.801581] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    0.801728] sata_nv 0000:00:0e.0: version 3.5
[    0.801950] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    0.802101] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.803645] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    0.807195] scsi host3: pata_jmicron
[    0.807458] scsi host4: pata_jmicron
[    0.807684] ata5: PATA max UDMA/100 cmd 0x8c00 ctl 0x8800 bmdma 0x7c00 irq 16
[    0.807822] ata6: PATA max UDMA/100 cmd 0x8400 ctl 0x8000 bmdma 0x7c08 irq 16
[    0.807970] ahci 0000:04:00.0: version 3.0
[    0.808215] ACPI: PCI Interrupt Link [AXV8] enabled at IRQ 16
[    0.808526] scsi host2: sata_nv
[    0.808883] scsi host5: sata_nv
[    0.809056] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    0.809203] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    0.809543] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    0.809689] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    0.810266] scsi host6: sata_nv
[    0.810522] scsi host7: sata_nv
[    0.810696] ata7: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    0.810837] ata8: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    0.810983] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.811370] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    0.824143] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.824335] ahci 0000:04:00.0: flags: 64bit ncq led clo pmp pio
[    0.824847] scsi host8: ahci
[    0.825068] scsi host9: ahci
[    0.825227] ata9: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 16
[    0.825410] ata10: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 16
[    0.967002] ata2: port disabled--ignoring
[    1.144033] ata10: SATA link down (SStatus 0 SControl 300)
[    1.144190] ata9: SATA link down (SStatus 0 SControl 300)
[    1.276033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.276035] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.284303] ata7.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    1.284437] ata7.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.300267] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
[    1.300412] ata7.00: configured for UDMA/133
[    1.332141] ata3.00: configured for UDMA/100
[    1.332682] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:04:4b:17:22:9a
[    1.332866] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.333309] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    1.334223] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[    1.350202] sr 2:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.350395] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.350681] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.350765] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.664021] tsc: Refined TSC clocksource calibration: 2999.958 MHz
[    1.816025] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.824289] ata4.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
[    1.824423] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.840306] ata4.00: configured for UDMA/133
[    1.840530] scsi 5:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 3B01 PQ: 0 ANSI: 5
[    1.840935] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    1.840938] sd 5:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.841041] sd 5:0:0:0: [sda] Write Protect is off
[    1.841043] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.841064] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.843365] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    1.843775] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    1.843784] sd 6:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.843928] sd 6:0:0:0: [sdb] Write Protect is off
[    1.843930] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.844104] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.856463] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x50ef @ 1, addr 00:04:4b:17:22:9b
[    1.856648] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.857070] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    1.857213] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    1.857823] scsi host10: sata_nv
[    1.858093] scsi host11: sata_nv
[    1.858268] ata11: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    1.858444] ata12: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    1.871956]  sda: sda1 sda2 < sda5 >
[    1.872454] sd 5:0:0:0: [sda] Attached SCSI disk
[    1.883738]  sdb: sdb1 sdb9
[    1.884207] sd 6:0:0:0: [sdb] Attached SCSI disk
[    2.312028] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.320288] ata8.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.320423] ata8.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.324029] ata11: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.332320] ata11.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.332455] ata11.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.336282] ata8.00: configured for UDMA/133
[    2.336478] scsi 7:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.336852] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    2.336854] sd 7:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.336959] sd 7:0:0:0: [sdc] Write Protect is off
[    2.336961] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.336978] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.348289] ata11.00: configured for UDMA/133
[    2.348496] scsi 10:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.348865] sd 10:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.348902] sd 10:0:0:0: Attached scsi generic sg4 type 0
[    2.349289] sd 10:0:0:0: [sdd] Write Protect is off
[    2.349409] sd 10:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.349439] sd 10:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.369361]  sdc: sdc1 sdc9
[    2.369666] sd 7:0:0:0: [sdc] Attached SCSI disk
[    2.378424]  sdd: sdd1 sdd9
[    2.378793] sd 10:0:0:0: [sdd] Attached SCSI disk
[    2.664091] Switched to clocksource tsc
[    2.816020] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.824277] ata12.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.824412] ata12.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.840268] ata12.00: configured for UDMA/133
[    2.840458] scsi 11:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.840830] sd 11:0:0:0: Attached scsi generic sg5 type 0
[    2.840832] sd 11:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.840890] sd 11:0:0:0: [sde] Write Protect is off
[    2.840891] sd 11:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.840910] sd 11:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.877392]  sde: sde1 sde9
[    2.877709] sd 11:0:0:0: [sde] Attached SCSI disk
[    2.969797] random: nonblocking pool is initialized
[    3.812024] floppy0: no floppy controllers found
[    4.925380] md: linear personality registered for level -1
[    4.927657] md: multipath personality registered for level -4
[    4.929958] md: raid0 personality registered for level 0
[    4.932512] md: raid1 personality registered for level 1
[    5.000020] raid6: sse2x1    4965 MB/s
[    5.068023] raid6: sse2x2    5595 MB/s
[    5.136017] raid6: sse2x4    8749 MB/s
[    5.136044] raid6: using algorithm sse2x4 (8749 MB/s)
[    5.136078] raid6: using ssse3x2 recovery algorithm
[    5.137221] xor: measuring software checksum speed
[    5.176008]    prefetch64-sse: 12531.000 MB/sec
[    5.216007]    generic_sse: 11041.000 MB/sec
[    5.216037] xor: using function: prefetch64-sse (12531.000 MB/sec)
[    5.217124] async_tx: api initialized (async)
[    5.223488] md: raid6 personality registered for level 6
[    5.223525] md: raid5 personality registered for level 5
[    5.223561] md: raid4 personality registered for level 4
[    5.228487] md: raid10 personality registered for level 10
[   10.259554] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[   10.259601] EXT4-fs (dm-0): write access will be enabled during recovery
[   11.019875] EXT4-fs (dm-0): recovery complete
[   11.024194] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   12.535120] zavl: module license 'CDDL' taints kernel.
[   12.535209] Disabling lock debugging due to kernel taint
[   12.535304] zavl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.543456] SPL: Loaded module v0.6.5.4-1~trusty
[   12.601054] ZFS: Loaded module v0.6.5.4-1~trusty, ZFS pool version 5000, ZFS filesystem version 5
[   14.094882] SPL: using hostid 0x007f0101
[   16.806797] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   16.996978] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   17.027539] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   18.125883] systemd-udevd[1817]: starting version 204
[   18.708558] lp: driver loaded but no devices found
[   20.144530] i2c i2c-0: nForce2 SMBus adapter at 0xf400
[   20.144590] i2c i2c-1: nForce2 SMBus adapter at 0xf000
[   20.183862] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.627456] [drm] Initialized drm 1.1.0 20060810
[   20.889711] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   20.889720] snd_hda_intel 0000:00:0f.1: Disabling MSI
[   21.724014] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   21.724018] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.724021] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   21.724024] sound hdaudioC0D0:    mono: mono_out=0x0
[   21.724026] sound hdaudioC0D0:    dig-out=0x11/0x1e
[   21.724028] sound hdaudioC0D0:    inputs:
[   21.724032] sound hdaudioC0D0:      Front Mic=0x19
[   21.724034] sound hdaudioC0D0:      Rear Mic=0x18
[   21.724037] sound hdaudioC0D0:      Line=0x1a
[   21.724039] sound hdaudioC0D0:    dig-in=0x1f
[   22.027881] audit: type=1400 audit(1455571536.759:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1979 comm="apparmor_parser"
[   22.027888] audit: type=1400 audit(1455571536.759:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1979 comm="apparmor_parser"
[   22.027892] audit: type=1400 audit(1455571536.759:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1979 comm="apparmor_parser"
[   22.027900] audit: type=1400 audit(1455571536.759:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1980 comm="apparmor_parser"
[   22.027906] audit: type=1400 audit(1455571536.759:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1980 comm="apparmor_parser"
[   22.027911] audit: type=1400 audit(1455571536.759:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1980 comm="apparmor_parser"
[   22.027923] audit: type=1400 audit(1455571536.759:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1981 comm="apparmor_parser"
[   22.027931] audit: type=1400 audit(1455571536.759:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1981 comm="apparmor_parser"
[   22.027936] audit: type=1400 audit(1455571536.759:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1981 comm="apparmor_parser"
[   22.028273] audit: type=1400 audit(1455571536.763:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1979 comm="apparmor_parser"
[   23.025575] forcedeth 0000:00:11.0 eth0: MSI enabled
[   23.080042] floppy0: no floppy controllers found
[   23.080052] work still pending
[   23.453763] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   23.453962] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[   23.453974] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.131  Sun Nov  8 21:43:33 PST 2015
[   23.580559] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input3
[   23.580648] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input4
[   23.582819] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
[   23.582915] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
[   23.583078] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
[   23.583152] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
[   23.583238] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
[   23.583624] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
[   24.204382] init: failsafe main process (2048) killed by TERM signal
[   27.839707] audit_printk_skb: 54 callbacks suppressed
[   27.839709] audit: type=1400 audit(1455571542.571:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=2531 comm="apparmor_parser"
[   32.499772] init: samba-ad-dc main process (2472) terminated with status 1
[   38.546982] init: plymouth-upstart-bridge main process ended, respawning
[   38.676673] Ebtables v2.0 registered
[   39.019784] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.120149] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   42.105711] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   42.414031] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   68.318007] cgroup: systemd-logind (1987) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   68.318010] cgroup: "memory" requires setting use_hierarchy to 1 on the root

```

An ls of the /var/log/ directory appears as follows:

```
alternatives.log    dmesg.0         lastlog         mysql.log.7.gz
alternatives.log.1  dmesg.1.gz      libvirt         samba
apache2             dmesg.2.gz      mail.err        syslog
apport.log          dmesg.3.gz      mail.err.1      syslog.1
apport.log.1        dmesg.4.gz      mail.err.2.gz   syslog.2.gz
apt                 dpkg.log        mail.log        syslog.3.gz
auth.log            dpkg.log.1      mail.log.1      syslog.4.gz
auth.log.1          faillog         mail.log.2.gz   syslog.5.gz
auth.log.2.gz       fontconfig.log  mysql           syslog.6.gz
auth.log.3.gz       fsck            mysql.err       syslog.7.gz
auth.log.4.gz       installer       mysql.log       udev
boot.log            kern.log        mysql.log.1.gz  unattended-upgrades
bootstrap.log       kern.log.1      mysql.log.2.gz  upstart
btmp                kern.log.2.gz   mysql.log.3.gz  wtmp
btmp.1              kern.log.3.gz   mysql.log.4.gz  wtmp.1
dist-upgrade        kern.log.4.gz   mysql.log.5.gz
dmesg               landscape       mysql.log.6.gz

```

I'm not seeing files of the name you mentioned. But I certainly see that there is a dmesg, dmesg.1.gz, etc. which you might be implying.

I've found further reference to what I believe to be my motherboard's networking hardware and drivers (nForce chipset) here: [http://manpages.ubuntu.com/manpages/trusty/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/trusty/man4/nfe.4freebsd.html). I'm not sure how to check what networking drivers are installed.

The messages at the server's terminal run off the screen and I don't know of a way to scroll back. They seem to have something to do with storage. But when I browse from a PC they're there and all's fine as if I missed a brief event or even a reboot.

Suggestions as to how to proceed? Thanks again!

---

### Post by kazz2 on 2016-02-15
Searching through those files I found that syslog.1 seems to have a record of what I was seeing at the terminal. However it overruns the buffer on putty.  Sorry this is so huge!

```
Feb 14 22:41:11 kazz-u0a1 dbus[1903]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)Feb 14 22:41:11 kazz-u0a1 dbus[1903]: [system] Successfully activated service 'org.freedesktop.systemd1'
Feb 14 06:28:59 kazz-u0a1 rsyslogd: message repeated 2 times: [ [origin software="rsyslogd" swVersion="7.4.4" x-pid="1929" x-info="http://www.rsyslog.com"] rsyslogd was HUPed]
Feb 14 22:41:11 kazz-u0a1 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1929" x-info="http://www.rsyslog.com"] exiting on signal 15.
Feb 14 22:45:42 kazz-u0a1 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1922" x-info="http://www.rsyslog.com"] start
Feb 14 22:45:42 kazz-u0a1 rsyslogd: rsyslogd's groupid changed to 104
Feb 14 22:45:42 kazz-u0a1 rsyslogd: rsyslogd's userid changed to 101
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Linux version 3.19.0-49-generic (buildd@lgw01-08) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 (Ubuntu 3.19.0-49.55~14.04.1-generic 3.19.8-ckt12)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] KERNEL supported cpus:
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   Intel GenuineIntel
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   AMD AuthenticAMD
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   Centaur CentaurHauls
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009b7ff] usable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009b800-0x000000000009ffff] reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfeeffff] usable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfef2fff] ACPI NVS
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bfef3000-0x00000000bfefffff] ACPI data
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] SMBIOS 2.4 present.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] DMI:  EVGA  132-CK-NF79/132-CK-NF79, BIOS   P10  12/30/2009
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] AGP: No AGP bridge found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] MTRR default type: uncachable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   00000-9FFFF write-back
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   C0000-CBFFF write-protect
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   CC000-FFFFF uncachable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] MTRR variable ranges enabled:
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   4 disabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   5 disabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   6 disabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   7 disabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] original variable MTRRs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 1, base: 8GB, range: 1GB, type WB
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 2, base: 3GB, range: 1GB, type UC
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] total RAM covered: 8191M
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Found optimal setting for mtrr clean up
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  gran_size: 64K        chunk_size: 2M  num_reg: 5      lose cover RAM: 0G
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] New variable MTRRs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] reg 4, base: 8GB, range: 1GB, type WB
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: last_pfn = 0xbfef0 max_arch_pfn = 0x400000000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] found SMP MP-table at [mem 0x000f3fd0-0x000f3fdf] mapped at [ffff8800000f3fd0]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] init_memory_mapping: [mem 0x220000000-0x23fdfffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0x220000000-0x23fdfffff] page 2M
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xbfeeffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0x00200000-0xbfdfffff] page 2M
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0xbfe00000-0xbfeeffff] page 4k
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x21fffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [mem 0x100000000-0x21fffffff] page 2M
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] RAMDISK: [mem 0x34cc8000-0x3665bfff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: Early table checksum verification disabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: RSDP 0x00000000000F7FA0 000014 (v00 Nvidia)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: RSDT 0x00000000BFEF3040 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: FACP 0x00000000BFEF30C0 000074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: DSDT 0x00000000BFEF3180 005447 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: FACS 0x00000000BFEF0000 000040
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: HPET 0x00000000BFEF8740 000038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: WDRT 0x00000000BFEF87C0 000047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: MCFG 0x00000000BFEF8880 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: APIC 0x00000000BFEF8640 000098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: OEMN 0x00000000BFEF8900 004AED (v01 NVIDIA NTUNEOEM 20302E31 NVDA 00000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] No NUMA configuration found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x23fff6000-0x23fffafff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Zone ranges:
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Movable zone start for each node
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Early memory node ranges
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009afff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   node   0: [mem 0x00100000-0xbfeeffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Initmem setup node 0 [mem 0x00001000-0x23fffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] On node 0 totalpages: 2096778
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA zone: 21 pages reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA zone: 3994 pages, LIFO batch:0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA32 zone: 12220 pages used for memmap
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   DMA32 zone: 782064 pages, LIFO batch:31
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   Normal zone: 20480 pages used for memmap
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: IRQ14 used by override.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: IRQ15 used by override.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfef0000-0xbfef2fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfef3000-0xbfefffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xdfffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] e820: [mem 0xbff00000-0xdfffffff] available for PCI devices
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88023fc00000 s86144 r8192 d32640 u524288
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2063993
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Policy zone: Normal
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] AGP: Checking aperture...
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] AGP: No AGP bridge found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Memory: 8146696K/8387112K available (7923K kernel code, 1174K rwdata, 3760K rodata, 1408K init, 1292K bss, 240416K reserved, 0K cma-reserved)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Hierarchical RCU implementation.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]        RCU dyntick-idle grace-period acceleration is enabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]        RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:456 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]        Offload RCU callbacks from all CPUs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000]        Offload RCU callbacks from CPUs: 0-3.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] Console: colour dummy device 80x25
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] console [tty0] enabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] hpet clockevent registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.000000] tsc: Detected 2999.976 MHz processor
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.95 BogoMIPS (lpj=11999904)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.004014] pid_max: default: 32768 minimum: 301
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.004020] ACPI: Core revision 20141107
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.010107] ACPI: All ACPI Tables successfully acquired
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.010130] Security Framework initialized
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.010149] AppArmor: AppArmor initialized
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.010151] Yama: becoming mindful.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.010674] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.014009] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015418] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015430] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015741] Initializing cgroup subsys memory
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015751] Initializing cgroup subsys devices
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015755] Initializing cgroup subsys freezer
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015758] Initializing cgroup subsys net_cls
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015762] Initializing cgroup subsys blkio
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015765] Initializing cgroup subsys perf_event
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015768] Initializing cgroup subsys net_prio
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015771] Initializing cgroup subsys hugetlb
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015794] CPU: Physical Processor ID: 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015797] CPU: Processor Core ID: 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015799] mce: CPU supports 6 MCE banks
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015805] CPU0: Thermal monitoring enabled (TM1)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015809] process: using mwait in idle threads
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015815] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015815] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.015902] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.019411] ftrace: allocating 30034 entries in 118 pages
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.028537] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.071799] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz (fam: 06, model: 17, stepping: 0a)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... version:                2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... bit width:              40
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... generic registers:      2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... value mask:             000000ffffffffff
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... max period:             000000007fffffff
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... fixed-purpose events:   3
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] ... event mask:             0000000700000003
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] x86: Booting SMP configuration:
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.072000] .... node  #0, CPUs:      #1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.082142] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.082251]  #2 #3
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.108027] x86: Booted up 1 node, 4 CPUs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.108035] smpboot: Total of 4 processors activated (23999.80 BogoMIPS)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.112138] devtmpfs: initialized
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116741] evm: security.selinux
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116743] evm: security.SMACK64
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116745] evm: security.SMACK64EXEC
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116747] evm: security.SMACK64TRANSMUTE
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116748] evm: security.SMACK64MMAP
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116750] evm: security.ima
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116751] evm: security.capability
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116765] PM: Registering ACPI NVS region [mem 0xbfef0000-0xbfef2fff] (12288 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116765] pinctrl core: initialized pinctrl subsystem
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116765] RTC time:  4:45:19, date: 02/15/16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.116765] NET: Registered protocol family 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.124007] cpuidle: using governor ladder
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.128006] cpuidle: using governor menu
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.128062] ACPI: bus type PCI registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.128066] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.128160] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.128171] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.128515] PCI: Using configuration type 1 for base access
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.132126] ACPI: Added _OSI(Module Device)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.132129] ACPI: Added _OSI(Processor Device)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.132136] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.132138] ACPI: Added _OSI(Processor Aggregator Device)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136472] ACPI: Interpreter enabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136478] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136484] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136496] ACPI: (supports S0 S3 S4 S5)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136498] ACPI: Using IOAPIC for interrupt routing
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136589] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.136606] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141452] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141459] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141548] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141634] acpi PNP0A08:00: _OSC: OS now controls [PME AER PCIeCapability]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141881] PCI host bridge to bus 0000:00
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141885] pci_bus 0000:00: root bus resource [bus 00-ff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141887] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141890] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141892] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141895] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141897] pci_bus 0000:00: root bus resource [mem 0xbff00000-0xfebfffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.141908] pci 0000:00:00.0: [10de:0800] type 00 class 0x060000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142022] pci 0000:00:00.1: [10de:0808] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142133] pci 0000:00:00.2: [10de:0809] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142240] pci 0000:00:00.3: [10de:080a] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142360] pci 0000:00:00.4: [10de:080b] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142478] pci 0000:00:00.5: [10de:080c] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142577] pci 0000:00:00.6: [10de:080d] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142684] pci 0000:00:00.7: [10de:080e] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142792] pci 0000:00:01.0: [10de:080f] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142890] pci 0000:00:01.1: [10de:0810] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.142989] pci 0000:00:01.2: [10de:0811] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143087] pci 0000:00:01.3: [10de:0812] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143195] pci 0000:00:01.4: [10de:0813] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143292] pci 0000:00:01.5: [10de:0814] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143391] pci 0000:00:01.6: [10de:081a] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143510] pci 0000:00:01.7: [10de:080e] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143629] pci 0000:00:02.0: [10de:0815] type 01 class 0x060400
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143712] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143764] pci 0000:00:02.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143824] pci 0000:00:04.0: [10de:0817] type 01 class 0x060400
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143902] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.143954] pci 0000:00:04.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144035] pci 0000:00:09.0: [10de:0369] type 00 class 0x050000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144282] pci 0000:00:0a.0: [10de:0360] type 00 class 0x060100
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144291] pci 0000:00:0a.0: reg 0x10: [io  0xfc00-0xfc7f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144392] pci 0000:00:0a.1: [10de:0368] type 00 class 0x0c0500
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144406] pci 0000:00:0a.1: reg 0x10: [io  0xf800-0xf83f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144428] pci 0000:00:0a.1: reg 0x20: [io  0xf400-0xf43f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144435] pci 0000:00:0a.1: reg 0x24: [io  0xf000-0xf03f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144472] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144559] pci 0000:00:0b.0: [10de:036c] type 00 class 0x0c0310
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144570] pci 0000:00:0b.0: reg 0x10: [mem 0xdffff000-0xdfffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144614] pci 0000:00:0b.0: supports D1 D2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144615] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144657] pci 0000:00:0b.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144697] pci 0000:00:0b.1: [10de:036d] type 00 class 0x0c0320
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144708] pci 0000:00:0b.1: reg 0x10: [mem 0xdfffe000-0xdfffe0ff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144755] pci 0000:00:0b.1: supports D1 D2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144757] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144811] pci 0000:00:0b.1: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144860] pci 0000:00:0d.0: [10de:036e] type 00 class 0x01018a
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144884] pci 0000:00:0d.0: reg 0x20: [io  0xec00-0xec0f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144895] pci 0000:00:0d.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144898] pci 0000:00:0d.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144900] pci 0000:00:0d.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144902] pci 0000:00:0d.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.144989] pci 0000:00:0e.0: [10de:037f] type 00 class 0x010185
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145001] pci 0000:00:0e.0: reg 0x10: [io  0x09f0-0x09f7]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145006] pci 0000:00:0e.0: reg 0x14: [io  0x0bf0-0x0bf3]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145012] pci 0000:00:0e.0: reg 0x18: [io  0x0970-0x0977]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145017] pci 0000:00:0e.0: reg 0x1c: [io  0x0b70-0x0b73]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145023] pci 0000:00:0e.0: reg 0x20: [io  0xd800-0xd80f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145028] pci 0000:00:0e.0: reg 0x24: [mem 0xdfffd000-0xdfffdfff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145128] pci 0000:00:0e.1: [10de:037f] type 00 class 0x010185
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145140] pci 0000:00:0e.1: reg 0x10: [io  0x09e0-0x09e7]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145145] pci 0000:00:0e.1: reg 0x14: [io  0x0be0-0x0be3]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145150] pci 0000:00:0e.1: reg 0x18: [io  0x0960-0x0967]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145156] pci 0000:00:0e.1: reg 0x1c: [io  0x0b60-0x0b63]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145161] pci 0000:00:0e.1: reg 0x20: [io  0xc400-0xc40f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145167] pci 0000:00:0e.1: reg 0x24: [mem 0xdfffc000-0xdfffcfff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145266] pci 0000:00:0e.2: [10de:037f] type 00 class 0x010185
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145278] pci 0000:00:0e.2: reg 0x10: [io  0xc000-0xc007]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145283] pci 0000:00:0e.2: reg 0x14: [io  0xbc00-0xbc03]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145289] pci 0000:00:0e.2: reg 0x18: [io  0xb800-0xb807]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145294] pci 0000:00:0e.2: reg 0x1c: [io  0xb400-0xb403]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145300] pci 0000:00:0e.2: reg 0x20: [io  0xb000-0xb00f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145305] pci 0000:00:0e.2: reg 0x24: [mem 0xdfffb000-0xdfffbfff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145410] pci 0000:00:0f.0: [10de:0370] type 01 class 0x060401
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145480] pci 0000:00:0f.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145522] pci 0000:00:0f.1: [10de:0371] type 00 class 0x040300
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145534] pci 0000:00:0f.1: reg 0x10: [mem 0xdfff0000-0xdfff3fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145587] pci 0000:00:0f.1: PME# supported from D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145632] pci 0000:00:0f.1: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145684] pci 0000:00:11.0: [10de:0373] type 00 class 0x068000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145698] pci 0000:00:11.0: reg 0x10: [mem 0xdfffa000-0xdfffafff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145704] pci 0000:00:11.0: reg 0x14: [io  0xac00-0xac07]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145709] pci 0000:00:11.0: reg 0x18: [mem 0xdfff9000-0xdfff90ff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145715] pci 0000:00:11.0: reg 0x1c: [mem 0xdfff8000-0xdfff800f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145760] pci 0000:00:11.0: supports D1 D2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145761] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145808] pci 0000:00:11.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145856] pci 0000:00:12.0: [10de:0373] type 00 class 0x068000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145875] pci 0000:00:12.0: reg 0x10: [mem 0xdfff7000-0xdfff7fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145881] pci 0000:00:12.0: reg 0x14: [io  0xa800-0xa807]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145886] pci 0000:00:12.0: reg 0x18: [mem 0xdfff6000-0xdfff60ff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145892] pci 0000:00:12.0: reg 0x1c: [mem 0xdfff5000-0xdfff500f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145936] pci 0000:00:12.0: supports D1 D2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145938] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.145986] pci 0000:00:12.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146031] pci 0000:00:15.0: [10de:0374] type 01 class 0x060400
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146076] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146120] pci 0000:00:15.0: System wakeup disabled by ACPI
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146232] pci 0000:01:00.0: [10de:0191] type 00 class 0x030000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146241] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146250] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146258] pci 0000:01:00.0: reg 0x1c: [mem 0xda000000-0xdbffffff 64bit]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146264] pci 0000:01:00.0: reg 0x24: [io  0x9c00-0x9c7f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146270] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146335] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146343] pci 0000:00:02.0: PCI bridge to [bus 01]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146349] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146353] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146358] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146419] pci 0000:00:04.0: PCI bridge to [bus 02]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146488] pci 0000:00:0f.0: PCI bridge to [bus 03] (subtractive decode)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146494] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146496] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146498] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146500] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146501] pci 0000:00:0f.0:   bridge window [mem 0xbff00000-0xfebfffff] (subtractive decode)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146556] pci 0000:04:00.0: [197b:2363] type 00 class 0x010601
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146627] pci 0000:04:00.0: reg 0x24: [mem 0xdfefe000-0xdfefffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146683] pci 0000:04:00.0: PME# supported from D3hot
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146740] pci 0000:04:00.1: [197b:2363] type 00 class 0x010185
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146757] pci 0000:04:00.1: reg 0x10: [io  0x8c00-0x8c07]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146765] pci 0000:04:00.1: reg 0x14: [io  0x8800-0x8803]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146773] pci 0000:04:00.1: reg 0x18: [io  0x8400-0x8407]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146781] pci 0000:04:00.1: reg 0x1c: [io  0x8000-0x8003]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146790] pci 0000:04:00.1: reg 0x20: [io  0x7c00-0x7c0f]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146879] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146889] pci 0000:00:15.0: PCI bridge to [bus 04]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146893] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.146896] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147285] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147331] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147375] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147420] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147465] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147509] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147553] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 *11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147597] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 *10 11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147641] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147684] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147728] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147778] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147821] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147866] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147910] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.147955] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148009] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148058] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148131] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148198] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148263] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148327] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148391] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148455] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148520] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148584] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148648] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148713] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148777] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148842] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148906] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.148971] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149035] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149099] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149164] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149229] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149293] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149357] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0, disabled.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] vgaarb: setting as boot device: PCI:0000:01:00.0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] vgaarb: loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] vgaarb: bridge control possible 0000:01:00.0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] SCSI subsystem initialized
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] libata version 3.00 loaded.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] ACPI: bus type USB registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] usbcore: registered new interface driver usbfs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] usbcore: registered new interface driver hub
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] usbcore: registered new device driver usb
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.149472] PCI: Using ACPI for IRQ routing
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156650] PCI: pci_cache_line_size set to 64 bytes
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156716] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156717] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156813] NetLabel: Initializing
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156815] NetLabel:  domain hash size = 128
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156817] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156830] NetLabel:  unlabeled traffic allowed by default
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156857] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156857] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.156857] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.160040] Switched to clocksource hpet
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166389] AppArmor: AppArmor Filesystem Enabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166456] pnp: PnP ACPI init
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166548] system 00:00: [io  0x1000-0x107f] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166551] system 00:00: [io  0x1080-0x10ff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166554] system 00:00: [io  0x1400-0x147f] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166556] system 00:00: [io  0x1480-0x14ff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166559] system 00:00: [io  0x1800-0x187f] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166562] system 00:00: [io  0x1880-0x18ff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166565] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166671] system 00:01: [io  0x04d0-0x04d1] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166675] system 00:01: [io  0x0295-0x0314] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166677] system 00:01: [io  0x0880-0x088f] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166680] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166734] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.166893] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167357] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167362] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167483] system 00:05: [mem 0x000d0000-0x000d3fff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167487] system 00:05: [mem 0x000d9000-0x000dbfff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167490] system 00:05: [mem 0x000f0000-0x000fbfff] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167493] system 00:05: [mem 0x000fc000-0x000fffff] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167495] system 00:05: [mem 0xbfef0000-0xbfefffff] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167498] system 00:05: [mem 0xffff0000-0xffffffff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167501] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167504] system 00:05: [mem 0x00100000-0xbfeeffff] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167507] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167509] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167512] system 00:05: [mem 0xfeff0000] has been reserved
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167515] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.167523] pnp: PnP ACPI: found 6 devices
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176251] pci 0000:01:00.0: BAR 6: assigned [mem 0xdd000000-0xdd01ffff pref]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176255] pci 0000:00:02.0: PCI bridge to [bus 01]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176259] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176264] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176269] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176275] pci 0000:00:04.0: PCI bridge to [bus 02]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176286] pci 0000:00:0f.0: PCI bridge to [bus 03]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176293] pci 0000:00:15.0: PCI bridge to [bus 04]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176296] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176300] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176306] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176308] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176309] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176311] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176313] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176315] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176316] pci_bus 0000:01: resource 1 [mem 0xda000000-0xddffffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176318] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176320] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176321] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176323] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176325] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176326] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xfebfffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176328] pci_bus 0000:04: resource 0 [io  0x7000-0x8fff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176330] pci_bus 0000:04: resource 1 [mem 0xdfe00000-0xdfefffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176355] NET: Registered protocol family 2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176567] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.176818] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.177169] TCP: Hash tables configured (established 65536 bind 65536)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.177210] TCP: reno registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.177221] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.177274] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.177352] NET: Registered protocol family 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.177689] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.248353] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.248568] pci 0000:01:00.0: Video device with shadowed ROM
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.248571] pci 0000:04:00.0: async suspend disabled to avoid multi-function power-on ordering issue
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.248576] pci 0000:04:00.1: async suspend disabled to avoid multi-function power-on ordering issue
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.248581] PCI: CLS 64 bytes, default 64
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.248631] Trying to unpack rootfs image as initramfs...
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.631903] Freeing initrd memory: 26192K (ffff880034cc8000 - ffff88003665c000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.631945] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.631949] software IO TLB [mem 0xbbef0000-0xbfef0000] (64MB) mapped at [ffff8800bbef0000-ffff8800bfeeffff]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632261] microcode: CPU0 sig=0x1067a, pf=0x10, revision=0xa07
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632277] microcode: CPU1 sig=0x1067a, pf=0x10, revision=0xa07
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632296] microcode: CPU2 sig=0x1067a, pf=0x10, revision=0xa07
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632316] microcode: CPU3 sig=0x1067a, pf=0x10, revision=0xa07
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632395] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632447] Scanning for low memory corruption every 60 seconds
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632724] futex hash table entries: 1024 (order: 4, 65536 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632742] Initialise system trusted keyring
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632762] audit: initializing netlink subsys (disabled)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.632781] audit: type=2000 audit(1455511519.632:1): initialized
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.633090] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.634759] zpool: loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.634761] zbud: loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.634920] VFS: Disk quotas dquot_6.5.2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.634956] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.635461] fuse init (API version 7.23)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.635605] Key type big_key registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636449] Key type asymmetric registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636453] Asymmetric key parser 'x509' registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636494] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636573] io scheduler noop registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636577] io scheduler deadline registered (default)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636608] io scheduler cfq registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.636912] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637183] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637359] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637362] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637367] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637385] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637390] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637403] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637406] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637408] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637412] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637418] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637435] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637468] vesafb: mode is 640x480x32, linelength=2560, pages=0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637471] vesafb: scrolling: redraw
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.637473] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.642243] vesafb: framebuffer at 0xdb000000, mapped to 0xffffc90010e80000, using 1216k, total 1216k
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.643528] Console: switching to colour frame buffer device 80x30
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.644753] fb0: VESA VGA frame buffer device
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.644803] intel_idle: does not run on family 6 model 23
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.644878] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.644930] ACPI: Power Button [PWRB]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.645001] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.646605] ACPI: Power Button [PWRF]
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.647728] GHES: HEST is not enabled!
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.648673] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.651312] Linux agpgart interface v0.103
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.653585] brd: module loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.655092] loop: module loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.656128] libphy: Fixed MDIO Bus: probed
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.656932] tun: Universal TUN/TAP device driver, 1.6
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.657735] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.658617] PPP generic driver version 2.4.2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.659511] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.660363] ehci-pci: EHCI PCI platform driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.661334] ehci-pci 0000:00:0b.1: EHCI Host Controller
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.662183] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.663883] ehci-pci 0000:00:0b.1: debug port 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.664793] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.664808] ehci-pci 0000:00:0b.1: irq 22, io mem 0xdfffe000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.676028] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.676919] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.677777] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.679465] usb usb1: Product: EHCI Host Controller
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.680325] usb usb1: Manufacturer: Linux 3.19.0-49-generic ehci_hcd
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.681168] usb usb1: SerialNumber: 0000:00:0b.1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.682113] hub 1-0:1.0: USB hub found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.682929] hub 1-0:1.0: 10 ports detected
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.683899] ehci-platform: EHCI generic platform driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.684717] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.685513] ohci-pci: OHCI PCI platform driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.686401] ohci-pci 0000:00:0b.0: OHCI PCI host controller
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.687186] ohci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.688789] ohci-pci 0000:00:0b.0: irq 23, io mem 0xdffff000
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.746037] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.746856] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.748505] usb usb2: Product: OHCI PCI host controller
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.749349] usb usb2: Manufacturer: Linux 3.19.0-49-generic ohci_hcd
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.750198] usb usb2: SerialNumber: 0000:00:0b.0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.751140] hub 2-0:1.0: USB hub found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.751966] hub 2-0:1.0: 10 ports detected
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.752964] ohci-platform: OHCI generic platform driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.753782] uhci_hcd: USB Universal Host Controller Interface driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.754652] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.755473] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.757786] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.758748] mousedev: PS/2 mouse device common for all mice
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.759745] rtc_cmos 00:02: RTC can wake from S4
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.760743] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.761606] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.763279] i2c /dev entries driver
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.764208] device-mapper: uevent: version 1.0.3
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.765121] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.766854] ledtrig-cpu: registered to indicate activity on CPUs
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.767965] PCCT header not found.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.768934] TCP: cubic registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.769896] NET: Registered protocol family 10
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.771007] NET: Registered protocol family 17
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.771841] Key type dns_resolver registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.773028] Loading compiled-in X.509 certificates
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.774685] Loaded X.509 cert 'Magrathea: Glacier signing key: a932dc237895a44d3959bf91a3566a20ee211f37'
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.776375] registered taskstats version 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.778891] Key type trusted registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.782638] Key type encrypted registered
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.783427] AppArmor: AppArmor sha1 policy hashing enabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.784257] ima: No TPM chip found, activating TPM-bypass!
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.785089] evm: HMAC attrs: 0x1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.786234] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.787926]   Magic number: 4:758:767
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.788873] rtc_cmos 00:02: setting system clock to 2016-02-15 04:45:20 UTC (1455511520)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.790601] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.791439] EDD information not available.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.792327] PM: Hibernation image not present or could not be loaded.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.792797] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.794496] Write protecting the kernel read-only data: 12288k
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.795622] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.797551] Freeing unused kernel memory: 336K (ffff880001bac000 - ffff880001c00000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.812658] systemd-udevd[120]: starting version 204
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.837436] pata_amd 0000:00:0d.0: version 0.4.1
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.838032] scsi host0: pata_amd
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.839070] scsi host1: pata_amd
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.839990] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.840936] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.842056] [drm] Initialized drm 1.1.0 20060810
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.843106] sata_nv 0000:00:0e.0: version 3.5
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.843360] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.844293] sata_nv 0000:00:0e.0: Using SWNCQ mode
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.845704] scsi host2: sata_nv
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.846716] scsi host3: sata_nv
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.847615] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.848536] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.849632] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.850522] sata_nv 0000:00:0e.1: Using SWNCQ mode
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.852885] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.854193] scsi host4: sata_nv
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.855203] scsi host5: pata_jmicron
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.855205] scsi host6: sata_nv
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.855261] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.855262] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.855285] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.855492] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.860977] wmi: Mapper loaded
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.861019] scsi host7: pata_jmicron
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.861073] ata7: PATA max UDMA/100 cmd 0x8c00 ctl 0x8800 bmdma 0x7c00 irq 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.861073] ata8: PATA max UDMA/100 cmd 0x8400 ctl 0x8000 bmdma 0x7c08 irq 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.861088] ahci 0000:04:00.0: version 3.0
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.861284] ACPI: PCI Interrupt Link [AXV8] enabled at IRQ 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.876513] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.878003] ahci 0000:04:00.0: flags: 64bit ncq led clo pmp pio
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.880160] scsi host8: ahci
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.881057] scsi host9: ahci
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.881918] ata9: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.883507] ata10: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 16
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.885380] checking generic (db000000 130000) vs hw (c0000000 10000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.885384] checking generic (db000000 130000) vs hw (da000000 2000000)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.885386] fb: switching to nouveaufb from VESA VGA
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.886237] Console: switching to colour dummy device 80x25
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.886710] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x450100a2
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.886718] nouveau  [  DEVICE][0000:01:00.0] Chipset: G80 (NV50)
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.886720] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.994243] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.994327] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
Feb 14 22:45:42 kazz-u0a1 kernel: [    0.994330] nouveau  [   VBIOS][0000:01:00.0] version 60.80.0a.00.00
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.007006] ata2: port disabled--ignoring
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.014509] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.014534] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR3
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.014537] nouveau  [     PFB][0000:01:00.0] RAM size: 768 MiB
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.014539] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 3142 tags
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.047254] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.047264] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.047267] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067127] nouveau  [     CLK][0000:01:00.0] 20: core 576 MHz shader 1350 MHz memory 900 MHz
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067160] nouveau  [     CLK][0000:01:00.0] --: core 198 MHz shader 1188 MHz memory 396 MHz
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067327] [TTM] Zone  kernel: Available graphics memory: 4087460 kiB
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067330] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067332] [TTM] Initializing pool allocator
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067338] [TTM] Initializing DMA pool allocator
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067348] nouveau  [     DRM] VRAM: 768 MiB
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067350] nouveau  [     DRM] GART: 1048576 MiB
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067353] nouveau  [     DRM] BIT table 'A' not found
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067356] nouveau  [     DRM] TMDS table version 2.0
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067358] nouveau  [     DRM] DCB version 4.0
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067361] nouveau  [     DRM] DCB outp 00: 04000320 00000028
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067364] nouveau  [     DRM] DCB outp 01: 01000322 00000030
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067366] nouveau  [     DRM] DCB outp 02: 02011310 00000028
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067368] nouveau  [     DRM] DCB outp 03: 02011312 00000030
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067370] nouveau  [     DRM] DCB outp 04: 010223f1 00c1c020
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067372] nouveau  [     DRM] DCB conn 00: 1030
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067375] nouveau  [     DRM] DCB conn 01: 2130
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067377] nouveau  [     DRM] DCB conn 02: 0210
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067379] nouveau  [     DRM] DCB conn 03: 0211
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.067381] nouveau  [     DRM] DCB conn 04: 0213
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.075053] nouveau W[     DRM] failed to create encoder 0/1/0: -19
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.075057] nouveau W[     DRM] TV-1 has no encoders, removing
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.075084] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.075086] [drm] Driver supports precise vblank timestamp query.
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.085569] nouveau  [     DRM] MM: using M2MF for buffer copies
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.149897] nouveau  [     DRM] allocated 1024x768 fb: 0x70000, bo ffff880232496000
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.149967] fbcon: nouveaufb (fb0) is primary device
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.204055] ata10: SATA link down (SStatus 0 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.204096] ata9: SATA link down (SStatus 0 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.216945] Console: switching to colour frame buffer device 128x48
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.217658] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.217685] nouveau 0000:01:00.0: registered panic notifier
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.220034] [drm] Initialized nouveau 1.2.1 20120801 for 0000:01:00.0 on minor 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.316026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.320029] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.328299] ata5.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.328309] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.340143] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.344295] ata5.00: configured for UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.372140] ata3.00: configured for UDMA/100
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.374017] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.380504] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:04:4b:17:22:9a
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.380514] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.380789] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.390211] sr 2:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.390222] cdrom: Uniform CD-ROM driver Revision: 3.20
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.390409] sr 2:0:0:0: Attached scsi CD-ROM sr0
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.390480] sr 2:0:0:0: Attached scsi generic sg0 type 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.632017] tsc: Refined TSC clocksource calibration: 2999.958 MHz
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.856025] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.872401] ata4.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.872608] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.889172] ata4.00: configured for UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.889441] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 3B01 PQ: 0 ANSI: 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.889818] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.889822] sd 3:0:0:0: Attached scsi generic sg1 type 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.889931] scsi 4:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.890117] sd 4:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.890134] sd 4:0:0:0: Attached scsi generic sg2 type 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.890164] sd 4:0:0:0: [sdb] Write Protect is off
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.890165] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.890188] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.894747] sd 3:0:0:0: [sda] Write Protect is off
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.895493] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.895519] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.904492] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x50ef @ 1, addr 00:04:4b:17:22:9b
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.904689] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.905569] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.906098] sata_nv 0000:00:0e.2: Using SWNCQ mode
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.910754] scsi host10: sata_nv
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.911113] scsi host11: sata_nv
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.911622] ata11: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.912422] ata12: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.920469]  sda: sda1 sda2 < sda5 >
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.921053] sd 3:0:0:0: [sda] Attached SCSI disk
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.924202]  sdb: sdb1 sdb9
Feb 14 22:45:42 kazz-u0a1 kernel: [    1.924660] sd 4:0:0:0: [sdb] Attached SCSI disk
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.356028] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.364283] ata6.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.364536] ata6.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.380038] ata11: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.380297] ata6.00: configured for UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.380881] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.381870] sd 6:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.381903] sd 6:0:0:0: Attached scsi generic sg3 type 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.383449] sd 6:0:0:0: [sdc] Write Protect is off
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.384248] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.384263] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.388309] ata11.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.388589] ata11.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.404292] ata11.00: configured for UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.431508]  sdc: sdc1 sdc9
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.431934] sd 6:0:0:0: [sdc] Attached SCSI disk
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.547212] scsi 10:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.547584] sd 10:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.548076] sd 10:0:0:0: Attached scsi generic sg4 type 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.548102] sd 10:0:0:0: [sdd] Write Protect is off
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.548104] sd 10:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.548129] sd 10:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.588260]  sdd: sdd1 sdd9
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.588754] sd 10:0:0:0: [sdd] Attached SCSI disk
Feb 14 22:45:42 kazz-u0a1 kernel: [    2.632104] Switched to clocksource tsc
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.016019] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.024275] ata12.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.024560] ata12.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.040271] ata12.00: configured for UDMA/133
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.040601] scsi 11:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.041177] sd 11:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.041229] sd 11:0:0:0: Attached scsi generic sg5 type 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.042738] sd 11:0:0:0: [sde] Write Protect is off
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.043538] sd 11:0:0:0: [sde] Mode Sense: 00 3a 00 00
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.043552] sd 11:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.081279]  sde: sde1 sde9
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.081708] sd 11:0:0:0: [sde] Attached SCSI disk
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.160048] random: nonblocking pool is initialized
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.848026] floppy0: no floppy controllers found
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.931522] md: linear personality registered for level -1
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.933795] md: multipath personality registered for level -4
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.936036] md: raid0 personality registered for level 0
Feb 14 22:45:42 kazz-u0a1 kernel: [    3.938570] md: raid1 personality registered for level 1
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.008021] raid6: sse2x1    4958 MB/s
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.076023] raid6: sse2x2    5629 MB/s
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.144013] raid6: sse2x4    8779 MB/s
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.144021] raid6: using algorithm sse2x4 (8779 MB/s)
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.144025] raid6: using ssse3x2 recovery algorithm
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.145139] xor: measuring software checksum speed
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.184008]    prefetch64-sse: 12517.000 MB/sec
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.224007]    generic_sse: 11040.000 MB/sec
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.224011] xor: using function: prefetch64-sse (12517.000 MB/sec)
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.225066] async_tx: api initialized (async)
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.231432] md: raid6 personality registered for level 6
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.231437] md: raid5 personality registered for level 5
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.231441] md: raid4 personality registered for level 4
Feb 14 22:45:42 kazz-u0a1 kernel: [    4.236352] md: raid10 personality registered for level 10
Feb 14 22:45:42 kazz-u0a1 kernel: [    9.263571] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Feb 14 22:45:42 kazz-u0a1 kernel: [    9.263577] EXT4-fs (dm-0): write access will be enabled during recovery
Feb 14 22:45:42 kazz-u0a1 kernel: [   11.193386] EXT4-fs (dm-0): orphan cleanup on readonly fs
Feb 14 22:45:42 kazz-u0a1 kernel: [   11.193453] EXT4-fs (dm-0): 1 orphan inode deleted
Feb 14 22:45:42 kazz-u0a1 kernel: [   11.193457] EXT4-fs (dm-0): recovery complete
Feb 14 22:45:42 kazz-u0a1 kernel: [   11.256043] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Feb 14 22:45:42 kazz-u0a1 kernel: [   12.908629] zavl: module license 'CDDL' taints kernel.
Feb 14 22:45:42 kazz-u0a1 kernel: [   12.908641] Disabling lock debugging due to kernel taint
Feb 14 22:45:42 kazz-u0a1 kernel: [   12.908668] zavl: module verification failed: signature and/or  required key missing - tainting kernel
Feb 14 22:45:42 kazz-u0a1 kernel: [   12.942447] SPL: Loaded module v0.6.5.4-1~trusty
Feb 14 22:45:42 kazz-u0a1 kernel: [   13.291736] ZFS: Loaded module v0.6.5.4-1~trusty, ZFS pool version 5000, ZFS filesystem version 5
Feb 14 22:45:42 kazz-u0a1 kernel: [   19.594099] SPL: using hostid 0x007f0101
Feb 14 22:45:42 kazz-u0a1 kernel: [   22.128903] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Feb 14 22:45:42 kazz-u0a1 kernel: [   22.197443] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
Feb 14 22:45:42 kazz-u0a1 kernel: [   22.202931] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
Feb 14 22:45:42 kazz-u0a1 kernel: [   22.928374] systemd-udevd[1900]: starting version 204
Feb 14 22:45:42 kazz-u0a1 kernel: [   22.950303] lp: driver loaded but no devices found
Feb 14 22:45:42 kazz-u0a1 dbus[1924]: [system] AppArmor D-Bus mediation is enabled
Feb 14 22:45:42 kazz-u0a1 rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.080341] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.087591] i2c i2c-4: nForce2 SMBus adapter at 0xf400
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.087753] i2c i2c-5: nForce2 SMBus adapter at 0xf000
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.126209] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.126219] snd_hda_intel 0000:00:0f.1: Disabling MSI
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282139] audit: type=1400 audit(1455511542.987:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=2026 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282145] audit: type=1400 audit(1455511542.987:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2026 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282149] audit: type=1400 audit(1455511542.987:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2026 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282163] audit: type=1400 audit(1455511542.987:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2028 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282172] audit: type=1400 audit(1455511542.987:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2028 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282176] audit: type=1400 audit(1455511542.987:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2028 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282187] audit: type=1400 audit(1455511542.987:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2029 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282193] audit: type=1400 audit(1455511542.987:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2029 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282198] audit: type=1400 audit(1455511542.987:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2029 comm="apparmor_parser"
Feb 14 22:45:42 kazz-u0a1 kernel: [   23.282501] audit: type=1400 audit(1455511542.987:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2026 comm="apparmor_parser"
Feb 14 22:45:43 kazz-u0a1 failsafe: Failsafe of 120 seconds reached.
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.621677] forcedeth 0000:00:11.0 eth0: MSI enabled
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864016] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864020] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864023] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864026] sound hdaudioC0D0:    mono: mono_out=0x0
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864028] sound hdaudioC0D0:    dig-out=0x11/0x1e
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864030] sound hdaudioC0D0:    inputs:
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864033] sound hdaudioC0D0:      Front Mic=0x19
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864036] sound hdaudioC0D0:      Rear Mic=0x18
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864039] sound hdaudioC0D0:      Line=0x1a
Feb 14 22:45:43 kazz-u0a1 kernel: [   23.864041] sound hdaudioC0D0:    dig-in=0x1f
Feb 14 22:45:44 kazz-u0a1 kernel: [   24.862036] init: failsafe main process (2120) killed by TERM signal
Feb 14 22:45:45 kazz-u0a1 cron[2441]: (CRON) INFO (pidfile fd = 3)
Feb 14 22:45:45 kazz-u0a1 acpid: starting up with netlink and the input layer
Feb 14 22:45:45 kazz-u0a1 cron[2552]: (CRON) STARTUP (fork ok)
Feb 14 22:45:45 kazz-u0a1 cron[2552]: (CRON) INFO (Running @reboot jobs)
Feb 14 22:45:45 kazz-u0a1 acpid: 1 rule loaded
Feb 14 22:45:45 kazz-u0a1 acpid: waiting for events: event logging is off
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721195] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input3
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721281] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input4
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721351] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721424] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721794] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721864] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.721936] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
Feb 14 22:45:45 kazz-u0a1 kernel: [   25.724729] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
Feb 14 22:45:45 kazz-u0a1 kernel: [   26.092032] floppy0: no floppy controllers found
Feb 14 22:45:45 kazz-u0a1 kernel: [   26.201707] init: samba-ad-dc main process (2550) terminated with status 1
Feb 14 22:45:48 kazz-u0a1 kernel: [   28.325548] Ebtables v2.0 registered
Feb 14 22:45:48 kazz-u0a1 kernel: [   28.387501] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 14 22:45:48 kazz-u0a1 kernel: [   28.394605] ip6_tables: (C) 2000-2006 Netfilter Core Team
Feb 14 22:45:48 kazz-u0a1 kernel: [   28.703337] init: plymouth-upstart-bridge main process ended, respawning
Feb 14 22:45:48 kazz-u0a1 /etc/mysql/debian-start[2871]: Upgrading MySQL tables if necessary.
Feb 14 22:45:48 kazz-u0a1 /etc/mysql/debian-start[2875]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Feb 14 22:45:48 kazz-u0a1 /etc/mysql/debian-start[2875]: Looking for 'mysql' as: /usr/bin/mysql
Feb 14 22:45:48 kazz-u0a1 /etc/mysql/debian-start[2875]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Feb 14 22:45:48 kazz-u0a1 /etc/mysql/debian-start[2875]: This installation of MySQL is already upgraded to 5.5.47, use --force if you still need to run mysql_upgrade
Feb 14 22:45:48 kazz-u0a1 /etc/mysql/debian-start[2886]: Checking for insecure root accounts.
Feb 14 22:45:49 kazz-u0a1 /etc/mysql/debian-start[2891]: Triggering myisam-recover for all MyISAM tables
Feb 14 22:45:50 kazz-u0a1 kernel: [   30.616073] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
Feb 14 22:45:50 kazz-u0a1 kernel: [   30.736269] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Feb 14 22:45:50 kazz-u0a1 dnsmasq[3036]: started, version 2.68 cachesize 150
Feb 14 22:45:50 kazz-u0a1 dnsmasq[3036]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Feb 14 22:45:50 kazz-u0a1 dnsmasq-dhcp[3036]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h
Feb 14 22:45:50 kazz-u0a1 dnsmasq-dhcp[3036]: DHCP, sockets bound exclusively to interface virbr0
Feb 14 22:45:50 kazz-u0a1 dnsmasq[3036]: reading /etc/resolv.conf
Feb 14 22:45:50 kazz-u0a1 dnsmasq[3036]: using nameserver 192.168.5.254#53
Feb 14 22:45:50 kazz-u0a1 dnsmasq[3036]: read /etc/hosts - 5 addresses
Feb 14 22:45:50 kazz-u0a1 dnsmasq[3036]: read /var/lib/libvirt/dnsmasq/default.addnhosts - 0 addresses
Feb 14 22:45:50 kazz-u0a1 dnsmasq-dhcp[3036]: read /var/lib/libvirt/dnsmasq/default.hostsfile
Feb 14 22:45:47 kazz-u0a1 ntpdate[2264]: step time server 91.189.89.199 offset -3.943272 sec
Feb 14 22:46:02 kazz-u0a1 ntpdate[3191]: adjust time server 91.189.89.199 offset 0.001912 sec
Feb 14 22:47:28 kazz-u0a1 kernel: [  132.733883] cgroup: systemd-logind (2017) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
Feb 14 22:47:28 kazz-u0a1 kernel: [  132.733886] cgroup: "memory" requires setting use_hierarchy to 1 on the root
Feb 14 22:51:50 kazz-u0a1 postfix/sendmail[3499]: fatal: open /etc/postfix/main.cf: No such file or directory
Feb 14 22:53:53 kazz-u0a1 kernel: [  517.237262] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Feb 14 23:09:01 kazz-u0a1 CRON[4219]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 14 23:17:01 kazz-u0a1 CRON[4530]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 14 23:39:01 kazz-u0a1 CRON[5297]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 00:09:01 kazz-u0a1 CRON[6338]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 00:17:01 kazz-u0a1 CRON[6628]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 00:39:01 kazz-u0a1 CRON[7370]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 01:09:02 kazz-u0a1 CRON[8411]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 01:17:01 kazz-u0a1 CRON[8692]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 01:39:01 kazz-u0a1 CRON[9464]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340036] ata4: EH in SWNCQ mode,QC:qc_active 0x7FFFFFFF sactive 0x7FFFFFFF
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340056] ata4: SWNCQ:qc_active 0x20000000 defer_bits 0x5FFFFFFF last_issue_tag 0x1d
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340056]   dhfis 0x20000000 dmafis 0x0 sdbfis 0x0
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340068] ata4: ATA_REG 0x41 ERR_REG 0x4
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340073] ata4: tag : dhfis dmafis sdbfis sactive
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340079] ata4: tag 0x1d: 1 0 0 1
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340090] ata4.00: exception Emask 0x1 SAct 0x7fffffff SErr 0x0 action 0x6 frozen
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340097] ata4.00: Ata error. fis:0x41
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340104] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340115] ata4.00: cmd 61/08:00:98:5b:38/00:00:00:00:00/40 tag 0 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340115]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340126] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340131] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340136] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340145] ata4.00: cmd 61/10:08:d0:5b:38/00:00:00:00:00/40 tag 1 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340145]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340156] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340161] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340166] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340174] ata4.00: cmd 61/08:10:18:5c:38/00:00:00:00:00/40 tag 2 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340174]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340189] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340192] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340196] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340201] ata4.00: cmd 61/08:18:48:5c:38/00:00:00:00:00/40 tag 3 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340201]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340209] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340212] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340215] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340221] ata4.00: cmd 61/08:20:70:5c:38/00:00:00:00:00/40 tag 4 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340221]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340229] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340232] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340235] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340241] ata4.00: cmd 61/08:28:d8:5c:38/00:00:00:00:00/40 tag 5 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340241]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340248] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340252] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340255] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340261] ata4.00: cmd 61/10:30:e8:5c:38/00:00:00:00:00/40 tag 6 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340261]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340268] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340272] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340275] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340280] ata4.00: cmd 61/08:38:c8:5d:38/00:00:00:00:00/40 tag 7 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340280]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.341580] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.342320] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.343031] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.343740] ata4.00: cmd 61/08:40:d8:5d:38/00:00:00:00:00/40 tag 8 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.343740]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.345163] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.345858] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.346556] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.347251] ata4.00: cmd 61/08:48:f8:5d:38/00:00:00:00:00/40 tag 9 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.347251]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.348668] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.349373] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.350061] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.350751] ata4.00: cmd 61/08:50:20:5e:38/00:00:00:00:00/40 tag 10 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.350751]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.352165] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.352870] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.353556] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.354253] ata4.00: cmd 61/18:58:40:5e:38/00:00:00:00:00/40 tag 11 ncq 12288 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.354253]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.355676] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.356395] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.357081] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.357782] ata4.00: cmd 61/08:60:68:5e:38/00:00:00:00:00/40 tag 12 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.357782]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.359210] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.359927] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.360632] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.361329] ata4.00: cmd 61/18:68:d8:5e:38/00:00:00:00:00/40 tag 13 ncq 12288 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.361329]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.362766] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.363486] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.364196] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.364898] ata4.00: cmd 61/08:70:30:5f:38/00:00:00:00:00/40 tag 14 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.364898]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.366339] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.367067] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.367766] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.368484] ata4.00: cmd 61/08:78:40:5f:38/00:00:00:00:00/40 tag 15 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.368484]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.369930] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.370657] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.371361] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.372082] ata4.00: cmd 61/08:80:a8:5f:38/00:00:00:00:00/40 tag 16 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.372082]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.373539] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.374265] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.374976] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.375701] ata4.00: cmd 61/28:88:c0:5f:38/00:00:00:00:00/40 tag 17 ncq 20480 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.375701]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.377162] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.377899] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.378605] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.379324] ata4.00: cmd 61/10:90:00:60:38/00:00:00:00:00/40 tag 18 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.379324]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.380798] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.381530] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.382242] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.382962] ata4.00: cmd 61/10:98:28:60:38/00:00:00:00:00/40 tag 19 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.382962]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.384432] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.385172] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.385887] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.386606] ata4.00: cmd 61/08:a0:48:60:38/00:00:00:00:00/40 tag 20 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.386606]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.388077] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.388818] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.389529] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.390248] ata4.00: cmd 61/08:a8:58:60:38/00:00:00:00:00/40 tag 21 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.390248]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.391712] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.392460] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.393171] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.393890] ata4.00: cmd 61/20:b0:68:60:38/01:00:00:00:00/40 tag 22 ncq 147456 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.393890]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.395356] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.396107] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.396817] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.397538] ata4.00: cmd 61/10:b8:90:61:38/00:00:00:00:00/40 tag 23 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.397538]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.398996] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.399742] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.400467] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.401181] ata4.00: cmd 61/08:c0:b0:61:38/00:00:00:00:00/40 tag 24 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.401181]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.402641] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.403388] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.404112] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.404827] ata4.00: cmd 61/30:c8:c0:61:38/00:00:00:00:00/40 tag 25 ncq 24576 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.404827]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.406294] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.407040] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.407756] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.408482] ata4.00: cmd 61/48:d0:f8:61:38/00:00:00:00:00/40 tag 26 ncq 36864 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.408482]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.409946] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.410692] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.411408] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.412136] ata4.00: cmd 61/08:d8:50:62:38/00:00:00:00:00/40 tag 27 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.412136]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.413600] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.414345] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.415063] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.415789] ata4.00: cmd 61/08:e0:f8:62:38/00:00:00:00:00/40 tag 28 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.415789]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.417259] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.418002] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.418720] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.419440] ata4.00: cmd 61/08:e8:20:5b:38/00:00:00:00:00/40 tag 29 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.419440]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.420914] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.421658] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.422376] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.423098] ata4.00: cmd 61/08:f0:48:5b:38/00:00:00:00:00/40 tag 30 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.423098]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.424575] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.425319] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.426036] ata4: hard resetting link
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.426038] ata4: nv: skipping hardreset on occupied port
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.892020] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.908814] ata4.00: configured for UDMA/133
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.908851] ata4: EH complete
Feb 15 02:09:01 kazz-u0a1 CRON[12505]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 02:17:01 kazz-u0a1 CRON[12788]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 02:39:01 kazz-u0a1 CRON[13532]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 03:09:01 kazz-u0a1 CRON[14566]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 03:17:01 kazz-u0a1 CRON[14844]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 03:39:01 kazz-u0a1 CRON[15598]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 04:09:01 kazz-u0a1 CRON[16629]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 04:17:01 kazz-u0a1 CRON[16918]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 04:39:01 kazz-u0a1 CRON[17683]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 05:09:01 kazz-u0a1 CRON[18724]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 05:17:01 kazz-u0a1 CRON[19009]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 05:39:01 kazz-u0a1 CRON[19769]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 06:09:02 kazz-u0a1 CRON[20784]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 15 06:17:01 kazz-u0a1 CRON[21081]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 15 06:25:01 kazz-u0a1 CRON[21364]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Feb 15 06:39:01 kazz-u0a1 CRON[21886]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))

```

I see what I think are error messages starting around 2am (I've not looked at the server today until just an hour or so ago). I'm not seeing what caused the issue other than as a result of something a cron job requested?

Thanks!

---

### Post by sandyd on 2016-02-15
Hmm.

Nothing in today's dmesg, we may have to go back in dmesg's logs. What's the last date that you had the issue on your machine?

About the logs,
Generally, the logs reside in /var/log, though when the log reaches a certain size, it is rotated by a software called logrotate. The old log is moved to *logname*.0 . Depending on the settings, even older logs such as *logname*.1 may be compressed with gzip (the files you see with the .gz extention) to save space, making them named *logname*.1.gz

By default, Ubuntu is unlike Windows, it has drivers built into the kernel. Most things seem to work with a some exceptions.

That being said, could you post the output of
```

lshw -C network
```

---

### Post by kazz2 on 2016-02-15
That command suggested I run as a super-user. Putting sudo in front didn't get any final output. The line originally said PCI (sysfs) and then  some other characters displayed. But, ultimately, there was no output, just another system prompt line. That makes me wonder if the GPU driver I just installed is creating a problem!

---

### Post by sandyd on 2016-02-15
Well, now we have the errors
```
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340036] ata4: EH in SWNCQ mode,QC:qc_active 0x7FFFFFFF sactive 0x7FFFFFFF
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340056] ata4: SWNCQ:qc_active 0x20000000 defer_bits 0x5FFFFFFF last_issue_tag 0x1d
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340056]   dhfis 0x20000000 dmafis 0x0 sdbfis 0x0
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340068] ata4: ATA_REG 0x41 ERR_REG 0x4
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340073] ata4: tag : dhfis dmafis sdbfis sactive
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340079] ata4: tag 0x1d: 1 0 0 1
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340090] ata4.00: exception Emask 0x1 SAct 0x7fffffff SErr 0x0 action 0x6 frozen
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340097] ata4.00: Ata error. fis:0x41
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340104] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340115] ata4.00: cmd 61/08:00:98:5b:38/00:00:00:00:00/40 tag 0 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340115]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340126] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340131] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340136] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340145] ata4.00: cmd 61/10:08:d0:5b:38/00:00:00:00:00/40 tag 1 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340145]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340156] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340161] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340166] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340174] ata4.00: cmd 61/08:10:18:5c:38/00:00:00:00:00/40 tag 2 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340174]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340189] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340192] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340196] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340201] ata4.00: cmd 61/08:18:48:5c:38/00:00:00:00:00/40 tag 3 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340201]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340209] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340212] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340215] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340221] ata4.00: cmd 61/08:20:70:5c:38/00:00:00:00:00/40 tag 4 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340221]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340229] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340232] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340235] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340241] ata4.00: cmd 61/08:28:d8:5c:38/00:00:00:00:00/40 tag 5 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340241]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340248] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340252] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340255] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340261] ata4.00: cmd 61/10:30:e8:5c:38/00:00:00:00:00/40 tag 6 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340261]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340268] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340272] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340275] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340280] ata4.00: cmd 61/08:38:c8:5d:38/00:00:00:00:00/40 tag 7 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.340280]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.341580] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.342320] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.343031] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.343740] ata4.00: cmd 61/08:40:d8:5d:38/00:00:00:00:00/40 tag 8 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.343740]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.345163] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.345858] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.346556] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.347251] ata4.00: cmd 61/08:48:f8:5d:38/00:00:00:00:00/40 tag 9 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.347251]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.348668] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.349373] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.350061] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.350751] ata4.00: cmd 61/08:50:20:5e:38/00:00:00:00:00/40 tag 10 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.350751]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.352165] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.352870] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.353556] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.354253] ata4.00: cmd 61/18:58:40:5e:38/00:00:00:00:00/40 tag 11 ncq 12288 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.354253]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.355676] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.356395] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.357081] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.357782] ata4.00: cmd 61/08:60:68:5e:38/00:00:00:00:00/40 tag 12 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.357782]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.359210] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.359927] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.360632] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.361329] ata4.00: cmd 61/18:68:d8:5e:38/00:00:00:00:00/40 tag 13 ncq 12288 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.361329]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.362766] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.363486] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.364196] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.364898] ata4.00: cmd 61/08:70:30:5f:38/00:00:00:00:00/40 tag 14 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.364898]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.366339] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.367067] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.367766] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.368484] ata4.00: cmd 61/08:78:40:5f:38/00:00:00:00:00/40 tag 15 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.368484]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.369930] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.370657] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.371361] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.372082] ata4.00: cmd 61/08:80:a8:5f:38/00:00:00:00:00/40 tag 16 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.372082]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.373539] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.374265] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.374976] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.375701] ata4.00: cmd 61/28:88:c0:5f:38/00:00:00:00:00/40 tag 17 ncq 20480 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.375701]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.377162] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.377899] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.378605] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.379324] ata4.00: cmd 61/10:90:00:60:38/00:00:00:00:00/40 tag 18 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.379324]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.380798] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.381530] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.382242] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.382962] ata4.00: cmd 61/10:98:28:60:38/00:00:00:00:00/40 tag 19 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.382962]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.384432] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.385172] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.385887] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.386606] ata4.00: cmd 61/08:a0:48:60:38/00:00:00:00:00/40 tag 20 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.386606]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.388077] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.388818] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.389529] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.390248] ata4.00: cmd 61/08:a8:58:60:38/00:00:00:00:00/40 tag 21 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.390248]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.391712] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.392460] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.393171] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.393890] ata4.00: cmd 61/20:b0:68:60:38/01:00:00:00:00/40 tag 22 ncq 147456 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.393890]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.395356] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.396107] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.396817] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.397538] ata4.00: cmd 61/10:b8:90:61:38/00:00:00:00:00/40 tag 23 ncq 8192 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.397538]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.398996] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.399742] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.400467] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.401181] ata4.00: cmd 61/08:c0:b0:61:38/00:00:00:00:00/40 tag 24 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.401181]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.402641] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.403388] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.404112] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.404827] ata4.00: cmd 61/30:c8:c0:61:38/00:00:00:00:00/40 tag 25 ncq 24576 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.404827]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.406294] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.407040] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.407756] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.408482] ata4.00: cmd 61/48:d0:f8:61:38/00:00:00:00:00/40 tag 26 ncq 36864 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.408482]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.409946] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.410692] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.411408] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.412136] ata4.00: cmd 61/08:d8:50:62:38/00:00:00:00:00/40 tag 27 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.412136]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.413600] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.414345] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.415063] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.415789] ata4.00: cmd 61/08:e0:f8:62:38/00:00:00:00:00/40 tag 28 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.415789]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.417259] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.418002] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.418720] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.419440] ata4.00: cmd 61/08:e8:20:5b:38/00:00:00:00:00/40 tag 29 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.419440]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.420914] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.421658] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.422376] ata4.00: failed command: WRITE FPDMA QUEUED
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.423098] ata4.00: cmd 61/08:f0:48:5b:38/00:00:00:00:00/40 tag 30 ncq 4096 out
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.423098]          res 41/04:00:00:00:00/04:00:00:00:00/00 Emask 0x1 (device error)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.424575] ata4.00: status: { DRDY ERR }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.425319] ata4.00: error: { ABRT }
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.426036] ata4: hard resetting link
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.426038] ata4: nv: skipping hardreset on occupied port
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.892020] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 15 02:03:18 kazz-u0a1 kernel: [11882.908814] ata4.00: configured for UDMA/133
```

They are not network card related, but more disk related, so we don't need to worry about the network card.

Seems all the errors are on ata4, we should probably check the disk over. May be that disk is failing or SATA port/cable issues

Whats the output of
```

ls -l /sys/block/sd* | sed -e 's@.*-> \.\..*/ata@/ata@' -e 's@/host@ @' -e 's@/target.*/@ @'
```

---

### Post by kazz2 on 2016-02-15
I slowed down, took a closer look, and agree. Here's your output:

```
ls -l /sys/block/sd* | sed -e 's@.*-> \.\..*/ata@/ata@' -e 's@/host@ @' -e 's@/target.*/@ @'
/ata4 5 sda
/ata7 6 sdb
/ata8 7 sdc
/ata11 10 sdd
/ata12 11 sde

```

I just breathed a sigh of relief that ata4 appears to be the OS drive not the RAIDZ array. Regardless, how do we know whether it's soft or hard errors? The OS drive is whatever filesystem Ubuntu installed by default, btw. I guess that means ext2 as this pared print all shows:

```
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sde: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Error: /dev/mapper/kazz--u0a1--vg-swap_1: unrecognised disk label


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/kazz--u0a1--vg-root: 241GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  241GB  241GB  ext4




(parted)



```

I definitely have another drive or three I could use to replace that one. But do we really know the problem yet?

---

### Post by sandyd on 2016-02-15
Usually, the drive will come up as bad under SMART status, sometimes not.

We can probably start by testing the SMART status with the commands below, and we can proceed with testing from common -> least common causes.

Sorry if I forget sudo in any commands, I have a bad habit of working in root and sometimes forget to add sudo to any commands I post.

```

sudo apt-get install smartmontools
sudo smartctl --test=short /dev/sda
## Wait a while
sudo smartctl /dev/sda -a
```

---

### Post by kazz2 on 2016-02-15
Apparently, the drive is healthy:

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-49-generic] (local build)Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Mon Feb 15 16:31:44 2016


Use smartctl -X to abort test.
lrju0@kazz-u0a1:/var/log$
lrju0@kazz-u0a1:/var/log$ sudo smartctl /dev/sda -a
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-49-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue (SATA)
Device Model:     WDC WD5000AAKS-00UU3A0
Serial Number:    WD-WCAYU8892458
LU WWN Device Id: 5 0014ee 1ae2366e2
Firmware Version: 01.03B01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Mon Feb 15 16:39:58 2016 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                ( 7980) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  95) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3037) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   143   142   021    Pre-fail  Always       -       3850
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       78
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1191
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       73
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       38
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       39
194 Temperature_Celsius     0x0022   113   108   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1191         -


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

This motherboard has an e-SATA plug on the motherboard and one on the back panel. Otherwise, there are two together - one this drive's connected to and one the optical drive's connected to. Then there is another bank of four, which is where the four drives in RAIDZ are connected.

Soft errors? Cable?

---

### Post by sandyd on 2016-02-15
Hmm. Check in the BIOS, is the drive controller set to be in AHCI mode, not RAID or IDE?

---

### Post by kazz2 on 2016-02-15
Here's where things are going to get sticky. First, I didn't think AHCI was an issue, really, unless using an SSD. Second, the only discernible option for SATA drives are RAID or ... not? There is no AHCI option, at any rate. Is this an issue?

---

### Post by sandyd on 2016-02-15
> **kazz2 said:**
> Here's where things are going to get sticky. First, I didn't think AHCI was an issue, really, unless using an SSD. Second, the only discernible option for SATA drives are RAID or ... not? There is no AHCI option, at any rate. Is this an issue?

Nah, sometimes bios hides this just as the standard option, as long as it is not RAID or IDE. Some people have reported booting with IDE or RAID mode will trigger the issue in all drives.

This is getting somewhat tricky, though I have found someone with the same issue and motherboard chipset, give me a sec to see what the script they posted does.

Edit:

Found out, lets give this a try:

```

sudo nano /etc/default/grub
```

On the line that says GRUB_CMDLINE_LINUX_DEFAULT, add the following between the two quotes.
```

libata.force=noncq noapic
```

If there is already something there, add a space before pasting so that everything is separated.

Press Control+X to save, and run
```

sudo update-grub
```
and reboot.

If it continues happening, run the below as well

```

sudo hdparm -W0 /dev/sda
```

If that works, to make it permanent, run:
```

sudo bash -c "echo 'hdparm -W0 /dev/sda' >> /etc/rc.local"
```

---

### Post by kazz2 on 2016-02-15
No problem. I greatly appreciate your time. Is a filesystem check on sda in order? Can that cause these kinds of issues?

Also, it seems when this happens, it appears on the directly-connected monitor but not on a remote terminal via putty. Is that true?

---

### Post by sandyd on 2016-02-15
> **kazz2 said:**
> No problem. I greatly appreciate your time. Is a filesystem check on sda in order? Can that cause these kinds of issues?

Also, it seems when this happens, it appears on the directly-connected monitor but not on a remote terminal via putty. Is that true?

There is no filesystem on sda, only the partitions contained within, which is why is it is more likely something to do with the disk as that is what the kernel is complaining above. Kernel messages generally will appear on TTYs (i.e. the console on the monitor), but not SSH sessions.

---

### Post by kazz2 on 2016-02-15
I understand your point. The complaint is about sda not a partition. And thanks for the info!

---

### Post by kazz2 on 2016-02-16
No errors so far today.

---

### Post by kazz2 on 2016-02-16
I would like to check for "soft" errors in partitions. But I'm seeing they need to be offline. Is there anything I can run while they're online?

Thanks.

---

### Post by kazz2 on 2016-02-16
Performed a sudo touch /forcefsck and rebooted. I watched the realtime display output that went by too quickly and can't find the log for fsck? /var/log/fsck/checkfs says (Nothing has been logged yet.)

Can anyone help me find it, please?

---

### Post by sandyd on 2016-02-17
There is no log due to [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644)

Note that it has affected Karmic and newer distros.

If you need to run a fsck with output, you can run it from a liveCD or liveUSB where the partitions will be unmounted.

---

### Post by kazz2 on 2016-02-18
I've found some instructions for creating a LiveCD (I'd prefer to do a CD or DVD over USB at this time) but are a little over a year old. Do you have a link to some instructions for creating a LiveCD? What I've found uses remastersys to create a backup of the current configuration - which seems like the right approach.

Thanks.

---

### Post by sandyd on 2016-02-18
The LiveDVD/USB generally refers to the installation media (i.e. Ubuntu Server DVD/USB, Ubuntu DVD/USB) that you used to install.

If you used a DVD to install Ubuntu Server, then choose "Rescue a broken system" from the menu that shows up after selecting the language when booting from the DVD.

Go through the rest of the process until you reach where it detects your disks. There, you should be able to choose it to allow you to "execute a shell in the installer environment". There, you can do the fsck.

The fsck can be done in a terminal with the Ubuntu Desktop LiveDVD as well, that can be obtained from [http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop) if you find that easier.

---

### Post by kazz2 on 2016-02-19
Thank you.

---

### Post by kazz2 on 2016-02-19
Last night provided much more information on this problem. In testing backup to a USB-attached drive, the rsync quickly locked up. A sudo zpool status showed multiple read and multiple right erros on all four drives. Finding it extraordinarily unlikely that there would be those kinds of issues on all four drives I got to Google-ing with more earnest. I also checked with smarttools and found no problems.

I found threads discussing NCQ errors with nVidia SATA controllers. One in this very forum: [http://ubuntuforums.org/showthread.php?t=1651369](http://ubuntuforums.org/showthread.php?t=1651369). The proposed solution in that thread is beyond my current knowledge by a long shot. And I'm not interested in doctoring this build up at that detail knowing that if there are any issues I'll have all of that to go through again.

So my next thought as to how to get a large single space running is to use the BIOS and create a RAID5 array. When I boot Ubuntu after doing so I should see a single drive. From there I can mount, redefine shares, etc. Again, I'm trying to leverage quality, older hardware to build a single server to which I can migrate the shares on two old Windows-based servers that are either out of support or soon will be. Ubuntu seemed a great solution. And I'm *THIS* close to having it all working.

If anyone has any other suggestions, I'm "all ears". Otherwise, later today I'll be changing all sharing and mounting to remove the RAIDZ array from the server and then using BIOS to create a new array and thereby a new, single, "logical" hard drive for mounting, defining shares, etc.

Thanks!

---

### Post by sandyd on 2016-02-23
Hmm.

The commands provided earlier in the thread are actually taken from the script they posted, so you've actually already applied the fixes in the thread.

On the disks that are having errors, run this after startup.
```

sudo bash -c "echo 1 > /sys/block/sdX/device/queue_depth"
```

Replace sdX with the drive, i.e. sda, sdb

---

### Post by kazz2 on 2016-02-24
I regret not having updated this thread. I went to a 3rd-party SATA3, RAID adapter. I implemented RAID (RAIDZ) with zfs. And I've seen no errors since. Data from other servers has been consolidated on the drives and backups using rsync to an external drive have all been successful.

At this point, the only minor concern is the following lines in dmesg:

```

[COLOR=#000000][    0.858170] rr640l: module license 'Proprietary' taints kernel.
[/COLOR][COLOR=#000000][    0.859053] Disabling lock debugging due to kernel taint
[/COLOR][COLOR=#000000][    0.860086] rr640l: module verification failed: signature and/or  required key missing - tainting kernel
[/COLOR][COLOR=#000000][    0.862260] rr640l:RocketRAID 640L/642L/644L/RR644LS SATA controller driver v1.3.11
[/COLOR][COLOR=#000000]
```

I'm going to follow-up with the mfr on that today.

FWIW, I do believe the queuing depth to be the issue. And I further believe that issue lies in the SATA controller on the motherboard. That's all water over the dam now, however!

Thanks for your help and support![/COLOR]

---

### Post by SeijiSensei on 2016-02-24
"Tainting" the kernel means that a driver was released only as a binary blob without source code.  These are usually commercial drivers that do not support the General Public License.  A message about "tainting" isn't an error, just a warning that you are using some piece of software with the kernel whose source code is not available.  It looks like that RAID card is such a proprietary device.

---

### Post by kazz2 on 2016-02-24
Thanks. I'll post the mfr's response here when I get it.

---

### Post by kazz2 on 2016-02-24
Verbatim reply:

```
[COLOR=#000000][FONT=tahoma]It is because that driver is not GPL license. You can ignore that since it is just a message and won\'t affect anything.
```[/FONT][/COLOR]

---

