---
title: "Can't use SD card"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by RATM_Owns on 2008-11-22
I'm not allowed to do anything to my SD card.

I've tried remounting it from terminal (sudo mount -t vfat /dev/sdd1 /media/disk-2 + sudo mount /dev/sdd1 /media/disk-2 -o user,uid1000 + sudo mount /dev/sdd1 /media/disk-2 -o umask=000), sudo chowning (sudo chown -hR andy:andy /media/disk-2 + sudo chown -R andy:andy /media/disk-2), sudo chmodding (sudo chmod 777 /media/disk-2 -R) and none of them work.

---

