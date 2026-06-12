---
title: "Install over Knoppix but retain existing grub"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by calelettus on 2008-04-26
I have a dual-boot laptop witn WinXP and Knoppix with grub.

I want to blow away the Knoppix to install Ubuntu 8.04 but I want to know if it is possible to do the install but NOT reinstall Grub? In other words, I want to keep my existing Grub because it has some backup/restore features I don't want to lose.

Thanks.

---

### Post by logos34 on 2008-04-26
If you're using the ubuntu livecd, when you get to 'Ready to Install' screen, press 'Advanced' (lower right) and change grub location from default (hd0) to **/dev/sda2**, or whatever root partition is. That way it won't overwrite grub on the MBR.  But you'll still loose the backup features and whatnot, because that's all on the knoppix menu.lst.  So you could save a copy of menu.lst and add the parts you want to ubuntu's own menu.lst, in which case just keep the default (hd0).  

Workaround:

Or do what I do and transfer your /boot/grub files to a [dedicated grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

---

