---
title: "to reinstall grub boot loader"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by wstay on 2012-04-21
I am using ubuntu 10.04.
I need to reinstall the grub boot loader.
After booting from a live ubuntu 10.04 dvd, in a terminal I enter the command:
........
find /boot/grub/stage1
It returned an error message:
stage1 cannot be found.
I find that my installation of ubuntu 10.04 where I need to reinstall the boot loader does not have a stage1 file in /boot/grub. Are we having a different file in place of stage1?
If so what file is it call?
Can someone please help.

---

### Post by bodhi.zazen on 2012-04-21
You have several options.

One is a graphical tool called boot repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The other is to use the command line

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

