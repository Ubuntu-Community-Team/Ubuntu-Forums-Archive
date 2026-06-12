---
title: "Can't modprobe lirc in 2.6.29-2 PPA kernel"
date: 2009-04-30
forum: Packaging and Compiling Programs
---

### Post by Lucid Smog on 2009-04-30
I am running the 2.6.29-2 PPA kernel because I need some driver support that was added in 2.6.29.

Problem is that I also use LIRC, specifically the lirc_mceusb2 module.

LIRC doesn't work out of the box, as I discovered, when I installed the PPA kernel.  I downloaded the LIRC development package and attempted to build it for the new kernel with dkms.  This failed miserably, and the log file had absolutely nothing in it.  Pasting in the piece of shell code it was running allowed me to see what was wrong though.

Turns out the kernel info() and warn() calls were changed to pr_info() and pr_warning(), so I changed the calls in the LIRC source appropriately.  Now it built without issue using dkms.  I installed the modules with dkms

I can modprobe lirc_dev, but when I modprobe lirc_mceusb2 I get errors about no symbol versions.  It happens for all of the EXPORT_SYMBOL declarations in the LIRC source code.  A dmesg error about "no symbol version for ..." followed by "Unknown symbol ...".

I then went in to the source files which had EXPORT_SYMBOL macros and included config/modversions.h in the hopess of magically adding the versions that the kernel appears to want.  This hasn't worked either.  I have also tried using the current CVS head of LIRC with similar results.

I notice that even after running dkms install that my System.map file is not updated with the symbol definitions for LIRC.

In any case I'm out of my league now and if there isn't some simple thing to do to solve this I'm just going to compile a kernel myself and turn off CONFIG_MODVERSIONS.  Any ideas?

---

