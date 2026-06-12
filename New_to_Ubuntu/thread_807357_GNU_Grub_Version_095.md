---
title: "GNU Grub Version: 095"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by GerardoUy on 2008-05-25
Once I formated my hard disk with Ubuntu 5.04 a couple of years ago, I got prompted with the question if I wanted to install GNU Grub, cause I got two hard disk on my Pc one with Ubuntu( master one) and a second hard disk with windows xp home.
Then it was easy to choose with wich disk start my machine.
But now I need to format the Ubuntu hard disk to do a clean install of ubuntu 7.10, an d want to take out this program to be able to start a machine only with the Windows disk.
I guess there is something written on the root sector of my win xp disk in order to do this, so, question is , how I get rid of GNU Grub version: 095, without damaging the instalation of win xp?(my whole life is on that disk, lol!)in order to be able to start the machine with only hard disk windows as harware.

---

### Post by quelx on 2008-05-25
If windows is all that is installed, boot from the XP cd and choose the recovery console and execute **fixmbr** once you get to a command prompt

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
[http://support.microsoft.com/KB/314503](http://support.microsoft.com/KB/314503)

---

