---
title: "garbled video on startup install"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by infoanalysis on 2008-05-01
amd 64 dual core 3800
ge force 6200 
existing xp professional

Performed an install off of 7.10 for pC. The system put out a garbled video. I ran it in graphic mode and also changed the vga settings. to no avail. It will boot up with the orange logo okay  butthen it gives the musicall sound and displays a repeated image of grpahic all garbled.

Upon boot up I am given the choice of xp or ubuntu  linyx. When ubuntu is selected it boots up to busybox 1.1.3 and also has the prompt (initramfs)any advice on how to proceed.

thanx in advance

John

---

### Post by iSplicer on 2008-05-01
Try booting into recovery mode and typing:

sudo dpkg-reconfigure xserver-xorg

---

### Post by infoanalysis on 2008-05-01
How do I go into recovery mode?

---

### Post by bsharp on 2008-05-01
It should be the 2nd option on the boot menu, something like this:

Ubuntu 7.10 2.6.22-generic
Ubuntu 7.10 2.6.22-generic (recovery mode)

---

### Post by infoanalysis on 2008-05-01
There is no option it just says ubuntu lynex or windows xp

---

