---
title: "[SOLVED] Can i ve a different background image on each workspace?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by LastWho on 2008-10-16
hi
i dlike to know if i could? and how please?
thanks

---

### Post by earthpigg on 2008-10-16
ive never heard of that being done in ubuntu, nor seen any screen shots to that effect. :\

---

### Post by tjwoosta on 2008-10-16
if you are using compiz fusion it is possible to get a different wallpaper on each side workspace, but it is not possible to have desktop icons if you do this

first you would open ccsm and set four different wallpapers (either with the wallpaper plugin, if you have one, or with the desktop cube plugin if you dont)

now the wallpapers you selected wont show up until you disable nautilus from drawing the desktop

to do that do this

press alt-f2 and type gconf-editor in the box

navigate to apps-nautilus-preferences and uncheck the box that says show desktop on the right

now nautilus should stop drawing the desktop (including the icons) and compiz should take over


to undo the process you will need to replace the check mark on show desktop and log out then back in again





if you dont have compiz it is still possible to get four different wallpapers witha program called wallpapoz


> ive never heard of that being done in ubuntu, nor seen any screen shots to that effect. :\

you must not look very hard    (google "4 different wallpapers" and you will see a bunch)

---

### Post by earthpigg on 2008-10-16
o. cool. sometimes it's good to be wrong :)

---

### Post by LastWho on 2008-10-16
Hola, danke shone!!!

please about disabling nautilus or compiz, is it the same as using: 
```
metacity --replace
```

---

### Post by tjwoosta on 2008-10-17
metacity --replace replaces compiz window decorator with the standard metacity window decorator

thats usefull for disabling compiz in order to play games

that is not the same thing as disabling nautilus from drawing the wallpaper

---

### Post by Keen101 on 2008-10-17
[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

you would have to probably run it every time at startup though. >System >Preferences >Sessions. and the add the command "daemon_wallpapoz"

I think KDE has the option built in.

---

### Post by HorryMorry on 2008-12-27
> **tjwoosta said:**
> if you are using compiz fusion it is possible to get a different wallpaper on each side workspace, but it is not possible to have desktop icons if you do this

first you would open ccsm and set four different wallpapers (either with the wallpaper plugin, if you have one, or with the desktop cube plugin if you dont)

now the wallpapers you selected wont show up until you disable nautilus from drawing the desktop

to do that do this

press alt-f2 and type gconf-editor in the box

navigate to apps-nautilus-preferences and uncheck the box that says show desktop on the right

now nautilus should stop drawing the desktop (including the icons) and compiz should take over


to undo the process you will need to replace the check mark on show desktop and log out then back in again





if you dont have compiz it is still possible to get four different wallpapers witha program called wallpapoz




you must not look very hard    (google "4 different wallpapers" and you will see a bunch)

Thank you, I know this is a bit late but I just made the swap and this really helped.

---

