---
title: "Unable to dual boot Ubuntu with Windows 8"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by samunitions on 2013-05-30
Hello,
I'm a Linux beginner, haven't used it since I graduated in 99.


Today I downloaded the latest ubuntu version and attempted to install it.
I created a bootable usb
Freed up 100GB of space on the hd, and left them unallocated

Rebooted , and chose the Install Inside Windows 8 option ....

I get a Signal 15 error and the machine reboots.

From reading many related threads it seems to be due to partition configuration.
I've attached a snapshot of my partition configuration.

Would appreciate advice on how to proceed from here, given that I cannot  delete this Win 8 installation, and require all the files in C: and F:  to remain intact.

Thanks
-Sam Amin

---

### Post by presence1960 on 2013-05-30
I may be wrong, but I believe Wubi (install inside windows) is not compatible with UEFI windows 8 machines.

[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

---

### Post by Mark Phelps on 2013-05-31
Freeing up space and then installing using Wubi are contradictions.  Wubi installs INSIDE a Windows partition.

You should boot from a CD or USB and install to the unallocated space you made using "something else".

---

### Post by fantab on 2013-05-31
Ubuntu/LINUX will not install on 'Dynamic Partitions'. You have to reverse them back to 'Basic'.
'Dynamic' Partitions are Microsoft proprietory. Linux won't recognize it and hence cannot work with it.

Partition Table, "msdos" has FOUR Primary Partitions limit. When a fifth is forced partitions are converted to Dynamic. To workaround this limitation we use EXTENDED partition, which contains LOGICAL Partitions.

---

