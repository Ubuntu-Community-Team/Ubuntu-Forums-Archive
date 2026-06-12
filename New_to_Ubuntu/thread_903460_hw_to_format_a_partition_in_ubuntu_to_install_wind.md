---
title: "hw to format a partition in ubuntu to install windows xp"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by drao on 2008-08-28
Hi, 

Could you anyone tell me how to format a partition in ubuntu, so that i can install winxp on that partition. Thanks in advance.

---

### Post by tuxxy on 2008-08-28
Boot the ubuntu CD and select the Live CD option, once its loaded run the application gparted to edit partitions.

---

### Post by drao on 2008-08-29
I dont know whether this group is relevant or not. I have installed ubuntu and xp on my pc.  Beacuse of virus, i have completely removed my xp and installed ubuntu in primary partition which was used by xp(c: drive) . Now am trying to re install xp on the partition (E: logical partition) which i was using for ubuntu. am facing problem to install xp in partition which i was used for linux. my question is, win xp need primary partition for installation??

---

### Post by drao on 2008-08-29
Sorry i forgot to tell you Thanks Mr tuxxy

---

### Post by plucky on 2008-08-29
> my question is, win xp need primary partition for installation?? 


Yes.

Also the installation will rewrite the MBR and you will not be able to boot into Ubuntu.But you can fix that using the Live Cd to reinstall grub.

See this thread for [how to install grub](http://ubuntuforums.org/showthread.php?t=224351)

Good Luck

---

### Post by drao on 2008-08-29
Thanks plucky. I came to knw that we can recover grub. I have done yesterday, its working fine. I want to know how can we convert a logical partition to primary in ubuntu using fdisk.

---

### Post by fastkid on 2008-08-29
> **drao said:**
> Hi, 

Could you anyone tell me how to format a partition in ubuntu, so that i can install winxp on that partition. Thanks in advance.

why dont you use the windows disc? :confused:

---

### Post by plucky on 2008-08-29
> **drao said:**
> Thanks plucky. I came to knw that we can recover grub. I have done yesterday, its working fine. I want to know how can we convert a logical partition to primary in ubuntu using fdisk.

Never used fdisk to manipulate partitions,I use the partition editor on the Live Cd or the [Gparted Live Cd](http://gparted.sourceforge.net/) which is very useful tool.Both are GUI and very easy to use.

Good Luck

---

