---
title: "[grub] DEFAULT=saved causing mishap"
date: 2020-10-20
forum: New to Ubuntu
---

### Post by stacksux on 2020-10-20
Just installed Ubuntu 20.04 but changed the sata cable and it's not working anymore,

tried reinstalling but the problem persists for all changes in disks i add and grub can't recognize as filesystems. :guitar::guitar:

Should i try to disable DEFAULT=saved[FONT=Arial]or [/FONT]GRUB_SAVEDEFAULT=true before trying to boot kernel from root=(hd0,msdos2)?

---

### Post by CelticWarrior on 2020-10-20
Perhaps you need to change the boot order to the drive where it was installed originally?
The order in BIOS or UEFI was changed when you changed the cable... Not that just replacing a cable would do that but in reality you connected it in another port, didn't you?

---

### Post by stacksux on 2020-10-21
Already solved. i've used the next grub command
set root=(ahci0,msdos2)
and then
insmod normal.mod
then reinstalled grub to the prior version.
also couldn't find the new grub terminal so did
insmod help 
and
insmod fshelp. 
i still can't see all modules on screen i think i need read more grub2 docs

---

