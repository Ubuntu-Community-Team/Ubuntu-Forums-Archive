---
title: "[SOLVED] unable to mount NTFS; have followed HOWTO"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by ieee488 on 2008-11-19
I have Ubuntu 8.10 installed on my 2nd hard drive sdb2.
Windows is installed on my 1st hard drive sdb1.

I have looked at [http://ubuntuforums.org/printthread.php?t=217009](http://ubuntuforums.org/printthread.php?t=217009)

I added */dev/sdba1     /media/Windows    ntfs-3g     defaults,locale=en_US.utf8   0    0* to /etc/fstab
but it doesn't work.

I have to go up to Places and select the 1st hard drive then it mounts.

---

### Post by bumanie on 2008-11-19
What you followed is very old. Since 8.04 ntfs-3g has been included as default. To automount your ntfs drive, in terminal > sudo apt-get install ntfs-configThen go to Applications --> System Tools --> Ntfs configuration tool. Fill out the window that appears and /etc/fstab is automatically updated.

---

### Post by redseventyseven on 2008-11-19
First of all, there's a typo:

> /dev/sdba1

If you copied and pasted that from your fstab file then that might be the cause of your problems.

Secondly, check the Synaptic Package Manager, see if the ntfs-3g package is installed.

Any help?

---

### Post by drs305 on 2008-11-19
reseventyseven is correct about the typo and that should correct the problem. ntfs-3g is installed by default in 8.10 and in fstab you can use either designation - ntfs or ntfs-3g.

ntfs doesn't support normal linux permissions, so the mountpoint will be shown as owned by root. If you would prefer it be owned by you, add your uid info into the fstab line. You might also want to add permissions (the example sets it at 750):
```

/dev/sdb1 /media/Windows ntfs-3g defaults,uid=*1000*,umask=027,locale=en_US.utf8 0 0

```

---

### Post by ieee488 on 2008-11-19
Argh!

It was a spelling error. Thank you all. :oops:

---

