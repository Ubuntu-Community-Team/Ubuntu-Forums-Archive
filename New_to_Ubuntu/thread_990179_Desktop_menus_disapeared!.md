---
title: "Desktop menus disapeared!"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by timbim on 2008-11-22
The menu bars at the top and bottom of the screen have disappeared for one user on my Xubuntu system.  How do I get them back?

---

### Post by shoot2kill on 2008-11-22
[ALT] + [F2]
type: gnome-panel

what happens for you ??

---

### Post by timbim on 2008-11-22
Fails, no such file or directory.

---

### Post by m_duck on 2008-11-22
As it is Xubuntu, try:
```
xfce4-panel
```

---

### Post by timbim on 2008-11-22
Fixed.  Thanks.

---

### Post by shoot2kill on 2008-11-22
try:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

edit: was too long with reply, and totally overlooked the whole xfce situation.. glad you have it fixed anyway..

---

