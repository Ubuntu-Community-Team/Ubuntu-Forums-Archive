---
title: "any way to view a session / currently access files"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Corrupter on 2008-05-29
hey guys, im a bit new to Linux although i have no trouble getting around, im looking for a way to view sessions currently connected to my machine and possibly what files they are accessing.  I would love to be able to view SSH/FTP/HTTP sessions / files accessed... any thoughts.

Thanks in advance.
Corrupter

---

### Post by K.Mandla on 2008-05-29
Moved to Absolute Beginner Talk.

---

### Post by eentonig on 2008-05-29
read the man page for lsof (List Open Files)

Since linux treats everything as a file, this will do exactly what you want. But it will take a learning curve.

---

### Post by drs305 on 2008-05-29
If you have saved a session via System, Preferences, Sessions, Session Optionis a file was created: ~/.gnome2/session. 

You can also view /var/log/dmesg to see what is happening on boot.

---

