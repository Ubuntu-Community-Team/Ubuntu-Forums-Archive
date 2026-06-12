---
title: "No Disk Space Problem.........???"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by usater on 2008-05-06
Hai, friends

i'm using Gusty(7.10) x86 64-bit.

when i'm browsing or using anything with _**wine**_ i always got a message of no disk space in home directory.Even a folder cannot be created there when wineserver is running.

On a reboot the problem will be solved, but when i start **_wine_** again it repeats.

why it is so?:confused:

i have now 2.1GB free in home directory.(when i'm using **_wine_**)

2 users has been created and one is never logged in till now.


thanks in advance

---

### Post by bone2006 on 2008-05-08
2GB is pretty low, but shouldn't be a problem
open up a terminal and type in df -h and ensure you really do have space.
Are you only experiencing this problem when running wine?

---

### Post by usater on 2008-05-10
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.1G  2.7G  2.2G  56% /
varrun                120M   88K  120M   1% /var/run
varlock               120M     0  120M   0% /var/lock
udev                  120M   88K  120M   1% /dev
devshm                120M     0  120M   0% /dev/shm
lrm                   120M   38M   83M  32% /lib/modules/2.6.22-14-generic/volatile
/dev/sda8              92M   24M   63M  28% /boot
/dev/sda7             4.7G  542M  3.9G  12% /home
/dev/sda1              19G   16G  3.2G  84% /media/sda1
/dev/sda10            8.2G  6.7G  1.5G  82% /media/sda10
/dev/sda11             19G   17G  2.1G  89% /media/sda11
/dev/sda5              19G   15G  4.0G  79% /media/sda5

This is the staus when executed hf -h

this promblem is only when i start wine.

if i reboot it stops and when i start wine it repeats

---

