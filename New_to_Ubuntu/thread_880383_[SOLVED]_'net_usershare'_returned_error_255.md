---
title: "[SOLVED] 'net usershare' returned error 255"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by GrnFrag on 2008-08-04
Hi all,

I'm trying to mount and share some ISO's across my LAN, to 2 winhosed computers.   i'm following the instructions here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

   when i try to share the folder, either graphically or in Terminal, i get the message above.   it says i don't have permissions to create a usershare, ask my admin.     Hello, i'm the closest to an admin around here.
Anyways, i tried a few things.   went to the directory above the one i want to share and 
```
every1@MoonRock:~/Work$ sudo chown every1:sambashare ISO
every1@MoonRock:~/Work$ sudo chmod 775 ISO
every1@MoonRock:~/Work$ sudo chmod g+s ISO

```
Which, if i'm understanding this, should grant my and my new group full access to the whole directory.  still no joy   P.S.   the folder is called ISO, i'm not sharing the mount point.     Although if i could it might make this easier


Thanks in advance, you guys rock!

---

### Post by GrnFrag on 2008-08-04
NM, i needed to reboot, apparently.   Mebbe that stupid firewall moblocker.   either way, sry to take your time

---

