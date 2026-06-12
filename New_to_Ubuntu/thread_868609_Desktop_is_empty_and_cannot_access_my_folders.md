---
title: "Desktop is empty and cannot access my folders"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by windriver on 2008-07-24
Hi, I use Hardy and suddenly realized that all the files from the desktop has vanished and also I cannot access to my hard drive, folders from the "places". However, I can access to all of them from terminal. Need help to solve this problem. Thanks.

---

### Post by scragar on 2008-07-24
try killing nautilus:
```
killall nautilus
```
and if that doesn't work try launching it again from a terminal, see what error messages there are if any.

---

### Post by windriver on 2008-07-24
error messages are [2] 7797
                 [1] Segmentation fault     nautilus

---

### Post by scragar on 2008-07-24
ok, first thing to try is reinstalling nautilus from a command line:
```
sudo apt-get install --reinstall nautilus
```
then try restarting nautilus, if that doesn't work you may be able to roll back to the previous version, in the package manager highlight nautilus and use "Packages>Force Package" in the top menu to roll it back.

---

