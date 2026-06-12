---
title: "adding application to menu"
date: 2007-01-18
forum: Programming Talk
---

### Post by ianare on 2007-01-18
i've made a .deb file which installs my program and creates the necessary .desktop file for inclusion in the menu. If i open up the menu editor it's there, and checked. However it will not show up in the menu unless I log out and log back in, or if uncheck and check it in the menu editor.

What am I missing?

---

### Post by mojoman on 2007-01-18
Try```
$ update-menus
```

---

### Post by ianare on 2007-01-18
```
root@ianare-ubuntu:/home/ianare# update-menus
bash: update-menus: command not found
```

it looks like this is part of the debian menu system, which is depreciated, and not installed by default on ubuntu. I am trying to do this using the freedesktop.org system

---

