---
title: "[SOLVED] Getting Back Bottom Pannel"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-01
I deleted the bottom panel where all of my programs go when I minize them. How do I get it back?

---

### Post by vikramaditya on 2008-08-01
You can restore Gnome Panels to default, thusly.  Open Terminal & copy paste the following commands...hit your "Enter" key after each one.
```
gconftool-2 --shutdown
```
Then enter the next command:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```
Your panels will reappear after the last action.

---

### Post by kspncr on 2008-08-01
> **diego898 said:**
> I deleted the bottom panel where all of my programs go when I minize them. How do I get it back?

You can right-click on the top panel and click "add new panel" and it will put the panel back on the bottom. Then right click on the bottom panel and click "add to panel" to re-add the things that were on the panel (eg, the deleted items folder, workplace switcher, etc.)

---

### Post by diego898 on 2008-08-01
> **kspncr said:**
> You can right-click on the top panel and click "add new panel" and it will put the panel back on the bottom. Then right click on the bottom panel and click "add to panel" to re-add the things that were on the panel (eg, the deleted items folder, workplace switcher, etc.)


Will that add the ability for my programs to go back there?

---

### Post by kspncr on 2008-08-01
I'm not sure what you mean. You want to minimize your windows to the bottom panel? Choose "window list" from the "add to panel" list and you will be able to minimize.

---

### Post by SunnyRabbiera on 2008-08-01
> **kspncr said:**
> I'm not sure what you mean. You want to minimize your windows to the bottom panel? Choose "window list" from the "add to panel" list and you will be able to minimize.

right, the windows list is our equivalent to the windows taskbar.

---

### Post by navic101 on 2008-10-12
Hi thanks for the rapid responses. Alt tab has allowed me to view all the open windows and close and view them. However it would be nice if they were tabbed at the bottom of the screen for me to view without alt tab.

Any suggestions?

---

