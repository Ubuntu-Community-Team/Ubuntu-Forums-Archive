---
title: "Missing file manager and trash can after deleting gdisk and fuse"
date: 2019-01-14
forum: New to Ubuntu
---

### Post by tarasiy on 2019-01-14
Accidentally, I'd deleted gdisk and fuse and after that file manager and trash can got missed as well as some other stuff (e.g. gnome-tweak-extensions). Of course, I reinstalled the deleted packages, but the apps still aren't available (or at least they aren't anywhere to find). Can you help me fix this issue? And maybe explain generally how badly the deletion affected the system? (I'm using Ubuntu 18.04)

---

### Post by Impavidus on 2019-01-15
When you removed those packages, you probably removed some packages depending on them too. Have you reinstalled those as well? If you don't know which packages they were, have a look at the log file:```
cat /var/logs/dpkg.log
```Look for packages removed at the same time as gdisk and fuse.

---

### Post by tarasiy on 2019-01-15
Thanks for the explanation. I've already reinstalled the whole system so now everything works again :)

---

