---
title: "which rt_preempt patch to take"
date: 2013-04-03
forum: Packaging and Compiling Programs
---

### Post by user000000 on 2013-04-03
Hello

I have three questions concerning following problem: I have a closed source kernel module for a PCI card that works only on 12.04.01 with kernel 3.2.0-29-generic. I need, though, to write a program in realtime preemption mode, because I have to guarantee to access the pci kernel module at least all 500us.

Question one: Can I compile 3.2.0-29 with rt_preemption patches and insert the closed source module which was compiled for 3.2.0-29-generic or won't this work?

Question two: If question one works, how can I find the correct realtime patches for this specific kernel? In the rt/3.2/older/ I can only find 3.2-rc1 until 3.2-rc6 or then above 3.2.5. Am I missing something?

Question three: Is there another way to guarantee to achieve the 500us guarantee?

Thanks a lot.

---

### Post by user000000 on 2013-04-09
Ok, I'm one step further. I have noticed that when doing "make menuconfig" on linux-source-3.2.0-29, there is the caption "Kernel 3.2.24". So for an unknown reason, the ubuntu Kernel 3.2.0-29 seems to correspond to the mainline kernel version 3.2.24... So i have compiled the kernel with the 3.2.24 rt_preempt patch and the option CONFIG_MODULE_FORCE_LOAD and CONFIG_PREEMPT_RT. And i took the .config file of the 3.2.0-29 ubuntu kernel to be sure that the other config options stay the same.

Now I can program realtime apps, but when I try to load the closed source module which worked on 3.2.0-29-generic with "modprobe -f module", I get "unknown symbol: mutex_lock" and "unknown symbol: down_read" and up_read and mutex_unlock.

Does anyone have a clue?

---

