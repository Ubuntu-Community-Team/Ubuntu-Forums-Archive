---
title: "Error compiling scramdisk-2.1"
date: 2011-12-21
forum: Packaging and Compiling Programs
---

### Post by jcoles on 2011-12-21
This error also occurs when attempting to compile scramdisk-2.1. This package compiled successfully on pre-3.0 kernels. The current kernel header packages are installed. After a couple of hours searching about in the package information online, I couldn't find a package that I don't already have installed that would supply the missing files. 

The problem is in the kernel files, not the application:
> In file included from /lib/modules/3.0.0-14-generic/build/include/linux/thread_info.h:52:0,
                 from /lib/modules/3.0.0-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/3.0.0-14-generic/build/include/linux/spinlock.h:50,
                 from /lib/modules/3.0.0-14-generic/build/include/linux/mmzone.h:7,
                 from /lib/modules/3.0.0-14-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/3.0.0-14-generic/build/include/linux/slab.h:12,
                 from cipher.c:52:
/lib/modules/3.0.0-14-generic/build/include/linux/bitops.h:22:24: fatal error: asm/bitops.h: No such file or directory


Any ideas about what's wrong?

---

### Post by oldos2er on 2011-12-21
Moved to Packaging & Compiling Programs.

---

### Post by SevenMachines on 2011-12-22
driver/Makefile uses the minor version number >6 (ie, 2.6.30) as its test for newer kernels, obviously 3.0.something fails this test so its considered an older kernel. You could replace the 
```
 ifeq ($(MINOR),6)
```with 
```
 ifeq ($(MAJOR),3)
```as a hack, this will break the build on 2.6 kernels though. You could also do something like
```
--- Makefile.bak    2011-12-22 09:49:35.733494463 +0000
+++ Makefile    2011-12-22 09:59:28.580434232 +0000
@@ -78,7 +78,9 @@
 MAINHDR = $(MAINSRC:.c=.h) sdstructs.h
 HEADERS = $(SOURCES:.c=.h) sdstructs.h
 
-ifeq ($(MINOR),6)
+KERNEL_GT_26 = ($(MAJOR) >= 3) || ($(MINOR) > 6)
+
+ifneq ($(KERNEL_GT_26),0)
 EXTRADIR = extra
 MODULEOBJECT = scramdisk.ko
 

```should work i think

---

### Post by jcoles on 2011-12-27
Thanks, SevenMachines.

It's also necessary to change the main Makefile. In the "deb:" section, change the line
```
elif test "$(MINOR)" = "6"; then \ 
```to 
```
elif test "$(MINOR)" = "6" -o "$(MAJOR)" = "3"; then \ 
```

---

