---
title: "How to add Win7 to a Win XP-Ubuntu 12.04 dual boot system?"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by Milind on 2012-07-11
Hi,
     I have a noob query. I have a Win XP -Ubuntu 12.04 dual boot system. What steps and in what order do I follow to add Win 7 to it, making a triple boot one? Will I need to make manual changes to GRUB later, and if so, how? I searched but couldn't find a guide. 

Any help appreciated.

---

### Post by miegiel on 2012-07-11
> **Milind said:**
> Hi,
     I have a noob query. I have a Win XP -Ubuntu 12.04 dual boot system. What steps and in what order do I follow to add Win 7 to it, making a triple boot one? Will I need to make manual changes to GRUB later, and if so, how? I searched but couldn't find a guide. 

Any help appreciated.

It depends a bit on your plans regarding partitions (or maybe a extra/separate disk). But all 3 OSes will need to be installed on their own partitions and the win7 installer will likely replace/remove any bootloader it finds on any of your disks. It will probably add the XP installation to the win7 bootloader, but not your ubuntu installation.

---

### Post by oldfred on 2012-07-11
Some additional info on miegiel post.

Windows only boots from a primary NTFS partition. If you do a second install to a logical partition it will still boot from the first install in the primary  partition, so best to install the second copy into a primary partition also.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Milind on 2012-07-12
Miegiel, Oldfred, thank you very much for your help.

---

