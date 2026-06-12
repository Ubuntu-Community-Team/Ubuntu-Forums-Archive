---
title: "difference between i686 and x86_64"
date: 2013-06-15
forum: Recurring Discussions
---

### Post by 0rajesh1 on 2013-06-15
I have Intel core 2 duo machine with the fallowing cpu details


Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               800.000
BogoMIPS:              3989.86
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K


Architecture field of lscpu is i686 but the CPU op modes is both 32 bit and 64 bit, Is it possible to install 64 bit OS on my machine, Specifically what is the difference between i686 and x86_64 ?
Also ht flag is present my CPU flags, is it possible to enable hyper threading on my machine? if so how to enable hyper threading?

---

### Post by 3rdalbum on 2013-06-16
Your CPU is 64-bit capable. You would have a slight speedup for some operations, if you install 64-bit Ubuntu.

The difference between i686 and x86_64 is that the latter is 64-bit and a little more optimised for modern CPUs.

I didn't think the Core 2 CPUs had hyperthreading, but if yours does it will automatically be used. If you don't see two extra CPUs, then either there is no hyperthreading or you have it turned off in your BIOS.

---

### Post by HiImTye on 2013-06-16
if you can use 64bit, and you have a decent amount of RAM (more than, say, 2GB), you should use a 64bit OS.
64bit instructions offer better performance, but also security features, etc, that 32bit does not without a PAE kernel. 
PAE kernels run slower than even 32bit kernels, and are normally chosen automagically if you have a 64bit capable machine.
64bit machines will fall back to 32bit mode if a 32bit OS is loaded, which is why your 32bit OS works

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by 0rajesh1 on 2013-06-16
thank u 3rdalbum

---

### Post by 0rajesh1 on 2013-06-16
thank u HiImtye

---

