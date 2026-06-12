---
title: "Black screen on start up :("
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Agusia on 2012-01-21
Hi all. :)
I've got a problem with my Ubuntu 11.10. When i start it, I only get black screen with pointer in the center. I can't do anything. Could anyone help me?? :(

---

### Post by sffvba[e0rt on 2012-01-21
Hi,

What you can try is to hold down shift while booting which should bring you to the GRUB menu.  There press F6 (if memory serves) and choose *nomodeset*.

This should let your system boot.  Once you have the right driver for your graphics installed this should be an issue anymore (if this was indeed a graphics issue).


404

---

### Post by Agusia on 2012-01-21
> **not found said:**
> Hi,

What you can try is to hold down shift while booting which should bring you to the GRUB menu.  There press F6 (if memory serves) and choose *nomodeset*.

This should let your system boot.  Once you have the right driver for your graphics installed this should be an issue anymore (if this was indeed a graphics issue).


404

Thanks for reply. :)
I've got Windows 7 and Ubuntu on my netbook, so GRUB always shows when i turn on my computer. I've pressed F6 and it didn't do anything. I've chosen Ubuntu normally and it has started. I don't know why sometimes it works, sometimes it doesn't. :(

---

### Post by sffvba[e0rt on 2012-01-21
Hmmm, intermittent problems are a bit more tricky.

I suspect it is time to delve into some log files (an area that is murky to me but will be great to explore and learn from :) )

In terminal we can use the command:

```
dmesg | less
```

This will give you a look at your boot log, perhaps there is some error in there that might shed some light on this problem (I am however not sure if it will only contained the latest boot's information which won't help much as the system is working).

Any how, I am sure one of the guru's will reply soon and maybe point out a solution and the silliness of this attempt :)


404

---

### Post by Agusia on 2012-01-21
> **not found said:**
> Hmmm, intermittent problems are a bit more tricky.

I suspect it is time to delve into some log files (an area that is murky to me but will be great to explore and learn from :) )

In terminal we can use the command:

```
dmesg | less
```This will give you a look at your boot log, perhaps there is some error in there that might shed some light on this problem (I am however not sure if it will only contained the latest boot's information which won't help much as the system is working).

Any how, I am sure one of the guru's will reply soon and maybe point out a solution and the silliness of this attempt :)


404

Now Ubuntu crashes at random moments. It goes through the black screen, show wallpaper and things and then crashes. :( Where is this terminal?

---

### Post by sffvba[e0rt on 2012-01-21
The terminal I was referring to can typically be found once you have successfully booted into Ubuntu by launching it from Gnome (Can find it by pressing the Super Key (Windows key) then typing term ... it should show up and you can either click on it or just press enter).

Another why would be to press Ctrl+Alt+F1 to get to a terminal prompt, but again the boot process must have completed.

Have you had any successful boots?  Been able to use the desktop for any amount of time?


404

---

### Post by Agusia on 2012-01-21
> **not found said:**
> The terminal I was referring to can typically be found once you have successfully booted into Ubuntu by launching it from Gnome (Can find it by pressing the Super Key (Windows key) then typing term ... it should show up and you can either click on it or just press enter).

Another why would be to press Ctrl+Alt+F1 to get to a terminal prompt, but again the boot process must have completed.

Have you had any successful boots?  Been able to use the desktop for any amount of time?


404

Now I'm on Ubuntu and it works without any problems. I have found the terminal but I don't know how to put this log here.

---

### Post by sffvba[e0rt on 2012-01-21
> **Agusia said:**
> Now I'm on Ubuntu and it works without any problems. I have found the terminal but I don't know how to put this log here.

You can highlight the text with your mouse like in any other editor, then either right click and copy or even use Ctrl+Shift+C to copy.

Another why would be to run *dmesg > ~/dmesg.txt* which should create a txt file in your home directory which you can open with any of the editors you like.

You can then post it here, just wrap the information in code brackets (the little hash in your edit tools) to make it easier to read.


404

PS - I am sure there are several ways of doing this easier or even narrowing down the amount of information but this is still new territory to me ;)

---

### Post by Agusia on 2012-01-21
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 (Ubuntu 3.0.0-15.25-generic 3.0.13)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=94aacb2f-b9d6-4480-b3b7-f5b2fe29ab46 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000de63a000 (usable)
[    0.000000]  BIOS-e820: 00000000de63a000 - 00000000de83a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000de83a000 - 00000000dfd3f000 (usable)
[    0.000000]  BIOS-e820: 00000000dfd3f000 - 00000000dfdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000dfdbf000 - 00000000dfebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfebf000 - 00000000dfef6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef6000 - 00000000dff00000 (usable)
[    0.000000]  BIOS-e820: 00000000dff00000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000010f000000 (usable)
[    0.000000]  BIOS-e820: 000000010f000000 - 000000011f000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Acer AO722/JE10-BZ, BIOS V1.07 09/19/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x10f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 0DFEBD000 mask FFFFFF000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000011f000000 aka 4592M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xdff00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fe1b0] fe1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000dff00000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dff00000 page 4k
[    0.000000] kernel direct mapping tables up to dff00000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000010f000000
[    0.000000]  0100000000 - 010f000000 page 2M
[    0.000000] kernel direct mapping tables up to 10f000000 @ dfefe000-dff00000
[    0.000000] RAMDISK: 365be000 - 372d7000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 00000000dfef5120 00064 (v01 ACRSYS ACRPRDCT 00000003      01000013)
[    0.000000] ACPI: FACP 00000000dfef4000 000F4 (v04 ACRSYS ACRPRDCT 00000003 1025 00040000)
[    0.000000] ACPI: DSDT 00000000dfee8000 089F9 (v01 ACRSYS ACRPRDCT F0000000 1025 00040000)
[    0.000000] ACPI: FACS 00000000dfe97000 00040
[    0.000000] ACPI: HPET 00000000dfef3000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 00000000dfef2000 00084 (v02 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 00000000dfef1000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: BOOT 00000000dfee7000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC 00000000dfee6000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 00000000dfee5000 0030C (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000dfee3000 0168E (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000010f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000010f000000
[    0.000000]   NODE_DATA [000000010effb000 - 000000010effffff]
[    0.000000]  [ffffea0000000000-ffffea0003bfffff] PMD -> [ffff88010aa00000-ffff88010dffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0010f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000de63a
[    0.000000]     0: 0x000de83a -> 0x000dfd3f
[    0.000000]     0: 0x000dfef6 -> 0x000dff00
[    0.000000]     0: 0x00100000 -> 0x0010f000
[    0.000000] On node 0 totalpages: 977624
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 897921 pages, LIFO batch:31
[    0.000000]   Normal zone: 840 pages used for memmap
[    0.000000]   Normal zone: 60600 pages, LIFO batch:15
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
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000de63a000 - 00000000de83a000
[    0.000000] PM: Registered nosave memory: 00000000dfd3f000 - 00000000dfdbf000
[    0.000000] PM: Registered nosave memory: 00000000dfdbf000 - 00000000dfebf000
[    0.000000] PM: Registered nosave memory: 00000000dfebf000 - 00000000dfef6000
[    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000e0000000
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
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88010ec00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 962443
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=94aacb2f-b9d6-4480-b3b7-f5b2fe29ab46 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3759772k/4440064k available (6136k kernel code, 529568k absent, 150724k reserved, 6898k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 31457280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 997.474 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 1994.94 BogoMIPS (lpj=3989896)
[    0.004021] pid_max: default: 32768 minimum: 301
[    0.004093] Security Framework initialized
[    0.004137] AppArmor: AppArmor initialized
[    0.004142] Yama: becoming mindful.
[    0.008563] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012500] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.014409] Mount-cache hash table entries: 256
[    0.014774] Initializing cgroup subsys cpuacct
[    0.014794] Initializing cgroup subsys memory
[    0.014818] Initializing cgroup subsys devices
[    0.014824] Initializing cgroup subsys freezer
[    0.014829] Initializing cgroup subsys net_cls
[    0.014835] Initializing cgroup subsys blkio
[    0.014855] Initializing cgroup subsys perf_event
[    0.014934] tseg: 00dff00000
[    0.014941] CPU: Physical Processor ID: 0
[    0.014945] CPU: Processor Core ID: 0
[    0.014951] mce: CPU supports 6 MCE banks
[    0.021134] ACPI: Core revision 20110413
[    0.036042] ftrace: allocating 25729 entries in 101 pages
[    0.040671] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082459] CPU0: AMD C-60 APU with Radeon(tm) HD Graphics stepping 00
[    0.084004] Performance Events: AMD PMU driver.
[    0.084004] ... version:                0
[    0.084004] ... bit width:              48
[    0.084004] ... generic registers:      4
[    0.084004] ... value mask:             0000ffffffffffff
[    0.084004] ... max period:             00007fffffffffff
[    0.084004] ... fixed-purpose events:   0
[    0.084004] ... event mask:             000000000000000f
[    0.084004] Booting Node   0, Processors  #1
[    0.084004] smpboot cpu 1: start_ip = 9a000
[    0.176039] Brought up 2 CPUs
[    0.176046] Total of 2 processors activated (3989.96 BogoMIPS).
[    0.176732] devtmpfs: initialized
[    0.176732] PM: Registering ACPI NVS region at de63a000 (2097152 bytes)
[    0.176732] PM: Registering ACPI NVS region at dfdbf000 (1048576 bytes)
[    0.182901] print_constraints: dummy: 
[    0.183010] Time: 14:48:30  Date: 01/21/12
[    0.183122] NET: Registered protocol family 16
[    0.183295] Trying to unpack rootfs image as initramfs...
[    0.183598] Extended Config Space enabled on 0 nodes
[    0.183650] ACPI: bus type pci registered
[    0.183899] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.183909] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.204511] PCI: Using configuration type 1 for base access
[    0.206885] bio: create slab <bio-0> at 0
[    0.210455] ACPI: EC: Look up EC in DSDT
[    0.214131] ACPI: Executed 1 blocks of module-level executable AML code
[    0.221048] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.241234] ACPI: Interpreter enabled
[    0.241245] ACPI: (supports S0 S3 S4 S5)
[    0.241301] ACPI: Using IOAPIC for interrupt routing
[    0.429074] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.429506] ACPI: No dock devices found.
[    0.429513] HEST: Table not found.
[    0.429522] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.429867] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.430366] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.430374] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.430382] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.430389] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.430396] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.430403] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.430410] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.430417] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.430423] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.430430] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.430437] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.430443] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.430450] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.430457] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.430463] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.430470] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf7ffffff]
[    0.430477] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xffffffff]
[    0.430495] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000ce3ff]
[    0.430527] pci 0000:00:00.0: [1022:1510] type 0 class 0x000600
[    0.430605] pci 0000:00:01.0: [1002:9807] type 0 class 0x000300
[    0.430626] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.430641] pci 0000:00:01.0: reg 14: [io  0x4000-0x40ff]
[    0.430656] pci 0000:00:01.0: reg 18: [mem 0xf0400000-0xf043ffff]
[    0.430718] pci 0000:00:01.0: supports D1 D2
[    0.430753] pci 0000:00:01.1: [1002:1314] type 0 class 0x000403
[    0.430771] pci 0000:00:01.1: reg 10: [mem 0xf0444000-0xf0447fff]
[    0.430848] pci 0000:00:01.1: supports D1 D2
[    0.430990] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.431023] pci 0000:00:11.0: reg 10: [io  0x4118-0x411f]
[    0.431042] pci 0000:00:11.0: reg 14: [io  0x4124-0x4127]
[    0.431060] pci 0000:00:11.0: reg 18: [io  0x4110-0x4117]
[    0.431079] pci 0000:00:11.0: reg 1c: [io  0x4120-0x4123]
[    0.431097] pci 0000:00:11.0: reg 20: [io  0x4100-0x410f]
[    0.431116] pci 0000:00:11.0: reg 24: [mem 0xf044c000-0xf044c3ff]
[    0.431195] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.431220] pci 0000:00:12.0: reg 10: [mem 0xf044b000-0xf044bfff]
[    0.431335] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.432038] pci 0000:00:12.2: reg 10: [mem 0xf044a000-0xf044a0ff]
[    0.435102] pci 0000:00:12.2: supports D1 D2
[    0.435108] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.435119] pci 0000:00:12.2: PME# disabled
[    0.435173] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.435198] pci 0000:00:13.0: reg 10: [mem 0xf0449000-0xf0449fff]
[    0.435315] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.435898] pci 0000:00:13.2: reg 10: [mem 0xf0448000-0xf04480ff]
[    0.438837] pci 0000:00:13.2: supports D1 D2
[    0.438843] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.438853] pci 0000:00:13.2: PME# disabled
[    0.438895] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.439024] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.439061] pci 0000:00:14.2: reg 10: [mem 0xf0440000-0xf0443fff 64bit]
[    0.439154] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.439163] pci 0000:00:14.2: PME# disabled
[    0.439189] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.439311] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.439397] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.439496] pci 0000:00:15.0: supports D1 D2
[    0.439545] pci 0000:00:15.2: [1002:43a2] type 1 class 0x000604
[    0.439642] pci 0000:00:15.2: supports D1 D2
[    0.439695] pci 0000:00:15.3: [1002:43a3] type 1 class 0x000604
[    0.439792] pci 0000:00:15.3: supports D1 D2
[    0.439844] pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
[    0.440082] pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
[    0.440141] pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
[    0.440203] pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
[    0.440274] pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
[    0.440332] pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
[    0.440390] pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
[    0.440455] pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
[    0.440614] pci 0000:00:14.4: PCI bridge to [bus 01-01] (subtractive decode)
[    0.440625] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.440636] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.440647] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.440655] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.440662] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.440669] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.440677] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.440684] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.440691] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.440699] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.440706] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.440713] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.440721] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.440728] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.440735] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.440742] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.440750] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.440757] pci 0000:00:14.4:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    0.440764] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xffffffff] (subtractive decode)
[    0.440922] pci 0000:00:15.0: PCI bridge to [bus 02-05]
[    0.440934] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    0.440944] pci 0000:00:15.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.440957] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.441079] pci 0000:06:00.0: [1969:2062] type 0 class 0x000200
[    0.441119] pci 0000:06:00.0: reg 10: [mem 0xf0200000-0xf023ffff 64bit]
[    0.441142] pci 0000:06:00.0: reg 18: [io  0x2000-0x207f]
[    0.441266] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.441277] pci 0000:06:00.0: PME# disabled
[    0.448172] pci 0000:00:15.2: PCI bridge to [bus 06-06]
[    0.448193] pci 0000:00:15.2:   bridge window [io  0x2000-0x2fff]
[    0.448204] pci 0000:00:15.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.448218] pci 0000:00:15.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.448389] pci 0000:07:00.0: [14e4:4727] type 0 class 0x000280
[    0.448436] pci 0000:07:00.0: reg 10: [mem 0xf0100000-0xf0103fff 64bit]
[    0.448591] pci 0000:07:00.0: supports D1 D2
[    0.448597] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.448609] pci 0000:07:00.0: PME# disabled
[    0.456203] pci 0000:00:15.3: PCI bridge to [bus 07-07]
[    0.456224] pci 0000:00:15.3:   bridge window [io  0xfffffffffffff000-0x0000] (disabled)
[    0.456237] pci 0000:00:15.3:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.456251] pci 0000:00:15.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.456309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.456691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    0.456791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB2._PRT]
[    0.456918] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB3._PRT]
[    0.457104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.457235]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.457245]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.457250] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.480068] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.480391] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.480706] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.481025] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.481293] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.481520] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.481779] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.482036] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.482403] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.482436] vgaarb: loaded
[    0.482440] vgaarb: bridge control possible 0000:00:01.0
[    0.482942] SCSI subsystem initialized
[    0.483130] libata version 3.00 loaded.
[    0.483256] usbcore: registered new interface driver usbfs
[    0.483285] usbcore: registered new interface driver hub
[    0.483369] usbcore: registered new device driver usb
[    0.483606] PCI: Using ACPI for IRQ routing
[    0.486734] PCI: pci_cache_line_size set to 64 bytes
[    0.486954] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.486967] reserve RAM buffer: 00000000de63a000 - 00000000dfffffff 
[    0.486975] reserve RAM buffer: 00000000dfd3f000 - 00000000dfffffff 
[    0.486983] reserve RAM buffer: 00000000dff00000 - 00000000dfffffff 
[    0.486988] reserve RAM buffer: 000000010f000000 - 000000010fffffff 
[    0.487250] NetLabel: Initializing
[    0.487256] NetLabel:  domain hash size = 128
[    0.487260] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.487292] NetLabel:  unlabeled traffic allowed by default
[    0.487458] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.487470] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.489074] Switching to clocksource hpet
[    0.490411] Switched to NOHz mode on CPU #0
[    0.490582] Switched to NOHz mode on CPU #1
[    0.505442] AppArmor: AppArmor Filesystem Enabled
[    0.505520] pnp: PnP ACPI init
[    0.505562] ACPI: bus type pnp registered
[    0.505947] pnp 00:00: [bus 00-ff]
[    0.505956] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.505963] pnp 00:00: [io  0x0d00-0xffff window]
[    0.505970] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.505977] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.505984] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.505991] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.505997] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.506003] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.506009] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.506016] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.506022] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.506028] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.506034] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.506040] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.506047] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.506053] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
[    0.506059] pnp 00:00: [mem 0xfc000000-0xffffffff window]
[    0.506066] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.506206] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.506351] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.506359] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.506489] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.506499] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.506509] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.506914] pnp 00:02: [irq 0 disabled]
[    0.507010] pnp 00:02: [irq 8]
[    0.507016] pnp 00:02: [mem 0xfed00000-0xfed003ff]
[    0.507095] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.507297] pnp 00:03: [io  0x0000-0x000f]
[    0.507304] pnp 00:03: [io  0x0081-0x008f]
[    0.507310] pnp 00:03: [io  0x00c0-0x00df]
[    0.507317] pnp 00:03: [dma 4]
[    0.507397] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.507435] pnp 00:04: [io  0x00f0-0x00fe]
[    0.507508] pnp 00:04: [irq 13]
[    0.507586] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.507693] pnp 00:05: [io  0x0070-0x0071]
[    0.507774] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.507801] pnp 00:06: [io  0x0061]
[    0.507881] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.507960] pnp 00:07: [io  0x0060]
[    0.507965] pnp 00:07: [io  0x0064]
[    0.508093] pnp 00:07: [irq 1]
[    0.508178] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.508608] pnp 00:08: [irq 12]
[    0.508693] pnp 00:08: Plug and Play ACPI device, IDs ETD0500 ETD0001 PNP0f13 (active)
[    0.508777] pnp 00:09: [io  0x0010-0x001f]
[    0.508783] pnp 00:09: [io  0x002e-0x002f]
[    0.508789] pnp 00:09: [io  0x0072-0x0073]
[    0.508801] pnp 00:09: [io  0x0080]
[    0.508806] pnp 00:09: [io  0x00b0-0x00b1]
[    0.508811] pnp 00:09: [io  0x0092]
[    0.508817] pnp 00:09: [io  0x0400-0x04cf]
[    0.508822] pnp 00:09: [io  0x04d0-0x04d1]
[    0.508827] pnp 00:09: [io  0x04d6]
[    0.508833] pnp 00:09: [io  0x0680-0x06ff]
[    0.508838] pnp 00:09: [io  0x077a]
[    0.508843] pnp 00:09: [io  0x0c00-0x0c01]
[    0.508848] pnp 00:09: [io  0x0c14]
[    0.508853] pnp 00:09: [io  0x0c50-0x0c52]
[    0.508858] pnp 00:09: [io  0x0c6c]
[    0.508863] pnp 00:09: [io  0x0c6f]
[    0.508868] pnp 00:09: [io  0x0cd0-0x0cdb]
[    0.509020] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.509029] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.509036] system 00:09: [io  0x04d6] has been reserved
[    0.509043] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.509050] system 00:09: [io  0x077a] has been reserved
[    0.509057] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.509065] system 00:09: [io  0x0c14] has been reserved
[    0.509072] system 00:09: [io  0x0c50-0x0c52] has been reserved
[    0.509079] system 00:09: [io  0x0c6c] has been reserved
[    0.509085] system 00:09: [io  0x0c6f] has been reserved
[    0.509092] system 00:09: [io  0x0cd0-0x0cdb] has been reserved
[    0.509102] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.509233] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.509240] pnp 00:0a: [mem 0xffe00000-0xffffffff]
[    0.509374] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.509384] system 00:0a: [mem 0xffe00000-0xffffffff] has been reserved
[    0.509394] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.576254] pnp: PnP ACPI: found 11 devices
[    0.576266] ACPI: ACPI bus type pnp unregistered
[    0.585593] PCI: max bus depth: 1 pci_try_num: 2
[    0.585663] pci 0000:00:14.4: PCI bridge to [bus 01-01]
[    0.585670] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.585681] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.585690] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.585704] pci 0000:00:15.0: PCI bridge to [bus 02-05]
[    0.585713] pci 0000:00:15.0:   bridge window [io  0x3000-0x3fff]
[    0.585724] pci 0000:00:15.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.585735] pci 0000:00:15.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.585748] pci 0000:00:15.2: PCI bridge to [bus 06-06]
[    0.585756] pci 0000:00:15.2:   bridge window [io  0x2000-0x2fff]
[    0.585766] pci 0000:00:15.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.585775] pci 0000:00:15.2:   bridge window [mem pref disabled]
[    0.585788] pci 0000:00:15.3: PCI bridge to [bus 07-07]
[    0.585792] pci 0000:00:15.3:   bridge window [io  disabled]
[    0.585803] pci 0000:00:15.3:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.585811] pci 0000:00:15.3:   bridge window [mem pref disabled]
[    0.585876] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.585887] pci 0000:00:15.0: setting latency timer to 64
[    0.585902] pci 0000:00:15.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.585912] pci 0000:00:15.2: setting latency timer to 64
[    0.585926] pci 0000:00:15.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.585935] pci 0000:00:15.3: setting latency timer to 64
[    0.585945] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.585952] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.585959] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.585965] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.585972] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.585978] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.585985] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.585991] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.585997] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.586004] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.586010] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.586016] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.586023] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.586029] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.586036] pci_bus 0000:00: resource 18 [mem 0xe0000000-0xf7ffffff]
[    0.586042] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xffffffff]
[    0.586049] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.586056] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.586062] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.586068] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.586074] pci_bus 0000:01: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.586081] pci_bus 0000:01: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.586087] pci_bus 0000:01: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.586093] pci_bus 0000:01: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.586100] pci_bus 0000:01: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.586106] pci_bus 0000:01: resource 13 [mem 0x000dc000-0x000dffff]
[    0.586113] pci_bus 0000:01: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.586119] pci_bus 0000:01: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.586125] pci_bus 0000:01: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.586132] pci_bus 0000:01: resource 17 [mem 0x000ec000-0x000effff]
[    0.586138] pci_bus 0000:01: resource 18 [mem 0xe0000000-0xf7ffffff]
[    0.586144] pci_bus 0000:01: resource 19 [mem 0xfc000000-0xffffffff]
[    0.586151] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.586157] pci_bus 0000:02: resource 1 [mem 0xf0300000-0xf03fffff]
[    0.586164] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.586171] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    0.586177] pci_bus 0000:06: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.586184] pci_bus 0000:07: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.586285] NET: Registered protocol family 2
[    0.586730] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.590089] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.596981] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.597754] TCP: Hash tables configured (established 524288 bind 65536)
[    0.597761] TCP reno registered
[    0.597806] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.597890] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.598208] NET: Registered protocol family 1
[    0.598250] pci 0000:00:01.0: Boot video device
[    0.660282] PCI: CLS 64 bytes, default 64
[    0.660294] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.660303] Placing 64MB software IO TLB between ffff8800da63a000 - ffff8800de63a000
[    0.660309] software IO TLB at phys 0xda63a000 - 0xde63a000
[    0.660423] Simple Boot Flag at 0x44 set to 0x1
[    0.661245] audit: initializing netlink socket (disabled)
[    0.661273] type=2000 audit(1327157310.660:1): initialized
[    0.743350] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.789247] VFS: Disk quotas dquot_6.5.2
[    0.789432] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.791418] fuse init (API version 7.16)
[    0.791682] msgmni has been set to 7343
[    0.793282] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.793439] io scheduler noop registered
[    0.793445] io scheduler deadline registered
[    0.793584] io scheduler cfq registered (default)
[    0.794213] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.794277] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.796281] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.797093] ACPI: AC Adapter [ACAD] (off-line)
[    0.797294] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.797308] ACPI: Power Button [PWRB]
[    0.797406] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.797415] ACPI: Sleep Button [SLPB]
[    0.797563] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.797701] ACPI: Lid Switch [LID]
[    0.797805] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.797814] ACPI: Power Button [PWRF]
[    0.797946] ACPI: acpi_idle registered with cpuidle
[    0.868429] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.868484] ERST: Table is not found!
[    0.868691] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.898823] Freeing initrd memory: 13412k freed
[    0.981632] Linux agpgart interface v0.103
[    0.984344] brd: module loaded
[    0.985745] loop: module loaded
[    0.986891] Fixed MDIO Bus: probed
[    0.986952] PPP generic driver version 2.4.2
[    0.987067] tun: Universal TUN/TAP device driver, 1.6
[    0.987073] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.987290] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.987430] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.987610] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.987619] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.987730] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.987825] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.987878] QUIRK: Enable AMD PLL fix
[    0.987969] ehci_hcd 0000:00:12.2: debug port 1
[    0.988067] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf044a000
[    1.000322] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.000645] hub 1-0:1.0: USB hub found
[    1.000655] hub 1-0:1.0: 5 ports detected
[    1.000942] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.001060] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    1.001067] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.001147] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.001232] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.001275] ehci_hcd 0000:00:13.2: debug port 1
[    1.001305] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf0448000
[    1.012129] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.012478] hub 2-0:1.0: USB hub found
[    1.012489] hub 2-0:1.0: 5 ports detected
[    1.012710] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.012835] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.012954] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    1.012963] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.013067] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.013209] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf044b000
[    1.072495] hub 3-0:1.0: USB hub found
[    1.072582] hub 3-0:1.0: 5 ports detected
[    1.072903] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.073029] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.073038] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.073143] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.073228] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0449000
[    1.132663] hub 4-0:1.0: USB hub found
[    1.132751] hub 4-0:1.0: 5 ports detected
[    1.133000] uhci_hcd: USB Universal Host Controller Interface driver
[    1.133187] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS1] at 0x60,0x64 irq 1,12
[    1.177703] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.177719] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.178083] mousedev: PS/2 mouse device common for all mice
[    1.179867] rtc_cmos 00:05: RTC can wake from S4
[    1.180131] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.180174] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.180554] device-mapper: uevent: version 1.0.3
[    1.180802] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.180987] cpuidle: using governor ladder
[    1.181260] cpuidle: using governor menu
[    1.181265] EFI Variables Facility v0.08 2004-May-17
[    1.181847] TCP cubic registered
[    1.182231] NET: Registered protocol family 10
[    1.183500] NET: Registered protocol family 17
[    1.183552] Registering the dns_resolver key type
[    1.183849] PM: Hibernation image not present or could not be loaded.
[    1.183878] registered taskstats version 1
[    1.225303]   Magic number: 12:817:839
[    1.225567] rtc_cmos 00:05: setting system clock to 2012-01-21 14:48:31 UTC (1327157311)
[    1.225587] powernow-k8: Found 1 AMD C-60 APU with Radeon(tm) HD Graphics (2 cpu cores) (version 2.20.00)
[    1.225619] powernow-k8: Core Performance Boosting: on.
[    1.225709] powernow-k8:    0 : pstate 0 (1000 MHz)
[    1.225714] powernow-k8:    1 : pstate 1 (800 MHz)
[    1.226229] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.226238] EDD information not available.
[    1.231590] Freeing unused kernel memory: 988k freed
[    1.232498] Write protecting the kernel read-only data: 12288k
[    1.233318] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.256058] Freeing unused kernel memory: 2036k freed
[    1.278929] Freeing unused kernel memory: 1388k freed
[    1.328598] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.339626] udevd[81]: starting version 173
[    1.652560] ACPI: Battery Slot [BAT1] (battery present)
[    1.660139] Refined TSC clocksource calibration: 997.501 MHz.
[    1.660154] Switching to clocksource tsc
[    2.076899] ahci 0000:00:11.0: version 3.0
[    2.077019] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.077226] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    2.077237] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.089388] atl1c 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.089485] atl1c 0000:06:00.0: setting latency timer to 64
[    2.090319] scsi0 : ahci
[    2.090664] ata1: SATA max UDMA/133 abar m1024@0xf044c000 port 0xf044c100 irq 19
[    2.217562] atl1c 0000:06:00.0: version 1.0.1.0-NAPI
[    2.580402] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.583735] ata1.00: ATA-8: WDC WD5000BPVT-22HXZT3, 01.01A01, max UDMA/133
[    2.583749] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.587561] ata1.00: configured for UDMA/133
[    2.588300] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BPVT-2 01.0 PQ: 0 ANSI: 5
[    2.588698] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.588771] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.588777] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.589404] sd 0:0:0:0: [sda] Write Protect is off
[    2.589416] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.589703] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.915930]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    2.916992] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.908584] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.908594] EXT4-fs (sda5): write access will be enabled during recovery
[    4.072143] EXT4-fs (sda5): orphan cleanup on readonly fs
[    4.072169] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178318
[    4.072240] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178313
[    4.072361] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178311
[    4.072384] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178310
[    4.072434] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178305
[    4.072457] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178272
[    4.072510] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178314
[    4.072531] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1178316
[    4.072577] EXT4-fs (sda5): 8 orphan inodes deleted
[    4.072583] EXT4-fs (sda5): recovery complete
[    4.429077] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.947799] udevd[296]: starting version 173
[   15.019220] lp: driver loaded but no devices found
[   15.045095] Adding 7254012k swap on /dev/sda6.  Priority:-1 extents:1 across:7254012k 
[   15.249716] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.599456] type=1400 audit(1327153725.869:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=515 comm="apparmor_parser"
[   15.612126] type=1400 audit(1327153725.885:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=515 comm="apparmor_parser"
[   15.612593] type=1400 audit(1327153725.885:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=515 comm="apparmor_parser"
[   15.679255] acpi device:01: registered as cooling_device2
[   15.682283] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   15.686365] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.687557] wmi: Mapper loaded
[   15.890082] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.890097] Disabling lock debugging due to kernel taint
[   15.939970] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.958725] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   15.967089] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   16.077588] atl1c 0000:06:00.0: irq 40 for MSI/MSI-X
[   16.174831] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.188219] cfg80211: Calling CRDA to update world regulatory domain
[   16.278179] brcmutil: module is from the staging directory, the quality is unknown, you have been warned.
[   16.299775] Linux video capture interface: v2.00
[   16.314917] brcmsmac: module is from the staging directory, the quality is unknown, you have been warned.
[   16.338613] brcmsmac 0000:07:00.0: bus 7 slot 0 func 0 irq 11
[   16.338850] brcmsmac 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.338865] brcmsmac 0000:07:00.0: setting latency timer to 64
[   16.344676] uvcvideo: Found UVC 1.00 device WebCam (064e:d214)
[   16.365790] input: WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input6
[   16.365991] usbcore: registered new interface driver uvcvideo
[   16.365997] USB Video Class driver (v1.1.0)
[   16.438419] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.438546] HDA Intel 0000:00:01.1: irq 41 for MSI/MSI-X
[   16.438601] HDA Intel 0000:00:01.1: setting latency timer to 64
[   16.468762] [fglrx] Maximum main memory to use for locked dma buffers: 3532 MBytes.
[   16.468900] [fglrx]   vendor: 1002 device: 9807 count: 1
[   16.470359] [fglrx] ioport: bar 1, base 0x4000, size: 0x100
[   16.470395] pci 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.470442] pci 0000:00:01.0: setting latency timer to 64
[   16.471669] [fglrx] Kernel PAT support is enabled
[   16.471727] [fglrx] module loaded - fglrx 8.91.4 [Oct 25 2011] with 1 minors
[   16.485214] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   16.487958] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input7
[   16.488754] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.489103] HDA Intel 0000:00:14.2: setting latency timer to 64
[   16.501487] type=1400 audit(1327153726.773:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=711 comm="apparmor_parser"
[   16.504513] type=1400 audit(1327153726.777:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=712 comm="apparmor_parser"
[   16.505389] type=1400 audit(1327153726.777:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=712 comm="apparmor_parser"
[   16.505857] type=1400 audit(1327153726.777:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=712 comm="apparmor_parser"
[   16.533686] type=1400 audit(1327153726.805:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=714 comm="apparmor_parser"
[   16.542720] type=1400 audit(1327153726.813:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=727 comm="apparmor_parser"
[   16.557558] type=1400 audit(1327153726.829:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=714 comm="apparmor_parser"
[   16.561272] hda_codec: CX20588: BIOS auto-probing.
[   16.847773] init: apport pre-start process (787) terminated with status 1
[   16.888648] init: apport post-stop process (816) terminated with status 1
[   16.939217] elantech: assuming hardware version 2, firmware version 4.2.19
[   17.043650] elantech: Synaptics capabilities query result 0x68, 0x18, 0x0c.
[   17.418741] acer_wmi: Acer Laptop ACPI-WMI Extras
[   17.418774] acer_wmi: No or unsupported WMI interface, unable to load
[   17.436081] elantech: retrying ps2 command 0xe6 (2).
[   17.557734] Bluetooth: Core ver 2.16
[   17.557807] NET: Registered protocol family 31
[   17.557812] Bluetooth: HCI device and connection manager initialized
[   17.557820] Bluetooth: HCI socket layer initialized
[   17.557825] Bluetooth: L2CAP socket layer initialized
[   17.563414] Bluetooth: SCO socket layer initialized
[   17.575565] Bluetooth: RFCOMM TTY layer initialized
[   17.575580] Bluetooth: RFCOMM socket layer initialized
[   17.575586] Bluetooth: RFCOMM ver 1.11
[   17.579904] cfg80211: World regulatory domain updated:
[   17.579918] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.579927] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.579934] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.579942] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.579949] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.579956] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.587557] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.587566] Bluetooth: BNEP filters: protocol multicast
[   17.679407] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.679419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679426] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.679434] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679441] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.679448] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679455] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.679462] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679468] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.679475] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679482] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.679489] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679495] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.679502] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679508] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.679515] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679521] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.679528] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679534] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.679541] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679547] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.679554] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679560] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.679567] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679573] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.679580] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.679586] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   17.679593] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   17.699512] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.708843] cfg80211: Calling CRDA for country: XV
[   17.724362] lib80211: common routines for IEEE802.11 drivers
[   17.724373] lib80211_crypt: registered algorithm 'NULL'
[   17.938953] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
[   17.938970] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
[   17.941766] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
[   17.943291] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.956726] elantech: retrying ps2 command 0xf8 (2).
[   18.151392] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   18.151403] vesafb: scrolling: redraw
[   18.151411] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   18.154527] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90006080000, using 3072k, total 3072k
[   18.157329] Console: switching to colour frame buffer device 128x48
[   18.157406] fb0: VESA VGA frame buffer device
[   18.193997] ppdev: user-space parallel port driver
[   18.660338] elantech: retrying ps2 command 0xf8 (1).
[   18.916119] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   19.020446] [fglrx] ATIF platform detected with notification ID: 0x81
[   19.267844] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[   20.666103] wlan0: authenticate with 00:26:5a:b1:d8:f6 (try 1)
[   20.672042] wlan0: authenticated
[   20.673305] wlan0: associate with 00:26:5a:b1:d8:f6 (try 1)
[   20.677488] wlan0: RX AssocResp from 00:26:5a:b1:d8:f6 (capab=0xc31 status=0 aid=2)
[   20.677500] wlan0: associated
[   20.678739] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: true (implement)
[   20.678751] ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
[   20.678776] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   20.680136] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.681219] cfg80211: Pending regulatory request, waiting for it to be processed...
[   20.773254] fglrx_pci 0000:00:01.0: irq 42 for MSI/MSI-X
[   20.774846] [fglrx] Firegl kernel thread PID: 1174
[   20.775291] [fglrx] Firegl kernel thread PID: 1175
[   20.775657] [fglrx] Firegl kernel thread PID: 1176
[   20.775859] [fglrx] IRQ 42 Enabled
[   20.879011] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[   20.891505] [fglrx] Gart USWC size:1152 M.
[   20.891516] [fglrx] Gart cacheable size:457 M.
[   20.891529] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   20.891537] [fglrx] Reserved FB block: Unshared offset:fc57000, size:39d000 
[   20.891544] [fglrx] Reserved FB block: Unshared offset:fff4000, size:c000 
[   25.773967] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   31.560048] wlan0: no IPv6 routers present
[  137.185150] audit_printk_skb: 21 callbacks suppressed
[  137.185161] type=1400 audit(1327153848.008:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1951 comm="apparmor_parser"
[  137.188148] type=1400 audit(1327153848.008:20): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1952 comm="apparmor_parser"
[  137.189073] type=1400 audit(1327153848.012:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1952 comm="apparmor_parser"
[  137.189539] type=1400 audit(1327153848.012:22): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1952 comm="apparmor_parser"
[  137.210585] type=1400 audit(1327153848.032:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/mission-control-5" pid=1955 comm="apparmor_parser"
[  137.220589] type=1400 audit(1327153848.044:24): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=1953 comm="apparmor_parser"
[  137.221605] type=1400 audit(1327153848.044:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=1955 comm="apparmor_parser"
[  137.235589] type=1400 audit(1327153848.056:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1956 comm="apparmor_parser"
[  137.241170] type=1400 audit(1327153848.064:27): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=1953 comm="apparmor_parser"
[  137.242349] type=1400 audit(1327153848.064:28): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1956 comm="apparmor_parser"
[  137.366025] init: rc-sysinit main process (1926) killed by TERM signal
[  137.371083] init: apport pre-start process (1979) terminated with status 1
[  137.395718] init: apport post-stop process (1995) terminated with status 1
[  138.072617] init: plymouth-stop pre-start process (2096) terminated with status 1

```

---

### Post by sffvba[e0rt on 2012-01-21
Well I didn't get anymore wiser from that info :(

All I saw that makes me a bit suspicious is that you are using Radeon graphics.  Do you know if you have the drivers installed?  (Even though I am not so sure it is video related as this is happening intermittently).



404

---

### Post by Agusia on 2012-01-21
> **not found said:**
> Well I didn't get anymore wider from that info :(

All I saw that makes me a bit suspicious is that you are using Radeon graphics.  Do you know if you have the drivers installed?  (Even though I am not so sure it is video related as this is happening intermittently).



404

Yes, I have Radeon. I have some problems with drivers for it. I attach screen. Sorry that it is in polish. I can install the third driver, but then I have a sign in right down corner of the screen: AMD Unsupported hardware (print screen doesn't capture it). When I try to install the first driver, I get error and link to jockey.log:

```
2012-01-20 23:10:07,628 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70>
2012-01-20 23:11:16,449 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2012-01-20 23:11:18,181 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-20 23:11:18,192 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-20 23:11:18,693 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-20 23:11:19,060 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-20 23:11:19,659 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-20 23:11:19,688 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-20 23:11:19,689 DEBUG: nvidia.available: falling back to default
2012-01-20 23:11:20,378 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-20 23:11:20,402 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-20 23:11:20,458 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-20 23:11:20,458 DEBUG: nvidia.available: falling back to default
2012-01-20 23:11:20,824 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-20 23:11:20,865 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-20 23:11:20,891 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-20 23:11:20,892 DEBUG: nvidia.available: falling back to default
2012-01-20 23:11:21,216 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-20 23:11:21,217 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-20 23:11:21,349 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-20 23:11:21,384 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-20 23:11:21,385 DEBUG: nvidia.available: falling back to default
2012-01-20 23:11:21,591 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-20 23:11:21,602 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-20 23:11:21,617 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-20 23:11:21,617 DEBUG: nvidia.available: falling back to default
2012-01-20 23:11:21,840 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-20 23:11:21,859 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-20 23:11:21,883 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-20 23:11:21,884 DEBUG: nvidia.available: falling back to default
2012-01-20 23:11:22,114 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-20 23:11:22,114 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-20 23:11:22,154 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-01-20 23:11:22,179 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-20 23:11:22,180 DEBUG: fglrx.available: falling back to default
2012-01-20 23:11:22,687 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-20 23:11:22,713 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-20 23:11:22,759 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-20 23:11:22,759 DEBUG: fglrx.available: falling back to default
2012-01-20 23:11:23,163 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-20 23:11:23,164 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-20 23:11:23,184 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-20 23:11:23,184 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-20 23:11:23,279 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-20 23:11:23,280 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-20 23:11:23,473 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-20 23:11:23,474 DEBUG: Firmware for DVB cards not available
2012-01-20 23:11:23,475 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-20 23:11:23,604 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-20 23:11:23,849 DEBUG: Software modem not available
2012-01-20 23:11:23,850 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-20 23:11:24,070 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-20 23:11:24,071 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-20 23:11:24,072 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-20 23:11:24,111 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-20 23:11:24,112 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-20 23:11:24,113 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-20 23:11:24,114 DEBUG: all custom handlers loaded
2012-01-20 23:11:24,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-20 23:11:24,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-20 23:11:24,138 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:24,588 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:24,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-20 23:11:24,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-20 23:11:24,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-20 23:11:26,671 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-20 23:11:26,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-20 23:11:26,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-20 23:11:26,816 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-20 23:11:26,816 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:26,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-20 23:11:26,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'platform:pcspkr')
2012-01-20 23:11:26,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-20 23:11:26,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,820 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-20 23:11:26,820 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'platform:regulatory')
2012-01-20 23:11:26,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-20 23:11:26,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-20 23:11:26,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-20 23:11:26,941 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-20 23:11:26,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,942 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-20 23:11:26,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-20 23:11:26,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-20 23:11:26,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:26,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-20 23:11:26,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-20 23:11:26,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-20 23:11:26,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:26,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-20 23:11:27,514 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:27,514 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:26,983 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-20 23:11:27,539 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-01-20 23:11:27,560 DEBUG: fglrx.available: falling back to default
2012-01-20 23:11:27,839 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:27,840 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:27,686 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-20 23:11:27,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-20 23:11:27,983 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:27,984 DEBUG: fglrx is not the alternative in use
2012-01-20 23:11:27,841 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-20 23:11:27,998 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-20 23:11:28,021 DEBUG: fglrx.available: falling back to default
2012-01-20 23:11:28,321 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:28,322 DEBUG: fglrx is not the alternative in use
2012-01-20 23:11:28,173 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-20 23:11:28,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-20 23:11:28,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-20 23:11:28,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:28,345 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-20 23:11:28,346 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:28,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-20 23:11:28,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:28,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-20 23:11:28,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-01-20 23:11:29,196 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:28,636 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-20 23:11:29,687 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:29,197 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-20 23:11:29,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-01-20 23:11:29,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:29,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-01-20 23:11:29,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:29,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-01-20 23:11:30,168 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:29,690 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-20 23:11:30,647 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:30,169 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-20 23:11:30,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-20 23:11:30,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-20 23:11:30,651 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:30,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-20 23:11:30,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-20 23:11:30,672 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-01-20 23:11:30,673 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-20 23:11:30,674 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:30,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-20 23:11:30,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-20 23:11:30,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,771 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-20 23:11:30,772 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-20 23:11:30,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-20 23:11:30,774 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:30,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-20 23:11:30,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-20 23:11:30,790 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-01-20 23:11:30,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-20 23:11:30,823 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-20 23:11:30,824 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-20 23:11:30,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-20 23:11:30,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:30,827 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-20 23:11:30,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-20 23:11:30,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-20 23:11:30,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-20 23:11:30,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-20 23:11:30,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:30,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-20 23:11:30,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-01-20 23:11:30,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-20 23:11:30,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-20 23:11:30,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-20 23:11:30,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,849 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-20 23:11:30,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-20 23:11:30,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-20 23:11:30,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-01-20 23:11:30,948 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,949 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-01-20 23:11:30,949 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-20 23:11:30,950 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-20 23:11:30,950 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-20 23:11:30,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-20 23:11:30,952 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,952 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-20 23:11:30,952 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-20 23:11:30,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-20 23:11:30,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-20 23:11:30,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b0ba70> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-20 23:11:30,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-20 23:11:30,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-20 23:11:30,978 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-20 23:11:30,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-20 23:11:30,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-20 23:11:30,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-20 23:11:30,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-20 23:11:30,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-20 23:11:30,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-20 23:11:30,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'platform:pcspkr')
2012-01-20 23:11:30,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'platform:regulatory')
2012-01-20 23:11:30,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-20 23:11:30,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-20 23:11:30,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-20 23:11:30,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-20 23:11:30,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-20 23:11:30,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-20 23:11:30,995 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-20 23:11:30,995 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-20 23:11:30,995 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-20 23:11:30,996 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,996 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-20 23:11:30,996 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,996 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-20 23:11:30,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-20 23:11:30,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-20 23:11:30,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-20 23:11:30,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-20 23:11:30,997 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-20 23:11:30,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-20 23:11:30,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-20 23:11:30,998 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:30,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-20 23:11:30,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-20 23:11:30,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-20 23:11:30,999 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:31,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-20 23:11:31,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:31,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-20 23:11:31,000 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-20 23:11:31,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-20 23:11:31,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-20 23:11:31,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-20 23:11:31,001 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-20 23:11:31,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-20 23:11:31,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-20 23:11:31,007 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-20 23:11:31,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-20 23:11:31,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-20 23:11:31,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-20 23:11:31,008 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-20 23:11:31,009 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-20 23:11:31,009 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-20 23:11:31,009 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-20 23:11:31,009 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-20 23:11:31,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d143f8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-20 23:11:31,184 DEBUG: handler xorg:fglrx_updates previously unseen
2012-01-20 23:11:31,184 DEBUG: handler kmod:wl previously unseen
2012-01-20 23:11:32,147 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:32,148 DEBUG: handler kmod:wl previously unused
2012-01-20 23:11:32,148 DEBUG: handler xorg:fglrx previously unseen
2012-01-20 23:11:32,148 DEBUG: writing back check cache /var/cache/jockey/check
2012-01-20 23:11:32,291 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:32,292 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:32,783 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:32,784 DEBUG: kmod:wl is already enabled or not available, not announcing
2012-01-20 23:11:32,926 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:32,926 DEBUG: fglrx is not the alternative in use
2012-01-20 23:11:33,143 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:33,144 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:33,687 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:34,691 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:45,208 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:45,209 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:45,816 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:46,295 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:46,440 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:46,441 DEBUG: fglrx is not the alternative in use
2012-01-20 23:11:46,587 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:46,587 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:46,787 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:46,787 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:11:47,077 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:47,553 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:11:57,880 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-01-20 23:11:57,881 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:12:10,206 DEBUG: Installing package: fglrx-updates
2012-01-20 23:12:11,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-01-20 23:12:11,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-01-20 23:12:11,827 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-01-20 23:12:11,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2012-01-20 23:12:11,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.006262
2012-01-20 23:12:12,412 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.352596
2012-01-20 23:12:12,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.793384
2012-01-20 23:12:13,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.301640
2012-01-20 23:12:13,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.816642
2012-01-20 23:12:14,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.342889
2012-01-20 23:12:14,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.974835
2012-01-20 23:12:15,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.305426
2012-01-20 23:12:15,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.142024
2012-01-20 23:12:16,428 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.136047
2012-01-20 23:12:16,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.980713
2012-01-20 23:12:16,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.990161
2012-01-20 23:12:16,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.064695
2012-01-20 23:12:16,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.084325
2012-01-20 23:12:17,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.303239
2012-01-20 23:12:17,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.675079
2012-01-20 23:12:18,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.382009
2012-01-20 23:12:18,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.226123
2012-01-20 23:12:19,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.205171
2012-01-20 23:12:19,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.300395
2012-01-20 23:12:20,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.309391
2012-01-20 23:12:20,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.403845
2012-01-20 23:12:21,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.543278
2012-01-20 23:12:21,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.633235
2012-01-20 23:12:22,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.849131
2012-01-20 23:12:22,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.152735
2012-01-20 23:12:23,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.504053
2012-01-20 23:12:23,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.903874
2012-01-20 23:12:24,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.328920
2012-01-20 23:12:24,884 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.639271
2012-01-20 23:12:25,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.170016
2012-01-20 23:12:25,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.694014
2012-01-20 23:12:26,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.262990
2012-01-20 23:12:26,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.879194
2012-01-20 23:12:27,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.578608
2012-01-20 23:12:27,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.437695
2012-01-20 23:12:28,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.515749
2012-01-20 23:12:28,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.562924
2012-01-20 23:12:29,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.793196
2012-01-20 23:12:29,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.000752
2012-01-20 23:12:30,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.161194
2012-01-20 23:12:30,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.287903
2012-01-20 23:12:31,410 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.232449
2012-01-20 23:12:31,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.374899
2012-01-20 23:12:32,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.497110
2012-01-20 23:12:32,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.875218
2012-01-20 23:12:33,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.141839
2012-01-20 23:12:33,919 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.178591
2012-01-20 23:12:34,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.368269
2012-01-20 23:12:34,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.623166
2012-01-20 23:12:35,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.952277
2012-01-20 23:12:35,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.326366
2012-01-20 23:12:36,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.526971
2012-01-20 23:12:36,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.195987
2012-01-20 23:12:37,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.747741
2012-01-20 23:12:37,935 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.214036
2012-01-20 23:12:38,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.590375
2012-01-20 23:12:38,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.128635
2012-01-20 23:12:39,440 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.545455
2012-01-20 23:12:39,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.018496
2012-01-20 23:12:40,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.579246
2012-01-20 23:12:40,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.295172
2012-01-20 23:12:41,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.696248
2012-01-20 23:12:41,950 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.367195
2012-01-20 23:12:42,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.473663
2012-01-20 23:12:42,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.535922
2012-01-20 23:12:43,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.314817
2012-01-20 23:12:44,158 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.887580
2012-01-20 23:12:44,659 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.760930
2012-01-20 23:12:45,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.638777
2012-01-20 23:12:45,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.426668
2012-01-20 23:12:46,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.315760
2012-01-20 23:12:46,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.925986
2012-01-20 23:12:47,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.540710
2012-01-20 23:12:47,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.461287
2012-01-20 23:12:48,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.422344
2012-01-20 23:12:48,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.180999
2012-01-20 23:12:49,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.939654
2012-01-20 23:12:49,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.558875
2012-01-20 23:12:50,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.292792
2012-01-20 23:12:50,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.080683
2012-01-20 23:12:51,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.823564
2012-01-20 23:12:51,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.836607
2012-01-20 23:12:51,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.697622
2012-01-20 23:12:52,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.330337
2012-01-20 23:12:52,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.960803
2012-01-20 23:12:53,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.499064
2012-01-20 23:12:53,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.223985
2012-01-20 23:12:53,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 100.000000
2012-01-20 23:12:55,483 DEBUG: install progress dpkg-exec 0.000000
2012-01-20 23:12:57,913 DEBUG: install progress libc6-i386 0.000000
2012-01-20 23:12:58,014 DEBUG: install progress libc6-i386 5.000000
2012-01-20 23:12:59,008 DEBUG: install progress libc6-i386 10.000000
2012-01-20 23:12:59,081 DEBUG: install progress libc6-i386 15.000000
2012-01-20 23:12:59,528 DEBUG: install progress lib32gcc1 15.000000
2012-01-20 23:12:59,631 DEBUG: install progress lib32gcc1 20.000000
2012-01-20 23:12:59,747 DEBUG: install progress lib32gcc1 25.000000
2012-01-20 23:12:59,809 DEBUG: install progress lib32gcc1 30.000000
2012-01-20 23:13:00,253 DEBUG: install progress fglrx-updates 30.000000
2012-01-20 23:13:00,355 DEBUG: install progress fglrx-updates 35.000000
2012-01-20 23:13:06,435 DEBUG: install progress fglrx-updates 40.000000
2012-01-20 23:13:06,520 DEBUG: install progress fglrx-updates 45.000000
2012-01-20 23:13:06,788 DEBUG: install progress fglrx-amdcccle-updates 45.000000
2012-01-20 23:13:06,890 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2012-01-20 23:13:07,452 DEBUG: install progress fglrx-amdcccle-updates 55.000000
2012-01-20 23:13:07,514 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-01-20 23:13:07,590 DEBUG: install progress ureadahead 60.000000
2012-01-20 23:13:07,986 DEBUG: install progress dpkg-exec 60.000000
2012-01-20 23:13:08,111 DEBUG: install progress libc6-i386 60.000000
2012-01-20 23:13:08,287 DEBUG: install progress libc6-i386 65.000000
2012-01-20 23:13:08,423 DEBUG: install progress libc6-i386 70.000000
2012-01-20 23:13:08,612 DEBUG: install progress lib32gcc1 70.000000
2012-01-20 23:13:08,679 DEBUG: install progress lib32gcc1 75.000000
2012-01-20 23:13:08,781 DEBUG: install progress lib32gcc1 80.000000
2012-01-20 23:13:08,881 DEBUG: install progress fglrx-updates 80.000000
2012-01-20 23:13:09,252 DEBUG: install progress fglrx-updates 85.000000
2012-01-20 23:13:59,190 DEBUG: install progress fglrx-updates 90.000000
2012-01-20 23:13:59,628 DEBUG: install progress bamfdaemon 90.000000
2012-01-20 23:13:59,841 DEBUG: install progress gnome-menus 90.000000
2012-01-20 23:14:00,064 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2012-01-20 23:14:00,153 DEBUG: install progress fglrx-amdcccle-updates 95.000000
2012-01-20 23:14:00,209 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-01-20 23:14:00,278 DEBUG: install progress libc-bin 100.000000
2012-01-20 23:14:00,569 DEBUG: install progress initramfs-tools 100.000000
2012-01-20 23:14:30,811 DEBUG: Selecting previously deselected package libc6-i386.
(Reading database ... 128288 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.13-20ubuntu5_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libc6-i386 (2.13-20ubuntu5) ...
Setting up lib32gcc1 (1:4.6.1-9ubuntu3) ...
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.911 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod.......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic

2012-01-20 23:14:31,554 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-01-20 23:14:31,826 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-01-20 23:14:32,022 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:32,023 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:32,108 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:32,108 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:32,236 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:32,237 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:32,323 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:32,324 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:45,863 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:45,863 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:45,957 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:45,958 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:46,260 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:14:46,739 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:14:46,896 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:46,896 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-20 23:14:47,071 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:47,071 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:47,165 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:47,166 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:47,375 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:47,376 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:47,470 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:47,470 DEBUG: fglrx_updates is not the alternative in use
2012-01-20 23:14:47,771 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:14:48,257 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-20 23:14:50,369 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-20 23:14:50,369 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-20 23:14:57,814 DEBUG: Shutting down
2012-01-21 01:25:56,592 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70>
2012-01-21 01:26:03,270 DEBUG: reading modalias file /lib/modules/3.0.0-15-generic/modules.alias
2012-01-21 01:26:03,634 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-21 01:26:03,636 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-21 01:26:03,749 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-21 01:26:03,824 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-21 01:26:03,918 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-21 01:26:03,933 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-21 01:26:03,934 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:04,201 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:26:04,212 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-21 01:26:04,227 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-21 01:26:04,228 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:04,356 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:26:04,370 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-21 01:26:04,384 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-21 01:26:04,385 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:04,501 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:04,502 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-21 01:26:04,524 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-21 01:26:04,539 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-21 01:26:04,540 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:04,677 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:04,689 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-21 01:26:04,703 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-21 01:26:04,704 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:04,836 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:26:04,848 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-21 01:26:04,863 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-21 01:26:04,864 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:05,006 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:05,006 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-21 01:26:05,042 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-21 01:26:05,042 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:05,204 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:05,213 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 01:26:05,226 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-21 01:26:05,227 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:05,378 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-21 01:26:05,379 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-21 01:26:05,392 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-21 01:26:05,393 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-21 01:26:05,455 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-21 01:26:05,456 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-21 01:26:05,656 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-21 01:26:05,658 DEBUG: Firmware for DVB cards not available
2012-01-21 01:26:05,659 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-21 01:26:05,733 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-21 01:26:05,781 DEBUG: Software modem not available
2012-01-21 01:26:05,782 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-21 01:26:05,862 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-21 01:26:05,863 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-21 01:26:05,864 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-21 01:26:05,878 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-21 01:26:05,879 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-21 01:26:05,879 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-21 01:26:05,880 DEBUG: all custom handlers loaded
2012-01-21 01:26:05,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 01:26:05,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 01:26:05,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:06,078 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:06,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 01:26:06,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 01:26:06,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:06,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:26:06,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:06,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 01:26:06,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:07,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 01:26:07,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:07,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 01:26:07,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 01:26:07,058 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-21 01:26:07,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,059 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-21 01:26:07,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 01:26:07,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 01:26:07,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 01:26:07,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:07,110 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:26:07,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,111 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:26:07,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 01:26:07,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 01:26:07,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:07,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 01:26:07,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 01:26:07,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-21 01:26:07,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,126 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-01-21 01:26:07,205 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:07,206 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:07,126 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:07,221 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:07,386 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:07,386 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:07,297 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:07,387 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-21 01:26:07,482 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:07,483 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:07,388 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:07,497 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:07,649 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:07,649 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:07,568 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:07,650 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-21 01:26:07,726 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:07,726 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:07,650 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 01:26:07,736 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 01:26:07,752 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:07,920 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:07,921 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:07,833 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 01:26:07,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 01:26:07,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-21 01:26:07,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,939 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-21 01:26:07,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:07,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 01:26:07,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:07,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 01:26:08,058 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-01-21 01:26:08,285 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:08,058 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:08,513 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:08,288 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:08,514 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-01-21 01:26:08,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:08,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-01-21 01:26:08,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:08,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-01-21 01:26:08,738 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:08,516 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:08,975 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:08,739 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:08,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:08,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 01:26:08,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 01:26:08,977 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:08,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:08,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 01:26:08,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 01:26:08,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-01-21 01:26:08,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:08,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 01:26:08,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:08,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:08,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 01:26:08,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 01:26:09,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-21 01:26:09,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 01:26:09,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 01:26:09,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:09,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:09,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 01:26:09,036 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-01-21 01:26:09,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 01:26:09,049 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 01:26:09,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,050 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 01:26:09,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 01:26:09,052 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:09,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 01:26:09,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 01:26:09,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 01:26:09,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 01:26:09,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 01:26:09,055 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:09,055 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 01:26:09,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-01-21 01:26:09,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 01:26:09,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 01:26:09,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 01:26:09,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 01:26:09,071 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 01:26:09,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 01:26:09,105 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-01-21 01:26:09,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,106 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-01-21 01:26:09,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 01:26:09,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:09,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:26:09,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,108 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:26:09,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:26:09,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:09,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 01:26:09,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 01:26:09,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1bcba70> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 01:26:09,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 01:26:09,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 01:26:09,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 01:26:09,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 01:26:09,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:09,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 01:26:09,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:09,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 01:26:09,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 01:26:09,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 01:26:09,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 01:26:09,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 01:26:09,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 01:26:09,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:09,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 01:26:09,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 01:26:09,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 01:26:09,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 01:26:09,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 01:26:09,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 01:26:09,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 01:26:09,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 01:26:09,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 01:26:09,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 01:26:09,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 01:26:09,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 01:26:09,128 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 01:26:09,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 01:26:09,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 01:26:09,129 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 01:26:09,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:09,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 01:26:09,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 01:26:09,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 01:26:09,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 01:26:09,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 01:26:09,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 01:26:09,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 01:26:09,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 01:26:09,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 01:26:09,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 01:26:09,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 01:26:09,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 01:26:09,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:09,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 01:26:09,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 01:26:09,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 01:26:09,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 01:26:09,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 01:26:09,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 01:26:09,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1de5248> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 01:26:09,512 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:09,512 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:09,668 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:09,668 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:09,807 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:09,808 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:10,084 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:10,563 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:10,918 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:11,611 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:11,886 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:12,347 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:12,480 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:12,481 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:12,848 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:12,848 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:13,238 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:13,239 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:13,595 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:13,595 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:13,725 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:13,725 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:13,858 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:13,858 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:14,164 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:14,164 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:14,309 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:14,310 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:14,440 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:14,441 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:14,710 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:15,154 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:15,432 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:15,884 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:16,148 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:16,592 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:25,676 DEBUG: Shutting down
2012-01-21 01:26:29,269 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70>
2012-01-21 01:26:35,840 DEBUG: reading modalias file /lib/modules/3.0.0-15-generic/modules.alias
2012-01-21 01:26:36,164 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-21 01:26:36,165 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-21 01:26:36,276 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-21 01:26:36,348 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-21 01:26:36,368 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-21 01:26:36,381 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-21 01:26:36,382 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:36,635 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:26:36,647 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-21 01:26:36,662 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-21 01:26:36,663 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:36,792 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:26:36,803 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-21 01:26:36,819 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-21 01:26:36,820 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:36,936 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:36,937 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-21 01:26:36,948 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-21 01:26:36,963 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-21 01:26:36,964 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:37,107 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:37,120 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-21 01:26:37,135 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-21 01:26:37,136 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:37,281 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:26:37,297 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-21 01:26:37,313 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-21 01:26:37,314 DEBUG: nvidia.available: falling back to default
2012-01-21 01:26:37,444 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:37,445 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-21 01:26:37,476 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-21 01:26:37,477 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:37,609 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:26:37,620 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 01:26:37,636 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-21 01:26:37,637 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:37,780 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-21 01:26:37,780 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-21 01:26:37,792 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-21 01:26:37,793 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-21 01:26:37,857 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-21 01:26:37,858 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-21 01:26:37,928 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-21 01:26:37,930 DEBUG: Firmware for DVB cards not available
2012-01-21 01:26:37,931 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-21 01:26:38,004 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-21 01:26:38,027 DEBUG: Software modem not available
2012-01-21 01:26:38,028 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-21 01:26:38,106 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-21 01:26:38,107 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-21 01:26:38,107 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-21 01:26:38,121 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-21 01:26:38,123 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-21 01:26:38,123 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-21 01:26:38,124 DEBUG: all custom handlers loaded
2012-01-21 01:26:38,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 01:26:38,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 01:26:38,143 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:38,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:38,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 01:26:38,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 01:26:38,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:39,449 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:26:39,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 01:26:39,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:39,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 01:26:39,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:39,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 01:26:39,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 01:26:39,530 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-21 01:26:39,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-21 01:26:39,532 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 01:26:39,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 01:26:39,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 01:26:39,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:39,597 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:26:39,597 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,598 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:26:39,598 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 01:26:39,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 01:26:39,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:39,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 01:26:39,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 01:26:39,613 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-21 01:26:39,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:39,614 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-01-21 01:26:39,696 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:39,697 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:39,615 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:39,711 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:39,870 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:39,871 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:39,779 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:39,871 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-21 01:26:39,970 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:39,971 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:39,872 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:39,986 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:40,147 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:40,147 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:26:40,054 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:26:40,148 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-21 01:26:40,231 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:40,232 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:40,148 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 01:26:40,243 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 01:26:40,257 DEBUG: fglrx.available: falling back to default
2012-01-21 01:26:40,418 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:26:40,419 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:26:40,330 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 01:26:40,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 01:26:40,435 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-21 01:26:40,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:40,436 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-21 01:26:40,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:40,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 01:26:40,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 01:26:40,575 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-01-21 01:26:40,837 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:40,576 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:41,088 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:40,839 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:41,089 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-01-21 01:26:41,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-01-21 01:26:41,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-01-21 01:26:41,312 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:41,091 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:41,545 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:26:41,313 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:26:41,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 01:26:41,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 01:26:41,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:41,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 01:26:41,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 01:26:41,565 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-01-21 01:26:41,566 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 01:26:41,567 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:41,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 01:26:41,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 01:26:41,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,607 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-21 01:26:41,607 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 01:26:41,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 01:26:41,609 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:41,609 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:41,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 01:26:41,612 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-01-21 01:26:41,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 01:26:41,625 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 01:26:41,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,626 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 01:26:41,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 01:26:41,628 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:41,628 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 01:26:41,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 01:26:41,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 01:26:41,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 01:26:41,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 01:26:41,631 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:41,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 01:26:41,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-01-21 01:26:41,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 01:26:41,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 01:26:41,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 01:26:41,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 01:26:41,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 01:26:41,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 01:26:41,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-01-21 01:26:41,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-01-21 01:26:41,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 01:26:41,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:26:41,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,682 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:26:41,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,683 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:26:41,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,683 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:26:41,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:26:41,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 01:26:41,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 01:26:41,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b14a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 01:26:41,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 01:26:41,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 01:26:41,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 01:26:41,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 01:26:41,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:41,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 01:26:41,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:41,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 01:26:41,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 01:26:41,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 01:26:41,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 01:26:41,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 01:26:41,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 01:26:41,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 01:26:41,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 01:26:41,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 01:26:41,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 01:26:41,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 01:26:41,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 01:26:41,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 01:26:41,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 01:26:41,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 01:26:41,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 01:26:41,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 01:26:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 01:26:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 01:26:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 01:26:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 01:26:41,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 01:26:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 01:26:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:26:41,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 01:26:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 01:26:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 01:26:41,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 01:26:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 01:26:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 01:26:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 01:26:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 01:26:41,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 01:26:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 01:26:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 01:26:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 01:26:41,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 01:26:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 01:26:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 01:26:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 01:26:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 01:26:41,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 01:26:41,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 01:26:41,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2d2e248> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 01:26:41,727 DEBUG: Shutting down
2012-01-21 01:26:56,735 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70>
2012-01-21 01:27:03,650 DEBUG: reading modalias file /lib/modules/3.0.0-15-generic/modules.alias
2012-01-21 01:27:04,052 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-21 01:27:04,053 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-21 01:27:04,198 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-21 01:27:04,257 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-21 01:27:04,278 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-21 01:27:04,300 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-21 01:27:04,301 DEBUG: nvidia.available: falling back to default
2012-01-21 01:27:04,565 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:27:04,575 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-21 01:27:04,591 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-21 01:27:04,591 DEBUG: nvidia.available: falling back to default
2012-01-21 01:27:04,721 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:27:04,733 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-21 01:27:04,749 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-21 01:27:04,750 DEBUG: nvidia.available: falling back to default
2012-01-21 01:27:04,885 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:27:04,886 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-21 01:27:04,898 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-21 01:27:04,914 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-21 01:27:04,914 DEBUG: nvidia.available: falling back to default
2012-01-21 01:27:05,037 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:27:05,047 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-21 01:27:05,063 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-21 01:27:05,064 DEBUG: nvidia.available: falling back to default
2012-01-21 01:27:05,189 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 01:27:05,200 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-21 01:27:05,220 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-21 01:27:05,221 DEBUG: nvidia.available: falling back to default
2012-01-21 01:27:05,346 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:27:05,347 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-21 01:27:05,383 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-21 01:27:05,383 DEBUG: fglrx.available: falling back to default
2012-01-21 01:27:05,543 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 01:27:05,554 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 01:27:05,567 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-21 01:27:05,568 DEBUG: fglrx.available: falling back to default
2012-01-21 01:27:05,750 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-21 01:27:05,750 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-21 01:27:05,763 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-21 01:27:05,764 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-21 01:27:05,828 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-21 01:27:05,829 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-21 01:27:05,912 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-21 01:27:05,914 DEBUG: Firmware for DVB cards not available
2012-01-21 01:27:05,914 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-21 01:27:05,984 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-21 01:27:06,012 DEBUG: Software modem not available
2012-01-21 01:27:06,013 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-21 01:27:06,085 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-21 01:27:06,085 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-21 01:27:06,086 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-21 01:27:06,099 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-21 01:27:06,100 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-21 01:27:06,101 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-21 01:27:06,101 DEBUG: all custom handlers loaded
2012-01-21 01:27:06,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 01:27:06,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 01:27:06,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:06,313 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:06,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 01:27:06,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 01:27:06,314 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 01:27:07,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:27:07,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 01:27:07,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:27:07,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 01:27:07,288 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:07,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 01:27:07,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 01:27:07,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-21 01:27:07,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-21 01:27:07,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 01:27:07,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 01:27:07,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 01:27:07,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 01:27:07,341 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:27:07,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,342 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 01:27:07,342 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 01:27:07,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 01:27:07,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:07,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 01:27:07,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 01:27:07,355 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-21 01:27:07,355 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:07,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-01-21 01:27:07,441 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:27:07,442 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:27:07,356 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:27:07,457 DEBUG: fglrx.available: falling back to default
2012-01-21 01:27:07,629 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:27:07,630 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:27:07,540 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:27:07,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-21 01:27:07,709 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:27:07,710 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:27:07,630 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:27:07,726 DEBUG: fglrx.available: falling back to default
2012-01-21 01:27:07,879 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:27:07,879 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 01:27:07,793 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 01:27:07,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-21 01:27:07,970 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:27:07,971 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:27:07,880 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 01:27:07,982 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 01:27:07,998 DEBUG: fglrx.available: falling back to default
2012-01-21 01:27:08,162 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 01:27:08,162 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 01:27:08,078 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 01:27:08,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 01:27:08,179 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-21 01:27:08,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:08,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-21 01:27:08,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:08,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 01:27:08,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:08,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 01:27:08,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-01-21 01:27:08,511 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:27:08,296 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:27:08,736 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:27:08,512 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:27:08,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-01-21 01:27:08,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:08,738 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-01-21 01:27:08,739 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:08,739 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-01-21 01:27:08,966 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:27:08,739 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:27:09,186 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 01:27:08,968 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 01:27:09,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 01:27:09,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 01:27:09,189 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:09,189 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 01:27:09,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 01:27:09,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-01-21 01:27:09,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 01:27:09,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:09,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 01:27:09,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 01:27:09,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-21 01:27:09,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 01:27:09,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 01:27:09,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:09,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:27:09,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 01:27:09,247 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-01-21 01:27:09,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 01:27:09,260 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 01:27:09,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 01:27:09,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 01:27:09,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:09,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 01:27:09,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 01:27:09,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 01:27:09,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 01:27:09,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 01:27:09,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:09,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 01:27:09,267 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-01-21 01:27:09,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 01:27:09,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 01:27:09,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 01:27:09,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 01:27:09,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 01:27:09,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 01:27:09,315 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-01-21 01:27:09,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,316 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-01-21 01:27:09,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 01:27:09,317 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 01:27:09,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,318 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:27:09,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,318 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:27:09,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,319 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 01:27:09,319 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 01:27:09,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 01:27:09,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 01:27:09,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x121ea70> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 01:27:09,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 01:27:09,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 01:27:09,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 01:27:09,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 01:27:09,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 01:27:09,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 01:27:09,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:27:09,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 01:27:09,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 01:27:09,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 01:27:09,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 01:27:09,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 01:27:09,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 01:27:09,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 01:27:09,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 01:27:09,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 01:27:09,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 01:27:09,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 01:27:09,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 01:27:09,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 01:27:09,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 01:27:09,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 01:27:09,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 01:27:09,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 01:27:09,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 01:27:09,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 01:27:09,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 01:27:09,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 01:27:09,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 01:27:09,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 01:27:09,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 01:27:09,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 01:27:09,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 01:27:09,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 01:27:09,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 01:27:09,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 01:27:09,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 01:27:09,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 01:27:09,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 01:27:09,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 01:27:09,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 01:27:09,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 01:27:09,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 01:27:09,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 01:27:09,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 01:27:09,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 01:27:09,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 01:27:09,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 01:27:09,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 01:27:09,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 01:27:09,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1438248> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 01:27:09,376 DEBUG: Shutting down
2012-01-21 20:09:39,894 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90>
2012-01-21 20:09:46,951 DEBUG: reading modalias file /lib/modules/3.0.0-15-generic/modules.alias
2012-01-21 20:09:47,303 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-21 20:09:47,315 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-21 20:09:47,424 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-21 20:09:47,504 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-21 20:09:47,597 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-21 20:09:47,611 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-21 20:09:47,612 DEBUG: nvidia.available: falling back to default
2012-01-21 20:09:47,897 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 20:09:47,907 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-21 20:09:47,921 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-21 20:09:47,922 DEBUG: nvidia.available: falling back to default
2012-01-21 20:09:48,044 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 20:09:48,055 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-21 20:09:48,067 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-21 20:09:48,068 DEBUG: nvidia.available: falling back to default
2012-01-21 20:09:48,189 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:09:48,190 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-21 20:09:48,213 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-21 20:09:48,227 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-21 20:09:48,228 DEBUG: nvidia.available: falling back to default
2012-01-21 20:09:48,351 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:09:48,362 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-21 20:09:48,376 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-21 20:09:48,377 DEBUG: nvidia.available: falling back to default
2012-01-21 20:09:48,502 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 20:09:48,512 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-21 20:09:48,527 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-21 20:09:48,528 DEBUG: nvidia.available: falling back to default
2012-01-21 20:09:48,653 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:09:48,653 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-21 20:09:48,688 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-21 20:09:48,689 DEBUG: fglrx.available: falling back to default
2012-01-21 20:09:48,826 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:09:48,836 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 20:09:48,850 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-21 20:09:48,850 DEBUG: fglrx.available: falling back to default
2012-01-21 20:09:48,989 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-21 20:09:48,990 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-21 20:09:49,001 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-21 20:09:49,002 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-21 20:09:49,073 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-21 20:09:49,074 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-21 20:09:49,169 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-21 20:09:49,171 DEBUG: Firmware for DVB cards not available
2012-01-21 20:09:49,171 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-21 20:09:49,240 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-21 20:09:49,279 DEBUG: Software modem not available
2012-01-21 20:09:49,280 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-21 20:09:49,347 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-21 20:09:49,348 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-21 20:09:49,349 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-21 20:09:49,364 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-21 20:09:49,366 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-21 20:09:49,366 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-21 20:09:49,367 DEBUG: all custom handlers loaded
2012-01-21 20:09:49,367 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 20:09:49,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 20:09:49,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:49,607 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:49,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 20:09:49,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 20:09:49,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 20:09:50,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 20:09:50,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 20:09:50,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:09:50,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 20:09:50,568 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:50,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 20:09:50,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 20:09:50,571 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-21 20:09:50,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,571 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-21 20:09:50,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 20:09:50,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 20:09:50,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 20:09:50,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 20:09:50,623 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 20:09:50,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,624 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 20:09:50,624 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 20:09:50,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 20:09:50,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:50,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 20:09:50,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 20:09:50,637 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-21 20:09:50,637 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:50,638 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2012-01-21 20:09:51,154 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:51,155 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:50,638 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 20:09:51,167 DEBUG: fglrx.available: falling back to default
2012-01-21 20:09:51,322 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:51,323 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:51,236 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 20:09:51,323 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-21 20:09:51,404 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:51,405 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:51,324 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 20:09:51,418 DEBUG: fglrx.available: falling back to default
2012-01-21 20:09:51,574 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:51,575 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:51,486 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 20:09:51,576 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-21 20:09:51,659 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:51,659 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:09:51,576 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 20:09:51,670 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-01-21 20:09:51,685 DEBUG: fglrx.available: falling back to default
2012-01-21 20:09:51,834 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:51,835 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:09:51,752 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 20:09:51,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 20:09:51,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-21 20:09:51,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:51,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-21 20:09:51,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:51,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 20:09:51,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:51,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 20:09:51,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-01-21 20:09:52,255 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:51,971 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:09:52,481 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:52,257 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:09:52,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-01-21 20:09:52,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:52,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-01-21 20:09:52,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:52,485 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-01-21 20:09:52,720 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:52,485 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:09:52,956 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:52,721 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:09:52,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:52,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFEip02')
2012-01-21 20:09:53,039 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 20:09:53,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 20:09:53,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 20:09:53,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:53,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 20:09:53,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 20:09:53,052 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-01-21 20:09:53,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 20:09:53,054 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:53,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 20:09:53,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 20:09:53,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-21 20:09:53,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 20:09:53,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 20:09:53,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:53,097 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 20:09:53,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-01-21 20:09:53,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:09:53,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v0781p74C3dA5DCdc00dsc00dp00ic08isc06ip50')
2012-01-21 20:09:53,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-01-21 20:09:53,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2012-01-21 20:09:53,108 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 20:09:53,120 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 20:09:53,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,121 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 20:09:53,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 20:09:53,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:53,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 20:09:53,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 20:09:53,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 20:09:53,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 20:09:53,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFDip01')
2012-01-21 20:09:53,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 20:09:53,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:53,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 20:09:53,129 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-01-21 20:09:53,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00ic06isc01ip01')
2012-01-21 20:09:53,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 20:09:53,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 20:09:53,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 20:09:53,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 20:09:53,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 20:09:53,179 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-01-21 20:09:53,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-01-21 20:09:53,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 20:09:53,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:09:53,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 20:09:53,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,182 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 20:09:53,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 20:09:53,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:09:53,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 20:09:53,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 20:09:53,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2081b90> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 20:09:53,195 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 20:09:53,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 20:09:53,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 20:09:53,196 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 20:09:53,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 20:09:53,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 20:09:53,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:09:53,197 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 20:09:53,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 20:09:53,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 20:09:53,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 20:09:53,198 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 20:09:53,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 20:09:53,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 20:09:53,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 20:09:53,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 20:09:53,199 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,200 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 20:09:53,200 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 20:09:53,200 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 20:09:53,200 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 20:09:53,200 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,201 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 20:09:53,201 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,201 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFEip02')
2012-01-21 20:09:53,201 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 20:09:53,201 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 20:09:53,202 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 20:09:53,202 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 20:09:53,202 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 20:09:53,202 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 20:09:53,202 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 20:09:53,202 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 20:09:53,203 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,203 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 20:09:53,203 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,203 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 20:09:53,204 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 20:09:53,204 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:09:53,204 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v0781p74C3dA5DCdc00dsc00dp00ic08isc06ip50')
2012-01-21 20:09:53,204 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,204 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 20:09:53,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 20:09:53,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 20:09:53,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 20:09:53,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 20:09:53,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 20:09:53,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFDip01')
2012-01-21 20:09:53,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 20:09:53,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 20:09:53,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00ic06isc01ip01')
2012-01-21 20:09:53,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 20:09:53,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 20:09:53,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 20:09:53,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 20:09:53,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 20:09:53,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 20:09:53,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 20:09:53,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 20:09:53,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 20:09:53,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2297368> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 20:09:53,375 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:53,375 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:53,719 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:54,173 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:54,317 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:54,318 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:09:54,686 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:54,687 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:54,892 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:09:54,893 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:09:55,180 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:09:55,637 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:10:20,669 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:20,670 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:24,664 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-01-21 20:10:24,918 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-01-21 20:10:25,154 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:25,155 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:25,240 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:25,241 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:42,006 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:42,007 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:42,082 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:42,082 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:42,372 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:10:42,826 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:10:42,978 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:42,979 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:10:43,372 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:43,373 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:43,456 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:43,457 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:43,665 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:43,666 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:43,754 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:43,755 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:10:44,043 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:10:44,508 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:10:45,853 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:45,854 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:10:47,741 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:10:47,742 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:10:48,596 DEBUG: Installing package: fglrx
2012-01-21 20:10:50,102 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-01-21 20:10:50,105 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-01-21 20:10:50,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-01-21 20:10:50,203 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-01-21 20:10:50,245 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.000000
2012-01-21 20:10:50,747 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 0.674494
2012-01-21 20:10:51,249 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 1.536730
2012-01-21 20:10:51,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 2.350486
2012-01-21 20:10:52,253 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 3.226573
2012-01-21 20:10:52,754 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 4.137288
2012-01-21 20:10:53,256 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 5.099945
2012-01-21 20:10:53,758 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 6.180337
2012-01-21 20:10:54,259 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 7.416555
2012-01-21 20:10:54,761 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 8.870928
2012-01-21 20:10:55,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 10.536532
2012-01-21 20:10:55,765 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 12.610746
2012-01-21 20:10:56,266 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 14.809620
2012-01-21 20:10:56,768 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 17.669889
2012-01-21 20:10:57,270 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 20.627115
2012-01-21 20:10:57,772 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 23.594730
2012-01-21 20:10:58,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 25.959818
2012-01-21 20:10:58,775 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 28.428791
2012-01-21 20:10:59,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 31.001647
2012-01-21 20:10:59,779 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 33.307868
2012-01-21 20:11:00,281 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 35.891112
2012-01-21 20:11:00,782 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 38.526299
2012-01-21 20:11:01,284 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 41.158023
2012-01-21 20:11:01,786 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 43.585441
2012-01-21 20:11:02,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 46.231016
2012-01-21 20:11:02,789 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 48.869665
2012-01-21 20:11:03,291 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 49.555299
2012-01-21 20:11:03,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 52.685799
2012-01-21 20:11:04,294 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 55.795254
2012-01-21 20:11:04,796 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 58.440829
2012-01-21 20:11:05,298 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 61.114106
2012-01-21 20:11:05,800 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 63.731979
2012-01-21 20:11:06,301 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 66.460661
2012-01-21 20:11:06,803 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 69.113161
2012-01-21 20:11:07,305 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 71.793364
2012-01-21 20:11:07,807 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 74.386997
2012-01-21 20:11:08,308 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 75.900238
2012-01-21 20:11:08,810 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 79.273000
2012-01-21 20:11:09,312 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 81.852781
2012-01-21 20:11:09,813 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 84.591852
2012-01-21 20:11:10,176 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.541192
2012-01-21 20:11:10,177 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 86.554515
2012-01-21 20:11:10,679 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 89.269346
2012-01-21 20:11:11,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 91.811037
2012-01-21 20:11:11,683 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 94.241918
2012-01-21 20:11:12,185 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 96.773221
2012-01-21 20:11:12,686 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 99.456887
2012-01-21 20:11:12,790 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:5559L> 100.000000
2012-01-21 20:11:14,470 DEBUG: install progress dpkg-exec 0.000000
2012-01-21 20:11:16,920 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-01-21 20:11:16,991 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-01-21 20:11:16,992 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-01-21 20:11:17,293 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-01-21 20:11:17,721 DEBUG: install progress fglrx-updates 18.750000
2012-01-21 20:11:17,823 DEBUG: install progress fglrx-updates 25.000000
2012-01-21 20:11:54,517 DEBUG: install progress fglrx-updates 31.250000
2012-01-21 20:11:55,394 DEBUG: install progress fglrx-updates 37.500000
2012-01-21 20:11:55,541 DEBUG: install progress bamfdaemon 37.500000
2012-01-21 20:11:55,776 DEBUG: install progress gnome-menus 37.500000
2012-01-21 20:11:55,955 DEBUG: install progress ureadahead 37.500000
2012-01-21 20:11:56,159 DEBUG: install progress initramfs-tools 37.500000
2012-01-21 20:12:22,309 DEBUG: install progress libc-bin 37.500000
2012-01-21 20:12:22,804 DEBUG: install progress dpkg-exec 37.500000
2012-01-21 20:12:23,762 DEBUG: install progress fglrx 37.500000
2012-01-21 20:12:23,864 DEBUG: install progress fglrx 43.750000
2012-01-21 20:12:28,436 DEBUG: install progress fglrx 50.000000
2012-01-21 20:12:28,527 DEBUG: install progress fglrx 56.250000
2012-01-21 20:12:28,820 DEBUG: install progress fglrx-amdcccle 56.250000
2012-01-21 20:12:28,822 DEBUG: install progress fglrx-amdcccle 62.500000
2012-01-21 20:12:29,496 DEBUG: install progress fglrx-amdcccle 68.750000
2012-01-21 20:12:29,555 DEBUG: install progress fglrx-amdcccle 75.000000
2012-01-21 20:12:29,623 DEBUG: install progress ureadahead 75.000000
2012-01-21 20:12:30,020 DEBUG: install progress dpkg-exec 75.000000
2012-01-21 20:12:30,143 DEBUG: install progress fglrx 75.000000
2012-01-21 20:12:30,529 DEBUG: install progress fglrx 81.250000
2012-01-21 20:13:00,853 DEBUG: install progress fglrx 87.500000
2012-01-21 20:13:01,379 DEBUG: install progress bamfdaemon 87.500000
2012-01-21 20:13:01,592 DEBUG: install progress gnome-menus 87.500000
2012-01-21 20:13:01,803 DEBUG: install progress fglrx-amdcccle 87.500000
2012-01-21 20:13:01,892 DEBUG: install progress fglrx-amdcccle 93.750000
2012-01-21 20:13:01,960 DEBUG: install progress fglrx-amdcccle 100.000000
2012-01-21 20:13:02,051 DEBUG: install progress initramfs-tools 100.000000
2012-01-21 20:13:27,049 DEBUG: install progress libc-bin 100.000000
2012-01-21 20:13:29,965 DEBUG: (Reading database ... 173697 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 173436 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-15-generic
Building for architecture x86_64
Building initial module for 3.0.0-15-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-15-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-01-21 20:13:30,612 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:00:01.0
2012-01-21 20:14:21,566 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:21,567 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:14:21,902 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:21,903 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:14:22,340 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:22,340 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:14:22,440 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:22,440 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:14:22,855 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:14:23,325 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:14:23,487 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:23,487 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:14:23,812 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:23,812 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:14:24,211 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:24,212 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:14:24,549 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:24,550 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:14:24,992 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:24,993 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:14:25,081 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:14:25,082 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:14:25,370 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:14:25,830 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:14:49,026 DEBUG: Shutting down
2012-01-21 20:16:59,196 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90>
2012-01-21 20:17:06,018 DEBUG: reading modalias file /lib/modules/3.0.0-15-generic/modules.alias
2012-01-21 20:17:06,379 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-01-21 20:17:06,391 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-01-21 20:17:06,506 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-01-21 20:17:06,580 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-01-21 20:17:06,674 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-01-21 20:17:06,688 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-21 20:17:06,689 DEBUG: nvidia.available: falling back to default
2012-01-21 20:17:06,981 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 20:17:06,992 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-21 20:17:07,006 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-21 20:17:07,007 DEBUG: nvidia.available: falling back to default
2012-01-21 20:17:07,132 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 20:17:07,140 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-01-21 20:17:07,155 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-01-21 20:17:07,156 DEBUG: nvidia.available: falling back to default
2012-01-21 20:17:07,284 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:17:07,285 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-01-21 20:17:07,318 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-01-21 20:17:07,332 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-01-21 20:17:07,333 DEBUG: nvidia.available: falling back to default
2012-01-21 20:17:07,514 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:17:07,527 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-01-21 20:17:07,546 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-01-21 20:17:07,547 DEBUG: nvidia.available: falling back to default
2012-01-21 20:17:07,676 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-21 20:17:07,686 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-01-21 20:17:07,699 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-01-21 20:17:07,700 DEBUG: nvidia.available: falling back to default
2012-01-21 20:17:07,827 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:17:07,828 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-01-21 20:17:07,851 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-01-21 20:17:07,866 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-01-21 20:17:07,867 DEBUG: fglrx.available: falling back to default
2012-01-21 20:17:08,007 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-01-21 20:17:08,033 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-01-21 20:17:08,034 DEBUG: fglrx.available: falling back to default
2012-01-21 20:17:08,173 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-01-21 20:17:08,174 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-01-21 20:17:08,184 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-01-21 20:17:08,185 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-01-21 20:17:08,262 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-01-21 20:17:08,262 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-01-21 20:17:08,397 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-01-21 20:17:08,399 DEBUG: Firmware for DVB cards not available
2012-01-21 20:17:08,399 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-01-21 20:17:08,480 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-01-21 20:17:08,529 DEBUG: Software modem not available
2012-01-21 20:17:08,529 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-01-21 20:17:08,641 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-01-21 20:17:08,641 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-01-21 20:17:08,642 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-01-21 20:17:08,658 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-01-21 20:17:08,660 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-01-21 20:17:08,660 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-01-21 20:17:08,660 DEBUG: all custom handlers loaded
2012-01-21 20:17:08,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 20:17:08,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 20:17:08,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:08,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:08,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 20:17:08,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 20:17:08,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 20:17:09,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 20:17:09,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:09,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 20:17:09,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:17:10,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 20:17:10,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:10,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:10,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 20:17:10,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 20:17:10,032 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-01-21 20:17:10,032 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:10,032 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-01-21 20:17:10,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:10,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 20:17:10,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 20:17:10,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 20:17:10,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 20:17:10,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 20:17:10,086 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:10,086 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-01-21 20:17:10,086 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:10,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 20:17:10,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 20:17:10,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:10,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 20:17:10,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 20:17:10,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-01-21 20:17:10,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:10,100 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-01-21 20:17:10,751 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:10,751 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:17:10,100 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 20:17:11,106 DEBUG: fglrx.available: falling back to default
2012-01-21 20:17:11,272 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:11,273 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:17:11,186 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 20:17:11,526 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-01-21 20:17:11,604 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:11,605 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:17:11,526 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 20:17:11,615 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-01-21 20:17:11,628 DEBUG: fglrx.available: falling back to default
2012-01-21 20:17:11,770 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:11,771 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:17:11,693 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-01-21 20:17:11,771 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-01-21 20:17:11,856 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:11,856 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:17:11,772 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 20:17:12,126 DEBUG: fglrx.available: falling back to default
2012-01-21 20:17:12,302 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:12,303 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:17:12,216 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-01-21 20:17:12,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 20:17:12,728 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-01-21 20:17:12,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:12,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-01-21 20:17:12,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:12,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 20:17:12,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:12,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 20:17:12,890 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-01-21 20:17:13,186 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:12,891 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:17:13,528 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:13,187 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:17:13,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-01-21 20:17:13,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:13,530 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-01-21 20:17:13,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:13,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2012-01-21 20:17:13,805 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:13,531 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:17:14,079 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:13,806 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2012-01-21 20:17:14,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFEip02')
2012-01-21 20:17:14,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 20:17:14,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 20:17:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 20:17:14,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:14,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 20:17:14,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 20:17:14,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-01-21 20:17:14,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 20:17:14,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:14,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 20:17:14,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 20:17:14,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-01-21 20:17:14,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 20:17:14,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 20:17:14,232 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:14,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 20:17:14,234 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-01-21 20:17:14,235 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:17:14,236 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v0781p74C3dA5DCdc00dsc00dp00ic08isc06ip50')
2012-01-21 20:17:14,245 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-01-21 20:17:14,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,245 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2012-01-21 20:17:14,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 20:17:14,261 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 20:17:14,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-01-21 20:17:14,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 20:17:14,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:14,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 20:17:14,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 20:17:14,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 20:17:14,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 20:17:14,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFDip01')
2012-01-21 20:17:14,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 20:17:14,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:14,271 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 20:17:14,271 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-01-21 20:17:14,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00ic06isc01ip01')
2012-01-21 20:17:14,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 20:17:14,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 20:17:14,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 20:17:14,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 20:17:14,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 20:17:14,330 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-01-21 20:17:14,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,331 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-01-21 20:17:14,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 20:17:14,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-01-21 20:17:14,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 20:17:14,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 20:17:14,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-01-21 20:17:14,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-01-21 20:17:14,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 20:17:14,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 20:17:14,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2c2db90> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 20:17:14,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0800:')
2012-01-21 20:17:14,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-01-21 20:17:14,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-01-21 20:17:14,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-01-21 20:17:14,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00001314sv00001025sd00000598bc04sc03i00')
2012-01-21 20:17:14,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-01-21 20:17:14,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:17:14,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-01-21 20:17:14,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-01-21 20:17:14,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'platform:pcspkr')
2012-01-21 20:17:14,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'platform:regulatory')
2012-01-21 20:17:14,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-01-21 20:17:14,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001510sv00001025sd00000598bc06sc00i00')
2012-01-21 20:17:14,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00004383sv00001025sd00000598bc04sc03i00')
2012-01-21 20:17:14,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-01-21 20:17:14,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0000:')
2012-01-21 20:17:14,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0103:')
2012-01-21 20:17:14,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00009807sv00001025sd00000598bc03sc00i00')
2012-01-21 20:17:14,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00004385sv00001025sd00000598bc0Csc05i00')
2012-01-21 20:17:14,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0200:')
2012-01-21 20:17:14,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000105Bsd0000E042bc02sc80i00')
2012-01-21 20:17:14,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFEip02')
2012-01-21 20:17:14,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc02ip00')
2012-01-21 20:17:14,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-01-21 20:17:14,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-01-21 20:17:14,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0303:')
2012-01-21 20:17:14,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001969d00002062sv00001025sd00000598bc02sc00i00')
2012-01-21 20:17:14,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-01-21 20:17:14,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-01-21 20:17:14,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.07:bd09/19/2011:svnAcer:pnAO722:pvrV1.07:rvnAcer:rnJE10-BZ:rvrBaseBoardVersion:cvnAcer:ct10:cvrV1.07:')
2012-01-21 20:17:14,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-01-21 20:17:14,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-01-21 20:17:14,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v064EpD214d0100dcEFdsc02dp01ic0Eisc01ip00')
2012-01-21 20:17:14,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-01-21 20:17:14,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v0781p74C3dA5DCdc00dsc00dp00ic08isc06ip50')
2012-01-21 20:17:14,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00004391sv00001025sd00000598bc01sc06i01')
2012-01-21 20:17:14,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0003v064EpD214e0100-e0,1,kD4,ramlsfw')
2012-01-21 20:17:14,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:ETD0500:ETD0001:PNP0F13:')
2012-01-21 20:17:14,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:37EC5FFF-1B99-4FBA-AC3C-0C820BC3D5CC')
2012-01-21 20:17:14,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0100:')
2012-01-21 20:17:14,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'platform:reg-dummy')
2012-01-21 20:17:14,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00icFFiscFDip01')
2012-01-21 20:17:14,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-01-21 20:17:14,361 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-01-21 20:17:14,361 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'usb:v05ACp129Ed0001dc00dsc00dp00ic06isc01ip01')
2012-01-21 20:17:14,361 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-01-21 20:17:14,361 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-01-21 20:17:14,362 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-01-21 20:17:14,362 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00004396sv00001025sd00000598bc0Csc03i20')
2012-01-21 20:17:14,362 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-01-21 20:17:14,362 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-01-21 20:17:14,363 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-01-21 20:17:14,363 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001025sd00000598bc06sc01i00')
2012-01-21 20:17:14,363 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-01-21 20:17:14,363 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e41560> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-01-21 20:17:14,553 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:14,553 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:17:14,978 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:15,514 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:15,657 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:15,658 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-01-21 20:17:16,344 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:16,344 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:17:16,514 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-01-21 20:17:16,515 DEBUG: fglrx_updates is not the alternative in use
2012-01-21 20:17:16,825 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:17:17,369 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-21 20:18:05,262 DEBUG: Shutting down
```

---

### Post by sffvba[e0rt on 2012-01-22
I have no experience with Radeon graphics or drivers but I suspect once we get the right drivers installed your issues will be over.

Normally the default drivers that are recommended by the restricted drivers are fine (at least for nVidia it seems to be the case).  Could you give more info on which graphics card / CPU etc. you have (if your not sure I see there is a command that may work in terminal *lspci | grep -i vga*)


Cheers
404

---

### Post by Agusia on 2012-01-22
Terminal says:
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9807
On my netbook I have a sticker: CPU: AMD Dual-Core Processor C60 with Turbo CORE Technology up to 1.333 GHz. I'm not sure but i think that I have Radeon 6270 or something like that.

---

### Post by elliotn on 2012-01-22
> **Agusia said:**
> Terminal says:
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9807
On my netbook I have a sticker: CPU: AMD Dual-Core Processor C60 with Turbo CORE Technology up to 1.333 GHz. I'm not sure but i think that I have Radeon 6270 or something like that.

I have had the same problem too, you have to remove any NVIDIA related driver, I did this by booting with rescue mode and going to synaptic and searched NVIDIA and found about 4 related packages and I removed them then reboot

---

### Post by Agusia on 2012-01-22
> **elliotn said:**
> I have had the same problem too, you have to remove any NVIDIA related driver, I did this by booting with rescue mode and going to synaptic and searched NVIDIA and found about 4 related packages and I removed them then reboot

Could you say how exactly to do this? I'm not an expert in computers.

---

### Post by raja.genupula on 2012-01-22
> **Agusia said:**
> Could you say how exactly to do this? I'm not an expert in computers.

[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

---

### Post by varunendra on 2012-01-23
I don't think I can offer any precise help at this point, but here's a slight correction to *not found's* 'F6' tip:

The 'F6' method *not found* suggested earlier in the thread is meant to work with Live booting, not on an installed system. In the installed system, the same 'nomodeset' option is available in "Recovery mode > failsafeX" mode from the grub menu.

So IF, this indeed is a graphics issue, you can boot normally in safe graphics mode by:

[LIST]
[*]Choose 2nd option (Recovery Mode) in the grub menu (you may have to press and hold 'shift' key while booting to bring up grub menu if it doesn't come up by default)
[*]in the recovery menu, choose FailsafeX mode to boot into.
[/LIST]
This is the same thing as 'nomodeset' and should allow you to boot normally in 'Low graphics mode'. From there you can proceed to this guide to install proper driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


If you are doubtful about currently installed drivers and the card itself, please post the outputs of:
```
sudo lshw -C display
lsmod

```

---

### Post by sffvba[e0rt on 2012-01-23
> **varunendra said:**
> I don't think I can offer any precise help at this point, but here's a slight correction to *not found's* 'F6' tip:

The 'F6' method *not found* suggested earlier in the thread is meant to work with Live booting, not on an installed system. In the installed system, the same 'nomodeset' option is available in "Recovery mode > failsafeX" mode from the grub menu.


Thanks for the correction.


404

---

### Post by Agusia on 2012-01-24
Sorry that it took so long, but i haven't got time to work with computer.
I've chosen Recovery mode, but I couldn't find there failsafeX.
I've installed that driver.
```
lspci -nn | grep VGA
```
returned:
```
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9807]
```
```
sudo lshw -C display
lsmod
```
returns:
```
  *-display               
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:42 memory:e0000000-efffffff ioport:4000(size=256) memory:f0400000-f043ffff
```

BTW. What is the difference between Chrome and Chromium?? And which one is better? ;)

---

### Post by Baldrick_NZ on 2012-01-24
> **Agusia said:**
> 

BTW. What is the difference between Chrome and Chromium?? And which one is better? ;)

From my understanding, Chrome is built on Chromium. So any changes that happen to Chromium usually take effect in Chrome soon after.

I use Chrome myself, because it's more widely circulated and thus possibly better supported.

Though on both these points I'm open to correction.

Cheers.

---

### Post by varunendra on 2012-01-24
> **Agusia said:**
> 
I've chosen Recovery mode, but I couldn't find there failsafeX.
I couldn't find it either :( Looks like they have removed that option from the recovery menu (can somebody tell me what good is that for, and what harm it was doing in there??)

Anyway, you can always set these kernel boot parameters during boot time by editing the kernel-booting line in grub. Follow this post by *fossfreedom* to see how: [http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation](http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation)

Let's hope it allows you to boot normally. We can then try permanent remedies to the problem.


As for the chrome Vs. chromium question, both are same at the core level as well as in functionality for the most part. The basic difference is that chromium is Open-Source while chrome is a slightly polished, non-free version of chromium. From the description of "chromium-browser" in synaptic-
> Chromium serves as a base for Google Chrome, which is Chromium rebranded (name
and logo) with very few additions such as usage tracking and an auto-updater
system.

A few more details: [http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en)

Although this suggests that chrome should be more stable and capable, _I personally prefer chromium_ since it is provided by default Ubuntu repositories and is thus better supported in Ubuntu. Whereas the proprietary packages from google, like google earth or chrome, seem to create problems with other packages sometimes ("libqt4 not found" error comes first to my mind).

---

### Post by Agusia on 2012-01-31
But sometimes it boots normally and works normally. Most times it freezes when it looks like everything is loaded, there is a wallpaper, mouse pointer and everything and after a while the mouse freezes and i can't do anything. :(

---

### Post by mathiaho on 2012-03-23
Hi, I noticed in the dmesg from the first page, this line:

```
[    0.430495] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000ce3ff]
```

It is pretty similar to the last message I get when trying to boot any newer kernel on my laptop, before it freezes. My laptop also have an ATI graphics card.

After searching a little around, I think this might be related: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Are your computer also running UEFI?

my thread is located here: [http://ubuntuforums.org/showthread.php?t=1942992](http://ubuntuforums.org/showthread.php?t=1942992)

---

### Post by Agusia on 2012-03-24
I don't know if I have UEFI. I've solved this problem by installing the Ubuntu 12. :)

---

