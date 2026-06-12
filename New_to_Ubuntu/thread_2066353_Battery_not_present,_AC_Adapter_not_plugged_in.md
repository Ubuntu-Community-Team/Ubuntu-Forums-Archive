---
title: "Battery not present, AC Adapter not plugged in"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Noor1101 on 2012-10-04
Hi, I'm wondering if someone can help me with this problem.

On Ubuntu 12.04 (32 bit) I installed kde-plasma a couple of days ago because I wasn't happy with Gnome/Unity. After adjusting the system tray settings so that it always shows the battery status, this worked fine for a couple of days. 

However, since I logged in this morning, the battery icon is an empty battery without a plug and with a red cross in front of it. When I click it, the status reads "Battery: Not present. AC Adapter: Not plugged in." (I have rebooted a couple of times but that's not fixed the problem.)

I searched for some answers online, and in Terminal/Konsole tried
```
cat /proc/acpi/battery/BAT1/state
```and
```
cat /proc/acpi/battery/BAT1/info
```and the - very short - reply to this reads:
```
noor@noor-EasyNote-MH35:~$ cat /proc/acpi/battery/BAT1/state
present:                 no
noor@noor-EasyNote-MH35:~$ cat /proc/acpi/battery/BAT1/info
present:                 no
```This is the reason why I'm starting this thread: I haven't come across it in any other forums/guides.

The battery definitely works because I can unplug it and the notebook keeps running, and the power supply definitely works because.. well I'm still online, aren't I?

Please note I've been using Linux/Ubuntu for only 1.5 months and I still find myself confused with certain terms. I'm eager to learn though!

Can anyone help me?
Thanks very much!

---

### Post by NikTh on 2012-10-04
Hi , 
With battery plugged 
is there any other entries inside /battery ? 

```
ls /proc/acpi/battery/
```Also try this 

```
sudo apt-get install acpi 
acpi -V 
```Thanks

---

### Post by Noor1101 on 2012-10-04
Thanks for your time!
No other batteries were found:

```
noor@noor-EasyNote-MH35:~$ ls /proc/acpi/battery/
BAT1
noor@noor-EasyNote-MH35:~$

```I succesfully installed acpi, like you said:
```
noor@noor-EasyNote-MH35:~$ sudo apt-get install acpi 
[sudo] password for noor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae libkdecorations4 libkwinglutils1
  wine-gecko1.4 libkwineffects1abi3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  acpi
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.3 kB of archives.
After this operation, 70.7 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/universe acpi i386 1.6-1 [13.3 kB]
Fetched 13.3 kB in 0s (55.2 kB/s)
Selecting previously unselected package acpi.
(Reading database ... 241690 files and directories currently installed.)
Unpacking acpi (from .../archives/acpi_1.6-1_i386.deb) ...
Processing triggers for man-db ...
Setting up acpi (1.6-1) ...

```And this is what I got with acpi -V:

```
noor@noor-EasyNote-MH35:~$ acpi -V
Adapter 0: off-line
Thermal 0: ok, 51.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 90.0 degrees C
Thermal 0: trip point 2 switches to mode active at temperature 60.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Fan 0 of 1
noor@noor-EasyNote-MH35:~$ 

```

---

### Post by NikTh on 2012-10-04
No , battery present. Weird. 

Try to reset you BIOS. I mean "Restore Defaults" settings. 

Also a good point would be the output of dmesg. 

```
dmesg >> dmesg.txt
```and with the text editor of Kubuntu , open it and copy-paste everything in here , between ```
 brackets. You know **[noparse][code]Here
```[/noparse]**

---

### Post by Noor1101 on 2012-10-04
Just to be sure, do you mean I should shut down my computer, turn it on, go to BIOS and search for "Restore Default" there? (And, again to be absolutely sure, by that I won't lose any data?)
(Sorry, I just want to be careful - don't really know what I'm doing half the time)


The dmesg.txt-file is as follows:

```
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7da0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7da0000 - 00000000b7da1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7da1000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: PACKARD BELL BV EasyNote MH35/PE1, BIOS PE14A04  02/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f86c0] f86c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000f8690 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT b7d97999 00094 (v01 PacBel PBNB000B 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b7d9fcc4 000F4 (v03 SiS    671MX    06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT b7d9b9c6 0428A (v01 PTLTD       671 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS b7da0fc0 00040
[    0.000000] ACPI: SLIC b7d9fdb8 00176 (v00 PacBel PBNB000B 06040000      00000000)
[    0.000000] ACPI: APIC b7d9ff2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG b7d9ff8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET b7d9ffc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SSDT b7d992d1 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d9922b 000A6 (v01  PmRef  Cpu7Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99185 000A6 (v01  PmRef  Cpu6Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d990df 000A6 (v01  PmRef  Cpu5Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99039 000A6 (v01  PmRef  Cpu4Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98f93 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98eed 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98e47 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d97a2d 0141A (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4de8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4100 pages used for memmap
[    0.000000]   HighMem zone: 520590 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=9b3867fe-5b6d-419c-98c6-e571f5a57d0a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d90)
[    0.000000] Memory: 2951184k/3012160k available (5818k kernel code, 60516k reserved, 2846k data, 740k init, 2098760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1831.780 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3663.56 BogoMIPS (lpj=7327120)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004060] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004100] Yama: becoming mindful.
[    0.004220] Mount-cache hash table entries: 512
[    0.004508] Initializing cgroup subsys cpuacct
[    0.004521] Initializing cgroup subsys memory
[    0.004538] Initializing cgroup subsys devices
[    0.004543] Initializing cgroup subsys freezer
[    0.004548] Initializing cgroup subsys blkio
[    0.004562] Initializing cgroup subsys perf_event
[    0.004619] CPU: Physical Processor ID: 0
[    0.004623] CPU: Processor Core ID: 0
[    0.004630] mce: CPU supports 6 MCE banks
[    0.004647] CPU0: Thermal monitoring enabled (TM2)
[    0.004654] using mwait in idle threads.
[    0.010859] ACPI: Core revision 20110623
[    0.020051] ftrace: allocating 26555 entries in 52 pages
[    0.024097] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024436] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065234] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f74cc000 soft=f74ce000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.156060] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156133] Brought up 2 CPUs
[    0.156139] Total of 2 processors activated (7327.36 BogoMIPS).
[    0.158831] devtmpfs: initialized
[    0.158831] EVM: security.selinux
[    0.158831] EVM: security.SMACK64
[    0.158831] EVM: security.capability
[    0.158831] PM: Registering ACPI NVS region at b7da0000 (4096 bytes)
[    0.161923] print_constraints: dummy: 
[    0.161969] RTC time: 17:15:22, date: 10/04/12
[    0.162054] NET: Registered protocol family 16
[    0.162206] Trying to unpack rootfs image as initramfs...
[    0.162347] EISA bus registered
[    0.162380] ACPI: bus type pci registered
[    0.162528] PCI: MMCONFIG for domain 0000 [bus 00-02] at [mem 0xe0000000-0xe02fffff] (base 0xe0000000)
[    0.162536] PCI: MMCONFIG at [mem 0xe0000000-0xe02fffff] reserved in E820
[    0.162540] PCI: Using MMCONFIG for extended config space
[    0.162544] PCI: Using configuration type 1 for base access
[    0.176162] bio: create slab <bio-0> at 0
[    0.176349] ACPI: Added _OSI(Module Device)
[    0.176355] ACPI: Added _OSI(Processor Device)
[    0.176360] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176365] ACPI: Added _OSI(Processor Aggregator Device)
[    0.178465] ACPI: EC: Look up EC in DSDT
[    0.185428] ACPI: SSDT b7d99deb 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.185983] ACPI: Dynamic OEM Table Load:
[    0.185991] ACPI: SSDT   (null) 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.188053] ACPI: SSDT b7d99530 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.188683] ACPI: Dynamic OEM Table Load:
[    0.188691] ACPI: SSDT   (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.232977] ACPI: SSDT b7d9a00a 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.233550] ACPI: Dynamic OEM Table Load:
[    0.233558] ACPI: SSDT   (null) 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.234089] ACPI: SSDT b7d99a48 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.234615] ACPI: Dynamic OEM Table Load:
[    0.234623] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.264561] ACPI: Interpreter enabled
[    0.264592] ACPI: (supports S0 S1 S3 S4 S5)
[    0.264638] ACPI: Using IOAPIC for interrupt routing
[    0.268775] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.271952] ACPI: Power Resource [QFAN] (off)
[    0.272396] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.272677] ACPI: No dock devices found.
[    0.272683] HEST: Table not found.
[    0.272696] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.273464] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.274872] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.274879] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.274885] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.274891] pci_root PNP0A03:00: host bridge window [mem 0xb8000000-0xffedffff]
[    0.274897] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.274904] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.274909] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.274915] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.274921] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.274958] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.274980] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.275086] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.275154] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.275295] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.275325] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.275342] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.275359] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.275376] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.275393] pci 0000:00:02.5: reg 20: [io  0x1080-0x108f]
[    0.275464] pci 0000:00:02.5: PME# supported from D3cold
[    0.275473] pci 0000:00:02.5: PME# disabled
[    0.275500] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.275523] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.275624] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.275647] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.275755] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.275782] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.275897] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.275905] pci 0000:00:03.3: PME# disabled
[    0.275941] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.275968] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.275985] pci 0000:00:04.0: reg 14: [io  0x1000-0x107f]
[    0.276103] pci 0000:00:04.0: supports D1 D2
[    0.276108] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.276116] pci 0000:00:04.0: PME# disabled
[    0.276145] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.276173] pci 0000:00:05.0: reg 10: [io  0x10c8-0x10cf]
[    0.276190] pci 0000:00:05.0: reg 14: [io  0x10bc-0x10bf]
[    0.276207] pci 0000:00:05.0: reg 18: [io  0x10c0-0x10c7]
[    0.276223] pci 0000:00:05.0: reg 1c: [io  0x10b8-0x10bb]
[    0.276240] pci 0000:00:05.0: reg 20: [io  0x10a0-0x10af]
[    0.276309] pci 0000:00:05.0: PME# supported from D3cold
[    0.276317] pci 0000:00:05.0: PME# disabled
[    0.276354] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.276489] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.276498] pci 0000:00:06.0: PME# disabled
[    0.276546] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.276680] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.276688] pci 0000:00:07.0: PME# disabled
[    0.276742] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.276774] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.276891] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.276900] pci 0000:00:0f.0: PME# disabled
[    0.276980] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.277008] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.277024] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.277039] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.277124] pci 0000:01:00.0: supports D1 D2
[    0.277188] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.277197] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.277206] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.277214] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.277299] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.277311] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.277320] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.277412] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.277457] pci_bus 0000:00: on NUMA node 0
[    0.277464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.278010]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.278018]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.278022] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.287771] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.287884] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.287993] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[    0.288110] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 9 10 11)
[    0.288249] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.288356] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.288463] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.288569] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.288886] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.288893] vgaarb: loaded
[    0.288897] vgaarb: bridge control possible 0000:01:00.0
[    0.289186] i2c-core: driver [aat2870] using legacy suspend method
[    0.289190] i2c-core: driver [aat2870] using legacy resume method
[    0.289377] SCSI subsystem initialized
[    0.289506] libata version 3.00 loaded.
[    0.289615] usbcore: registered new interface driver usbfs
[    0.289643] usbcore: registered new interface driver hub
[    0.289708] usbcore: registered new device driver usb
[    0.289922] PCI: Using ACPI for IRQ routing
[    0.289980] PCI: pci_cache_line_size set to 64 bytes
[    0.290092] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.290098] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.290342] NetLabel: Initializing
[    0.290347] NetLabel:  domain hash size = 128
[    0.290350] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.290375] NetLabel:  unlabeled traffic allowed by default
[    0.290486] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.290495] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.290506] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.296102] Switching to clocksource hpet
[    0.316279] AppArmor: AppArmor Filesystem Enabled
[    0.316346] pnp: PnP ACPI init
[    0.316389] ACPI: bus type pnp registered
[    0.317207] pnp 00:00: [bus 00-ff]
[    0.317214] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.317220] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.317226] pnp 00:00: [io  0x0d00-0xffff window]
[    0.317232] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.317238] pnp 00:00: [mem 0xb8000000-0xffedffff window]
[    0.317243] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.317249] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.317255] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.317260] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.317266] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.317271] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.317276] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.317282] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.317287] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.317292] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.317298] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.317303] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.317434] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.317789] pnp 00:01: [io  0x0000-0x000f]
[    0.317794] pnp 00:01: [io  0x0081-0x008f]
[    0.317799] pnp 00:01: [io  0x00c0-0x00df]
[    0.317804] pnp 00:01: [io  0x0480-0x048f]
[    0.317810] pnp 00:01: [dma 4]
[    0.317903] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.317964] pnp 00:02: [io  0x0070-0x0071]
[    0.318053] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.318075] pnp 00:03: [io  0x0061]
[    0.318159] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.318252] pnp 00:04: [io  0x8000-0x80be]
[    0.318258] pnp 00:04: [io  0x8100-0x812f]
[    0.318263] pnp 00:04: [io  0x0080]
[    0.318267] pnp 00:04: [io  0x04d0-0x04d1]
[    0.318272] pnp 00:04: [io  0xfe00]
[    0.318276] pnp 00:04: [io  0x002e]
[    0.318281] pnp 00:04: [io  0x002f]
[    0.318285] pnp 00:04: [io  0x0092]
[    0.318289] pnp 00:04: [io  0x0072-0x0073]
[    0.318294] pnp 00:04: [io  0x0078-0x0079]
[    0.318299] pnp 00:04: [io  0x0290-0x0297]
[    0.318304] pnp 00:04: [mem 0xe0000000-0xefffffff]
[    0.318309] pnp 00:04: [mem 0xfec00000-0xfeefffff]
[    0.318314] pnp 00:04: [mem 0xffb80000-0xffbfffff]
[    0.318319] pnp 00:04: [mem 0xffc00000-0xffc00fff]
[    0.318324] pnp 00:04: [mem 0xffe00000-0xffe00fff]
[    0.318329] pnp 00:04: [mem 0xffe80000-0xffefffff]
[    0.318485] system 00:04: [io  0x8000-0x80be] has been reserved
[    0.318492] system 00:04: [io  0x8100-0x812f] has been reserved
[    0.318500] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.318511] system 00:04: [io  0xfe00] has been reserved
[    0.318517] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.318526] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.318533] system 00:04: [mem 0xfec00000-0xfeefffff] could not be reserved
[    0.318540] system 00:04: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.318546] system 00:04: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.318553] system 00:04: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.318559] system 00:04: [mem 0xffe80000-0xffefffff] could not be reserved
[    0.318568] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.318616] pnp 00:05: [io  0x00f0-0x00ff]
[    0.318647] pnp 00:05: [irq 13]
[    0.318736] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.318760] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    0.318765] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    0.318770] pnp 00:06: [mem 0xffc00000-0xffc00fff]
[    0.318775] pnp 00:06: [mem 0xffe00000-0xffe00fff]
[    0.318863] pnp 00:06: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.319013] pnp 00:07: [irq 0 disabled]
[    0.319024] pnp 00:07: [irq 8]
[    0.319035] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.319136] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.319160] pnp 00:08: [io  0x0060]
[    0.319165] pnp 00:08: [io  0x0064]
[    0.319176] pnp 00:08: [irq 1]
[    0.319267] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.319294] pnp 00:09: [irq 12]
[    0.319392] pnp 00:09: Plug and Play ACPI device, IDs SYN101f PNP0f13 (active)
[    0.319718] pnp: PnP ACPI: found 10 devices
[    0.319723] ACPI: ACPI bus type pnp unregistered
[    0.319731] PnPBIOS: Disabled by ACPI PNP
[    0.358651] PCI: max bus depth: 1 pci_try_num: 2
[    0.358719] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.358727] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.358734] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.358745] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.358753] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.358766] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.358772] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.358782] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.358791] pci 0000:00:06.0:   bridge window [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.358804] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.358841] pci 0000:00:01.0: setting latency timer to 64
[    0.358879] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.358888] pci 0000:00:06.0: setting latency timer to 64
[    0.358901] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.358910] pci 0000:00:07.0: setting latency timer to 64
[    0.358919] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.358925] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.358931] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.358936] pci_bus 0000:00: resource 7 [mem 0xb8000000-0xffedffff]
[    0.358942] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.358947] pci_bus 0000:00: resource 9 [mem 0x000d4000-0x000d7fff]
[    0.358953] pci_bus 0000:00: resource 10 [mem 0x000d8000-0x000dbfff]
[    0.358958] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000dffff]
[    0.358964] pci_bus 0000:00: resource 12 [mem 0x000e0000-0x000e3fff]
[    0.358970] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.358975] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.358981] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.358987] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.358992] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.358998] pci_bus 0000:04: resource 2 [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.359096] NET: Registered protocol family 2
[    0.359266] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.359812] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.360767] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.361244] TCP: Hash tables configured (established 131072 bind 65536)
[    0.361249] TCP reno registered
[    0.361256] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.361274] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.361458] NET: Registered protocol family 1
[    0.361552] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.416066] pci 0000:00:03.0: PCI INT A disabled
[    0.416118] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.472061] pci 0000:00:03.1: PCI INT B disabled
[    0.472107] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.472139] pci 0000:00:03.3: PCI INT C disabled
[    0.472173] pci 0000:01:00.0: Boot video device
[    0.472180] PCI: CLS 16 bytes, default 64
[    0.472946] audit: initializing netlink socket (disabled)
[    0.472971] type=2000 audit(1349370922.468:1): initialized
[    0.521817] highmem bounce pool size: 64 pages
[    0.521830] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.526857] VFS: Disk quotas dquot_6.5.2
[    0.527003] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.528320] fuse init (API version 7.17)
[    0.528543] msgmni has been set to 1664
[    0.529261] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.529323] io scheduler noop registered
[    0.529328] io scheduler deadline registered
[    0.529344] io scheduler cfq registered (default)
[    0.529780] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.529840] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.530031] intel_idle: MWAIT substates: 0x22220
[    0.530036] intel_idle: does not run on family 6 model 15
[    0.530181] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.530297] ACPI: AC Adapter [ACAD] (off-line)
[    0.530458] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.530833] ACPI: Lid Switch [LID0]
[    0.530941] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.530951] ACPI: Power Button [PWRB]
[    0.531049] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.531057] ACPI: Power Button [PWRF]
[    0.531193] ACPI: Fan [FAN] (off)
[    0.548380] Monitor-Mwait will be used to enter C-1 state
[    0.548447] Monitor-Mwait will be used to enter C-2 state
[    0.556311] Monitor-Mwait will be used to enter C-3 state
[    0.556330] Marking TSC unstable due to TSC halts in idle
[    0.556354] ACPI: acpi_idle registered with cpuidle
[    0.562652] thermal LNXTHERM:00: registered as thermal_zone0
[    0.562659] ACPI: Thermal Zone [THRM] (53 C)
[    0.562718] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.562743] ACPI: Battery Slot [BAT1] (battery absent)
[    0.562838] ERST: Table is not found!
[    0.562842] GHES: HEST is not enabled!
[    0.563029] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.563606] ACPI: Battery Slot [BAT1] (battery absent)
[    0.563625] isapnp: Scanning for PnP cards...
[    0.826472] Freeing initrd memory: 13840k freed
[    0.918169] isapnp: No Plug & Play device found
[    0.964889] Linux agpgart interface v0.103
[    0.968582] brd: module loaded
[    0.970430] loop: module loaded
[    0.970863] pata_sis 0000:00:02.5: version 0.5.2
[    0.970894] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.971713] scsi0 : pata_sis
[    0.971898] scsi1 : pata_sis
[    0.972495] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    0.972501] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    0.972609] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.972684] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.973512] Fixed MDIO Bus: probed
[    0.973565] tun: Universal TUN/TAP device driver, 1.6
[    0.973571] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.973688] PPP generic driver version 2.4.2
[    0.973917] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.973952] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.973979] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.974076] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.974120] ehci_hcd 0000:00:03.3: cache line size of 16 is not supported
[    0.974153] ehci_hcd 0000:00:03.3: irq 22, io mem 0xd4106000
[    0.984029] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.984355] hub 1-0:1.0: USB hub found
[    0.984365] hub 1-0:1.0: 8 ports detected
[    0.984532] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.984561] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.984589] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.984684] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.984722] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd4104000
[    1.046255] hub 2-0:1.0: USB hub found
[    1.046266] hub 2-0:1.0: 4 ports detected
[    1.046401] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.046422] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.046530] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.046567] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4105000
[    1.102267] hub 3-0:1.0: USB hub found
[    1.102278] hub 3-0:1.0: 4 ports detected
[    1.102427] uhci_hcd: USB Universal Host Controller Interface driver
[    1.102558] usbcore: registered new interface driver libusual
[    1.102665] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.106579] i8042: Detected active multiplexing controller, rev 1.1
[    1.108058] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.108070] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.108146] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.108207] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.108274] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.108548] mousedev: PS/2 mouse device common for all mice
[    1.108943] rtc_cmos 00:02: RTC can wake from S4
[    1.109145] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.109176] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.109306] device-mapper: uevent: version 1.0.3
[    1.109472] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.109550] EISA: Probing bus 0 at eisa.0
[    1.109556] EISA: Cannot allocate resource for mainboard
[    1.109561] Cannot allocate resource for EISA slot 1
[    1.109565] Cannot allocate resource for EISA slot 2
[    1.109570] Cannot allocate resource for EISA slot 3
[    1.109574] Cannot allocate resource for EISA slot 4
[    1.109578] Cannot allocate resource for EISA slot 5
[    1.109582] Cannot allocate resource for EISA slot 6
[    1.109586] Cannot allocate resource for EISA slot 7
[    1.109590] Cannot allocate resource for EISA slot 8
[    1.109594] EISA: Detected 0 cards.
[    1.109614] cpufreq-nforce2: No nForce2 chipset.
[    1.109759] cpuidle: using governor ladder
[    1.109996] cpuidle: using governor menu
[    1.110001] EFI Variables Facility v0.08 2004-May-17
[    1.110625] TCP cubic registered
[    1.110912] NET: Registered protocol family 10
[    1.112311] NET: Registered protocol family 17
[    1.112322] Registering the dns_resolver key type
[    1.112373] Using IPI No-Shortcut mode
[    1.112650] PM: Hibernation image not present or could not be loaded.
[    1.112680] registered taskstats version 1
[    1.127607]   Magic number: 0:846:288
[    1.127674] tty tty21: hash matches
[    1.127760] rtc_cmos 00:02: setting system clock to 2012-10-04 17:15:23 UTC (1349370923)
[    1.128492] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128495] EDD information not available.
[    1.136312] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    1.144558] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.152285] ata1.00: configured for UDMA/33
[    1.154721] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    1.156952] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.156956] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.157128] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.157259] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.157363] ata2: port disabled--ignoring
[    1.157510] Freeing unused kernel memory: 740k freed
[    1.157938] Write protecting the kernel text: 5820k
[    1.157969] Write protecting the kernel read-only data: 2376k
[    1.157971] NX-protecting the kernel data: 4420k
[    1.180286] udevd[95]: starting version 175
[    1.266724] sata_sis 0000:00:05.0: version 1.0
[    1.266756] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.266764] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.267439] scsi2 : sata_sis
[    1.267718] scsi3 : sata_sis
[    1.268311] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
[    1.268315] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17
[    1.271481] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.271524] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.271539] sis190 0000:00:04.0: setting latency timer to 64
[    1.271561] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.352039] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.364025] sis190: 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1
[    1.432247] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.432251] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.448235] ata3.00: configured for UDMA/133
[    1.448429] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.448616] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.448656] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.448680] sd 2:0:0:0: [sda] Write Protect is off
[    1.448684] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.448712] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.483904]  sda: sda1 sda2 < sda5 >
[    1.484347] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.502699] usbcore: registered new interface driver uas
[    1.502968] Initializing USB Mass Storage driver...
[    1.503018] usbcore: registered new interface driver usb-storage
[    1.503020] USB Mass Storage support registered.
[    1.614781] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.618614] scsi4 : usb-storage 1-4:1.0
[    1.618740] usbcore: registered new interface driver ums-realtek
[    1.868053] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[    1.876029] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.908713] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8412000 (IRQ: 19), 00:1e:68:24:0c:41
[    1.908717] sis190 0000:00:04.0: eth0: GMII mode.
[    1.908726] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
[    2.053657] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.328039] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    2.628638] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.629457] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.631989] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   19.411871] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.451923] udevd[309]: starting version 175
[   19.488161] lp: driver loaded but no devices found
[   19.529271] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.530112] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   19.537453] Adding 3010556k swap on /dev/sda5.  Priority:-1 extents:1 across:3010556k 
[   19.576076] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   19.656287] type=1400 audit(1349363742.027:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[   19.657038] type=1400 audit(1349363742.027:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[   19.657347] type=1400 audit(1349363742.027:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[   19.740577] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.769357] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.784285] acpi device:0e: registered as cooling_device3
[   19.784455] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input4
[   19.786334] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.800572] Linux video capture interface: v2.00
[   19.801454] uvcvideo: Found UVC 1.00 device CNF7045 (04f2:b062)
[   19.806515] input: CNF7045 as /devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input5
[   19.806622] usbcore: registered new interface driver uvcvideo
[   19.806625] USB Video Class driver (1.1.1)
[   19.827097] cfg80211: Calling CRDA to update world regulatory domain
[   19.924936] snd_hda_intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.924987] snd_hda_intel 0000:00:0f.0: setting latency timer to 64
[   19.951806] input: MLK OM1007 Wireless Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input6
[   19.952209] generic-usb 0003:04FC:0538.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK OM1007 Wireless Mouse] on usb-0000:00:03.0-2/input0
[   19.952238] usbcore: registered new interface driver usbhid
[   19.952240] usbhid: USB HID core driver
[   19.960103] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input7
[   19.960243] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input8
[   20.054722] cfg80211: World regulatory domain updated:
[   20.054727] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.054731] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.054735] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.054738] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.054741] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.054744] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.269923] init: failsafe main process (724) killed by TERM signal
[   20.311845] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.311850] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311854] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.311857] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311860] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.311863] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311866] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.311869] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311872] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.311876] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311878] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.311882] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311885] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.311888] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311891] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.311894] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311897] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.311900] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311903] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.311906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311909] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.311913] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.311915] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.311919] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.311922] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.311925] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.311928] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.311931] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.315481] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.316584] ieee80211 phy0: hwaddr 00:17:c4:1c:54:1d, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   20.353320] rtl8187: Customer ID is 0x00
[   20.353572] Registered led device: rtl8187-phy0::radio
[   20.354059] Registered led device: rtl8187-phy0::tx
[   20.354093] Registered led device: rtl8187-phy0::rx
[   20.354808] rtl8187: wireless switch is on
[   20.355119] usbcore: registered new interface driver rtl8187
[   20.405787] ppdev: user-space parallel port driver
[   20.425979] Bluetooth: Core ver 2.16
[   20.426397] NET: Registered protocol family 31
[   20.426401] Bluetooth: HCI device and connection manager initialized
[   20.426405] Bluetooth: HCI socket layer initialized
[   20.426408] Bluetooth: L2CAP socket layer initialized
[   20.426424] Bluetooth: SCO socket layer initialized
[   20.448934] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.448938] Bluetooth: BNEP filters: protocol multicast
[   20.488041] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.488044] vesafb: scrolling: redraw
[   20.488048] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.490082] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 1216k, total 1216k
[   20.496216] fbcon: VESA VGA (fb0) is primary device
[   20.496330] Console: switching to colour frame buffer device 80x30
[   20.496349] fb0: VESA VGA frame buffer device
[   20.507778] type=1400 audit(1349363742.875:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=832 comm="apparmor_parser"
[   20.517905] type=1400 audit(1349363742.887:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=831 comm="apparmor_parser"
[   20.528628] type=1400 audit(1349363742.899:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=832 comm="apparmor_parser"
[   20.528937] type=1400 audit(1349363742.899:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=832 comm="apparmor_parser"
[   20.546861] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   20.552151] Bluetooth: RFCOMM TTY layer initialized
[   20.552159] Bluetooth: RFCOMM socket layer initialized
[   20.552162] Bluetooth: RFCOMM ver 1.11
[   20.566861] type=1400 audit(1349363742.935:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=846 comm="apparmor_parser"
[   20.588834] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.589995] type=1400 audit(1349363742.959:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=850 comm="apparmor_parser"
[   20.595369] type=1400 audit(1349363742.963:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=850 comm="apparmor_parser"
[   20.899343] init: kdm main process (906) killed by TERM signal
[   24.594552] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.594957] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.597947] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.600910] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.929261] wlan0: direct probe to 40:4a:03:fb:6d:6c (try 1/3)
[   29.933618] wlan0: direct probe responded
[   29.948048] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[   29.952450] wlan0: authenticated
[   29.952915] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[   29.964504] wlan0: RX AssocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[   29.964510] wlan0: associated
[   29.970074] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.972783] cfg80211: Calling CRDA for country: NL
[   29.982436] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.982444] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982447] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.982451] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982454] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.982457] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982460] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.982463] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982466] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.982470] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982473] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.982476] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982479] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.982482] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982485] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.982488] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982491] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.982495] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982497] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.982501] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982503] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.982507] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982509] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.982513] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982515] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.982519] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.982521] cfg80211: Disabling freq 2484 MHz
[   29.982525] cfg80211: Regulatory domain changed to country: NL
[   29.982528] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.982531] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.982534] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.982537] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.982540] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   32.852042] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[   34.648023] sis190 0000:00:04.0: eth0: auto-negotiating...
[   36.791591] init: plymouth-stop pre-start process (1426) terminated with status 1
[   40.368095] wlan0: no IPv6 routers present
[   52.772850] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   52.774454] sd 4:0:0:0: [sdb] Asking for cache data failed
[   52.774461] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   52.904067] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  104.472605] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  104.474097] sd 4:0:0:0: [sdb] Asking for cache data failed
[  104.474105] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  104.596081] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  156.184626] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.186119] sd 4:0:0:0: [sdb] Asking for cache data failed
[  156.186126] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  207.896648] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  207.898142] sd 4:0:0:0: [sdb] Asking for cache data failed
[  207.898150] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  220.756085] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  258.085174] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  258.086740] sd 4:0:0:0: [sdb] Asking for cache data failed
[  258.086753] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  258.292140] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  309.784625] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  309.786117] sd 4:0:0:0: [sdb] Asking for cache data failed
[  309.786124] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  309.948085] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  361.492789] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  361.494259] sd 4:0:0:0: [sdb] Asking for cache data failed
[  361.494268] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  413.208667] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  413.210160] sd 4:0:0:0: [sdb] Asking for cache data failed
[  413.210167] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  413.364087] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  464.920565] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  464.922056] sd 4:0:0:0: [sdb] Asking for cache data failed
[  464.922063] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  465.084088] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  516.632584] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  516.634079] sd 4:0:0:0: [sdb] Asking for cache data failed
[  516.634086] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  516.792070] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  568.344607] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  568.346099] sd 4:0:0:0: [sdb] Asking for cache data failed
[  568.346107] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  568.468072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  610.967800] mtrr: no MTRR for c0000000,8000000 found
[  620.056630] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  620.058121] sd 4:0:0:0: [sdb] Asking for cache data failed
[  620.058128] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  671.768653] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  671.770150] sd 4:0:0:0: [sdb] Asking for cache data failed
[  671.770157] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  691.093503] mtrr: no MTRR for c0000000,8000000 found
[  723.476522] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  723.477892] sd 4:0:0:0: [sdb] Asking for cache data failed
[  723.477896] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  726.100053] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  773.668636] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  773.670126] sd 4:0:0:0: [sdb] Asking for cache data failed
[  773.670133] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  773.796090] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  825.368652] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  825.370141] sd 4:0:0:0: [sdb] Asking for cache data failed
[  825.370148] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  877.080673] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  877.082163] sd 4:0:0:0: [sdb] Asking for cache data failed
[  877.082171] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  928.792696] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  928.794185] sd 4:0:0:0: [sdb] Asking for cache data failed
[  928.794192] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  928.940065] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  980.500584] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  980.502066] sd 4:0:0:0: [sdb] Asking for cache data failed
[  980.502070] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  980.676072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1032.216613] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1032.218129] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1032.218137] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1032.396090] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1083.928744] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1083.930273] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1083.930281] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1135.640576] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1135.642066] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1135.642073] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1135.792103] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1187.352630] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1187.354122] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1187.354130] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1202.596057] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[ 1202.696187] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1202.696199] cfg80211: Restoring regulatory settings
[ 1202.696218] cfg80211: Calling CRDA to update world regulatory domain
[ 1202.705325] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705334] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705340] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705346] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705352] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705358] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705363] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705369] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705374] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705386] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705392] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705397] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705403] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705408] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705422] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705427] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705433] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705439] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705445] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705450] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705457] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705462] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705468] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1202.705473] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705480] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1202.705485] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1202.705491] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1202.705498] cfg80211: World regulatory domain updated:
[ 1202.705502] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1202.705509] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705515] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1202.705521] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1202.705527] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1202.705532] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1205.061313] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[ 1205.063072] wlan0: authenticated
[ 1205.201314] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[ 1205.210944] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[ 1205.210953] wlan0: associated
[ 1205.217534] cfg80211: Calling CRDA for country: NL
[ 1205.228742] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228751] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228757] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228763] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228769] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228775] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228780] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228786] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228792] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228798] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228803] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228809] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228814] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228820] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228825] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228832] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228837] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228843] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228848] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228855] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228860] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228866] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228871] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228877] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228882] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1205.228889] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1205.228893] cfg80211: Disabling freq 2484 MHz
[ 1205.228900] cfg80211: Regulatory domain changed to country: NL
[ 1205.228904] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1205.228910] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1205.228915] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1205.228921] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1205.228927] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 1239.064562] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1239.066052] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1239.066059] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1239.224102] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1290.776617] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1290.778106] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1290.778113] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1342.488709] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1342.490179] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1342.490188] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1394.200601] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1394.202089] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1394.202097] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1394.328073] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1445.912780] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1445.914268] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1445.914275] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1446.084104] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1497.624835] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1497.626326] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1497.626333] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1497.764085] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1549.336764] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1549.338253] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1549.338261] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1549.460082] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1601.048568] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1601.050057] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1601.050064] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1601.240104] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1652.760626] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1652.762114] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1652.762121] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1652.888086] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1704.472859] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1704.474487] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1704.474497] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1756.184607] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1756.186110] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1756.186119] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1756.364104] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1807.896662] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1807.898151] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1807.898159] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1808.024070] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1859.608714] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1859.610206] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1859.610213] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1911.320646] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1911.322294] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1911.322301] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1924.180097] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 1961.508630] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1961.510266] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1961.510272] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1961.696082] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2013.208999] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2013.210691] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2013.210714] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2013.368086] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2064.920635] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2064.922126] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2064.922133] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2065.072090] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2116.632565] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2116.634055] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2116.634062] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2116.760102] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2168.344616] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2168.346110] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2168.346117] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2168.500071] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2207.524096] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[ 2207.636186] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2207.636196] cfg80211: Restoring regulatory settings
[ 2207.636204] cfg80211: Calling CRDA to update world regulatory domain
[ 2207.645432] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645441] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645446] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645453] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645458] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645465] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645470] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645476] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645481] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645488] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645493] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645499] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645504] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645510] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645515] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645522] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645527] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645533] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645538] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645545] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645550] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645556] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645561] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645568] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2207.645573] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645579] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2207.645585] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 2207.645591] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2207.645598] cfg80211: World regulatory domain updated:
[ 2207.645602] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2207.645608] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645614] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2207.645620] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2207.645625] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2207.645631] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2210.005330] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[ 2210.007080] wlan0: authenticated
[ 2210.141330] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[ 2210.151199] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[ 2210.151207] wlan0: associated
[ 2210.158365] cfg80211: Calling CRDA for country: NL
[ 2210.166753] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166763] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166768] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166775] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166780] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166786] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166791] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166798] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166803] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166809] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166814] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166820] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166826] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166832] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166837] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166843] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166848] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166855] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166860] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166866] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166871] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166878] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166883] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166889] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166894] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2210.166900] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2210.166905] cfg80211: Disabling freq 2484 MHz
[ 2210.166911] cfg80211: Regulatory domain changed to country: NL
[ 2210.166916] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2210.166922] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2210.166928] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2210.166933] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2210.166939] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 2220.056672] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2220.058163] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2220.058171] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2220.180074] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2271.768603] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2271.770093] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2271.770100] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2311.252060] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2321.956607] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2321.958098] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2321.958105] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2322.120085] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2373.656536] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2373.658028] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2373.658036] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2373.820070] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2425.368590] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2425.370082] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2425.370088] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2477.080645] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2477.082136] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2477.082144] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2477.232084] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2528.792574] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2528.794066] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2528.794072] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2528.956090] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2580.504628] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2580.506120] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2580.506127] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2580.696081] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2632.216934] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2632.218430] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2632.218436] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2632.360115] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2683.928613] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2683.930106] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2683.930113] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2684.104086] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2735.640687] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2735.642208] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2735.642214] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2735.768119] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2787.352598] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2787.354090] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2787.354097] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2839.064653] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2839.066144] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2839.066151] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2890.776582] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2890.778074] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2890.778081] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2890.900075] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 2942.488638] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2942.490129] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2942.490137] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2994.200565] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2994.202059] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2994.202066] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2994.324072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3045.912620] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3045.914112] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3045.914119] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3046.068078] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3097.624552] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3097.626043] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3097.626050] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3097.784139] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3149.336604] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3149.338097] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3149.338104] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3149.516081] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3201.048536] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3201.050026] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3201.050033] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3201.176059] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3252.760591] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3252.762081] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3252.762088] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3304.472646] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3304.474135] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3304.474142] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3304.640087] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3356.184574] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3356.186064] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3356.186071] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3356.312076] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3407.896627] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3407.898120] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3407.898128] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3459.608584] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3459.610050] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3459.610057] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3459.760079] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3511.320612] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3511.322106] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3511.322113] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3563.032667] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3563.034158] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3563.034165] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3563.180081] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3614.744596] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3614.746087] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3614.746094] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3614.884079] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3666.456649] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3666.458145] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3666.458152] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3666.608058] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3718.168579] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3718.170072] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3718.170079] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3718.328076] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3769.880637] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3769.882127] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3769.882134] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3781.540050] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[ 3781.625904] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3781.625916] cfg80211: Restoring regulatory settings
[ 3781.625924] cfg80211: Calling CRDA to update world regulatory domain
[ 3781.636794] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636803] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636809] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636815] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636820] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636827] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636832] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636838] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636843] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636849] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636854] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636861] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636866] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636872] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636877] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636884] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636889] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636895] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636900] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636907] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636912] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636918] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636924] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636930] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3781.636935] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636941] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3781.636947] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 3781.636953] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3781.636959] cfg80211: World regulatory domain updated:
[ 3781.636963] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3781.636970] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636976] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3781.636982] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3781.636988] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3781.636994] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3784.001326] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[ 3784.003079] wlan0: authenticated
[ 3784.137329] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[ 3784.148202] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[ 3784.148209] wlan0: associated
[ 3784.154329] cfg80211: Calling CRDA for country: NL
[ 3784.163639] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163648] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163654] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163660] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163665] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163672] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163677] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163683] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163688] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163695] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163700] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163706] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163711] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163717] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163722] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163729] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163734] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163740] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163745] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163751] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163756] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163763] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163768] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163774] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163779] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 3784.163786] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3784.163790] cfg80211: Disabling freq 2484 MHz
[ 3784.163797] cfg80211: Regulatory domain changed to country: NL
[ 3784.163801] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3784.163807] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3784.163812] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3784.163818] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3784.163823] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 3821.592690] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3821.594181] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3821.594189] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3854.932104] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 3871.780573] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3871.782075] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3871.782083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3923.480626] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3923.482117] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3923.482125] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3975.188533] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 3975.190024] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3975.190029] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4026.904609] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4026.906100] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4026.906107] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4078.616537] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4078.618029] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4078.618036] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4130.328595] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4130.330084] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4130.330091] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4182.040646] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4182.042139] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4182.042145] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4182.204075] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4233.752577] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4233.754069] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4233.754076] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4233.900083] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4285.464628] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4285.466119] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4285.466126] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4285.616072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4337.176560] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4337.178054] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4337.178061] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4337.304074] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4388.888616] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4388.890107] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4388.890114] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4389.044059] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4440.596521] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4440.598020] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4440.598024] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4492.312599] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4492.314092] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4492.314099] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4492.464080] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4544.020637] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4544.022130] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4544.022135] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4544.148085] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4595.736585] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4595.738076] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4595.738083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4647.448830] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4647.450293] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4647.450303] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4647.680149] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4699.160568] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4699.162060] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4699.162067] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4699.308083] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4750.872622] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4750.874114] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4750.874121] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4751.044087] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4802.588976] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4802.590661] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4802.590671] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4802.788094] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4845.604047] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[ 4845.700141] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4845.700152] cfg80211: Restoring regulatory settings
[ 4845.700172] cfg80211: Calling CRDA to update world regulatory domain
[ 4845.708863] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708872] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708878] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708885] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708890] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708897] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708902] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708957] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708963] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708969] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708974] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708981] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708986] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.708992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.708997] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709003] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.709008] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709015] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.709020] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709026] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.709031] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709037] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.709043] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709049] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4845.709054] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709060] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4845.709065] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 4845.709072] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4845.709079] cfg80211: World regulatory domain updated:
[ 4845.709083] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4845.709089] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.709095] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4845.709101] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4845.709107] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4845.709112] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4848.065262] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[ 4848.067497] wlan0: authenticated
[ 4848.205265] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[ 4848.214431] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[ 4848.214440] wlan0: associated
[ 4848.220722] cfg80211: Calling CRDA for country: NL
[ 4848.231421] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231431] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231436] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231443] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231448] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231454] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231459] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231466] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231471] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231477] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231482] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231488] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231493] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231499] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231504] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231511] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231516] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231522] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231528] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231534] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231539] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231545] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231550] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231556] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231561] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 4848.231567] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4848.231572] cfg80211: Disabling freq 2484 MHz
[ 4848.231578] cfg80211: Regulatory domain changed to country: NL
[ 4848.231582] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4848.231588] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4848.231595] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4848.231600] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4848.231606] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 4854.296604] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4854.298098] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4854.298106] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4854.472086] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4906.008673] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4906.010154] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4906.010161] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4906.136070] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 4957.720574] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 4957.722067] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 4957.722072] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5009.432769] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5009.434270] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5009.434278] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5009.572089] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5061.144579] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5061.146068] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5061.146075] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5061.320080] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5112.856630] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5112.858131] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5112.858138] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5113.036097] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5164.564543] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5164.566036] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5164.566040] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5164.728071] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5216.280614] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5216.282106] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5216.282114] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5247.572089] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5266.470372] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5266.471878] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5266.471886] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5266.656111] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5318.168671] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5318.170324] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5318.170332] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5369.880599] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5369.882253] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5369.882263] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5419.604397] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[ 5422.104550] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5422.106042] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5422.106049] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5473.817114] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5473.818884] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5473.818893] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5525.528534] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5525.530026] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5525.530033] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5577.240588] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5577.242080] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5577.242088] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5628.952642] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 5628.954136] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 5628.954144] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5629.084062] usb 1-4: reset high-speed USB device number 3 using ehci_hcd

```

thanks

---

### Post by NikTh on 2012-10-04
> **Noor1101 said:**
> Just to be sure, do you mean I should shut down my computer, turn it on, go to BIOS and search for "Restore Default" there? (And, again to be absolutely sure, by that I won't lose any data?)
(Sorry, I just want to be careful - don't really know what I'm doing half the time)

Yes , that I mean. I think is an F key , you should see it as option in BIOS config page.

Restore Defaults is a safe option , nothing to do with OS = data. It will restore the default (factory settings) in you BIOS , in case that some option is responsible for the battery's fault. 

Thanks

---

### Post by NikTh on 2012-10-04
Hi , 
I can see a LOT OF errors in dmesg related to a disk [sdb]

```
[   52.772850] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   52.774454] sd 4:0:0:0: [sdb] Asking for cache data failed 
```Can post the results of 

```
sudo fdisk -l 
sudo parted -l
```Thanks

---

### Post by Noor1101 on 2012-10-04
I went to BIOS and set default settings, but the problem persists.

I wonder what sdb could be, because I my HDD is not partitioned and there are no external discs connected. (Could it be my wireless-mouse-USB? The mouse works fine)

Here is the output:

```
noor@noor-EasyNote-MH35:~$ sudo fdisk -l 
[sudo] password for noor: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000021e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   482373631   241185792   83  Linux
/dev/sda2       482375678   488396799     3010561    5  Extended
/dev/sda5       482375680   488396799     3010560   82  Linux swap / Solaris

noor@noor-EasyNote-MH35:~$ sudo parted -l
Model: ATA ST9250827AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  247GB  247GB   primary   ext4
 2      247GB   250GB  3083MB  extended
 5      247GB   250GB  3083MB  logical   linux-swap(v1)


noor@noor-EasyNote-MH35:~$ 

```thanks

EDIT: sdb is NOT my USB-mouse. I unplugged it and made another dmesg.txt-file and the sdb-errors are still there

---

### Post by NikTh on 2012-10-04
> **Noor1101 said:**
> 
I wonder what sdb could be, because I my HDD is not partitioned and there are no external discs connected. (Could it be my wireless-mouse-USB? The mouse works fine)


EDIT: sdb is NOT my USB-mouse. I unplugged it and made another dmesg.txt-file and the sdb-errors are still there

I wonder the same thing . [sdb] usually refers to scsi device (HDD , or maybe usb stick , card reader  or any external device connected) . 

Maybe is this a bug ? 

Give the list of modules loaded please 
```
lsmod
```Thanks

---

### Post by Noor1101 on 2012-10-04
The only connected device is my wireless-mouse-USB: no SDcard in the slot, 2 free (unused) USB-slots, no cd-rom in its drive.

Here's the output you requested:

```
noor@noor-EasyNote-MH35:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rtl8187                56323  0 
mac80211              436455  1 rtl8187
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 rtl8187,mac80211
eeprom_93cx6           12653  1 rtl8187
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                86421  0 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
joydev                 17393  0 
video                  19068  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mac_hid                13077  0 
sis_agp                13165  1 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
uas                    17828  0 
sata_sis               12700  2 
sis190                 22575  0 
noor@noor-EasyNote-MH35:~$

```

thanks for your effort :)

---

### Post by NikTh on 2012-10-04
Hi , 

try this ```
echo 'blacklist ums_realtek' | sudo tee -a /etc/modprobe.d/blacklist.conf
``` 

Reboot your PC and check again dmesg for sdb errors. 

Also check again the battery with acpi 
```
acpi -V
``` 

If no battery present , then try this 

1) Close the Laptop (poweroff) 
2) Remove the battery 
3) Plug the Power cable 
4) Hold down the Power ON/OFF button for 10 secs. 
5) Close the Laptop (poweroff) 
6) Unplug the Power Cable 
7) Plug the battery and switch ON. 

See if battery measure works . Trust acpi , so ```
acpi -V
``` 

Another thought of mine , is to Test with a LiveCd/Usb , so we can excluded the Fault of Installed OS. 

Thanks

---

### Post by Noor1101 on 2012-10-04
Hi Nik,

the sdb-errors are still there after the suggested
```
echo 'blacklist ums_realtek' | sudo tee -a /etc/modprobe.d/blacklist.conf
```


I did what you said in your 7 steps but it hasn't changed anything:

```
noor@noor-EasyNote-MH35:~$ acpi -V
Adapter 0: off-line
Thermal 0: ok, 56.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 90.0 degrees C
Thermal 0: trip point 2 switches to mode active at temperature 60.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Fan 0 of 1
noor@noor-EasyNote-MH35:~$ 
```
How do I "test with LiveCd/Usb"? I have an Ubuntu12.04 installation USB ready, will have a look on it now.

---

### Post by Noor1101 on 2012-10-04
Do I have to boot from the USB to test my OS?

---

### Post by NikTh on 2012-10-04
> **Noor1101 said:**
> Hi Nik,

the sdb-errors are still there after the suggested

Is the module loaded ? check it with ```
lsmod | grep ums
``` 

Yes, boot from Usb and check if battery works there. We just want to exclude the possibility that the installed Kubuntu creates the problem. 

If the problem occurs at the live session too , then is not a fault of Installed OS (Kubuntu). 

But if the problem not exists in the live session and battery measures works there , then we must search on what happen in your installed OS. 

Thanks

---

### Post by Noor1101 on 2012-10-04
I booted the USB and there was no battery icon. In Terminal I wanted to check with ```
acpi -V
``` whether the battery was present, but I couldn't (easily): in order to install acpi I need to 'enable component "universe"'. I don't know what that is or how to do it, so I instead used the commands I used before (is that OK?). The battery was still not present:
```

:~$ cat /proc/acpi/battery/BAT1/state
present:                 no
:~$ cat /proc/acpi/battery/BAT1/info
present:                 no
:~$ ls /proc/acpi/battery/
BAT1

```
Any other ideas?

(By the way, you wrote "Kubuntu" in your post - is that a typo, or do I have Kubuntu without knowing it?)

---

### Post by Noor1101 on 2012-10-04
Ooh! Something changed. Spontaneously.
Now, the icon is a battery WITH a plug next to it (and still the red cross in front). It now reads 
Battery: Not present
AC Adapter: Plugged in

So I tried this again: 

```
noor@noor-EasyNote-MH35:~$ acpi -V
Adapter 0: on-line
Thermal 0: ok, 54.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 90.0 degrees C
Thermal 0: trip point 2 switches to mode active at temperature 60.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Fan 0 of 1
noor@noor-EasyNote-MH35:~$ 
```

Adapter has changed from off-line to online.

Nice. But still, where's the battery!?

---

### Post by Noor1101 on 2012-10-04
I might have found out what's wrong - although it does **not** explain why the message said "AC Adapter: Not Plugged in"

I just logged in to my account after rebooting, and got a message on my desktop
> **Power Management System**
Your battery capacity is 48%. This means your battery is broken and needs a replacement. Please contact your hardware vendor for more details.The battery icon looks normal now, and when clicked it says 
Battery: 98% (Charging)
AC Adapter: Plugged in

So.. should I get a new battery? It's 4,5 years old, so maybe about time?

Could it just be that the battery being old/broken is messing things up?


EDIT: and could the mysterious sdb-error messages have anything to do with the battery being broken?

---

### Post by NikTh on 2012-10-04
> **Noor1101 said:**
> 
I just logged in to my account after rebooting, and got a message on my desktop
The battery icon looks normal now, and when clicked it says 
Battery: 98% (Charging)
AC Adapter: Plugged in

So.. should I get a new battery? It's 4,5 years old, so maybe about time?

Could it just be that the battery being old/broken is messing things up? 

Maybe battery is broken , maybe not. Give it a try for a couple of days and you will see.
4-5 years old it is old yes  , but as I said , give it try , maybe more of couple of days. 

Also it could be the adapter you know ? But nothing of that are for sure. YOU only can see whats going on , with tests. A week maybe. 


> **Noor1101 said:**
> EDIT: and could the mysterious sdb-error messages have anything to do with the battery being broken?

I don't think so. This message was a bug (but I cannot find it now) with the module I told you (ums_realtek) and the card reader . This module is driver for card reader . Card readers usually recognized as scsi devices , so a name like [sdb] would be appropriate.
I told you to blacklist the module for preventing it to load at startup and check the dmesg. You said dmesg writes the same about [sdb] and I told you to check if this module is loaded. 
```
lsmod | grep ums
```If module is loaded then the blacklist method didn't work. We can try other methods. 

Thanks

---

### Post by Noor1101 on 2012-10-05
When I turned on my notebook this morning and logged in, _according to the system_ the battery wasn't there again, but the AC Adapter was plugged in. I logged out and in again (because that changed things yesterday) and I got the message my battery was broken again, and the battery is detected and its icon back in system tray.

I'll leave the battery as it is for a while because since I found out how expensive those batteries are, I realise I can't afford one now.


The ums_realtek Blacklist method didn't work, I think (I tried last night and just now again):

```
noor@noor-EasyNote-MH35:~$ lsmod | grep ums
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
noor@noor-EasyNote-MH35:~$ echo 'blacklist ums_realtek' | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for noor: 
blacklist ums_realtek
noor@noor-EasyNote-MH35:~$ lsmod | grep ums
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
noor@noor-EasyNote-MH35:~$ dmesg >> dmesg.txt
```the dmseg.txt file:

```
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7da0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7da0000 - 00000000b7da1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7da1000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: PACKARD BELL BV EasyNote MH35/PE1, BIOS PE14A04  02/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f86c0] f86c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000f8690 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT b7d97999 00094 (v01 PacBel PBNB000B 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b7d9fcc4 000F4 (v03 SiS    671MX    06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT b7d9b9c6 0428A (v01 PTLTD       671 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS b7da0fc0 00040
[    0.000000] ACPI: SLIC b7d9fdb8 00176 (v00 PacBel PBNB000B 06040000      00000000)
[    0.000000] ACPI: APIC b7d9ff2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG b7d9ff8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET b7d9ffc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SSDT b7d992d1 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d9922b 000A6 (v01  PmRef  Cpu7Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99185 000A6 (v01  PmRef  Cpu6Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d990df 000A6 (v01  PmRef  Cpu5Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99039 000A6 (v01  PmRef  Cpu4Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98f93 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98eed 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98e47 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d97a2d 0141A (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4de8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4100 pages used for memmap
[    0.000000]   HighMem zone: 520590 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=9b3867fe-5b6d-419c-98c6-e571f5a57d0a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d90)
[    0.000000] Memory: 2951184k/3012160k available (5818k kernel code, 60516k reserved, 2846k data, 740k init, 2098760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1831.834 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3663.66 BogoMIPS (lpj=7327336)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004059] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004100] Yama: becoming mindful.
[    0.004220] Mount-cache hash table entries: 512
[    0.004508] Initializing cgroup subsys cpuacct
[    0.004521] Initializing cgroup subsys memory
[    0.004538] Initializing cgroup subsys devices
[    0.004543] Initializing cgroup subsys freezer
[    0.004547] Initializing cgroup subsys blkio
[    0.004562] Initializing cgroup subsys perf_event
[    0.004618] CPU: Physical Processor ID: 0
[    0.004622] CPU: Processor Core ID: 0
[    0.004628] mce: CPU supports 6 MCE banks
[    0.004645] CPU0: Thermal monitoring enabled (TM2)
[    0.004652] using mwait in idle threads.
[    0.011073] ACPI: Core revision 20110623
[    0.024051] ftrace: allocating 26555 entries in 52 pages
[    0.028096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028434] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069772] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.072003] PEBS disabled due to CPU errata.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f74cc000 soft=f74ce000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.160059] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160131] Brought up 2 CPUs
[    0.160137] Total of 2 processors activated (7327.46 BogoMIPS).
[    0.162831] devtmpfs: initialized
[    0.162831] EVM: security.selinux
[    0.162831] EVM: security.SMACK64
[    0.162831] EVM: security.capability
[    0.162831] PM: Registering ACPI NVS region at b7da0000 (4096 bytes)
[    0.165923] print_constraints: dummy: 
[    0.165969] RTC time: 21:02:32, date: 10/04/12
[    0.166055] NET: Registered protocol family 16
[    0.166206] Trying to unpack rootfs image as initramfs...
[    0.166347] EISA bus registered
[    0.166380] ACPI: bus type pci registered
[    0.166529] PCI: MMCONFIG for domain 0000 [bus 00-02] at [mem 0xe0000000-0xe02fffff] (base 0xe0000000)
[    0.166536] PCI: MMCONFIG at [mem 0xe0000000-0xe02fffff] reserved in E820
[    0.166540] PCI: Using MMCONFIG for extended config space
[    0.166544] PCI: Using configuration type 1 for base access
[    0.180149] bio: create slab <bio-0> at 0
[    0.180342] ACPI: Added _OSI(Module Device)
[    0.180348] ACPI: Added _OSI(Processor Device)
[    0.180353] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180358] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182460] ACPI: EC: Look up EC in DSDT
[    0.189432] ACPI: SSDT b7d99deb 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.189987] ACPI: Dynamic OEM Table Load:
[    0.189995] ACPI: SSDT   (null) 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.192052] ACPI: SSDT b7d99530 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.192683] ACPI: Dynamic OEM Table Load:
[    0.192691] ACPI: SSDT   (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.236980] ACPI: SSDT b7d9a00a 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.237553] ACPI: Dynamic OEM Table Load:
[    0.237561] ACPI: SSDT   (null) 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.238093] ACPI: SSDT b7d99a48 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.238619] ACPI: Dynamic OEM Table Load:
[    0.238626] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.268561] ACPI: Interpreter enabled
[    0.268592] ACPI: (supports S0 S1 S3 S4 S5)
[    0.268639] ACPI: Using IOAPIC for interrupt routing
[    0.272778] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.275960] ACPI: Power Resource [QFAN] (off)
[    0.276403] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.276685] ACPI: No dock devices found.
[    0.276691] HEST: Table not found.
[    0.276704] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277472] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.278881] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.278888] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.278894] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.278900] pci_root PNP0A03:00: host bridge window [mem 0xb8000000-0xffedffff]
[    0.278906] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.278913] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.278919] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.278925] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.278930] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.278967] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.278989] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.279094] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.279162] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.279303] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.279333] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.279350] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.279367] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.279384] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.279401] pci 0000:00:02.5: reg 20: [io  0x1080-0x108f]
[    0.279472] pci 0000:00:02.5: PME# supported from D3cold
[    0.279481] pci 0000:00:02.5: PME# disabled
[    0.279508] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.279531] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.279632] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.279655] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.279763] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.279790] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.279905] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.279913] pci 0000:00:03.3: PME# disabled
[    0.279948] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.279976] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.279993] pci 0000:00:04.0: reg 14: [io  0x1000-0x107f]
[    0.280112] pci 0000:00:04.0: supports D1 D2
[    0.280117] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280126] pci 0000:00:04.0: PME# disabled
[    0.280154] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.280181] pci 0000:00:05.0: reg 10: [io  0x10c8-0x10cf]
[    0.280198] pci 0000:00:05.0: reg 14: [io  0x10bc-0x10bf]
[    0.280215] pci 0000:00:05.0: reg 18: [io  0x10c0-0x10c7]
[    0.280231] pci 0000:00:05.0: reg 1c: [io  0x10b8-0x10bb]
[    0.280248] pci 0000:00:05.0: reg 20: [io  0x10a0-0x10af]
[    0.280317] pci 0000:00:05.0: PME# supported from D3cold
[    0.280325] pci 0000:00:05.0: PME# disabled
[    0.280362] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.280497] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.280505] pci 0000:00:06.0: PME# disabled
[    0.280553] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.280687] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.280695] pci 0000:00:07.0: PME# disabled
[    0.280751] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.280781] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.280899] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.280907] pci 0000:00:0f.0: PME# disabled
[    0.280987] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.281016] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.281032] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.281047] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.281133] pci 0000:01:00.0: supports D1 D2
[    0.281196] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.281205] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.281214] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.281222] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.281307] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.281319] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.281328] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.281420] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.281465] pci_bus 0000:00: on NUMA node 0
[    0.281472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.282019]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.282027]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.282031] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.291764] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.291878] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.291986] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[    0.292104] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 9 10 11)
[    0.292243] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.292350] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.292456] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.292562] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.292880] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.292887] vgaarb: loaded
[    0.292891] vgaarb: bridge control possible 0000:01:00.0
[    0.293174] i2c-core: driver [aat2870] using legacy suspend method
[    0.293179] i2c-core: driver [aat2870] using legacy resume method
[    0.293365] SCSI subsystem initialized
[    0.293495] libata version 3.00 loaded.
[    0.293602] usbcore: registered new interface driver usbfs
[    0.293630] usbcore: registered new interface driver hub
[    0.293696] usbcore: registered new device driver usb
[    0.293908] PCI: Using ACPI for IRQ routing
[    0.293967] PCI: pci_cache_line_size set to 64 bytes
[    0.294079] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.294085] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.294329] NetLabel: Initializing
[    0.294333] NetLabel:  domain hash size = 128
[    0.294337] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.294361] NetLabel:  unlabeled traffic allowed by default
[    0.294473] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.294481] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.294493] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.300101] Switching to clocksource hpet
[    0.320291] AppArmor: AppArmor Filesystem Enabled
[    0.320360] pnp: PnP ACPI init
[    0.320403] ACPI: bus type pnp registered
[    0.321220] pnp 00:00: [bus 00-ff]
[    0.321227] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.321233] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.321239] pnp 00:00: [io  0x0d00-0xffff window]
[    0.321245] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.321251] pnp 00:00: [mem 0xb8000000-0xffedffff window]
[    0.321257] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.321262] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.321268] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.321273] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.321278] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.321284] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.321289] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.321294] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.321300] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.321305] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.321310] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.321315] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.321444] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.321799] pnp 00:01: [io  0x0000-0x000f]
[    0.321804] pnp 00:01: [io  0x0081-0x008f]
[    0.321809] pnp 00:01: [io  0x00c0-0x00df]
[    0.321814] pnp 00:01: [io  0x0480-0x048f]
[    0.321820] pnp 00:01: [dma 4]
[    0.321912] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.321974] pnp 00:02: [io  0x0070-0x0071]
[    0.322065] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.322086] pnp 00:03: [io  0x0061]
[    0.322171] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.322264] pnp 00:04: [io  0x8000-0x80be]
[    0.322269] pnp 00:04: [io  0x8100-0x812f]
[    0.322274] pnp 00:04: [io  0x0080]
[    0.322279] pnp 00:04: [io  0x04d0-0x04d1]
[    0.322284] pnp 00:04: [io  0xfe00]
[    0.322288] pnp 00:04: [io  0x002e]
[    0.322292] pnp 00:04: [io  0x002f]
[    0.322297] pnp 00:04: [io  0x0092]
[    0.322301] pnp 00:04: [io  0x0072-0x0073]
[    0.322306] pnp 00:04: [io  0x0078-0x0079]
[    0.322310] pnp 00:04: [io  0x0290-0x0297]
[    0.322316] pnp 00:04: [mem 0xe0000000-0xefffffff]
[    0.322321] pnp 00:04: [mem 0xfec00000-0xfeefffff]
[    0.322325] pnp 00:04: [mem 0xffb80000-0xffbfffff]
[    0.322330] pnp 00:04: [mem 0xffc00000-0xffc00fff]
[    0.322335] pnp 00:04: [mem 0xffe00000-0xffe00fff]
[    0.322340] pnp 00:04: [mem 0xffe80000-0xffefffff]
[    0.322496] system 00:04: [io  0x8000-0x80be] has been reserved
[    0.322503] system 00:04: [io  0x8100-0x812f] has been reserved
[    0.322510] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.322522] system 00:04: [io  0xfe00] has been reserved
[    0.322528] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.322537] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.322544] system 00:04: [mem 0xfec00000-0xfeefffff] could not be reserved
[    0.322550] system 00:04: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.322557] system 00:04: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.322564] system 00:04: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.322570] system 00:04: [mem 0xffe80000-0xffefffff] could not be reserved
[    0.322579] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322628] pnp 00:05: [io  0x00f0-0x00ff]
[    0.322661] pnp 00:05: [irq 13]
[    0.322750] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322773] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    0.322778] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    0.322783] pnp 00:06: [mem 0xffc00000-0xffc00fff]
[    0.322788] pnp 00:06: [mem 0xffe00000-0xffe00fff]
[    0.322875] pnp 00:06: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.323026] pnp 00:07: [irq 0 disabled]
[    0.323038] pnp 00:07: [irq 8]
[    0.323049] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.323149] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.323174] pnp 00:08: [io  0x0060]
[    0.323178] pnp 00:08: [io  0x0064]
[    0.323188] pnp 00:08: [irq 1]
[    0.323279] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323306] pnp 00:09: [irq 12]
[    0.323402] pnp 00:09: Plug and Play ACPI device, IDs SYN101f PNP0f13 (active)
[    0.323728] pnp: PnP ACPI: found 10 devices
[    0.323732] ACPI: ACPI bus type pnp unregistered
[    0.323742] PnPBIOS: Disabled by ACPI PNP
[    0.362665] PCI: max bus depth: 1 pci_try_num: 2
[    0.362732] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362740] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362747] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.362758] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.362766] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.362779] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.362785] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.362796] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.362805] pci 0000:00:06.0:   bridge window [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362817] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.362853] pci 0000:00:01.0: setting latency timer to 64
[    0.362892] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362901] pci 0000:00:06.0: setting latency timer to 64
[    0.362913] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362922] pci 0000:00:07.0: setting latency timer to 64
[    0.362931] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.362937] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.362943] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.362948] pci_bus 0000:00: resource 7 [mem 0xb8000000-0xffedffff]
[    0.362954] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.362959] pci_bus 0000:00: resource 9 [mem 0x000d4000-0x000d7fff]
[    0.362965] pci_bus 0000:00: resource 10 [mem 0x000d8000-0x000dbfff]
[    0.362970] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000dffff]
[    0.362976] pci_bus 0000:00: resource 12 [mem 0x000e0000-0x000e3fff]
[    0.362982] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.362987] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.362993] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.362999] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.363004] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.363010] pci_bus 0000:04: resource 2 [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.363109] NET: Registered protocol family 2
[    0.363279] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.363817] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.364778] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.365245] TCP: Hash tables configured (established 131072 bind 65536)
[    0.365250] TCP reno registered
[    0.365257] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.365275] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.365458] NET: Registered protocol family 1
[    0.365553] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.420063] pci 0000:00:03.0: PCI INT A disabled
[    0.420114] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.476062] pci 0000:00:03.1: PCI INT B disabled
[    0.476108] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.476139] pci 0000:00:03.3: PCI INT C disabled
[    0.476173] pci 0000:01:00.0: Boot video device
[    0.476180] PCI: CLS 16 bytes, default 64
[    0.476941] audit: initializing netlink socket (disabled)
[    0.476965] type=2000 audit(1349384551.472:1): initialized
[    0.525812] highmem bounce pool size: 64 pages
[    0.525824] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.530845] VFS: Disk quotas dquot_6.5.2
[    0.530990] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.532307] fuse init (API version 7.17)
[    0.532529] msgmni has been set to 1664
[    0.533245] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.533303] io scheduler noop registered
[    0.533307] io scheduler deadline registered
[    0.533323] io scheduler cfq registered (default)
[    0.533769] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533829] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.534022] intel_idle: MWAIT substates: 0x22220
[    0.534027] intel_idle: does not run on family 6 model 15
[    0.534172] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.534288] ACPI: AC Adapter [ACAD] (off-line)
[    0.534449] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.534826] ACPI: Lid Switch [LID0]
[    0.534934] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.534943] ACPI: Power Button [PWRB]
[    0.535043] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.535050] ACPI: Power Button [PWRF]
[    0.535187] ACPI: Fan [FAN] (off)
[    0.552413] Monitor-Mwait will be used to enter C-1 state
[    0.552473] Monitor-Mwait will be used to enter C-2 state
[    0.560341] Monitor-Mwait will be used to enter C-3 state
[    0.560360] Marking TSC unstable due to TSC halts in idle
[    0.560385] ACPI: acpi_idle registered with cpuidle
[    0.567031] thermal LNXTHERM:00: registered as thermal_zone0
[    0.567037] ACPI: Thermal Zone [THRM] (52 C)
[    0.567098] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.567123] ACPI: Battery Slot [BAT1] (battery absent)
[    0.567183] ERST: Table is not found!
[    0.567188] GHES: HEST is not enabled!
[    0.567376] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.567682] ACPI: Battery Slot [BAT1] (battery absent)
[    0.567698] isapnp: Scanning for PnP cards...
[    0.830506] Freeing initrd memory: 13840k freed
[    0.922210] isapnp: No Plug & Play device found
[    0.965034] Linux agpgart interface v0.103
[    0.968723] brd: module loaded
[    0.970569] loop: module loaded
[    0.971001] pata_sis 0000:00:02.5: version 0.5.2
[    0.971030] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.971848] scsi0 : pata_sis
[    0.972049] scsi1 : pata_sis
[    0.972628] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    0.972634] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    0.972743] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.972815] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.973643] Fixed MDIO Bus: probed
[    0.973696] tun: Universal TUN/TAP device driver, 1.6
[    0.973702] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.973819] PPP generic driver version 2.4.2
[    0.974049] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.974085] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.974112] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.974209] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.974255] ehci_hcd 0000:00:03.3: cache line size of 16 is not supported
[    0.974288] ehci_hcd 0000:00:03.3: irq 22, io mem 0xd4106000
[    0.984029] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.984356] hub 1-0:1.0: USB hub found
[    0.984366] hub 1-0:1.0: 8 ports detected
[    0.984533] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.984561] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.984590] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.984685] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.984724] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd4104000
[    1.046255] hub 2-0:1.0: USB hub found
[    1.046266] hub 2-0:1.0: 4 ports detected
[    1.046402] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.046424] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.046531] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.046568] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4105000
[    1.102269] hub 3-0:1.0: USB hub found
[    1.102279] hub 3-0:1.0: 4 ports detected
[    1.102427] uhci_hcd: USB Universal Host Controller Interface driver
[    1.102558] usbcore: registered new interface driver libusual
[    1.102666] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.106549] i8042: Detected active multiplexing controller, rev 1.1
[    1.108028] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.108041] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.108116] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.108177] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.108244] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.108519] mousedev: PS/2 mouse device common for all mice
[    1.108913] rtc_cmos 00:02: RTC can wake from S4
[    1.109113] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.109145] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.109276] device-mapper: uevent: version 1.0.3
[    1.109442] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.109520] EISA: Probing bus 0 at eisa.0
[    1.109525] EISA: Cannot allocate resource for mainboard
[    1.109530] Cannot allocate resource for EISA slot 1
[    1.109535] Cannot allocate resource for EISA slot 2
[    1.109539] Cannot allocate resource for EISA slot 3
[    1.109544] Cannot allocate resource for EISA slot 4
[    1.109548] Cannot allocate resource for EISA slot 5
[    1.109552] Cannot allocate resource for EISA slot 6
[    1.109556] Cannot allocate resource for EISA slot 7
[    1.109560] Cannot allocate resource for EISA slot 8
[    1.109564] EISA: Detected 0 cards.
[    1.109583] cpufreq-nforce2: No nForce2 chipset.
[    1.109728] cpuidle: using governor ladder
[    1.109965] cpuidle: using governor menu
[    1.109971] EFI Variables Facility v0.08 2004-May-17
[    1.110596] TCP cubic registered
[    1.110881] NET: Registered protocol family 10
[    1.112280] NET: Registered protocol family 17
[    1.112290] Registering the dns_resolver key type
[    1.112330] Using IPI No-Shortcut mode
[    1.112609] PM: Hibernation image not present or could not be loaded.
[    1.112640] registered taskstats version 1
[    1.127525]   Magic number: 0:514:44
[    1.127672] rtc_cmos 00:02: setting system clock to 2012-10-04 21:02:33 UTC (1349384553)
[    1.128443] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128446] EDD information not available.
[    1.136312] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    1.144429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.152286] ata1.00: configured for UDMA/33
[    1.154721] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    1.157033] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.157037] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.157202] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.157334] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.157453] ata2: port disabled--ignoring
[    1.157592] Freeing unused kernel memory: 740k freed
[    1.158017] Write protecting the kernel text: 5820k
[    1.158047] Write protecting the kernel read-only data: 2376k
[    1.158049] NX-protecting the kernel data: 4420k
[    1.179936] udevd[96]: starting version 175
[    1.269990] sata_sis 0000:00:05.0: version 1.0
[    1.270015] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.270022] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.271574] scsi2 : sata_sis
[    1.272176] scsi3 : sata_sis
[    1.272752] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
[    1.272757] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17
[    1.272904] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.272947] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.272961] sis190 0000:00:04.0: setting latency timer to 64
[    1.272985] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.352043] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.360020] sis190: 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1
[    1.436255] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.436259] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.452245] ata3.00: configured for UDMA/133
[    1.452446] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.452678] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.452687] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.452762] sd 2:0:0:0: [sda] Write Protect is off
[    1.452766] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.452795] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.502881] Initializing USB Mass Storage driver...
[    1.502948] usbcore: registered new interface driver usb-storage
[    1.502950] USB Mass Storage support registered.
[    1.503175] usbcore: registered new interface driver uas
[    1.519544]  sda: sda1 sda2 < sda5 >
[    1.520106] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.620260] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.624375] scsi4 : usb-storage 1-4:1.0
[    1.624485] usbcore: registered new interface driver ums-realtek
[    1.872041] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[    1.880018] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.920711] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8412000 (IRQ: 19), 00:1e:68:24:0c:41
[    1.920716] sis190 0000:00:04.0: eth0: GMII mode.
[    1.920723] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
[    2.133165] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.320032] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    2.636651] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.637495] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.640000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   19.501226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.529827] udevd[312]: starting version 175
[   19.616508] Adding 3010556k swap on /dev/sda5.  Priority:-1 extents:1 across:3010556k 
[   19.654825] lp: driver loaded but no devices found
[   19.657957] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.658170] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   19.664979] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   19.727946] type=1400 audit(1349377372.093:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
[   19.728543] type=1400 audit(1349377372.097:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=415 comm="apparmor_parser"
[   19.728848] type=1400 audit(1349377372.097:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=415 comm="apparmor_parser"
[   19.821793] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.853365] cfg80211: Calling CRDA to update world regulatory domain
[   19.962570] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.965029] Linux video capture interface: v2.00
[   19.967496] acpi device:0e: registered as cooling_device3
[   19.967641] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input4
[   19.967755] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.968731] uvcvideo: Found UVC 1.00 device CNF7045 (04f2:b062)
[   19.972864] input: CNF7045 as /devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input5
[   19.973049] usbcore: registered new interface driver uvcvideo
[   19.973053] USB Video Class driver (1.1.1)
[   20.082296] snd_hda_intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.082381] snd_hda_intel 0000:00:0f.0: setting latency timer to 64
[   20.133887] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input6
[   20.134129] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input7
[   20.187619] input: MLK OM1007 Wireless Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input8
[   20.187884] generic-usb 0003:04FC:0538.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK OM1007 Wireless Mouse] on usb-0000:00:03.0-2/input0
[   20.187911] usbcore: registered new interface driver usbhid
[   20.187914] usbhid: USB HID core driver
[   20.203258] cfg80211: World regulatory domain updated:
[   20.203263] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.203267] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.203271] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.203274] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.203277] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.203280] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328783] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.328788] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328791] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.328795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328797] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.328801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328804] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.328807] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328810] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.328813] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328816] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.328819] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328822] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.328825] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328828] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.328849] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328852] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.328856] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328858] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.328862] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328864] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.328868] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328870] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.328874] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.328877] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.328880] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.328883] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.328886] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.333378] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.334472] ieee80211 phy0: hwaddr 00:17:c4:1c:54:1d, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   20.355949] rtl8187: Customer ID is 0x00
[   20.356044] Registered led device: rtl8187-phy0::radio
[   20.356074] Registered led device: rtl8187-phy0::tx
[   20.356101] Registered led device: rtl8187-phy0::rx
[   20.357939] rtl8187: wireless switch is on
[   20.357996] usbcore: registered new interface driver rtl8187
[   20.416550] init: failsafe main process (765) killed by TERM signal
[   20.516348] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   20.543314] type=1400 audit(1349377372.909:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=849 comm="apparmor_parser"
[   20.558912] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.569678] type=1400 audit(1349377372.937:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=850 comm="apparmor_parser"
[   20.572326] type=1400 audit(1349377372.941:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=850 comm="apparmor_parser"
[   20.572635] type=1400 audit(1349377372.941:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=850 comm="apparmor_parser"
[   20.595206] Bluetooth: Core ver 2.16
[   20.595434] NET: Registered protocol family 31
[   20.595438] Bluetooth: HCI device and connection manager initialized
[   20.595442] Bluetooth: HCI socket layer initialized
[   20.595444] Bluetooth: L2CAP socket layer initialized
[   20.595452] Bluetooth: SCO socket layer initialized
[   20.599366] ppdev: user-space parallel port driver
[   20.610062] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.610067] Bluetooth: BNEP filters: protocol multicast
[   20.627118] type=1400 audit(1349377372.993:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=882 comm="apparmor_parser"
[   20.628906] type=1400 audit(1349377372.997:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=882 comm="apparmor_parser"
[   20.635282] type=1400 audit(1349377373.001:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=883 comm="apparmor_parser"
[   20.717896] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.717899] vesafb: scrolling: redraw
[   20.717903] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.721425] vesafb: framebuffer at 0xc0000000, mapped to 0xf8980000, using 1216k, total 1216k
[   20.721893] fbcon: VESA VGA (fb0) is primary device
[   20.721983] Console: switching to colour frame buffer device 80x30
[   20.722001] fb0: VESA VGA frame buffer device
[   20.725101] Bluetooth: RFCOMM TTY layer initialized
[   20.725110] Bluetooth: RFCOMM socket layer initialized
[   20.725113] Bluetooth: RFCOMM ver 1.11
[   21.130402] init: kdm main process (969) killed by TERM signal
[   24.662577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.662978] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.666817] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.667345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.708104] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[   29.966922] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[   29.971514] wlan0: authenticated
[   29.972756] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[   29.981684] wlan0: RX AssocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[   29.981691] wlan0: associated
[   29.987511] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.989384] cfg80211: Calling CRDA for country: NL
[   29.996650] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.996656] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996659] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.996663] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996666] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.996669] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996672] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.996675] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996678] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.996682] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996685] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.996688] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996691] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.996694] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996697] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.996700] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996703] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.996706] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996709] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.996713] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996715] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.996719] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996721] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.996725] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996728] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.996731] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996734] cfg80211: Disabling freq 2484 MHz
[   29.996737] cfg80211: Regulatory domain changed to country: NL
[   29.996739] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.996743] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.996746] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.996749] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.996751] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   34.712021] sis190 0000:00:04.0: eth0: auto-negotiating...
[   37.176841] init: plymouth-stop pre-start process (1475) terminated with status 1
[   41.104039] wlan0: no IPv6 routers present
[   52.772567] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   52.774057] sd 4:0:0:0: [sdb] Asking for cache data failed
[   52.774062] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   52.908053] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  104.472647] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  104.474138] sd 4:0:0:0: [sdb] Asking for cache data failed
[  104.474145] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  127.396044] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[  127.496187] cfg80211: All devices are disconnected, going to restore regulatory settings
[  127.496198] cfg80211: Restoring regulatory settings
[  127.496217] cfg80211: Calling CRDA to update world regulatory domain
[  127.505359] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  127.505368] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505374] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  127.505381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505386] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  127.505393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505398] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  127.505405] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505410] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  127.505416] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505421] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  127.505427] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505432] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  127.505438] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505443] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  127.505449] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505454] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  127.505461] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505466] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  127.505472] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505477] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  127.505483] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505488] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  127.505494] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505499] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  127.505506] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505511] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  127.505517] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505523] cfg80211: World regulatory domain updated:
[  127.505527] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  127.505533] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505539] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505545] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505551] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505556] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  129.861250] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[  129.865492] wlan0: authenticated
[  130.001307] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[  130.010825] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[  130.010832] wlan0: associated
[  130.016941] cfg80211: Calling CRDA for country: NL
[  130.025642] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  130.025652] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025657] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  130.025664] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025669] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  130.025676] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025681] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  130.025687] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025692] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  130.025699] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025704] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  130.025710] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025715] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  130.025721] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025726] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  130.025732] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025737] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  130.025743] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025748] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  130.025754] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025759] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  130.025765] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025770] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  130.025776] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025781] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  130.025787] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025791] cfg80211: Disabling freq 2484 MHz
[  130.025797] cfg80211: Regulatory domain changed to country: NL
[  130.025801] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  130.025807] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  130.025812] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  130.025818] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  130.025823] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  156.184583] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.186075] sd 4:0:0:0: [sdb] Asking for cache data failed
[  156.186081] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  169.044082] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7da0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7da0000 - 00000000b7da1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7da1000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: PACKARD BELL BV EasyNote MH35/PE1, BIOS PE14A04  02/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f86c0] f86c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000f8690 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT b7d97999 00094 (v01 PacBel PBNB000B 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b7d9fcc4 000F4 (v03 SiS    671MX    06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT b7d9b9c6 0428A (v01 PTLTD       671 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS b7da0fc0 00040
[    0.000000] ACPI: SLIC b7d9fdb8 00176 (v00 PacBel PBNB000B 06040000      00000000)
[    0.000000] ACPI: APIC b7d9ff2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG b7d9ff8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET b7d9ffc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SSDT b7d992d1 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d9922b 000A6 (v01  PmRef  Cpu7Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99185 000A6 (v01  PmRef  Cpu6Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d990df 000A6 (v01  PmRef  Cpu5Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99039 000A6 (v01  PmRef  Cpu4Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98f93 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98eed 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98e47 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d97a2d 0141A (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4de8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4100 pages used for memmap
[    0.000000]   HighMem zone: 520590 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=9b3867fe-5b6d-419c-98c6-e571f5a57d0a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d90)
[    0.000000] Memory: 2951184k/3012160k available (5818k kernel code, 60516k reserved, 2846k data, 740k init, 2098760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1831.914 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3663.82 BogoMIPS (lpj=7327656)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004059] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004100] Yama: becoming mindful.
[    0.004218] Mount-cache hash table entries: 512
[    0.004505] Initializing cgroup subsys cpuacct
[    0.004519] Initializing cgroup subsys memory
[    0.004535] Initializing cgroup subsys devices
[    0.004540] Initializing cgroup subsys freezer
[    0.004545] Initializing cgroup subsys blkio
[    0.004559] Initializing cgroup subsys perf_event
[    0.004615] CPU: Physical Processor ID: 0
[    0.004620] CPU: Processor Core ID: 0
[    0.004627] mce: CPU supports 6 MCE banks
[    0.004644] CPU0: Thermal monitoring enabled (TM2)
[    0.004651] using mwait in idle threads.
[    0.011496] ACPI: Core revision 20110623
[    0.024050] ftrace: allocating 26555 entries in 52 pages
[    0.028097] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070391] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.072003] PEBS disabled due to CPU errata.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f74cc000 soft=f74ce000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.008000] calibrate_delay_direct() ignoring timer_rate as we had a TSC wrap around start=4285634451 >=post_end=5322246
[    0.160059] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160132] Brought up 2 CPUs
[    0.160138] Total of 2 processors activated (7327.63 BogoMIPS).
[    0.162825] devtmpfs: initialized
[    0.162825] EVM: security.selinux
[    0.162825] EVM: security.SMACK64
[    0.162825] EVM: security.capability
[    0.162825] PM: Registering ACPI NVS region at b7da0000 (4096 bytes)
[    0.165914] print_constraints: dummy: 
[    0.165959] RTC time: 12:24:18, date: 10/05/12
[    0.166044] NET: Registered protocol family 16
[    0.166193] Trying to unpack rootfs image as initramfs...
[    0.166336] EISA bus registered
[    0.166370] ACPI: bus type pci registered
[    0.166517] PCI: MMCONFIG for domain 0000 [bus 00-02] at [mem 0xe0000000-0xe02fffff] (base 0xe0000000)
[    0.166524] PCI: MMCONFIG at [mem 0xe0000000-0xe02fffff] reserved in E820
[    0.166529] PCI: Using MMCONFIG for extended config space
[    0.166533] PCI: Using configuration type 1 for base access
[    0.180146] bio: create slab <bio-0> at 0
[    0.180341] ACPI: Added _OSI(Module Device)
[    0.180347] ACPI: Added _OSI(Processor Device)
[    0.180352] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180357] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182455] ACPI: EC: Look up EC in DSDT
[    0.189431] ACPI: SSDT b7d99deb 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.189986] ACPI: Dynamic OEM Table Load:
[    0.189994] ACPI: SSDT   (null) 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.192046] ACPI: SSDT b7d99530 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.192676] ACPI: Dynamic OEM Table Load:
[    0.192684] ACPI: SSDT   (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.236975] ACPI: SSDT b7d9a00a 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.237547] ACPI: Dynamic OEM Table Load:
[    0.237555] ACPI: SSDT   (null) 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.238086] ACPI: SSDT b7d99a48 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.238610] ACPI: Dynamic OEM Table Load:
[    0.238618] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.268558] ACPI: Interpreter enabled
[    0.268588] ACPI: (supports S0 S1 S3 S4 S5)
[    0.268636] ACPI: Using IOAPIC for interrupt routing
[    0.272778] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.275951] ACPI: Power Resource [QFAN] (off)
[    0.276401] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.276682] ACPI: No dock devices found.
[    0.276688] HEST: Table not found.
[    0.276701] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277471] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.278879] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.278886] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.278892] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.278899] pci_root PNP0A03:00: host bridge window [mem 0xb8000000-0xffedffff]
[    0.278905] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.278911] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.278917] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.278922] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.278927] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.278965] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.278987] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.279093] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.279160] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.279300] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.279331] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.279348] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.279365] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.279382] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.279399] pci 0000:00:02.5: reg 20: [io  0x1080-0x108f]
[    0.279469] pci 0000:00:02.5: PME# supported from D3cold
[    0.279478] pci 0000:00:02.5: PME# disabled
[    0.279506] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.279528] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.279630] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.279653] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.279761] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.279788] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.279902] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.279910] pci 0000:00:03.3: PME# disabled
[    0.279945] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.279972] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.279989] pci 0000:00:04.0: reg 14: [io  0x1000-0x107f]
[    0.280114] pci 0000:00:04.0: supports D1 D2
[    0.280119] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280127] pci 0000:00:04.0: PME# disabled
[    0.280155] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.280183] pci 0000:00:05.0: reg 10: [io  0x10c8-0x10cf]
[    0.280200] pci 0000:00:05.0: reg 14: [io  0x10bc-0x10bf]
[    0.280217] pci 0000:00:05.0: reg 18: [io  0x10c0-0x10c7]
[    0.280233] pci 0000:00:05.0: reg 1c: [io  0x10b8-0x10bb]
[    0.280250] pci 0000:00:05.0: reg 20: [io  0x10a0-0x10af]
[    0.280318] pci 0000:00:05.0: PME# supported from D3cold
[    0.280326] pci 0000:00:05.0: PME# disabled
[    0.280363] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.280498] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.280506] pci 0000:00:06.0: PME# disabled
[    0.280554] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.280687] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.280695] pci 0000:00:07.0: PME# disabled
[    0.280752] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.280781] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.280899] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.280907] pci 0000:00:0f.0: PME# disabled
[    0.280986] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.281015] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.281030] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.281045] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.281131] pci 0000:01:00.0: supports D1 D2
[    0.281195] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.281203] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.281212] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.281221] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.281305] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.281317] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.281326] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.281416] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.281461] pci_bus 0000:00: on NUMA node 0
[    0.281468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.282015]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.282023]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.282027] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.291767] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.291880] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.291988] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[    0.292113] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 9 10 11)
[    0.292252] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.292360] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.292465] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.292571] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.292891] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.292898] vgaarb: loaded
[    0.292902] vgaarb: bridge control possible 0000:01:00.0
[    0.293185] i2c-core: driver [aat2870] using legacy suspend method
[    0.293189] i2c-core: driver [aat2870] using legacy resume method
[    0.293374] SCSI subsystem initialized
[    0.293505] libata version 3.00 loaded.
[    0.293613] usbcore: registered new interface driver usbfs
[    0.293641] usbcore: registered new interface driver hub
[    0.293707] usbcore: registered new device driver usb
[    0.293919] PCI: Using ACPI for IRQ routing
[    0.293977] PCI: pci_cache_line_size set to 64 bytes
[    0.294088] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.294094] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.294337] NetLabel: Initializing
[    0.294341] NetLabel:  domain hash size = 128
[    0.294345] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.294368] NetLabel:  unlabeled traffic allowed by default
[    0.294480] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.294489] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.294500] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.300101] Switching to clocksource hpet
[    0.320328] AppArmor: AppArmor Filesystem Enabled
[    0.320395] pnp: PnP ACPI init
[    0.320437] ACPI: bus type pnp registered
[    0.321260] pnp 00:00: [bus 00-ff]
[    0.321267] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.321273] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.321279] pnp 00:00: [io  0x0d00-0xffff window]
[    0.321285] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.321290] pnp 00:00: [mem 0xb8000000-0xffedffff window]
[    0.321296] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.321301] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.321306] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.321312] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.321317] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.321323] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.321328] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.321333] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.321338] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.321344] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.321349] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.321355] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.321479] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.321833] pnp 00:01: [io  0x0000-0x000f]
[    0.321839] pnp 00:01: [io  0x0081-0x008f]
[    0.321843] pnp 00:01: [io  0x00c0-0x00df]
[    0.321848] pnp 00:01: [io  0x0480-0x048f]
[    0.321854] pnp 00:01: [dma 4]
[    0.321946] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.322008] pnp 00:02: [io  0x0070-0x0071]
[    0.322097] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.322119] pnp 00:03: [io  0x0061]
[    0.322203] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.322296] pnp 00:04: [io  0x8000-0x80be]
[    0.322301] pnp 00:04: [io  0x8100-0x812f]
[    0.322306] pnp 00:04: [io  0x0080]
[    0.322311] pnp 00:04: [io  0x04d0-0x04d1]
[    0.322316] pnp 00:04: [io  0xfe00]
[    0.322320] pnp 00:04: [io  0x002e]
[    0.322324] pnp 00:04: [io  0x002f]
[    0.322328] pnp 00:04: [io  0x0092]
[    0.322333] pnp 00:04: [io  0x0072-0x0073]
[    0.322338] pnp 00:04: [io  0x0078-0x0079]
[    0.322342] pnp 00:04: [io  0x0290-0x0297]
[    0.322347] pnp 00:04: [mem 0xe0000000-0xefffffff]
[    0.322353] pnp 00:04: [mem 0xfec00000-0xfeefffff]
[    0.322358] pnp 00:04: [mem 0xffb80000-0xffbfffff]
[    0.322363] pnp 00:04: [mem 0xffc00000-0xffc00fff]
[    0.322368] pnp 00:04: [mem 0xffe00000-0xffe00fff]
[    0.322372] pnp 00:04: [mem 0xffe80000-0xffefffff]
[    0.322528] system 00:04: [io  0x8000-0x80be] has been reserved
[    0.322535] system 00:04: [io  0x8100-0x812f] has been reserved
[    0.322542] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.322554] system 00:04: [io  0xfe00] has been reserved
[    0.322560] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.322568] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.322576] system 00:04: [mem 0xfec00000-0xfeefffff] could not be reserved
[    0.322582] system 00:04: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.322589] system 00:04: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.322596] system 00:04: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.322602] system 00:04: [mem 0xffe80000-0xffefffff] could not be reserved
[    0.322611] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322660] pnp 00:05: [io  0x00f0-0x00ff]
[    0.322684] pnp 00:05: [irq 13]
[    0.322772] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322795] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    0.322801] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    0.322806] pnp 00:06: [mem 0xffc00000-0xffc00fff]
[    0.322810] pnp 00:06: [mem 0xffe00000-0xffe00fff]
[    0.322898] pnp 00:06: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.323049] pnp 00:07: [irq 0 disabled]
[    0.323060] pnp 00:07: [irq 8]
[    0.323071] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.323171] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.323197] pnp 00:08: [io  0x0060]
[    0.323202] pnp 00:08: [io  0x0064]
[    0.323212] pnp 00:08: [irq 1]
[    0.323302] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323329] pnp 00:09: [irq 12]
[    0.323426] pnp 00:09: Plug and Play ACPI device, IDs SYN101f PNP0f13 (active)
[    0.323751] pnp: PnP ACPI: found 10 devices
[    0.323756] ACPI: ACPI bus type pnp unregistered
[    0.323765] PnPBIOS: Disabled by ACPI PNP
[    0.362706] PCI: max bus depth: 1 pci_try_num: 2
[    0.362772] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362781] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362788] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.362798] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.362807] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.362819] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.362826] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.362836] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.362845] pci 0000:00:06.0:   bridge window [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362858] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.362894] pci 0000:00:01.0: setting latency timer to 64
[    0.362934] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362943] pci 0000:00:06.0: setting latency timer to 64
[    0.362955] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362964] pci 0000:00:07.0: setting latency timer to 64
[    0.362972] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.362978] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.362984] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.362989] pci_bus 0000:00: resource 7 [mem 0xb8000000-0xffedffff]
[    0.362995] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.363000] pci_bus 0000:00: resource 9 [mem 0x000d4000-0x000d7fff]
[    0.363006] pci_bus 0000:00: resource 10 [mem 0x000d8000-0x000dbfff]
[    0.363011] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000dffff]
[    0.363017] pci_bus 0000:00: resource 12 [mem 0x000e0000-0x000e3fff]
[    0.363022] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.363028] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.363033] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.363039] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.363044] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.363050] pci_bus 0000:04: resource 2 [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.363150] NET: Registered protocol family 2
[    0.363320] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.363844] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.364815] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.365277] TCP: Hash tables configured (established 131072 bind 65536)
[    0.365282] TCP reno registered
[    0.365290] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.365308] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.365491] NET: Registered protocol family 1
[    0.365597] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.420063] pci 0000:00:03.0: PCI INT A disabled
[    0.420117] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.476062] pci 0000:00:03.1: PCI INT B disabled
[    0.476108] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.476139] pci 0000:00:03.3: PCI INT C disabled
[    0.476173] pci 0000:01:00.0: Boot video device
[    0.476180] PCI: CLS 16 bytes, default 64
[    0.476945] audit: initializing netlink socket (disabled)
[    0.476969] type=2000 audit(1349439857.472:1): initialized
[    0.525827] highmem bounce pool size: 64 pages
[    0.525840] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.530860] VFS: Disk quotas dquot_6.5.2
[    0.531007] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.532327] fuse init (API version 7.17)
[    0.532549] msgmni has been set to 1664
[    0.533264] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.533326] io scheduler noop registered
[    0.533330] io scheduler deadline registered
[    0.533346] io scheduler cfq registered (default)
[    0.533782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533842] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.534033] intel_idle: MWAIT substates: 0x22220
[    0.534038] intel_idle: does not run on family 6 model 15
[    0.534180] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.534295] ACPI: AC Adapter [ACAD] (off-line)
[    0.534455] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.534836] ACPI: Lid Switch [LID0]
[    0.534944] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.534954] ACPI: Power Button [PWRB]
[    0.535051] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.535059] ACPI: Power Button [PWRF]
[    0.535196] ACPI: Fan [FAN] (off)
[    0.542989] Monitor-Mwait will be used to enter C-1 state
[    0.543718] Monitor-Mwait will be used to enter C-2 state
[    0.544638] Monitor-Mwait will be used to enter C-3 state
[    0.544657] Marking TSC unstable due to TSC halts in idle
[    0.544675] ACPI: acpi_idle registered with cpuidle
[    0.563012] thermal LNXTHERM:00: registered as thermal_zone0
[    0.563019] ACPI: Thermal Zone [THRM] (28 C)
[    0.563088] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.563115] ACPI: Battery Slot [BAT1] (battery absent)
[    0.563226] ERST: Table is not found!
[    0.563230] GHES: HEST is not enabled!
[    0.563421] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.563682] ACPI: Battery Slot [BAT1] (battery absent)
[    0.563716] isapnp: Scanning for PnP cards...
[    0.835072] Freeing initrd memory: 13840k freed
[    0.917995] isapnp: No Plug & Play device found
[    0.964883] Linux agpgart interface v0.103
[    0.968586] brd: module loaded
[    0.970416] loop: module loaded
[    0.970844] pata_sis 0000:00:02.5: version 0.5.2
[    0.970875] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.971685] scsi0 : pata_sis
[    0.971873] scsi1 : pata_sis
[    0.972496] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    0.972503] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    0.972606] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.972679] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.973505] Fixed MDIO Bus: probed
[    0.973559] tun: Universal TUN/TAP device driver, 1.6
[    0.973565] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.973680] PPP generic driver version 2.4.2
[    0.973918] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.973952] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.973979] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.974089] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.974141] ehci_hcd 0000:00:03.3: cache line size of 16 is not supported
[    0.974173] ehci_hcd 0000:00:03.3: irq 22, io mem 0xd4106000
[    0.984028] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.984334] hub 1-0:1.0: USB hub found
[    0.984344] hub 1-0:1.0: 8 ports detected
[    0.984516] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.984544] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.984567] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.984661] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.984698] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd4104000
[    1.046258] hub 2-0:1.0: USB hub found
[    1.046269] hub 2-0:1.0: 4 ports detected
[    1.046404] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.046425] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.046528] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.046565] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4105000
[    1.102270] hub 3-0:1.0: USB hub found
[    1.102280] hub 3-0:1.0: 4 ports detected
[    1.102426] uhci_hcd: USB Universal Host Controller Interface driver
[    1.102555] usbcore: registered new interface driver libusual
[    1.102661] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.106231] i8042: Detected active multiplexing controller, rev 1.1
[    1.108075] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.108090] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.108163] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.108232] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.108293] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.108578] mousedev: PS/2 mouse device common for all mice
[    1.108969] rtc_cmos 00:02: RTC can wake from S4
[    1.109158] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.109190] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.109321] device-mapper: uevent: version 1.0.3
[    1.109482] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.109555] EISA: Probing bus 0 at eisa.0
[    1.109561] EISA: Cannot allocate resource for mainboard
[    1.109566] Cannot allocate resource for EISA slot 1
[    1.109570] Cannot allocate resource for EISA slot 2
[    1.109575] Cannot allocate resource for EISA slot 3
[    1.109579] Cannot allocate resource for EISA slot 4
[    1.109583] Cannot allocate resource for EISA slot 5
[    1.109587] Cannot allocate resource for EISA slot 6
[    1.109591] Cannot allocate resource for EISA slot 7
[    1.109595] Cannot allocate resource for EISA slot 8
[    1.109599] EISA: Detected 0 cards.
[    1.109617] cpufreq-nforce2: No nForce2 chipset.
[    1.109765] cpuidle: using governor ladder
[    1.110002] cpuidle: using governor menu
[    1.110007] EFI Variables Facility v0.08 2004-May-17
[    1.110629] TCP cubic registered
[    1.110911] NET: Registered protocol family 10
[    1.112310] NET: Registered protocol family 17
[    1.112320] Registering the dns_resolver key type
[    1.112363] Using IPI No-Shortcut mode
[    1.112632] PM: Hibernation image not present or could not be loaded.
[    1.112660] registered taskstats version 1
[    1.127592]   Magic number: 0:47:430
[    1.127741] rtc_cmos 00:02: setting system clock to 2012-10-05 12:24:19 UTC (1349439859)
[    1.128466] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128469] EDD information not available.
[    1.136288] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    1.144278] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.152277] ata1.00: configured for UDMA/33
[    1.163911] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    1.166159] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.166163] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.166331] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.166468] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.166577] ata2: port disabled--ignoring
[    1.166723] Freeing unused kernel memory: 740k freed
[    1.167178] Write protecting the kernel text: 5820k
[    1.167208] Write protecting the kernel read-only data: 2376k
[    1.167210] NX-protecting the kernel data: 4420k
[    1.189602] udevd[96]: starting version 175
[    1.273478] sata_sis 0000:00:05.0: version 1.0
[    1.273507] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.273514] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.277333] scsi2 : sata_sis
[    1.280691] scsi3 : sata_sis
[    1.281306] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
[    1.281310] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17
[    1.284286] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.284336] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.284354] sis190 0000:00:04.0: setting latency timer to 64
[    1.284379] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.352039] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.372030] sis190: 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1
[    1.444254] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.444258] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.460247] ata3.00: configured for UDMA/133
[    1.460447] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.460692] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.460696] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.460765] sd 2:0:0:0: [sda] Write Protect is off
[    1.460769] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.460797] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.502750] usbcore: registered new interface driver uas
[    1.503009] Initializing USB Mass Storage driver...
[    1.503057] usbcore: registered new interface driver usb-storage
[    1.503059] USB Mass Storage support registered.
[    1.526730]  sda: sda1 sda2 < sda5 >
[    1.527244] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.612026] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.631264] scsi4 : usb-storage 1-4:1.0
[    1.631386] usbcore: registered new interface driver ums-realtek
[    1.864031] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[    1.888030] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.920719] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8412000 (IRQ: 19), 00:1e:68:24:0c:41
[    1.920724] sis190 0000:00:04.0: eth0: GMII mode.
[    1.920733] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
[    2.107420] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.324051] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    2.640660] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.641500] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.644025] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   19.543368] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.570556] udevd[307]: starting version 175
[   19.656983] Adding 3010556k swap on /dev/sda5.  Priority:-1 extents:1 across:3010556k 
[   19.683938] lp: driver loaded but no devices found
[   19.686711] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   19.688644] type=1400 audit(1349432678.056:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=359 comm="apparmor_parser"
[   19.689180] type=1400 audit(1349432678.056:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=359 comm="apparmor_parser"
[   19.689477] type=1400 audit(1349432678.056:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=359 comm="apparmor_parser"
[   19.698481] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   19.699511] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.822716] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.831664] Linux video capture interface: v2.00
[   19.837042] uvcvideo: Found UVC 1.00 device CNF7045 (04f2:b062)
[   19.844141] acpi device:0e: registered as cooling_device3
[   19.844889] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input4
[   19.845098] input: CNF7045 as /devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input5
[   19.845186] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.845572] usbcore: registered new interface driver uvcvideo
[   19.845576] USB Video Class driver (1.1.1)
[   19.904694] cfg80211: Calling CRDA to update world regulatory domain
[   19.918849] input: MLK OM1007 Wireless Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input6
[   19.919113] generic-usb 0003:04FC:0538.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK OM1007 Wireless Mouse] on usb-0000:00:03.0-2/input0
[   19.919142] usbcore: registered new interface driver usbhid
[   19.919145] usbhid: USB HID core driver
[   19.969396] snd_hda_intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.969484] snd_hda_intel 0000:00:0f.0: setting latency timer to 64
[   20.019329] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input7
[   20.019574] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input8
[   20.098666] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.244074] cfg80211: World regulatory domain updated:
[   20.244081] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.244085] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.244088] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.244092] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.244095] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.244098] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349542] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.349548] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349551] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.349555] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349558] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.349561] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349564] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.349567] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349570] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.349573] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349576] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.349580] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349582] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.349586] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349589] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.349592] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349595] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.349598] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349601] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.349605] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349607] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.349611] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349614] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.349617] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.349620] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.349623] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.349626] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.349630] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.353174] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.354012] ieee80211 phy0: hwaddr 00:17:c4:1c:54:1d, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   20.378967] rtl8187: Customer ID is 0x00
[   20.379045] Registered led device: rtl8187-phy0::radio
[   20.379075] Registered led device: rtl8187-phy0::tx
[   20.379103] Registered led device: rtl8187-phy0::rx
[   20.380374] rtl8187: wireless switch is on
[   20.380458] usbcore: registered new interface driver rtl8187
[   20.488706] init: failsafe main process (730) killed by TERM signal
[   20.590307] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.590311] vesafb: scrolling: redraw
[   20.590314] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.591694] vesafb: framebuffer at 0xc0000000, mapped to 0xf8800000, using 1216k, total 1216k
[   20.591887] Console: switching to colour frame buffer device 80x30
[   20.591905] fb0: VESA VGA frame buffer device
[   20.626057] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   20.633507] ppdev: user-space parallel port driver
[   20.670748] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.720449] Bluetooth: Core ver 2.16
[   20.720481] NET: Registered protocol family 31
[   20.720484] Bluetooth: HCI device and connection manager initialized
[   20.720488] Bluetooth: HCI socket layer initialized
[   20.720491] Bluetooth: L2CAP socket layer initialized
[   20.725183] Bluetooth: SCO socket layer initialized
[   20.730346] type=1400 audit(1349432679.096:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=808 comm="apparmor_parser"
[   20.731001] type=1400 audit(1349432679.096:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=808 comm="apparmor_parser"
[   20.756064] Bluetooth: RFCOMM TTY layer initialized
[   20.756073] Bluetooth: RFCOMM socket layer initialized
[   20.756076] Bluetooth: RFCOMM ver 1.11
[   20.772095] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.772099] Bluetooth: BNEP filters: protocol multicast
[   20.877909] type=1400 audit(1349432679.244:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   20.881033] type=1400 audit(1349432679.248:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=848 comm="apparmor_parser"
[   20.883185] type=1400 audit(1349432679.248:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   20.883491] type=1400 audit(1349432679.248:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   20.897511] type=1400 audit(1349432679.264:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=852 comm="apparmor_parser"
[   21.368701] init: kdm main process (918) killed by TERM signal
[   24.743118] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.743575] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.747666] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.748176] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.756144] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[   30.037414] wlan0: direct probe to 40:4a:03:fb:6d:6c (try 1/3)
[   30.041899] wlan0: direct probe responded
[   30.056107] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[   30.057913] wlan0: authenticated
[   30.059039] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[   30.069660] wlan0: RX AssocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[   30.069670] wlan0: associated
[   30.075706] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.077391] cfg80211: Calling CRDA for country: NL
[   30.085562] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   30.085568] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085572] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   30.085575] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085578] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   30.085581] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085584] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   30.085588] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085590] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   30.085594] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085597] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   30.085600] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085603] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   30.085606] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085609] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   30.085612] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085615] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   30.085618] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085621] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   30.085624] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085627] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   30.085631] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085633] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   30.085637] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085639] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   30.085643] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085645] cfg80211: Disabling freq 2484 MHz
[   30.085649] cfg80211: Regulatory domain changed to country: NL
[   30.085651] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.085654] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.085657] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.085660] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.085663] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   34.776022] sis190 0000:00:04.0: eth0: auto-negotiating...
[   37.420544] init: plymouth-stop pre-start process (1416) terminated with status 1
[   40.872072] wlan0: no IPv6 routers present
[   53.780600] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   53.782093] sd 4:0:0:0: [sdb] Asking for cache data failed
[   53.782098] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  103.508068] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  106.008562] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  106.010054] sd 4:0:0:0: [sdb] Asking for cache data failed
[  106.010062] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  120.916076] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  122.404045] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[  122.492165] cfg80211: All devices are disconnected, going to restore regulatory settings
[  122.492175] cfg80211: Restoring regulatory settings
[  122.492192] cfg80211: Calling CRDA to update world regulatory domain
[  122.501422] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  122.501431] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501437] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  122.501444] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501450] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  122.501456] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501461] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  122.501468] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501473] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  122.501479] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501484] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  122.501490] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501495] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  122.501501] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501506] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  122.501512] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501517] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  122.501524] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501529] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  122.501535] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501540] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  122.501546] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501551] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  122.501557] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501562] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  122.501569] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501574] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  122.501580] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501586] cfg80211: World regulatory domain updated:
[  122.501590] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  122.501596] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501602] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501608] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501614] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501619] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  124.853357] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[  124.855466] wlan0: authenticated
[  124.993286] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[  125.003528] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[  125.003535] wlan0: associated
[  125.009549] cfg80211: Calling CRDA for country: NL
[  125.018238] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  125.018266] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018272] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  125.018278] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018284] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  125.018290] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018296] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  125.018307] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018312] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  125.018318] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018323] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  125.018330] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018335] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  125.018341] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018346] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  125.018352] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018357] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  125.018364] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018369] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  125.018375] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018380] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  125.018394] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018400] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  125.018406] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018411] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  125.018417] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018422] cfg80211: Disabling freq 2484 MHz
[  125.018428] cfg80211: Regulatory domain changed to country: NL
[  125.018432] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  125.018438] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.018443] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.018449] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.018454] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  156.196588] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.198079] sd 4:0:0:0: [sdb] Asking for cache data failed
[  156.198086] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  207.896514] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  207.898005] sd 4:0:0:0: [sdb] Asking for cache data failed
[  207.898010] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  208.020080] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  259.608591] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  259.610082] sd 4:0:0:0: [sdb] Asking for cache data failed
[  259.610089] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  259.780072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  311.320654] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  311.322145] sd 4:0:0:0: [sdb] Asking for cache data failed
[  311.322152] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  311.480071] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  363.032589] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  363.034081] sd 4:0:0:0: [sdb] Asking for cache data failed
[  363.034089] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  363.208078] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  414.742642] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  414.744242] sd 4:0:0:0: [sdb] Asking for cache data failed
[  414.744248] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  414.884041] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  432.548046] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[  432.640183] cfg80211: All devices are disconnected, going to restore regulatory settings
[  432.640192] cfg80211: Restoring regulatory settings
[  432.640200] cfg80211: Calling CRDA to update world regulatory domain
[  432.649270] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  432.649280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649286] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  432.649292] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649298] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  432.649304] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649309] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  432.649315] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649320] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  432.649326] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649331] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  432.649337] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649342] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  432.649349] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649354] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  432.649360] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649365] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  432.649371] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649376] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  432.649382] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649387] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  432.649394] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649399] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  432.649405] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649410] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  432.649416] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649422] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  432.649428] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649434] cfg80211: World regulatory domain updated:
[  432.649438] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  432.649444] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649450] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649456] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649462] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649468] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  435.001282] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[  435.007021] wlan0: authenticated
[  435.141338] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[  435.150474] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[  435.150480] wlan0: associated
[  435.156484] cfg80211: Calling CRDA for country: NL
[  435.164911] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  435.164920] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164926] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  435.164932] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164938] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  435.164944] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164949] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  435.164955] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164961] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  435.164967] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164972] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  435.164978] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164983] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  435.164989] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164994] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  435.165000] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165005] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  435.165011] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165016] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  435.165022] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165027] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  435.165033] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165038] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  435.165044] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165049] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  435.165056] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165060] cfg80211: Disabling freq 2484 MHz
[  435.165067] cfg80211: Regulatory domain changed to country: NL
[  435.165071] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  435.165076] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  435.165082] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  435.165087] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  435.165092] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  466.452575] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  466.454066] sd 4:0:0:0: [sdb] Asking for cache data failed
[  466.454070] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  466.572065] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  514.687472] show_signal_msg: 42 callbacks suppressed
[  514.687478] nepomukservices[1731]: segfault at 0 ip   (null) sp bfb7391c error 14 in nepomukservicestub[8048000+6000]
[  517.669607] mtrr: no MTRR for c0000000,8000000 found
[  518.164379] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  518.165874] sd 4:0:0:0: [sdb] Asking for cache data failed
[  518.165879] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  569.880586] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  569.882076] sd 4:0:0:0: [sdb] Asking for cache data failed
[  569.882083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  621.588636] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  621.590133] sd 4:0:0:0: [sdb] Asking for cache data failed
[  621.590139] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  673.304584] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  673.306076] sd 4:0:0:0: [sdb] Asking for cache data failed
[  673.306083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  673.456083] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  725.016646] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  725.018138] sd 4:0:0:0: [sdb] Asking for cache data failed
[  725.018144] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  725.148094] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  776.728582] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  776.730074] sd 4:0:0:0: [sdb] Asking for cache data failed
[  776.730081] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  808.020162] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  826.916790] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  826.918252] sd 4:0:0:0: [sdb] Asking for cache data failed
[  826.918263] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  827.044089] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  827.348080] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  877.092638] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  877.094128] sd 4:0:0:0: [sdb] Asking for cache data failed
[  877.094135] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  877.252074] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  928.792579] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  928.794071] sd 4:0:0:0: [sdb] Asking for cache data failed
[  928.794078] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  928.948072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  980.504640] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  980.506132] sd 4:0:0:0: [sdb] Asking for cache data failed
[  980.506139] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  980.636079] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
```
Could you (or someone else) explain to me what a 'module' is, and what it means to 'blacklist' it?


Thanks for all your thinking, time, effort, NikTH!

---

### Post by NikTh on 2012-10-05
Hi , 
module = driver. Linux has lot of drivers integrated. 

I see that the module is loaded. 
Blacklist means to prevent the module from loading in boot. 
If I am right about this module bug (bug means fault - problem) then do as follows . 

```
sudo sed -i 's/blacklist ums_realtek//g' /etc/modprobe.d/blacklist.conf
```above command will remove the line **blacklist ums_realtek** from blacklist.conf file.

Then do this. 

```
gksudo kate /etc/rc.local
```at the opened window add the following line **before _exit 0_**
```
modprobe -r ums_realtek
```save the document and reboot. 
When login  open the terminal and copy-paste the bellow command 
```
dmesg | grep sdb
```Post back here the results. 

Thanks

---

### Post by Noor1101 on 2012-10-06
> **NikTh said:**
> 
```
gksudo kate /etc/rc.local
```at the opened window add the following line **before _exit 0_**
```
modprobe -r ums_realtek
```save the document and reboot. 


Hi, there is no window opening after giving the command above, all it does is

```
noor@noor-EasyNote-MH35:~$ gksudo kate /etc/rc.local
noor@noor-EasyNote-MH35:~$ 

```and nothing else happens.

When I browse to the rc.local file, open it with KWrite or gedit and try to add the line, I'm not allowed to save it:
it says "Access denied"
I think I have to get some kind of root-permissions? How do I do that?

Thanks

--edit-- I tried giving the command ```
sudo -i
``` first and then, after giving my password 
give the command ```
gksudo kate /etc/rc.local
``` again, but still nothing happens

---

### Post by Noor1101 on 2012-10-06
> **Noor1101 said:**
> Hi, there is no window opening after giving the command 
[....]

When I browse to the rc.local file, open it with KWrite or gedit and try to add the line, I'm not allowed to save it:
it says "Access denied"
I think I have to get some kind of root-permissions? How do I do that?



I got it, I now understand 'kate' is a text editor and it is not installed on my computer so I instead used the command ```
gksudo gedit /etc/rc.local
```That made the system ask me for my password and I was able to add the line above exit 0. So I rebooted, and here is the output you requested:
```
noor@noor-EasyNote-MH35:~$ dmesg | grep sdb
[    2.624236] sd 4:0:0:0: [sdb] Attached SCSI removable disk
noor@noor-EasyNote-MH35:~$ 
```
Thanks Nik :)


edit: I made a new dmesg.txt file, thought that might be helpful..?

```
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7da0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7da0000 - 00000000b7da1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7da1000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: PACKARD BELL BV EasyNote MH35/PE1, BIOS PE14A04  02/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f86c0] f86c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000f8690 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT b7d97999 00094 (v01 PacBel PBNB000B 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b7d9fcc4 000F4 (v03 SiS    671MX    06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT b7d9b9c6 0428A (v01 PTLTD       671 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS b7da0fc0 00040
[    0.000000] ACPI: SLIC b7d9fdb8 00176 (v00 PacBel PBNB000B 06040000      00000000)
[    0.000000] ACPI: APIC b7d9ff2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG b7d9ff8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET b7d9ffc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SSDT b7d992d1 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d9922b 000A6 (v01  PmRef  Cpu7Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99185 000A6 (v01  PmRef  Cpu6Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d990df 000A6 (v01  PmRef  Cpu5Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99039 000A6 (v01  PmRef  Cpu4Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98f93 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98eed 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98e47 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d97a2d 0141A (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4de8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4100 pages used for memmap
[    0.000000]   HighMem zone: 520590 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=9b3867fe-5b6d-419c-98c6-e571f5a57d0a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d90)
[    0.000000] Memory: 2951184k/3012160k available (5818k kernel code, 60516k reserved, 2846k data, 740k init, 2098760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1831.834 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3663.66 BogoMIPS (lpj=7327336)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004059] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004100] Yama: becoming mindful.
[    0.004220] Mount-cache hash table entries: 512
[    0.004508] Initializing cgroup subsys cpuacct
[    0.004521] Initializing cgroup subsys memory
[    0.004538] Initializing cgroup subsys devices
[    0.004543] Initializing cgroup subsys freezer
[    0.004547] Initializing cgroup subsys blkio
[    0.004562] Initializing cgroup subsys perf_event
[    0.004618] CPU: Physical Processor ID: 0
[    0.004622] CPU: Processor Core ID: 0
[    0.004628] mce: CPU supports 6 MCE banks
[    0.004645] CPU0: Thermal monitoring enabled (TM2)
[    0.004652] using mwait in idle threads.
[    0.011073] ACPI: Core revision 20110623
[    0.024051] ftrace: allocating 26555 entries in 52 pages
[    0.028096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028434] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069772] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.072003] PEBS disabled due to CPU errata.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f74cc000 soft=f74ce000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.160059] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160131] Brought up 2 CPUs
[    0.160137] Total of 2 processors activated (7327.46 BogoMIPS).
[    0.162831] devtmpfs: initialized
[    0.162831] EVM: security.selinux
[    0.162831] EVM: security.SMACK64
[    0.162831] EVM: security.capability
[    0.162831] PM: Registering ACPI NVS region at b7da0000 (4096 bytes)
[    0.165923] print_constraints: dummy: 
[    0.165969] RTC time: 21:02:32, date: 10/04/12
[    0.166055] NET: Registered protocol family 16
[    0.166206] Trying to unpack rootfs image as initramfs...
[    0.166347] EISA bus registered
[    0.166380] ACPI: bus type pci registered
[    0.166529] PCI: MMCONFIG for domain 0000 [bus 00-02] at [mem 0xe0000000-0xe02fffff] (base 0xe0000000)
[    0.166536] PCI: MMCONFIG at [mem 0xe0000000-0xe02fffff] reserved in E820
[    0.166540] PCI: Using MMCONFIG for extended config space
[    0.166544] PCI: Using configuration type 1 for base access
[    0.180149] bio: create slab <bio-0> at 0
[    0.180342] ACPI: Added _OSI(Module Device)
[    0.180348] ACPI: Added _OSI(Processor Device)
[    0.180353] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180358] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182460] ACPI: EC: Look up EC in DSDT
[    0.189432] ACPI: SSDT b7d99deb 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.189987] ACPI: Dynamic OEM Table Load:
[    0.189995] ACPI: SSDT   (null) 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.192052] ACPI: SSDT b7d99530 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.192683] ACPI: Dynamic OEM Table Load:
[    0.192691] ACPI: SSDT   (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.236980] ACPI: SSDT b7d9a00a 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.237553] ACPI: Dynamic OEM Table Load:
[    0.237561] ACPI: SSDT   (null) 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.238093] ACPI: SSDT b7d99a48 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.238619] ACPI: Dynamic OEM Table Load:
[    0.238626] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.268561] ACPI: Interpreter enabled
[    0.268592] ACPI: (supports S0 S1 S3 S4 S5)
[    0.268639] ACPI: Using IOAPIC for interrupt routing
[    0.272778] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.275960] ACPI: Power Resource [QFAN] (off)
[    0.276403] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.276685] ACPI: No dock devices found.
[    0.276691] HEST: Table not found.
[    0.276704] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277472] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.278881] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.278888] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.278894] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.278900] pci_root PNP0A03:00: host bridge window [mem 0xb8000000-0xffedffff]
[    0.278906] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.278913] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.278919] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.278925] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.278930] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.278967] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.278989] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.279094] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.279162] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.279303] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.279333] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.279350] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.279367] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.279384] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.279401] pci 0000:00:02.5: reg 20: [io  0x1080-0x108f]
[    0.279472] pci 0000:00:02.5: PME# supported from D3cold
[    0.279481] pci 0000:00:02.5: PME# disabled
[    0.279508] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.279531] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.279632] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.279655] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.279763] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.279790] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.279905] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.279913] pci 0000:00:03.3: PME# disabled
[    0.279948] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.279976] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.279993] pci 0000:00:04.0: reg 14: [io  0x1000-0x107f]
[    0.280112] pci 0000:00:04.0: supports D1 D2
[    0.280117] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280126] pci 0000:00:04.0: PME# disabled
[    0.280154] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.280181] pci 0000:00:05.0: reg 10: [io  0x10c8-0x10cf]
[    0.280198] pci 0000:00:05.0: reg 14: [io  0x10bc-0x10bf]
[    0.280215] pci 0000:00:05.0: reg 18: [io  0x10c0-0x10c7]
[    0.280231] pci 0000:00:05.0: reg 1c: [io  0x10b8-0x10bb]
[    0.280248] pci 0000:00:05.0: reg 20: [io  0x10a0-0x10af]
[    0.280317] pci 0000:00:05.0: PME# supported from D3cold
[    0.280325] pci 0000:00:05.0: PME# disabled
[    0.280362] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.280497] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.280505] pci 0000:00:06.0: PME# disabled
[    0.280553] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.280687] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.280695] pci 0000:00:07.0: PME# disabled
[    0.280751] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.280781] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.280899] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.280907] pci 0000:00:0f.0: PME# disabled
[    0.280987] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.281016] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.281032] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.281047] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.281133] pci 0000:01:00.0: supports D1 D2
[    0.281196] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.281205] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.281214] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.281222] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.281307] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.281319] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.281328] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.281420] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.281465] pci_bus 0000:00: on NUMA node 0
[    0.281472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.282019]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.282027]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.282031] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.291764] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.291878] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.291986] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[    0.292104] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 9 10 11)
[    0.292243] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.292350] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.292456] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.292562] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.292880] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.292887] vgaarb: loaded
[    0.292891] vgaarb: bridge control possible 0000:01:00.0
[    0.293174] i2c-core: driver [aat2870] using legacy suspend method
[    0.293179] i2c-core: driver [aat2870] using legacy resume method
[    0.293365] SCSI subsystem initialized
[    0.293495] libata version 3.00 loaded.
[    0.293602] usbcore: registered new interface driver usbfs
[    0.293630] usbcore: registered new interface driver hub
[    0.293696] usbcore: registered new device driver usb
[    0.293908] PCI: Using ACPI for IRQ routing
[    0.293967] PCI: pci_cache_line_size set to 64 bytes
[    0.294079] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.294085] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.294329] NetLabel: Initializing
[    0.294333] NetLabel:  domain hash size = 128
[    0.294337] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.294361] NetLabel:  unlabeled traffic allowed by default
[    0.294473] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.294481] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.294493] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.300101] Switching to clocksource hpet
[    0.320291] AppArmor: AppArmor Filesystem Enabled
[    0.320360] pnp: PnP ACPI init
[    0.320403] ACPI: bus type pnp registered
[    0.321220] pnp 00:00: [bus 00-ff]
[    0.321227] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.321233] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.321239] pnp 00:00: [io  0x0d00-0xffff window]
[    0.321245] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.321251] pnp 00:00: [mem 0xb8000000-0xffedffff window]
[    0.321257] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.321262] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.321268] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.321273] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.321278] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.321284] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.321289] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.321294] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.321300] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.321305] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.321310] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.321315] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.321444] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.321799] pnp 00:01: [io  0x0000-0x000f]
[    0.321804] pnp 00:01: [io  0x0081-0x008f]
[    0.321809] pnp 00:01: [io  0x00c0-0x00df]
[    0.321814] pnp 00:01: [io  0x0480-0x048f]
[    0.321820] pnp 00:01: [dma 4]
[    0.321912] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.321974] pnp 00:02: [io  0x0070-0x0071]
[    0.322065] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.322086] pnp 00:03: [io  0x0061]
[    0.322171] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.322264] pnp 00:04: [io  0x8000-0x80be]
[    0.322269] pnp 00:04: [io  0x8100-0x812f]
[    0.322274] pnp 00:04: [io  0x0080]
[    0.322279] pnp 00:04: [io  0x04d0-0x04d1]
[    0.322284] pnp 00:04: [io  0xfe00]
[    0.322288] pnp 00:04: [io  0x002e]
[    0.322292] pnp 00:04: [io  0x002f]
[    0.322297] pnp 00:04: [io  0x0092]
[    0.322301] pnp 00:04: [io  0x0072-0x0073]
[    0.322306] pnp 00:04: [io  0x0078-0x0079]
[    0.322310] pnp 00:04: [io  0x0290-0x0297]
[    0.322316] pnp 00:04: [mem 0xe0000000-0xefffffff]
[    0.322321] pnp 00:04: [mem 0xfec00000-0xfeefffff]
[    0.322325] pnp 00:04: [mem 0xffb80000-0xffbfffff]
[    0.322330] pnp 00:04: [mem 0xffc00000-0xffc00fff]
[    0.322335] pnp 00:04: [mem 0xffe00000-0xffe00fff]
[    0.322340] pnp 00:04: [mem 0xffe80000-0xffefffff]
[    0.322496] system 00:04: [io  0x8000-0x80be] has been reserved
[    0.322503] system 00:04: [io  0x8100-0x812f] has been reserved
[    0.322510] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.322522] system 00:04: [io  0xfe00] has been reserved
[    0.322528] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.322537] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.322544] system 00:04: [mem 0xfec00000-0xfeefffff] could not be reserved
[    0.322550] system 00:04: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.322557] system 00:04: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.322564] system 00:04: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.322570] system 00:04: [mem 0xffe80000-0xffefffff] could not be reserved
[    0.322579] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322628] pnp 00:05: [io  0x00f0-0x00ff]
[    0.322661] pnp 00:05: [irq 13]
[    0.322750] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322773] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    0.322778] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    0.322783] pnp 00:06: [mem 0xffc00000-0xffc00fff]
[    0.322788] pnp 00:06: [mem 0xffe00000-0xffe00fff]
[    0.322875] pnp 00:06: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.323026] pnp 00:07: [irq 0 disabled]
[    0.323038] pnp 00:07: [irq 8]
[    0.323049] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.323149] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.323174] pnp 00:08: [io  0x0060]
[    0.323178] pnp 00:08: [io  0x0064]
[    0.323188] pnp 00:08: [irq 1]
[    0.323279] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323306] pnp 00:09: [irq 12]
[    0.323402] pnp 00:09: Plug and Play ACPI device, IDs SYN101f PNP0f13 (active)
[    0.323728] pnp: PnP ACPI: found 10 devices
[    0.323732] ACPI: ACPI bus type pnp unregistered
[    0.323742] PnPBIOS: Disabled by ACPI PNP
[    0.362665] PCI: max bus depth: 1 pci_try_num: 2
[    0.362732] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362740] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362747] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.362758] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.362766] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.362779] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.362785] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.362796] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.362805] pci 0000:00:06.0:   bridge window [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362817] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.362853] pci 0000:00:01.0: setting latency timer to 64
[    0.362892] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362901] pci 0000:00:06.0: setting latency timer to 64
[    0.362913] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362922] pci 0000:00:07.0: setting latency timer to 64
[    0.362931] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.362937] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.362943] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.362948] pci_bus 0000:00: resource 7 [mem 0xb8000000-0xffedffff]
[    0.362954] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.362959] pci_bus 0000:00: resource 9 [mem 0x000d4000-0x000d7fff]
[    0.362965] pci_bus 0000:00: resource 10 [mem 0x000d8000-0x000dbfff]
[    0.362970] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000dffff]
[    0.362976] pci_bus 0000:00: resource 12 [mem 0x000e0000-0x000e3fff]
[    0.362982] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.362987] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.362993] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.362999] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.363004] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.363010] pci_bus 0000:04: resource 2 [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.363109] NET: Registered protocol family 2
[    0.363279] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.363817] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.364778] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.365245] TCP: Hash tables configured (established 131072 bind 65536)
[    0.365250] TCP reno registered
[    0.365257] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.365275] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.365458] NET: Registered protocol family 1
[    0.365553] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.420063] pci 0000:00:03.0: PCI INT A disabled
[    0.420114] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.476062] pci 0000:00:03.1: PCI INT B disabled
[    0.476108] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.476139] pci 0000:00:03.3: PCI INT C disabled
[    0.476173] pci 0000:01:00.0: Boot video device
[    0.476180] PCI: CLS 16 bytes, default 64
[    0.476941] audit: initializing netlink socket (disabled)
[    0.476965] type=2000 audit(1349384551.472:1): initialized
[    0.525812] highmem bounce pool size: 64 pages
[    0.525824] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.530845] VFS: Disk quotas dquot_6.5.2
[    0.530990] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.532307] fuse init (API version 7.17)
[    0.532529] msgmni has been set to 1664
[    0.533245] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.533303] io scheduler noop registered
[    0.533307] io scheduler deadline registered
[    0.533323] io scheduler cfq registered (default)
[    0.533769] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533829] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.534022] intel_idle: MWAIT substates: 0x22220
[    0.534027] intel_idle: does not run on family 6 model 15
[    0.534172] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.534288] ACPI: AC Adapter [ACAD] (off-line)
[    0.534449] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.534826] ACPI: Lid Switch [LID0]
[    0.534934] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.534943] ACPI: Power Button [PWRB]
[    0.535043] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.535050] ACPI: Power Button [PWRF]
[    0.535187] ACPI: Fan [FAN] (off)
[    0.552413] Monitor-Mwait will be used to enter C-1 state
[    0.552473] Monitor-Mwait will be used to enter C-2 state
[    0.560341] Monitor-Mwait will be used to enter C-3 state
[    0.560360] Marking TSC unstable due to TSC halts in idle
[    0.560385] ACPI: acpi_idle registered with cpuidle
[    0.567031] thermal LNXTHERM:00: registered as thermal_zone0
[    0.567037] ACPI: Thermal Zone [THRM] (52 C)
[    0.567098] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.567123] ACPI: Battery Slot [BAT1] (battery absent)
[    0.567183] ERST: Table is not found!
[    0.567188] GHES: HEST is not enabled!
[    0.567376] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.567682] ACPI: Battery Slot [BAT1] (battery absent)
[    0.567698] isapnp: Scanning for PnP cards...
[    0.830506] Freeing initrd memory: 13840k freed
[    0.922210] isapnp: No Plug & Play device found
[    0.965034] Linux agpgart interface v0.103
[    0.968723] brd: module loaded
[    0.970569] loop: module loaded
[    0.971001] pata_sis 0000:00:02.5: version 0.5.2
[    0.971030] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.971848] scsi0 : pata_sis
[    0.972049] scsi1 : pata_sis
[    0.972628] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    0.972634] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    0.972743] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.972815] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.973643] Fixed MDIO Bus: probed
[    0.973696] tun: Universal TUN/TAP device driver, 1.6
[    0.973702] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.973819] PPP generic driver version 2.4.2
[    0.974049] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.974085] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.974112] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.974209] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.974255] ehci_hcd 0000:00:03.3: cache line size of 16 is not supported
[    0.974288] ehci_hcd 0000:00:03.3: irq 22, io mem 0xd4106000
[    0.984029] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.984356] hub 1-0:1.0: USB hub found
[    0.984366] hub 1-0:1.0: 8 ports detected
[    0.984533] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.984561] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.984590] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.984685] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.984724] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd4104000
[    1.046255] hub 2-0:1.0: USB hub found
[    1.046266] hub 2-0:1.0: 4 ports detected
[    1.046402] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.046424] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.046531] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.046568] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4105000
[    1.102269] hub 3-0:1.0: USB hub found
[    1.102279] hub 3-0:1.0: 4 ports detected
[    1.102427] uhci_hcd: USB Universal Host Controller Interface driver
[    1.102558] usbcore: registered new interface driver libusual
[    1.102666] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.106549] i8042: Detected active multiplexing controller, rev 1.1
[    1.108028] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.108041] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.108116] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.108177] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.108244] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.108519] mousedev: PS/2 mouse device common for all mice
[    1.108913] rtc_cmos 00:02: RTC can wake from S4
[    1.109113] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.109145] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.109276] device-mapper: uevent: version 1.0.3
[    1.109442] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.109520] EISA: Probing bus 0 at eisa.0
[    1.109525] EISA: Cannot allocate resource for mainboard
[    1.109530] Cannot allocate resource for EISA slot 1
[    1.109535] Cannot allocate resource for EISA slot 2
[    1.109539] Cannot allocate resource for EISA slot 3
[    1.109544] Cannot allocate resource for EISA slot 4
[    1.109548] Cannot allocate resource for EISA slot 5
[    1.109552] Cannot allocate resource for EISA slot 6
[    1.109556] Cannot allocate resource for EISA slot 7
[    1.109560] Cannot allocate resource for EISA slot 8
[    1.109564] EISA: Detected 0 cards.
[    1.109583] cpufreq-nforce2: No nForce2 chipset.
[    1.109728] cpuidle: using governor ladder
[    1.109965] cpuidle: using governor menu
[    1.109971] EFI Variables Facility v0.08 2004-May-17
[    1.110596] TCP cubic registered
[    1.110881] NET: Registered protocol family 10
[    1.112280] NET: Registered protocol family 17
[    1.112290] Registering the dns_resolver key type
[    1.112330] Using IPI No-Shortcut mode
[    1.112609] PM: Hibernation image not present or could not be loaded.
[    1.112640] registered taskstats version 1
[    1.127525]   Magic number: 0:514:44
[    1.127672] rtc_cmos 00:02: setting system clock to 2012-10-04 21:02:33 UTC (1349384553)
[    1.128443] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128446] EDD information not available.
[    1.136312] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    1.144429] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.152286] ata1.00: configured for UDMA/33
[    1.154721] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    1.157033] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.157037] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.157202] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.157334] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.157453] ata2: port disabled--ignoring
[    1.157592] Freeing unused kernel memory: 740k freed
[    1.158017] Write protecting the kernel text: 5820k
[    1.158047] Write protecting the kernel read-only data: 2376k
[    1.158049] NX-protecting the kernel data: 4420k
[    1.179936] udevd[96]: starting version 175
[    1.269990] sata_sis 0000:00:05.0: version 1.0
[    1.270015] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.270022] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.271574] scsi2 : sata_sis
[    1.272176] scsi3 : sata_sis
[    1.272752] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
[    1.272757] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17
[    1.272904] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.272947] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.272961] sis190 0000:00:04.0: setting latency timer to 64
[    1.272985] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.352043] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.360020] sis190: 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1
[    1.436255] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.436259] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.452245] ata3.00: configured for UDMA/133
[    1.452446] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.452678] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.452687] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.452762] sd 2:0:0:0: [sda] Write Protect is off
[    1.452766] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.452795] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.502881] Initializing USB Mass Storage driver...
[    1.502948] usbcore: registered new interface driver usb-storage
[    1.502950] USB Mass Storage support registered.
[    1.503175] usbcore: registered new interface driver uas
[    1.519544]  sda: sda1 sda2 < sda5 >
[    1.520106] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.620260] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.624375] scsi4 : usb-storage 1-4:1.0
[    1.624485] usbcore: registered new interface driver ums-realtek
[    1.872041] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[    1.880018] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.920711] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8412000 (IRQ: 19), 00:1e:68:24:0c:41
[    1.920716] sis190 0000:00:04.0: eth0: GMII mode.
[    1.920723] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
[    2.133165] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.320032] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    2.636651] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.637495] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.640000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   19.501226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.529827] udevd[312]: starting version 175
[   19.616508] Adding 3010556k swap on /dev/sda5.  Priority:-1 extents:1 across:3010556k 
[   19.654825] lp: driver loaded but no devices found
[   19.657957] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.658170] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   19.664979] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   19.727946] type=1400 audit(1349377372.093:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
[   19.728543] type=1400 audit(1349377372.097:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=415 comm="apparmor_parser"
[   19.728848] type=1400 audit(1349377372.097:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=415 comm="apparmor_parser"
[   19.821793] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.853365] cfg80211: Calling CRDA to update world regulatory domain
[   19.962570] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.965029] Linux video capture interface: v2.00
[   19.967496] acpi device:0e: registered as cooling_device3
[   19.967641] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input4
[   19.967755] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.968731] uvcvideo: Found UVC 1.00 device CNF7045 (04f2:b062)
[   19.972864] input: CNF7045 as /devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input5
[   19.973049] usbcore: registered new interface driver uvcvideo
[   19.973053] USB Video Class driver (1.1.1)
[   20.082296] snd_hda_intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.082381] snd_hda_intel 0000:00:0f.0: setting latency timer to 64
[   20.133887] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input6
[   20.134129] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input7
[   20.187619] input: MLK OM1007 Wireless Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input8
[   20.187884] generic-usb 0003:04FC:0538.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK OM1007 Wireless Mouse] on usb-0000:00:03.0-2/input0
[   20.187911] usbcore: registered new interface driver usbhid
[   20.187914] usbhid: USB HID core driver
[   20.203258] cfg80211: World regulatory domain updated:
[   20.203263] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.203267] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.203271] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.203274] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.203277] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.203280] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328783] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.328788] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328791] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.328795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328797] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.328801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328804] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.328807] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328810] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.328813] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328816] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.328819] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328822] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.328825] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328828] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.328849] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328852] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.328856] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328858] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.328862] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328864] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.328868] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.328870] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.328874] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.328877] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.328880] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.328883] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.328886] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.333378] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.334472] ieee80211 phy0: hwaddr 00:17:c4:1c:54:1d, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   20.355949] rtl8187: Customer ID is 0x00
[   20.356044] Registered led device: rtl8187-phy0::radio
[   20.356074] Registered led device: rtl8187-phy0::tx
[   20.356101] Registered led device: rtl8187-phy0::rx
[   20.357939] rtl8187: wireless switch is on
[   20.357996] usbcore: registered new interface driver rtl8187
[   20.416550] init: failsafe main process (765) killed by TERM signal
[   20.516348] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   20.543314] type=1400 audit(1349377372.909:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=849 comm="apparmor_parser"
[   20.558912] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.569678] type=1400 audit(1349377372.937:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=850 comm="apparmor_parser"
[   20.572326] type=1400 audit(1349377372.941:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=850 comm="apparmor_parser"
[   20.572635] type=1400 audit(1349377372.941:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=850 comm="apparmor_parser"
[   20.595206] Bluetooth: Core ver 2.16
[   20.595434] NET: Registered protocol family 31
[   20.595438] Bluetooth: HCI device and connection manager initialized
[   20.595442] Bluetooth: HCI socket layer initialized
[   20.595444] Bluetooth: L2CAP socket layer initialized
[   20.595452] Bluetooth: SCO socket layer initialized
[   20.599366] ppdev: user-space parallel port driver
[   20.610062] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.610067] Bluetooth: BNEP filters: protocol multicast
[   20.627118] type=1400 audit(1349377372.993:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=882 comm="apparmor_parser"
[   20.628906] type=1400 audit(1349377372.997:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=882 comm="apparmor_parser"
[   20.635282] type=1400 audit(1349377373.001:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=883 comm="apparmor_parser"
[   20.717896] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.717899] vesafb: scrolling: redraw
[   20.717903] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.721425] vesafb: framebuffer at 0xc0000000, mapped to 0xf8980000, using 1216k, total 1216k
[   20.721893] fbcon: VESA VGA (fb0) is primary device
[   20.721983] Console: switching to colour frame buffer device 80x30
[   20.722001] fb0: VESA VGA frame buffer device
[   20.725101] Bluetooth: RFCOMM TTY layer initialized
[   20.725110] Bluetooth: RFCOMM socket layer initialized
[   20.725113] Bluetooth: RFCOMM ver 1.11
[   21.130402] init: kdm main process (969) killed by TERM signal
[   24.662577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.662978] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.666817] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.667345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.708104] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[   29.966922] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[   29.971514] wlan0: authenticated
[   29.972756] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[   29.981684] wlan0: RX AssocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[   29.981691] wlan0: associated
[   29.987511] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.989384] cfg80211: Calling CRDA for country: NL
[   29.996650] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.996656] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996659] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.996663] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996666] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.996669] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996672] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.996675] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996678] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.996682] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996685] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.996688] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996691] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.996694] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996697] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.996700] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996703] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.996706] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996709] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.996713] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996715] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.996719] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996721] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.996725] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996728] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.996731] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   29.996734] cfg80211: Disabling freq 2484 MHz
[   29.996737] cfg80211: Regulatory domain changed to country: NL
[   29.996739] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.996743] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.996746] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.996749] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.996751] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   34.712021] sis190 0000:00:04.0: eth0: auto-negotiating...
[   37.176841] init: plymouth-stop pre-start process (1475) terminated with status 1
[   41.104039] wlan0: no IPv6 routers present
[   52.772567] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   52.774057] sd 4:0:0:0: [sdb] Asking for cache data failed
[   52.774062] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   52.908053] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  104.472647] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  104.474138] sd 4:0:0:0: [sdb] Asking for cache data failed
[  104.474145] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  127.396044] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[  127.496187] cfg80211: All devices are disconnected, going to restore regulatory settings
[  127.496198] cfg80211: Restoring regulatory settings
[  127.496217] cfg80211: Calling CRDA to update world regulatory domain
[  127.505359] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  127.505368] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505374] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  127.505381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505386] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  127.505393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505398] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  127.505405] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505410] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  127.505416] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505421] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  127.505427] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505432] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  127.505438] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505443] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  127.505449] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505454] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  127.505461] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505466] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  127.505472] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505477] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  127.505483] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505488] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  127.505494] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505499] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  127.505506] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505511] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  127.505517] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505523] cfg80211: World regulatory domain updated:
[  127.505527] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  127.505533] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505539] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505545] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  127.505551] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  127.505556] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  129.861250] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[  129.865492] wlan0: authenticated
[  130.001307] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[  130.010825] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[  130.010832] wlan0: associated
[  130.016941] cfg80211: Calling CRDA for country: NL
[  130.025642] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  130.025652] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025657] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  130.025664] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025669] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  130.025676] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025681] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  130.025687] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025692] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  130.025699] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025704] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  130.025710] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025715] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  130.025721] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025726] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  130.025732] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025737] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  130.025743] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025748] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  130.025754] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025759] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  130.025765] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025770] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  130.025776] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025781] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  130.025787] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  130.025791] cfg80211: Disabling freq 2484 MHz
[  130.025797] cfg80211: Regulatory domain changed to country: NL
[  130.025801] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  130.025807] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  130.025812] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  130.025818] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  130.025823] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  156.184583] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.186075] sd 4:0:0:0: [sdb] Asking for cache data failed
[  156.186081] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  169.044082] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7da0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7da0000 - 00000000b7da1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7da1000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: PACKARD BELL BV EasyNote MH35/PE1, BIOS PE14A04  02/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f86c0] f86c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000f8690 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT b7d97999 00094 (v01 PacBel PBNB000B 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b7d9fcc4 000F4 (v03 SiS    671MX    06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT b7d9b9c6 0428A (v01 PTLTD       671 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS b7da0fc0 00040
[    0.000000] ACPI: SLIC b7d9fdb8 00176 (v00 PacBel PBNB000B 06040000      00000000)
[    0.000000] ACPI: APIC b7d9ff2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG b7d9ff8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET b7d9ffc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SSDT b7d992d1 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d9922b 000A6 (v01  PmRef  Cpu7Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99185 000A6 (v01  PmRef  Cpu6Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d990df 000A6 (v01  PmRef  Cpu5Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99039 000A6 (v01  PmRef  Cpu4Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98f93 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98eed 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98e47 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d97a2d 0141A (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4de8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4100 pages used for memmap
[    0.000000]   HighMem zone: 520590 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=9b3867fe-5b6d-419c-98c6-e571f5a57d0a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d90)
[    0.000000] Memory: 2951184k/3012160k available (5818k kernel code, 60516k reserved, 2846k data, 740k init, 2098760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1831.914 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3663.82 BogoMIPS (lpj=7327656)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004059] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004100] Yama: becoming mindful.
[    0.004218] Mount-cache hash table entries: 512
[    0.004505] Initializing cgroup subsys cpuacct
[    0.004519] Initializing cgroup subsys memory
[    0.004535] Initializing cgroup subsys devices
[    0.004540] Initializing cgroup subsys freezer
[    0.004545] Initializing cgroup subsys blkio
[    0.004559] Initializing cgroup subsys perf_event
[    0.004615] CPU: Physical Processor ID: 0
[    0.004620] CPU: Processor Core ID: 0
[    0.004627] mce: CPU supports 6 MCE banks
[    0.004644] CPU0: Thermal monitoring enabled (TM2)
[    0.004651] using mwait in idle threads.
[    0.011496] ACPI: Core revision 20110623
[    0.024050] ftrace: allocating 26555 entries in 52 pages
[    0.028097] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070391] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.072003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.072003] PEBS disabled due to CPU errata.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f74cc000 soft=f74ce000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.008000] calibrate_delay_direct() ignoring timer_rate as we had a TSC wrap around start=4285634451 >=post_end=5322246
[    0.160059] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160132] Brought up 2 CPUs
[    0.160138] Total of 2 processors activated (7327.63 BogoMIPS).
[    0.162825] devtmpfs: initialized
[    0.162825] EVM: security.selinux
[    0.162825] EVM: security.SMACK64
[    0.162825] EVM: security.capability
[    0.162825] PM: Registering ACPI NVS region at b7da0000 (4096 bytes)
[    0.165914] print_constraints: dummy: 
[    0.165959] RTC time: 12:24:18, date: 10/05/12
[    0.166044] NET: Registered protocol family 16
[    0.166193] Trying to unpack rootfs image as initramfs...
[    0.166336] EISA bus registered
[    0.166370] ACPI: bus type pci registered
[    0.166517] PCI: MMCONFIG for domain 0000 [bus 00-02] at [mem 0xe0000000-0xe02fffff] (base 0xe0000000)
[    0.166524] PCI: MMCONFIG at [mem 0xe0000000-0xe02fffff] reserved in E820
[    0.166529] PCI: Using MMCONFIG for extended config space
[    0.166533] PCI: Using configuration type 1 for base access
[    0.180146] bio: create slab <bio-0> at 0
[    0.180341] ACPI: Added _OSI(Module Device)
[    0.180347] ACPI: Added _OSI(Processor Device)
[    0.180352] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180357] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182455] ACPI: EC: Look up EC in DSDT
[    0.189431] ACPI: SSDT b7d99deb 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.189986] ACPI: Dynamic OEM Table Load:
[    0.189994] ACPI: SSDT   (null) 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.192046] ACPI: SSDT b7d99530 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.192676] ACPI: Dynamic OEM Table Load:
[    0.192684] ACPI: SSDT   (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.236975] ACPI: SSDT b7d9a00a 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.237547] ACPI: Dynamic OEM Table Load:
[    0.237555] ACPI: SSDT   (null) 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.238086] ACPI: SSDT b7d99a48 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.238610] ACPI: Dynamic OEM Table Load:
[    0.238618] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.268558] ACPI: Interpreter enabled
[    0.268588] ACPI: (supports S0 S1 S3 S4 S5)
[    0.268636] ACPI: Using IOAPIC for interrupt routing
[    0.272778] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.275951] ACPI: Power Resource [QFAN] (off)
[    0.276401] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.276682] ACPI: No dock devices found.
[    0.276688] HEST: Table not found.
[    0.276701] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277471] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.278879] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.278886] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.278892] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.278899] pci_root PNP0A03:00: host bridge window [mem 0xb8000000-0xffedffff]
[    0.278905] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.278911] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.278917] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.278922] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.278927] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.278965] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.278987] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.279093] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.279160] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.279300] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.279331] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.279348] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.279365] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.279382] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.279399] pci 0000:00:02.5: reg 20: [io  0x1080-0x108f]
[    0.279469] pci 0000:00:02.5: PME# supported from D3cold
[    0.279478] pci 0000:00:02.5: PME# disabled
[    0.279506] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.279528] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.279630] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.279653] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.279761] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.279788] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.279902] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.279910] pci 0000:00:03.3: PME# disabled
[    0.279945] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.279972] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.279989] pci 0000:00:04.0: reg 14: [io  0x1000-0x107f]
[    0.280114] pci 0000:00:04.0: supports D1 D2
[    0.280119] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280127] pci 0000:00:04.0: PME# disabled
[    0.280155] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.280183] pci 0000:00:05.0: reg 10: [io  0x10c8-0x10cf]
[    0.280200] pci 0000:00:05.0: reg 14: [io  0x10bc-0x10bf]
[    0.280217] pci 0000:00:05.0: reg 18: [io  0x10c0-0x10c7]
[    0.280233] pci 0000:00:05.0: reg 1c: [io  0x10b8-0x10bb]
[    0.280250] pci 0000:00:05.0: reg 20: [io  0x10a0-0x10af]
[    0.280318] pci 0000:00:05.0: PME# supported from D3cold
[    0.280326] pci 0000:00:05.0: PME# disabled
[    0.280363] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.280498] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.280506] pci 0000:00:06.0: PME# disabled
[    0.280554] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.280687] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.280695] pci 0000:00:07.0: PME# disabled
[    0.280752] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.280781] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.280899] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.280907] pci 0000:00:0f.0: PME# disabled
[    0.280986] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.281015] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.281030] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.281045] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.281131] pci 0000:01:00.0: supports D1 D2
[    0.281195] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.281203] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.281212] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.281221] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.281305] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.281317] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.281326] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.281416] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.281461] pci_bus 0000:00: on NUMA node 0
[    0.281468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.282015]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.282023]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.282027] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.291767] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.291880] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.291988] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[    0.292113] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 9 10 11)
[    0.292252] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.292360] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.292465] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.292571] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.292891] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.292898] vgaarb: loaded
[    0.292902] vgaarb: bridge control possible 0000:01:00.0
[    0.293185] i2c-core: driver [aat2870] using legacy suspend method
[    0.293189] i2c-core: driver [aat2870] using legacy resume method
[    0.293374] SCSI subsystem initialized
[    0.293505] libata version 3.00 loaded.
[    0.293613] usbcore: registered new interface driver usbfs
[    0.293641] usbcore: registered new interface driver hub
[    0.293707] usbcore: registered new device driver usb
[    0.293919] PCI: Using ACPI for IRQ routing
[    0.293977] PCI: pci_cache_line_size set to 64 bytes
[    0.294088] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.294094] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.294337] NetLabel: Initializing
[    0.294341] NetLabel:  domain hash size = 128
[    0.294345] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.294368] NetLabel:  unlabeled traffic allowed by default
[    0.294480] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.294489] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.294500] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.300101] Switching to clocksource hpet
[    0.320328] AppArmor: AppArmor Filesystem Enabled
[    0.320395] pnp: PnP ACPI init
[    0.320437] ACPI: bus type pnp registered
[    0.321260] pnp 00:00: [bus 00-ff]
[    0.321267] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.321273] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.321279] pnp 00:00: [io  0x0d00-0xffff window]
[    0.321285] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.321290] pnp 00:00: [mem 0xb8000000-0xffedffff window]
[    0.321296] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.321301] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.321306] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.321312] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.321317] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.321323] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.321328] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.321333] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.321338] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.321344] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.321349] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.321355] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.321479] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.321833] pnp 00:01: [io  0x0000-0x000f]
[    0.321839] pnp 00:01: [io  0x0081-0x008f]
[    0.321843] pnp 00:01: [io  0x00c0-0x00df]
[    0.321848] pnp 00:01: [io  0x0480-0x048f]
[    0.321854] pnp 00:01: [dma 4]
[    0.321946] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.322008] pnp 00:02: [io  0x0070-0x0071]
[    0.322097] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.322119] pnp 00:03: [io  0x0061]
[    0.322203] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.322296] pnp 00:04: [io  0x8000-0x80be]
[    0.322301] pnp 00:04: [io  0x8100-0x812f]
[    0.322306] pnp 00:04: [io  0x0080]
[    0.322311] pnp 00:04: [io  0x04d0-0x04d1]
[    0.322316] pnp 00:04: [io  0xfe00]
[    0.322320] pnp 00:04: [io  0x002e]
[    0.322324] pnp 00:04: [io  0x002f]
[    0.322328] pnp 00:04: [io  0x0092]
[    0.322333] pnp 00:04: [io  0x0072-0x0073]
[    0.322338] pnp 00:04: [io  0x0078-0x0079]
[    0.322342] pnp 00:04: [io  0x0290-0x0297]
[    0.322347] pnp 00:04: [mem 0xe0000000-0xefffffff]
[    0.322353] pnp 00:04: [mem 0xfec00000-0xfeefffff]
[    0.322358] pnp 00:04: [mem 0xffb80000-0xffbfffff]
[    0.322363] pnp 00:04: [mem 0xffc00000-0xffc00fff]
[    0.322368] pnp 00:04: [mem 0xffe00000-0xffe00fff]
[    0.322372] pnp 00:04: [mem 0xffe80000-0xffefffff]
[    0.322528] system 00:04: [io  0x8000-0x80be] has been reserved
[    0.322535] system 00:04: [io  0x8100-0x812f] has been reserved
[    0.322542] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.322554] system 00:04: [io  0xfe00] has been reserved
[    0.322560] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.322568] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.322576] system 00:04: [mem 0xfec00000-0xfeefffff] could not be reserved
[    0.322582] system 00:04: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.322589] system 00:04: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.322596] system 00:04: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.322602] system 00:04: [mem 0xffe80000-0xffefffff] could not be reserved
[    0.322611] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322660] pnp 00:05: [io  0x00f0-0x00ff]
[    0.322684] pnp 00:05: [irq 13]
[    0.322772] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322795] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    0.322801] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    0.322806] pnp 00:06: [mem 0xffc00000-0xffc00fff]
[    0.322810] pnp 00:06: [mem 0xffe00000-0xffe00fff]
[    0.322898] pnp 00:06: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.323049] pnp 00:07: [irq 0 disabled]
[    0.323060] pnp 00:07: [irq 8]
[    0.323071] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.323171] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.323197] pnp 00:08: [io  0x0060]
[    0.323202] pnp 00:08: [io  0x0064]
[    0.323212] pnp 00:08: [irq 1]
[    0.323302] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323329] pnp 00:09: [irq 12]
[    0.323426] pnp 00:09: Plug and Play ACPI device, IDs SYN101f PNP0f13 (active)
[    0.323751] pnp: PnP ACPI: found 10 devices
[    0.323756] ACPI: ACPI bus type pnp unregistered
[    0.323765] PnPBIOS: Disabled by ACPI PNP
[    0.362706] PCI: max bus depth: 1 pci_try_num: 2
[    0.362772] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362781] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.362788] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.362798] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.362807] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.362819] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.362826] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.362836] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.362845] pci 0000:00:06.0:   bridge window [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.362858] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.362894] pci 0000:00:01.0: setting latency timer to 64
[    0.362934] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362943] pci 0000:00:06.0: setting latency timer to 64
[    0.362955] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362964] pci 0000:00:07.0: setting latency timer to 64
[    0.362972] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.362978] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.362984] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.362989] pci_bus 0000:00: resource 7 [mem 0xb8000000-0xffedffff]
[    0.362995] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.363000] pci_bus 0000:00: resource 9 [mem 0x000d4000-0x000d7fff]
[    0.363006] pci_bus 0000:00: resource 10 [mem 0x000d8000-0x000dbfff]
[    0.363011] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000dffff]
[    0.363017] pci_bus 0000:00: resource 12 [mem 0x000e0000-0x000e3fff]
[    0.363022] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.363028] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.363033] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.363039] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.363044] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.363050] pci_bus 0000:04: resource 2 [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.363150] NET: Registered protocol family 2
[    0.363320] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.363844] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.364815] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.365277] TCP: Hash tables configured (established 131072 bind 65536)
[    0.365282] TCP reno registered
[    0.365290] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.365308] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.365491] NET: Registered protocol family 1
[    0.365597] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.420063] pci 0000:00:03.0: PCI INT A disabled
[    0.420117] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.476062] pci 0000:00:03.1: PCI INT B disabled
[    0.476108] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.476139] pci 0000:00:03.3: PCI INT C disabled
[    0.476173] pci 0000:01:00.0: Boot video device
[    0.476180] PCI: CLS 16 bytes, default 64
[    0.476945] audit: initializing netlink socket (disabled)
[    0.476969] type=2000 audit(1349439857.472:1): initialized
[    0.525827] highmem bounce pool size: 64 pages
[    0.525840] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.530860] VFS: Disk quotas dquot_6.5.2
[    0.531007] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.532327] fuse init (API version 7.17)
[    0.532549] msgmni has been set to 1664
[    0.533264] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.533326] io scheduler noop registered
[    0.533330] io scheduler deadline registered
[    0.533346] io scheduler cfq registered (default)
[    0.533782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533842] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.534033] intel_idle: MWAIT substates: 0x22220
[    0.534038] intel_idle: does not run on family 6 model 15
[    0.534180] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.534295] ACPI: AC Adapter [ACAD] (off-line)
[    0.534455] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.534836] ACPI: Lid Switch [LID0]
[    0.534944] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.534954] ACPI: Power Button [PWRB]
[    0.535051] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.535059] ACPI: Power Button [PWRF]
[    0.535196] ACPI: Fan [FAN] (off)
[    0.542989] Monitor-Mwait will be used to enter C-1 state
[    0.543718] Monitor-Mwait will be used to enter C-2 state
[    0.544638] Monitor-Mwait will be used to enter C-3 state
[    0.544657] Marking TSC unstable due to TSC halts in idle
[    0.544675] ACPI: acpi_idle registered with cpuidle
[    0.563012] thermal LNXTHERM:00: registered as thermal_zone0
[    0.563019] ACPI: Thermal Zone [THRM] (28 C)
[    0.563088] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.563115] ACPI: Battery Slot [BAT1] (battery absent)
[    0.563226] ERST: Table is not found!
[    0.563230] GHES: HEST is not enabled!
[    0.563421] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.563682] ACPI: Battery Slot [BAT1] (battery absent)
[    0.563716] isapnp: Scanning for PnP cards...
[    0.835072] Freeing initrd memory: 13840k freed
[    0.917995] isapnp: No Plug & Play device found
[    0.964883] Linux agpgart interface v0.103
[    0.968586] brd: module loaded
[    0.970416] loop: module loaded
[    0.970844] pata_sis 0000:00:02.5: version 0.5.2
[    0.970875] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.971685] scsi0 : pata_sis
[    0.971873] scsi1 : pata_sis
[    0.972496] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    0.972503] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    0.972606] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.972679] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.973505] Fixed MDIO Bus: probed
[    0.973559] tun: Universal TUN/TAP device driver, 1.6
[    0.973565] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.973680] PPP generic driver version 2.4.2
[    0.973918] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.973952] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.973979] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.974089] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.974141] ehci_hcd 0000:00:03.3: cache line size of 16 is not supported
[    0.974173] ehci_hcd 0000:00:03.3: irq 22, io mem 0xd4106000
[    0.984028] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.984334] hub 1-0:1.0: USB hub found
[    0.984344] hub 1-0:1.0: 8 ports detected
[    0.984516] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.984544] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.984567] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.984661] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.984698] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd4104000
[    1.046258] hub 2-0:1.0: USB hub found
[    1.046269] hub 2-0:1.0: 4 ports detected
[    1.046404] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.046425] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.046528] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.046565] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4105000
[    1.102270] hub 3-0:1.0: USB hub found
[    1.102280] hub 3-0:1.0: 4 ports detected
[    1.102426] uhci_hcd: USB Universal Host Controller Interface driver
[    1.102555] usbcore: registered new interface driver libusual
[    1.102661] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.106231] i8042: Detected active multiplexing controller, rev 1.1
[    1.108075] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.108090] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.108163] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.108232] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.108293] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.108578] mousedev: PS/2 mouse device common for all mice
[    1.108969] rtc_cmos 00:02: RTC can wake from S4
[    1.109158] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.109190] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.109321] device-mapper: uevent: version 1.0.3
[    1.109482] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.109555] EISA: Probing bus 0 at eisa.0
[    1.109561] EISA: Cannot allocate resource for mainboard
[    1.109566] Cannot allocate resource for EISA slot 1
[    1.109570] Cannot allocate resource for EISA slot 2
[    1.109575] Cannot allocate resource for EISA slot 3
[    1.109579] Cannot allocate resource for EISA slot 4
[    1.109583] Cannot allocate resource for EISA slot 5
[    1.109587] Cannot allocate resource for EISA slot 6
[    1.109591] Cannot allocate resource for EISA slot 7
[    1.109595] Cannot allocate resource for EISA slot 8
[    1.109599] EISA: Detected 0 cards.
[    1.109617] cpufreq-nforce2: No nForce2 chipset.
[    1.109765] cpuidle: using governor ladder
[    1.110002] cpuidle: using governor menu
[    1.110007] EFI Variables Facility v0.08 2004-May-17
[    1.110629] TCP cubic registered
[    1.110911] NET: Registered protocol family 10
[    1.112310] NET: Registered protocol family 17
[    1.112320] Registering the dns_resolver key type
[    1.112363] Using IPI No-Shortcut mode
[    1.112632] PM: Hibernation image not present or could not be loaded.
[    1.112660] registered taskstats version 1
[    1.127592]   Magic number: 0:47:430
[    1.127741] rtc_cmos 00:02: setting system clock to 2012-10-05 12:24:19 UTC (1349439859)
[    1.128466] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.128469] EDD information not available.
[    1.136288] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    1.144278] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.152277] ata1.00: configured for UDMA/33
[    1.163911] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    1.166159] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.166163] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.166331] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.166468] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.166577] ata2: port disabled--ignoring
[    1.166723] Freeing unused kernel memory: 740k freed
[    1.167178] Write protecting the kernel text: 5820k
[    1.167208] Write protecting the kernel read-only data: 2376k
[    1.167210] NX-protecting the kernel data: 4420k
[    1.189602] udevd[96]: starting version 175
[    1.273478] sata_sis 0000:00:05.0: version 1.0
[    1.273507] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.273514] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.277333] scsi2 : sata_sis
[    1.280691] scsi3 : sata_sis
[    1.281306] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
[    1.281310] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17
[    1.284286] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.284336] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.284354] sis190 0000:00:04.0: setting latency timer to 64
[    1.284379] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.352039] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.372030] sis190: 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1
[    1.444254] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.444258] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.460247] ata3.00: configured for UDMA/133
[    1.460447] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.460692] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.460696] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.460765] sd 2:0:0:0: [sda] Write Protect is off
[    1.460769] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.460797] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.502750] usbcore: registered new interface driver uas
[    1.503009] Initializing USB Mass Storage driver...
[    1.503057] usbcore: registered new interface driver usb-storage
[    1.503059] USB Mass Storage support registered.
[    1.526730]  sda: sda1 sda2 < sda5 >
[    1.527244] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.612026] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.631264] scsi4 : usb-storage 1-4:1.0
[    1.631386] usbcore: registered new interface driver ums-realtek
[    1.864031] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[    1.888030] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.920719] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8412000 (IRQ: 19), 00:1e:68:24:0c:41
[    1.920724] sis190 0000:00:04.0: eth0: GMII mode.
[    1.920733] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
[    2.107420] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.324051] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    2.640660] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.641500] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.644025] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   19.543368] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.570556] udevd[307]: starting version 175
[   19.656983] Adding 3010556k swap on /dev/sda5.  Priority:-1 extents:1 across:3010556k 
[   19.683938] lp: driver loaded but no devices found
[   19.686711] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   19.688644] type=1400 audit(1349432678.056:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=359 comm="apparmor_parser"
[   19.689180] type=1400 audit(1349432678.056:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=359 comm="apparmor_parser"
[   19.689477] type=1400 audit(1349432678.056:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=359 comm="apparmor_parser"
[   19.698481] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   19.699511] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.822716] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.831664] Linux video capture interface: v2.00
[   19.837042] uvcvideo: Found UVC 1.00 device CNF7045 (04f2:b062)
[   19.844141] acpi device:0e: registered as cooling_device3
[   19.844889] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input4
[   19.845098] input: CNF7045 as /devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input5
[   19.845186] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.845572] usbcore: registered new interface driver uvcvideo
[   19.845576] USB Video Class driver (1.1.1)
[   19.904694] cfg80211: Calling CRDA to update world regulatory domain
[   19.918849] input: MLK OM1007 Wireless Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input6
[   19.919113] generic-usb 0003:04FC:0538.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK OM1007 Wireless Mouse] on usb-0000:00:03.0-2/input0
[   19.919142] usbcore: registered new interface driver usbhid
[   19.919145] usbhid: USB HID core driver
[   19.969396] snd_hda_intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.969484] snd_hda_intel 0000:00:0f.0: setting latency timer to 64
[   20.019329] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input7
[   20.019574] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input8
[   20.098666] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.244074] cfg80211: World regulatory domain updated:
[   20.244081] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.244085] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.244088] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.244092] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.244095] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.244098] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349542] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.349548] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349551] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.349555] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349558] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.349561] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349564] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.349567] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349570] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.349573] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349576] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.349580] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349582] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.349586] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349589] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.349592] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349595] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.349598] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349601] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.349605] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349607] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.349611] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.349614] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.349617] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.349620] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.349623] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.349626] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.349630] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.353174] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.354012] ieee80211 phy0: hwaddr 00:17:c4:1c:54:1d, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   20.378967] rtl8187: Customer ID is 0x00
[   20.379045] Registered led device: rtl8187-phy0::radio
[   20.379075] Registered led device: rtl8187-phy0::tx
[   20.379103] Registered led device: rtl8187-phy0::rx
[   20.380374] rtl8187: wireless switch is on
[   20.380458] usbcore: registered new interface driver rtl8187
[   20.488706] init: failsafe main process (730) killed by TERM signal
[   20.590307] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.590311] vesafb: scrolling: redraw
[   20.590314] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.591694] vesafb: framebuffer at 0xc0000000, mapped to 0xf8800000, using 1216k, total 1216k
[   20.591887] Console: switching to colour frame buffer device 80x30
[   20.591905] fb0: VESA VGA frame buffer device
[   20.626057] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   20.633507] ppdev: user-space parallel port driver
[   20.670748] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.720449] Bluetooth: Core ver 2.16
[   20.720481] NET: Registered protocol family 31
[   20.720484] Bluetooth: HCI device and connection manager initialized
[   20.720488] Bluetooth: HCI socket layer initialized
[   20.720491] Bluetooth: L2CAP socket layer initialized
[   20.725183] Bluetooth: SCO socket layer initialized
[   20.730346] type=1400 audit(1349432679.096:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=808 comm="apparmor_parser"
[   20.731001] type=1400 audit(1349432679.096:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=808 comm="apparmor_parser"
[   20.756064] Bluetooth: RFCOMM TTY layer initialized
[   20.756073] Bluetooth: RFCOMM socket layer initialized
[   20.756076] Bluetooth: RFCOMM ver 1.11
[   20.772095] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.772099] Bluetooth: BNEP filters: protocol multicast
[   20.877909] type=1400 audit(1349432679.244:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   20.881033] type=1400 audit(1349432679.248:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=848 comm="apparmor_parser"
[   20.883185] type=1400 audit(1349432679.248:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   20.883491] type=1400 audit(1349432679.248:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   20.897511] type=1400 audit(1349432679.264:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=852 comm="apparmor_parser"
[   21.368701] init: kdm main process (918) killed by TERM signal
[   24.743118] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.743575] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.747666] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.748176] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.756144] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[   30.037414] wlan0: direct probe to 40:4a:03:fb:6d:6c (try 1/3)
[   30.041899] wlan0: direct probe responded
[   30.056107] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[   30.057913] wlan0: authenticated
[   30.059039] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[   30.069660] wlan0: RX AssocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[   30.069670] wlan0: associated
[   30.075706] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.077391] cfg80211: Calling CRDA for country: NL
[   30.085562] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   30.085568] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085572] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   30.085575] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085578] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   30.085581] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085584] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   30.085588] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085590] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   30.085594] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085597] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   30.085600] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085603] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   30.085606] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085609] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   30.085612] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085615] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   30.085618] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085621] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   30.085624] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085627] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   30.085631] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085633] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   30.085637] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085639] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   30.085643] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.085645] cfg80211: Disabling freq 2484 MHz
[   30.085649] cfg80211: Regulatory domain changed to country: NL
[   30.085651] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.085654] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.085657] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.085660] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.085663] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   34.776022] sis190 0000:00:04.0: eth0: auto-negotiating...
[   37.420544] init: plymouth-stop pre-start process (1416) terminated with status 1
[   40.872072] wlan0: no IPv6 routers present
[   53.780600] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   53.782093] sd 4:0:0:0: [sdb] Asking for cache data failed
[   53.782098] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  103.508068] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  106.008562] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  106.010054] sd 4:0:0:0: [sdb] Asking for cache data failed
[  106.010062] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  120.916076] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  122.404045] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[  122.492165] cfg80211: All devices are disconnected, going to restore regulatory settings
[  122.492175] cfg80211: Restoring regulatory settings
[  122.492192] cfg80211: Calling CRDA to update world regulatory domain
[  122.501422] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  122.501431] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501437] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  122.501444] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501450] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  122.501456] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501461] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  122.501468] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501473] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  122.501479] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501484] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  122.501490] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501495] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  122.501501] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501506] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  122.501512] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501517] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  122.501524] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501529] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  122.501535] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501540] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  122.501546] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501551] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  122.501557] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501562] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  122.501569] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501574] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  122.501580] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501586] cfg80211: World regulatory domain updated:
[  122.501590] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  122.501596] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501602] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501608] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  122.501614] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  122.501619] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  124.853357] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[  124.855466] wlan0: authenticated
[  124.993286] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[  125.003528] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[  125.003535] wlan0: associated
[  125.009549] cfg80211: Calling CRDA for country: NL
[  125.018238] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  125.018266] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018272] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  125.018278] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018284] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  125.018290] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018296] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  125.018307] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018312] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  125.018318] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018323] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  125.018330] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018335] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  125.018341] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018346] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  125.018352] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018357] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  125.018364] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018369] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  125.018375] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018380] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  125.018394] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018400] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  125.018406] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018411] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  125.018417] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  125.018422] cfg80211: Disabling freq 2484 MHz
[  125.018428] cfg80211: Regulatory domain changed to country: NL
[  125.018432] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  125.018438] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.018443] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.018449] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  125.018454] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  156.196588] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  156.198079] sd 4:0:0:0: [sdb] Asking for cache data failed
[  156.198086] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  207.896514] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  207.898005] sd 4:0:0:0: [sdb] Asking for cache data failed
[  207.898010] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  208.020080] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  259.608591] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  259.610082] sd 4:0:0:0: [sdb] Asking for cache data failed
[  259.610089] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  259.780072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  311.320654] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  311.322145] sd 4:0:0:0: [sdb] Asking for cache data failed
[  311.322152] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  311.480071] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  363.032589] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  363.034081] sd 4:0:0:0: [sdb] Asking for cache data failed
[  363.034089] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  363.208078] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  414.742642] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  414.744242] sd 4:0:0:0: [sdb] Asking for cache data failed
[  414.744248] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  414.884041] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  432.548046] ieee80211 phy0: wlan0: No probe response from AP 40:4a:03:fb:6d:6c after 500ms, disconnecting.
[  432.640183] cfg80211: All devices are disconnected, going to restore regulatory settings
[  432.640192] cfg80211: Restoring regulatory settings
[  432.640200] cfg80211: Calling CRDA to update world regulatory domain
[  432.649270] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  432.649280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649286] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  432.649292] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649298] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  432.649304] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649309] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  432.649315] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649320] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  432.649326] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649331] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  432.649337] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649342] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  432.649349] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649354] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  432.649360] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649365] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  432.649371] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649376] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  432.649382] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649387] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  432.649394] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649399] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  432.649405] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649410] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  432.649416] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649422] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  432.649428] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649434] cfg80211: World regulatory domain updated:
[  432.649438] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  432.649444] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649450] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649456] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  432.649462] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.649468] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  435.001282] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[  435.007021] wlan0: authenticated
[  435.141338] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[  435.150474] wlan0: RX ReassocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[  435.150480] wlan0: associated
[  435.156484] cfg80211: Calling CRDA for country: NL
[  435.164911] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  435.164920] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164926] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  435.164932] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164938] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  435.164944] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164949] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  435.164955] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164961] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  435.164967] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164972] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  435.164978] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164983] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  435.164989] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.164994] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  435.165000] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165005] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  435.165011] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165016] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  435.165022] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165027] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  435.165033] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165038] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  435.165044] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165049] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  435.165056] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  435.165060] cfg80211: Disabling freq 2484 MHz
[  435.165067] cfg80211: Regulatory domain changed to country: NL
[  435.165071] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  435.165076] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  435.165082] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  435.165087] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  435.165092] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  466.452575] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  466.454066] sd 4:0:0:0: [sdb] Asking for cache data failed
[  466.454070] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  466.572065] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  514.687472] show_signal_msg: 42 callbacks suppressed
[  514.687478] nepomukservices[1731]: segfault at 0 ip   (null) sp bfb7391c error 14 in nepomukservicestub[8048000+6000]
[  517.669607] mtrr: no MTRR for c0000000,8000000 found
[  518.164379] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  518.165874] sd 4:0:0:0: [sdb] Asking for cache data failed
[  518.165879] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  569.880586] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  569.882076] sd 4:0:0:0: [sdb] Asking for cache data failed
[  569.882083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  621.588636] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  621.590133] sd 4:0:0:0: [sdb] Asking for cache data failed
[  621.590139] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  673.304584] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  673.306076] sd 4:0:0:0: [sdb] Asking for cache data failed
[  673.306083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  673.456083] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  725.016646] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  725.018138] sd 4:0:0:0: [sdb] Asking for cache data failed
[  725.018144] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  725.148094] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  776.728582] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  776.730074] sd 4:0:0:0: [sdb] Asking for cache data failed
[  776.730081] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  808.020162] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  826.916790] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  826.918252] sd 4:0:0:0: [sdb] Asking for cache data failed
[  826.918263] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  827.044089] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  827.348080] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  877.092638] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  877.094128] sd 4:0:0:0: [sdb] Asking for cache data failed
[  877.094135] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  877.252074] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  928.792579] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  928.794071] sd 4:0:0:0: [sdb] Asking for cache data failed
[  928.794078] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  928.948072] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[  980.504640] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  980.506132] sd 4:0:0:0: [sdb] Asking for cache data failed
[  980.506139] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  980.636079] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7da0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7da0000 - 00000000b7da1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7da1000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: PACKARD BELL BV EasyNote MH35/PE1, BIOS PE14A04  02/22/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f86c0] f86c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 000f8690 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT b7d97999 00094 (v01 PacBel PBNB000B 06040000  LTP 00000000)
[    0.000000] ACPI: FACP b7d9fcc4 000F4 (v03 SiS    671MX    06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT b7d9b9c6 0428A (v01 PTLTD       671 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS b7da0fc0 00040
[    0.000000] ACPI: SLIC b7d9fdb8 00176 (v00 PacBel PBNB000B 06040000      00000000)
[    0.000000] ACPI: APIC b7d9ff2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG b7d9ff8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET b7d9ffc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: SSDT b7d992d1 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d9922b 000A6 (v01  PmRef  Cpu7Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99185 000A6 (v01  PmRef  Cpu6Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d990df 000A6 (v01  PmRef  Cpu5Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d99039 000A6 (v01  PmRef  Cpu4Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98f93 000A6 (v01  PmRef  Cpu3Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98eed 000A6 (v01  PmRef  Cpu2Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d98e47 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT b7d97a2d 0141A (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f4de8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4100 pages used for memmap
[    0.000000]   HighMem zone: 520590 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=9b3867fe-5b6d-419c-98c6-e571f5a57d0a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d90)
[    0.000000] Memory: 2951184k/3012160k available (5818k kernel code, 60516k reserved, 2846k data, 740k init, 2098760k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
[    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1831.868 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3663.73 BogoMIPS (lpj=7327472)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004060] Security Framework initialized
[    0.004097] AppArmor: AppArmor initialized
[    0.004101] Yama: becoming mindful.
[    0.004221] Mount-cache hash table entries: 512
[    0.004508] Initializing cgroup subsys cpuacct
[    0.004521] Initializing cgroup subsys memory
[    0.004538] Initializing cgroup subsys devices
[    0.004543] Initializing cgroup subsys freezer
[    0.004547] Initializing cgroup subsys blkio
[    0.004562] Initializing cgroup subsys perf_event
[    0.004618] CPU: Physical Processor ID: 0
[    0.004622] CPU: Processor Core ID: 0
[    0.004629] mce: CPU supports 6 MCE banks
[    0.004646] CPU0: Thermal monitoring enabled (TM2)
[    0.004654] using mwait in idle threads.
[    0.010857] ACPI: Core revision 20110623
[    0.020051] ftrace: allocating 26555 entries in 52 pages
[    0.024096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065173] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f74cc000 soft=f74ce000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.156059] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156133] Brought up 2 CPUs
[    0.156139] Total of 2 processors activated (7327.54 BogoMIPS).
[    0.158826] devtmpfs: initialized
[    0.158826] EVM: security.selinux
[    0.158826] EVM: security.SMACK64
[    0.158826] EVM: security.capability
[    0.158826] PM: Registering ACPI NVS region at b7da0000 (4096 bytes)
[    0.161917] print_constraints: dummy: 
[    0.161963] RTC time: 18:17:17, date: 10/06/12
[    0.162049] NET: Registered protocol family 16
[    0.162199] Trying to unpack rootfs image as initramfs...
[    0.162340] EISA bus registered
[    0.162374] ACPI: bus type pci registered
[    0.162522] PCI: MMCONFIG for domain 0000 [bus 00-02] at [mem 0xe0000000-0xe02fffff] (base 0xe0000000)
[    0.162530] PCI: MMCONFIG at [mem 0xe0000000-0xe02fffff] reserved in E820
[    0.162534] PCI: Using MMCONFIG for extended config space
[    0.162538] PCI: Using configuration type 1 for base access
[    0.176160] bio: create slab <bio-0> at 0
[    0.176346] ACPI: Added _OSI(Module Device)
[    0.176352] ACPI: Added _OSI(Processor Device)
[    0.176357] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176363] ACPI: Added _OSI(Processor Aggregator Device)
[    0.178459] ACPI: EC: Look up EC in DSDT
[    0.185435] ACPI: SSDT b7d99deb 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.185989] ACPI: Dynamic OEM Table Load:
[    0.185997] ACPI: SSDT   (null) 0021F (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.188061] ACPI: SSDT b7d99530 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.188690] ACPI: Dynamic OEM Table Load:
[    0.188698] ACPI: SSDT   (null) 00518 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.232979] ACPI: SSDT b7d9a00a 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.233550] ACPI: Dynamic OEM Table Load:
[    0.233559] ACPI: SSDT   (null) 001B0 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.234089] ACPI: SSDT b7d99a48 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.234614] ACPI: Dynamic OEM Table Load:
[    0.234622] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.264558] ACPI: Interpreter enabled
[    0.264589] ACPI: (supports S0 S1 S3 S4 S5)
[    0.264636] ACPI: Using IOAPIC for interrupt routing
[    0.268773] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.271943] ACPI: Power Resource [QFAN] (off)
[    0.272393] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.272672] ACPI: No dock devices found.
[    0.272678] HEST: Table not found.
[    0.272691] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.273462] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.274868] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.274875] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.274881] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.274887] pci_root PNP0A03:00: host bridge window [mem 0xb8000000-0xffedffff]
[    0.274893] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.274899] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.274905] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.274911] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.274916] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.274954] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.274976] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.275081] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.275148] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.275289] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.275319] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.275336] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.275353] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.275370] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.275387] pci 0000:00:02.5: reg 20: [io  0x1080-0x108f]
[    0.275457] pci 0000:00:02.5: PME# supported from D3cold
[    0.275466] pci 0000:00:02.5: PME# disabled
[    0.275494] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.275516] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.275618] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.275640] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.275749] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.275776] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.275890] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.275899] pci 0000:00:03.3: PME# disabled
[    0.275935] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.275962] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.275979] pci 0000:00:04.0: reg 14: [io  0x1000-0x107f]
[    0.276105] pci 0000:00:04.0: supports D1 D2
[    0.276110] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.276118] pci 0000:00:04.0: PME# disabled
[    0.276147] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.276174] pci 0000:00:05.0: reg 10: [io  0x10c8-0x10cf]
[    0.276191] pci 0000:00:05.0: reg 14: [io  0x10bc-0x10bf]
[    0.276207] pci 0000:00:05.0: reg 18: [io  0x10c0-0x10c7]
[    0.276224] pci 0000:00:05.0: reg 1c: [io  0x10b8-0x10bb]
[    0.276240] pci 0000:00:05.0: reg 20: [io  0x10a0-0x10af]
[    0.276309] pci 0000:00:05.0: PME# supported from D3cold
[    0.276317] pci 0000:00:05.0: PME# disabled
[    0.276354] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.276489] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.276497] pci 0000:00:06.0: PME# disabled
[    0.276545] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.276679] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.276687] pci 0000:00:07.0: PME# disabled
[    0.276745] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.276773] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.276891] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.276900] pci 0000:00:0f.0: PME# disabled
[    0.276980] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.277008] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.277024] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.277038] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.277124] pci 0000:01:00.0: supports D1 D2
[    0.277188] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.277197] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.277205] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.277214] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.277299] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.277311] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.277319] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.277411] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.277455] pci_bus 0000:00: on NUMA node 0
[    0.277463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.278009]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.278017]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.278021] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.287753] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.287867] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.287975] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11)
[    0.288100] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 9 10 11)
[    0.288239] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.288347] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.288453] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.288559] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.288877] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.288884] vgaarb: loaded
[    0.288888] vgaarb: bridge control possible 0000:01:00.0
[    0.289171] i2c-core: driver [aat2870] using legacy suspend method
[    0.289175] i2c-core: driver [aat2870] using legacy resume method
[    0.289362] SCSI subsystem initialized
[    0.289489] libata version 3.00 loaded.
[    0.289596] usbcore: registered new interface driver usbfs
[    0.289624] usbcore: registered new interface driver hub
[    0.289691] usbcore: registered new device driver usb
[    0.289904] PCI: Using ACPI for IRQ routing
[    0.289963] PCI: pci_cache_line_size set to 64 bytes
[    0.290075] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.290081] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.290329] NetLabel: Initializing
[    0.290333] NetLabel:  domain hash size = 128
[    0.290337] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.290360] NetLabel:  unlabeled traffic allowed by default
[    0.290473] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.290482] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.290493] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.296102] Switching to clocksource hpet
[    0.316295] AppArmor: AppArmor Filesystem Enabled
[    0.316362] pnp: PnP ACPI init
[    0.316404] ACPI: bus type pnp registered
[    0.317226] pnp 00:00: [bus 00-ff]
[    0.317234] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.317240] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.317245] pnp 00:00: [io  0x0d00-0xffff window]
[    0.317251] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.317257] pnp 00:00: [mem 0xb8000000-0xffedffff window]
[    0.317262] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.317268] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.317273] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.317278] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.317284] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.317289] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.317294] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.317300] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.317305] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.317310] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.317315] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.317321] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.317447] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.317802] pnp 00:01: [io  0x0000-0x000f]
[    0.317807] pnp 00:01: [io  0x0081-0x008f]
[    0.317812] pnp 00:01: [io  0x00c0-0x00df]
[    0.317817] pnp 00:01: [io  0x0480-0x048f]
[    0.317823] pnp 00:01: [dma 4]
[    0.317915] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.317977] pnp 00:02: [io  0x0070-0x0071]
[    0.318066] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.318088] pnp 00:03: [io  0x0061]
[    0.318172] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.318266] pnp 00:04: [io  0x8000-0x80be]
[    0.318271] pnp 00:04: [io  0x8100-0x812f]
[    0.318276] pnp 00:04: [io  0x0080]
[    0.318281] pnp 00:04: [io  0x04d0-0x04d1]
[    0.318285] pnp 00:04: [io  0xfe00]
[    0.318289] pnp 00:04: [io  0x002e]
[    0.318294] pnp 00:04: [io  0x002f]
[    0.318298] pnp 00:04: [io  0x0092]
[    0.318302] pnp 00:04: [io  0x0072-0x0073]
[    0.318307] pnp 00:04: [io  0x0078-0x0079]
[    0.318312] pnp 00:04: [io  0x0290-0x0297]
[    0.318317] pnp 00:04: [mem 0xe0000000-0xefffffff]
[    0.318322] pnp 00:04: [mem 0xfec00000-0xfeefffff]
[    0.318327] pnp 00:04: [mem 0xffb80000-0xffbfffff]
[    0.318332] pnp 00:04: [mem 0xffc00000-0xffc00fff]
[    0.318337] pnp 00:04: [mem 0xffe00000-0xffe00fff]
[    0.318342] pnp 00:04: [mem 0xffe80000-0xffefffff]
[    0.318497] system 00:04: [io  0x8000-0x80be] has been reserved
[    0.318504] system 00:04: [io  0x8100-0x812f] has been reserved
[    0.318511] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.318523] system 00:04: [io  0xfe00] has been reserved
[    0.318529] system 00:04: [io  0x0290-0x0297] has been reserved
[    0.318538] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.318545] system 00:04: [mem 0xfec00000-0xfeefffff] could not be reserved
[    0.318551] system 00:04: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.318558] system 00:04: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.318565] system 00:04: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.318572] system 00:04: [mem 0xffe80000-0xffefffff] could not be reserved
[    0.318580] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.318630] pnp 00:05: [io  0x00f0-0x00ff]
[    0.318653] pnp 00:05: [irq 13]
[    0.318742] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.318765] pnp 00:06: [mem 0xfec00000-0xfecfffff]
[    0.318771] pnp 00:06: [mem 0xfee00000-0xfeefffff]
[    0.318776] pnp 00:06: [mem 0xffc00000-0xffc00fff]
[    0.318780] pnp 00:06: [mem 0xffe00000-0xffe00fff]
[    0.318868] pnp 00:06: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.319019] pnp 00:07: [irq 0 disabled]
[    0.319031] pnp 00:07: [irq 8]
[    0.319042] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.319142] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.319167] pnp 00:08: [io  0x0060]
[    0.319172] pnp 00:08: [io  0x0064]
[    0.319183] pnp 00:08: [irq 1]
[    0.319273] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.319299] pnp 00:09: [irq 12]
[    0.319396] pnp 00:09: Plug and Play ACPI device, IDs SYN101f PNP0f13 (active)
[    0.319721] pnp: PnP ACPI: found 10 devices
[    0.319726] ACPI: ACPI bus type pnp unregistered
[    0.319735] PnPBIOS: Disabled by ACPI PNP
[    0.358660] PCI: max bus depth: 1 pci_try_num: 2
[    0.358727] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.358735] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.358742] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.358753] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.358761] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.358773] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.358780] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff]
[    0.358790] pci 0000:00:06.0:   bridge window [mem 0xdc000000-0xdfffffff]
[    0.358799] pci 0000:00:06.0:   bridge window [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.358812] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.358847] pci 0000:00:01.0: setting latency timer to 64
[    0.358886] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.358894] pci 0000:00:06.0: setting latency timer to 64
[    0.358907] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.358916] pci 0000:00:07.0: setting latency timer to 64
[    0.358925] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.358931] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.358936] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.358942] pci_bus 0000:00: resource 7 [mem 0xb8000000-0xffedffff]
[    0.358948] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.358953] pci_bus 0000:00: resource 9 [mem 0x000d4000-0x000d7fff]
[    0.358959] pci_bus 0000:00: resource 10 [mem 0x000d8000-0x000dbfff]
[    0.358965] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000dffff]
[    0.358970] pci_bus 0000:00: resource 12 [mem 0x000e0000-0x000e3fff]
[    0.358976] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.358982] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.358987] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.358993] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.358999] pci_bus 0000:04: resource 1 [mem 0xdc000000-0xdfffffff]
[    0.359004] pci_bus 0000:04: resource 2 [mem 0xb8000000-0xb81fffff 64bit pref]
[    0.359104] NET: Registered protocol family 2
[    0.359275] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.359804] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.360770] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.361239] TCP: Hash tables configured (established 131072 bind 65536)
[    0.361244] TCP reno registered
[    0.361252] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.361269] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.361452] NET: Registered protocol family 1
[    0.361554] pci 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.416064] pci 0000:00:03.0: PCI INT A disabled
[    0.416116] pci 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.472063] pci 0000:00:03.1: PCI INT B disabled
[    0.472111] pci 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.472143] pci 0000:00:03.3: PCI INT C disabled
[    0.472176] pci 0000:01:00.0: Boot video device
[    0.472184] PCI: CLS 16 bytes, default 64
[    0.472939] audit: initializing netlink socket (disabled)
[    0.472964] type=2000 audit(1349547436.468:1): initialized
[    0.521813] highmem bounce pool size: 64 pages
[    0.521826] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.526846] VFS: Disk quotas dquot_6.5.2
[    0.526991] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.528315] fuse init (API version 7.17)
[    0.528537] msgmni has been set to 1664
[    0.529246] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.529309] io scheduler noop registered
[    0.529313] io scheduler deadline registered
[    0.529329] io scheduler cfq registered (default)
[    0.529764] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.529823] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.530018] intel_idle: MWAIT substates: 0x22220
[    0.530022] intel_idle: does not run on family 6 model 15
[    0.530168] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.530283] ACPI: AC Adapter [ACAD] (off-line)
[    0.530443] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.530823] ACPI: Lid Switch [LID0]
[    0.530930] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.530940] ACPI: Power Button [PWRB]
[    0.531039] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.531047] ACPI: Power Button [PWRF]
[    0.531183] ACPI: Fan [FAN] (off)
[    0.538204] Monitor-Mwait will be used to enter C-1 state
[    0.538975] Monitor-Mwait will be used to enter C-2 state
[    0.539695] Monitor-Mwait will be used to enter C-3 state
[    0.539717] Marking TSC unstable due to TSC halts in idle
[    0.539736] ACPI: acpi_idle registered with cpuidle
[    0.546007] thermal LNXTHERM:00: registered as thermal_zone0
[    0.546013] ACPI: Thermal Zone [THRM] (53 C)
[    0.546076] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.546098] ACPI: Battery Slot [BAT1] (battery absent)
[    0.546179] ERST: Table is not found!
[    0.546182] GHES: HEST is not enabled!
[    0.546420] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.546709] ACPI: Battery Slot [BAT1] (battery absent)
[    0.546743] isapnp: Scanning for PnP cards...
[    0.827522] Freeing initrd memory: 13840k freed
[    0.901285] isapnp: No Plug & Play device found
[    0.944962] Linux agpgart interface v0.103
[    0.948638] brd: module loaded
[    0.950489] loop: module loaded
[    0.950909] pata_sis 0000:00:02.5: version 0.5.2
[    0.950939] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.951716] scsi0 : pata_sis
[    0.951893] scsi1 : pata_sis
[    0.952478] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    0.952484] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    0.952582] pata_acpi 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.952656] pata_acpi 0000:00:05.0: PCI INT A disabled
[    0.953494] Fixed MDIO Bus: probed
[    0.953543] tun: Universal TUN/TAP device driver, 1.6
[    0.953548] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.953664] PPP generic driver version 2.4.2
[    0.953899] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.953934] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.953964] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.954059] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.954110] ehci_hcd 0000:00:03.3: cache line size of 16 is not supported
[    0.954146] ehci_hcd 0000:00:03.3: irq 22, io mem 0xd4106000
[    0.964028] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.964350] hub 1-0:1.0: USB hub found
[    0.964360] hub 1-0:1.0: 8 ports detected
[    0.964529] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.964557] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.964585] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.964679] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.964717] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd4104000
[    1.026253] hub 2-0:1.0: USB hub found
[    1.026264] hub 2-0:1.0: 4 ports detected
[    1.026402] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.026423] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.026527] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.026562] ohci_hcd 0000:00:03.1: irq 21, io mem 0xd4105000
[    1.082269] hub 3-0:1.0: USB hub found
[    1.082279] hub 3-0:1.0: 4 ports detected
[    1.082419] uhci_hcd: USB Universal Host Controller Interface driver
[    1.082549] usbcore: registered new interface driver libusual
[    1.082656] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.086180] i8042: Detected active multiplexing controller, rev 1.1
[    1.088278] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.088291] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.088359] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.088426] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.088486] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.088767] mousedev: PS/2 mouse device common for all mice
[    1.089154] rtc_cmos 00:02: RTC can wake from S4
[    1.089349] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.089382] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.089518] device-mapper: uevent: version 1.0.3
[    1.089684] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.089757] EISA: Probing bus 0 at eisa.0
[    1.089762] EISA: Cannot allocate resource for mainboard
[    1.089767] Cannot allocate resource for EISA slot 1
[    1.089771] Cannot allocate resource for EISA slot 2
[    1.089775] Cannot allocate resource for EISA slot 3
[    1.089780] Cannot allocate resource for EISA slot 4
[    1.089784] Cannot allocate resource for EISA slot 5
[    1.089788] Cannot allocate resource for EISA slot 6
[    1.089792] Cannot allocate resource for EISA slot 7
[    1.089796] Cannot allocate resource for EISA slot 8
[    1.089800] EISA: Detected 0 cards.
[    1.089819] cpufreq-nforce2: No nForce2 chipset.
[    1.089964] cpuidle: using governor ladder
[    1.090199] cpuidle: using governor menu
[    1.090205] EFI Variables Facility v0.08 2004-May-17
[    1.090827] TCP cubic registered
[    1.091111] NET: Registered protocol family 10
[    1.092502] NET: Registered protocol family 17
[    1.092512] Registering the dns_resolver key type
[    1.092559] Using IPI No-Shortcut mode
[    1.092833] PM: Hibernation image not present or could not be loaded.
[    1.092859] registered taskstats version 1
[    1.107910]   Magic number: 0:105:291
[    1.107973] tty tty24: hash matches
[    1.108082] rtc_cmos 00:02: setting system clock to 2012-10-06 18:17:18 UTC (1349547438)
[    1.108774] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.108777] EDD information not available.
[    1.116289] ata1.00: ATAPI: MATSHITADVD-RAM UJ870PC, 1.00, max UDMA/33
[    1.124459] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.132280] ata1.00: configured for UDMA/33
[    1.134757] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870PC  1.00 PQ: 0 ANSI: 5
[    1.144530] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.144534] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.144695] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.144826] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.144953] ata2: port disabled--ignoring
[    1.145092] Freeing unused kernel memory: 740k freed
[    1.145540] Write protecting the kernel text: 5820k
[    1.145570] Write protecting the kernel read-only data: 2376k
[    1.145572] NX-protecting the kernel data: 4420k
[    1.167005] udevd[96]: starting version 175
[    1.256949] sata_sis 0000:00:05.0: version 1.0
[    1.256985] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.256991] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.258101] scsi2 : sata_sis
[    1.261783] scsi3 : sata_sis
[    1.262373] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 17
[    1.262377] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 17
[    1.270978] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.271028] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.271043] sis190 0000:00:04.0: setting latency timer to 64
[    1.271069] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.332046] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.364024] sis190: 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1
[    1.424249] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.424254] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.440239] ata3.00: configured for UDMA/133
[    1.440427] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.440665] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.440670] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.440737] sd 2:0:0:0: [sda] Write Protect is off
[    1.440741] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.440769] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.482850] usbcore: registered new interface driver uas
[    1.483102] Initializing USB Mass Storage driver...
[    1.483152] usbcore: registered new interface driver usb-storage
[    1.483154] USB Mass Storage support registered.
[    1.500733]  sda: sda1 sda2 < sda5 >
[    1.501262] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.592031] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.611485] scsi4 : usb-storage 1-4:1.0
[    1.611609] usbcore: registered new interface driver ums-realtek
[    1.844032] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[    1.884052] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    1.916719] sis190 0000:00:04.0: eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f841a000 (IRQ: 19), 00:1e:68:24:0c:41
[    1.916723] sis190 0000:00:04.0: eth0: GMII mode.
[    1.916730] sis190 0000:00:04.0: eth0: Enabling Auto-negotiation
[    2.081514] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.296044] usb 2-2: new low-speed USB device number 2 using ohci_hcd
[    2.620882] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.621729] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.624236] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   19.461245] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.489025] udevd[309]: starting version 175
[   19.575478] Adding 3010556k swap on /dev/sda5.  Priority:-1 extents:1 across:3010556k 
[   19.612269] type=1400 audit(1349540257.003:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=376 comm="apparmor_parser"
[   19.612801] type=1400 audit(1349540257.003:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=376 comm="apparmor_parser"
[   19.613107] type=1400 audit(1349540257.003:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=376 comm="apparmor_parser"
[   19.621296] lp: driver loaded but no devices found
[   19.622904] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.625901] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   19.631440] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   19.701944] input: MLK OM1007 Wireless Mouse as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input4
[   19.702363] generic-usb 0003:04FC:0538.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK OM1007 Wireless Mouse] on usb-0000:00:03.0-2/input0
[   19.702438] usbcore: registered new interface driver usbhid
[   19.702441] usbhid: USB HID core driver
[   19.765948] Linux video capture interface: v2.00
[   19.789734] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.792763] uvcvideo: Found UVC 1.00 device CNF7045 (04f2:b062)
[   19.798637] input: CNF7045 as /devices/pci0000:00/0000:00:03.3/usb1/1-8/1-8:1.0/input/input5
[   19.798974] usbcore: registered new interface driver uvcvideo
[   19.798978] USB Video Class driver (1.1.1)
[   19.799448] acpi device:0e: registered as cooling_device3
[   19.800284] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/LNXVIDEO:00/input/input6
[   19.800378] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.808265] cfg80211: Calling CRDA to update world regulatory domain
[   19.873609] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.063135] cfg80211: World regulatory domain updated:
[   20.063140] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.063144] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.063147] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.063150] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.063154] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.063157] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.138236] snd_hda_intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.138290] snd_hda_intel 0000:00:0f.0: setting latency timer to 64
[   20.171508] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input7
[   20.171796] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input8
[   20.240719] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.240724] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240727] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.240731] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240736] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.240740] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240742] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.240746] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240749] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.240752] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240757] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.240761] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240764] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.240767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240770] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.240774] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240779] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.240783] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240785] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.240789] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240792] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.240795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.240798] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.240801] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.240804] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.240807] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.240810] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.240814] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.249488] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   20.250335] ieee80211 phy0: hwaddr 00:17:c4:1c:54:1d, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   20.275182] rtl8187: Customer ID is 0x00
[   20.275338] Registered led device: rtl8187-phy0::radio
[   20.275402] Registered led device: rtl8187-phy0::tx
[   20.275482] Registered led device: rtl8187-phy0::rx
[   20.276922] rtl8187: wireless switch is on
[   20.277015] usbcore: registered new interface driver rtl8187
[   20.332399] init: failsafe main process (732) killed by TERM signal
[   20.429185] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   20.429189] vesafb: scrolling: redraw
[   20.429192] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.430547] vesafb: framebuffer at 0xc0000000, mapped to 0xf8780000, using 1216k, total 1216k
[   20.431093] Console: switching to colour frame buffer device 80x30
[   20.431111] fb0: VESA VGA frame buffer device
[   20.475472] Bluetooth: Core ver 2.16
[   20.475514] NET: Registered protocol family 31
[   20.475517] Bluetooth: HCI device and connection manager initialized
[   20.475521] Bluetooth: HCI socket layer initialized
[   20.475524] Bluetooth: L2CAP socket layer initialized
[   20.475930] Bluetooth: SCO socket layer initialized
[   20.496406] ppdev: user-space parallel port driver
[   20.516716] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.516721] Bluetooth: BNEP filters: protocol multicast
[   20.534834] Bluetooth: RFCOMM TTY layer initialized
[   20.534841] Bluetooth: RFCOMM socket layer initialized
[   20.534844] Bluetooth: RFCOMM ver 1.11
[   20.554029] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   20.592957] type=1400 audit(1349540257.983:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=815 comm="apparmor_parser"
[   20.594597] type=1400 audit(1349540257.983:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=815 comm="apparmor_parser"
[   20.596352] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.873360] type=1400 audit(1349540258.263:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=846 comm="apparmor_parser"
[   20.873792] type=1400 audit(1349540258.263:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=847 comm="apparmor_parser"
[   20.874430] type=1400 audit(1349540258.263:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=847 comm="apparmor_parser"
[   20.874739] type=1400 audit(1349540258.263:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=847 comm="apparmor_parser"
[   20.880651] type=1400 audit(1349540258.271:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=850 comm="apparmor_parser"
[   21.184971] init: kdm main process (917) killed by TERM signal
[   22.296394] init: plymouth-upstart-bridge main process (762) killed by TERM signal
[   24.826572] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.826994] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.830070] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.832686] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.131008] wlan0: authenticate with 40:4a:03:fb:6d:6c (try 1)
[   30.133244] wlan0: authenticated
[   30.133994] wlan0: associate with 40:4a:03:fb:6d:6c (try 1)
[   30.142958] wlan0: RX AssocResp from 40:4a:03:fb:6d:6c (capab=0xc11 status=0 aid=2)
[   30.142967] wlan0: associated
[   30.148755] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.150465] cfg80211: Calling CRDA for country: NL
[   30.160737] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   30.160748] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160751] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   30.160754] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160757] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   30.160761] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160764] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   30.160767] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160770] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   30.160773] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160776] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   30.160780] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160782] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   30.160786] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160789] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   30.160792] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160795] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   30.160798] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160801] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   30.160805] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160807] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   30.160811] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160814] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   30.160817] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160820] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   30.160823] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   30.160826] cfg80211: Disabling freq 2484 MHz
[   30.160829] cfg80211: Regulatory domain changed to country: NL
[   30.160832] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.160836] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.160839] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.160842] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.160844] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   34.872027] sis190 0000:00:04.0: eth0: auto-negotiating...
[   36.508063] usb 1-4: reset high-speed USB device number 3 using ehci_hcd
[   37.836075] usbcore: deregistering interface driver ums-realtek
[   37.872106] usbcore: deregistering interface driver usb-storage
[   37.901345] init: plymouth-stop pre-start process (1604) terminated with status 1
[   40.568024] wlan0: no IPv6 routers present
```

---

### Post by NikTh on 2012-10-07
I can see the exactly same errors with this [sdb] device. 

Sorry  but I have no further ideas for now. 

If you want to undo the previous action 

```
gksudo gedit  /etc/rc.local
``` 
and **remove** the line we added before . **modprobe -r ums_realtek**

It seems that do , nothing.

Thanks

---

### Post by Noor1101 on 2012-10-07
Thank you very much for your time and effort, NikTH!

I'll mark this thread as solved as the battery-problem seems to be due to the battery itself.

When I run into problems with the sdb device I'll open another thread.

Regards,
Noor

---

