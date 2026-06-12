---
title: "bug"
date: 2013-06-06
forum: Programming Talk
---

### Post by girishdev14 on 2013-06-06
how to remove the bug:-drivers/video/omap2/vram.c:35:23: fatal error: plat/sram.h: No such file or directory
compilation terminated..while compiling the kernel..link is

[https://wiki.ubuntu.com/KernelTeam/ARMKernelCrossCompile](https://wiki.ubuntu.com/KernelTeam/ARMKernelCrossCompile)

---

### Post by lisati on 2013-06-06
*Thread moved to **Programming Talk**.*

---

### Post by ofnuts on 2013-06-07
If you consider thiis to be a "bug" you are dealing with stuff that is currently out of your league. What happens here is that a C source file is "including" another file (plat/sram.h) but the compiler doesn't find it. Normally the build process gives the compiler a series of directories where it can look for included files. If you are missing prerequisites you may be missing on or more of these directories.

---

