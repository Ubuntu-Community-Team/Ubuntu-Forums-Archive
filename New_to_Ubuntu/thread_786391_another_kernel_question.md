---
title: "another kernel question"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-08
i am using Ubuntu 8.04
What is the difference between the following 2 folders?
Which is the main one?
1. linux-headers-2.6.24-16
2. linux-headers-2.6.24-16-generic

these 2 folders are found in Computer/Filesystem/usr/src

thank you

---

### Post by Rocket2DMn on 2008-05-08
The first is for the kernel version itself, the second is specific for your hardware architecture.  From Synaptic:
> Header files related to Linux kernel version 2.6.24 
This package provides kernel header files for version 2.6.24, for sites
that want the latest kernel headers. Please read
/usr/share/doc/linux-headers-2.6.24-16/debian.README.gz for details
> Linux kernel headers for version 2.6.24 on x86/x86_64 
This package provides kernel header files for version 2.6.24 on
x86/x86_64.

This is for sites that want the latest kernel headers.  Please read
/usr/share/doc/linux-headers-2.6.24-16/debian.README.gz for details.

These are used so programs can communicate with the kernel.

---

