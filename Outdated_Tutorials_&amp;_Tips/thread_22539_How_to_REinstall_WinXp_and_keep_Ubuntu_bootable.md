---
title: "How to REinstall WinXp and keep Ubuntu bootable"
date: 2005-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by th0mas on 2005-03-28
Hello everyone,

Few months ago i installed Ubuntu 4.1 with XP already running. So my grub asks me which OS i want each time I start my computer.

The thing is that i would like to reinstall XP (going more & more crappy those days). But i understood it will erase the "MBR".

How can i do to keep a Grub ? to keep my Ubuntu bootable ?

I hope i'm enough precise.

THX!

---

### Post by Buffalo Soldier on 2005-03-28
Out of curiosity, are you reinstalling Windows because you want a clean fresh install of Windows or someting related to GRUB default OS when booting?

---

### Post by puelly on 2005-03-28
[QUOTE=th0mas]Hello everyone,

Few months ago i installed Ubuntu 4.1 with XP already running. So my grub asks me which OS i want each time I start my computer.

The thing is that i would like to reinstall XP (going more & more crappy those days). But i understood it will erase the "MBR".

How can i do to keep a Grub ? to keep my Ubuntu bootable ?

I hope i'm enough precise.

THX![/QUOTE]
 you should make a bootdisk for ubuntu before installing windows. then install windows, use the bootdisk to boot into grub and run grub-install

Sorry I can't remember the exact command to create a boot disk but it should be on the forum somewhere.

---

### Post by th0mas on 2005-03-28
[QUOTE=Buffalo Soldier]Out of curiosity, are you reinstalling Windows because you want a clean fresh install of Windows or someting related to GRUB default OS when booting?[/QUOTE]

yup, i want a clean refresh of my windows. I still keep xp cause some softs and things don't run with linux...

my grub was ok, letting me chose Ubuntu or Windows when booting.
but i heard reinstalling XP will erase the MBR and my Grub...

---

### Post by garyng on 2005-03-28
[QUOTE=th0mas]yup, i want a clean refresh of my windows. I still keep xp cause some softs and things don't run with linux...

my grub was ok, letting me chose Ubuntu or Windows when booting.
but i heard reinstalling XP will erase the MBR and my Grub...[/QUOTE]

You are right BUT XP may preserve GRUB as the original DOS boot sector and you may have an option to "boot previous window"(which is in fact GRUB) in XP.

You can always do it yourself by :

dd if=/dev/hda of=/mnt/C/grub bs=512 count=1

to save the GRUB sector to a file that is readable by BOTH XP and linux(say a FAT32 as C:, just don't let XP change it to NTFS). Then add the line yourself to C:\BOOT.INI after XP has done its installation.

---

### Post by th0mas on 2005-03-28
[QUOTE=puelly]you should make a bootdisk for ubuntu before installing windows. then install windows, use the bootdisk to boot into grub and run grub-install

Sorry I can't remember the exact command to create a boot disk but it should be on the forum somewhere.[/QUOTE]

Don't you think i could do this more easily using an Ubuntu LiveCD (after having reinstalled Xp), so that i have access to my linux partitions and do some modifications ?

Anyway, i've just seen this url, hope it will help others...
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by Buffalo Soldier on 2005-03-28
A similar discussion going on at [Windows Install after Ubuntu?](http://ubuntuforums.org/showthread.php?t=22537) thread.

---

### Post by kuleali on 2005-04-12
i have the sam issue. Would be nice if i had a disk station.

---

