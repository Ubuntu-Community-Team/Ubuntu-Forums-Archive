---
title: "Install xp on ubuntu machine /dual boot"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by pete_zahuat on 2008-07-20
I use Ubuntu 100% of the time, however I need xp for my work and was wondering how to go about dual booting. How much memory (hard drive space) is needed to run xp and where can I find information on the dual boot process?

---

### Post by glauco.b on 2008-07-20
XP runs in approximately 2,5 Gbytes, but this strongly depends on what you plan to install. Microsoft Office alone would eat up 1 GB more, for instance.

When you install windows, it will wipe out the MBR, that is, linux will not boot any more.

This is not a real problem, you can easily restore the GRUB MBR running an Ubuntu live CD. Just run grub, then root to the linux partition (you'll find in the /boot/grub/menu.lst file) and run "setup (hd0)"

Configuring grub to boot windows is very easy, just add an entry like this

```


title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

replace hd0,0 with the windows partition number

hd0,1 is first hard disk, second partition, and so forth

Anyway, whenever you mess up things in grub, you'll always be able to change anything from the grub command line at boottime

---

### Post by Sef on 2008-07-20
Read [Psychocat's Ubuntu]("http://www.psychocats.net/ubuntu/").

---

