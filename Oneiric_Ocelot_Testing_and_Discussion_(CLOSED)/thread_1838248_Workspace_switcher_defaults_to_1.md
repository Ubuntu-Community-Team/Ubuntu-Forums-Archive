---
title: "Workspace switcher defaults to 1"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-09-03
Suddenly the workspace switcher shows only one square. Right clicking brings up the dialog and I increase the number to 4. Close and it resets to 1. 

Also right clicking on the bottom panel open program icons opens a menu but the options - move to workspace left etc. are missing.

Michael

---

### Post by dino99 on 2011-09-03
i've this issue too

metacity --replace &

---

### Post by mc4man on 2011-09-03
While probably not the cause of your issue based on description **If** you log in to gnome-shell then the number of Ws;s available in unity-2d and probaly gnome fallback (classic) will be altered based on how many were open when exiting gnome-shell (typically 1

current on that
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/826089](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/826089)

---

### Post by Yumi on 2011-09-04
It only happens when I log into "Gnome classic". When I log into "Gnome classic (no effects) all workspaces show as I am used to.

Michael

---

### Post by dino99 on 2011-09-04
> **Yumi said:**
> It only happens when I log into "Gnome classic". When I log into "Gnome classic (no effects) all workspaces show as I am used to.

Michael

hm, on my system i use gnome-classic without effects, and i need to load metacity, see my previous post, to get more than 1 workspace and to be able to move/resize windows.

---

