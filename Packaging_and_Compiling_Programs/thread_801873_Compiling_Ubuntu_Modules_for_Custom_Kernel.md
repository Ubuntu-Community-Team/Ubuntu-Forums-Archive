---
title: "Compiling Ubuntu Modules for Custom Kernel"
date: 2008-05-21
forum: Packaging and Compiling Programs
---

### Post by eteq on 2008-05-21
I needed to compile a custom kernel due to some buggy graphics hardware (an Asus F8Sv-B1 laptop apparently doesn't have its BIOS set up to correctly report memory addresses for 3GB of memory and hence needs some massaging to correctly locate the graphics card memory...).  With the stock kernel, everthing works fine except the graphics card, and I managed to get the graphics working perfectly with the custom kernel.  BUT, a few other things (sound, wireless, and possibly a few other hardware items) no longer work in the new kernel.  As far as I can tell, it's because the linux-ubuntu-modules package doesn't get installed in /lib/modules/<the new kernel> ... 

I followed the "old Debian way" directions at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) , but that doesn't explain how to get the modules compiled for the new kernel... and I'm at a loss as to what to do other than to compile each of the modules by hand one at a time (which I'm particularly loath to do, because the iwlwifi drivers claim they should already be built into the 2.6.24 kernel, even though they appear to only be in the linux-ubuntu-modules package).  Any pointers as to how I can convince the package to compile for my custom kernel?

---

