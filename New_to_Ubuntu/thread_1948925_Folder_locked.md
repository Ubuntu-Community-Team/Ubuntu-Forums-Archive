---
title: "Folder locked"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-03-29
Hi friends,

root folders like /etc, /bin, /usr, & all i mean folders in "/" directory were looks locked when i logged as user (eg: username= dev001) but when i logged in root account (username = root) all folders are looks like normal.

i cant run crontab in user account
error i come accrossed is 
"you are not allowed to run crontab"

kindly help friends

---

### Post by zombifier25 on 2012-03-29
Those folders belong to root with a permission set so that only the root user can modify it (and in some case, view it) This is for security purpose, so that a compromised user can't damage the system
Also, crontab cannot be run without being a root user, since only root can modify system files.
If your user account has an entry in the sudoer file (a.k.a. an admin account) then you can run a command as root by
```
sudo command
```

P.S. Read here to se why logging as root is bad, really, REALLY bad: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

