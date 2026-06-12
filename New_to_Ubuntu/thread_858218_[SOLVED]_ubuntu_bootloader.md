---
title: "[SOLVED] ubuntu bootloader"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by azery on 2008-07-13
another newbie question.

The bootloader of ubuntu is filling up rapidly with different kernel versions.

I found a solution at [http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

From the comments attached to that article, I understand that the nicest way is to edit the /boot/grub/menu.lst file and change the line saying: 
# howmany=all

two questions:

- do I have to remove the # (is it for commenting the line?)?
- I have a dual boot with windows. I thought of setting the value to 2, the latest kernel and one fallback option in case of problems. Will I still see my windows os?

---

### Post by WRDN on 2008-07-13
You should not remove the #, and set it to "howmany=1". It only refers to the Linux kernels, not the Windows entry, which will still appear.

---

### Post by Moop on 2008-07-13
Startupmanager is a app you can install that offers a gui for doing what you want to do. It's available for hardy.  [http://packages.ubuntu.com/hardy/startupmanager](http://packages.ubuntu.com/hardy/startupmanager)

---

### Post by drs305 on 2008-07-13
I highly recommend StartUp-Manager. It can control how many kernels you see, how long the menu is displayed, what the default OS or kernel should be, and lots more.

To install SUM:
```
sudo aptitude install startupmanager
```
To run:
System, Administration, StartUp-Manager

I've provided more details about using it here:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Sunfist on 2008-07-13
Second that on the manager, I managed to mess up grub on a regular basis before I started using that, it makes the whole thing painless.

---

### Post by azery on 2008-07-16
used the manager, works perfectly

thanks for the tip

azery

---

### Post by Canis familiaris on 2008-07-16
If your problem is solved kindly mark it as solved (only a request)

---

