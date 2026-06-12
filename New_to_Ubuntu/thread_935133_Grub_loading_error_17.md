---
title: "Grub loading error 17"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by jemmyyong on 2008-10-01
I just installed OpenSuse. When the computer restart "grub loading...error 17". Before this installation, I have Ubuntu & Windows running well..Please help me..thanks

---

### Post by uberdonkey5 on 2008-10-01
There are lots of posts on this subject. This may help:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Error 17 is a problem with missing system files or a broken system registry (I got this when I accidently deleted my grub loader). Unfortuantely I ended up doing a complete reinstall (after using the live disk to remove my data).

---

### Post by Forbees on 2008-10-01
you can reinstall grub with the live cd

do the same as a ubuntu install

just be sure to NOT creat new partitions

use the old Ubuntu and XP and i guess opensuse partition, and DONT clikc on format

that should reinstall the kernal with grub and not make you lose any data

---

### Post by caljohnsmith on 2008-10-01
Boot your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu and also your OpenSUSE partition in the form of (hdX,Y). Remember that Grub's numbering starts with zero, so:
```
sda1 = (hd0,0)
sda2 = (hd0,1)
sda3 = (hd0,3)
...etc.
```
So from the output of the find commands above, choose your Ubuntu partition, and proceed with:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you run into problems.

---

### Post by jemmyyong on 2008-10-02
Thanks all, I have reinstall Ubuntu from LiveCD and solve the problem. But now I am missing OpenSuse. How to find installed OpenSuse and add to GRUB?

---

