---
title: "MATE: can't find xterm in menu"
date: 2021-06-13
forum: New to Ubuntu
---

### Post by maketopsite on 2021-06-13
Ubuntu 20.04

Is it please possible to add xterm to MATE menu ?

---

### Post by TheFu on 2021-06-13
Yes.   Create a .desktop file and force the system to re-index all .desktop files.  No clue how to accomplish that. Might just be able to place the .desktop file in the same directory as all the other .desktop files?  IDK.

Probably don't want to put this file into any "autostart" directory.

```
$ locate .desktop |grep xterm
```
Found existing xterm .desktop files.
/usr/share/applications/debian-uxterm.desktop
/usr/share/applications/debian-xterm.desktop
/usr/share/mate/applications/debian-uxterm.desktop
/usr/share/mate/applications/debian-xterm.desktop

---

### Post by dddman on 2021-06-13
Have you checked your edit menu?
[https://ubuntu-mate.community/t/adding-installed-apps-to-application-menu/792/4](https://ubuntu-mate.community/t/adding-installed-apps-to-application-menu/792/4)

---

### Post by Dennis N on 2021-06-13
Copy the .desktop file from /usr/share/applications to ~/.local/share/applications 
No changes are necessary to the file.
Then it will show immediately in the Menu. (see attachment).

System: Ubuntu MATE 20.04

---

### Post by maketopsite on 2021-06-16
Thank to all, it was solved by Edit Menus [https://ubuntu-mate.community/t/adding-installed-apps-to-application-menu/792/3](https://ubuntu-mate.community/t/adding-installed-apps-to-application-menu/792/3)

---

