---
title: "When in boot selection menu, why 2 possible windows?"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by ruben6 on 2014-02-16
Hey everybody, after installing ubuntu and having to use boot repair tool for it to apear on the boot menu, I found that there are 2 possible windows 7 options. dev/sda1 and dev/sda2 (if I remember correctly). 

Why is that? Any difference between any of them?

Thanks!

---

### Post by 3rdalbum on 2014-02-16
sda1 and sda2 are two different partitions. Unless you have Windows installed twice, I would assume that sda1 contains Windows and the sda2 contains your "recovery" or "restore to factory defaults" partition.

---

### Post by oldfred on 2014-02-16
If you have run Boot-Repair, it often copies boot files from sda1 to sda2 as a backup. But then grub sees both as bootable and adds entries for both. You can boot from either.

Windows normal install has a separate 100MB boot partition that you do not see in Windows. So many users just delete that not knowing it is vital, that Boot-Repair just decided to copy files.

The main reason for a separate boot partition was so you could encrypt main install as boot files cannot be encrypted with Windows. The boot partition also has Windows repair tools (f8) that may work to fix Windows, but still better to make a Windows repair CD or flash drive just in case.

---

