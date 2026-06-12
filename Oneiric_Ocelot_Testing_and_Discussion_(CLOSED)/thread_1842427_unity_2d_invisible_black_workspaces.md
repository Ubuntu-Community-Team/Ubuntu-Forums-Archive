---
title: "unity 2d invisible black workspaces"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by madjr on 2011-09-11
anyone else has this problem in unity 2d?

workspaces went totally black after some updates

---

### Post by lucazade on 2011-09-11
> **madjr said:**
> anyone else has this problem in unity 2d?

workspaces went totally black after some updates

here the workspace switcher is still working correctly.
(just a weird space if you disable launcher autohide.. but this is another old issue!)

---

### Post by mc4man on 2011-09-11
Possibly your issue?
If you happen to login to gnome-shell when logging out it will write a gconf key setting the # of workspace to however many were open when exiting gnome-shell

unity-2d will then read this key and only show the num value

see screen where GS has set to 1, so unity-2d will only use 1
(you can adjust there if desired 
known bug, not yet addressed

Edit: - to further some info
by default unity-2d does not use that key, it is not set in ~/.gconf/apps/metacity in a default install
It will however use the value of that key if it does exist
gnome-shell does create the key & value, but doesn't use it on login

---

### Post by madjr on 2011-09-11
> **mc4man said:**
> Possibly your issue?
If you happen to login to gnome-shell when logging out it will write a gconf key setting the # of workspace to however many were open when exiting gnome-shell

unity-2d will then read this key and only show the num value

see screen where GS has set to 1, so unity-2d will only use 1
(you can adjust there if desired 
known bug, not yet addressed

Edit: - to further some info
by default unity-2d does not use that key, it is not set in ~/.gconf/apps/metacity in a default install
It will however use the value of that key if it does exist
gnome-shell does create the key & value, but doesn't use it on login

i dont have gnome-shell installed

---

### Post by mc4man on 2011-09-11
Well then that wouldn't be your issue - 
if you open up gconf and set that key to 4 do you get 4 spaces?

---

### Post by madjr on 2011-09-11
> **mc4man said:**
> Well then that wouldn't be your issue - 
if you open up gconf and set that key to 4 do you get 4 spaces?

i have all 4 spaces, the problem is that they are all black and dont use the wallpaper anymore, but i can see the apps on each black space (i'll upload a screen soon when am back in oneiric)

---

### Post by mc4man on 2011-09-11
Sorry -very poor reading comprehension on my part, maybe search current unity-2d bugs on LP

---

