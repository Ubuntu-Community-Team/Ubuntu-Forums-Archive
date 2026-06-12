---
title: "Virtualbox OSE will not start!"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-06-07
Whenever I try to run a virtual machine is Virtualbox OSE, I get an error.

```
--Failed to start the virtual machine OpenSUSE 11.0 Alpha 2--

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

Tried reinstalling the module, logging out, logging in, etc, nothings working though.

---

### Post by Xerp on 2008-06-07
Do you have virtualbox-ose-modules-generic installed?

---

### Post by Madman6510 on 2008-06-07
Yeah, it's installed.

---

### Post by saratchandra on 2008-06-07
Did you update the kernel recently?

---

### Post by Promaster91 on 2008-06-07
What kernel do you have. I know the kernel update knocked out Virtual Box support.

---

### Post by saratchandra on 2008-06-07
Agree with promaster. I downloaded the official version from their site and reinstalled it. It automatically installed the modules and everything is working fine.

---

### Post by Madman6510 on 2008-06-07
That doesn't seem to work either.

I'll try booting into an earlier kernel version later to see if that works.

---

