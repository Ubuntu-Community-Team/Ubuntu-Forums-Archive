---
title: "Compiling blcr, trouble with kernel build path"
date: 2012-08-24
forum: Packaging and Compiling Programs
---

### Post by threepoint14 on 2012-08-24
This must be an easy one.  I need to compile the static library (libcr.a) for blcr, however the configure script keeps giving me a hard time about the location of the kernel build files.  For example: 

> [FONT=Courier New]checking for Linux kernel build in /usr/src/linux-3.2.0-29-generic-obj... not found
checking for Linux kernel build in /usr/src/linux-3.2.0-29-generic... include/linux/version.h missing
checking for Linux kernel build in /usr/src/kernels/3.2.0-29-generic... not found
configure: error: Could not find a directory containing a Linux kernel 3.2.0-29-generic build.  Perhaps try --with-linux=FULL_PATH_TO_KERNEL_BUILD[/FONT]
What do I need to install to allow this to compile?  I've tried referring it to the headers folders, and to the unzipped linux-source-3.2.0 folder, but it is still unsatisfied.  Am I misunderstanding its needs?

---

### Post by Bachstelze on 2012-08-24
include/linux/version.h no longer exists in the kernel. Find out which kernel versions are compatible with what you want to build.

---

### Post by MadCow108 on 2012-08-25
blcr does not work with kernels newer than 2.6.38, its not just a compilation problem, it simply won't work.
Latest upstream news entry:

> October 11, 2011
 Version 0.8.4 is now available from the Checkpoint Downloads page.
 This version fixes some minor bugs, and extends support to kernels through 2.6.38.
[https://ftg.lbl.gov/projects/CheckpointRestart/](https://ftg.lbl.gov/projects/CheckpointRestart/)

---

### Post by threepoint14 on 2012-08-31
Thanks, I just gave up on this effort. I wanted it for use with mpich2 running a fortran code, but it turned out that openmpi was faster on my system, and did not require libcr. Easy fix!

---

