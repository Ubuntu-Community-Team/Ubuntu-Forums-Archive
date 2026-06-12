---
title: "Linux distros exclusively for 64bit"
date: 2008-08-31
forum: Other OS Talk
---

### Post by crimesaucer on 2008-08-31
Hello, I recently got a laptop with an AMD Turion64x2 TL-60 and of course moved to a x86_64 distro. I had been using Arch i686 with my old Celeron M laptop, so I installed the newest Arch x86_64 overlord for my new 64bit hp dv9920us notebook because I really like Archlinux's rolling releases and the pacman package manager with AUR/ABS, plus the Archwiki's have most of the information needed for installing/configuring anything.


So recently I started using a newer kernel that was available in the Arch AUR called the zenmm-git: [http://aur.archlinux.org/packages.php?ID=18272](http://aur.archlinux.org/packages.php?ID=18272) which is based on the Andrew Morton mm patches and these patches: [http://zen-sources.org/](http://zen-sources.org/). Everything seems to work better/faster besides losing a few things like the automatic mounting of my usb digital camera, and my pm-suspend (actually broken on my hp since the regular Arch kernel went from 2.6.25 to 2.6.26... so I don't think this is a zenmm 2.6.27-rc-1 problem).


Anyway, after building and rebuilding this zenmm kernel, trying different nice setting and latency settings, and seeing if I could build a kernel with only the AMD64 modules, the new hp modules, and nvidia modules, I noticed what a broad range of hardware that the linux kernel can be built for..... anything from really old hardware, old hardware, somewhat recent hardware, super-computers, embedded systems, servers, and the newer hardware like my AMD64x2 or the Intel Dual Core Duo.


Then I was thinking that there are a large portion of us out there that install Linux distros for use on our new laptops and new desktops..... mostly on regular computers that you see in the Sunday paper's advertisements from Circuit City, Office Depot, and Best Buy.....  


Most of these computer's for sale these days are 64bit processors, and mostly dual core AMD or Intel Core Duo..... Yes, I know, Linux is good for old computers..... for giving new life to old hardware, for finding outdated computers for sale at super-cheap prices and then putting a FREE OS on them that is better than vista..... but it seems that a 64bit Linux OS should be more popular than it is, and not considered useless or not needed because i386 is just as fast, or "too beta".....


I'm sure this is an old rant, but I always see people saying that i386 or i686 is just as fast as x86_64 (even thought you lose 1GB for 4GB's of ram), and that a 64bit OS is a pain in the *** to install flash with the 32libs and the nspluggin..... or having to use icetea for java..... I see this in a lot of forums from different distros..... but I also see the threads that are success stories..... and I hear how much people love their 64bit Linux once they configure everything properly.


Now what I also noticed is that when I searched for Linux 64bit distros..... there weren't any that were specializing only in 64. 


All of the 64bit operating systems were just part of the regular distros, like Ubuntu, Arch, or Gentoo..... or even distros like slamd64. And it always seems like 64bit is a side project rather than a main distro..... which to me seems weird, considering the last couple of years 64 bit dual core/quad core/etc has become mainstream and basically the only thing being sold in most computers today.


So my point is that I wish there was someone that would consider putting a lot of focus into a solid 64bit dual core linux distro, that has everything working out of the box, or at least with easily installable packages..... 


Plus, instead of generic 64bit settings, it would be nice during install to have it configured and optimized to the exact 64bit processor that you have..... whether AMD64x2 or Intel Core Dou, or the newer phenom.....


Maybe I'm impatient, maybe I don't know what I'm talking about, but I felt a difference from using a kerenl optimized for my AMD64 over one that was generic x86_64 settings..... not much, maybe it was a few of the other things that I configured into the zenmm kernel that also made everything feel a bit faster and better.


If anybody knows of "the ultimate Linux64 distro" please list it.



At the moment I'm considering the move from Arch to Gentoo AMD64..... I don't know if I'm up to starting over and learning another distro..... the move from xubuntu to Arch was a major leap, and moving from Arch to Gentoo also seems like another leap.....


I guess my winey complaint is that I just wish there was a new distro like Arch that had an install that optimized everything for the exact hardware, with a really good package manager like pacman or aptitiude, that catered exclusively to a 64bit OS and included as many 64bit apps and their work-arounds for things like flash and 32libs.

---

### Post by fwojciec on 2008-08-31
I use 64bit Arch -- it's configured properly and I love it.

I don't think Arch64 can be described as a "side project" that's somehow inferior compared to Arch32, though if you want something preconfigured and everything working out of the box Arch is, obviously, not a good choice.

What makes Arch64 kind of unique (and perhaps more tricky to set up) is that it is, by design, a pure 64bit distro.  Most other "64bit" distros are actually "multilib" and come with 32bit libraries preinstalled.

Unlike with 32bit distros, by the way, processor-specific optimizations in 64bit are pretty meaningless.  Not that they are that meaningful in 32bit distros to begin with...  

However, judging by your comments on the zenmm-git kernel, you might be one of those people who are susceptible to placebo effects :P

---

### Post by mrsteveman1 on 2008-08-31
> **crimesaucer said:**
> 
it seems that a 64bit Linux OS should be more popular than it is, and not considered useless or not needed because i386 is just as fast, or "too beta".....

For most users, the difference is i386 works on just about anything made in the last ~8 years? And x86_64 only works on AMD chips made in the last ~6 years or so, and Intel chips made in the last 4.5-5 years. That's why most people just use i386, its a baseline of compatibility.


> **crimesaucer said:**
> 
So my point is that I wish there was someone that would consider putting a lot of focus into a solid 64bit dual core linux distro, that has everything working out of the box, or at least with easily installable packages..... 


Would be better for anyone who wishes to improve things to just work on an existing distros x86_64 rather than make a new distro entirely :D

> **crimesaucer said:**
> 
Plus, instead of generic 64bit settings, it would be nice during install to have it configured and optimized to the exact 64bit processor that you have..... whether AMD64x2 or Intel Core Dou, or the newer phenom.....

... 

I guess my winey complaint is that I just wish there was a new distro like Arch that had an install that optimized everything for the exact hardware, with a really good package manager like pacman or aptitiude, that catered exclusively to a 64bit OS and included as many 64bit apps and their work-arounds for things like flash and 32libs.

There are very few processor instructions that differ between AMD64 and EM64T, so most distros just compile for what is common between them and avoid per-processor stuff. 

The advantage is probably negligible, the real advantage with x86_64 happened because of increased register size and number, and of course increased address space for memory. You get those things even compiling for generic x86_64.

Plus you would have to do one of a few different things. The gentoo approach would be to compile the packages from source at installation. This takes forever, and requires either a DVD to hold it all or internet access. Plus I've used gentoo extensively, and the "compile at installation" stuff never worked, not once. The only thing that ever worked was to use the stage3 package. So i have little confidence in this approach.

Then you could of course create entirely separate CDs and repositories for each cpu brand, which of course divides things even more than they are now and creates more work to maintain.

Then there is the Apple approach, which is to include code for each architecture in every binary on the system so it just installs and runs on anything. Apples binaries actually run on multiple entirely different architectures, ppc 32 and ppc64, x86, and x86_64. As far as i know the ELF binary format can't do that or at least it isn't right now and no one seems interested (though it really is a cool idea). Plus this probably increases the space needed for installer files, and would push it well over the 700mb CD limit into DVD territory, which increases bandwidth costs for maintainers and users, all for code that in most cases will never be executed, in Apples case only 1 of the multiple arch supported ever get used, but no one is downloading Apples installer anyway it comes on a DVD9 i think.

So in the end, all of the ways a distro might cater to specific brand CPU instructions require a lot of work for what i believe would be little benefit, but i don't really know as i have never seen benchmarks of this sort.

---

### Post by crimesaucer on 2008-08-31
@ fwojciec- I've used Archlinux for about a year now, never had any problems with the install or anything eles..... for either my old Intel Celeron M, or my new AMD Turion64x2 TL-60.....


When I said "side project", I meant it in the way that there is only a Arch64 thread in the Arch forums..... rather than a complete OS dedicated only to a 64bit OS..... and I never claimed it inferior in anyway..... since I've used both the i686 and the x86_64 for my different laptops.


And let's be honest..... Arch is known as the "i686 distro" that's faster than the i386 ubuntu's..... I would like to find the distro that claims to be the best "64bit distro" in the way that Arch can claim it's self as the faster i686 distro.

 

This is most of the info available for Arch64: [http://wiki.archlinux.org/index.php/Arch64_FAQ](http://wiki.archlinux.org/index.php/Arch64_FAQ)

and this: [http://wiki.archlinux.org/index.php/Category:Arch64_(English](http://wiki.archlinux.org/index.php/Category:Arch64_(English))

.....both wiki's helped a lot, but I still had to find out about icedtea for Java in a gentoo AMD64 wiki page. It's in the Arch repo's, but was never mentioned as a way to fix any problems with the java plugin not working in Arch64.


Do not get me wrong..... I love my Arch install, and I love it even better with the zenmm-git kernel from the Arch AUR. But once I compiled my own kernel and set my own tuneables and configured the AMD64 settings, I finally stopped getting certain messages in my dmesg that I would see from the generic Arch26 kernel.


from Arch 2.6.26 x86_64:
```

Clockevents: could not switch to one-shot mode: lapic is not functional.
Could not switch to high resolution mode on CPU 0
Clockevents: could not switch to one-shot mode: lapic is not functional.
Could not switch to high resolution mode on CPU 1

```

from zenmm 2.6.27 for AMD64:
```

Switched to high resolution mode on CPU 0
Switched to high resolution mode on CPU 1

```


more differences in the dmesg:

Arch:
```

SMP: Allowing 2 CPUs, 0 hotplug CPUs
PERCPU: Allocating 34152 bytes of per cpu data
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 964693
Kernel command line: root=/dev/disk/by-uuid/fe976406-f6d8-4cd0-99ea-e6e8aab2c397 resume=/dev/sda5 ro

```


zenmm:
```

PERCPU: Allocating 45504 bytes of per cpu data
NR_CPUS: 2, nr_cpu_ids: 2, nr_node_ids 1
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 964586
Kernel command line: root=/dev/disk/by-uuid/fe976406-f6d8-4cd0-99ea-e6e8aab2c397 resume=swap:/dev/sda5 iommu=noaperture ro

```


Arch:
```

Linux version 2.6.25-ARCH (root@architect) (gcc version 4.3.1 (GCC) ) #1 SMP PREEMPT Thu Jul 3 19:55:27 CEST 2008
Command line: root=/dev/disk/by-uuid/fe976406-f6d8-4cd0-99ea-e6e8aab2c397 resume=/dev/sda5 ro
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
 BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000bffd0000 (usable)
 BIOS-e820: 00000000bffd0000 - 00000000bffe5000 (ACPI data)
 BIOS-e820: 00000000bffe5000 - 00000000bffe6000 (ACPI NVS)
 BIOS-e820: 00000000bffe6000 - 00000000c0000000 (reserved)
 BIOS-e820: 00000000cbf80000 - 00000000d0000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Entering add_active_range(0, 0, 158) 0 entries of 256 used
Entering add_active_range(0, 256, 786384) 1 entries of 256 used
Entering add_active_range(0, 1048576, 1245184) 2 entries of 256 used
end_pfn_map = 1245184
DMI present.
ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
ACPI: XSDT BFFDC0A6, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
ACPI: FACP BFFE4992, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
ACPI: DSDT BFFDC112, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
ACPI: FACS BFFE5FC0, 0040
ACPI: TCPA BFFE4A86, 0032 (r1 Phoeni  x        6040000  TL         0)
ACPI: SRAT BFFE4AB8, 00C8 (r1 AMD    HAMMER    6040000 AMD         1)
ACPI: SSDT BFFE4B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
ACPI: MCFG BFFE4D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
ACPI: HPET BFFE4DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
ACPI: APIC BFFE4DFA, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
ACPI: BOOT BFFE4E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
ACPI: SLIC BFFE4E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
ACPI: DMI detected: Hewlett-Packard
Entering add_active_range(0, 0, 158) 0 entries of 256 used
Entering add_active_range(0, 256, 786384) 1 entries of 256 used
Entering add_active_range(0, 1048576, 1245184) 2 entries of 256 used
early res: 0 [0-fff] BIOS data page
early res: 1 [6000-7fff] SMP_TRAMPOLINE
early res: 2 [200000-68d7cb] TEXT DATA BSS
early res: 3 [37f5b000-37fef987] RAMDISK
early res: 4 [9e000-9efff] EBDA
early res: 5 [8000-dfff] PGTABLE
 [ffffe20000000000-ffffe200001fffff] PMD ->ffff810001200000 on node 0
 [ffffe20000200000-ffffe200003fffff] PMD ->ffff810001600000 on node 0
 [ffffe20000400000-ffffe200005fffff] PMD ->ffff810001a00000 on node 0
 [ffffe20000600000-ffffe200007fffff] PMD ->ffff810001e00000 on node 0
 [ffffe20000800000-ffffe200009fffff] PMD ->ffff810002200000 on node 0
 [ffffe20000a00000-ffffe20000bfffff] PMD ->ffff810002600000 on node 0
 [ffffe20000c00000-ffffe20000dfffff] PMD ->ffff810002a00000 on node 0
 [ffffe20000e00000-ffffe20000ffffff] PMD ->ffff810002e00000 on node 0
 [ffffe20001000000-ffffe200011fffff] PMD ->ffff810003200000 on node 0
 [ffffe20001200000-ffffe200013fffff] PMD ->ffff810003600000 on node 0
 [ffffe20001400000-ffffe200015fffff] PMD ->ffff810003a00000 on node 0
 [ffffe20001600000-ffffe200017fffff] PMD ->ffff810003e00000 on node 0
 [ffffe20001800000-ffffe200019fffff] PMD ->ffff810004200000 on node 0
 [ffffe20001a00000-ffffe20001bfffff] PMD ->ffff810004600000 on node 0
 [ffffe20001c00000-ffffe20001dfffff] PMD ->ffff810004a00000 on node 0
 [ffffe20001e00000-ffffe20001ffffff] PMD ->ffff810004e00000 on node 0
 [ffffe20002000000-ffffe200021fffff] PMD ->ffff810005200000 on node 0
 [ffffe20002200000-ffffe200023fffff] PMD ->ffff810005600000 on node 0
 [ffffe20002400000-ffffe200025fffff] PMD ->ffff810005a00000 on node 0
 [ffffe20002600000-ffffe200027fffff] PMD ->ffff810005e00000 on node 0
 [ffffe20002800000-ffffe200029fffff] PMD ->ffff810006200000 on node 0
 [ffffe20002a00000-ffffe20002bfffff] PMD ->ffff810006600000 on node 0
 [ffffe20002c00000-ffffe20002dfffff] PMD ->ffff810006a00000 on node 0
 [ffffe20002e00000-ffffe20002ffffff] PMD ->ffff810006e00000 on node 0
 [ffffe20003000000-ffffe200031fffff] PMD ->ffff810007200000 on node 0
 [ffffe20003200000-ffffe200033fffff] PMD ->ffff810007600000 on node 0
 [ffffe20003400000-ffffe200035fffff] PMD ->ffff810007a00000 on node 0
 [ffffe20003600000-ffffe200037fffff] PMD ->ffff810007e00000 on node 0
 [ffffe20003800000-ffffe200039fffff] PMD ->ffff810008200000 on node 0
 [ffffe20003a00000-ffffe20003bfffff] PMD ->ffff810008600000 on node 0
 [ffffe20003c00000-ffffe20003dfffff] PMD ->ffff810008a00000 on node 0
 [ffffe20003e00000-ffffe20003ffffff] PMD ->ffff810008e00000 on node 0
 [ffffe20004000000-ffffe200041fffff] PMD ->ffff810009200000 on node 0
 [ffffe20004200000-ffffe200043fffff] PMD ->ffff810009600000 on node 0
Zone PFN ranges:
 DMA             0 ->     4096
  DMA32        4096 ->  1048576
  Normal    1048576 ->  1245184
Movable zone start PFN for each node
early_node_map[3] active PFN ranges
    0:        0 ->      158
    0:      256 ->   786384
    0:  1048576 ->  1245184
On node 0 totalpages: 982894
  DMA zone: 56 pages used for memmap
  DMA zone: 1177 pages reserved
  DMA zone: 2765 pages, LIFO batch:0
  DMA32 zone: 14280 pages used for memmap
  DMA32 zone: 768008 pages, LIFO batch:31
  Normal zone: 2688 pages used for memmap
  Normal zone: 193920 pages, LIFO batch:31
  Movable zone: 0 pages used for memmap
Detected use of extended apic ids on hypertransport bus
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 (Bootup-CPU)
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Processor #1
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Setting APIC routing to flat
ACPI: HPET id: 0x10de8201 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information

```


zenmm:
```

Linux version 2.6.27-rc1-zenmm0 (root@hp) (gcc version 4.3.1 20080724 (prerelease) (GCC) ) #1 SMP PREEMPT ZEN Fri Aug 22 19:13:47 EDT 2008
Command line: root=/dev/disk/by-uuid/fe976406-f6d8-4cd0-99ea-e6e8aab2c397 resume=swap:/dev/sda5 iommu=noaperture ro
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
  Centaur CentaurHauls
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
 BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000bffd0000 (usable)
 BIOS-e820: 00000000bffd0000 - 00000000bffe5000 (ACPI data)
 BIOS-e820: 00000000bffe5000 - 00000000bffe6000 (ACPI NVS)
 BIOS-e820: 00000000bffe6000 - 00000000c0000000 (reserved)
 BIOS-e820: 00000000cbf80000 - 00000000d0000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
last_pfn = 0xbffd0 max_arch_pfn = 0x3ffffffff
init_memory_mapping
 0000000000 - 00bfe00000 page 2M
 00bfe00000 - 00bffd0000 page 4k
kernel direct mapping tables up to bffd0000 @ 8000-d000
last_map_addr: bffd0000 end: bffd0000
init_memory_mapping
 0100000000 - 0130000000 page 2M
kernel direct mapping tables up to 130000000 @ b000-11000
last_map_addr: 130000000 end: 130000000
RAMDISK: 37f87000 - 37fefb54
DMI present.
ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
ACPI: XSDT BFFDC0A6, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
ACPI: FACP BFFE4992, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
ACPI: DSDT BFFDC112, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
ACPI: FACS BFFE5FC0, 0040
ACPI: TCPA BFFE4A86, 0032 (r1 Phoeni  x        6040000  TL         0)
ACPI: SRAT BFFE4AB8, 00C8 (r1 AMD    HAMMER    6040000 AMD         1)
ACPI: SSDT BFFE4B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
ACPI: MCFG BFFE4D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
ACPI: HPET BFFE4DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
ACPI: APIC BFFE4DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
ACPI: BOOT BFFE4E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
ACPI: SLIC BFFE4E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
ACPI: DMI detected: Hewlett-Packard
(7 early reservations) ==> bootmem [0000000000 - 0130000000]
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
  #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
  #2 [0000200000 - 0000699b74]    TEXT DATA BSS ==> [0000200000 - 0000699b74]
  #3 [0037f87000 - 0037fefb54]          RAMDISK ==> [0037f87000 - 0037fefb54]
  #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
  #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
  #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
Scan SMP from ffff880000000000 for 1024 bytes.
Scan SMP from ffff88000009fc00 for 1024 bytes.
Scan SMP from ffff8800000f0000 for 65536 bytes.
found SMP MP-table at [ffff8800000f8220] 000f8220
 [ffffe20000000000-ffffe200043fffff] PMD -> [ffff880028200000-ffff88002c5fffff] on node 0
sizeof(struct page) = 56
Zone PFN ranges:
  DMA      0x00000000 -> 0x00001000
  DMA32    0x00001000 -> 0x00100000
  Normal   0x00100000 -> 0x00130000
Movable zone start PFN for each node
early_node_map[3] active PFN ranges
    0: 0x00000000 -> 0x0000009e
    0: 0x00000100 -> 0x000bffd0
    0: 0x00100000 -> 0x00130000
On node 0 totalpages: 982894
  DMA zone: 2658 pages, LIFO batch:0
  DMA32 zone: 768008 pages, LIFO batch:31
  Normal zone: 193920 pages, LIFO batch:31
Detected use of extended apic ids on hypertransport bus
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
ACPI: HPET id: 0x10de8201 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information
SMP: Allowing 2 CPUs, 0 hotplug CPUs

```


..... now I'm not going to show the rest of the dmesg files of the acpi differences because I'm sure it all has to do with the zenmm-rc-1 having new experimental HP WMI modules which I'm using, and of course being the new 2.6.27 rc.


As for compiling the kernel, the Arch kerenl use basically the same settings in the .config as the config.saved.x86_64 that I made with the "super slick menuconfig" that I used for the zenmm kernel, they are practically the same except for the zen tuneables part. 


All I did was switch from generic 64 to AMD64 (and of course the new hp wmi and anything that was new for 2.6.27).




I should say that I am far from expert..... this is all new to me, but I am into learning this because I enjoy Linux and learning as much as I can about computers.



This is in no way an attack against Arch, I know I could just compile Arch kerenl with menuconfig and set the AMD settings instead of generic64, and I could even add zen patches or the mm patches. This post wasn't about Arch, but rather about lack of 64bit options for most distros. I think Arch is one of the better supported 64bit distro..... if you look into the x86_64 forum of ubuntu, it will almost make you not want to install the 64bit OS because of so many anti-64 posts and problem posts.


***********************************************************************


@ mrsteveman1- Your first 2 responses made a lot of sense.


For your third responses, they all make sense to me too, but it also seems that an independent distro could create an OS that just focused on all of the most recent chips (with what they already know and use) and the most mainstream laptops and desktops. Dropping the hardware, and modules, and coding for older computers and other things that are already covered by so many good distros. Instead of adding support for super computers, and embedded systems (already covered by everyone else), why not just thin it out and just include new 64bit chips and the common systems that it runs on.


Creating 2 different 64bit OS (choice of either AMD64 or Intel), with each having the individual settings for all of the choices that each manufacturer has available in the last 5-8 years including the newest dual core chips, supporting the most common and new motherboards and graphic cards, and then creating this distro for the average computer user that doesn't run a server, or isn't a systems-administrator running linux at the work place.


Basically, someone that has spent time on Ubuntu and Arch, that enjoys using Linux at home instead of Vista or xp and isn't worried about supper computing and networks/sys-admin stuff like someone using gentoo, redhat, debian, or fedora might, even though they enjoy using a terminal and compiling packages for the fun of it.


I just figure that all of the popular distros seem to have everything covered, all of the development of new things, and maintaining legacy. And every day I see some "New Distro" that is just an Ubuntu clone..... with a blue theme and about 5 things that are easily installable or configured..... so why not something new.

---

### Post by fwojciec on 2008-09-01
Arch is not faster than Ubuntu because it is i686 optimized -- overall speed is the cumulative effect of many variables.  Debian or CentOS, which are both i386 optimized, can be as fast if not faster than Arch: [http://bbs.archlinux.org/viewtopic.php?id=44716]("http://bbs.archlinux.org/viewtopic.php?id=44716").  Not to mention Slackware, i486 optimized, which is certainly not slower than Arch.  I've also used a 32bit Crux system which was fully compiled with optimizations for my specific processor and it wasn't perceptibly faster than generic i686 Arch.

Even if one could make the case that there are differences/benefits to using a i686 optimized distro over a i386 optimized one, it's much more difficult to make an argument like that for 64bit distros, since all 64bit processors are pretty similar, as mrsteveman1 also mentions.  All 64bit distros are, in essence, "i686" distros -- that's what I was trying to say.

Icedtea6 is now openjdk6 by the way -- it was just added to [extra] a week ago or so, and it is on its way to becoming the default Java package in Arch: [http://archlinux.org/pipermail/arch-dev-public/2008-August/007416.html]("http://archlinux.org/pipermail/arch-dev-public/2008-August/007416.html")  As you can see the whole opensource java thing is about a month old, at least in Arch -- this is why there isn't a whole lot of documentation about it yet.

As for different kernels:
```
$ dmesg | grep "high resolution"
Switched to high resolution mode on CPU 0
Switched to high resolution mode on CPU 1
```
This is with standard Arch64 kernel, so apparently there is some bug with the current kernel on your hardware.  LAPIC problems are not uncommon, I know that quite a lot of people were experiencing lapic_timer related problems with the latest kernel ([http://bbs.archlinux.org/viewtopic.php?id=53521]("http://bbs.archlinux.org/viewtopic.php?id=53521")) -- I don't know if this is the same issue as on your system, though.  Generally speaking, my experience is that experimental kernels are too much hassle and, in the long run, introduce more problems than improvements.

I haven't heard of any distro like what you're describing/envisioning.  If you want something tailor-made for your hardware you can always use gentoo or another source based distro...

EDIT:  Also, "thinning out" kernels doesn't make much sense, since most things are compiled as modules these days, and loaded only as necessary.  So the only real benefit of doing this would be to save disk space (we're talking 10-15MB, not more) and maybe a couple of seconds during boot, since the module detection step can be skipped if things are compiled directly into the kernel (not as modules).

---

### Post by crimesaucer on 2008-09-01
> **fwojciec said:**
> Arch is not faster than Ubuntu because it is i686 optimized -- overall speed is the cumulative effect of many variables. 

I found Arch i686 MUCH faster than Ubuntu and Xubuntu. I have seen a lot people that think the same. Even back when I was using xubuntu with no compiz, and all of the most known speed hacks, I found that a fresh Arch install was much faster, even if I used compiz (on xfce4).



> Icedtea6 is now openjdk6 by the way -- it was just added to [extra] a week ago or so, and it is on its way to becoming the default Java package in Arch: [http://archlinux.org/pipermail/arch-dev-public/2008-August/007416.html]("http://archlinux.org/pipermail/arch-dev-public/2008-August/007416.html")  As you can see the whole opensource java thing is about a month old, at least in Arch -- this is why there isn't a whole lot of documentation about it yet.


Yes, I realize that and probably should call it by it's correct name. Like I said, it was easily installable from the arch repo, I just hadn't read anywhere about it in the forums or the wiki.... I didn't really look either because there is only one website that I visit that needs java, so maybe there was info on java and 64 in a thread that I never saw since I didn't care. Most technical questions about anything have already been asked and solved on the Arch forums if you search around enough.

Again, I enjoy arch a lot and think it's a really good distro, so please don't take me as sounding like I'm anti-arch or anti-ubuntu or anything.....  


> Generally speaking, my experience is that experimental kernels are too much hassle and, in the long run, introduce more problems than improvements.


The zenmm-git has been a fun learning experience for me, and not really a hassle yet..... if I run into a problem, I still have my regular Arch kernel and my dual boot Vista.


> I haven't heard of any distro like what you're describing/envisioning.  If you want something tailor-made for your hardware you can always use gentoo or another source based distro...


Well..... I don't think anything exists like that yet, and gentoo seems to be one of the most dedicated to 64bit.


> EDIT:  Also, "thinning out" kernels doesn't make much sense, since most things are compiled as modules these days, and loaded only as necessary.  So the only real benefit of doing this would be to save disk space (we're talking 10-15MB, not more) and maybe a couple of seconds during boot, since the module detection step can be skipped if things are compiled directly into the kernel (not as modules).


True, but I wouldn't mind the added space of another mp3, and most of the modules included in the default Linux kernel aren't ever going to be used by the average user on a recent computer of the last 5-8 years. And for the super technical Linux users, they aren't going to leave the top distros that they're using. And I found the time to compile all of the added modules that I didn't need compared to the bare minimum of necessary modules to be very noticeable.

---

### Post by mrsteveman1 on 2008-09-01
There is a lot of stuff in the kernel source that compiles down to nothing when you select a specific architecture. For instance you won't find the compiler process paying too much attention to ARM or PPC source files if you select x86_64, and there probably won't be anything left of them in the binary at the end.

Same goes for the mainframe stuff.

---

### Post by crimesaucer on 2008-09-01
> **mrsteveman1 said:**
> There is a lot of stuff in the kernel source that compiles down to nothing when you select a specific architecture. For instance you won't find the compiler process paying too much attention to ARM or PPC source files if you select x86_64, and there probably won't be anything left of them in the binary at the end.

Same goes for the mainframe stuff.

Yeah, like I said I'm just now trying to learn about the kernel and what really makes Linux work.


I guess I'm going to give gentoo a try to see how it compares to Arch.

---

### Post by mips on 2008-09-01
Ach64 here and I love it, no problems to complain about.

There used to be a distro that was 64 bit only but I cannot remember its name.

---

