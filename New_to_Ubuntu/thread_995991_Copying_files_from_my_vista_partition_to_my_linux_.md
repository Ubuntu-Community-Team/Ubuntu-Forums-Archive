---
title: "Copying files from my vista partition to my linux partition"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Gusss on 2008-11-28
Hi,
Can I access my Vista partition from my ubuntu 8:10 partion on my dual boot machine ? I either want to copy the files across or just access them. Interestingly enough there is a HP recovery partion that I can acess easily but the main Windows vista partition doesnt even show up under "computer".

---

### Post by taurus on 2008-11-28
Yes, you can access your vista partition but first you need to mount it before you can access it.  You can do that with ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Gusss on 2008-11-28
> **taurus said:**
> Yes, you can access your vista partition but first you need to mount it before you can access it.  You can do that with ntfs-config.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Thanyou for your answer. Will this interfere with the functioning of my Vista ?

---

### Post by taurus on 2008-11-28
Not as long as you don't delete files that vista needs to boot or run.  If you just copy files from vista to Ubuntu, shouldn't be a problem.

---

