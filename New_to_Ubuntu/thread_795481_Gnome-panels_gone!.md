---
title: "Gnome-panels gone!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-15
&#65279;On the other account on my 8.04, after restart the gnome-panels are gone, I even tried running killall gnome-panel, no use

---

### Post by GCoffee on 2008-05-15
I know in XFCE you can just add panels to your hearts content.. Try looking under administration for something..

---

### Post by shoaibi on 2008-05-15
not a very useful post, even though i mentioned "GNOME"...
Problem still there...
I know how to get panels back, i will simply delete my .gnome, .gnome2, and .gconf folder, and they will be back, but i dont wanna add all the applets again...

---

### Post by drs305 on 2008-05-15
Too late for this time ](*,) but you can save your panel settings to prevent having to recreate them:
To save:
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel_saved_settings
```

To restore:
```
gconftool-2 --load ~/Desktop/panel_saved_settings
```

---

### Post by daemon3 on 2008-05-15
It may not work, but you could write a simple bash script and name it something like LoadPanel.sh:
```

gnome-panel;

```
Then in the main menu, go to System > Preferences > Sessions.  Then under "Startup Programs" tab, click "Add" and enter anything in the boxes except for "Command," which needs to be
```
sh ~/gnome-panel
```
Hope that helps.

---

### Post by shoaibi on 2008-05-15
&#65279;in which directory under my home dir, my gnome applets, launchers on the panels and workspace count settings are stored? I had a problem with gnome-panels. Suddenly the disappeared, even killall gnome-panels couldn't make them back, now I made a backup of .gconf, gconfd, .gnome, .gnome2, .gnome2_private, and I just want to restore my launchers, and applets,...

---

### Post by Arthur Archnix on 2008-05-15
Are you sure they are not still there and just invisible because your desktop is sized incorrectly? Have you tried creating new panels and seeing if they show up where you expect?

---

