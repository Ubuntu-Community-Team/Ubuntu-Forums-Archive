---
title: "live cd on usb"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by madeki0663 on 2013-11-29
yesterday i installed ubuntu-12.04.3-desktop-amd64 on usb stick with Universal-USB-Installer-1.9.5.1. (with persistence file)

Everything went fine and I did some changes!
Today I wanted to start up and got following error ;

sh:1  cannot create /var/run/motd.new : input/output error

what to do now ?

---

### Post by sudodus on 2013-11-29
- Could you boot to a working system with a graphical user interface before you did some changes?

- What changes? Some changes can be undone, some not (or it is easier to start with a fresh install again).

Edit: Or maybe you unplugged the stick before everything was written from the RAM to the stick. It is important to let it shut down and wait until it has finished.

---

### Post by C.S.Cameron on 2013-11-29
Many people have had problems with Universal.
Try UNetbootin, or better yet, Startup Disk Creator, (from the Live CD).

---

### Post by madeki0663 on 2013-11-30
Yes I think I removed the stick too fast ! It already works ok now ! 

thnx .

---

