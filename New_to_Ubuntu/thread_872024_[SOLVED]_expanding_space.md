---
title: "[SOLVED] expanding space"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by im new here on 2008-07-27
how can i expand the ext3 drive space from by deleting another fat32 and adding its space after installation of xubuntu and not from applications menu (i mean by using a terminal) 
thanks

---

### Post by Diabolis on 2008-07-27
Have you used gparted before? It'll do whatever you want, its in the repositories.

---

### Post by kdb424 on 2008-07-27
Is this on a mac or a PC? I recommend using Gparted live CD to do it personally. (Gparted on macs may not work with the mouse.)

---

### Post by JKyleOKC on 2008-07-27
The easiest way would be to install a partition manager such as GPartEd. However with no space available in which to install anything you might have to do this in Windows rather than in xubuntu.

However you do it, the empty space created by deleting a FAT partition will have to be adjacent, physically, to the ext3 partition, and all of your partitions should be defragged and moved as necessary to make this happen. It's not a simple and straightforward process!

You might get up to speed faster by cleaning up the four additional FAT partitions, then uninstalling xubuntu and re-installing it from scratch, giving it the additional space at that time!

---

### Post by Diabolis on 2008-07-27
> **JKyleOKC said:**
> 
However you do it, the empty space created by deleting a FAT partition will have to be adjacent, physically, to the ext3 partition

Not true, with gparted you can move around partitions. Takes quite some time, but it can be done.

---

### Post by im new here on 2008-07-28
thanks everybody a fromated and resized and reinstalled xubuntu

---

