---
title: "Rebooting new kernel failed"
date: 2015-11-11
forum: New to Ubuntu
---

### Post by adrianxu on 2015-11-11
[FONT=arial]Hi guys,

I'm new to Linux. I've been trying to compile and install a new kernel following the rest steps:

[/FONT][FONT=arial][COLOR=#000000]$makemenuconfig
[/COLOR][COLOR=#000000]$make[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]$make modules[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]$make modules_install[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]$make install[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]$cd /boot[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]$mkinitramfs -o initrd.img-2.6.39 2.6.39[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]$update-grub[/COLOR][/FONT]
[FONT=arial][COLOR=#000000]
Everything worked just fine, but when I reboot and choose the new kernel, it got stuck at loading initial ramdisk...

Does anyone know where went wrong?
Appreciate it!![/COLOR][/FONT]

---

### Post by grahammechanical on 2015-11-12
Did you get any error messages informing you that certain modules were not compiled? Did you download the three relevant kernel packages.

linux-headers- .... .... _amd64.deb
linux-headers- .... .... _all.deb
linux-image- .... .... _amd64.deb

Assuming that you have a 64 bit CPU and not a 32 bit CPU. I followed this guide

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

Regards.

 

Regards

---

### Post by deadflowr on 2015-11-12
Try changing the mkinitramfs to /boot/initrd instead of just initrd.

Seems it needs the absolute path, from reading around:
[https://www.howtoforge.com/howto_linux_kernel_2.6_compile_debian](https://www.howtoforge.com/howto_linux_kernel_2.6_compile_debian)
> [I][FONT=Courier New, Courier, mono][SIZE=2]cd /boot/
mkinitrd -o /boot/initrd.img-2.6.8.1 2.6.8.1[/SIZE][/FONT][/I]

also, why such an old kernel?
(And can we really call an old kernel in anyway, new?)

---

