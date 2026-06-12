---
title: "Ubuntu won't recognize my USB flash drive"
date: 2015-01-15
forum: New to Ubuntu
---

### Post by regin.mallari on 2015-01-15
Hello all,

You've probably seen this problem hundreds of times. But I'm new to Ubuntu, I installed it last night on my laptop, but now it can't recognize my USB flash drive.

Here's the dmesg log, I hope it can help? If not pls tell me what to do, thx.

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-44-generic (buildd@lamiak) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 (Ubuntu 3.13.0-44.73-generic 3.13.11-ckt12)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-44-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000956affff] usable
[    0.000000] BIOS-e820: [mem 0x00000000956b0000-0x0000000095eaffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000095eb0000-0x000000009aabefff] usable
[    0.000000] BIOS-e820: [mem 0x000000009aabf000-0x000000009aebefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009aebf000-0x000000009afbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009afbf000-0x000000009affefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009afff000-0x000000009affffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b000000-0x000000009f9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe101000-0x00000000fe112fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO 20428/VIUU4, BIOS AACN15WW 06/10/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x15f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7E00000000 write-back
[    0.000000]   1 base 009B000000 mask 7FFF000000 uncachable
[    0.000000]   2 base 009C000000 mask 7FFC000000 uncachable
[    0.000000]   3 base 00A0000000 mask 7FE0000000 uncachable
[    0.000000]   4 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 2480MB, range: 16MB, type UC
[    0.000000] reg 2, base: 2496MB, range: 64MB, type UC
[    0.000000] reg 3, base: 2560MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6576M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2480MB, range: 16MB, type UC
[    0.000000] reg 3, base: 2496MB, range: 64MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] e820: update [mem 0x9b000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x9b000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15f400000-0x15f5fffff]
[    0.000000]  [mem 0x15f400000-0x15f5fffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15c000000-0x15f3fffff]
[    0.000000]  [mem 0x15c000000-0x15f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x15bffffff]
[    0.000000]  [mem 0x100000000-0x13fffffff] page 1G
[    0.000000]  [mem 0x140000000-0x15bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x956affff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x955fffff] page 2M
[    0.000000]  [mem 0x95600000-0x956affff] page 4k
[    0.000000] init_memory_mapping: [mem 0x95eb0000-0x9aabefff]
[    0.000000]  [mem 0x95eb0000-0x95ffffff] page 4k
[    0.000000]  [mem 0x96000000-0x9a9fffff] page 2M
[    0.000000]  [mem 0x9aa00000-0x9aabefff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9afff000-0x9affffff]
[    0.000000]  [mem 0x9afff000-0x9affffff] page 4k
[    0.000000] RAMDISK: [mem 0x3480e000-0x363fefff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 000000009affe210 0000CC (v01 LENOVO CB-01    00000001      01000013)
[    0.000000] ACPI: FACP 000000009afed000 00010C (v05 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20131115/tbfadt-202)
[    0.000000] ACPI: DSDT 000000009afda000 00F238 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FACS 000000009afba000 000040
[    0.000000] ACPI: SLIC 000000009affd000 000176 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: UEFI 000000009affc000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009aff2000 009A51 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 000000009aff0000 000044 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MSDM 000000009afef000 000055 (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 000000009afee000 0000A5 (v32 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 000000009afec000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 000000009afeb000 00008C (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 000000009afea000 00003C (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afd7000 002028 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 000000009afd5000 000028 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: LPIT 000000009afd4000 000094 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 000000009afd2000 000034 (v07 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DBGP 000000009afd1000 000034 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afc9000 000494 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afc8000 000AD8 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afc4000 0034C2 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afc3000 000393 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: PCCT 000000009afc2000 00006E (v05 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afc1000 000AC4 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x15f5fffff]
[    0.000000]   NODE_DATA [mem 0x15f5f8000-0x15f5fcfff]
[    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015ac00000-ffff88015ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x15f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x956affff]
[    0.000000]   node   0: [mem 0x95eb0000-0x9aabefff]
[    0.000000]   node   0: [mem 0x9afff000-0x9affffff]
[    0.000000]   node   0: [mem 0x100000000-0x15f5fffff]
[    0.000000] On node 0 totalpages: 1022044
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9803 pages used for memmap
[    0.000000]   DMA32 zone: 627392 pages, LIFO batch:31
[    0.000000]   Normal zone: 6104 pages used for memmap
[    0.000000]   Normal zone: 390656 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 56
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x956b0000-0x95eaffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9aabf000-0x9aebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9aebf000-0x9afbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9afbf000-0x9affefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfe100fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe101000-0xfe112fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe113000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb10000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88015f200000 s82304 r8192 d24192 u262144
[    0.000000] pcpu-alloc: s82304 r8192 d24192 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1006052
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-44-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3910428K/4088176K available (7383K kernel code, 1144K rwdata, 3408K rodata, 1336K init, 1444K bss, 177748K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:1016 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration failed
[    0.008000] tsc: PIT calibration matches HPET. 1 loops
[    0.008000] tsc: Detected 1496.210 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.42 BogoMIPS (lpj=5984840)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000044] Security Framework initialized
[    0.000069] AppArmor: AppArmor initialized
[    0.000071] Yama: becoming mindful.
[    0.000525] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001762] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002295] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002306] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002565] Initializing cgroup subsys memory
[    0.002572] Initializing cgroup subsys devices
[    0.002574] Initializing cgroup subsys freezer
[    0.002576] Initializing cgroup subsys blkio
[    0.002578] Initializing cgroup subsys perf_event
[    0.002582] Initializing cgroup subsys hugetlb
[    0.002613] CPU: Physical Processor ID: 0
[    0.002615] CPU: Processor Core ID: 0
[    0.002621] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002621] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004147] mce: CPU supports 7 MCE banks
[    0.004168] CPU0: Thermal monitoring enabled (TM1)
[    0.004184] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.004184] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.004184] tlb_flushall_shift: 6
[    0.004341] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.005790] ACPI: Core revision 20131115
[    0.025334] ACPI: All ACPI Tables successfully acquired
[    0.027596] ftrace: allocating 28554 entries in 112 pages
[    0.046849] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.086515] smpboot: CPU0: Intel(R) Core(TM) i3-4012Y CPU @ 1.50GHz (fam: 06, model: 45, stepping: 01)
[    0.086526] TSC deadline timer enabled
[    0.086541] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.086550] ... version:                3
[    0.086552] ... bit width:              48
[    0.086553] ... generic registers:      4
[    0.086554] ... value mask:             0000ffffffffffff
[    0.086556] ... max period:             0000ffffffffffff
[    0.086557] ... fixed-purpose events:   3
[    0.086558] ... event mask:             000000070000000f
[    0.088897] x86: Booting SMP configuration:
[    0.103832] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088900] .... node  #0, CPUs:      #1 #2 #3
[    0.133322] x86: Booted up 1 node, 4 CPUs
[    0.133326] smpboot: Total of 4 processors activated (11969.68 BogoMIPS)
[    0.139038] devtmpfs: initialized
[    0.143664] EVM: security.selinux
[    0.143666] EVM: security.SMACK64
[    0.143667] EVM: security.ima
[    0.143668] EVM: security.capability
[    0.143734] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[    0.144795] pinctrl core: initialized pinctrl subsystem
[    0.144866] regulator-dummy: no parameters
[    0.144930] RTC time: 15:01:46, date: 01/14/15
[    0.144973] NET: Registered protocol family 16
[    0.145101] cpuidle: using governor ladder
[    0.145103] cpuidle: using governor menu
[    0.145156] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.145158] ACPI: bus type PCI registered
[    0.145160] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.145240] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.145243] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.178808] PCI: Using configuration type 1 for base access
[    0.180016] bio: create slab <bio-0> at 0
[    0.180211] ACPI: Added _OSI(Module Device)
[    0.180213] ACPI: Added _OSI(Processor Device)
[    0.180215] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180217] ACPI: Added _OSI(Processor Aggregator Device)
[    0.187542] ACPI: Executed 1 blocks of module-level executable AML code
[    0.203295] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.204597] ACPI: SSDT 000000009ae78c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.205504] ACPI: Dynamic OEM Table Load:
[    0.205507] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.207114] ACPI: SSDT 000000009ae78618 0005AA (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.208127] ACPI: Dynamic OEM Table Load:
[    0.208130] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.210899] ACPI: SSDT 000000009ae77d98 000119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.211805] ACPI: Dynamic OEM Table Load:
[    0.211807] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.217154] ACPI: Interpreter enabled
[    0.217166] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.217175] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.217201] ACPI: (supports S0 S3 S4 S5)
[    0.217203] ACPI: Using IOAPIC for interrupt routing
[    0.217242] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.217582] ACPI: No dock devices found.
[    0.233488] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.233496] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.234297] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.235452] PCI host bridge to bus 0000:00
[    0.235456] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.235459] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.235461] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.235464] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.235466] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    0.235477] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.235710] pci 0000:00:02.0: [8086:0a1e] type 00 class 0x030000
[    0.235727] pci 0000:00:02.0: reg 0x10: [mem 0xb0000000-0xb03fffff 64bit]
[    0.235742] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.235749] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.235970] pci 0000:00:03.0: [8086:0a0c] type 00 class 0x040300
[    0.235982] pci 0000:00:03.0: reg 0x10: [mem 0xb0518000-0xb051bfff 64bit]
[    0.236213] pci 0000:00:04.0: [8086:0a03] type 00 class 0x118000
[    0.236230] pci 0000:00:04.0: reg 0x10: [mem 0xb0510000-0xb0517fff 64bit]
[    0.236518] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.236568] pci 0000:00:14.0: reg 0x10: [mem 0xb0500000-0xb050ffff 64bit]
[    0.236735] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.236910] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.236966] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    0.237018] pci 0000:00:16.0: reg 0x10: [mem 0xb0520000-0xb052001f 64bit]
[    0.237197] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.237449] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.237487] pci 0000:00:1b.0: reg 0x10: [mem 0xb051c000-0xb051ffff 64bit]
[    0.237666] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.237850] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.237908] pci 0000:00:1c.0: [8086:9c14] type 01 class 0x060400
[    0.238104] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.238294] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.238368] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    0.238417] pci 0000:00:1d.0: reg 0x10: [mem 0xb0524000-0xb05243ff]
[    0.238640] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.238841] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.238892] pci 0000:00:1f.0: [8086:9c43] type 00 class 0x060100
[    0.239340] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    0.239384] pci 0000:00:1f.2: reg 0x10: [io  0x3088-0x308f]
[    0.239403] pci 0000:00:1f.2: reg 0x14: [io  0x3094-0x3097]
[    0.239423] pci 0000:00:1f.2: reg 0x18: [io  0x3080-0x3087]
[    0.239442] pci 0000:00:1f.2: reg 0x1c: [io  0x3090-0x3093]
[    0.239462] pci 0000:00:1f.2: reg 0x20: [io  0x3060-0x307f]
[    0.239481] pci 0000:00:1f.2: reg 0x24: [mem 0xb0523000-0xb05237ff]
[    0.239591] pci 0000:00:1f.2: PME# supported from D3hot
[    0.239805] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.239843] pci 0000:00:1f.3: reg 0x10: [mem 0xb0521000-0xb05210ff 64bit]
[    0.239897] pci 0000:00:1f.3: reg 0x20: [io  0x3040-0x305f]
[    0.240159] pci 0000:00:1f.6: [8086:9c24] type 00 class 0x118000
[    0.240222] pci 0000:00:1f.6: reg 0x10: [mem 0xb0522000-0xb0522fff 64bit]
[    0.240791] pci 0000:01:00.0: [168c:0036] type 00 class 0x028000
[    0.240829] pci 0000:01:00.0: reg 0x10: [mem 0xb0400000-0xb047ffff 64bit]
[    0.240908] pci 0000:01:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.240991] pci 0000:01:00.0: supports D1 D2
[    0.240993] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.241040] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.247785] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.247792] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb04fffff]
[    0.247816] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.249656] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *7
[    0.249722] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.249783] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.249843] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.249902] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.249962] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.250021] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.250080] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.250783] ACPI: Enabled 4 GPEs in block 00 to 7F
[    0.250794] ACPI: \_SB_.PCI0: notify handler is installed
[    0.250911] Found 1 acpi root devices
[    0.250956] ACPI : EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
[    0.251082] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.251084] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.251088] vgaarb: loaded
[    0.251090] vgaarb: bridge control possible 0000:00:02.0
[    0.251293] SCSI subsystem initialized
[    0.251354] libata version 3.00 loaded.
[    0.251379] ACPI: bus type USB registered
[    0.251398] usbcore: registered new interface driver usbfs
[    0.251407] usbcore: registered new interface driver hub
[    0.251434] usbcore: registered new device driver usb
[    0.251568] PCI: Using ACPI for IRQ routing
[    0.258363] PCI: pci_cache_line_size set to 64 bytes
[    0.258406] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    0.258408] e820: reserve RAM buffer [mem 0x956b0000-0x97ffffff]
[    0.258410] e820: reserve RAM buffer [mem 0x9aabf000-0x9bffffff]
[    0.258412] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    0.258414] e820: reserve RAM buffer [mem 0x15f600000-0x15fffffff]
[    0.258509] NetLabel: Initializing
[    0.258511] NetLabel:  domain hash size = 128
[    0.258512] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.258528] NetLabel:  unlabeled traffic allowed by default
[    0.258600] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.258608] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.260645] Switched to clocksource hpet
[    0.266649] AppArmor: AppArmor Filesystem Enabled
[    0.266675] pnp: PnP ACPI init
[    0.266689] ACPI: bus type PNP registered
[    0.267448] pnp 00:00: [dma 4]
[    0.267481] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.267506] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.267634] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.267704] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.267707] system 00:03: [io  0xffff] has been reserved
[    0.267710] system 00:03: [io  0xffff] has been reserved
[    0.267712] system 00:03: [io  0xffff] has been reserved
[    0.267715] system 00:03: [io  0x1800-0x18fe] could not be reserved
[    0.267717] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.267721] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.267774] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.267825] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.267829] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.267899] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.267931] pnp 00:07: Plug and Play ACPI device, IDs ETD061d ETD0000 PNP0f13 (active)
[    0.268101] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.268106] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.268109] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.268111] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.268114] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.268116] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.268119] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.268122] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.268124] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.268127] system 00:08: [mem 0x9fa20000-0x9fa20fff] has been reserved
[    0.268129] system 00:08: [mem 0x9fa10000-0x9fa1ffff] has been reserved
[    0.268132] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.268469] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.269185] pnp: PnP ACPI: found 10 devices
[    0.269187] ACPI: bus type PNP unregistered
[    0.275589] pci 0000:01:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.275610] pci 0000:00:1c.0: BAR 15: assigned [mem 0x9fb00000-0x9fbfffff pref]
[    0.275614] pci 0000:01:00.0: BAR 6: assigned [mem 0x9fb00000-0x9fb0ffff pref]
[    0.275617] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.275623] pci 0000:00:1c.0:   bridge window [mem 0xb0400000-0xb04fffff]
[    0.275627] pci 0000:00:1c.0:   bridge window [mem 0x9fb00000-0x9fbfffff pref]
[    0.275635] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.275638] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.275640] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.275643] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    0.275645] pci_bus 0000:01: resource 1 [mem 0xb0400000-0xb04fffff]
[    0.275648] pci_bus 0000:01: resource 2 [mem 0x9fb00000-0x9fbfffff pref]
[    0.275687] NET: Registered protocol family 2
[    0.275938] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.276044] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.276121] TCP: Hash tables configured (established 32768 bind 32768)
[    0.276144] TCP: reno registered
[    0.276156] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.276175] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.276253] NET: Registered protocol family 1
[    0.276267] pci 0000:00:02.0: Video device with shadowed ROM
[    0.292768] PCI: CLS 64 bytes, default 64
[    0.292846] Trying to unpack rootfs image as initramfs...
[    1.003209] Freeing initrd memory: 28612K (ffff88003480e000 - ffff8800363ff000)
[    1.003216] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.003219] software IO TLB [mem 0x96abf000-0x9aabf000] (64MB) mapped at [ffff880096abf000-ffff88009aabefff]
[    1.003280] Simple Boot Flag at 0x44 set to 0x1
[    1.003460] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x17
[    1.003468] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x17
[    1.003478] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x17
[    1.003488] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x17
[    1.003541] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.003543] Scanning for low memory corruption every 60 seconds
[    1.003863] Initialise system trusted keyring
[    1.003917] audit: initializing netlink socket (disabled)
[    1.003928] type=2000 audit(1421247706.996:1): initialized
[    1.045494] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.046777] zbud: loaded
[    1.046973] VFS: Disk quotas dquot_6.5.2
[    1.047025] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.047528] fuse init (API version 7.22)
[    1.047613] msgmni has been set to 7693
[    1.047679] Key type big_key registered
[    1.048122] Key type asymmetric registered
[    1.048125] Asymmetric key parser 'x509' registered
[    1.048165] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.048207] io scheduler noop registered
[    1.048210] io scheduler deadline registered (default)
[    1.048238] io scheduler cfq registered
[    1.048499] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    1.048595] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.048598] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.048603] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.048618] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.048634] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.048677] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    1.048678] vesafb: scrolling: redraw
[    1.048680] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.049254] vesafb: framebuffer at 0xa0000000, mapped to 0xffffc90010780000, using 4160k, total 4160k
[    1.187904] Console: switching to colour frame buffer device 170x48
[    1.326136] fb0: VESA VGA frame buffer device
[    1.326156] intel_idle: MWAIT substates: 0x11142120
[    1.326158] intel_idle: v0.4 model 0x45
[    1.326159] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.326332] ipmi message handler version 39.2
[    1.328534] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.330740] ACPI: AC Adapter [ADP0] (on-line)
[    1.330839] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.330871] ACPI: Lid Switch [LID0]
[    1.330909] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.330914] ACPI: Power Button [PWRB]
[    1.330952] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.330955] ACPI: Power Button [PWRF]
[    1.331481] [Firmware Bug]: No valid trip found
[    1.331999] thermal LNXTHERM:01: registered as thermal_zone0
[    1.332002] ACPI: Thermal Zone [TZ01] (30 C)
[    1.332029] GHES: HEST is not enabled!
[    1.332134] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.334693] Linux agpgart interface v0.103
[    1.336106] brd: module loaded
[    1.336905] loop: module loaded
[    1.337311] libphy: Fixed MDIO Bus: probed
[    1.337413] tun: Universal TUN/TAP device driver, 1.6
[    1.337414] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.337461] PPP generic driver version 2.4.2
[    1.337507] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.337511] ehci-pci: EHCI PCI platform driver
[    1.337664] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.337671] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.337685] ehci-pci 0000:00:1d.0: debug port 2
[    1.341585] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.341605] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb0524000
[    1.352262] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.352315] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.352317] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.352319] usb usb1: Product: EHCI Host Controller
[    1.352322] usb usb1: Manufacturer: Linux 3.13.0-44-generic ehci_hcd
[    1.352323] usb usb1: SerialNumber: 0000:00:1d.0
[    1.352455] hub 1-0:1.0: USB hub found
[    1.352462] hub 1-0:1.0: 2 ports detected
[    1.352603] ehci-platform: EHCI generic platform driver
[    1.352613] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.352615] ohci-pci: OHCI PCI platform driver
[    1.352624] ohci-platform: OHCI generic platform driver
[    1.352633] uhci_hcd: USB Universal Host Controller Interface driver
[    1.352824] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.352833] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.352923] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.352945] xhci_hcd 0000:00:14.0: irq 57 for MSI/MSI-X
[    1.353017] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.353019] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.353021] usb usb2: Product: xHCI Host Controller
[    1.353023] usb usb2: Manufacturer: Linux 3.13.0-44-generic xhci_hcd
[    1.353025] usb usb2: SerialNumber: 0000:00:14.0
[    1.353152] hub 2-0:1.0: USB hub found
[    1.353165] hub 2-0:1.0: 9 ports detected
[    1.355544] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.355549] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.355589] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.355591] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.355594] usb usb3: Product: xHCI Host Controller
[    1.355596] usb usb3: Manufacturer: Linux 3.13.0-44-generic xhci_hcd
[    1.355598] usb usb3: SerialNumber: 0000:00:14.0
[    1.355715] hub 3-0:1.0: USB hub found
[    1.355724] hub 3-0:1.0: 4 ports detected
[    1.364501] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.367289] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.367299] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.367451] mousedev: PS/2 mouse device common for all mice
[    1.367628] rtc_cmos 00:04: RTC can wake from S4
[    1.367777] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.367807] rtc_cmos 00:04: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.367888] device-mapper: uevent: version 1.0.3
[    1.367971] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
[    1.367980] ledtrig-cpu: registered to indicate activity on CPUs
[    1.368103] TCP: cubic registered
[    1.368212] NET: Registered protocol family 10
[    1.368430] NET: Registered protocol family 17
[    1.368445] Key type dns_resolver registered
[    1.368712] Loading compiled-in X.509 certificates
[    1.369983] Loaded X.509 cert 'Magrathea: Glacier signing key: 508c3b4bf108ed36b6062f812782f77c37b98537'
[    1.369997] registered taskstats version 1
[    1.372583] Key type trusted registered
[    1.373280] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.375287] Key type encrypted registered
[    1.377497] AppArmor: AppArmor sha1 policy hashing enabled
[    1.377503] IMA: No TPM chip found, activating TPM-bypass!
[    1.377805] regulator-dummy: disabling
[    1.377863]   Magic number: 15:571:32
[    1.377981] rtc_cmos 00:04: setting system clock to 2015-01-14 15:01:47 UTC (1421247707)
[    1.378872] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.378875] EDD information not available.
[    1.378924] PM: Hibernation image not present or could not be loaded.
[    1.420606] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.420615] ACPI: Battery Slot [BAT0] (battery present)
[    1.421676] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.421680] Write protecting the kernel read-only data: 12288k
[    1.424477] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    1.426702] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.443474] systemd-udevd[124]: starting version 204
[    1.474245] ahci 0000:00:1f.2: version 3.0
[    1.474853] ahci 0000:00:1f.2: irq 58 for MSI/MSI-X
[    1.474890] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.474913] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x2 impl SATA mode
[    1.474918] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo only pio slum part deso sadm sds apst 
[    1.476556] scsi0 : ahci
[    1.476693] scsi1 : ahci
[    1.476792] scsi2 : ahci
[    1.477072] scsi3 : ahci
[    1.477145] ata1: DUMMY
[    1.477150] ata2: SATA max UDMA/133 abar m2048@0xb0523000 port 0xb0523180 irq 58
[    1.477152] ata3: DUMMY
[    1.477154] ata4: DUMMY
[    1.478109] [drm] Initialized drm 1.1.0 20060810
[    1.507313] [drm] Memory usable by graphics device = 2048M
[    1.507321] checking generic (a0000000 410000) vs hw (a0000000 10000000)
[    1.507324] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    1.507345] Console: switching to colour dummy device 80x25
[    1.572346] i915 0000:00:02.0: irq 59 for MSI/MSI-X
[    1.572365] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.572367] [drm] Driver supports precise vblank timestamp query.
[    1.572469] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.622039] fbcon: inteldrmfb (fb0) is primary device
[    1.668244] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.796171] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.800539] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.800541] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.800815] hub 1-1:1.0: USB hub found
[    1.800894] hub 1-1:1.0: 8 ports detected
[    1.831974] ata2.00: ATA-9: ST500LX012-SSHD-8GB, 0001LVM1, max UDMA/133
[    1.831976] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.880132] ata2.00: configured for UDMA/133
[    1.880320] scsi 1:0:0:0: Direct-Access     ATA      ST500LX012-SSHD- 0001 PQ: 0 ANSI: 5
[    1.880495] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.880498] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.880525] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.880622] sd 1:0:0:0: [sda] Write Protect is off
[    1.880626] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.880652] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.882041]  sda: sda1 sda2 < sda5 >
[    1.882722] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.968152] usb 2-1: new high-speed USB device number 2 using xhci_hcd
[    1.993873] usb 2-1: New USB device found, idVendor=1bcf, idProduct=2c66
[    1.993875] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.993877] usb 2-1: Product: Lenovo EasyCamera
[    1.993878] usb 2-1: Manufacturer: J5CE9I0FC
[    2.000080] tsc: Refined TSC clocksource calibration: 1496.535 MHz
[    2.047540] psmouse serio1: elantech: unknown hardware version, aborting...
[    2.160125] usb 2-5: new full-speed USB device number 3 using xhci_hcd
[    2.177485] usb 2-5: New USB device found, idVendor=0cf3, idProduct=3004
[    2.177488] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.240793] input: PS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input5
[    2.344029] usb 2-6: new full-speed USB device number 4 using xhci_hcd
[    2.819863] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    2.999922] Switched to clocksource tsc
[    3.263620] Console: switching to colour frame buffer device 170x48
[    3.267089] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.267091] i915 0000:00:02.0: registered panic notifier
[    3.273724] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.274321] acpi device:3e: registered as cooling_device4
[    3.274413] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    3.274506] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.363588] usb 2-6: New USB device found, idVendor=048d, idProduct=8386
[    7.363595] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.363598] usb 2-6: Product: ITE Device(8386)
[    7.363602] usb 2-6: Manufacturer: ITE Tech. Inc.
[    7.368263] hidraw: raw HID events driver (C) Jiri Kosina
[    7.405372] usbcore: registered new interface driver usbhid
[    7.405376] usbhid: USB HID core driver
[    7.530066] usb 2-7: new full-speed USB device number 5 using xhci_hcd
[    7.555236] usb 2-7: New USB device found, idVendor=03eb, idProduct=8c1d
[    7.555241] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.555245] usb 2-7: Product: Atmel maXTouch Digitizer
[    7.555249] usb 2-7: Manufacturer: Atmel
[    7.567367] hid-generic 0003:03EB:8C1D.0003: hiddev0,hidraw0: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:14.0-7/input1
[    8.635629] random: cryptsetup urandom read with 101 bits of entropy available
[    8.640461] bio: create slab <bio-1> at 1
[    8.826659] bio: create slab <bio-1> at 1
[    8.892608] random: nonblocking pool is initialized
[    8.910639] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[    8.910643] EXT4-fs (dm-1): write access will be enabled during recovery
[   10.579993] EXT4-fs (dm-1): recovery complete
[   10.581532] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   13.056079] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   13.156765] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   13.162506] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   13.191639] systemd-udevd[460]: starting version 204
[   13.258321] lp: driver loaded but no devices found
[   13.280987] ppdev: user-space parallel port driver
[   13.394018] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   13.394030] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.394036] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   13.394042] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   13.394048] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.394050] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   13.394056] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   13.394061] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \IO_D 3 (20131115/utaddress-251)
[   13.394067] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.394069] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   13.426512] input: Atmel Atmel maXTouch Digitizer as /devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input7
[   13.427132] hid-multitouch 0003:03EB:8C1D.0002: input,hidraw1: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:14.0-7/input0
[   13.431857] cfg80211: Calling CRDA to update world regulatory domain
[   13.464739] mei_me 0000:00:16.0: irq 60 for MSI/MSI-X
[   13.491903] Bluetooth: Core ver 2.17
[   13.508051] NET: Registered protocol family 31
[   13.508057] Bluetooth: HCI device and connection manager initialized
[   13.508067] Bluetooth: HCI socket layer initialized
[   13.508075] Bluetooth: L2CAP socket layer initialized
[   13.508081] Bluetooth: SCO socket layer initialized
[   13.515286] usbcore: registered new interface driver btusb
[   13.517580] HDA driver get symbol successfully from i915 module
[   13.517813] snd_hda_intel 0000:00:1b.0: irq 61 for MSI/MSI-X
[   13.518025] ath: phy0: WB335 1-ANT card detected
[   13.518029] ath: phy0: Set BT/WLAN RX diversity capability
[   13.521229] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.521234] Bluetooth: BNEP filters: protocol multicast
[   13.521244] Bluetooth: BNEP socket layer initialized
[   13.525337] ath: phy0: Enable LNA combining
[   13.525410] snd_hda_intel 0000:00:03.0: irq 62 for MSI/MSI-X
[   13.526569] ath: EEPROM regdomain: 0x65
[   13.526573] ath: EEPROM indicates we should expect a direct regpair map
[   13.526577] ath: Country alpha2 being used: 00
[   13.526579] ath: Regpair used: 0x65
[   13.535807] hda_codec: CX20756: BIOS auto-probing.
[   13.536039] autoconfig: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[   13.536042]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.536045]    hp_outs=1 (0x16/0x0/0x0/0x0/0x0)
[   13.536047]    mono: mono_out=0x0
[   13.536049]    inputs:
[   13.536052]      Internal Mic=0x1a
[   13.536054]      Mic=0x19
[   13.536127] Linux video capture interface: v2.00
[   13.536740] hda_codec: Enable sync_write for stable communication
[   13.540416] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   13.540520] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[   13.554061] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (1bcf:2c66)
[   13.558952] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12
[   13.568333] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.568799] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc90010900000, irq=18
[   13.569440] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[   13.569608] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10
[   13.575513] kvm: disabled by bios
[   13.575642] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/input/input13
[   13.575740] usbcore: registered new interface driver uvcvideo
[   13.575743] USB Video Class driver (1.1.1)
[   13.634158] Bluetooth: RFCOMM TTY layer initialized
[   13.634172] Bluetooth: RFCOMM socket layer initialized
[   13.634188] Bluetooth: RFCOMM ver 1.11
[   13.666618] usb 2-5: USB disconnect, device number 3
[   13.666923] usbcore: registered new interface driver ath3k
[   13.713901] type=1400 audit(1421276519.836:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=699 comm="apparmor_parser"
[   13.713914] type=1400 audit(1421276519.836:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=699 comm="apparmor_parser"
[   13.714714] type=1400 audit(1421276519.836:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=699 comm="apparmor_parser"
[   13.732145] intel_rapl: domain uncore energy ctr 6524:6524 not working, skip
[   13.779368] init: cups main process (706) killed by HUP signal
[   13.779386] init: cups main process ended, respawning
[   13.787151] cfg80211: World regulatory domain updated:
[   13.787157] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.787161] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.787164] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.787167] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.787170] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.787173] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.869301] type=1400 audit(1421276519.992:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=727 comm="apparmor_parser"
[   13.869314] type=1400 audit(1421276519.992:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
[   13.869323] type=1400 audit(1421276519.992:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
[   13.870148] type=1400 audit(1421276519.992:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
[   13.870159] type=1400 audit(1421276519.992:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
[   13.870591] type=1400 audit(1421276519.992:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
[   13.936024] usb 2-5: new full-speed USB device number 6 using xhci_hcd
[   14.001264] init: failsafe main process (736) killed by TERM signal
[   14.234688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.235099] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.244342] type=1400 audit(1421276520.368:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=997 comm="apparmor_parser"
[   15.125029] wlan0: authenticate with 00:24:6c:7f:e6:a1
[   15.139692] wlan0: send auth to 00:24:6c:7f:e6:a1 (try 1/3)
[   15.159217] wlan0: authenticated
[   15.163345] wlan0: associate with 00:24:6c:7f:e6:a1 (try 1/3)
[   15.169691] wlan0: RX AssocResp from 00:24:6c:7f:e6:a1 (capab=0x21 status=0 aid=18)
[   15.169727] wlan0: associated
[   15.169738] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.933969] xhci_hcd 0000:00:14.0: Timeout while waiting for address device command
[   18.934000] ------------[ cut here ]------------
[   18.934013] WARNING: CPU: 1 PID: 0 at /build/buildd/linux-3.13.0/drivers/usb/host/xhci-ring.c:1582 handle_cmd_completion+0xe46/0xe50()
[   18.934015] Modules linked in: hid_sensor_accel_3d hid_sensor_als hid_sensor_gyro_3d hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common joydev rfcomm intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm uvcvideo snd_hda_codec_hdmi videobuf2_vmalloc arc4 videobuf2_memops videobuf2_core snd_hda_codec_conexant videodev ath3k bnep btusb snd_hda_intel ath9k serio_raw snd_hda_codec ath9k_common ath9k_hw snd_hwdep snd_pcm bluetooth snd_page_alloc ath snd_seq_midi snd_seq_midi_event mac80211 hid_sensor_hub snd_rawmidi snd_seq mei_me snd_seq_device hid_multitouch snd_timer cfg80211 snd lpc_ich mei soundcore parport_pc ppdev lp parport mac_hid hid_generic usbhid hid dm_crypt crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel i915 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd i2c_algo_bit drm_kms_helper psmouse drm ahci libahci video
[   18.934075] CPU: 1 PID: 0 Comm: swapper/1 Not tainted 3.13.0-44-generic #73-Ubuntu
[   18.934076] Hardware name: LENOVO 20428/VIUU4, BIOS AACN15WW 06/10/2014
[   18.934078]  0000000000000009 ffff88015f243da8 ffffffff81720d86 0000000000000000
[   18.934082]  ffff88015f243de0 ffffffff810677cd ffff8801534475b0 ffff8801534471c0
[   18.934085]  0000000000000005 00000001534471c0 ffff8801588d4000 ffff88015f243df0
[   18.934089] Call Trace:
[   18.934091]  <IRQ>  [<ffffffff81720d86>] dump_stack+0x45/0x56
[   18.934099]  [<ffffffff810677cd>] warn_slowpath_common+0x7d/0xa0
[   18.934103]  [<ffffffff810678aa>] warn_slowpath_null+0x1a/0x20
[   18.934107]  [<ffffffff8157db96>] handle_cmd_completion+0xe46/0xe50
[   18.934114]  [<ffffffffa0564175>] ? ath9k_iowrite32+0x35/0x90 [ath9k]
[   18.934118]  [<ffffffff8157f4d3>] xhci_irq+0x333/0xa60
[   18.934122]  [<ffffffff8157fc11>] xhci_msi_irq+0x11/0x20
[   18.934126]  [<ffffffff810bfa5e>] handle_irq_event_percpu+0x3e/0x1d0
[   18.934129]  [<ffffffff810bfc2d>] handle_irq_event+0x3d/0x60
[   18.934132]  [<ffffffff810c26b7>] handle_edge_irq+0x77/0x130
[   18.934137]  [<ffffffff81015e5e>] handle_irq+0x1e/0x30
[   18.934142]  [<ffffffff81733b9d>] do_IRQ+0x4d/0xc0
[   18.934146]  [<ffffffff817292ad>] common_interrupt+0x6d/0x6d
[   18.934147]  <EOI>  [<ffffffff815d3792>] ? cpuidle_enter_state+0x52/0xc0
[   18.934155]  [<ffffffff815d38b9>] cpuidle_idle_call+0xb9/0x1f0
[   18.934159]  [<ffffffff8101d35e>] arch_cpu_idle+0xe/0x30
[   18.934162]  [<ffffffff810bef35>] cpu_startup_entry+0xc5/0x290
[   18.934167]  [<ffffffff810413fd>] start_secondary+0x21d/0x2d0
[   18.934169] ---[ end trace 9482332f663dbcb1 ]---
[   19.138169] usb 2-5: Device not responding to set address.
[   19.341836] usb 2-5: device not accepting address 6, error -71
[   19.453868] usb 2-5: new full-speed USB device number 7 using xhci_hcd
[   19.471296] usb 2-5: New USB device found, idVendor=0cf3, idProduct=3004
[   19.471302] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   19.753656] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
[   19.753666] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host.
[   19.753698] Bluetooth: hci0 urb ffff88008a24ed80 failed to resubmit (22)
[   19.753703] Bluetooth: hci0 urb ffff88008a24e9c0 failed to resubmit (22)
[   19.753706] Bluetooth: hci0 urb ffff88008a24e600 failed to resubmit (22)
[   19.753712] xhci_hcd 0000:00:14.0: HC died; cleaning up
[   19.753737] usb 2-1: USB disconnect, device number 2
[   19.798006] usb 2-5: USB disconnect, device number 7
[   19.798586] usb 2-6: USB disconnect, device number 4
[   19.799299] usb 2-7: USB disconnect, device number 5
[   19.812546] init: plymouth-upstart-bridge main process ended, respawning
[   29.832262] cfg80211: Calling CRDA to update world regulatory domain
[   29.838582] cfg80211: World regulatory domain updated:
[   29.838586] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.838589] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.838591] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.838593] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.838594] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.838596] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.998543] wlan0: authenticate with 00:24:6c:7f:e7:a1
[   30.018878] wlan0: send auth to 00:24:6c:7f:e7:a1 (try 1/3)
[   30.022822] wlan0: authenticated
[   30.025945] wlan0: associate with 00:24:6c:7f:e7:a1 (try 1/3)
[   30.038602] wlan0: RX AssocResp from 00:24:6c:7f:e7:a1 (capab=0x21 status=0 aid=1)
[   30.038638] wlan0: associated
[   43.814837] audit_printk_skb: 150 callbacks suppressed
[   43.814841] type=1400 audit(1421276549.948:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2534 comm="apparmor_parser"
[   43.814849] type=1400 audit(1421276549.948:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2534 comm="apparmor_parser"
[   43.815347] type=1400 audit(1421276549.948:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2534 comm="apparmor_parser"
[  299.708504] mce: [Hardware Error]: Machine check events logged
```

---

### Post by Florian_Braun on 2015-01-15
Think this is your Drive:

[ 19.138169] usb 2-5: Device not responding to set address. 
[ 19.341836] usb 2-5: device not accepting address 6, error -71 
[ 19.453868] usb 2-5: new full-speed USB device number 7 using xhci_hcd 
[ 19.471296] usb 2-5: New USB device found, idVendor=0cf3, idProduct=3004 
[ 19.471302] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0

so you might try this:

[http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error](http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error)

Also try other port and dont use extention cables.
If it persists try stick on Android Phone , PC or other devices , if there is the same problem the stick is dead ;)

Greetings From Germany,
Flo

---

### Post by llamabr on 2015-01-15
Tell us the output of:

sudo modprobe -l | grep ehci

Also, once you plug the thing in, you have to wait a minute or two.  Then post the output of dmesg (we only need the last 20 lines or so:

dmesg | tail -20

---

### Post by regin.mallari on 2015-01-16
```
modprobe: invalid option -- 'l'
```

The USB device works on my other computer (PC). After waiting a few minutes or so, still not working, here's the output of dmesg (last 20 lines)

```
[   21.080584] xhci_hcd 0000:00:14.0: HC died; cleaning up[   21.117627] init: plymouth-upstart-bridge main process ended, respawning
[   26.274667] xhci_hcd 0000:00:14.0: Timeout while waiting for address device command
[   26.274675] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   26.478596] usb 2-5: device not accepting address 6, error -108
[   31.475007] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[   31.475012] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   36.470692] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[   36.470700] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   41.466458] xhci_hcd 0000:00:14.0: Timeout while waiting for a slot
[   41.466469] xhci_hcd 0000:00:14.0: Abort the command ring, but the xHCI is dead.
[   41.466496] usb 2-1: USB disconnect, device number 2
[   41.486714] usb 2-6: USB disconnect, device number 4
[   41.489191] usb 2-7: USB disconnect, device number 5
[   46.071184] audit_printk_skb: 150 callbacks suppressed
[   46.071191] type=1400 audit(1421384920.213:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2740 comm="apparmor_parser"
[   46.071202] type=1400 audit(1421384920.213:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2740 comm="apparmor_parser"
[   46.072005] type=1400 audit(1421384920.213:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2740 comm="apparmor_parser"
[  299.572086] mce: [Hardware Error]: Machine check events logged
[  355.873607] systemd-hostnamed[3058]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

Is it possible that I need to reinstall some driver?

---

### Post by sandyd on 2015-01-16
Smells like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1254581](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1254581)

---

### Post by llamabr on 2015-01-16
I'm not sure it's a bug.  Sorry about the modprobe.  Please report these:

lsmod | grep usb

and 

lsmod | grep ehci

What I'm looking for is to remove usb2, so that your stick will load without it.

---

### Post by regin.mallari on 2015-01-16
```
btusb                  32412  0 bluetooth             391136  12 bnep,ath3k,btusb,rfcomm
usbhid                 52659  0 
hid                   106148  4 hid_multitouch,hid_generic,hid_sensor_hub,usbhid
```

was the result for grep usb, while the other one didn't produce anything

---

### Post by llamabr on 2015-01-16
Sorry, I didn't read the above very carefully.  I don't know how badly you want to keep troubleshooting this, but We're looking for xhci_hcd. (not ehci, which was the previous generation)

Try 

sudo rmmod xhci-hcd

and then plug it in.  Hang back, and then dmesg.   Does it work?

Some people report having to rmmod xhci-hcd and then straight away putting it back with modprobe xhci-hcd

Let us know what happens

---

### Post by regin.mallari on 2015-01-16
```
rmmod: ERROR: Module xhci_hcd is builtin.
```

^^

---

### Post by buzzingrobot on 2015-01-16
Just in case, try repartioning and reformatting it.  FAT32.   Seems to cure most of my USB stick issues.

---

### Post by regin.mallari on 2015-01-17
mmkay, i just turned on my laptop, and it works now, I didn't really do anything? :shock:

---

### Post by sudodus on 2015-01-17
Yes, you did. The old trick from MSDOS and Windows, reboot, and in really bad cases shutdown and cold start, can help solve many problems, when computers get stuck :-P

---

