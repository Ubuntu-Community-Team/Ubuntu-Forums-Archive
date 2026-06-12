---
title: "11:04 - restore bottom toolbar"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by jwreader on 2011-12-18
i accidentally deleted the bottom toolbar on the desktop - where windows
go to rest. how do i restore it?

---

### Post by lechien73 on 2011-12-18
Hi...my 11.04 installation didn't have a bottom toolbar (but that could be because I'd already deleted it - I forget!).

In previous Gnome-based versions of Ubuntu, the method for restoring the bottom toolbar was to open a terminal window and type:

```
gconftool –-recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by JC Cheloven on 2011-12-18
> **jwreader said:**
> i accidentally deleted the bottom toolbar on the desktop - where windows
go to rest. how do i restore it?
Your question suggest that you're using classic gnome (gnome2 with gnome panel). If so, simply:
- Right-click at an empty space on your upper panel.
- Choose add panel. Put the new panel to the bottom.
- Right-click in the newly created panel, choose "add items", and do so as desired (add a windows list, in your case).

Cheers

---

