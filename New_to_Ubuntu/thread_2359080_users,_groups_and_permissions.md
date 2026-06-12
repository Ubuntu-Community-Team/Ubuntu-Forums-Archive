---
title: "users, groups and permissions"
date: 2017-04-20
forum: New to Ubuntu
---

### Post by sasab on 2017-04-20
A bit confused.
I have a server and two users. They were created like this
```

adduser mario
usermod -aG sudo mario
adduser marioftp --ingroup ftpaccess --shell /usr/sbin/nologin

```

I don't know if something else has been done. 
I was told to upload files with marioftp. But marioftp can't be logged on so user mario is logged on to view the files. If I want to edit files i should take ownership to mario.
So I thought why couldn't I add mario user to ftpaccess group and set permission on all files to 770 and have mario always be able to edit files.
```
usermod -a -G ftpaccess mario
```
But then I can't login into shell with mario anymore until i use root to remove mario from ftpaccess group.
What did I miss?

---

