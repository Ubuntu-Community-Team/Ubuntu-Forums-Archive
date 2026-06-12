---
title: "unity-2d, gnome-shell, workspaces"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-08-17
Maybe just an issue here, but simple to check, occurs here with both nvidia and nouveau

A default A3 or later install and login to unity-2d will show 4 workspaces when clicking on the launcher icon. 

After then installing and logging into GS - when returning to the unity-2d session only 1 WS is shown

Removing the empty  ~/.gconf/apps/metacity/%.gconf.xml and a log out/in returns the 4 WS's

Seen here with orig. and newly created user, the new user must obviously login to GS once

---

### Post by dino99 on 2011-08-17
you are not alone with this issue, i've too ;)

---

### Post by mc4man on 2011-08-17
Here is bug (messy) I filed a ways back, still don't get why removing the .xml 'fixes'
[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/826089](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/826089)

---

### Post by dino99 on 2011-08-17
Confirmed. On my side , with each boot, i need to manually load gnome-panel & metacity, as i dont use unity. Otherwise i only get a nautilus menu ;)

---

### Post by mc4man on 2011-08-18
Finally figured this silliness out
When you exit Gs it writes to ~/gconf/apps/metacity/general and sets the number of workspaces based on how many in use when exiting GS

So typically that would be 1, as in 
<entry name="num_workspaces" mtime="1313702896" type="int" value="1"/>

Then if logging into unity-2d it will use that value and only display 1

I gather that removing the .xml at the top of the dir. invalidated the whole tree or something like that
The solution would probably be don;t mis GS & unity-2d or unity-2d shouldn't read that .xml

---

