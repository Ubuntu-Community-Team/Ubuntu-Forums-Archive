---
title: "boot error"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by adityamagadi on 2013-01-19
hey guys i run a dual ubuntu windows 7 till yesterday ubuntu was fine today morning when i boot up ubuntu it tell "target system doesnt have /sbin/init" and a busy box prompt opens.

how can i fix this problem? pla help me out i have a lot of data on ubuntu which i dont wanna loose :(

---

### Post by cariboo on 2013-01-20
I'd suggest you use a live cd to boot your system, and before you do anything, backup all your valuable data. After you have backed up your data, run the following command in a terminal:

```
sudo fsck -c-y /dev/sdxX
```

where /dev/sdxX = your / partition.

Once the fsck command has finished running, shutdown the system, and reboot.

---

### Post by adityamagadi on 2013-01-21
thanks a ton it worked :)

---

