---
title: "[SOLVED] login manager not starting"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by nerdking on 2008-10-25
system-administration-login window. when i click on it it will be there for a brief second then close and i don't know why.

---

### Post by quirks on 2008-10-25
Honestly, right now I have no clue what could cause this. Other windows / administrative tools work, don't they?

Try to launch the tool from a terminal (Applications -> Accessories -> Terminal) using this command:
```
gksu /usr/sbin/gdmsetup
```
Maybe it produces some output on the command line which is helpful.

---

