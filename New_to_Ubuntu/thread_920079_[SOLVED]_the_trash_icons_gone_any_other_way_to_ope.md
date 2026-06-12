---
title: "[SOLVED] the trash icons gone any other way to open trash?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by wawadave on 2008-09-14
my trash icon lower right has disappeared.
is there any other way to access it?

---

### Post by starcannon on 2008-09-14
R-click on the bar, then Add to Panel, Choose "Trash" from menu, click Add, click Close.


If you want it on your desktop:
alt+F2

```
gconf-editor
```

/apps/nautilus/desktop

Put a check mark in "trash_icon_visible"

exit.

---

### Post by iaculallad on 2008-09-14
Using terminal:

```
cd ~/.local/share/Trash/files
```

---

### Post by wawadave on 2008-09-14
thank you first solution solved the problem! will save second as a fall back!!!

---

