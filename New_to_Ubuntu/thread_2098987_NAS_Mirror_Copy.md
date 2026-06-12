---
title: "NAS Mirror Copy"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by petronell on 2012-12-28
Hi Everyone,

Merry Christmas. I have what is probably quite a simple problem for those of you that know!

I have a NAS box that has a 2TB disk installed that all of my family use as a simple file server. We use a variety of clients, MAC OS X, Windows 7 and personally I use Ubuntu 12.04.1 on my laptop.

Because we now have about 800gb of data stored on the NAS I would like to make a mirror copy of it. I have been reading up on both rsync and unison.

I have purchased a second 2TB USB drive which is now plugged into my Ubuntu laptop and would like some recommendations on the best way I can keep these two in sync where the NAS is the master copy.

Many thanks,

D

---

### Post by vanadium on 2012-12-28
You can keep two file sytems that support unix permissions perfectly in sync with the command
```

rsync -av --delete <source> <destination>

```

rsync is very fast in that it only propagates the changes on the source file system to the target.

-a ("archive") is a summary option and is equivalent to -rlptgoD (see "man rsync"). If the target system does not support unix permissions, some of thes options need to be removed/changed.

The --delete option deletes all files on the destination that do not exist in the source. Be carefull with it. Only add the option once you know the command is working as expected. Otherwise, you may unadvertently erase data on the target you did not intend.

---

