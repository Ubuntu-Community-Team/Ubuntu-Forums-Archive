---
title: "ubuntu 32-bit or 64-bit for this computer?"
date: 2016-06-14
forum: New to Ubuntu
---

### Post by Tom_Carr on 2016-06-14
[COLOR=#000000][FONT=Ubuntu]System details says I have a Pentium dual core  CPU es800 @3.30GHz x 2
4 GB memory

Will 64 bit work with this?

I would like to switch to 64 bit so I can get chrome support.


[/FONT][/COLOR]

---

### Post by Tom_Carr on 2016-06-14
This says the Pentium ES800 has 64-bit instruction set

[http://ark.intel.com/products/42802/Intel-Pentium-Processor-E5800-2M-Cache-3_20-GHz-800-MHz-FSB](http://ark.intel.com/products/42802/Intel-Pentium-Processor-E5800-2M-Cache-3_20-GHz-800-MHz-FSB)

This info from the down load site is what is confusing:
> 

[64-bit PC (AMD64) desktop image]("http://releases.ubuntu.com/16.04/ubuntu-16.04-desktop-amd64.iso")Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the i386 images instead.[32-bit PC (i386) desktop image]("http://releases.ubuntu.com/16.04/ubuntu-16.04-desktop-i386.iso")For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.


[http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

It says 32-bit is for most machines, but i believe most machines made in the last 5 year are 64-bit, so it this out of date?

---

### Post by grahammechanical on 2016-06-14
Not necessarily.

It is a fact that a 32 bit OS will run on both 32 bit and 64 bit CPUs but a 64 bit OS will only run on a 64 bit CPU. A lot of potential users have no idea if their machine is 32 bit or 64 bit. So, installing a 32 bit OS will nearly always get them a working OS. This is the reasoning.

Now, take into account the desire of those who have XP machines not to put on the scrap heap working hardware and we just might agree that the statement "for almost all machines" is still applicable. Some XP machines, even with a 64 bit CPU, might benefit from running a 32 bit OS because the 32 bit version will load to a desktop and use less memory than the 64 bit OS. How much memory applications use is a different subject.

[https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared](https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared)

The Ubuntu download page used to have 32 bit Ubuntu as recommended. That has been changed. Now the default is 64 bit Ubuntu and that takes into account the fact that for several years all new machines have come with 64 bit CPUs.

Things are never simple. And excessive technical explanations can cause even more confusion to those who have never before installed a computer operating system.

Regards.

---

### Post by $yl9pAR%t on 2016-06-14
You can use 32-bit OS on both 32-bit and 64-bit computers, hence  "[COLOR=#000000]32-bit is for most machines". Anyway, go ahead with 64-bit Ubuntu.[/COLOR]

---

### Post by poorguy on 2016-06-15
Just because your processor will support 64 bit you also have to have a motherboard that supports 64 bit also. That has all to do with what bios the motherboard is running. You may have to update your motherboard bios. Not all motherboards support 64 bit just because the processor does.

---

### Post by rdb3 on 2016-06-15
My understanding is that the OS is CPU dependent.  So if processor is 64 bit, you can instal 64 bit.  True or not?

 [https://www.quora.com/Is-an-operating-system-cpu-architecture-dependent](https://www.quora.com/Is-an-operating-system-cpu-architecture-dependent)

---

### Post by poorguy on 2016-06-15
I have found that you sometimes just have to try it and see depending on how old the hardware is.

---

