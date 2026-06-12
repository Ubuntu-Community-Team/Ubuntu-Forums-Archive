---
title: "chmod problem"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by AlexHudghton on 2013-11-17
I am running a dual boot XP / 12.04 system

All the disks are originally formatted with XP and I understand it is not possible to change permissions on these using Ubuntu

I have an 8GB flash drive that I have formatted with Ubuntu

I create an empty file, so, I am the owner of it

I try to change the permissions to 777 using chmod - no change

I use sudo with the same command - no change

Someone like to try and explain what's going on please?



alex@desktop:~$ cd /media/Flash
alex@desktop:/media/Flash$ ls -al
total 8
drwx------ 2 alex alex 4096 Jan  1  1970 .
drwxr-xr-x 6 root root 4096 Nov 17 11:08 ..
alex@desktop:/media/Flash$ >test
alex@desktop:/media/Flash$ ls -al
total 8
drwx------ 2 alex alex 4096 Nov 17 11:09 .
drwxr-xr-x 6 root root 4096 Nov 17 11:08 ..
-rw-r--r-- 1 alex alex    0 Nov 17 11:09 test
alex@desktop:/media/Flash$ chmod 777 test
alex@desktop:/media/Flash$ ls -al
total 8
drwx------ 2 alex alex 4096 Nov 17 11:09 .
drwxr-xr-x 6 root root 4096 Nov 17 11:08 ..
-rw-r--r-- 1 alex alex    0 Nov 17 11:09 test
alex@desktop:/media/Flash$ sudo chmod 777 test
[sudo] password for alex: 
alex@desktop:/media/Flash$ ls -al
total 8
drwx------ 2 alex alex 4096 Nov 17 11:09 .
drwxr-xr-x 6 root root 4096 Nov 17 11:08 ..
-rw-r--r-- 1 alex alex    0 Nov 17 11:09 test
alex@desktop:/media/Flash$

---

### Post by Impavidus on 2013-11-17
It's not about the system you used to format the drive, it's about the partition type to which you formatted. Windows only knows about fat and ntfs, which don't support unix permissions. Linux uses ext4 (older systems ext2/3), which does support unix permissions, and Ubuntu obviously can format partitions as such. Most usb flash drives use the fat32 format, which is old but supported on almost any OS, and therefore cannot use permissions.

You can check the partition type of your flash drive mounted at /media/Flash with```
mount | grep Flash
```

---

### Post by AlexHudghton on 2013-11-17
thanks for the reply  - so, when the time comes to get rid of XP (very soon) I'll need to reformat all my drives to have full control?

---

### Post by AlexHudghton on 2013-11-17
OK all understood now - thanks again

---

### Post by Morbius1 on 2013-11-17
Actually, as you move to releases later than 12.04 it won't much matter how you format these external usb drives. In 12.04 they mount to /media/LABEL. In 13.04 they mount to /media/your-user-name/LABEL.

/media/your-user-name is now controlled automatically by an Access Control List that allows only "your-user-name" access to it and anything beyond it. You could format the partition to ext4 and set permissions to 777 and it will still only allow "your-user-name" access to it.

---

### Post by Impavidus on 2013-11-17
When you get rid of Windows, just reformat the ntfs partitions. The partition on which Ubuntu is installed has been formatted during the installation.

For usb flash drives, there is one reason why I don't use ext4 as filesystem. I tend to use my flash drives to transfer data between various computers. For that you need a file system understood by all OSs.

---

