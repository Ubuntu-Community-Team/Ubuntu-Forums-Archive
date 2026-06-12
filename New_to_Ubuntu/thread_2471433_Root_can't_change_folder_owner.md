---
title: "Root can't change folder owner"
date: 2022-01-30
forum: New to Ubuntu
---

### Post by ggolub on 2022-01-30
Hello Forum,

i am encountering the following error.
Can you please help me to fix this issue.

root@sl400:/u1/a# chown gene /u1/a
chown: changing ownership of '/u1/a': Operation not permitted

---

### Post by TheFu on 2022-01-30
root cannot change own on 
* NFS mounts from other systems (root on the client system doesn't get powers over storage on another box)
* non-Linux file systems like NTFS, FAT32 or exFAT (owner and group for these can only be set through mount options)
* Sometimes, if there is any network share at or below the directory level - specifically samba or "user" shares.
* If the new username doesn't exist on the system. It can be either in the /etc/passwd file or some LDAP directory server configured.
* Storage mounted read-only or 
* directories set to "immutable"  (chattr command)

That's all the things I can think of off the top of my head.

---

### Post by oliver-lau on 2022-01-30
The command has the following form:

sudo chown name:name file-name-or-folder

Make a cd ..

an try aforementioned command again.

---

### Post by ggolub on 2022-01-30
Thank you guys for your answer. File system was formated with fat. I used Gparted to unmount, format and then mounting back. All worked.

---

### Post by ActionParsnip on 2022-01-31
> **ggolub said:**
> Thank you guys for your answer. File system was formated with fat. I used Gparted to unmount, format and then mounting back. All worked.

Please mark as solved if the issue has been sorted

---

