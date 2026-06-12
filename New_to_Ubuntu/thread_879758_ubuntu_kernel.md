---
title: "ubuntu kernel"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by ub007 on 2008-08-04
Hi,

> uname -r gives me the current kernel version.
Is there any code which shows me the current kernel configuration?Also,can I edit and make changes to the configuration without having to re compile the kernel again..?

Thanks in advance,
David

---

### Post by ET! on 2008-08-04
you have a .config file in the kernel folder...that has the current configuration of the kernel

---

### Post by ET! on 2008-08-04
find it using 
locate .config 
and open it using gedit

---

### Post by Bachstelze on 2008-08-04
**ET!**, please! When you don't know the answer, just say nothing instead of throwing vague guesses!

**ub007**, if you are using a standard Ubuntu kernel, the kernel configuration file is stored at /boot/config-<kernel_version>, for example /boot/config-2.6.26-5-generic for kernel version 2.6.26-5-generic. Alternatively, you can also access it from /proc/config.gz, which is a virtual file containing your kernel configuration and compressed in gzip format, you can view it with:

```
zcat /proc/config.gz
```

To answer your second question, no, you can not just edit the config file and hope it will change anything. The configuration is used at compile-time so the compiler know which parts of the kernel it must compile, and how, and afterwards is only there as a reminder.

---

### Post by AdamWood on 2008-08-04
You should also have a copy of the config file in the /boot directory.

---

### Post by ub007 on 2008-08-05
That was helpful....I was interested in comparing how the ubuntu server kernel differs from the desktop version and more so how the server kernel is hardened to resist syn flood & other attacks.....Thanks

---

