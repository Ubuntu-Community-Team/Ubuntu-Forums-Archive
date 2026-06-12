---
title: "How to put file manager on panel"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by stanley45 on 2008-05-23
The panel has this neat add dialog that lets you put almost everything on the panel - very convenient.  But it won't let me pull the top item on the Places menu there - the file manager (starts off in home page).  Long ago I got it up there, but then had to reload everything out of sheer stupidity.  I can't find any way to move the file manager to the panel.

Suggestions?

---

### Post by SunnyRabbiera on 2008-05-23
you mean like a quicklaunch right?

---

### Post by drs305 on 2008-05-23
System, Places, click and hold on Home Folder, then drag to the top panel and release.

If you want a custom location to open in nautilus, RC on panel, Add to Panel, Custom Application Launcher, in the command, enter:
```
nautilus /[path.to.desired.folder
```

Is that what you were looking for?

Added: You can save your panel settings with (choose your own location and filename):
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel_settings
```

To restore:
```
gconftool-2 --load ~/Desktop/panel_settings
```

---

### Post by philinux on 2008-05-23
> **drs305 said:**
> System, Places, click and hold on Home Folder, then drag to the top panel and release.


Or bottom panel even \\:D/

---

