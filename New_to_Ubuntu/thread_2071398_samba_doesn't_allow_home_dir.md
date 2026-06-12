---
title: "samba doesn't allow home dir"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-10-15
Hi,

I set up my share folder like this ```
[Home]
    comment = Home Folder
    path = /home/deniz
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
```
But when I want to create new folder in this share folder windows saying > You need permission to perform this action

---

### Post by Gone fishing on 2012-10-15
THe samba user isn't deniz and so can't create folders in deniz home. I suggets you create a folder to share at /home/share and put 777 permissions on that folder.

---

