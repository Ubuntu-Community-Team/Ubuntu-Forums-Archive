---
title: "Compiling Custom Kernel"
date: 2009-08-25
forum: Packaging and Compiling Programs
---

### Post by DavidFromCanada on 2009-08-25
Hi I successfully compiled a patched version of Linux Kernel 2.6.31-rc6 on my headless ubuntu server using these two instructions, the first one I used the commands to patch and configure the kernel but then I used the Ubuntu Wiki's compile command to compile it as a debian package. 
[http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization](http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I installed the packages with no errors and set the system's grub to load the new kernel. Instead what I get is the regular default kernel on boot, the commands ```
sudo reboot
``` and ```
sudo shutdown -r now
``` don't work and apache2 doesn't startup on a reboot. How do I get this custom kernel to boot from grub? I tried editing the menu.lst, but with no success. The only thing I can think of it removing the other kernels.

---

### Post by pdoes on 2009-11-09
What does your menu.lst look like?

---

