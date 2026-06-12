---
title: "Which packages needed to build a kernel module?"
date: 2009-05-27
forum: Programming Talk
---

### Post by Robert Dodier on 2009-05-27
Hello,

I need to compile a kernel module (specifically the driver for the LabJack U3 DAQ). Which packages do I need to compile a module? I am working on a Dell Mini 9 which has iirc Hardy Heron. I have installed kernel-package and build-essentials via synaptic.

The Makefile for the LabJack driver expects there to be /lib/modules/<kernel-version>/build which doesn't exist. I have a RedHat system in which build is a symbolic link to /usr/src/kernels/<version> which seems to contain some stuff related to modules, and the LabJack Makefile builds the driver successfully on that system.

Dunno where to go from here. Any light you can shed on this problem is much appreciated.

Robert Dodier

---

### Post by Robert Dodier on 2009-05-27
A quick update, after some more searching I found that a linux-headers-<version> package is needed. So I installed that, now I can build the module successfully. Dunno yet if it works but anyway I was able to build it.

---

### Post by lensman3 on 2009-05-28
The config file for the current running kernel is usually found in the /boot directory.  Copy this config file to the top of the kernel tree source and name it .config.  In the kernel directory is a read me, and somewhere in it is the "make" command so that you can enable the new module.  Once the module is enabled, then run yjr "make" to build the new kernel including the loadable modules.  The "read me" has the instructions including how and where install the system.   Be sure to use the /boot/config??????.  That way the kernel that is compiled is a "tested" (and old) kernel instead of a bleeding edge kernel.

Hope this helps.  It has been about 2 years since I built a kernel and then all I wanted was to add a truecrypt module.

---

