---
title: "[SOLVED] Primary Partition v Logical Drive"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by SBFree on 2008-08-03
Hi
I have installed Heron as a dual OS with WinXP to a Laptop. I see that it was installed in a logical drive with my Windows recovery info created by Acronis True Image. I have a couple of questions. First, the choice to boot my recovery software has disappeared. Can I install it as a choice to boot in GRUB which I believe is now the boot loader? Is it more difficult to back up my Linux install as a logical drive than active partition? I have been a fan of using drive & partition images for backups and restore. One of my first learning tasks to be learning how to back up and restore my Linux install. Any suggestions in this type of environment would be appreciated. Thanks.
Scott

---

### Post by CatKiller on 2008-08-03
It is possible to chain-load another boot loader with GRUB. People use that to load the Windows boot loader for dual booting Windows. It's possible that you can chain load the recovery software's boot loader, but someone more experienced than me would have to tell you how.

As long a GRUB knows where your Linux is installed, there's absolutely no difference between having it installed in a primary partition and having it installed in a logical drive. It shouldn't make any difference to backing up, either, as long as you bear the four primary partition limit in mind when thinking about your partitioning scheme.

If you like full partition images as a backup method, you can use **dd** to do a bit-by-bit copy from the partition you're using to your backup partition. It won't be quick, though. I believe that others use **rsync** for backups; that just copies the differences, as I understand it.

---

### Post by The Cog on 2008-08-03
You should be able to add a stanza to /boot/grub/menu.lst for your recovery software. Add a copy the stanza for the windows boot and then modify it by changing the title and the root partition. I guess the partiton needs chainloading much the same as windows needs chainloading.

I don't think being a logcal partition makes any difference to how you back the partition up. A couple of Linux tools for making images are **dd** which will produce a complete bit-for-bit image without regard to the disk filesystem layout or contents. **partimage** on the other hand intelligently only saves sectors that the filesystem has stored data on.

---

