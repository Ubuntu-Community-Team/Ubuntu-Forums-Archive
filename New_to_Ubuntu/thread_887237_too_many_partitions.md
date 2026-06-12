---
title: "too many partitions"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by dbr1968 on 2008-08-11
I think I really screwed up my partions. I installed ubuntu once and thought it was messed up so I installed it again. Now when my system boots up I can choose from two that are the same except for "(on /dev/sda1)" after one of the sets. 
I would like to clean it up, can I get rid of the duplicate OS?

---

### Post by sandysandy on 2008-08-11
post output of [COLOR="Red"][SIZE="3"]sudo fdisk -lu[/SIZE][/COLOR]



regards

---

### Post by dbr1968 on 2008-08-11
Device    Boot     Start         End       Blocks   ID    System
/dev/sda1  *          63   150448724     75224331   83     Linux
/dev/sda2      150448725   156360644      2955960    5     Extended
/dev/sda5      155059443   156360644       650601   82  linux swap/Solaris
/dev/sda6      150448851   154722014      2136582   83     Linux
/dev/sda7      154722078   155059379       168651   82  linux swap/Solaris

Partition table entries are not in disk order

---

### Post by sandysandy on 2008-08-11
depending on which install (first /second) u want to delete u can modify the menu.lst file so that the second OS does not come in the boot options.

before deleting the second OS be very sure that the other one is OK. try booting from both to check that.

regards

---

### Post by dbr1968 on 2008-08-11
> **sandysandy said:**
> depending on which install (first /second) u want to delete u can modify the menu.lst file so that the second OS does not come in the boot options.

before deleting the second OS be very sure that the other one is OK. try booting from both to check that.

regards

Could you tell me how to do that?

---

### Post by ntu on 2008-08-11
And after checking the 1st OS, you can delete the 2nd OS partition with Gparted.

Just highlight the partition and press delete and then apply.

---

### Post by dbr1968 on 2008-08-11
> **ntu said:**
> And after checking the 1st OS, you can delete the 2nd OS partition with Gparted.

Just highlight the partition and press delete and then apply.

I have no idea how to do that either.

---

### Post by sandysandy on 2008-08-11
just to repeat, it is important to check that the OS u plan to retain is booting properly before u delete the other OS.

after u boot from OS u want to retain, take [COLOR="Red"][SIZE="4"]backup [/SIZE][/COLOR]of menu.lst file as it is an important file.

to open this file for editing the code is

gksudo gedit /boot/grub/menu.lst

u will get the various boot options listed. put # in front of the other OS u do not want to show during booting.

do not be in a hurry to delete the other OS.:)

regards

---

### Post by ntu on 2008-08-12
> **dbr1968 said:**
> I have no idea how to do that either.

Gparted, Gnome partion editor, is in System>Administration> 

"System" is at the top towards the lhs of your screen.

---

### Post by mc4100 on 2008-08-12
> **ntu said:**
> Gparted, Gnome partion editor, is in System>Administration> 

"System" is at the top towards the lhs of your screen.
Unless they're running from a LiveCD (which is probably a good idea), GParted won't be installed.
```
sudo apt-get install gparted
```

---

### Post by dbr1968 on 2008-08-12
> **sandysandy said:**
> just to repeat, it is important to check that the OS u plan to retain is booting properly before u delete the other OS.

after u boot from OS u want to retain, take [COLOR="Red"][SIZE="4"]backup [/SIZE][/COLOR]of menu.lst file as it is an important file.

to open this file for editing the code is

gksudo gedit /boot/grub/menu.lst

u will get the various boot options listed. put # in front of the other OS u do not want to show during booting.

do not be in a hurry to delete the other OS.:)

regards

I put in the command above and got this:
(gksudo:5621): Gtk-WARNING **: cannot open display:

---

### Post by sandysandy on 2008-08-12
try

sudo gedit /boot/grub/menu.lst

on the Gtk-WARNING ** see these threads

[http://ubuntuforums.org/showthread.php?t=166863&page=2](http://ubuntuforums.org/showthread.php?t=166863&page=2)

[http://www.linuxforums.org/forum/mandriva-linux-help/110148-gtk-warning-cannot-open-display.html](http://www.linuxforums.org/forum/mandriva-linux-help/110148-gtk-warning-cannot-open-display.html)

regards

---

