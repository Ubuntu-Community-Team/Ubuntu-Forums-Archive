---
title: "How to activate SWAP partition permanently?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by prookie on 2012-01-03
Hello everyone,

I've installed Ubuntu without SWAP partition. After installation, I've created new SWAP paritition and activated it by using commands:
```

mkswap /dev/sda2
sync
swapon /dev/sda2

```

Unfortunately, after reboot SWAP partition is inactive again. I guess I have to edit some system files.

Please, can someone help me with that. Thank you in advance.

pRookie

---

### Post by spacecheck on 2012-01-03
I turned mine on with Gparted (right clicked the partition & selected "swapon"). It has stayed on ever since.

Good luck!

---

### Post by mcduck on 2012-01-03
You need to configure the swap partition in /etc/fstab to get it mounted automatically on boot. Same as with any other partitions you'd want mounted on boot.

Check the correct UUID for the partition using *sudo blkid* command, and then add a line like this in fstab (using the correct UUID of course):

```
UUID=a6753a67-7496-408d-8660-6c1bd9b24ac6 none swap sw 0 0
```

(and keep in mind that if you run the *mkswap* command again it will change the partition's UUID so you'll have to fix fstab again. Not that you should ever really need to run *mkswap* more than once per swap partition...)

---

### Post by daniroma on 2012-03-11
@mcduck : Problem solved. Thank You

---

