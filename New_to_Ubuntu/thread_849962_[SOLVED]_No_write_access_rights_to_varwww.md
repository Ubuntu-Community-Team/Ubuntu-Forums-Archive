---
title: "[SOLVED] No write access rights to /var/www"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by WebSiteGuru on 2008-07-05
I just installed web server on my ubuntu machine. But it will not give me write access how can I fix this problem?

Thanks!

---

### Post by NikoC on 2008-07-05
Easiest way imo opinion is to start nautilus in sudo mode, i.e. in a terminal type sudo nautilus
It will prompt for you sudo password. When you right click a folder you can change permissions to write...

Cheers

---

### Post by cpetercarter on 2008-07-05
The directory is owned by root, so you need to use sudo to change permissions.

Or you could move the default "localhost" site elsewhere e.g. to somewhere in your home directory. See the section on virtual hosts in [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by hyper_ch on 2008-07-05
or you could chown the /var/ww folder

---

### Post by uarale on 2008-07-05
You can press Alt+F2, type: gksudo nautilus

Then in nautilus press Ctrl+N for new window into which you copy files.

---

### Post by sayakb on 2008-07-05
Agree with hyper_ch.. at a terminal:
```
sudo chown username:group /var/www
```Where username is your own username.

---

### Post by WebSiteGuru on 2008-07-06
Thank you very much everyone. Now I can get some work done. :D

---

