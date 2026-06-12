---
title: "help, ubuntu wont boot"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by boblemur on 2008-08-19
i am trying to boot up into ubuntu but it wont boot.

im trying to restore a damaged hard disk, but ubuntu wont boot with it plugged in. i have turned off quiet and i keep getting disk read failures, is there any way to deal with this? so i can get to a terminal or boot?

---

### Post by spiderbatdad on 2008-08-19
try replacing quiet splash with: all_generic_ide
Are you sure the disk hasn't failed?

---

### Post by boblemur on 2008-08-20
yes the disk has failed, thats what im trying to achieve, i would like to attempt to read any available sectors of the disk that are still able to be read.

however, sdb is not accessable by fdisk so i cant try and mount it or anything. any advice would be much appreciated...


ps. the dead disk is not the one im trying to boot off...

---

