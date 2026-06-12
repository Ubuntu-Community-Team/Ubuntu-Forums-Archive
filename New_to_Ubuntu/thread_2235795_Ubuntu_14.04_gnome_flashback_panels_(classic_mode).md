---
title: "Ubuntu 14.04 gnome flashback panels (classic mode)"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by Billisnice on 2014-07-23
I goofed around and mess my top and bottom panels up. How do I reset both top and bottom panels?

Thanks

---

### Post by ibjsb4 on 2014-07-23
Open a terminal and enter:
```
dconf reset -f /org/gnome/gnome-panel/
```
and then
```
killall gnome-panel
```
If you ever hose your desktop settings you can reset with:
```
dconf reset -f /org/gnome/desktop/
```

---

