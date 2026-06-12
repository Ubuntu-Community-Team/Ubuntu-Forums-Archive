---
title: "[SOLVED] File permissions on mounted HDD"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Korijn on 2008-05-28
I have an external USB HDD (NTFS) mounted through /etc/fstab on /media/external.

This is also the DocumentRoot of my apache2 webserver. Now I have a problem. I want to adjust the permissions of some of these files, but whenever I do they just automatically revert back to 777!

Specifically, I'm trying to issue the following command:

```
sudo chmod o-rw /media/external/phpMyAdmin/config.inc.php
```

But it just keeps changing back. What do I do?!

---

### Post by drkameleon on 2008-05-28
Perhaps it's a file-ownership issue.

Try

```
chown USERNAME FILE
```

---

### Post by sam_delta on 2008-05-28
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

few questions
does it return to 777 when you unmount/mount? or imediatly?

are you the current owner of the file? if not, try the command posted above

try 
```
sudo chmod 700 /media/external/phpMyAdmin/config.inc.php
```

sam

---

### Post by Korijn on 2008-05-28
I tried both suggestions but both values are immediately reverted to owner: root and permissions: 777.

This happens immediately after I issue the command.

---

### Post by kpkeerthi on 2008-05-28
> **Korijn said:**
> I tried both suggestions but both values are immediately reverted to owner: root and permissions: 777.

This happens immediately after I issue the command.

I don't think permission can be set on a file present in NTFS partitions.

NTFS does not support UNIX/Linux file permissions.

---

### Post by hyper_ch on 2008-05-28
I have to agree with the above poster. NTFS does not support linux file permissions.

---

### Post by Korijn on 2008-05-28
That sucks. xD

/thread

---

### Post by chrisccoulson on 2008-05-28
Yes, NTFS doesn't understand Unix file permissions. If you want to change the permissions of everything on it, you can use the uid, gid and umask options in your fstab. For example, 'uid=0,gid=0,umask=0002' will set the mount ownership to root:root and the permissions of everything on it to 775

---

### Post by Korijn on 2008-05-30
Alright, I ended up switching DocumentRoot back to /var/www. So that's where it's probably going to stay.

Thanks alot for the help.

---

