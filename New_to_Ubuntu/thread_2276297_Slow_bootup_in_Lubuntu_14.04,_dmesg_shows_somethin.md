---
title: "Slow bootup in Lubuntu 14.04, dmesg shows something..."
date: 2015-05-01
forum: New to Ubuntu
---

### Post by viktor5 on 2015-05-01
Hi guys, I have a pentium 4 2.4 Ghz with 1.2 Gb of RAM,

dmesg shows something:

                                                     [    6.084016] ata2: link is slow to respond, please be patient (ready=0)            
            [   11.068014] ata2: device not ready (errno=-16), forcing hardreset            
            [   16.264014] ata2: link is slow to respond, please be patient (ready=0)            
            [   21.080015] ata2: SRST failed (errno=-16)            
            [   26.276014] ata2: link is slow to respond, please be patient (ready=0)            
            [   31.092015] ata2: SRST failed (errno=-16)            
            [   36.288015] ata2: link is slow to respond, please be patient (ready=0)            
            [   66.136016] ata2: SRST failed (errno=-16)            
            [   71.164015] ata2: SRST failed (errno=-16)            
            [   71.175203] ata2: reset failed, giving up
 
What does it mean?
 
Hee's the whole dmesg:
 
```
                                                    [    0.000000] Initializing cgroup subsys cpuset            
            [    0.000000] Initializing cgroup subsys cpu            
            [    0.000000] Initializing cgroup subsys cpuacct            
            [    0.000000] Linux version 3.13.0-51-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #84-Ubuntu SMP Wed Apr 15 12:11:46 UTC 2015 (Ubuntu 3.13.0-51.84-generic 3.13.11-ckt18)            
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
            [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable            
            [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved            
            [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved            
            [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000004f7effff] usable            
            [    0.000000] BIOS-e820: [mem 0x000000004f7f0000-0x000000004f7fffff] reserved            
            [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved            
            [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!            
            [    0.000000] SMBIOS 2.3 present.            
            [    0.000000] DMI: Compaq Evo D310/0804h, BIOS 686O2 v2.18 09/24/2002            
            [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved            
            [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable            
            [    0.000000] e820: last_pfn = 0x4f7f0 max_arch_pfn = 0x1000000            
            [    0.000000] MTRR default type: uncachable            
            [    0.000000] MTRR fixed ranges enabled:            
            [    0.000000]   00000-9FFFF write-back            
            [    0.000000]   A0000-BFFFF uncachable            
            [    0.000000]   C0000-CFFFF write-protect            
            [    0.000000]   D0000-DFFFF uncachable            
            [    0.000000]   E0000-EFFFF write-back            
            [    0.000000]   F0000-FFFFF write-protect            
            [    0.000000] MTRR variable ranges enabled:            
            [    0.000000]   0 base 04F800000 mask FFF800000 uncachable            
            [    0.000000]   1 base 000000000 mask FC0000000 write-back            
            [    0.000000]   2 base 040000000 mask FF0000000 write-back            
            [    0.000000]   3 base 0FEDA0000 mask FFFFE0000 write-back            
            [    0.000000]   4 disabled            
            [    0.000000]   5 disabled            
            [    0.000000]   6 disabled            
            [    0.000000]   7 disabled            
            [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106            
            [    0.000000] original variable MTRRs            
            [    0.000000] reg 0, base: 1272MB, range: 8MB, type UC            
            [    0.000000] reg 1, base: 0GB, range: 1GB, type WB            
            [    0.000000] reg 2, base: 1GB, range: 256MB, type WB            
            [    0.000000] reg 3, base: 4175488KB, range: 128KB, type WB            
            [    0.000000] total RAM covered: 1272M            
            [    0.000000] Found optimal setting for mtrr clean up            
            [    0.000000]  gran_size: 64K chunk_size: 16M num_reg: 4  lose cover RAM: 0G            
            [    0.000000] New variable MTRRs            
            [    0.000000] reg 0, base: 0GB, range: 1GB, type WB            
            [    0.000000] reg 1, base: 1GB, range: 256MB, type WB            
            [    0.000000] reg 2, base: 1272MB, range: 8MB, type UC            
            [    0.000000] reg 3, base: 4175488KB, range: 128KB, type WB            
            [    0.000000] e820: update [mem 0x4f800000-0xfed9ffff] usable ==> reserved            
            [    0.000000] found SMP MP-table at [mem 0x000f9bf0-0x000f9bff] mapped at [c00f9bf0]            
            [    0.000000] Scanning 1 areas for low memory corruption            
            [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]            
            [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384            
            [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]            
            [    0.000000]  [mem 0x00000000-0x000fffff] page 4k            
            [    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]            
            [    0.000000]  [mem 0x37800000-0x379fffff] page 2M            
            [    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]            
            [    0.000000]  [mem 0x34000000-0x377fffff] page 2M            
            [    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]            
            [    0.000000]  [mem 0x00100000-0x001fffff] page 4k            
            [    0.000000]  [mem 0x00200000-0x33ffffff] page 2M            
            [    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]            
            [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k            
            [    0.000000] BRK [0x01b99000, 0x01b99fff] PGTABLE            
            [    0.000000] RAMDISK: [mem 0x35c1c000-0x36e05fff]            
            [    0.000000] ACPI: RSDP 000eaa10 000014 (v00 COMPAQ)            
            [    0.000000] ACPI: RSDT 000e6740 000074 (v01 COMPAQ CPQ0053  20020924      00000000)            
            [    0.000000] ACPI: FACP 000e67f8 000074 (v01 COMPAQ BROOKDG  00000001      00000000)            
            [    0.000000] ACPI: DSDT 000e68c6 000B73 (v01 COMPAQ     DSDT 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: FACS 000e6700 000040            
            [    0.000000] ACPI: SSDT 000e7439 00073D (v01 COMPAQ  PROJECT 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e7b76 00053A (v01 COMPAQ CORE_PNP 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e80b0 00019B (v01 COMPAQ CORE_UTL 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e824b 000308 (v01 COMPAQ VILLTBL1 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e8553 00053F (v01 COMPAQ LGCYLITE 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e8a92 000167 (v01 COMPAQ    UART2 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e8bf9 00014E (v01 COMPAQ   FLOPPY 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: APIC 000e686c 00005A (v01 COMPAQ BROOKDG  00000001      00000000)            
            [    0.000000] ACPI: SSDT 000ea6be 0000B2 (v01 COMPAQ     APIC 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e91b5 000424 (v01 COMPAQ PNP_PRSS 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e95d9 00016D (v01 COMPAQ UR2_PRSS 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e9746 000119 (v01 COMPAQ FPY_PRSS 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e98f7 000135 (v01 COMPAQ       S3 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e9a2c 00013B (v01 COMPAQ  CORE_S3 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e9b67 000173 (v01 COMPAQ   PIDETM 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e9e52 000180 (v01 COMPAQ     GTF0 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000e9fd2 000185 (v01 COMPAQ     GTF1 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000ea461 0000F0 (v01 COMPAQ      L08 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: SSDT 000ea859 000053 (v01 COMPAQ    FINIS 00000001 MSFT 0100000E)            
            [    0.000000] ACPI: Local APIC address 0xfee00000            
            [    0.000000] 379MB HIGHMEM available.            
            [    0.000000] 891MB LOWMEM available.            
            [    0.000000]   mapped low ram: 0 - 37bfe000            
            [    0.000000]   low ram: 0 - 37bfe000            
            [    0.000000] BRK [0x01b9a000, 0x01b9afff] PGTABLE            
            [    0.000000] Zone ranges:            
            [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]            
            [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]            
            [    0.000000]   HighMem  [mem 0x37bfe000-0x4f7effff]            
            [    0.000000] Movable zone start for each node            
            [    0.000000] Early memory node ranges            
            [    0.000000]   node   0: [mem 0x00001000-0x0009efff]            
            [    0.000000]   node   0: [mem 0x00100000-0x4f7effff]            
            [    0.000000] On node 0 totalpages: 325518            
            [    0.000000] free_area_init_node: node 0, pgdat c199f780, node_mem_map f720e020            
            [    0.000000]   DMA zone: 32 pages used for memmap            
            [    0.000000]   DMA zone: 0 pages reserved            
            [    0.000000]   DMA zone: 3998 pages, LIFO batch:0            
            [    0.000000]   Normal zone: 1752 pages used for memmap            
            [    0.000000]   Normal zone: 224254 pages, LIFO batch:31            
            [    0.000000]   HighMem zone: 760 pages used for memmap            
            [    0.000000]   HighMem zone: 97266 pages, LIFO batch:31            
            [    0.000000] Using APIC driver default            
            [    0.000000] ACPI: PM-Timer IO Port: 0xf808            
            [    0.000000] ACPI: Local APIC address 0xfee00000            
            [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)            
            [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])            
            [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])            
            [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23            
            [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)            
            [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)            
            [    0.000000] ACPI: IRQ0 used by override.            
            [    0.000000] ACPI: IRQ2 used by override.            
            [    0.000000] ACPI: IRQ9 used by override.            
            [    0.000000] Using ACPI (MADT) for SMP configuration information            
            [    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs            
            [    0.000000] nr_irqs_gsi: 40            
            [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]            
            [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]            
            [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]            
            [    0.000000] e820: [mem 0x4f800000-0xfebfffff] available for PCI devices            
            [    0.000000] Booting paravirtualized kernel on bare hardware            
            [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1            
            [    0.000000] PERCPU: Embedded 14 pages/cpu @f71f9000 s35520 r0 d21824 u57344            
            [    0.000000] pcpu-alloc: s35520 r0 d21824 u57344 alloc=14*4096            
            [    0.000000] pcpu-alloc: [0] 0            
            [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 323734            
            [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-51-generic root=UUID=e11b218b-b7ce-404b-ad8b-d63ee0888e62 ro quiet splash vt.handoff=7            
            [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)            
            [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)            
            [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)            
            [    0.000000] CPU0 microcode updated early to revision 0x37, date = 2003-06-04            
            [    0.000000] Initializing CPU#0            
            [    0.000000] allocated 2604920 bytes of page_cgroup            
            [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups            
            [    0.000000] Initializing HighMem for node 0 (00037bfe:0004f7f0)            
            [    0.000000] Memory: 1258164K/1302072K available (6553K kernel code, 641K rwdata, 2768K rodata, 880K init, 924K bss, 43908K reserved, 389064K highmem)            
            [    0.000000] virtual kernel memory layout:            
            [    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)            
            [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)            
            [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)            
            [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)            
            [    0.000000]       .init : 0xc19bd000 - 0xc1a99000   ( 880 kB)            
            [    0.000000]       .data : 0xc16667b4 - 0xc19bc600   (3415 kB)            
            [    0.000000]       .text : 0xc1000000 - 0xc16667b4   (6553 kB)            
            [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.            
            [    0.000000] SLUB: HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1            
            [    0.000000] Hierarchical RCU implementation.            
            [    0.000000] RCU dyntick-idle grace-period acceleration is enabled.            
            [    0.000000] RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.            
            [    0.000000] NR_IRQS:2304 nr_irqs:256 16            
            [    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000            
            [    0.000000] Console: colour dummy device 80x25            
            [    0.000000] console [tty0] enabled            
            [    0.000000] tsc: Fast TSC calibration using PIT            
            [    0.000000] tsc: Detected 2391.380 MHz processor            
            [    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4782.76 BogoMIPS (lpj=9565520)            
            [    0.008012] pid_max: default: 32768 minimum: 301            
            [    0.008070] Security Framework initialized            
            [    0.008119] AppArmor: AppArmor initialized            
            [    0.008124] Yama: becoming mindful.            
            [    0.008232] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)            
            [    0.008238] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)            
            [    0.008701] Initializing cgroup subsys memory            
            [    0.008721] Initializing cgroup subsys devices            
            [    0.008728] Initializing cgroup subsys freezer            
            [    0.008734] Initializing cgroup subsys blkio            
            [    0.008741] Initializing cgroup subsys perf_event            
            [    0.008748] Initializing cgroup subsys hugetlb            
            [    0.008801] CPU0: Hyper-Threading is disabled            
            [    0.008810] mce: CPU supports 4 MCE banks            
            [    0.008827] CPU0: Thermal monitoring enabled (TM1)            
            [    0.008857] Last level iTLB entries: 4KB 128, 2MB 128, 4MB 128            
            [    0.008857] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 64            
            [    0.008857] tlb_flushall_shift: 6            
            [    0.036136] Freeing SMP alternatives memory: 32K (c1a99000 - c1aa1000)            
            [    0.037863] ACPI: Core revision 20131115            
            [    0.042407] ACPI: All ACPI Tables successfully acquired            
            [    0.042623] ftrace: allocating 27866 entries in 55 pages            
            [    0.056300] Enabling APIC mode:  Flat.  Using 1 I/O APICs            
            [    0.056673] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1            
            [    0.097100] smpboot: CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz (fam: 0f, model: 02, stepping: 07)            
            [    0.100000] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.            
            [    0.100000] ... version:                0            
            [    0.100000] ... bit width:              40            
            [    0.100000] ... generic registers:      18            
            [    0.100000] ... value mask:             000000ffffffffff            
            [    0.100000] ... max period:             0000007fffffffff            
            [    0.100000] ... fixed-purpose events:   0            
            [    0.100000] ... event mask:             000000000003ffff            
            [    0.100000] x86: Booted up 1 node, 1 CPUs            
            [    0.100000] smpboot: Total of 1 processors activated (4782.76 BogoMIPS)            
            [    0.100197] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.            
            [    0.100391] devtmpfs: initialized            
            [    0.100704] EVM: security.selinux            
            [    0.100708] EVM: security.SMACK64            
            [    0.100711] EVM: security.ima            
            [    0.100715] EVM: security.capability            
            [    0.102727] pinctrl core: initialized pinctrl subsystem            
            [    0.102899] regulator-dummy: no parameters            
            [    0.102938] RTC time: 18:23:37, date: 05/01/15            
            [    0.103020] NET: Registered protocol family 16            
            [    0.103333] EISA bus registered            
            [    0.103339] cpuidle: using governor ladder            
            [    0.103344] cpuidle: using governor menu            
            [    0.103496] ACPI: bus type PCI registered            
            [    0.103504] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5            
            [    0.103890] PCI: PCI BIOS revision 2.20 entry at 0xeca48, last bus=5            
            [    0.103894] PCI: Using configuration type 1 for base access            
            [    0.105988] bio: create slab <bio-0> at 0            
            [    0.106273] ACPI: Added _OSI(Module Device)            
            [    0.106279] ACPI: Added _OSI(Processor Device)            
            [    0.106283] ACPI: Added _OSI(3.0 _SCP Extensions)            
            [    0.106287] ACPI: Added _OSI(Processor Aggregator Device)            
            [    0.108733] ACPI: Interpreter enabled            
            [    0.108756] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)            
            [    0.108778] ACPI: (supports S0 S1 S3 S4 S5)            
            [    0.108782] ACPI: Using IOAPIC for interrupt routing            
            [    0.108834] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug            
            [    0.108943] ACPI: No dock devices found.            
            [    0.114554] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 14 15)            
            [    0.114673] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)            
            [    0.114788] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)            
            [    0.114902] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)            
            [    0.115017] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)            
            [    0.115130] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.            
            [    0.115245] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.            
            [    0.115361] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)            
            [    0.115526] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])            
            [    0.115538] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]            
            [    0.115549] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM            
            [    0.115782] acpi PNP0A03:00: host bridge window [mem 0x4f900000-0xfebfffff] (ignored)            
            [    0.115788] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)            
            [    0.115794] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)            
            [    0.115799] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)            
            [    0.115805] PCI: root bus 00: using default resources            
            [    0.115812] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.            
            [    0.115971] PCI host bridge to bus 0000:00            
            [    0.115978] pci_bus 0000:00: root bus resource [bus 00-ff]            
            [    0.115984] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]            
            [    0.115990] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]            
            [    0.116029] pci 0000:00:00.0: [8086:2560] type 00 class 0x060000            
            [    0.116046] pci 0000:00:00.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]            
            [    0.116186] pci 0000:00:02.0: [8086:2562] type 00 class 0x030000            
            [    0.116206] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]            
            [    0.116219] pci 0000:00:02.0: reg 0x14: [mem 0xfc400000-0xfc47ffff]            
            [    0.116390] pci 0000:00:1d.0: [8086:24c2] type 00 class 0x0c0300            
            [    0.116442] pci 0000:00:1d.0: reg 0x20: [io  0x2440-0x245f]            
            [    0.116511] pci 0000:00:1d.0: System wakeup disabled by ACPI            
            [    0.116570] pci 0000:00:1d.1: [8086:24c4] type 00 class 0x0c0300            
            [    0.116621] pci 0000:00:1d.1: reg 0x20: [io  0x2460-0x247f]            
            [    0.116688] pci 0000:00:1d.1: System wakeup disabled by ACPI            
            [    0.116757] pci 0000:00:1d.7: [8086:24cd] type 00 class 0x0c0320            
            [    0.116785] pci 0000:00:1d.7: reg 0x10: [mem 0xfc480000-0xfc4803ff]            
            [    0.116890] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold            
            [    0.116938] pci 0000:00:1d.7: System wakeup disabled by ACPI            
            [    0.116997] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060400            
            [    0.117074] pci 0000:00:1e.0: System wakeup disabled by ACPI            
            [    0.117131] pci 0000:00:1f.0: [8086:24c0] type 00 class 0x060100            
            [    0.117137] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,            
            [    0.117137] * this clock source is slow. If you are sure your timer does not have            
            [    0.117137] * this bug, please use "acpi_pm_good" to disable the workaround            
            [    0.117216] pci 0000:00:1f.0: address space collision: [io  0xf800-0xf87f] conflicts with ACPI CPU throttle [??? 0x0000f810-0x0000f815 flags 0x80000000]            
            [    0.117225] pci 0000:00:1f.0: quirk: [io  0xfa00-0xfa3f] claimed by ICH4 GPIO            
            [    0.117308] pci 0000:00:1f.1: [8086:24cb] type 00 class 0x01018a            
            [    0.117327] pci 0000:00:1f.1: reg 0x10: [io  0x24b0-0x24b7]            
            [    0.117341] pci 0000:00:1f.1: reg 0x14: [io  0x24c0-0x24c3]            
            [    0.117355] pci 0000:00:1f.1: reg 0x18: [io  0x24b8-0x24bf]            
            [    0.117369] pci 0000:00:1f.1: reg 0x1c: [io  0x24c4-0x24c7]            
            [    0.117384] pci 0000:00:1f.1: reg 0x20: [io  0x24a0-0x24af]            
            [    0.117398] pci 0000:00:1f.1: reg 0x24: [mem 0x00000000-0x000003ff]            
            [    0.117504] pci 0000:00:1f.5: [8086:24c5] type 00 class 0x040100            
            [    0.117525] pci 0000:00:1f.5: reg 0x10: [io  0x2000-0x20ff]            
            [    0.117539] pci 0000:00:1f.5: reg 0x14: [io  0x2400-0x243f]            
            [    0.117552] pci 0000:00:1f.5: reg 0x18: [mem 0xfc480400-0xfc4805ff]            
            [    0.117566] pci 0000:00:1f.5: reg 0x1c: [mem 0xfc480600-0xfc4806ff]            
            [    0.117620] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold            
            [    0.117763] pci 0000:05:08.0: [8086:1039] type 00 class 0x020000            
            [    0.117784] pci 0000:05:08.0: reg 0x10: [mem 0xfc500000-0xfc500fff]            
            [    0.117798] pci 0000:05:08.0: reg 0x14: [io  0x1400-0x143f]            
            [    0.117866] pci 0000:05:08.0: supports D1 D2            
            [    0.117871] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold            
            [    0.117953] pci 0000:05:09.0: [11c1:044c] type 00 class 0x078000            
            [    0.117975] pci 0000:05:09.0: reg 0x10: [mem 0xfc501000-0xfc5010ff]            
            [    0.117989] pci 0000:05:09.0: reg 0x14: [io  0x1440-0x1447]            
            [    0.118003] pci 0000:05:09.0: reg 0x18: [io  0x1000-0x10ff]            
            [    0.118067] pci 0000:05:09.0: supports D2            
            [    0.118072] pci 0000:05:09.0: PME# supported from D2 D3hot            
            [    0.118161] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)            
            [    0.118169] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]            
            [    0.118177] pci 0000:00:1e.0:   bridge window [mem 0xfc500000-0xfc7fffff]            
            [    0.118185] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)            
            [    0.118191] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)            
            [    0.118205] pci_bus 0000:00: on NUMA node 0            
            [    0.118783] ACPI: \_SB_.PCI0: notify handler is installed            
            [    0.118808] Found 1 acpi root devices            
            [    0.119048] vgaarb: setting as boot device: PCI:0000:00:02.0            
            [    0.119053] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none            
            [    0.119058] vgaarb: loaded            
            [    0.119062] vgaarb: bridge control possible 0000:00:02.0            
            [    0.119488] SCSI subsystem initialized            
            [    0.119610] libata version 3.00 loaded.            
            [    0.119663] ACPI: bus type USB registered            
            [    0.119708] usbcore: registered new interface driver usbfs            
            [    0.119726] usbcore: registered new interface driver hub            
            [    0.119770] usbcore: registered new device driver usb            
            [    0.120011] PCI: Using ACPI for IRQ routing            
            [    0.120155] PCI: pci_cache_line_size set to 64 bytes            
            [    0.120205] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]            
            [    0.120212] e820: reserve RAM buffer [mem 0x4f7f0000-0x4fffffff]            
            [    0.120406] NetLabel: Initializing            
            [    0.120411] NetLabel:  domain hash size = 128            
            [    0.120414] NetLabel:  protocols = UNLABELED CIPSOv4            
            [    0.120439] NetLabel:  unlabeled traffic allowed by default            
            [    0.120674] Switched to clocksource refined-jiffies            
            [    0.133895] AppArmor: AppArmor Filesystem Enabled            
            [    0.134012] pnp: PnP ACPI init            
            [    0.134046] ACPI: bus type PNP registered            
            [    0.134483] pnp 00:00: Plug and Play ACPI device, IDs PNP0c04 (active)            
            [    0.134510] pnp 00:01: [dma 4]            
            [    0.134542] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)            
            [    0.134597] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)            
            [    0.134641] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)            
            [    0.134690] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active)            
            [    0.134747] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)            
            [    0.135153] pnp 00:06: [dma 3]            
            [    0.135260] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)            
            [    0.135652] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)            
            [    0.135910] pnp 00:08: [dma 2]            
            [    0.135967] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)            
            [    0.136121] pnp 00:09: Plug and Play ACPI device, IDs PNP0003 (active)            
            [    0.136229] system 00:0a: [io  0x04d0-0x04d1] has been reserved            
            [    0.136236] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)            
            [    0.136277] pnp 00:0b: disabling [io  0xf800-0xf81f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]            
            [    0.136284] pnp 00:0b: disabling [io  0xf820-0xf83f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]            
            [    0.136290] pnp 00:0b: disabling [io  0xf840-0xf85f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]            
            [    0.136297] pnp 00:0b: disabling [io  0xf860-0xf87f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]            
            [    0.136342] system 00:0b: [io  0x0400-0x041f] has been reserved            
            [    0.136349] system 00:0b: [io  0x0420-0x043f] has been reserved            
            [    0.136355] system 00:0b: [io  0x0440-0x045f] has been reserved            
            [    0.136361] system 00:0b: [io  0x0460-0x047f] has been reserved            
            [    0.136367] system 00:0b: [io  0xfa00-0xfa3f] has been reserved            
            [    0.136374] system 00:0b: [io  0xfc00-0xfc7f] has been reserved            
            [    0.136380] system 00:0b: [io  0xfc80-0xfcff] has been reserved            
            [    0.136386] system 00:0b: [io  0xfe00-0xfe7f] has been reserved            
            [    0.136392] system 00:0b: [io  0xfe80-0xfeff] has been reserved            
            [    0.136398] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)            
            [    0.136821] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved            
            [    0.136828] system 00:0c: [mem 0x00100000-0x4f7fffff] could not be reserved            
            [    0.136835] system 00:0c: [mem 0x4f800000-0x4f8fffff] could not be reserved            
            [    0.136841] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved            
            [    0.136848] system 00:0c: [mem 0xfec01000-0xffffffff] has been reserved            
            [    0.136854] system 00:0c: [mem 0x000cc400-0x000dffff] has been reserved            
            [    0.136860] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)            
            [    0.136873] pnp: PnP ACPI: found 13 devices            
            [    0.136877] ACPI: bus type PNP unregistered            
            [    0.136885] PnPBIOS: Disabled by ACPI PNP            
            [    0.174273] Switched to clocksource acpi_pm            
            [    0.174314] pci 0000:00:1f.0: BAR 13: [io  0xf800-0xf87f] has bogus alignment            
            [    0.174331] pci 0000:00:1f.1: BAR 5: assigned [mem 0x50000000-0x500003ff]            
            [    0.174343] pci 0000:00:1e.0: PCI bridge to [bus 05]            
            [    0.174351] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]            
            [    0.174360] pci 0000:00:1e.0:   bridge window [mem 0xfc500000-0xfc7fffff]            
            [    0.174374] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]            
            [    0.174379] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]            
            [    0.174386] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]            
            [    0.174391] pci_bus 0000:05: resource 1 [mem 0xfc500000-0xfc7fffff]            
            [    0.174397] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]            
            [    0.174402] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]            
            [    0.174483] NET: Registered protocol family 2            
            [    0.174938] TCP established hash table entries: 8192 (order: 3, 32768 bytes)            
            [    0.174983] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)            
            [    0.175056] TCP: Hash tables configured (established 8192 bind 8192)            
            [    0.175169] TCP: reno registered            
            [    0.175177] UDP hash table entries: 512 (order: 2, 16384 bytes)            
            [    0.175199] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)            
            [    0.175312] NET: Registered protocol family 1            
            [    0.175346] pci 0000:00:02.0: Video device with shadowed ROM            
            [    0.175346] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling            
            [    0.175346] PCI: CLS 64 bytes, default 64            
            [    0.175346] Trying to unpack rootfs image as initramfs...            
            [    0.805458] Freeing initrd memory: 18344K (f5c1c000 - f6e06000)            
            [    0.805908] microcode: CPU0 sig=0xf27, pf=0x4, revision=0x37            
            [    0.806028] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba            
            [    0.806034] Scanning for low memory corruption every 60 seconds            
            [    0.806475] Initialise system trusted keyring            
            [    0.806573] audit: initializing netlink socket (disabled)            
            [    0.806604] type=2000 audit(1430504617.803:1): initialized            
            [    0.837300] bounce pool size: 64 pages            
            [    0.837322] HugeTLB registered 2 MB page size, pre-allocated 0 pages            
            [    0.839481] zbud: loaded            
            [    0.839653] VFS: Disk quotas dquot_6.5.2            
            [    0.839754] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)            
            [    0.840635] fuse init (API version 7.22)            
            [    0.840778] msgmni has been set to 1733            
            [    0.840897] Key type big_key registered            
            [    0.841470] Key type asymmetric registered            
            [    0.841475] Asymmetric key parser 'x509' registered            
            [    0.841566] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)            
            [    0.841627] io scheduler noop registered            
            [    0.841631] io scheduler deadline registered (default)            
            [    0.841688] io scheduler cfq registered            
            [    0.841894] pci_hotplug: PCI Hot Plug PCI Core version: 0.5            
            [    0.841923] pciehp: PCI Express Hot Plug Controller Driver version: 0.4            
            [    0.842006] vesafb: mode is 1024x768x32, linelength=4096, pages=0            
            [    0.842010] vesafb: scrolling: redraw            
            [    0.842015] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0            
            [    0.842347] vesafb: framebuffer at 0xf0000000, mapped to 0xf8400000, using 3072k, total 3072k            
            [    0.908550] Console: switching to colour frame buffer device 128x48            
            [    0.974522] fb0: VESA VGA frame buffer device            
            [    0.974586] ipmi message handler version 39.2            
            [    0.974719] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0            
            [    0.974735] ACPI: Power Button [PBTN]            
            [    0.974804] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1            
            [    0.974810] ACPI: Power Button [PWRF]            
            [    0.975034] GHES: HEST is not enabled!            
            [    0.975211] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled            
            [    0.995719] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A            
            [    0.995795] isapnp: Scanning for PnP cards...            
            [    1.047037] Linux agpgart interface v0.103            
            [    1.047123] agpgart-intel 0000:00:00.0: Intel 845G Chipset            
            [    1.047159] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable            
            [    1.047358] agpgart-intel 0000:00:00.0: detected 8192K stolen memory            
            [    1.047597] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000            
            [    1.049995] brd: module loaded            
            [    1.051232] loop: module loaded            
            [    1.051520] ata_piix 0000:00:1f.1: version 2.13            
            [    1.051542] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)            
            [    1.052487] scsi0 : ata_piix            
            [    1.052609] scsi1 : ata_piix            
            [    1.052679] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x24a0 irq 14            
            [    1.052684] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x24a8 irq 15            
            [    1.053255] libphy: Fixed MDIO Bus: probed            
            [    1.053445] tun: Universal TUN/TAP device driver, 1.6            
            [    1.053449] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>            
            [    1.053634] PPP generic driver version 2.4.2            
            [    1.053716] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver            
            [    1.053728] ehci-pci: EHCI PCI platform driver            
            [    1.053972] ehci-pci 0000:00:1d.7: EHCI Host Controller            
            [    1.053986] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1            
            [    1.054014] ehci-pci 0000:00:1d.7: debug port 1            
            [    1.057945] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported            
            [    1.058175] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfc480000            
            [    1.101788] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00            
            [    1.189077] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002            
            [    1.189083] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1            
            [    1.189088] usb usb1: Product: EHCI Host Controller            
            [    1.189093] usb usb1: Manufacturer: Linux 3.13.0-51-generic ehci_hcd            
            [    1.189098] usb usb1: SerialNumber: 0000:00:1d.7            
            [    1.189315] hub 1-0:1.0: USB hub found            
            [    1.189330] hub 1-0:1.0: 6 ports detected            
            [    1.189593] ehci-platform: EHCI generic platform driver            
            [    1.189622] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver            
            [    1.189626] ohci-pci: OHCI PCI platform driver            
            [    1.189649] ohci-platform: OHCI generic platform driver            
            [    1.189663] uhci_hcd: USB Universal Host Controller Interface driver            
            [    1.189859] uhci_hcd 0000:00:1d.0: UHCI Host Controller            
            [    1.189870] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2            
            [    1.189921] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00002440            
            [    1.190024] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001            
            [    1.190030] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1            
            [    1.190035] usb usb2: Product: UHCI Host Controller            
            [    1.190040] usb usb2: Manufacturer: Linux 3.13.0-51-generic uhci_hcd            
            [    1.190045] usb usb2: SerialNumber: 0000:00:1d.0            
            [    1.190225] hub 2-0:1.0: USB hub found            
            [    1.190239] hub 2-0:1.0: 2 ports detected            
            [    1.190517] uhci_hcd 0000:00:1d.1: UHCI Host Controller            
            [    1.190528] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3            
            [    1.190572] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002460            
            [    1.190661] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001            
            [    1.190666] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1            
            [    1.190671] usb usb3: Product: UHCI Host Controller            
            [    1.190676] usb usb3: Manufacturer: Linux 3.13.0-51-generic uhci_hcd            
            [    1.190681] usb usb3: SerialNumber: 0000:00:1d.1            
            [    1.190863] hub 3-0:1.0: USB hub found            
            [    1.190878] hub 3-0:1.0: 2 ports detected            
            [    1.191170] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12            
            [    1.237613] serio: i8042 KBD port at 0x60,0x64 irq 1            
            [    1.237628] serio: i8042 AUX port at 0x60,0x64 irq 12            
            [    1.325574] isapnp: No Plug & Play device found            
            [    1.326384] mousedev: PS/2 mouse device common for all mice            
            [    1.326600] rtc_cmos 00:02: RTC can wake from S4            
            [    1.326756] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0            
            [    1.326797] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram            
            [    1.326944] device-mapper: uevent: version 1.0.3            
            [    1.327058] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com            
            [    1.327108] platform eisa.0: Probing EISA bus 0            
            [    1.327121] platform eisa.0: Cannot allocate resource for EISA slot 1            
            [    1.327127] platform eisa.0: Cannot allocate resource for EISA slot 2            
            [    1.327160] platform eisa.0: EISA: Detected 0 cards            
            [    1.327179] cpufreq-nforce2: No nForce2 chipset.            
            [    1.327186] ledtrig-cpu: registered to indicate activity on CPUs            
            [    1.327409] TCP: cubic registered            
            [    1.327577] NET: Registered protocol family 10            
            [    1.327929] NET: Registered protocol family 17            
            [    1.327955] Key type dns_resolver registered            
            [    1.328338] Using IPI No-Shortcut mode            
            [    1.328479] Loading compiled-in X.509 certificates            
            [    1.335652] Loaded X.509 cert 'Magrathea: Glacier signing key: 1f88723dce4086a12303dadd54a7ae35e9e44d58'            
            [    1.335681] registered taskstats version 1            
            [    1.340615] Key type trusted registered            
            [    1.349752] Key type encrypted registered            
            [    1.349765] AppArmor: AppArmor sha1 policy hashing enabled            
            [    1.349771] IMA: No TPM chip found, activating TPM-bypass!            
            [    1.350013] regulator-dummy: disabling            
            [    1.350112]   Magic number: 15:798:391            
            [    1.350130] hub 3-0:1.0: hash matches            
            [    1.350265] rtc_cmos 00:02: setting system clock to 2015-05-01 18:23:38 UTC (1430504618)            
            [    1.350403] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found            
            [    1.350407] EDD information not available.            
            [    1.350453] PM: Hibernation image not present or could not be loaded.            
            [    1.358703] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2            
            [    1.374006] ata1.00: ATA-7: ST3160215ACE, 3.ARC, max UDMA/100            
            [    1.374013] ata1.00: 312581808 sectors, multi 16: LBA48            
            [    1.374027] ata1.01: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100            
            [    1.374032] ata1.01: 78165360 sectors, multi 16: LBA            
            [    1.440569] ata1.00: configured for UDMA/100            
            [    1.456186] ata1.01: configured for UDMA/100            
            [    1.456407] scsi 0:0:0:0: Direct-Access     ATA      ST3160215ACE     3.AR PQ: 0 ANSI: 5            
            [    1.456716] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)            
            [    1.456830] sd 0:0:0:0: [sda] Write Protect is off            
            [    1.456837] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00            
            [    1.456885] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA            
            [    1.457147] sd 0:0:0:0: Attached scsi generic sg0 type 0            
            [    1.496875]  sda: sda1            
            [    1.496954] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5            
            [    1.497329] sd 0:0:1:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)            
            [    1.497614] sd 0:0:1:0: [sdb] Write Protect is off            
            [    1.497621] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00            
            [    1.497669] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA            
            [    1.497779] sd 0:0:1:0: Attached scsi generic sg1 type 0            
            [    1.498229] sd 0:0:0:0: [sda] Attached SCSI disk            
            [    1.521559]  sdb: sdb1            
            [    1.521972] sd 0:0:1:0: [sdb] Attached SCSI disk            
            [    1.804044] tsc: Refined TSC clocksource calibration: 2391.437 MHz            
            [    2.804115] Switched to clocksource tsc            
            [    6.084016] ata2: link is slow to respond, please be patient (ready=0)            
            [   11.068014] ata2: device not ready (errno=-16), forcing hardreset            
            [   16.264014] ata2: link is slow to respond, please be patient (ready=0)            
            [   21.080015] ata2: SRST failed (errno=-16)            
            [   26.276014] ata2: link is slow to respond, please be patient (ready=0)            
            [   31.092015] ata2: SRST failed (errno=-16)            
            [   36.288015] ata2: link is slow to respond, please be patient (ready=0)            
            [   66.136016] ata2: SRST failed (errno=-16)            
            [   71.164015] ata2: SRST failed (errno=-16)            
            [   71.175203] ata2: reset failed, giving up            
            [   71.176830] Freeing unused kernel memory: 880K (c19bd000 - c1a99000)            
            [   71.176903] Write protecting the kernel text: 6556k            
            [   71.176998] Write protecting the kernel read-only data: 2772k            
            [   71.212501] systemd-udevd[95]: starting version 204            
            [   71.324767] Floppy drive(s): fd0 is 1.44M            
            [   71.342216] FDC 0 is a post-1991 82077            
            [   71.376309] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI            
            [   71.376316] e100: Copyright(c) 1999-2006 Intel Corporation            
            [   71.403058] e100 0000:05:08.0 eth0: addr 0xfc500000, irq 20, MAC addr 00:0b:cd:06:7f:28            
            [   72.543152] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4            
            [   77.075910] EXT4-fs (sda1): mounting ext3 file system using the ext4 subsystem            
            [   77.118169] random: nonblocking pool is initialized            
            [   77.119743] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)            
            [   97.299144] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready            
            [   98.052430] systemd-udevd[258]: starting version 204            
            [   99.303448] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro            
            [   99.793636] parport_pc 00:06: reported by Plug and Play ACPI            
            [   99.793698] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]            
            [   99.939355] lp0: using parport0 (interrupt-driven).            
            [  100.084306] ppdev: user-space parallel port driver            
            [  100.348089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4            
            [  100.362667] intel_rng: Firmware space is locked read-only. If you can't or            
            [  100.362667] intel_rng: don't want to disable this in firmware setup, and if            
            [  100.362667] intel_rng: you are certain that your system has a functional            
            [  100.362667] intel_rng: RNG, try using the 'no_fwh_detect' option.            
            [  100.888199] ACPI Warning: 0x0000f828-0x0000f82f SystemIO conflicts with Region \ICHP 1 (20131115/utaddress-251)            
            [  100.888214] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver            
            [  100.889017] lpc_ich: Resource conflict(s) found affecting gpio_ich            
            [  101.235215] [drm] Initialized drm 1.1.0 20060810            
            [  101.257999] type=1400 audit(1430497518.404:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=324 comm="apparmor_parser"            
            [  101.258016] type=1400 audit(1430497518.404:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=324 comm="apparmor_parser"            
            [  101.258026] type=1400 audit(1430497518.404:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=324 comm="apparmor_parser"            
            [  101.259211] type=1400 audit(1430497518.404:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=324 comm="apparmor_parser"            
            [  101.259225] type=1400 audit(1430497518.404:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=324 comm="apparmor_parser"            
            [  101.259799] type=1400 audit(1430497518.404:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=324 comm="apparmor_parser"            
            [  101.267328] type=1400 audit(1430497518.412:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=327 comm="apparmor_parser"            
            [  102.437615] [drm] Memory usable by graphics device = 128M            
            [  102.437627] checking generic (f0000000 300000) vs hw (f0000000 8000000)            
            [  102.437631] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver            
            [  102.437685] Console: switching to colour dummy device 80x25            
            [  102.441091] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).            
            [  102.441097] [drm] Driver supports precise vblank timestamp query.            
            [  102.441189] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem            
            [  102.453149] [drm] initialized overlay support            
            [  102.533733] fbcon: inteldrmfb (fb0) is primary device            
            [  102.565454] ip_tables: (C) 2000-2006 Netfilter Core Team            
            [  102.592089] Console: switching to colour frame buffer device 128x48            
            [  102.596965] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device            
            [  102.596970] i915 0000:00:02.0: registered panic notifier            
            [  102.596995] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0            
            [  102.984887] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)            
            [  103.492031] intel8x0_measure_ac97_clock: measured 55864 usecs (2691 samples)            
            [  103.492040] intel8x0: clocking to 48000            
            [  103.809338] ip6_tables: (C) 2000-2006 Netfilter Core Team            
            [  106.660234] Bluetooth: Core ver 2.17            
            [  106.660344] NET: Registered protocol family 31            
            [  106.660348] Bluetooth: HCI device and connection manager initialized            
            [  106.660372] Bluetooth: HCI socket layer initialized            
            [  106.660379] Bluetooth: L2CAP socket layer initialized            
            [  106.660390] Bluetooth: SCO socket layer initialized            
            [  106.683943] init: failsafe main process (477) killed by TERM signal            
            [  106.888877] Bluetooth: BNEP (Ethernet Emulation) ver 1.3            
            [  106.888886] Bluetooth: BNEP filters: protocol multicast            
            [  106.888909] Bluetooth: BNEP socket layer initialized            
            [  107.034165] Bluetooth: RFCOMM TTY layer initialized            
            [  107.034197] Bluetooth: RFCOMM socket layer initialized            
            [  107.034220] Bluetooth: RFCOMM ver 1.11            
            [  107.489890] type=1400 audit(1430497524.636:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=681 comm="apparmor_parser"            
            [  107.489907] type=1400 audit(1430497524.636:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=681 comm="apparmor_parser"            
            [  107.491202] type=1400 audit(1430497524.636:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=681 comm="apparmor_parser"            
            [  108.462437] type=1400 audit(1430497525.608:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=749 comm="apparmor_parser"            
            [  108.462457] type=1400 audit(1430497525.608:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=749 comm="apparmor_parser"            
            [  108.463232] type=1400 audit(1430497525.608:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=749 comm="apparmor_parser"            
            [  108.499939] type=1400 audit(1430497525.644:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=750 comm="apparmor_parser"            
            [  108.499962] type=1400 audit(1430497525.644:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=750 comm="apparmor_parser"            
            [  108.499973] type=1400 audit(1430497525.644:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=750 comm="apparmor_parser"            
            [  108.502261] type=1400 audit(1430497525.648:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=750 comm="apparmor_parser"            
            [  108.975190] init: cups main process (683) killed by HUP signal            
            [  108.975222] init: cups main process ended, respawning            
            [  112.329164] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready            
            [  112.330313] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready            
            [  112.332232] e100 0000:05:08.0 eth0: NIC Link is Up 100 Mbps Full Duplex            
            [  112.332732] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready            
            [  123.365233] init: plymouth-upstart-bridge main process ended, respawning            
            [  123.417799] init: plymouth-upstart-bridge main process ended, respawning            
            [  138.009854] audit_printk_skb: 87 callbacks suppressed            
            [  138.009863] type=1400 audit(1430497555.157:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1667 comm="apparmor_parser"            
            [  138.009881] type=1400 audit(1430497555.157:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1667 comm="apparmor_parser"            
            [  138.011169] type=1400 audit(1430497555.157:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1667 comm="apparmor_parser"            
            

```

Thank you very much !

---

### Post by TheFu on 2015-05-01
I'd check the cables are seated in correctly. If that doesn't change anything, swap the cable out.
Drive cables sometimes do go bad. Look for crimps or bad bends - replace if there is an question the cable may have been compromised. Sometimes interfaces on these devices fail too.
If that doesn't help - is this SATA or IDE? If IDE, verify the pri/sec switch on the drive is set correctly or CS (cable select) is set.

---

### Post by viktor5 on 2015-05-02
I unplugged the cd rom drive and that cutted down the boot of 1 minute,
which is good, (the hdd are all IDE),

Thank you !

Now the other thing that is taking a lot of time is [FONT=Times New Roman]**random: nonblocking pool is initialized**[/FONT]

                                                    ```
[FONT=Times New Roman]**[    7.165928] EXT4-fs (sda1): mounting ext3 file system using the ext4 subsystem**[/FONT]            
            [FONT=Times New Roman]**[    7.210056] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)**[/FONT]            
            [FONT=Times New Roman]**[    8.722671] random: nonblocking pool is initialized**[/FONT]            
            [FONT=Times New Roman]**[   27.393285] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready**[/FONT]
```

Is there anything I can do for this problem ?

The whole dmesg:

                                        ```
[FONT=Times New Roman]**Initializing cgroup subsys cpuset**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Initializing cgroup subsys cpu**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Initializing cgroup subsys cpuacct**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Linux version 3.13.0-51-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #84-Ubuntu SMP Wed Apr 15 12:11:46 UTC 2015 (Ubuntu 3.13.0-51.84-generic 3.13.11-ckt18)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] KERNEL supported cpus:**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Intel GenuineIntel**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   AMD AuthenticAMD**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   NSC Geode by NSC**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Cyrix CyrixInstead**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Centaur CentaurHauls**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Transmeta GenuineTMx86**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Transmeta TransmetaCPU**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   UMC UMC UMC UMC**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] e820: BIOS-provided physical RAM map:**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000004f7effff] usable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BIOS-e820: [mem 0x000000004f7f0000-0x000000004f7fffff] reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] SMBIOS 2.3 present.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] DMI: Compaq Evo D310/0804h, BIOS 686O2 v2.18 09/24/2002**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] e820: last_pfn = 0x4f7f0 max_arch_pfn = 0x1000000**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] MTRR default type: uncachable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] MTRR fixed ranges enabled:**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   00000-9FFFF write-back**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   A0000-BFFFF uncachable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   C0000-CFFFF write-protect**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   D0000-DFFFF uncachable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   E0000-EFFFF write-back**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   F0000-FFFFF write-protect**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] MTRR variable ranges enabled:**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   0 base 04F800000 mask FFF800000 uncachable**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   1 base 000000000 mask FC0000000 write-back**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   2 base 040000000 mask FF0000000 write-back**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   3 base 0FEDA0000 mask FFFFE0000 write-back**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   4 disabled**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   5 disabled**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   6 disabled**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   7 disabled**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] original variable MTRRs**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 0, base: 1272MB, range: 8MB, type UC**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 1, base: 0GB, range: 1GB, type WB**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 2, base: 1GB, range: 256MB, type WB**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 3, base: 4175488KB, range: 128KB, type WB**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] total RAM covered: 1272M**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Found optimal setting for mtrr clean up**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  gran_size: 64K chunk_size: 16M num_reg: 4  lose cover RAM: 0G**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] New variable MTRRs**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 0, base: 0GB, range: 1GB, type WB**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 1, base: 1GB, range: 256MB, type WB**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 2, base: 1272MB, range: 8MB, type UC**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] reg 3, base: 4175488KB, range: 128KB, type WB**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] e820: update [mem 0x4f800000-0xfed9ffff] usable ==> reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] found SMP MP-table at [mem 0x000f9bf0-0x000f9bff] mapped at [c00f9bf0]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Scanning 1 areas for low memory corruption**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  [mem 0x00000000-0x000fffff] page 4k**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  [mem 0x37800000-0x379fffff] page 2M**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  [mem 0x34000000-0x377fffff] page 2M**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  [mem 0x00100000-0x001fffff] page 4k**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BRK [0x01b99000, 0x01b99fff] PGTABLE**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] RAMDISK: [mem 0x35c1c000-0x36e05fff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: RSDP 000eaa10 000014 (v00 COMPAQ)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: RSDT 000e6740 000070 (v01 COMPAQ CPQ0053  20020924      00000000)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: FACP 000e67f8 000074 (v01 COMPAQ BROOKDG  00000001      00000000)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: DSDT 000e68c6 000B73 (v01 COMPAQ     DSDT 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: FACS 000e6700 000040**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e7439 00073D (v01 COMPAQ  PROJECT 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e7b76 00053A (v01 COMPAQ CORE_PNP 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e80b0 00019B (v01 COMPAQ CORE_UTL 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e824b 000308 (v01 COMPAQ VILLTBL1 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e8553 00053F (v01 COMPAQ LGCYLITE 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e8a92 000167 (v01 COMPAQ    UART2 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e8bf9 00014E (v01 COMPAQ   FLOPPY 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: APIC 000e686c 00005A (v01 COMPAQ BROOKDG  00000001      00000000)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000ea6be 0000B2 (v01 COMPAQ     APIC 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e91b5 000424 (v01 COMPAQ PNP_PRSS 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e95d9 00016D (v01 COMPAQ UR2_PRSS 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e9746 000119 (v01 COMPAQ FPY_PRSS 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e98f7 000135 (v01 COMPAQ       S3 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e9a2c 00013B (v01 COMPAQ  CORE_S3 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e9b67 000173 (v01 COMPAQ   PIDETM 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000e9e52 000180 (v01 COMPAQ     GTF0 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000ea461 0000F0 (v01 COMPAQ      L08 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: SSDT 000ea859 000053 (v01 COMPAQ    FINIS 00000001 MSFT 0100000E)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: Local APIC address 0xfee00000**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] 379MB HIGHMEM available.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] 891MB LOWMEM available.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   mapped low ram: 0 - 37bfe000**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   low ram: 0 - 37bfe000**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] BRK [0x01b9a000, 0x01b9afff] PGTABLE**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Zone ranges:**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   HighMem  [mem 0x37bfe000-0x4f7effff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Movable zone start for each node**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Early memory node ranges**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   node   0: [mem 0x00001000-0x0009efff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   node   0: [mem 0x00100000-0x4f7effff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] On node 0 totalpages: 325518**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] free_area_init_node: node 0, pgdat c199f780, node_mem_map f720e020**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   DMA zone: 32 pages used for memmap**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   DMA zone: 0 pages reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   DMA zone: 3998 pages, LIFO batch:0**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Normal zone: 1752 pages used for memmap**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   Normal zone: 224254 pages, LIFO batch:31**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   HighMem zone: 760 pages used for memmap**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]   HighMem zone: 97266 pages, LIFO batch:31**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Using APIC driver default**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: PM-Timer IO Port: 0xf808**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: Local APIC address 0xfee00000**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: IRQ0 used by override.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: IRQ2 used by override.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] ACPI: IRQ9 used by override.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Using ACPI (MADT) for SMP configuration information**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] nr_irqs_gsi: 40**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] e820: [mem 0x4f800000-0xfebfffff] available for PCI devices**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Booting paravirtualized kernel on bare hardware**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] PERCPU: Embedded 14 pages/cpu @f71f9000 s35520 r0 d21824 u57344**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] pcpu-alloc: s35520 r0 d21824 u57344 alloc=14*4096**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] pcpu-alloc: [0] 0**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 323734**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-51-generic root=UUID=e11b218b-b7ce-404b-ad8b-d63ee0888e62 ro quiet splash vt.handoff=7**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] CPU0 microcode updated early to revision 0x37, date = 2003-06-04**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Initializing CPU#0**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] allocated 2604920 bytes of page_cgroup**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Initializing HighMem for node 0 (00037bfe:0004f7f0)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Memory: 1258164K/1302072K available (6553K kernel code, 641K rwdata, 2768K rodata, 880K init, 924K bss, 43908K reserved, 389064K highmem)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] virtual kernel memory layout:**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]       .init : 0xc19bd000 - 0xc1a99000   ( 880 kB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]       .data : 0xc16667b4 - 0xc19bc600   (3415 kB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000]       .text : 0xc1000000 - 0xc16667b4   (6553 kB)**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] SLUB: HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Hierarchical RCU implementation.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] RCU dyntick-idle grace-period acceleration is enabled.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] NR_IRQS:2304 nr_irqs:256 16**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] Console: colour dummy device 80x25**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] console [tty0] enabled**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] tsc: Fast TSC calibration using PIT**[/FONT]            
            [FONT=Times New Roman]**[    0.000000] tsc: Detected 2391.420 MHz processor**[/FONT]            
            [FONT=Times New Roman]**[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4782.84 BogoMIPS (lpj=9565680)**[/FONT]            
            [FONT=Times New Roman]**[    0.004012] pid_max: default: 32768 minimum: 301**[/FONT]            
            [FONT=Times New Roman]**[    0.004072] Security Framework initialized**[/FONT]            
            [FONT=Times New Roman]**[    0.004121] AppArmor: AppArmor initialized**[/FONT]            
            [FONT=Times New Roman]**[    0.004126] Yama: becoming mindful.**[/FONT]            
            [FONT=Times New Roman]**[    0.004234] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.004240] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.004698] Initializing cgroup subsys memory**[/FONT]            
            [FONT=Times New Roman]**[    0.004720] Initializing cgroup subsys devices**[/FONT]            
            [FONT=Times New Roman]**[    0.004726] Initializing cgroup subsys freezer**[/FONT]            
            [FONT=Times New Roman]**[    0.004733] Initializing cgroup subsys blkio**[/FONT]            
            [FONT=Times New Roman]**[    0.004740] Initializing cgroup subsys perf_event**[/FONT]            
            [FONT=Times New Roman]**[    0.004747] Initializing cgroup subsys hugetlb**[/FONT]            
            [FONT=Times New Roman]**[    0.004802] CPU0: Hyper-Threading is disabled**[/FONT]            
            [FONT=Times New Roman]**[    0.004810] mce: CPU supports 4 MCE banks**[/FONT]            
            [FONT=Times New Roman]**[    0.004827] CPU0: Thermal monitoring enabled (TM1)**[/FONT]            
            [FONT=Times New Roman]**[    0.004859] Last level iTLB entries: 4KB 128, 2MB 128, 4MB 128**[/FONT]            
            [FONT=Times New Roman]**[    0.004859] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 64**[/FONT]            
            [FONT=Times New Roman]**[    0.004859] tlb_flushall_shift: 6**[/FONT]            
            [FONT=Times New Roman]**[    0.032151] Freeing SMP alternatives memory: 32K (c1a99000 - c1aa1000)**[/FONT]            
            [FONT=Times New Roman]**[    0.033880] ACPI: Core revision 20131115**[/FONT]            
            [FONT=Times New Roman]**[    0.038289] ACPI: All ACPI Tables successfully acquired**[/FONT]            
            [FONT=Times New Roman]**[    0.038507] ftrace: allocating 27866 entries in 55 pages**[/FONT]            
            [FONT=Times New Roman]**[    0.052302] Enabling APIC mode:  Flat.  Using 1 I/O APICs**[/FONT]            
            [FONT=Times New Roman]**[    0.052672] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1**[/FONT]            
            [FONT=Times New Roman]**[    0.092944] smpboot: CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz (fam: 0f, model: 02, stepping: 07)**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... version:                0**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... bit width:              40**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... generic registers:      18**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... value mask:             000000ffffffffff**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... max period:             0000007fffffffff**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... fixed-purpose events:   0**[/FONT]            
            [FONT=Times New Roman]**[    0.096000] ... event mask:             000000000003ffff**[/FONT]            
            [FONT=Times New Roman]**[    0.096292] x86: Booted up 1 node, 1 CPUs**[/FONT]            
            [FONT=Times New Roman]**[    0.096302] smpboot: Total of 1 processors activated (4782.84 BogoMIPS)**[/FONT]            
            [FONT=Times New Roman]**[    0.096629] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.**[/FONT]            
            [FONT=Times New Roman]**[    0.096969] devtmpfs: initialized**[/FONT]            
            [FONT=Times New Roman]**[    0.097279] EVM: security.selinux**[/FONT]            
            [FONT=Times New Roman]**[    0.097283] EVM: security.SMACK64**[/FONT]            
            [FONT=Times New Roman]**[    0.097287] EVM: security.ima**[/FONT]            
            [FONT=Times New Roman]**[    0.097290] EVM: security.capability**[/FONT]            
            [FONT=Times New Roman]**[    0.099240] pinctrl core: initialized pinctrl subsystem**[/FONT]            
            [FONT=Times New Roman]**[    0.099416] regulator-dummy: no parameters**[/FONT]            
            [FONT=Times New Roman]**[    0.099456] RTC time: 19:20:23, date: 05/01/15**[/FONT]            
            [FONT=Times New Roman]**[    0.099539] NET: Registered protocol family 16**[/FONT]            
            [FONT=Times New Roman]**[    0.099852] EISA bus registered**[/FONT]            
            [FONT=Times New Roman]**[    0.099858] cpuidle: using governor ladder**[/FONT]            
            [FONT=Times New Roman]**[    0.099862] cpuidle: using governor menu**[/FONT]            
            [FONT=Times New Roman]**[    0.100128] ACPI: bus type PCI registered**[/FONT]            
            [FONT=Times New Roman]**[    0.100136] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5**[/FONT]            
            [FONT=Times New Roman]**[    0.100522] PCI: PCI BIOS revision 2.20 entry at 0xeca48, last bus=5**[/FONT]            
            [FONT=Times New Roman]**[    0.100526] PCI: Using configuration type 1 for base access**[/FONT]            
            [FONT=Times New Roman]**[    0.102531] bio: create slab <bio-0> at 0**[/FONT]            
            [FONT=Times New Roman]**[    0.102818] ACPI: Added _OSI(Module Device)**[/FONT]            
            [FONT=Times New Roman]**[    0.102823] ACPI: Added _OSI(Processor Device)**[/FONT]            
            [FONT=Times New Roman]**[    0.102827] ACPI: Added _OSI(3.0 _SCP Extensions)**[/FONT]            
            [FONT=Times New Roman]**[    0.102832] ACPI: Added _OSI(Processor Aggregator Device)**[/FONT]            
            [FONT=Times New Roman]**[    0.105250] ACPI: Interpreter enabled**[/FONT]            
            [FONT=Times New Roman]**[    0.105273] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)**[/FONT]            
            [FONT=Times New Roman]**[    0.105295] ACPI: (supports S0 S1 S3 S4 S5)**[/FONT]            
            [FONT=Times New Roman]**[    0.105299] ACPI: Using IOAPIC for interrupt routing**[/FONT]            
            [FONT=Times New Roman]**[    0.105353] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug**[/FONT]            
            [FONT=Times New Roman]**[    0.105460] ACPI: No dock devices found.**[/FONT]            
            [FONT=Times New Roman]**[    0.110993] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 14 15)**[/FONT]            
            [FONT=Times New Roman]**[    0.111113] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)**[/FONT]            
            [FONT=Times New Roman]**[    0.111228] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)**[/FONT]            
            [FONT=Times New Roman]**[    0.111343] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)**[/FONT]            
            [FONT=Times New Roman]**[    0.111457] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)**[/FONT]            
            [FONT=Times New Roman]**[    0.111571] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.**[/FONT]            
            [FONT=Times New Roman]**[    0.111686] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.**[/FONT]            
            [FONT=Times New Roman]**[    0.111802] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)**[/FONT]            
            [FONT=Times New Roman]**[    0.111963] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])**[/FONT]            
            [FONT=Times New Roman]**[    0.111975] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]**[/FONT]            
            [FONT=Times New Roman]**[    0.111986] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM**[/FONT]            
            [FONT=Times New Roman]**[    0.112238] acpi PNP0A03:00: host bridge window [mem 0x4f900000-0xfebfffff] (ignored)**[/FONT]            
            [FONT=Times New Roman]**[    0.112244] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)**[/FONT]            
            [FONT=Times New Roman]**[    0.112250] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)**[/FONT]            
            [FONT=Times New Roman]**[    0.112255] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)**[/FONT]            
            [FONT=Times New Roman]**[    0.112261] PCI: root bus 00: using default resources**[/FONT]            
            [FONT=Times New Roman]**[    0.112269] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.**[/FONT]            
            [FONT=Times New Roman]**[    0.112432] PCI host bridge to bus 0000:00**[/FONT]            
            [FONT=Times New Roman]**[    0.112439] pci_bus 0000:00: root bus resource [bus 00-ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.112445] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.112450] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.112474] pci 0000:00:00.0: [8086:2560] type 00 class 0x060000**[/FONT]            
            [FONT=Times New Roman]**[    0.112491] pci 0000:00:00.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]**[/FONT]            
            [FONT=Times New Roman]**[    0.112631] pci 0000:00:02.0: [8086:2562] type 00 class 0x030000**[/FONT]            
            [FONT=Times New Roman]**[    0.112651] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]**[/FONT]            
            [FONT=Times New Roman]**[    0.112664] pci 0000:00:02.0: reg 0x14: [mem 0xfc400000-0xfc47ffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.112834] pci 0000:00:1d.0: [8086:24c2] type 00 class 0x0c0300**[/FONT]            
            [FONT=Times New Roman]**[    0.112886] pci 0000:00:1d.0: reg 0x20: [io  0x2440-0x245f]**[/FONT]            
            [FONT=Times New Roman]**[    0.112955] pci 0000:00:1d.0: System wakeup disabled by ACPI**[/FONT]            
            [FONT=Times New Roman]**[    0.113009] pci 0000:00:1d.1: [8086:24c4] type 00 class 0x0c0300**[/FONT]            
            [FONT=Times New Roman]**[    0.113061] pci 0000:00:1d.1: reg 0x20: [io  0x2460-0x247f]**[/FONT]            
            [FONT=Times New Roman]**[    0.113126] pci 0000:00:1d.1: System wakeup disabled by ACPI**[/FONT]            
            [FONT=Times New Roman]**[    0.113200] pci 0000:00:1d.7: [8086:24cd] type 00 class 0x0c0320**[/FONT]            
            [FONT=Times New Roman]**[    0.113228] pci 0000:00:1d.7: reg 0x10: [mem 0xfc480000-0xfc4803ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.113333] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold**[/FONT]            
            [FONT=Times New Roman]**[    0.113381] pci 0000:00:1d.7: System wakeup disabled by ACPI**[/FONT]            
            [FONT=Times New Roman]**[    0.113439] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060400**[/FONT]            
            [FONT=Times New Roman]**[    0.113515] pci 0000:00:1e.0: System wakeup disabled by ACPI**[/FONT]            
            [FONT=Times New Roman]**[    0.113567] pci 0000:00:1f.0: [8086:24c0] type 00 class 0x060100**[/FONT]            
            [FONT=Times New Roman]**[    0.113573] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,**[/FONT]            
            [FONT=Times New Roman]**[    0.113573] * this clock source is slow. If you are sure your timer does not have**[/FONT]            
            [FONT=Times New Roman]**[    0.113573] * this bug, please use "acpi_pm_good" to disable the workaround**[/FONT]            
            [FONT=Times New Roman]**[    0.113652] pci 0000:00:1f.0: address space collision: [io  0xf800-0xf87f] conflicts with ACPI CPU throttle [??? 0x0000f810-0x0000f815 flags 0x80000000]**[/FONT]            
            [FONT=Times New Roman]**[    0.113661] pci 0000:00:1f.0: quirk: [io  0xfa00-0xfa3f] claimed by ICH4 GPIO**[/FONT]            
            [FONT=Times New Roman]**[    0.113749] pci 0000:00:1f.1: [8086:24cb] type 00 class 0x01018a**[/FONT]            
            [FONT=Times New Roman]**[    0.113768] pci 0000:00:1f.1: reg 0x10: [io  0x24b0-0x24b7]**[/FONT]            
            [FONT=Times New Roman]**[    0.113782] pci 0000:00:1f.1: reg 0x14: [io  0x24c0-0x24c3]**[/FONT]            
            [FONT=Times New Roman]**[    0.113796] pci 0000:00:1f.1: reg 0x18: [io  0x24b8-0x24bf]**[/FONT]            
            [FONT=Times New Roman]**[    0.113811] pci 0000:00:1f.1: reg 0x1c: [io  0x24c4-0x24c7]**[/FONT]            
            [FONT=Times New Roman]**[    0.113825] pci 0000:00:1f.1: reg 0x20: [io  0x24a0-0x24af]**[/FONT]            
            [FONT=Times New Roman]**[    0.113839] pci 0000:00:1f.1: reg 0x24: [mem 0x00000000-0x000003ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.113943] pci 0000:00:1f.5: [8086:24c5] type 00 class 0x040100**[/FONT]            
            [FONT=Times New Roman]**[    0.113964] pci 0000:00:1f.5: reg 0x10: [io  0x2000-0x20ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.113977] pci 0000:00:1f.5: reg 0x14: [io  0x2400-0x243f]**[/FONT]            
            [FONT=Times New Roman]**[    0.113991] pci 0000:00:1f.5: reg 0x18: [mem 0xfc480400-0xfc4805ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114004] pci 0000:00:1f.5: reg 0x1c: [mem 0xfc480600-0xfc4806ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114058] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold**[/FONT]            
            [FONT=Times New Roman]**[    0.114202] pci 0000:05:08.0: [8086:1039] type 00 class 0x020000**[/FONT]            
            [FONT=Times New Roman]**[    0.114223] pci 0000:05:08.0: reg 0x10: [mem 0xfc500000-0xfc500fff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114237] pci 0000:05:08.0: reg 0x14: [io  0x1400-0x143f]**[/FONT]            
            [FONT=Times New Roman]**[    0.114305] pci 0000:05:08.0: supports D1 D2**[/FONT]            
            [FONT=Times New Roman]**[    0.114310] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold**[/FONT]            
            [FONT=Times New Roman]**[    0.114393] pci 0000:05:09.0: [11c1:044c] type 00 class 0x078000**[/FONT]            
            [FONT=Times New Roman]**[    0.114415] pci 0000:05:09.0: reg 0x10: [mem 0xfc501000-0xfc5010ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114429] pci 0000:05:09.0: reg 0x14: [io  0x1440-0x1447]**[/FONT]            
            [FONT=Times New Roman]**[    0.114443] pci 0000:05:09.0: reg 0x18: [io  0x1000-0x10ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114506] pci 0000:05:09.0: supports D2**[/FONT]            
            [FONT=Times New Roman]**[    0.114511] pci 0000:05:09.0: PME# supported from D2 D3hot**[/FONT]            
            [FONT=Times New Roman]**[    0.114597] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)**[/FONT]            
            [FONT=Times New Roman]**[    0.114606] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114613] pci 0000:00:1e.0:   bridge window [mem 0xfc500000-0xfc7fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.114622] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)**[/FONT]            
            [FONT=Times New Roman]**[    0.114627] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)**[/FONT]            
            [FONT=Times New Roman]**[    0.114641] pci_bus 0000:00: on NUMA node 0**[/FONT]            
            [FONT=Times New Roman]**[    0.115217] ACPI: \_SB_.PCI0: notify handler is installed**[/FONT]            
            [FONT=Times New Roman]**[    0.115241] Found 1 acpi root devices**[/FONT]            
            [FONT=Times New Roman]**[    0.115483] vgaarb: setting as boot device: PCI:0000:00:02.0**[/FONT]            
            [FONT=Times New Roman]**[    0.115487] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none**[/FONT]            
            [FONT=Times New Roman]**[    0.115493] vgaarb: loaded**[/FONT]            
            [FONT=Times New Roman]**[    0.115497] vgaarb: bridge control possible 0000:00:02.0**[/FONT]            
            [FONT=Times New Roman]**[    0.115920] SCSI subsystem initialized**[/FONT]            
            [FONT=Times New Roman]**[    0.116054] libata version 3.00 loaded.**[/FONT]            
            [FONT=Times New Roman]**[    0.116103] ACPI: bus type USB registered**[/FONT]            
            [FONT=Times New Roman]**[    0.116151] usbcore: registered new interface driver usbfs**[/FONT]            
            [FONT=Times New Roman]**[    0.116170] usbcore: registered new interface driver hub**[/FONT]            
            [FONT=Times New Roman]**[    0.116215] usbcore: registered new device driver usb**[/FONT]            
            [FONT=Times New Roman]**[    0.116427] PCI: Using ACPI for IRQ routing**[/FONT]            
            [FONT=Times New Roman]**[    0.116571] PCI: pci_cache_line_size set to 64 bytes**[/FONT]            
            [FONT=Times New Roman]**[    0.116620] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.116626] e820: reserve RAM buffer [mem 0x4f7f0000-0x4fffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.116825] NetLabel: Initializing**[/FONT]            
            [FONT=Times New Roman]**[    0.116829] NetLabel:  domain hash size = 128**[/FONT]            
            [FONT=Times New Roman]**[    0.116831] NetLabel:  protocols = UNLABELED CIPSOv4**[/FONT]            
            [FONT=Times New Roman]**[    0.116857] NetLabel:  unlabeled traffic allowed by default**[/FONT]            
            [FONT=Times New Roman]**[    0.117088] Switched to clocksource refined-jiffies**[/FONT]            
            [FONT=Times New Roman]**[    0.130291] AppArmor: AppArmor Filesystem Enabled**[/FONT]            
            [FONT=Times New Roman]**[    0.130397] pnp: PnP ACPI init**[/FONT]            
            [FONT=Times New Roman]**[    0.130431] ACPI: bus type PNP registered**[/FONT]            
            [FONT=Times New Roman]**[    0.130871] pnp 00:00: Plug and Play ACPI device, IDs PNP0c04 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.130903] pnp 00:01: [dma 4]**[/FONT]            
            [FONT=Times New Roman]**[    0.130934] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.130983] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.131034] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.131083] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.131133] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.131536] pnp 00:06: [dma 3]**[/FONT]            
            [FONT=Times New Roman]**[    0.131648] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.132093] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.132357] pnp 00:08: [dma 2]**[/FONT]            
            [FONT=Times New Roman]**[    0.132408] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.132519] pnp 00:09: Plug and Play ACPI device, IDs PNP0003 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.132624] system 00:0a: [io  0x04d0-0x04d1] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132631] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.132665] pnp 00:0b: disabling [io  0xf800-0xf81f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]**[/FONT]            
            [FONT=Times New Roman]**[    0.132671] pnp 00:0b: disabling [io  0xf820-0xf83f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]**[/FONT]            
            [FONT=Times New Roman]**[    0.132678] pnp 00:0b: disabling [io  0xf840-0xf85f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]**[/FONT]            
            [FONT=Times New Roman]**[    0.132684] pnp 00:0b: disabling [io  0xf860-0xf87f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]**[/FONT]            
            [FONT=Times New Roman]**[    0.132735] system 00:0b: [io  0x0400-0x041f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132742] system 00:0b: [io  0x0420-0x043f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132748] system 00:0b: [io  0x0440-0x045f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132754] system 00:0b: [io  0x0460-0x047f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132760] system 00:0b: [io  0xfa00-0xfa3f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132766] system 00:0b: [io  0xfc00-0xfc7f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132773] system 00:0b: [io  0xfc80-0xfcff] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132779] system 00:0b: [io  0xfe00-0xfe7f] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132785] system 00:0b: [io  0xfe80-0xfeff] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.132791] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.133215] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.133223] system 00:0c: [mem 0x00100000-0x4f7fffff] could not be reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.133229] system 00:0c: [mem 0x4f800000-0x4f8fffff] could not be reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.133235] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.133241] system 00:0c: [mem 0xfec01000-0xffffffff] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.133248] system 00:0c: [mem 0x000cc400-0x000dffff] has been reserved**[/FONT]            
            [FONT=Times New Roman]**[    0.133254] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)**[/FONT]            
            [FONT=Times New Roman]**[    0.133267] pnp: PnP ACPI: found 13 devices**[/FONT]            
            [FONT=Times New Roman]**[    0.133270] ACPI: bus type PNP unregistered**[/FONT]            
            [FONT=Times New Roman]**[    0.133279] PnPBIOS: Disabled by ACPI PNP**[/FONT]            
            [FONT=Times New Roman]**[    0.170679] Switched to clocksource acpi_pm**[/FONT]            
            [FONT=Times New Roman]**[    0.170719] pci 0000:00:1f.0: BAR 13: [io  0xf800-0xf87f] has bogus alignment**[/FONT]            
            [FONT=Times New Roman]**[    0.170736] pci 0000:00:1f.1: BAR 5: assigned [mem 0x50000000-0x500003ff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170748] pci 0000:00:1e.0: PCI bridge to [bus 05]**[/FONT]            
            [FONT=Times New Roman]**[    0.170755] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170764] pci 0000:00:1e.0:   bridge window [mem 0xfc500000-0xfc7fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170778] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170784] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170790] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170796] pci_bus 0000:05: resource 1 [mem 0xfc500000-0xfc7fffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170802] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170807] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]**[/FONT]            
            [FONT=Times New Roman]**[    0.170888] NET: Registered protocol family 2**[/FONT]            
            [FONT=Times New Roman]**[    0.171340] TCP established hash table entries: 8192 (order: 3, 32768 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.171383] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.171461] TCP: Hash tables configured (established 8192 bind 8192)**[/FONT]            
            [FONT=Times New Roman]**[    0.171573] TCP: reno registered**[/FONT]            
            [FONT=Times New Roman]**[    0.171581] UDP hash table entries: 512 (order: 2, 16384 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.171601] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.171722] NET: Registered protocol family 1**[/FONT]            
            [FONT=Times New Roman]**[    0.171756] pci 0000:00:02.0: Video device with shadowed ROM**[/FONT]            
            [FONT=Times New Roman]**[    0.171756] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling**[/FONT]            
            [FONT=Times New Roman]**[    0.171756] PCI: CLS 64 bytes, default 64**[/FONT]            
            [FONT=Times New Roman]**[    0.171756] Trying to unpack rootfs image as initramfs...**[/FONT]            
            [FONT=Times New Roman]**[    0.801807] Freeing initrd memory: 18344K (f5c1c000 - f6e06000)**[/FONT]            
            [FONT=Times New Roman]**[    0.802266] microcode: CPU0 sig=0xf27, pf=0x4, revision=0x37**[/FONT]            
            [FONT=Times New Roman]**[    0.802386] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba**[/FONT]            
            [FONT=Times New Roman]**[    0.802391] Scanning for low memory corruption every 60 seconds**[/FONT]            
            [FONT=Times New Roman]**[    0.802840] Initialise system trusted keyring**[/FONT]            
            [FONT=Times New Roman]**[    0.802929] audit: initializing netlink socket (disabled)**[/FONT]            
            [FONT=Times New Roman]**[    0.802958] type=2000 audit(1430508022.799:1): initialized**[/FONT]            
            [FONT=Times New Roman]**[    0.834111] bounce pool size: 64 pages**[/FONT]            
            [FONT=Times New Roman]**[    0.834132] HugeTLB registered 2 MB page size, pre-allocated 0 pages**[/FONT]            
            [FONT=Times New Roman]**[    0.836360] zbud: loaded**[/FONT]            
            [FONT=Times New Roman]**[    0.836530] VFS: Disk quotas dquot_6.5.2**[/FONT]            
            [FONT=Times New Roman]**[    0.836626] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)**[/FONT]            
            [FONT=Times New Roman]**[    0.837472] fuse init (API version 7.22)**[/FONT]            
            [FONT=Times New Roman]**[    0.837614] msgmni has been set to 1733**[/FONT]            
            [FONT=Times New Roman]**[    0.837729] Key type big_key registered**[/FONT]            
            [FONT=Times New Roman]**[    0.838306] Key type asymmetric registered**[/FONT]            
            [FONT=Times New Roman]**[    0.838312] Asymmetric key parser 'x509' registered**[/FONT]            
            [FONT=Times New Roman]**[    0.838403] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)**[/FONT]            
            [FONT=Times New Roman]**[    0.838464] io scheduler noop registered**[/FONT]            
            [FONT=Times New Roman]**[    0.838469] io scheduler deadline registered (default)**[/FONT]            
            [FONT=Times New Roman]**[    0.838526] io scheduler cfq registered**[/FONT]            
            [FONT=Times New Roman]**[    0.838729] pci_hotplug: PCI Hot Plug PCI Core version: 0.5**[/FONT]            
            [FONT=Times New Roman]**[    0.838758] pciehp: PCI Express Hot Plug Controller Driver version: 0.4**[/FONT]            
            [FONT=Times New Roman]**[    0.838849] vesafb: mode is 1024x768x32, linelength=4096, pages=0**[/FONT]            
            [FONT=Times New Roman]**[    0.838853] vesafb: scrolling: redraw**[/FONT]            
            [FONT=Times New Roman]**[    0.838858] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0**[/FONT]            
            [FONT=Times New Roman]**[    0.839191] vesafb: framebuffer at 0xf0000000, mapped to 0xf8400000, using 3072k, total 3072k**[/FONT]            
            [FONT=Times New Roman]**[    0.905400] Console: switching to colour frame buffer device 128x48**[/FONT]            
            [FONT=Times New Roman]**[    0.971371] fb0: VESA VGA frame buffer device**[/FONT]            
            [FONT=Times New Roman]**[    0.971438] ipmi message handler version 39.2**[/FONT]            
            [FONT=Times New Roman]**[    0.971574] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0**[/FONT]            
            [FONT=Times New Roman]**[    0.971588] ACPI: Power Button [PBTN]**[/FONT]            
            [FONT=Times New Roman]**[    0.971654] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1**[/FONT]            
            [FONT=Times New Roman]**[    0.971660] ACPI: Power Button [PWRF]**[/FONT]            
            [FONT=Times New Roman]**[    0.971883] GHES: HEST is not enabled!**[/FONT]            
            [FONT=Times New Roman]**[    0.972109] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled**[/FONT]            
            [FONT=Times New Roman]**[    0.992592] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A**[/FONT]            
            [FONT=Times New Roman]**[    0.992669] isapnp: Scanning for PnP cards...**[/FONT]            
            [FONT=Times New Roman]**[    1.043951] Linux agpgart interface v0.103**[/FONT]            
            [FONT=Times New Roman]**[    1.044075] agpgart-intel 0000:00:00.0: Intel 845G Chipset**[/FONT]            
            [FONT=Times New Roman]**[    1.044111] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable**[/FONT]            
            [FONT=Times New Roman]**[    1.044302] agpgart-intel 0000:00:00.0: detected 8192K stolen memory**[/FONT]            
            [FONT=Times New Roman]**[    1.044506] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000**[/FONT]            
            [FONT=Times New Roman]**[    1.046906] brd: module loaded**[/FONT]            
            [FONT=Times New Roman]**[    1.048207] loop: module loaded**[/FONT]            
            [FONT=Times New Roman]**[    1.048502] ata_piix 0000:00:1f.1: version 2.13**[/FONT]            
            [FONT=Times New Roman]**[    1.048522] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)**[/FONT]            
            [FONT=Times New Roman]**[    1.049392] scsi0 : ata_piix**[/FONT]            
            [FONT=Times New Roman]**[    1.049535] scsi1 : ata_piix**[/FONT]            
            [FONT=Times New Roman]**[    1.049591] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x24a0 irq 14**[/FONT]            
            [FONT=Times New Roman]**[    1.049596] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x24a8 irq 15**[/FONT]            
            [FONT=Times New Roman]**[    1.050191] libphy: Fixed MDIO Bus: probed**[/FONT]            
            [FONT=Times New Roman]**[    1.050382] tun: Universal TUN/TAP device driver, 1.6**[/FONT]            
            [FONT=Times New Roman]**[    1.050386] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>**[/FONT]            
            [FONT=Times New Roman]**[    1.050552] PPP generic driver version 2.4.2**[/FONT]            
            [FONT=Times New Roman]**[    1.050637] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver**[/FONT]            
            [FONT=Times New Roman]**[    1.050648] ehci-pci: EHCI PCI platform driver**[/FONT]            
            [FONT=Times New Roman]**[    1.050873] ehci-pci 0000:00:1d.7: EHCI Host Controller**[/FONT]            
            [FONT=Times New Roman]**[    1.050886] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1**[/FONT]            
            [FONT=Times New Roman]**[    1.050910] ehci-pci 0000:00:1d.7: debug port 1**[/FONT]            
            [FONT=Times New Roman]**[    1.054853] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported**[/FONT]            
            [FONT=Times New Roman]**[    1.055156] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfc480000**[/FONT]            
            [FONT=Times New Roman]**[    1.098783] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00**[/FONT]            
            [FONT=Times New Roman]**[    1.142455] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002**[/FONT]            
            [FONT=Times New Roman]**[    1.142460] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1**[/FONT]            
            [FONT=Times New Roman]**[    1.142466] usb usb1: Product: EHCI Host Controller**[/FONT]            
            [FONT=Times New Roman]**[    1.142471] usb usb1: Manufacturer: Linux 3.13.0-51-generic ehci_hcd**[/FONT]            
            [FONT=Times New Roman]**[    1.142476] usb usb1: SerialNumber: 0000:00:1d.7**[/FONT]            
            [FONT=Times New Roman]**[    1.142689] hub 1-0:1.0: USB hub found**[/FONT]            
            [FONT=Times New Roman]**[    1.142703] hub 1-0:1.0: 6 ports detected**[/FONT]            
            [FONT=Times New Roman]**[    1.142959] ehci-platform: EHCI generic platform driver**[/FONT]            
            [FONT=Times New Roman]**[    1.142987] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver**[/FONT]            
            [FONT=Times New Roman]**[    1.142991] ohci-pci: OHCI PCI platform driver**[/FONT]            
            [FONT=Times New Roman]**[    1.143013] ohci-platform: OHCI generic platform driver**[/FONT]            
            [FONT=Times New Roman]**[    1.143028] uhci_hcd: USB Universal Host Controller Interface driver**[/FONT]            
            [FONT=Times New Roman]**[    1.143230] uhci_hcd 0000:00:1d.0: UHCI Host Controller**[/FONT]            
            [FONT=Times New Roman]**[    1.143242] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2**[/FONT]            
            [FONT=Times New Roman]**[    1.143296] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00002440**[/FONT]            
            [FONT=Times New Roman]**[    1.143398] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001**[/FONT]            
            [FONT=Times New Roman]**[    1.143404] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1**[/FONT]            
            [FONT=Times New Roman]**[    1.143409] usb usb2: Product: UHCI Host Controller**[/FONT]            
            [FONT=Times New Roman]**[    1.143414] usb usb2: Manufacturer: Linux 3.13.0-51-generic uhci_hcd**[/FONT]            
            [FONT=Times New Roman]**[    1.143419] usb usb2: SerialNumber: 0000:00:1d.0**[/FONT]            
            [FONT=Times New Roman]**[    1.143604] hub 2-0:1.0: USB hub found**[/FONT]            
            [FONT=Times New Roman]**[    1.143618] hub 2-0:1.0: 2 ports detected**[/FONT]            
            [FONT=Times New Roman]**[    1.143903] uhci_hcd 0000:00:1d.1: UHCI Host Controller**[/FONT]            
            [FONT=Times New Roman]**[    1.143915] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3**[/FONT]            
            [FONT=Times New Roman]**[    1.143958] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002460**[/FONT]            
            [FONT=Times New Roman]**[    1.144100] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001**[/FONT]            
            [FONT=Times New Roman]**[    1.144106] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1**[/FONT]            
            [FONT=Times New Roman]**[    1.144111] usb usb3: Product: UHCI Host Controller**[/FONT]            
            [FONT=Times New Roman]**[    1.144116] usb usb3: Manufacturer: Linux 3.13.0-51-generic uhci_hcd**[/FONT]            
            [FONT=Times New Roman]**[    1.144121] usb usb3: SerialNumber: 0000:00:1d.1**[/FONT]            
            [FONT=Times New Roman]**[    1.144299] hub 3-0:1.0: USB hub found**[/FONT]            
            [FONT=Times New Roman]**[    1.144312] hub 3-0:1.0: 2 ports detected**[/FONT]            
            [FONT=Times New Roman]**[    1.144606] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12**[/FONT]            
            [FONT=Times New Roman]**[    1.191040] serio: i8042 KBD port at 0x60,0x64 irq 1**[/FONT]            
            [FONT=Times New Roman]**[    1.191054] serio: i8042 AUX port at 0x60,0x64 irq 12**[/FONT]            
            [FONT=Times New Roman]**[    1.322705] isapnp: No Plug & Play device found**[/FONT]            
            [FONT=Times New Roman]**[    1.323010] mousedev: PS/2 mouse device common for all mice**[/FONT]            
            [FONT=Times New Roman]**[    1.323232] rtc_cmos 00:02: RTC can wake from S4**[/FONT]            
            [FONT=Times New Roman]**[    1.323384] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0**[/FONT]            
            [FONT=Times New Roman]**[    1.323423] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram**[/FONT]            
            [FONT=Times New Roman]**[    1.323570] device-mapper: uevent: version 1.0.3**[/FONT]            
            [FONT=Times New Roman]**[    1.323680] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com**[/FONT]            
            [FONT=Times New Roman]**[    1.323725] platform eisa.0: Probing EISA bus 0**[/FONT]            
            [FONT=Times New Roman]**[    1.323739] platform eisa.0: Cannot allocate resource for EISA slot 1**[/FONT]            
            [FONT=Times New Roman]**[    1.323745] platform eisa.0: Cannot allocate resource for EISA slot 2**[/FONT]            
            [FONT=Times New Roman]**[    1.323777] platform eisa.0: EISA: Detected 0 cards**[/FONT]            
            [FONT=Times New Roman]**[    1.323796] cpufreq-nforce2: No nForce2 chipset.**[/FONT]            
            [FONT=Times New Roman]**[    1.323802] ledtrig-cpu: registered to indicate activity on CPUs**[/FONT]            
            [FONT=Times New Roman]**[    1.324135] TCP: cubic registered**[/FONT]            
            [FONT=Times New Roman]**[    1.324305] NET: Registered protocol family 10**[/FONT]            
            [FONT=Times New Roman]**[    1.324655] NET: Registered protocol family 17**[/FONT]            
            [FONT=Times New Roman]**[    1.324691] Key type dns_resolver registered**[/FONT]            
            [FONT=Times New Roman]**[    1.324972] Using IPI No-Shortcut mode**[/FONT]            
            [FONT=Times New Roman]**[    1.325108] Loading compiled-in X.509 certificates**[/FONT]            
            [FONT=Times New Roman]**[    1.332296] Loaded X.509 cert 'Magrathea: Glacier signing key: 1f88723dce4086a12303dadd54a7ae35e9e44d58'**[/FONT]            
            [FONT=Times New Roman]**[    1.332325] registered taskstats version 1**[/FONT]            
            [FONT=Times New Roman]**[    1.337342] Key type trusted registered**[/FONT]            
            [FONT=Times New Roman]**[    1.346469] Key type encrypted registered**[/FONT]            
            [FONT=Times New Roman]**[    1.346481] AppArmor: AppArmor sha1 policy hashing enabled**[/FONT]            
            [FONT=Times New Roman]**[    1.346487] IMA: No TPM chip found, activating TPM-bypass!**[/FONT]            
            [FONT=Times New Roman]**[    1.346729] regulator-dummy: disabling**[/FONT]            
            [FONT=Times New Roman]**[    1.346823]   Magic number: 15:354:343**[/FONT]            
            [FONT=Times New Roman]**[    1.346889] tty tty60: hash matches**[/FONT]            
            [FONT=Times New Roman]**[    1.346997] rtc_cmos 00:02: setting system clock to 2015-05-01 19:20:24 UTC (1430508024)**[/FONT]            
            [FONT=Times New Roman]**[    1.347140] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found**[/FONT]            
            [FONT=Times New Roman]**[    1.347143] EDD information not available.**[/FONT]            
            [FONT=Times New Roman]**[    1.347194] PM: Hibernation image not present or could not be loaded.**[/FONT]            
            [FONT=Times New Roman]**[    1.354639] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2**[/FONT]            
            [FONT=Times New Roman]**[    1.367943] ata1.00: ATA-7: ST3160215ACE, 3.ARC, max UDMA/100**[/FONT]            
            [FONT=Times New Roman]**[    1.367949] ata1.00: 312581808 sectors, multi 16: LBA48**[/FONT]            
            [FONT=Times New Roman]**[    1.442834] ata1.00: configured for UDMA/100**[/FONT]            
            [FONT=Times New Roman]**[    1.443058] scsi 0:0:0:0: Direct-Access     ATA      ST3160215ACE     3.AR PQ: 0 ANSI: 5**[/FONT]            
            [FONT=Times New Roman]**[    1.443365] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)**[/FONT]            
            [FONT=Times New Roman]**[    1.443477] sd 0:0:0:0: [sda] Write Protect is off**[/FONT]            
            [FONT=Times New Roman]**[    1.443483] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00**[/FONT]            
            [FONT=Times New Roman]**[    1.443531] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA**[/FONT]            
            [FONT=Times New Roman]**[    1.443755] sd 0:0:0:0: Attached scsi generic sg0 type 0**[/FONT]            
            [FONT=Times New Roman]**[    1.499129]  sda: sda1**[/FONT]            
            [FONT=Times New Roman]**[    1.499596] sd 0:0:0:0: [sda] Attached SCSI disk**[/FONT]            
            [FONT=Times New Roman]**[    1.501139] Freeing unused kernel memory: 880K (c19bd000 - c1a99000)**[/FONT]            
            [FONT=Times New Roman]**[    1.501234] Write protecting the kernel text: 6556k**[/FONT]            
            [FONT=Times New Roman]**[    1.501331] Write protecting the kernel read-only data: 2772k**[/FONT]            
            [FONT=Times New Roman]**[    1.536515] systemd-udevd[94]: starting version 204**[/FONT]            
            [FONT=Times New Roman]**[    1.650849] Floppy drive(s): fd0 is 1.44M**[/FONT]            
            [FONT=Times New Roman]**[    1.666233] FDC 0 is a post-1991 82077**[/FONT]            
            [FONT=Times New Roman]**[    1.699112] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI**[/FONT]            
            [FONT=Times New Roman]**[    1.699120] e100: Copyright(c) 1999-2006 Intel Corporation**[/FONT]            
            [FONT=Times New Roman]**[    1.727986] e100 0000:05:08.0 eth0: addr 0xfc500000, irq 20, MAC addr 00:0b:cd:06:7f:28**[/FONT]            
            [FONT=Times New Roman]**[    1.800101] tsc: Refined TSC clocksource calibration: 2391.437 MHz**[/FONT]            
            [FONT=Times New Roman]**[    2.800139] Switched to clocksource tsc**[/FONT]            
            [FONT=Times New Roman]**[    2.883257] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4**[/FONT]            
            [FONT=Times New Roman]**[    7.165928] EXT4-fs (sda1): mounting ext3 file system using the ext4 subsystem**[/FONT]            
            [FONT=Times New Roman]**[    7.210056] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)**[/FONT]            
            [FONT=Times New Roman]**[    8.722671] random: nonblocking pool is initialized**[/FONT]            
            [FONT=Times New Roman]**[   27.393285] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready**[/FONT]            
            [FONT=Times New Roman]**[   28.116468] systemd-udevd[256]: starting version 204**[/FONT]            
            [FONT=Times New Roman]**[   29.763247] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro**[/FONT]            
            [FONT=Times New Roman]**[   29.853923] lp: driver loaded but no devices found**[/FONT]            
            [FONT=Times New Roman]**[   29.910420] parport_pc 00:06: reported by Plug and Play ACPI**[/FONT]            
            [FONT=Times New Roman]**[   29.910483] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]**[/FONT]            
            [FONT=Times New Roman]**[   29.992685] ppdev: user-space parallel port driver**[/FONT]            
            [FONT=Times New Roman]**[   30.005234] lp0: using parport0 (interrupt-driven).**[/FONT]            
            [FONT=Times New Roman]**[   30.228113] intel_rng: Firmware space is locked read-only. If you can't or**[/FONT]            
            [FONT=Times New Roman]**[   30.228113] intel_rng: don't want to disable this in firmware setup, and if**[/FONT]            
            [FONT=Times New Roman]**[   30.228113] intel_rng: you are certain that your system has a functional**[/FONT]            
            [FONT=Times New Roman]**[   30.228113] intel_rng: RNG, try using the 'no_fwh_detect' option.**[/FONT]            
            [FONT=Times New Roman]**[   30.275990] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4**[/FONT]            
            [FONT=Times New Roman]**[   30.737092] ACPI Warning: 0x0000f828-0x0000f82f SystemIO conflicts with Region \ICHP 1 (20131115/utaddress-251)**[/FONT]            
            [FONT=Times New Roman]**[   30.737105] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver**[/FONT]            
            [FONT=Times New Roman]**[   30.737869] lpc_ich: Resource conflict(s) found affecting gpio_ich**[/FONT]            
            [FONT=Times New Roman]**[   31.117775] [drm] Initialized drm 1.1.0 20060810**[/FONT]            
            [FONT=Times New Roman]**[   31.290174] type=1400 audit(1430500854.439:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=327 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   31.290191] type=1400 audit(1430500854.439:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   31.290201] type=1400 audit(1430500854.439:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   31.291426] type=1400 audit(1430500854.439:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   31.291439] type=1400 audit(1430500854.439:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   31.292094] type=1400 audit(1430500854.443:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   31.299583] type=1400 audit(1430500854.447:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=328 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   32.321237] [drm] Memory usable by graphics device = 128M**[/FONT]            
            [FONT=Times New Roman]**[   32.321248] checking generic (f0000000 300000) vs hw (f0000000 8000000)**[/FONT]            
            [FONT=Times New Roman]**[   32.321253] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver**[/FONT]            
            [FONT=Times New Roman]**[   32.321308] Console: switching to colour dummy device 80x25**[/FONT]            
            [FONT=Times New Roman]**[   32.326327] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).**[/FONT]            
            [FONT=Times New Roman]**[   32.326333] [drm] Driver supports precise vblank timestamp query.**[/FONT]            
            [FONT=Times New Roman]**[   32.326427] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem**[/FONT]            
            [FONT=Times New Roman]**[   32.341186] [drm] initialized overlay support**[/FONT]            
            [FONT=Times New Roman]**[   32.429208] fbcon: inteldrmfb (fb0) is primary device**[/FONT]            
            [FONT=Times New Roman]**[   32.480087] Console: switching to colour frame buffer device 128x48**[/FONT]            
            [FONT=Times New Roman]**[   32.484939] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device**[/FONT]            
            [FONT=Times New Roman]**[   32.484944] i915 0000:00:02.0: registered panic notifier**[/FONT]            
            [FONT=Times New Roman]**[   32.484968] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0**[/FONT]            
            [FONT=Times New Roman]**[   32.741949] ip_tables: (C) 2000-2006 Netfilter Core Team**[/FONT]            
            [FONT=Times New Roman]**[   33.158935] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)**[/FONT]            
            [FONT=Times New Roman]**[   33.404030] intel8x0_measure_ac97_clock: measured 54820 usecs (2641 samples)**[/FONT]            
            [FONT=Times New Roman]**[   33.404038] intel8x0: clocking to 48000**[/FONT]            
            [FONT=Times New Roman]**[   33.992494] ip6_tables: (C) 2000-2006 Netfilter Core Team**[/FONT]            
            [FONT=Times New Roman]**[   36.932306] init: failsafe main process (611) killed by TERM signal**[/FONT]            
            [FONT=Times New Roman]**[   38.549517] Bluetooth: Core ver 2.17**[/FONT]            
            [FONT=Times New Roman]**[   38.549604] NET: Registered protocol family 31**[/FONT]            
            [FONT=Times New Roman]**[   38.549608] Bluetooth: HCI device and connection manager initialized**[/FONT]            
            [FONT=Times New Roman]**[   38.551125] Bluetooth: HCI socket layer initialized**[/FONT]            
            [FONT=Times New Roman]**[   38.551139] Bluetooth: L2CAP socket layer initialized**[/FONT]            
            [FONT=Times New Roman]**[   38.551162] Bluetooth: SCO socket layer initialized**[/FONT]            
            [FONT=Times New Roman]**[   38.567749] type=1400 audit(1430500861.715:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=717 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   38.567770] type=1400 audit(1430500861.715:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=717 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   38.573059] type=1400 audit(1430500861.723:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=717 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   38.998783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3**[/FONT]            
            [FONT=Times New Roman]**[   38.998793] Bluetooth: BNEP filters: protocol multicast**[/FONT]            
            [FONT=Times New Roman]**[   38.998821] Bluetooth: BNEP socket layer initialized**[/FONT]            
            [FONT=Times New Roman]**[   39.016542] Bluetooth: RFCOMM TTY layer initialized**[/FONT]            
            [FONT=Times New Roman]**[   39.016573] Bluetooth: RFCOMM socket layer initialized**[/FONT]            
            [FONT=Times New Roman]**[   39.016597] Bluetooth: RFCOMM ver 1.11**[/FONT]            
            [FONT=Times New Roman]**[   39.784334] init: cups main process (728) killed by HUP signal**[/FONT]            
            [FONT=Times New Roman]**[   39.784364] init: cups main process ended, respawning**[/FONT]            
            [FONT=Times New Roman]**[   42.713144] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready**[/FONT]            
            [FONT=Times New Roman]**[   42.714303] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready**[/FONT]            
            [FONT=Times New Roman]**[   42.716183] e100 0000:05:08.0 eth0: NIC Link is Up 100 Mbps Full Duplex**[/FONT]            
            [FONT=Times New Roman]**[   42.716960] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready**[/FONT]            
            [FONT=Times New Roman]**[   43.303481] type=1400 audit(1430500866.451:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=884 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   43.303500] type=1400 audit(1430500866.451:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=884 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   43.304654] type=1400 audit(1430500866.455:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=884 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   43.314965] type=1400 audit(1430500866.463:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=885 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   43.314986] type=1400 audit(1430500866.463:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   43.314998] type=1400 audit(1430500866.463:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   43.316688] type=1400 audit(1430500866.467:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   53.305287] init: plymouth-upstart-bridge main process ended, respawning**[/FONT]            
            [FONT=Times New Roman]**[   53.362424] init: plymouth-upstart-bridge main process ended, respawning**[/FONT]            
            [FONT=Times New Roman]**[   68.840726] audit_printk_skb: 87 callbacks suppressed**[/FONT]            
            [FONT=Times New Roman]**[   68.840734] type=1400 audit(1430500891.990:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1648 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   68.840751] type=1400 audit(1430500891.990:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1648 comm="apparmor_parser"**[/FONT]            
            [FONT=Times New Roman]**[   68.842039] type=1400 audit(1430500891.990:50): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1648 comm="apparmor_parser"**[/FONT]
```


Thanks for your help

---

### Post by viktor5 on 2015-05-03
Bump!

---

