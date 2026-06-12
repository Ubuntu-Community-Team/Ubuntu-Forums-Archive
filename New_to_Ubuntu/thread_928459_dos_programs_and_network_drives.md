---
title: "dos programs and network drives"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by alpdo on 2008-09-24
i have a dos program and its on a network drive...
i used : nautilus smb://xxxx.xxxx.xxxx.xxxx/d to open the network shared drive then i right the exe file of my program then run with dosemu... it works fine.
but when i mount the network shared drive using : 
sudo mount -t cifs //domainname/shared /media/program -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
then i open the mounted drive and run my dos program using dosemu...
i gives a lot of error....

what did i do wrong ?????

---

### Post by bab1 on 2008-09-24
I believe this is a filesystem problem.  Is the drive you're mounting vfat, FAT32 or NTFS?  Do you need to mount it with the CIFS option?  Just a thought; why hard mount it at all?  Use Nautilus and bookmark the share.  I use Samba and never hard mount shares.  I've never have a problem.

---

