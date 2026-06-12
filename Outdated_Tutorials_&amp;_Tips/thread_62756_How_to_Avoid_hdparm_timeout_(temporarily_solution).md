---
title: "How to: Avoid hdparm timeout (temporarily solution)"
date: 2005-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by vnbuddy2002 on 2005-09-05
If you enable DMA mode with hdparm, many times you will experience "timeout waiting for DMA" and it will automatically switch back to PIO mode (turtle mode). There was a patch for this problem but it is only for 2.4.x kernels. One of the simple way is to disable "APIC" from the kernel.  If it works on my system, it might works on yours. Here is how you do it:

1. open up /boot/grub/menu.lst
2. look for your kernel and add "apic=no"

It should look like

kernel  ............   apic = no

Let me know the results. :)

---

### Post by tseliot on 2005-09-06
[QUOTE=vnbuddy2002]If you enable DMA mode with hdparm, many times you will experience "timeout waiting for DMA" and it will automatically switch back to PIO mode (turtle mode). There was a patch for this problem but it is only for 2.4.x kernels. One of the simple way is to disable "APIC" from the kernel.  If it works on my system, it might works on yours. Here is how you do it:

1. open up /boot/grub/menu.lst
2. look for your kernel and add "apic=no"

It should look like

kernel  ............   apic = no

Let me know the results. :)[/QUOTE]
Or you might put "noapic" as well.

---

