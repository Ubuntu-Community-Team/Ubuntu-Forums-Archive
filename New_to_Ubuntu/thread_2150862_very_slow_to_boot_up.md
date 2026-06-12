---
title: "very slow to boot up"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by MikeJunker on 2013-06-02
I just installed Lubuntu on my wife's old netbook, a Toshiba NB205, and it boots up now incredibly slowly.  Like 5+ minutes.  once it gets going everything is fine.  I'd appreciate any guidance anyone can offer on how to sort it out.

---

### Post by techvish81 on 2013-06-02
please give some details about your setup, i.e installation, system hardware version of lubuntu etc.

---

### Post by Bucky Ball on 2013-06-02
Welcome to the forum.

> **techvish81 said:**
> please give some details about your setup, i.e installation, system hardware version of lubuntu etc.

Yes, and when you boot, as soon as you get to the desktop copy and paste 'dmesg' in to a terminal (Applications>Accessories>Terminal) and hit return. Look for anything that might be holding it up.

The other thing to try is to boot from the recovery kernel (second on the list at boot) and keep an eye out for where it stalls. You should get a message then. If it makes it to the recovery options after five minutes, choose to drop to a terminal and run dmesg from there. Look for anomalies.

---

### Post by MikeJunker on 2013-06-02
Like I said, I'm using a Toshiba NB205 netbook (There's a review with specifications here:[http://www.laptopmag.com/review/laptops/toshiba-mini-nb-205.aspx](http://www.laptopmag.com/review/laptops/toshiba-mini-nb-205.aspx))

I downloaded and installed the current iso from lubuntu.net, presumably 13.04, but I don't know that it said anywhere.  I'm happy to check if you can tell me where to look.  

I didn't do anything fancy with the install, no partition or anything else, just wiped out windows and put in Lubuntu.

---

### Post by MikeJunker on 2013-06-02
Here's what I get when I run dmesg.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-23-generic (buildd@aatxe) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #34-Ubuntu SMP Wed May 29 20:24:54 UTC 2013 (Ubuntu 3.8.0-23.34-generic 3.8.11)
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
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f6cffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003f6d0000-0x000000003f6e1fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000003f6e2000-0x000000003f6e2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003f6e3000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: TOSHIBA TOSHIBA NB205/KAVAA, BIOS V2.10 06/22/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3f6d0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] total RAM covered: 1015M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000f7a70-0x000f7a7f] mapped at [c00f7a70]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x36170000-0x370affff]
[    0.000000] ACPI: RSDP 000f79f0 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT 3f6d50b0 0008C (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3f6e1bd2 000F4 (v03 INTEL  CALISTGA 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 3f6d645c 0B702 (v01 TOSCPL CALISTGA 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 3f6e2fc0 00040
[    0.000000] ACPI: APIC 3f6e1cc6 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 3f6e1d2e 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 3f6e1d66 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 3f6e1da2 00032 (v01 PTLTD  CALISTGA 06040000  PTL 00000001)
[    0.000000] ACPI: TMOR 3f6e1dd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 3f6e1dfa 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 3f6e1f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f6e1fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f6d6252 0020A (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d5698 0021F (v02  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d5632 00066 (v02  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f6d513c 004F6 (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 122MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3f6cffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3f6cffff]
[    0.000000] On node 0 totalpages: 259679
[    0.000000] free_area_init_node: node 0, pgdat c18f6100, node_mem_map f740d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 246 pages used for memmap
[    0.000000]   HighMem zone: 31196 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73eb000 s35008 r0 d22336 u57344
[    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257649
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-23-generic root=UUID=103c0470-2b49-4b9d-b201-2f7392e36c17 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2078208 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f6d0)
[    0.000000] Memory: 1001012k/1039168k available (6251k kernel code, 37704k reserved, 2973k data, 788k init, 125768k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1903000 - 0xc19c8000   ( 788 kB)
[    0.000000]       .data : 0xc161afb0 - 0xc1902440   (2973 kB)
[    0.000000]       .text : 0xc1000000 - 0xc161afb0   (6251 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1662.447 MHz processor
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.89 BogoMIPS (lpj=6649788)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004088] Security Framework initialized
[    0.004108] AppArmor: AppArmor initialized
[    0.004112] Yama: becoming mindful.
[    0.004225] Mount-cache hash table entries: 512
[    0.004634] Initializing cgroup subsys cpuacct
[    0.004642] Initializing cgroup subsys memory
[    0.004660] Initializing cgroup subsys devices
[    0.004665] Initializing cgroup subsys freezer
[    0.004671] Initializing cgroup subsys blkio
[    0.004676] Initializing cgroup subsys perf_event
[    0.004684] Initializing cgroup subsys hugetlb
[    0.004741] CPU: Physical Processor ID: 0
[    0.004746] CPU: Processor Core ID: 0
[    0.004752] mce: CPU supports 5 MCE banks
[    0.004769] CPU0: Thermal monitoring enabled (TM2)
[    0.004776] process: using mwait in idle threads
[    0.004794] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
[    0.004794] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
[    0.004794] tlb_flushall_shift: 6
[    0.005168] Freeing SMP alternatives: 24k freed
[    0.009792] ACPI: Core revision 20121018
[    0.020053] ftrace: allocating 26119 entries in 52 pages
[    0.040183] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040685] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081604] smpboot: CPU0: Intel(R) Atom(TM) CPU N280   @ 1.66GHz (fam: 06, model: 1c, stepping: 02)
[    0.084000] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
[    0.084000] ... version:                3
[    0.084000] ... bit width:              40
[    0.084000] ... generic registers:      2
[    0.084000] ... value mask:             000000ffffffffff
[    0.084000] ... max period:             000000007fffffff
[    0.084000] ... fixed-purpose events:   3
[    0.084000] ... event mask:             0000000700000003
[    0.084000] CPU 1 irqstacks, hard=f5cd8000 soft=f5cda000
[    0.084000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.096056] Brought up 2 CPUs
[    0.096069] smpboot: Total of 2 processors activated (6649.78 BogoMIPS)
[    0.096245] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.096833] devtmpfs: initialized
[    0.096833] EVM: security.selinux
[    0.096833] EVM: security.SMACK64
[    0.096833] EVM: security.capability
[    0.100130] PM: Registering ACPI NVS region [mem 0x3f6e2000-0x3f6e2fff] (4096 bytes)
[    0.100401] regulator-dummy: no parameters
[    0.100545] NET: Registered protocol family 16
[    0.100901] EISA bus registered
[    0.101092] ACPI: bus type pci registered
[    0.101228] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.101236] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.101240] PCI: Using MMCONFIG for extended config space
[    0.101244] PCI: Using configuration type 1 for base access
[    0.104257] bio: create slab <bio-0> at 0
[    0.104257] ACPI: Added _OSI(Module Device)
[    0.104257] ACPI: Added _OSI(Processor Device)
[    0.104257] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.104257] ACPI: Added _OSI(Processor Aggregator Device)
[    0.106845] ACPI: EC: Look up EC in DSDT
[    0.112635] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.113551] ACPI: SSDT 3f6d5f7b 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.114199] ACPI: Dynamic OEM Table Load:
[    0.114206] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.114537] ACPI: SSDT 3f6d58b7 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.115144] ACPI: Dynamic OEM Table Load:
[    0.115151] ACPI: SSDT   (null) 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.115731] ACPI: SSDT 3f6d617e 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.116379] ACPI: Dynamic OEM Table Load:
[    0.116386] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.116615] ACPI: SSDT 3f6d5ef6 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.117226] ACPI: Dynamic OEM Table Load:
[    0.117233] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.156417] ACPI: Interpreter enabled
[    0.156432] ACPI: (supports S0 S3 S4 S5)
[    0.156472] ACPI: Using IOAPIC for interrupt routing
[    0.245757] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.246055] ACPI: No dock devices found.
[    0.246069] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.246823] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.246832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.248603] PCI host bridge to bus 0000:00
[    0.248614] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.248621] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.248627] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.248634] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.248640] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.248646] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.248652] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.248658] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfebfffff]
[    0.248681] pci 0000:00:00.0: [8086:27ac] type 00 class 0x060000
[    0.248751] pci 0000:00:02.0: [8086:27ae] type 00 class 0x030000
[    0.248770] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf007ffff]
[    0.248781] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.248792] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.248803] pci 0000:00:02.0: reg 1c: [mem 0xf0200000-0xf023ffff]
[    0.248861] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
[    0.248877] pci 0000:00:02.1: reg 10: [mem 0xf0080000-0xf00fffff]
[    0.249005] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.249037] pci 0000:00:1b.0: reg 10: [mem 0xf0440000-0xf0443fff 64bit]
[    0.249161] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.249208] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.249337] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.249386] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.249514] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.249563] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
[    0.249691] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.249739] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.249867] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.249916] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.249985] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.250045] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.250114] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.250184] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.250252] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.250312] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.250380] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.250454] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.250486] pci 0000:00:1d.7: reg 10: [mem 0xf0444000-0xf04443ff]
[    0.250615] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.250654] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.250778] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
[    0.250897] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.250908] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.250917] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.250925] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 007f)
[    0.250934] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.250999] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.251023] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.251041] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.251058] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.251075] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.251093] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.251163] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
[    0.251193] pci 0000:00:1f.2: reg 10: [io  0x18c8-0x18cf]
[    0.251210] pci 0000:00:1f.2: reg 14: [io  0x18c0-0x18c3]
[    0.251227] pci 0000:00:1f.2: reg 18: [io  0x18a8-0x18af]
[    0.251244] pci 0000:00:1f.2: reg 1c: [io  0x180c-0x180f]
[    0.251261] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
[    0.251279] pci 0000:00:1f.2: reg 24: [mem 0xf0444400-0xf04447ff]
[    0.251348] pci 0000:00:1f.2: PME# supported from D3hot
[    0.251381] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.251459] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.251587] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.251724] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.251778] pci 0000:03:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
[    0.252032] pci 0000:03:00.0: supports D1
[    0.252039] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.260060] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.260081] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.260271] pci 0000:04:00.0: [10ec:8136] type 00 class 0x020000
[    0.260343] pci 0000:04:00.0: reg 10: [io  0x2000-0x20ff]
[    0.260464] pci 0000:04:00.0: reg 18: [mem 0xf0510000-0xf0510fff 64bit pref]
[    0.260541] pci 0000:04:00.0: reg 20: [mem 0xf0500000-0xf050ffff 64bit pref]
[    0.260592] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.260869] pci 0000:04:00.0: supports D1 D2
[    0.260875] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.261068] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.261078] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.261094] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.261170] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.261282] pci 0000:00:1e.0: PCI bridge to [bus 06] (subtractive decode)
[    0.261301] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.261307] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.261314] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.261320] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.261326] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.261333] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.261339] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.261380] pci_bus 0000:00: on NUMA node 0
[    0.261427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.261553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.261672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.261789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.261966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.262370]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.262376]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.264968] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.265101] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.265227] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.265354] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.265482] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.265610] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.265737] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.265863] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.266134] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.266134] vgaarb: loaded
[    0.266134] vgaarb: bridge control possible 0000:00:02.0
[    0.266134] SCSI subsystem initialized
[    0.266134] ACPI: bus type scsi registered
[    0.266134] libata version 3.00 loaded.
[    0.266134] ACPI: bus type usb registered
[    0.266134] usbcore: registered new interface driver usbfs
[    0.266134] usbcore: registered new interface driver hub
[    0.266134] usbcore: registered new device driver usb
[    0.266134] PCI: Using ACPI for IRQ routing
[    0.276488] PCI: pci_cache_line_size set to 64 bytes
[    0.276616] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.276623] e820: reserve RAM buffer [mem 0x3f6d0000-0x3fffffff]
[    0.276870] NetLabel: Initializing
[    0.276876] NetLabel:  domain hash size = 128
[    0.276879] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.276904] NetLabel:  unlabeled traffic allowed by default
[    0.276952] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.276952] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.276952] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.280040] Switching to clocksource hpet
[    0.295401] AppArmor: AppArmor Filesystem Enabled
[    0.295476] pnp: PnP ACPI init
[    0.295510] ACPI: bus type pnp registered
[    0.295771] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.295782] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.295789] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.295796] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.295803] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.295810] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.295817] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.295824] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.295835] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296405] pnp 00:01: [dma 4]
[    0.296481] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.296727] system 00:02: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.296737] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.296844] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.296980] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.296989] system 00:04: [io  0x1000-0x107f] has been reserved
[    0.296996] system 00:04: [io  0x1180-0x11bf] has been reserved
[    0.297003] system 00:04: [io  0xfe00] has been reserved
[    0.297010] system 00:04: [io  0xff2c-0xff7f] has been reserved
[    0.297018] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.297104] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.324221] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.324318] pnp 00:07: Plug and Play ACPI device, IDs AUI0311 SYN0700 SYN0002 PNP0f13 (active)
[    0.324391] pnp: PnP ACPI: found 8 devices
[    0.324397] ACPI: ACPI bus type pnp unregistered
[    0.324404] PnPBIOS: Disabled by ACPI PNP
[    0.365027] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.365040] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.365048] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.365066] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.365074] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.365093] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x001fffff] to [bus 04] add_size 400000
[    0.365111] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.365118] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000
[    0.365126] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 05] add_size 200000
[    0.365154] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.365162] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.365169] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.365176] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x001fffff] get_res_add_size add_size 400000
[    0.365183] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.365190] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.365197] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.365204] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.365210] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.365225] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.365235] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.365245] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[    0.365254] pci 0000:00:1c.2: BAR 14: assigned [mem 0x40600000-0x40afffff]
[    0.365263] pci 0000:00:1c.3: BAR 14: assigned [mem 0x40b00000-0x40cfffff]
[    0.365273] pci 0000:00:1c.3: BAR 15: assigned [mem 0x40d00000-0x40efffff 64bit pref]
[    0.365284] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.365293] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.365303] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.365312] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.365321] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.365332] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.365342] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.365355] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.365362] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.365373] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.365383] pci 0000:00:1c.1:   bridge window [mem 0x40400000-0x405fffff 64bit pref]
[    0.365398] pci 0000:04:00.0: BAR 6: assigned [mem 0xf0520000-0xf053ffff pref]
[    0.365405] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.365412] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.365423] pci 0000:00:1c.2:   bridge window [mem 0x40600000-0x40afffff]
[    0.365433] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.365445] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.365452] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.365463] pci 0000:00:1c.3:   bridge window [mem 0x40b00000-0x40cfffff]
[    0.365473] pci 0000:00:1c.3:   bridge window [mem 0x40d00000-0x40efffff 64bit pref]
[    0.365485] pci 0000:00:1e.0: PCI bridge to [bus 06]
[    0.365599] pci 0000:00:1e.0: setting latency timer to 64
[    0.365609] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.365616] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.365622] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.365628] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.365635] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.365641] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.365647] pci_bus 0000:00: resource 10 [mem 0x40000000-0xfebfffff]
[    0.365654] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.365660] pci_bus 0000:02: resource 1 [mem 0x40000000-0x401fffff]
[    0.365666] pci_bus 0000:02: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.365673] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.365679] pci_bus 0000:03: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.365686] pci_bus 0000:03: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[    0.365692] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.365698] pci_bus 0000:04: resource 1 [mem 0x40600000-0x40afffff]
[    0.365705] pci_bus 0000:04: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.365711] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.365717] pci_bus 0000:05: resource 1 [mem 0x40b00000-0x40cfffff]
[    0.365724] pci_bus 0000:05: resource 2 [mem 0x40d00000-0x40efffff 64bit pref]
[    0.365731] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.365737] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.365743] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.365749] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.365755] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.365761] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.365768] pci_bus 0000:06: resource 10 [mem 0x40000000-0xfebfffff]
[    0.365847] NET: Registered protocol family 2
[    0.366147] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.366208] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.366265] TCP: Hash tables configured (established 8192 bind 8192)
[    0.366311] TCP: reno registered
[    0.366319] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.366336] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.366464] NET: Registered protocol family 1
[    0.366498] pci 0000:00:02.0: Boot video device
[    0.366747] PCI: CLS 64 bytes, default 64
[    0.366869] Trying to unpack rootfs image as initramfs...
[    1.024422] Freeing initrd memory: 15616k freed
[    1.038692] Simple Boot Flag at 0x36 set to 0x1
[    1.039340] Initialise module verification
[    1.039435] audit: initializing netlink socket (disabled)
[    1.039461] type=2000 audit(1370197401.036:1): initialized
[    1.085663] bounce pool size: 64 pages
[    1.085690] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.089514] VFS: Disk quotas dquot_6.5.2
[    1.089642] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.091100] fuse init (API version 7.20)
[    1.091325] msgmni has been set to 1740
[    1.092492] Key type asymmetric registered
[    1.092501] Asymmetric key parser 'x509' registered
[    1.092612] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.092686] io scheduler noop registered
[    1.092694] io scheduler deadline registered (default)
[    1.092713] io scheduler cfq registered
[    1.093032] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.093222] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.093407] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.093584] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.093759] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.093814] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.093938] intel_idle: MWAIT substates: 0x20220
[    1.093959] intel_idle: v0.4 model 0x1C
[    1.093964] intel_idle: lapic_timer_reliable_states 0x2
[    1.093970] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
[    1.111319] ACPI: AC Adapter [ACAD] (on-line)
[    1.111475] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.111519] ACPI: Lid Switch [LID0]
[    1.111614] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.111623] ACPI: Power Button [PWRB]
[    1.111744] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.111753] ACPI: Power Button [PWRF]
[    1.111915] ACPI: Requesting acpi_cpufreq
[    1.180582] GHES: HEST is not enabled!
[    1.180776] isapnp: Scanning for PnP cards...
[    1.180867] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.477039] ACPI: Battery Slot [BAT1] (battery present)
[    1.477288] Linux agpgart interface v0.103
[    1.477468] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.477594] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.477725] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.477985] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.482687] brd: module loaded
[    1.485129] loop: module loaded
[    1.485595] ata_piix 0000:00:1f.1: version 2.13
[    1.485697] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.486465] scsi0 : ata_piix
[    1.487389] scsi1 : ata_piix
[    1.487524] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.487533] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.488780] libphy: Fixed MDIO Bus: probed
[    1.489100] tun: Universal TUN/TAP device driver, 1.6
[    1.489105] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.489334] PPP generic driver version 2.4.2
[    1.489487] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.489494] ehci-pci: EHCI PCI platform driver
[    1.489572] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.489583] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.489600] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.489630] ehci-pci 0000:00:1d.7: debug port 1
[    1.493556] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.493617] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf0444000
[    1.493860] ata2: port disabled--ignoring
[    1.504044] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.504099] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.504108] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.504116] usb usb1: Product: EHCI Host Controller
[    1.504123] usb usb1: Manufacturer: Linux 3.8.0-23-generic ehci_hcd
[    1.504130] usb usb1: SerialNumber: 0000:00:1d.7
[    1.504468] hub 1-0:1.0: USB hub found
[    1.504483] hub 1-0:1.0: 8 ports detected
[    1.505259] ehci-platform: EHCI generic platform driver
[    1.505298] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.505366] uhci_hcd: USB Universal Host Controller Interface driver
[    1.505429] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.505439] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.505457] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.505509] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.505608] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.505617] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.505624] usb usb2: Product: UHCI Host Controller
[    1.505631] usb usb2: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    1.505639] usb usb2: SerialNumber: 0000:00:1d.0
[    1.505953] hub 2-0:1.0: USB hub found
[    1.505968] hub 2-0:1.0: 2 ports detected
[    1.506240] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.506250] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.506265] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.506335] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.506432] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.506441] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.506448] usb usb3: Product: UHCI Host Controller
[    1.506456] usb usb3: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    1.506463] usb usb3: SerialNumber: 0000:00:1d.1
[    1.506751] hub 3-0:1.0: USB hub found
[    1.506766] hub 3-0:1.0: 2 ports detected
[    1.507032] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.507042] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.507057] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.507125] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.507233] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.507242] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.507250] usb usb4: Product: UHCI Host Controller
[    1.507257] usb usb4: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    1.507264] usb usb4: SerialNumber: 0000:00:1d.2
[    1.507553] hub 4-0:1.0: USB hub found
[    1.507568] hub 4-0:1.0: 2 ports detected
[    1.507867] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.507877] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.507892] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.507962] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.508099] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.508108] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.508115] usb usb5: Product: UHCI Host Controller
[    1.508123] usb usb5: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    1.508130] usb usb5: SerialNumber: 0000:00:1d.3
[    1.508429] hub 5-0:1.0: USB hub found
[    1.508444] hub 5-0:1.0: 2 ports detected
[    1.508933] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.534629] isapnp: No Plug & Play device found
[    1.570924] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.570943] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.571293] mousedev: PS/2 mouse device common for all mice
[    1.575044] rtc_cmos 00:05: RTC can wake from S4
[    1.575292] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.575340] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.575567] device-mapper: uevent: version 1.0.3
[    1.575751] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    1.575822] EISA: Probing bus 0 at eisa.0
[    1.575832] EISA: Cannot allocate resource for mainboard
[    1.575841] Cannot allocate resource for EISA slot 1
[    1.575848] Cannot allocate resource for EISA slot 2
[    1.575852] Cannot allocate resource for EISA slot 3
[    1.575857] Cannot allocate resource for EISA slot 4
[    1.575862] Cannot allocate resource for EISA slot 5
[    1.575866] Cannot allocate resource for EISA slot 6
[    1.575871] Cannot allocate resource for EISA slot 7
[    1.575876] Cannot allocate resource for EISA slot 8
[    1.575880] EISA: Detected 0 cards.
[    1.575898] cpufreq-nforce2: No nForce2 chipset.
[    1.575994] cpuidle: using governor ladder
[    1.576175] cpuidle: using governor menu
[    1.576184] ledtrig-cpu: registered to indicate activity on CPUs
[    1.576189] EFI Variables Facility v0.08 2004-May-17
[    1.576768] ashmem: initialized
[    1.577093] TCP: cubic registered
[    1.577365] NET: Registered protocol family 10
[    1.577772] NET: Registered protocol family 17
[    1.577799] Key type dns_resolver registered
[    1.578198] Using IPI No-Shortcut mode
[    1.578490] Loading module verification certificates
[    1.590277] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d2833f1699a39f5a097a0653bde4b9d83163415d'
[    1.590311] registered taskstats version 1
[    1.596808] Key type trusted registered
[    1.602950] Key type encrypted registered
[    1.610295] rtc_cmos 00:05: setting system clock to 2013-06-02 18:23:22 UTC (1370197402)
[    1.611262] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.611269] EDD information not available.
[    1.627036] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.648330] Freeing unused kernel memory: 788k freed
[    1.648922] Write protecting the kernel text: 6252k
[    1.649055] Write protecting the kernel read-only data: 2436k
[    1.649060] NX-protecting the kernel data: 3988k
[    1.684065] udevd[99]: starting version 175
[    1.877599] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.878094] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.878682] r8169 0000:04:00.0 eth0: RTL8102e at 0xf8420000, 00:26:22:37:df:a8, XID 04c00000 IRQ 44
[    1.980247] Disabling lock debugging due to kernel taint
[    1.988371] ahci 0000:00:1f.2: version 3.0
[    1.988512] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.988677] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.988692] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.988706] ahci 0000:00:1f.2: setting latency timer to 64
[    1.990780] scsi2 : ahci
[    1.994790] scsi3 : ahci
[    1.995107] scsi4 : ahci
[    1.995383] scsi5 : ahci
[    1.995571] ata3: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444500 irq 45
[    1.995581] ata4: DUMMY
[    1.995590] ata5: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444600 irq 45
[    1.995597] ata6: DUMMY
[    2.312136] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.312198] ata5: SATA link down (SStatus 0 SControl 300)
[    2.312890] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.367446] ata3.00: ATA-8: TOSHIBA MK1655GSX, FG011M, max UDMA/100
[    2.367456] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.368773] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.369021] ata3.00: configured for UDMA/100
[    2.369414] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1655GS FG01 PQ: 0 ANSI: 5
[    2.370105] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.370153] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.370553] sd 2:0:0:0: [sda] Write Protect is off
[    2.370567] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.370676] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.096173]  sda: sda1 sda2 < sda5 >
[    4.097325] sd 2:0:0:0: [sda] Attached SCSI disk
[   32.061299] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  328.097309] Adding 1037308k swap on /dev/sda5.  Priority:-1 extents:1 across:1037308k 
[  329.075050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  329.157433] udevd[332]: starting version 175
[  329.452883] lp: driver loaded but no devices found
[  329.545632] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  329.587509] [drm] Initialized drm 1.1.0 20060810
[  329.796321] acpi device:00: registered as cooling_device2
[  329.796467] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  329.796833] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[  330.008602] wmi: Mapper loaded
[  330.139568] cfg80211: Calling CRDA to update world regulatory domain
[  330.347461] type=1400 audit(1370197731.231:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
[  330.349475] type=1400 audit(1370197731.235:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[  330.350270] type=1400 audit(1370197731.235:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[  330.381158] type=1400 audit(1370197731.267:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=556 comm="apparmor_parser"
[  330.417749] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[  330.418016] input: Toshiba input device as /devices/virtual/input/input5
[  330.464254] intel_rng: FWH not detected
[  330.568690] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[  330.568710] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  330.568719] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[  330.568732] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  330.568738] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[  330.568750] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  330.568756] lpc_ich: Resource conflict(s) found affecting gpio_ich
[  330.721781] leds_ss4200: no LED devices found
[  330.875944] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
[  331.016824] Bluetooth: Core ver 2.16
[  331.016886] NET: Registered protocol family 31
[  331.016893] Bluetooth: HCI device and connection manager initialized
[  331.016912] Bluetooth: HCI socket layer initialized
[  331.016924] Bluetooth: L2CAP socket layer initialized
[  331.016944] Bluetooth: SCO socket layer initialized
[  331.058188] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  331.058198] Bluetooth: BNEP filters: protocol multicast
[  331.058221] Bluetooth: BNEP socket layer initialized
[  331.140265] i915 0000:00:02.0: setting latency timer to 64
[  331.152423] Bluetooth: RFCOMM TTY layer initialized
[  331.152462] Bluetooth: RFCOMM socket layer initialized
[  331.152470] Bluetooth: RFCOMM ver 1.11
[  331.157190] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  331.157200] [drm] Driver supports precise vblank timestamp query.
[  331.157370] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  331.413687] [drm] initialized overlay support
[  331.614290] ath: phy0: ASPM enabled: 0x43
[  331.614295] ath: EEPROM regdomain: 0x65
[  331.614297] ath: EEPROM indicates we should expect a direct regpair map
[  331.614302] ath: Country alpha2 being used: 00
[  331.614304] ath: Regpair used: 0x65
[  331.803099] fbcon: inteldrmfb (fb0) is primary device
[  331.803921] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  331.805978] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8980000, irq=17
[  331.992801] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
[  332.014320] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[  332.074112] cfg80211: World regulatory domain updated:
[  332.074114] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  332.074119] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  332.074122] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  332.074125] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  332.074127] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  332.074130] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  332.140243] Console: switching to colour frame buffer device 128x37
[  332.147406] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[  332.147411] i915 0000:00:02.0: registered panic notifier
[  332.147429] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  332.147714] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[  332.231717] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[  332.234214] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[  332.665690] init: failsafe main process (698) killed by TERM signal
[  332.706323] vesafb: mode is 800x600x32, linelength=3200, pages=0
[  332.706333] vesafb: scrolling: redraw
[  332.706342] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[  332.709500] vesafb: framebuffer at 0xd0000000, mapped to 0xf8d80000, using 1920k, total 1920k
[  332.709728] fb1: VESA VGA frame buffer device
[  332.898869] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[  332.977725] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[  335.037223] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  335.039027] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  335.061327] r8169 0000:04:00.0 eth0: link down
[  335.061418] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  335.062598] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  336.471671] type=1400 audit(1370197737.355:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=881 comm="apparmor_parser"
[  336.473517] type=1400 audit(1370197737.359:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=881 comm="apparmor_parser"
[  336.474357] type=1400 audit(1370197737.359:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=881 comm="apparmor_parser"
[  336.474844] type=1400 audit(1370197737.359:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=880 comm="apparmor_parser"
[  336.476103] type=1400 audit(1370197737.363:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=880 comm="apparmor_parser"
[  336.490180] type=1400 audit(1370197737.375:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=883 comm="apparmor_parser"
[  336.491949] type=1400 audit(1370197737.375:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=883 comm="apparmor_parser"
[  336.502007] type=1400 audit(1370197737.387:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=884 comm="apparmor_parser"
[  336.510317] type=1400 audit(1370197737.395:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=882 comm="apparmor_parser"
[  336.518647] type=1400 audit(1370197737.403:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=886 comm="apparmor_parser"
[  337.294531] wlan0: authenticate with 3c:ea:4f:e2:03:89
[  337.299188] wlan0: send auth to 3c:ea:4f:e2:03:89 (try 1/3)
[  337.302060] wlan0: authenticated
[  337.302530] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  337.302544] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  337.304112] wlan0: associate with 3c:ea:4f:e2:03:89 (try 1/3)
[  337.306444] wlan0: RX AssocResp from 3c:ea:4f:e2:03:89 (capab=0x431 status=0 aid=3)
[  337.306563] wlan0: associated
[  337.306657] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  337.306805] cfg80211: Calling CRDA for country: US
[  337.332771] ath: regdomain 0x8348 updated by CountryIE
[  337.332782] ath: EEPROM regdomain: 0x8348
[  337.332788] ath: EEPROM indicates we should expect a country code
[  337.332794] ath: doing EEPROM country->regdmn map search
[  337.332801] ath: country maps to regdmn code: 0x3a
[  337.332807] ath: Country alpha2 being used: US
[  337.332812] ath: Regpair used: 0x3a
[  337.332866] cfg80211: Regulatory domain changed to country: US
[  337.332873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  337.332880] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  337.332887] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  337.332895] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  337.332902] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  337.332909] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  337.332916] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
```

---

### Post by MikeJunker on 2013-06-02
You linix folks are more whimsical than I realized.  I wouldn't expect to see emoticons in a windows log.

---

### Post by ajgreeny on 2013-06-02
Hold shift down at your next boot from the time you press the power button to start, and when you see the grub menu hit the "E" key to edit the entry. Using cursor keys move to the "quiet splash" line and delete just those two words.  Now use Ctrl+X to boot and you will see the text that is normally hidden, telling you what is going on.  From this you may be able to see at what activity the system boot lag starts.

---

### Post by MikeJunker on 2013-06-02
That didn't work.  Holding down shift just held me at the toshiba splash screen.  I could hit F2 for the setup menu or F12 for the boot menu.  Were one of those what you meant?

---

### Post by Bucky Ball on 2013-06-02
Are you getting a list of OSs (kernels) to boot when you boot? If so, you don't need the shift. 

Hit shift right after the BIOS screen at boot (not right from the start). You don't have much time but you should see the 'Toshiba' BIOS screen flash up and immediately after that, start mashing. I basically just mash mine (tap it repeatedly) until the list screen comes up.

Without editing the kernel, as suggested, once at the list screen you can boot to the recovery kernel (second on the list) to achieve the same result as editing the 'quiet splash' out. Recovery will give you the text you generally don't see. Quicker, easier. As per my previous post.

Also, please use [code] tags for your terminal output. They can be found at 'Go Advanced' when editing a post.

---

### Post by MikeJunker on 2013-06-02
I'm not getting  a list of OSs. The only thing I've got on this PC is lubuntu.

---

### Post by pqwoerituytrueiwoq on 2013-06-02
It is complaining about your swap partition, check the [FONT=courier new]UUID[/FONT] of it in [FONT=courier new]/etc/fstab[/FONT] and [FONT=courier new]/etc/initramfs-tools/conf.d/resume[/FONT]
it should match the uuid in [FONT=courier new]sudo blkid | grep swap[/FONT]
[[IMG]http://i.imgur.com/BbQRQP0s.png[/IMG]](http://i.imgur.com/BbQRQP0.png)

---

### Post by Bucky Ball on 2013-06-02
> **MikeJunker said:**
> I'm not getting  a list of OSs. The only thing I've got on this PC is lubuntu.

Forget about the OSs. Doesn't matter. You should still be getting a list of the kernels you have installed, in this instance probably just the one. Directly under that you will find the recovery version of that same kernel. 

Try this. Open a terminal and:

```
sudo nano /etc/default/grub
```

Once you're there look for these headings and change them to *_exactly_* what I have here:

```
GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
```

Reboot. You should now get to the list and it will stay there for ten seconds only unless you hit a key. Press the down arrow key once, (have a look and get familiar with the page). If you hit the down arrow once you should be ready to choose the second entry, the recovery kernel. Hit return and watch for errors. When/if you get to the recovery options screen, drop to shell and run 'dmesg'. You could also 'Fix broken packages' for the heck of it.

Just a note; might be an idea to backup /etc/default/grub file before tweaking in case you break it (unlikely if you follow instructions exactly but safer). Do this before tweaking:

```
sudo cp /etc/default/grub /etc/default/grub.backup
```

... or whatever tag you want to put on the end (.date). If you break it and want to revert:

```
sudo cp /etc/default/grub.backup /etc/default/grub
```

A heads up; if you want to tweak grub do it using the /etc/default/grub file. DO NOT edit the /boot/grub/grub.cfg directly unless it is specifically directed/necessary, which it rarely is. ;)

@ pqwoerituytrueiwoq: That is exactly the same entry I have for my grub, different UUID, naturally. What exactly is wrong with the UUID you have underlined? Am I missing something? Could you elaborate?

My /swap entry:

```
UUID=63d86782-bff4-41c1-924f-37d093fbe371       none    swap    sw      0       0
```

---

### Post by pqwoerituytrueiwoq on 2013-06-02
@Bucky 
that is the way is it supposed to be based on the dmesg output from the op there is likely a inconsistency there on there system

---

### Post by Bucky Ball on 2013-06-02
> **pqwoerituytrueiwoq said:**
> ... based on the dmesg output from the op there is likely a inconsistency there on there system

I see. Which part of the dmesg suggests that? I'm not seeing anything, but I'm no expert. ;)

@MikeJunker: Whimsical? Yes, it would be a sorry thing if the life of a computer junkie was all coffee, doughtnuts and coding ... I don't drink coffee, rarely eat doughnuts and know little about coding, but I do a lot of this between times :guitar:

Maybe you could also post the output of your fstab:

```
nano /etc/fstab
```

... and post back the result (in code tags, please).

---

### Post by pqwoerituytrueiwoq on 2013-06-02
See where the numbers take a large jump on the left, that is time passed in seconds```
[    4.097325] sd 2:0:0:0: [sda] Attached SCSI disk
[   32.061299] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  328.097309] Adding 1037308k swap on /dev/sda5.  Priority:-1 extents:1 across:1037308k 
[  329.075050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
```
This is from my dmesg at that point
```
[    6.913454] fb0: VESA VGA frame buffer device
[    7.283495] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.487258] Adding 16779888k swap on /dev/sdb6.  Priority:-1 extents:1 across:16779888k 
[    7.529383] udevd[482]: starting version 175
```

---

### Post by Bucky Ball on 2013-06-03
Is that a problem with /swap or sda1? It hits sda1 and halts then adds the swap in a second, or am I reading that the wrong way around. I'd be leaning more toward sda1. Well spotted!

---

### Post by pqwoerituytrueiwoq on 2013-06-03
it is taking too long to mound sda1, but the time to mount swap is ridiculous
i think it took almost 5 min to mount swap

i once had a issue like this back on 10.04 it was the cause of swap uuids in the resume file in my case
another method i use is bootchart, charts are saved to /var/log/bootchart/

---

### Post by Bucky Ball on 2013-06-03
> **pqwoerituytrueiwoq said:**
> it is taking too long to mound sda1, but the time to mount swap is ridiculous
i think it took almost 5 min to mount swap

i once had a issue like this back on 10.04 it was the cause of swap uuids in the resume file in my case
another method i use is bootchart, charts are saved to /var/log/bootchart/

Cheers. ;)

---

### Post by MikeJunker on 2013-06-03
> **pqwoerituytrueiwoq said:**
> It is complaining about your swap partition, check the [FONT=courier new]UUID[/FONT] of it in [FONT=courier new]/etc/fstab[/FONT] and [FONT=courier new]/etc/initramfs-tools/conf.d/resume[/FONT]
it should match the uuid in [FONT=courier new]sudo blkid | grep swap[/FONT]
[[IMG]http://i.imgur.com/BbQRQP0s.png[/IMG]]("http://i.imgur.com/BbQRQP0.png")

I'm gathering from what I understand of the conversation last night, that this is likely to be the most productive avenue of investigation.  I've got a little bit of time this morning before I need to head to work, and decided to see what I could figure out, and I think I'm going to need things pitched at a bit more of a absolute beginner level.

You're telling me to check a couple files, correct?  I looked through the file manager, and I don't seem to have the folders you're looking for.

I've got /etc/fstab.d/, but there's nothing in there.
I've got /etc/initramfs-tools/, but no conf.d within it.

I recognize the last item you told me to look at as a terminal command.  Should I be looking at the others with the terminal as well?

---

### Post by MikeJunker on 2013-06-03
> **Bucky Ball said:**
> Forget about the OSs. Doesn't matter. You should still be getting a list of the kernels you have installed, in this instance probably just the one. Directly under that you will find the recovery version of that same kernel. 


In fact, I don't get a list of kernels.  The Toshiba splash screen pops up for a second. Then about five minutes of black screen.  Then the lubuntu screen.

I should be able to do some tinkering tonight if you still think it would be productive to try it.

---

### Post by pqwoerituytrueiwoq on 2013-06-03
> **MikeJunker said:**
> I'm gathering from what I understand of the conversation last night, that this is likely to be the most productive avenue of investigation.  I've got a little bit of time this morning before I need to head to work, and decided to see what I could figure out, and I think I'm going to need things pitched at a bit more of a absolute beginner level.

You're telling me to check a couple files, correct?  I looked through the file manager, and I don't seem to have the folders you're looking for.

I've got /etc/fstab.d/, but there's nothing in there.
I've got /etc/initramfs-tools/, but no conf.d within it.

I recognize the last item you told me to look at as a terminal command.  Should I be looking at the others with the terminal as well?

it is /etc/fstab not /etc/fstab.d it is a file not a directory
if you could post the output of the 3 commands i used, that would help
```
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
sudo blkid | grep swap
```

---

### Post by MikeJunker on 2013-06-03
Ok, I think I can tinker a bit tonight.  Here's the results of the terminal commands you wanted me to run.

```
michael@michael-TOSHIBA-NB205:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=77fc7e11-83c5-45d3-9750-9790c5d79b17
michael@michael-TOSHIBA-NB205:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=103c0470-2b49-4b9d-b201-2f7392e36c17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=77fc7e11-83c5-45d3-9750-9790c5d79b17 none            swap    sw              0       0
michael@michael-TOSHIBA-NB205:~$ sudo blkid | grep swap
[sudo] password for michael: 
/dev/sda5: UUID="77fc7e11-83c5-45d3-9750-9790c5d79b17" TYPE="swap" 



```

---

### Post by pqwoerituytrueiwoq on 2013-06-04
well that is not the issue, that looks like it should
run 
[FONT=courier new]sudo rm /var/lib/ureadahead/pack[/FONT]
then reboot and see if that made a difference

---

### Post by Bucky Ball on 2013-06-04
Yep, the swap looks fine in fstab. 

Just after the Toshiba screen, are you mashing the shift key? That should get you to a list. If not, follow the instructions I have already given ('Try this' in post #12, edit /etc/fstab) and reboot.

---

### Post by MikeJunker on 2013-06-04
I'll go back and try some of your suggestions tonight, BuckyBall.

---

### Post by hpsgty on 2013-06-04
[COLOR=#000000]Hit shift right after the BIOS screen at boot (not right from the start). You don't have much time but you should see the 'Toshiba' BIOS screen flash up and immediately after that, start mashing. I basically just mash mine (tap it repeatedly) until the list screen comes up.[/COLOR]

---

### Post by MikeJunker on 2013-06-04
I managed to boot into recovery mode, and got a couple snapshots of first place it hung up.  Here's what was on screen at the time.
[ATTACH=CONFIG]243511[/ATTACH]

---

### Post by Bucky Ball on 2013-06-04
Okay, good. This particular hold up appears to be because it is looking for UUID number for a partition/drive that doesn't exist. When you open your fstab, look for the UUID that matches the one in your error message. For the moment, put a # at the beginning of that line and reboot. What happens? To change that file you'll need to issue sudo first so open it with:

```
sudo nano /etc/fstab
```

The odd thing is that it is pointing to your / partition, where the OS is actually stored. From your fstab:

```
# / was on /dev/sda1 during installation
UUID=103c0470-2b49-4b9d-b201-2f7392e36c17 /               ext4    errors=remount-ro 0       1
```

Before doing any of this, could you provide the output of:

```
sudo blkid
```

... also, please. Those UUIDs may have changed for some reason and need to be re-entered in the fstab. ;)

Are there any other points where it halts and gives and error?

---

### Post by pqwoerituytrueiwoq on 2013-06-04
odd if that partition did not exist under that uuid what is in [FONT=courier new]/boot/grub/grub.cfg[/FONT] it should have been able to even boot that far, the uuid of the [FONT=courier new]/boot[/FONT] partition or in this case [FONT=courier new]/[/FONT] as there is only 1 partition aside from windows and swap would be in the boot file
i suggest running [FONT=courier new]sudo smartctl -a /dev/sda[/FONT] and posted the output here, it would appear that your hdd vanished during boot, best make sure it is not failing and please use code tags or pastebin when you post the output
[PHP]```
Terminal output here
```[/PHP]

---

### Post by MikeJunker on 2013-06-07
Been busy the last couple nights, but I'm not gone.  I'll have a chance to try the latest advice this weekend.

---

