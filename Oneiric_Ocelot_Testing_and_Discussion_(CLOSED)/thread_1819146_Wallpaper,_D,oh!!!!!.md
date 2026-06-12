---
title: "Wallpaper, D,oh!?!?!?!?!"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seeker5528 on 2011-08-05
Hmmmm. The wallpaper/background applet seems to be missing from the control center.

What?

Just open the image in Eye of Gnome and set the wallpaper from there you say?

Uhm. 

Yeah I can set the background from ther, but then when you want to choose between stretch, scale, etc... it tries to take you to the non-existent background applet.
:-k:-k:-k

Haven't looked for a bug report on it, I'm assuming for the moment it's been left out in Ubuntu because of some kind of failure to build. 

Later, Seeker

---

### Post by VinDSL on 2011-08-05
The only problem I've experienced with walls is...

Once I use a wall, then choose another one, it won't allow me to use the original wall again.

In other words, I can only choose a wall once.

If I want to re-use a wall, I have to rename it.  LoL!

This has been an ongoing problem since A1, and continues to be a mystery to me.

EDIT

BTW, I'm running a Live USB Image of A3, at the moment, and the background applet is present.  ;)

---

### Post by seeker5528 on 2011-08-05
> **VinDSL said:**
> Once I use a wall, then choose another one, it won't allow me to use the original wall again.

Wasn't that the thing where you were opening the background applet and clicking on the add button, and once it is added you can just select it from the list of wallpapers, so they don't give you the option to add it a second time? 

Or am I thinking of someone else? :P

If I look at the list of installed files for gnome-control-center and gnome-control-center-data it seems like the background applet should be there, but it's not showing up when I open gnome-control-center and not showing if I go to the command line and type ```
gnome-control-center background
```

For me the issue gets stranger. Appears when you set the wallpaper from EOG, it caches the image as '/home/seeker/.local/share/eog-wallpaper.jpg' and if I attempt to change the wallpaper a second time it doesn't work. If I open 'dconf-editor' and go to 'org --> gnome --> desktop --> background' and change the uri to something like 'file:///media/hda6/seeker/Wallpaper/some-wallpaper.jpg', then setting the background from EOG will work again one time.

Hmmmmmm.

If it's still borked on Monday, maybe I will look into it more.

Later, Seeker

---

### Post by seeker5528 on 2011-08-08
Hmmm. For some reason there was a file 'gnome-background-panel.desktop' in my '~/.local/share/applications/' directory, after deleting that it works fine again.

Don't understand why that prevented it from coming up when typing ```
gnome-control-center background
``` in at at the command line, but it did. :P

Later, Seeker

---

