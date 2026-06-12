---
title: "custom kernel build, some questions"
date: 2009-02-05
forum: Packaging and Compiling Programs
---

### Post by eilenbeb on 2009-02-05
I'm new at this, so I really don't even know what questions to ask.

I've built a kernel using the kernel source from the standard hardy repositories.  I'm running on an AMD64 and trying to target the same architecture.  The exact version doesn't seem to matter, as I've had the same problems with every source version I've tried.

I am -not- trying to replace my currently running kernel.
I've another drive with a large ext2 and matching swap partition, this is where I want to install the new kernel.
The ext2 partition is blank except for the basic file structure (boot, bin, and so on).
***edit I also built makedev and populated /dev ***edit
I've a bootloader hardwired to load the vmlinuz symlink/hardlink located under / in the target partition.
When I place the kernel image and map in (targetdrive) /boot, bootup works (very quickly, I might add).


The problems I'm having are these:

1)  As I've said, I'm targetting a 64bit processor.  Here's a relevant piece of my .config file:
> 
CONFIG_64BIT=y
# CONFIG_X86_32 is not set
CONFIG_X86_64=y
CONFIG_X86=y

I compile from top of my kernel source tree using:
> 
make O=/home/eilenbeb/sources/linux-source-2.6.99/build_output

Under build_output/arch I get the x86 and x86_64 subdirs.  The x86_64 directory is empty execpt for a symlink, whereas the x86 gets populated.
Make is telling me:
> 
Kernel: arch/x86/boot/bzImage is ready  (#1)

My question is, how do I know for sure I'm building a 64-bit binary?  I want to be absolutely sure I'm not doing something wrong and getting 32-bit output.


2) Installing the modules on the target drive.  Is it sufficient to simply copy the modules subfolder to the target filesystem?  I know I'll need modprobe (automatic kernel module loading is enabled), but for the moment the only module I have is scsi_wait_scan.
As all my scsi support is built in, so this -should- be irrelevant, but I can't seem to get rid of it or make it built-in.

3) Another worrying piece of make's output:
> 
Root device is (8, 33)

Repeat, there is nothing in the new filesystem except the kernel, map, modules and the root symlink->kernel.
***edit Sorry, I also populated /dev using makedev ***edit
When I boot, I'm getting a busybox.  shouldn't I be getting a panic?
Is the kernel somehow tied to the filesystem it was compiled under?

4) Make install seems to be using my distrib install script (/sbin/installkernel) which tries to install to my currently running system.
I don't have enough know-how to write my own, atm.
Is there another script somewhere for non-local installations?  'make help'  wasn't much help.

Sorry for the long post, hopefully they're simple to answer.

---

### Post by eilenbeb on 2009-02-19
#1 Solved.

#2-4 I'm still unsure of.  Any Advice?

---

