---
title: "Video( movie) lags in ubuntu 12.04 64bit."
date: 2015-03-06
forum: New to Ubuntu
---

### Post by semicolon2 on 2015-03-06
Hi,
No matter which player I use to play movie, it lags whenever some fast scene comes during the movie. I tried vlc player, smplayer, totem movie player 3.0.1.
some outputs:
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

uname -a
Linux oz 3.13.0-46-generic #77~precise1-Ubuntu SMP Mon Mar 2 23:24:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

 sudo lshw -C video
*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4080(size=8)






sudo lshw
description: Notebook
    product: HP ProBook 6550b (WZ303UT#ABA)
    vendor: Hewlett-Packard
    serial: CNU1152CP0
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=WZ303UT#ABA uuid=2CEA36DD-0413-E011-9059-2AC25F06E056
  *-core
       description: Motherboard
       product: 146D
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 73.13
       serial: CNU1152CP0
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 9
          version: 68CDE Ver. F.06
          date: 01/11/2011
          size: 64KiB
          capacity: 2496KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
          slot: CPU 1
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4

---

### Post by gordintoronto on 2015-03-07
What is the resolution of the movie? Your screen is 1366 by 768, so if the movie is higher resolution, displaying each frame takes more work.

---

### Post by semicolon2 on 2015-03-07
I checked with lower resolution as well. And in windows 7, no problem at all. 
How did you know my screen resolution is 1366 by 768?

---

### Post by gordintoronto on 2015-03-08
Your lshw command identified your computer as an HP Probook 6550b, so I could look up the specs.

It's quite puzzling; an i5 should be wonderful for video playback.

---

### Post by semicolon2 on 2015-03-08
I found that if i play movie while sound is mute, I don't see any lag.

---

