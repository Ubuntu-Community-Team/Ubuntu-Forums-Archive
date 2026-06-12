---
title: "Random Crash/Freeze"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by bonkers22 on 2008-11-23
Hello my fellow Ubuntu users.  I have ran into some problems with the new 8.10 version of ubuntu and as I can see I am not the only one.  There are a few issues, but the most annoying is that my computer randomly freezes, I have yet to determine a pattern to the crashes.  But more or less, it happens when I am doing something with the video card (example playing a youtube video.)  But it often happens when opening LimeWire, or even when installing software through the package manager (Synaptic).  It never happens when I install packages through the good old command line.  Here is the "edited" version of

```

sudo lshw

description: Desktop Computer
    *-core
       description: Motherboard
       product: M2A-VM
       vendor: ASUSTeK Computer INC.
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          version: ASUS M2A-VM ACPI BIOS Revision 0804 (06/15/2007)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          slot: Socket AM2
          size: 2100MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
        *-cache:1
             description: L2 cache
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
        *-bank:3
             description: DIMM [empty]
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
             vendor: ATI Technologies Inc
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
    
       *-display
                description: VGA compatible controller
                product: G70 [GeForce 7300 GT]
                vendor: nVidia Corporation
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver

           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

           *-disk:0
                description: ATA Disk
                product: WDC WD800AAJS-00
                vendor: Western Digital
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAP99561045
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=031b031a
           
             *-disk:1
                description: ATA Disk
                product: WDC WD1600AAJS-7
                vendor: Western Digital
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000245ae

```

In a Nutshell

Motherboard: Asus M2A-VM
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ Socket AM2
Memory: 1GB
Video Card: nVidia GeForce 7300 GT
Storage 1: 80 GB SATA II
Storage 2: 160 GB SATA II

```

uname -a
Linux cisco 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

```

This a complete fresh installation, the system was working well before (ubuntu 8.04).  Although I have installed a lot of software (mainly because I use this computer a file server, web server, share iTunes media library etc.)  But this issue has been going on even before installing all this software.

My System logs don't say much.  It just says restart.

```

Nov 23 01:45:47 cisco pulseaudio[5850]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 23 01:45:47 cisco kernel: [   35.339633] hda-intel: Invalid position buffer, using LPIB read method instead.
Nov 23 01:46:08 cisco kernel: [   56.065120] UDF-fs: Partition marked readonly; forcing readonly mount
Nov 23 01:46:08 cisco kernel: [   56.100261] UDF-fs INFO UDF: Mounting volume 'TVCVOLUME', timestamp 2008/11/21 22:49 (1ed4)
Nov 23 01:52:16 cisco syslogd 1.5.0#2ubuntu6: restart.
Nov 23 01:52:17 cisco kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov 23 01:52:17 cisco kernel: Cannot find map file.
Nov 23 01:52:17 cisco kernel: Loaded 66493 symbols from 77 modules.
Nov 23 01:52:17 cisco kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 23 01:52:17 cisco kernel: [    0.000000] Initializing cgroup subsys cpu

```
I don't know what to make of it.  I've also been getting the famous acpid: exiting hang, when shutting down or restarting.  If I wait long enough it does restart or shut down but its very annoying.

I hope someone can point me in the right direction or a SOLUTION...hehe.

Muchas Gracias....


---------------------------

AN UPDATE:

Every time i open my bit torrent client, after about 5 minutes of use it freezes Every TIME, without fail.  This is strange because previously (about 3 days ago, I downloaded two 1.5gig files without a hitch)...

I would appreciate any help...

Thank you.


---------------------------

ANOTHER UPDATE:

The reason why my bit torrent was freezing up is because I am downloading 15GB worth of stuff and the partition that I am downloading to only has 8 GB.  So my mistake.  Regardless I was still locking up and freezing under some random circumstances.  So what I did was fresh install Ubuntu i686 (no 64 bit for me, at least for now).  I don't get the acpid: exiting anymore.  I am currently updating, which includes the newest kernel.  After installation will post results.

---

### Post by Chachee on 2008-12-06
Hey,
  I was having the same problem and have posted about it.  Search my username to find it.  Are you running restriced drivers?  I seem to have cleared up most of the problem by not using them.

  I can still run compiz, and play BSFlag all right.

  Hope this helps.

JT

---

### Post by zieglerj on 2009-02-17
I've been having similar issues. I used to think that they were caused by NVIDIA but the fixes that worked with Hardy don't in Intrepid. Now a pattern is starting to emerge. I've noticed that every time the system crashes or freezes I've got torrents downloading.

I know I have enough space on the partition I'm downloading to (over 300 gb).

---

### Post by .:Justus:. on 2009-03-17
Sorry for bumping an old thread, but i´m experiencing the same problem on intrepid, dunno why. Hope this bug will be fixed soon.

---

