---
title: "Error while startup in Lubuntu"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by inger on 2011-10-05
Hi,
 
I have installed Lubuntu 11.04. When I boot up, sometimes the start up don't get well. The startup procedure stops and a "-" is blinking on the screen. After ctrl-alt-delete the process proceed, and the Lubuntu GUI is OK.
Other times the startup is fine.
Some solution for this?

---

### Post by amjjawad on 2011-10-05
> **inger said:**
> Hi,
 
I have installed Lubuntu 11.04. When I boot up, sometimes the start up don't get well. The startup procedure stops and a "-" is blinking on the screen. After ctrl-alt-delete the process proceed, and the Lubuntu GUI is OK.
Other times the startup is fine.
Some solution for this?

Hi,

1- What are the hardware specifications of your machine?

2- After you downloaded the iso file for Lubuntu and BEFORE creating the LiveCD or LiveUSB, have you checked MD5SUM?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

3- Is Lubuntu the only OS on your machine?

---

### Post by inger on 2011-10-06
Hi,
 
1. The hardware specification is:
[LIST]
[*]CPU: Intel Atom 1.6GHz
[*]RAM: 2 GB
[*]BIOS: Phoenix BIOS
[*]Mass Storage: 160 GB 2.5" SATA HDD
[/LIST]2. Now I have tested the MD5SUM. The hashed sum is: 76e5865ce8d0d08fa9f833d781016fe3, just like it should be.
 
3. Lubuntu is the only OS.
 
Due to the letter size. What I think is so strange is that sometimes the  size is small and sometimes the size is bigger. I haven't adjust the letter size.

---

### Post by amjjawad on 2011-10-07
> **inger said:**
> Hi,
 
1. The hardware specification is:
[LIST]
[*]CPU: Intel Atom 1.6GHz
[*]RAM: 2 GB
[*]BIOS: Phoenix BIOS
[*]Mass Storage: 160 GB 2.5" SATA HDD
[/LIST]
2. Now I have tested the MD5SUM. The hashed sum is: 76e5865ce8d0d08fa9f833d781016fe3, just like it should be.
 
3. Lubuntu is the only OS.
 
Due to the letter size. What I think is so strange is that sometimes the  size is small and sometimes the size is bigger. I haven't adjust the letter size.

Hi again and sorry for the late reply.

For the size issue, I'm not sure why is that? but is it the resolution that keeps changing? or the font itself?

As for the blinking cursor, is it still happening? when you turn your machine ON and then Hold Shift Key, you are suppose to see GRUB Menu. Could you please do that and tell me what do you have?

---

### Post by inger on 2011-10-10
Thanks :),
 
It seems to just be the font that is very small sometimes. This is the font for the command window , the desktop and all other programs I test. The desktop icon seem to be the same size all time.
 
The blinking cursor still appears.
The GRUB version is 1.99~rc1-13ubuntu3
 
Sometimes the PC stops in the boot up text also. Today under boot-up it stops and I saw this line:
```

Starting ....                                [OK]
Starting .....                               [OK]
Starting load fallback graphics devices [fail]
 
Stopping ....                                [OK]
Stopping ...                                 [OK]

```

---

### Post by amjjawad on 2011-10-10
> **inger said:**
> It seems to just be the font that is very small sometimes. This is the font for the **command window** , the desktop and all other programs I test. The desktop icon seem to be the same size all time.
Sorry, what do you mean "Command Window"?

 
> The blinking cursor still appears.
The GRUB version is 1.99~rc1-13ubuntu3
 
Sometimes the PC stops in the boot up text also. Today under boot-up it stops and I saw this line:
```

Starting ....                                [OK]
Starting .....                               [OK]
Starting load fallback graphics devices [fail]
 
Stopping ....                                [OK]
Stopping ...                                 [OK]

```
I'm not an expert in this but hope this is the right thing to do.

Please run this command:
```
leafpad /var/log/dmesg
```

Copy the content, write CODE between [ ], paste the content, write CODE between [/ ] and post OR paste the content of the file, select it all here in your post then click "#".

---

### Post by inger on 2011-10-12
When I wrote CommandWindow, I meant the Terminal.
My startup disk is 8GB SSD.
 
The dmesg is like:
```

[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 0000000000090000 (usable)
[ 0.000000] BIOS-e820: 0000000000090000 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000003f6b0000 (usable)
[ 0.000000] BIOS-e820: 000000003f6b0000 - 000000003f6bc000 (ACPI data)
[ 0.000000] BIOS-e820: 000000003f6bc000 - 000000003f6bf000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000003f6bf000 - 0000000040000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[ 0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[ 0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[ 0.000000] DMI present.
[ 0.000000] DMI: CompuLab CM-iAM/SBC-FITPC2i/CM-iAM/SBC-FITPC2i, BIOS NAPA0001.86C.0000.D.1009141059 09/14/2010
[ 0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[ 0.000000] last_pfn = 0x3f6b0 max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-CFFFF write-protect
[ 0.000000] D0000-DFFFF uncachable
[ 0.000000] E0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask 0C0000000 write-back
[ 0.000000] 1 base 03F700000 mask 0FFF00000 uncachable
[ 0.000000] 2 base 03F800000 mask 0FF800000 uncachable
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] found SMP MP-table at [c00f8600] f8600
[ 0.000000] initial memory mapped : 0 - 01c00000
[ 0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 0037400000 page 2M
[ 0.000000] 0037400000 - 00377fe000 page 4k
[ 0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[ 0.000000] RAMDISK: 35cb4000 - 36e52000
[ 0.000000] ACPI: RSDP 000f85d0 00024 (v02 PTLTD )
[ 0.000000] ACPI: XSDT 3f6b77e1 00064 (v01 PTLTD ? XSDT 06040000 LTP 00000000)
[ 0.000000] ACPI: FACP 3f6bbdb0 000F4 (v03 INTEL POULSBO 06040000 INTC 00000032)
[ 0.000000] ACPI: DSDT 3f6b803a 03CF2 (v01 INTEL POULSBO 06040000 INTL 20050624)
[ 0.000000] ACPI: FACS 3f6befc0 00040
[ 0.000000] ACPI: HPET 3f6bbea4 00038 (v01 INTEL POULSBO 06040000 INTC 00000032)
[ 0.000000] ACPI: MCFG 3f6bbedc 0003C (v01 INTEL POULSBO 06040000 INTC 00000032)
[ 0.000000] ACPI: TCPA 3f6bbf18 00032 (v01 PTLTD CALISTGA 06040000 PTL 00000001)
[ 0.000000] ACPI: TMOR 3f6bbf4a 00026 (v01 PTLTD 06040000 PTL 00000003)
[ 0.000000] ACPI: APIC 3f6bbf70 00068 (v01 PTLTD ? APIC 06040000 LTP 00000000)
[ 0.000000] ACPI: BOOT 3f6bbfd8 00028 (v01 PTLTD $SBFTBL$ 06040000 LTP 00000001)
[ 0.000000] ACPI: SSDT 3f6b7845 004DC (v02 PmRef CpuPm 00003000 INTL 20050624)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 126MB HIGHMEM available.
[ 0.000000] 887MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 377fe000
[ 0.000000] low ram: 0 - 377fe000
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x000377fe
[ 0.000000] HighMem 0x000377fe -> 0x0003f6b0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x00000090
[ 0.000000] 0: 0x00000100 -> 0x0003f6b0
[ 0.000000] On node 0 totalpages: 259632
[ 0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f700d200
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3936 pages, LIFO batch:0
[ 0.000000] Normal zone: 1744 pages used for memmap
[ 0.000000] Normal zone: 221486 pages, LIFO batch:31
[ 0.000000] HighMem zone: 254 pages used for memmap
[ 0.000000] HighMem zone: 32180 pages, LIFO batch:7
[ 0.000000] Using APIC driver default
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 40
[ 0.000000] PM: Registered nosave memory: 0000000000090000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[ 0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u2097152
[ 0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[ 0.000000] pcpu-alloc: [0] 0 1 
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 257602
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e474acb0-eb3a-4e40-af76-e000a18da082 ro vga=771 quiet splash vt.handoff=7
[ 0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 5194880 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Initializing HighMem for node 0 (000377fe:0003f6b0)
[ 0.000000] Memory: 996988k/1039040k available (5188k kernel code, 41540k reserved, 2540k data, 700k init, 129736k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff16000 - 0xfffff000 ( 932 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xf7ffe000 - 0xff7fe000 ( 120 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xf77fe000 ( 887 MB)
[ 0.000000] .init : 0xc178d000 - 0xc183c000 ( 700 kB)
[ 0.000000] .data : 0xc15112a1 - 0xc178c480 (2540 kB)
[ 0.000000] .text : 0xc1000000 - 0xc15112a1 (5188 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] RCU dyntick-idle grace-period acceleration is enabled.
[ 0.000000] RCU-based detection of stalled CPUs is disabled.
[ 0.000000] NR_IRQS:2304 nr_irqs:512 16
[ 0.000000] CPU 0 irqstacks, hard=f4c08000 soft=f4c0a000
[ 0.000000] Extended CMOS year: 2000
[ 0.000000] vt handoff: transparent VT on vt#7
[ 0.000000] Console: colour dummy device 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] hpet clockevent registered
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1595.735 MHz processor.
[ 0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.47 BogoMIPS (lpj=6382940)
[ 0.004020] pid_max: default: 32768 minimum: 301
[ 0.004079] Security Framework initialized
[ 0.004118] AppArmor: AppArmor initialized
[ 0.004123] Yama: becoming mindful.
[ 0.004259] Mount-cache hash table entries: 512
[ 0.004551] Initializing cgroup subsys ns
[ 0.004561] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[ 0.004569] Initializing cgroup subsys cpuacct
[ 0.004581] Initializing cgroup subsys memory
[ 0.004600] Initializing cgroup subsys devices
[ 0.004607] Initializing cgroup subsys freezer
[ 0.004613] Initializing cgroup subsys net_cls
[ 0.004618] Initializing cgroup subsys blkio
[ 0.004692] CPU: Physical Processor ID: 0
[ 0.004698] CPU: Processor Core ID: 0
[ 0.004704] mce: CPU supports 5 MCE banks
[ 0.004723] CPU0: Thermal monitoring enabled (TM1)
[ 0.004732] using mwait in idle threads.
[ 0.010179] ACPI: Core revision 20110112
[ 0.016029] ftrace: allocating 23640 entries in 47 pages
[ 0.020117] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.020449] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.062820] CPU0: Intel(R) Atom(TM) CPU Z530 @ 1.60GHz stepping 02
[ 0.064003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[ 0.064003] ... version: 3
[ 0.064003] ... bit width: 40
[ 0.064003] ... generic registers: 2
[ 0.064003] ... value mask: 000000ffffffffff
[ 0.064003] ... max period: 000000007fffffff
[ 0.064003] ... fixed-purpose events: 3
[ 0.064003] ... event mask: 0000000700000003
[ 0.064003] CPU 1 irqstacks, hard=f4caa000 soft=f4cac000
[ 0.064003] Booting Node 0, Processors #1 Ok.
[ 0.008000] Initializing CPU#1
[ 0.156045] Brought up 2 CPUs
[ 0.156055] Total of 2 processors activated (6383.42 BogoMIPS).
[ 0.156419] devtmpfs: initialized
[ 0.156472] CompuLab SBC-FITPC2 series board detected. Selecting BIOS-method for reboots.
[ 0.160358] print_constraints: dummy: 
[ 0.160391] Time: 5:31:03 Date: 10/12/11
[ 0.160483] NET: Registered protocol family 16
[ 0.160511] Trying to unpack rootfs image as initramfs...
[ 0.160916] EISA bus registered
[ 0.160943] ACPI: bus type pci registered
[ 0.161192] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[ 0.161205] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[ 0.161212] PCI: Using MMCONFIG for extended config space
[ 0.161218] PCI: Using configuration type 1 for base access
[ 0.165744] bio: create slab <bio-0> at 0
[ 0.168947] ACPI: EC: Look up EC in DSDT
[ 0.174284] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 0.175500] ACPI: SSDT 3f6b7d21 00245 (v02 PmRef Cpu0Ist 00003000 INTL 20050624)
[ 0.176248] ACPI: Dynamic OEM Table Load:
[ 0.176260] ACPI: SSDT (null) 00245 (v02 PmRef Cpu0Ist 00003000 INTL 20050624)
[ 0.177222] ACPI: SSDT 3f6b7f66 000D4 (v02 PmRef Cpu1Ist 00003000 INTL 20050624)
[ 0.177927] ACPI: Dynamic OEM Table Load:
[ 0.177940] ACPI: SSDT (null) 000D4 (v02 PmRef Cpu1Ist 00003000 INTL 20050624)
[ 0.376670] ACPI: Interpreter enabled
[ 0.376670] ACPI: (supports S0 S3 S4 S5)
[ 0.376670] ACPI: Using IOAPIC for interrupt routing
[ 0.378543] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[ 0.391627] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[ 0.392056] ACPI: No dock devices found.
[ 0.392066] HEST: Table not found.
[ 0.392077] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[ 0.392372] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[ 0.392922] pci_root PNP0A08:00: host bridge window [io 0x0000-0x0cf7]
[ 0.392934] pci_root PNP0A08:00: host bridge window [io 0x0d00-0xffff]
[ 0.392944] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[ 0.392954] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[ 0.392963] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000effff]
[ 0.392973] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
[ 0.392983] pci_root PNP0A08:00: host bridge window [mem 0x3f800000-0xfebfffff]
[ 0.393001] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c0000-0x000dffff] conflicts with reserved [mem 0x000d2000-0x000fffff]
[ 0.393037] pci 0000:00:00.0: [8086:8100] type 0 class 0x000600
[ 0.393142] pci 0000:00:02.0: [8086:8108] type 0 class 0x000300
[ 0.393175] pci 0000:00:02.0: reg 10: [mem 0xd0080000-0xd00fffff]
[ 0.393194] pci 0000:00:02.0: reg 14: [io 0x1800-0x1807]
[ 0.393214] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff]
[ 0.393235] pci 0000:00:02.0: reg 1c: [mem 0xd0040000-0xd007ffff]
[ 0.393376] pci 0000:00:1b.0: [8086:811b] type 0 class 0x000403
[ 0.393406] pci 0000:00:1b.0: reg 10: [mem 0xd0010000-0xd0013fff 64bit]
[ 0.393487] pci 0000:00:1b.0: PME# supported from D0 D3hot
[ 0.393498] pci 0000:00:1b.0: PME# disabled
[ 0.393536] pci 0000:00:1c.0: [8086:8110] type 1 class 0x000604
[ 0.393615] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.393625] pci 0000:00:1c.0: PME# disabled
[ 0.393664] pci 0000:00:1c.1: [8086:8112] type 1 class 0x000604
[ 0.393741] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.393752] pci 0000:00:1c.1: PME# disabled
[ 0.393797] pci 0000:00:1d.0: [8086:8114] type 0 class 0x000c03
[ 0.393852] pci 0000:00:1d.0: reg 20: [io 0x1820-0x183f]
[ 0.393905] pci 0000:00:1d.1: [8086:8115] type 0 class 0x000c03
[ 0.393963] pci 0000:00:1d.1: reg 20: [io 0x1840-0x185f]
[ 0.394018] pci 0000:00:1d.2: [8086:8116] type 0 class 0x000c03
[ 0.394084] pci 0000:00:1d.2: reg 20: [io 0x1860-0x187f]
[ 0.394158] pci 0000:00:1d.7: [8086:8117] type 0 class 0x000c03
[ 0.394197] pci 0000:00:1d.7: reg 10: [mem 0xd0014000-0xd00143ff]
[ 0.394324] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.394336] pci 0000:00:1d.7: PME# disabled
[ 0.394371] pci 0000:00:1e.0: [8086:811c] type 0 class 0x000805
[ 0.394395] pci 0000:00:1e.0: reg 10: [mem 0xd0014400-0xd00144ff]
[ 0.394485] pci 0000:00:1e.1: [8086:811d] type 0 class 0x000805
[ 0.394509] pci 0000:00:1e.1: reg 10: [mem 0xd0014800-0xd00148ff]
[ 0.394598] pci 0000:00:1e.2: [8086:811e] type 0 class 0x000805
[ 0.394622] pci 0000:00:1e.2: reg 10: [mem 0xd0014c00-0xd0014cff]
[ 0.394722] pci 0000:00:1f.0: [8086:8119] type 0 class 0x000601
[ 0.394837] pci 0000:00:1f.1: [8086:811a] type 0 class 0x000101
[ 0.394895] pci 0000:00:1f.1: reg 20: [io 0x1810-0x181f]
[ 0.395031] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[ 0.395062] pci 0000:02:00.0: reg 10: [io 0x2000-0x20ff]
[ 0.395106] pci 0000:02:00.0: reg 18: [mem 0xd0100000-0xd0100fff 64bit]
[ 0.395138] pci 0000:02:00.0: reg 20: [mem 0xd0500000-0xd050ffff 64bit pref]
[ 0.395162] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[ 0.395221] pci 0000:02:00.0: supports D1 D2
[ 0.395229] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.395241] pci 0000:02:00.0: PME# disabled
[ 0.400108] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[ 0.400128] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.400141] pci 0000:00:1c.0: bridge window [mem 0xd0100000-0xd01fffff]
[ 0.400153] pci 0000:00:1c.0: bridge window [mem 0xd0500000-0xd05fffff pref]
[ 0.400253] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[ 0.400287] pci 0000:03:00.0: reg 10: [io 0x3000-0x30ff]
[ 0.400332] pci 0000:03:00.0: reg 18: [mem 0xd0200000-0xd0200fff 64bit]
[ 0.400364] pci 0000:03:00.0: reg 20: [mem 0xd0600000-0xd060ffff 64bit pref]
[ 0.400387] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[ 0.400453] pci 0000:03:00.0: supports D1 D2
[ 0.400461] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.400474] pci 0000:03:00.0: PME# disabled
[ 0.408104] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[ 0.408123] pci 0000:00:1c.1: bridge window [io 0x3000-0x3fff]
[ 0.408136] pci 0000:00:1c.1: bridge window [mem 0xd0200000-0xd02fffff]
[ 0.408149] pci 0000:00:1c.1: bridge window [mem 0xd0600000-0xd06fffff pref]
[ 0.408180] pci_bus 0000:00: on NUMA node 0
[ 0.408207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.408656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[ 0.408840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[ 0.409166] pci0000:00: Requesting ACPI _OSC control (0x1d)
[ 0.420951] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[ 0.421143] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[ 0.421335] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[ 0.421518] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[ 0.421700] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[ 0.421897] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 0.422082] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[ 0.422266] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 0.422636] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.422667] vgaarb: loaded
[ 0.423570] SCSI subsystem initialized
[ 0.423783] libata version 3.00 loaded.
[ 0.423995] usbcore: registered new interface driver usbfs
[ 0.424106] usbcore: registered new interface driver hub
[ 0.424257] usbcore: registered new device driver usb
[ 0.424767] wmi: Mapper loaded
[ 0.424774] PCI: Using ACPI for IRQ routing
[ 0.424785] PCI: pci_cache_line_size set to 64 bytes
[ 0.424916] Expanded resource reserved due to conflict with PCI Bus 0000:00
[ 0.424927] reserve RAM buffer: 000000003f6b0000 - 000000003fffffff 
[ 0.425317] NetLabel: Initializing
[ 0.425325] NetLabel: domain hash size = 128
[ 0.425331] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.425371] NetLabel: unlabeled traffic allowed by default
[ 0.425513] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.425531] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.425547] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 0.432241] Switching to clocksource hpet
[ 0.434998] Switched to NOHz mode on CPU #0
[ 0.435043] Switched to NOHz mode on CPU #1
[ 0.455733] AppArmor: AppArmor Filesystem Enabled
[ 0.455821] pnp: PnP ACPI init
[ 0.455880] ACPI: bus type pnp registered
[ 0.456404] pnp 00:00: [bus 00-ff]
[ 0.456415] pnp 00:00: [io 0x0000-0x0cf7 window]
[ 0.456424] pnp 00:00: [io 0x0cf8-0x0cff]
[ 0.456432] pnp 00:00: [io 0x0d00-0xffff window]
[ 0.456441] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[ 0.456450] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[ 0.456459] pnp 00:00: [mem 0x000e0000-0x000effff window]
[ 0.456468] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[ 0.456477] pnp 00:00: [mem 0x3f800000-0xfebfffff window]
[ 0.456486] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[ 0.456677] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[ 0.456847] pnp 00:01: [mem 0xfd000000-0xfd003fff]
[ 0.456857] pnp 00:01: [mem 0xe0000000-0xefffffff]
[ 0.456866] pnp 00:01: [mem 0xfed00000-0xfed3ffff]
[ 0.456875] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[ 0.456884] pnp 00:01: [mem 0xfed45000-0xfed4bfff]
[ 0.457088] system 00:01: [mem 0xfd000000-0xfd003fff] has been reserved
[ 0.457100] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[ 0.457111] system 00:01: [mem 0xfed00000-0xfed3ffff] could not be reserved
[ 0.457122] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[ 0.457132] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[ 0.457145] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.457773] pnp 00:02: [io 0x0000-0x001f]
[ 0.457783] pnp 00:02: [io 0x0081-0x0091]
[ 0.457791] pnp 00:02: [io 0x0093-0x009f]
[ 0.457799] pnp 00:02: [io 0x00c0-0x00df]
[ 0.457807] pnp 00:02: [dma 4]
[ 0.457958] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[ 0.457997] pnp 00:03: [mem 0xff000000-0xffffffff]
[ 0.458144] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[ 0.458279] pnp 00:04: [irq 0 disabled]
[ 0.458307] pnp 00:04: [irq 8]
[ 0.458316] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[ 0.458467] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[ 0.458517] pnp 00:05: [io 0x00f0]
[ 0.458533] pnp 00:05: [irq 13]
[ 0.458673] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[ 0.458729] pnp 00:06: [io 0x002e-0x002f]
[ 0.458738] pnp 00:06: [io 0x004e-0x004f]
[ 0.458745] pnp 00:06: [io 0x0061]
[ 0.458752] pnp 00:06: [io 0x0063]
[ 0.458759] pnp 00:06: [io 0x0065]
[ 0.458766] pnp 00:06: [io 0x0067]
[ 0.458773] pnp 00:06: [io 0x0070]
[ 0.458780] pnp 00:06: [io 0x0080]
[ 0.458787] pnp 00:06: [io 0x0092]
[ 0.458795] pnp 00:06: [io 0x00b2-0x00b3]
[ 0.458803] pnp 00:06: [io 0x0295-0x0296]
[ 0.458810] pnp 00:06: [io 0x0680-0x069f]
[ 0.458818] pnp 00:06: [io 0x8080]
[ 0.458825] pnp 00:06: [io 0x1000-0x107f]
[ 0.458833] pnp 00:06: [io 0x1180-0x11bf]
[ 0.458840] pnp 00:06: [io 0x1640-0x164f]
[ 0.459075] system 00:06: [io 0x0295-0x0296] has been reserved
[ 0.459088] system 00:06: [io 0x0680-0x069f] has been reserved
[ 0.459098] system 00:06: [io 0x8080] has been reserved
[ 0.459108] system 00:06: [io 0x1000-0x107f] has been reserved
[ 0.459119] system 00:06: [io 0x1180-0x11bf] has been reserved
[ 0.459129] system 00:06: [io 0x1640-0x164f] has been reserved
[ 0.459142] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.459261] pnp 00:07: [io 0x0070-0x0073]
[ 0.459419] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[ 0.459714] pnp 00:08: [io 0x002e-0x002f]
[ 0.459724] pnp 00:08: [io 0x0000-0xffffffff disabled]
[ 0.459915] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.460965] pnp 00:09: [io 0x03f8-0x03ff]
[ 0.460996] pnp 00:09: [irq 4]
[ 0.461645] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[ 0.461702] pnp: PnP ACPI: found 10 devices
[ 0.461710] ACPI: ACPI bus type pnp unregistered
[ 0.461721] PnPBIOS: Disabled by ACPI PNP
[ 0.503989] pci 0000:02:00.0: BAR 6: assigned [mem 0xd0520000-0xd053ffff pref]
[ 0.504038] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[ 0.504051] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.504064] pci 0000:00:1c.0: bridge window [mem 0xd0100000-0xd01fffff]
[ 0.504076] pci 0000:00:1c.0: bridge window [mem 0xd0500000-0xd05fffff pref]
[ 0.504094] pci 0000:03:00.0: BAR 6: assigned [mem 0xd0620000-0xd063ffff pref]
[ 0.504103] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[ 0.504113] pci 0000:00:1c.1: bridge window [io 0x3000-0x3fff]
[ 0.504125] pci 0000:00:1c.1: bridge window [mem 0xd0200000-0xd02fffff]
[ 0.504137] pci 0000:00:1c.1: bridge window [mem 0xd0600000-0xd06fffff pref]
[ 0.504198] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 0.504212] pci 0000:00:1c.0: setting latency timer to 64
[ 0.504240] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[ 0.504252] pci 0000:00:1c.1: setting latency timer to 64
[ 0.504263] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7]
[ 0.504272] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff]
[ 0.504281] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[ 0.504291] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[ 0.504300] pci_bus 0000:00: resource 8 [mem 0x000f0000-0x000fffff]
[ 0.504309] pci_bus 0000:00: resource 9 [mem 0x3f800000-0xfebfffff]
[ 0.504319] pci_bus 0000:02: resource 0 [io 0x2000-0x2fff]
[ 0.504327] pci_bus 0000:02: resource 1 [mem 0xd0100000-0xd01fffff]
[ 0.504337] pci_bus 0000:02: resource 2 [mem 0xd0500000-0xd05fffff pref]
[ 0.504347] pci_bus 0000:03: resource 0 [io 0x3000-0x3fff]
[ 0.504355] pci_bus 0000:03: resource 1 [mem 0xd0200000-0xd02fffff]
[ 0.504365] pci_bus 0000:03: resource 2 [mem 0xd0600000-0xd06fffff pref]
[ 0.504488] NET: Registered protocol family 2
[ 0.504694] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.505582] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.506895] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.507677] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.507689] TCP reno registered
[ 0.507705] UDP hash table entries: 512 (order: 2, 16384 bytes)
[ 0.507733] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[ 0.508119] NET: Registered protocol family 1
[ 0.508176] pci 0000:00:02.0: Boot video device
[ 0.508338] PCI: CLS 64 bytes, default 64
[ 0.508411] Simple Boot Flag at 0x36 set to 0x1
[ 0.509079] cpufreq-nforce2: No nForce2 chipset.
[ 0.509554] audit: initializing netlink socket (disabled)
[ 0.509585] type=2000 audit(1318397462.504:1): initialized
[ 0.534556] highmem bounce pool size: 64 pages
[ 0.534574] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.541778] VFS: Disk quotas dquot_6.5.2
[ 0.542009] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.544762] fuse init (API version 7.16)
[ 0.545146] msgmni has been set to 1693
[ 0.546001] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.546126] io scheduler noop registered
[ 0.546133] io scheduler deadline registered
[ 0.546213] io scheduler cfq registered (default)
[ 0.546792] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.546906] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.547138] intel_idle: MWAIT substates: 0x3020220
[ 0.547158] intel_idle: v0.4 model 0x1C
[ 0.547164] intel_idle: lapic_timer_reliable_states 0x2
[ 0.547183] Marking TSC unstable due to TSC halts in idle states deeper than C2
[ 0.547385] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.547553] ACPI: AC Adapter [ADP1] (on-line)
[ 0.547800] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[ 0.547817] ACPI: Power Button [PWRB]
[ 0.548073] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[ 0.548087] ACPI: Power Button [PWRF]
[ 0.548104] ACPI Error: Could not enable PowerButton event (20110112/evxfevnt-198)
[ 0.548119] ACPI Warning: Could not enable fixed event 0x2 (20110112/evxface-197)
[ 0.584235] button: probe of LNXPWRBN:00 failed with error -22
[ 0.584732] ACPI: acpi_idle yielding to intel_idle
[ 0.589750] thermal LNXTHERM:00: registered as thermal_zone0
[ 0.589761] ACPI: Thermal Zone [TZ00] (0 C)
[ 0.590310] ACPI: Invalid active0 threshold
[ 0.590713] thermal LNXTHERM:01: registered as thermal_zone1
[ 0.590722] ACPI: Thermal Zone [TZ01] (0 C)
[ 0.590810] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.590861] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.590897] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.591068] ERST: Table is not found!
[ 0.591377] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[ 0.600254] ACPI: Battery Slot [BAT0] (battery absent)
[ 0.600315] ACPI: Battery Slot [BAT1] (battery absent)
[ 0.600369] ACPI: Battery Slot [BAT2] (battery absent)
[ 0.600438] isapnp: Scanning for PnP cards...
[ 0.611911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.955094] isapnp: No Plug & Play device found
[ 1.124744] Freeing initrd memory: 18040k freed
[ 1.188117] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.188785] Linux agpgart interface v0.103
[ 1.192241] brd: module loaded
[ 1.193847] loop: module loaded
[ 1.194130] i2c-core: driver [adp5520] using legacy suspend method
[ 1.194136] i2c-core: driver [adp5520] using legacy resume method
[ 1.194529] pata_acpi 0000:00:1f.1: setting latency timer to 64
[ 1.195530] Fixed MDIO Bus: probed
[ 1.195644] PPP generic driver version 2.4.2
[ 1.195771] tun: Universal TUN/TAP device driver, 1.6
[ 1.195777] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1.196051] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.196119] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[ 1.196154] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 1.196163] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 1.196264] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 1.196391] ehci_hcd 0000:00:1d.7: debug port 1
[ 1.200285] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[ 1.200321] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xd0014000
[ 1.216030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 1.216352] hub 1-0:1.0: USB hub found
[ 1.216365] hub 1-0:1.0: 8 ports detected
[ 1.216555] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.216597] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.216697] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1.216712] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1.216719] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 1.216828] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1.216937] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[ 1.217266] hub 2-0:1.0: USB hub found
[ 1.217278] hub 2-0:1.0: 2 ports detected
[ 1.217442] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1.217456] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1.217463] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 1.217567] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 1.217667] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[ 1.217989] hub 3-0:1.0: USB hub found
[ 1.218001] hub 3-0:1.0: 2 ports detected
[ 1.218161] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1.218175] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1.218182] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 1.218283] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 1.220102] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[ 1.220440] hub 4-0:1.0: USB hub found
[ 1.220452] hub 4-0:1.0: 2 ports detected
[ 1.220743] i8042: PNP: No PS/2 controller found. Probing ports directly.
[ 1.222798] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.222815] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.223163] mousedev: PS/2 mouse device common for all mice
[ 1.223409] rtc_cmos 00:07: RTC can wake from S4
[ 1.224175] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[ 1.224210] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[ 1.224462] device-mapper: uevent: version 1.0.3
[ 1.224690] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[ 1.224873] device-mapper: multipath: version 1.2.0 loaded
[ 1.224882] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 1.225107] EISA: Probing bus 0 at eisa.0
[ 1.225114] EISA: Cannot allocate resource for mainboard
[ 1.225121] Cannot allocate resource for EISA slot 1
[ 1.225127] Cannot allocate resource for EISA slot 2
[ 1.225132] Cannot allocate resource for EISA slot 3
[ 1.225138] Cannot allocate resource for EISA slot 4
[ 1.225144] Cannot allocate resource for EISA slot 5
[ 1.225149] Cannot allocate resource for EISA slot 6
[ 1.225155] Cannot allocate resource for EISA slot 7
[ 1.225160] Cannot allocate resource for EISA slot 8
[ 1.225165] EISA: Detected 0 cards.
[ 1.225514] cpuidle: using governor ladder
[ 1.225858] cpuidle: using governor menu
[ 1.226517] TCP cubic registered
[ 1.226876] NET: Registered protocol family 10
[ 1.228214] NET: Registered protocol family 17
[ 1.228268] Registering the dns_resolver key type
[ 1.229319] Using IPI No-Shortcut mode
[ 1.229612] PM: Hibernation image not present or could not be loaded.
[ 1.229648] registered taskstats version 1
[ 1.230019] Magic number: 15:929:516
[ 1.230151] rtc_cmos 00:07: setting system clock to 2011-10-12 05:31:04 UTC (1318397464)
[ 1.230161] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.230165] EDD information not available.
[ 1.230403] Freeing unused kernel memory: 700k freed
[ 1.230977] Write protecting the kernel text: 5192k
[ 1.231066] Write protecting the kernel read-only data: 2148k
[ 1.297149] <30>udev[65]: starting version 167
[ 1.557831] pata_sch 0000:00:1f.1: version 0.2
[ 1.557938] pata_sch 0000:00:1f.1: setting latency timer to 64
[ 1.576061] scsi0 : pata_sch
[ 1.580278] scsi1 : pata_sch
[ 1.581288] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[ 1.581301] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[ 1.583842] sdhci: Secure Digital Host Controller Interface driver
[ 1.583852] sdhci: Copyright(c) Pierre Ossman
[ 1.610828] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[ 1.629206] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.629271] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.629346] r8169 0000:02:00.0: setting latency timer to 64
[ 1.629442] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[ 1.631068] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8016000, 00:01:c0:06:40:0b, XID 1c4000c0 IRQ 40
[ 1.644241] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.644305] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1.644371] r8169 0000:03:00.0: setting latency timer to 64
[ 1.644468] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
[ 1.646213] r8169 0000:03:00.0: eth1: RTL8168c/8111c at 0xf80c4000, 00:01:c0:06:40:0c, XID 1c4000c0 IRQ 41
[ 1.712371] acpi device:05: registered as cooling_device2
[ 1.747066] ata1.00: ATA-8: SanDisk pSSD-S2 8GB, SSD 6.00, max UDMA/133
[ 1.747075] ata1.00: 15649200 sectors, multi 0: LBA48 
[ 1.752051] usb 1-7: new high speed USB device using ehci_hcd and address 5
[ 1.762528] ata1.00: configured for UDMA/100
[ 1.762813] scsi 0:0:0:0: Direct-Access ATA SanDisk pSSD-S2 SSD PQ: 0 ANSI: 5
[ 1.763436] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.763556] sd 0:0:0:0: [sda] 15649200 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 1.763796] sd 0:0:0:0: [sda] Write Protect is off
[ 1.763807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.763919] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.764331] acpi device:06: registered as cooling_device3
[ 1.764583] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input2
[ 1.764763] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 1.764938] sdhci-pci 0000:00:1e.0: SDHCI controller found [8086:811c] (rev 7)
[ 1.764993] sdhci-pci 0000:00:1e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1.765073] sdhci-pci 0000:00:1e.0: setting latency timer to 64
[ 1.765124] mmc0: no vmmc regulator found
[ 1.765261] Registered led device: mmc0::
[ 1.765380] mmc0: SDHCI controller on PCI [0000:00:1e.0] using DMA
[ 1.765417] sdhci-pci 0000:00:1e.1: SDHCI controller found [8086:811d] (rev 7)
[ 1.765465] sdhci-pci 0000:00:1e.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[ 1.765523] sdhci-pci 0000:00:1e.1: setting latency timer to 64
[ 1.765567] mmc1: no vmmc regulator found
[ 1.765676] Registered led device: mmc1::
[ 1.765789] mmc1: SDHCI controller on PCI [0000:00:1e.1] using DMA
[ 1.765825] sdhci-pci 0000:00:1e.2: SDHCI controller found [8086:811e] (rev 7)
[ 1.765855] sdhci-pci 0000:00:1e.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1.765911] sdhci-pci 0000:00:1e.2: setting latency timer to 64
[ 1.765934] mmc2: no vmmc regulator found
[ 1.766032] Registered led device: mmc2::
[ 1.766142] mmc2: SDHCI controller on PCI [0000:00:1e.2] using DMA
[ 1.767611] sda: sda1 sda2 < sda5 >
[ 1.768807] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.090309] vesafb: framebuffer at 0x3f800000, mapped to 0xf8100000, using 512k, total 512k
[ 2.090322] vesafb: mode is 800x600x8, linelength=832, pages=0
[ 2.090329] vesafb: scrolling: redraw
[ 2.090338] vesafb: Pseudocolor: size=0:6:6:6, shift=0:0:0:0
[ 2.091539] Console: switching to colour frame buffer device 100x37
[ 2.091611] fb0: VESA VGA frame buffer device
[ 2.144137] usb 3-1: new low speed USB device using uhci_hcd and address 2
[ 2.410563] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[ 2.411189] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[ 2.411266] usbcore: registered new interface driver usbhid
[ 2.411275] usbhid: USB HID core driver
[ 2.417000] Btrfs loaded
[ 2.435404] xor: automatically using best checksumming function: pIII_sse
[ 2.452019] pIII_sse : 4857.000 MB/sec
[ 2.452029] xor: using function: pIII_sse (4857.000 MB/sec)
[ 2.460090] device-mapper: dm-raid45: initialized v0.2594b
[ 2.564093] usb 2-1: new low speed USB device using uhci_hcd and address 2
[ 2.582895] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[ 2.760269] input: LiteON HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[ 2.760531] generic-usb 0003:03F0:0324.0002: input,hidraw1: USB HID v1.00 Keyboard [LiteON HP Basic USB Keyboard] on usb-0000:00:1d.0-1/input0
[ 3.004070] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 3.176946] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5
[ 3.177392] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
[ 3.177671] generic-usb 0003:0EEF:0001.0003: input,hidraw2: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1d.0-2/input0
[ 3.508435] Adding 1037308k swap on /dev/sda5. Priority:-1 extents:1 across:1037308k SS
[ 3.589440] <30>udev[317]: starting version 167
[ 3.666693] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 3.701571] lp: driver loaded but no devices found
[ 4.357166] type=1400 audit(1318397467.623:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=444 comm="apparmor_parser"
[ 4.359642] type=1400 audit(1318397467.623:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=434 comm="apparmor_parser"
[ 4.360314] type=1400 audit(1318397467.627:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=444 comm="apparmor_parser"
[ 4.364476] type=1400 audit(1318397467.631:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=444 comm="apparmor_parser"
[ 4.365875] type=1400 audit(1318397467.631:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=434 comm="apparmor_parser"
[ 4.366702] type=1400 audit(1318397467.631:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=434 comm="apparmor_parser"
[ 4.380458] type=1400 audit(1318397467.647:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=488 comm="apparmor_parser"
[ 4.412890] type=1400 audit(1318397467.679:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=487 comm="apparmor_parser"
[ 5.282022] r8169 0000:02:00.0: eth0: link down
[ 5.282035] r8169 0000:02:00.0: eth0: link down
[ 5.282730] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5.326069] r8169 0000:03:00.0: eth1: link down
[ 5.344686] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5.836862] type=1400 audit(1318397469.103:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=685 comm="apparmor_parser"
[ 5.838067] type=1400 audit(1318397469.103:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[ 5.838877] type=1400 audit(1318397469.103:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[ 5.882065] type=1400 audit(1318397469.147:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=686 comm="apparmor_parser"
[ 5.926366] type=1400 audit(1318397469.191:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=687 comm="apparmor_parser"
[ 5.957534] type=1400 audit(1318397469.223:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=687 comm="apparmor_parser"
[ 5.968665] type=1400 audit(1318397469.235:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=686 comm="apparmor_parser"
[ 6.008901] type=1400 audit(1318397469.275:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=693 comm="apparmor_parser"
[ 6.015500] type=1400 audit(1318397469.279:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=686 comm="apparmor_parser"
[ 6.016625] cfg80211: Calling CRDA to update world regulatory domain
[ 6.057797] type=1400 audit(1318397469.323:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=694 comm="apparmor_parser"

```

---

### Post by amjjawad on 2011-10-12
> **inger said:**
> When I wrote CommandWindow, I meant the Terminal.
So, all your fonts are ok except the Terminal font? 
I'm sorry, I still don't understand what you mean. A screenshot perhaps will be better.

> 
The dmesg is like:
```

[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 0000000000090000 (usable)
[ 0.000000] BIOS-e820: 0000000000090000 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000003f6b0000 (usable)
[ 0.000000] BIOS-e820: 000000003f6b0000 - 000000003f6bc000 (ACPI data)
[ 0.000000] BIOS-e820: 000000003f6bc000 - 000000003f6bf000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000003f6bf000 - 0000000040000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[ 0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[ 0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[ 0.000000] DMI present.
[ 0.000000] DMI: CompuLab CM-iAM/SBC-FITPC2i/CM-iAM/SBC-FITPC2i, BIOS NAPA0001.86C.0000.D.1009141059 09/14/2010
[ 0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[ 0.000000] last_pfn = 0x3f6b0 max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-CFFFF write-protect
[ 0.000000] D0000-DFFFF uncachable
[ 0.000000] E0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask 0C0000000 write-back
[ 0.000000] 1 base 03F700000 mask 0FFF00000 uncachable
[ 0.000000] 2 base 03F800000 mask 0FF800000 uncachable
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] found SMP MP-table at [c00f8600] f8600
[ 0.000000] initial memory mapped : 0 - 01c00000
[ 0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 0037400000 page 2M
[ 0.000000] 0037400000 - 00377fe000 page 4k
[ 0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[ 0.000000] RAMDISK: 35cb4000 - 36e52000
[ 0.000000] ACPI: RSDP 000f85d0 00024 (v02 PTLTD )
[ 0.000000] ACPI: XSDT 3f6b77e1 00064 (v01 PTLTD ? XSDT 06040000 LTP 00000000)
[ 0.000000] ACPI: FACP 3f6bbdb0 000F4 (v03 INTEL POULSBO 06040000 INTC 00000032)
[ 0.000000] ACPI: DSDT 3f6b803a 03CF2 (v01 INTEL POULSBO 06040000 INTL 20050624)
[ 0.000000] ACPI: FACS 3f6befc0 00040
[ 0.000000] ACPI: HPET 3f6bbea4 00038 (v01 INTEL POULSBO 06040000 INTC 00000032)
[ 0.000000] ACPI: MCFG 3f6bbedc 0003C (v01 INTEL POULSBO 06040000 INTC 00000032)
[ 0.000000] ACPI: TCPA 3f6bbf18 00032 (v01 PTLTD CALISTGA 06040000 PTL 00000001)
[ 0.000000] ACPI: TMOR 3f6bbf4a 00026 (v01 PTLTD 06040000 PTL 00000003)
[ 0.000000] ACPI: APIC 3f6bbf70 00068 (v01 PTLTD ? APIC 06040000 LTP 00000000)
[ 0.000000] ACPI: BOOT 3f6bbfd8 00028 (v01 PTLTD $SBFTBL$ 06040000 LTP 00000001)
[ 0.000000] ACPI: SSDT 3f6b7845 004DC (v02 PmRef CpuPm 00003000 INTL 20050624)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 126MB HIGHMEM available.
[ 0.000000] 887MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 377fe000
[ 0.000000] low ram: 0 - 377fe000
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x000377fe
[ 0.000000] HighMem 0x000377fe -> 0x0003f6b0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x00000090
[ 0.000000] 0: 0x00000100 -> 0x0003f6b0
[ 0.000000] On node 0 totalpages: 259632
[ 0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f700d200
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3936 pages, LIFO batch:0
[ 0.000000] Normal zone: 1744 pages used for memmap
[ 0.000000] Normal zone: 221486 pages, LIFO batch:31
[ 0.000000] HighMem zone: 254 pages used for memmap
[ 0.000000] HighMem zone: 32180 pages, LIFO batch:7
[ 0.000000] Using APIC driver default
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 40
[ 0.000000] PM: Registered nosave memory: 0000000000090000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[ 0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u2097152
[ 0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[ 0.000000] pcpu-alloc: [0] 0 1 
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 257602
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e474acb0-eb3a-4e40-af76-e000a18da082 ro vga=771 quiet splash vt.handoff=7
[ 0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 5194880 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Initializing HighMem for node 0 (000377fe:0003f6b0)
[ 0.000000] Memory: 996988k/1039040k available (5188k kernel code, 41540k reserved, 2540k data, 700k init, 129736k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff16000 - 0xfffff000 ( 932 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xf7ffe000 - 0xff7fe000 ( 120 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xf77fe000 ( 887 MB)
[ 0.000000] .init : 0xc178d000 - 0xc183c000 ( 700 kB)
[ 0.000000] .data : 0xc15112a1 - 0xc178c480 (2540 kB)
[ 0.000000] .text : 0xc1000000 - 0xc15112a1 (5188 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] RCU dyntick-idle grace-period acceleration is enabled.
[ 0.000000] RCU-based detection of stalled CPUs is disabled.
[ 0.000000] NR_IRQS:2304 nr_irqs:512 16
[ 0.000000] CPU 0 irqstacks, hard=f4c08000 soft=f4c0a000
[ 0.000000] Extended CMOS year: 2000
[ 0.000000] vt handoff: transparent VT on vt#7
[ 0.000000] Console: colour dummy device 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] hpet clockevent registered
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1595.735 MHz processor.
[ 0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.47 BogoMIPS (lpj=6382940)
[ 0.004020] pid_max: default: 32768 minimum: 301
[ 0.004079] Security Framework initialized
[ 0.004118] AppArmor: AppArmor initialized
[ 0.004123] Yama: becoming mindful.
[ 0.004259] Mount-cache hash table entries: 512
[ 0.004551] Initializing cgroup subsys ns
[ 0.004561] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[ 0.004569] Initializing cgroup subsys cpuacct
[ 0.004581] Initializing cgroup subsys memory
[ 0.004600] Initializing cgroup subsys devices
[ 0.004607] Initializing cgroup subsys freezer
[ 0.004613] Initializing cgroup subsys net_cls
[ 0.004618] Initializing cgroup subsys blkio
[ 0.004692] CPU: Physical Processor ID: 0
[ 0.004698] CPU: Processor Core ID: 0
[ 0.004704] mce: CPU supports 5 MCE banks
[ 0.004723] CPU0: Thermal monitoring enabled (TM1)
[ 0.004732] using mwait in idle threads.
[ 0.010179] ACPI: Core revision 20110112
[ 0.016029] ftrace: allocating 23640 entries in 47 pages
[ 0.020117] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.020449] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.062820] CPU0: Intel(R) Atom(TM) CPU Z530 @ 1.60GHz stepping 02
[ 0.064003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[ 0.064003] ... version: 3
[ 0.064003] ... bit width: 40
[ 0.064003] ... generic registers: 2
[ 0.064003] ... value mask: 000000ffffffffff
[ 0.064003] ... max period: 000000007fffffff
[ 0.064003] ... fixed-purpose events: 3
[ 0.064003] ... event mask: 0000000700000003
[ 0.064003] CPU 1 irqstacks, hard=f4caa000 soft=f4cac000
[ 0.064003] Booting Node 0, Processors #1 Ok.
[ 0.008000] Initializing CPU#1
[ 0.156045] Brought up 2 CPUs
[ 0.156055] Total of 2 processors activated (6383.42 BogoMIPS).
[ 0.156419] devtmpfs: initialized
[ 0.156472] CompuLab SBC-FITPC2 series board detected. Selecting BIOS-method for reboots.
[ 0.160358] print_constraints: dummy: 
[ 0.160391] Time: 5:31:03 Date: 10/12/11
[ 0.160483] NET: Registered protocol family 16
[ 0.160511] Trying to unpack rootfs image as initramfs...
[ 0.160916] EISA bus registered
[ 0.160943] ACPI: bus type pci registered
[ 0.161192] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[ 0.161205] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[ 0.161212] PCI: Using MMCONFIG for extended config space
[ 0.161218] PCI: Using configuration type 1 for base access
[ 0.165744] bio: create slab <bio-0> at 0
[ 0.168947] ACPI: EC: Look up EC in DSDT
[ 0.174284] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 0.175500] ACPI: SSDT 3f6b7d21 00245 (v02 PmRef Cpu0Ist 00003000 INTL 20050624)
[ 0.176248] ACPI: Dynamic OEM Table Load:
[ 0.176260] ACPI: SSDT (null) 00245 (v02 PmRef Cpu0Ist 00003000 INTL 20050624)
[ 0.177222] ACPI: SSDT 3f6b7f66 000D4 (v02 PmRef Cpu1Ist 00003000 INTL 20050624)
[ 0.177927] ACPI: Dynamic OEM Table Load:
[ 0.177940] ACPI: SSDT (null) 000D4 (v02 PmRef Cpu1Ist 00003000 INTL 20050624)
[ 0.376670] ACPI: Interpreter enabled
[ 0.376670] ACPI: (supports S0 S3 S4 S5)
[ 0.376670] ACPI: Using IOAPIC for interrupt routing
[ 0.378543] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[ 0.391627] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[ 0.392056] ACPI: No dock devices found.
[ 0.392066] HEST: Table not found.
[ 0.392077] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[ 0.392372] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[ 0.392922] pci_root PNP0A08:00: host bridge window [io 0x0000-0x0cf7]
[ 0.392934] pci_root PNP0A08:00: host bridge window [io 0x0d00-0xffff]
[ 0.392944] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[ 0.392954] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[ 0.392963] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000effff]
[ 0.392973] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
[ 0.392983] pci_root PNP0A08:00: host bridge window [mem 0x3f800000-0xfebfffff]
[ 0.393001] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c0000-0x000dffff] conflicts with reserved [mem 0x000d2000-0x000fffff]
[ 0.393037] pci 0000:00:00.0: [8086:8100] type 0 class 0x000600
[ 0.393142] pci 0000:00:02.0: [8086:8108] type 0 class 0x000300
[ 0.393175] pci 0000:00:02.0: reg 10: [mem 0xd0080000-0xd00fffff]
[ 0.393194] pci 0000:00:02.0: reg 14: [io 0x1800-0x1807]
[ 0.393214] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff]
[ 0.393235] pci 0000:00:02.0: reg 1c: [mem 0xd0040000-0xd007ffff]
[ 0.393376] pci 0000:00:1b.0: [8086:811b] type 0 class 0x000403
[ 0.393406] pci 0000:00:1b.0: reg 10: [mem 0xd0010000-0xd0013fff 64bit]
[ 0.393487] pci 0000:00:1b.0: PME# supported from D0 D3hot
[ 0.393498] pci 0000:00:1b.0: PME# disabled
[ 0.393536] pci 0000:00:1c.0: [8086:8110] type 1 class 0x000604
[ 0.393615] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.393625] pci 0000:00:1c.0: PME# disabled
[ 0.393664] pci 0000:00:1c.1: [8086:8112] type 1 class 0x000604
[ 0.393741] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.393752] pci 0000:00:1c.1: PME# disabled
[ 0.393797] pci 0000:00:1d.0: [8086:8114] type 0 class 0x000c03
[ 0.393852] pci 0000:00:1d.0: reg 20: [io 0x1820-0x183f]
[ 0.393905] pci 0000:00:1d.1: [8086:8115] type 0 class 0x000c03
[ 0.393963] pci 0000:00:1d.1: reg 20: [io 0x1840-0x185f]
[ 0.394018] pci 0000:00:1d.2: [8086:8116] type 0 class 0x000c03
[ 0.394084] pci 0000:00:1d.2: reg 20: [io 0x1860-0x187f]
[ 0.394158] pci 0000:00:1d.7: [8086:8117] type 0 class 0x000c03
[ 0.394197] pci 0000:00:1d.7: reg 10: [mem 0xd0014000-0xd00143ff]
[ 0.394324] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.394336] pci 0000:00:1d.7: PME# disabled
[ 0.394371] pci 0000:00:1e.0: [8086:811c] type 0 class 0x000805
[ 0.394395] pci 0000:00:1e.0: reg 10: [mem 0xd0014400-0xd00144ff]
[ 0.394485] pci 0000:00:1e.1: [8086:811d] type 0 class 0x000805
[ 0.394509] pci 0000:00:1e.1: reg 10: [mem 0xd0014800-0xd00148ff]
[ 0.394598] pci 0000:00:1e.2: [8086:811e] type 0 class 0x000805
[ 0.394622] pci 0000:00:1e.2: reg 10: [mem 0xd0014c00-0xd0014cff]
[ 0.394722] pci 0000:00:1f.0: [8086:8119] type 0 class 0x000601
[ 0.394837] pci 0000:00:1f.1: [8086:811a] type 0 class 0x000101
[ 0.394895] pci 0000:00:1f.1: reg 20: [io 0x1810-0x181f]
[ 0.395031] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[ 0.395062] pci 0000:02:00.0: reg 10: [io 0x2000-0x20ff]
[ 0.395106] pci 0000:02:00.0: reg 18: [mem 0xd0100000-0xd0100fff 64bit]
[ 0.395138] pci 0000:02:00.0: reg 20: [mem 0xd0500000-0xd050ffff 64bit pref]
[ 0.395162] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[ 0.395221] pci 0000:02:00.0: supports D1 D2
[ 0.395229] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.395241] pci 0000:02:00.0: PME# disabled
[ 0.400108] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[ 0.400128] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.400141] pci 0000:00:1c.0: bridge window [mem 0xd0100000-0xd01fffff]
[ 0.400153] pci 0000:00:1c.0: bridge window [mem 0xd0500000-0xd05fffff pref]
[ 0.400253] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[ 0.400287] pci 0000:03:00.0: reg 10: [io 0x3000-0x30ff]
[ 0.400332] pci 0000:03:00.0: reg 18: [mem 0xd0200000-0xd0200fff 64bit]
[ 0.400364] pci 0000:03:00.0: reg 20: [mem 0xd0600000-0xd060ffff 64bit pref]
[ 0.400387] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[ 0.400453] pci 0000:03:00.0: supports D1 D2
[ 0.400461] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.400474] pci 0000:03:00.0: PME# disabled
[ 0.408104] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[ 0.408123] pci 0000:00:1c.1: bridge window [io 0x3000-0x3fff]
[ 0.408136] pci 0000:00:1c.1: bridge window [mem 0xd0200000-0xd02fffff]
[ 0.408149] pci 0000:00:1c.1: bridge window [mem 0xd0600000-0xd06fffff pref]
[ 0.408180] pci_bus 0000:00: on NUMA node 0
[ 0.408207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.408656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[ 0.408840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[ 0.409166] pci0000:00: Requesting ACPI _OSC control (0x1d)
[ 0.420951] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[ 0.421143] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[ 0.421335] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[ 0.421518] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[ 0.421700] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[ 0.421897] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 0.422082] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[ 0.422266] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 0.422636] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.422667] vgaarb: loaded
[ 0.423570] SCSI subsystem initialized
[ 0.423783] libata version 3.00 loaded.
[ 0.423995] usbcore: registered new interface driver usbfs
[ 0.424106] usbcore: registered new interface driver hub
[ 0.424257] usbcore: registered new device driver usb
[ 0.424767] wmi: Mapper loaded
[ 0.424774] PCI: Using ACPI for IRQ routing
[ 0.424785] PCI: pci_cache_line_size set to 64 bytes
[ 0.424916] Expanded resource reserved due to conflict with PCI Bus 0000:00
[ 0.424927] reserve RAM buffer: 000000003f6b0000 - 000000003fffffff 
[ 0.425317] NetLabel: Initializing
[ 0.425325] NetLabel: domain hash size = 128
[ 0.425331] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.425371] NetLabel: unlabeled traffic allowed by default
[ 0.425513] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.425531] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.425547] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 0.432241] Switching to clocksource hpet
[ 0.434998] Switched to NOHz mode on CPU #0
[ 0.435043] Switched to NOHz mode on CPU #1
[ 0.455733] AppArmor: AppArmor Filesystem Enabled
[ 0.455821] pnp: PnP ACPI init
[ 0.455880] ACPI: bus type pnp registered
[ 0.456404] pnp 00:00: [bus 00-ff]
[ 0.456415] pnp 00:00: [io 0x0000-0x0cf7 window]
[ 0.456424] pnp 00:00: [io 0x0cf8-0x0cff]
[ 0.456432] pnp 00:00: [io 0x0d00-0xffff window]
[ 0.456441] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[ 0.456450] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[ 0.456459] pnp 00:00: [mem 0x000e0000-0x000effff window]
[ 0.456468] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[ 0.456477] pnp 00:00: [mem 0x3f800000-0xfebfffff window]
[ 0.456486] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[ 0.456677] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[ 0.456847] pnp 00:01: [mem 0xfd000000-0xfd003fff]
[ 0.456857] pnp 00:01: [mem 0xe0000000-0xefffffff]
[ 0.456866] pnp 00:01: [mem 0xfed00000-0xfed3ffff]
[ 0.456875] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[ 0.456884] pnp 00:01: [mem 0xfed45000-0xfed4bfff]
[ 0.457088] system 00:01: [mem 0xfd000000-0xfd003fff] has been reserved
[ 0.457100] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[ 0.457111] system 00:01: [mem 0xfed00000-0xfed3ffff] could not be reserved
[ 0.457122] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[ 0.457132] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[ 0.457145] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.457773] pnp 00:02: [io 0x0000-0x001f]
[ 0.457783] pnp 00:02: [io 0x0081-0x0091]
[ 0.457791] pnp 00:02: [io 0x0093-0x009f]
[ 0.457799] pnp 00:02: [io 0x00c0-0x00df]
[ 0.457807] pnp 00:02: [dma 4]
[ 0.457958] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[ 0.457997] pnp 00:03: [mem 0xff000000-0xffffffff]
[ 0.458144] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[ 0.458279] pnp 00:04: [irq 0 disabled]
[ 0.458307] pnp 00:04: [irq 8]
[ 0.458316] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[ 0.458467] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[ 0.458517] pnp 00:05: [io 0x00f0]
[ 0.458533] pnp 00:05: [irq 13]
[ 0.458673] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[ 0.458729] pnp 00:06: [io 0x002e-0x002f]
[ 0.458738] pnp 00:06: [io 0x004e-0x004f]
[ 0.458745] pnp 00:06: [io 0x0061]
[ 0.458752] pnp 00:06: [io 0x0063]
[ 0.458759] pnp 00:06: [io 0x0065]
[ 0.458766] pnp 00:06: [io 0x0067]
[ 0.458773] pnp 00:06: [io 0x0070]
[ 0.458780] pnp 00:06: [io 0x0080]
[ 0.458787] pnp 00:06: [io 0x0092]
[ 0.458795] pnp 00:06: [io 0x00b2-0x00b3]
[ 0.458803] pnp 00:06: [io 0x0295-0x0296]
[ 0.458810] pnp 00:06: [io 0x0680-0x069f]
[ 0.458818] pnp 00:06: [io 0x8080]
[ 0.458825] pnp 00:06: [io 0x1000-0x107f]
[ 0.458833] pnp 00:06: [io 0x1180-0x11bf]
[ 0.458840] pnp 00:06: [io 0x1640-0x164f]
[ 0.459075] system 00:06: [io 0x0295-0x0296] has been reserved
[ 0.459088] system 00:06: [io 0x0680-0x069f] has been reserved
[ 0.459098] system 00:06: [io 0x8080] has been reserved
[ 0.459108] system 00:06: [io 0x1000-0x107f] has been reserved
[ 0.459119] system 00:06: [io 0x1180-0x11bf] has been reserved
[ 0.459129] system 00:06: [io 0x1640-0x164f] has been reserved
[ 0.459142] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.459261] pnp 00:07: [io 0x0070-0x0073]
[ 0.459419] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[ 0.459714] pnp 00:08: [io 0x002e-0x002f]
[ 0.459724] pnp 00:08: [io 0x0000-0xffffffff disabled]
[ 0.459915] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.460965] pnp 00:09: [io 0x03f8-0x03ff]
[ 0.460996] pnp 00:09: [irq 4]
[ 0.461645] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[ 0.461702] pnp: PnP ACPI: found 10 devices
[ 0.461710] ACPI: ACPI bus type pnp unregistered
[ 0.461721] PnPBIOS: Disabled by ACPI PNP
[ 0.503989] pci 0000:02:00.0: BAR 6: assigned [mem 0xd0520000-0xd053ffff pref]
[ 0.504038] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[ 0.504051] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.504064] pci 0000:00:1c.0: bridge window [mem 0xd0100000-0xd01fffff]
[ 0.504076] pci 0000:00:1c.0: bridge window [mem 0xd0500000-0xd05fffff pref]
[ 0.504094] pci 0000:03:00.0: BAR 6: assigned [mem 0xd0620000-0xd063ffff pref]
[ 0.504103] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[ 0.504113] pci 0000:00:1c.1: bridge window [io 0x3000-0x3fff]
[ 0.504125] pci 0000:00:1c.1: bridge window [mem 0xd0200000-0xd02fffff]
[ 0.504137] pci 0000:00:1c.1: bridge window [mem 0xd0600000-0xd06fffff pref]
[ 0.504198] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 0.504212] pci 0000:00:1c.0: setting latency timer to 64
[ 0.504240] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[ 0.504252] pci 0000:00:1c.1: setting latency timer to 64
[ 0.504263] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7]
[ 0.504272] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff]
[ 0.504281] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[ 0.504291] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[ 0.504300] pci_bus 0000:00: resource 8 [mem 0x000f0000-0x000fffff]
[ 0.504309] pci_bus 0000:00: resource 9 [mem 0x3f800000-0xfebfffff]
[ 0.504319] pci_bus 0000:02: resource 0 [io 0x2000-0x2fff]
[ 0.504327] pci_bus 0000:02: resource 1 [mem 0xd0100000-0xd01fffff]
[ 0.504337] pci_bus 0000:02: resource 2 [mem 0xd0500000-0xd05fffff pref]
[ 0.504347] pci_bus 0000:03: resource 0 [io 0x3000-0x3fff]
[ 0.504355] pci_bus 0000:03: resource 1 [mem 0xd0200000-0xd02fffff]
[ 0.504365] pci_bus 0000:03: resource 2 [mem 0xd0600000-0xd06fffff pref]
[ 0.504488] NET: Registered protocol family 2
[ 0.504694] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.505582] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.506895] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.507677] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.507689] TCP reno registered
[ 0.507705] UDP hash table entries: 512 (order: 2, 16384 bytes)
[ 0.507733] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[ 0.508119] NET: Registered protocol family 1
[ 0.508176] pci 0000:00:02.0: Boot video device
[ 0.508338] PCI: CLS 64 bytes, default 64
[ 0.508411] Simple Boot Flag at 0x36 set to 0x1
[ 0.509079] cpufreq-nforce2: No nForce2 chipset.
[ 0.509554] audit: initializing netlink socket (disabled)
[ 0.509585] type=2000 audit(1318397462.504:1): initialized
[ 0.534556] highmem bounce pool size: 64 pages
[ 0.534574] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.541778] VFS: Disk quotas dquot_6.5.2
[ 0.542009] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.544762] fuse init (API version 7.16)
[ 0.545146] msgmni has been set to 1693
[ 0.546001] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.546126] io scheduler noop registered
[ 0.546133] io scheduler deadline registered
[ 0.546213] io scheduler cfq registered (default)
[ 0.546792] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.546906] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.547138] intel_idle: MWAIT substates: 0x3020220
[ 0.547158] intel_idle: v0.4 model 0x1C
[ 0.547164] intel_idle: lapic_timer_reliable_states 0x2
[ 0.547183] Marking TSC unstable due to TSC halts in idle states deeper than C2
[ 0.547385] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.547553] ACPI: AC Adapter [ADP1] (on-line)
[ 0.547800] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[ 0.547817] ACPI: Power Button [PWRB]
[ 0.548073] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[ 0.548087] ACPI: Power Button [PWRF]
[ 0.548104] ACPI Error: Could not enable PowerButton event (20110112/evxfevnt-198)
[ 0.548119] ACPI Warning: Could not enable fixed event 0x2 (20110112/evxface-197)
[ 0.584235] button: probe of LNXPWRBN:00 failed with error -22
[ 0.584732] ACPI: acpi_idle yielding to intel_idle
[ 0.589750] thermal LNXTHERM:00: registered as thermal_zone0
[ 0.589761] ACPI: Thermal Zone [TZ00] (0 C)
[ 0.590310] ACPI: Invalid active0 threshold
[ 0.590713] thermal LNXTHERM:01: registered as thermal_zone1
[ 0.590722] ACPI: Thermal Zone [TZ01] (0 C)
[ 0.590810] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.590861] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.590897] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[ 0.591068] ERST: Table is not found!
[ 0.591377] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[ 0.600254] ACPI: Battery Slot [BAT0] (battery absent)
[ 0.600315] ACPI: Battery Slot [BAT1] (battery absent)
[ 0.600369] ACPI: Battery Slot [BAT2] (battery absent)
[ 0.600438] isapnp: Scanning for PnP cards...
[ 0.611911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.955094] isapnp: No Plug & Play device found
[ 1.124744] Freeing initrd memory: 18040k freed
[ 1.188117] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.188785] Linux agpgart interface v0.103
[ 1.192241] brd: module loaded
[ 1.193847] loop: module loaded
[ 1.194130] i2c-core: driver [adp5520] using legacy suspend method
[ 1.194136] i2c-core: driver [adp5520] using legacy resume method
[ 1.194529] pata_acpi 0000:00:1f.1: setting latency timer to 64
[ 1.195530] Fixed MDIO Bus: probed
[ 1.195644] PPP generic driver version 2.4.2
[ 1.195771] tun: Universal TUN/TAP device driver, 1.6
[ 1.195777] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1.196051] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.196119] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[ 1.196154] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 1.196163] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 1.196264] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 1.196391] ehci_hcd 0000:00:1d.7: debug port 1
[ 1.200285] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[ 1.200321] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xd0014000
[ 1.216030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 1.216352] hub 1-0:1.0: USB hub found
[ 1.216365] hub 1-0:1.0: 8 ports detected
[ 1.216555] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.216597] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.216697] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1.216712] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1.216719] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 1.216828] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1.216937] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[ 1.217266] hub 2-0:1.0: USB hub found
[ 1.217278] hub 2-0:1.0: 2 ports detected
[ 1.217442] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1.217456] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1.217463] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 1.217567] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 1.217667] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[ 1.217989] hub 3-0:1.0: USB hub found
[ 1.218001] hub 3-0:1.0: 2 ports detected
[ 1.218161] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1.218175] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1.218182] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 1.218283] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 1.220102] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[ 1.220440] hub 4-0:1.0: USB hub found
[ 1.220452] hub 4-0:1.0: 2 ports detected
[ 1.220743] i8042: PNP: No PS/2 controller found. Probing ports directly.
[ 1.222798] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.222815] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.223163] mousedev: PS/2 mouse device common for all mice
[ 1.223409] rtc_cmos 00:07: RTC can wake from S4
[ 1.224175] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[ 1.224210] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[ 1.224462] device-mapper: uevent: version 1.0.3
[ 1.224690] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[ 1.224873] device-mapper: multipath: version 1.2.0 loaded
[ 1.224882] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 1.225107] EISA: Probing bus 0 at eisa.0
[ 1.225114] EISA: Cannot allocate resource for mainboard
[ 1.225121] Cannot allocate resource for EISA slot 1
[ 1.225127] Cannot allocate resource for EISA slot 2
[ 1.225132] Cannot allocate resource for EISA slot 3
[ 1.225138] Cannot allocate resource for EISA slot 4
[ 1.225144] Cannot allocate resource for EISA slot 5
[ 1.225149] Cannot allocate resource for EISA slot 6
[ 1.225155] Cannot allocate resource for EISA slot 7
[ 1.225160] Cannot allocate resource for EISA slot 8
[ 1.225165] EISA: Detected 0 cards.
[ 1.225514] cpuidle: using governor ladder
[ 1.225858] cpuidle: using governor menu
[ 1.226517] TCP cubic registered
[ 1.226876] NET: Registered protocol family 10
[ 1.228214] NET: Registered protocol family 17
[ 1.228268] Registering the dns_resolver key type
[ 1.229319] Using IPI No-Shortcut mode
[ 1.229612] PM: Hibernation image not present or could not be loaded.
[ 1.229648] registered taskstats version 1
[ 1.230019] Magic number: 15:929:516
[ 1.230151] rtc_cmos 00:07: setting system clock to 2011-10-12 05:31:04 UTC (1318397464)
[ 1.230161] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.230165] EDD information not available.
[ 1.230403] Freeing unused kernel memory: 700k freed
[ 1.230977] Write protecting the kernel text: 5192k
[ 1.231066] Write protecting the kernel read-only data: 2148k
[ 1.297149] <30>udev[65]: starting version 167
[ 1.557831] pata_sch 0000:00:1f.1: version 0.2
[ 1.557938] pata_sch 0000:00:1f.1: setting latency timer to 64
[ 1.576061] scsi0 : pata_sch
[ 1.580278] scsi1 : pata_sch
[ 1.581288] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[ 1.581301] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[ 1.583842] sdhci: Secure Digital Host Controller Interface driver
[ 1.583852] sdhci: Copyright(c) Pierre Ossman
[ 1.610828] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[ 1.629206] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.629271] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1.629346] r8169 0000:02:00.0: setting latency timer to 64
[ 1.629442] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[ 1.631068] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8016000, 00:01:c0:06:40:0b, XID 1c4000c0 IRQ 40
[ 1.644241] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.644305] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1.644371] r8169 0000:03:00.0: setting latency timer to 64
[ 1.644468] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
[ 1.646213] r8169 0000:03:00.0: eth1: RTL8168c/8111c at 0xf80c4000, 00:01:c0:06:40:0c, XID 1c4000c0 IRQ 41
[ 1.712371] acpi device:05: registered as cooling_device2
[ 1.747066] ata1.00: ATA-8: SanDisk pSSD-S2 8GB, SSD 6.00, max UDMA/133
[ 1.747075] ata1.00: 15649200 sectors, multi 0: LBA48 
[ 1.752051] usb 1-7: new high speed USB device using ehci_hcd and address 5
[ 1.762528] ata1.00: configured for UDMA/100
[ 1.762813] scsi 0:0:0:0: Direct-Access ATA SanDisk pSSD-S2 SSD PQ: 0 ANSI: 5
[ 1.763436] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.763556] sd 0:0:0:0: [sda] 15649200 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 1.763796] sd 0:0:0:0: [sda] Write Protect is off
[ 1.763807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.763919] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.764331] acpi device:06: registered as cooling_device3
[ 1.764583] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input2
[ 1.764763] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 1.764938] sdhci-pci 0000:00:1e.0: SDHCI controller found [8086:811c] (rev 7)
[ 1.764993] sdhci-pci 0000:00:1e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1.765073] sdhci-pci 0000:00:1e.0: setting latency timer to 64
[ 1.765124] mmc0: no vmmc regulator found
[ 1.765261] Registered led device: mmc0::
[ 1.765380] mmc0: SDHCI controller on PCI [0000:00:1e.0] using DMA
[ 1.765417] sdhci-pci 0000:00:1e.1: SDHCI controller found [8086:811d] (rev 7)
[ 1.765465] sdhci-pci 0000:00:1e.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[ 1.765523] sdhci-pci 0000:00:1e.1: setting latency timer to 64
[ 1.765567] mmc1: no vmmc regulator found
[ 1.765676] Registered led device: mmc1::
[ 1.765789] mmc1: SDHCI controller on PCI [0000:00:1e.1] using DMA
[ 1.765825] sdhci-pci 0000:00:1e.2: SDHCI controller found [8086:811e] (rev 7)
[ 1.765855] sdhci-pci 0000:00:1e.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1.765911] sdhci-pci 0000:00:1e.2: setting latency timer to 64
[ 1.765934] mmc2: no vmmc regulator found
[ 1.766032] Registered led device: mmc2::
[ 1.766142] mmc2: SDHCI controller on PCI [0000:00:1e.2] using DMA
[ 1.767611] sda: sda1 sda2 < sda5 >
[ 1.768807] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.090309] vesafb: framebuffer at 0x3f800000, mapped to 0xf8100000, using 512k, total 512k
[ 2.090322] vesafb: mode is 800x600x8, linelength=832, pages=0
[ 2.090329] vesafb: scrolling: redraw
[ 2.090338] vesafb: Pseudocolor: size=0:6:6:6, shift=0:0:0:0
[ 2.091539] Console: switching to colour frame buffer device 100x37
[ 2.091611] fb0: VESA VGA frame buffer device
[ 2.144137] usb 3-1: new low speed USB device using uhci_hcd and address 2
[ 2.410563] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[ 2.411189] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[ 2.411266] usbcore: registered new interface driver usbhid
[ 2.411275] usbhid: USB HID core driver
[ 2.417000] Btrfs loaded
[ 2.435404] xor: automatically using best checksumming function: pIII_sse
[ 2.452019] pIII_sse : 4857.000 MB/sec
[ 2.452029] xor: using function: pIII_sse (4857.000 MB/sec)
[ 2.460090] device-mapper: dm-raid45: initialized v0.2594b
[ 2.564093] usb 2-1: new low speed USB device using uhci_hcd and address 2
[ 2.582895] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[ 2.760269] input: LiteON HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[ 2.760531] generic-usb 0003:03F0:0324.0002: input,hidraw1: USB HID v1.00 Keyboard [LiteON HP Basic USB Keyboard] on usb-0000:00:1d.0-1/input0
[ 3.004070] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 3.176946] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5
[ 3.177392] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
[ 3.177671] generic-usb 0003:0EEF:0001.0003: input,hidraw2: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1d.0-2/input0
[ 3.508435] Adding 1037308k swap on /dev/sda5. Priority:-1 extents:1 across:1037308k SS
[ 3.589440] <30>udev[317]: starting version 167
[ 3.666693] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 3.701571] lp: driver loaded but no devices found
[ 4.357166] type=1400 audit(1318397467.623:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=444 comm="apparmor_parser"
[ 4.359642] type=1400 audit(1318397467.623:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=434 comm="apparmor_parser"
[ 4.360314] type=1400 audit(1318397467.627:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=444 comm="apparmor_parser"
[ 4.364476] type=1400 audit(1318397467.631:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=444 comm="apparmor_parser"
[ 4.365875] type=1400 audit(1318397467.631:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=434 comm="apparmor_parser"
[ 4.366702] type=1400 audit(1318397467.631:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=434 comm="apparmor_parser"
[ 4.380458] type=1400 audit(1318397467.647:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=488 comm="apparmor_parser"
[ 4.412890] type=1400 audit(1318397467.679:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=487 comm="apparmor_parser"
[ 5.282022] r8169 0000:02:00.0: eth0: link down
[ 5.282035] r8169 0000:02:00.0: eth0: link down
[ 5.282730] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5.326069] r8169 0000:03:00.0: eth1: link down
[ 5.344686] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5.836862] type=1400 audit(1318397469.103:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=685 comm="apparmor_parser"
[ 5.838067] type=1400 audit(1318397469.103:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[ 5.838877] type=1400 audit(1318397469.103:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[ 5.882065] type=1400 audit(1318397469.147:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=686 comm="apparmor_parser"
[ 5.926366] type=1400 audit(1318397469.191:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=687 comm="apparmor_parser"
[ 5.957534] type=1400 audit(1318397469.223:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=687 comm="apparmor_parser"
[ 5.968665] type=1400 audit(1318397469.235:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=686 comm="apparmor_parser"
[ 6.008901] type=1400 audit(1318397469.275:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=693 comm="apparmor_parser"
[ 6.015500] type=1400 audit(1318397469.279:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=686 comm="apparmor_parser"
[ 6.016625] cfg80211: Calling CRDA to update world regulatory domain
[ 6.057797] type=1400 audit(1318397469.323:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=694 comm="apparmor_parser"

```

I can't see any thing wrong.
I noticed your Kernel is: 2.6.38-8-generic while the latest one for Lubuntu 11.04 is 2.6.38-11-generic. You can upgrade OR you can wait for tomorrow and install Lubuntu 11.10 if you are interested.

Sorry, I'm running out of ideas :(

---

### Post by inger on 2011-10-13
Thanks, anyway:).
I have got an idea from one of my colleagues that maybe the startup process is to fast, so the screen driver isn't ready when it had to do. I'll check up the new Lubuntu 11.10 today.

---

### Post by amjjawad on 2011-10-13
> **inger said:**
> Thanks, anyway:).
I have got an idea from one of my colleagues that maybe the startup process is to fast, so the screen driver isn't ready when it had to do. I'll check up the new Lubuntu 11.10 today.

Well, not sure how true that theory is but ... let's wait for 11.10 and give that a try? :)

---

### Post by amjjawad on 2011-10-13
I have P4 with 2MB L2 Cache and 2GB RAM.
If I'm not mistaken, my CPU is faster than yours. You can check your CPU Model and google that, you'll find the speed and cache. 

I  don't think the speed theory is correct but that's my opinion :)

---

### Post by www.rzr.online.fr on 2011-10-18
```

ACPI: Thermal Zone [TZ00] (0 C)

```

This line is suspecious I think , isnt it ?

I am investigating a similar log :

[http://rzr.online.fr/q/sensor](http://rzr.online.fr/q/sensor)

---

### Post by mathewd on 2012-04-12
> **inger said:**
> Hi,
 
I have installed Lubuntu 11.04. When I boot up, sometimes the start up don't get well. The startup procedure stops and a "-" is blinking on the screen. After ctrl-alt-delete the process proceed, and the Lubuntu GUI is OK.
Other times the startup is fine.
Some solution for this?

I had this same issue recently. I tried installing it several times, each the same result.
Then I happened to try starting into Lubuntu from the USB stick ("Try Lubuntu") and then running the installer from there. Restarted, and no problem! Not sure why that worked, but it could be worth a try.

---

