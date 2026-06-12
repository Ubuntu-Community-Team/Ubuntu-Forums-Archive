---
title: "Searching sourcecode that fully loads CPU while compiling"
date: 2005-11-18
forum: Programming Talk
---

### Post by fbn on 2005-11-18
Hi,

I want to check if my hardware is okay and for this check I'm planning to let a python script compile some source code again and again and check if the output (md5sum) is the same everytime.

First I wanted to use the Linux kernel source but it's a bit too huge, I'm looking for some code that is not larger than 5 MB and makes heavy load on CPU while compiling.

Any ideas?

---

### Post by toojays on 2005-11-18
How about bash?

It sounds to me like what you should really do is run memtest, which should be one of the options in your boot menu if you are on an x86 machine.

---

### Post by ubuntu_demon on 2005-11-18
some tips.

cpu :
-compile the kernel

videocard :
-run a heavy computer game like doom 3 or quake 4

memory :
-run a memtest (choose from grub)

harddisk :
$ sudo touch /forcefsck

dust :
-open the case and remove all the dust. (a toothbrush may work to get to some places)

heat :
-be sure to monitor the system temperatures (in the bios or using lm-sensors). If the system crashes collide with heat peaks you probably need some more cooling.

think logically and remove/add/replace hardware to find the problem.

After everything is more or less ruled out and there are still problems and you are sure that it's not software problems then  it's probably the power supply or mainboard. Try replacing those and see if it solves the problem.

good luck!

---

