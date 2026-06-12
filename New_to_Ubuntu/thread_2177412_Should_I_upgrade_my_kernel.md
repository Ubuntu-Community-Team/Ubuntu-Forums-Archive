---
title: "Should I upgrade my kernel?"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by Pedro_Matias on 2013-09-28
I am having some troubles with my Ubuntu, case sometimes it just freezes for no reason.

I had some troubles with the drivers when I installed Ubuntu (Broadmcom Wireless Card) , and I thought maybe with a new kernel those problems get fixed.
Right now I have thos kernel:
```
pedro@pedro-HP-Pavilion-dm1-Notebook-PC:~$ uname -a
Linux pedro-HP-Pavilion-dm1-Notebook-PC 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

Should I upgrade my kernel to the 3.11.2 version?

---

### Post by Jonathan Precise on 2013-09-28
If:

```
sudo apt-get update && sudo apt-get upgrade
```

doesn't upgrade your kernel, then no. If it does, then yes. If it says the packages are held back, then:

```
sudo apt-get install ***package-name***
```

---

### Post by Pedro_Matias on 2013-09-28
I did the code, and it doesn't upgrade the kernel... So I guess I will just have to live with the freezes for now :(

---

### Post by Bucky Ball on 2013-09-28
I suggest you give more information about the freezes and we might have a better chance of fixing what is causing it. ;)

When does it freeze? 
Are you doing anything in particular when it freezes? Does it happen when you plug in a particular device or have two particular apps open at once?
Does it then 'unfreeze'? 
What release number are you using (the kernel number doesn't necessarily tell us if you've tried different ones)?

Also: Is wireless working (most Broadcom cards, except the very new, now work out of the box and you don't need to install anything manually)?

If it unfreezes, immediately open a terminal, type in 'dmesg', go to the bottom of the output. What does it say? It should give some clue as to what just happened with the freeze.

Post the last part of the output here please.

PS: I would forget about the kernel upgrade (could be problematic and just complicates things). The kernel wouldn't have anything to do with it, except in the rarest of situations, like a machine with hardware from another planet or another I can't think of right now. 

The kernel will upgrade as it should for your release with the commands Jonathon Precise gave or just by doing regular updates when they pop up via Update Manager. You'll see the new kernel or updates to the present one there in the list. ;)

---

### Post by Pedro_Matias on 2013-09-28
It just freezes randomly... When I turn on the computer I can do whatever I want and it doesn't freezes, but if the system suspends ( if I'm AFK or if I just close the laptop... ) , when resumes again, like 90% of the times it freezes , and it doesn't unfreezes, I can't even REISUB it...
Yes right now the wireless it's working but I had to download and install the bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb package , cause when the system tried to install the driver always gave an error...

---

### Post by Bucky Ball on 2013-09-28
Okay, so for clarity:

You boot the laptop and everything is fine, but when you suspend the laptop by closing the lid, then open it again, the system is frozen and stays 'in suspension', so to speak?

---

### Post by Pedro_Matias on 2013-09-28
No , no. It resumes I can make the login and see my desktop ( or whatever I had opened before ), but after a while (like 30 seconds or something) freezes

---

### Post by Pedro_Matias on 2013-09-28
I had a freeze right now. I went to dinner, I came back I resumed my computer, replied your post , and then I opened a new tab on Chromium and the system freezed...

EDIT: I don't know if is important or not but just for the record, i'm using Ubuntu 12.04 LTS and my DE is Unit 2D

---

### Post by Jonathan Precise on 2013-09-28
Please post the outputs of

```
dmesg
```

If it is too big to scroll back up, then:

```
dmesg | less
```

Post with [noparse]```

```[/noparse] tags.

---

### Post by Pedro_Matias on 2013-09-28
The file was to big to scroll but instead of doing dmesg | less I did dmesg > output.txt and copied all the text to here is that ok?

Here it is the output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 (Ubuntu 3.8.0-31.46~precise1-generic 3.8.13.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b67f1e8f-2cca-4ea6-bb11-23b6eafd8938 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000df9befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df9bf000-0x00000000dfabefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dfabf000-0x00000000dfbbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dfbbf000-0x00000000dfbf4fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dfbf5000-0x00000000dfbfffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dfc00000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000106ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000107000000-0x000000011effffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dm1 Notebook PC/3387, BIOS F.19 02/04/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x107000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFBBD000 mask FFFFFF000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000011f000000 aka 4592M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdfc00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdfbfffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xdfbfffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdfbfffff @ [mem 0x1fffe000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x106ffffff]
[    0.000000]  [mem 0x100000000-0x106ffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x106ffffff @ [mem 0xdfbfe000-0xdfbfffff]
[    0.000000] RAMDISK: [mem 0x36104000-0x37079fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000dfbf4120 0007C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000dfbf3000 000F4 (v04 HPQOEM SLIC-MPC 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000dfbdf000 0F5D1 (v01 HP     INSYDE   F0000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000dfb86000 00040
[    0.000000] ACPI: HPET 00000000dfbf2000 00038 (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000dfbf1000 00084 (v02 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000dfbf0000 0003C (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 00000000dfbef000 000A5 (v32 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000dfbde000 00028 (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000dfbdd000 00176 (v01 HPQOEM SLIC-MPC 00000001 ACPI 00040000)
[    0.000000] ACPI: WDRT 00000000dfbdc000 00047 (v01 HP     INSYDE   00000000 ACPI 00040000)
[    0.000000] ACPI: WDAT 00000000dfbdb000 001AC (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000dfbda000 003DE (v01 HP     INSYDE   00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000dfbd8000 0168E (v02 HP     INSYDE   00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000106ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x106ffffff]
[    0.000000]   NODE_DATA [mem 0x106ffb000-0x106ffffff]
[    0.000000]  [ffffea0000000000-ffffea00041fffff] PMD -> [ffff880102c00000-ffff8801065fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x106ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xdf9befff]
[    0.000000]   node   0: [mem 0xdfbf5000-0xdfbfffff]
[    0.000000]   node   0: [mem 0x100000000-0x106ffffff]
[    0.000000] On node 0 totalpages: 944473
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14248 pages used for memmap
[    0.000000]   DMA32 zone: 897570 pages, LIFO batch:31
[    0.000000]   Normal zone: 448 pages used for memmap
[    0.000000]   Normal zone: 28224 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df9bf000 - 00000000dfabf000
[    0.000000] PM: Registered nosave memory: 00000000dfabf000 - 00000000dfbbf000
[    0.000000] PM: Registered nosave memory: 00000000dfbbf000 - 00000000dfbf5000
[    0.000000] PM: Registered nosave memory: 00000000dfc00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880106c00000 s84928 r8192 d21568 u524288
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 929707
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b67f1e8f-2cca-4ea6-bb11-23b6eafd8938 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3620328k/4308992k available (7171k kernel code, 531100k absent, 157564k reserved, 6072k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 15204352 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1646.520 MHz processor
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3293.04 BogoMIPS (lpj=6586080)
[    0.000014] pid_max: default: 32768 minimum: 301
[    0.000063] Security Framework initialized
[    0.000089] AppArmor: AppArmor initialized
[    0.000091] Yama: becoming mindful.
[    0.000731] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003394] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004586] Mount-cache hash table entries: 256
[    0.004953] Initializing cgroup subsys cpuacct
[    0.004963] Initializing cgroup subsys memory
[    0.004980] Initializing cgroup subsys devices
[    0.004983] Initializing cgroup subsys freezer
[    0.004987] Initializing cgroup subsys blkio
[    0.004989] Initializing cgroup subsys perf_event
[    0.004995] Initializing cgroup subsys hugetlb
[    0.005043] tseg: 00dfc00000
[    0.005048] CPU: Physical Processor ID: 0
[    0.005050] CPU: Processor Core ID: 0
[    0.005054] mce: CPU supports 6 MCE banks
[    0.005073] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005073] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005073] tlb_flushall_shift: 5
[    0.005302] Freeing SMP alternatives: 24k freed
[    0.010032] ACPI: Core revision 20121018
[    0.024626] ftrace: allocating 29359 entries in 115 pages
[    1.064503] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.104142] smpboot: CPU0: AMD E-450 APU with Radeon(tm) HD Graphics (fam: 14, model: 02, stepping: 00)
[    1.209382] Performance Events: AMD PMU driver.
[    1.209391] ... version:                0
[    1.209394] ... bit width:              48
[    1.209396] ... generic registers:      4
[    1.209398] ... value mask:             0000ffffffffffff
[    1.209401] ... max period:             00007fffffffffff
[    1.209404] ... fixed-purpose events:   0
[    1.209406] ... event mask:             000000000000000f
[    1.211925] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    1.212143] smpboot: Booting Node   0, Processors  #1
[    1.225256] Brought up 2 CPUs
[    1.225261] smpboot: Total of 2 processors activated (6586.08 BogoMIPS)
[    1.226404] devtmpfs: initialized
[    1.229118] EVM: security.selinux
[    1.229123] EVM: security.SMACK64
[    1.229125] EVM: security.capability
[    1.229512] PM: Registering ACPI NVS region [mem 0xdfabf000-0xdfbbefff] (1048576 bytes)
[    1.231525] regulator-dummy: no parameters
[    1.231642] NET: Registered protocol family 16
[    1.232168] ACPI: bus type pci registered
[    1.232373] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    1.232379] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    1.238526] PCI: Using configuration type 1 for base access
[    1.240890] bio: create slab <bio-0> at 0
[    1.241432] ACPI: Added _OSI(Module Device)
[    1.241441] ACPI: Added _OSI(Processor Device)
[    1.241444] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.241447] ACPI: Added _OSI(Processor Aggregator Device)
[    1.244235] ACPI: EC: Look up EC in DSDT
[    1.247136] ACPI: Executed 1 blocks of module-level executable AML code
[    1.253090] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.403152] ACPI: Interpreter enabled
[    1.403177] ACPI: (supports S0 S3 S4 S5)
[    1.403227] ACPI: Using IOAPIC for interrupt routing
[    1.810182] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    1.810467] ACPI: No dock devices found.
[    1.810478] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.817028] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.817040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.817727] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce3ff])
[    1.817741] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.817823] PCI host bridge to bus 0000:00
[    1.817830] pci_bus 0000:00: root bus resource [bus 00-ff]
[    1.817835] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.817840] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.817844] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.817848] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.817852] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.817856] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.817860] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.817864] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.817868] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.817872] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.817876] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.817880] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.817884] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    1.817887] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    1.817891] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xf7ffffff]
[    1.817895] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    1.817899] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    1.817917] pci 0000:00:00.0: [1022:1510] type 00 class 0x060000
[    1.817981] pci 0000:00:01.0: [1002:9806] type 00 class 0x030000
[    1.817998] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    1.818008] pci 0000:00:01.0: reg 14: [io  0x4000-0x40ff]
[    1.818019] pci 0000:00:01.0: reg 18: [mem 0xf0300000-0xf033ffff]
[    1.818083] pci 0000:00:01.0: supports D1 D2
[    1.818110] pci 0000:00:01.1: [1002:1314] type 00 class 0x040300
[    1.818123] pci 0000:00:01.1: reg 10: [mem 0xf0344000-0xf0347fff]
[    1.818199] pci 0000:00:01.1: supports D1 D2
[    1.818233] pci 0000:00:04.0: [1022:1512] type 01 class 0x060400
[    1.818329] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.818457] pci 0000:00:11.0: [1002:4394] type 00 class 0x010601
[    1.818484] pci 0000:00:11.0: reg 10: [io  0x4118-0x411f]
[    1.818498] pci 0000:00:11.0: reg 14: [io  0x4124-0x4127]
[    1.818513] pci 0000:00:11.0: reg 18: [io  0x4110-0x4117]
[    1.818527] pci 0000:00:11.0: reg 1c: [io  0x4120-0x4123]
[    1.818541] pci 0000:00:11.0: reg 20: [io  0x4100-0x410f]
[    1.818556] pci 0000:00:11.0: reg 24: [mem 0xf034e000-0xf034e3ff]
[    1.818639] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    1.818658] pci 0000:00:12.0: reg 10: [mem 0xf034d000-0xf034dfff]
[    1.818758] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    1.819295] pci 0000:00:12.2: reg 10: [mem 0xf034c000-0xf034c0ff]
[    1.822275] pci 0000:00:12.2: supports D1 D2
[    1.822280] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.822315] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    1.822335] pci 0000:00:13.0: reg 10: [mem 0xf034b000-0xf034bfff]
[    1.822440] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    1.822953] pci 0000:00:13.2: reg 10: [mem 0xf034a000-0xf034a0ff]
[    1.825817] pci 0000:00:13.2: supports D1 D2
[    1.825821] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.825857] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    1.825968] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    1.825999] pci 0000:00:14.2: reg 10: [mem 0xf0340000-0xf0343fff 64bit]
[    1.826089] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.826112] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    1.826218] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    1.826292] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
[    1.826401] pci 0000:00:15.0: supports D1 D2
[    1.826440] pci 0000:00:15.1: [1002:43a1] type 01 class 0x060400
[    1.826548] pci 0000:00:15.1: supports D1 D2
[    1.826590] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    1.826610] pci 0000:00:16.0: reg 10: [mem 0xf0349000-0xf0349fff]
[    1.826714] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    1.827229] pci 0000:00:16.2: reg 10: [mem 0xf0348000-0xf03480ff]
[    1.830092] pci 0000:00:16.2: supports D1 D2
[    1.830097] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    1.830135] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
[    1.830188] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
[    1.830236] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
[    1.830286] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
[    1.830347] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
[    1.830395] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
[    1.830442] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
[    1.830493] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
[    1.830674] pci 0000:00:04.0: PCI bridge to [bus 01]
[    1.830805] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    1.830819] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.830824] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.830828] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.830832] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    1.830836] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    1.830840] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    1.830844] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.830848] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.830852] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.830857] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.830861] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    1.830865] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    1.830868] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    1.830872] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    1.830877] pci 0000:00:14.4:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    1.830881] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    1.830884] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    1.830989] pci 0000:03:00.0: [14e4:4727] type 00 class 0x028000
[    1.831024] pci 0000:03:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    1.831194] pci 0000:03:00.0: supports D1 D2
[    1.836700] pci 0000:00:15.0: PCI bridge to [bus 03-06]
[    1.836718] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    1.836727] pci 0000:00:15.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    1.836738] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.836853] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    1.836882] pci 0000:07:00.0: reg 10: [io  0x2000-0x20ff]
[    1.836923] pci 0000:07:00.0: reg 18: [mem 0xf0104000-0xf0104fff 64bit pref]
[    1.836949] pci 0000:07:00.0: reg 20: [mem 0xf0100000-0xf0103fff 64bit pref]
[    1.837062] pci 0000:07:00.0: supports D1 D2
[    1.837067] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.844684] pci 0000:00:15.1: PCI bridge to [bus 07]
[    1.844702] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    1.844717] pci 0000:00:15.1:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    1.844784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.VGA_._PRT]
[    1.844885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    1.844973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    1.845040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT]
[    1.845114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AZAL._PRT]
[    1.845215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.845555]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.846072]  pci0000:00: ACPI _OSC control (0x19) granted
[    1.848627] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.848856] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.848973] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.849088] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.849184] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.849260] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.849336] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.849411] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.849812] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    1.849831] vgaarb: loaded
[    1.849833] vgaarb: bridge control possible 0000:00:01.0
[    1.850238] SCSI subsystem initialized
[    1.850243] ACPI: bus type scsi registered
[    1.850559] libata version 3.00 loaded.
[    1.850623] ACPI: bus type usb registered
[    1.850676] usbcore: registered new interface driver usbfs
[    1.850694] usbcore: registered new interface driver hub
[    1.850982] usbcore: registered new device driver usb
[    1.851555] PCI: Using ACPI for IRQ routing
[    1.854277] PCI: pci_cache_line_size set to 64 bytes
[    1.854410] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    1.854415] e820: reserve RAM buffer [mem 0xdf9bf000-0xdfffffff]
[    1.854419] e820: reserve RAM buffer [mem 0xdfc00000-0xdfffffff]
[    1.854423] e820: reserve RAM buffer [mem 0x107000000-0x107ffffff]
[    1.854648] NetLabel: Initializing
[    1.854652] NetLabel:  domain hash size = 128
[    1.854654] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.854675] NetLabel:  unlabeled traffic allowed by default
[    1.854966] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.854979] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.857034] Switching to clocksource hpet
[    1.867988] AppArmor: AppArmor Filesystem Enabled
[    1.868054] pnp: PnP ACPI init
[    1.868083] ACPI: bus type pnp registered
[    1.868360] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.868366] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    1.868374] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.868763] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.868839] pnp 00:02: [dma 4]
[    1.868879] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.868931] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.869095] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.869234] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.869371] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.869509] pnp 00:07: Plug and Play ACPI device, IDs SYN1e50 PNP0f13 (active)
[    1.869602] system 00:08: [io  0x0400-0x04cf] has been reserved
[    1.869607] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    1.869612] system 00:08: [io  0x04d6] has been reserved
[    1.869616] system 00:08: [io  0x0680-0x06ff] has been reserved
[    1.869620] system 00:08: [io  0x077a] has been reserved
[    1.869624] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    1.869628] system 00:08: [io  0x0c14] has been reserved
[    1.869633] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    1.869637] system 00:08: [io  0x0c6c] has been reserved
[    1.869641] system 00:08: [io  0x0c6f] has been reserved
[    1.869645] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    1.869649] system 00:08: [io  0x0380-0x0387] has been reserved
[    1.869655] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.869796] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    1.869802] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    1.869808] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.870471] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
[    2.070230] pnp: PnP ACPI: found 11 devices
[    2.070240] ACPI: ACPI bus type pnp unregistered
[    2.081280] pci 0000:00:04.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    2.081292] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    2.081298] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    2.081377] pci 0000:00:04.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    2.081382] pci 0000:00:04.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    2.081387] pci 0000:00:04.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    2.081401] pci 0000:00:04.0: BAR 14: assigned [mem 0xf0400000-0xf05fffff]
[    2.081412] pci 0000:00:04.0: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
[    2.081418] pci 0000:00:04.0: BAR 13: assigned [io  0x1000-0x1fff]
[    2.081424] pci 0000:00:04.0: PCI bridge to [bus 01]
[    2.081431] pci 0000:00:04.0:   bridge window [io  0x1000-0x1fff]
[    2.081439] pci 0000:00:04.0:   bridge window [mem 0xf0400000-0xf05fffff]
[    2.081445] pci 0000:00:04.0:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
[    2.081453] pci 0000:00:14.4: PCI bridge to [bus 02]
[    2.081511] pci 0000:00:15.0: PCI bridge to [bus 03-06]
[    2.081517] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    2.081525] pci 0000:00:15.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    2.081532] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    2.081541] pci 0000:00:15.1: PCI bridge to [bus 07]
[    2.081546] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    2.081557] pci 0000:00:15.1:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    2.081621] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.081625] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.081630] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.081634] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.081637] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.081641] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.081645] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.081649] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.081653] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.081657] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    2.081661] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.081665] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.081668] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.081672] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    2.081676] pci_bus 0000:00: resource 18 [mem 0xe0000000-0xf7ffffff]
[    2.081680] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xfed3ffff]
[    2.081684] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    2.081688] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    2.081692] pci_bus 0000:01: resource 1 [mem 0xf0400000-0xf05fffff]
[    2.081696] pci_bus 0000:01: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
[    2.081701] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    2.081705] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    2.081708] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    2.081712] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.081716] pci_bus 0000:02: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.081720] pci_bus 0000:02: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.081724] pci_bus 0000:02: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.081728] pci_bus 0000:02: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.081732] pci_bus 0000:02: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.081735] pci_bus 0000:02: resource 13 [mem 0x000dc000-0x000dffff]
[    2.081739] pci_bus 0000:02: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.081743] pci_bus 0000:02: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.081747] pci_bus 0000:02: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.081751] pci_bus 0000:02: resource 17 [mem 0x000ec000-0x000effff]
[    2.081755] pci_bus 0000:02: resource 18 [mem 0xe0000000-0xf7ffffff]
[    2.081759] pci_bus 0000:02: resource 19 [mem 0xfc000000-0xfed3ffff]
[    2.081762] pci_bus 0000:02: resource 20 [mem 0xfed45000-0xffffffff]
[    2.081766] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    2.081770] pci_bus 0000:03: resource 1 [mem 0xf0200000-0xf02fffff]
[    2.081774] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    2.081778] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    2.081782] pci_bus 0000:07: resource 2 [mem 0xf0100000-0xf01fffff 64bit pref]
[    2.081846] NET: Registered protocol family 2
[    2.082161] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    2.082509] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    2.082788] TCP: Hash tables configured (established 32768 bind 32768)
[    2.082888] TCP: reno registered
[    2.082921] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.082973] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.083158] NET: Registered protocol family 1
[    2.083193] pci 0000:00:01.0: Boot video device
[    2.859986] PCI: CLS 64 bytes, default 64
[    2.860096] Trying to unpack rootfs image as initramfs...
[    3.365894] Freeing initrd memory: 15832k freed
[    3.375275] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.375289] software IO TLB [mem 0xdb9bf000-0xdf9bf000] (64MB) mapped at [ffff8800db9bf000-ffff8800df9befff]
[    3.375461] Simple Boot Flag at 0x44 set to 0x1
[    3.375728] LVT offset 0 assigned for vector 0x400
[    3.375883] perf: AMD IBS detected (0x000000ff)
[    3.376396] Initialise module verification
[    3.376485] audit: initializing netlink socket (disabled)
[    3.376510] type=2000 audit(1380405115.252:1): initialized
[    3.424202] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.428436] VFS: Disk quotas dquot_6.5.2
[    3.428549] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.429954] fuse init (API version 7.20)
[    3.430261] msgmni has been set to 7101
[    3.431414] Key type asymmetric registered
[    3.431422] Asymmetric key parser 'x509' registered
[    3.431524] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.431682] io scheduler noop registered
[    3.431692] io scheduler deadline registered (default)
[    3.431715] io scheduler cfq registered
[    3.432000] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    3.432288] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.432437] pciehp 0000:00:04.0:pcie04: HPC vendor_id 1022 device_id 1512 ss_vid 1022 ss_did 1234
[    3.432502] pciehp 0000:00:04.0:pcie04: service driver pciehp loaded
[    3.432512] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.566968] ACPI: AC Adapter [ACAD] (off-line)
[    3.567218] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.567228] ACPI: Power Button [PWRB]
[    3.567322] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    3.568175] ACPI: Lid Switch [LID]
[    3.568313] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.568323] ACPI: Power Button [PWRF]
[    3.568681] ACPI: acpi_idle registered with cpuidle
[    3.981181] thermal LNXTHERM:00: registered as thermal_zone0
[    3.981191] ACPI: Thermal Zone [THRM] (58 C)
[    3.981272] GHES: HEST is not enabled!
[    3.981462] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.988259] Linux agpgart interface v0.103
[    3.992621] brd: module loaded
[    3.995156] loop: module loaded
[    3.995851] libphy: Fixed MDIO Bus: probed
[    3.995977] tun: Universal TUN/TAP device driver, 1.6
[    3.995980] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.996303] PPP generic driver version 2.4.2
[    3.996498] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.996502] ehci-pci: EHCI PCI platform driver
[    3.996663] ehci-pci 0000:00:12.2: EHCI Host Controller
[    3.996677] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.996695] QUIRK: Enable AMD PLL fix
[    3.996699] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.996787] ehci-pci 0000:00:12.2: debug port 1
[    3.996853] ehci-pci 0000:00:12.2: irq 17, io mem 0xf034c000
[    4.006212] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    4.006295] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.006301] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.006306] usb usb1: Product: EHCI Host Controller
[    4.006310] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    4.006313] usb usb1: SerialNumber: 0000:00:12.2
[    4.006860] hub 1-0:1.0: USB hub found
[    4.006875] hub 1-0:1.0: 5 ports detected
[    4.007322] ehci-pci 0000:00:13.2: EHCI Host Controller
[    4.007334] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    4.007344] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    4.007363] ehci-pci 0000:00:13.2: debug port 1
[    4.007415] ehci-pci 0000:00:13.2: irq 17, io mem 0xf034a000
[    4.018203] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    4.018267] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.018273] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.018278] usb usb2: Product: EHCI Host Controller
[    4.018282] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    4.018286] usb usb2: SerialNumber: 0000:00:13.2
[    4.018784] hub 2-0:1.0: USB hub found
[    4.018800] hub 2-0:1.0: 5 ports detected
[    4.019252] ehci-pci 0000:00:16.2: EHCI Host Controller
[    4.019268] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    4.019278] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    4.019297] ehci-pci 0000:00:16.2: debug port 1
[    4.019347] ehci-pci 0000:00:16.2: irq 17, io mem 0xf0348000
[    4.030185] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    4.030287] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    4.030293] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.030298] usb usb3: Product: EHCI Host Controller
[    4.030302] usb usb3: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    4.030306] usb usb3: SerialNumber: 0000:00:16.2
[    4.030830] hub 3-0:1.0: USB hub found
[    4.030848] hub 3-0:1.0: 4 ports detected
[    4.031239] ehci-platform: EHCI generic platform driver
[    4.031259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.031479] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.031492] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    4.031543] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf034d000
[    4.090114] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    4.090123] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.090128] usb usb4: Product: OHCI Host Controller
[    4.090132] usb usb4: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    4.090136] usb usb4: SerialNumber: 0000:00:12.0
[    4.090589] hub 4-0:1.0: USB hub found
[    4.090676] hub 4-0:1.0: 5 ports detected
[    4.091012] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.091025] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    4.091059] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf034b000
[    4.150019] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    4.150029] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.150033] usb usb5: Product: OHCI Host Controller
[    4.150038] usb usb5: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    4.150041] usb usb5: SerialNumber: 0000:00:13.0
[    4.150492] hub 5-0:1.0: USB hub found
[    4.150589] hub 5-0:1.0: 5 ports detected
[    4.150928] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    4.150941] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    4.150979] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf0349000
[    4.190041] ACPI: Battery Slot [BAT0] (battery present)
[    4.210013] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    4.210022] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.210027] usb usb6: Product: OHCI Host Controller
[    4.210031] usb usb6: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    4.210035] usb usb6: SerialNumber: 0000:00:16.0
[    4.210608] hub 6-0:1.0: USB hub found
[    4.210695] hub 6-0:1.0: 4 ports detected
[    4.210986] uhci_hcd: USB Universal Host Controller Interface driver
[    4.211193] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.214835] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.214849] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.215540] mousedev: PS/2 mouse device common for all mice
[    4.216729] rtc_cmos 00:04: RTC can wake from S4
[    4.216925] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.216971] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    4.217159] device-mapper: uevent: version 1.0.3
[    4.217351] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    4.217412] cpuidle: using governor ladder
[    4.217547] cpuidle: using governor menu
[    4.217556] ledtrig-cpu: registered to indicate activity on CPUs
[    4.217559] EFI Variables Facility v0.08 2004-May-17
[    4.218563] ashmem: initialized
[    4.218856] TCP: cubic registered
[    4.219033] NET: Registered protocol family 10
[    4.219334] NET: Registered protocol family 17
[    4.219362] Key type dns_resolver registered
[    4.219969] Loading module verification certificates
[    4.222371] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: ef66b5fef7cf2d982f954bc9bd9879a3cb821073'
[    4.222397] registered taskstats version 1
[    4.228147] Key type trusted registered
[    4.232708] Key type encrypted registered
[    4.238774] rtc_cmos 00:04: setting system clock to 2013-09-28 21:51:57 UTC (1380405117)
[    4.238940] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    4.241237] acpi-cpufreq: overriding BIOS provided _PSD data
[    4.241485] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.241489] EDD information not available.
[    4.244838] Freeing unused kernel memory: 1012k freed
[    4.245413] Write protecting the kernel read-only data: 12288k
[    4.251981] Freeing unused kernel memory: 1012k freed
[    4.259078] Freeing unused kernel memory: 1008k freed
[    4.284157] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.308203] udevd[96]: starting version 175
[    4.317584] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    4.373625] tsc: Refined TSC clocksource calibration: 1646.493 MHz
[    4.373641] Switching to clocksource tsc
[    4.497468] usb 1-3: New USB device found, idVendor=064e, idProduct=d217
[    4.497479] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.497483] usb 1-3: Product: HP TrueVision HD
[    4.497488] usb 1-3: Manufacturer: SuYin
[    4.497491] usb 1-3: SerialNumber: HF1016-A821-OV03-VH-R02.09.02
[    4.521851] Disabling lock debugging due to kernel taint
[    4.523518] ahci 0000:00:11.0: version 3.0
[    4.536944] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.545619] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    4.545630] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    4.549171] scsi0 : ahci
[    4.557280] r8169 0000:07:00.0: irq 41 for MSI/MSI-X
[    4.557782] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000066a000, 80:c1:6e:49:47:50, XID 0c900800 IRQ 41
[    4.557788] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    4.607382] ata1: SATA max UDMA/133 abar m1024@0xf034e000 port 0xf034e100 irq 19
[    4.872957] usb 3-4: new high-speed USB device number 3 using ehci-pci
[    5.018031] usb 3-4: New USB device found, idVendor=0bda, idProduct=0138
[    5.018047] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.018055] usb 3-4: Product: USB2.0-CRW
[    5.018063] usb 3-4: Manufacturer: Generic
[    5.018070] usb 3-4: SerialNumber: 20090516388200000
[    5.030936] Initializing USB Mass Storage driver...
[    5.031079] usbcore: registered new interface driver usb-storage
[    5.031082] USB Mass Storage support registered.
[    5.057848] scsi1 : usb-storage 3-4:1.0
[    5.058049] usbcore: registered new interface driver ums-realtek
[    5.096676] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.098178] ata1.00: ATA-8: Hitachi HTS545050B9A300, PB4OCA1G, max UDMA/100
[    5.098194] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.099734] ata1.00: configured for UDMA/100
[    5.100431] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 PB4O PQ: 0 ANSI: 5
[    5.100929] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.100942] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.101037] sd 0:0:0:0: [sda] Write Protect is off
[    5.101044] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.101091] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.155742]  sda: sda1 sda2 < sda5 >
[    5.157287] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.288308] usb 6-1: new full-speed USB device number 2 using ohci_hcd
[    5.433278] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.433289] EXT4-fs (sda1): write access will be enabled during recovery
[    5.463245] usb 6-1: New USB device found, idVendor=0a5c, idProduct=21e3
[    5.463260] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.463269] usb 6-1: Product: BCM20702A0
[    5.463277] usb 6-1: Manufacturer: Broadcom Corp
[    5.463284] usb 6-1: SerialNumber: 642737C270DA
[    5.591784] usb 3-4: USB disconnect, device number 3
[    6.003401] EXT4-fs (sda1): orphan cleanup on readonly fs
[    6.003433] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623240
[    6.003576] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623236
[    6.003608] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623440
[    6.018363] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623438
[    6.050115] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3146959
[    6.050778] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147160
[    6.050886] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147158
[    6.050916] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147156
[    6.050941] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147154
[    6.065597] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623221
[    6.080164] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623156
[    6.080245] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623225
[    6.080276] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623154
[    6.080302] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623052
[    6.080328] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623436
[    6.080353] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623448
[    6.080381] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888773
[    6.080409] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 400339
[    6.080484] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 400338
[    6.080511] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 400337
[    6.100004] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 400268
[    6.100127] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 18350099
[    6.100146] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 18350097
[    6.100173] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623229
[    6.100203] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623222
[    6.100228] EXT4-fs (sda1): 25 orphan inodes deleted
[    6.100232] EXT4-fs (sda1): recovery complete
[    6.330697] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.939249] init: ureadahead main process (263) terminated with status 5
[    9.058819] Adding 3776508k swap on /dev/sda5.  Priority:-1 extents:1 across:3776508k 
[   10.749036] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.197562] udevd[339]: starting version 175
[   12.809547] lp: driver loaded but no devices found
[   13.406614] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.950801] lib80211: common routines for IEEE802.11 drivers
[   13.950812] lib80211_crypt: registered algorithm 'NULL'
[   14.077728] wmi: Mapper loaded
[   14.128712] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   14.128722] AMD IOMMUv2 functionality not available on this system
[   14.156674] microcode: CPU0: patch_level=0x05000101
[   14.160622] input: HP WMI hotkeys as /devices/virtual/input/input4
[   14.171813] acpi device:00: registered as cooling_device2
[   14.171909] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.172087] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   14.617276] microcode: CPU0: new patch_level=0x05000119
[   14.617593] microcode: CPU1: patch_level=0x05000101
[   14.625213] microcode: CPU1: new patch_level=0x05000119
[   14.625563] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.638941] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   14.700953] hp_accel: laptop model unknown, using default axes configuration
[   14.702682] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   14.702818] sp5100_tco: PCI Revision ID: 0x42
[   14.702945] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   14.702960] sp5100_tco: Last reboot was not triggered by watchdog.
[   14.704529] sp5100_tco: initialized (0xffffc90000676b00). heartbeat=60 sec (nowayout=0)
[   14.711921] lis3lv02d: 8 bits 3DC sensor found
[   14.750140] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   14.765947] cfg80211: Calling CRDA to update world regulatory domain
[   15.247643] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1679, fw id: 724542
[   15.289798] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   15.504572] Linux video capture interface: v2.00
[   15.778916] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.979201] Bluetooth: Core ver 2.16
[   15.979358] NET: Registered protocol family 31
[   15.979363] Bluetooth: HCI device and connection manager initialized
[   15.979881] Bluetooth: HCI socket layer initialized
[   15.979892] Bluetooth: L2CAP socket layer initialized
[   15.979912] Bluetooth: SCO socket layer initialized
[   15.988149] kvm: Nested Virtualization enabled
[   15.988167] kvm: Nested Paging enabled
[   16.084687] uvcvideo: Found UVC 1.00 device HP TrueVision HD (064e:d217)
[   16.090265] input: HP TrueVision HD as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input8
[   16.090706] usbcore: registered new interface driver uvcvideo
[   16.090711] USB Video Class driver (1.1.1)
[   16.597544] <6>[fglrx] Maximum main memory to use for locked dma buffers: 3398 MBytes.
[   16.597797] <6>[fglrx]   vendor: 1002 device: 9806 count: 1
[   16.598577] <6>[fglrx] ioport: bar 1, base 0x4000, size: 0x100
[   16.599237] <6>[fglrx] Kernel PAT support is enabled
[   16.599288] <6>[fglrx] module loaded - fglrx 12.10.5 [Mar 28 2013] with 1 minors
[   16.689205] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[   16.743448] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   16.969234] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   16.969738] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   17.383805] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   17.384178] usbcore: registered new interface driver btusb
[   17.455733] lib80211_crypt: registered algorithm 'TKIP'
[   17.600063] Bluetooth: can't load firmware, may not work correctly
[   18.616884] type=1400 audit(1380405131.896:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=728 comm="apparmor_parser"
[   18.616986] type=1400 audit(1380405131.896:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=729 comm="apparmor_parser"
[   18.617679] type=1400 audit(1380405131.896:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=728 comm="apparmor_parser"
[   18.617801] type=1400 audit(1380405131.896:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=729 comm="apparmor_parser"
[   18.618138] type=1400 audit(1380405131.896:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=728 comm="apparmor_parser"
[   18.618285] type=1400 audit(1380405131.896:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=729 comm="apparmor_parser"
[   19.861894] init: failsafe main process (793) killed by TERM signal
[   20.849287] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   21.261626] type=1400 audit(1380405134.544:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=887 comm="apparmor_parser"
[   21.262472] type=1400 audit(1380405134.544:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=887 comm="apparmor_parser"
[   21.262935] type=1400 audit(1380405134.544:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=887 comm="apparmor_parser"
[   21.483574] type=1400 audit(1380405134.768:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=886 comm="apparmor_parser"
[   21.694381] ppdev: user-space parallel port driver
[   21.751355] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   21.751365] vesafb: scrolling: redraw
[   21.751371] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   21.752223] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004980000, using 3072k, total 3072k
[   21.753585] Console: switching to colour frame buffer device 128x48
[   21.758960] fb0: VESA VGA frame buffer device
[   22.234036] Bluetooth: RFCOMM TTY layer initialized
[   22.234068] Bluetooth: RFCOMM socket layer initialized
[   22.234072] Bluetooth: RFCOMM ver 1.11
[   22.435466] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.435477] Bluetooth: BNEP filters: protocol multicast
[   22.435502] Bluetooth: BNEP socket layer initialized
[   27.704837] r8169 0000:07:00.0 eth0: link down
[   27.704927] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.705750] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.384901] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
[   35.386421] <6>[fglrx] Firegl kernel thread PID: 1389
[   35.386885] <6>[fglrx] Firegl kernel thread PID: 1390
[   35.387251] <6>[fglrx] Firegl kernel thread PID: 1391
[   35.387440] <6>[fglrx] IRQ 43 Enabled
[   35.393725] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   35.393731] <6>[fglrx] Reserved FB block: Unshared offset:fc14000, size:3ec000 
[   35.393736] <6>[fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
[   35.425357] <6>[fglrx] ATIF platform detected with notification ID: 0x81
[   50.584685] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   57.046280] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   57.189870] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   60.236178] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   60.242501] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   63.035831] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   63.036134] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   69.028864] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   75.017592] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   81.008783] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   86.999302] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   91.966990] audit_printk_skb: 51 callbacks suppressed
[   91.967002] type=1400 audit(1380405205.356:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2157 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   98.896494] cfg80211: Calling CRDA to update world regulatory domain



```

---

### Post by Pedro_Matias on 2013-09-29
Is this normal? xD

```
80211_get_station : Wrong Mac address[   57.046280] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   57.189870] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   60.236178] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   60.242501] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   63.035831] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   63.036134] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   69.028864] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   75.017592] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   81.008783] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   86.999302] ERROR @wl_cfg80211_get_station : Wrong Mac address
```

---

### Post by Pedro_Matias on 2013-09-30
Bump

---

### Post by heir4c on 2013-09-30
I have no wireless card, but maybe this helps you out:
[http://askubuntu.com/questions/249566/wrong-mac-address-error-in-virtual-console](http://askubuntu.com/questions/249566/wrong-mac-address-error-in-virtual-console)
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers)
Normally Ubuntu have 6.20 version. 
download-page for newer version (If you want to install a newer version):
[http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

Look also on this forum, there are more with this error.

---

### Post by Bucky Ball on 2013-09-30
This:

[   60.236178] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   60.242501] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.

Indicates an issue with the graphics, AMD/ATI I presume. Would depend on what you have installed as to what the problem is.

---

### Post by Pedro_Matias on 2013-09-30
> **heir4c said:**
> I have no wireless card, but maybe this helps you out:
[http://askubuntu.com/questions/249566/wrong-mac-address-error-in-virtual-console](http://askubuntu.com/questions/249566/wrong-mac-address-error-in-virtual-console)
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers)
Normally Ubuntu have 6.20 version. 
download-page for newer version (If you want to install a newer version):
[http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

Look also on this forum, there are more with this error.

I will try to install the wireless card drivers to see if the the problem with the wireless card disappears.

---

### Post by Pedro_Matias on 2013-09-30
> **Bucky Ball said:**
> This:

[   60.236178] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   60.242501] <3>[fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.

Indicates an issue with the graphics, AMD/ATI I presume. Would depend on what you have installed as to what the problem is.

Right now the driver I have installed. Is the "ATI/AMD proprietary FGLRX graphics driver (**experimental** beta)" from the aditional drivers.
I also had the "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" from the adtional drivers and I had the same error...

---

### Post by Pedro_Matias on 2013-09-30
Right now I think witd the "ATI/AMD proprietary FGLRX graphics driver (**experimental** beta)" the "apl initialize fail" is fixed, but I think I have an error with the Chromium and the graphic card.

Right now my output of my dmesg is this:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 (Ubuntu 3.8.0-31.46~precise1-generic 3.8.13.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b67f1e8f-2cca-4ea6-bb11-23b6eafd8938 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000df9befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df9bf000-0x00000000dfabefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dfabf000-0x00000000dfbbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dfbbf000-0x00000000dfbf4fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dfbf5000-0x00000000dfbfffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dfc00000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000106ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000107000000-0x000000011effffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dm1 Notebook PC/3387, BIOS F.19 02/04/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x107000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFBBD000 mask FFFFFF000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000011f000000 aka 4592M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdfc00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdfbfffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xdfbfffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdfbfffff @ [mem 0x1fffe000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x106ffffff]
[    0.000000]  [mem 0x100000000-0x106ffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x106ffffff @ [mem 0xdfbfe000-0xdfbfffff]
[    0.000000] RAMDISK: [mem 0x36104000-0x37079fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000dfbf4120 0007C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000dfbf3000 000F4 (v04 HPQOEM SLIC-MPC 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000dfbdf000 0F5D1 (v01 HP     INSYDE   F0000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000dfb86000 00040
[    0.000000] ACPI: HPET 00000000dfbf2000 00038 (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000dfbf1000 00084 (v02 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000dfbf0000 0003C (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 00000000dfbef000 000A5 (v32 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000dfbde000 00028 (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000dfbdd000 00176 (v01 HPQOEM SLIC-MPC 00000001 ACPI 00040000)
[    0.000000] ACPI: WDRT 00000000dfbdc000 00047 (v01 HP     INSYDE   00000000 ACPI 00040000)
[    0.000000] ACPI: WDAT 00000000dfbdb000 001AC (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000dfbda000 003DE (v01 HP     INSYDE   00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000dfbd8000 0168E (v02 HP     INSYDE   00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000106ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x106ffffff]
[    0.000000]   NODE_DATA [mem 0x106ffb000-0x106ffffff]
[    0.000000]  [ffffea0000000000-ffffea00041fffff] PMD -> [ffff880102c00000-ffff8801065fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x106ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xdf9befff]
[    0.000000]   node   0: [mem 0xdfbf5000-0xdfbfffff]
[    0.000000]   node   0: [mem 0x100000000-0x106ffffff]
[    0.000000] On node 0 totalpages: 944473
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14248 pages used for memmap
[    0.000000]   DMA32 zone: 897570 pages, LIFO batch:31
[    0.000000]   Normal zone: 448 pages used for memmap
[    0.000000]   Normal zone: 28224 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df9bf000 - 00000000dfabf000
[    0.000000] PM: Registered nosave memory: 00000000dfabf000 - 00000000dfbbf000
[    0.000000] PM: Registered nosave memory: 00000000dfbbf000 - 00000000dfbf5000
[    0.000000] PM: Registered nosave memory: 00000000dfc00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880106c00000 s84928 r8192 d21568 u524288
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 929707
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b67f1e8f-2cca-4ea6-bb11-23b6eafd8938 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3620328k/4308992k available (7171k kernel code, 531100k absent, 157564k reserved, 6072k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 15204352 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1646.476 MHz processor
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3292.95 BogoMIPS (lpj=6585904)
[    0.000014] pid_max: default: 32768 minimum: 301
[    0.000063] Security Framework initialized
[    0.000088] AppArmor: AppArmor initialized
[    0.000090] Yama: becoming mindful.
[    0.000724] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003355] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004531] Mount-cache hash table entries: 256
[    0.004891] Initializing cgroup subsys cpuacct
[    0.004901] Initializing cgroup subsys memory
[    0.004917] Initializing cgroup subsys devices
[    0.004921] Initializing cgroup subsys freezer
[    0.004924] Initializing cgroup subsys blkio
[    0.004926] Initializing cgroup subsys perf_event
[    0.004931] Initializing cgroup subsys hugetlb
[    0.004980] tseg: 00dfc00000
[    0.004985] CPU: Physical Processor ID: 0
[    0.004987] CPU: Processor Core ID: 0
[    0.004991] mce: CPU supports 6 MCE banks
[    0.005010] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005010] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005010] tlb_flushall_shift: 5
[    0.005237] Freeing SMP alternatives: 24k freed
[    0.009959] ACPI: Core revision 20121018
[    0.024739] ftrace: allocating 29359 entries in 115 pages
[    1.064958] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.104595] smpboot: CPU0: AMD E-450 APU with Radeon(tm) HD Graphics (fam: 14, model: 02, stepping: 00)
[    1.209379] Performance Events: AMD PMU driver.
[    1.209389] ... version:                0
[    1.209392] ... bit width:              48
[    1.209394] ... generic registers:      4
[    1.209397] ... value mask:             0000ffffffffffff
[    1.209399] ... max period:             00007fffffffffff
[    1.209402] ... fixed-purpose events:   0
[    1.209404] ... event mask:             000000000000000f
[    1.211921] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    1.212137] smpboot: Booting Node   0, Processors  #1
[    1.225316] Brought up 2 CPUs
[    1.225321] smpboot: Total of 2 processors activated (6585.90 BogoMIPS)
[    1.226491] devtmpfs: initialized
[    1.229204] EVM: security.selinux
[    1.229208] EVM: security.SMACK64
[    1.229210] EVM: security.capability
[    1.229606] PM: Registering ACPI NVS region [mem 0xdfabf000-0xdfbbefff] (1048576 bytes)
[    1.231613] regulator-dummy: no parameters
[    1.231728] NET: Registered protocol family 16
[    1.232188] ACPI: bus type pci registered
[    1.232393] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    1.232399] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    1.238546] PCI: Using configuration type 1 for base access
[    1.240901] bio: create slab <bio-0> at 0
[    1.241366] ACPI: Added _OSI(Module Device)
[    1.241392] ACPI: Added _OSI(Processor Device)
[    1.241395] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.241399] ACPI: Added _OSI(Processor Aggregator Device)
[    1.244208] ACPI: EC: Look up EC in DSDT
[    1.247103] ACPI: Executed 1 blocks of module-level executable AML code
[    1.253042] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.354914] ACPI: Interpreter enabled
[    1.354930] ACPI: (supports S0 S3 S4 S5)
[    1.354979] ACPI: Using IOAPIC for interrupt routing
[    1.762552] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    1.762836] ACPI: No dock devices found.
[    1.762847] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.765112] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.765123] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.765805] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce3ff])
[    1.765819] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.765896] PCI host bridge to bus 0000:00
[    1.765903] pci_bus 0000:00: root bus resource [bus 00-ff]
[    1.765909] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.765913] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.765918] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.765922] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.765926] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.765930] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.765934] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.765938] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.765941] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.765945] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.765949] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.765953] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.765957] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    1.765961] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    1.765965] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xf7ffffff]
[    1.765969] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    1.765973] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    1.765989] pci 0000:00:00.0: [1022:1510] type 00 class 0x060000
[    1.766053] pci 0000:00:01.0: [1002:9806] type 00 class 0x030000
[    1.766069] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    1.766080] pci 0000:00:01.0: reg 14: [io  0x4000-0x40ff]
[    1.766091] pci 0000:00:01.0: reg 18: [mem 0xf0300000-0xf033ffff]
[    1.766155] pci 0000:00:01.0: supports D1 D2
[    1.766181] pci 0000:00:01.1: [1002:1314] type 00 class 0x040300
[    1.766195] pci 0000:00:01.1: reg 10: [mem 0xf0344000-0xf0347fff]
[    1.766271] pci 0000:00:01.1: supports D1 D2
[    1.766305] pci 0000:00:04.0: [1022:1512] type 01 class 0x060400
[    1.766400] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.766528] pci 0000:00:11.0: [1002:4394] type 00 class 0x010601
[    1.766555] pci 0000:00:11.0: reg 10: [io  0x4118-0x411f]
[    1.766570] pci 0000:00:11.0: reg 14: [io  0x4124-0x4127]
[    1.766584] pci 0000:00:11.0: reg 18: [io  0x4110-0x4117]
[    1.766598] pci 0000:00:11.0: reg 1c: [io  0x4120-0x4123]
[    1.766612] pci 0000:00:11.0: reg 20: [io  0x4100-0x410f]
[    1.766627] pci 0000:00:11.0: reg 24: [mem 0xf034e000-0xf034e3ff]
[    1.766710] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    1.766730] pci 0000:00:12.0: reg 10: [mem 0xf034d000-0xf034dfff]
[    1.766829] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    1.767363] pci 0000:00:12.2: reg 10: [mem 0xf034c000-0xf034c0ff]
[    1.770341] pci 0000:00:12.2: supports D1 D2
[    1.770346] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.770383] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    1.770404] pci 0000:00:13.0: reg 10: [mem 0xf034b000-0xf034bfff]
[    1.770509] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    1.770998] pci 0000:00:13.2: reg 10: [mem 0xf034a000-0xf034a0ff]
[    1.773860] pci 0000:00:13.2: supports D1 D2
[    1.773865] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.773901] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    1.774013] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    1.774044] pci 0000:00:14.2: reg 10: [mem 0xf0340000-0xf0343fff 64bit]
[    1.774135] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.774159] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    1.774266] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    1.774342] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
[    1.774452] pci 0000:00:15.0: supports D1 D2
[    1.774490] pci 0000:00:15.1: [1002:43a1] type 01 class 0x060400
[    1.774599] pci 0000:00:15.1: supports D1 D2
[    1.774642] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    1.774663] pci 0000:00:16.0: reg 10: [mem 0xf0349000-0xf0349fff]
[    1.774768] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    1.775254] pci 0000:00:16.2: reg 10: [mem 0xf0348000-0xf03480ff]
[    1.778116] pci 0000:00:16.2: supports D1 D2
[    1.778120] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    1.778157] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
[    1.778209] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
[    1.778255] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
[    1.778304] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
[    1.778365] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
[    1.778411] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
[    1.778457] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
[    1.778507] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
[    1.778659] pci 0000:00:04.0: PCI bridge to [bus 01]
[    1.778796] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    1.778809] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.778814] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.778818] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.778822] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    1.778826] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    1.778830] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    1.778834] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.778838] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.778842] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.778846] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.778850] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    1.778854] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    1.778858] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    1.778862] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    1.778866] pci 0000:00:14.4:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    1.778870] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    1.778874] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    1.779025] pci 0000:03:00.0: [14e4:4727] type 00 class 0x028000
[    1.779059] pci 0000:03:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    1.779227] pci 0000:03:00.0: supports D1 D2
[    1.784791] pci 0000:00:15.0: PCI bridge to [bus 03-06]
[    1.784809] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    1.784818] pci 0000:00:15.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    1.784828] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.784944] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    1.784973] pci 0000:07:00.0: reg 10: [io  0x2000-0x20ff]
[    1.785014] pci 0000:07:00.0: reg 18: [mem 0xf0104000-0xf0104fff 64bit pref]
[    1.785040] pci 0000:07:00.0: reg 20: [mem 0xf0100000-0xf0103fff 64bit pref]
[    1.785154] pci 0000:07:00.0: supports D1 D2
[    1.785158] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.792779] pci 0000:00:15.1: PCI bridge to [bus 07]
[    1.792797] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    1.792811] pci 0000:00:15.1:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    1.792877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.VGA_._PRT]
[    1.792976] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    1.793063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    1.793131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT]
[    1.793204] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AZAL._PRT]
[    1.793305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.793644]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.794179]  pci0000:00: ACPI _OSC control (0x19) granted
[    1.796742] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.796979] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797095] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797210] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797305] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797381] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797456] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797531] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.797944] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    1.797963] vgaarb: loaded
[    1.797965] vgaarb: bridge control possible 0000:00:01.0
[    1.798364] SCSI subsystem initialized
[    1.798370] ACPI: bus type scsi registered
[    1.798681] libata version 3.00 loaded.
[    1.798744] ACPI: bus type usb registered
[    1.798802] usbcore: registered new interface driver usbfs
[    1.798820] usbcore: registered new interface driver hub
[    1.799105] usbcore: registered new device driver usb
[    1.799721] PCI: Using ACPI for IRQ routing
[    1.802421] PCI: pci_cache_line_size set to 64 bytes
[    1.802553] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    1.802559] e820: reserve RAM buffer [mem 0xdf9bf000-0xdfffffff]
[    1.802562] e820: reserve RAM buffer [mem 0xdfc00000-0xdfffffff]
[    1.802566] e820: reserve RAM buffer [mem 0x107000000-0x107ffffff]
[    1.802795] NetLabel: Initializing
[    1.802798] NetLabel:  domain hash size = 128
[    1.802800] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.802821] NetLabel:  unlabeled traffic allowed by default
[    1.803040] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.803054] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.805107] Switching to clocksource hpet
[    1.816025] AppArmor: AppArmor Filesystem Enabled
[    1.816089] pnp: PnP ACPI init
[    1.816118] ACPI: bus type pnp registered
[    1.816390] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.816397] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    1.816406] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.816801] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.816873] pnp 00:02: [dma 4]
[    1.816912] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.817002] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.817097] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.817147] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.817250] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.817391] pnp 00:07: Plug and Play ACPI device, IDs SYN1e50 PNP0f13 (active)
[    1.817483] system 00:08: [io  0x0400-0x04cf] has been reserved
[    1.817488] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    1.817492] system 00:08: [io  0x04d6] has been reserved
[    1.817497] system 00:08: [io  0x0680-0x06ff] has been reserved
[    1.817501] system 00:08: [io  0x077a] has been reserved
[    1.817505] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    1.817509] system 00:08: [io  0x0c14] has been reserved
[    1.817513] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    1.817518] system 00:08: [io  0x0c6c] has been reserved
[    1.817522] system 00:08: [io  0x0c6f] has been reserved
[    1.817526] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    1.817530] system 00:08: [io  0x0380-0x0387] has been reserved
[    1.817536] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.817678] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    1.817683] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    1.817689] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.818245] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
[    2.018267] pnp: PnP ACPI: found 11 devices
[    2.018277] ACPI: ACPI bus type pnp unregistered
[    2.028884] pci 0000:00:04.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    2.028897] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    2.028903] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    2.028941] pci 0000:00:04.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    2.028946] pci 0000:00:04.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    2.028951] pci 0000:00:04.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    2.028965] pci 0000:00:04.0: BAR 14: assigned [mem 0xf0400000-0xf05fffff]
[    2.028976] pci 0000:00:04.0: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
[    2.028982] pci 0000:00:04.0: BAR 13: assigned [io  0x1000-0x1fff]
[    2.028988] pci 0000:00:04.0: PCI bridge to [bus 01]
[    2.028995] pci 0000:00:04.0:   bridge window [io  0x1000-0x1fff]
[    2.029003] pci 0000:00:04.0:   bridge window [mem 0xf0400000-0xf05fffff]
[    2.029009] pci 0000:00:04.0:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
[    2.029017] pci 0000:00:14.4: PCI bridge to [bus 02]
[    2.029104] pci 0000:00:15.0: PCI bridge to [bus 03-06]
[    2.029110] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    2.029118] pci 0000:00:15.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    2.029125] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    2.029134] pci 0000:00:15.1: PCI bridge to [bus 07]
[    2.029140] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    2.029150] pci 0000:00:15.1:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    2.029214] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.029219] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.029223] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.029227] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.029231] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.029235] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.029239] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.029243] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.029246] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.029250] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    2.029254] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.029258] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.029262] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.029266] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    2.029270] pci_bus 0000:00: resource 18 [mem 0xe0000000-0xf7ffffff]
[    2.029273] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xfed3ffff]
[    2.029277] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    2.029282] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    2.029286] pci_bus 0000:01: resource 1 [mem 0xf0400000-0xf05fffff]
[    2.029290] pci_bus 0000:01: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
[    2.029294] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    2.029298] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    2.029302] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    2.029306] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.029309] pci_bus 0000:02: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.029313] pci_bus 0000:02: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.029317] pci_bus 0000:02: resource 10 [mem 0x000d0000-0x000d3fff]
[    2.029321] pci_bus 0000:02: resource 11 [mem 0x000d4000-0x000d7fff]
[    2.029325] pci_bus 0000:02: resource 12 [mem 0x000d8000-0x000dbfff]
[    2.029329] pci_bus 0000:02: resource 13 [mem 0x000dc000-0x000dffff]
[    2.029333] pci_bus 0000:02: resource 14 [mem 0x000e0000-0x000e3fff]
[    2.029336] pci_bus 0000:02: resource 15 [mem 0x000e4000-0x000e7fff]
[    2.029340] pci_bus 0000:02: resource 16 [mem 0x000e8000-0x000ebfff]
[    2.029344] pci_bus 0000:02: resource 17 [mem 0x000ec000-0x000effff]
[    2.029348] pci_bus 0000:02: resource 18 [mem 0xe0000000-0xf7ffffff]
[    2.029352] pci_bus 0000:02: resource 19 [mem 0xfc000000-0xfed3ffff]
[    2.029356] pci_bus 0000:02: resource 20 [mem 0xfed45000-0xffffffff]
[    2.029360] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    2.029364] pci_bus 0000:03: resource 1 [mem 0xf0200000-0xf02fffff]
[    2.029368] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    2.029372] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    2.029376] pci_bus 0000:07: resource 2 [mem 0xf0100000-0xf01fffff 64bit pref]
[    2.029440] NET: Registered protocol family 2
[    2.029756] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    2.030100] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    2.030375] TCP: Hash tables configured (established 32768 bind 32768)
[    2.030473] TCP: reno registered
[    2.030506] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.030558] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.030741] NET: Registered protocol family 1
[    2.030777] pci 0000:00:01.0: Boot video device
[    2.808061] PCI: CLS 64 bytes, default 64
[    2.808171] Trying to unpack rootfs image as initramfs...
[    3.313504] Freeing initrd memory: 15832k freed
[    3.322683] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.322695] software IO TLB [mem 0xdb9bf000-0xdf9bf000] (64MB) mapped at [ffff8800db9bf000-ffff8800df9befff]
[    3.322866] Simple Boot Flag at 0x44 set to 0x1
[    3.323084] LVT offset 0 assigned for vector 0x400
[    3.323239] perf: AMD IBS detected (0x000000ff)
[    3.323818] Initialise module verification
[    3.323923] audit: initializing netlink socket (disabled)
[    3.323945] type=2000 audit(1380551191.200:1): initialized
[    3.371479] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.375682] VFS: Disk quotas dquot_6.5.2
[    3.375796] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.377092] fuse init (API version 7.20)
[    3.377345] msgmni has been set to 7101
[    3.378397] Key type asymmetric registered
[    3.378405] Asymmetric key parser 'x509' registered
[    3.378502] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.378630] io scheduler noop registered
[    3.378639] io scheduler deadline registered (default)
[    3.378662] io scheduler cfq registered
[    3.379044] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    3.379364] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.379514] pciehp 0000:00:04.0:pcie04: HPC vendor_id 1022 device_id 1512 ss_vid 1022 ss_did 1234
[    3.379580] pciehp 0000:00:04.0:pcie04: service driver pciehp loaded
[    3.379590] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.531304] ACPI: AC Adapter [ACAD] (off-line)
[    3.531542] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.531553] ACPI: Power Button [PWRB]
[    3.531653] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    3.532280] ACPI: Lid Switch [LID]
[    3.532392] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.532398] ACPI: Power Button [PWRF]
[    3.532719] ACPI: acpi_idle registered with cpuidle
[    3.945319] thermal LNXTHERM:00: registered as thermal_zone0
[    3.945328] ACPI: Thermal Zone [THRM] (59 C)
[    3.945409] GHES: HEST is not enabled!
[    3.945708] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.951618] Linux agpgart interface v0.103
[    3.956064] brd: module loaded
[    3.958421] loop: module loaded
[    3.959118] libphy: Fixed MDIO Bus: probed
[    3.959239] tun: Universal TUN/TAP device driver, 1.6
[    3.959243] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.959561] PPP generic driver version 2.4.2
[    3.959753] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.959757] ehci-pci: EHCI PCI platform driver
[    3.959912] ehci-pci 0000:00:12.2: EHCI Host Controller
[    3.959925] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.959947] QUIRK: Enable AMD PLL fix
[    3.959951] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.960040] ehci-pci 0000:00:12.2: debug port 1
[    3.960106] ehci-pci 0000:00:12.2: irq 17, io mem 0xf034c000
[    3.970131] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.970202] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.970209] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.970213] usb usb1: Product: EHCI Host Controller
[    3.970217] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    3.970221] usb usb1: SerialNumber: 0000:00:12.2
[    3.970780] hub 1-0:1.0: USB hub found
[    3.970798] hub 1-0:1.0: 5 ports detected
[    3.971233] ehci-pci 0000:00:13.2: EHCI Host Controller
[    3.971245] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.971256] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.971274] ehci-pci 0000:00:13.2: debug port 1
[    3.971325] ehci-pci 0000:00:13.2: irq 17, io mem 0xf034a000
[    3.982254] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.982316] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    3.982323] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.982327] usb usb2: Product: EHCI Host Controller
[    3.982331] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    3.982335] usb usb2: SerialNumber: 0000:00:13.2
[    3.982827] hub 2-0:1.0: USB hub found
[    3.982842] hub 2-0:1.0: 5 ports detected
[    3.983296] ehci-pci 0000:00:16.2: EHCI Host Controller
[    3.983308] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    3.983319] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    3.983337] ehci-pci 0000:00:16.2: debug port 1
[    3.983386] ehci-pci 0000:00:16.2: irq 17, io mem 0xf0348000
[    3.994236] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    3.994299] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    3.994305] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.994310] usb usb3: Product: EHCI Host Controller
[    3.994314] usb usb3: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    3.994318] usb usb3: SerialNumber: 0000:00:16.2
[    3.994836] hub 3-0:1.0: USB hub found
[    3.994852] hub 3-0:1.0: 4 ports detected
[    3.995253] ehci-platform: EHCI generic platform driver
[    3.995272] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.995415] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.995427] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    3.995479] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf034d000
[    4.054163] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    4.054173] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.054177] usb usb4: Product: OHCI Host Controller
[    4.054182] usb usb4: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    4.054185] usb usb4: SerialNumber: 0000:00:12.0
[    4.054681] hub 4-0:1.0: USB hub found
[    4.054767] hub 4-0:1.0: 5 ports detected
[    4.055094] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.055110] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    4.055143] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf034b000
[    4.114062] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    4.114072] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.114077] usb usb5: Product: OHCI Host Controller
[    4.114081] usb usb5: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    4.114085] usb usb5: SerialNumber: 0000:00:13.0
[    4.114545] hub 5-0:1.0: USB hub found
[    4.114608] hub 5-0:1.0: 5 ports detected
[    4.114892] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    4.114905] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    4.114939] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf0349000
[    4.154291] ACPI: Battery Slot [BAT0] (battery present)
[    4.174059] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    4.174069] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.174073] usb usb6: Product: OHCI Host Controller
[    4.174077] usb usb6: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    4.174081] usb usb6: SerialNumber: 0000:00:16.0
[    4.174616] hub 6-0:1.0: USB hub found
[    4.174701] hub 6-0:1.0: 4 ports detected
[    4.174988] uhci_hcd: USB Universal Host Controller Interface driver
[    4.175133] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.179777] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.179790] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.180518] mousedev: PS/2 mouse device common for all mice
[    4.181674] rtc_cmos 00:04: RTC can wake from S4
[    4.181850] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.181962] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    4.182143] device-mapper: uevent: version 1.0.3
[    4.182396] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    4.182544] cpuidle: using governor ladder
[    4.182682] cpuidle: using governor menu
[    4.182691] ledtrig-cpu: registered to indicate activity on CPUs
[    4.182694] EFI Variables Facility v0.08 2004-May-17
[    4.183374] ashmem: initialized
[    4.183693] TCP: cubic registered
[    4.183871] NET: Registered protocol family 10
[    4.184182] NET: Registered protocol family 17
[    4.184213] Key type dns_resolver registered
[    4.185068] Loading module verification certificates
[    4.187491] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: ef66b5fef7cf2d982f954bc9bd9879a3cb821073'
[    4.187523] registered taskstats version 1
[    4.193318] Key type trusted registered
[    4.198102] Key type encrypted registered
[    4.204596] rtc_cmos 00:04: setting system clock to 2013-09-30 14:26:34 UTC (1380551194)
[    4.204749] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    4.207529] acpi-cpufreq: overriding BIOS provided _PSD data
[    4.207779] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.207782] EDD information not available.
[    4.211110] Freeing unused kernel memory: 1012k freed
[    4.211660] Write protecting the kernel read-only data: 12288k
[    4.218345] Freeing unused kernel memory: 1012k freed
[    4.225279] Freeing unused kernel memory: 1008k freed
[    4.250304] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.274650] udevd[96]: starting version 175
[    4.281637] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    4.317688] tsc: Refined TSC clocksource calibration: 1646.493 MHz
[    4.317703] Switching to clocksource tsc
[    4.461472] usb 1-3: New USB device found, idVendor=064e, idProduct=d217
[    4.461482] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.461487] usb 1-3: Product: HP TrueVision HD
[    4.461491] usb 1-3: Manufacturer: SuYin
[    4.461495] usb 1-3: SerialNumber: HF1016-A821-OV03-VH-R02.09.02
[    4.483711] Disabling lock debugging due to kernel taint
[    4.484904] ahci 0000:00:11.0: version 3.0
[    4.485125] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    4.485132] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    4.492986] scsi0 : ahci
[    4.511120] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.511556] r8169 0000:07:00.0: irq 41 for MSI/MSI-X
[    4.511935] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000066a000, 80:c1:6e:49:47:50, XID 0c900800 IRQ 41
[    4.511941] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    4.573945] ata1: SATA max UDMA/133 abar m1024@0xf034e000 port 0xf034e100 irq 19
[    4.988875] usb 6-1: new full-speed USB device number 2 using ohci_hcd
[    5.064707] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.066458] ata1.00: ATA-8: Hitachi HTS545050B9A300, PB4OCA1G, max UDMA/100
[    5.066469] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.067996] ata1.00: configured for UDMA/100
[    5.068439] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 PB4O PQ: 0 ANSI: 5
[    5.068801] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.068927] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.069045] sd 0:0:0:0: [sda] Write Protect is off
[    5.069051] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.069097] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.125181]  sda: sda1 sda2 < sda5 >
[    5.126524] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.163680] usb 6-1: New USB device found, idVendor=0a5c, idProduct=21e3
[    5.163696] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.163704] usb 6-1: Product: BCM20702A0
[    5.163712] usb 6-1: Manufacturer: Broadcom Corp
[    5.163720] usb 6-1: SerialNumber: 642737C270DA
[    5.398044] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.398054] EXT4-fs (sda1): write access will be enabled during recovery
[    6.703899] EXT4-fs (sda1): orphan cleanup on readonly fs
[    6.703930] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 412207
[    6.703997] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 412128
[    6.704013] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 412028
[    6.704029] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 400273
[    6.704047] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 18350099
[    6.704064] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 18350097
[    6.704177] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623430
[    6.704204] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623432
[    6.704246] EXT4-fs (sda1): 8 orphan inodes deleted
[    6.704250] EXT4-fs (sda1): recovery complete
[    6.854872] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.420489] init: ureadahead main process (246) terminated with status 5
[    9.493965] Adding 3776508k swap on /dev/sda5.  Priority:-1 extents:1 across:3776508k 
[   10.829182] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.288269] udevd[323]: starting version 175
[   12.736943] lp: driver loaded but no devices found
[   13.065697] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.332311] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   13.332319] AMD IOMMUv2 functionality not available on this system
[   13.370956] wmi: Mapper loaded
[   13.727835] acpi device:00: registered as cooling_device2
[   13.727928] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.728189] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   13.922015] input: HP WMI hotkeys as /devices/virtual/input/input5
[   13.924873] microcode: CPU0: patch_level=0x05000101
[   13.982457] hp_accel: laptop model unknown, using default axes configuration
[   13.986813] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.992878] lis3lv02d: 8 bits 3DC sensor found
[   14.031485] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   14.105997] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   14.106164] sp5100_tco: PCI Revision ID: 0x42
[   14.106275] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   14.106289] sp5100_tco: Last reboot was not triggered by watchdog.
[   14.108024] sp5100_tco: initialized (0xffffc9000067ab00). heartbeat=60 sec (nowayout=0)
[   14.141557] microcode: CPU0: new patch_level=0x05000119
[   14.141592] microcode: CPU1: patch_level=0x05000101
[   14.147698] microcode: CPU1: new patch_level=0x05000119
[   14.148364] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.375474] lib80211: common routines for IEEE802.11 drivers
[   14.375483] lib80211_crypt: registered algorithm 'NULL'
[   14.549069] cfg80211: Calling CRDA to update world regulatory domain
[   14.549772] kvm: Nested Virtualization enabled
[   14.549786] kvm: Nested Paging enabled
[   15.235406] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1679, fw id: 724542
[   15.277916] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   15.429517] Linux video capture interface: v2.00
[   15.528537] Bluetooth: Core ver 2.16
[   15.528587] NET: Registered protocol family 31
[   15.528591] Bluetooth: HCI device and connection manager initialized
[   15.529038] Bluetooth: HCI socket layer initialized
[   15.529048] Bluetooth: L2CAP socket layer initialized
[   15.529061] Bluetooth: SCO socket layer initialized
[   15.980612] uvcvideo: Found UVC 1.00 device HP TrueVision HD (064e:d217)
[   15.986045] input: HP TrueVision HD as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input8
[   15.986430] usbcore: registered new interface driver uvcvideo
[   15.986435] USB Video Class driver (1.1.1)
[   16.048165] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[   16.102184] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   16.136982] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.225964] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   16.226408] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   17.135322] usbcore: registered new interface driver btusb
[   17.139347] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   17.181303] lib80211_crypt: registered algorithm 'TKIP'
[   17.433299] Bluetooth: can't load firmware, may not work correctly
[   17.783078] <6>[fglrx] Maximum main memory to use for locked dma buffers: 3398 MBytes.
[   17.783321] <6>[fglrx]   vendor: 1002 device: 9806 count: 1
[   17.783982] <6>[fglrx] ioport: bar 1, base 0x4000, size: 0x100
[   17.784461] <6>[fglrx] Kernel PAT support is enabled
[   17.784503] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[   18.197929] type=1400 audit(1380551208.510:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[   18.198024] type=1400 audit(1380551208.510:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=685 comm="apparmor_parser"
[   18.198567] type=1400 audit(1380551208.510:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   18.198689] type=1400 audit(1380551208.510:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[   18.198933] type=1400 audit(1380551208.510:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[   18.199076] type=1400 audit(1380551208.510:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[   19.027335] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   19.849757] init: failsafe main process (773) killed by TERM signal
[   21.117727] type=1400 audit(1380551211.434:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=872 comm="apparmor_parser"
[   21.118410] type=1400 audit(1380551211.434:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=872 comm="apparmor_parser"
[   21.118780] type=1400 audit(1380551211.434:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=872 comm="apparmor_parser"
[   21.441626] type=1400 audit(1380551211.758:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=871 comm="apparmor_parser"
[   21.889555] ppdev: user-space parallel port driver
[   21.964989] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   21.964997] vesafb: scrolling: redraw
[   21.965002] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   21.965643] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004880000, using 3072k, total 3072k
[   21.966011] Console: switching to colour frame buffer device 128x48
[   21.970318] fb0: VESA VGA frame buffer device
[   22.469537] Bluetooth: RFCOMM TTY layer initialized
[   22.469563] Bluetooth: RFCOMM socket layer initialized
[   22.469566] Bluetooth: RFCOMM ver 1.11
[   22.904151] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.904160] Bluetooth: BNEP filters: protocol multicast
[   22.904177] Bluetooth: BNEP socket layer initialized
[   27.980432] r8169 0000:07:00.0 eth0: link down
[   27.980514] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.981204] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.113571] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
[   37.114733] <6>[fglrx] Firegl kernel thread PID: 1479
[   37.114914] <6>[fglrx] Firegl kernel thread PID: 1480
[   37.115277] <6>[fglrx] Firegl kernel thread PID: 1481
[   37.115479] <6>[fglrx] IRQ 43 Enabled
[   37.120556] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   37.120561] <6>[fglrx] Reserved FB block: Unshared offset:fc14000, size:3ec000 
[   37.120565] <6>[fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
[   37.174886] <6>[fglrx] ATIF platform detected with notification ID: 0x81
[   91.019167] audit_printk_skb: 51 callbacks suppressed
[   91.019176] type=1400 audit(1380551282.348:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2138 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  205.815027] chromium-browse[2696]: segfault at 44 ip 00007f6914e6051f sp 00007fff81bf5e60 error 4 in fglrx_dri.so[7f6914125000+1d9a000]
[  207.871559] chromium-browse[2709]: segfault at 44 ip 00007ff10352e51f sp 00007fff02c4f040 error 4 in fglrx_dri.so[7ff1027f3000+1d9a000]
[  209.619346] chromium-browse[2720]: segfault at 44 ip 00007f25dd83751f sp 00007fffc372dd40 error 4 in fglrx_dri.so[7f25dcafc000+1d9a000]
[  927.421820] type=1400 audit(1380552120.000:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=958 comm="cupsd" pid=958 comm="cupsd" capability=36  capname="block_suspend"
```

And if I do ```
 dmesg | grep fglrx
```

This is my output:

```
[   17.783078] <6>[fglrx] Maximum main memory to use for locked dma buffers: 3398 MBytes.
[   17.783321] <6>[fglrx]   vendor: 1002 device: 9806 count: 1
[   17.783982] <6>[fglrx] ioport: bar 1, base 0x4000, size: 0x100
[   17.784461] <6>[fglrx] Kernel PAT support is enabled
[   17.784503] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[   37.113571] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
[   37.114733] <6>[fglrx] Firegl kernel thread PID: 1479
[   37.114914] <6>[fglrx] Firegl kernel thread PID: 1480
[   37.115277] <6>[fglrx] Firegl kernel thread PID: 1481
[   37.115479] <6>[fglrx] IRQ 43 Enabled
[   37.120556] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   37.120561] <6>[fglrx] Reserved FB block: Unshared offset:fc14000, size:3ec000 
[   37.120565] <6>[fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
[   37.174886] <6>[fglrx] ATIF platform detected with notification ID: 0x81
[  205.815027] chromium-browse[2696]: segfault at 44 ip 00007f6914e6051f sp 00007fff81bf5e60 error 4 in fglrx_dri.so[7f6914125000+1d9a000]
[  207.871559] chromium-browse[2709]: segfault at 44 ip 00007ff10352e51f sp 00007fff02c4f040 error 4 in fglrx_dri.so[7ff1027f3000+1d9a000]
[  209.619346] chromium-browse[2720]: segfault at 44 ip 00007f25dd83751f sp 00007fffc372dd40 error 4 in fglrx_dri.so[7f25dcafc000+1d9a000]

```

I think this:

```
 [  205.815027] chromium-browse[2696]: segfault at 44 ip 00007f6914e6051f sp 00007fff81bf5e60 error 4 in fglrx_dri.so[7f6914125000+1d9a000][  207.871559] chromium-browse[2709]: segfault at 44 ip 00007ff10352e51f sp 00007fff02c4f040 error 4 in fglrx_dri.so[7ff1027f3000+1d9a000]
[  209.619346] chromium-browse[2720]: segfault at 44 ip 00007f25dd83751f sp 00007fffc372dd40 error 4 in fglrx_dri.so[7f25dcafc000+1d9a000]
```

is the problem cause usualy the computer freezes in the Chromium....

I think

---

### Post by heir4c on 2013-09-30
It's only with chromium or also with FireFox (or another browser) ?

---

### Post by Pedro_Matias on 2013-09-30
I don't have annother browser cause I uninstalled firefox, because I wanted my bookmarks. You think I sould try firefox?

---

### Post by Pedro_Matias on 2013-09-30
Can someone help me with the manual installing of the Broadcom wireless drivers from their website? Their drivers come compressed in tar.gz and I don't know how to install them...

---

### Post by heir4c on 2013-09-30
> **Pedro_Matias said:**
> I don't have annother browser cause I uninstalled firefox, because I wanted my bookmarks. You think I sould try firefox?

Maybe, just to test it.
Or reïnstall Chromium. (?)

---

### Post by Bucky Ball on 2013-09-30
Switch off the video drivers in Additional Drivers, reboot and that will probably fix the Error 11. Like I said, that seems to be related to fglrx.

---

### Post by Pedro_Matias on 2013-09-30
> **Bucky Ball said:**
> Switch off the video drivers in Additional Drivers, reboot and that will probably fix the Error 11. Like I said, that seems to be related to fglrx.

So your suggestion is that I don't use any Additional Drivers?

---

### Post by Pedro_Matias on 2013-09-30
I uninstalled chromium and installed chrome to see if the problem stands with the chrome...

Now with chrome i just get one error:

```
[  445.140063] chrome[3128]: segfault at 44 ip 00007f19d272351f sp 00007fff30eee6a0 error 4 in fglrx_dri.so[7f19d19e8000+1d9a000]
```

And I don't know why, cause I haven't installed the Broadcom drivers that I downloaded ( they are tar.gz files and I don't know how to install them ), but the "wrong MAC address" error has disappeared...

---

### Post by Pedro_Matias on 2013-09-30
Everytime e turn on my computer, before the screen saying Ubuntu appears, I always get a black screen saying "[   17.938110] INFO @wl_cfg80211_attach : Registered CFG80211 phy" don't know why

---

### Post by heir4c on 2013-09-30
Like Bucky Ball saying: first deal with the graphic driver and than (I guess) the message will disappear. I read this in a (Dutch) tread. It's just INFO not a Error or Warning.

---

### Post by Pedro_Matias on 2013-09-30
> **heir4c said:**
> Like Bucky Ball saying: first deal with the graphic driver and than (I guess) the message will disappear. I read this in a (Dutch) tread. It's just INFO not a Error or Warning.

So what should I do now? Switch off the additional drivers for the video card?

---

### Post by Bucky Ball on 2013-10-01
> **Pedro_Matias said:**
> So what should I do now? Switch off the additional drivers for the video card?

Not sure if we can make this any clearer ... YES!

---

### Post by Pedro_Matias on 2013-10-01
Ok I did it, I switched off the additional drivers.

Let's see if the freezes disspeared...

---

### Post by Bucky Ball on 2013-10-01
Make sure to restart.

---

### Post by Pedro_Matias on 2013-10-01
It countinues freezing.... Maybe it's something with the wireless card?

---

### Post by Bucky Ball on 2013-10-01
[QUOTE=Bucky]Switch off the video drivers in Additional Drivers, reboot and that will probably fix the Error 11.[/QUOTE]

Did it fix Error 11? That is what we want to know for now and that is why we asked you to do it. 

Could you please give the full details of what you try and the outcome in the one post before moving on? It will make it easier to help.

---

### Post by Gyokuro on 2013-10-01
Hi

As some member already pointed you to your problems - you should disable all your closed source drivers:

1.) frglx => for your graphic card
2.) wireless driver

reboot and look whether your box is freezing. If it is freezing again - check whether it is cooled enough and I have noticed after I have checked your dmesg file you have a lot of messages like this:

 6.050115] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3146959
[    6.050778] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147160
[    6.050886] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147158
[    6.050916] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147156

I have snipped the rest but are you sure that your hard disk is ok? A lot of freezes can happen if the system/kernel write/read data to/of your disk and the disk is damaged.

---

### Post by Pedro_Matias on 2013-10-01
> **Bucky Ball said:**
> Did it fix Error 11? That is what we want to know for now and that is why we asked you to do it. 

Could you please give the full details of what you try and the outcome in the one post before moving on? It will make it easier to help.

Yes, I guess.


Right now this is my output for dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 (Ubuntu 3.8.0-31.46~precise1-generic 3.8.13.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b67f1e8f-2cca-4ea6-bb11-23b6eafd8938 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000df9befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df9bf000-0x00000000dfabefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dfabf000-0x00000000dfbbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dfbbf000-0x00000000dfbf4fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dfbf5000-0x00000000dfbfffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dfc00000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000106ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000107000000-0x000000011effffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dm1 Notebook PC/3387, BIOS F.19 02/04/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x107000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFBBD000 mask FFFFFF000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000011f000000 aka 4592M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdfc00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdfbfffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xdfbfffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdfbfffff @ [mem 0x1fffe000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x106ffffff]
[    0.000000]  [mem 0x100000000-0x106ffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x106ffffff @ [mem 0xdfbfe000-0xdfbfffff]
[    0.000000] RAMDISK: [mem 0x36104000-0x37079fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000dfbf4120 0007C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000dfbf3000 000F4 (v04 HPQOEM SLIC-MPC 00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000dfbdf000 0F5D1 (v01 HP     INSYDE   F0000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000dfb86000 00040
[    0.000000] ACPI: HPET 00000000dfbf2000 00038 (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000dfbf1000 00084 (v02 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000dfbf0000 0003C (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 00000000dfbef000 000A5 (v32 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000dfbde000 00028 (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000dfbdd000 00176 (v01 HPQOEM SLIC-MPC 00000001 ACPI 00040000)
[    0.000000] ACPI: WDRT 00000000dfbdc000 00047 (v01 HP     INSYDE   00000000 ACPI 00040000)
[    0.000000] ACPI: WDAT 00000000dfbdb000 001AC (v01 HP     INSYDE   00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000dfbda000 003DE (v01 HP     INSYDE   00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000dfbd8000 0168E (v02 HP     INSYDE   00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000106ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x106ffffff]
[    0.000000]   NODE_DATA [mem 0x106ffb000-0x106ffffff]
[    0.000000]  [ffffea0000000000-ffffea00041fffff] PMD -> [ffff880102c00000-ffff8801065fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x106ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xdf9befff]
[    0.000000]   node   0: [mem 0xdfbf5000-0xdfbfffff]
[    0.000000]   node   0: [mem 0x100000000-0x106ffffff]
[    0.000000] On node 0 totalpages: 944473
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14248 pages used for memmap
[    0.000000]   DMA32 zone: 897570 pages, LIFO batch:31
[    0.000000]   Normal zone: 448 pages used for memmap
[    0.000000]   Normal zone: 28224 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df9bf000 - 00000000dfabf000
[    0.000000] PM: Registered nosave memory: 00000000dfabf000 - 00000000dfbbf000
[    0.000000] PM: Registered nosave memory: 00000000dfbbf000 - 00000000dfbf5000
[    0.000000] PM: Registered nosave memory: 00000000dfc00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880106c00000 s84928 r8192 d21568 u524288
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 929707
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=b67f1e8f-2cca-4ea6-bb11-23b6eafd8938 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3620328k/4308992k available (7171k kernel code, 531100k absent, 157564k reserved, 6072k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 15204352 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1646.556 MHz processor
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3293.11 BogoMIPS (lpj=6586224)
[    0.000014] pid_max: default: 32768 minimum: 301
[    0.000062] Security Framework initialized
[    0.000088] AppArmor: AppArmor initialized
[    0.000090] Yama: becoming mindful.
[    0.000723] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003321] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004534] Mount-cache hash table entries: 256
[    0.004897] Initializing cgroup subsys cpuacct
[    0.004905] Initializing cgroup subsys memory
[    0.004921] Initializing cgroup subsys devices
[    0.004925] Initializing cgroup subsys freezer
[    0.004928] Initializing cgroup subsys blkio
[    0.004931] Initializing cgroup subsys perf_event
[    0.004936] Initializing cgroup subsys hugetlb
[    0.004984] tseg: 00dfc00000
[    0.004989] CPU: Physical Processor ID: 0
[    0.004991] CPU: Processor Core ID: 0
[    0.004995] mce: CPU supports 6 MCE banks
[    0.005014] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005014] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.005014] tlb_flushall_shift: 5
[    0.005240] Freeing SMP alternatives: 24k freed
[    0.009965] ACPI: Core revision 20121018
[    0.024557] ftrace: allocating 29359 entries in 115 pages
[    0.405580] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.445220] smpboot: CPU0: AMD E-450 APU with Radeon(tm) HD Graphics (fam: 14, model: 02, stepping: 00)
[    0.550585] Performance Events: AMD PMU driver.
[    0.550594] ... version:                0
[    0.550597] ... bit width:              48
[    0.550599] ... generic registers:      4
[    0.550601] ... value mask:             0000ffffffffffff
[    0.550604] ... max period:             00007fffffffffff
[    0.550607] ... fixed-purpose events:   0
[    0.550609] ... event mask:             000000000000000f
[    0.553141] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.553357] smpboot: Booting Node   0, Processors  #1
[    0.566469] Brought up 2 CPUs
[    0.566474] smpboot: Total of 2 processors activated (6586.22 BogoMIPS)
[    0.567593] devtmpfs: initialized
[    0.570299] EVM: security.selinux
[    0.570303] EVM: security.SMACK64
[    0.570305] EVM: security.capability
[    0.570677] PM: Registering ACPI NVS region [mem 0xdfabf000-0xdfbbefff] (1048576 bytes)
[    0.572719] regulator-dummy: no parameters
[    0.572836] NET: Registered protocol family 16
[    0.573388] ACPI: bus type pci registered
[    0.573596] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.573601] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.579749] PCI: Using configuration type 1 for base access
[    0.582101] bio: create slab <bio-0> at 0
[    0.582641] ACPI: Added _OSI(Module Device)
[    0.582649] ACPI: Added _OSI(Processor Device)
[    0.582653] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.582656] ACPI: Added _OSI(Processor Aggregator Device)
[    0.585444] ACPI: EC: Look up EC in DSDT
[    0.588338] ACPI: Executed 1 blocks of module-level executable AML code
[    0.594348] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.724283] ACPI: Interpreter enabled
[    0.724308] ACPI: (supports S0 S3 S4 S5)
[    0.724359] ACPI: Using IOAPIC for interrupt routing
[    1.131442] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    1.131725] ACPI: No dock devices found.
[    1.131736] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.138031] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.138042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.138699] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce3ff])
[    1.138713] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    1.138794] PCI host bridge to bus 0000:00
[    1.138801] pci_bus 0000:00: root bus resource [bus 00-ff]
[    1.138807] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.138811] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.138816] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.138820] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.138824] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.138828] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.138832] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.138836] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.138840] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.138844] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.138848] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.138852] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.138856] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    1.138859] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    1.138863] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xf7ffffff]
[    1.138867] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    1.138871] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    1.138888] pci 0000:00:00.0: [1022:1510] type 00 class 0x060000
[    1.138952] pci 0000:00:01.0: [1002:9806] type 00 class 0x030000
[    1.138968] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    1.138979] pci 0000:00:01.0: reg 14: [io  0x4000-0x40ff]
[    1.138990] pci 0000:00:01.0: reg 18: [mem 0xf0300000-0xf033ffff]
[    1.139054] pci 0000:00:01.0: supports D1 D2
[    1.139081] pci 0000:00:01.1: [1002:1314] type 00 class 0x040300
[    1.139095] pci 0000:00:01.1: reg 10: [mem 0xf0344000-0xf0347fff]
[    1.139170] pci 0000:00:01.1: supports D1 D2
[    1.139205] pci 0000:00:04.0: [1022:1512] type 01 class 0x060400
[    1.139300] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.139413] pci 0000:00:11.0: [1002:4394] type 00 class 0x010601
[    1.139440] pci 0000:00:11.0: reg 10: [io  0x4118-0x411f]
[    1.139455] pci 0000:00:11.0: reg 14: [io  0x4124-0x4127]
[    1.139469] pci 0000:00:11.0: reg 18: [io  0x4110-0x4117]
[    1.139483] pci 0000:00:11.0: reg 1c: [io  0x4120-0x4123]
[    1.139498] pci 0000:00:11.0: reg 20: [io  0x4100-0x410f]
[    1.139512] pci 0000:00:11.0: reg 24: [mem 0xf034e000-0xf034e3ff]
[    1.139595] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    1.139615] pci 0000:00:12.0: reg 10: [mem 0xf034d000-0xf034dfff]
[    1.139715] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    1.140250] pci 0000:00:12.2: reg 10: [mem 0xf034c000-0xf034c0ff]
[    1.143144] pci 0000:00:12.2: supports D1 D2
[    1.143149] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.143185] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    1.143205] pci 0000:00:13.0: reg 10: [mem 0xf034b000-0xf034bfff]
[    1.143311] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    1.143799] pci 0000:00:13.2: reg 10: [mem 0xf034a000-0xf034a0ff]
[    1.146664] pci 0000:00:13.2: supports D1 D2
[    1.146669] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.146705] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    1.146817] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    1.146848] pci 0000:00:14.2: reg 10: [mem 0xf0340000-0xf0343fff 64bit]
[    1.146940] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.146963] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    1.147070] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    1.147146] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
[    1.147257] pci 0000:00:15.0: supports D1 D2
[    1.147296] pci 0000:00:15.1: [1002:43a1] type 01 class 0x060400
[    1.147405] pci 0000:00:15.1: supports D1 D2
[    1.147448] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    1.147469] pci 0000:00:16.0: reg 10: [mem 0xf0349000-0xf0349fff]
[    1.147575] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    1.148062] pci 0000:00:16.2: reg 10: [mem 0xf0348000-0xf03480ff]
[    1.150923] pci 0000:00:16.2: supports D1 D2
[    1.150928] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    1.150965] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
[    1.151017] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
[    1.151064] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
[    1.151113] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
[    1.151175] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
[    1.151222] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
[    1.151269] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
[    1.151320] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
[    1.151462] pci 0000:00:04.0: PCI bridge to [bus 01]
[    1.151623] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    1.151637] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.151641] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.151645] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.151649] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    1.151653] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    1.151657] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    1.151661] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.151665] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.151669] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.151673] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.151677] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    1.151681] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    1.151685] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    1.151689] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    1.151693] pci 0000:00:14.4:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    1.151697] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    1.151701] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    1.151843] pci 0000:03:00.0: [14e4:4727] type 00 class 0x028000
[    1.151877] pci 0000:03:00.0: reg 10: [mem 0xf0200000-0xf0203fff 64bit]
[    1.152046] pci 0000:03:00.0: supports D1 D2
[    1.157926] pci 0000:00:15.0: PCI bridge to [bus 03-06]
[    1.157946] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    1.157955] pci 0000:00:15.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    1.157966] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.158077] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    1.158106] pci 0000:07:00.0: reg 10: [io  0x2000-0x20ff]
[    1.158147] pci 0000:07:00.0: reg 18: [mem 0xf0104000-0xf0104fff 64bit pref]
[    1.158173] pci 0000:07:00.0: reg 20: [mem 0xf0100000-0xf0103fff 64bit pref]
[    1.158286] pci 0000:07:00.0: supports D1 D2
[    1.158291] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.165912] pci 0000:00:15.1: PCI bridge to [bus 07]
[    1.165933] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    1.165948] pci 0000:00:15.1:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    1.166014] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.VGA_._PRT]
[    1.166113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    1.166201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    1.166268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT]
[    1.166342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AZAL._PRT]
[    1.166442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.166773]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.167329]  pci0000:00: ACPI _OSC control (0x19) granted
[    1.169926] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170153] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170270] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170386] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170481] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170557] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170632] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.170708] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    1.171106] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    1.171124] vgaarb: loaded
[    1.171127] vgaarb: bridge control possible 0000:00:01.0
[    1.171525] SCSI subsystem initialized
[    1.171530] ACPI: bus type scsi registered
[    1.171837] libata version 3.00 loaded.
[    1.171901] ACPI: bus type usb registered
[    1.171959] usbcore: registered new interface driver usbfs
[    1.171977] usbcore: registered new interface driver hub
[    1.172261] usbcore: registered new device driver usb
[    1.172829] PCI: Using ACPI for IRQ routing
[    1.175579] PCI: pci_cache_line_size set to 64 bytes
[    1.175711] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    1.175716] e820: reserve RAM buffer [mem 0xdf9bf000-0xdfffffff]
[    1.175719] e820: reserve RAM buffer [mem 0xdfc00000-0xdfffffff]
[    1.175723] e820: reserve RAM buffer [mem 0x107000000-0x107ffffff]
[    1.175945] NetLabel: Initializing
[    1.175948] NetLabel:  domain hash size = 128
[    1.175951] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.175972] NetLabel:  unlabeled traffic allowed by default
[    1.176261] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.176274] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.178329] Switching to clocksource hpet
[    1.189249] AppArmor: AppArmor Filesystem Enabled
[    1.189315] pnp: PnP ACPI init
[    1.189344] ACPI: bus type pnp registered
[    1.189619] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.189625] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    1.189634] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.189985] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.190061] pnp 00:02: [dma 4]
[    1.190100] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.190174] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.190339] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.190388] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.190523] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.190655] pnp 00:07: Plug and Play ACPI device, IDs SYN1e50 PNP0f13 (active)
[    1.190747] system 00:08: [io  0x0400-0x04cf] has been reserved
[    1.190753] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    1.190757] system 00:08: [io  0x04d6] has been reserved
[    1.190761] system 00:08: [io  0x0680-0x06ff] has been reserved
[    1.190766] system 00:08: [io  0x077a] has been reserved
[    1.190770] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    1.190774] system 00:08: [io  0x0c14] has been reserved
[    1.190778] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    1.190782] system 00:08: [io  0x0c6c] has been reserved
[    1.190786] system 00:08: [io  0x0c6f] has been reserved
[    1.190791] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    1.190795] system 00:08: [io  0x0380-0x0387] has been reserved
[    1.190801] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.190942] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    1.190947] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    1.190953] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.191547] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.391515] pnp: PnP ACPI: found 11 devices
[    1.391524] ACPI: ACPI bus type pnp unregistered
[    1.401862] pci 0000:00:04.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    1.401874] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    1.401880] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    1.401988] pci 0000:00:04.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    1.401993] pci 0000:00:04.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    1.401998] pci 0000:00:04.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    1.402012] pci 0000:00:04.0: BAR 14: assigned [mem 0xf0400000-0xf05fffff]
[    1.402023] pci 0000:00:04.0: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
[    1.402030] pci 0000:00:04.0: BAR 13: assigned [io  0x1000-0x1fff]
[    1.402036] pci 0000:00:04.0: PCI bridge to [bus 01]
[    1.402043] pci 0000:00:04.0:   bridge window [io  0x1000-0x1fff]
[    1.402051] pci 0000:00:04.0:   bridge window [mem 0xf0400000-0xf05fffff]
[    1.402057] pci 0000:00:04.0:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
[    1.402066] pci 0000:00:14.4: PCI bridge to [bus 02]
[    1.402134] pci 0000:00:15.0: PCI bridge to [bus 03-06]
[    1.402139] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    1.402147] pci 0000:00:15.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    1.402154] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.402163] pci 0000:00:15.1: PCI bridge to [bus 07]
[    1.402169] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    1.402180] pci 0000:00:15.1:   bridge window [mem 0xf0100000-0xf01fffff 64bit pref]
[    1.402243] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.402247] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.402252] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.402256] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.402260] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.402263] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.402267] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    1.402271] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    1.402275] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    1.402279] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    1.402283] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    1.402287] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    1.402291] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    1.402294] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    1.402298] pci_bus 0000:00: resource 18 [mem 0xe0000000-0xf7ffffff]
[    1.402302] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xfed3ffff]
[    1.402306] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    1.402310] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    1.402314] pci_bus 0000:01: resource 1 [mem 0xf0400000-0xf05fffff]
[    1.402318] pci_bus 0000:01: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
[    1.402323] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    1.402327] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    1.402330] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    1.402334] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.402338] pci_bus 0000:02: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.402342] pci_bus 0000:02: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.402346] pci_bus 0000:02: resource 10 [mem 0x000d0000-0x000d3fff]
[    1.402350] pci_bus 0000:02: resource 11 [mem 0x000d4000-0x000d7fff]
[    1.402353] pci_bus 0000:02: resource 12 [mem 0x000d8000-0x000dbfff]
[    1.402357] pci_bus 0000:02: resource 13 [mem 0x000dc000-0x000dffff]
[    1.402361] pci_bus 0000:02: resource 14 [mem 0x000e0000-0x000e3fff]
[    1.402365] pci_bus 0000:02: resource 15 [mem 0x000e4000-0x000e7fff]
[    1.402369] pci_bus 0000:02: resource 16 [mem 0x000e8000-0x000ebfff]
[    1.402373] pci_bus 0000:02: resource 17 [mem 0x000ec000-0x000effff]
[    1.402377] pci_bus 0000:02: resource 18 [mem 0xe0000000-0xf7ffffff]
[    1.402381] pci_bus 0000:02: resource 19 [mem 0xfc000000-0xfed3ffff]
[    1.402384] pci_bus 0000:02: resource 20 [mem 0xfed45000-0xffffffff]
[    1.402389] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    1.402392] pci_bus 0000:03: resource 1 [mem 0xf0200000-0xf02fffff]
[    1.402396] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    1.402401] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    1.402405] pci_bus 0000:07: resource 2 [mem 0xf0100000-0xf01fffff 64bit pref]
[    1.402468] NET: Registered protocol family 2
[    1.402785] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    1.403138] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.403413] TCP: Hash tables configured (established 32768 bind 32768)
[    1.403510] TCP: reno registered
[    1.403543] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.403594] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.403775] NET: Registered protocol family 1
[    1.403810] pci 0000:00:01.0: Boot video device
[    1.666072] PCI: CLS 64 bytes, default 64
[    1.666181] Trying to unpack rootfs image as initramfs...
[    2.171507] Freeing initrd memory: 15832k freed
[    2.180677] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.180690] software IO TLB [mem 0xdb9bf000-0xdf9bf000] (64MB) mapped at [ffff8800db9bf000-ffff8800df9befff]
[    2.180860] Simple Boot Flag at 0x44 set to 0x1
[    2.181082] LVT offset 0 assigned for vector 0x400
[    2.181238] perf: AMD IBS detected (0x000000ff)
[    2.181823] Initialise module verification
[    2.181927] audit: initializing netlink socket (disabled)
[    2.181948] type=2000 audit(1380643642.716:1): initialized
[    2.229469] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.233658] VFS: Disk quotas dquot_6.5.2
[    2.233772] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.235137] fuse init (API version 7.20)
[    2.235386] msgmni has been set to 7101
[    2.236464] Key type asymmetric registered
[    2.236473] Asymmetric key parser 'x509' registered
[    2.236571] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.236840] io scheduler noop registered
[    2.236881] io scheduler deadline registered (default)
[    2.236905] io scheduler cfq registered
[    2.237214] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    2.237534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.237682] pciehp 0000:00:04.0:pcie04: HPC vendor_id 1022 device_id 1512 ss_vid 1022 ss_did 1234
[    2.237748] pciehp 0000:00:04.0:pcie04: service driver pciehp loaded
[    2.237758] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.350216] ACPI: AC Adapter [ACAD] (on-line)
[    2.350472] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.350482] ACPI: Power Button [PWRB]
[    2.350572] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    2.351493] ACPI: Lid Switch [LID]
[    2.351631] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.351641] ACPI: Power Button [PWRF]
[    2.351985] ACPI: acpi_idle registered with cpuidle
[    2.762911] thermal LNXTHERM:00: registered as thermal_zone0
[    2.762925] ACPI: Thermal Zone [THRM] (70 C)
[    2.763002] GHES: HEST is not enabled!
[    2.763181] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.769756] Linux agpgart interface v0.103
[    2.774324] brd: module loaded
[    2.776915] loop: module loaded
[    2.777626] libphy: Fixed MDIO Bus: probed
[    2.777750] tun: Universal TUN/TAP device driver, 1.6
[    2.777754] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.777982] PPP generic driver version 2.4.2
[    2.778160] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.778164] ehci-pci: EHCI PCI platform driver
[    2.778317] ehci-pci 0000:00:12.2: EHCI Host Controller
[    2.778330] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.778350] QUIRK: Enable AMD PLL fix
[    2.778354] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.778443] ehci-pci 0000:00:12.2: debug port 1
[    2.778509] ehci-pci 0000:00:12.2: irq 17, io mem 0xf034c000
[    2.788191] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.788261] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.788268] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.788273] usb usb1: Product: EHCI Host Controller
[    2.788277] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    2.788281] usb usb1: SerialNumber: 0000:00:12.2
[    2.788826] hub 1-0:1.0: USB hub found
[    2.788841] hub 1-0:1.0: 5 ports detected
[    2.789282] ehci-pci 0000:00:13.2: EHCI Host Controller
[    2.789298] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.789309] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.789327] ehci-pci 0000:00:13.2: debug port 1
[    2.789375] ehci-pci 0000:00:13.2: irq 17, io mem 0xf034a000
[    2.800315] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.800377] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.800383] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.800388] usb usb2: Product: EHCI Host Controller
[    2.800392] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    2.800395] usb usb2: SerialNumber: 0000:00:13.2
[    2.800905] hub 2-0:1.0: USB hub found
[    2.800920] hub 2-0:1.0: 5 ports detected
[    2.801364] ehci-pci 0000:00:16.2: EHCI Host Controller
[    2.801377] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    2.801387] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.801405] ehci-pci 0000:00:16.2: debug port 1
[    2.801454] ehci-pci 0000:00:16.2: irq 17, io mem 0xf0348000
[    2.812297] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.812373] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.812380] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.812385] usb usb3: Product: EHCI Host Controller
[    2.812389] usb usb3: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    2.812392] usb usb3: SerialNumber: 0000:00:16.2
[    2.812918] hub 3-0:1.0: USB hub found
[    2.812933] hub 3-0:1.0: 4 ports detected
[    2.813329] ehci-platform: EHCI generic platform driver
[    2.813350] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.813492] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.813504] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.813559] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf034d000
[    2.872224] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.872234] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.872238] usb usb4: Product: OHCI Host Controller
[    2.872242] usb usb4: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    2.872246] usb usb4: SerialNumber: 0000:00:12.0
[    2.872717] hub 4-0:1.0: USB hub found
[    2.872806] hub 4-0:1.0: 5 ports detected
[    2.873135] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.873151] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.873184] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf034b000
[    2.932144] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.932153] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.932158] usb usb5: Product: OHCI Host Controller
[    2.932162] usb usb5: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    2.932166] usb usb5: SerialNumber: 0000:00:13.0
[    2.932641] hub 5-0:1.0: USB hub found
[    2.932727] hub 5-0:1.0: 5 ports detected
[    2.933049] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.933061] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    2.933096] ohci_hcd 0000:00:16.0: irq 18, io mem 0xf0349000
[    2.970857] ACPI: Battery Slot [BAT0] (battery present)
[    2.991894] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.991900] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.991904] usb usb6: Product: OHCI Host Controller
[    2.991909] usb usb6: Manufacturer: Linux 3.8.0-31-generic ohci_hcd
[    2.991912] usb usb6: SerialNumber: 0000:00:16.0
[    2.992373] hub 6-0:1.0: USB hub found
[    2.992459] hub 6-0:1.0: 4 ports detected
[    2.992743] uhci_hcd: USB Universal Host Controller Interface driver
[    2.992945] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.996895] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.996908] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.997604] mousedev: PS/2 mouse device common for all mice
[    2.998474] rtc_cmos 00:04: RTC can wake from S4
[    2.998647] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.998760] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.998947] device-mapper: uevent: version 1.0.3
[    2.999109] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.999172] cpuidle: using governor ladder
[    2.999311] cpuidle: using governor menu
[    2.999319] ledtrig-cpu: registered to indicate activity on CPUs
[    2.999322] EFI Variables Facility v0.08 2004-May-17
[    3.000080] ashmem: initialized
[    3.000369] TCP: cubic registered
[    3.000549] NET: Registered protocol family 10
[    3.000858] NET: Registered protocol family 17
[    3.000880] Key type dns_resolver registered
[    3.001421] Loading module verification certificates
[    3.003826] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: ef66b5fef7cf2d982f954bc9bd9879a3cb821073'
[    3.003853] registered taskstats version 1
[    3.009867] Key type trusted registered
[    3.014833] Key type encrypted registered
[    3.020448] rtc_cmos 00:04: setting system clock to 2013-10-01 16:07:24 UTC (1380643644)
[    3.020545] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    3.022919] acpi-cpufreq: overriding BIOS provided _PSD data
[    3.023139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.023142] EDD information not available.
[    3.026527] Freeing unused kernel memory: 1012k freed
[    3.027105] Write protecting the kernel read-only data: 12288k
[    3.033847] Freeing unused kernel memory: 1012k freed
[    3.040894] Freeing unused kernel memory: 1008k freed
[    3.065767] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.089202] udevd[96]: starting version 175
[    3.099776] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    3.175508] tsc: Refined TSC clocksource calibration: 1646.493 MHz
[    3.175522] Switching to clocksource tsc
[    3.279625] usb 1-3: New USB device found, idVendor=064e, idProduct=d217
[    3.279635] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.279640] usb 1-3: Product: HP TrueVision HD
[    3.279644] usb 1-3: Manufacturer: SuYin
[    3.279648] usb 1-3: SerialNumber: HF1016-A821-OV03-VH-R02.09.02
[    3.302592] Disabling lock debugging due to kernel taint
[    3.310466] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.310829] r8169 0000:07:00.0: irq 41 for MSI/MSI-X
[    3.311218] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000636000, 80:c1:6e:49:47:50, XID 0c900800 IRQ 41
[    3.311224] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.324884] ahci 0000:00:11.0: version 3.0
[    3.335724] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    3.335736] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    3.339193] scsi0 : ahci
[    3.363965] ata1: SATA max UDMA/133 abar m1024@0xf034e000 port 0xf034e100 irq 19
[    3.806813] usb 6-1: new full-speed USB device number 2 using ohci_hcd
[    3.854810] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.856317] ata1.00: ATA-8: Hitachi HTS545050B9A300, PB4OCA1G, max UDMA/100
[    3.856333] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.857870] ata1.00: configured for UDMA/100
[    3.858564] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 PB4O PQ: 0 ANSI: 5
[    3.859061] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.859068] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.859176] sd 0:0:0:0: [sda] Write Protect is off
[    3.859182] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.859227] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.914641]  sda: sda1 sda2 < sda5 >
[    3.916260] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.981532] usb 6-1: New USB device found, idVendor=0a5c, idProduct=21e3
[    3.981548] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.981557] usb 6-1: Product: BCM20702A0
[    3.981565] usb 6-1: Manufacturer: Broadcom Corp
[    3.981573] usb 6-1: SerialNumber: 642737C270DA
[    4.317060] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.872651] init: ureadahead main process (259) terminated with status 5
[    6.985588] Adding 3776508k swap on /dev/sda5.  Priority:-1 extents:1 across:3776508k 
[    8.442734] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.001877] udevd[335]: starting version 175
[   10.831686] lp: driver loaded but no devices found
[   11.189317] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.638590] wmi: Mapper loaded
[   11.811377] lib80211: common routines for IEEE802.11 drivers
[   11.811387] lib80211_crypt: registered algorithm 'NULL'
[   11.953047] acpi device:00: registered as cooling_device2
[   11.953172] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.953304] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   12.079385] input: HP WMI hotkeys as /devices/virtual/input/input5
[   12.081145] microcode: CPU0: patch_level=0x05000101
[   12.201939] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.454182] microcode: CPU0: new patch_level=0x05000119
[   12.454214] microcode: CPU1: patch_level=0x05000101
[   12.460320] microcode: CPU1: new patch_level=0x05000119
[   12.461748] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.494598] hp_accel: laptop model unknown, using default axes configuration
[   12.502850] lis3lv02d: 8 bits 3DC sensor found
[   12.545837] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   12.607142] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   12.607261] sp5100_tco: PCI Revision ID: 0x42
[   12.607381] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   12.607396] sp5100_tco: Last reboot was not triggered by watchdog.
[   12.607524] sp5100_tco: initialized (0xffffc9000066eb00). heartbeat=60 sec (nowayout=0)
[   12.958969] cfg80211: Calling CRDA to update world regulatory domain
[   13.225815] Bluetooth: Core ver 2.16
[   13.225865] NET: Registered protocol family 31
[   13.225869] Bluetooth: HCI device and connection manager initialized
[   13.225886] Bluetooth: HCI socket layer initialized
[   13.225891] Bluetooth: L2CAP socket layer initialized
[   13.225902] Bluetooth: SCO socket layer initialized
[   13.253631] Linux video capture interface: v2.00
[   13.305138] [drm] Initialized drm 1.1.0 20060810
[   13.680204] kvm: Nested Virtualization enabled
[   13.680214] kvm: Nested Paging enabled
[   13.728131] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1679, fw id: 724542
[   13.735012] uvcvideo: Found UVC 1.00 device HP TrueVision HD (064e:d217)
[   13.740161] input: HP TrueVision HD as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input7
[   13.740545] usbcore: registered new interface driver uvcvideo
[   13.740549] USB Video Class driver (1.1.1)
[   13.769595] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.238693] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.461401] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[   14.470984] [drm] radeon defaulting to kernel modesetting.
[   14.470993] [drm] radeon kernel modesetting enabled.
[   14.548800] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   14.628989] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   14.629449] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   14.637350] [drm] initializing kernel modesetting (PALM 0x1002:0x9806 0x103C:0x3387).
[   14.637452] [drm] register mmio base: 0xF0300000
[   14.637455] [drm] register mmio size: 262144
[   14.638304] ATOM BIOS: HP
[   14.638412] radeon 0000:00:01.0: VRAM: 384M 0x0000000000000000 - 0x0000000017FFFFFF (384M used)
[   14.638418] radeon 0000:00:01.0: GTT: 512M 0x0000000018000000 - 0x0000000037FFFFFF
[   14.645569] [drm] Detected VRAM RAM=384M, BAR=256M
[   14.645579] [drm] RAM width 32bits DDR
[   14.649357] [TTM] Zone  kernel: Available graphics memory: 1819608 kiB
[   14.649365] [TTM] Initializing pool allocator
[   14.649373] [TTM] Initializing DMA pool allocator
[   14.649419] [drm] radeon: 384M of VRAM memory ready
[   14.649423] [drm] radeon: 512M of GTT memory ready.
[   14.649458] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.652810] [drm] Loading PALM Microcode
[   14.918220] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   14.918452] radeon 0000:00:01.0: WB enabled
[   14.918460] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000018000c00 and cpu addr 0xffff8800da8e5c00
[   14.918466] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000018000c0c and cpu addr 0xffff8800da8e5c0c
[   14.918471] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.918473] [drm] Driver supports precise vblank timestamp query.
[   14.918534] radeon 0000:00:01.0: irq 43 for MSI/MSI-X
[   14.918560] radeon 0000:00:01.0: radeon: using MSI.
[   14.918603] [drm] radeon: irq initialized.
[   14.935900] [drm] ring test on 0 succeeded in 1 usecs
[   14.935969] [drm] ring test on 3 succeeded in 1 usecs
[   14.936843] [drm] ib test on ring 0 succeeded in 0 usecs
[   14.936885] [drm] ib test on ring 3 succeeded in 0 usecs
[   14.994044] [drm] radeon atom DIG backlight initialized
[   14.994064] [drm] Radeon Display Connectors
[   14.994071] [drm] Connector 0:
[   14.994077] [drm]   LVDS-1
[   14.994080] [drm]   HPD1
[   14.994085] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   14.994087] [drm]   Encoders:
[   14.994090] [drm]     LCD1: INTERNAL_UNIPHY
[   14.994092] [drm] Connector 1:
[   14.994095] [drm]   HDMI-A-1
[   14.994097] [drm]   HPD2
[   14.994100] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   14.994103] [drm]   Encoders:
[   14.994105] [drm]     DFP1: INTERNAL_UNIPHY
[   14.994107] [drm] Connector 2:
[   14.994110] [drm]   VGA-1
[   14.994113] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   14.994115] [drm]   Encoders:
[   14.994118] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   14.994183] [drm] Internal thermal controller without fan control
[   14.994505] [drm] radeon: power management initialized
[   15.297985] usbcore: registered new interface driver btusb
[   15.299296] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   15.423743] [drm] fb mappable at 0xE0142000
[   15.423751] [drm] vram apper at 0xE0000000
[   15.423754] [drm] size 4325376
[   15.423756] [drm] fb depth is 24
[   15.423759] [drm]    pitch is 5632
[   15.424131] fbcon: radeondrmfb (fb0) is primary device
[   15.598879] Bluetooth: can't load firmware, may not work correctly
[   15.672125] lib80211_crypt: registered algorithm 'TKIP'
[   15.976752] Console: switching to colour frame buffer device 170x48
[   15.982536] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[   15.982540] radeon 0000:00:01.0: registered panic notifier
[   15.982880] [drm] Initialized radeon 2.29.0 20080528 for 0000:00:01.0 on minor 0
[   16.987555] type=1400 audit(1380643658.483:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=692 comm="apparmor_parser"
[   16.988200] type=1400 audit(1380643658.483:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=692 comm="apparmor_parser"
[   16.988565] type=1400 audit(1380643658.483:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=692 comm="apparmor_parser"
[   16.989513] type=1400 audit(1380643658.483:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=693 comm="apparmor_parser"
[   16.990154] type=1400 audit(1380643658.483:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=693 comm="apparmor_parser"
[   16.990529] type=1400 audit(1380643658.483:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=693 comm="apparmor_parser"
[   18.846877] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   18.913833] init: failsafe main process (810) killed by TERM signal
[   20.558981] ppdev: user-space parallel port driver
[   20.772259] Bluetooth: RFCOMM TTY layer initialized
[   20.772287] Bluetooth: RFCOMM socket layer initialized
[   20.772290] Bluetooth: RFCOMM ver 1.11
[   21.125918] type=1400 audit(1380643662.631:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=926 comm="apparmor_parser"
[   21.126681] type=1400 audit(1380643662.631:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=926 comm="apparmor_parser"
[   21.161349] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.161358] Bluetooth: BNEP filters: protocol multicast
[   21.161376] Bluetooth: BNEP socket layer initialized
[   25.898468] type=1400 audit(1380643667.407:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=996 comm="apparmor_parser"
[   25.899172] type=1400 audit(1380643667.407:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=996 comm="apparmor_parser"
[   25.899554] type=1400 audit(1380643667.407:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=996 comm="apparmor_parser"
[   26.089541] type=1400 audit(1380643667.599:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=995 comm="apparmor_parser"
[   26.090071] type=1400 audit(1380643667.599:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=995 comm="apparmor_parser"
[   26.246330] type=1400 audit(1380643667.759:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=998 comm="apparmor_parser"
[   26.431237] type=1400 audit(1380643667.939:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=999 comm="apparmor_parser"
[   26.431995] type=1400 audit(1380643667.939:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=999 comm="apparmor_parser"
[   26.439331] type=1400 audit(1380643667.947:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1002 comm="apparmor_parser"
[   26.440164] type=1400 audit(1380643667.947:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1002 comm="apparmor_parser"
[   26.782472] r8169 0000:07:00.0 eth0: link down
[   26.782557] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.783272] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  263.672741] audit_printk_skb: 27 callbacks suppressed
[  263.672752] type=1400 audit(1380643905.429:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2318 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  283.868002] hp_wmi: Unknown event_id - 0 - 0x0
[  541.123484] type=1400 audit(1380644183.292:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=942 comm="cupsd" pid=942 comm="cupsd" capability=36  capname="block_suspend"
[11746.467611] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[11746.467622] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[11746.467636] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[11746.467640] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[11746.467650] ERROR @wl_dev_intvar_get : error (-1)
[11746.467653] ERROR @wl_cfg80211_get_tx_power : error (-1)

```

This is my output for dmesg | grep ERROR

```
[11746.467611] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[11746.467622] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[11746.467636] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[11746.467640] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[11746.467650] ERROR @wl_dev_intvar_get : error (-1)
[11746.467653] ERROR @wl_cfg80211_get_tx_power : error (-1)
```

This is my output for dmesg | grep error

```
[   11.189317] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[11746.467650] ERROR @wl_dev_intvar_get : error (-1)
[11746.467653] ERROR @wl_cfg80211_get_tx_power : error (-1)
```

Right now what I did was remove the Addicional Drivers for the video card , and all the errors related to fglrx disappeared...
Now all this errors are related to the wireless card... And this errors appeared when my system suspended and then resumed, cause if I shutdown my computer and then I turn it on this errors don't appear, just when I suspend and resume...

---

### Post by Pedro_Matias on 2013-10-01
> **Gyokuro said:**
> Hi

As some member already pointed you to your problems - you should disable all your closed source drivers:

1.) frglx => for your graphic card
2.) wireless driver

reboot and look whether your box is freezing. If it is freezing again - check whether it is cooled enough and I have noticed after I have checked your dmesg file you have a lot of messages like this:

 6.050115] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3146959
[    6.050778] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147160
[    6.050886] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147158
[    6.050916] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3147156

I have snipped the rest but are you sure that your hard disk is ok? A lot of freezes can happen if the system/kernel write/read data to/of your disk and the disk is damaged.

I finished now the Primary Hard Disk Self Test in BIOS, and the test didn't gave me any error...

---

### Post by Gyokuro on 2013-10-02
Hi

The BIOS hard disk test is a very simple one and it do not test for bad sectors and for new disks you should test with smart and badblocks.

---

### Post by heir4c on 2013-10-02
The Errors for the wireless card, it's a bug, see:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1114281](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1114281)

For the fglrx driver. I have a E35M1-M motherboard (for desktop) and that works fine with the driver (without extra graphics card), but I have also Errors in my logs. 
But there is a little bit strange in your dmesg: 
```
radeon 0000:00:01.0: VRAM: 384M 0x0000000000000000 - 0x0000000017FFFFFF (384M used)
[   14.638418] radeon 0000:00:01.0: GTT: 512M 0x0000000018000000 - 0x0000000037FFFFFF
[   14.645569] [drm] Detected VRAM RAM=384M, BAR=256M
[   14.645579] [drm] RAM width 32bits DDR
[   14.649357] [TTM] Zone  kernel: Available graphics memory: 1819608 kiB

```
I see there 32bits DDR. (That's the VRAM I think?) And I think you run a Ubuntu 64-bit. (Yes?).
I run a 64-bit Ubuntu on my board but I don't see that [drm] and VRAM in my dmesg.
Maybe somebody can explain that? And that's maybe the reason why it freezing? Or I'll be wrong and do not understand it?

---

### Post by Pedro_Matias on 2013-10-03
> **Gyokuro said:**
> Hi

The BIOS hard disk test is a very simple one and it do not test for bad sectors and for new disks you should test with smart and badblocks.

I will run those tests now

---

### Post by Pedro_Matias on 2013-10-03
> **heir4c said:**
> The Errors for the wireless card, it's a bug, see:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1114281](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1114281)

For the fglrx driver. I have a E35M1-M motherboard (for desktop) and that works fine with the driver (without extra graphics card), but I have also Errors in my logs. 
But there is a little bit strange in your dmesg: 
```
radeon 0000:00:01.0: VRAM: 384M 0x0000000000000000 - 0x0000000017FFFFFF (384M used)
[   14.638418] radeon 0000:00:01.0: GTT: 512M 0x0000000018000000 - 0x0000000037FFFFFF
[   14.645569] [drm] Detected VRAM RAM=384M, BAR=256M
[   14.645579] [drm] RAM width 32bits DDR
[   14.649357] [TTM] Zone  kernel: Available graphics memory: 1819608 kiB

```
I see there 32bits DDR. (That's the VRAM I think?) And I think you run a Ubuntu 64-bit. (Yes?).
I run a 64-bit Ubuntu on my board but I don't see that [drm] and VRAM in my dmesg.
Maybe somebody can explain that? And that's maybe the reason why it freezing? Or I'll be wrong and do not understand it?

I don't think so, cause my computer when I bought it had Windows 7 64-bits version installed

---

### Post by heir4c on 2013-10-03
Ok.

For your wireless, have you look at the links in this post? (the first and second link):
[http://ubuntuforums.org/showthread.php?t=2177412&page=2&p=12803294#post12803294](http://ubuntuforums.org/showthread.php?t=2177412&page=2&p=12803294#post12803294)

---

### Post by Pedro_Matias on 2013-10-04
> **Gyokuro said:**
> Hi

The BIOS hard disk test is a very simple one and it do not test for bad sectors and for new disks you should test with smart and badblocks.

I tested with SMART and had no erros , I will test now with badblocks

---

### Post by Pedro_Matias on 2013-10-04
> **heir4c said:**
> Ok.

For your wireless, have you look at the links in this post? (the first and second link):
[http://ubuntuforums.org/showthread.php?t=2177412&page=2&p=12803294#post12803294](http://ubuntuforums.org/showthread.php?t=2177412&page=2&p=12803294#post12803294)

I already did but I just don't know how to install the Broadcom drivers downloaded from their website cause are tar.gz files...

---

### Post by heir4c on 2013-10-04
Pedro, in the second link there is a explanation what to do. I can't do this here because I have no wireless in my PC. So I would install it here but I think I get errors or not enough info to finish the install. So I hope there is somebody else who can help you and explain it.
Maybe you can try to follow the howto and when you stuck on something you ask it here. Maybe you can write down every step you made, to remember what you already did.
I hope you can solve this problem.
Succes!!!
Greetings
Gerolf

---

### Post by Pedro_Matias on 2013-10-04
> **heir4c said:**
> Pedro, in the second link there is a explanation what to do. I can't do this here because I have no wireless in my PC. So I would install it here but I think I get errors or not enough info to finish the install. So I hope there is somebody else who can help you and explain it.
Maybe you can try to follow the howto and when you stuck on something you ask it here. Maybe you can write down every step you made, to remember what you already did.
I hope you can solve this problem.
Succes!!!
Greetings
Gerolf

I have installed the b43 package and the LED in my keyboard for the wireless is orange wich usually was suposed to mean the wireless card was off, but I can get wifi with no problems.
So as long as this fixes my problem I guess ok to get the orange LED :)
I will test now to see if the freezes disapeared

---

### Post by Bucky Ball on 2013-10-05
Now install: firmware-b43-installer. Reboot.

---

### Post by Pedro_Matias on 2013-10-08
> **Bucky Ball said:**
> Now install: firmware-b43-installer. Reboot.

I did that right now. I will test to see if the freezes disappeared

---

### Post by Bucky Ball on 2013-10-08
Please, make the change, try it out, *_then_* report back. Try and get the whole process in one post. What you've done and what was the result (someone else mentioned this earlier). Post back when you know when it has fixed or not. Thanks. ;)

---

