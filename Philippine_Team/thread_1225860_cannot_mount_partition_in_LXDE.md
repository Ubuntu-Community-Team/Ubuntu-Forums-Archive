---
title: "cannot mount partition in LXDE"
date: 2009-07-29
forum: Philippine Team
---

### Post by sieg06 on 2009-07-29
i formatted a 80gb hdd drive and partition it in two :

1 ext3
1 fat32

now i have a problem in LXDE i cannot mount the fat32 drive. 

help

---

### Post by dodimar on 2009-07-29
any error messages?

---

### Post by dannybuntu on 2009-07-29
How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT) 
    Local mount folder: /media/windows 

```
sudo mkdir /media/windows
sudo cp -a /etc/fstab /etc/fstab_backup
sudo echo -e "/dev/hda1\t/media/windows vfat\tiocharset=utf8,umask=000\t0 0" >>/etc/fstab
```

[http://ubuntuguide.org/wiki/Ubuntu:Edgy/Windows](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Windows)

---

### Post by dodimar on 2009-07-29
Mounting UUID would be good if you have multiple physical hard drive...

[http://ubuntuforums.org/showpost.php?p=7657537&postcount=7](http://ubuntuforums.org/showpost.php?p=7657537&postcount=7)

---

