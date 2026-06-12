---
title: "[!] Kernel compiler and gcc seem to be different versions."
date: 2009-03-28
forum: Packaging and Compiling Programs
---

### Post by sdowney717 on 2009-03-28
while trying to compile qc-usb, i get these errors.
(by the way, qc-usb module was already in the kernel but my quickcam web does not work, so I thought I would try and compile it)


```
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.18.93.20081009
Kernel compiler: gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
	export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
```

so what to do?

---

### Post by jokker on 2009-04-25
Same error here on Ubuntu Jaunty... Did you find a solution man ?

---

### Post by sdowney717 on 2009-05-26
never did.
some of these things are not meant to be.
the people who bothered to put this stuff together in the first place, unless they actively maintain code, things like this happen, IMO.
I ended up buying a different web cam and then I ended up not using it at all.

---

