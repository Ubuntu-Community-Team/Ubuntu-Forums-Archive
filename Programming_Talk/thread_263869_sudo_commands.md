---
title: "sudo commands"
date: 2006-09-23
forum: Programming Talk
---

### Post by antoz on 2006-09-23
I have been trying to get into the grub menu but it does not accept the commands in root terminal.
It is the older Ubuntu version 4.10 the command line I am using is
**sudo gedit/boot/grub/menu.lst** what am I doing wrong?

---

### Post by divague on 2006-09-23
between gedit and /boot/... should be an space, like this

sudo gedit /boot/grub/menu.lst

---

### Post by Ptero-4 on 2006-09-23
also, use gksudo, sud is meant for command line apps while xsu/gksudo/kdesu are meant for X11 apps.

---

### Post by antoz on 2006-09-23
Thanks having a space there made all the difference.
Have a great day, Antoz :D

---

