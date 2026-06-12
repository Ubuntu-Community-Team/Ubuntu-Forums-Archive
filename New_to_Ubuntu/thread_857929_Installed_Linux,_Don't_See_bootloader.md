---
title: "Installed Linux, Don't See bootloader"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-07-13
Hello

I am running a windows xp computer.  I want to dual boot it with both Windows xp and Ubuntu.  I installed Ubuntu and used the partition tool to make a separate partition for Ubuntu.  When I restarted my computer, I don't see the bootloader that is supposed to show up, although I can see the partition from Windows Disk Manager.

Please Help
Matt

---

### Post by Sef on 2008-07-13
From the Live CD, type or copy/paste this command in the Terminal (Applications > Accessories > Terminal):

```
sudo fdisk -l
``` Small L

---

### Post by hellodoggie on 2008-07-13
What does that do?  Something about formatting the drive?

---

### Post by Canis familiaris on 2008-07-13
> **hellodoggie said:**
> What does that do?  Something about formatting the drive?

It lists all your partitions.

---

### Post by WRDN on 2008-07-13
Check a file called "menu.lst" exists in /boot/grub
If it does, post the entire contents of the file here please.

---

### Post by fidamehran on 2008-07-13
Yuo can also have an app enabled (Startup manager) which you can install from Synaptic Package Manager. You don't absolutely need this for looking at the boot options, but you can change the boot options and settings very easily from here.

---

### Post by zipperback on 2008-07-13
Hi Matt,

If you want to create a dual boot system check out these links.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

The following link has several different tutorials which deal with dual booting.
Linux, XP, Vista, etc.....
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

Hope this helps you.

- zipperback
:popcorn:

---

