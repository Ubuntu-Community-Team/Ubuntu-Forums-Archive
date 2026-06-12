---
title: "Can't install Nvidia Driver after Kernel update"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by iowabeakster on 2011-09-29
Running 10.04 Xubuntu...

I've been through this many times.  After a Ubuntu update that has a new kernel (like I did a few minutes ago), I need to install my proprietary Nvidia Driver.  I've done it so many times I can't count.

--shut down the x server
--cd to my directory with the Driver
--and sh Nvidia_whatever_whatever
--bingo, I'm back to normal

Today, the driver starts to install but I get:

ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.

This is unfamiliar territory for me... Any Help?

Oh, and I don't dual-boot anymore.  So I don't get a grub menu that allows me to use an older kernel (or at least I don't know how).

---

### Post by iowabeakster on 2011-09-29
I think I have it.  I went into Synaptic and found a kernel lib dev file, and saw that I did not have the appropriate header file installed.  Maybe a mistake in the update package... not sure.

I manually Installed the matching header file... and now the Nvidia driver installed fine.

I'm not really sure what I'm doing.  But at least I'm not in low graphics mode anymore.

---

### Post by iowabeakster on 2011-09-29
And I just discovered that the update also broke my vitualbox that I need for a class I'm taking...#-o

So, I've been trying to sort out that mess.

---

