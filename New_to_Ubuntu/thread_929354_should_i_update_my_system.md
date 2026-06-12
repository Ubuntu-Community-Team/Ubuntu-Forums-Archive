---
title: "should i update my system?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by terry liang on 2008-09-24
i use the ubuntu 8.04 now.And the graphy card is NVIDIA 6100.
At first,my kernel was 2.6.16 and i can  use the restricted driver.  after i update it to 2.6.19. and i can not use it again.
so i have to prefer the old kernel every time.should i update it?


another question:i founld i can not listen music on line.
:(

---

### Post by Melk79 on 2008-09-25
Have you installed the ubuntu-restricted-extras package from Synaptic? (System>Administration>Synaptic Package Manager)  That will add many of the restricted codecs and plugins required to play various media formats.

Yes, updating is good and shouldn't have broken your Nvidia driver.  I use Nvidia as well and have never had that occur.  You could try checking under System>Administration>Hardware Drivers and see if it is enabled.  Let us know some more detail from those items and we can help.

---

### Post by onero on 2008-09-25
The drivers for nvidia are proprietary, and are implemented as kernel modules. What this means is every time a new kernel is installed, the nvidia kernel module has to be recompiled for the new kernel. Ubuntu tries to do this automatically, but it doesn't always work; personally, I've taken to installing the drivers manually every time the kernel upgrades, which isn't all that often anyway.

You can download the drivers from [http://www.nvidia.com/page/drivers.html](http://www.nvidia.com/page/drivers.html), then restart your computer and in the GRUB prompt choose the option that gives the root shell (recovery mode, or something). Then in the shel, just cd to where you downloaded the file, and run

sh <filename>

Just go though the prompts, and the driver should install with no problems. Then just reboot.

---

