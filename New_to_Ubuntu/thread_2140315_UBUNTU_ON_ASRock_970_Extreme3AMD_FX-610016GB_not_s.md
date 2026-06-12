---
title: "UBUNTU ON ASRock 970 Extreme3/AMD FX-6100/16GB not seeing past 8GB"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by JJJJNR on 2013-04-29
I have ubuntu 12.04LTS running on a ASrock 970 extreme 3 M/B that has 16GB ram, yet when I go to   my OS (ubuntu 64bit or vmware ESXi 4/5) it will only see 8GB, but when I fire a  command at the OS  it reports that there are 16GB ram installed but it  is not released to  the OS..
 [INDENT]                     sudo python check-my-memory.py
[sudo] password for rory: 
check-my-memory.py - version: SJ 2013-02-22
OK, you're root
ANALYSIS:
Total of physical memory modules found 16384 MB in 4 memory module(s)
BIOS offers 8169 MB as usable
Memory seen by OS 7966 MB
BIOS version 06/26/2012
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 8215 MB
Memory difference between BIOS offering and memory seen by OS 203 MB
Memory difference between DIMM hardware and memory seen by OS 8418 MB

ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 16GiB
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 4GiB
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 4GiB
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 4GiB
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 4GiB
       description: BIOS
       size: 64KiB
       capacity: 4032KiB

Finished

 
I've also ran memcheck and it will pass all tests but only on 8GB!                 
[/INDENT]
[INDENT]Tried fedora live CD and it only see's 8GB also, have an old hard drive  with a 32bit version of vista and it boots no problem and can see 16GB  with 4GB usable, at this stage im just lost.
[/INDENT]
 

 
ASRock 970 Extreme3
AMD FX-6100
16GB-Kit G.Skill Ares PC3-10667U CL9-9-9-24
30GB SSD
BIOS 1.60                 (latest)

---

### Post by bigpook on 2013-06-08
I am having the same exact issue as you.
Same mobo, using FX8350 and GSkill memory.

dmesg suggests enabling IOMMU in the BIOS. Default is disabled. I enabled IOMMU but still only see 8G.
dmesg still suggests enabling IOMMU in the BIOS.
Perhaps linux is not seeing that?

I am using linux mint 15 64 bit.
I tried booting off the mint 15 live disk but get the same memory issue.

Let me know if you figured it out.

Still working on it on my end.

---

