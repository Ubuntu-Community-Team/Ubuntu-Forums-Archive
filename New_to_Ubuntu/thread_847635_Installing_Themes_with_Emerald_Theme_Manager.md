---
title: "Installing Themes with Emerald Theme Manager"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-07-02
I went to sites such as Gnome-look.org and noticed that they had themes, however I have no clue whatsoever on how to download that theme onto my computer.

Any help?:KS

-Armaniboy- :lolflag:

---

### Post by paul101 on 2008-07-02
ok, have you got emerald installed??


look in Synaptic package manager for it

---

### Post by SunnyRabbiera on 2008-07-02
its spelled synaptic.

---

### Post by paul101 on 2008-07-02
open up emerald and install, its easy :)



also, look for compiz fusion icon, where you can easily switch window manager and switch emerald on/off

---

### Post by tjwoosta on 2008-07-02
after importing your .emerald  into the emerald theme manager you have to do this to make it switch on

press alt-f2 

in the box type ```
emerald --replace
```

if you want this to run at every login go to System-Preferences-Sessions

click add and put the command in the command box (whatever you want in the other two)

---

### Post by paul101 on 2008-07-02
^^^


personally the compiz fusion icon takes care of that for me :) . . . simple effective and easy :popcorn:

---

### Post by Armaniboy on 2008-07-02
How do I get other themes after I install the Emerald Theme Manager, enable the Sessions?

For example, if I go to gnome-look.org how would I be able to download a theme?


-Armaniboy:KS

---

### Post by tjwoosta on 2008-07-02
find your emerald theme (should be under beryl in the menu) (or you can use compiz themes)

click on it
click the download link and save to Desktop (or anywhere)
open emerald theme manager 
click import
find .emerald that you just  downloaded
press alt-f2
type emerald --replace in the box
(and it should switch on when you hit enter)

to make it start every boot add the command to System-Preferences-session




alternatively if you need a GUI i guess you can use the fusion-icon to enable emerald

to install fusion-icon

```
sudo apt-get install fusion-icon
```

then go to applications-system tools-compiz fusion icon

---

