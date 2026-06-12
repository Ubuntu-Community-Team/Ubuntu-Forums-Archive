---
title: "Intermittent problem recognizing DVD drive on Ubuntu 16.04"
date: 2017-01-06
forum: New to Ubuntu
---

### Post by nickworley2 on 2017-01-06
I'm experiencing this odd problem on Ubuntu 16.04 where sometimes my DVDs are recognized and sometimes not.
I have the restricted extras installed.
It only happens with movie DVDs, never data CDs.
Sometimes I'll put a movie DVD in the drive and it's recognized and plays, other times I'll put one in and the drive makes noises, but the DVD is never recognized, even if I leave it in the drive for a good minute or two.
It's very hit and miss and I have no idea why sometimes a DVD is recognized and other times not. 
Sometimes restarting works, other times not.
It would make more sense for DVDs to never be recognized or always be recognized, but this intermittent behaviour is puzzling.
It crossed my mind that maybe the CD/DVD drive is on its way out, but if that's the case then surely I'd have the same problem with data CDs.
Anyone have any idea what's going on here?
Anyone experienced the same thing and know the solution?

---

### Post by DuckHook on 2017-01-07
Hello nickworley2 and welcome to the forums.

You mention that it doesn't happen with data CDs. Is this true only of CDs? Or are data DVDs also well behaved? Or are *all* DVDs, irrespective of type, problematic?

Please provide complete HW info, without which, it is not possible to help. In particular, age/make/model of all HW, age/make/model of DVD drive, etc. For the sort of info needed, see the link in my sig: *How to Ask for Help.*

---

### Post by nickworley2 on 2017-01-09
> **DuckHook said:**
> Hello nickworley2 and welcome to the forums.

You mention that it doesn't happen with data CDs. Is this true only of CDs? Or are data DVDs also well behaved? Or are *all* DVDs, irrespective of type, problematic?

Please provide complete HW info, without which, it is not possible to help. In particular, age/make/model of all HW, age/make/model of DVD drive, etc. For the sort of info needed, see the link in my sig: *How to Ask for Help.*

Thanks for your reply DuckHook.

I only have a couple of data DVDs and I've just tried both:
Encarta Reference Suite 2001: Not recognized
Encyclopaedia Britannica 2003 Ultimate Reference Suite: Recognized
So the plot thickens. It never occured to me to try data DVDs.

The weird thing is that this behaviour can happen with the **same** movie DVD. One day the disc will be recognized, but not the next day. As I said it's puzzling.
For example I'm currently watching series 9 of the BBC series Spooks (called MI-5 in some countries) and this series comes on 3 DVDs. The other day I watched the first episode on DVD 3 and the next day I wanted to watch the second episode on the same DVD and Ubuntu simply would not recognize the disc. Sometimes restarting will enable the DVD to be recognized, but after watching Ep 1 on DVD 3, Ubuntu will simply not recognize the disc any more. It's very odd. But if I put the disc into my DVD player connected to my TV, then it's recognized immediately, so it's clearly not an issue with the disc itself. You may think "Well watch it on your TV then", but sometimes I want to watch DVDs in bed on my laptop rather than sitting in front of the TV. And in any case I want to get to the bottom of this problem.

My laptop is a pretty old general-purpose laptop with correspondingly old hardware: Toshiba Satellite L350-235 (bought second hand around 2010 if I remember correctly)
All hardware listed below came with the laptop and nothing has been changed since buying it:
RAM: 3GB RAM
Processor: Pentium Dual-Core CPU T4200 @ 2.00GHz × 2
Graphics: Mobile Intel GM45 Express Chipset x86/MMX/SSE2
CD/DVD drive: CD-RW & DVD-RW (that's -RW, not +RW) (ATA TSSTcorp CDDVDW TS-L633A)

When I bought the laptop it came with Vista, but I didn't like it so formatted the drive NTFS and installed XP on it (I had an old OEM version of XP Pro from an old desktop computer and I installed that on my laptop).
When XP support ended, I installed Ubuntu 16.04 LTS (32 bit) and I use Wine for programs I have that don't come in Linux versions (mainly reference works and German-English dictionaries). So far Wine has worked perfectly and I'm very impressed with it.

I'm using VLC media player version 2.2.2 for watching movie DVDs.

Anyway, at present the CD/DVD drive isn't being mounted on boot and doesn't appear in the file manager (is this called Nautilus? it's the Ubuntu equivalent of Windows Explorer anyway).
On a few occasions I've received an error message about no reference to the CD/DVD drive being present in /etc/fstab.
I've Googled this, and done some reading, but I don't really understand it. I don't understand what fstab does exactly and what the relationship between fstab and mounting CD/DVD drives is. I'm out of my comfort zone here.

I also suspect that I may have installed the restricted extras in an improper manner. I may have to uninstall them and reinstall them, but I don't even know how to do that.

Any advice would be appreciated.

---

### Post by DuckHook on 2017-01-09
It sounds to me like the old bird is simply wearing out on you. I'm a bit of an old-HW hound myself, and have seen similar symptoms over the years in a lot of my old equipment. The DVD lasers and tracking system start to give up the ghost, with weird results much like yours: intermittent unresponsiveness, never-ending seeks, almost random faults. The lasers in particular have a limited number of read/writes before they start to deteriorate beyond reliable performance.

Because DVDs are finer-grained than CDs, they tend to misbehave first while CDs are still readable.

You could try running a LiveUSB of L/Xubuntu or Ubuntu-mate to see if a different flavour will make a difference. If the problems go away, then perhaps it is a kernel or OS issue and you know that HW is still okay. You can also take a look at your logs immediately after a failed read/write. *dmesg* may give you some info. But if the system is no longer even seeing the drive itself at boot, then the problem is almost certainly HW and no amount of tinkering will help. It sounds like you've gotten your fair share of usage out of the thing. Can't be too surprised if it expires of old age.> **nickworley2 said:**
> My laptop is a pretty old general-purpose laptop with correspondingly old hardware: Toshiba Satellite L350-235 (bought second hand around 2010 if I remember correctly)Not that old, actually. A duo-core machine is still very usable today, especially if you run a light flavour on it like any of the L/Xubuntu-mate ones.> When I bought the laptop it came with Vista, but I didn't like it so formatted the drive NTFS and installed XP on it (I had an old OEM version of XP Pro from an old desktop computer and I installed that on my laptop).
When XP support ended, I installed Ubuntu 16.04 LTS (32 bit) and I use Wine for programs I have that don't come in Linux versions (mainly reference works and German-English dictionaries). So far Wine has worked perfectly and I'm very impressed with it.Your experience mirrors my own. The 'buntus are good at giving older equipment a second youth. I'm surprised you're happy with Unity though. It uses a fair amount of system resources, leaving less for apps.> Anyway, at present the CD/DVD drive isn't being mounted on boot and doesn't appear in the file manager (is this called Nautilus?Yes, it is Nautilus. As stated, this points to an HW problem.> On a few occasions I've received an error message about no reference to the CD/DVD drive being present in /etc/fstab.
I've Googled this, and done some reading, but I don't really understand it. I don't understand what fstab does exactly and what the relationship between fstab and mounting CD/DVD drives is. I'm out of my comfort zone here.Yes, it does get a bit technical. *fstab* is the configuration file that tells the system what disks to automount at boot (including your main system disk). But, oddly enough, this should *not* include the DVD drive, which mounts through a different subsystem and isn't really a disk anyway until you put a DVD/CD into it. Until then, it is just a device, hence, why it should not be showing up in fstab. I don't know why your system is calling for an fstab entry. This is very odd behaviour and you should not create such an entry. I can only guess that it is your system's way of trying to resolve a HW fault in the drive itself, which is now preventing the system from recognizing the device as a DVD.> I also suspect that I may have installed the restricted extras in an improper manner. I may have to uninstall them and reinstall them, but I don't even know how to do that.It is highly unlikely that restricted extras would give rise to your symptoms, and certainly would not cause the system to stop detecting your device altogether.> Any advice would be appreciated.If problem is HW, there are some options. You can buy an external USB DVD, try eBay for old second-hand DVD drives for your model of laptop, or just blast canned air into your DVD to see if clearing out the dust accumulation will revive it. Surprising how often this last trick works.

---

### Post by nickworley2 on 2017-01-09
> **DuckHook said:**
> It sounds to me like the old bird is simply wearing out on you. I'm a bit of an old-HW hound myself, and have seen similar symptoms over the years in a lot of my old equipment. The DVD lasers and tracking system start to give up the ghost, with weird results much like yours: intermittent unresponsiveness, never-ending seeks, almost random faults. The lasers in particular have a limited number of read/writes before they start to deteriorate beyond reliable performance.

Because DVDs are finer-grained than CDs, they tend to misbehave first while CDs are still readable.

You could try running a LiveUSB of L/Xubuntu or Ubuntu-mate to see if a different flavour will make a difference. If the problems go away, then perhaps it is a kernel or OS issue and you know that HW is still okay. You can also take a look at your logs immediately after a failed read/write. *dmesg* may give you some info. But if the system is no longer even seeing the drive itself at boot, then the problem is almost certainly HW and no amount of tinkering will help. It sounds like you've gotten your fair share of usage out of the thing. Can't be too surprised if it expires of old age.Not that old, actually. A duo-core machine is still very usable today, especially if you run a light flavour on it like any of the L/Xubuntu-mate ones.Your experience mirrors my own. The 'buntus are good at giving older equipment a second youth. I'm surprised you're happy with Unity though. It uses a fair amount of system resources, leaving less for apps.Yes, it is Nautilus. As stated, this points to an HW problem.Yes, it does get a bit technical. *fstab* is the configuration file that tells the system what disks to automount at boot (including your main system disk). But, oddly enough, this should *not* include the DVD drive, which mounts through a different subsystem and isn't really a disk anyway until you put a DVD/CD into it. Until then, it is just a device, hence, why it should not be showing up in fstab. I don't know why your system is calling for an fstab entry. This is very odd behaviour and you should not create such an entry. I can only guess that it is your system's way of trying to resolve a HW fault in the drive itself, which is now preventing the system from recognizing the device as a DVD.It is highly unlikely that restricted extras would give rise to your symptoms, and certainly would not cause the system to stop detecting your device altogether.If problem is HW, there are some options. You can buy an external USB DVD, try eBay for old second-hand DVD drives for your model of laptop, or just blast canned air into your DVD to see if clearing out the dust accumulation will revive it. Surprising how often this last trick works.

Thanks DH for your detailed reply. 
I'll try a LiveUSB and report back (give me a few days though -- got stuff to do).
Where are the read/write logs stored btw? What's the filepath?
See below for the output from dmesg (this is gobbledygook to me, but presumably means something to you).
I'll try the canned air, since it'll be a good cheap fix if it works.
If that doesn't work I'll try an ext USB DVD drive.
If nothing works, I'll have a temper tantrum and go and sulk in the corner!




Output from dmesg:

```
user@user-computer:~$ sudo dmesg
[sudo] password for user: 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-57-generic (buildd@lcy01-15) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #78-Ubuntu SMP Fri Dec 9 23:46:51 UTC 2016 (Ubuntu 4.4.0-57.78-generic 4.4.35)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Enabled xstate features 0x3, context size is 576 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b7b6bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b7b6c000-0x00000000b7bbefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b7bbf000-0x00000000b7c85fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b7c86000-0x00000000b7cbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b7cbf000-0x00000000b7cecfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b7ced000-0x00000000b7cfefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000b7cff000-0x00000000b7cfffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b7d00000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite L350/Portable PC, BIOS 1.90 06/04/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xb7d00 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-CFFFF uncachable
[    0.000000]   D0000-DFFFF write-protect
[    0.000000]   E0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFFE0000 mask FFFFE0000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 base 0B7D00000 mask FFFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] BRK [0x01d5e000, 0x01d5efff] PGTABLE
[    0.000000] BRK [0x01d5f000, 0x01d5ffff] PGTABLE
[    0.000000] RAMDISK: [mem 0x337ee000-0x35beefff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 0x00000000B7CFE120 000064 (v01 TOSINV TOSINV00 00000001      01000013)
[    0.000000] ACPI: FACP 0x00000000B7CFD000 0000F4 (v04 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 0x00000000B7CF0000 008F1A (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 0x00000000B7C93000 000040
[    0.000000] ACPI: FACS 0x00000000B7C93000 000040
[    0.000000] ACPI: HPET 0x00000000B7CFC000 000038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 0x00000000B7CFB000 00006C (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 0x00000000B7CFA000 00003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 0x00000000B7CF9000 0000A5 (v32 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 0x00000000B7CEF000 000176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 0x00000000B7CEE000 000028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000B7CED000 000655 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2049MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x0000000037bfdfff]
[    0.000000]   HighMem  [mem 0x0000000037bfe000-0x00000000b7cfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000b7b6bfff]
[    0.000000]   node   0: [mem 0x00000000b7bbf000-0x00000000b7c85fff]
[    0.000000]   node   0: [mem 0x00000000b7cbf000-0x00000000b7cecfff]
[    0.000000]   node   0: [mem 0x00000000b7cff000-0x00000000b7cfffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000000b7cfffff]
[    0.000000] On node 0 totalpages: 752639
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 524388 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics stolen memory at 0xb8000000-0xbfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0xc0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 19 pages/cpu @f5d8b000 s47436 r0 d30388 u77824
[    0.000000] pcpu-alloc: s47436 r0 d30388 u77824 alloc=19*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 750409
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-4.4.0-57-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:000b7d00)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 2927940K/3010556K available (7912K kernel code, 769K rwdata, 3148K rodata, 944K init, 800K bss, 82616K reserved, 0K cma-reserved, 2097552K highmem)
[    0.000000] virtual kernel memory layout:
                   fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
                   pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
                   vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
                   lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
                     .init : 0xc1b91000 - 0xc1c7d000   ( 944 kB)
                     .data : 0xc17ba73b - 0xc1b8f400   (3923 kB)
                     .text : 0xc1000000 - 0xc17ba73b   (7913 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 32.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=4
[    0.000000] NR_IRQS:2304 nr_irqs:456 16
[    0.000000] CPU 0 irqstacks, hard=f3038000 soft=f303a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 3145728 bytes of page_ext
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1994.777 MHz processor
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.55 BogoMIPS (lpj=7979108)
[    0.004020] pid_max: default: 32768 minimum: 301
[    0.004035] ACPI: Core revision 20150930
[    0.004039] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.004127] ACPI: Forced DSDT copy: length 0x08F1A copied locally, original unmapped
[    0.016243] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.016268] Security Framework initialized
[    0.016271] Yama: becoming mindful.
[    0.016299] AppArmor: AppArmor initialized
[    0.016346] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.016349] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.016643] Initializing cgroup subsys io
[    0.016649] Initializing cgroup subsys memory
[    0.016659] Initializing cgroup subsys devices
[    0.016663] Initializing cgroup subsys freezer
[    0.016667] Initializing cgroup subsys net_cls
[    0.016670] Initializing cgroup subsys perf_event
[    0.016674] Initializing cgroup subsys net_prio
[    0.016681] Initializing cgroup subsys hugetlb
[    0.016684] Initializing cgroup subsys pids
[    0.016711] CPU: Physical Processor ID: 0
[    0.016713] CPU: Processor Core ID: 0
[    0.016719] mce: CPU supports 6 MCE banks
[    0.016730] CPU0: Thermal monitoring enabled (TM2)
[    0.016734] process: using mwait in idle threads
[    0.016742] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.016744] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.017431] Freeing SMP alternatives memory: 28K (c1c7d000 - c1c84000)
[    0.020013] ftrace: allocating 31348 entries in 62 pages
[    0.032112] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.032116] smpboot: Max logical packages: 2
[    0.032120] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076000] smpboot: CPU0: Intel Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz (family: 0x6, model: 0x17, stepping: 0xa)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076000] CPU 1 irqstacks, hard=f28ce000 soft=f28d8000
[    0.076000] x86: Booting SMP configuration:
[    0.076000] .... node  #0, CPUs:      #1
[    0.008000] Initializing CPU#1
[    0.076000] x86: Booted up 1 node, 2 CPUs
[    0.076000] smpboot: Total of 2 processors activated (7979.10 BogoMIPS)
[    0.076137] devtmpfs: initialized
[    0.076477] evm: security.selinux
[    0.076480] evm: security.SMACK64
[    0.076481] evm: security.SMACK64EXEC
[    0.076483] evm: security.SMACK64TRANSMUTE
[    0.076484] evm: security.SMACK64MMAP
[    0.076485] evm: security.ima
[    0.076487] evm: security.capability
[    0.076620] PM: Registering ACPI NVS region [mem 0xb7c86000-0xb7cbefff] (233472 bytes)
[    0.076742] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.076794] pinctrl core: initialized pinctrl subsystem
[    0.076794] RTC time: 18:14:50, date: 01/09/17
[    0.076794] NET: Registered protocol family 16
[    0.076794] EISA bus registered
[    0.084006] cpuidle: using governor ladder
[    0.096003] cpuidle: using governor menu
[    0.096007] PCCT header not found.
[    0.100032] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.100035] Simple Boot Flag at 0x44 set to 0x1
[    0.100074] ACPI: bus type PCI registered
[    0.100077] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.100177] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.100181] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.100182] PCI: Using MMCONFIG for extended config space
[    0.100184] PCI: Using configuration type 1 for base access
[    0.100355] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.100356] mtrr: probably your BIOS does not setup all CPUs.
[    0.100358] mtrr: corrected configuration.
[    0.112131] ACPI: Added _OSI(Module Device)
[    0.112134] ACPI: Added _OSI(Processor Device)
[    0.112136] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.112138] ACPI: Added _OSI(Processor Aggregator Device)
[    0.116168] ACPI: Executed 1 blocks of module-level executable AML code
[    0.117309] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.117805] ACPI: Dynamic OEM Table Load:
[    0.117814] ACPI: SSDT 0x00000000F286E400 000229 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.118467] ACPI: Dynamic OEM Table Load:
[    0.118475] ACPI: SSDT 0x00000000F3012000 000537 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.119426] ACPI: Dynamic OEM Table Load:
[    0.119433] ACPI: SSDT 0x00000000F2966800 0001CF (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.120057] ACPI: Dynamic OEM Table Load:
[    0.120063] ACPI: SSDT 0x00000000F2938180 00008D (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.120749] ACPI : EC: EC started
[    0.244436] ACPI: Interpreter enabled
[    0.244471] ACPI: (supports S0 S3 S4 S5)
[    0.244474] ACPI: Using IOAPIC for interrupt routing
[    0.244513] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.256850] ACPI: Power Resource [FN00] (on)
[    0.258380] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.258389] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.258396] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.258401] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.258986] PCI host bridge to bus 0000:00
[    0.258990] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.258993] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.258996] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.258999] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff window]
[    0.259002] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.259015] pci 0000:00:00.0: [8086:2a40] type 00 class 0x060000
[    0.259050] DMAR: Forcing write-buffer flush capability
[    0.259051] DMAR: Disabling IOMMU for graphics on this chipset
[    0.259157] pci 0000:00:02.0: [8086:2a42] type 00 class 0x030000
[    0.259178] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.259188] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.259195] pci 0000:00:02.0: reg 0x20: [io  0x5110-0x5117]
[    0.259322] pci 0000:00:02.1: [8086:2a43] type 00 class 0x038000
[    0.259339] pci 0000:00:02.1: reg 0x10: [mem 0xd3500000-0xd35fffff 64bit]
[    0.259517] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.259612] pci 0000:00:1a.0: reg 0x20: [io  0x50e0-0x50ff]
[    0.259771] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.259868] pci 0000:00:1a.1: reg 0x20: [io  0x50c0-0x50df]
[    0.260055] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.260097] pci 0000:00:1a.7: reg 0x10: [mem 0xd6705c00-0xd6705fff]
[    0.260206] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.260331] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.260371] pci 0000:00:1b.0: reg 0x10: [mem 0xd6700000-0xd6703fff 64bit]
[    0.260466] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.260532] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.260597] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.260706] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.260772] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.260840] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.260953] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.261019] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.261090] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    0.261185] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.261251] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.261324] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.261422] pci 0000:00:1d.0: reg 0x20: [io  0x50a0-0x50bf]
[    0.261564] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.261636] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.261729] pci 0000:00:1d.1: reg 0x20: [io  0x5080-0x509f]
[    0.261867] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.261936] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.262032] pci 0000:00:1d.2: reg 0x20: [io  0x5060-0x507f]
[    0.262204] pci 0000:00:1d.3: [8086:2939] type 00 class 0x0c0300
[    0.262301] pci 0000:00:1d.3: reg 0x20: [io  0x5040-0x505f]
[    0.262468] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.262510] pci 0000:00:1d.7: reg 0x10: [mem 0xd6705800-0xd6705bff]
[    0.262617] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.262699] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.262765] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.262889] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.262956] pci 0000:00:1f.0: [8086:2919] type 00 class 0x060100
[    0.263188] pci 0000:00:1f.2: [8086:2929] type 00 class 0x010601
[    0.263228] pci 0000:00:1f.2: reg 0x10: [io  0x5108-0x510f]
[    0.263241] pci 0000:00:1f.2: reg 0x14: [io  0x511c-0x511f]
[    0.263253] pci 0000:00:1f.2: reg 0x18: [io  0x5100-0x5107]
[    0.263264] pci 0000:00:1f.2: reg 0x1c: [io  0x5118-0x511b]
[    0.263276] pci 0000:00:1f.2: reg 0x20: [io  0x5020-0x503f]
[    0.263288] pci 0000:00:1f.2: reg 0x24: [mem 0xd6705000-0xd67057ff]
[    0.263337] pci 0000:00:1f.2: PME# supported from D3hot
[    0.263454] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.263477] pci 0000:00:1f.3: reg 0x10: [mem 0xd6706000-0xd67060ff 64bit]
[    0.263509] pci 0000:00:1f.3: reg 0x20: [io  0x5000-0x501f]
[    0.263774] pci 0000:02:00.0: [10ec:8136] type 00 class 0x020000
[    0.263932] pci 0000:02:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.264047] pci 0000:02:00.0: reg 0x18: [mem 0xd0410000-0xd0410fff 64bit pref]
[    0.264116] pci 0000:02:00.0: reg 0x20: [mem 0xd0400000-0xd040ffff 64bit pref]
[    0.264162] pci 0000:02:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.264358] pci 0000:02:00.0: supports D1 D2
[    0.264360] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264567] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.264574] pci 0000:00:1c.0:   bridge window [io  0x3000-0x4fff]
[    0.264579] pci 0000:00:1c.0:   bridge window [mem 0xd5700000-0xd66fffff]
[    0.264586] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd14fffff 64bit pref]
[    0.264693] pci 0000:03:00.0: [168c:001c] type 00 class 0x020000
[    0.264758] pci 0000:03:00.0: reg 0x10: [mem 0xd4600000-0xd460ffff 64bit]
[    0.264988] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.265001] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.265007] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.265011] pci 0000:00:1c.1:   bridge window [mem 0xd4600000-0xd56fffff]
[    0.265019] pci 0000:00:1c.1:   bridge window [mem 0xd1500000-0xd24fffff 64bit pref]
[    0.265125] acpiphp: Slot [1] registered
[    0.265133] pci 0000:00:1c.4: PCI bridge to [bus 06-07]
[    0.265139] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.265144] pci 0000:00:1c.4:   bridge window [mem 0xd3600000-0xd45fffff]
[    0.265153] pci 0000:00:1c.4:   bridge window [mem 0xd2500000-0xd34fffff 64bit pref]
[    0.265255] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.265270] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.265273] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.265275] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.265279] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff window] (subtractive decode)
[    0.265310] pci_bus 0000:00: on NUMA node 0
[    0.265436] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12)
[    0.265525] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.265613] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.265699] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.265785] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.265873] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.265960] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.266047] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.266638] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.266727] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.266873] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.266873] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.266873] vgaarb: loaded
[    0.266873] vgaarb: bridge control possible 0000:00:02.0
[    0.266873] SCSI subsystem initialized
[    0.266873] libata version 3.00 loaded.
[    0.266873] ACPI: bus type USB registered
[    0.266873] usbcore: registered new interface driver usbfs
[    0.266873] usbcore: registered new interface driver hub
[    0.266873] usbcore: registered new device driver usb
[    0.266873] PCI: Using ACPI for IRQ routing
[    0.269872] PCI: pci_cache_line_size set to 64 bytes
[    0.269962] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.269965] e820: reserve RAM buffer [mem 0xb7b6c000-0xb7ffffff]
[    0.269968] e820: reserve RAM buffer [mem 0xb7c86000-0xb7ffffff]
[    0.269970] e820: reserve RAM buffer [mem 0xb7ced000-0xb7ffffff]
[    0.269972] e820: reserve RAM buffer [mem 0xb7d00000-0xb7ffffff]
[    0.270153] NetLabel: Initializing
[    0.270155] NetLabel:  domain hash size = 128
[    0.270157] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.270172] NetLabel:  unlabeled traffic allowed by default
[    0.270207] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.270207] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.270207] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.272018] amd_nb: Cannot enumerate AMD northbridges
[    0.272032] clocksource: Switched to clocksource hpet
[    0.283898] AppArmor: AppArmor Filesystem Enabled
[    0.284034] pnp: PnP ACPI init
[    0.284548] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff]
[    0.284634] system 00:00: [io  0x0800-0x080f] has been reserved
[    0.284638] system 00:00: [io  0x0810-0x0817] has been reserved
[    0.284641] system 00:00: [io  0x0820-0x0823] has been reserved
[    0.284644] system 00:00: [io  0x0400-0x047f] could not be reserved
[    0.284647] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.284650] system 00:00: [io  0x0580-0x05ff] has been reserved
[    0.284653] system 00:00: [io  0x0600-0x0627] has been reserved
[    0.284657] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.284661] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.284664] system 00:00: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.284667] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.284670] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.284674] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.284677] system 00:00: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.284680] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.284683] system 00:00: [mem 0xff800000-0xffffffff] could not be reserved
[    0.284689] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.284751] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.284842] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.284906] pnp 00:03: Plug and Play ACPI device, IDs SYN1913 SYN1900 SYN0002 PNP0f13 (active)
[    0.285014] pnp: PnP ACPI: found 4 devices
[    0.285020] PnPBIOS: Disabled by ACPI PNP
[    0.322789] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.322801] pci 0000:02:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    0.322858] pci 0000:02:00.0: BAR 6: assigned [mem 0xd5700000-0xd571ffff pref]
[    0.322862] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.322866] pci 0000:00:1c.0:   bridge window [io  0x3000-0x4fff]
[    0.322873] pci 0000:00:1c.0:   bridge window [mem 0xd5700000-0xd66fffff]
[    0.322878] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd14fffff 64bit pref]
[    0.322887] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.322890] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.322898] pci 0000:00:1c.1:   bridge window [mem 0xd4600000-0xd56fffff]
[    0.322903] pci 0000:00:1c.1:   bridge window [mem 0xd1500000-0xd24fffff 64bit pref]
[    0.322911] pci 0000:00:1c.4: PCI bridge to [bus 06-07]
[    0.322915] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.322922] pci 0000:00:1c.4:   bridge window [mem 0xd3600000-0xd45fffff]
[    0.322927] pci 0000:00:1c.4:   bridge window [mem 0xd2500000-0xd34fffff 64bit pref]
[    0.322936] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.322953] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.322955] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.322958] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.322961] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff window]
[    0.322964] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    0.322967] pci_bus 0000:02: resource 1 [mem 0xd5700000-0xd66fffff]
[    0.322970] pci_bus 0000:02: resource 2 [mem 0xd0400000-0xd14fffff 64bit pref]
[    0.322973] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.322975] pci_bus 0000:03: resource 1 [mem 0xd4600000-0xd56fffff]
[    0.322978] pci_bus 0000:03: resource 2 [mem 0xd1500000-0xd24fffff 64bit pref]
[    0.322981] pci_bus 0000:06: resource 0 [io  0x1000-0x1fff]
[    0.322983] pci_bus 0000:06: resource 1 [mem 0xd3600000-0xd45fffff]
[    0.322986] pci_bus 0000:06: resource 2 [mem 0xd2500000-0xd34fffff 64bit pref]
[    0.322990] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7 window]
[    0.322993] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff window]
[    0.322995] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.322998] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfebfffff window]
[    0.323041] NET: Registered protocol family 2
[    0.323270] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.323288] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.323313] TCP: Hash tables configured (established 8192 bind 8192)
[    0.323349] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.323356] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.323417] NET: Registered protocol family 1
[    0.323437] pci 0000:00:02.0: Video device with shadowed ROM
[    1.924018] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.524019] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.524337] PCI: CLS 64 bytes, default 64
[    3.524408] Trying to unpack rootfs image as initramfs...
[    4.364652] Freeing initrd memory: 36868K (f37ee000 - f5bef000)
[    4.364970] Scanning for low memory corruption every 60 seconds
[    4.365472] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    4.365524] audit: initializing netlink subsys (disabled)
[    4.365549] audit: type=2000 audit(1483985694.360:1): initialized
[    4.365999] Initialise system trusted keyring
[    4.366154] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.368762] zbud: loaded
[    4.368919] VFS: Disk quotas dquot_6.6.0
[    4.368977] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.369376] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    4.369773] fuse init (API version 7.23)
[    4.370007] Key type big_key registered
[    4.370032] Allocating IMA MOK and blacklist keyrings.
[    4.370597] Key type asymmetric registered
[    4.370602] Asymmetric key parser 'x509' registered
[    4.370624] bounce: pool size: 64 pages
[    4.370680] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    4.370725] io scheduler noop registered
[    4.370729] io scheduler deadline registered (default)
[    4.370783] io scheduler cfq registered
[    4.371629] pcieport 0000:00:1c.4: enabling device (0000 -> 0003)
[    4.371958] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.371968] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.372045] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    4.372047] vesafb: scrolling: redraw
[    4.372049] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.372070] vesafb: framebuffer at 0xc0000000, mapped to 0xf8600000, using 3072k, total 3072k
[    4.372217] Console: switching to colour frame buffer device 128x48
[    4.372246] fb0: VESA VGA frame buffer device
[    4.372271] intel_idle: does not run on family 6 model 23
[    4.372385] ACPI: AC Adapter [ADP0] (off-line)
[    4.372481] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    4.372486] ACPI: Power Button [PWRB]
[    4.372553] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    4.374695] ACPI: Lid Switch [LID0]
[    4.374772] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.374776] ACPI: Power Button [PWRF]
[    4.374990] Monitor-Mwait will be used to enter C-1 state
[    4.374998] Monitor-Mwait will be used to enter C-2 state
[    4.375003] tsc: Marking TSC unstable due to TSC halts in idle
[    4.375008] ACPI: acpi_idle registered with cpuidle
[    4.382331] thermal LNXTHERM:00: registered as thermal_zone0
[    4.382334] ACPI: Thermal Zone [THRM] (23 C)
[    4.382381] GHES: HEST is not enabled!
[    4.383165] ACPI: Battery Slot [BAT0] (battery present)
[    4.383222] isapnp: Scanning for PnP cards...
[    4.384093] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.386489] Linux agpgart interface v0.103
[    4.386605] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    4.386627] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    4.386926] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    4.387057] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    4.395283] brd: module loaded
[    4.397170] loop: module loaded
[    4.397543] libphy: Fixed MDIO Bus: probed
[    4.397547] tun: Universal TUN/TAP device driver, 1.6
[    4.397549] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.397613] PPP generic driver version 2.4.2
[    4.397704] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.397711] ehci-pci: EHCI PCI platform driver
[    4.398012] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    4.398021] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.398036] ehci-pci 0000:00:1a.7: debug port 1
[    4.401931] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    4.401955] ehci-pci 0000:00:1a.7: irq 19, io mem 0xd6705c00
[    4.412032] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.412092] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.412095] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.412098] usb usb1: Product: EHCI Host Controller
[    4.412101] usb usb1: Manufacturer: Linux 4.4.0-57-generic ehci_hcd
[    4.412103] usb usb1: SerialNumber: 0000:00:1a.7
[    4.412274] hub 1-0:1.0: USB hub found
[    4.412286] hub 1-0:1.0: 4 ports detected
[    4.412706] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    4.412714] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.412728] ehci-pci 0000:00:1d.7: debug port 1
[    4.416639] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    4.416660] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd6705800
[    4.428033] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.428087] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.428090] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.428093] usb usb2: Product: EHCI Host Controller
[    4.428095] usb usb2: Manufacturer: Linux 4.4.0-57-generic ehci_hcd
[    4.428098] usb usb2: SerialNumber: 0000:00:1d.7
[    4.428256] hub 2-0:1.0: USB hub found
[    4.428265] hub 2-0:1.0: 8 ports detected
[    4.428552] ehci-platform: EHCI generic platform driver
[    4.428576] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.428582] ohci-pci: OHCI PCI platform driver
[    4.428604] ohci-platform: OHCI generic platform driver
[    4.428619] uhci_hcd: USB Universal Host Controller Interface driver
[    4.428850] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.428857] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.428865] uhci_hcd 0000:00:1a.0: detected 2 ports
[    4.428898] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000050e0
[    4.428962] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    4.428965] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.428968] usb usb3: Product: UHCI Host Controller
[    4.428970] usb usb3: Manufacturer: Linux 4.4.0-57-generic uhci_hcd
[    4.428973] usb usb3: SerialNumber: 0000:00:1a.0
[    4.429132] hub 3-0:1.0: USB hub found
[    4.429141] hub 3-0:1.0: 2 ports detected
[    4.429492] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.429500] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.429509] uhci_hcd 0000:00:1a.1: detected 2 ports
[    4.429540] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050c0
[    4.429603] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    4.429606] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.429608] usb usb4: Product: UHCI Host Controller
[    4.429611] usb usb4: Manufacturer: Linux 4.4.0-57-generic uhci_hcd
[    4.429613] usb usb4: SerialNumber: 0000:00:1a.1
[    4.429771] hub 4-0:1.0: USB hub found
[    4.429780] hub 4-0:1.0: 2 ports detected
[    4.430137] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.430145] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.430154] uhci_hcd 0000:00:1d.0: detected 2 ports
[    4.430179] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[    4.430239] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    4.430242] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.430244] usb usb5: Product: UHCI Host Controller
[    4.430247] usb usb5: Manufacturer: Linux 4.4.0-57-generic uhci_hcd
[    4.430249] usb usb5: SerialNumber: 0000:00:1d.0
[    4.430403] hub 5-0:1.0: USB hub found
[    4.430412] hub 5-0:1.0: 2 ports detected
[    4.430758] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.430765] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.430774] uhci_hcd 0000:00:1d.1: detected 2 ports
[    4.430797] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005080
[    4.430856] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    4.430859] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.430862] usb usb6: Product: UHCI Host Controller
[    4.430864] usb usb6: Manufacturer: Linux 4.4.0-57-generic uhci_hcd
[    4.430866] usb usb6: SerialNumber: 0000:00:1d.1
[    4.431017] hub 6-0:1.0: USB hub found
[    4.431026] hub 6-0:1.0: 2 ports detected
[    4.431369] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.431377] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.431386] uhci_hcd 0000:00:1d.2: detected 2 ports
[    4.431409] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00005060
[    4.431473] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    4.431476] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.431478] usb usb7: Product: UHCI Host Controller
[    4.431481] usb usb7: Manufacturer: Linux 4.4.0-57-generic uhci_hcd
[    4.431483] usb usb7: SerialNumber: 0000:00:1d.2
[    4.431635] hub 7-0:1.0: USB hub found
[    4.431644] hub 7-0:1.0: 2 ports detected
[    4.431993] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.432000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.432033] uhci_hcd 0000:00:1d.3: detected 2 ports
[    4.432065] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00005040
[    4.432127] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    4.432130] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.432132] usb usb8: Product: UHCI Host Controller
[    4.432135] usb usb8: Manufacturer: Linux 4.4.0-57-generic uhci_hcd
[    4.432137] usb usb8: SerialNumber: 0000:00:1d.3
[    4.432292] hub 8-0:1.0: USB hub found
[    4.432301] hub 8-0:1.0: 2 ports detected
[    4.432531] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    4.463840] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.463847] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.464054] mousedev: PS/2 mouse device common for all mice
[    4.464997] rtc_cmos 00:01: RTC can wake from S4
[    4.465163] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    4.465195] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.465207] i2c /dev entries driver
[    4.465293] device-mapper: uevent: version 1.0.3
[    4.465392] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: [email]dm-devel@redhat.com[/email]
[    4.465431] platform eisa.0: Probing EISA bus 0
[    4.465434] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    4.465437] platform eisa.0: Cannot allocate resource for EISA slot 1
[    4.465440] platform eisa.0: Cannot allocate resource for EISA slot 2
[    4.465442] platform eisa.0: Cannot allocate resource for EISA slot 3
[    4.465445] platform eisa.0: Cannot allocate resource for EISA slot 4
[    4.465448] platform eisa.0: Cannot allocate resource for EISA slot 5
[    4.465450] platform eisa.0: Cannot allocate resource for EISA slot 6
[    4.465453] platform eisa.0: Cannot allocate resource for EISA slot 7
[    4.465456] platform eisa.0: Cannot allocate resource for EISA slot 8
[    4.465459] platform eisa.0: EISA: Detected 0 cards
[    4.465476] cpufreq-nforce2: No nForce2 chipset.
[    4.465487] ledtrig-cpu: registered to indicate activity on CPUs
[    4.465888] NET: Registered protocol family 10
[    4.466230] NET: Registered protocol family 17
[    4.466254] Key type dns_resolver registered
[    4.466561] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[    4.466570] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[    4.466618] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.466633] Using IPI No-Shortcut mode
[    4.466826] registered taskstats version 1
[    4.466848] Loading compiled-in X.509 certificates
[    4.471069] Loaded X.509 cert 'Build time autogenerated kernel key: 4b016e187dd6a3deb46ff9d6e6da32b116441344'
[    4.471093] zswap: loaded using pool lzo/zbud
[    4.474029] Key type trusted registered
[    4.479361] Key type encrypted registered
[    4.479371] AppArmor: AppArmor sha1 policy hashing enabled
[    4.479376] ima: No TPM chip found, activating TPM-bypass!
[    4.479406] evm: HMAC attrs: 0x1
[    4.479885]   Magic number: 1:721:240
[    4.479996] rtc_cmos 00:01: setting system clock to 2017-01-09 18:14:55 UTC (1483985695)
[    4.480464] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.480466] EDD information not available.
[    4.480589] PM: Hibernation image not present or could not be loaded.
[    4.495933] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.693706] isapnp: No Plug & Play device found
[    4.694134] Freeing unused kernel memory: 944K (c1b91000 - c1c7d000)
[    4.694232] Write protecting the kernel text: 7916k
[    4.694278] Write protecting the kernel read-only data: 3152k
[    4.694279] NX-protecting the kernel data: 6420k
[    4.710995] random: systemd-udevd: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.711134] random: systemd-udevd: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.711173] random: systemd-udevd: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.711935] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.712057] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.712318] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.712438] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.712547] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.712642] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.712743] random: udevadm: uninitialized urandom read (16 bytes read, 3 bits of entropy available)
[    4.724078] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    4.791335] [drm] Initialized drm 1.1.0 20060810
[    4.799143] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    4.857255] ahci 0000:00:1f.2: version 3.0
[    4.857651] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.857655] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc ems sxs 
[    4.859077] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.859091] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.859741] r8169 0000:02:00.0 eth0: RTL8102e at 0xf843a000, 00:1e:33:d4:37:dd, XID 14a00000 IRQ 28
[    4.884382] scsi host0: ahci
[    4.884578] scsi host1: ahci
[    4.887281] scsi host2: ahci
[    4.887460] scsi host3: ahci
[    4.887608] scsi host4: ahci
[    4.887748] scsi host5: ahci
[    4.887841] ata1: SATA max UDMA/133 abar m2048@0xd6705000 port 0xd6705100 irq 27
[    4.887846] ata2: SATA max UDMA/133 abar m2048@0xd6705000 port 0xd6705180 irq 27
[    4.887848] ata3: DUMMY
[    4.887850] ata4: DUMMY
[    4.887853] ata5: SATA max UDMA/133 abar m2048@0xd6705000 port 0xd6705300 irq 27
[    4.887855] ata6: SATA max UDMA/133 abar m2048@0xd6705000 port 0xd6705380 irq 27
[    4.888828] [drm] Memory usable by graphics device = 2048M
[    4.888834] checking generic (c0000000 300000) vs hw (c0000000 10000000)
[    4.888836] fb: switching to inteldrmfb from VESA VGA
[    4.888873] Console: switching to colour dummy device 80x25
[    4.889013] [drm] Replacing VGA console driver
[    4.895882] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.895885] [drm] Driver supports precise vblank timestamp query.
[    4.896026] usb 1-2: New USB device found, idVendor=04f2, idProduct=b070
[    4.896029] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    4.896032] usb 1-2: Product: CNF7051
[    4.896035] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
[    4.896037] usb 1-2: SerialNumber: SN0001
[    4.896821] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    4.929300] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    4.993342] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    5.006847] acpi device:02: registered as cooling_device3
[    5.006951] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    5.007096] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    5.017899] fbcon: inteldrmfb (fb0) is primary device
[    5.018006] Console: switching to colour frame buffer device 180x56
[    5.018057] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    5.204072] ata2: SATA link down (SStatus 0 SControl 300)
[    5.208070] ata5: SATA link down (SStatus 0 SControl 300)
[    5.364079] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x3981d0c4603, max_idle_ns: 881590599482 ns
[    5.492098] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.504790] ata6.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TO01, max UDMA/100
[    5.538857] ata6.00: configured for UDMA/100
[    5.656039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.009162] psmouse serio1: synaptics: queried max coordinates: x [..5866], y [..5756]
[    6.033843] ata1.00: ATA-8: TOSHIBA MK2546GSX, LB011A, max UDMA/100
[    6.033846] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    6.035328] ata1.00: configured for UDMA/100
[    6.035544] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2546GS 1A   PQ: 0 ANSI: 5
[    6.035919] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/233 GiB)
[    6.035985] sd 0:0:0:0: [sda] Write Protect is off
[    6.035989] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.036033] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.036138] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.077782] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa04000/0x20000/0x0, board id: 0, fw id: 515625
[    6.077788] psmouse serio1: synaptics: Toshiba Satellite L350 detected, limiting rate to 40pps.
[    6.079318] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TO01 PQ: 0 ANSI: 5
[    6.089461]  sda: sda1 sda2 < sda5 >
[    6.089980] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.165459] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    6.187427] sr 5:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.187433] cdrom: Uniform CD-ROM driver Revision: 3.20
[    6.187633] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    6.187761] sr 5:0:0:0: Attached scsi generic sg1 type 5
[   12.385305] random: nonblocking pool is initialized
[   12.427416] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   14.302831] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[   14.303004] systemd[1]: Detected architecture x86.
[   14.315588] systemd[1]: Set hostname to <user-computer>.
[   17.545760] systemd[1]: Reached target Encrypted Volumes.
[   17.545891] systemd[1]: Reached target User and Group Name Lookups.
[   17.545971] systemd[1]: Listening on Journal Socket (/dev/log).
[   17.546116] systemd[1]: Created slice User and Session Slice.
[   17.546173] systemd[1]: Listening on Syslog Socket.
[   17.546205] systemd[1]: Reached target Remote File Systems (Pre).
[   17.546228] systemd[1]: Reached target Remote File Systems.
[   17.546360] systemd[1]: Listening on Journal Audit Socket.
[   17.546424] systemd[1]: Listening on udev Control Socket.
[   17.546624] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   17.546691] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[   17.546750] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   17.546801] systemd[1]: Listening on LVM2 poll daemon socket.
[   17.546843] systemd[1]: Listening on LVM2 metadata daemon socket.
[   17.546913] systemd[1]: Listening on Journal Socket.
[   17.546971] systemd[1]: Listening on fsck to fsckd communication Socket.
[   17.547024] systemd[1]: Listening on udev Kernel Socket.
[   17.547151] systemd[1]: Created slice System Slice.
[   17.560339] systemd[1]: Starting Journal Service...
[   17.561238] systemd[1]: Mounting POSIX Message Queue File System...
[   17.561289] systemd[1]: Reached target Slices.
[   17.561506] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   17.664302] systemd[1]: Starting Load Kernel Modules...
[   17.665187] systemd[1]: Started Braille Device Support.
[   17.816281] systemd[1]: Starting Uncomplicated firewall...
[   17.817138] systemd[1]: Mounting Debug File System...
[   17.818121] systemd[1]: Mounting Huge Pages File System...
[   17.819005] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
[   17.820178] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   17.821124] systemd[1]: Started Read required files in advance.
[   17.822184] systemd[1]: Starting Set console keymap...
[   17.822334] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   18.062890] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   18.076313] systemd[1]: Starting Create Static Device Nodes in /dev...
[   18.474445] lp: driver loaded but no devices found
[   18.529339] systemd[1]: Mounted Huge Pages File System.
[   18.529424] systemd[1]: Mounted POSIX Message Queue File System.
[   18.529457] systemd[1]: Mounted Debug File System.
[   18.544868] ppdev: user-space parallel port driver
[   18.759089] systemd[1]: Started Load Kernel Modules.
[   18.772352] systemd[1]: Starting Apply Kernel Variables...
[   18.773340] systemd[1]: Mounting FUSE Control File System...
[   18.782061] systemd[1]: Mounted FUSE Control File System.
[   18.832304] systemd[1]: Started LVM2 metadata daemon.
[   19.198397] systemd[1]: Started Journal Service.
[   19.766446] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.071878] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.429100] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.019295] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   24.270969] systemd-journald[223]: Received request to flush runtime journal from PID 1
[   25.022435] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.036071] wmi: Mapper loaded
[   25.093150] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.23
[   25.110638] input: Toshiba input device as /devices/virtual/input/input7
[   25.151490] toshiba_acpi: Supported laptop features: hotkeys touchpad
[   25.202492] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMBA) (20150930/utaddress-254)
[   25.202502] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.202507] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000053B (\GPIO) (20150930/utaddress-254)
[   25.202512] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.202514] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000053B (\GPIO) (20150930/utaddress-254)
[   25.202519] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.202521] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   26.038880] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   26.039051] ath5k 0000:03:00.0: registered as 'phy0'
[   26.547890] ath: EEPROM regdomain: 0x65
[   26.547895] ath: EEPROM indicates we should expect a direct regpair map
[   26.547898] ath: Country alpha2 being used: 00
[   26.547900] ath: Regpair used: 0x65
[   26.636283] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   26.636684] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   26.931505] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC268: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   26.931512] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   26.931515] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   26.931518] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   26.931520] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   26.931523] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x19
[   26.931526] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[   27.200978] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   27.201090] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   27.747013] media: Linux media interface: v0.10
[   27.895209] Linux video capture interface: v2.00
[   27.962241] ath5k 0000:03:00.0 wlp3s0: renamed from wlan0
[   28.953000] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[   28.969737] input: CNF7051 as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input10
[   28.969836] usbcore: registered new interface driver uvcvideo
[   28.969838] USB Video Class driver (1.1.1)
[   30.545342] cfg80211: World regulatory domain updated:
[   30.545347] cfg80211:  DFS Master region: unset
[   30.545349] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   30.545352] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   30.545355] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   30.545357] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   30.545360] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   30.545363] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   30.545366] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   30.545368] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   30.545371] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   31.538828] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   31.636815] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   32.072705] Adding 3006460k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:3006460k FS
[   42.792214] audit: type=1400 audit(1483985733.808:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=902 comm="apparmor_parser"
[   42.792227] audit: type=1400 audit(1483985733.808:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
[   42.792234] audit: type=1400 audit(1483985733.808:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=902 comm="apparmor_parser"
[   42.792241] audit: type=1400 audit(1483985733.808:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
[   42.792780] audit: type=1400 audit(1483985733.808:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=901 comm="apparmor_parser"
[   42.792793] audit: type=1400 audit(1483985733.808:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=901 comm="apparmor_parser"
[   42.796552] audit: type=1400 audit(1483985733.812:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/freshclam" pid=905 comm="apparmor_parser"
[   42.843543] audit: type=1400 audit(1483985733.860:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="webbrowser-app" pid=906 comm="apparmor_parser"
[   42.843559] audit: type=1400 audit(1483985733.860:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="webbrowser-app//oxide_helper" pid=906 comm="apparmor_parser"
[   42.846230] audit: type=1400 audit(1483985733.860:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=907 comm="apparmor_parser"
[   46.638655] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   46.649215] r8169 0000:02:00.0 enp2s0: link down
[   46.649285] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   46.668494] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   46.683309] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   47.741251] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   53.162000] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   53.168759] vboxdrv: Found 2 processor cores
[   53.171614] vboxdrv: fAsync=0 offMin=0x2f8 offMax=0x4c86
[   53.272364] vboxdrv: TSC mode is Synchronous, tentative frequency 1994999268 Hz
[   53.272369] vboxdrv: Successfully loaded version 5.0.24_Ubuntu (interface 0x00240000)
[   53.291217] VBoxNetFlt: Successfully started.
[   53.308940] VBoxNetAdp: Successfully started.
[   53.339268] VBoxPciLinuxInit
[   53.355446] vboxpci: IOMMU not found (not registered)
[  339.900064] usb 2-3: new high-speed USB device number 2 using ehci-pci
[  340.033052] usb 2-3: New USB device found, idVendor=19d2, idProduct=0307
[  340.033058] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[  340.033064] usb 2-3: Product: MT65xx Android Phone
[  340.033068] usb 2-3: Manufacturer: MediaTek
[  340.033072] usb 2-3: SerialNumber: 0123456789ABCDEF
[  387.592356] usb 2-3: USB disconnect, device number 2
[  387.960036] usb 2-3: new high-speed USB device number 3 using ehci-pci
[  388.093174] usb 2-3: New USB device found, idVendor=19d2, idProduct=1365
[  388.093182] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[  388.093187] usb 2-3: Product: MT65xx Android Phone
[  388.093191] usb 2-3: Manufacturer: MediaTek
[  388.093195] usb 2-3: SerialNumber: 0123456789ABCDEF
[  388.141539] usbcore: registered new interface driver cdc_ether
[  388.165919] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 26:28:41:1b:a9:20
[  388.174798] usbcore: registered new interface driver rndis_host
[  388.198691] usbcore: registered new interface driver rndis_wlan
[  388.241724] rndis_host 2-3:1.0 enp0s29f7u3: renamed from usb0
[  388.268687] IPv6: ADDRCONF(NETDEV_UP): enp0s29f7u3: link is not ready
[  392.173782] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[  454.917302] perf interrupt took too long (2515 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  463.010155] systemd[1]: apt-daily.timer: Adding 1h 32min 53.298750s random time.
[  463.266809] systemd[1]: apt-daily.timer: Adding 6h 54min 13.616924s random time.
[  463.521671] systemd[1]: apt-daily.timer: Adding 1h 8min 29.297994s random time.
[  463.774997] systemd[1]: apt-daily.timer: Adding 11h 19min 43.150124s random time.
[  464.026791] systemd[1]: apt-daily.timer: Adding 2h 11min 43.009956s random time.
[  464.278691] systemd[1]: apt-daily.timer: Adding 8h 44min 1.102107s random time.
[  472.065993] systemd[1]: apt-daily.timer: Adding 7h 36min 30.317261s random time.
[  472.337210] systemd[1]: apt-daily.timer: Adding 7h 56min 42.713662s random time.
[  472.617324] systemd[1]: apt-daily.timer: Adding 10h 9min 18.885822s random time.
[  473.005456] systemd[1]: apt-daily.timer: Adding 1h 41min 8.302815s random time.
[ 1784.223347] perf interrupt took too long (5004 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 2021.482094] usb 2-3: USB disconnect, device number 3
[ 2021.484328] rndis_host 2-3:1.0 enp0s29f7u3: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
[ 2028.672066] usb 2-3: new high-speed USB device number 4 using ehci-pci
[ 2028.805009] usb 2-3: New USB device found, idVendor=19d2, idProduct=0307
[ 2028.805017] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 2028.805022] usb 2-3: Product: MT65xx Android Phone
[ 2028.805026] usb 2-3: Manufacturer: MediaTek
[ 2028.805030] usb 2-3: SerialNumber: 0123456789ABCDEF
[ 2047.220699] usb 2-3: USB disconnect, device number 4
[ 2047.596067] usb 2-3: new high-speed USB device number 5 using ehci-pci
[ 2047.729228] usb 2-3: New USB device found, idVendor=19d2, idProduct=1365
[ 2047.729234] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 2047.729237] usb 2-3: Product: MT65xx Android Phone
[ 2047.729240] usb 2-3: Manufacturer: MediaTek
[ 2047.729242] usb 2-3: SerialNumber: 0123456789ABCDEF
[ 2047.736096] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 62:6b:e3:1e:31:18
[ 2047.826714] rndis_host 2-3:1.0 enp0s29f7u3: renamed from usb0
[ 2047.858333] IPv6: ADDRCONF(NETDEV_UP): enp0s29f7u3: link is not ready
[ 2234.488136] UDF-fs: warning (device sr0): udf_fill_super: No partition found (2)
[ 2234.563783] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2234.566701] ISOFS: changing to secondary root
[ 2258.443767] VFS: busy inodes on changed media or resized disk sr0
[ 3539.637707] usb 2-3: USB disconnect, device number 5
[ 3539.639941] rndis_host 2-3:1.0 enp0s29f7u3: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
[ 3539.900044] usb 2-3: new high-speed USB device number 6 using ehci-pci
[ 3540.033100] usb 2-3: New USB device found, idVendor=19d2, idProduct=1365
[ 3540.033105] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 3540.033108] usb 2-3: Product: MT65xx Android Phone
[ 3540.033111] usb 2-3: Manufacturer: MediaTek
[ 3540.033113] usb 2-3: SerialNumber: 0123456789ABCDEF
[ 3540.036780] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 62:6b:e3:1e:31:18
[ 3540.081518] rndis_host 2-3:1.0 enp0s29f7u3: renamed from usb0
[ 3540.247474] IPv6: ADDRCONF(NETDEV_UP): enp0s29f7u3: link is not ready
[ 3597.977085] usb 2-3: USB disconnect, device number 6
[ 3597.979308] rndis_host 2-3:1.0 enp0s29f7u3: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
[ 3598.240047] usb 2-3: new high-speed USB device number 7 using ehci-pci
[ 3598.372980] usb 2-3: New USB device found, idVendor=19d2, idProduct=1365
[ 3598.372985] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 3598.372988] usb 2-3: Product: MT65xx Android Phone
[ 3598.372991] usb 2-3: Manufacturer: MediaTek
[ 3598.372993] usb 2-3: SerialNumber: 0123456789ABCDEF
[ 3598.378262] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 62:6b:e3:1e:31:18
[ 3598.472210] rndis_host 2-3:1.0 enp0s29f7u3: renamed from usb0
[ 3598.506776] IPv6: ADDRCONF(NETDEV_UP): enp0s29f7u3: link is not ready
[ 4528.383598] usb 2-3: USB disconnect, device number 7
[ 4528.385885] rndis_host 2-3:1.0 enp0s29f7u3: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
[ 5217.244048] usb 2-3: new high-speed USB device number 8 using ehci-pci
[ 5217.376933] usb 2-3: New USB device found, idVendor=19d2, idProduct=0307
[ 5217.376940] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 5217.376946] usb 2-3: Product: MT65xx Android Phone
[ 5217.376950] usb 2-3: Manufacturer: MediaTek
[ 5217.376954] usb 2-3: SerialNumber: 0123456789ABCDEF
[ 5219.481160] usb 2-3: USB disconnect, device number 8
[ 5219.848045] usb 2-3: new high-speed USB device number 9 using ehci-pci
[ 5219.982347] usb 2-3: New USB device found, idVendor=19d2, idProduct=1365
[ 5219.982352] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 5219.982355] usb 2-3: Product: MT65xx Android Phone
[ 5219.982358] usb 2-3: Manufacturer: MediaTek
[ 5219.982360] usb 2-3: SerialNumber: 0123456789ABCDEF
[ 5219.987050] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 3e:1f:32:86:11:f6
[ 5220.025399] rndis_host 2-3:1.0 enp0s29f7u3: renamed from usb0
[ 5220.057492] IPv6: ADDRCONF(NETDEV_UP): enp0s29f7u3: link is not ready
[11676.456244] usb 2-3: USB disconnect, device number 9
[11676.458521] rndis_host 2-3:1.0 enp0s29f7u3: unregister 'rndis_host' usb-0000:00:1d.7-3, RNDIS device
[11676.716037] usb 2-3: new high-speed USB device number 10 using ehci-pci
[11676.864543] usb 2-3: device descriptor read/all, error -71
[11677.780044] usb 2-3: new high-speed USB device number 12 using ehci-pci
[11677.913263] usb 2-3: New USB device found, idVendor=19d2, idProduct=1365
[11677.913271] usb 2-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[11677.913276] usb 2-3: Product: MT65xx Android Phone
[11677.913280] usb 2-3: Manufacturer: MediaTek
[11677.913284] usb 2-3: SerialNumber: 0123456789ABCDEF
[11677.920611] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 3e:1f:32:86:11:f6
[11677.986182] rndis_host 2-3:1.0 enp0s29f7u3: renamed from usb0
[11678.038287] IPv6: ADDRCONF(NETDEV_UP): enp0s29f7u3: link is not ready
user@user-computer:~$
```

---

### Post by DuckHook on 2017-01-09
> **nickworley2 said:**
> …Where are the read/write logs stored btw? What's the filepath?Most system logs are stored in /var/log/   Ubuntu has a nice little log reader accessible from the Dash. Just search for system log. From a terminal, it is:```
gnome-system-log
```> 
…output from dmesg … is gobbledygook to me, but presumably means something to you…Heh, heh. It *is* pretty thick stuff, but it's probably not as dense as it first looks. What we are looking for are lines that contain "error" or "fail" or "warning" or something similar. These can often alert us to problems that the system is experiencing at boot. Don't let system logs intimidate you. I don't know of anyone who is truly comfortable with them. Some gurus may say that they can read them like bad poetry, but I believe that's just posturing. It's a chore and an ordeal for anyone who has to do it. There are command line tricks for zeroing in on items of interest using *grep* and *sort*, but that's a topic for another day.> 
If nothing works, I'll have a temper tantrum and go and sulk in the corner!:lolflag:

…which I've done on more occasions than I can count.

NOTE:

A quick glance through your output shows nothing of note. I'll have a more detailed look later.

Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity and readability. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. I've already edited your last post to conform to this.

---

