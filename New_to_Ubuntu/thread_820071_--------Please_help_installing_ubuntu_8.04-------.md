---
title: "--------Please help installing ubuntu 8.04-------"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by luvuman on 2008-06-05
hey guys......
i'v just installed ubuntu 8.04 in ma PC. but it didn't work... after i installed it i got a error like this
> BusyBox v 1.1.3(Debian 1:1.1.3-5ubuntu12) Built-in shell(ash). Enter 'help' for a list of built-in commands.
(initramfs)
when i pressed Ctrl+Alt+F1 then it gives a error like this...
> Starting up...
Loading, please wait...
        check root=bootarg cat /proc/cmdline
        or missing modules, devices : cat /proc/modules ls/dev

ALERT! /dev/disk/by-uuid/2d58033b-7d9f-42849392-5f779e97943a does not exist. Dr opping to a shell
i even tried upgrading to ubuntu 8.o4 from the 7.10. but the result was same....
please help me... what should i do..here are ma PC configuration
[b]cpu- 2.5GHz
Ram- 1 GB
vga- 256MB nvidia Geforce 6200[/b]
:(:(:( plesae can anyone help me :(:(:(

---

### Post by ajmorris on 2008-06-06
hi there, boot into a recovery system, and log in. Then post here the contents of /etc/fstab and the output of sudo fdisk -l.
(if booting into the recovery option from grub doesnt work either, just boot off of a live cd, and mount the ubuntu partition, then do the above)

AJ

---

