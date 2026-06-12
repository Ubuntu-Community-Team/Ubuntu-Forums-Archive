---
title: "NVIDIA Driver Installation and Ubuntu Server"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by hardlinux on 2008-05-04
Hi,

I have a ubuntu server 8.04 with a Nvidia Geforce2 mx 400 video card in it.  I downloaded the ".run" file from nvidia, and stopped the x system, and then typed sudo sh NVIDIA-Linux-xx-xx-xx.run

To make a long story short.  It tells me that I need to specify where the kernel-source is in order to install the driver.

Can someone please help me find out where the path is for the kernel-source, kernel-headers, kernel-devel packages, and how to create a linker?

I am very new to ubuntu but very excited to have a server.

Thanks,

---

### Post by nowshining on 2008-05-04
no need, just install from the repos the kernel headers if I remember correctly and all should work well, just look for headers and find ur kernel version. The only time you'll need to keep the kernel source is when you compile your own from kernel.org, etc..

also it's in /etc/src/

again with ubuntu/kubuntu/etc.. default kernel again all you need to install should be the kernel headers in the repos.

---

