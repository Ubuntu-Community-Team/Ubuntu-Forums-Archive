---
title: "Bugs? In compiz cube wallpaper settings"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by acerunner on 2008-08-22
I'm trying to set different wallpapers for each of the 4 sides of the desktop cube.

I followed instructions i found online to do this:
> 1) Alt+F2 and run gconf-editor
2) Navigate to nautilus -> preferences
3) uncheck "show desktop"
4) go into Advanced Desktop Settings and select Desktop Cube
5) under Appearance, add and arrange the desktop backgrounds that you want for each face of the cube

I have a directory in user home /Pictures/Wallpapers/ where the images I wanted to use are located. I try to add these into the background images list in CompizConfig > Desktop Cube > Appearance. However, when browsing to that folder, only some of the images show up. Is there some kind of filter on the desktop cube wallpapers that only allow you to choose certain images? or possibly a bug? I tried manually typing in the filename. But some of the photos show as the background, some don't. The background would just be black.

Of the wallpapers selected, can I format how they are displayed (ie centered, fill screen, tiled, etc)? 

Also, not sure if step 2 above was necessary (unchecking "show desktop"). I still want the desktop to show. Is there a way to do that, show desktop AND have different wallpapers? Or does one negate the other.

I also noticed that after making this change. The rotating the cube is a little buggy. After making a few rotations of the desktop, sometimes it would freeze on one desktop. After the few seconds, I can rotate again.
edit: new observation. Seems like when it freezes, if I run the mouse over either the upper or lower panel, I can rotate again.

Any help would be appreciated.

---

### Post by neurostu on 2008-08-22
Bugs in Compiz? Wow I'm totally surprised....  actually I've encountered a ton of bugs in Compiz... You should probably file a bug report or talk to the compiz guys in #compis @ irc.freenode.net

---

### Post by Thingymebob on 2008-08-22
Yes step 2 is necessary you have to stop nautilus drawing the desktop to allow compiz to do it so you can't have different wallpapers and show desktop icons

---

