---
title: "Xp and Ubuntu"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-08-19
I've just got Ubuntu installed on my system but kind of want XP as well.

Is there a way to have both on my comp?

Do I have install xp and then do ubuntu again?

cheers

---

### Post by Ryadt on 2008-08-19
I would recommend installing xp and then install ubuntu. It avoid any messing up with Grup.

---

### Post by ace007 on 2008-08-19
The easiest way is to first install Windows, then Ubuntu.  Windows doesn't play nice with others, so you have to slip ubuntu in the back door.  

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Read all the sections in the "just beginning" section for additional info

---

### Post by sandysandy on 2008-08-19
though installing XP first is preferred, u can install XP after ubuntu also.

however ur MBR will get overwritten by XP and u will have to restore it by Super Grub Disk or by following the instructions in the thread below

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

see dual boot site (Ubuntu installed first)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

regards

---

### Post by alienexplorers on 2008-08-19
This page has a lot of information about dual booting:
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by 3rdalbum on 2008-08-19
An easier option would be to install XP within a virtual machine, like Virtualbox. That way Ubuntu is your main system, and XP runs within Ubuntu. If you decide that you don't need XP, you can remove it like any other file.

---

### Post by highlyevolved on 2008-08-19
Im having a bit of trouble trying to install XP.

When I click the setup.exe file it opens (with wine) but it pretty much freezes when I click install.

What to do?

---

### Post by Orlsend on 2008-08-19
Try it in the Terminal,Wine its pretty nooby about being helpfull. So instead of Double clink the EXE run it in the terminal

---

### Post by Paqman on 2008-08-19
> **highlyevolved said:**
> Im having a bit of trouble trying to install XP.

When I click the setup.exe file it opens (with wine) but it pretty much freezes when I click install.

What to do?

What are yu actually trying to do? Install XP in a Virtual Machine (eg:VMWare or Virtualbox) on Ubuntu or set up a dual boot with XP on it's own partition?

---

### Post by sandysandy on 2008-08-20
[QUOTE=highlyevolved]Im having a bit of trouble trying to install XP.

When I click the setup.exe file it opens (with wine) but it pretty much freezes when I click install.

What to do?[/QUOTE]

u will need to dual boot XP and ubuntu.

that means u will need a separate partition for installing XP.

pop the XP cd in the CD drive and reboot. u will get setup menu of XP. install XP to its own partition. ( if u do not have separate XP partition, use an utility like gparted to shrink ur ubuntu and create a separate partition for XP)

to repeat my earlier post

>  though installing XP first is preferred, u can install XP after ubuntu also.

however ur MBR will get overwritten by XP and u will have to restore it by Super Grub Disk or by following the instructions in the thread below

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

see dual boot site (Ubuntu installed first)

[http://apcmag.com/how_to_dual_boot_l...lled_first.htm](http://apcmag.com/how_to_dual_boot_l...lled_first.htm)



regards

---

