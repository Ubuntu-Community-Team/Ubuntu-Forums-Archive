---
title: "Menu bar disappeared..."
date: 2012-07-11
forum: New to Ubuntu
---

### Post by emreergecen on 2012-07-11
Hi guys,

All of sudden my menu bar on the top of screen disappeared and I don't know why. I'm using xubuntu. 

I'm looking forward to your comments.

Thanks

---

### Post by OM55 on 2012-07-11
What may happen is that either the gnome-panel crashed for some reason (extremely rare) or that you removed the top-panel accidentally.

If you have the bottom panel, you can always right-click on it (or  superbutton right click in gnome-session-fallback) and 'Add' top panel.  You will need to add to the panel again the different applets.

If you are using Gnome, you can launch it by typing in terminal:
```
gnome-panel
```

If after a reboot it is still not showing, verify you have gnome-panel installed. You can always re-install it by:

```
sudo apt-get install gnome-panel
```

Hope that helps.

---

### Post by Toz on 2012-07-11
If you are using xubuntu, note that its _not_ gnome-panel but rather xfce4-panel. Please don't install gnome-panel in a xubuntu install as it will bring in a boat load of unnecessary gnome dependencies.

Try to restart xfce4-panel:
```
xfce4-panel
```

---

### Post by Peripheral Visionary on 2012-07-12
+1 to the above, don't draw in all that extra Gnome stuff! It has enough already to make it awesome....

I don't use a panel at all. I like a nice clean desktop. Instant menu - right-click anywhere on the desktop: Bingo, there's the menu.

Looking for a minimized application that is open? Middle-click on the desktop. Bingo, there it is. Left-click on it to restore.

Who needs a panel?

But if you want one, right-click anywhere on the desktop and choose **Applications > Settings > Settings Manager**.  Then click on **Panel** and customize your own from there.  Left, right, top, bottom, multiple panels, goodies like the clock, weather widget, etc. See attached screenshot for a look at my customized Xubuntu panel on the bottom with launchers and applets just the way I liked them at the time.

---

