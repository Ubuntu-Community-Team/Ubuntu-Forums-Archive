---
title: "Ubuntu crashes: &quot;Could not write byte: broken pipe&quot;"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by vallvi on 2012-10-06
Hi,

Once so often, my Ubuntu 12.04 crashes, I get a black sreen with the message: "Could not write byte: broken pipe".  A few weeks ago, I did a fresh install hoping that this would solve the problem, but now it happened again. 

The computer totally blocks and the only way to get out of it is to turn off the computer (no keyboard keys respond). I then even have problems restarting (light goes on, but the computer even doesn't make it to the bios message & doesn't access the hard disk. just a black screen. Only after waiting for half an hour before restart, it loads up again. 

I've a Acer aspire, AX3810, ATI radeon card, , 6 gig RAM. Since the fresh install, I have installed no new software, except thunderbird, clementine, skype and vlc media player. I don't get this problem on windows (I've a double boot)

I searched on the forum, and get all kinds of suggestions: nvidia problem, disks not mounted, etc. So I am confused.  Is there any straight forward and simple way to solve this issue?

Thanks for any help you might be able to give.

---

### Post by NikTh on 2012-10-06
Hi , 

If you can login to Ubuntu  , open a terminal and give here the full dmesg log. 

```
dmesg >> dmesg.txt
gedit dmesg.txt
``` 

Copy-paste here the full log of dmesg. 

_PLEASE_ put the result between the brackets **[noparse]```
Here
```[/noparse]** so can be readable. 

The log is very LONG , and we can exterminate for further errors - details that might help.

This message **Could not write byte: broken pipe **usually refers to a broken filesystem , but is not for sure. 

Thanks

---

### Post by vallvi on 2012-10-09
thanks, Nikth, for your offer to help. The result is pasted below. (but today I didn't have any problem with my computer crashing.

 **```
**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic-pae 3.2.28)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01100 (reserved)
[    0.000000]  BIOS-e820: 00000000fed02000 - 00000000fed14c00 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire X3810/WG43M, BIOS P01-A3 05/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ee000 - 3726f000
[    0.000000] ACPI: RSDP 000fa770 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff90100 0006C (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bff90290 000F4 (v04 052609 FACP2056 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bff905c0 061D5 (v02   P01-   P01-A3 000000A3 INTL 20051117)
[    0.000000] ACPI: FACS bff9e000 00040
[    0.000000] ACPI: APIC bff90390 0006C (v02 052609 APIC2056 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bff90400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: SLIC bff90440 00176 (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bff9e040 00072 (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bff9a5c0 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bff9e0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: AWMI bffa00f0 0004E (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffa0940 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6276MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572638
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f2cee200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331849 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558301
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6179240k/7340032k available (5818k kernel code, 111312k reserved, 2846k data, 740k init, 5377608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.650 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.30 BogoMIPS (lpj=9310600)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004042] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004094] Mount-cache hash table entries: 512
[    0.004217] Initializing cgroup subsys cpuacct
[    0.004223] Initializing cgroup subsys memory
[    0.004230] Initializing cgroup subsys devices
[    0.004232] Initializing cgroup subsys freezer
[    0.004234] Initializing cgroup subsys blkio
[    0.004240] Initializing cgroup subsys perf_event
[    0.004265] CPU: Physical Processor ID: 0
[    0.004266] CPU: Processor Core ID: 0
[    0.004269] mce: CPU supports 6 MCE banks
[    0.004277] CPU0: Thermal monitoring enabled (TM2)
[    0.004280] using mwait in idle threads.
[    0.009714] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 26555 entries in 52 pages
[    0.024042] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024389] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066480] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.068003] APIC calibration not consistent with PM-Timer: 139ms instead of 100ms
[    0.068003] APIC delta adjusted to PM-Timer: 2078348 (2909656)
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156032] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156123] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.156125]  #2
[    0.156127] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248117] CPU 3 irqstacks, hard=f752e000 soft=f7538000
[    0.248119]  #3 Ok.
[    0.248120] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.340037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340060] Brought up 4 CPUs
[    0.340063] Total of 4 processors activated (18662.90 BogoMIPS).
[    0.343004] devtmpfs: initialized
[    0.343004] EVM: security.selinux
[    0.343004] EVM: security.SMACK64
[    0.343004] EVM: security.capability
[    0.343004] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.344576] print_constraints: dummy: 
[    0.344603] RTC time: 18:58:08, date: 10/09/12
[    0.344640] NET: Registered protocol family 16
[    0.344649] Trying to unpack rootfs image as initramfs...
[    0.344771] EISA bus registered
[    0.344798] ACPI: bus type pci registered
[    0.344860] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.344863] PCI: not using MMCONFIG
[    0.344936] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.344996] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.344998] PCI: Using configuration type 1 for base access
[    0.346082] bio: create slab <bio-0> at 0
[    0.346082] ACPI: Added _OSI(Module Device)
[    0.346082] ACPI: Added _OSI(Processor Device)
[    0.346082] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.346082] ACPI: Added _OSI(Processor Aggregator Device)
[    0.346082] ACPI: EC: Look up EC in DSDT
[    0.348956] ACPI: Executed 1 blocks of module-level executable AML code
[    0.351650] ACPI: SSDT bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.351961] ACPI: Dynamic OEM Table Load:
[    0.351964] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.352255] ACPI: SSDT bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352564] ACPI: Dynamic OEM Table Load:
[    0.352567] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352843] ACPI: SSDT bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353154] ACPI: Dynamic OEM Table Load:
[    0.353157] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353426] ACPI: SSDT bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353739] ACPI: Dynamic OEM Table Load:
[    0.353742] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353929] ACPI: Interpreter enabled
[    0.353935] ACPI: (supports S0 S3 S4 S5)
[    0.353954] ACPI: Using IOAPIC for interrupt routing
[    0.353979] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.355173] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.355175] PCI: Using MMCONFIG for extended config space
[    0.360654] ACPI: No dock devices found.
[    0.360658] HEST: Table not found.
[    0.360662] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.360746] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360924] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.360926] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.360929] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.360931] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.360934] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.360936] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.360949] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.360991] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.361030] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.361034] pci 0000:00:01.0: PME# disabled
[    0.361072] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    0.361089] pci 0000:00:19.0: reg 10: [mem 0xfe9e0000-0xfe9fffff]
[    0.361097] pci 0000:00:19.0: reg 14: [mem 0xfe9de000-0xfe9defff]
[    0.361106] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.361165] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.361168] pci 0000:00:19.0: PME# disabled
[    0.361186] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.361226] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.361275] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.361315] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.361363] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.361403] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.361459] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.361479] pci 0000:00:1a.7: reg 10: [mem 0xfe9dc000-0xfe9dc3ff]
[    0.361565] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.361569] pci 0000:00:1a.7: PME# disabled
[    0.361592] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.361606] pci 0000:00:1b.0: reg 10: [mem 0xfe9d8000-0xfe9dbfff 64bit]
[    0.361669] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.361672] pci 0000:00:1b.0: PME# disabled
[    0.361691] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.361756] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.361760] pci 0000:00:1c.0: PME# disabled
[    0.361785] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.361826] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.361876] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.361916] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.361965] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.362004] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.362060] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.362080] pci 0000:00:1d.7: reg 10: [mem 0xfe9d6000-0xfe9d63ff]
[    0.362167] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.362171] pci 0000:00:1d.7: PME# disabled
[    0.362191] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.362249] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.362361] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.362379] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.362386] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.362394] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.362401] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.362409] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb41f]
[    0.362417] pci 0000:00:1f.2: reg 24: [mem 0xfe9d4000-0xfe9d47ff]
[    0.362462] pci 0000:00:1f.2: PME# supported from D3hot
[    0.362465] pci 0000:00:1f.2: PME# disabled
[    0.362481] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.362495] pci 0000:00:1f.3: reg 10: [mem 0xfe9d3c00-0xfe9d3cff 64bit]
[    0.362515] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.362571] pci 0000:01:00.0: [1002:954f] type 0 class 0x000300
[    0.362585] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362595] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.362603] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.362615] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.362646] pci 0000:01:00.0: supports D1 D2
[    0.362665] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.362678] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.362737] pci 0000:01:00.1: supports D1 D2
[    0.362766] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362769] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.362773] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.362777] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362832] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.362854] pci 0000:02:00.0: reg 10: [mem 0xfebff800-0xfebfffff 64bit]
[    0.362866] pci 0000:02:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.362959] pci 0000:02:00.0: supports D2
[    0.362961] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.362965] pci 0000:02:00.0: PME# disabled
[    0.368041] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.368045] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.368049] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.368113] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.368122] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.368125] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.368127] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.368130] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.368132] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.368135] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.368157] pci_bus 0000:00: on NUMA node 0
[    0.368161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.368376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.368427]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.368431]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.368432] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.377225] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.377274] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.377317] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.377364] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.377410] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.377456] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.377503] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.377549] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.377661] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.377661] vgaarb: loaded
[    0.377661] vgaarb: bridge control possible 0000:01:00.0
[    0.377661] i2c-core: driver [aat2870] using legacy suspend method
[    0.377661] i2c-core: driver [aat2870] using legacy resume method
[    0.377661] SCSI subsystem initialized
[    0.377661] libata version 3.00 loaded.
[    0.377661] usbcore: registered new interface driver usbfs
[    0.377661] usbcore: registered new interface driver hub
[    0.377661] usbcore: registered new device driver usb
[    0.377661] PCI: Using ACPI for IRQ routing
[    0.377661] PCI: pci_cache_line_size set to 64 bytes
[    0.377661] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.377661] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.377661] NetLabel: Initializing
[    0.377661] NetLabel:  domain hash size = 128
[    0.377661] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.377661] NetLabel:  unlabeled traffic allowed by default
[    0.377661] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.377661] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.377661] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.392155] Switching to clocksource hpet
[    0.400285] AppArmor: AppArmor Filesystem Enabled
[    0.400313] pnp: PnP ACPI init
[    0.400331] ACPI: bus type pnp registered
[    0.400447] pnp 00:00: [bus 00-ff]
[    0.400450] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.400453] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.400455] pnp 00:00: [io  0x0d00-0xffff window]
[    0.400457] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.400460] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.400462] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.400464] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.400520] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.400530] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.400532] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.400587] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.400589] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.400593] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.400629] pnp 00:02: [dma 4]
[    0.400631] pnp 00:02: [io  0x0000-0x000f]
[    0.400633] pnp 00:02: [io  0x0081-0x0083]
[    0.400635] pnp 00:02: [io  0x0087]
[    0.400637] pnp 00:02: [io  0x0089-0x008b]
[    0.400639] pnp 00:02: [io  0x008f]
[    0.400641] pnp 00:02: [io  0x00c0-0x00df]
[    0.400668] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.400679] pnp 00:03: [io  0x0070-0x0071]
[    0.400689] pnp 00:03: [irq 8]
[    0.400718] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.400746] pnp 00:04: [io  0x0060]
[    0.400749] pnp 00:04: [io  0x0064]
[    0.400754] pnp 00:04: [irq 1]
[    0.400782] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.400826] pnp 00:05: [irq 12]
[    0.400855] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.400864] pnp 00:06: [io  0x0061]
[    0.400894] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.400903] pnp 00:07: [io  0x00f0-0x00ff]
[    0.400907] pnp 00:07: [irq 13]
[    0.400935] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.401330] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.401333] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.401335] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.401339] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.401341] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.401391] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.401394] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.401396] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.401399] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.401402] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401511] pnp 00:09: [io  0x0010-0x001f]
[    0.401513] pnp 00:09: [io  0x0022-0x003f]
[    0.401515] pnp 00:09: [io  0x0044-0x005f]
[    0.401517] pnp 00:09: [io  0x0062-0x0063]
[    0.401519] pnp 00:09: [io  0x0065-0x006f]
[    0.401521] pnp 00:09: [io  0x0072-0x007f]
[    0.401523] pnp 00:09: [io  0x0080]
[    0.401525] pnp 00:09: [io  0x0084-0x0086]
[    0.401527] pnp 00:09: [io  0x0088]
[    0.401529] pnp 00:09: [io  0x008c-0x008e]
[    0.401531] pnp 00:09: [io  0x0090-0x009f]
[    0.401533] pnp 00:09: [io  0x00a2-0x00bf]
[    0.401535] pnp 00:09: [io  0x00e0-0x00ef]
[    0.401537] pnp 00:09: [io  0x04d0-0x04d1]
[    0.401539] pnp 00:09: [io  0x0800-0x087f]
[    0.401541] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.401543] pnp 00:09: [io  0x0500-0x057f]
[    0.401545] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.401547] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.401549] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.401610] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.401613] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.401615] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.401618] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.401621] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.401624] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.401627] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401681] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.401712] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.401761] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.401763] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.401795] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.401836] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.401885] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.401888] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401966] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.401968] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.402018] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.402021] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.402024] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402068] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.402116] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.402119] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402294] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.402296] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.402298] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.402301] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.402303] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.402363] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.402366] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.402368] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.402371] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.402374] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.402377] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.402506] pnp: PnP ACPI: found 16 devices
[    0.402508] ACPI: ACPI bus type pnp unregistered
[    0.402511] PnPBIOS: Disabled by ACPI PNP
[    0.440569] PCI: max bus depth: 1 pci_try_num: 2
[    0.440600] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440604] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.440606] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.440610] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.440613] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440617] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.440620] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.440625] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.440629] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440634] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.440661] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.440664] pci 0000:00:01.0: setting latency timer to 64
[    0.440674] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.440678] pci 0000:00:1c.0: setting latency timer to 64
[    0.440684] pci 0000:00:1e.0: setting latency timer to 64
[    0.440688] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.440690] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.440692] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440695] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440697] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440699] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440702] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.440704] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.440707] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440709] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.440712] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.440714] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440717] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.440719] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.440721] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440723] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440726] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440728] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440769] NET: Registered protocol family 2
[    0.440841] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.441057] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.441384] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.441550] TCP: Hash tables configured (established 131072 bind 65536)
[    0.441552] TCP reno registered
[    0.441555] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.441563] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.441645] NET: Registered protocol family 1
[    0.441674] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.441690] pci 0000:00:1a.0: PCI INT A disabled
[    0.441704] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.441719] pci 0000:00:1a.1: PCI INT B disabled
[    0.441729] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.441744] pci 0000:00:1a.2: PCI INT D disabled
[    0.441755] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441785] pci 0000:00:1a.7: PCI INT C disabled
[    0.441800] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441814] pci 0000:00:1d.0: PCI INT A disabled
[    0.441821] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.441836] pci 0000:00:1d.1: PCI INT B disabled
[    0.441842] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441857] pci 0000:00:1d.2: PCI INT C disabled
[    0.441865] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441878] pci 0000:00:1d.7: PCI INT A disabled
[    0.441892] pci 0000:01:00.0: Boot video device
[    0.441900] PCI: CLS 32 bytes, default 64
[    0.442390] audit: initializing netlink socket (disabled)
[    0.442399] type=2000 audit(1349809087.436:1): initialized
[    0.463394] highmem bounce pool size: 64 pages
[    0.463400] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.466033] VFS: Disk quotas dquot_6.5.2
[    0.466095] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.466676] fuse init (API version 7.17)
[    0.466792] msgmni has been set to 1565
[    0.467341] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.467386] io scheduler noop registered
[    0.467388] io scheduler deadline registered
[    0.467400] io scheduler cfq registered (default)
[    0.467509] pcieport 0000:00:01.0: setting latency timer to 64
[    0.467540] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.467587] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.467621] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.467700] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.467724] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.467785] intel_idle: MWAIT substates: 0x20
[    0.467787] intel_idle: does not run on family 6 model 23
[    0.467869] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.467874] ACPI: Power Button [PWRB]
[    0.467919] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.467923] ACPI: Power Button [PWRF]
[    0.470589] ERST: Table is not found!
[    0.470591] GHES: HEST is not enabled!
[    0.470689] isapnp: Scanning for PnP cards...
[    0.470693] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.631366] Freeing initrd memory: 13828k freed
[    0.823572] isapnp: No Plug & Play device found
[    0.876587] Linux agpgart interface v0.103
[    0.878701] brd: module loaded
[    0.879728] loop: module loaded
[    0.879866] ahci 0000:00:1f.2: version 3.0
[    0.879877] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.879915] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.879959] ahci: SSS flag set, parallel bus scan disabled
[    0.879990] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.879994] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.879998] ahci 0000:00:1f.2: setting latency timer to 64
[    0.920605] scsi0 : ahci
[    0.920717] scsi1 : ahci
[    0.920813] scsi2 : ahci
[    0.920910] scsi3 : ahci
[    0.921009] scsi4 : ahci
[    0.921111] scsi5 : ahci
[    0.921275] ata1: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4100 irq 42
[    0.921278] ata2: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4180 irq 42
[    0.921280] ata3: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4200 irq 42
[    0.921283] ata4: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4280 irq 42
[    0.921286] ata5: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4300 irq 42
[    0.921288] ata6: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4380 irq 42
[    0.921702] Fixed MDIO Bus: probed
[    0.921722] tun: Universal TUN/TAP device driver, 1.6
[    0.921724] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.921804] PPP generic driver version 2.4.2
[    0.921960] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.921976] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.921989] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.921993] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.922062] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.922084] ehci_hcd 0000:00:1a.7: debug port 1
[    0.925951] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.925966] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9dc000
[    0.940015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.940179] hub 1-0:1.0: USB hub found
[    0.940184] hub 1-0:1.0: 6 ports detected
[    0.940261] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.940271] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.940274] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.940339] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.940360] ehci_hcd 0000:00:1d.7: debug port 1
[    0.944234] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.944248] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9d6000
[    0.960014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.960155] hub 2-0:1.0: USB hub found
[    0.960159] hub 2-0:1.0: 6 ports detected
[    0.960232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.960245] uhci_hcd: USB Universal Host Controller Interface driver
[    0.960260] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.960267] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.960270] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.960332] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.960362] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.960510] hub 3-0:1.0: USB hub found
[    0.960514] hub 3-0:1.0: 2 ports detected
[    0.960577] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.960585] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.960588] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.960662] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.960693] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.960840] hub 4-0:1.0: USB hub found
[    0.960843] hub 4-0:1.0: 2 ports detected
[    0.960912] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.960918] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.960921] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.960987] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.961017] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.961163] hub 5-0:1.0: USB hub found
[    0.961166] hub 5-0:1.0: 2 ports detected
[    0.961226] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.961232] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.961235] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.961302] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.961322] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.961468] hub 6-0:1.0: USB hub found
[    0.961472] hub 6-0:1.0: 2 ports detected
[    0.961538] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.961545] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.961547] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.961614] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.961635] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.961780] hub 7-0:1.0: USB hub found
[    0.961784] hub 7-0:1.0: 2 ports detected
[    0.961848] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.961855] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.961858] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.961923] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.961944] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.962096] hub 8-0:1.0: USB hub found
[    0.962100] hub 8-0:1.0: 2 ports detected
[    0.962214] usbcore: registered new interface driver libusual
[    0.962273] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.962634] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.962641] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.962799] mousedev: PS/2 mouse device common for all mice
[    0.963014] rtc_cmos 00:03: RTC can wake from S4
[    0.963137] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.963159] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.963218] device-mapper: uevent: version 1.0.3
[    0.963315] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.963347] EISA: Probing bus 0 at eisa.0
[    0.963349] EISA: Cannot allocate resource for mainboard
[    0.963351] Cannot allocate resource for EISA slot 1
[    0.963353] Cannot allocate resource for EISA slot 2
[    0.963354] Cannot allocate resource for EISA slot 3
[    0.963356] Cannot allocate resource for EISA slot 4
[    0.963358] Cannot allocate resource for EISA slot 5
[    0.963359] Cannot allocate resource for EISA slot 6
[    0.963361] Cannot allocate resource for EISA slot 7
[    0.963363] Cannot allocate resource for EISA slot 8
[    0.963364] EISA: Detected 0 cards.
[    0.963373] cpufreq-nforce2: No nForce2 chipset.
[    0.963375] cpuidle: using governor ladder
[    0.963377] cpuidle: using governor menu
[    0.963379] EFI Variables Facility v0.08 2004-May-17
[    0.963643] TCP cubic registered
[    0.963770] NET: Registered protocol family 10
[    0.964343] NET: Registered protocol family 17
[    0.964347] Registering the dns_resolver key type
[    0.964371] Using IPI No-Shortcut mode
[    0.964533] PM: Hibernation image not present or could not be loaded.
[    0.964544] registered taskstats version 1
[    0.971419]   Magic number: 0:54:999
[    0.971460] system 00:01: hash matches
[    0.971462]  pnp0: hash matches
[    0.971523] rtc_cmos 00:03: setting system clock to 2012-10-09 18:58:09 UTC (1349809089)
[    0.972586] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.972588] EDD information not available.
[    0.979396] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.240021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.243031] ata1.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.246909] ata1.00: configured for UDMA/100
[    1.252016] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.257625] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.266069] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.266072] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.266219] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.266302] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.440015] Refined TSC clocksource calibration: 2327.754 MHz.
[    1.440020] Switching to clocksource tsc
[    1.568012] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.584015] ata2: SATA link down (SStatus 0 SControl 300)
[    1.704392] Initializing USB Mass Storage driver...
[    1.704558] scsi6 : usb-storage 2-3:1.0
[    1.704636] usbcore: registered new interface driver usb-storage
[    1.704638] USB Mass Storage support registered.
[    1.904014] ata3: SATA link down (SStatus 0 SControl 300)
[    1.940013] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    2.224015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.242239] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.242243] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.243260] ata4.00: configured for UDMA/133
[    2.243381] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.243495] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.243541] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.243562] sd 3:0:0:0: [sda] Write Protect is off
[    2.243565] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.243589] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.286130]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.286610] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.560014] ata5: SATA link down (SStatus 0 SControl 300)
[    2.704832] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.705454] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.706262] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.706462] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.709933] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.710555] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.880021] ata6: SATA link down (SStatus 0 SControl 300)
[    2.880115] Freeing unused kernel memory: 740k freed
[    2.880383] Write protecting the kernel text: 5820k
[    2.880412] Write protecting the kernel read-only data: 2376k
[    2.880414] NX-protecting the kernel data: 4420k
[    2.897294] udevd[113]: starting version 175
[    2.929202] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.929205] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.929243] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.929252] e1000e 0000:00:19.0: setting latency timer to 64
[    2.929356] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.931976] generic-usb 0003:058F:6363.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.934159] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.934168] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.947556] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.947688] generic-usb 0003:046D:C51B.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    2.961151] generic-usb 0003:046D:C51B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    2.961171] usbcore: registered new interface driver usbhid
[    2.961173] usbhid: USB HID core driver
[    2.996049] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.120316] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:f4:ca:94
[    3.120320] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.120343] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    3.496105] firewire_core: created device fw0: GUID 001d72ffae924fff, S400
[    3.628091] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.558354] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.574468] udevd[345]: starting version 175
[   13.612205] lp: driver loaded but no devices found
[   13.613255] [drm] Initialized drm 1.1.0 20060810
[   13.627489] Adding 9068540k swap on /dev/sda5.  Priority:-1 extents:1 across:9068540k 
[   13.645401] wmi: Mapper loaded
[   13.647362] [drm] radeon defaulting to kernel modesetting.
[   13.647365] [drm] radeon kernel modesetting enabled.
[   13.648293] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.648299] radeon 0000:01:00.0: setting latency timer to 64
[   13.666981] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x174B:0xE990).
[   13.667009] [drm] register mmio base: 0xFEAF0000
[   13.667011] [drm] register mmio size: 65536
[   13.667131] ATOM BIOS: 11X
[   13.667162] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   13.667165] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   13.669611] [drm] Detected VRAM RAM=512M, BAR=256M
[   13.669614] [drm] RAM width 64bits DDR
[   13.670153] [TTM] Zone  kernel: Available graphics memory: 408100 kiB.
[   13.670156] [TTM] Zone highmem: Available graphics memory: 3096904 kiB.
[   13.670157] [TTM] Initializing pool allocator.
[   13.670180] [drm] radeon: 512M of VRAM memory ready
[   13.670182] [drm] radeon: 512M of GTT memory ready.
[   13.670197] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.670199] [drm] Driver supports precise vblank timestamp query.
[   13.670261] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   13.670267] radeon 0000:01:00.0: radeon: using MSI.
[   13.670299] [drm] radeon: irq initialized.
[   13.670303] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.671330] [drm] Loading RV710 Microcode
[   13.671791] type=1400 audit(1349801902.193:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=497 comm="apparmor_parser"
[   13.672385] type=1400 audit(1349801902.197:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   13.672625] type=1400 audit(1349801902.197:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   13.697069] cfg80211: Calling CRDA to update world regulatory domain
[   13.720298] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.720347] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.720372] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   13.823592] cfg80211: World regulatory domain updated:
[   13.823595] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.823598] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.823601] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.823603] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.823605] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.823608] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.824118] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
[   13.856981] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   13.857032] radeon 0000:01:00.0: WB enabled
[   13.903019] [drm] ring test succeeded in 1 usecs
[   13.903179] [drm] radeon: ib pool ready.
[   13.903252] [drm] ib test succeeded in 0 usecs
[   13.903551] [drm] Radeon Display Connectors
[   13.903553] [drm] Connector 0:
[   13.903554] [drm]   VGA
[   13.903556] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   13.903558] [drm]   Encoders:
[   13.903559] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   13.903561] [drm] Connector 1:
[   13.903562] [drm]   HDMI-A
[   13.903563] [drm]   HPD1
[   13.903565] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   13.903567] [drm]   Encoders:
[   13.903568] [drm]     DFP1: INTERNAL_UNIPHY
[   13.903570] [drm] Connector 2:
[   13.903571] [drm]   DVI-I
[   13.903572] [drm]   HPD4
[   13.903574] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   13.903576] [drm]   Encoders:
[   13.903577] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.903579] [drm]     DFP2: INTERNAL_UNIPHY2
[   13.903596] [drm] Internal thermal controller with fan control
[   13.903639] [drm] radeon: power management initialized
[   13.977654] [drm] fb mappable at 0xD0142000
[   13.977657] [drm] vram apper at 0xD0000000
[   13.977658] [drm] size 5242880
[   13.977660] [drm] fb depth is 24
[   13.977661] [drm]    pitch is 5120
[   13.977744] fbcon: radeondrmfb (fb0) is primary device
[   13.977857] Console: switching to colour frame buffer device 160x64
[   13.977888] fb0: radeondrmfb frame buffer device
[   13.977890] drm: registered panic notifier
[   13.977896] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   13.995600] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.995604] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995606] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.995609] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995611] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.995614] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995616] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.995618] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995620] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.995623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995625] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.995628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995630] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.995632] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995634] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.995637] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995639] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.995642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995644] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.995647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995649] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.995651] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995654] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.995656] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.995658] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.995661] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.995663] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.995665] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.997016] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.998735] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.999370] Registered led device: rt2800usb-phy0::radio
[   13.999406] Registered led device: rt2800usb-phy0::assoc
[   13.999434] Registered led device: rt2800usb-phy0::quality
[   13.999480] usbcore: registered new interface driver rt2800usb
[   14.345257] init: failsafe main process (782) killed by TERM signal
[   14.381923] Bluetooth: Core ver 2.16
[   14.381948] NET: Registered protocol family 31
[   14.381949] Bluetooth: HCI device and connection manager initialized
[   14.381952] Bluetooth: HCI socket layer initialized
[   14.381954] Bluetooth: L2CAP socket layer initialized
[   14.381960] Bluetooth: SCO socket layer initialized
[   14.383907] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.383910] Bluetooth: BNEP filters: protocol multicast
[   14.389033] Bluetooth: RFCOMM TTY layer initialized
[   14.389039] Bluetooth: RFCOMM socket layer initialized
[   14.389041] Bluetooth: RFCOMM ver 1.11
[   14.405181] ppdev: user-space parallel port driver
[   14.417647] type=1400 audit(1349801902.941:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=854 comm="apparmor_parser"
[   14.418166] type=1400 audit(1349801902.941:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=854 comm="apparmor_parser"
[   14.556943] type=1400 audit(1349801903.081:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=890 comm="apparmor_parser"
[   14.557297] type=1400 audit(1349801903.081:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=891 comm="apparmor_parser"
[   14.557754] type=1400 audit(1349801903.081:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=891 comm="apparmor_parser"
[   14.558000] type=1400 audit(1349801903.081:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=891 comm="apparmor_parser"
[   14.559005] type=1400 audit(1349801903.081:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=894 comm="apparmor_parser"
[   14.624209] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.647625] init: alsa-restore main process (933) terminated with status 19
[   14.680114] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.680352] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.680699] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.896351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.896833] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.772015] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   17.780029] hda-intel: No response from codec, disabling MSI: last cmd=0x300f0000
[   18.176283] wlan0: authenticate with 00:1a:2b:13:ba:89 (try 1)
[   18.177794] wlan0: authenticated
[   18.232283] wlan0: associate with 00:1a:2b:13:ba:89 (try 1)
[   18.234046] wlan0: RX AssocResp from 00:1a:2b:13:ba:89 (capab=0x411 status=0 aid=1)
[   18.234050] wlan0: associated
[   18.243835] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.784013] hda-intel: Codec #3 probe error; disabling it...
[   18.827233] hda_codec: ALC888: BIOS auto-probing.
[   18.835472] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   18.835634] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   18.835708] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.835779] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.835849] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.835918] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.835989] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.836380] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.836448] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   18.836472] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   18.854374] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   18.854514] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   18.984643] init: plymouth-stop pre-start process (1556) terminated with status 1
[   29.008005] wlan0: no IPv6 routers present
**
```**

---

### Post by audiomick on 2012-10-09
I wont try to improve on NikTh's advice because I can't;)

Regarding having to shut off the computer when it freezes up, though. Have a look at this

[http://en.wikipedia.org/wiki/Reisub#Uses]("http://en.wikipedia.org/wiki/Reisub#Uses")

What is described there is a safe way to restart a frozen computer.

edit: That page shows how to use alt+sysrq+reisub to reboot. On that page above the point I linked to there is a table showing the various functions. Because I have been wondering about it myself, I tried an o on the end (letter o, not zero) instead of the b based on the listing in the table and found that it does indeed shut down the system without rebooting.

---

### Post by NikTh on 2012-10-09
> **vallvi said:**
> thanks, Nikth, for your offer to help. The result is pasted below. (**but today I didn't have any problem with my computer crashing.**

 

dmesg is usable and helpful , when the crashing take a place. 

Now I cannot see any weird messages or errors in dmesg you posted. 

Maybe we must look in older logs 

```
sudo cat /var/log/dmesg.0 > dmesg0.txt
gedit dmesg0.txt
```OR 
```
sudo zcat /var/log/dmesg.1.gz > dmesg1.txt
gedit dmesg1.txt
```Another log might help is Xorg log 
```
sudo cat /var/log/Xorg.0.log.old > xorg.txt
gedit xorg.txt
```Hopefully the error was temporary and will not repeated , but if you want to examine that better , give the results. 

Thanks

---

### Post by vallvi on 2012-10-09
ok nickth, here you go. Any feedback welcome:

 [B]```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic-pae 3.2.28)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01100 (reserved)
[    0.000000]  BIOS-e820: 00000000fed02000 - 00000000fed14c00 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire X3810/WG43M, BIOS P01-A3 05/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ee000 - 3726f000
[    0.000000] ACPI: RSDP 000fa770 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff90100 0006C (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bff90290 000F4 (v04 052609 FACP2056 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bff905c0 061D5 (v02   P01-   P01-A3 000000A3 INTL 20051117)
[    0.000000] ACPI: FACS bff9e000 00040
[    0.000000] ACPI: APIC bff90390 0006C (v02 052609 APIC2056 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bff90400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: SLIC bff90440 00176 (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bff9e040 00072 (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bff9a5c0 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bff9e0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: AWMI bffa00f0 0004E (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffa0940 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6276MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572638
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f2cee200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331849 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558301
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6179240k/7340032k available (5818k kernel code, 111312k reserved, 2846k data, 740k init, 5377608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.716 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.43 BogoMIPS (lpj=9310864)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004093] Mount-cache hash table entries: 512
[    0.004216] Initializing cgroup subsys cpuacct
[    0.004222] Initializing cgroup subsys memory
[    0.004230] Initializing cgroup subsys devices
[    0.004232] Initializing cgroup subsys freezer
[    0.004234] Initializing cgroup subsys blkio
[    0.004240] Initializing cgroup subsys perf_event
[    0.004264] CPU: Physical Processor ID: 0
[    0.004266] CPU: Processor Core ID: 0
[    0.004269] mce: CPU supports 6 MCE banks
[    0.004276] CPU0: Thermal monitoring enabled (TM2)
[    0.004279] using mwait in idle threads.
[    0.009713] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 26555 entries in 52 pages
[    0.024042] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024386] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066495] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.068003] APIC calibration not consistent with PM-Timer: 135ms instead of 100ms
[    0.068003] APIC delta adjusted to PM-Timer: 2078344 (2826523)
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156033] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156124] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.156126]  #2
[    0.156127] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248116] CPU 3 irqstacks, hard=f752e000 soft=f7538000
[    0.248118]  #3 Ok.
[    0.248120] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.340037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340061] Brought up 4 CPUs
[    0.340064] Total of 4 processors activated (18621.95 BogoMIPS).
[    0.343009] devtmpfs: initialized
[    0.343009] EVM: security.selinux
[    0.343009] EVM: security.SMACK64
[    0.343009] EVM: security.capability
[    0.343009] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.344579] print_constraints: dummy: 
[    0.344606] RTC time: 19:58:39, date: 10/08/12
[    0.344644] NET: Registered protocol family 16
[    0.344652] Trying to unpack rootfs image as initramfs...
[    0.344773] EISA bus registered
[    0.344801] ACPI: bus type pci registered
[    0.344863] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.344866] PCI: not using MMCONFIG
[    0.344943] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.345003] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.345004] PCI: Using configuration type 1 for base access
[    0.346089] bio: create slab <bio-0> at 0
[    0.346089] ACPI: Added _OSI(Module Device)
[    0.346089] ACPI: Added _OSI(Processor Device)
[    0.346089] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.346089] ACPI: Added _OSI(Processor Aggregator Device)
[    0.346089] ACPI: EC: Look up EC in DSDT
[    0.348965] ACPI: Executed 1 blocks of module-level executable AML code
[    0.351656] ACPI: SSDT bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.351966] ACPI: Dynamic OEM Table Load:
[    0.351969] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.352264] ACPI: SSDT bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352574] ACPI: Dynamic OEM Table Load:
[    0.352577] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352853] ACPI: SSDT bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353164] ACPI: Dynamic OEM Table Load:
[    0.353167] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353436] ACPI: SSDT bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353749] ACPI: Dynamic OEM Table Load:
[    0.353752] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353939] ACPI: Interpreter enabled
[    0.353944] ACPI: (supports S0 S3 S4 S5)
[    0.353964] ACPI: Using IOAPIC for interrupt routing
[    0.353989] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.355181] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.355183] PCI: Using MMCONFIG for extended config space
[    0.360664] ACPI: No dock devices found.
[    0.360667] HEST: Table not found.
[    0.360671] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.360756] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360933] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.360936] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.360938] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.360941] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.360943] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.360946] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.360959] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.361000] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.361040] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.361043] pci 0000:00:01.0: PME# disabled
[    0.361081] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    0.361098] pci 0000:00:19.0: reg 10: [mem 0xfe9e0000-0xfe9fffff]
[    0.361106] pci 0000:00:19.0: reg 14: [mem 0xfe9de000-0xfe9defff]
[    0.361115] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.361174] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.361177] pci 0000:00:19.0: PME# disabled
[    0.361195] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.361234] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.361283] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.361324] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.361372] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.361411] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.361468] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.361488] pci 0000:00:1a.7: reg 10: [mem 0xfe9dc000-0xfe9dc3ff]
[    0.361573] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.361578] pci 0000:00:1a.7: PME# disabled
[    0.361600] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.361614] pci 0000:00:1b.0: reg 10: [mem 0xfe9d8000-0xfe9dbfff 64bit]
[    0.361677] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.361681] pci 0000:00:1b.0: PME# disabled
[    0.361699] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.361764] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.361768] pci 0000:00:1c.0: PME# disabled
[    0.361794] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.361834] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.361885] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.361924] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.361972] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.362012] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.362068] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.362088] pci 0000:00:1d.7: reg 10: [mem 0xfe9d6000-0xfe9d63ff]
[    0.362174] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.362178] pci 0000:00:1d.7: PME# disabled
[    0.362198] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.362257] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.362369] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.362386] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.362394] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.362401] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.362409] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.362417] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb41f]
[    0.362425] pci 0000:00:1f.2: reg 24: [mem 0xfe9d4000-0xfe9d47ff]
[    0.362469] pci 0000:00:1f.2: PME# supported from D3hot
[    0.362473] pci 0000:00:1f.2: PME# disabled
[    0.362488] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.362502] pci 0000:00:1f.3: reg 10: [mem 0xfe9d3c00-0xfe9d3cff 64bit]
[    0.362522] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.362579] pci 0000:01:00.0: [1002:954f] type 0 class 0x000300
[    0.362592] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362602] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.362610] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.362623] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.362653] pci 0000:01:00.0: supports D1 D2
[    0.362672] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.362685] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.362745] pci 0000:01:00.1: supports D1 D2
[    0.362774] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362777] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.362780] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.362785] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362840] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.362862] pci 0000:02:00.0: reg 10: [mem 0xfebff800-0xfebfffff 64bit]
[    0.362874] pci 0000:02:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.362966] pci 0000:02:00.0: supports D2
[    0.362968] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.362973] pci 0000:02:00.0: PME# disabled
[    0.368041] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.368045] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.368049] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.368112] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.368122] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.368124] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.368127] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.368129] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.368132] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.368134] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.368157] pci_bus 0000:00: on NUMA node 0
[    0.368161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.368374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.368424]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.368427]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.368429] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.377219] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.377268] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.377311] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.377357] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.377404] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.377450] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.377496] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.377542] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.377655] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.377655] vgaarb: loaded
[    0.377655] vgaarb: bridge control possible 0000:01:00.0
[    0.377655] i2c-core: driver [aat2870] using legacy suspend method
[    0.377655] i2c-core: driver [aat2870] using legacy resume method
[    0.377655] SCSI subsystem initialized
[    0.377655] libata version 3.00 loaded.
[    0.377655] usbcore: registered new interface driver usbfs
[    0.377655] usbcore: registered new interface driver hub
[    0.377655] usbcore: registered new device driver usb
[    0.377655] PCI: Using ACPI for IRQ routing
[    0.377655] PCI: pci_cache_line_size set to 64 bytes
[    0.377655] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.377655] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.377655] NetLabel: Initializing
[    0.377655] NetLabel:  domain hash size = 128
[    0.377655] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.377655] NetLabel:  unlabeled traffic allowed by default
[    0.377655] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.377655] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.377655] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.392157] Switching to clocksource hpet
[    0.400291] AppArmor: AppArmor Filesystem Enabled
[    0.400321] pnp: PnP ACPI init
[    0.400338] ACPI: bus type pnp registered
[    0.400454] pnp 00:00: [bus 00-ff]
[    0.400457] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.400459] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.400461] pnp 00:00: [io  0x0d00-0xffff window]
[    0.400464] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.400466] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.400468] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.400470] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.400527] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.400537] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.400539] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.400594] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.400597] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.400600] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.400635] pnp 00:02: [dma 4]
[    0.400638] pnp 00:02: [io  0x0000-0x000f]
[    0.400640] pnp 00:02: [io  0x0081-0x0083]
[    0.400642] pnp 00:02: [io  0x0087]
[    0.400643] pnp 00:02: [io  0x0089-0x008b]
[    0.400645] pnp 00:02: [io  0x008f]
[    0.400647] pnp 00:02: [io  0x00c0-0x00df]
[    0.400674] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.400685] pnp 00:03: [io  0x0070-0x0071]
[    0.400696] pnp 00:03: [irq 8]
[    0.400725] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.400754] pnp 00:04: [io  0x0060]
[    0.400756] pnp 00:04: [io  0x0064]
[    0.400761] pnp 00:04: [irq 1]
[    0.400789] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.400833] pnp 00:05: [irq 12]
[    0.400862] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.400872] pnp 00:06: [io  0x0061]
[    0.400901] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.400910] pnp 00:07: [io  0x00f0-0x00ff]
[    0.400915] pnp 00:07: [irq 13]
[    0.400943] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.401339] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.401341] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.401344] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.401348] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.401350] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.401401] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.401403] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.401406] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.401408] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.401412] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401521] pnp 00:09: [io  0x0010-0x001f]
[    0.401523] pnp 00:09: [io  0x0022-0x003f]
[    0.401525] pnp 00:09: [io  0x0044-0x005f]
[    0.401527] pnp 00:09: [io  0x0062-0x0063]
[    0.401529] pnp 00:09: [io  0x0065-0x006f]
[    0.401531] pnp 00:09: [io  0x0072-0x007f]
[    0.401533] pnp 00:09: [io  0x0080]
[    0.401535] pnp 00:09: [io  0x0084-0x0086]
[    0.401536] pnp 00:09: [io  0x0088]
[    0.401538] pnp 00:09: [io  0x008c-0x008e]
[    0.401540] pnp 00:09: [io  0x0090-0x009f]
[    0.401542] pnp 00:09: [io  0x00a2-0x00bf]
[    0.401544] pnp 00:09: [io  0x00e0-0x00ef]
[    0.401546] pnp 00:09: [io  0x04d0-0x04d1]
[    0.401548] pnp 00:09: [io  0x0800-0x087f]
[    0.401551] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.401553] pnp 00:09: [io  0x0500-0x057f]
[    0.401555] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.401557] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.401559] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.401619] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.401622] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.401625] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.401628] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.401631] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.401633] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.401637] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401691] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.401721] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.401770] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.401772] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.401805] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.401845] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.401894] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.401897] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401975] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.401977] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.402027] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.402030] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.402034] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402078] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.402125] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.402128] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402303] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.402305] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.402307] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.402309] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.402311] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.402372] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.402375] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.402377] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.402380] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.402383] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.402386] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.402515] pnp: PnP ACPI: found 16 devices
[    0.402517] ACPI: ACPI bus type pnp unregistered
[    0.402520] PnPBIOS: Disabled by ACPI PNP
[    0.440575] PCI: max bus depth: 1 pci_try_num: 2
[    0.440607] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440610] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.440613] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.440617] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.440620] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440625] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.440627] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.440632] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.440636] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440642] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.440670] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.440674] pci 0000:00:01.0: setting latency timer to 64
[    0.440684] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.440688] pci 0000:00:1c.0: setting latency timer to 64
[    0.440694] pci 0000:00:1e.0: setting latency timer to 64
[    0.440698] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.440700] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.440703] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440705] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440708] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440710] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440713] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.440715] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.440717] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440720] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.440722] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.440725] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440727] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.440729] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.440732] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440734] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440736] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440739] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440779] NET: Registered protocol family 2
[    0.440852] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.441066] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.441404] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.441586] TCP: Hash tables configured (established 131072 bind 65536)
[    0.441587] TCP reno registered
[    0.441590] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.441599] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.441677] NET: Registered protocol family 1
[    0.441706] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.441722] pci 0000:00:1a.0: PCI INT A disabled
[    0.441736] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.441751] pci 0000:00:1a.1: PCI INT B disabled
[    0.441761] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.441776] pci 0000:00:1a.2: PCI INT D disabled
[    0.441787] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441816] pci 0000:00:1a.7: PCI INT C disabled
[    0.441831] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441846] pci 0000:00:1d.0: PCI INT A disabled
[    0.441853] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.441867] pci 0000:00:1d.1: PCI INT B disabled
[    0.441875] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441890] pci 0000:00:1d.2: PCI INT C disabled
[    0.441898] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441912] pci 0000:00:1d.7: PCI INT A disabled
[    0.441925] pci 0000:01:00.0: Boot video device
[    0.441933] PCI: CLS 32 bytes, default 64
[    0.442413] audit: initializing netlink socket (disabled)
[    0.442423] type=2000 audit(1349726318.436:1): initialized
[    0.463422] highmem bounce pool size: 64 pages
[    0.463427] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.466064] VFS: Disk quotas dquot_6.5.2
[    0.466127] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.466713] fuse init (API version 7.17)
[    0.466824] msgmni has been set to 1565
[    0.467376] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.467416] io scheduler noop registered
[    0.467423] io scheduler deadline registered
[    0.467433] io scheduler cfq registered (default)
[    0.467544] pcieport 0000:00:01.0: setting latency timer to 64
[    0.467573] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.467620] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.467654] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.467732] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.467757] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.467818] intel_idle: MWAIT substates: 0x20
[    0.467819] intel_idle: does not run on family 6 model 23
[    0.467902] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.467907] ACPI: Power Button [PWRB]
[    0.467952] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.467955] ACPI: Power Button [PWRF]
[    0.470626] ERST: Table is not found!
[    0.470629] GHES: HEST is not enabled!
[    0.470729] isapnp: Scanning for PnP cards...
[    0.470761] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.630506] Freeing initrd memory: 13828k freed
[    0.823593] isapnp: No Plug & Play device found
[    0.876587] Linux agpgart interface v0.103
[    0.878712] brd: module loaded
[    0.879736] loop: module loaded
[    0.879874] ahci 0000:00:1f.2: version 3.0
[    0.879886] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.879924] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.879971] ahci: SSS flag set, parallel bus scan disabled
[    0.880012] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.880016] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.880020] ahci 0000:00:1f.2: setting latency timer to 64
[    0.920617] scsi0 : ahci
[    0.920738] scsi1 : ahci
[    0.920842] scsi2 : ahci
[    0.920943] scsi3 : ahci
[    0.921047] scsi4 : ahci
[    0.921154] scsi5 : ahci
[    0.921321] ata1: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4100 irq 42
[    0.921324] ata2: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4180 irq 42
[    0.921327] ata3: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4200 irq 42
[    0.921329] ata4: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4280 irq 42
[    0.921332] ata5: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4300 irq 42
[    0.921334] ata6: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4380 irq 42
[    0.921759] Fixed MDIO Bus: probed
[    0.921779] tun: Universal TUN/TAP device driver, 1.6
[    0.921781] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.921858] PPP generic driver version 2.4.2
[    0.922016] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.922032] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.922046] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.922049] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.922118] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.922141] ehci_hcd 0000:00:1a.7: debug port 1
[    0.926026] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.926040] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9dc000
[    0.940014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.940179] hub 1-0:1.0: USB hub found
[    0.940183] hub 1-0:1.0: 6 ports detected
[    0.940260] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.940270] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.940273] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.940338] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.940359] ehci_hcd 0000:00:1d.7: debug port 1
[    0.944248] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.944261] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9d6000
[    0.960014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.960155] hub 2-0:1.0: USB hub found
[    0.960159] hub 2-0:1.0: 6 ports detected
[    0.960232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.960246] uhci_hcd: USB Universal Host Controller Interface driver
[    0.960261] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.960267] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.960270] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.960335] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.960364] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.960511] hub 3-0:1.0: USB hub found
[    0.960515] hub 3-0:1.0: 2 ports detected
[    0.960578] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.960585] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.960588] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.960662] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.960693] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.960838] hub 4-0:1.0: USB hub found
[    0.960842] hub 4-0:1.0: 2 ports detected
[    0.960910] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.960917] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.960920] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.960985] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.961014] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.961160] hub 5-0:1.0: USB hub found
[    0.961164] hub 5-0:1.0: 2 ports detected
[    0.961224] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.961230] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.961233] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.961300] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.961321] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.961468] hub 6-0:1.0: USB hub found
[    0.961471] hub 6-0:1.0: 2 ports detected
[    0.961534] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.961541] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.961544] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.961611] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.961632] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.961778] hub 7-0:1.0: USB hub found
[    0.961781] hub 7-0:1.0: 2 ports detected
[    0.961845] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.961851] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.961854] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.961922] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.961942] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.962089] hub 8-0:1.0: USB hub found
[    0.962093] hub 8-0:1.0: 2 ports detected
[    0.962207] usbcore: registered new interface driver libusual
[    0.962266] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.962624] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.962631] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.962793] mousedev: PS/2 mouse device common for all mice
[    0.963008] rtc_cmos 00:03: RTC can wake from S4
[    0.963130] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.963152] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.963210] device-mapper: uevent: version 1.0.3
[    0.963306] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.963338] EISA: Probing bus 0 at eisa.0
[    0.963340] EISA: Cannot allocate resource for mainboard
[    0.963342] Cannot allocate resource for EISA slot 1
[    0.963344] Cannot allocate resource for EISA slot 2
[    0.963345] Cannot allocate resource for EISA slot 3
[    0.963347] Cannot allocate resource for EISA slot 4
[    0.963349] Cannot allocate resource for EISA slot 5
[    0.963350] Cannot allocate resource for EISA slot 6
[    0.963352] Cannot allocate resource for EISA slot 7
[    0.963354] Cannot allocate resource for EISA slot 8
[    0.963355] EISA: Detected 0 cards.
[    0.963364] cpufreq-nforce2: No nForce2 chipset.
[    0.963366] cpuidle: using governor ladder
[    0.963368] cpuidle: using governor menu
[    0.963370] EFI Variables Facility v0.08 2004-May-17
[    0.963634] TCP cubic registered
[    0.963760] NET: Registered protocol family 10
[    0.964329] NET: Registered protocol family 17
[    0.964333] Registering the dns_resolver key type
[    0.964352] Using IPI No-Shortcut mode
[    0.964518] PM: Hibernation image not present or could not be loaded.
[    0.964530] registered taskstats version 1
[    0.971489]   Magic number: 0:85:1001
[    0.971530] rtc_cmos 00:03: hash matches
[    0.971591] rtc_cmos 00:03: setting system clock to 2012-10-08 19:58:40 UTC (1349726320)
[    0.972652] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.972654] EDD information not available.
[    0.978873] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.240019] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.243031] ata1.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.246902] ata1.00: configured for UDMA/100
[    1.252015] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.257621] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.266065] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.266068] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.266216] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.266318] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.440015] Refined TSC clocksource calibration: 2327.754 MHz.
[    1.440020] Switching to clocksource tsc
[    1.568012] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.584014] ata2: SATA link down (SStatus 0 SControl 300)
[    1.704274] Initializing USB Mass Storage driver...
[    1.704419] scsi6 : usb-storage 2-3:1.0
[    1.704490] usbcore: registered new interface driver usb-storage
[    1.704492] USB Mass Storage support registered.
[    1.904014] ata3: SATA link down (SStatus 0 SControl 300)
[    1.940013] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    2.224015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.239178] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.239182] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.240198] ata4.00: configured for UDMA/133
[    2.240300] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.240470] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.240477] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.240577] sd 3:0:0:0: [sda] Write Protect is off
[    2.240585] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.240614] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.283075]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.283493] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.560014] ata5: SATA link down (SStatus 0 SControl 300)
[    2.704859] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.705460] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.706027] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.706174] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.709572] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.710334] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.880021] ata6: SATA link down (SStatus 0 SControl 300)
[    2.880105] Freeing unused kernel memory: 740k freed
[    2.880354] Write protecting the kernel text: 5820k
[    2.880383] Write protecting the kernel read-only data: 2376k
[    2.880385] NX-protecting the kernel data: 4420k
[    2.897298] udevd[113]: starting version 175
[    2.931119] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.931122] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.931163] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.931173] e1000e 0000:00:19.0: setting latency timer to 64
[    2.931276] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.934203] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.934213] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.935210] generic-usb 0003:058F:6363.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.950624] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.950911] generic-usb 0003:046D:C51B.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    2.964167] generic-usb 0003:046D:C51B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    2.964187] usbcore: registered new interface driver usbhid
[    2.964188] usbhid: USB HID core driver
[    2.996053] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.118453] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:f4:ca:94
[    3.118457] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.118477] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    3.336992] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.336995] EXT4-fs (sda6): write access will be enabled during recovery
[    3.496112] firewire_core: created device fw0: GUID 001d72ffae924fff, S400
[    6.257244] EXT4-fs (sda6): recovery complete
[    6.257590] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.338585] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.363651] udevd[360]: starting version 175
[   15.400937] lp: driver loaded but no devices found
[   15.403306] Adding 9068540k swap on /dev/sda5.  Priority:-1 extents:1 across:9068540k 
[   15.403381] [drm] Initialized drm 1.1.0 20060810
[   15.424746] [drm] radeon defaulting to kernel modesetting.
[   15.424750] [drm] radeon kernel modesetting enabled.
[   15.424810] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.424816] radeon 0000:01:00.0: setting latency timer to 64
[   15.425170] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x174B:0xE990).
[   15.425195] [drm] register mmio base: 0xFEAF0000
[   15.425196] [drm] register mmio size: 65536
[   15.425319] ATOM BIOS: 11X
[   15.425342] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   15.425345] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   15.427461] [drm] Detected VRAM RAM=512M, BAR=256M
[   15.427464] [drm] RAM width 64bits DDR
[   15.429123] [TTM] Zone  kernel: Available graphics memory: 408100 kiB.
[   15.429125] [TTM] Zone highmem: Available graphics memory: 3096904 kiB.
[   15.429127] [TTM] Initializing pool allocator.
[   15.429150] [drm] radeon: 512M of VRAM memory ready
[   15.429152] [drm] radeon: 512M of GTT memory ready.
[   15.429167] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.429168] [drm] Driver supports precise vblank timestamp query.
[   15.429212] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   15.429218] radeon 0000:01:00.0: radeon: using MSI.
[   15.429249] [drm] radeon: irq initialized.
[   15.429254] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.429986] [drm] Loading RV710 Microcode
[   15.435207] type=1400 audit(1349719134.958:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=467 comm="apparmor_parser"
[   15.435653] type=1400 audit(1349719134.958:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=467 comm="apparmor_parser"
[   15.435898] type=1400 audit(1349719134.958:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=467 comm="apparmor_parser"
[   15.449855] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.449907] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.449933] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.470292] wmi: Mapper loaded
[   15.492182] cfg80211: Calling CRDA to update world regulatory domain
[   15.574752] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.605912] cfg80211: World regulatory domain updated:
[   15.605915] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.605917] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.605920] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.605922] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.605925] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.605927] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.624051] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
[   15.670249] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   15.670300] radeon 0000:01:00.0: WB enabled
[   15.716261] [drm] ring test succeeded in 1 usecs
[   15.716426] [drm] radeon: ib pool ready.
[   15.716497] [drm] ib test succeeded in 0 usecs
[   15.716849] [drm] Radeon Display Connectors
[   15.716851] [drm] Connector 0:
[   15.716852] [drm]   VGA
[   15.716855] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.716856] [drm]   Encoders:
[   15.716858] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   15.716859] [drm] Connector 1:
[   15.716861] [drm]   HDMI-A
[   15.716862] [drm]   HPD1
[   15.716864] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.716865] [drm]   Encoders:
[   15.716867] [drm]     DFP1: INTERNAL_UNIPHY
[   15.716868] [drm] Connector 2:
[   15.716870] [drm]   DVI-I
[   15.716871] [drm]   HPD4
[   15.716873] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   15.716874] [drm]   Encoders:
[   15.716876] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.716877] [drm]     DFP2: INTERNAL_UNIPHY2
[   15.716896] [drm] Internal thermal controller with fan control
[   15.716938] [drm] radeon: power management initialized
[   15.772047] init: failsafe main process (735) killed by TERM signal
[   15.789250] [drm] fb mappable at 0xD0142000
[   15.789253] [drm] vram apper at 0xD0000000
[   15.789255] [drm] size 5242880
[   15.789256] [drm] fb depth is 24
[   15.789258] [drm]    pitch is 5120
[   15.789351] fbcon: radeondrmfb (fb0) is primary device
[   15.789458] Console: switching to colour frame buffer device 160x64
[   15.789490] fb0: radeondrmfb frame buffer device
[   15.789492] drm: registered panic notifier
[   15.789498] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   15.795825] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.795829] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795831] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.795834] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795836] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.795839] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795841] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.795844] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795846] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.795848] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795850] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.795853] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795855] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.795858] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795860] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.795863] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795865] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.795867] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795870] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.795872] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795874] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.795877] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.795879] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.795881] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.795884] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.795886] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.795888] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.795891] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.798825] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.799456] Registered led device: rt2800usb-phy0::radio
[   15.799478] Registered led device: rt2800usb-phy0::assoc
[   15.799500] Registered led device: rt2800usb-phy0::quality
[   15.799531] usbcore: registered new interface driver rt2800usb
[   15.823588] Bluetooth: Core ver 2.16
[   15.823637] NET: Registered protocol family 31
[   15.823639] Bluetooth: HCI device and connection manager initialized
[   15.823642] Bluetooth: HCI socket layer initialized
[   15.823644] Bluetooth: L2CAP socket layer initialized
[   15.823694] Bluetooth: SCO socket layer initialized
[   15.830153] Bluetooth: RFCOMM TTY layer initialized
[   15.830158] Bluetooth: RFCOMM socket layer initialized
[   15.830160] Bluetooth: RFCOMM ver 1.11
[   15.838331] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.838334] Bluetooth: BNEP filters: protocol multicast
[   15.869107] ppdev: user-space parallel port driver
[   15.884186] type=1400 audit(1349719135.410:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=845 comm="apparmor_parser"
[   15.884725] type=1400 audit(1349719135.410:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=845 comm="apparmor_parser"
[   16.008200] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   16.064054] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   16.064273] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.064601] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.212254] type=1400 audit(1349719135.738:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=880 comm="apparmor_parser"
[   16.212662] type=1400 audit(1349719135.738:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=881 comm="apparmor_parser"
[   16.213106] type=1400 audit(1349719135.738:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=881 comm="apparmor_parser"
[   16.213673] type=1400 audit(1349719135.738:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=881 comm="apparmor_parser"
[   16.217056] type=1400 audit(1349719135.742:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=884 comm="apparmor_parser"
[   16.260157] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.260602] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.323891] init: alsa-restore main process (931) terminated with status 19

........

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic-pae 3.2.28)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01100 (reserved)
[    0.000000]  BIOS-e820: 00000000fed02000 - 00000000fed14c00 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire X3810/WG43M, BIOS P01-A3 05/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ee000 - 3726f000
[    0.000000] ACPI: RSDP 000fa770 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff90100 0006C (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bff90290 000F4 (v04 052609 FACP2056 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bff905c0 061D5 (v02   P01-   P01-A3 000000A3 INTL 20051117)
[    0.000000] ACPI: FACS bff9e000 00040
[    0.000000] ACPI: APIC bff90390 0006C (v02 052609 APIC2056 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bff90400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: SLIC bff90440 00176 (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bff9e040 00072 (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bff9a5c0 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bff9e0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: AWMI bffa00f0 0004E (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffa0940 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6276MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572638
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f2cee200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331849 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558301
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6179240k/7340032k available (5818k kernel code, 111312k reserved, 2846k data, 740k init, 5377608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.731 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.46 BogoMIPS (lpj=9310924)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004093] Mount-cache hash table entries: 512
[    0.004217] Initializing cgroup subsys cpuacct
[    0.004223] Initializing cgroup subsys memory
[    0.004230] Initializing cgroup subsys devices
[    0.004232] Initializing cgroup subsys freezer
[    0.004234] Initializing cgroup subsys blkio
[    0.004240] Initializing cgroup subsys perf_event
[    0.004264] CPU: Physical Processor ID: 0
[    0.004266] CPU: Processor Core ID: 0
[    0.004269] mce: CPU supports 6 MCE banks
[    0.004276] CPU0: Thermal monitoring enabled (TM2)
[    0.004279] using mwait in idle threads.
[    0.009713] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 26555 entries in 52 pages
[    0.024042] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024386] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066481] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.068003] APIC calibration not consistent with PM-Timer: 135ms instead of 100ms
[    0.068003] APIC delta adjusted to PM-Timer: 2078348 (2826523)
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156033] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156124] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.156126]  #2
[    0.156128] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248117] CPU 3 irqstacks, hard=f752e000 soft=f7538000
[    0.248118]  #3 Ok.
[    0.248120] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.340037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340060] Brought up 4 CPUs
[    0.340063] Total of 4 processors activated (18621.96 BogoMIPS).
[    0.343012] devtmpfs: initialized
[    0.343012] EVM: security.selinux
[    0.343012] EVM: security.SMACK64
[    0.343012] EVM: security.capability
[    0.343012] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.344574] print_constraints: dummy: 
[    0.344601] RTC time: 18:40:09, date: 10/07/12
[    0.344639] NET: Registered protocol family 16
[    0.344648] Trying to unpack rootfs image as initramfs...
[    0.344769] EISA bus registered
[    0.344796] ACPI: bus type pci registered
[    0.344859] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.344862] PCI: not using MMCONFIG
[    0.344936] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.344995] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.344997] PCI: Using configuration type 1 for base access
[    0.346082] bio: create slab <bio-0> at 0
[    0.346082] ACPI: Added _OSI(Module Device)
[    0.346082] ACPI: Added _OSI(Processor Device)
[    0.346082] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.346082] ACPI: Added _OSI(Processor Aggregator Device)
[    0.346082] ACPI: EC: Look up EC in DSDT
[    0.348958] ACPI: Executed 1 blocks of module-level executable AML code
[    0.351649] ACPI: SSDT bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.351959] ACPI: Dynamic OEM Table Load:
[    0.351962] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.352255] ACPI: SSDT bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352564] ACPI: Dynamic OEM Table Load:
[    0.352567] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352845] ACPI: SSDT bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353155] ACPI: Dynamic OEM Table Load:
[    0.353158] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353428] ACPI: SSDT bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353740] ACPI: Dynamic OEM Table Load:
[    0.353744] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353931] ACPI: Interpreter enabled
[    0.353937] ACPI: (supports S0 S3 S4 S5)
[    0.353956] ACPI: Using IOAPIC for interrupt routing
[    0.353982] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.355174] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.355177] PCI: Using MMCONFIG for extended config space
[    0.360658] ACPI: No dock devices found.
[    0.360661] HEST: Table not found.
[    0.360666] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.360751] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360928] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.360931] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.360934] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.360936] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.360939] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.360941] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.360954] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.360998] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.361036] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.361039] pci 0000:00:01.0: PME# disabled
[    0.361077] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    0.361094] pci 0000:00:19.0: reg 10: [mem 0xfe9e0000-0xfe9fffff]
[    0.361102] pci 0000:00:19.0: reg 14: [mem 0xfe9de000-0xfe9defff]
[    0.361111] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.361170] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.361173] pci 0000:00:19.0: PME# disabled
[    0.361191] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.361231] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.361279] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.361320] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.361368] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.361408] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.361464] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.361484] pci 0000:00:1a.7: reg 10: [mem 0xfe9dc000-0xfe9dc3ff]
[    0.361570] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.361574] pci 0000:00:1a.7: PME# disabled
[    0.361596] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.361611] pci 0000:00:1b.0: reg 10: [mem 0xfe9d8000-0xfe9dbfff 64bit]
[    0.361673] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.361677] pci 0000:00:1b.0: PME# disabled
[    0.361696] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.361760] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.361764] pci 0000:00:1c.0: PME# disabled
[    0.361790] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.361832] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.361881] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.361920] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.361968] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.362008] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.362064] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.362084] pci 0000:00:1d.7: reg 10: [mem 0xfe9d6000-0xfe9d63ff]
[    0.362171] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.362175] pci 0000:00:1d.7: PME# disabled
[    0.362194] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.362253] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.362365] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.362382] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.362390] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.362398] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.362405] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.362414] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb41f]
[    0.362422] pci 0000:00:1f.2: reg 24: [mem 0xfe9d4000-0xfe9d47ff]
[    0.362465] pci 0000:00:1f.2: PME# supported from D3hot
[    0.362469] pci 0000:00:1f.2: PME# disabled
[    0.362484] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.362498] pci 0000:00:1f.3: reg 10: [mem 0xfe9d3c00-0xfe9d3cff 64bit]
[    0.362518] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.362575] pci 0000:01:00.0: [1002:954f] type 0 class 0x000300
[    0.362588] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362599] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.362606] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.362619] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.362649] pci 0000:01:00.0: supports D1 D2
[    0.362668] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.362681] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.362740] pci 0000:01:00.1: supports D1 D2
[    0.362769] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362772] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.362776] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.362780] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362835] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.362857] pci 0000:02:00.0: reg 10: [mem 0xfebff800-0xfebfffff 64bit]
[    0.362869] pci 0000:02:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.362961] pci 0000:02:00.0: supports D2
[    0.362963] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.362968] pci 0000:02:00.0: PME# disabled
[    0.368040] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.368045] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.368049] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.368112] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.368122] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.368124] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.368127] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.368129] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.368132] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.368134] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.368152] pci_bus 0000:00: on NUMA node 0
[    0.368162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.368376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.368428]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.368431]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.368433] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.377212] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.377261] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.377304] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.377351] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.377397] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.377443] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.377490] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.377536] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.377648] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.377648] vgaarb: loaded
[    0.377648] vgaarb: bridge control possible 0000:01:00.0
[    0.377648] i2c-core: driver [aat2870] using legacy suspend method
[    0.377648] i2c-core: driver [aat2870] using legacy resume method
[    0.377648] SCSI subsystem initialized
[    0.377648] libata version 3.00 loaded.
[    0.377648] usbcore: registered new interface driver usbfs
[    0.377648] usbcore: registered new interface driver hub
[    0.377648] usbcore: registered new device driver usb
[    0.377648] PCI: Using ACPI for IRQ routing
[    0.377648] PCI: pci_cache_line_size set to 64 bytes
[    0.377648] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.377648] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.377648] NetLabel: Initializing
[    0.377648] NetLabel:  domain hash size = 128
[    0.377648] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.377648] NetLabel:  unlabeled traffic allowed by default
[    0.377648] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.377648] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.377648] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.392165] Switching to clocksource hpet
[    0.400292] AppArmor: AppArmor Filesystem Enabled
[    0.400321] pnp: PnP ACPI init
[    0.400338] ACPI: bus type pnp registered
[    0.400455] pnp 00:00: [bus 00-ff]
[    0.400458] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.400460] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.400462] pnp 00:00: [io  0x0d00-0xffff window]
[    0.400464] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.400467] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.400469] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.400471] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.400527] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.400537] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.400539] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.400594] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.400597] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.400600] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.400636] pnp 00:02: [dma 4]
[    0.400638] pnp 00:02: [io  0x0000-0x000f]
[    0.400640] pnp 00:02: [io  0x0081-0x0083]
[    0.400642] pnp 00:02: [io  0x0087]
[    0.400644] pnp 00:02: [io  0x0089-0x008b]
[    0.400646] pnp 00:02: [io  0x008f]
[    0.400648] pnp 00:02: [io  0x00c0-0x00df]
[    0.400675] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.400686] pnp 00:03: [io  0x0070-0x0071]
[    0.400696] pnp 00:03: [irq 8]
[    0.400725] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.400753] pnp 00:04: [io  0x0060]
[    0.400756] pnp 00:04: [io  0x0064]
[    0.400761] pnp 00:04: [irq 1]
[    0.400789] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.400833] pnp 00:05: [irq 12]
[    0.400862] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.400871] pnp 00:06: [io  0x0061]
[    0.400901] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.400910] pnp 00:07: [io  0x00f0-0x00ff]
[    0.400915] pnp 00:07: [irq 13]
[    0.400943] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.401338] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.401341] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.401343] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.401347] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.401349] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.401400] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.401402] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.401405] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.401407] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.401411] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401519] pnp 00:09: [io  0x0010-0x001f]
[    0.401522] pnp 00:09: [io  0x0022-0x003f]
[    0.401524] pnp 00:09: [io  0x0044-0x005f]
[    0.401526] pnp 00:09: [io  0x0062-0x0063]
[    0.401528] pnp 00:09: [io  0x0065-0x006f]
[    0.401529] pnp 00:09: [io  0x0072-0x007f]
[    0.401531] pnp 00:09: [io  0x0080]
[    0.401533] pnp 00:09: [io  0x0084-0x0086]
[    0.401535] pnp 00:09: [io  0x0088]
[    0.401537] pnp 00:09: [io  0x008c-0x008e]
[    0.401539] pnp 00:09: [io  0x0090-0x009f]
[    0.401541] pnp 00:09: [io  0x00a2-0x00bf]
[    0.401543] pnp 00:09: [io  0x00e0-0x00ef]
[    0.401545] pnp 00:09: [io  0x04d0-0x04d1]
[    0.401547] pnp 00:09: [io  0x0800-0x087f]
[    0.401549] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.401551] pnp 00:09: [io  0x0500-0x057f]
[    0.401553] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.401555] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.401557] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.401618] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.401621] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.401623] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.401626] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.401629] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.401632] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.401635] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401690] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.401720] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.401769] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.401771] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.401804] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.401844] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.401893] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.401896] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401974] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.401977] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.402026] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.402029] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.402033] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402077] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.402124] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.402127] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402302] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.402305] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.402307] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.402309] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.402311] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.402372] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.402375] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.402377] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.402380] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.402383] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.402386] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.402516] pnp: PnP ACPI: found 16 devices
[    0.402517] ACPI: ACPI bus type pnp unregistered
[    0.402520] PnPBIOS: Disabled by ACPI PNP
[    0.440589] PCI: max bus depth: 1 pci_try_num: 2
[    0.440621] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440624] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.440627] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.440631] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.440634] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440638] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.440641] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.440645] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.440649] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440655] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.440681] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.440685] pci 0000:00:01.0: setting latency timer to 64
[    0.440695] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.440699] pci 0000:00:1c.0: setting latency timer to 64
[    0.440705] pci 0000:00:1e.0: setting latency timer to 64
[    0.440709] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.440711] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.440713] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440715] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440718] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440720] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440723] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.440725] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.440728] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440730] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.440732] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.440735] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440737] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.440740] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.440742] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440744] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440747] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440749] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440791] NET: Registered protocol family 2
[    0.440862] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.441082] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.441408] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.441574] TCP: Hash tables configured (established 131072 bind 65536)
[    0.441576] TCP reno registered
[    0.441579] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.441587] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.441668] NET: Registered protocol family 1
[    0.441698] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.441715] pci 0000:00:1a.0: PCI INT A disabled
[    0.441729] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.441744] pci 0000:00:1a.1: PCI INT B disabled
[    0.441754] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.441769] pci 0000:00:1a.2: PCI INT D disabled
[    0.441780] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441810] pci 0000:00:1a.7: PCI INT C disabled
[    0.441825] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441840] pci 0000:00:1d.0: PCI INT A disabled
[    0.441846] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.441861] pci 0000:00:1d.1: PCI INT B disabled
[    0.441867] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441882] pci 0000:00:1d.2: PCI INT C disabled
[    0.441890] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441903] pci 0000:00:1d.7: PCI INT A disabled
[    0.441917] pci 0000:01:00.0: Boot video device
[    0.441925] PCI: CLS 32 bytes, default 64
[    0.442416] audit: initializing netlink socket (disabled)
[    0.442425] type=2000 audit(1349635208.436:1): initialized
[    0.463423] highmem bounce pool size: 64 pages
[    0.463428] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.466064] VFS: Disk quotas dquot_6.5.2
[    0.466127] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.466708] fuse init (API version 7.17)
[    0.466824] msgmni has been set to 1565
[    0.467374] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.467415] io scheduler noop registered
[    0.467421] io scheduler deadline registered
[    0.467431] io scheduler cfq registered (default)
[    0.467543] pcieport 0000:00:01.0: setting latency timer to 64
[    0.467573] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.467621] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.467655] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.467733] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.467757] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.467819] intel_idle: MWAIT substates: 0x20
[    0.467820] intel_idle: does not run on family 6 model 23
[    0.467901] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.467907] ACPI: Power Button [PWRB]
[    0.467952] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.467955] ACPI: Power Button [PWRF]
[    0.470625] ERST: Table is not found!
[    0.470627] GHES: HEST is not enabled!
[    0.470717] isapnp: Scanning for PnP cards...
[    0.470742] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.631377] Freeing initrd memory: 13828k freed
[    0.823613] isapnp: No Plug & Play device found
[    0.880519] Linux agpgart interface v0.103
[    0.882636] brd: module loaded
[    0.883657] loop: module loaded
[    0.883798] ahci 0000:00:1f.2: version 3.0
[    0.883810] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.883848] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.883894] ahci: SSS flag set, parallel bus scan disabled
[    0.883926] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.883929] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.883933] ahci 0000:00:1f.2: setting latency timer to 64
[    0.924606] scsi0 : ahci
[    0.924720] scsi1 : ahci
[    0.924818] scsi2 : ahci
[    0.924917] scsi3 : ahci
[    0.925019] scsi4 : ahci
[    0.925117] scsi5 : ahci
[    0.925281] ata1: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4100 irq 42
[    0.925284] ata2: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4180 irq 42
[    0.925286] ata3: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4200 irq 42
[    0.925289] ata4: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4280 irq 42
[    0.925291] ata5: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4300 irq 42
[    0.925294] ata6: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4380 irq 42
[    0.925706] Fixed MDIO Bus: probed
[    0.925726] tun: Universal TUN/TAP device driver, 1.6
[    0.925729] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.925808] PPP generic driver version 2.4.2
[    0.925966] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.925983] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.925996] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.925999] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.926066] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.926089] ehci_hcd 0000:00:1a.7: debug port 1
[    0.929958] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.929972] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9dc000
[    0.944015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.944181] hub 1-0:1.0: USB hub found
[    0.944186] hub 1-0:1.0: 6 ports detected
[    0.944267] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.944277] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.944281] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.944352] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.944372] ehci_hcd 0000:00:1d.7: debug port 1
[    0.948241] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.948255] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9d6000
[    0.964014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.964150] hub 2-0:1.0: USB hub found
[    0.964154] hub 2-0:1.0: 6 ports detected
[    0.964228] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.964242] uhci_hcd: USB Universal Host Controller Interface driver
[    0.964257] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.964264] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.964267] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.964329] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.964360] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.964508] hub 3-0:1.0: USB hub found
[    0.964512] hub 3-0:1.0: 2 ports detected
[    0.964577] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.964583] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.964586] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.964661] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.964690] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.964838] hub 4-0:1.0: USB hub found
[    0.964842] hub 4-0:1.0: 2 ports detected
[    0.964908] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.964915] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.964918] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.964987] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.965017] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.965161] hub 5-0:1.0: USB hub found
[    0.965165] hub 5-0:1.0: 2 ports detected
[    0.965226] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.965232] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.965235] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.965300] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.965321] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.965474] hub 6-0:1.0: USB hub found
[    0.965477] hub 6-0:1.0: 2 ports detected
[    0.965539] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.965545] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.965548] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.965614] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.965634] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.965781] hub 7-0:1.0: USB hub found
[    0.965785] hub 7-0:1.0: 2 ports detected
[    0.965846] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.965852] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.965855] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.965921] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.965942] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.966093] hub 8-0:1.0: USB hub found
[    0.966097] hub 8-0:1.0: 2 ports detected
[    0.966214] usbcore: registered new interface driver libusual
[    0.966272] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.966633] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.966640] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.966797] mousedev: PS/2 mouse device common for all mice
[    0.967014] rtc_cmos 00:03: RTC can wake from S4
[    0.967136] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.967158] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.967217] device-mapper: uevent: version 1.0.3
[    0.967312] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.967344] EISA: Probing bus 0 at eisa.0
[    0.967347] EISA: Cannot allocate resource for mainboard
[    0.967349] Cannot allocate resource for EISA slot 1
[    0.967350] Cannot allocate resource for EISA slot 2
[    0.967352] Cannot allocate resource for EISA slot 3
[    0.967354] Cannot allocate resource for EISA slot 4
[    0.967355] Cannot allocate resource for EISA slot 5
[    0.967357] Cannot allocate resource for EISA slot 6
[    0.967359] Cannot allocate resource for EISA slot 7
[    0.967360] Cannot allocate resource for EISA slot 8
[    0.967362] EISA: Detected 0 cards.
[    0.967371] cpufreq-nforce2: No nForce2 chipset.
[    0.967373] cpuidle: using governor ladder
[    0.967375] cpuidle: using governor menu
[    0.967376] EFI Variables Facility v0.08 2004-May-17
[    0.967641] TCP cubic registered
[    0.967765] NET: Registered protocol family 10
[    0.968334] NET: Registered protocol family 17
[    0.968338] Registering the dns_resolver key type
[    0.968360] Using IPI No-Shortcut mode
[    0.968527] PM: Hibernation image not present or could not be loaded.
[    0.968539] registered taskstats version 1
[    0.975565]   Magic number: 0:592:695
[    0.975608] pci 0000:00:00.0: hash matches
[    0.975666] rtc_cmos 00:03: setting system clock to 2012-10-07 18:40:10 UTC (1349635210)
[    0.976725] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.976727] EDD information not available.
[    0.983361] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.244021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.247033] ata1.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.250904] ata1.00: configured for UDMA/100
[    1.256016] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.261622] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.270067] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.270071] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.270217] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.270302] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.440016] Refined TSC clocksource calibration: 2327.754 MHz.
[    1.440021] Switching to clocksource tsc
[    1.572012] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.588016] ata2: SATA link down (SStatus 0 SControl 300)
[    1.708358] Initializing USB Mass Storage driver...
[    1.708524] scsi6 : usb-storage 2-3:1.0
[    1.708604] usbcore: registered new interface driver usb-storage
[    1.708606] USB Mass Storage support registered.
[    1.908014] ata3: SATA link down (SStatus 0 SControl 300)
[    1.944010] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    2.228015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.247643] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.247647] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.248664] ata4.00: configured for UDMA/133
[    2.248785] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.248945] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.248952] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.249018] sd 3:0:0:0: [sda] Write Protect is off
[    2.249021] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.249057] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.291539]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.291954] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.568014] ata5: SATA link down (SStatus 0 SControl 300)
[    2.708842] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.709466] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.710273] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.710478] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.713944] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.714706] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.888014] ata6: SATA link down (SStatus 0 SControl 300)
[    2.888107] Freeing unused kernel memory: 740k freed
[    2.888365] Write protecting the kernel text: 5820k
[    2.888394] Write protecting the kernel read-only data: 2376k
[    2.888395] NX-protecting the kernel data: 4420k
[    2.905419] udevd[113]: starting version 175
[    2.938574] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.938577] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.938617] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.938626] e1000e 0000:00:19.0: setting latency timer to 64
[    2.938715] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.950042] generic-usb 0003:058F:6363.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.957113] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.957121] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.965595] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.965699] generic-usb 0003:046D:C51B.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    2.979142] generic-usb 0003:046D:C51B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    2.979166] usbcore: registered new interface driver usbhid
[    2.979168] usbhid: USB HID core driver
[    3.020051] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.126350] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:f4:ca:94
[    3.126353] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.126376] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    3.520089] firewire_core: created device fw0: GUID 001d72ffae924fff, S400
[    3.591332] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   12.922233] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.938394] udevd[334]: starting version 175
[   12.973776] lp: driver loaded but no devices found
[   12.985516] [drm] Initialized drm 1.1.0 20060810
[   12.991296] Adding 9068540k swap on /dev/sda5.  Priority:-1 extents:1 across:9068540k 
[   13.002830] cfg80211: Calling CRDA to update world regulatory domain
[   13.012940] [drm] radeon defaulting to kernel modesetting.
[   13.012942] [drm] radeon kernel modesetting enabled.
[   13.013029] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.013035] radeon 0000:01:00.0: setting latency timer to 64
[   13.013721] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x174B:0xE990).
[   13.013744] [drm] register mmio base: 0xFEAF0000
[   13.013746] [drm] register mmio size: 65536
[   13.013863] ATOM BIOS: 11X
[   13.014074] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   13.014077] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   13.016245] [drm] Detected VRAM RAM=512M, BAR=256M
[   13.016248] [drm] RAM width 64bits DDR
[   13.016589] [TTM] Zone  kernel: Available graphics memory: 408100 kiB.
[   13.016591] [TTM] Zone highmem: Available graphics memory: 3096904 kiB.
[   13.016593] [TTM] Initializing pool allocator.
[   13.016618] [drm] radeon: 512M of VRAM memory ready
[   13.016620] [drm] radeon: 512M of GTT memory ready.
[   13.016690] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.016692] [drm] Driver supports precise vblank timestamp query.
[   13.016738] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   13.016743] radeon 0000:01:00.0: radeon: using MSI.
[   13.016776] [drm] radeon: irq initialized.
[   13.016781] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.017874] [drm] Loading RV710 Microcode
[   13.027014] type=1400 audit(1349628022.547:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=438 comm="apparmor_parser"
[   13.027426] type=1400 audit(1349628022.547:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=438 comm="apparmor_parser"
[   13.027662] type=1400 audit(1349628022.547:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=438 comm="apparmor_parser"
[   13.028615] wmi: Mapper loaded
[   13.098258] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.098304] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.098857] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   13.133985] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
[   13.183809] cfg80211: World regulatory domain updated:
[   13.183812] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.183815] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.183818] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.183820] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.183823] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.183825] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.229403] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   13.229460] radeon 0000:01:00.0: WB enabled
[   13.275394] [drm] ring test succeeded in 1 usecs
[   13.275534] [drm] radeon: ib pool ready.
[   13.275613] [drm] ib test succeeded in 0 usecs
[   13.276163] [drm] Radeon Display Connectors
[   13.276165] [drm] Connector 0:
[   13.276167] [drm]   VGA
[   13.276169] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   13.276171] [drm]   Encoders:
[   13.276172] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   13.276173] [drm] Connector 1:
[   13.276175] [drm]   HDMI-A
[   13.276176] [drm]   HPD1
[   13.276178] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   13.276180] [drm]   Encoders:
[   13.276181] [drm]     DFP1: INTERNAL_UNIPHY
[   13.276183] [drm] Connector 2:
[   13.276184] [drm]   DVI-I
[   13.276185] [drm]   HPD4
[   13.276187] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   13.276189] [drm]   Encoders:
[   13.276190] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.276192] [drm]     DFP2: INTERNAL_UNIPHY2
[   13.276210] [drm] Internal thermal controller with fan control
[   13.276255] [drm] radeon: power management initialized
[   13.307581] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.307585] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307587] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.307590] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307592] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.307594] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307596] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.307599] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307601] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.307604] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307606] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.307608] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307611] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.307613] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307615] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.307618] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307620] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.307623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307625] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.307627] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307630] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.307632] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.307634] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.307637] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.307639] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.307642] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.307644] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.307646] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.310106] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.310734] Registered led device: rt2800usb-phy0::radio
[   13.310756] Registered led device: rt2800usb-phy0::assoc
[   13.310778] Registered led device: rt2800usb-phy0::quality
[   13.310810] usbcore: registered new interface driver rt2800usb
[   13.349802] [drm] fb mappable at 0xD0142000
[   13.349805] [drm] vram apper at 0xD0000000
[   13.349807] [drm] size 5242880
[   13.349808] [drm] fb depth is 24
[   13.349809] [drm]    pitch is 5120
[   13.349909] fbcon: radeondrmfb (fb0) is primary device
[   13.350013] Console: switching to colour frame buffer device 160x64
[   13.350044] fb0: radeondrmfb frame buffer device
[   13.350046] drm: registered panic notifier
[   13.350052] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   13.357981] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.691081] init: failsafe main process (764) killed by TERM signal
[   13.734871] Bluetooth: Core ver 2.16
[   13.734901] NET: Registered protocol family 31
[   13.734903] Bluetooth: HCI device and connection manager initialized
[   13.734905] Bluetooth: HCI socket layer initialized
[   13.734907] Bluetooth: L2CAP socket layer initialized
[   13.734955] Bluetooth: SCO socket layer initialized
[   13.738421] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.738424] Bluetooth: BNEP filters: protocol multicast
[   13.744669] Bluetooth: RFCOMM TTY layer initialized
[   13.744675] Bluetooth: RFCOMM socket layer initialized
[   13.744676] Bluetooth: RFCOMM ver 1.11
[   13.758403] ppdev: user-space parallel port driver
[   13.774004] type=1400 audit(1349628023.295:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=837 comm="apparmor_parser"
[   13.774525] type=1400 audit(1349628023.295:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=837 comm="apparmor_parser"
[   13.923617] type=1400 audit(1349628023.443:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=873 comm="apparmor_parser"
[   13.923786] type=1400 audit(1349628023.443:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=872 comm="apparmor_parser"
[   13.923970] type=1400 audit(1349628023.443:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=876 comm="apparmor_parser"
[   13.924142] type=1400 audit(1349628023.447:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=873 comm="apparmor_parser"
[   13.924383] type=1400 audit(1349628023.447:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=873 comm="apparmor_parser"
[   13.961981] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.014698] init: alsa-restore main process (917) terminated with status 19
[   14.016164] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.016392] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.016738] ADDRCONF(NETDEV_UP): eth0: link is not ready

....

[    16.373] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    16.373] X Protocol Version 11, Revision 0
[    16.373] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    16.373] Current Operating System: Linux Compuabajo 3.2.0-31-generic-pae #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 i686
[    16.373] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    16.373] Build Date: 29 August 2012  12:10:05AM
[    16.373] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    16.373] Current version of pixman: 0.24.4
[    16.373]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.373] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.373] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct  8 19:58:55 2012
[    16.399] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.399] (==) No Layout section.  Using the first Screen section.
[    16.399] (==) No screen section available. Using defaults.
[    16.399] (**) |-->Screen "Default Screen Section" (0)
[    16.399] (**) |   |-->Monitor "<default monitor>"
[    16.399] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.399] (==) Automatically adding devices
[    16.399] (==) Automatically enabling devices
[    16.399] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.399]     Entry deleted from font path.
[    16.399] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.399]     Entry deleted from font path.
[    16.399] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.399]     Entry deleted from font path.
[    16.399] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.399]     Entry deleted from font path.
[    16.399] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.399]     Entry deleted from font path.
[    16.399] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.399]     Entry deleted from font path.
[    16.399] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    16.399] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.399] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.399] (II) Loader magic: 0xb77495a0
[    16.399] (II) Module ABI versions:
[    16.399]     X.Org ANSI C Emulation: 0.4
[    16.399]     X.Org Video Driver: 11.0
[    16.399]     X.Org XInput driver : 16.0
[    16.399]     X.Org Server Extension : 6.0
[    16.400] (--) PCI:*(0:1:0:0) 1002:954f:174b:e990 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    16.400] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.400] (II) LoadModule: "extmod"
[    16.476] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.476] (II) Module extmod: vendor="X.Org Foundation"
[    16.476]     compiled for 1.11.3, module version = 1.0.0
[    16.476]     Module class: X.Org Server Extension
[    16.476]     ABI class: X.Org Server Extension, version 6.0
[    16.476] (II) Loading extension MIT-SCREEN-SAVER
[    16.476] (II) Loading extension XFree86-VidModeExtension
[    16.476] (II) Loading extension XFree86-DGA
[    16.476] (II) Loading extension DPMS
[    16.476] (II) Loading extension XVideo
[    16.476] (II) Loading extension XVideo-MotionCompensation
[    16.476] (II) Loading extension X-Resource
[    16.476] (II) LoadModule: "dbe"
[    16.476] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.476] (II) Module dbe: vendor="X.Org Foundation"
[    16.476]     compiled for 1.11.3, module version = 1.0.0
[    16.476]     Module class: X.Org Server Extension
[    16.476]     ABI class: X.Org Server Extension, version 6.0
[    16.476] (II) Loading extension DOUBLE-BUFFER
[    16.476] (II) LoadModule: "glx"
[    16.477] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.477] (II) Module glx: vendor="X.Org Foundation"
[    16.477]     compiled for 1.11.3, module version = 1.0.0
[    16.477]     ABI class: X.Org Server Extension, version 6.0
[    16.477] (==) AIGLX enabled
[    16.477] (II) Loading extension GLX
[    16.477] (II) LoadModule: "record"
[    16.477] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.477] (II) Module record: vendor="X.Org Foundation"
[    16.477]     compiled for 1.11.3, module version = 1.13.0
[    16.477]     Module class: X.Org Server Extension
[    16.477]     ABI class: X.Org Server Extension, version 6.0
[    16.477] (II) Loading extension RECORD
[    16.477] (II) LoadModule: "dri"
[    16.477] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.478] (II) Module dri: vendor="X.Org Foundation"
[    16.478]     compiled for 1.11.3, module version = 1.0.0
[    16.478]     ABI class: X.Org Server Extension, version 6.0
[    16.478] (II) Loading extension XFree86-DRI
[    16.478] (II) LoadModule: "dri2"
[    16.478] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.478] (II) Module dri2: vendor="X.Org Foundation"
[    16.478]     compiled for 1.11.3, module version = 1.2.0
[    16.478]     ABI class: X.Org Server Extension, version 6.0
[    16.478] (II) Loading extension DRI2
[    16.478] (==) Matched fglrx as autoconfigured driver 0
[    16.478] (==) Matched ati as autoconfigured driver 1
[    16.478] (==) Matched vesa as autoconfigured driver 2
[    16.478] (==) Matched fbdev as autoconfigured driver 3
[    16.478] (==) Assigned the driver to the xf86ConfigLayout
[    16.478] (II) LoadModule: "fglrx"
[    16.479] (WW) Warning, couldn't open module fglrx
[    16.479] (II) UnloadModule: "fglrx"
[    16.479] (II) Unloading fglrx
[    16.479] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.479] (II) LoadModule: "ati"
[    16.479] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.479] (II) Module ati: vendor="X.Org Foundation"
[    16.479]     compiled for 1.11.3, module version = 6.14.99
[    16.479]     Module class: X.Org Video Driver
[    16.479]     ABI class: X.Org Video Driver, version 11.0
[    16.479] (II) LoadModule: "radeon"
[    16.479] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.479] (II) Module radeon: vendor="X.Org Foundation"
[    16.479]     compiled for 1.11.3, module version = 6.14.99
[    16.479]     Module class: X.Org Video Driver
[    16.479]     ABI class: X.Org Video Driver, version 11.0
[    16.479] (II) LoadModule: "vesa"
[    16.480] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.480] (II) Module vesa: vendor="X.Org Foundation"
[    16.480]     compiled for 1.11.3, module version = 2.3.0
[    16.480]     Module class: X.Org Video Driver
[    16.480]     ABI class: X.Org Video Driver, version 11.0
[    16.480] (II) LoadModule: "fbdev"
[    16.480] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.480] (II) Module fbdev: vendor="X.Org Foundation"
[    16.480]     compiled for 1.11.3, module version = 0.4.2
[    16.480]     ABI class: X.Org Video Driver, version 11.0
[    16.480] (==) Matched fglrx as autoconfigured driver 0
[    16.480] (==) Matched ati as autoconfigured driver 1
[    16.480] (==) Matched vesa as autoconfigured driver 2
[    16.480] (==) Matched fbdev as autoconfigured driver 3
[    16.480] (==) Assigned the driver to the xf86ConfigLayout
[    16.480] (II) LoadModule: "fglrx"
[    16.481] (WW) Warning, couldn't open module fglrx
[    16.481] (II) UnloadModule: "fglrx"
[    16.481] (II) Unloading fglrx
[    16.481] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.481] (II) LoadModule: "ati"
[    16.481] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.481] (II) Module ati: vendor="X.Org Foundation"
[    16.481]     compiled for 1.11.3, module version = 6.14.99
[    16.481]     Module class: X.Org Video Driver
[    16.481]     ABI class: X.Org Video Driver, version 11.0
[    16.481] (II) LoadModule: "vesa"
[    16.481] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.481] (II) Module vesa: vendor="X.Org Foundation"
[    16.481]     compiled for 1.11.3, module version = 2.3.0
[    16.481]     Module class: X.Org Video Driver
[    16.481]     ABI class: X.Org Video Driver, version 11.0
[    16.481] (II) UnloadModule: "vesa"
[    16.481] (II) Unloading vesa
[    16.481] (II) Failed to load module "vesa" (already loaded, 0)
[    16.481] (II) LoadModule: "fbdev"
[    16.481] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.481] (II) Module fbdev: vendor="X.Org Foundation"
[    16.481]     compiled for 1.11.3, module version = 0.4.2
[    16.481]     ABI class: X.Org Video Driver, version 11.0
[    16.481] (II) UnloadModule: "fbdev"
[    16.481] (II) Unloading fbdev
[    16.481] (II) Failed to load module "fbdev" (already loaded, 0)
[    16.481] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    16.485] (II) VESA: driver for VESA chipsets: vesa
[    16.485] (II) FBDEV: driver for framebuffer: fbdev
[    16.485] (++) using VT number 7

[    16.485] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.485] (II) [KMS] Kernel modesetting enabled.
[    16.485] (WW) Falling back to old probe method for vesa
[    16.485] (WW) Falling back to old probe method for fbdev
[    16.485] (II) Loading sub module "fbdevhw"
[    16.485] (II) LoadModule: "fbdevhw"
[    16.486] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.486] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.486]     compiled for 1.11.3, module version = 0.0.2
[    16.486]     ABI class: X.Org Video Driver, version 11.0
[    16.486] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    16.486] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    16.486] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.486] (==) RADEON(0): Default visual is TrueColor
[    16.486] (==) RADEON(0): RGB weight 888
[    16.486] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    16.486] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[    16.486] (II) RADEON(0): PCIE card detected
[    16.486] drmOpenDevice: node name is /dev/dri/card0
[    16.486] drmOpenDevice: open result is 9, (OK)
[    16.486] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    16.486] drmOpenDevice: node name is /dev/dri/card0
[    16.486] drmOpenDevice: open result is 9, (OK)
[    16.486] drmOpenByBusid: drmOpenMinor returns 9
[    16.486] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    16.486] (II) Loading sub module "exa"
[    16.486] (II) LoadModule: "exa"
[    16.486] (II) Loading /usr/lib/xorg/modules/libexa.so
[    16.486] (II) Module exa: vendor="X.Org Foundation"
[    16.486]     compiled for 1.11.3, module version = 2.5.0
[    16.486]     ABI class: X.Org Video Driver, version 11.0
[    16.486] (II) RADEON(0): KMS Color Tiling: enabled
[    16.486] (II) RADEON(0): KMS Pageflipping: enabled
[    16.486] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    16.512] (II) RADEON(0): Output VGA-0 has no monitor section
[    16.516] (II) RADEON(0): Output HDMI-0 has no monitor section
[    16.572] (II) RADEON(0): Output DVI-0 has no monitor section
[    16.596] (II) RADEON(0): EDID for output VGA-0
[    16.600] (II) RADEON(0): EDID for output HDMI-0
[    16.656] (II) RADEON(0): EDID for output DVI-0
[    16.656] (II) RADEON(0): Manufacturer: DEL  Model: a00a  Serial#: 1111576887
[    16.656] (II) RADEON(0): Year: 2004  Week: 2
[    16.656] (II) RADEON(0): EDID Version: 1.3
[    16.656] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    16.656] (II) RADEON(0): Sync:  Separate
[    16.656] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    16.656] (II) RADEON(0): Gamma: 2.20
[    16.656] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    16.656] (II) RADEON(0): First detailed timing is preferred mode
[    16.656] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[    16.656] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[    16.656] (II) RADEON(0): Supported established timings:
[    16.656] (II) RADEON(0): 720x400@70Hz
[    16.656] (II) RADEON(0): 640x480@60Hz
[    16.656] (II) RADEON(0): 640x480@75Hz
[    16.656] (II) RADEON(0): 800x600@60Hz
[    16.656] (II) RADEON(0): 800x600@75Hz
[    16.656] (II) RADEON(0): 1024x768@60Hz
[    16.656] (II) RADEON(0): 1024x768@75Hz
[    16.656] (II) RADEON(0): 1280x1024@75Hz
[    16.656] (II) RADEON(0): Manufacturer's mask: 0
[    16.656] (II) RADEON(0): Supported standard timings:
[    16.656] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    16.656] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    16.656] (II) RADEON(0): Supported detailed timing:
[    16.656] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    16.656] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    16.656] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    16.656] (II) RADEON(0): Serial No: P144641ABAQ7
[    16.656] (II) RADEON(0): Monitor name: DELL E172FP
[    16.656] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 145 MHz
[    16.656] (II) RADEON(0): EDID (in hex):
[    16.656] (II) RADEON(0):     00ffffffffffff0010ac0aa037514142
[    16.657] (II) RADEON(0):     020e010368221b78eac5c6a3574a9c23
[    16.657] (II) RADEON(0):     124f54a54b00714f8180010101010101
[    16.657] (II) RADEON(0):     010101010101302a009851002a403070
[    16.657] (II) RADEON(0):     1300520e1100001e000000ff00503134
[    16.657] (II) RADEON(0):     3436343141424151370a000000fc0044
[    16.657] (II) RADEON(0):     454c4c204531373246500a20000000fd
[    16.657] (II) RADEON(0):     00384c1f500e000a202020202020000e
[    16.657] (II) RADEON(0): Printing probed modes for output DVI-0
[    16.657] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    16.657] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    16.657] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    16.657] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    16.657] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    16.657] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    16.657] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    16.657] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    16.657] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    16.657] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    16.657] (II) RADEON(0): Output VGA-0 disconnected
[    16.657] (II) RADEON(0): Output HDMI-0 disconnected
[    16.657] (II) RADEON(0): Output DVI-0 connected
[    16.657] (II) RADEON(0): Using exact sizes for initial modes
[    16.657] (II) RADEON(0): Output DVI-0 using initial mode 1280x1024
[    16.657] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    16.657] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fac0000
[    16.657] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    16.657] (==) RADEON(0): DPI set to (96, 96)
[    16.657] (II) Loading sub module "fb"
[    16.657] (II) LoadModule: "fb"
[    16.657] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.657] (II) Module fb: vendor="X.Org Foundation"
[    16.657]     compiled for 1.11.3, module version = 1.0.0
[    16.657]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.657] (II) Loading sub module "ramdac"
[    16.657] (II) LoadModule: "ramdac"
[    16.657] (II) Module "ramdac" already built-in
[    16.657] (II) UnloadModule: "vesa"
[    16.657] (II) Unloading vesa
[    16.657] (II) UnloadModule: "fbdev"
[    16.657] (II) Unloading fbdev
[    16.657] (II) UnloadModule: "fbdevhw"
[    16.657] (II) Unloading fbdevhw
[    16.657] (--) Depth 24 pixmap format is 32 bpp
[    16.657] (II) RADEON(0): [DRI2] Setup complete
[    16.657] (II) RADEON(0): [DRI2]   DRI driver: r600
[    16.657] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    16.658] (II) RADEON(0): Front buffer size: 5120K
[    16.658] (II) RADEON(0): VRAM usage limit set to 226483K
[    16.658] (==) RADEON(0): Backing store disabled
[    16.658] (II) RADEON(0): Direct rendering enabled
[    16.658] (II) RADEON(0): Setting EXA maxPitchBytes
[    16.658] (II) EXA(0): Driver allocated offscreen pixmaps
[    16.658] (II) EXA(0): Driver registered support for the following operations:
[    16.658] (II)         Solid
[    16.658] (II)         Copy
[    16.658] (II)         Composite (RENDER acceleration)
[    16.658] (II)         UploadToScreen
[    16.658] (II)         DownloadFromScreen
[    16.658] (II) RADEON(0): Acceleration enabled
[    16.658] (==) RADEON(0): DPMS enabled
[    16.658] (==) RADEON(0): Silken mouse enabled
[    16.658] (II) RADEON(0): Set up textured video
[    16.658] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    16.658] (II) RADEON(0): [XvMC] Extension initialized.
[    16.658] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.658] (--) RandR disabled
[    16.658] (II) Initializing built-in extension Generic Event Extension
[    16.658] (II) Initializing built-in extension SHAPE
[    16.658] (II) Initializing built-in extension MIT-SHM
[    16.658] (II) Initializing built-in extension XInputExtension
[    16.658] (II) Initializing built-in extension XTEST
[    16.658] (II) Initializing built-in extension BIG-REQUESTS
[    16.658] (II) Initializing built-in extension SYNC
[    16.658] (II) Initializing built-in extension XKEYBOARD
[    16.658] (II) Initializing built-in extension XC-MISC
[    16.658] (II) Initializing built-in extension SECURITY
[    16.658] (II) Initializing built-in extension XINERAMA
[    16.658] (II) Initializing built-in extension XFIXES
[    16.658] (II) Initializing built-in extension RENDER
[    16.658] (II) Initializing built-in extension RANDR
[    16.658] (II) Initializing built-in extension COMPOSITE
[    16.658] (II) Initializing built-in extension DAMAGE
[    16.677] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.677] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.677] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.677] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.678] (II) AIGLX: Loaded and initialized r600
[    16.678] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.678] (II) RADEON(0): Setting screen physical size to 338 x 270
[    16.686] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.689] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.689] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.689] (II) LoadModule: "evdev"
[    16.689] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.690] (II) Module evdev: vendor="X.Org Foundation"
[    16.690]     compiled for 1.11.3, module version = 2.7.0
[    16.690]     Module class: X.Org XInput Driver
[    16.690]     ABI class: X.Org XInput driver, version 16.0
[    16.690] (II) Using input driver 'evdev' for 'Power Button'
[    16.690] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.690] (**) Power Button: always reports core events
[    16.690] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.690] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.690] (--) evdev: Power Button: Found keys
[    16.690] (II) evdev: Power Button: Configuring as keyboard
[    16.690] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.690] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.690] (**) Option "xkb_rules" "evdev"
[    16.690] (**) Option "xkb_model" "pc105"
[    16.690] (**) Option "xkb_layout" "es"
[    16.692] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    16.693] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.693] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.693] (II) Using input driver 'evdev' for 'Power Button'
[    16.693] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.693] (**) Power Button: always reports core events
[    16.693] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.693] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.693] (--) evdev: Power Button: Found keys
[    16.693] (II) evdev: Power Button: Configuring as keyboard
[    16.693] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.693] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    16.693] (**) Option "xkb_rules" "evdev"
[    16.693] (**) Option "xkb_model" "pc105"
[    16.693] (**) Option "xkb_layout" "es"
[    16.694] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    16.694] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.694] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.694] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.694] (**) Logitech USB Receiver: always reports core events
[    16.694] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[    16.694] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51b
[    16.694] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    16.694] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    16.694] (--) evdev: Logitech USB Receiver: Found relative axes
[    16.694] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    16.694] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    16.694] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    16.694] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.694] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.694] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3/event3"
[    16.694] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 8)
[    16.694] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    16.694] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    16.694] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    16.694] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    16.694] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    16.695] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    16.695] (II) No input driver specified, ignoring this device.
[    16.695] (II) This device may have been added with another device file.
[    16.695] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    16.695] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.695] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.695] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.695] (**) AT Translated Set 2 keyboard: always reports core events
[    16.695] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    16.695] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.695] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.695] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.695] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    16.695] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    16.695] (**) Option "xkb_rules" "evdev"
[    16.695] (**) Option "xkb_model" "pc105"
[    16.695] (**) Option "xkb_layout" "es"
[    17.396] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[    17.396] (II) RADEON(0): Using EDID range info for horizontal sync
[    17.396] (II) RADEON(0): Using EDID range info for vertical refresh
[    17.396] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.396] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.396] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.396] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.396] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.396] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.396] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.396] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.396] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.396] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.396] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.088] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[    18.088] (II) RADEON(0): Using hsync ranges from config file
[    18.088] (II) RADEON(0): Using vrefresh ranges from config file
[    18.088] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.088] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.088] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.088] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.088] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.088] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.088] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.088] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.088] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.088] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.088] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.460] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[    18.460] (II) RADEON(0): Using hsync ranges from config file
[    18.460] (II) RADEON(0): Using vrefresh ranges from config file
[    18.460] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.460] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.460] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.460] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.460] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.460] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.460] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.460] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.460] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.460] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.460] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    19.037] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    20.588] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event9)
[    20.588] (II) No input driver specified, ignoring this device.
[    20.588] (II) This device may have been added with another device file.
[    20.591] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event8)
[    20.591] (II) No input driver specified, ignoring this device.
[    20.591] (II) This device may have been added with another device file.
[    20.593] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[    20.593] (II) No input driver specified, ignoring this device.
[    20.593] (II) This device may have been added with another device file.
[    20.594] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[    20.594] (II) No input driver specified, ignoring this device.
[    20.594] (II) This device may have been added with another device file.
[    20.597] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event4)
[    20.597] (II) No input driver specified, ignoring this device.
[    20.597] (II) This device may have been added with another device file.
[    20.597] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event10)
[    20.597] (II) No input driver specified, ignoring this device.
[    20.597] (II) This device may have been added with another device file.
[    20.598] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[    20.598] (II) No input driver specified, ignoring this device.
[    20.598] (II) This device may have been added with another device file.
[    20.611] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[    20.611] (II) No input driver specified, ignoring this device.
[    20.611] (II) This device may have been added with another device file.
[    21.200] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[    21.200] (II) RADEON(0): Using hsync ranges from config file
[    21.200] (II) RADEON(0): Using vrefresh ranges from config file
[    21.200] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.200] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.200] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.200] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.200] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.200] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.200] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    21.200] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.200] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.200] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.200] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    38.016] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[    38.016] (II) RADEON(0): Using hsync ranges from config file
[    38.016] (II) RADEON(0): Using vrefresh ranges from config file
[    38.016] (II) RADEON(0): Printing DDC gathered Modelines:
[    38.016] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    38.016] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    38.016] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    38.016] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    38.016] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    38.016] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    38.016] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    38.016] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    38.016] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    38.016] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   619.388] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[   619.388] (II) RADEON(0): Using hsync ranges from config file
[   619.388] (II) RADEON(0): Using vrefresh ranges from config file
[   619.388] (II) RADEON(0): Printing DDC gathered Modelines:
[   619.388] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   619.388] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   619.388] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   619.388] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   619.388] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   619.388] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   619.388] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   619.388] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   619.388] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   619.388] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2576.556] (II) RADEON(0): EDID vendor "DEL", prod id 40970
[  2576.556] (II) RADEON(0): Using hsync ranges from config file
[  2576.556] (II) RADEON(0): Using vrefresh ranges from config file
[  2576.556] (II) RADEON(0): Printing DDC gathered Modelines:
[  2576.556] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2576.556] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2576.556] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2576.556] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2576.556] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2576.556] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2576.556] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2576.556] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2576.556] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2576.556] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[ 11601.736] (II) evdev: Power Button: Close
[ 11601.736] (II) UnloadModule: "evdev"
[ 11601.736] (II) Unloading evdev
[ 11601.784] (II) evdev: Power Button: Close
[ 11601.784] (II) UnloadModule: "evdev"
[ 11601.784] (II) Unloading evdev
[ 11601.828] (II) evdev: Logitech USB Receiver: Close
[ 11601.828] (II) UnloadModule: "evdev"
[ 11601.828] (II) Unloading evdev
[ 11601.888] (II) evdev: AT Translated Set 2 keyboard: Close
[ 11601.888] (II) UnloadModule: "evdev"
[ 11601.888] (II) Unloading evdev
[ 11601.894]  ddxSigGiveUp: Closing log
[ 11601.894] Server terminated successfully (0). Closing log file.




```[/B]

---

### Post by NikTh on 2012-10-09
Hi , 
OK, I think dmesgs are clear. This is good news. 

I found some similar and multiple WW(warnings)- EE(errors) in Xorg.txt 
> ```
[    16.479] (WW) Warning, couldn't open module fglrx
[    16.481] (WW) Warning, couldn't open module fglrx
[    16.481] (EE) Failed to load module "fglrx" (module does not exist, 0)
```This log is from > ```
[    16.373] Build Date: **29 August 2012  12:10:05AM**
```I don't know if a crash made then , but if you face this situation again take a look at your graphics driver. 
I don't want to say that is for sure , but is possible an error with the driver broke the system. 

Now it seems OK. 

Thanks

---

### Post by vallvi on 2012-10-10
Thanks again!
We'll consider the issue as solve then, for now.

---

### Post by gacb on 2012-10-11
Get rid of all your fglrx and nvidia files except nvidia-common. Worked for me, and they aren't installed at all in 12.10.

---

### Post by vallvi on 2012-10-21
Hi NikTh and everybody,

I got the 'broken pipe' crach again. Here is the dmes log:

[B]```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 (Ubuntu 3.2.0-31.50-generic-pae 3.2.28)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01100 (reserved)
[    0.000000]  BIOS-e820: 00000000fed02000 - 00000000fed14c00 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire X3810/WG43M, BIOS P01-A3 05/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ee000 - 3726f000
[    0.000000] ACPI: RSDP 000fa770 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff90100 0006C (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bff90290 000F4 (v04 052609 FACP2056 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bff905c0 061D5 (v02   P01-   P01-A3 000000A3 INTL 20051117)
[    0.000000] ACPI: FACS bff9e000 00040
[    0.000000] ACPI: APIC bff90390 0006C (v02 052609 APIC2056 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bff90400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: SLIC bff90440 00176 (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bff9e040 00072 (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bff9a5c0 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bff9e0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: AWMI bffa00f0 0004E (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffa0940 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6276MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572638
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f2cee200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331849 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558301
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6179240k/7340032k available (5818k kernel code, 111312k reserved, 2846k data, 740k init, 5377608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.650 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.30 BogoMIPS (lpj=9310600)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004042] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004094] Mount-cache hash table entries: 512
[    0.004217] Initializing cgroup subsys cpuacct
[    0.004223] Initializing cgroup subsys memory
[    0.004230] Initializing cgroup subsys devices
[    0.004232] Initializing cgroup subsys freezer
[    0.004234] Initializing cgroup subsys blkio
[    0.004240] Initializing cgroup subsys perf_event
[    0.004265] CPU: Physical Processor ID: 0
[    0.004266] CPU: Processor Core ID: 0
[    0.004269] mce: CPU supports 6 MCE banks
[    0.004277] CPU0: Thermal monitoring enabled (TM2)
[    0.004280] using mwait in idle threads.
[    0.009714] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 26555 entries in 52 pages
[    0.024042] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024389] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066480] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.068003] APIC calibration not consistent with PM-Timer: 139ms instead of 100ms
[    0.068003] APIC delta adjusted to PM-Timer: 2078348 (2909656)
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156032] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156123] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.156125]  #2
[    0.156127] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248117] CPU 3 irqstacks, hard=f752e000 soft=f7538000
[    0.248119]  #3 Ok.
[    0.248120] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.340037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340060] Brought up 4 CPUs
[    0.340063] Total of 4 processors activated (18662.90 BogoMIPS).
[    0.343004] devtmpfs: initialized
[    0.343004] EVM: security.selinux
[    0.343004] EVM: security.SMACK64
[    0.343004] EVM: security.capability
[    0.343004] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.344576] print_constraints: dummy: 
[    0.344603] RTC time: 18:58:08, date: 10/09/12
[    0.344640] NET: Registered protocol family 16
[    0.344649] Trying to unpack rootfs image as initramfs...
[    0.344771] EISA bus registered
[    0.344798] ACPI: bus type pci registered
[    0.344860] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.344863] PCI: not using MMCONFIG
[    0.344936] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.344996] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.344998] PCI: Using configuration type 1 for base access
[    0.346082] bio: create slab <bio-0> at 0
[    0.346082] ACPI: Added _OSI(Module Device)
[    0.346082] ACPI: Added _OSI(Processor Device)
[    0.346082] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.346082] ACPI: Added _OSI(Processor Aggregator Device)
[    0.346082] ACPI: EC: Look up EC in DSDT
[    0.348956] ACPI: Executed 1 blocks of module-level executable AML code
[    0.351650] ACPI: SSDT bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.351961] ACPI: Dynamic OEM Table Load:
[    0.351964] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.352255] ACPI: SSDT bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352564] ACPI: Dynamic OEM Table Load:
[    0.352567] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.352843] ACPI: SSDT bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353154] ACPI: Dynamic OEM Table Load:
[    0.353157] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.353426] ACPI: SSDT bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353739] ACPI: Dynamic OEM Table Load:
[    0.353742] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.353929] ACPI: Interpreter enabled
[    0.353935] ACPI: (supports S0 S3 S4 S5)
[    0.353954] ACPI: Using IOAPIC for interrupt routing
[    0.353979] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.355173] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.355175] PCI: Using MMCONFIG for extended config space
[    0.360654] ACPI: No dock devices found.
[    0.360658] HEST: Table not found.
[    0.360662] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.360746] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360924] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.360926] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.360929] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.360931] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.360934] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.360936] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.360949] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.360991] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.361030] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.361034] pci 0000:00:01.0: PME# disabled
[    0.361072] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    0.361089] pci 0000:00:19.0: reg 10: [mem 0xfe9e0000-0xfe9fffff]
[    0.361097] pci 0000:00:19.0: reg 14: [mem 0xfe9de000-0xfe9defff]
[    0.361106] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.361165] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.361168] pci 0000:00:19.0: PME# disabled
[    0.361186] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.361226] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.361275] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.361315] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.361363] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.361403] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.361459] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.361479] pci 0000:00:1a.7: reg 10: [mem 0xfe9dc000-0xfe9dc3ff]
[    0.361565] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.361569] pci 0000:00:1a.7: PME# disabled
[    0.361592] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.361606] pci 0000:00:1b.0: reg 10: [mem 0xfe9d8000-0xfe9dbfff 64bit]
[    0.361669] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.361672] pci 0000:00:1b.0: PME# disabled
[    0.361691] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.361756] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.361760] pci 0000:00:1c.0: PME# disabled
[    0.361785] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.361826] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.361876] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.361916] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.361965] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.362004] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.362060] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.362080] pci 0000:00:1d.7: reg 10: [mem 0xfe9d6000-0xfe9d63ff]
[    0.362167] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.362171] pci 0000:00:1d.7: PME# disabled
[    0.362191] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.362249] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.362361] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.362379] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.362386] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.362394] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.362401] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.362409] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb41f]
[    0.362417] pci 0000:00:1f.2: reg 24: [mem 0xfe9d4000-0xfe9d47ff]
[    0.362462] pci 0000:00:1f.2: PME# supported from D3hot
[    0.362465] pci 0000:00:1f.2: PME# disabled
[    0.362481] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.362495] pci 0000:00:1f.3: reg 10: [mem 0xfe9d3c00-0xfe9d3cff 64bit]
[    0.362515] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.362571] pci 0000:01:00.0: [1002:954f] type 0 class 0x000300
[    0.362585] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362595] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.362603] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.362615] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.362646] pci 0000:01:00.0: supports D1 D2
[    0.362665] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.362678] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.362737] pci 0000:01:00.1: supports D1 D2
[    0.362766] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362769] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.362773] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.362777] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.362832] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.362854] pci 0000:02:00.0: reg 10: [mem 0xfebff800-0xfebfffff 64bit]
[    0.362866] pci 0000:02:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.362959] pci 0000:02:00.0: supports D2
[    0.362961] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.362965] pci 0000:02:00.0: PME# disabled
[    0.368041] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.368045] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.368049] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.368113] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.368122] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.368125] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.368127] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.368130] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.368132] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.368135] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.368157] pci_bus 0000:00: on NUMA node 0
[    0.368161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.368376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.368427]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.368431]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.368432] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.377225] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.377274] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.377317] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.377364] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.377410] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.377456] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.377503] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.377549] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.377661] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.377661] vgaarb: loaded
[    0.377661] vgaarb: bridge control possible 0000:01:00.0
[    0.377661] i2c-core: driver [aat2870] using legacy suspend method
[    0.377661] i2c-core: driver [aat2870] using legacy resume method
[    0.377661] SCSI subsystem initialized
[    0.377661] libata version 3.00 loaded.
[    0.377661] usbcore: registered new interface driver usbfs
[    0.377661] usbcore: registered new interface driver hub
[    0.377661] usbcore: registered new device driver usb
[    0.377661] PCI: Using ACPI for IRQ routing
[    0.377661] PCI: pci_cache_line_size set to 64 bytes
[    0.377661] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.377661] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.377661] NetLabel: Initializing
[    0.377661] NetLabel:  domain hash size = 128
[    0.377661] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.377661] NetLabel:  unlabeled traffic allowed by default
[    0.377661] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.377661] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.377661] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.392155] Switching to clocksource hpet
[    0.400285] AppArmor: AppArmor Filesystem Enabled
[    0.400313] pnp: PnP ACPI init
[    0.400331] ACPI: bus type pnp registered
[    0.400447] pnp 00:00: [bus 00-ff]
[    0.400450] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.400453] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.400455] pnp 00:00: [io  0x0d00-0xffff window]
[    0.400457] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.400460] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.400462] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.400464] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.400520] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.400530] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.400532] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.400587] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.400589] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.400593] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.400629] pnp 00:02: [dma 4]
[    0.400631] pnp 00:02: [io  0x0000-0x000f]
[    0.400633] pnp 00:02: [io  0x0081-0x0083]
[    0.400635] pnp 00:02: [io  0x0087]
[    0.400637] pnp 00:02: [io  0x0089-0x008b]
[    0.400639] pnp 00:02: [io  0x008f]
[    0.400641] pnp 00:02: [io  0x00c0-0x00df]
[    0.400668] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.400679] pnp 00:03: [io  0x0070-0x0071]
[    0.400689] pnp 00:03: [irq 8]
[    0.400718] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.400746] pnp 00:04: [io  0x0060]
[    0.400749] pnp 00:04: [io  0x0064]
[    0.400754] pnp 00:04: [irq 1]
[    0.400782] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.400826] pnp 00:05: [irq 12]
[    0.400855] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.400864] pnp 00:06: [io  0x0061]
[    0.400894] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.400903] pnp 00:07: [io  0x00f0-0x00ff]
[    0.400907] pnp 00:07: [irq 13]
[    0.400935] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.401330] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.401333] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.401335] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.401339] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.401341] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.401391] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.401394] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.401396] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.401399] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.401402] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401511] pnp 00:09: [io  0x0010-0x001f]
[    0.401513] pnp 00:09: [io  0x0022-0x003f]
[    0.401515] pnp 00:09: [io  0x0044-0x005f]
[    0.401517] pnp 00:09: [io  0x0062-0x0063]
[    0.401519] pnp 00:09: [io  0x0065-0x006f]
[    0.401521] pnp 00:09: [io  0x0072-0x007f]
[    0.401523] pnp 00:09: [io  0x0080]
[    0.401525] pnp 00:09: [io  0x0084-0x0086]
[    0.401527] pnp 00:09: [io  0x0088]
[    0.401529] pnp 00:09: [io  0x008c-0x008e]
[    0.401531] pnp 00:09: [io  0x0090-0x009f]
[    0.401533] pnp 00:09: [io  0x00a2-0x00bf]
[    0.401535] pnp 00:09: [io  0x00e0-0x00ef]
[    0.401537] pnp 00:09: [io  0x04d0-0x04d1]
[    0.401539] pnp 00:09: [io  0x0800-0x087f]
[    0.401541] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.401543] pnp 00:09: [io  0x0500-0x057f]
[    0.401545] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.401547] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.401549] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.401610] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.401613] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.401615] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.401618] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.401621] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.401624] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.401627] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401681] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.401712] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.401761] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.401763] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.401795] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.401836] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.401885] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.401888] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.401966] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.401968] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.402018] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.402021] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.402024] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402068] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.402116] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.402119] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.402294] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.402296] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.402298] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.402301] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.402303] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.402363] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.402366] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.402368] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.402371] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.402374] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.402377] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.402506] pnp: PnP ACPI: found 16 devices
[    0.402508] ACPI: ACPI bus type pnp unregistered
[    0.402511] PnPBIOS: Disabled by ACPI PNP
[    0.440569] PCI: max bus depth: 1 pci_try_num: 2
[    0.440600] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440604] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.440606] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.440610] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.440613] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440617] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.440620] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.440625] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.440629] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440634] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.440661] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.440664] pci 0000:00:01.0: setting latency timer to 64
[    0.440674] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.440678] pci 0000:00:1c.0: setting latency timer to 64
[    0.440684] pci 0000:00:1e.0: setting latency timer to 64
[    0.440688] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.440690] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.440692] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440695] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440697] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440699] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440702] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.440704] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.440707] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.440709] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.440712] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.440714] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.440717] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.440719] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.440721] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.440723] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.440726] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.440728] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.440769] NET: Registered protocol family 2
[    0.440841] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.441057] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.441384] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.441550] TCP: Hash tables configured (established 131072 bind 65536)
[    0.441552] TCP reno registered
[    0.441555] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.441563] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.441645] NET: Registered protocol family 1
[    0.441674] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.441690] pci 0000:00:1a.0: PCI INT A disabled
[    0.441704] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.441719] pci 0000:00:1a.1: PCI INT B disabled
[    0.441729] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.441744] pci 0000:00:1a.2: PCI INT D disabled
[    0.441755] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441785] pci 0000:00:1a.7: PCI INT C disabled
[    0.441800] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441814] pci 0000:00:1d.0: PCI INT A disabled
[    0.441821] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.441836] pci 0000:00:1d.1: PCI INT B disabled
[    0.441842] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.441857] pci 0000:00:1d.2: PCI INT C disabled
[    0.441865] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441878] pci 0000:00:1d.7: PCI INT A disabled
[    0.441892] pci 0000:01:00.0: Boot video device
[    0.441900] PCI: CLS 32 bytes, default 64
[    0.442390] audit: initializing netlink socket (disabled)
[    0.442399] type=2000 audit(1349809087.436:1): initialized
[    0.463394] highmem bounce pool size: 64 pages
[    0.463400] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.466033] VFS: Disk quotas dquot_6.5.2
[    0.466095] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.466676] fuse init (API version 7.17)
[    0.466792] msgmni has been set to 1565
[    0.467341] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.467386] io scheduler noop registered
[    0.467388] io scheduler deadline registered
[    0.467400] io scheduler cfq registered (default)
[    0.467509] pcieport 0000:00:01.0: setting latency timer to 64
[    0.467540] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.467587] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.467621] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.467700] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.467724] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.467785] intel_idle: MWAIT substates: 0x20
[    0.467787] intel_idle: does not run on family 6 model 23
[    0.467869] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.467874] ACPI: Power Button [PWRB]
[    0.467919] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.467923] ACPI: Power Button [PWRF]
[    0.470589] ERST: Table is not found!
[    0.470591] GHES: HEST is not enabled!
[    0.470689] isapnp: Scanning for PnP cards...
[    0.470693] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.631366] Freeing initrd memory: 13828k freed
[    0.823572] isapnp: No Plug & Play device found
[    0.876587] Linux agpgart interface v0.103
[    0.878701] brd: module loaded
[    0.879728] loop: module loaded
[    0.879866] ahci 0000:00:1f.2: version 3.0
[    0.879877] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.879915] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.879959] ahci: SSS flag set, parallel bus scan disabled
[    0.879990] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.879994] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.879998] ahci 0000:00:1f.2: setting latency timer to 64
[    0.920605] scsi0 : ahci
[    0.920717] scsi1 : ahci
[    0.920813] scsi2 : ahci
[    0.920910] scsi3 : ahci
[    0.921009] scsi4 : ahci
[    0.921111] scsi5 : ahci
[    0.921275] ata1: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4100 irq 42
[    0.921278] ata2: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4180 irq 42
[    0.921280] ata3: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4200 irq 42
[    0.921283] ata4: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4280 irq 42
[    0.921286] ata5: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4300 irq 42
[    0.921288] ata6: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4380 irq 42
[    0.921702] Fixed MDIO Bus: probed
[    0.921722] tun: Universal TUN/TAP device driver, 1.6
[    0.921724] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.921804] PPP generic driver version 2.4.2
[    0.921960] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.921976] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.921989] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.921993] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.922062] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.922084] ehci_hcd 0000:00:1a.7: debug port 1
[    0.925951] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.925966] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9dc000
[    0.940015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.940179] hub 1-0:1.0: USB hub found
[    0.940184] hub 1-0:1.0: 6 ports detected
[    0.940261] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.940271] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.940274] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.940339] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.940360] ehci_hcd 0000:00:1d.7: debug port 1
[    0.944234] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.944248] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9d6000
[    0.960014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.960155] hub 2-0:1.0: USB hub found
[    0.960159] hub 2-0:1.0: 6 ports detected
[    0.960232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.960245] uhci_hcd: USB Universal Host Controller Interface driver
[    0.960260] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.960267] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.960270] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.960332] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.960362] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.960510] hub 3-0:1.0: USB hub found
[    0.960514] hub 3-0:1.0: 2 ports detected
[    0.960577] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.960585] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.960588] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.960662] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.960693] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.960840] hub 4-0:1.0: USB hub found
[    0.960843] hub 4-0:1.0: 2 ports detected
[    0.960912] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.960918] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.960921] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.960987] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.961017] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.961163] hub 5-0:1.0: USB hub found
[    0.961166] hub 5-0:1.0: 2 ports detected
[    0.961226] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.961232] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.961235] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.961302] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.961322] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.961468] hub 6-0:1.0: USB hub found
[    0.961472] hub 6-0:1.0: 2 ports detected
[    0.961538] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.961545] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.961547] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.961614] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.961635] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.961780] hub 7-0:1.0: USB hub found
[    0.961784] hub 7-0:1.0: 2 ports detected
[    0.961848] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.961855] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.961858] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.961923] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.961944] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.962096] hub 8-0:1.0: USB hub found
[    0.962100] hub 8-0:1.0: 2 ports detected
[    0.962214] usbcore: registered new interface driver libusual
[    0.962273] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.962634] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.962641] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.962799] mousedev: PS/2 mouse device common for all mice
[    0.963014] rtc_cmos 00:03: RTC can wake from S4
[    0.963137] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.963159] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.963218] device-mapper: uevent: version 1.0.3
[    0.963315] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.963347] EISA: Probing bus 0 at eisa.0
[    0.963349] EISA: Cannot allocate resource for mainboard
[    0.963351] Cannot allocate resource for EISA slot 1
[    0.963353] Cannot allocate resource for EISA slot 2
[    0.963354] Cannot allocate resource for EISA slot 3
[    0.963356] Cannot allocate resource for EISA slot 4
[    0.963358] Cannot allocate resource for EISA slot 5
[    0.963359] Cannot allocate resource for EISA slot 6
[    0.963361] Cannot allocate resource for EISA slot 7
[    0.963363] Cannot allocate resource for EISA slot 8
[    0.963364] EISA: Detected 0 cards.
[    0.963373] cpufreq-nforce2: No nForce2 chipset.
[    0.963375] cpuidle: using governor ladder
[    0.963377] cpuidle: using governor menu
[    0.963379] EFI Variables Facility v0.08 2004-May-17
[    0.963643] TCP cubic registered
[    0.963770] NET: Registered protocol family 10
[    0.964343] NET: Registered protocol family 17
[    0.964347] Registering the dns_resolver key type
[    0.964371] Using IPI No-Shortcut mode
[    0.964533] PM: Hibernation image not present or could not be loaded.
[    0.964544] registered taskstats version 1
[    0.971419]   Magic number: 0:54:999
[    0.971460] system 00:01: hash matches
[    0.971462]  pnp0: hash matches
[    0.971523] rtc_cmos 00:03: setting system clock to 2012-10-09 18:58:09 UTC (1349809089)
[    0.972586] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.972588] EDD information not available.
[    0.979396] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.240021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.243031] ata1.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.246909] ata1.00: configured for UDMA/100
[    1.252016] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.257625] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.266069] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.266072] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.266219] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.266302] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.440015] Refined TSC clocksource calibration: 2327.754 MHz.
[    1.440020] Switching to clocksource tsc
[    1.568012] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.584015] ata2: SATA link down (SStatus 0 SControl 300)
[    1.704392] Initializing USB Mass Storage driver...
[    1.704558] scsi6 : usb-storage 2-3:1.0
[    1.704636] usbcore: registered new interface driver usb-storage
[    1.704638] USB Mass Storage support registered.
[    1.904014] ata3: SATA link down (SStatus 0 SControl 300)
[    1.940013] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    2.224015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.242239] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.242243] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.243260] ata4.00: configured for UDMA/133
[    2.243381] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.243495] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.243541] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.243562] sd 3:0:0:0: [sda] Write Protect is off
[    2.243565] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.243589] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.286130]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.286610] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.560014] ata5: SATA link down (SStatus 0 SControl 300)
[    2.704832] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.705454] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.706262] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.706462] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.709933] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.710555] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.880021] ata6: SATA link down (SStatus 0 SControl 300)
[    2.880115] Freeing unused kernel memory: 740k freed
[    2.880383] Write protecting the kernel text: 5820k
[    2.880412] Write protecting the kernel read-only data: 2376k
[    2.880414] NX-protecting the kernel data: 4420k
[    2.897294] udevd[113]: starting version 175
[    2.929202] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.929205] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.929243] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.929252] e1000e 0000:00:19.0: setting latency timer to 64
[    2.929356] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.931976] generic-usb 0003:058F:6363.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.934159] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.934168] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.947556] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.947688] generic-usb 0003:046D:C51B.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    2.961151] generic-usb 0003:046D:C51B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    2.961171] usbcore: registered new interface driver usbhid
[    2.961173] usbhid: USB HID core driver
[    2.996049] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.120316] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:f4:ca:94
[    3.120320] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.120343] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    3.496105] firewire_core: created device fw0: GUID 001d72ffae924fff, S400
[    3.628091] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.558354] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.574468] udevd[345]: starting version 175
[   13.612205] lp: driver loaded but no devices found
[   13.613255] [drm] Initialized drm 1.1.0 20060810
[   13.627489] Adding 9068540k swap on /dev/sda5.  Priority:-1 extents:1 across:9068540k 
[   13.645401] wmi: Mapper loaded
[   13.647362] [drm] radeon defaulting to kernel modesetting.
[   13.647365] [drm] radeon kernel modesetting enabled.
[   13.648293] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.648299] radeon 0000:01:00.0: setting latency timer to 64
[   13.666981] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x174B:0xE990).
[   13.667009] [drm] register mmio base: 0xFEAF0000
[   13.667011] [drm] register mmio size: 65536
[   13.667131] ATOM BIOS: 11X
[   13.667162] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   13.667165] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   13.669611] [drm] Detected VRAM RAM=512M, BAR=256M
[   13.669614] [drm] RAM width 64bits DDR
[   13.670153] [TTM] Zone  kernel: Available graphics memory: 408100 kiB.
[   13.670156] [TTM] Zone highmem: Available graphics memory: 3096904 kiB.
[   13.670157] [TTM] Initializing pool allocator.
[   13.670180] [drm] radeon: 512M of VRAM memory ready
[   13.670182] [drm] radeon: 512M of GTT memory ready.
[   13.670197] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.670199] [drm] Driver supports precise vblank timestamp query.
[   13.670261] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   13.670267] radeon 0000:01:00.0: radeon: using MSI.
[   13.670299] [drm] radeon: irq initialized.
[   13.670303] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.671330] [drm] Loading RV710 Microcode
[   13.671791] type=1400 audit(1349801902.193:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=497 comm="apparmor_parser"
[   13.672385] type=1400 audit(1349801902.197:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   13.672625] type=1400 audit(1349801902.197:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   13.697069] cfg80211: Calling CRDA to update world regulatory domain
[   13.720298] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.720347] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.720372] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   13.823592] cfg80211: World regulatory domain updated:
[   13.823595] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.823598] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.823601] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.823603] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.823605] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.823608] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.824118] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
[   13.856981] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   13.857032] radeon 0000:01:00.0: WB enabled
[   13.903019] [drm] ring test succeeded in 1 usecs
[   13.903179] [drm] radeon: ib pool ready.
[   13.903252] [drm] ib test succeeded in 0 usecs
[   13.903551] [drm] Radeon Display Connectors
[   13.903553] [drm] Connector 0:
[   13.903554] [drm]   VGA
[   13.903556] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   13.903558] [drm]   Encoders:
[   13.903559] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   13.903561] [drm] Connector 1:
[   13.903562] [drm]   HDMI-A
[   13.903563] [drm]   HPD1
[   13.903565] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   13.903567] [drm]   Encoders:
[   13.903568] [drm]     DFP1: INTERNAL_UNIPHY
[   13.903570] [drm] Connector 2:
[   13.903571] [drm]   DVI-I
[   13.903572] [drm]   HPD4
[   13.903574] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   13.903576] [drm]   Encoders:
[   13.903577] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.903579] [drm]     DFP2: INTERNAL_UNIPHY2
[   13.903596] [drm] Internal thermal controller with fan control
[   13.903639] [drm] radeon: power management initialized
[   13.977654] [drm] fb mappable at 0xD0142000
[   13.977657] [drm] vram apper at 0xD0000000
[   13.977658] [drm] size 5242880
[   13.977660] [drm] fb depth is 24
[   13.977661] [drm]    pitch is 5120
[   13.977744] fbcon: radeondrmfb (fb0) is primary device
[   13.977857] Console: switching to colour frame buffer device 160x64
[   13.977888] fb0: radeondrmfb frame buffer device
[   13.977890] drm: registered panic notifier
[   13.977896] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   13.995600] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.995604] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995606] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.995609] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995611] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.995614] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995616] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.995618] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995620] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.995623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995625] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.995628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995630] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.995632] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995634] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.995637] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995639] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.995642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995644] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.995647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995649] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.995651] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.995654] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.995656] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.995658] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.995661] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.995663] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.995665] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.997016] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   13.998735] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.999370] Registered led device: rt2800usb-phy0::radio
[   13.999406] Registered led device: rt2800usb-phy0::assoc
[   13.999434] Registered led device: rt2800usb-phy0::quality
[   13.999480] usbcore: registered new interface driver rt2800usb
[   14.345257] init: failsafe main process (782) killed by TERM signal
[   14.381923] Bluetooth: Core ver 2.16
[   14.381948] NET: Registered protocol family 31
[   14.381949] Bluetooth: HCI device and connection manager initialized
[   14.381952] Bluetooth: HCI socket layer initialized
[   14.381954] Bluetooth: L2CAP socket layer initialized
[   14.381960] Bluetooth: SCO socket layer initialized
[   14.383907] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.383910] Bluetooth: BNEP filters: protocol multicast
[   14.389033] Bluetooth: RFCOMM TTY layer initialized
[   14.389039] Bluetooth: RFCOMM socket layer initialized
[   14.389041] Bluetooth: RFCOMM ver 1.11
[   14.405181] ppdev: user-space parallel port driver
[   14.417647] type=1400 audit(1349801902.941:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=854 comm="apparmor_parser"
[   14.418166] type=1400 audit(1349801902.941:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=854 comm="apparmor_parser"
[   14.556943] type=1400 audit(1349801903.081:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=890 comm="apparmor_parser"
[   14.557297] type=1400 audit(1349801903.081:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=891 comm="apparmor_parser"
[   14.557754] type=1400 audit(1349801903.081:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=891 comm="apparmor_parser"
[   14.558000] type=1400 audit(1349801903.081:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=891 comm="apparmor_parser"
[   14.559005] type=1400 audit(1349801903.081:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=894 comm="apparmor_parser"
[   14.624209] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.647625] init: alsa-restore main process (933) terminated with status 19
[   14.680114] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.680352] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.680699] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.896351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.896833] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.772015] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   17.780029] hda-intel: No response from codec, disabling MSI: last cmd=0x300f0000
[   18.176283] wlan0: authenticate with 00:1a:2b:13:ba:89 (try 1)
[   18.177794] wlan0: authenticated
[   18.232283] wlan0: associate with 00:1a:2b:13:ba:89 (try 1)
[   18.234046] wlan0: RX AssocResp from 00:1a:2b:13:ba:89 (capab=0x411 status=0 aid=1)
[   18.234050] wlan0: associated
[   18.243835] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.784013] hda-intel: Codec #3 probe error; disabling it...
[   18.827233] hda_codec: ALC888: BIOS auto-probing.
[   18.835472] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   18.835634] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   18.835708] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.835779] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.835849] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.835918] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.835989] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.836380] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.836448] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   18.836472] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   18.854374] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   18.854514] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   18.984643] init: plymouth-stop pre-start process (1556) terminated with status 1
[   29.008005] wlan0: no IPv6 routers present
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-32-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 (Ubuntu 3.2.0-32.51-generic-pae 3.2.30)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01100 (reserved)
[    0.000000]  BIOS-e820: 00000000fed02000 - 00000000fed14c00 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire X3810/WG43M, BIOS P01-A3 05/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ec000 - 3726e000
[    0.000000] ACPI: RSDP 000fa770 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff90100 0006C (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bff90290 000F4 (v04 052609 FACP2056 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bff905c0 061D5 (v02   P01-   P01-A3 000000A3 INTL 20051117)
[    0.000000] ACPI: FACS bff9e000 00040
[    0.000000] ACPI: APIC bff90390 0006C (v02 052609 APIC2056 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bff90400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: SLIC bff90440 00176 (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bff9e040 00072 (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bff9a5c0 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bff9e0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: AWMI bffa00f0 0004E (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffa0940 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6276MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572638
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f2cec200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331849 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558301
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6179236k/7340032k available (5820k kernel code, 111316k reserved, 2844k data, 740k init, 5377608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15af13c - 0xc1876280   (2844 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15af13c   (5820 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.825 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.65 BogoMIPS (lpj=9311300)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004094] Mount-cache hash table entries: 512
[    0.004218] Initializing cgroup subsys cpuacct
[    0.004224] Initializing cgroup subsys memory
[    0.004232] Initializing cgroup subsys devices
[    0.004234] Initializing cgroup subsys freezer
[    0.004236] Initializing cgroup subsys blkio
[    0.004241] Initializing cgroup subsys perf_event
[    0.004266] CPU: Physical Processor ID: 0
[    0.004268] CPU: Processor Core ID: 0
[    0.004271] mce: CPU supports 6 MCE banks
[    0.004279] CPU0: Thermal monitoring enabled (TM2)
[    0.004282] using mwait in idle threads.
[    0.009934] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 26564 entries in 52 pages
[    0.020043] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062722] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156032] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156125] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.156127]  #2
[    0.156128] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248117] CPU 3 irqstacks, hard=f752e000 soft=f7538000
[    0.248119]  #3 Ok.
[    0.248120] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.344037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.344060] Brought up 4 CPUs
[    0.344063] Total of 4 processors activated (18622.14 BogoMIPS).
[    0.347008] devtmpfs: initialized
[    0.347008] EVM: security.selinux
[    0.347008] EVM: security.SMACK64
[    0.347008] EVM: security.capability
[    0.347008] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.348572] print_constraints: dummy: 
[    0.348599] RTC time:  8:07:11, date: 10/21/12
[    0.348636] NET: Registered protocol family 16
[    0.348645] Trying to unpack rootfs image as initramfs...
[    0.348764] EISA bus registered
[    0.348792] ACPI: bus type pci registered
[    0.348854] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.348857] PCI: not using MMCONFIG
[    0.348933] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.348993] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.348994] PCI: Using configuration type 1 for base access
[    0.350091] bio: create slab <bio-0> at 0
[    0.350091] ACPI: Added _OSI(Module Device)
[    0.350091] ACPI: Added _OSI(Processor Device)
[    0.350091] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.350091] ACPI: Added _OSI(Processor Aggregator Device)
[    0.350091] ACPI: EC: Look up EC in DSDT
[    0.352970] ACPI: Executed 1 blocks of module-level executable AML code
[    0.355656] ACPI: SSDT bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.355965] ACPI: Dynamic OEM Table Load:
[    0.355968] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.356258] ACPI: SSDT bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.356568] ACPI: Dynamic OEM Table Load:
[    0.356571] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.356847] ACPI: SSDT bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.357158] ACPI: Dynamic OEM Table Load:
[    0.357161] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.357430] ACPI: SSDT bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.357742] ACPI: Dynamic OEM Table Load:
[    0.357745] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.357932] ACPI: Interpreter enabled
[    0.357938] ACPI: (supports S0 S3 S4 S5)
[    0.357958] ACPI: Using IOAPIC for interrupt routing
[    0.357983] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.359172] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.359174] PCI: Using MMCONFIG for extended config space
[    0.364655] ACPI: No dock devices found.
[    0.364659] HEST: Table not found.
[    0.364663] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.364749] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.364926] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.364929] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.364931] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.364934] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.364936] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.364939] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.364953] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.364994] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.365032] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.365035] pci 0000:00:01.0: PME# disabled
[    0.365074] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    0.365091] pci 0000:00:19.0: reg 10: [mem 0xfe9e0000-0xfe9fffff]
[    0.365100] pci 0000:00:19.0: reg 14: [mem 0xfe9de000-0xfe9defff]
[    0.365108] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.365166] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.365170] pci 0000:00:19.0: PME# disabled
[    0.365188] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.365229] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.365277] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.365316] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.365364] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.365403] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.365461] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.365481] pci 0000:00:1a.7: reg 10: [mem 0xfe9dc000-0xfe9dc3ff]
[    0.365565] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.365570] pci 0000:00:1a.7: PME# disabled
[    0.365592] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.365606] pci 0000:00:1b.0: reg 10: [mem 0xfe9d8000-0xfe9dbfff 64bit]
[    0.365669] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.365673] pci 0000:00:1b.0: PME# disabled
[    0.365691] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.365760] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.365764] pci 0000:00:1c.0: PME# disabled
[    0.365789] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.365829] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.365876] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.365917] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.365965] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.366004] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.366063] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.366083] pci 0000:00:1d.7: reg 10: [mem 0xfe9d6000-0xfe9d63ff]
[    0.366167] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.366172] pci 0000:00:1d.7: PME# disabled
[    0.366191] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.366250] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.366363] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.366380] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.366388] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.366395] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.366403] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.366411] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb41f]
[    0.366418] pci 0000:00:1f.2: reg 24: [mem 0xfe9d4000-0xfe9d47ff]
[    0.366461] pci 0000:00:1f.2: PME# supported from D3hot
[    0.366465] pci 0000:00:1f.2: PME# disabled
[    0.366480] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.366494] pci 0000:00:1f.3: reg 10: [mem 0xfe9d3c00-0xfe9d3cff 64bit]
[    0.366514] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.366570] pci 0000:01:00.0: [1002:954f] type 0 class 0x000300
[    0.366584] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.366595] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.366602] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.366617] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.366647] pci 0000:01:00.0: supports D1 D2
[    0.366666] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.366680] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.366736] pci 0000:01:00.1: supports D1 D2
[    0.366765] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.366768] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.366772] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.366776] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.366831] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.366853] pci 0000:02:00.0: reg 10: [mem 0xfebff800-0xfebfffff 64bit]
[    0.366866] pci 0000:02:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.366959] pci 0000:02:00.0: supports D2
[    0.366961] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.366966] pci 0000:02:00.0: PME# disabled
[    0.372042] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.372046] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.372050] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.372123] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.372137] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.372143] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.372145] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.372148] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.372150] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.372153] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.372166] pci_bus 0000:00: on NUMA node 0
[    0.372170] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.372376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.372427]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.372430]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.372432] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.381191] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.381240] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.381283] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.381329] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.381376] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.381422] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.381469] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.381515] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.381626] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.381626] vgaarb: loaded
[    0.381626] vgaarb: bridge control possible 0000:01:00.0
[    0.381626] i2c-core: driver [aat2870] using legacy suspend method
[    0.381626] i2c-core: driver [aat2870] using legacy resume method
[    0.381626] SCSI subsystem initialized
[    0.381626] libata version 3.00 loaded.
[    0.381626] usbcore: registered new interface driver usbfs
[    0.381626] usbcore: registered new interface driver hub
[    0.381626] usbcore: registered new device driver usb
[    0.381626] PCI: Using ACPI for IRQ routing
[    0.381626] PCI: pci_cache_line_size set to 64 bytes
[    0.381626] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.381626] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.381626] NetLabel: Initializing
[    0.381626] NetLabel:  domain hash size = 128
[    0.381626] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.381626] NetLabel:  unlabeled traffic allowed by default
[    0.381626] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.381626] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.381626] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.396145] Switching to clocksource hpet
[    0.404296] AppArmor: AppArmor Filesystem Enabled
[    0.404325] pnp: PnP ACPI init
[    0.404342] ACPI: bus type pnp registered
[    0.404459] pnp 00:00: [bus 00-ff]
[    0.404461] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.404464] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.404466] pnp 00:00: [io  0x0d00-0xffff window]
[    0.404469] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.404471] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.404474] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.404476] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.404533] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.404543] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.404545] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.404600] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.404603] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.404607] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.404641] pnp 00:02: [dma 4]
[    0.404644] pnp 00:02: [io  0x0000-0x000f]
[    0.404646] pnp 00:02: [io  0x0081-0x0083]
[    0.404648] pnp 00:02: [io  0x0087]
[    0.404650] pnp 00:02: [io  0x0089-0x008b]
[    0.404652] pnp 00:02: [io  0x008f]
[    0.404653] pnp 00:02: [io  0x00c0-0x00df]
[    0.404680] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.404691] pnp 00:03: [io  0x0070-0x0071]
[    0.404702] pnp 00:03: [irq 8]
[    0.404731] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.404759] pnp 00:04: [io  0x0060]
[    0.404762] pnp 00:04: [io  0x0064]
[    0.404767] pnp 00:04: [irq 1]
[    0.404795] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.404839] pnp 00:05: [irq 12]
[    0.404867] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.404877] pnp 00:06: [io  0x0061]
[    0.404906] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.404915] pnp 00:07: [io  0x00f0-0x00ff]
[    0.404920] pnp 00:07: [irq 13]
[    0.404948] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.405339] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.405342] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.405344] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.405348] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.405350] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.405401] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.405404] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.405407] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.405409] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.405413] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.405521] pnp 00:09: [io  0x0010-0x001f]
[    0.405524] pnp 00:09: [io  0x0022-0x003f]
[    0.405526] pnp 00:09: [io  0x0044-0x005f]
[    0.405528] pnp 00:09: [io  0x0062-0x0063]
[    0.405530] pnp 00:09: [io  0x0065-0x006f]
[    0.405532] pnp 00:09: [io  0x0072-0x007f]
[    0.405534] pnp 00:09: [io  0x0080]
[    0.405536] pnp 00:09: [io  0x0084-0x0086]
[    0.405538] pnp 00:09: [io  0x0088]
[    0.405540] pnp 00:09: [io  0x008c-0x008e]
[    0.405542] pnp 00:09: [io  0x0090-0x009f]
[    0.405544] pnp 00:09: [io  0x00a2-0x00bf]
[    0.405546] pnp 00:09: [io  0x00e0-0x00ef]
[    0.405548] pnp 00:09: [io  0x04d0-0x04d1]
[    0.405550] pnp 00:09: [io  0x0800-0x087f]
[    0.405552] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.405554] pnp 00:09: [io  0x0500-0x057f]
[    0.405556] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.405559] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.405561] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.405621] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.405623] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.405626] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.405629] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.405632] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.405635] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.405638] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.405692] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.405723] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.405771] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.405774] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.405808] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.405847] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.405896] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.405899] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.405977] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.405979] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.406030] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.406033] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.406036] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.406080] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.406127] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.406131] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.406305] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.406308] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.406310] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.406313] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.406315] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.406374] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.406377] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.406380] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.406382] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.406385] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.406388] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.406517] pnp: PnP ACPI: found 16 devices
[    0.406518] ACPI: ACPI bus type pnp unregistered
[    0.406522] PnPBIOS: Disabled by ACPI PNP
[    0.444593] PCI: max bus depth: 1 pci_try_num: 2
[    0.444624] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.444628] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.444631] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.444635] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.444638] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.444642] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.444645] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.444650] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.444654] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.444659] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.444686] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.444691] pci 0000:00:01.0: setting latency timer to 64
[    0.444701] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.444705] pci 0000:00:1c.0: setting latency timer to 64
[    0.444712] pci 0000:00:1e.0: setting latency timer to 64
[    0.444715] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.444718] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.444720] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.444723] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.444725] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.444727] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.444730] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.444732] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.444735] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.444737] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.444740] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.444742] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.444745] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.444747] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.444750] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.444752] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.444755] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.444757] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.444797] NET: Registered protocol family 2
[    0.444867] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.445082] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.445418] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.445585] TCP: Hash tables configured (established 131072 bind 65536)
[    0.445588] TCP reno registered
[    0.445591] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.445599] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.445685] NET: Registered protocol family 1
[    0.445714] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.445731] pci 0000:00:1a.0: PCI INT A disabled
[    0.445746] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.445761] pci 0000:00:1a.1: PCI INT B disabled
[    0.445771] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.445785] pci 0000:00:1a.2: PCI INT D disabled
[    0.445796] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.445826] pci 0000:00:1a.7: PCI INT C disabled
[    0.445840] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.445855] pci 0000:00:1d.0: PCI INT A disabled
[    0.445862] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.445877] pci 0000:00:1d.1: PCI INT B disabled
[    0.445884] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.445899] pci 0000:00:1d.2: PCI INT C disabled
[    0.445907] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.445920] pci 0000:00:1d.7: PCI INT A disabled
[    0.445933] pci 0000:01:00.0: Boot video device
[    0.445941] PCI: CLS 32 bytes, default 64
[    0.446427] audit: initializing netlink socket (disabled)
[    0.446435] type=2000 audit(1350806831.440:1): initialized
[    0.467415] highmem bounce pool size: 64 pages
[    0.467420] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.470050] VFS: Disk quotas dquot_6.5.2
[    0.470112] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.470699] fuse init (API version 7.17)
[    0.470809] msgmni has been set to 1565
[    0.471357] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.471392] io scheduler noop registered
[    0.471399] io scheduler deadline registered
[    0.471411] io scheduler cfq registered (default)
[    0.471520] pcieport 0000:00:01.0: setting latency timer to 64
[    0.471550] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.471598] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.471632] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.471710] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.471735] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.471797] intel_idle: MWAIT substates: 0x20
[    0.471798] intel_idle: does not run on family 6 model 23
[    0.471882] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.471887] ACPI: Power Button [PWRB]
[    0.471933] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.471936] ACPI: Power Button [PWRF]
[    0.474594] ERST: Table is not found!
[    0.474596] GHES: HEST is not enabled!
[    0.474696] isapnp: Scanning for PnP cards...
[    0.474727] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.633794] Freeing initrd memory: 13832k freed
[    0.827591] isapnp: No Plug & Play device found
[    0.880586] Linux agpgart interface v0.103
[    0.882714] brd: module loaded
[    0.883740] loop: module loaded
[    0.883878] ahci 0000:00:1f.2: version 3.0
[    0.883891] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.883929] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.883974] ahci: SSS flag set, parallel bus scan disabled
[    0.884015] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.884019] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.884023] ahci 0000:00:1f.2: setting latency timer to 64
[    0.924625] scsi0 : ahci
[    0.924743] scsi1 : ahci
[    0.924848] scsi2 : ahci
[    0.924939] scsi3 : ahci
[    0.925055] scsi4 : ahci
[    0.925162] scsi5 : ahci
[    0.925333] ata1: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4100 irq 42
[    0.925336] ata2: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4180 irq 42
[    0.925339] ata3: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4200 irq 42
[    0.925341] ata4: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4280 irq 42
[    0.925344] ata5: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4300 irq 42
[    0.925347] ata6: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4380 irq 42
[    0.925778] Fixed MDIO Bus: probed
[    0.925799] tun: Universal TUN/TAP device driver, 1.6
[    0.925801] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.925878] PPP generic driver version 2.4.2
[    0.926037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.926054] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.926067] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.926070] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.926139] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.926161] ehci_hcd 0000:00:1a.7: debug port 1
[    0.930031] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.930046] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9dc000
[    0.944015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.944178] hub 1-0:1.0: USB hub found
[    0.944182] hub 1-0:1.0: 6 ports detected
[    0.944258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.944268] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.944271] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.944336] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.944358] ehci_hcd 0000:00:1d.7: debug port 1
[    0.948254] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.948267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9d6000
[    0.964014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.964155] hub 2-0:1.0: USB hub found
[    0.964159] hub 2-0:1.0: 6 ports detected
[    0.964232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.964245] uhci_hcd: USB Universal Host Controller Interface driver
[    0.964261] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.964268] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.964271] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.964337] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.964366] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.964513] hub 3-0:1.0: USB hub found
[    0.964517] hub 3-0:1.0: 2 ports detected
[    0.964579] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.964587] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.964590] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.964657] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.964688] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.964836] hub 4-0:1.0: USB hub found
[    0.964840] hub 4-0:1.0: 2 ports detected
[    0.964908] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.964914] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.964917] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.964983] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.965012] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.965158] hub 5-0:1.0: USB hub found
[    0.965161] hub 5-0:1.0: 2 ports detected
[    0.965221] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.965227] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.965230] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.965297] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.965318] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.965466] hub 6-0:1.0: USB hub found
[    0.965469] hub 6-0:1.0: 2 ports detected
[    0.965531] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.965538] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.965541] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.965607] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.965628] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.965774] hub 7-0:1.0: USB hub found
[    0.965778] hub 7-0:1.0: 2 ports detected
[    0.965841] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.965848] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.965851] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.965919] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.965939] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.966085] hub 8-0:1.0: USB hub found
[    0.966089] hub 8-0:1.0: 2 ports detected
[    0.966203] usbcore: registered new interface driver libusual
[    0.966261] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.966621] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.966628] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.966789] mousedev: PS/2 mouse device common for all mice
[    0.967002] rtc_cmos 00:03: RTC can wake from S4
[    0.967124] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.967146] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.967204] device-mapper: uevent: version 1.0.3
[    0.967302] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.967333] EISA: Probing bus 0 at eisa.0
[    0.967335] EISA: Cannot allocate resource for mainboard
[    0.967338] Cannot allocate resource for EISA slot 1
[    0.967339] Cannot allocate resource for EISA slot 2
[    0.967341] Cannot allocate resource for EISA slot 3
[    0.967343] Cannot allocate resource for EISA slot 4
[    0.967345] Cannot allocate resource for EISA slot 5
[    0.967346] Cannot allocate resource for EISA slot 6
[    0.967348] Cannot allocate resource for EISA slot 7
[    0.967350] Cannot allocate resource for EISA slot 8
[    0.967352] EISA: Detected 0 cards.
[    0.967360] cpufreq-nforce2: No nForce2 chipset.
[    0.967363] cpuidle: using governor ladder
[    0.967365] cpuidle: using governor menu
[    0.967366] EFI Variables Facility v0.08 2004-May-17
[    0.967627] TCP cubic registered
[    0.967754] NET: Registered protocol family 10
[    0.968322] NET: Registered protocol family 17
[    0.968327] Registering the dns_resolver key type
[    0.968346] Using IPI No-Shortcut mode
[    0.968506] PM: Hibernation image not present or could not be loaded.
[    0.968518] registered taskstats version 1
[    0.975453]   Magic number: 0:514:119
[    0.975552] rtc_cmos 00:03: setting system clock to 2012-10-21 08:07:12 UTC (1350806832)
[    0.976603] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.976605] EDD information not available.
[    0.982903] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.244020] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.247035] ata1.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.250909] ata1.00: configured for UDMA/100
[    1.256016] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.258547] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.267019] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.267023] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.267162] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.267239] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.444015] Refined TSC clocksource calibration: 2327.754 MHz.
[    1.444020] Switching to clocksource tsc
[    1.572012] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.584017] ata2: SATA link down (SStatus 0 SControl 300)
[    1.708224] Initializing USB Mass Storage driver...
[    1.708385] scsi6 : usb-storage 2-3:1.0
[    1.708467] usbcore: registered new interface driver usb-storage
[    1.708469] USB Mass Storage support registered.
[    1.904014] ata3: SATA link down (SStatus 0 SControl 300)
[    1.944012] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    2.224015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.237691] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.237695] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.238712] ata4.00: configured for UDMA/133
[    2.238837] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.238983] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.238999] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.239054] sd 3:0:0:0: [sda] Write Protect is off
[    2.239057] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.239088] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.281580]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.281984] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.556014] ata5: SATA link down (SStatus 0 SControl 300)
[    2.708731] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.709346] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.710137] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.710284] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.713828] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.714579] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.876014] ata6: SATA link down (SStatus 0 SControl 300)
[    2.876104] Freeing unused kernel memory: 740k freed
[    2.876361] Write protecting the kernel text: 5824k
[    2.876390] Write protecting the kernel read-only data: 2376k
[    2.876392] NX-protecting the kernel data: 4416k
[    2.893320] udevd[113]: starting version 175
[    2.923318] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.923321] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.923364] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.923374] e1000e 0000:00:19.0: setting latency timer to 64
[    2.923473] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.924649] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.924657] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.931691] generic-usb 0003:058F:6363.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.946556] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.946749] generic-usb 0003:046D:C51B.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    2.960142] generic-usb 0003:046D:C51B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    2.960167] usbcore: registered new interface driver usbhid
[    2.960169] usbhid: USB HID core driver
[    2.988049] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.110403] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:f4:ca:94
[    3.110407] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.110429] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    3.345506] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.345509] EXT4-fs (sda6): write access will be enabled during recovery
[    3.488107] firewire_core: created device fw0: GUID 001d72ffae924fff, S400
[    4.982885] EXT4-fs (sda6): recovery complete
[    4.983211] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.153896] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.186353] udevd[358]: starting version 175
[   16.239207] Adding 9068540k swap on /dev/sda5.  Priority:-1 extents:1 across:9068540k 
[   16.239586] lp: driver loaded but no devices found
[   16.240442] [drm] Initialized drm 1.1.0 20060810
[   16.259772] cfg80211: Calling CRDA to update world regulatory domain
[   16.259868] type=1400 audit(1350799647.777:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=461 comm="apparmor_parser"
[   16.260328] type=1400 audit(1350799647.781:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=461 comm="apparmor_parser"
[   16.260573] type=1400 audit(1350799647.781:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=461 comm="apparmor_parser"
[   16.266680] [drm] radeon defaulting to kernel modesetting.
[   16.266684] [drm] radeon kernel modesetting enabled.
[   16.266747] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.266753] radeon 0000:01:00.0: setting latency timer to 64
[   16.279922] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x174B:0xE990).
[   16.279953] [drm] register mmio base: 0xFEAF0000
[   16.279955] [drm] register mmio size: 65536
[   16.280111] ATOM BIOS: 11X
[   16.280142] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   16.280145] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   16.282200] [drm] Detected VRAM RAM=512M, BAR=256M
[   16.282205] [drm] RAM width 64bits DDR
[   16.284844] [TTM] Zone  kernel: Available graphics memory: 408100 kiB.
[   16.284847] [TTM] Zone highmem: Available graphics memory: 3096904 kiB.
[   16.284849] [TTM] Initializing pool allocator.
[   16.284870] [drm] radeon: 512M of VRAM memory ready
[   16.284872] [drm] radeon: 512M of GTT memory ready.
[   16.284891] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.284893] [drm] Driver supports precise vblank timestamp query.
[   16.284935] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   16.284940] radeon 0000:01:00.0: radeon: using MSI.
[   16.284970] [drm] radeon: irq initialized.
[   16.284974] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   16.285836] [drm] Loading RV710 Microcode
[   16.311054] wmi: Mapper loaded
[   16.334828] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.334876] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.334899] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.413246] cfg80211: World regulatory domain updated:
[   16.413249] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.413252] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.413255] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.413258] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.413260] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.413263] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.420031] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
[   16.435711] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   16.435761] radeon 0000:01:00.0: WB enabled
[   16.481706] [drm] ring test succeeded in 1 usecs
[   16.481848] [drm] radeon: ib pool ready.
[   16.481921] [drm] ib test succeeded in 0 usecs
[   16.482279] [drm] Radeon Display Connectors
[   16.482281] [drm] Connector 0:
[   16.482283] [drm]   VGA
[   16.482285] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   16.482287] [drm]   Encoders:
[   16.482288] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   16.482290] [drm] Connector 1:
[   16.482291] [drm]   HDMI-A
[   16.482293] [drm]   HPD1
[   16.482295] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   16.482296] [drm]   Encoders:
[   16.482298] [drm]     DFP1: INTERNAL_UNIPHY
[   16.482299] [drm] Connector 2:
[   16.482301] [drm]   DVI-I
[   16.482302] [drm]   HPD4
[   16.482304] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   16.482306] [drm]   Encoders:
[   16.482307] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   16.482309] [drm]     DFP2: INTERNAL_UNIPHY2
[   16.482327] [drm] Internal thermal controller with fan control
[   16.482368] [drm] radeon: power management initialized
[   16.556826] [drm] fb mappable at 0xD0142000
[   16.556828] [drm] vram apper at 0xD0000000
[   16.556829] [drm] size 5242880
[   16.556831] [drm] fb depth is 24
[   16.556832] [drm]    pitch is 5120
[   16.556932] fbcon: radeondrmfb (fb0) is primary device
[   16.557017] Console: switching to colour frame buffer device 160x64
[   16.557051] fb0: radeondrmfb frame buffer device
[   16.557052] drm: registered panic notifier
[   16.557057] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   16.591910] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.591914] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591917] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.591919] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591922] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.591924] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591926] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.591929] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591931] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.591934] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591936] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.591939] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591941] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.591944] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591946] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.591948] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591951] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.591953] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591956] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.591958] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591960] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.591963] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591965] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.591968] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.591970] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.591973] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.591975] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   16.591978] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.594435] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.595067] Registered led device: rt2800usb-phy0::radio
[   16.595089] Registered led device: rt2800usb-phy0::assoc
[   16.595112] Registered led device: rt2800usb-phy0::quality
[   16.595142] usbcore: registered new interface driver rt2800usb
[   17.000484] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.091927] init: failsafe main process (778) killed by TERM signal
[   17.121892] Bluetooth: Core ver 2.16
[   17.121917] NET: Registered protocol family 31
[   17.121919] Bluetooth: HCI device and connection manager initialized
[   17.121922] Bluetooth: HCI socket layer initialized
[   17.121924] Bluetooth: L2CAP socket layer initialized
[   17.121930] Bluetooth: SCO socket layer initialized
[   17.124803] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.124806] Bluetooth: BNEP filters: protocol multicast
[   17.125175] Bluetooth: RFCOMM TTY layer initialized
[   17.125181] Bluetooth: RFCOMM socket layer initialized
[   17.125183] Bluetooth: RFCOMM ver 1.11
[   17.163541] ppdev: user-space parallel port driver
[   17.176598] type=1400 audit(1350799648.697:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=853 comm="apparmor_parser"
[   17.177121] type=1400 audit(1350799648.697:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=853 comm="apparmor_parser"
[   17.280237] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.283846] type=1400 audit(1350799648.801:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=885 comm="apparmor_parser"
[   17.286077] type=1400 audit(1350799648.805:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=886 comm="apparmor_parser"
[   17.286197] type=1400 audit(1350799648.805:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=889 comm="apparmor_parser"
[   17.286530] type=1400 audit(1350799648.805:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=886 comm="apparmor_parser"
[   17.286774] type=1400 audit(1350799648.805:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=886 comm="apparmor_parser"
[   17.336070] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.336302] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.336678] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.405887] init: alsa-restore main process (931) terminated with status 19
[   17.552162] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.552410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.380018] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   20.388061] hda-intel: No response from codec, disabling MSI: last cmd=0x300f0000
[   20.864236] wlan0: authenticate with 00:1a:2b:13:ba:89 (try 1)
[   20.865756] wlan0: authenticated
[   20.920234] wlan0: associate with 00:1a:2b:13:ba:89 (try 1)
[   20.922124] wlan0: RX AssocResp from 00:1a:2b:13:ba:89 (capab=0x411 status=0 aid=1)
[   20.922128] wlan0: associated
[   20.930399] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.396071] hda-intel: Codec #3 probe error; disabling it...
[   21.443165] hda_codec: ALC888: BIOS auto-probing.
[   21.452350] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   21.452529] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   21.452683] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   21.452838] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   21.452991] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   21.453162] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.453328] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.454962] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.456277] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   21.456310] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   21.480812] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   21.480995] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   21.659007] init: plymouth-stop pre-start process (1556) terminated with status 1
[   30.960011] wlan0: no IPv6 routers present
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-32-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 (Ubuntu 3.2.0-32.51-generic-pae 3.2.30)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01100 (reserved)
[    0.000000]  BIOS-e820: 00000000fed02000 - 00000000fed14c00 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire X3810/WG43M, BIOS P01-A3 05/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ec000 - 3726e000
[    0.000000] ACPI: RSDP 000fa770 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff90100 0006C (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: FACP bff90290 000F4 (v04 052609 FACP2056 20090526 MSFT 00000097)
[    0.000000] ACPI: DSDT bff905c0 061D5 (v02   P01-   P01-A3 000000A3 INTL 20051117)
[    0.000000] ACPI: FACS bff9e000 00040
[    0.000000] ACPI: APIC bff90390 0006C (v02 052609 APIC2056 20090526 MSFT 00000097)
[    0.000000] ACPI: MCFG bff90400 0003C (v01 052609 OEMMCFG  20090526 MSFT 00000097)
[    0.000000] ACPI: SLIC bff90440 00176 (v01 ACRSYS ACRPRDCT 20090526 MSFT 00000097)
[    0.000000] ACPI: OEMB bff9e040 00072 (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: HPET bff9a5c0 00038 (v01 052609 OEMHPET  20090526 MSFT 00000097)
[    0.000000] ACPI: GSCI bff9e0c0 02024 (v01 052609 GMCHSCI  20090526 MSFT 00000097)
[    0.000000] ACPI: AWMI bffa00f0 0004E (v01 052609 OEMB2056 20090526 MSFT 00000097)
[    0.000000] ACPI: SSDT bffa0940 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6276MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572638
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f2cec200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331849 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558301
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6179236k/7340032k available (5820k kernel code, 111316k reserved, 2844k data, 740k init, 5377608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15af13c - 0xc1876280   (2844 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15af13c   (5820 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.825 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.65 BogoMIPS (lpj=9311300)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004094] Mount-cache hash table entries: 512
[    0.004218] Initializing cgroup subsys cpuacct
[    0.004224] Initializing cgroup subsys memory
[    0.004232] Initializing cgroup subsys devices
[    0.004234] Initializing cgroup subsys freezer
[    0.004236] Initializing cgroup subsys blkio
[    0.004241] Initializing cgroup subsys perf_event
[    0.004266] CPU: Physical Processor ID: 0
[    0.004268] CPU: Processor Core ID: 0
[    0.004271] mce: CPU supports 6 MCE banks
[    0.004279] CPU0: Thermal monitoring enabled (TM2)
[    0.004282] using mwait in idle threads.
[    0.009934] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 26564 entries in 52 pages
[    0.020043] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062722] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156032] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156125] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.156127]  #2
[    0.156128] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248031] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248117] CPU 3 irqstacks, hard=f752e000 soft=f7538000
[    0.248119]  #3 Ok.
[    0.248120] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.344037] NMI watchdog enabled, takes one hw-pmu counter.
[    0.344060] Brought up 4 CPUs
[    0.344063] Total of 4 processors activated (18622.14 BogoMIPS).
[    0.347008] devtmpfs: initialized
[    0.347008] EVM: security.selinux
[    0.347008] EVM: security.SMACK64
[    0.347008] EVM: security.capability
[    0.347008] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.348572] print_constraints: dummy: 
[    0.348599] RTC time:  8:07:11, date: 10/21/12
[    0.348636] NET: Registered protocol family 16
[    0.348645] Trying to unpack rootfs image as initramfs...
[    0.348764] EISA bus registered
[    0.348792] ACPI: bus type pci registered
[    0.348854] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.348857] PCI: not using MMCONFIG
[    0.348933] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.348993] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.348994] PCI: Using configuration type 1 for base access
[    0.350091] bio: create slab <bio-0> at 0
[    0.350091] ACPI: Added _OSI(Module Device)
[    0.350091] ACPI: Added _OSI(Processor Device)
[    0.350091] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.350091] ACPI: Added _OSI(Processor Aggregator Device)
[    0.350091] ACPI: EC: Look up EC in DSDT
[    0.352970] ACPI: Executed 1 blocks of module-level executable AML code
[    0.355656] ACPI: SSDT bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.355965] ACPI: Dynamic OEM Table Load:
[    0.355968] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.356258] ACPI: SSDT bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.356568] ACPI: Dynamic OEM Table Load:
[    0.356571] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.356847] ACPI: SSDT bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.357158] ACPI: Dynamic OEM Table Load:
[    0.357161] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.357430] ACPI: SSDT bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.357742] ACPI: Dynamic OEM Table Load:
[    0.357745] ACPI: SSDT   (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.357932] ACPI: Interpreter enabled
[    0.357938] ACPI: (supports S0 S3 S4 S5)
[    0.357958] ACPI: Using IOAPIC for interrupt routing
[    0.357983] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.359172] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.359174] PCI: Using MMCONFIG for extended config space
[    0.364655] ACPI: No dock devices found.
[    0.364659] HEST: Table not found.
[    0.364663] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.364749] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.364926] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.364929] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.364931] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.364934] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.364936] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.364939] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.364953] pci 0000:00:00.0: [8086:2e20] type 0 class 0x000600
[    0.364994] pci 0000:00:01.0: [8086:2e21] type 1 class 0x000604
[    0.365032] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.365035] pci 0000:00:01.0: PME# disabled
[    0.365074] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    0.365091] pci 0000:00:19.0: reg 10: [mem 0xfe9e0000-0xfe9fffff]
[    0.365100] pci 0000:00:19.0: reg 14: [mem 0xfe9de000-0xfe9defff]
[    0.365108] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.365166] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.365170] pci 0000:00:19.0: PME# disabled
[    0.365188] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    0.365229] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.365277] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    0.365316] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.365364] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    0.365403] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.365461] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    0.365481] pci 0000:00:1a.7: reg 10: [mem 0xfe9dc000-0xfe9dc3ff]
[    0.365565] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.365570] pci 0000:00:1a.7: PME# disabled
[    0.365592] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    0.365606] pci 0000:00:1b.0: reg 10: [mem 0xfe9d8000-0xfe9dbfff 64bit]
[    0.365669] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.365673] pci 0000:00:1b.0: PME# disabled
[    0.365691] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    0.365760] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.365764] pci 0000:00:1c.0: PME# disabled
[    0.365789] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    0.365829] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.365876] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    0.365917] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.365965] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    0.366004] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.366063] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    0.366083] pci 0000:00:1d.7: reg 10: [mem 0xfe9d6000-0xfe9d63ff]
[    0.366167] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.366172] pci 0000:00:1d.7: PME# disabled
[    0.366191] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.366250] pci 0000:00:1f.0: [8086:3a18] type 0 class 0x000601
[    0.366363] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    0.366380] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.366388] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.366395] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.366403] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.366411] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb41f]
[    0.366418] pci 0000:00:1f.2: reg 24: [mem 0xfe9d4000-0xfe9d47ff]
[    0.366461] pci 0000:00:1f.2: PME# supported from D3hot
[    0.366465] pci 0000:00:1f.2: PME# disabled
[    0.366480] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    0.366494] pci 0000:00:1f.3: reg 10: [mem 0xfe9d3c00-0xfe9d3cff 64bit]
[    0.366514] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.366570] pci 0000:01:00.0: [1002:954f] type 0 class 0x000300
[    0.366584] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.366595] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.366602] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.366617] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.366647] pci 0000:01:00.0: supports D1 D2
[    0.366666] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.366680] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.366736] pci 0000:01:00.1: supports D1 D2
[    0.366765] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.366768] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.366772] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.366776] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.366831] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.366853] pci 0000:02:00.0: reg 10: [mem 0xfebff800-0xfebfffff 64bit]
[    0.366866] pci 0000:02:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.366959] pci 0000:02:00.0: supports D2
[    0.366961] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.366966] pci 0000:02:00.0: PME# disabled
[    0.372042] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.372046] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.372050] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.372123] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.372137] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.372143] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.372145] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.372148] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.372150] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.372153] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.372166] pci_bus 0000:00: on NUMA node 0
[    0.372170] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.372376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.372427]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.372430]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.372432] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.381191] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.381240] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.381283] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.381329] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.381376] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.381422] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.381469] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.381515] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.381626] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.381626] vgaarb: loaded
[    0.381626] vgaarb: bridge control possible 0000:01:00.0
[    0.381626] i2c-core: driver [aat2870] using legacy suspend method
[    0.381626] i2c-core: driver [aat2870] using legacy resume method
[    0.381626] SCSI subsystem initialized
[    0.381626] libata version 3.00 loaded.
[    0.381626] usbcore: registered new interface driver usbfs
[    0.381626] usbcore: registered new interface driver hub
[    0.381626] usbcore: registered new device driver usb
[    0.381626] PCI: Using ACPI for IRQ routing
[    0.381626] PCI: pci_cache_line_size set to 64 bytes
[    0.381626] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.381626] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.381626] NetLabel: Initializing
[    0.381626] NetLabel:  domain hash size = 128
[    0.381626] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.381626] NetLabel:  unlabeled traffic allowed by default
[    0.381626] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.381626] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.381626] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.396145] Switching to clocksource hpet
[    0.404296] AppArmor: AppArmor Filesystem Enabled
[    0.404325] pnp: PnP ACPI init
[    0.404342] ACPI: bus type pnp registered
[    0.404459] pnp 00:00: [bus 00-ff]
[    0.404461] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.404464] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.404466] pnp 00:00: [io  0x0d00-0xffff window]
[    0.404469] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.404471] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.404474] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.404476] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.404533] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.404543] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.404545] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.404600] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.404603] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.404607] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.404641] pnp 00:02: [dma 4]
[    0.404644] pnp 00:02: [io  0x0000-0x000f]
[    0.404646] pnp 00:02: [io  0x0081-0x0083]
[    0.404648] pnp 00:02: [io  0x0087]
[    0.404650] pnp 00:02: [io  0x0089-0x008b]
[    0.404652] pnp 00:02: [io  0x008f]
[    0.404653] pnp 00:02: [io  0x00c0-0x00df]
[    0.404680] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.404691] pnp 00:03: [io  0x0070-0x0071]
[    0.404702] pnp 00:03: [irq 8]
[    0.404731] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.404759] pnp 00:04: [io  0x0060]
[    0.404762] pnp 00:04: [io  0x0064]
[    0.404767] pnp 00:04: [irq 1]
[    0.404795] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.404839] pnp 00:05: [irq 12]
[    0.404867] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.404877] pnp 00:06: [io  0x0061]
[    0.404906] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.404915] pnp 00:07: [io  0x00f0-0x00ff]
[    0.404920] pnp 00:07: [irq 13]
[    0.404948] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.405339] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.405342] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.405344] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.405348] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.405350] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.405401] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.405404] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.405407] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.405409] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.405413] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.405521] pnp 00:09: [io  0x0010-0x001f]
[    0.405524] pnp 00:09: [io  0x0022-0x003f]
[    0.405526] pnp 00:09: [io  0x0044-0x005f]
[    0.405528] pnp 00:09: [io  0x0062-0x0063]
[    0.405530] pnp 00:09: [io  0x0065-0x006f]
[    0.405532] pnp 00:09: [io  0x0072-0x007f]
[    0.405534] pnp 00:09: [io  0x0080]
[    0.405536] pnp 00:09: [io  0x0084-0x0086]
[    0.405538] pnp 00:09: [io  0x0088]
[    0.405540] pnp 00:09: [io  0x008c-0x008e]
[    0.405542] pnp 00:09: [io  0x0090-0x009f]
[    0.405544] pnp 00:09: [io  0x00a2-0x00bf]
[    0.405546] pnp 00:09: [io  0x00e0-0x00ef]
[    0.405548] pnp 00:09: [io  0x04d0-0x04d1]
[    0.405550] pnp 00:09: [io  0x0800-0x087f]
[    0.405552] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.405554] pnp 00:09: [io  0x0500-0x057f]
[    0.405556] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.405559] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.405561] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.405621] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.405623] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.405626] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.405629] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.405632] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.405635] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.405638] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.405692] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.405723] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.405771] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.405774] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.405808] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.405847] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.405896] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.405899] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.405977] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.405979] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.406030] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.406033] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.406036] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.406080] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.406127] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.406131] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.406305] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.406308] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.406310] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.406313] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.406315] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.406374] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.406377] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.406380] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.406382] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.406385] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.406388] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.406517] pnp: PnP ACPI: found 16 devices
[    0.406518] ACPI: ACPI bus type pnp unregistered
[    0.406522] PnPBIOS: Disabled by ACPI PNP
[    0.444593] PCI: max bus depth: 1 pci_try_num: 2
[    0.444624] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.444628] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.444631] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.444635] pci 0000:00:01.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.444638] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.444642] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.444645] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.444650] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.444654] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.444659] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.444686] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.444691] pci 0000:00:01.0: setting latency timer to 64
[    0.444701] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.444705] pci 0000:00:1c.0: setting latency timer to 64
[    0.444712] pci 0000:00:1e.0: setting latency timer to 64
[    0.444715] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.444718] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.444720] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.444723] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.444725] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.444727] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.444730] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.444732] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.444735] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.444737] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.444740] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.444742] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.444745] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.444747] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.444750] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.444752] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.444755] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.444757] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.444797] NET: Registered protocol family 2
[    0.444867] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.445082] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.445418] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.445585] TCP: Hash tables configured (established 131072 bind 65536)
[    0.445588] TCP reno registered
[    0.445591] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.445599] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.445685] NET: Registered protocol family 1
[    0.445714] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.445731] pci 0000:00:1a.0: PCI INT A disabled
[    0.445746] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.445761] pci 0000:00:1a.1: PCI INT B disabled
[    0.445771] pci 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.445785] pci 0000:00:1a.2: PCI INT D disabled
[    0.445796] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.445826] pci 0000:00:1a.7: PCI INT C disabled
[    0.445840] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.445855] pci 0000:00:1d.0: PCI INT A disabled
[    0.445862] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.445877] pci 0000:00:1d.1: PCI INT B disabled
[    0.445884] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.445899] pci 0000:00:1d.2: PCI INT C disabled
[    0.445907] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.445920] pci 0000:00:1d.7: PCI INT A disabled
[    0.445933] pci 0000:01:00.0: Boot video device
[    0.445941] PCI: CLS 32 bytes, default 64
[    0.446427] audit: initializing netlink socket (disabled)
[    0.446435] type=2000 audit(1350806831.440:1): initialized
[    0.467415] highmem bounce pool size: 64 pages
[    0.467420] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.470050] VFS: Disk quotas dquot_6.5.2
[    0.470112] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.470699] fuse init (API version 7.17)
[    0.470809] msgmni has been set to 1565
[    0.471357] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.471392] io scheduler noop registered
[    0.471399] io scheduler deadline registered
[    0.471411] io scheduler cfq registered (default)
[    0.471520] pcieport 0000:00:01.0: setting latency timer to 64
[    0.471550] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.471598] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.471632] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.471710] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.471735] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.471797] intel_idle: MWAIT substates: 0x20
[    0.471798] intel_idle: does not run on family 6 model 23
[    0.471882] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.471887] ACPI: Power Button [PWRB]
[    0.471933] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.471936] ACPI: Power Button [PWRF]
[    0.474594] ERST: Table is not found!
[    0.474596] GHES: HEST is not enabled!
[    0.474696] isapnp: Scanning for PnP cards...
[    0.474727] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.633794] Freeing initrd memory: 13832k freed
[    0.827591] isapnp: No Plug & Play device found
[    0.880586] Linux agpgart interface v0.103
[    0.882714] brd: module loaded
[    0.883740] loop: module loaded
[    0.883878] ahci 0000:00:1f.2: version 3.0
[    0.883891] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.883929] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.883974] ahci: SSS flag set, parallel bus scan disabled
[    0.884015] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.884019] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.884023] ahci 0000:00:1f.2: setting latency timer to 64
[    0.924625] scsi0 : ahci
[    0.924743] scsi1 : ahci
[    0.924848] scsi2 : ahci
[    0.924939] scsi3 : ahci
[    0.925055] scsi4 : ahci
[    0.925162] scsi5 : ahci
[    0.925333] ata1: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4100 irq 42
[    0.925336] ata2: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4180 irq 42
[    0.925339] ata3: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4200 irq 42
[    0.925341] ata4: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4280 irq 42
[    0.925344] ata5: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4300 irq 42
[    0.925347] ata6: SATA max UDMA/133 abar m2048@0xfe9d4000 port 0xfe9d4380 irq 42
[    0.925778] Fixed MDIO Bus: probed
[    0.925799] tun: Universal TUN/TAP device driver, 1.6
[    0.925801] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.925878] PPP generic driver version 2.4.2
[    0.926037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.926054] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.926067] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.926070] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.926139] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.926161] ehci_hcd 0000:00:1a.7: debug port 1
[    0.930031] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.930046] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9dc000
[    0.944015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.944178] hub 1-0:1.0: USB hub found
[    0.944182] hub 1-0:1.0: 6 ports detected
[    0.944258] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.944268] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.944271] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.944336] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.944358] ehci_hcd 0000:00:1d.7: debug port 1
[    0.948254] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.948267] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9d6000
[    0.964014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.964155] hub 2-0:1.0: USB hub found
[    0.964159] hub 2-0:1.0: 6 ports detected
[    0.964232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.964245] uhci_hcd: USB Universal Host Controller Interface driver
[    0.964261] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.964268] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.964271] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.964337] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.964366] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.964513] hub 3-0:1.0: USB hub found
[    0.964517] hub 3-0:1.0: 2 ports detected
[    0.964579] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.964587] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.964590] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.964657] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.964688] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.964836] hub 4-0:1.0: USB hub found
[    0.964840] hub 4-0:1.0: 2 ports detected
[    0.964908] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.964914] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.964917] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.964983] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.965012] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.965158] hub 5-0:1.0: USB hub found
[    0.965161] hub 5-0:1.0: 2 ports detected
[    0.965221] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.965227] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.965230] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.965297] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.965318] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.965466] hub 6-0:1.0: USB hub found
[    0.965469] hub 6-0:1.0: 2 ports detected
[    0.965531] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.965538] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.965541] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.965607] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.965628] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.965774] hub 7-0:1.0: USB hub found
[    0.965778] hub 7-0:1.0: 2 ports detected
[    0.965841] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.965848] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.965851] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.965919] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.965939] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.966085] hub 8-0:1.0: USB hub found
[    0.966089] hub 8-0:1.0: 2 ports detected
[    0.966203] usbcore: registered new interface driver libusual
[    0.966261] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.966621] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.966628] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.966789] mousedev: PS/2 mouse device common for all mice
[    0.967002] rtc_cmos 00:03: RTC can wake from S4
[    0.967124] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.967146] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.967204] device-mapper: uevent: version 1.0.3
[    0.967302] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.967333] EISA: Probing bus 0 at eisa.0
[    0.967335] EISA: Cannot allocate resource for mainboard
[    0.967338] Cannot allocate resource for EISA slot 1
[    0.967339] Cannot allocate resource for EISA slot 2
[    0.967341] Cannot allocate resource for EISA slot 3
[    0.967343] Cannot allocate resource for EISA slot 4
[    0.967345] Cannot allocate resource for EISA slot 5
[    0.967346] Cannot allocate resource for EISA slot 6
[    0.967348] Cannot allocate resource for EISA slot 7
[    0.967350] Cannot allocate resource for EISA slot 8
[    0.967352] EISA: Detected 0 cards.
[    0.967360] cpufreq-nforce2: No nForce2 chipset.
[    0.967363] cpuidle: using governor ladder
[    0.967365] cpuidle: using governor menu
[    0.967366] EFI Variables Facility v0.08 2004-May-17
[    0.967627] TCP cubic registered
[    0.967754] NET: Registered protocol family 10
[    0.968322] NET: Registered protocol family 17
[    0.968327] Registering the dns_resolver key type
[    0.968346] Using IPI No-Shortcut mode
[    0.968506] PM: Hibernation image not present or could not be loaded.
[    0.968518] registered taskstats version 1
[    0.975453]   Magic number: 0:514:119
[    0.975552] rtc_cmos 00:03: setting system clock to 2012-10-21 08:07:12 UTC (1350806832)
[    0.976603] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.976605] EDD information not available.
[    0.982903] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.244020] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.247035] ata1.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.250909] ata1.00: configured for UDMA/100
[    1.256016] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    1.258547] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.267019] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.267023] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.267162] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.267239] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.444015] Refined TSC clocksource calibration: 2327.754 MHz.
[    1.444020] Switching to clocksource tsc
[    1.572012] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.584017] ata2: SATA link down (SStatus 0 SControl 300)
[    1.708224] Initializing USB Mass Storage driver...
[    1.708385] scsi6 : usb-storage 2-3:1.0
[    1.708467] usbcore: registered new interface driver usb-storage
[    1.708469] USB Mass Storage support registered.
[    1.904014] ata3: SATA link down (SStatus 0 SControl 300)
[    1.944012] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    2.224015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.237691] ata4.00: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    2.237695] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.238712] ata4.00: configured for UDMA/133
[    2.238837] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    2.238983] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.238999] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.239054] sd 3:0:0:0: [sda] Write Protect is off
[    2.239057] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.239088] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.281580]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.281984] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.556014] ata5: SATA link down (SStatus 0 SControl 300)
[    2.708731] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.709346] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    2.710137] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.710284] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.713828] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.714579] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.876014] ata6: SATA link down (SStatus 0 SControl 300)
[    2.876104] Freeing unused kernel memory: 740k freed
[    2.876361] Write protecting the kernel text: 5824k
[    2.876390] Write protecting the kernel read-only data: 2376k
[    2.876392] NX-protecting the kernel data: 4416k
[    2.893320] udevd[113]: starting version 175
[    2.923318] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.923321] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.923364] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.923374] e1000e 0000:00:19.0: setting latency timer to 64
[    2.923473] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.924649] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.924657] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.931691] generic-usb 0003:058F:6363.0001: hiddev0,hidraw0: USB HID v1.10 Device [Generic Mass Storage Device] on usb-0000:00:1d.7-3/input1
[    2.946556] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.946749] generic-usb 0003:046D:C51B.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1/input0
[    2.960142] generic-usb 0003:046D:C51B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-1/input1
[    2.960167] usbcore: registered new interface driver usbhid
[    2.960169] usbhid: USB HID core driver
[    2.988049] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.110403] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:f4:ca:94
[    3.110407] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.110429] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    3.345506] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.345509] EXT4-fs (sda6): write access will be enabled during recovery
[    3.488107] firewire_core: created device fw0: GUID 001d72ffae924fff, S400
[    4.982885] EXT4-fs (sda6): recovery complete
[    4.983211] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.153896] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.186353] udevd[358]: starting version 175
[   16.239207] Adding 9068540k swap on /dev/sda5.  Priority:-1 extents:1 across:9068540k 
[   16.239586] lp: driver loaded but no devices found
[   16.240442] [drm] Initialized drm 1.1.0 20060810
[   16.259772] cfg80211: Calling CRDA to update world regulatory domain
[   16.259868] type=1400 audit(1350799647.777:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=461 comm="apparmor_parser"
[   16.260328] type=1400 audit(1350799647.781:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=461 comm="apparmor_parser"
[   16.260573] type=1400 audit(1350799647.781:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=461 comm="apparmor_parser"
[   16.266680] [drm] radeon defaulting to kernel modesetting.
[   16.266684] [drm] radeon kernel modesetting enabled.
[   16.266747] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.266753] radeon 0000:01:00.0: setting latency timer to 64
[   16.279922] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x174B:0xE990).
[   16.279953] [drm] register mmio base: 0xFEAF0000
[   16.279955] [drm] register mmio size: 65536
[   16.280111] ATOM BIOS: 11X
[   16.280142] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   16.280145] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   16.282200] [drm] Detected VRAM RAM=512M, BAR=256M
[   16.282205] [drm] RAM width 64bits DDR
[   16.284844] [TTM] Zone  kernel: Available graphics memory: 408100 kiB.
[   16.284847] [TTM] Zone highmem: Available graphics memory: 3096904 kiB.
[   16.284849] [TTM] Initializing pool allocator.
[   16.284870] [drm] radeon: 512M of VRAM memory ready
[   16.284872] [drm] radeon: 512M of GTT memory ready.
[   16.284891] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.284893] [drm] Driver supports precise vblank timestamp query.
[   16.284935] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   16.284940] radeon 0000:01:00.0: radeon: using MSI.
[   16.284970] [drm] radeon: irq initialized.
[   16.284974] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   16.285836] [drm] Loading RV710 Microcode
[   16.311054] wmi: Mapper loaded
[   16.334828] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.334876] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.334899] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.413246] cfg80211: World regulatory domain updated:
[   16.413249] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.413252] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.413255] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.413258] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.413260] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.413263] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.420031] usb 1-4: reset high-speed USB device number 2 using ehci_hcd
[   16.435711] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   16.435761] radeon 0000:01:00.0: WB enabled
[   16.481706] [drm] ring test succeeded in 1 usecs
[   16.481848] [drm] radeon: ib pool ready.
[   16.481921] [drm] ib test succeeded in 0 usecs
[   16.482279] [drm] Radeon Display Connectors
[   16.482281] [drm] Connector 0:
[   16.482283] [drm]   VGA
[   16.482285] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   16.482287] [drm]   Encoders:
[   16.482288] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   16.482290] [drm] Connector 1:
[   16.482291] [drm]   HDMI-A
[   16.482293] [drm]   HPD1
[   16.482295] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   16.482296] [drm]   Encoders:
[   16.482298] [drm]     DFP1: INTERNAL_UNIPHY
[   16.482299] [drm] Connector 2:
[   16.482301] [drm]   DVI-I
[   16.482302] [drm]   HPD4
[   16.482304] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   16.482306] [drm]   Encoders:
[   16.482307] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   16.482309] [drm]     DFP2: INTERNAL_UNIPHY2
[   16.482327] [drm] Internal thermal controller with fan control
[   16.482368] [drm] radeon: power management initialized
[   16.556826] [drm] fb mappable at 0xD0142000
[   16.556828] [drm] vram apper at 0xD0000000
[   16.556829] [drm] size 5242880
[   16.556831] [drm] fb depth is 24
[   16.556832] [drm]    pitch is 5120
[   16.556932] fbcon: radeondrmfb (fb0) is primary device
[   16.557017] Console: switching to colour frame buffer device 160x64
[   16.557051] fb0: radeondrmfb frame buffer device
[   16.557052] drm: registered panic notifier
[   16.557057] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   16.591910] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.591914] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591917] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.591919] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591922] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.591924] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591926] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.591929] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591931] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.591934] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591936] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.591939] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591941] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.591944] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591946] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.591948] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591951] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.591953] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591956] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.591958] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591960] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.591963] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.591965] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.591968] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.591970] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.591973] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.591975] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   16.591978] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.594435] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.595067] Registered led device: rt2800usb-phy0::radio
[   16.595089] Registered led device: rt2800usb-phy0::assoc
[   16.595112] Registered led device: rt2800usb-phy0::quality
[   16.595142] usbcore: registered new interface driver rt2800usb
[   17.000484] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.091927] init: failsafe main process (778) killed by TERM signal
[   17.121892] Bluetooth: Core ver 2.16
[   17.121917] NET: Registered protocol family 31
[   17.121919] Bluetooth: HCI device and connection manager initialized
[   17.121922] Bluetooth: HCI socket layer initialized
[   17.121924] Bluetooth: L2CAP socket layer initialized
[   17.121930] Bluetooth: SCO socket layer initialized
[   17.124803] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.124806] Bluetooth: BNEP filters: protocol multicast
[   17.125175] Bluetooth: RFCOMM TTY layer initialized
[   17.125181] Bluetooth: RFCOMM socket layer initialized
[   17.125183] Bluetooth: RFCOMM ver 1.11
[   17.163541] ppdev: user-space parallel port driver
[   17.176598] type=1400 audit(1350799648.697:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=853 comm="apparmor_parser"
[   17.177121] type=1400 audit(1350799648.697:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=853 comm="apparmor_parser"
[   17.280237] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.283846] type=1400 audit(1350799648.801:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=885 comm="apparmor_parser"
[   17.286077] type=1400 audit(1350799648.805:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=886 comm="apparmor_parser"
[   17.286197] type=1400 audit(1350799648.805:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=889 comm="apparmor_parser"
[   17.286530] type=1400 audit(1350799648.805:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=886 comm="apparmor_parser"
[   17.286774] type=1400 audit(1350799648.805:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=886 comm="apparmor_parser"
[   17.336070] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.336302] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.336678] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.405887] init: alsa-restore main process (931) terminated with status 19
[   17.552162] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.552410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.380018] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   20.388061] hda-intel: No response from codec, disabling MSI: last cmd=0x300f0000
[   20.864236] wlan0: authenticate with 00:1a:2b:13:ba:89 (try 1)
[   20.865756] wlan0: authenticated
[   20.920234] wlan0: associate with 00:1a:2b:13:ba:89 (try 1)
[   20.922124] wlan0: RX AssocResp from 00:1a:2b:13:ba:89 (capab=0x411 status=0 aid=1)
[   20.922128] wlan0: associated
[   20.930399] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.396071] hda-intel: Codec #3 probe error; disabling it...
[   21.443165] hda_codec: ALC888: BIOS auto-probing.
[   21.452350] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   21.452529] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   21.452683] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   21.452838] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   21.452991] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   21.453162] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   21.453328] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.454962] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.456277] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   21.456310] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   21.480812] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   21.480995] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   21.659007] init: plymouth-stop pre-start process (1556) terminated with status 1
[   30.960011] wlan0: no IPv6 routers present

```[/B] 

and here is the xorg:

[B]```

[  1080.048] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  1080.048] X Protocol Version 11, Revision 0
[  1080.048] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[  1080.048] Current Operating System: Linux Compuabajo 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686
[  1080.048] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=3169b696-02b9-4593-b5f7-30c72e816dc7 ro quiet splash vt.handoff=7
[  1080.048] Build Date: 29 August 2012  12:10:05AM
[  1080.048] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[  1080.048] Current version of pixman: 0.24.4
[  1080.048]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1080.048] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1080.048] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 21 08:01:46 2012
[  1080.049] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1080.049] (==) No Layout section.  Using the first Screen section.
[  1080.049] (==) No screen section available. Using defaults.
[  1080.049] (**) |-->Screen "Default Screen Section" (0)
[  1080.049] (**) |   |-->Monitor "<default monitor>"
[  1080.049] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1080.049] (==) Automatically adding devices
[  1080.049] (==) Automatically enabling devices
[  1080.049] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1080.049]     Entry deleted from font path.
[  1080.049] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1080.049]     Entry deleted from font path.
[  1080.049] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1080.049]     Entry deleted from font path.
[  1080.049] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1080.049]     Entry deleted from font path.
[  1080.049] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1080.049]     Entry deleted from font path.
[  1080.049] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  1080.049]     Entry deleted from font path.
[  1080.049] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1080.049] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1080.049] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1080.049] (II) Loader magic: 0xb77295a0
[  1080.049] (II) Module ABI versions:
[  1080.049]     X.Org ANSI C Emulation: 0.4
[  1080.049]     X.Org Video Driver: 11.0
[  1080.049]     X.Org XInput driver : 16.0
[  1080.049]     X.Org Server Extension : 6.0
[  1080.050] (--) PCI:*(0:1:0:0) 1002:954f:174b:e990 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[  1080.050] (II) Open ACPI successful (/var/run/acpid.socket)
[  1080.050] (II) LoadModule: "extmod"
[  1080.051] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1080.051] (II) Module extmod: vendor="X.Org Foundation"
[  1080.051]     compiled for 1.11.3, module version = 1.0.0
[  1080.051]     Module class: X.Org Server Extension
[  1080.051]     ABI class: X.Org Server Extension, version 6.0
[  1080.051] (II) Loading extension MIT-SCREEN-SAVER
[  1080.051] (II) Loading extension XFree86-VidModeExtension
[  1080.051] (II) Loading extension XFree86-DGA
[  1080.051] (II) Loading extension DPMS
[  1080.051] (II) Loading extension XVideo
[  1080.051] (II) Loading extension XVideo-MotionCompensation
[  1080.051] (II) Loading extension X-Resource
[  1080.051] (II) LoadModule: "dbe"
[  1080.051] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1080.051] (II) Module dbe: vendor="X.Org Foundation"
[  1080.051]     compiled for 1.11.3, module version = 1.0.0
[  1080.051]     Module class: X.Org Server Extension
[  1080.051]     ABI class: X.Org Server Extension, version 6.0
[  1080.051] (II) Loading extension DOUBLE-BUFFER
[  1080.051] (II) LoadModule: "glx"
[  1080.052] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1080.052] (II) Module glx: vendor="X.Org Foundation"
[  1080.052]     compiled for 1.11.3, module version = 1.0.0
[  1080.052]     ABI class: X.Org Server Extension, version 6.0
[  1080.052] (==) AIGLX enabled
[  1080.052] (II) Loading extension GLX
[  1080.052] (II) LoadModule: "record"
[  1080.052] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1080.052] (II) Module record: vendor="X.Org Foundation"
[  1080.052]     compiled for 1.11.3, module version = 1.13.0
[  1080.053]     Module class: X.Org Server Extension
[  1080.053]     ABI class: X.Org Server Extension, version 6.0
[  1080.053] (II) Loading extension RECORD
[  1080.053] (II) LoadModule: "dri"
[  1080.053] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1080.053] (II) Module dri: vendor="X.Org Foundation"
[  1080.053]     compiled for 1.11.3, module version = 1.0.0
[  1080.053]     ABI class: X.Org Server Extension, version 6.0
[  1080.053] (II) Loading extension XFree86-DRI
[  1080.053] (II) LoadModule: "dri2"
[  1080.053] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1080.054] (II) Module dri2: vendor="X.Org Foundation"
[  1080.054]     compiled for 1.11.3, module version = 1.2.0
[  1080.054]     ABI class: X.Org Server Extension, version 6.0
[  1080.054] (II) Loading extension DRI2
[  1080.054] (==) Matched fglrx as autoconfigured driver 0
[  1080.054] (==) Matched ati as autoconfigured driver 1
[  1080.054] (==) Matched vesa as autoconfigured driver 2
[  1080.054] (==) Matched fbdev as autoconfigured driver 3
[  1080.054] (==) Assigned the driver to the xf86ConfigLayout
[  1080.054] (II) LoadModule: "fglrx"
[  1080.054] (WW) Warning, couldn't open module fglrx
[  1080.054] (II) UnloadModule: "fglrx"
[  1080.054] (II) Unloading fglrx
[  1080.054] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1080.054] (II) LoadModule: "ati"
[  1080.054] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1080.055] (II) Module ati: vendor="X.Org Foundation"
[  1080.055]     compiled for 1.11.3, module version = 6.14.99
[  1080.055]     Module class: X.Org Video Driver
[  1080.055]     ABI class: X.Org Video Driver, version 11.0
[  1080.055] (II) LoadModule: "radeon"
[  1080.055] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  1080.055] (II) Module radeon: vendor="X.Org Foundation"
[  1080.055]     compiled for 1.11.3, module version = 6.14.99
[  1080.055]     Module class: X.Org Video Driver
[  1080.055]     ABI class: X.Org Video Driver, version 11.0
[  1080.055] (II) LoadModule: "vesa"
[  1080.055] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1080.055] (II) Module vesa: vendor="X.Org Foundation"
[  1080.055]     compiled for 1.11.3, module version = 2.3.0
[  1080.055]     Module class: X.Org Video Driver
[  1080.055]     ABI class: X.Org Video Driver, version 11.0
[  1080.055] (II) LoadModule: "fbdev"
[  1080.056] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1080.056] (II) Module fbdev: vendor="X.Org Foundation"
[  1080.056]     compiled for 1.11.3, module version = 0.4.2
[  1080.056]     ABI class: X.Org Video Driver, version 11.0
[  1080.056] (==) Matched fglrx as autoconfigured driver 0
[  1080.056] (==) Matched ati as autoconfigured driver 1
[  1080.056] (==) Matched vesa as autoconfigured driver 2
[  1080.056] (==) Matched fbdev as autoconfigured driver 3
[  1080.056] (==) Assigned the driver to the xf86ConfigLayout
[  1080.056] (II) LoadModule: "fglrx"
[  1080.056] (WW) Warning, couldn't open module fglrx
[  1080.056] (II) UnloadModule: "fglrx"
[  1080.056] (II) Unloading fglrx
[  1080.056] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1080.056] (II) LoadModule: "ati"
[  1080.057] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1080.057] (II) Module ati: vendor="X.Org Foundation"
[  1080.057]     compiled for 1.11.3, module version = 6.14.99
[  1080.057]     Module class: X.Org Video Driver
[  1080.057]     ABI class: X.Org Video Driver, version 11.0
[  1080.057] (II) LoadModule: "vesa"
[  1080.057] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1080.057] (II) Module vesa: vendor="X.Org Foundation"
[  1080.057]     compiled for 1.11.3, module version = 2.3.0
[  1080.057]     Module class: X.Org Video Driver
[  1080.057]     ABI class: X.Org Video Driver, version 11.0
[  1080.057] (II) UnloadModule: "vesa"
[  1080.057] (II) Unloading vesa
[  1080.057] (II) Failed to load module "vesa" (already loaded, 0)
[  1080.057] (II) LoadModule: "fbdev"
[  1080.057] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1080.057] (II) Module fbdev: vendor="X.Org Foundation"
[  1080.057]     compiled for 1.11.3, module version = 0.4.2
[  1080.057]     ABI class: X.Org Video Driver, version 11.0
[  1080.057] (II) UnloadModule: "fbdev"
[  1080.057] (II) Unloading fbdev
[  1080.057] (II) Failed to load module "fbdev" (already loaded, 0)
[  1080.057] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[  1080.062] (II) VESA: driver for VESA chipsets: vesa
[  1080.062] (II) FBDEV: driver for framebuffer: fbdev
[  1080.062] (++) using VT number 7

[  1080.062] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  1080.062] (II) [KMS] Kernel modesetting enabled.
[  1080.062] (WW) Falling back to old probe method for vesa
[  1080.062] (WW) Falling back to old probe method for fbdev
[  1080.062] (II) Loading sub module "fbdevhw"
[  1080.062] (II) LoadModule: "fbdevhw"
[  1080.062] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1080.062] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1080.062]     compiled for 1.11.3, module version = 0.0.2
[  1080.062]     ABI class: X.Org Video Driver, version 11.0
[  1080.062] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1080.062] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  1080.062] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  1080.062] (==) RADEON(0): Default visual is TrueColor
[  1080.062] (==) RADEON(0): RGB weight 888
[  1080.062] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  1080.062] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[  1080.062] (II) RADEON(0): PCIE card detected
[  1080.062] drmOpenDevice: node name is /dev/dri/card0
[  1080.062] drmOpenDevice: open result is 9, (OK)
[  1080.062] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  1080.062] drmOpenDevice: node name is /dev/dri/card0
[  1080.062] drmOpenDevice: open result is 9, (OK)
[  1080.062] drmOpenByBusid: drmOpenMinor returns 9
[  1080.062] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  1080.062] (II) Loading sub module "exa"
[  1080.063] (II) LoadModule: "exa"
[  1080.063] (II) Loading /usr/lib/xorg/modules/libexa.so
[  1080.063] (II) Module exa: vendor="X.Org Foundation"
[  1080.063]     compiled for 1.11.3, module version = 2.5.0
[  1080.063]     ABI class: X.Org Video Driver, version 11.0
[  1080.063] (II) RADEON(0): KMS Color Tiling: enabled
[  1080.063] (II) RADEON(0): KMS Pageflipping: enabled
[  1080.063] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  1080.088] (II) RADEON(0): Output VGA-0 has no monitor section
[  1080.092] (II) RADEON(0): Output HDMI-0 has no monitor section
[  1080.148] (II) RADEON(0): Output DVI-0 has no monitor section
[  1080.172] (II) RADEON(0): EDID for output VGA-0
[  1080.176] (II) RADEON(0): EDID for output HDMI-0
[  1080.232] (II) RADEON(0): EDID for output DVI-0
[  1080.232] (II) RADEON(0): Manufacturer: DEL  Model: a00a  Serial#: 1111576887
[  1080.232] (II) RADEON(0): Year: 2004  Week: 2
[  1080.232] (II) RADEON(0): EDID Version: 1.3
[  1080.232] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[  1080.232] (II) RADEON(0): Sync:  Separate
[  1080.232] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[  1080.232] (II) RADEON(0): Gamma: 2.20
[  1080.232] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[  1080.232] (II) RADEON(0): First detailed timing is preferred mode
[  1080.232] (II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
[  1080.232] (II) RADEON(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
[  1080.232] (II) RADEON(0): Supported established timings:
[  1080.232] (II) RADEON(0): 720x400@70Hz
[  1080.232] (II) RADEON(0): 640x480@60Hz
[  1080.232] (II) RADEON(0): 640x480@75Hz
[  1080.232] (II) RADEON(0): 800x600@60Hz
[  1080.232] (II) RADEON(0): 800x600@75Hz
[  1080.232] (II) RADEON(0): 1024x768@60Hz
[  1080.232] (II) RADEON(0): 1024x768@75Hz
[  1080.232] (II) RADEON(0): 1280x1024@75Hz
[  1080.232] (II) RADEON(0): Manufacturer's mask: 0
[  1080.232] (II) RADEON(0): Supported standard timings:
[  1080.232] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  1080.232] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  1080.232] (II) RADEON(0): Supported detailed timing:
[  1080.232] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[  1080.232] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[  1080.232] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[  1080.232] (II) RADEON(0): Serial No: P144641ABAQ7
[  1080.232] (II) RADEON(0): Monitor name: DELL E172FP
[  1080.232] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 145 MHz
[  1080.232] (II) RADEON(0): EDID (in hex):
[  1080.232] (II) RADEON(0):     00ffffffffffff0010ac0aa037514142
[  1080.232] (II) RADEON(0):     020e010368221b78eac5c6a3574a9c23
[  1080.232] (II) RADEON(0):     124f54a54b00714f8180010101010101
[  1080.232] (II) RADEON(0):     010101010101302a009851002a403070
[  1080.232] (II) RADEON(0):     1300520e1100001e000000ff00503134
[  1080.232] (II) RADEON(0):     3436343141424151370a000000fc0044
[  1080.232] (II) RADEON(0):     454c4c204531373246500a20000000fd
[  1080.232] (II) RADEON(0):     00384c1f500e000a202020202020000e
[  1080.232] (II) RADEON(0): Printing probed modes for output DVI-0
[  1080.232] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1080.232] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1080.232] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1080.232] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[  1080.232] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1080.232] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1080.233] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1080.233] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1080.233] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1080.233] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1080.233] (II) RADEON(0): Output VGA-0 disconnected
[  1080.233] (II) RADEON(0): Output HDMI-0 disconnected
[  1080.233] (II) RADEON(0): Output DVI-0 connected
[  1080.233] (II) RADEON(0): Using exact sizes for initial modes
[  1080.233] (II) RADEON(0): Output DVI-0 using initial mode 1280x1024
[  1080.233] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1080.233] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fac0000
[  1080.233] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  1080.233] (==) RADEON(0): DPI set to (96, 96)
[  1080.233] (II) Loading sub module "fb"
[  1080.233] (II) LoadModule: "fb"
[  1080.233] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1080.233] (II) Module fb: vendor="X.Org Foundation"
[  1080.233]     compiled for 1.11.3, module version = 1.0.0
[  1080.233]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1080.233] (II) Loading sub module "ramdac"
[  1080.233] (II) LoadModule: "ramdac"
[  1080.233] (II) Module "ramdac" already built-in
[  1080.233] (II) UnloadModule: "vesa"
[  1080.233] (II) Unloading vesa
[  1080.233] (II) UnloadModule: "fbdev"
[  1080.233] (II) Unloading fbdev
[  1080.233] (II) UnloadModule: "fbdevhw"
[  1080.233] (II) Unloading fbdevhw
[  1080.233] (--) Depth 24 pixmap format is 32 bpp
[  1080.233] (II) RADEON(0): [DRI2] Setup complete
[  1080.233] (II) RADEON(0): [DRI2]   DRI driver: r600
[  1080.233] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[  1080.233] (II) RADEON(0): Front buffer size: 5120K
[  1080.233] (II) RADEON(0): VRAM usage limit set to 226483K
[  1080.233] (==) RADEON(0): Backing store disabled
[  1080.233] (II) RADEON(0): Direct rendering enabled
[  1080.233] (II) RADEON(0): Setting EXA maxPitchBytes
[  1080.233] (II) EXA(0): Driver allocated offscreen pixmaps
[  1080.233] (II) EXA(0): Driver registered support for the following operations:
[  1080.233] (II)         Solid
[  1080.234] (II)         Copy
[  1080.234] (II)         Composite (RENDER acceleration)
[  1080.234] (II)         UploadToScreen
[  1080.234] (II)         DownloadFromScreen
[  1080.234] (II) RADEON(0): Acceleration enabled
[  1080.234] (==) RADEON(0): DPMS enabled
[  1080.234] (==) RADEON(0): Silken mouse enabled
[  1080.234] (II) RADEON(0): Set up textured video
[  1080.234] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  1080.234] (II) RADEON(0): [XvMC] Extension initialized.
[  1080.234] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1080.234] (--) RandR disabled
[  1080.234] (II) Initializing built-in extension Generic Event Extension
[  1080.234] (II) Initializing built-in extension SHAPE
[  1080.234] (II) Initializing built-in extension MIT-SHM
[  1080.234] (II) Initializing built-in extension XInputExtension
[  1080.234] (II) Initializing built-in extension XTEST
[  1080.234] (II) Initializing built-in extension BIG-REQUESTS
[  1080.234] (II) Initializing built-in extension SYNC
[  1080.234] (II) Initializing built-in extension XKEYBOARD
[  1080.234] (II) Initializing built-in extension XC-MISC
[  1080.234] (II) Initializing built-in extension SECURITY
[  1080.234] (II) Initializing built-in extension XINERAMA
[  1080.234] (II) Initializing built-in extension XFIXES
[  1080.234] (II) Initializing built-in extension RENDER
[  1080.234] (II) Initializing built-in extension RANDR
[  1080.234] (II) Initializing built-in extension COMPOSITE
[  1080.234] (II) Initializing built-in extension DAMAGE
[  1080.253] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1080.253] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1080.253] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1080.253] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1080.253] (II) AIGLX: Loaded and initialized r600
[  1080.253] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1080.254] (II) RADEON(0): Setting screen physical size to 338 x 270
[  1080.262] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1080.265] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1080.265] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1080.265] (II) LoadModule: "evdev"
[  1080.266] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1080.266] (II) Module evdev: vendor="X.Org Foundation"
[  1080.266]     compiled for 1.11.3, module version = 2.7.0
[  1080.266]     Module class: X.Org XInput Driver
[  1080.266]     ABI class: X.Org XInput driver, version 16.0
[  1080.266] (II) Using input driver 'evdev' for 'Power Button'
[  1080.266] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1080.266] (**) Power Button: always reports core events
[  1080.266] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1080.266] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1080.266] (--) evdev: Power Button: Found keys
[  1080.266] (II) evdev: Power Button: Configuring as keyboard
[  1080.266] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1080.266] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1080.266] (**) Option "xkb_rules" "evdev"
[  1080.266] (**) Option "xkb_model" "pc105"
[  1080.266] (**) Option "xkb_layout" "es"
[  1080.268] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[  1080.269] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1080.269] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1080.269] (II) Using input driver 'evdev' for 'Power Button'
[  1080.269] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1080.269] (**) Power Button: always reports core events
[  1080.269] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1080.269] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1080.269] (--) evdev: Power Button: Found keys
[  1080.269] (II) evdev: Power Button: Configuring as keyboard
[  1080.269] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1080.269] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1080.269] (**) Option "xkb_rules" "evdev"
[  1080.269] (**) Option "xkb_model" "pc105"
[  1080.269] (**) Option "xkb_layout" "es"
[  1080.270] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[  1080.270] (II) No input driver specified, ignoring this device.
[  1080.270] (II) This device may have been added with another device file.
[  1080.270] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[  1080.270] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  1080.270] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  1080.270] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1080.270] (**) Logitech USB Receiver: always reports core events
[  1080.270] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event3"
[  1080.270] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51b
[  1080.270] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[  1080.270] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[  1080.270] (--) evdev: Logitech USB Receiver: Found relative axes
[  1080.270] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[  1080.270] (II) evdev: Logitech USB Receiver: Configuring as mouse
[  1080.270] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[  1080.270] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  1080.270] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1080.270] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3/event3"
[  1080.270] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 8)
[  1080.270] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[  1080.271] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  1080.271] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  1080.271] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  1080.271] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  1080.271] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  1080.271] (II) No input driver specified, ignoring this device.
[  1080.271] (II) This device may have been added with another device file.
[  1080.271] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event10)
[  1080.271] (II) No input driver specified, ignoring this device.
[  1080.271] (II) This device may have been added with another device file.
[  1080.271] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event4)
[  1080.271] (II) No input driver specified, ignoring this device.
[  1080.271] (II) This device may have been added with another device file.
[  1080.272] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[  1080.272] (II) No input driver specified, ignoring this device.
[  1080.272] (II) This device may have been added with another device file.
[  1080.272] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[  1080.272] (II) No input driver specified, ignoring this device.
[  1080.272] (II) This device may have been added with another device file.
[  1080.272] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[  1080.272] (II) No input driver specified, ignoring this device.
[  1080.272] (II) This device may have been added with another device file.
[  1080.273] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event8)
[  1080.273] (II) No input driver specified, ignoring this device.
[  1080.273] (II) This device may have been added with another device file.
[  1080.273] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event9)
[  1080.273] (II) No input driver specified, ignoring this device.
[  1080.273] (II) This device may have been added with another device file.
[  1080.273] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1080.273] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1080.273] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1080.273] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1080.273] (**) AT Translated Set 2 keyboard: always reports core events
[  1080.273] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1080.273] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1080.273] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1080.273] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1080.273] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1080.273] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[  1080.273] (**) Option "xkb_rules" "evdev"
[  1080.273] (**) Option "xkb_model" "pc105"
[  1080.273] (**) Option "xkb_layout" "es"
[  1080.376] (II) evdev: Power Button: Close
[  1080.376] (II) UnloadModule: "evdev"
[  1080.376] (II) Unloading evdev
[  1080.436] (II) evdev: Power Button: Close
[  1080.436] (II) UnloadModule: "evdev"
[  1080.436] (II) Unloading evdev
[  1080.445] (II) evdev: Logitech USB Receiver: Close
[  1080.445] (II) UnloadModule: "evdev"
[  1080.445] (II) Unloading evdev
[  1080.448] (II) evdev: AT Translated Set 2 keyboard: Close
[  1080.448] (II) UnloadModule: "evdev"
[  1080.448] (II) Unloading evdev
[  1080.454]  ddxSigGiveUp: Closing log
[  1080.454] Server terminated successfully (0). Closing log file.

```

Thanks so much for any help!

[/B]

---

### Post by NikTh on 2012-10-21
Hi , 

I cannot see something weird in your dmesg and Xorg seems clean , except this message about fglrx module. 

> ```
[  1080.056] (WW) Warning, couldn't open module fglrx
```but this means nothing , probably . If you not use the fglrx module (AMD/ATI restricted driver) , this message simply means that this module not exists in your system.. and its OK.

I've searched and found this : [Ubuntu 11.10 not booting: “Could not write bytes: broken pipes” ]("http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes")

take a look maybe helps you. 

If not , we are here :) 
I will give you some commands and we will perform some tests in the filesystem and your HDD and we will see. 
Thanks
[]("http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes")

---

### Post by vallvi on 2012-10-21
Thanks,

In case this has something to do with it: I've an ATI Radeon (HD4350 512MB) card, and when I try to install the proprietary driver from the system settings menu, the system tells me that it cannot be activated and asks me to look at the /var/log/jokey.log. So I don't have that driver activated.

I copied the jockey log below. 

If this continues (the crashes) would a fresh install of Ubuntu help? Or is it a hardware compatibility issue?

```

2012-10-21 10:11:08,660 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c>
2012-10-21 10:11:10,689 DEBUG: reading modalias file /lib/modules/3.2.0-32-generic-pae/modules.alias
2012-10-21 10:11:10,824 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-10-21 10:11:10,839 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-10-21 10:11:10,897 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-10-21 10:11:10,972 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-10-21 10:11:10,972 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-10-21 10:11:10,973 DEBUG: cdv.available: falling back to default
2012-10-21 10:11:11,109 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-10-21 10:11:11,109 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-10-21 10:11:11,125 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-10-21 10:11:11,149 DEBUG: Software modem not available
2012-10-21 10:11:11,149 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-10-21 10:11:11,167 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-10-21 10:11:11,167 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-10-21 10:11:11,190 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-10-21 10:11:11,190 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-10-21 10:11:11,196 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-10-21 10:11:11,200 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-10-21 10:11:11,225 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-10-21 10:11:11,225 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-10-21 10:11:11,249 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-10-21 10:11:11,253 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-10-21 10:11:11,254 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,269 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:11:11,269 DEBUG: NVIDIA accelerated graphics driver not available
2012-10-21 10:11:11,272 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-10-21 10:11:11,276 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-10-21 10:11:11,277 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,309 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:11:11,313 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-10-21 10:11:11,316 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-10-21 10:11:11,317 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,353 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:11:11,357 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-10-21 10:11:11,361 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-10-21 10:11:11,362 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,376 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:11:11,377 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-10-21 10:11:11,380 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-10-21 10:11:11,383 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-10-21 10:11:11,384 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,417 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:11:11,420 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-10-21 10:11:11,424 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-10-21 10:11:11,425 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,458 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:11:11,461 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2012-10-21 10:11:11,479 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2012-10-21 10:11:11,480 DEBUG: nvidia.available: falling back to default
2012-10-21 10:11:11,495 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2012-10-21 10:11:11,495 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-10-21 10:11:11,551 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-10-21 10:11:11,551 DEBUG: Firmware for DVB cards not available
2012-10-21 10:11:11,552 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-10-21 10:11:11,557 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-10-21 10:11:11,561 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-10-21 10:11:11,562 DEBUG: fglrx.available: falling back to default
2012-10-21 10:11:11,595 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:11:11,598 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-10-21 10:11:11,602 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-10-21 10:11:11,602 DEBUG: fglrx.available: falling back to default
2012-10-21 10:11:11,635 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-10-21 10:11:11,635 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-10-21 10:11:11,639 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-10-21 10:11:11,656 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-10-21 10:11:11,656 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-10-21 10:11:11,656 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-10-21 10:11:11,661 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-10-21 10:11:11,661 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-10-21 10:11:11,661 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-10-21 10:11:11,661 DEBUG: all custom handlers loaded
2012-10-21 10:11:11,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:11:11,956 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:11:12,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:11:12,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:11:12,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:11:12,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:11:12,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-10-21 10:11:12,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:11:12,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:11:12,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:11:12,328 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2012-10-21 10:11:12,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:11:12,328 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:11:12,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:11:12,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:11:12,345 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-10-21 10:11:12,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:11:12,345 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,345 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:11:12,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:11:12,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:11:12,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:11:12,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:11:12,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:11:12,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:11:12,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:11:12,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:11:12,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:11:12,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-10-21 10:11:12,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-10-21 10:11:12,420 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,420 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:11:12,356 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:11:12,423 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-10-21 10:11:12,427 DEBUG: fglrx.available: falling back to default
2012-10-21 10:11:12,455 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,455 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:11:12,444 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:11:12,456 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-10-21 10:11:12,467 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,467 DEBUG: fglrx is not the alternative in use
2012-10-21 10:11:12,456 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:11:12,471 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-10-21 10:11:12,474 DEBUG: fglrx.available: falling back to default
2012-10-21 10:11:12,503 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,503 DEBUG: fglrx is not the alternative in use
2012-10-21 10:11:12,491 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:11:12,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:11:12,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:11:12,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:11:12,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:11:12,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb'}
2012-10-21 10:11:12,519 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:11:12,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:11:12,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:11:12,525 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:11:12,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:11:12,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:11:12,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:11:12,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:11:12,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:11:12,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:11:12,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:11:12,570 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:11:12,570 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,570 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-10-21 10:11:12,570 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:11:12,571 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:11:12,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:11:12,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:11:12,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:11:12,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:11:12,575 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-10-21 10:11:12,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:11:12,583 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:11:12,583 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:11:12,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:11:12,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,584 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:11:12,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:11:12,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:11:12,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:11:12,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-10-21 10:11:12,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:11:12,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-10-21 10:11:12,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-10-21 10:11:12,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:11:12,612 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-10-21 10:11:12,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,612 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-10-21 10:11:12,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,612 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:11:12,615 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:11:12,615 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:11:12,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f86a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:11:12,615 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:11:12,615 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,616 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:11:12,617 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,618 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:11:12,619 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x921f5ec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:11:12,647 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,647 DEBUG: fglrx is not the alternative in use
2012-10-21 10:11:12,714 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,714 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:11:12,738 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,738 DEBUG: fglrx is not the alternative in use
2012-10-21 10:11:12,770 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,770 DEBUG: fglrx is not the alternative in use
2012-10-21 10:11:12,791 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:12,791 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:11:41,609 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-10-21 10:11:41,609 DEBUG: fglrx is not the alternative in use
2012-10-21 10:11:45,758 DEBUG: Installing package: fglrx
2012-10-21 10:11:46,183 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-10-21 10:11:46,184 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-10-21 10:11:46,265 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-10-21 10:11:46,325 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.000000
2012-10-21 10:11:46,411 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.002592
2012-10-21 10:11:46,912 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.114574
2012-10-21 10:11:47,089 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.161448
2012-10-21 10:11:47,089 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.161961
2012-10-21 10:11:47,590 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.293140
2012-10-21 10:11:47,834 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.355736
2012-10-21 10:11:47,834 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.356514
2012-10-21 10:11:48,335 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.487693
2012-10-21 10:11:48,836 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.526087
2012-10-21 10:11:49,336 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.567680
2012-10-21 10:11:49,837 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.567680
2012-10-21 10:11:50,338 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.766049
2012-10-21 10:11:50,839 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 0.897228
2012-10-21 10:11:51,340 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.028407
2012-10-21 10:11:51,840 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.095596
2012-10-21 10:11:52,341 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.181983
2012-10-21 10:11:52,842 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.287566
2012-10-21 10:11:53,343 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.287566
2012-10-21 10:11:53,844 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.578720
2012-10-21 10:11:54,345 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.700301
2012-10-21 10:11:54,845 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.818682
2012-10-21 10:11:55,346 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 1.940263
2012-10-21 10:11:55,847 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.071442
2012-10-21 10:11:56,348 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.202621
2012-10-21 10:11:56,849 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.330601
2012-10-21 10:11:57,350 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.407388
2012-10-21 10:11:57,850 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.573762
2012-10-21 10:11:58,351 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.704941
2012-10-21 10:11:58,852 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.836121
2012-10-21 10:11:59,353 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 2.967300
2012-10-21 10:11:59,854 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.098479
2012-10-21 10:12:00,355 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.229658
2012-10-21 10:12:00,855 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.360837
2012-10-21 10:12:01,356 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.389633
2012-10-21 10:12:01,857 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.389633
2012-10-21 10:12:02,358 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.389633
2012-10-21 10:12:02,859 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.389633
2012-10-21 10:12:03,359 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.389633
2012-10-21 10:12:03,860 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.389633
2012-10-21 10:12:04,361 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.469620
2012-10-21 10:12:04,862 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.600799
2012-10-21 10:12:05,363 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.731978
2012-10-21 10:12:05,864 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.863158
2012-10-21 10:12:06,364 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 3.994337
2012-10-21 10:12:06,865 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.125516
2012-10-21 10:12:07,366 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.231099
2012-10-21 10:12:07,867 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.231099
2012-10-21 10:12:08,368 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.375077
2012-10-21 10:12:08,868 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.535051
2012-10-21 10:12:09,369 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.666230
2012-10-21 10:12:09,870 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.797410
2012-10-21 10:12:10,371 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.899793
2012-10-21 10:12:10,872 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 4.899793
2012-10-21 10:12:11,373 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.162152
2012-10-21 10:12:11,873 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.293331
2012-10-21 10:12:12,374 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.424510
2012-10-21 10:12:12,875 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.555689
2012-10-21 10:12:13,376 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.686869
2012-10-21 10:12:13,877 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.818048
2012-10-21 10:12:14,377 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 5.949227
2012-10-21 10:12:14,878 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.080406
2012-10-21 10:12:15,379 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.211585
2012-10-21 10:12:15,880 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.342765
2012-10-21 10:12:16,381 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.473944
2012-10-21 10:12:16,882 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.605123
2012-10-21 10:12:17,382 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.736302
2012-10-21 10:12:17,883 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.867481
2012-10-21 10:12:18,384 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 6.998661
2012-10-21 10:12:18,885 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.129840
2012-10-21 10:12:19,386 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.261019
2012-10-21 10:12:19,887 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.392198
2012-10-21 10:12:20,387 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.523377
2012-10-21 10:12:20,888 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.654557
2012-10-21 10:12:21,389 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.785736
2012-10-21 10:12:21,890 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 7.916915
2012-10-21 10:12:22,391 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.048094
2012-10-21 10:12:22,892 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.179273
2012-10-21 10:12:23,392 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.310453
2012-10-21 10:12:23,893 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.441632
2012-10-21 10:12:24,394 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.572811
2012-10-21 10:12:24,895 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.703990
2012-10-21 10:12:25,396 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.835169
2012-10-21 10:12:25,896 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 8.966349
2012-10-21 10:12:26,397 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.097528
2012-10-21 10:12:26,898 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.228707
2012-10-21 10:12:27,399 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.359886
2012-10-21 10:12:27,900 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.491065
2012-10-21 10:12:28,401 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.622245
2012-10-21 10:12:28,901 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.753424
2012-10-21 10:12:29,402 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.884603
2012-10-21 10:12:29,903 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.996585
2012-10-21 10:12:30,404 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.996585
2012-10-21 10:12:30,905 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.996585
2012-10-21 10:12:31,405 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.996585
2012-10-21 10:12:31,906 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.996585
2012-10-21 10:12:32,407 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 9.996585
2012-10-21 10:12:32,908 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.089371
2012-10-21 10:12:33,409 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.220550
2012-10-21 10:12:33,910 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.351729
2012-10-21 10:12:34,410 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.482908
2012-10-21 10:12:34,911 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.540499
2012-10-21 10:12:35,412 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.585292
2012-10-21 10:12:35,913 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.748466
2012-10-21 10:12:36,414 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 10.902042
2012-10-21 10:12:36,914 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.033221
2012-10-21 10:12:37,415 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.154802
2012-10-21 10:12:37,916 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.154802
2012-10-21 10:12:38,417 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.365968
2012-10-21 10:12:38,918 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.497147
2012-10-21 10:12:39,419 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.628327
2012-10-21 10:12:39,919 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.759506
2012-10-21 10:12:40,420 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 11.890685
2012-10-21 10:12:40,921 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.021864
2012-10-21 10:12:41,422 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.153043
2012-10-21 10:12:41,923 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.284223
2012-10-21 10:12:42,424 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.415402
2012-10-21 10:12:42,924 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.546581
2012-10-21 10:12:43,425 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.677760
2012-10-21 10:12:43,926 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.808939
2012-10-21 10:12:44,427 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 12.940119
2012-10-21 10:12:44,928 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.071298
2012-10-21 10:12:45,428 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.202477
2012-10-21 10:12:45,929 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.333656
2012-10-21 10:12:46,430 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.464835
2012-10-21 10:12:46,931 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.596015
2012-10-21 10:12:47,432 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.727194
2012-10-21 10:12:47,933 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.858373
2012-10-21 10:12:48,433 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 13.989552
2012-10-21 10:12:48,934 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.120731
2012-10-21 10:12:49,435 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.251911
2012-10-21 10:12:49,936 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.383090
2012-10-21 10:12:50,437 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.514269
2012-10-21 10:12:50,938 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.645448
2012-10-21 10:12:51,438 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.776627
2012-10-21 10:12:51,939 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 14.907807
2012-10-21 10:12:52,440 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.038986
2012-10-21 10:12:52,941 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.170165
2012-10-21 10:12:53,442 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.301344
2012-10-21 10:12:53,947 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.435723
2012-10-21 10:12:54,448 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.566902
2012-10-21 10:12:54,949 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.698081
2012-10-21 10:12:55,450 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.829261
2012-10-21 10:12:55,950 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 15.960440
2012-10-21 10:12:56,451 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.088419
2012-10-21 10:12:56,952 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.222798
2012-10-21 10:12:57,453 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.318783
2012-10-21 10:12:57,954 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.361472
2012-10-21 10:12:58,455 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.616336
2012-10-21 10:12:58,955 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.747515
2012-10-21 10:12:59,456 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 16.878694
2012-10-21 10:12:59,957 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.009873
2012-10-21 10:13:00,458 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.141053
2012-10-21 10:13:00,959 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.272232
2012-10-21 10:13:01,459 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.403411
2012-10-21 10:13:01,960 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.534590
2012-10-21 10:13:02,461 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.665769
2012-10-21 10:13:02,962 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.796949
2012-10-21 10:13:03,463 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 17.928128
2012-10-21 10:13:03,964 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.059307
2012-10-21 10:13:04,464 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.190486
2012-10-21 10:13:04,965 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.321665
2012-10-21 10:13:05,466 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.452845
2012-10-21 10:13:05,967 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.584024
2012-10-21 10:13:06,468 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.715203
2012-10-21 10:13:06,968 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.846382
2012-10-21 10:13:07,469 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 18.977561
2012-10-21 10:13:07,970 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.108741
2012-10-21 10:13:08,471 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.239920
2012-10-21 10:13:08,971 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.371099
2012-10-21 10:13:09,472 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.502278
2012-10-21 10:13:09,973 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.633457
2012-10-21 10:13:10,474 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.764637
2012-10-21 10:13:10,975 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 19.895816
2012-10-21 10:13:11,476 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.026995
2012-10-21 10:13:11,977 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.158174
2012-10-21 10:13:12,477 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.289353
2012-10-21 10:13:12,978 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.420533
2012-10-21 10:13:13,479 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.551712
2012-10-21 10:13:13,980 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.682891
2012-10-21 10:13:14,481 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.814070
2012-10-21 10:13:14,982 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 20.945249
2012-10-21 10:13:15,483 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.076429
2012-10-21 10:13:15,983 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.207608
2012-10-21 10:13:16,484 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.338787
2012-10-21 10:13:16,985 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.469966
2012-10-21 10:13:17,486 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.601145
2012-10-21 10:13:17,987 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.732325
2012-10-21 10:13:18,488 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.863504
2012-10-21 10:13:18,989 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 21.994683
2012-10-21 10:13:19,489 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.125862
2012-10-21 10:13:19,990 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.257042
2012-10-21 10:13:20,491 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.388221
2012-10-21 10:13:20,992 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.519400
2012-10-21 10:13:21,493 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.650579
2012-10-21 10:13:21,994 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.781758
2012-10-21 10:13:22,495 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 22.912938
2012-10-21 10:13:22,995 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.044117
2012-10-21 10:13:23,496 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.175296
2012-10-21 10:13:23,997 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.306475
2012-10-21 10:13:24,498 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.437654
2012-10-21 10:13:24,999 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.568834
2012-10-21 10:13:25,500 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.700013
2012-10-21 10:13:26,001 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.831192
2012-10-21 10:13:26,501 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 23.962371
2012-10-21 10:13:27,002 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.093550
2012-10-21 10:13:27,503 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.224730
2012-10-21 10:13:28,004 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.355909
2012-10-21 10:13:28,505 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.487088
2012-10-21 10:13:29,006 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.573474
2012-10-21 10:13:29,507 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.579873
2012-10-21 10:13:30,008 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.851830
2012-10-21 10:13:30,508 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 24.983009
2012-10-21 10:13:31,009 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.114189
2012-10-21 10:13:31,510 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.248567
2012-10-21 10:13:32,011 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.379746
2012-10-21 10:13:32,512 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.510926
2012-10-21 10:13:33,013 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.642105
2012-10-21 10:13:33,514 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.773284
2012-10-21 10:13:34,014 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 25.904463
2012-10-21 10:13:34,515 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.035642
2012-10-21 10:13:35,016 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.166822
2012-10-21 10:13:35,517 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.298001
2012-10-21 10:13:36,018 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.429180
2012-10-21 10:13:36,519 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.560359
2012-10-21 10:13:37,020 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.691538
2012-10-21 10:13:37,520 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.822718
2012-10-21 10:13:38,021 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 26.953897
2012-10-21 10:13:38,522 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.085076
2012-10-21 10:13:39,023 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.216255
2012-10-21 10:13:39,524 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.347434
2012-10-21 10:13:40,025 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.478614
2012-10-21 10:13:40,526 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.609793
2012-10-21 10:13:41,026 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.740972
2012-10-21 10:13:41,527 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 27.872151
2012-10-21 10:13:42,028 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.003330
2012-10-21 10:13:42,529 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.134510
2012-10-21 10:13:43,030 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.265689
2012-10-21 10:13:43,531 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.396868
2012-10-21 10:13:44,032 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.528047
2012-10-21 10:13:44,532 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.659226
2012-10-21 10:13:45,033 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.790406
2012-10-21 10:13:45,534 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 28.921585
2012-10-21 10:13:46,035 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.052764
2012-10-21 10:13:46,536 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.183943
2012-10-21 10:13:47,037 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.315123
2012-10-21 10:13:47,538 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.446302
2012-10-21 10:13:48,038 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.577481
2012-10-21 10:13:48,539 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.708660
2012-10-21 10:13:49,040 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.839839
2012-10-21 10:13:49,541 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 29.971019
2012-10-21 10:13:50,042 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.102198
2012-10-21 10:13:50,543 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.233377
2012-10-21 10:13:51,044 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.364556
2012-10-21 10:13:51,545 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.495735
2012-10-21 10:13:52,045 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.626915
2012-10-21 10:13:52,546 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.758094
2012-10-21 10:13:53,047 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 30.780490
2012-10-21 10:13:53,548 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.004455
2012-10-21 10:13:54,049 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.135634
2012-10-21 10:13:54,550 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.266813
2012-10-21 10:13:55,051 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.397992
2012-10-21 10:13:55,551 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.529171
2012-10-21 10:13:56,052 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.660351
2012-10-21 10:13:56,553 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.791530
2012-10-21 10:13:57,054 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 31.922709
2012-10-21 10:13:57,555 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.053888
2012-10-21 10:13:58,056 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.185067
2012-10-21 10:13:58,557 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.316247
2012-10-21 10:13:59,057 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.447426
2012-10-21 10:13:59,558 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.578605
2012-10-21 10:14:00,059 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.709784
2012-10-21 10:14:00,560 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.840964
2012-10-21 10:14:01,061 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 32.972143
2012-10-21 10:14:01,562 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.103322
2012-10-21 10:14:02,063 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.234501
2012-10-21 10:14:02,563 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.368880
2012-10-21 10:14:03,064 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.500059
2012-10-21 10:14:03,565 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.631238
2012-10-21 10:14:04,066 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.762417
2012-10-21 10:14:04,567 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 33.893597
2012-10-21 10:14:05,068 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.021576
2012-10-21 10:14:05,569 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.152756
2012-10-21 10:14:06,069 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.283935
2012-10-21 10:14:06,570 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.415114
2012-10-21 10:14:07,071 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.546293
2012-10-21 10:14:07,572 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.677472
2012-10-21 10:14:08,073 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.811851
2012-10-21 10:14:08,574 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 34.943030
2012-10-21 10:14:09,075 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.074209
2012-10-21 10:14:09,576 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.205389
2012-10-21 10:14:10,076 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.336568
2012-10-21 10:14:10,577 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.467747
2012-10-21 10:14:11,078 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.598926
2012-10-21 10:14:11,579 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.730105
2012-10-21 10:14:12,080 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.861285
2012-10-21 10:14:12,581 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 35.992464
2012-10-21 10:14:13,082 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.123643
2012-10-21 10:14:13,582 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.254822
2012-10-21 10:14:14,083 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.386001
2012-10-21 10:14:14,584 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.517181
2012-10-21 10:14:15,085 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.648360
2012-10-21 10:14:15,586 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.779539
2012-10-21 10:14:16,087 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 36.910718
2012-10-21 10:14:16,588 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.006703
2012-10-21 10:14:17,088 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.006703
2012-10-21 10:14:17,589 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.288258
2012-10-21 10:14:18,090 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.419438
2012-10-21 10:14:18,591 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.550617
2012-10-21 10:14:19,092 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.681796
2012-10-21 10:14:19,593 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.812975
2012-10-21 10:14:20,094 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 37.944154
2012-10-21 10:14:20,594 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.075334
2012-10-21 10:14:21,095 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.206513
2012-10-21 10:14:21,596 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.337692
2012-10-21 10:14:22,097 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.468871
2012-10-21 10:14:22,598 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.600050
2012-10-21 10:14:23,099 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.731230
2012-10-21 10:14:23,600 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.862409
2012-10-21 10:14:24,100 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 38.993588
2012-10-21 10:14:24,601 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.124767
2012-10-21 10:14:25,102 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.255946
2012-10-21 10:14:25,603 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.387126
2012-10-21 10:14:26,104 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.518305
2012-10-21 10:14:26,605 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.649484
2012-10-21 10:14:27,106 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.780663
2012-10-21 10:14:27,606 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 39.911842
2012-10-21 10:14:28,107 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.043022
2012-10-21 10:14:28,608 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.174201
2012-10-21 10:14:29,109 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.305380
2012-10-21 10:14:29,610 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.423761
2012-10-21 10:14:30,111 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.423761
2012-10-21 10:14:30,612 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.590135
2012-10-21 10:14:31,113 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.612531
2012-10-21 10:14:31,613 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.612531
2012-10-21 10:14:32,114 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.612531
2012-10-21 10:14:32,615 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.612531
2012-10-21 10:14:33,116 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.634928
2012-10-21 10:14:33,617 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.772506
2012-10-21 10:14:34,118 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 40.903685
2012-10-21 10:14:34,619 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.034864
2012-10-21 10:14:35,119 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.166044
2012-10-21 10:14:35,620 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.297223
2012-10-21 10:14:36,121 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.428402
2012-10-21 10:14:36,622 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.559581
2012-10-21 10:14:37,123 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.690760
2012-10-21 10:14:37,624 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.821940
2012-10-21 10:14:38,125 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.821940
2012-10-21 10:14:38,625 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 41.901927
2012-10-21 10:14:39,126 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.103495
2012-10-21 10:14:39,627 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.234674
2012-10-21 10:14:40,128 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.365853
2012-10-21 10:14:40,629 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.497033
2012-10-21 10:14:41,130 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.513030
2012-10-21 10:14:41,631 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.516230
2012-10-21 10:14:42,132 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.852176
2012-10-21 10:14:42,632 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 42.983356
2012-10-21 10:14:43,133 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.114535
2012-10-21 10:14:43,634 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.245714
2012-10-21 10:14:44,135 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.376893
2012-10-21 10:14:44,636 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.508072
2012-10-21 10:14:45,137 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.639252
2012-10-21 10:14:45,638 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.770431
2012-10-21 10:14:46,138 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 43.901610
2012-10-21 10:14:46,639 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.032789
2012-10-21 10:14:47,140 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.163968
2012-10-21 10:14:47,641 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.295148
2012-10-21 10:14:48,142 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.426327
2012-10-21 10:14:48,643 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.557506
2012-10-21 10:14:49,144 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.688685
2012-10-21 10:14:49,644 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.819864
2012-10-21 10:14:50,145 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 44.951044
2012-10-21 10:14:50,646 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.082223
2012-10-21 10:14:51,147 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.213402
2012-10-21 10:14:51,648 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.344581
2012-10-21 10:14:52,149 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.475760
2012-10-21 10:14:52,650 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.606940
2012-10-21 10:14:53,150 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.738119
2012-10-21 10:14:53,651 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 45.869298
2012-10-21 10:14:54,152 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.000477
2012-10-21 10:14:54,653 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.131656
2012-10-21 10:14:55,154 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.262836
2012-10-21 10:14:55,655 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.394015
2012-10-21 10:14:56,156 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.525194
2012-10-21 10:14:56,656 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.656373
2012-10-21 10:14:57,157 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.787552
2012-10-21 10:14:57,658 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 46.918732
2012-10-21 10:14:58,159 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.049911
2012-10-21 10:14:58,660 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.181090
2012-10-21 10:14:59,161 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.312269
2012-10-21 10:14:59,662 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.443448
2012-10-21 10:15:00,163 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.574628
2012-10-21 10:15:00,663 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.705807
2012-10-21 10:15:01,164 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.836986
2012-10-21 10:15:01,665 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 47.968165
2012-10-21 10:15:02,166 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.099344
2012-10-21 10:15:02,667 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.230524
2012-10-21 10:15:03,168 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.361703
2012-10-21 10:15:03,669 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.492882
2012-10-21 10:15:04,169 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.627261
2012-10-21 10:15:04,670 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.758440
2012-10-21 10:15:05,171 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 48.889619
2012-10-21 10:15:05,672 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.020798
2012-10-21 10:15:06,173 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.151978
2012-10-21 10:15:06,674 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.283157
2012-10-21 10:15:07,175 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.414336
2012-10-21 10:15:07,675 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.545515
2012-10-21 10:15:08,176 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.676694
2012-10-21 10:15:08,677 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.807874
2012-10-21 10:15:09,178 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 49.939053
2012-10-21 10:15:09,679 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.070232
2012-10-21 10:15:10,180 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.086229
2012-10-21 10:15:10,681 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.089429
2012-10-21 10:15:11,181 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.418977
2012-10-21 10:15:11,682 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.550156
2012-10-21 10:15:12,183 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.681335
2012-10-21 10:15:12,684 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.812514
2012-10-21 10:15:13,185 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 50.943693
2012-10-21 10:15:13,686 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.074873
2012-10-21 10:15:14,186 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.206052
2012-10-21 10:15:14,687 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.337231
2012-10-21 10:15:15,188 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.468410
2012-10-21 10:15:15,689 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.599589
2012-10-21 10:15:16,190 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.730769
2012-10-21 10:15:16,691 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.861948
2012-10-21 10:15:17,192 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 51.993127
2012-10-21 10:15:17,692 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.124306
2012-10-21 10:15:18,193 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.255486
2012-10-21 10:15:18,694 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.386665
2012-10-21 10:15:19,195 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.517844
2012-10-21 10:15:19,696 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.649023
2012-10-21 10:15:20,197 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.780202
2012-10-21 10:15:20,698 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 52.911382
2012-10-21 10:15:21,199 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.042561
2012-10-21 10:15:21,699 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.173740
2012-10-21 10:15:22,200 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.304919
2012-10-21 10:15:22,701 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.436098
2012-10-21 10:15:23,202 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.567278
2012-10-21 10:15:23,703 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.698457
2012-10-21 10:15:24,204 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.829636
2012-10-21 10:15:24,705 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 53.960815
2012-10-21 10:15:25,205 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.091994
2012-10-21 10:15:25,706 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.223174
2012-10-21 10:15:26,207 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.354353
2012-10-21 10:15:26,708 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.485532
2012-10-21 10:15:27,209 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.616711
2012-10-21 10:15:27,710 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.747890
2012-10-21 10:15:28,211 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 54.879070
2012-10-21 10:15:28,711 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.010249
2012-10-21 10:15:29,212 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.141428
2012-10-21 10:15:29,713 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.272607
2012-10-21 10:15:30,214 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.403786
2012-10-21 10:15:30,715 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.534966
2012-10-21 10:15:31,216 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.666145
2012-10-21 10:15:31,717 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.698140
2012-10-21 10:15:32,217 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 55.701339
2012-10-21 10:15:32,718 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.027687
2012-10-21 10:15:33,219 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.158867
2012-10-21 10:15:33,720 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.290046
2012-10-21 10:15:34,221 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.421225
2012-10-21 10:15:34,722 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.552404
2012-10-21 10:15:35,223 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.683583
2012-10-21 10:15:35,723 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.814763
2012-10-21 10:15:36,224 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 56.945942
2012-10-21 10:15:36,725 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.077121
2012-10-21 10:15:37,226 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.208300
2012-10-21 10:15:37,727 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.339479
2012-10-21 10:15:38,228 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.470659
2012-10-21 10:15:38,729 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.601838
2012-10-21 10:15:39,229 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.733017
2012-10-21 10:15:39,730 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.864196
2012-10-21 10:15:40,231 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 57.995375
2012-10-21 10:15:40,732 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.126555
2012-10-21 10:15:41,233 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.257734
2012-10-21 10:15:41,734 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.388913
2012-10-21 10:15:42,235 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.520092
2012-10-21 10:15:42,735 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.651272
2012-10-21 10:15:43,236 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.782451
2012-10-21 10:15:43,737 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 58.913630
2012-10-21 10:15:44,238 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.044809
2012-10-21 10:15:44,739 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.175988
2012-10-21 10:15:45,240 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.307168
2012-10-21 10:15:45,741 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.438347
2012-10-21 10:15:46,241 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.569526
2012-10-21 10:15:46,742 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.700705
2012-10-21 10:15:47,243 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.831884
2012-10-21 10:15:47,744 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 59.963064
2012-10-21 10:15:48,245 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.094243
2012-10-21 10:15:48,746 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.225422
2012-10-21 10:15:49,247 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.356601
2012-10-21 10:15:49,748 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.487780
2012-10-21 10:15:50,248 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.618960
2012-10-21 10:15:50,749 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.750139
2012-10-21 10:15:51,250 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 60.881318
2012-10-21 10:15:51,751 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.012497
2012-10-21 10:15:52,252 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.143676
2012-10-21 10:15:52,753 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.274856
2012-10-21 10:15:53,254 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.406035
2012-10-21 10:15:53,755 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.537214
2012-10-21 10:15:54,255 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.668393
2012-10-21 10:15:54,756 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.799572
2012-10-21 10:15:55,257 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 61.930752
2012-10-21 10:15:55,758 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.061931
2012-10-21 10:15:56,259 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.193110
2012-10-21 10:15:56,760 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.324289
2012-10-21 10:15:57,261 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.455468
2012-10-21 10:15:57,761 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.516259
2012-10-21 10:15:58,262 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.516259
2012-10-21 10:15:58,763 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.781817
2012-10-21 10:15:59,264 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 62.909796
2012-10-21 10:15:59,765 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.040976
2012-10-21 10:16:00,266 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.172155
2012-10-21 10:16:00,767 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.274539
2012-10-21 10:16:01,267 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.274539
2012-10-21 10:16:01,768 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.338528
2012-10-21 10:16:02,269 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.479306
2012-10-21 10:16:02,770 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.629682
2012-10-21 10:16:03,271 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.757662
2012-10-21 10:16:03,772 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.757662
2012-10-21 10:16:04,273 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 63.856846
2012-10-21 10:16:04,773 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.032818
2012-10-21 10:16:05,274 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.163998
2012-10-21 10:16:05,775 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.295177
2012-10-21 10:16:06,276 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.426356
2012-10-21 10:16:06,777 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.503144
2012-10-21 10:16:07,278 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.506343
2012-10-21 10:16:07,779 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.787899
2012-10-21 10:16:08,279 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 64.919078
2012-10-21 10:16:08,780 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.050257
2012-10-21 10:16:09,281 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.181436
2012-10-21 10:16:09,782 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.312615
2012-10-21 10:16:10,283 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.443795
2012-10-21 10:16:10,784 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.574974
2012-10-21 10:16:11,285 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.706153
2012-10-21 10:16:11,785 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.837332
2012-10-21 10:16:12,286 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 65.968511
2012-10-21 10:16:12,787 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.099691
2012-10-21 10:16:13,288 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.230870
2012-10-21 10:16:13,789 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.362049
2012-10-21 10:16:14,290 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.493228
2012-10-21 10:16:14,791 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.624407
2012-10-21 10:16:15,291 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.755587
2012-10-21 10:16:15,792 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 66.886766
2012-10-21 10:16:16,293 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.017945
2012-10-21 10:16:16,794 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.149124
2012-10-21 10:16:17,295 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.280303
2012-10-21 10:16:17,796 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.411483
2012-10-21 10:16:18,297 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.542662
2012-10-21 10:16:18,798 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.673841
2012-10-21 10:16:19,298 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.805020
2012-10-21 10:16:19,799 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 67.936199
2012-10-21 10:16:20,300 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.067379
2012-10-21 10:16:20,801 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.198558
2012-10-21 10:16:21,302 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.329737
2012-10-21 10:16:21,803 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.460916
2012-10-21 10:16:22,304 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.592095
2012-10-21 10:16:22,804 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.723275
2012-10-21 10:16:23,305 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.854454
2012-10-21 10:16:23,806 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 68.985633
2012-10-21 10:16:24,307 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.116812
2012-10-21 10:16:24,808 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.247991
2012-10-21 10:16:25,309 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.379171
2012-10-21 10:16:25,810 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.503951
2012-10-21 10:16:26,310 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.503951
2012-10-21 10:16:26,811 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.769509
2012-10-21 10:16:27,312 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 69.900688
2012-10-21 10:16:27,813 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.031867
2012-10-21 10:16:28,314 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.163046
2012-10-21 10:16:28,815 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.294226
2012-10-21 10:16:29,316 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.425405
2012-10-21 10:16:29,816 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.489395
2012-10-21 10:16:30,317 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.652569
2012-10-21 10:16:30,818 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.662167
2012-10-21 10:16:31,319 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.665367
2012-10-21 10:16:31,820 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.665367
2012-10-21 10:16:32,321 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.665367
2012-10-21 10:16:32,822 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.671766
2012-10-21 10:16:33,322 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.854137
2012-10-21 10:16:33,823 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 70.985316
2012-10-21 10:16:34,324 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.116495
2012-10-21 10:16:34,825 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.247674
2012-10-21 10:16:35,326 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.266871
2012-10-21 10:16:35,827 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.327662
2012-10-21 10:16:36,328 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.510033
2012-10-21 10:16:36,828 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.638013
2012-10-21 10:16:37,329 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.641212
2012-10-21 10:16:37,830 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.647611
2012-10-21 10:16:38,331 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 71.964361
2012-10-21 10:16:38,832 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.095540
2012-10-21 10:16:39,333 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.226719
2012-10-21 10:16:39,834 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.357898
2012-10-21 10:16:40,334 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.489078
2012-10-21 10:16:40,835 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.540270
2012-10-21 10:16:41,336 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.569065
2012-10-21 10:16:41,837 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.719441
2012-10-21 10:16:42,338 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 72.879416
2012-10-21 10:16:42,839 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.010595
2012-10-21 10:16:43,340 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.141774
2012-10-21 10:16:43,840 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.272953
2012-10-21 10:16:44,341 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.282552
2012-10-21 10:16:44,842 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.336943
2012-10-21 10:16:45,343 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.634496
2012-10-21 10:16:45,844 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.765675
2012-10-21 10:16:46,345 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 73.896854
2012-10-21 10:16:46,846 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.028034
2012-10-21 10:16:47,346 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.159213
2012-10-21 10:16:47,847 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.290392
2012-10-21 10:16:48,348 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.421571
2012-10-21 10:16:48,849 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.552750
2012-10-21 10:16:49,350 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.683930
2012-10-21 10:16:49,851 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.815109
2012-10-21 10:16:50,352 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 74.946288
2012-10-21 10:16:50,853 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.077467
2012-10-21 10:16:51,353 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.208646
2012-10-21 10:16:51,854 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.339826
2012-10-21 10:16:52,355 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.471005
2012-10-21 10:16:52,856 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.602184
2012-10-21 10:16:53,357 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.733363
2012-10-21 10:16:53,858 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.864542
2012-10-21 10:16:54,359 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 75.995722
2012-10-21 10:16:54,859 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.126901
2012-10-21 10:16:55,360 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.258080
2012-10-21 10:16:55,861 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.389259
2012-10-21 10:16:56,362 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.520439
2012-10-21 10:16:56,863 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.651618
2012-10-21 10:16:57,364 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.782797
2012-10-21 10:16:57,865 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 76.913976
2012-10-21 10:16:58,365 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.045155
2012-10-21 10:16:58,866 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.176335
2012-10-21 10:16:59,367 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.307514
2012-10-21 10:16:59,868 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.438693
2012-10-21 10:17:00,369 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.569872
2012-10-21 10:17:00,870 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.701051
2012-10-21 10:17:01,371 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.832231
2012-10-21 10:17:01,871 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 77.963410
2012-10-21 10:17:02,372 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.094589
2012-10-21 10:17:02,873 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.225768
2012-10-21 10:17:03,374 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.356947
2012-10-21 10:17:03,875 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.488127
2012-10-21 10:17:04,376 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.619306
2012-10-21 10:17:04,877 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.750485
2012-10-21 10:17:05,378 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 78.881664
2012-10-21 10:17:05,878 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.012843
2012-10-21 10:17:06,379 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.144023
2012-10-21 10:17:06,880 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.275202
2012-10-21 10:17:07,381 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.406381
2012-10-21 10:17:07,882 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.537560
2012-10-21 10:17:08,383 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.668739
2012-10-21 10:17:08,884 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.799919
2012-10-21 10:17:09,384 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 79.931098
2012-10-21 10:17:09,885 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.062277
2012-10-21 10:17:10,386 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.193456
2012-10-21 10:17:10,887 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.324635
2012-10-21 10:17:11,388 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.455815
2012-10-21 10:17:11,889 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.586994
2012-10-21 10:17:12,390 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.718173
2012-10-21 10:17:12,891 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.846153
2012-10-21 10:17:13,391 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.846153
2012-10-21 10:17:13,892 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 80.890946
2012-10-21 10:17:14,393 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.201296
2012-10-21 10:17:14,894 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.332476
2012-10-21 10:17:15,395 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.463655
2012-10-21 10:17:15,896 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.594834
2012-10-21 10:17:16,397 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.726013
2012-10-21 10:17:16,897 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.857192
2012-10-21 10:17:17,398 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 81.988372
2012-10-21 10:17:17,899 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.119551
2012-10-21 10:17:18,400 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.250730
2012-10-21 10:17:18,901 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.381909
2012-10-21 10:17:19,402 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.513088
2012-10-21 10:17:19,903 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.644268
2012-10-21 10:17:20,403 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.775447
2012-10-21 10:17:20,904 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 82.906626
2012-10-21 10:17:21,405 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.037805
2012-10-21 10:17:21,906 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.168984
2012-10-21 10:17:22,407 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.300164
2012-10-21 10:17:22,908 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.431343
2012-10-21 10:17:23,409 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.562522
2012-10-21 10:17:23,909 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.693701
2012-10-21 10:17:24,410 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.824880
2012-10-21 10:17:24,911 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 83.956060
2012-10-21 10:17:25,412 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.087239
2012-10-21 10:17:25,913 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.218418
2012-10-21 10:17:26,414 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.349597
2012-10-21 10:17:26,915 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.480776
2012-10-21 10:17:27,415 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.611956
2012-10-21 10:17:27,916 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.743135
2012-10-21 10:17:28,417 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 84.874314
2012-10-21 10:17:28,918 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.005493
2012-10-21 10:17:29,419 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.136672
2012-10-21 10:17:29,920 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.267852
2012-10-21 10:17:30,421 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.399031
2012-10-21 10:17:30,921 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.530210
2012-10-21 10:17:31,422 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.661389
2012-10-21 10:17:31,923 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.792568
2012-10-21 10:17:32,424 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 85.923748
2012-10-21 10:17:32,925 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.054927
2012-10-21 10:17:33,426 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.186106
2012-10-21 10:17:33,927 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.317285
2012-10-21 10:17:34,428 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.448465
2012-10-21 10:17:34,928 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.534851
2012-10-21 10:17:35,429 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.538050
2012-10-21 10:17:35,930 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.826005
2012-10-21 10:17:36,431 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 86.957184
2012-10-21 10:17:36,601 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.001024
2012-10-21 10:17:36,601 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.001365
2012-10-21 10:17:37,102 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.132544
2012-10-21 10:17:37,603 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.263723
2012-10-21 10:17:38,103 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.394902
2012-10-21 10:17:38,604 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.526082
2012-10-21 10:17:39,105 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.657261
2012-10-21 10:17:39,606 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.788440
2012-10-21 10:17:40,107 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 87.919619
2012-10-21 10:17:40,607 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.047599
2012-10-21 10:17:41,108 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.178778
2012-10-21 10:17:41,609 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.309957
2012-10-21 10:17:42,110 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.441136
2012-10-21 10:17:42,611 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.572316
2012-10-21 10:17:43,112 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.706694
2012-10-21 10:17:43,612 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.837874
2012-10-21 10:17:44,113 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 88.969053
2012-10-21 10:17:44,614 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.100232
2012-10-21 10:17:45,115 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.231411
2012-10-21 10:17:45,616 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.362590
2012-10-21 10:17:46,117 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.493770
2012-10-21 10:17:46,617 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.624949
2012-10-21 10:17:47,118 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.756128
2012-10-21 10:17:47,619 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 89.887307
2012-10-21 10:17:48,120 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.018486
2012-10-21 10:17:48,621 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.149666
2012-10-21 10:17:49,122 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.280845
2012-10-21 10:17:49,622 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.412024
2012-10-21 10:17:50,123 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.543203
2012-10-21 10:17:50,624 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.674382
2012-10-21 10:17:51,125 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.805562
2012-10-21 10:17:51,626 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 90.936741
2012-10-21 10:17:52,126 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.067920
2012-10-21 10:17:52,627 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.199099
2012-10-21 10:17:53,128 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.330278
2012-10-21 10:17:53,629 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.461458
2012-10-21 10:17:54,130 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.592637
2012-10-21 10:17:54,631 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.723816
2012-10-21 10:17:55,131 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.854995
2012-10-21 10:17:55,632 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 91.986174
2012-10-21 10:17:56,133 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.117354
2012-10-21 10:17:56,634 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.248533
2012-10-21 10:17:57,134 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.379712
2012-10-21 10:17:57,635 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.510891
2012-10-21 10:17:58,136 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.642070
2012-10-21 10:17:58,637 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.773250
2012-10-21 10:17:59,138 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 92.904429
2012-10-21 10:17:59,638 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.035608
2012-10-21 10:18:00,139 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.166787
2012-10-21 10:18:00,640 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.297966
2012-10-21 10:18:01,141 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.371555
2012-10-21 10:18:01,642 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.374754
2012-10-21 10:18:02,143 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.669108
2012-10-21 10:18:02,643 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.800287
2012-10-21 10:18:03,144 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 93.931466
2012-10-21 10:18:03,645 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.062645
2012-10-21 10:18:04,146 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.193824
2012-10-21 10:18:04,647 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.325004
2012-10-21 10:18:05,147 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.456183
2012-10-21 10:18:05,648 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.587362
2012-10-21 10:18:06,149 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.718541
2012-10-21 10:18:06,650 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.849720
2012-10-21 10:18:07,151 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 94.980900
2012-10-21 10:18:07,652 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.112079
2012-10-21 10:18:08,152 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.243258
2012-10-21 10:18:08,653 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.374437
2012-10-21 10:18:09,154 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.505616
2012-10-21 10:18:09,655 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.636796
2012-10-21 10:18:10,156 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.767975
2012-10-21 10:18:10,656 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 95.899154
2012-10-21 10:18:11,157 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.030333
2012-10-21 10:18:11,658 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.161512
2012-10-21 10:18:12,159 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.292692
2012-10-21 10:18:12,660 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.423871
2012-10-21 10:18:13,161 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.555050
2012-10-21 10:18:13,661 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.686229
2012-10-21 10:18:14,162 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.817408
2012-10-21 10:18:14,663 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 96.948588
2012-10-21 10:18:15,164 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.079767
2012-10-21 10:18:15,665 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.210946
2012-10-21 10:18:16,166 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.342125
2012-10-21 10:18:16,666 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.473304
2012-10-21 10:18:17,167 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.604484
2012-10-21 10:18:17,668 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.735663
2012-10-21 10:18:18,169 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.866842
2012-10-21 10:18:18,670 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 97.998021
2012-10-21 10:18:19,171 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.129200
2012-10-21 10:18:19,671 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.260380
2012-10-21 10:18:20,172 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.330769
2012-10-21 10:18:20,673 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.394758
2012-10-21 10:18:21,174 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.647518
2012-10-21 10:18:21,675 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.778697
2012-10-21 10:18:22,176 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 98.909877
2012-10-21 10:18:22,676 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.041056
2012-10-21 10:18:23,177 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.172235
2012-10-21 10:18:23,678 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.303414
2012-10-21 10:18:24,179 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.434594
2012-10-21 10:18:24,680 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.565773
2012-10-21 10:18:25,180 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.696952
2012-10-21 10:18:25,681 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.828131
2012-10-21 10:18:26,182 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 99.959310
2012-10-21 10:18:26,335 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:6549L> 100.000000
2012-10-21 10:18:27,087 DEBUG: install progress dpkg-exec 0.000000
2012-10-21 10:18:29,212 DEBUG: install progress dkms 0.000000
2012-10-21 10:18:29,213 DEBUG: install progress dkms 5.000000
2012-10-21 10:18:29,765 DEBUG: install progress dkms 10.000000
2012-10-21 10:18:29,832 DEBUG: install progress dkms 15.000000
2012-10-21 10:18:30,111 DEBUG: install progress fakeroot 15.000000
2012-10-21 10:18:30,111 DEBUG: install progress fakeroot 20.000000
2012-10-21 10:18:30,461 DEBUG: install progress fakeroot 25.000000
2012-10-21 10:18:30,534 DEBUG: install progress fakeroot 30.000000
2012-10-21 10:18:30,964 DEBUG: install progress fglrx 30.000000
2012-10-21 10:18:30,964 DEBUG: install progress fglrx 35.000000
2012-10-21 10:18:34,103 DEBUG: install progress fglrx 40.000000
2012-10-21 10:18:34,195 DEBUG: install progress fglrx 45.000000
2012-10-21 10:18:34,399 DEBUG: install progress fglrx-amdcccle 45.000000
2012-10-21 10:18:34,499 DEBUG: install progress fglrx-amdcccle 50.000000
2012-10-21 10:18:34,845 DEBUG: install progress fglrx-amdcccle 55.000000
2012-10-21 10:18:34,927 DEBUG: install progress fglrx-amdcccle 60.000000
2012-10-21 10:18:35,022 DEBUG: install progress man-db 60.000000
2012-10-21 10:18:37,702 DEBUG: install progress ureadahead 60.000000
2012-10-21 10:18:38,020 DEBUG: install progress dpkg-exec 60.000000
2012-10-21 10:18:38,061 DEBUG: install progress dkms 60.000000
2012-10-21 10:18:39,038 DEBUG: install progress dkms 65.000000
2012-10-21 10:18:39,117 DEBUG: install progress dkms 70.000000
2012-10-21 10:18:39,190 DEBUG: install progress fakeroot 70.000000
2012-10-21 10:18:39,257 DEBUG: install progress fakeroot 75.000000
2012-10-21 10:18:39,772 DEBUG: install progress fakeroot 80.000000
2012-10-21 10:18:39,864 DEBUG: install progress fglrx 80.000000
2012-10-21 10:18:40,151 DEBUG: install progress fglrx 85.000000
2012-10-21 10:19:09,314 DEBUG: install progress fglrx 90.000000
2012-10-21 10:19:09,734 DEBUG: install progress bamfdaemon 90.000000
2012-10-21 10:19:09,995 DEBUG: install progress fglrx-amdcccle 90.000000
2012-10-21 10:19:10,095 DEBUG: install progress fglrx-amdcccle 95.000000
2012-10-21 10:19:10,180 DEBUG: install progress fglrx-amdcccle 100.000000
2012-10-21 10:19:10,264 DEBUG: install progress initramfs-tools 100.000000
2012-10-21 10:19:20,113 DEBUG: install progress libc-bin 100.000000
2012-10-21 10:19:21,315 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 243226 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.960-0ubuntu1.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx (2:8.960-0ubuntu1.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-32-generic-pae
Building for architecture i686
Building initial module for 3.2.0-32-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic-pae/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.960-0ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-10-21 10:19:39,311 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,311 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:39,403 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,403 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:39,511 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,512 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:39,603 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,603 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:39,740 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,741 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:19:39,774 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,774 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:39,866 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,866 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:39,979 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:39,979 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:40,071 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:40,071 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:19:40,172 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:19:40,172 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:22:12,165 DEBUG: Shutting down
2012-10-21 10:23:33,904 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c>
2012-10-21 10:23:36,130 DEBUG: reading modalias file /lib/modules/3.2.0-32-generic-pae/modules.alias
2012-10-21 10:23:36,280 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-10-21 10:23:36,295 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-10-21 10:23:36,361 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-10-21 10:23:36,436 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-10-21 10:23:36,436 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-10-21 10:23:36,437 DEBUG: cdv.available: falling back to default
2012-10-21 10:23:36,562 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-10-21 10:23:36,562 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-10-21 10:23:36,576 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-10-21 10:23:36,604 DEBUG: Software modem not available
2012-10-21 10:23:36,605 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-10-21 10:23:36,622 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-10-21 10:23:36,622 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-10-21 10:23:36,637 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-10-21 10:23:36,638 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-10-21 10:23:36,642 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-10-21 10:23:36,646 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-10-21 10:23:36,669 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-10-21 10:23:36,669 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-10-21 10:23:36,688 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-10-21 10:23:36,691 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-10-21 10:23:36,692 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,705 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:23:36,706 DEBUG: NVIDIA accelerated graphics driver not available
2012-10-21 10:23:36,708 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-10-21 10:23:36,712 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-10-21 10:23:36,713 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,742 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:23:36,745 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-10-21 10:23:36,748 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-10-21 10:23:36,749 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,782 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:23:36,785 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-10-21 10:23:36,789 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-10-21 10:23:36,790 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,803 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:23:36,803 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-10-21 10:23:36,806 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-10-21 10:23:36,809 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-10-21 10:23:36,810 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,839 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:23:36,842 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-10-21 10:23:36,846 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-10-21 10:23:36,847 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,876 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:23:36,879 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2012-10-21 10:23:36,895 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2012-10-21 10:23:36,896 DEBUG: nvidia.available: falling back to default
2012-10-21 10:23:36,909 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2012-10-21 10:23:36,909 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-10-21 10:23:36,980 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-10-21 10:23:36,980 DEBUG: Firmware for DVB cards not available
2012-10-21 10:23:36,980 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-10-21 10:23:36,985 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-10-21 10:23:36,989 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-10-21 10:23:36,989 DEBUG: fglrx.available: falling back to default
2012-10-21 10:23:37,018 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:23:37,025 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-10-21 10:23:37,025 DEBUG: fglrx.available: falling back to default
2012-10-21 10:23:37,055 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-10-21 10:23:37,055 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-10-21 10:23:37,059 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-10-21 10:23:37,073 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-10-21 10:23:37,074 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-10-21 10:23:37,074 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-10-21 10:23:37,077 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-10-21 10:23:37,078 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-10-21 10:23:37,078 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-10-21 10:23:37,078 DEBUG: all custom handlers loaded
2012-10-21 10:23:37,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:23:37,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:23:37,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,489 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:23:37,490 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:23:37,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:37,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:23:37,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:23:37,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-10-21 10:23:37,769 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:23:37,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:23:37,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:23:37,772 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2012-10-21 10:23:37,772 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:23:37,772 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:37,772 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:23:37,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:23:37,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:23:37,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-10-21 10:23:37,789 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:23:37,790 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:37,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,790 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:23:37,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:23:37,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:23:37,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:37,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:23:37,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:23:37,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:23:37,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:23:37,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:23:37,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:23:37,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:23:37,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-10-21 10:23:37,801 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:37,801 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-10-21 10:23:37,879 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:37,879 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:37,801 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:23:37,987 DEBUG: fglrx.available: falling back to default
2012-10-21 10:23:38,013 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:38,014 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:38,002 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:23:38,089 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-10-21 10:23:38,101 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:38,101 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:23:38,090 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:23:38,104 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-10-21 10:23:38,107 DEBUG: fglrx.available: falling back to default
2012-10-21 10:23:38,133 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:38,134 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:23:38,122 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:23:38,134 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-10-21 10:23:38,145 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:38,145 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:38,134 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:23:38,225 DEBUG: fglrx.available: falling back to default
2012-10-21 10:23:38,251 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:38,251 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:38,240 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:23:38,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:23:38,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:23:38,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:23:38,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:23:38,340 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb'}
2012-10-21 10:23:38,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:23:38,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:23:38,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:23:38,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:38,346 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:23:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:23:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:23:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:23:38,348 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:23:38,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:23:38,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:23:38,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:38,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:23:38,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:23:38,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-10-21 10:23:38,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:23:38,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:23:38,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:23:38,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:23:38,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:23:38,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:23:38,396 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-10-21 10:23:38,396 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,402 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:23:38,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:23:38,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,405 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:23:38,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:23:38,405 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:38,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,405 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:23:38,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:23:38,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:23:38,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:23:38,424 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-10-21 10:23:38,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:23:38,425 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-10-21 10:23:38,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,425 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-10-21 10:23:38,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:23:38,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-10-21 10:23:38,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-10-21 10:23:38,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:23:38,437 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:23:38,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8bfba0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:23:38,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:23:38,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:23:38,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:23:38,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:23:38,441 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:23:38,441 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:23:38,441 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e9460c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:23:38,511 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:38,511 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:38,958 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:39,144 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:23:39,333 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:39,333 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:39,511 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:39,511 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:23:51,724 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:23:51,724 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:24:02,386 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:24:02,387 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:24:06,011 DEBUG: Installing package: fglrx-updates
2012-10-21 10:24:06,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-10-21 10:24:06,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-10-21 10:24:06,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-10-21 10:24:06,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2012-10-21 10:24:06,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.002590
2012-10-21 10:24:07,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.114973
2012-10-21 10:24:07,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.246623
2012-10-21 10:24:08,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.378272
2012-10-21 10:24:08,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.509921
2012-10-21 10:24:09,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.558085
2012-10-21 10:24:09,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.599828
2012-10-21 10:24:10,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.795696
2012-10-21 10:24:10,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.940189
2012-10-21 10:24:11,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.071838
2012-10-21 10:24:11,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.132846
2012-10-21 10:24:12,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.171378
2012-10-21 10:24:12,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.383301
2012-10-21 10:24:13,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.514950
2012-10-21 10:24:13,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.646599
2012-10-21 10:24:14,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.778248
2012-10-21 10:24:14,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.909898
2012-10-21 10:24:15,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.041547
2012-10-21 10:24:15,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.173196
2012-10-21 10:24:16,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.304845
2012-10-21 10:24:16,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.436494
2012-10-21 10:24:17,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.568143
2012-10-21 10:24:17,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.699793
2012-10-21 10:24:18,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.831442
2012-10-21 10:24:18,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.963091
2012-10-21 10:24:19,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.094740
2012-10-21 10:24:19,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.226389
2012-10-21 10:24:20,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.325929
2012-10-21 10:24:20,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.325929
2012-10-21 10:24:21,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.605282
2012-10-21 10:24:21,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.736931
2012-10-21 10:24:22,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.868580
2012-10-21 10:24:22,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.000230
2012-10-21 10:24:23,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.131879
2012-10-21 10:24:23,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.263528
2012-10-21 10:24:24,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.395177
2012-10-21 10:24:24,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.526826
2012-10-21 10:24:25,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.658475
2012-10-21 10:24:25,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.790125
2012-10-21 10:24:26,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.921774
2012-10-21 10:24:26,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.053423
2012-10-21 10:24:27,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.185072
2012-10-21 10:24:27,890 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.316721
2012-10-21 10:24:28,391 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.448370
2012-10-21 10:24:28,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.580020
2012-10-21 10:24:29,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.711669
2012-10-21 10:24:29,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.843318
2012-10-21 10:24:30,394 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.974967
2012-10-21 10:24:30,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.106616
2012-10-21 10:24:31,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.238265
2012-10-21 10:24:31,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.369915
2012-10-21 10:24:32,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.501564
2012-10-21 10:24:32,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.633213
2012-10-21 10:24:33,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.764862
2012-10-21 10:24:33,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.896511
2012-10-21 10:24:34,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.028161
2012-10-21 10:24:34,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.163021
2012-10-21 10:24:35,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.294670
2012-10-21 10:24:35,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.426319
2012-10-21 10:24:36,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.557968
2012-10-21 10:24:36,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.689617
2012-10-21 10:24:37,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.821267
2012-10-21 10:24:37,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.952916
2012-10-21 10:24:38,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.084565
2012-10-21 10:24:38,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.216214
2012-10-21 10:24:39,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.347863
2012-10-21 10:24:39,911 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.479512
2012-10-21 10:24:40,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.611162
2012-10-21 10:24:40,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.742811
2012-10-21 10:24:41,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.874460
2012-10-21 10:24:41,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.006109
2012-10-21 10:24:42,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.137758
2012-10-21 10:24:42,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.269407
2012-10-21 10:24:43,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.381791
2012-10-21 10:24:43,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.381791
2012-10-21 10:24:44,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.664355
2012-10-21 10:24:44,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.796004
2012-10-21 10:24:45,420 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.927653
2012-10-21 10:24:45,921 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.059302
2012-10-21 10:24:46,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.190952
2012-10-21 10:24:46,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.322601
2012-10-21 10:24:47,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.454250
2012-10-21 10:24:47,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.585899
2012-10-21 10:24:48,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.717548
2012-10-21 10:24:48,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.849197
2012-10-21 10:24:49,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.980847
2012-10-21 10:24:49,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.112496
2012-10-21 10:24:50,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.244145
2012-10-21 10:24:50,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.379005
2012-10-21 10:24:51,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.510654
2012-10-21 10:24:51,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.642303
2012-10-21 10:24:52,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.773953
2012-10-21 10:24:52,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.905602
2012-10-21 10:24:53,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.037251
2012-10-21 10:24:53,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.127158
2012-10-21 10:24:54,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.127158
2012-10-21 10:24:54,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.127158
2012-10-21 10:24:55,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.127158
2012-10-21 10:24:55,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.127158
2012-10-21 10:24:56,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.130369
2012-10-21 10:24:56,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.236330
2012-10-21 10:24:57,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.367979
2012-10-21 10:24:57,941 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.499629
2012-10-21 10:24:58,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.631278
2012-10-21 10:24:58,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.679442
2012-10-21 10:24:59,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.679442
2012-10-21 10:24:59,944 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.788615
2012-10-21 10:25:00,445 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.965217
2012-10-21 10:25:00,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.096866
2012-10-21 10:25:01,447 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.186773
2012-10-21 10:25:01,948 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.186773
2012-10-21 10:25:02,449 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.318422
2012-10-21 10:25:02,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.501447
2012-10-21 10:25:03,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.633096
2012-10-21 10:25:03,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.764745
2012-10-21 10:25:04,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.896394
2012-10-21 10:25:04,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.925293
2012-10-21 10:25:05,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.931715
2012-10-21 10:25:05,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.256021
2012-10-21 10:25:06,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.387670
2012-10-21 10:25:06,956 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.519320
2012-10-21 10:25:07,457 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.650969
2012-10-21 10:25:07,958 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.782618
2012-10-21 10:25:08,459 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.914267
2012-10-21 10:25:08,960 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.045916
2012-10-21 10:25:09,461 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.177565
2012-10-21 10:25:09,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.309215
2012-10-21 10:25:10,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.440864
2012-10-21 10:25:10,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.572513
2012-10-21 10:25:11,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.704162
2012-10-21 10:25:11,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.835811
2012-10-21 10:25:12,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.967460
2012-10-21 10:25:12,966 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.099110
2012-10-21 10:25:13,467 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.230759
2012-10-21 10:25:13,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.362408
2012-10-21 10:25:14,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.494057
2012-10-21 10:25:14,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.625706
2012-10-21 10:25:15,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.757355
2012-10-21 10:25:15,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.889005
2012-10-21 10:25:16,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.020654
2012-10-21 10:25:16,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.155514
2012-10-21 10:25:17,474 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.287163
2012-10-21 10:25:17,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.418812
2012-10-21 10:25:18,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.547250
2012-10-21 10:25:18,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.678900
2012-10-21 10:25:19,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.810549
2012-10-21 10:25:19,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.942198
2012-10-21 10:25:20,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.077058
2012-10-21 10:25:20,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.208707
2012-10-21 10:25:21,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.340356
2012-10-21 10:25:21,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.472006
2012-10-21 10:25:22,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.603655
2012-10-21 10:25:22,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.735304
2012-10-21 10:25:23,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.866953
2012-10-21 10:25:23,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.998602
2012-10-21 10:25:24,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.130252
2012-10-21 10:25:24,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.261901
2012-10-21 10:25:25,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.393550
2012-10-21 10:25:25,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.525199
2012-10-21 10:25:26,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.656848
2012-10-21 10:25:26,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.788497
2012-10-21 10:25:27,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.920147
2012-10-21 10:25:27,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.051796
2012-10-21 10:25:28,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.183445
2012-10-21 10:25:28,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.315094
2012-10-21 10:25:29,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.446743
2012-10-21 10:25:29,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.578392
2012-10-21 10:25:30,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.710042
2012-10-21 10:25:30,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.841691
2012-10-21 10:25:31,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.973340
2012-10-21 10:25:31,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.104989
2012-10-21 10:25:32,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.236638
2012-10-21 10:25:32,999 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.368287
2012-10-21 10:25:33,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.499937
2012-10-21 10:25:34,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.515991
2012-10-21 10:25:34,501 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.519202
2012-10-21 10:25:35,002 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.865986
2012-10-21 10:25:35,503 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.997635
2012-10-21 10:25:36,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.129284
2012-10-21 10:25:36,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.260933
2012-10-21 10:25:37,006 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.392582
2012-10-21 10:25:37,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.527442
2012-10-21 10:25:38,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.659092
2012-10-21 10:25:38,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.790741
2012-10-21 10:25:39,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.922390
2012-10-21 10:25:39,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.054039
2012-10-21 10:25:40,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.185688
2012-10-21 10:25:40,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.317337
2012-10-21 10:25:41,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.448987
2012-10-21 10:25:41,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.580636
2012-10-21 10:25:42,018 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.712285
2012-10-21 10:25:42,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.843934
2012-10-21 10:25:43,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.975583
2012-10-21 10:25:43,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.107232
2012-10-21 10:25:44,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.238882
2012-10-21 10:25:44,522 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.370531
2012-10-21 10:25:45,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.502180
2012-10-21 10:25:45,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.633829
2012-10-21 10:25:46,025 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.765478
2012-10-21 10:25:46,526 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.897127
2012-10-21 10:25:47,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.028777
2012-10-21 10:25:47,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.160426
2012-10-21 10:25:48,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.292075
2012-10-21 10:25:48,529 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.423724
2012-10-21 10:25:49,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.555373
2012-10-21 10:25:49,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.687022
2012-10-21 10:25:50,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.821883
2012-10-21 10:25:50,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.953532
2012-10-21 10:25:51,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.085181
2012-10-21 10:25:51,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.216830
2012-10-21 10:25:52,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.348479
2012-10-21 10:25:52,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.480128
2012-10-21 10:25:53,036 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.611778
2012-10-21 10:25:53,537 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.743427
2012-10-21 10:25:54,038 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.875076
2012-10-21 10:25:54,539 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.006725
2012-10-21 10:25:55,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.138374
2012-10-21 10:25:55,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.164062
2012-10-21 10:25:56,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.170484
2012-10-21 10:25:56,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.517267
2012-10-21 10:25:57,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.648916
2012-10-21 10:25:57,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.780565
2012-10-21 10:25:58,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.912215
2012-10-21 10:25:58,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.043864
2012-10-21 10:25:59,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.175513
2012-10-21 10:25:59,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.307162
2012-10-21 10:26:00,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.438811
2012-10-21 10:26:00,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.570460
2012-10-21 10:26:01,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.705321
2012-10-21 10:26:01,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.836970
2012-10-21 10:26:02,050 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.968619
2012-10-21 10:26:02,551 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.100268
2012-10-21 10:26:03,052 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.231917
2012-10-21 10:26:03,553 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.363566
2012-10-21 10:26:04,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.495216
2012-10-21 10:26:04,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.626865
2012-10-21 10:26:05,055 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.758514
2012-10-21 10:26:05,556 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.890163
2012-10-21 10:26:06,057 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.021812
2012-10-21 10:26:06,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.153461
2012-10-21 10:26:07,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.285111
2012-10-21 10:26:07,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.416760
2012-10-21 10:26:08,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.548409
2012-10-21 10:26:08,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.680058
2012-10-21 10:26:09,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.811707
2012-10-21 10:26:09,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.943357
2012-10-21 10:26:10,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.075006
2012-10-21 10:26:10,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.206655
2012-10-21 10:26:11,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.338304
2012-10-21 10:26:11,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.469953
2012-10-21 10:26:12,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.601602
2012-10-21 10:26:12,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.733252
2012-10-21 10:26:13,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.864901
2012-10-21 10:26:13,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.980495
2012-10-21 10:26:14,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.051136
2012-10-21 10:26:14,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.051136
2012-10-21 10:26:15,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.051136
2012-10-21 10:26:15,573 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.051136
2012-10-21 10:26:16,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.051136
2012-10-21 10:26:16,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.051136
2012-10-21 10:26:17,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.134621
2012-10-21 10:26:17,576 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.266270
2012-10-21 10:26:18,077 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.397919
2012-10-21 10:26:18,578 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.529569
2012-10-21 10:26:19,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.596999
2012-10-21 10:26:19,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.609842
2012-10-21 10:26:20,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.767179
2012-10-21 10:26:20,581 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.921305
2012-10-21 10:26:21,082 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.052954
2012-10-21 10:26:21,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.184603
2012-10-21 10:26:22,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.316253
2012-10-21 10:26:22,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.345151
2012-10-21 10:26:23,085 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.348362
2012-10-21 10:26:23,586 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.666247
2012-10-21 10:26:24,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.797896
2012-10-21 10:26:24,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.932756
2012-10-21 10:26:25,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.064405
2012-10-21 10:26:25,589 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.196054
2012-10-21 10:26:26,089 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.327704
2012-10-21 10:26:26,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.459353
2012-10-21 10:26:27,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.587791
2012-10-21 10:26:27,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.719440
2012-10-21 10:26:28,093 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.851089
2012-10-21 10:26:28,594 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.985949
2012-10-21 10:26:29,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.117599
2012-10-21 10:26:29,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.249248
2012-10-21 10:26:30,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.380897
2012-10-21 10:26:30,597 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.512546
2012-10-21 10:26:31,098 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.644195
2012-10-21 10:26:31,599 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.775844
2012-10-21 10:26:32,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.907494
2012-10-21 10:26:32,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.039143
2012-10-21 10:26:33,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.170792
2012-10-21 10:26:33,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.302441
2012-10-21 10:26:34,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.434090
2012-10-21 10:26:34,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.565739
2012-10-21 10:26:35,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.697389
2012-10-21 10:26:35,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.829038
2012-10-21 10:26:36,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.960687
2012-10-21 10:26:36,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.092336
2012-10-21 10:26:37,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.223985
2012-10-21 10:26:37,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.355635
2012-10-21 10:26:38,109 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.487284
2012-10-21 10:26:38,610 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.618933
2012-10-21 10:26:39,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.750582
2012-10-21 10:26:39,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.882231
2012-10-21 10:26:40,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.013880
2012-10-21 10:26:40,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.145530
2012-10-21 10:26:41,114 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.277179
2012-10-21 10:26:41,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.408828
2012-10-21 10:26:42,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.540477
2012-10-21 10:26:42,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.672126
2012-10-21 10:26:43,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.803775
2012-10-21 10:26:43,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.935425
2012-10-21 10:26:44,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.067074
2012-10-21 10:26:44,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.198723
2012-10-21 10:26:45,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.330372
2012-10-21 10:26:45,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.465232
2012-10-21 10:26:46,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.596881
2012-10-21 10:26:46,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.728531
2012-10-21 10:26:47,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.860180
2012-10-21 10:26:47,625 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.991829
2012-10-21 10:26:48,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.123478
2012-10-21 10:26:48,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.255127
2012-10-21 10:26:49,127 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.386776
2012-10-21 10:26:49,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.518426
2012-10-21 10:26:50,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.650075
2012-10-21 10:26:50,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.781724
2012-10-21 10:26:51,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.913373
2012-10-21 10:26:51,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.926217
2012-10-21 10:26:52,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.929428
2012-10-21 10:26:52,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.266578
2012-10-21 10:26:53,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.398227
2012-10-21 10:26:53,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.529877
2012-10-21 10:26:54,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.661526
2012-10-21 10:26:54,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.793175
2012-10-21 10:26:55,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.924824
2012-10-21 10:26:55,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.056473
2012-10-21 10:26:56,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.188122
2012-10-21 10:26:56,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.319772
2012-10-21 10:26:57,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.451421
2012-10-21 10:26:57,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.583070
2012-10-21 10:26:58,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.714719
2012-10-21 10:26:58,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.846368
2012-10-21 10:26:59,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.978017
2012-10-21 10:26:59,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.112878
2012-10-21 10:27:00,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.244527
2012-10-21 10:27:00,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.376176
2012-10-21 10:27:01,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.507825
2012-10-21 10:27:01,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.639474
2012-10-21 10:27:02,148 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.771123
2012-10-21 10:27:02,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.902773
2012-10-21 10:27:03,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.034422
2012-10-21 10:27:03,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.166071
2012-10-21 10:27:04,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.297720
2012-10-21 10:27:04,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.429369
2012-10-21 10:27:05,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.561018
2012-10-21 10:27:05,654 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.692668
2012-10-21 10:27:06,155 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.824317
2012-10-21 10:27:06,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.955966
2012-10-21 10:27:07,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.087615
2012-10-21 10:27:07,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.219264
2012-10-21 10:27:08,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.350914
2012-10-21 10:27:08,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.482563
2012-10-21 10:27:09,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.614212
2012-10-21 10:27:09,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.745861
2012-10-21 10:27:10,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.877510
2012-10-21 10:27:10,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.009159
2012-10-21 10:27:11,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.140809
2012-10-21 10:27:11,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.272458
2012-10-21 10:27:12,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.404107
2012-10-21 10:27:12,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.497225
2012-10-21 10:27:13,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.561444
2012-10-21 10:27:13,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.564655
2012-10-21 10:27:14,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.905016
2012-10-21 10:27:14,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.036665
2012-10-21 10:27:15,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.165103
2012-10-21 10:27:15,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.296753
2012-10-21 10:27:16,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.428402
2012-10-21 10:27:16,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.560051
2012-10-21 10:27:17,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.694911
2012-10-21 10:27:17,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.826560
2012-10-21 10:27:18,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.958209
2012-10-21 10:27:18,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.089858
2012-10-21 10:27:19,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.221508
2012-10-21 10:27:19,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.353157
2012-10-21 10:27:20,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.484806
2012-10-21 10:27:20,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.616455
2012-10-21 10:27:21,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.748104
2012-10-21 10:27:21,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.879754
2012-10-21 10:27:22,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.011403
2012-10-21 10:27:22,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.143052
2012-10-21 10:27:23,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.274701
2012-10-21 10:27:23,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.406350
2012-10-21 10:27:24,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.537999
2012-10-21 10:27:24,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.669649
2012-10-21 10:27:25,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.801298
2012-10-21 10:27:25,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.932947
2012-10-21 10:27:26,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.064596
2012-10-21 10:27:26,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.196245
2012-10-21 10:27:27,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.327894
2012-10-21 10:27:27,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.459544
2012-10-21 10:27:28,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.591193
2012-10-21 10:27:28,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.722842
2012-10-21 10:27:29,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.854491
2012-10-21 10:27:29,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.986140
2012-10-21 10:27:30,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.117789
2012-10-21 10:27:30,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.249439
2012-10-21 10:27:31,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.381088
2012-10-21 10:27:31,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.512737
2012-10-21 10:27:32,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.644386
2012-10-21 10:27:32,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.776035
2012-10-21 10:27:33,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.907684
2012-10-21 10:27:33,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.039334
2012-10-21 10:27:34,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.170983
2012-10-21 10:27:34,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.305843
2012-10-21 10:27:35,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.437492
2012-10-21 10:27:35,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.569141
2012-10-21 10:27:36,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.700790
2012-10-21 10:27:36,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.832440
2012-10-21 10:27:37,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.964089
2012-10-21 10:27:37,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.095738
2012-10-21 10:27:38,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.227387
2012-10-21 10:27:38,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.359036
2012-10-21 10:27:39,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.371880
2012-10-21 10:27:39,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.375091
2012-10-21 10:27:40,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.721874
2012-10-21 10:27:40,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.853523
2012-10-21 10:27:41,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.985173
2012-10-21 10:27:41,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.116822
2012-10-21 10:27:42,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.248471
2012-10-21 10:27:42,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.380120
2012-10-21 10:27:43,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.511769
2012-10-21 10:27:43,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.643419
2012-10-21 10:27:44,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.775068
2012-10-21 10:27:44,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.906717
2012-10-21 10:27:45,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.038366
2012-10-21 10:27:45,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.170015
2012-10-21 10:27:46,220 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.301664
2012-10-21 10:27:46,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.433314
2012-10-21 10:27:47,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.564963
2012-10-21 10:27:47,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.696612
2012-10-21 10:27:48,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.828261
2012-10-21 10:27:48,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.959910
2012-10-21 10:27:49,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.091559
2012-10-21 10:27:49,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.223209
2012-10-21 10:27:50,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.354858
2012-10-21 10:27:50,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.486507
2012-10-21 10:27:51,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.619274
2012-10-21 10:27:51,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.750923
2012-10-21 10:27:52,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.882572
2012-10-21 10:27:52,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.014221
2012-10-21 10:27:53,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.145870
2012-10-21 10:27:53,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.216511
2012-10-21 10:27:54,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.216511
2012-10-21 10:27:54,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.216511
2012-10-21 10:27:55,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.216511
2012-10-21 10:27:55,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.216511
2012-10-21 10:27:56,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.216511
2012-10-21 10:27:56,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.344950
2012-10-21 10:27:57,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.476599
2012-10-21 10:27:57,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.608248
2012-10-21 10:27:58,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.743108
2012-10-21 10:27:58,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.813749
2012-10-21 10:27:59,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.820171
2012-10-21 10:27:59,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.977508
2012-10-21 10:28:00,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.131634
2012-10-21 10:28:00,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.263283
2012-10-21 10:28:01,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.394932
2012-10-21 10:28:01,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.526581
2012-10-21 10:28:02,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.558691
2012-10-21 10:28:02,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.561902
2012-10-21 10:28:03,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.886208
2012-10-21 10:28:03,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.017857
2012-10-21 10:28:04,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.149507
2012-10-21 10:28:04,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.281156
2012-10-21 10:28:05,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.412805
2012-10-21 10:28:05,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.544454
2012-10-21 10:28:06,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.676103
2012-10-21 10:28:06,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.807752
2012-10-21 10:28:07,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.939402
2012-10-21 10:28:07,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.071051
2012-10-21 10:28:08,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.202700
2012-10-21 10:28:08,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.334349
2012-10-21 10:28:09,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.465998
2012-10-21 10:28:09,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.597648
2012-10-21 10:28:10,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.729297
2012-10-21 10:28:10,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.860946
2012-10-21 10:28:11,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.992595
2012-10-21 10:28:11,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.124244
2012-10-21 10:28:12,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.255893
2012-10-21 10:28:12,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.387543
2012-10-21 10:28:13,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.522403
2012-10-21 10:28:13,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.650841
2012-10-21 10:28:14,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.785701
2012-10-21 10:28:14,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.917350
2012-10-21 10:28:15,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.045788
2012-10-21 10:28:15,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.177438
2012-10-21 10:28:16,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.309087
2012-10-21 10:28:16,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.443947
2012-10-21 10:28:17,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.575596
2012-10-21 10:28:17,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.707245
2012-10-21 10:28:18,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.838894
2012-10-21 10:28:18,772 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.970544
2012-10-21 10:28:19,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.102193
2012-10-21 10:28:19,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.233842
2012-10-21 10:28:20,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.365491
2012-10-21 10:28:20,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.497140
2012-10-21 10:28:21,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.628789
2012-10-21 10:28:21,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.760439
2012-10-21 10:28:22,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.892088
2012-10-21 10:28:22,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.023737
2012-10-21 10:28:23,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.155386
2012-10-21 10:28:23,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.287035
2012-10-21 10:28:24,281 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.418684
2012-10-21 10:28:24,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.550334
2012-10-21 10:28:25,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.681983
2012-10-21 10:28:25,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.813632
2012-10-21 10:28:26,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.945281
2012-10-21 10:28:26,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.076930
2012-10-21 10:28:27,286 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.208579
2012-10-21 10:28:27,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.340229
2012-10-21 10:28:28,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.471878
2012-10-21 10:28:28,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.603527
2012-10-21 10:28:29,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.735176
2012-10-21 10:28:29,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.866825
2012-10-21 10:28:30,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.001685
2012-10-21 10:28:30,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.133335
2012-10-21 10:28:31,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.149389
2012-10-21 10:28:31,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.152600
2012-10-21 10:28:32,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.486540
2012-10-21 10:28:32,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.618189
2012-10-21 10:28:33,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.749838
2012-10-21 10:28:33,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.881487
2012-10-21 10:28:34,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.013136
2012-10-21 10:28:34,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.144786
2012-10-21 10:28:35,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.276435
2012-10-21 10:28:35,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.408084
2012-10-21 10:28:36,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.539733
2012-10-21 10:28:36,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.671382
2012-10-21 10:28:37,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.803031
2012-10-21 10:28:37,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.934681
2012-10-21 10:28:38,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.066330
2012-10-21 10:28:38,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.197979
2012-10-21 10:28:39,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.329628
2012-10-21 10:28:39,807 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.461277
2012-10-21 10:28:40,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.592927
2012-10-21 10:28:40,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.724576
2012-10-21 10:28:41,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.856225
2012-10-21 10:28:41,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.987874
2012-10-21 10:28:42,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.119523
2012-10-21 10:28:42,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.251172
2012-10-21 10:28:43,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.382822
2012-10-21 10:28:43,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.514471
2012-10-21 10:28:44,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.646120
2012-10-21 10:28:44,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.777769
2012-10-21 10:28:45,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.909418
2012-10-21 10:28:45,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.041067
2012-10-21 10:28:46,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.172717
2012-10-21 10:28:46,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.304366
2012-10-21 10:28:47,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.436015
2012-10-21 10:28:47,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.567664
2012-10-21 10:28:48,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.702524
2012-10-21 10:28:48,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.834173
2012-10-21 10:28:49,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.965823
2012-10-21 10:28:49,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.097472
2012-10-21 10:28:50,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.229121
2012-10-21 10:28:50,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.360770
2012-10-21 10:28:51,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.492419
2012-10-21 10:28:51,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.624068
2012-10-21 10:28:52,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.755718
2012-10-21 10:28:52,827 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.845624
2012-10-21 10:28:53,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.845624
2012-10-21 10:28:53,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.131399
2012-10-21 10:28:54,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.263049
2012-10-21 10:28:54,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.394698
2012-10-21 10:28:55,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.526347
2012-10-21 10:28:55,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.657996
2012-10-21 10:28:56,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.789645
2012-10-21 10:28:56,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.921294
2012-10-21 10:28:57,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.052944
2012-10-21 10:28:57,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.184593
2012-10-21 10:28:58,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.316242
2012-10-21 10:28:58,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.447891
2012-10-21 10:28:59,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.579540
2012-10-21 10:28:59,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.711189
2012-10-21 10:29:00,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.842839
2012-10-21 10:29:00,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.974488
2012-10-21 10:29:01,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.109348
2012-10-21 10:29:01,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.240997
2012-10-21 10:29:02,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.372646
2012-10-21 10:29:02,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.504295
2012-10-21 10:29:03,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.635945
2012-10-21 10:29:03,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.767594
2012-10-21 10:29:04,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.899243
2012-10-21 10:29:04,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.030892
2012-10-21 10:29:05,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.162541
2012-10-21 10:29:05,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.294190
2012-10-21 10:29:06,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.425840
2012-10-21 10:29:06,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.557489
2012-10-21 10:29:07,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.689138
2012-10-21 10:29:07,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.820787
2012-10-21 10:29:08,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.952436
2012-10-21 10:29:08,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.084086
2012-10-21 10:29:09,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.215735
2012-10-21 10:29:09,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.347384
2012-10-21 10:29:10,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.479033
2012-10-21 10:29:10,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.610682
2012-10-21 10:29:11,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.742331
2012-10-21 10:29:11,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.873981
2012-10-21 10:29:12,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.005630
2012-10-21 10:29:12,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.137279
2012-10-21 10:29:13,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.268928
2012-10-21 10:29:13,862 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.400577
2012-10-21 10:29:14,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.532226
2012-10-21 10:29:14,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.663876
2012-10-21 10:29:15,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.795525
2012-10-21 10:29:15,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.927174
2012-10-21 10:29:16,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.058823
2012-10-21 10:29:16,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.190472
2012-10-21 10:29:17,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.322121
2012-10-21 10:29:17,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.453771
2012-10-21 10:29:18,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.588631
2012-10-21 10:29:18,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.707436
2012-10-21 10:29:19,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.707436
2012-10-21 10:29:19,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.707436
2012-10-21 10:29:20,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.025321
2012-10-21 10:29:20,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.156970
2012-10-21 10:29:21,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.288619
2012-10-21 10:29:21,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.420268
2012-10-21 10:29:22,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.474854
2012-10-21 10:29:22,877 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.494120
2012-10-21 10:29:23,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.667512
2012-10-21 10:29:23,879 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.821638
2012-10-21 10:29:24,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.953287
2012-10-21 10:29:24,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.084936
2012-10-21 10:29:25,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.216585
2012-10-21 10:29:25,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.219796
2012-10-21 10:29:26,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.255117
2012-10-21 10:29:26,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.573001
2012-10-21 10:29:27,385 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.704650
2012-10-21 10:29:27,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.836300
2012-10-21 10:29:28,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.967949
2012-10-21 10:29:28,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.099598
2012-10-21 10:29:29,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.231247
2012-10-21 10:29:29,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.362896
2012-10-21 10:29:30,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.494545
2012-10-21 10:29:30,890 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.626195
2012-10-21 10:29:31,391 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.757844
2012-10-21 10:29:31,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.889493
2012-10-21 10:29:32,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.021142
2012-10-21 10:29:32,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.152791
2012-10-21 10:29:33,394 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.284440
2012-10-21 10:29:33,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.416090
2012-10-21 10:29:34,396 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.547739
2012-10-21 10:29:34,897 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.679388
2012-10-21 10:29:35,398 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.811037
2012-10-21 10:29:35,899 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.942686
2012-10-21 10:29:36,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.074335
2012-10-21 10:29:36,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.205985
2012-10-21 10:29:37,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.337634
2012-10-21 10:29:37,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.469283
2012-10-21 10:29:38,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.600932
2012-10-21 10:29:38,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.732581
2012-10-21 10:29:39,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.864231
2012-10-21 10:29:39,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.995880
2012-10-21 10:29:40,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.127529
2012-10-21 10:29:40,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.259178
2012-10-21 10:29:41,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.394038
2012-10-21 10:29:41,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.525687
2012-10-21 10:29:42,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.657337
2012-10-21 10:29:42,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.788986
2012-10-21 10:29:43,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.920635
2012-10-21 10:29:43,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.052284
2012-10-21 10:29:44,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.183933
2012-10-21 10:29:44,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.315582
2012-10-21 10:29:45,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.447232
2012-10-21 10:29:45,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.578881
2012-10-21 10:29:46,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.710530
2012-10-21 10:29:46,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.842179
2012-10-21 10:29:47,418 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.973828
2012-10-21 10:29:47,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.105477
2012-10-21 10:29:48,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.237127
2012-10-21 10:29:48,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.368776
2012-10-21 10:29:49,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.500425
2012-10-21 10:29:49,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.632074
2012-10-21 10:29:50,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.763723
2012-10-21 10:29:50,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.895372
2012-10-21 10:29:51,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.957549
2012-10-21 10:29:51,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.958977
2012-10-21 10:29:51,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.090626
2012-10-21 10:29:52,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.222276
2012-10-21 10:29:52,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.353925
2012-10-21 10:29:53,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.485574
2012-10-21 10:29:53,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.575481
2012-10-21 10:29:54,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.646122
2012-10-21 10:29:54,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.646122
2012-10-21 10:29:55,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.646122
2012-10-21 10:29:55,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.646122
2012-10-21 10:29:56,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.646122
2012-10-21 10:29:56,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.687864
2012-10-21 10:29:57,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.819513
2012-10-21 10:29:57,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.951163
2012-10-21 10:29:58,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.082812
2012-10-21 10:29:58,674 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.172718
2012-10-21 10:29:59,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.172718
2012-10-21 10:29:59,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.307579
2012-10-21 10:30:00,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.487392
2012-10-21 10:30:00,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.619041
2012-10-21 10:30:01,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.750690
2012-10-21 10:30:01,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.882340
2012-10-21 10:30:02,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.920871
2012-10-21 10:30:02,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.924082
2012-10-21 10:30:03,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.232334
2012-10-21 10:30:03,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.360772
2012-10-21 10:30:04,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.492421
2012-10-21 10:30:04,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.627281
2012-10-21 10:30:05,185 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.758930
2012-10-21 10:30:05,686 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.890580
2012-10-21 10:30:06,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.022229
2012-10-21 10:30:06,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.153878
2012-10-21 10:30:07,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.285527
2012-10-21 10:30:07,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.417176
2012-10-21 10:30:08,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.548825
2012-10-21 10:30:08,691 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.680475
2012-10-21 10:30:09,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.812124
2012-10-21 10:30:09,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.943773
2012-10-21 10:30:10,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.075422
2012-10-21 10:30:10,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.207071
2012-10-21 10:30:11,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.338720
2012-10-21 10:30:11,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.470370
2012-10-21 10:30:12,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.602019
2012-10-21 10:30:12,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.733668
2012-10-21 10:30:13,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.865317
2012-10-21 10:30:13,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.996966
2012-10-21 10:30:14,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.128616
2012-10-21 10:30:14,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.260265
2012-10-21 10:30:15,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.391914
2012-10-21 10:30:15,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.523563
2012-10-21 10:30:16,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.655212
2012-10-21 10:30:16,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.786861
2012-10-21 10:30:17,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.918511
2012-10-21 10:30:17,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.050160
2012-10-21 10:30:18,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.181809
2012-10-21 10:30:18,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.313458
2012-10-21 10:30:19,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.445107
2012-10-21 10:30:19,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.576756
2012-10-21 10:30:20,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.708406
2012-10-21 10:30:20,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.840055
2012-10-21 10:30:21,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.971704
2012-10-21 10:30:21,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.106564
2012-10-21 10:30:22,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.238213
2012-10-21 10:30:22,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.369862
2012-10-21 10:30:23,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.501512
2012-10-21 10:30:23,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.633161
2012-10-21 10:30:24,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.764810
2012-10-21 10:30:24,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.896459
2012-10-21 10:30:25,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.028108
2012-10-21 10:30:25,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.159757
2012-10-21 10:30:26,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.291407
2012-10-21 10:30:26,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.423056
2012-10-21 10:30:27,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.554705
2012-10-21 10:30:27,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.686354
2012-10-21 10:30:28,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.818003
2012-10-21 10:30:28,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.949652
2012-10-21 10:30:29,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.081302
2012-10-21 10:30:29,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.212951
2012-10-21 10:30:30,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.344600
2012-10-21 10:30:30,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.476249
2012-10-21 10:30:31,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.540468
2012-10-21 10:30:31,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.543679
2012-10-21 10:30:32,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.851931
2012-10-21 10:30:32,730 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.983580
2012-10-21 10:30:33,231 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.112018
2012-10-21 10:30:33,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.243668
2012-10-21 10:30:34,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.375317
2012-10-21 10:30:34,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.506966
2012-10-21 10:30:35,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.641826
2012-10-21 10:30:35,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.773475
2012-10-21 10:30:36,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.905124
2012-10-21 10:30:36,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.036774
2012-10-21 10:30:37,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.168423
2012-10-21 10:30:37,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.300072
2012-10-21 10:30:38,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.431721
2012-10-21 10:30:38,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.563370
2012-10-21 10:30:39,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.695019
2012-10-21 10:30:39,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.826669
2012-10-21 10:30:40,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.958318
2012-10-21 10:30:40,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.089967
2012-10-21 10:30:41,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.221616
2012-10-21 10:30:41,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.353265
2012-10-21 10:30:42,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.484914
2012-10-21 10:30:42,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.616564
2012-10-21 10:30:43,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.748213
2012-10-21 10:30:43,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.879862
2012-10-21 10:30:44,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2012-10-21 10:30:44,995 DEBUG: install progress dpkg-exec 0.000000
2012-10-21 10:30:47,046 DEBUG: install progress fglrx-amdcccle 0.000000
2012-10-21 10:30:47,046 DEBUG: install progress fglrx-amdcccle 6.250000
2012-10-21 10:30:47,125 DEBUG: install progress fglrx-amdcccle 12.500000
2012-10-21 10:30:47,370 DEBUG: install progress fglrx-amdcccle 18.750000
2012-10-21 10:30:47,795 DEBUG: install progress fglrx 18.750000
2012-10-21 10:30:47,896 DEBUG: install progress fglrx 25.000000
2012-10-21 10:31:01,159 DEBUG: install progress fglrx 31.250000
2012-10-21 10:31:01,955 DEBUG: install progress fglrx 37.500000
2012-10-21 10:31:02,057 DEBUG: install progress bamfdaemon 37.500000
2012-10-21 10:31:02,208 DEBUG: install progress ureadahead 37.500000
2012-10-21 10:31:02,302 DEBUG: install progress initramfs-tools 37.500000
2012-10-21 10:31:12,744 DEBUG: install progress libc-bin 37.500000
2012-10-21 10:31:13,111 DEBUG: install progress dpkg-exec 37.500000
2012-10-21 10:31:13,762 DEBUG: install progress fglrx-updates 37.500000
2012-10-21 10:31:13,762 DEBUG: install progress fglrx-updates 43.750000
2012-10-21 10:31:17,025 DEBUG: install progress fglrx-updates 50.000000
2012-10-21 10:31:17,117 DEBUG: install progress fglrx-updates 56.250000
2012-10-21 10:31:17,321 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-10-21 10:31:17,421 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-10-21 10:31:17,909 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-10-21 10:31:18,000 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-10-21 10:31:18,095 DEBUG: install progress ureadahead 75.000000
2012-10-21 10:31:18,416 DEBUG: install progress dpkg-exec 75.000000
2012-10-21 10:31:18,457 DEBUG: install progress fglrx-updates 75.000000
2012-10-21 10:31:18,868 DEBUG: install progress fglrx-updates 81.250000
2012-10-21 10:31:41,758 DEBUG: install progress fglrx-updates 87.500000
2012-10-21 10:31:42,136 DEBUG: install progress bamfdaemon 87.500000
2012-10-21 10:31:42,380 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-10-21 10:31:42,472 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-10-21 10:31:42,549 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-10-21 10:31:42,617 DEBUG: install progress initramfs-tools 100.000000
2012-10-21 10:31:50,976 DEBUG: install progress libc-bin 100.000000
2012-10-21 10:31:52,178 DEBUG: (Reading database ... 243558 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-updates.
(Reading database ... 243317 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.960-0ubuntu1.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-32-generic-pae
Building for architecture i686
Building initial module for 3.2.0-32-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-10-21 10:31:52,538 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-10-21 10:32:09,702 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:32:09,702 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:32:09,716 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:32:09,717 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:03,865 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c>
2012-10-21 10:47:05,582 DEBUG: reading modalias file /lib/modules/3.2.0-32-generic-pae/modules.alias
2012-10-21 10:47:05,684 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-10-21 10:47:05,685 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-10-21 10:47:05,730 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-10-21 10:47:05,735 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-10-21 10:47:05,736 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-10-21 10:47:05,736 DEBUG: cdv.available: falling back to default
2012-10-21 10:47:05,804 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-10-21 10:47:05,804 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-10-21 10:47:05,821 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-10-21 10:47:05,829 DEBUG: Software modem not available
2012-10-21 10:47:05,829 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-10-21 10:47:05,833 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-10-21 10:47:05,833 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-10-21 10:47:05,848 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-10-21 10:47:05,848 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-10-21 10:47:05,853 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-10-21 10:47:05,858 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-10-21 10:47:05,884 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-10-21 10:47:05,884 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-10-21 10:47:05,890 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-10-21 10:47:05,894 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-10-21 10:47:05,895 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:05,910 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:47:05,911 DEBUG: NVIDIA accelerated graphics driver not available
2012-10-21 10:47:05,914 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-10-21 10:47:05,918 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-10-21 10:47:05,919 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:05,952 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:47:05,955 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-10-21 10:47:05,959 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-10-21 10:47:05,960 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:05,996 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:47:06,000 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-10-21 10:47:06,004 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-10-21 10:47:06,005 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:06,020 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:47:06,020 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-10-21 10:47:06,023 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-10-21 10:47:06,028 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-10-21 10:47:06,028 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:06,062 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:47:06,066 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-10-21 10:47:06,070 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-10-21 10:47:06,071 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:06,104 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:47:06,107 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2012-10-21 10:47:06,126 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2012-10-21 10:47:06,127 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:06,142 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2012-10-21 10:47:06,142 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-10-21 10:47:06,164 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-10-21 10:47:06,164 DEBUG: Firmware for DVB cards not available
2012-10-21 10:47:06,164 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-10-21 10:47:06,174 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-10-21 10:47:06,174 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:06,207 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:47:06,211 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-10-21 10:47:06,215 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-10-21 10:47:06,215 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:06,248 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-10-21 10:47:06,249 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-10-21 10:47:06,253 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-10-21 10:47:06,270 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-10-21 10:47:06,270 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-10-21 10:47:06,270 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-10-21 10:47:06,274 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-10-21 10:47:06,274 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-10-21 10:47:06,275 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-10-21 10:47:06,275 DEBUG: all custom handlers loaded
2012-10-21 10:47:06,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:47:06,591 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:06,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:06,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:47:06,662 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:06,662 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,662 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:47:06,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:47:06,937 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-10-21 10:47:06,937 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:47:06,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:47:06,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:47:06,940 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2012-10-21 10:47:06,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:47:06,940 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:06,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:47:06,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:06,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:47:06,957 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-10-21 10:47:06,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:47:06,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:06,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:47:06,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:47:06,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:47:06,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:06,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:47:06,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:47:06,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:47:06,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:47:06,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:47:06,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:47:06,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:47:06,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-10-21 10:47:06,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:06,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-10-21 10:47:06,982 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:06,982 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:06,969 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:06,986 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:07,016 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,017 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:07,003 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:07,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-10-21 10:47:07,030 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,030 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:07,017 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:07,034 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:07,064 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,064 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:07,051 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:07,065 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-10-21 10:47:07,077 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,078 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:07,065 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:47:07,081 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-10-21 10:47:07,085 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:07,115 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,115 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:07,102 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:47:07,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:47:07,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:47:07,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:47:07,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:47:07,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb'}
2012-10-21 10:47:07,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:07,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:47:07,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:47:07,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:07,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:07,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:47:07,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:47:07,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:07,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:47:07,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:47:07,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:47:07,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:47:07,158 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:07,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:47:07,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:47:07,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-10-21 10:47:07,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:07,184 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:47:07,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:47:07,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:47:07,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:07,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:47:07,188 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-10-21 10:47:07,188 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:47:07,197 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:07,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,197 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:07,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:47:07,197 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:07,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,197 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:47:07,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:47:07,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:07,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:47:07,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-10-21 10:47:07,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:47:07,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-10-21 10:47:07,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,218 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-10-21 10:47:07,218 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:47:07,225 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-10-21 10:47:07,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-10-21 10:47:07,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:47:07,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:07,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c9aa0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:47:07,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:47:07,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:47:07,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:07,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:47:07,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:47:07,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:47:07,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:07,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:47:07,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f3360c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:47:07,282 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,282 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:07,387 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,387 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:07,418 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,418 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:07,453 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,454 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:07,553 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:07,553 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:11,806 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:11,806 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:11,909 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:11,909 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:18,246 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:18,246 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:20,686 DEBUG: Shutting down
2012-10-21 10:47:22,708 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c>
2012-10-21 10:47:24,411 DEBUG: reading modalias file /lib/modules/3.2.0-32-generic-pae/modules.alias
2012-10-21 10:47:24,512 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-10-21 10:47:24,512 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-10-21 10:47:24,557 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-10-21 10:47:24,562 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-10-21 10:47:24,562 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-10-21 10:47:24,563 DEBUG: cdv.available: falling back to default
2012-10-21 10:47:24,633 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-10-21 10:47:24,634 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-10-21 10:47:24,650 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-10-21 10:47:24,658 DEBUG: Software modem not available
2012-10-21 10:47:24,658 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-10-21 10:47:24,662 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-10-21 10:47:24,662 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-10-21 10:47:24,677 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-10-21 10:47:24,677 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-10-21 10:47:24,682 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-10-21 10:47:24,686 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-10-21 10:47:24,712 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-10-21 10:47:24,712 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-10-21 10:47:24,718 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-10-21 10:47:24,722 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-10-21 10:47:24,724 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,739 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:47:24,739 DEBUG: NVIDIA accelerated graphics driver not available
2012-10-21 10:47:24,742 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-10-21 10:47:24,746 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-10-21 10:47:24,747 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,780 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:47:24,783 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-10-21 10:47:24,788 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-10-21 10:47:24,789 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,825 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:47:24,829 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-10-21 10:47:24,833 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-10-21 10:47:24,833 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,848 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2012-10-21 10:47:24,848 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-10-21 10:47:24,852 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-10-21 10:47:24,856 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-10-21 10:47:24,857 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,890 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:47:24,893 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-10-21 10:47:24,897 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-10-21 10:47:24,898 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,931 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-10-21 10:47:24,934 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2012-10-21 10:47:24,953 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2012-10-21 10:47:24,954 DEBUG: nvidia.available: falling back to default
2012-10-21 10:47:24,969 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2012-10-21 10:47:24,969 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-10-21 10:47:24,990 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-10-21 10:47:24,991 DEBUG: Firmware for DVB cards not available
2012-10-21 10:47:24,991 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-10-21 10:47:25,001 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-10-21 10:47:25,001 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:25,034 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-10-21 10:47:25,037 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-10-21 10:47:25,041 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-10-21 10:47:25,042 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:25,075 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-10-21 10:47:25,075 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-10-21 10:47:25,079 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-10-21 10:47:25,095 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-10-21 10:47:25,096 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-10-21 10:47:25,096 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-10-21 10:47:25,100 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-10-21 10:47:25,100 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-10-21 10:47:25,100 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-10-21 10:47:25,101 DEBUG: all custom handlers loaded
2012-10-21 10:47:25,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:47:25,416 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:25,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:25,480 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:47:25,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:25,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:47:25,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:47:25,761 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-10-21 10:47:25,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:47:25,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:47:25,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:47:25,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2012-10-21 10:47:25,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:47:25,764 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:25,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:47:25,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:25,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:47:25,781 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-10-21 10:47:25,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:47:25,782 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:25,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,782 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:47:25,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:47:25,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:47:25,783 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:25,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:47:25,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:47:25,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:47:25,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:47:25,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:47:25,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:47:25,789 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:47:25,793 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-10-21 10:47:25,793 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,793 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-10-21 10:47:25,807 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:25,807 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:25,794 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:25,811 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:25,841 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:25,841 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:25,828 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:25,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-10-21 10:47:25,853 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:25,854 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:25,841 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:25,858 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:25,887 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:25,888 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:25,875 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-10-21 10:47:25,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-10-21 10:47:25,900 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:25,900 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:25,888 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:47:25,904 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-10-21 10:47:25,908 DEBUG: fglrx.available: falling back to default
2012-10-21 10:47:25,937 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:25,937 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:25,925 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-10-21 10:47:25,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:47:25,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:25,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:47:25,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:47:25,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:47:25,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb'}
2012-10-21 10:47:25,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt2800usb', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:25,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:47:25,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:47:25,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:25,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:25,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:47:25,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:47:25,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:25,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,962 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:47:25,962 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:25,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:47:25,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:47:25,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:47:25,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:25,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:25,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:47:26,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:47:26,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-10-21 10:47:26,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:26,006 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-10-21 10:47:26,006 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:47:26,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:47:26,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:26,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:47:26,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-10-21 10:47:26,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:47:26,018 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:26,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,019 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-10-21 10:47:26,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:47:26,019 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:26,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,019 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-10-21 10:47:26,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:47:26,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:26,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:47:26,039 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2012-10-21 10:47:26,039 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,039 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:47:26,039 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-10-21 10:47:26,039 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-10-21 10:47:26,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:47:26,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-10-21 10:47:26,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,048 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-10-21 10:47:26,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:47:26,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-10-21 10:47:26,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9568a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv0000174Bsd0000AA38bc04sc03i00')
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001025sd00000250bc01sc06i01')
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001025sd00000250bc06sc01i00')
2012-10-21 10:47:26,051 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d000010CEsv00001025sd00000250bc02sc00i00')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'platform:regulatory')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001025sd00000250bc0Csc05i00')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'platform:eisa')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001025sd00000250bc06sc00i00')
2012-10-21 10:47:26,052 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'wmi:3A73BA9A-C9D0-48DF-95AE-F48DE1FC299C')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00001002d0000954Fsv0000174Bsd0000E990bc03sc00i00')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v07D1p3C09d0101dc00dsc00dp00icFFiscFFipFF')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001025sd00000250bc06sc04i01')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0003v046DpC51Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2012-10-21 10:47:26,053 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'dmi:bvnAMI:bvrP01-A3:bd05/26/2009:svnAcer:pnAspireX3810:pvr:rvnAcer:rnWG43M:rvr:cvnAcer:ct3:cvr:')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc01ip02')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v046DpC51Bd4600dc00dsc00dp00ic03isc00ip00')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:INT0800:')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001025sd00000250bc0Csc03i20')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v058Fp6363d0100dc00dsc00dp00ic08isc06ip50')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001025sd00000250bc04sc03i00')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-10-21 10:47:26,054 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00001106d00003403sv00001025sd00000250bc0Csc00i10')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'platform:pcspkr')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001025sd00000250bc0Csc03i00')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-10-21 10:47:26,055 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x980160c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-10-21 10:47:26,135 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:26,135 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:26,237 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:26,237 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:26,262 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:26,262 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:26,370 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:26,371 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:26,473 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:26,473 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:31,738 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:31,738 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:32,720 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:32,720 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:33,281 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:33,281 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:33,708 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:33,708 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-10-21 10:47:34,086 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-10-21 10:47:34,087 DEBUG: fglrx_updates is not the alternative in use
2012-10-21 10:47:37,934 DEBUG: Shutting down

```

---

### Post by NikTh on 2012-10-22
Did you try this ? 

> **NikTh said:**
> Hi , I've searched and found this : [Ubuntu 11.10 not booting: &#8220;Could not write bytes: broken pipes&#8221; ]("http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes"). 

Maybe the graphics card driver has nothing to do with this problem. 

Try the best answer (marked green) and watch  if this problem appears again. 

Thanks

---

