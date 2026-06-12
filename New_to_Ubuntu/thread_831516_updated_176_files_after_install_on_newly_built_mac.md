---
title: "updated 176 files after install on newly built machine=black screen"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by jinjuriki on 2008-06-16
hello I am totally new to ubuntu. It is a great program and I would be using it except for one problem. I updated 176 files in the file manager and rebooted. No boot up screen nada except the drum sound. I am running and an AMD athlon64duo with 2gig of ram and the big kicker is nvidia geforce 8600 gt. I have read other threads about a black screen and tried the ctrl alt f1 to no avail. could someone please help me?

---

### Post by NT4usB on 2008-06-17
Are you saying Ctrl+Alt+F1 did not take you to a terminal? 
Try ...F2, F3, etc. 
If you can get to a terminal, log in and type:```
sudo dpkg-reconfigure -phigh xserver-xorg
```and hit Enter until you get through any options that pop up.
then```
sudo /etc/init.d/gdm restart
```
iirc, there are ways to boot to a repair mode and/or boot to the original install disk but I've never done these so I don't know the steps.
I've always had good luck fixing xorg from a terminal.

---

