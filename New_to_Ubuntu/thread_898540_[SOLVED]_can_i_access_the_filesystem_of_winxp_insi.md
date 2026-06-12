---
title: "[SOLVED] can i access the filesystem of winxp inside xubuntu?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-23
hi, i just want to ask if its possible to access the filesystem of winxp inside xubuntu? i installed xubuntu as a dual boot. thanks in advance...

---

### Post by kk0sse54 on 2008-08-23
Yes you can as I believe Xubuntu already has the NTFS drivers installed by default which will allow you to both read and write to your Windows partition

---

### Post by qstraza on 2008-08-23
Try looking into the /media folder, ubuntu usually automatically detects windows.

if that doesnt work than type this in (look for win partition (ntfs) and remember its path (eg. /dev/sda1))
```
sudo fdisk /dev/sda -l
```

make a dir for windows
```
sudo mkdir /media/win
```

Replace sda with your device (usually is sda). This will list all the partitions on sda, so than you just mount the XP 

```
sudo mount -t ntfs /dev/sda1 /media/win
```

sda1 is win partition, change this so it will fit your specifications.

If this works, add it to /etc/fsab for auto mounting at boot.

---

