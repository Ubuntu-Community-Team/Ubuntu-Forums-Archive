---
title: "[SOLVED] grub"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by swaknight on 2008-06-28
i had fedora on my old 98 toshiba tecra 8100 and tried to put puppy linux on it because fedora was too slow. apparently something interrupted the format proces ss and messed up my disk, it finished but when i start it, it just says
```
Grub....
```

i tried completely reformatting the drive with the live CD and Installing Deli Linux this time, but still get the same error. any ideas?

ps, im sorry for this not being Ubuntu related

---

### Post by bodhi.zazen on 2008-06-28
Well, grub is installed into the MBR so you need to install Puppy and then re-install GRUB.

By the way , puppy is difficult to install and is designed to run live, with a persistent home to save your changes ...

---

### Post by sandysandy on 2008-06-28
have a look at gparted in case u want to format ur hard disk

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

regards

---

### Post by swaknight on 2008-06-28
I use gparted to format the entire drive from the live CD then tried to install Deli Linux. it still gives me the same thing

---

### Post by caljohnsmith on 2008-06-29
> **swaknight said:**
> i had fedora on my old 98 toshiba tecra 8100 and tried to put puppy linux on it because fedora was too slow. apparently something interrupted the format proces ss and messed up my disk, it finished but when i start it, it just says
```
Grub....
```

i tried completely reformatting the drive with the live CD and Installing Deli Linux this time, but still get the same error. any ideas?

ps, im sorry for this not being Ubuntu related
Try booting from a live CD, mount your Puppy linux partition to say /mnt/hda1 (if you need help with that let me know), and then do the following command to reinstall Grub to the MBR:
```

sudo grub-install --root-directory=/mnt/hda1 /dev/hda --recheck
```

That command will make the Puppy linux distro control the grub boot process. (You should replace hda with sda if that is how your HD shows up in /dev).

---

### Post by swaknight on 2008-06-29
i fixed it :D

apparently one thing that microsoft does right is their partitioning software during XP installation, go figure. I just popped the cd in, went to the format process, formatted it. then i remembered Xubuntu works on older laptops, installed it, and now it works like a charm.

---

