---
title: "bad IP netmask combination: 192.168.0.100/244.255.255.0"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by Kneegrowplease on 2012-04-24
What are the rules regarding ip's and subnets?:confused:

```
/etc/dhcp/dhcpd.conf line 53: subnet 192.168.0.100 netmask 244.255.255.0: bad subnet number/mask combination.
subnet 192.168.0.100 netmask 244.255.255.0 
```


tried 255.255.255.0 first, that didn't work


my eth0 IP is manually set, my box gets net via wifi...not sure if that matters when setting default gateway in /etc/init.d/dhcpd.conf

---

### Post by Kneegrowplease on 2012-04-24
netmask and get this;


```
bad range, address 192.168.0.110 not in subnet 192.168.0.100 netmask 255.255.255.255
```




GOD I feel dumb sometimes...

---

### Post by anewguy on 2012-04-24
Did you try 255.255.255._0_?

---

### Post by Kneegrowplease on 2012-04-24
```

```> **anewguy said:**
> Did you try 255.255.255._0_?



Yeah, that was the first thing I tried, got all that worked out now. but I get this error. gotta google syslog now...


```
knee@knee-ET1330:~$ sudo /etc/init.d/isc-dhcp-server start
[sudo] password for knee: 
 * Starting ISC DHCP server dhcpd                                                * check syslog for diagnostics.
                                                                         [fail]


```



```
knee@knee-ET1330:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-generic-pae (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 (Ubuntu 3.0.0-17.30-generic-pae 3.0.22)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffc0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffce000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: eMachines ET1330/MCP61PM-GM, BIOS P01-A0 08/13/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 00000001c0000000 aka 7168M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 365f6000 - 372f3000
[    0.000000] ACPI: RSDP 000fb250 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bffc0000 00048 (v01 ACRSYS ACRPRDCT 20090813 MSFT 00000097)
[    0.000000] ACPI: FACP bffc0200 00084 (v01 081309 FACP1645 20090813 MSFT 00000097)
[    0.000000] ACPI: DSDT bffc0620 055BE (v01  1ADKR 1ADKR019 00000019 INTL 20051117)
[    0.000000] ACPI: FACS bffce000 00040
[    0.000000] ACPI: APIC bffc0390 00080 (v01 081309 APIC1645 20090813 MSFT 00000097)
[    0.000000] ACPI: MCFG bffc0410 0003C (v01 081309 OEMMCFG  20090813 MSFT 00000097)
[    0.000000] ACPI: SLIC bffc0450 00176 (v01 ACRSYS ACRPRDCT 20090813 MSFT 00000097)
[    0.000000] ACPI: WDRT bffc05d0 00047 (v01 081309 NV-WDRT  20090813 MSFT 00000097)
[    0.000000] ACPI: OEMB bffce040 00072 (v01 081309 OEMB1645 20090813 MSFT 00000097)
[    0.000000] ACPI: HPET bffca620 00038 (v01 081309 OEMHPET0 20090813 MSFT 00000097)
[    0.000000] ACPI: AWMI bffce0c0 0004E (v01 081309 OEMB1645 20090813 MSFT 00000097)
[    0.000000] ACPI: SSDT bffca660 00458 (v01 A M I  POWERNOW 00000001 AMD  00000001)
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
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffc0
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1572687
[    0.000000] free_area_init_node: node 0, pgdat c17f6500, node_mem_map f2df6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 12553 pages used for memmap
[    0.000000]   HighMem zone: 1331897 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u524288
[    0.000000] pcpu-alloc: s29952 r0 d23296 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1558350
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic-pae root=UUID=d20d028a-25fa-40b7-b370-66ddb07f5f44 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 29359872 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:001c0000)
[    0.000000] Memory: 6180468k/7340032k available (5527k kernel code, 110280k reserved, 2670k data, 720k init, 5377800k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1802000 - 0xc18b6000   ( 720 kB)
[    0.000000]       .data : 0xc1565fbc - 0xc1801880   (2670 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1565fbc   (5527 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2712.679 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5425.35 BogoMIPS (lpj=10850716)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004029] Security Framework initialized
[    0.004045] AppArmor: AppArmor initialized
[    0.004046] Yama: becoming mindful.
[    0.004100] Mount-cache hash table entries: 512
[    0.004217] Initializing cgroup subsys cpuacct
[    0.004222] Initializing cgroup subsys memory
[    0.004230] Initializing cgroup subsys devices
[    0.004232] Initializing cgroup subsys freezer
[    0.004235] Initializing cgroup subsys net_cls
[    0.004237] Initializing cgroup subsys blkio
[    0.004243] Initializing cgroup subsys perf_event
[    0.004268] CPU: Physical Processor ID: 0
[    0.004269] CPU: Processor Core ID: 0
[    0.004273] mce: CPU supports 6 MCE banks
[    0.004282] using AMD E400 aware idle routine
[    0.006051] ACPI: Core revision 20110413
[    0.011905] ftrace: allocating 25676 entries in 51 pages
[    0.016082] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016623] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058503] CPU0: AMD Athlon(tm) II X2 235e Processor stepping 02
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] CPU 1 irqstacks, hard=f74d2000 soft=f74d4000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148008] TSC synchronization [CPU#0 -> CPU#1]:
[    0.148008] Measured 2565633122 cycles TSC warp between CPUs, turning off TSC clock.
[    0.148008] Marking TSC unstable due to check_tsc_sync_source failed
[    0.148018] Brought up 2 CPUs
[    0.148020] Total of 2 processors activated (10849.99 BogoMIPS).
[    0.148507] devtmpfs: initialized
[    0.148507] PM: Registering ACPI NVS region at bffce000 (139264 bytes)
[    0.149523] print_constraints: dummy: 
[    0.149554] Time: 23:40:13  Date: 04/23/12
[    0.149584] NET: Registered protocol family 16
[    0.149667] EISA bus registered
[    0.149672] node 0 link 0: io port [1000, ffffff]
[    0.149675] TOM: 00000000c0000000 aka 3072M
[    0.149678] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.149680] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.149683] node 0 link 0: mmio [a0000, bffff]
[    0.149685] node 0 link 0: mmio [c0000000, fe0bffff] ==> [c0000000, dfffffff] and [f0000000, fe0bffff]
[    0.149689] TOM2: 00000001c0000000 aka 7168M
[    0.149691] bus: [00, 07] on node 0 link 0
[    0.149693] bus: 00 index 0 [io  0x0000-0xffff]
[    0.149593] Trying to unpack rootfs image as initramfs...
[    0.149699] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.149701] bus: 00 index 2 [mem 0xc0000000-0xdfffffff]
[    0.149703] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.149705] bus: 00 index 4 [mem 0x1c0000000-0xfcffffffff]
[    0.149712] Extended Config Space enabled on 1 nodes
[    0.149726] ACPI: bus type pci registered
[    0.149774] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149777] PCI: not using MMCONFIG
[    0.150490] PCI: Using configuration type 1 for base access
[    0.150491] PCI: Using configuration type 1 for extended access
[    0.151159] bio: create slab <bio-0> at 0
[    0.152871] ACPI: EC: Look up EC in DSDT
[    0.154244] ACPI: Executed 1 blocks of module-level executable AML code
[    0.156271] ACPI: Interpreter enabled
[    0.156275] ACPI: (supports S0 S3 S4 S5)
[    0.156289] ACPI: Using IOAPIC for interrupt routing
[    0.156304] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157937] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.157939] PCI: Using MMCONFIG for extended config space
[    0.162907] ACPI: No dock devices found.
[    0.162908] HEST: Table not found.
[    0.162911] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.163047] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.163172] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.163174] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.163177] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.163179] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.163181] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.163183] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.163208] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
[    0.163379] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
[    0.163385] pci 0000:00:01.0: reg 10: [io  0x4f00-0x4fff]
[    0.163419] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
[    0.163429] pci 0000:00:01.1: reg 10: [io  0x4900-0x493f]
[    0.163444] pci 0000:00:01.1: reg 20: [io  0x4d00-0x4d3f]
[    0.163450] pci 0000:00:01.1: reg 24: [io  0x4e00-0x4e3f]
[    0.163477] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.163482] pci 0000:00:01.1: PME# disabled
[    0.163492] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
[    0.163532] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
[    0.163540] pci 0000:00:02.0: reg 10: [mem 0xdbf7f000-0xdbf7ffff]
[    0.163573] pci 0000:00:02.0: supports D1 D2
[    0.163575] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163578] pci 0000:00:02.0: PME# disabled
[    0.163588] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
[    0.163598] pci 0000:00:02.1: reg 10: [mem 0xdbf7ec00-0xdbf7ecff]
[    0.163638] pci 0000:00:02.1: supports D1 D2
[    0.163640] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163642] pci 0000:00:02.1: PME# disabled
[    0.163659] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
[    0.163698] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
[    0.163708] pci 0000:00:05.0: reg 10: [mem 0xdbf78000-0xdbf7bfff]
[    0.163750] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.163752] pci 0000:00:05.0: PME# disabled
[    0.163769] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
[    0.163790] pci 0000:00:06.0: reg 20: [io  0xffa0-0xffaf]
[    0.163820] pci 0000:00:07.0: [10de:03ef] type 0 class 0x000680
[    0.163829] pci 0000:00:07.0: reg 10: [mem 0xdbf7d000-0xdbf7dfff]
[    0.163834] pci 0000:00:07.0: reg 14: [io  0xd480-0xd487]
[    0.163868] pci 0000:00:07.0: supports D1 D2
[    0.163870] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163874] pci 0000:00:07.0: PME# disabled
[    0.163885] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
[    0.163893] pci 0000:00:08.0: reg 10: [io  0xd400-0xd407]
[    0.163897] pci 0000:00:08.0: reg 14: [io  0xd080-0xd083]
[    0.163901] pci 0000:00:08.0: reg 18: [io  0xd000-0xd007]
[    0.163905] pci 0000:00:08.0: reg 1c: [io  0xcc00-0xcc03]
[    0.163910] pci 0000:00:08.0: reg 20: [io  0xc880-0xc88f]
[    0.163914] pci 0000:00:08.0: reg 24: [mem 0xdbf7c000-0xdbf7cfff]
[    0.163941] pci 0000:00:08.1: [10de:03f6] type 0 class 0x000101
[    0.163949] pci 0000:00:08.1: reg 10: [io  0xc800-0xc807]
[    0.163954] pci 0000:00:08.1: reg 14: [io  0xc480-0xc483]
[    0.163958] pci 0000:00:08.1: reg 18: [io  0xc400-0xc407]
[    0.163962] pci 0000:00:08.1: reg 1c: [io  0xc080-0xc083]
[    0.163966] pci 0000:00:08.1: reg 20: [io  0xc000-0xc00f]
[    0.163970] pci 0000:00:08.1: reg 24: [mem 0xdbf77000-0xdbf77fff]
[    0.164014] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
[    0.164041] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164044] pci 0000:00:09.0: PME# disabled
[    0.164057] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
[    0.164083] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164085] pci 0000:00:0b.0: PME# disabled
[    0.164097] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
[    0.164123] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.164125] pci 0000:00:0c.0: PME# disabled
[    0.164143] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.164158] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.164170] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.164182] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.164197] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.164255] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.164258] pci 0000:00:04.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.164261] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.164264] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.164267] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.164269] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.164271] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.164273] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.164275] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.164278] pci 0000:00:04.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.164309] pci 0000:02:00.0: [10de:0615] type 0 class 0x000300
[    0.164321] pci 0000:02:00.0: reg 10: [mem 0xdf000000-0xdfffffff]
[    0.164334] pci 0000:02:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.164346] pci 0000:02:00.0: reg 1c: [mem 0xdc000000-0xddffffff 64bit]
[    0.164354] pci 0000:02:00.0: reg 24: [io  0xec00-0xec7f]
[    0.164363] pci 0000:02:00.0: reg 30: [mem 0xdefe0000-0xdeffffff pref]
[    0.172039] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.172045] pci 0000:00:09.0:   bridge window [io  0xe000-0xefff]
[    0.172048] pci 0000:00:09.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.172052] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.172082] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.172085] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.172088] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.172091] pci 0000:00:0b.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.172111] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.172114] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.172117] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.172120] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.172129] pci_bus 0000:00: on NUMA node 0
[    0.172135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.172266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.172294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.172317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.172340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.172439]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.172553]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
[    0.172555] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.175878] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.175949] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.176038] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.176106] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.176174] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.176241] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.176309] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.176379] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *10
[    0.176448] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7
[    0.176525] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.176595] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.176664] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.176732] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.176802] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.176877] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[    0.176953] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.177023] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.177105] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.177195] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.177197] vgaarb: loaded
[    0.177198] vgaarb: bridge control possible 0000:02:00.0
[    0.177350] SCSI subsystem initialized
[    0.177398] libata version 3.00 loaded.
[    0.177431] usbcore: registered new interface driver usbfs
[    0.177439] usbcore: registered new interface driver hub
[    0.177458] usbcore: registered new device driver usb
[    0.177518] PCI: Using ACPI for IRQ routing
[    0.183719] PCI: pci_cache_line_size set to 64 bytes
[    0.183766] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.183768] reserve RAM buffer: 00000000bffc0000 - 00000000bfffffff 
[    0.183841] NetLabel: Initializing
[    0.183842] NetLabel:  domain hash size = 128
[    0.183843] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.183852] NetLabel:  unlabeled traffic allowed by default
[    0.183880] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.183886] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.183889] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.192100] Switching to clocksource hpet
[    0.195611] Switched to NOHz mode on CPU #0
[    0.195714] Switched to NOHz mode on CPU #1
[    0.196837] AppArmor: AppArmor Filesystem Enabled
[    0.196867] pnp: PnP ACPI init
[    0.196882] ACPI: bus type pnp registered
[    0.196988] pnp 00:00: [bus 00-ff]
[    0.196990] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.196993] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.196995] pnp 00:00: [io  0x0d00-0xffff window]
[    0.196997] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.196999] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.197001] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.197002] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.197060] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.197082] pnp 00:01: [dma 4]
[    0.197083] pnp 00:01: [io  0x0000-0x000f]
[    0.197085] pnp 00:01: [io  0x0081-0x0083]
[    0.197087] pnp 00:01: [io  0x0087]
[    0.197088] pnp 00:01: [io  0x0089-0x008b]
[    0.197090] pnp 00:01: [io  0x008f]
[    0.197091] pnp 00:01: [io  0x00c0-0x00df]
[    0.197108] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.197116] pnp 00:02: [io  0x0070-0x0071]
[    0.197129] pnp 00:02: [irq 8]
[    0.197145] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.197151] pnp 00:03: [io  0x0061]
[    0.197168] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.197175] pnp 00:04: [io  0x00f0-0x00ff]
[    0.197182] pnp 00:04: [irq 13]
[    0.197198] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.198676] pnp 00:05: [mem 0x000d0000-0x000d3fff window]
[    0.198678] pnp 00:05: [mem 0x000d4000-0x000d7fff window]
[    0.198680] pnp 00:05: [mem 0x000de000-0x000dffff window]
[    0.198681] pnp 00:05: [io  0x0010-0x001f]
[    0.198683] pnp 00:05: [io  0x0022-0x003f]
[    0.198685] pnp 00:05: [io  0x0044-0x004d]
[    0.198686] pnp 00:05: [io  0x0050-0x005f]
[    0.198688] pnp 00:05: [io  0x0062-0x0063]
[    0.198689] pnp 00:05: [io  0x0065-0x006f]
[    0.198691] pnp 00:05: [io  0x0072-0x007f]
[    0.198692] pnp 00:05: [io  0x0080]
[    0.198694] pnp 00:05: [io  0x0084-0x0086]
[    0.198695] pnp 00:05: [io  0x0088]
[    0.198697] pnp 00:05: [io  0x008c-0x008e]
[    0.198698] pnp 00:05: [io  0x0090-0x009f]
[    0.198700] pnp 00:05: [io  0x00a2-0x00bf]
[    0.198701] pnp 00:05: [io  0x00e0-0x00ef]
[    0.198703] pnp 00:05: [io  0x04d0-0x04d1]
[    0.198705] pnp 00:05: [io  0x0800-0x080f]
[    0.198706] pnp 00:05: [io  0x4000-0x407f]
[    0.198708] pnp 00:05: [io  0x4080-0x40ff]
[    0.198709] pnp 00:05: [io  0x4400-0x447f]
[    0.198711] pnp 00:05: [io  0x4480-0x44ff]
[    0.198712] pnp 00:05: [io  0x4800-0x487f]
[    0.198714] pnp 00:05: [io  0x4880-0x48ff]
[    0.198715] pnp 00:05: [io  0x4c00-0x4c7f]
[    0.198717] pnp 00:05: [io  0x4c80-0x4cff]
[    0.198719] pnp 00:05: [mem 0xfec80000-0x1fd93ffff]
[    0.198721] pnp 00:05: [mem 0xfefe0000-0xfefe01ff]
[    0.198722] pnp 00:05: [mem 0xfefe1000-0xfefe1fff]
[    0.198724] pnp 00:05: [mem 0xfee01000-0xfeefffff]
[    0.198726] pnp 00:05: [mem 0xffb80000-0xffffffff]
[    0.198793] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.198800] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.198802] system 00:05: [io  0x4000-0x407f] has been reserved
[    0.198804] system 00:05: [io  0x4080-0x40ff] has been reserved
[    0.198806] system 00:05: [io  0x4400-0x447f] has been reserved
[    0.198809] system 00:05: [io  0x4480-0x44ff] has been reserved
[    0.198811] system 00:05: [io  0x4800-0x487f] has been reserved
[    0.198813] system 00:05: [io  0x4880-0x48ff] has been reserved
[    0.198815] system 00:05: [io  0x4c00-0x4c7f] has been reserved
[    0.198817] system 00:05: [io  0x4c80-0x4cff] has been reserved
[    0.198820] system 00:05: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.198822] system 00:05: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.198825] system 00:05: [mem 0x000de000-0x000dffff window] has been reserved
[    0.198827] system 00:05: [mem 0xfec80000-0x1fd93ffff] could not be reserved
[    0.198830] system 00:05: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.198832] system 00:05: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.198834] system 00:05: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.198837] system 00:05: [mem 0xffb80000-0xffffffff] could not be reserved
[    0.198840] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.198882] pnp 00:06: [mem 0xfeff0000-0xfeff0fff]
[    0.198900] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.198953] pnp 00:07: [mem 0xfec00000-0xfec00fff]
[    0.198955] pnp 00:07: [mem 0xfee00000-0xfee00fff]
[    0.198984] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.198986] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.198989] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199007] pnp 00:08: [io  0x0060]
[    0.199009] pnp 00:08: [io  0x0064]
[    0.199017] pnp 00:08: [irq 1]
[    0.199040] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.199072] pnp 00:09: [irq 12]
[    0.199094] pnp 00:09: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.199193] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.199195] pnp 00:0a: [io  0x0a00-0x0a0f]
[    0.199196] pnp 00:0a: [io  0x0a10-0x0a1f]
[    0.199198] pnp 00:0a: [io  0x0a20-0x0a2f]
[    0.199200] pnp 00:0a: [io  0x0a30-0x0a3f]
[    0.199231] system 00:0a: [io  0x0a00-0x0a0f] has been reserved
[    0.199234] system 00:0a: [io  0x0a10-0x0a1f] has been reserved
[    0.199236] system 00:0a: [io  0x0a20-0x0a2f] has been reserved
[    0.199238] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.199240] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199271] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.199302] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.199304] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.199428] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.199430] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.199432] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.199434] pnp 00:0c: [mem 0x00100000-0xbfffffff]
[    0.199435] pnp 00:0c: [mem 0xfec00000-0xffffffff]
[    0.199476] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.199479] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.199481] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.199483] system 00:0c: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.199486] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.199488] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.199685] pnp: PnP ACPI: found 13 devices
[    0.199686] ACPI: ACPI bus type pnp unregistered
[    0.199689] PnPBIOS: Disabled by ACPI PNP
[    0.235316] PCI: max bus depth: 1 pci_try_num: 2
[    0.235330] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.235332] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.235335] pci 0000:00:04.0:   bridge window [mem disabled]
[    0.235337] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.235341] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.235344] pci 0000:00:09.0:   bridge window [io  0xe000-0xefff]
[    0.235347] pci 0000:00:09.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.235350] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.235353] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.235354] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.235357] pci 0000:00:0b.0:   bridge window [mem disabled]
[    0.235359] pci 0000:00:0b.0:   bridge window [mem pref disabled]
[    0.235362] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.235364] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.235366] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.235368] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.235375] pci 0000:00:04.0: setting latency timer to 64
[    0.235379] pci 0000:00:09.0: setting latency timer to 64
[    0.235383] pci 0000:00:0b.0: setting latency timer to 64
[    0.235386] pci 0000:00:0c.0: setting latency timer to 64
[    0.235389] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.235391] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.235393] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.235395] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.235398] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.235400] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.235402] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.235404] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.235406] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.235408] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.235410] pci_bus 0000:01: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.235412] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.235414] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.235416] pci_bus 0000:02: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.235418] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.235451] NET: Registered protocol family 2
[    0.235506] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.235688] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.236168] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.236408] TCP: Hash tables configured (established 131072 bind 65536)
[    0.236410] TCP reno registered
[    0.236413] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.236421] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.236510] NET: Registered protocol family 1
[    0.312113] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312162] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312219] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312274] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312329] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312389] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312452] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312519] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.312537] pci 0000:02:00.0: Boot video device
[    0.312540] PCI: CLS 64 bytes, default 64
[    0.312809] audit: initializing netlink socket (disabled)
[    0.312817] type=2000 audit(1335224413.308:1): initialized
[    0.338480] highmem bounce pool size: 64 pages
[    0.338485] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.357219] VFS: Disk quotas dquot_6.5.2
[    0.357279] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.357794] fuse init (API version 7.16)
[    0.357864] msgmni has been set to 1567
[    0.358103] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.358123] io scheduler noop registered
[    0.358125] io scheduler deadline registered
[    0.358137] io scheduler cfq registered (default)
[    0.358228] pcieport 0000:00:09.0: setting latency timer to 64
[    0.358252] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.358281] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.358298] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.358324] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.358341] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.358384] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.358402] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.358497] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.358503] ACPI: Power Button [PWRB]
[    0.358535] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.358538] ACPI: Power Button [PWRF]
[    0.358561] ACPI: acpi_idle registered with cpuidle
[    0.361711] ERST: Table is not found!
[    0.361780] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.361848] isapnp: Scanning for PnP cards...
[    0.429585] Freeing initrd memory: 13300k freed
[    0.714773] isapnp: No Plug & Play device found
[    0.719711] Linux agpgart interface v0.103
[    0.720710] brd: module loaded
[    0.721124] loop: module loaded
[    0.721292] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.721436] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.721450] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.721461] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.721466] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.721584] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.721593] pata_acpi 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.721603] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.721608] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.721831] Fixed MDIO Bus: probed
[    0.721847] PPP generic driver version 2.4.2
[    0.721876] tun: Universal TUN/TAP device driver, 1.6
[    0.721878] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.721937] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.722056] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.722065] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.722073] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.722076] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.722101] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.722118] ehci_hcd 0000:00:02.1: debug port 1
[    0.722125] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.722143] ehci_hcd 0000:00:02.1: irq 21, io mem 0xdbf7ec00
[    0.732046] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.732195] hub 1-0:1.0: USB hub found
[    0.732198] hub 1-0:1.0: 10 ports detected
[    0.732264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732422] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.732438] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.732453] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.732456] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.732485] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.732513] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdbf7f000
[    0.790163] hub 2-0:1.0: USB hub found
[    0.790169] hub 2-0:1.0: 10 ports detected
[    0.790233] uhci_hcd: USB Universal Host Controller Interface driver
[    0.790309] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.790754] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.790763] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.790892] mousedev: PS/2 mouse device common for all mice
[    0.790989] rtc_cmos 00:02: RTC can wake from S4
[    0.791097] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.791134] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.791211] device-mapper: uevent: version 1.0.3
[    0.791270] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.791305] EISA: Probing bus 0 at eisa.0
[    0.791307] EISA: Cannot allocate resource for mainboard
[    0.791309] Cannot allocate resource for EISA slot 1
[    0.791310] Cannot allocate resource for EISA slot 2
[    0.791312] Cannot allocate resource for EISA slot 3
[    0.791313] Cannot allocate resource for EISA slot 4
[    0.791315] Cannot allocate resource for EISA slot 5
[    0.791316] Cannot allocate resource for EISA slot 6
[    0.791317] Cannot allocate resource for EISA slot 7
[    0.791319] Cannot allocate resource for EISA slot 8
[    0.791320] EISA: Detected 0 cards.
[    0.791329] cpufreq-nforce2: No nForce2 chipset.
[    0.791331] cpuidle: using governor ladder
[    0.791332] cpuidle: using governor menu
[    0.791334] EFI Variables Facility v0.08 2004-May-17
[    0.791537] TCP cubic registered
[    0.791635] NET: Registered protocol family 10
[    0.792088] NET: Registered protocol family 17
[    0.792102] Registering the dns_resolver key type
[    0.792123] Using IPI No-Shortcut mode
[    0.792173] PM: Hibernation image not present or could not be loaded.
[    0.792182] registered taskstats version 1
[    0.805601]   Magic number: 8:290:707
[    0.805715] rtc_cmos 00:02: setting system clock to 2012-04-23 23:40:14 UTC (1335224414)
[    0.805722] powernow-k8: Found 1 AMD Athlon(tm) II X2 235e Processor (2 cpu cores) (version 2.20.00)
[    0.805753] powernow-k8:    0 : pstate 0 (2700 MHz)
[    0.805755] powernow-k8:    1 : pstate 1 (1900 MHz)
[    0.805756] powernow-k8:    2 : pstate 2 (1500 MHz)
[    0.805758] powernow-k8:    3 : pstate 3 (800 MHz)
[    0.806122] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.806124] EDD information not available.
[    0.806242] Freeing unused kernel memory: 720k freed
[    0.806489] Write protecting the kernel text: 5528k
[    0.806546] Write protecting the kernel read-only data: 2248k
[    0.806547] NX-protecting the kernel data: 4712k
[    0.813588] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.826214] udevd[82]: starting version 173
[    0.874144] pata_amd 0000:00:06.0: version 0.4.1
[    0.874181] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.881589] scsi0 : pata_amd
[    0.885249] scsi1 : pata_amd
[    0.885883] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.885885] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.886021] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.886160] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    0.886165] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    0.886169] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.044055] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.051098] ata2: port disabled. ignoring.
[    1.178140] hub 1-1:1.0: USB hub found
[    1.178441] hub 1-1:1.0: 4 ports detected
[    1.408879] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:25:11:a2:d8:88
[    1.408884] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.408950] sata_nv 0000:00:08.0: version 3.5
[    1.408967] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.409008] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.409519] scsi2 : sata_nv
[    1.409680] scsi3 : sata_nv
[    1.409779] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 23
[    1.409781] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 23
[    1.409795] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.409824] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.410055] scsi4 : sata_nv
[    1.410142] scsi5 : sata_nv
[    1.410239] ata5: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 22
[    1.410242] ata6: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 22
[    1.708068] usb 2-3: new full speed USB device number 2 using ohci_hcd
[    1.876073] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.884187] ata3.00: ATAPI: HL-DT-ST DVDRAM GH41N, MN01, max UDMA/100
[    1.900184] ata3.00: configured for UDMA/100
[    1.904403] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH41N     MN01 PQ: 0 ANSI: 5
[    1.909114] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.909118] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.909244] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.909325] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.944263] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
[    1.944361] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-3/input0
[    1.955186] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input4
[    1.955312] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-3/input1
[    1.955329] usbcore: registered new interface driver usbhid
[    1.955331] usbhid: USB HID core driver
[    2.212066] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.220395] ata5.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    2.220399] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.238734] ata5.00: configured for UDMA/133
[    2.240051] usb 2-9: new full speed USB device number 3 using ohci_hcd
[    2.376061] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.384298] ata4.00: ATA-7: SAMSUNG HD154UI, 1AG01118, max UDMA7
[    2.384301] ata4.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.392313] ata4.00: configured for UDMA/133
[    2.392523] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD154UI  1AG0 PQ: 0 ANSI: 5
[    2.392690] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.392801] scsi 4:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    2.392891] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.392936] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.392969] sd 4:0:0:0: [sdb] Write Protect is off
[    2.392971] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.392985] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.393212] sd 3:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.393241] sd 3:0:0:0: [sda] Write Protect is off
[    2.393243] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.393257] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.428081]  sdb: sdb1
[    2.428368] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.515573]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    2.515918] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.528324] usb 1-1.4: new high speed USB device number 5 using ehci_hcd
[    2.860075] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.884182] ata6.00: ATAPI: HL-DT-ST BD-RE  WH10LS30, 1.00, max UDMA/133
[    2.916183] ata6.00: configured for UDMA/133
[    2.927754] scsi 5:0:0:0: CD-ROM            HL-DT-ST BD-RE  WH10LS30  1.00 PQ: 0 ANSI: 5
[    2.938025] sr1: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.938163] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    2.938231] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    3.321090] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    6.156430] udevd[348]: starting version 173
[    6.520311] Adding 6289404k swap on /dev/sda6.  Priority:-1 extents:1 across:6289404k 
[    7.693790] lp: driver loaded but no devices found
[    8.429147] wmi: Mapper loaded
[    8.447646] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[    8.447669] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
[    9.223156] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    9.462797] [drm] Initialized drm 1.1.0 20060810
[   10.176525] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 19
[   10.176543] nouveau 0000:02:00.0: PCI INT A -> Link[LNED] -> GSI 19 (level, low) -> IRQ 19
[   10.176549] nouveau 0000:02:00.0: setting latency timer to 64
[   10.177659] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x092a80a2)
[   10.180993] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
[   10.261760] [drm] nouveau 0000:02:00.0: ... appears to be valid
[   10.261764] [drm] nouveau 0000:02:00.0: BIT BIOS found
[   10.261766] [drm] nouveau 0000:02:00.0: Bios version 62.92.9a.00
[   10.261770] [drm] nouveau 0000:02:00.0: TMDS table version 2.0
[   10.261773] [drm] nouveau 0000:02:00.0: Found Display Configuration Block version 4.0
[   10.261776] [drm] nouveau 0000:02:00.0: Raw DCB entry 0: 04011310 00000028
[   10.261778] [drm] nouveau 0000:02:00.0: Raw DCB entry 1: 02000300 00020028
[   10.261780] [drm] nouveau 0000:02:00.0: Raw DCB entry 2: 01000302 00020030
[   10.261782] [drm] nouveau 0000:02:00.0: Raw DCB entry 3: 02022322 00020010
[   10.261784] [drm] nouveau 0000:02:00.0: Raw DCB entry 4: 0000000e 00000000
[   10.261787] [drm] nouveau 0000:02:00.0: DCB connector table: VHER 0x40 5 16 4
[   10.261790] [drm] nouveau 0000:02:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   10.261792] [drm] nouveau 0000:02:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[   10.261794] [drm] nouveau 0000:02:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
[   10.261799] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0xC7E5
[   10.294136] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xCD9A
[   10.296969] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0xDB78
[   10.296978] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xDC76
[   10.298052] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0xDEE2
[   10.298054] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table at offset 0xDF47
[   10.317901] [drm] nouveau 0000:02:00.0: 0xDF47: Condition still not met after 20ms, skipping following opcodes
[   10.336750] [drm] nouveau 0000:02:00.0: 2 available performance level(s)
[   10.336754] [drm] nouveau 0000:02:00.0: 0: memory 100MHz core 300MHz shader 600MHz voltage 950mV fanspeed 100% timing 0
[   10.336758] [drm] nouveau 0000:02:00.0: 3: memory 900MHz core 675MHz shader 1458MHz voltage 1200mV fanspeed 100% timing 2
[   10.336777] [drm] nouveau 0000:02:00.0: c: memory 399MHz core 399MHz shader 810MHz voltage 1200mV
[   10.336887] [TTM] Zone  kernel: Available graphics memory: 408344 kiB.
[   10.336889] [TTM] Zone highmem: Available graphics memory: 3097244 kiB.
[   10.336891] [TTM] Initializing pool allocator.
[   10.336907] [drm] nouveau 0000:02:00.0: Detected 1024MiB VRAM
[   10.338640] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)
[   10.352923] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.352924] [drm] No driver support for vblank timestamp query.
[   10.519385] [drm] nouveau 0000:02:00.0: allocated 1280x1024 fb: 0x40000000, bo f07c1a00
[   10.519452] fbcon: nouveaufb (fb0) is primary device
[   10.519565] Console: switching to colour frame buffer device 160x64
[   10.519599] fb0: nouveaufb frame buffer device
[   10.519600] drm: registered panic notifier
[   10.519606] [drm] Initialized nouveau 0.0.16 20090420 for 0000:02:00.0 on minor 0
[   10.629926] usbcore: registered new interface driver usbserial
[   10.629942] USB Serial support registered for generic
[   10.629970] usbcore: registered new interface driver usbserial_generic
[   10.629971] usbserial: USB Serial Driver core
[   10.674873] USB Serial support registered for pl2303
[   10.674893] pl2303 2-9:1.0: pl2303 converter detected
[   10.706204] usb 2-9: pl2303 converter now attached to ttyUSB0
[   10.706222] usbcore: registered new interface driver pl2303
[   10.706224] pl2303: Prolific PL2303 USB to serial adaptor driver
[   10.986202] cfg80211: Calling CRDA to update world regulatory domain
[   11.569507] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.569511] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569514] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.569516] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569518] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.569520] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569522] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.569524] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569526] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.569528] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569529] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.569532] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569533] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.569535] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569537] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.569539] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569541] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.569543] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569545] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.569547] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569548] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.569550] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569552] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   11.569554] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569556] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   11.569558] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.569560] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   11.569562] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.933450] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.933959] Registered led device: rt2800usb-phy0::radio
[   11.933973] Registered led device: rt2800usb-phy0::assoc
[   11.933988] Registered led device: rt2800usb-phy0::quality
[   11.934235] usbcore: registered new interface driver rt2800usb
[   12.288202] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   12.288209] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.288212] hda_intel: Disabling MSI
[   12.288236] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.356060] hda_codec: ALC1200: BIOS auto-probing.
[   13.356065] hda_codec: ALC1200: SKU not ready 0x411111f0
[   13.374986] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.374991] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.374993] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.374996] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.374998] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.375000] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375002] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.375004] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375006] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.375008] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375009] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.375011] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375013] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.375015] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375017] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.375019] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375021] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.375023] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375024] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.375026] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375028] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.375030] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375032] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.375034] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375036] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.375038] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375040] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.375042] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.375044] cfg80211: World regulatory domain updated:
[   13.375045] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.375048] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.375050] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.375052] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.375054] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.375056] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.550013] type=1400 audit(1335249627.238:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=635 comm="apparmor_parser"
[   13.550049] type=1400 audit(1335249627.238:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=634 comm="apparmor_parser"
[   13.550345] type=1400 audit(1335249627.238:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=635 comm="apparmor_parser"
[   13.550395] type=1400 audit(1335249627.238:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
[   13.550556] type=1400 audit(1335249627.238:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=635 comm="apparmor_parser"
[   13.550609] type=1400 audit(1335249627.238:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
[   13.551010] type=1400 audit(1335249627.238:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=760 comm="apparmor_parser"
[   13.551374] type=1400 audit(1335249627.238:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=760 comm="apparmor_parser"
[   13.551607] type=1400 audit(1335249627.238:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=760 comm="apparmor_parser"
[   13.708285] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   16.852988] init: failsafe main process (872) killed by TERM signal
[   19.634501] type=1400 audit(1335249633.322:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=927 comm="apparmor_parser"
[   19.634918] type=1400 audit(1335249633.322:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=927 comm="apparmor_parser"
[   19.635171] type=1400 audit(1335249633.322:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=927 comm="apparmor_parser"
[   19.800979] type=1400 audit(1335249633.494:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=926 comm="apparmor_parser"
[   19.990864] type=1400 audit(1335249633.678:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=928 comm="apparmor_parser"
[   19.995333] type=1400 audit(1335249633.682:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=928 comm="apparmor_parser"
[   19.998022] type=1400 audit(1335249633.686:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=928 comm="apparmor_parser"
[   20.059164] type=1400 audit(1335249633.746:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=934 comm="apparmor_parser"
[   20.059509] type=1400 audit(1335249633.746:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=934 comm="apparmor_parser"
[   20.172342] type=1400 audit(1335249633.862:20): apparmor="STATUS" operation="profile_load" name="/usr/sbin/dhcpd" pid=940 comm="apparmor_parser"
[   20.332148] ppdev: user-space parallel port driver
[   21.889075] init: apport pre-start process (1000) terminated with status 1
[   21.891358] init: apport post-stop process (1031) terminated with status 1
[   24.157221] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.187662] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   25.142641] Bluetooth: Core ver 2.16
[   25.142665] NET: Registered protocol family 31
[   25.142667] Bluetooth: HCI device and connection manager initialized
[   25.142670] Bluetooth: HCI socket layer initialized
[   25.142671] Bluetooth: L2CAP socket layer initialized
[   25.143310] Bluetooth: SCO socket layer initialized
[   25.168930] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.168933] Bluetooth: BNEP filters: protocol multicast
[   25.197844] Bluetooth: RFCOMM TTY layer initialized
[   25.197849] Bluetooth: RFCOMM socket layer initialized
[   25.197851] Bluetooth: RFCOMM ver 1.11
[   28.076793] wlan0: authenticate with (try 1)
[   28.080071] wlan0: authenticated
[   28.100044] wlan0: associate with (try 1)
[   28.102299] wlan0: RX AssocResp from  (capab=0x431 status=0 aid=1)
[   28.102301] wlan0: associated
[   28.110103] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.576414] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   29.324239] init: plymouth-stop pre-start process (1333) terminated with status 1
[   30.718708] init: tftpd-hpa main process (1375) terminated with status 1
[   30.718739] init: tftpd-hpa main process ended, respawning
[   34.736028] eth0: no IPv6 routers present
[   38.512028] wlan0: no IPv6 routers present
[   40.627058] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   54.549374] ISO 9660 Extensions: Microsoft Joliet Level 3
[   54.606105] ISO 9660 Extensions: RRIP_1991A
[   58.104031] eth0: no IPv6 routers present
[   81.408031] eth0: no IPv6 routers present
[  104.632038] eth0: no IPv6 routers present
[  227.909978] wlan0: direct probe to  (try 1/3)
[  227.922198] wlan0: direct probe responded
[  227.932026] wlan0: authenticate with  (try 1)
[  227.940560] wlan0: authenticated
[  227.960105] wlan0: associate with  (try 1)
[  227.964316] wlan0: RX ReassocResp from  (capab=0x431 status=0 aid=1)
[  227.964320] wlan0: associated

```

---

### Post by scheuri on 2012-04-24
uhm, wait...that is not really correct.

I am not sure if you tried this.

You have a host IP address that is 192.168.0.110, right?
That would be in the network 192.168.0.0/255.255.255.0.

That 110 IP is NOT in the subnet 192.168.0.**100**/255.255.255.0.
That 100 is incorrect.

You want a subnet that starts with 192.168.0.0 and goes to 192.168.0.255, right?
That would be 192.168.0.0/255.255.255.0 (where the IP 192.168.0.110 is part of).

Either its that or I am completely missing the point.
cheers
scheuri

---

### Post by bab1 on 2012-04-24
> **Kneegrowplease said:**
> What are the rules regarding ip's and subnets?:confused:

```
/etc/dhcp/dhcpd.conf line 53: subnet 192.168.0.100 netmask 244.255.255.0: bad subnet number/mask combination.
subnet 192.168.0.100 netmask 244.255.255.0 
```

The subnet mask defines the network ID and the host range.  It does this by providing an unbroken (contiguous) range of binary zeros for the host range. in the case of 255.255.255.0 we have this```
[COLOR="Red"]111111111111111111111111[/COLOR][COLOR="Blue"]00000000[/COLOR] = 255.255.255.0
```The decimal number 255 equals a binary 11111111 (8 bits). In this case the first three octets mask (filter by anding) the network (192.168.0 part) and the last octet (00000000) equals the range of IP addresses for the hosts in the network (000000001 (1) to 11111110 (254).  The network ID uses 00000000 (decimal 0) and the broadcast IP address is 11111111 (255).

The subnet mask of 244.255.255.0 is not a legitimate mask.  It looks like this ```
11110100111111111111111100000000
```  The nearest network would be ```
[COLOR="Red"]11110000[/COLOR][COLOR="Blue"]000000000000000000000000[/COLOR]
```  That would be the 240.0.0.0. not a 192.0.0.0 network which looks like this```
[COLOR="Red"]11000000[/COLOR][COLOR="Blue"]000000000000000000000000[/COLOR]
```

Beside the numbers there are boundaries and contiguous ranges.  The decimal that you use must conform the binary that the machine uses.

---

### Post by Kneegrowplease on 2012-04-24
I didn't mention it, thought people would see in my syslog, changed my ip tp 192.168.2.0 with a netmask of 255.255.255.0



still doesn't work, all that stuff about binary and netmasks and ip ranges was extremely informative if not a little overwhelming:lolflag: 



AND it appears to have been typed in traditional chinese:confused:

---

### Post by Kneegrowplease on 2012-04-24
could someone just pack a spoon full of ubuntu and force feed me the answer? lmao, just tell me what ip subnet and mask to use, trying to set up dhcp to do a bootp on an embedded device (NAS) and boot a new kernel. so I couldn't care less what the numbers are as long as they work!!!):P


although my new error is different, I no longer get the bad range warning. just a failure to start the service. could someone please review my syslog and give me a lil hint?

---

### Post by chamber on 2012-04-24
It all depends on the IP of your router.

It will be your gateway and your netmask will be 255.255.255.0

Generally most home networks will be a /24 network (192.168.0.1 - 255) and will always have a subnet as described above.

---

### Post by chamber on 2012-04-24
Post output of

```
ip addr
ifconfig
iwconfig
```

---

### Post by Kneegrowplease on 2012-04-24
> **chamber said:**
> Post output of

```
ip addr
ifconfig
iwconfig
```


ip of the wireless AP that issues me my IP:

172.20.128.1

my IP for wlan0:

172.20.203.54  Bcast:172.20.255.255  Mask:255.255.128.0

and eth0:

doesn't even have an ip unless I manually set one.

EDIT:  since eth0 gets no IP from the AP, and I'm attempting to set up eth0 as the dhcp server, I assumed the output of iwconfig and the IP of the AP that serves me my internet wouldn't matter a bit.

---

### Post by chamber on 2012-04-24
Does your router act as a DHCP server ok? Does eth0 appear when you run ip addr?

---

### Post by slugg007 on 2012-04-24
Go to:
[http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php)

This will help you find your netmask and will show you IP range for this netmask. It will also tell you if you have chosen an improper subnet and IP range.

If your IP range is 192.168.1 through 192.168.0.254 your netmask will be 255.255.255.0.

If your IP range is different, your netmask will be different.

Then there is your gateway IP. Most people I work with use the first IP in the range. For example 192.168.0.1. But it can be anything you want.

---

### Post by bab1 on 2012-04-24
> **slugg007 said:**
> Go to:
[http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php)

This will help you find your netmask and will show you IP range for this netmask. It will also tell you if you have chosen an improper subnet and IP range.

If your IP range is 192.168.1 through 192.168.0.254 your netmask will be 255.255.255.0.

If your IP range is different, your netmask will be different.

Then there is your gateway IP. Most people I work with use the first IP in the range. For example 192.168.0.1. But it can be anything you want.

The gateway IP is the LAN side IP address of the network's router.  It is not just any address in the network.

---

### Post by bab1 on 2012-04-24
> **Kneegrowplease said:**
> I didn't mention it, thought people would see in my syslog, changed my ip tp 192.168.2.0 with a netmask of 255.255.255.0



still doesn't work, all that stuff about binary and netmasks and ip ranges was extremely informative if not a little overwhelming:lolflag: 



AND it appears to have been typed in traditional chinese:confused:

I thought by this > What are the rules regarding ip's and subnets?you really wanted to understand.

Maybe you don't know how to ask for the advice you *really* need.    :-(

---

### Post by Kneegrowplease on 2012-04-24
> **bab1 said:**
> I thought by this you really wanted to understand.

Maybe you don't know how to ask for the advice you *really* need.    :-(




Hey, I was joking. I read that 3 times till I understood What you were talking about,:lolflag:



What confuses me is that I'm not trying to share my internet with a device plugged into a router plugged into my NIC.(and I don't want to provide it internet so why does my gateway matter one lick?) I plugged the device directly into my NIC and want my computer to issue this and only this device an ip for the purpose of NETBOOTING. my NIC has no IP because my internet is supplied through wlan0. am I missing something huge or just not explaining correctly????

---

### Post by Kneegrowplease on 2012-04-24
wlan0 is a USB wifi card, which gets it's signal from 2300 Yards away with a 2w amp and 24dbi parabolic grid antenna. 


can I get a simple yes or no as to weather this matters(since I'm not trying to share that connection, or does DHCP not work without sharing internet?)? everyone keeps talking about my gateway IP which is 172.20.128.1 but I can't understand why....



I'm not trying to be rude, just frustrated with my own ignorance

---

### Post by Kneegrowplease on 2012-04-24
I want my computer to be the sole DHCP server for any device connected to my LAN (really just one device, but for simplicity's sake...)

---

### Post by JKyleOKC on 2012-04-24
> **Kneegrowplease said:**
> can I get a simple yes or no as to weather this matters(since I'm not trying to share that connection, or does DHCP not work without sharing internet?)? everyone keeps talking about my gateway IP which is 172.20.128.1 but I can't understand why....I'll try to clear things up a bit, now that you've made it plain that all you want to do with this question is find a way to communicate between your computer and the NAS device. In that situation, the gateway IP has nothing to do with your problem.

However, neither does your router. The router is capable of only one job at a time, and you have it occupied full-time providing your internet connection through the wireless AP. The connection between your computer and the NAS cannot go through the router at all.

Instead, you need a direct connection between the two devices. However using a standard CAT5 cable won't work, because it connects the receive pin at one end to the receive pin at the other end and ditto for all the other signals involved. What you need is a "crossover cable" that switches the connections around so that outgoing data fed to one end appears as incoming data at the other end.

If such a cable is difficult for you to obtain, you can use standard cables by adding a third device, known as a hub, in the middle. A hub looks a bit like a router, and like a router has a number of sockets for network cables (usually 5 or 8; for your needs a 5-port device is ample). Outgoing signals from a device plugged into one of its ports appear as incoming signals at all the other ports, so you connect your computer with standard cable to one port of the hub and the NAS box to another.

Of course this doesn't answer the question of how you get an IP address assigned to the NAS; most such devices come with an IP address assigned to them and shown on a sticker somewhere on the unit, or in the instruction book. A few come with a CD (that can run only in Windows) to set them up and assign the address. If you have one of these you'll have to borrow a Windows machine to do the setup. Once you know (or configure) the IP address of the NAS, you can use the "sudo ifconfig" commands to assign your eth0 interface another address on the same subnet, and that should solve the problem.

For DHCP to work, you would have to install a DHCP server program on your computer, and the NAS would have to include a DHCP client in its firmware. If this is what the NAS expects, the instruction manual should provide full details for setting it up.

I hope this helps a bit. I was just going back through some saved Emails from 2001 when I was first attempting to set up my little LAN using Linux, and they reminded me just how totally confusing the subject appears when you first delve into it!!!

---

### Post by bab1 on 2012-04-24
> **Kneegrowplease said:**
> What confuses me is that I'm not trying to share my internet with a device plugged into a router plugged into my NIC.(and I don't want to provide it internet so why does my gateway matter one lick?)
Your right, it doesn't matter, but you have not been clear about what you are attempting to do.  Most folks can only envision the basic network set up. > 
I plugged the device directly into my NIC and want my computer to issue this and only this device an ip for the purpose of NETBOOTING.
This would not be a NAS.  Didn't you mention that this was a NAS device (e.g *"trying to set up dhcp to do a bootp on an embedded device (NAS)"*.  Net booting usually refers to thin clients (no hardrive) that are configured upon boot up.  Is the device a thin client or a NAS?  Have you configured the DHCP to provide bootp addresses?
> 
my NIC has no IP because my internet is supplied through wlan0. am I missing something huge or just not explaining correctly???? 
...
wlan0 is a USB wifi card, which gets it's signal from 2300 Yards away with a 2w amp and 24dbi parabolic grid antenna.
As **you** say: the wlan0 interface is irrelevant> 

can I get a simple yes or no as to weather (should be: [COLOR="Red"]**whether**[/COLOR] (weather is the state of the atmosphere at a place and time as regards heat, cloudiness, dryness, sunshine, wind, rain, etc.))  
this matters(since I'm not trying to share that connection, or does DHCP not work without sharing internet?)? everyone keeps talking about my gateway IP which is 172.20.128.1 but I can't understand why....

I'm not trying to be rude, just frustrated with my own ignorance 

I want my computer to be the sole DHCP server for any device connected to my LAN (really just one device, but for simplicity's sake...)
DHCP needs to be configured for whatever you want to do.  Typically a DHCP server responds to a request from a DHCP client by offering an IP address from a pool of addresses.  The client then accepts the lease of that address.

If indeed you are booting an image (PXE) and need an IP address assigned to the thin client then you need to configure that with the DHCP server conf file.  In any case, just plugging in an Ethernet cable won't work.  

You also should confirm is that the NIC's at both ends will auto configure for both transmit (TX) and receive (RX). If the NIC's don't, then you will need either a crossover cable or a switch to provide this functionality.

The eth0 interface should be configured with a specific IP address in the subnet of your choice, but not in the pool of addresses controlled by the DHCP server (in 192.168.0.0/24 network or some such).

You have a lot to think about now.  Is it going to be easy (Plug 'n Play)?  No; but that's how your going to learn how this stuff works.  ;-)

[COLOR="Blue"]**Edit:** Both DHCP and bootp are configured by the same file.  See **_[[COLOR="Blue"]4.3.2. Setting up a DHCP server[/COLOR]]("http://www.debian.org/releases/stable/alpha/ch04s03.html.en#dhcpd")_**.[/COLOR]

---

### Post by bab1 on 2012-04-24
> **JKyleOKC said:**
> I'll try to clear things up a bit, now that you've made it plain that all you want to do with this question is find a way to communicate between your computer and the NAS device. In that situation, the gateway IP has nothing to do with your problem.
This may be a PXE environment.> 

However, neither does your router. The router is capable of only one job at a time, and you have it occupied full-time providing your internet connection through the wireless AP. The connection between your computer and the NAS cannot go through the router at all.

Instead, you need a direct connection between the two devices. However using a standard CAT5 cable won't work, because it connects the receive pin at one end to the receive pin at the other end and ditto for all the other signals involved. What you need is a "crossover cable" that switches the connections around so that outgoing data fed to one end appears as incoming data at the other end.

If such a cable is difficult for you to obtain, you can use standard cables by adding a third device, known as a hub, in the middle. A hub looks a bit like a router, and like a router has a number of sockets for network cables (usually 5 or 8; for your needs a 5-port device is ample). Outgoing signals from a device plugged into one of its ports appear as incoming signals at all the other ports, so you connect your computer with standard cable to one port of the hub and the NAS box to another.
A switch is more common to get and just as cheap.> 

Of course this doesn't answer the question of how you get an IP address assigned to the NAS; most such devices come with an IP address assigned to them and shown on a sticker somewhere on the unit, or in the instruction book. A few come with a CD (that can run only in Windows) to set them up and assign the address. If you have one of these you'll have to borrow a Windows machine to do the setup. Once you know (or configure) the IP address of the NAS, you can use the "sudo ifconfig" commands to assign your eth0 interface another address on the same subnet, and that should solve the problem.

For DHCP to work, you would have to install a DHCP server program on your computer, and the NAS would have to include a DHCP client in its firmware. If this is what the NAS expects, the instruction manual should provide full details for setting it up.

I hope this helps a bit. I was just going back through some saved Emails from 2001 when I was first attempting to set up my little LAN using Linux, and they reminded me just how totally confusing the subject appears when you first delve into it!!!

We need for him to confirm whether it is PXE (thin client) or a NAS device.

---

### Post by Kneegrowplease on 2012-04-25
this NAS runs a bull **** linux OS with NO UI, (tivic windrunner) no ssh or telnet access, no webui, nothing! Downloads must be started through a chinese website.   there is a similar NAS device
on the market (NS-k330) that has a pretty nice aftermarket FW and GUI called snake-os. snake-os SHOULD run on my device but everything needs to be done through my serial cable using commands availible in the uboot because of the lack of UI. 

I can flash new kernels and rootfs by tftp'ing the rootfs to 200000, then a cp.b (copy bits) 200000 xxxxxxx ooooooo (x's is the start address to write to, o's are the end address) then I have to tftp the new kernel and boot,


I can do it all with the bootp command within uboot in one shot if I can get my computer to give it an ip...


this will obviously help greatly in my endeavor to create a stable, functional kernel for this device...
[COLOR="Red"]
I own multiple switches and routers, although NONE are in use for now[/COLOR]


there is also a PXE option for booting within uboot, but I have compiled a bootp image

---

### Post by bab1 on 2012-04-25
> **Kneegrowplease said:**
> this NAS runs a bull **** linux OS with NO UI, (tivic windrunner) no ssh or telnet access, no webui, nothing! Downloads must be started through a chinese website.   there is a similar NAS device
on the market (NS-k330) that has a pretty nice aftermarket FW and GUI called snake-os. snake-os SHOULD run on my device but everything needs to be done through my serial cable using commands availible in the uboot because of the lack of UI. 

I can flash new kernels and rootfs by tftp'ing the rootfs to 200000, then a cp.b (copy bits) 200000 xxxxxxx ooooooo (x's is the start address to write to, o's are the end address) then I have to tftp the new kernel and boot,


I can do it all with the bootp command within uboot in one shot if I can get my computer to give it an ip...


this will obviously help greatly in my endeavor to create a stable, functional kernel for this device...
[COLOR="Red"]
I own multiple switches and routers, although NONE are in use for now[/COLOR]


there is also a PXE option for booting within uboot, but I have compiled a bootp image

Look at my edit - It has the information to configure the DHCP server for bootp.

---

### Post by Kneegrowplease on 2012-04-25
Thanks bab1, do you think it would be easier through a switch or router?

take a look @ my .conf file, tell me what you think...




```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
  subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.10 192.168.2.30;
  option domain-name-servers 192.168.2.0, 8.8.4.4;
# option domain-name "internal.example.org";
  option routers 192.168.2.0;
  option broadcast-address 192.168.2.255;
  default-lease-time 600;
  max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
  hardware ethernet 00.xx.cd.00.xx.8e;
  fixed-address 192.168.2.10;
}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
```


printenv in the NAS's uboot shows ipaddr 192.168.0.10 serverip 192.168.2.0 netmask 255.255.255.0

---

### Post by bab1 on 2012-04-25
> **Kneegrowplease said:**
> Thanks bab1, do you think it would be easier through a switch or router?
DHCP is a LAN technology.  You can't traverse a router with DHCP requests unless you use DHCP helpers.  Use a switch only.

It wouldn't do any good for me to look at your conf file.  I've never setup a ISC DHCP server for bootp.  I would be following on of the guides just like you are.  I can tell you that you need to remove the hash tags (#) on the items you want to be configured.  If you don't the data will not be parsed when the server is booted (e.g they are just comments if you leave the hash tags (#) in place)

Here is the Debian [**_[COLOR="Blue"]Howto[/COLOR]_**]("http://www.debian-administration.org/articles/478") on a PXE configuration of a ISC DHCP server.

**[COLOR="Blue"]EDIT2:[/COLOR]** [**_[COLOR="Red"]Here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1964191") is a discussion going on right now on PXE booting.  The user @Jonathan L is very knowledgeable.> 

take a look @ my .conf file, tell me what you think...

Is passacaglia or fantasia one of your hosts?> 


```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
  subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.10 192.168.2.30;
  option domain-name-servers 192.168.2.0, 8.8.4.4;
# option domain-name "internal.example.org";
  option routers 192.168.2.0;
  option broadcast-address 192.168.2.255;
  default-lease-time 600;
  max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
  hardware ethernet 00.xx.cd.00.xx.8e;
  fixed-address 192.168.2.10;
}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
```

---

### Post by Kneegrowplease on 2012-04-25
Thanks bab1 and extra thanks for the links, hadn't even looked into pxe booting.

---

### Post by bab1 on 2012-04-25
> **Kneegrowplease said:**
> Thanks bab1 and extra thanks for the links, hadn't even looked into pxe booting.
You're welcome.  Have you seen **_[COLOR="Red"][this]("http://sideramota.com/?p=92")[/COLOR]_**?

---

### Post by Kneegrowplease on 2012-04-25
> **bab1 said:**
> You're welcome.  Have you seen **_[COLOR="Red"][this]("http://sideramota.com/?p=92")[/COLOR]_**?


LMAO, actually andrew (hank) is the one who wrote the kernel I've booted on this thing. the one who set me down this path of self discovery and learning. the only problem is his build takes 28 minutes to boot!!!!:lolflag: no disrespect, he did the work and it DOES boot, so hat's off. but maybe with some research, I can do better...

---

### Post by Kneegrowplease on 2012-04-25
seems PXE isn't an option on the tivic, just bootp which is basically the same, but I cannot get it to work. it just times out.


```

Star Equuleus # bootp                                                           
Check Link Status ...Up                                                         
BOOTP broadcast 1                                                               
BOOTP broadcast 2                                                               
BOOTP broadcast 3                                                               
BOOTP broadcast 4                                                               
BOOTP broadcast 5                                                               
                                                                                
Retry count exceeded; starting again
```

---

### Post by Kneegrowplease on 2012-05-20
Son of a bitch, I solved this problem and never posted the solution, now I'm up the same creek in a new install and retracing all my steps.

---

### Post by mips on 2012-05-20
Configure a VALID subnet & mask, ie 192.168.0.0 255.255.255.0 and then in your DHCP pool only have a single address for the device you want to net boot.

---

### Post by Kneegrowplease on 2012-05-21
here we go, tftp to an embedded device....

install dhcp3-server:

```
sudo apt-get install -y dhcp3-server
```

Now we must configure our DHCP server. We must tell it from which IP range it should assign IP addresses to requesting clients, which gateway it should assign, which DNS servers, etc.

The configuration file for our DHCP server is /etc/dhcp3/dhcpd.conf. Currently it contains a sample configuration which we copy to /etc/dhcp3/dhcpd.conf_orig for future reference:

```
cp /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf_orig
cat /dev/null > /etc/dhcp3/dhcpd.conf
```

now open the file with your favorite text editor:

```
sudo gedit /etc/dhcp3/dhcpd.conf
```

you can either edit the existing file, or if you're only tftp'ing to one device you can usemy config here just change the ip address, subnet and client MAC (hardware ethernet) to the actual numbers being used on your system or edit your ethernet settings to match these:

```
option domain-name 192.168.1.50;
option domain-name-servers 192.168.1.50;
option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;
server-name 192.168.1.50;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.70 192.168.1.100;
  option routers 192.168.1.50;
}

host clientname {
  filename "tftpboot;
  server-name 192.168.1.50;
  next-server 192.168.1.50;
  hardware ethernet 08.00.50.a4.34.72;
  fixed-address 192.168.1.70;
}
```

one thig I've learned is it doesn't matter which "filename" is in dhcpd.conf but "hardware ethernet" has to be right or nothing but timeouts.


place your image/rootfs into /var/lib/tftp

I'm tftp'ing rootfs and kernel to an embedded device running uboot bootloader, so I access the bootloader via mini/pico com and use the tftp command: 


```
tftp <address> <filename>
```


"address" is the location in memory where you want to load the data. "filename" is the name of the file or image you want to retrieve


example:


```
Star Equuleus # tftp 200000 rootfs.jffs2                                        
Check Link Status ..Up                                                          
Waiting 3 seconds ..                                                            
TFTP from server 192.168.1.50; our IP address is 192.168.1.70                   
Filename 'rootfs.jffs2'.                                                        
Load address: 0x200000                                                          
Loading: #################################################################      
         #################################################################      
         #################################################################      
         #################################################################      
         #################################################################      
         #################################################################      
         #################################################################      
         #################################################################      
         ##################                                                     
done                                                                            
Bytes transferred = 2752512 (2a0000 hex)
```


then tftp the kernel to your location of choice:


```
Star Equuleus # tftp 60000 zImage                                               
Check Link Status ...Up                                                         
Waiting 3 seconds ..                                                            
TFTP from server 192.168.1.50; our IP address is 192.168.1.70                   
Filename 'zImage'.                                                              
Load address: 0x60000                                                           
Loading: #################################################################      
         #################################################################      
         ##############################################################         
done                                                                            
Bytes transferred = 978824 (eef88 hex) 
```


then go <kernel memory location>:


```
Star Equuleus # go 60000                                                        
## Starting application at 0x00060000 ...                                       
Uncompressing Linux.............................................................

```


hope this helps someone. it'll help me if I ever forget again!!!:):P

---

### Post by Kneegrowplease on 2012-05-21
can a mod or admin please change the title of this thread to:


"how to tftp a kernel to an embedded device running uboot"


then please remove this reply.

---

