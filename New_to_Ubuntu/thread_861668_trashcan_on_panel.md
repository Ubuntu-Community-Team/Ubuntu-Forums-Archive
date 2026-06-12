---
title: "trashcan on panel"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by TJ-Tigger on 2008-07-16
Is there a way to have the trashcan applet on the gnome panel not have active the Remove from Panel open when the applet is locked?  I have removed it I don't know how many times by rightclicking it to empty it and accidentily selecting remove rather than Empty Trash

---

### Post by nowshining on 2008-07-16
have u tried moving the icon to the taskbar to see if it sticks? by default in kubuntu it's there and easy to put up on the panel.. :)

---

### Post by RomeReactor on 2008-07-16
There's also the option to have the trash can it on the desktop, where it won't be deleted by accident; open a terminal (or press ALT+F2) and paste:
```
gconftool --type=bool -s /apps/nautilus/desktop/trash_icon_visible 1
```

---

### Post by kaibob on 2008-07-16
> **TJ-Tigger said:**
> Is there a way to have the trashcan applet on the gnome panel not have active the Remove from Panel open when the applet is locked?  I have removed it I don't know how many times by rightclicking it to empty it and accidentily selecting remove rather than Empty Trash

You can eliminate the remove-from-panel option by enabling the following key in the configuration editor:

/apps/panel/global/locked_down

Unfortunately, it locks down all icons in the panel, so this is probably more than you want.

---

