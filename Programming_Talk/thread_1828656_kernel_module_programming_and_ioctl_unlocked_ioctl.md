---
title: "kernel module programming and ioctl unlocked ioctl"
date: 2011-08-19
forum: Programming Talk
---

### Post by mehrun on 2011-08-19
Dear guys,
I have a question about ioctl in the kernel module programming and the device driver programming.
In compiling a character device driver I have been forced to modify the ioctl to the unlocked_ioctl for the sake of loss of ioctl from kernel's header files. I want to know, which approach is the reason of this change?

An article, mailing list talk and/or everything else that describes entire ioctl and new kernel changes or ubuntu specific changes is ideal ;)

Thank you in advance.

---

