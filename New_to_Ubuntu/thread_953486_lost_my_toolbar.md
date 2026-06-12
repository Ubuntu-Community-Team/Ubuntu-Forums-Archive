---
title: "lost my toolbar"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by santhosh.raju on 2008-10-20
dear friends
  I accidentally lost the toolbar(usually present at the bottom of screen) onto which all the applications which I have minimized or present on screen would be shown.I tried restoring it in many ways but couldn't get the solution.I would be delighted if anyone posts the solution

---

### Post by Toet on 2008-10-20
Is the panel at the bottom totally gone? Or is it only the applicationlist, which is missing?

---

### Post by geirha on 2008-10-20
Right click your other panel and select "New Panel". Press the middle mouse button on the new panel and drag it around to move it where you want it. Then right click this new panel and select "add to panel" and add the Window list applet (or something like that). You'll also need to add the other applets you had the same way.

It might be easier to just reset the panels to the way they are for a freshly created user. To do this, you type in a terminal:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by nothingspecial on 2008-10-20
If you want a new panel at the bottom of the screen, right click on the top one and select add new panel.

Which ever panel you want your open and minimized widows visible on, right click on it, click add to panel and select window list.

---

