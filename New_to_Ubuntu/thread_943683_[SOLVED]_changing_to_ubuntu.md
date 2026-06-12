---
title: "[SOLVED] changing to ubuntu"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by mickey390 on 2008-10-10
As a total novice I managed to destroy windows on my laptop and installed xubuntu. I now want to install ubuntu.I have downloaded the program several times and copied to disk and checked with md5sum and all seems ok. I have changed the bios settings to boot from cd rom but it still will not boot. I have burned cd at slow speeds as this was a problem when installing xubuntu. any help would be appreciated

---

### Post by jamesrl on 2008-10-10
If you have xubuntu installed, you could simply install (gnome)-ubuntu from there. 

```
sudo apt-get install ubuntu-desktop
```

and then after you reboot (and choose gdm as your session)

```
sudo apt-get remove xubuntu-desktop xubuntu-artwork-usplash
sudo apt-get autoremove
```
You may also want to upgrade ubuntu to the latest version (8.04) while you are at it, which can be done: 
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")
There lots of potential reasons why you aren't getting your computer isn't booting from cd.  You can try the ubuntu alternate cd or another method of installation:
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by mickey390 on 2008-10-10
Thank you that worked and it seemed so easy. Now I can start to learn all about ubuntu and hopfully understand it all. :)

---

### Post by namegame on 2008-10-10
Just so you know, Ubuntu and Xubuntu, and even Kubuntu are essentially identical. The main difference is the Desktop Environment they each use, Gnome, Xfce, and KDE, respectively. So the "guts" of each are the same, but they are wearing different "clothes." :P

---

