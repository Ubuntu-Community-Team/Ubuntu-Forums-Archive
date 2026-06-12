---
title: "[SOLVED] Need to share a drive"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-24
I want to share one of my external drives on my local network.  If I right click on the folder the drive is mounted in (/media/XXX) and select sharing options, check all the boxes, and specify for permissions to be added automatically, everything seems to work.  Other computers can see the share, but when they try to mount it, they get a dialog asking for a username and password.  Neither my username and password or those of that computer's administrator, or the current user will allow the drive to be mounted.  This dialog only appears with shares that are in the /media directory.  Is there a way to grant permission to other computers to access shares in the /media directory?

Thanks!

---

### Post by BDNiner on 2008-07-24
are you using samba to connect to the share. it would be samba if the drive is formatted as NTFS. you would need to add yourself to the samba users in order to login.

---

### Post by pi.boy.travis on 2008-07-24
The drive is FAT32, but adding users to the samba group should work. . .

---

### Post by pi.boy.travis on 2008-07-24
That did it!  Thanks!

---

