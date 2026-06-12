---
title: "Edited GNOME Main menu"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by harsh_ on 2008-06-07
Using 8.04 and had three things on the panel as applications, places and system which is by default.... did some changes and it all went away. Added the main GNOME menu bar but was comfortable with the earlier look How do i regain the same. Please help

---

### Post by spiderbatdad on 2008-06-07
right clicking on the icons in the panel allows you to unlock them and remove them. Selecting add to panel by right clicking an open area of the panel, allows you to choose items you can add to the panel from the main menu.

Menu Bar is the default item. Main menu is similar, and has the other menus incorporated.

Here is a shot of my Desktop...Only using a bottom panel.

And one here, running cairo-dock:[http://img139.imageshack.us/my.php?image=screenshotpq7.png](http://img139.imageshack.us/my.php?image=screenshotpq7.png)

---

### Post by mevets on 2008-06-07
if what you mean is that you had a menu compressed into one icon then you can find itt by going into add applets. it is located next to the menubar. i can not remember the name but it might be close to something like gnome-main-menu

---

### Post by starcannon on 2008-06-07
If you want to restore gnome-panels back to the default settings:

```
rm -r ~/.gconf
```

Then reboot, and they will be back to the way they looked when you first installed.

---

