---
title: "Makeing a small custom kernel"
date: 2009-07-13
forum: Packaging and Compiling Programs
---

### Post by SteelWo1f on 2009-07-13
Hi. I'm trying to build a custom kernel with a patch to support the latest winbond watchdog. I run 

`fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers` 

and everything works great except the /lib comes out to be 1.1GB. Compare that to the 100-200MB that the server image creates in lib. Does anybody know how to make my image smaller? Whats the magical incantation to make?

Thanks

---

### Post by SteelWo1f on 2009-07-13
make menuconfig -> "Kernel hacking" -> "Compile the kernel with debug info"

Turn the option off.

---

