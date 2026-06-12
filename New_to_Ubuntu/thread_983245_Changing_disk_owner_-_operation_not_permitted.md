---
title: "Changing disk owner - operation not permitted"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by ozzyprv on 2008-11-15
I am trying to change the owner of a disk I have installed in my computer.

> 
user@Ubuntu:/media$ ls -l
total 48
lrwxrwxrwx  1 root root        6 2008-11-01 17:45 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-11-01 17:45 cdrom0
drwxrwxrwx  1 root root    12288 2008-10-11 00:32 disk
drwxrwx--- 12 root plugdev 32768 2008-11-15 11:26 shared
user@Ubuntu:/media$ sudo chown user shared
chown: changing ownership of `shared': Operation not permitted
user@Ubuntu:/media$ 


---

### Post by Elfy on 2008-11-15
Try

```
sudo chown user:user /path/to/folder
```

So if drive is /media/shared and you are bert

sudo chown bert:bert /media/shared

---

### Post by taurus on 2008-11-15
What device mounted to shared and what is the filesystem of that partition?

---

### Post by ozzyprv on 2008-11-15
This is what I get as bert

> bert@MobilUbuntu:/media$ sudo chown bert /media/shared
chown: changing ownership of `/media/shared': Operation not permitted
bert@MobilUbuntu:/media$ 



from fstab

> UUID=9DB4-4DD5  /media/shared   vfat    utf8,umask=007,gid=46 0       1

---

### Post by Elfy on 2008-11-16
You need to set permisssions in fstab - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

A long thread - the section you need is
VFAT/NTFS:

Bit further down there are some examples.

Make sure to backup before editing the file

```
sudo cp /etc/fstab /etc/fstab.1611
```

---

