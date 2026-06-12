---
title: "where are my partitions?"
date: 2010-08-17
forum: Philippine Team
---

### Post by enhu on 2010-08-17
when i do

> ubuntu:/# ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4

mounting the device don't work too. and  when i run df -h, the output are just these..

> ubuntu:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             7.9G  2.0G  5.6G  26% /
none                  245M  248K  245M   1% /dev
none                  249M  148K  249M   1% /dev/shm
none                  249M   92K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw


Zenwalk however that's in the /sda3 can see all the drives everytime i boot it. anyone got into same situation?
any solutions please?
i'm running xubuntu 10.04

---

