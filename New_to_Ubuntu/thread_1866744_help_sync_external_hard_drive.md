---
title: "help sync external hard drive"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by SpaceOdin on 2011-10-21
hey, 

been searching for an answer to this, no luck yet. I'm trying to get my system to let me access my external hard drive. everything on it was backed up through vista, mainly just general media id rather not lose. i tried auto mounting it, and then manual mounting. did a dmesg | tail which gave me :

pikez@ubuntu:~$ dmesg | tail
[   55.428603] usbhid: USB HID core driver
[ 1057.437384] composite sync not supported
[ 1057.468506] composite sync not supported
[ 1059.570748] composite sync not supported
[ 1060.181290] composite sync not supported
[ 1060.217522] composite sync not supported
[ 1066.945376] composite sync not supported
[ 1068.219584] composite sync not supported
[ 1068.420070] composite sync not supported
[ 1069.720865] composite sync not supported

its a wd 640 gig drive if that matters

---

### Post by SpaceOdin on 2011-10-21
edit: i think i need the drivers, no option on their the wd website. anyone know where i can get them? its a western digital WD6400h1U

---

