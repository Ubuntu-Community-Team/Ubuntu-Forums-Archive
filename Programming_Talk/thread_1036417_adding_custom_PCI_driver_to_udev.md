---
title: "adding custom PCI driver to udev?"
date: 2009-01-10
forum: Programming Talk
---

### Post by hardyn on 2009-01-10
I have a driver that was provided by the manuf. of a PCI I/O board;  the driver was written for earlier linux kernels.

I have ported the driver to compile successfully under 2.6.24... but its install scrip is pre-udev.  I need some help on either either a script to manually create the /dev entries; or preferred, to add the custom driver to udev.

the driver compiles and installs correctly, but /dev nodes are excluded as the installer seems to be based on a static /dev directory.  does the driver code have to be modified to create the nodes when the module loads; or can linking the nodes to the kernel module be done externally of driver code? 

thanks for any help

---

