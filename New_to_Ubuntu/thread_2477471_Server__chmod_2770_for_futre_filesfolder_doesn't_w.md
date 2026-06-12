---
title: "Server / chmod 2770 for futre files/folder doesn't work"
date: 2022-07-26
forum: New to Ubuntu
---

### Post by stewartsherah on 2022-07-26
Hey folks

I have a folder, added a group and want, that 2 users can work on this projekt

```
addgroup projektxy
usermod -a -G projektxy sebastian
usermod -a -G projektxy matthias
mkdir -p /projekte/xy
chgrp projektxy /projekte/xy
chmod 755 /projekte
chmod 2770 /projekte/xy
```

Matthias can add folders to /projekte/xy and also files
but sebastian can't edit them, because he hasn't got the permission

Alle the new files and folders only get "-rw-r--r-- "

All future files should have the same permission as 770 - what do i miss?

thanks for u help

---

### Post by Holger_Gehrke on 2022-07-26
Check the umask for user Matthias ('umask -pS').

Holger

---

### Post by stewartsherah on 2022-07-26
amazing! Thanks for the hint

umask 2 did the thing!

---

