---
title: "Exporting Kernel Module Functions to Userspace"
date: 2010-03-06
forum: Programming Talk
---

### Post by DBQ on 2010-03-06
Hi everybody.

Does anybody know how to export the functions defined in the kernel module to userspace?

Ie I want a user program to be able to call function defined in the kernel module.

---

### Post by jpkotta on 2010-03-06
> **DBQ said:**
> Hi everybody.

Does anybody know how to export the functions defined in the kernel module to userspace?

Ie I want a user program to be able to call function defined in the kernel module.

In general, no.  If it's something that doesn't depend on any kernel functionality (something like strcpy() or sqrt()), then you could probably do it with a couple of #ifdefs.  If it does depend on kernel functionality, e.g. get the state of some kernel variables or writing to kernel data structures, then you'd have to use some sort of interface like ioctl or a device node in /dev/.  I guess the closest thing to calling a kernel function would be a syscall, but an ioctl is probably what you want.

---

