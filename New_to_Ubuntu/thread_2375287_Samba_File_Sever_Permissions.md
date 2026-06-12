---
title: "Samba File Sever Permissions"
date: 2017-10-23
forum: New to Ubuntu
---

### Post by daenir on 2017-10-23
Hey all, new to Ubuntu Server 17.10.

I've been following this guide:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

But the problem that occurs is that I can log in to my partitioned network drive but I can't interact with it.
I can't save files to it etc.

Here's my smb.comf

```
 
[Storage]
   comment = File Server
   path = /srv/samba/Storage
   browsable = yes
   guest ok = no
   read only = no
   create mask = 0755

```

Any help/guidelines would be much appreciated

---

### Post by ajgreeny on 2017-10-23
Duplicate at [https://ubuntuforums.org/showthread.php?t=2375281&p=13702029#post13702029](https://ubuntuforums.org/showthread.php?t=2375281&p=13702029#post13702029)

**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 

Closed.

---

