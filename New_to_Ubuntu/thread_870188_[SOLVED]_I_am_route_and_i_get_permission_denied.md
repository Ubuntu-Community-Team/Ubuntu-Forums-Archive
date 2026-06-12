---
title: "[SOLVED] I am route and i get permission denied"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by AnonUK on 2008-07-25
Hi everybody

I'm installing Tor on ubuntu and i'm having a problem with privoxy

root@anonymous-desktop:~# /etc/privoxy/config
-bash: /etc/privoxy/config: Permission denied


can anybody please help ?

edit-bad spelling in title

thanks for the help!

---

### Post by tamoneya on 2008-07-25
that file may not have executable permissions.  Check it out with this:```
ls -l /etc/privoxy/
```

---

### Post by AnonUK on 2008-07-25
-rw-r--r-- 1 root    root 40669 2008-03-14 10:34 config
-rw-r--r-- 1 root    root 44792 2008-03-14 10:34 default.action
-rw-r--r-- 1 root    root 52462 2008-03-14 10:34 default.filter
-rw-r--r-- 1 privoxy root   506 2008-03-14 10:34 global.action
-rw-r--r-- 1 root    root  2666 2008-03-14 10:34 standard.action
drwxr-xr-x 2 root    root  4096 2008-07-25 19:40 templates
-rw-r--r-- 1 privoxy root  3697 2008-03-14 10:34 trust
-rw-r--r-- 1 privoxy root  5982 2008-03-14 10:34 user.action

---

### Post by tamoneya on 2008-07-25
yep it isnt executable.```
chmod +x /etc/privoxy/config
/etc/privoxy/config
```
btw: you really shouldnt need to log in as root to do this.  You should be using sudo.

---

