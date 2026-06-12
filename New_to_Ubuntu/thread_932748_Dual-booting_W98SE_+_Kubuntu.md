---
title: "Dual-booting W98SE + Kubuntu"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by metacognition on 2008-09-28
So I was cleaning up my closet and I found my old 98SE install disc, since my computer is somewhat old, I want to install it alongside my Kubuntu 8.04 install. I've seen things mess up with the MBR and GRUB, but those seemed to only apply to Windows XP or Vista. Any precautions I should be aware of?

Here's the steps I'm going to take:
1. Clean-up HDD
2. Partition via Gparted
3. Install 98SE on empty partition

Any ideas/help?

---

### Post by JKyleOKC on 2008-09-28
Note that Windows will rewrite the MBR of your hard disk, thus wiping out your GRUB loader. You'll need to re-install GRUB to get back the ability to boot to Kubuntu. There are a number of threads here on doing that. Most of them refer to XP or Vista, but the procedure will be the same for Win98SE -- which I'm dual-booting on four machines at present.

---

### Post by zvacet on 2008-09-28
[Here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by kansasnoob on 2008-09-28
This may be of help:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by Excalibre on 2008-09-29
One other note is that Windows reportedly doesn't like it if you don't install it on a primary partition. Your partitioning program should tell you whether the new partition you're creating is a primary or a logical one, and if you have four or less they should all be primary partitions. But if you have more than that you're probably using an extended partition somewhere (it's basically a container that holds logical partitions, so that you can have more than 4 partitions on a disk), and you have to make sure the partition you install Windows on is a primary partition.

---

