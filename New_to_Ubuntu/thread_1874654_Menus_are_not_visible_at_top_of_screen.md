---
title: "Menus are not visible at top of screen"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by orygunjon on 2011-11-03
Unity menu at left of screen appears partially, but cannot see menus at top at all. I think it's is a display size issue of some kind.  The menus are there and I can access them by mousing above the displayed screen.

Nvidia GT430 video
Samsung Syncmaster 2450 24" monitor
HDMI connection

Have installed/reinstalled the Nvidia proprietary drivers.
Rebooted after install

Ubuntu 11.10

---

### Post by wolfen69 on 2011-11-03
Do
```
gksudo nvidia-settings
```
and check your resolution settings.

---

### Post by orygunjon on 2011-11-03
Screen resolution 1920x1080 (160x90 millimeters)
305x305 dots per inch

The 1920x1080 is the same resolution as the Windows PC I have hooked to this monitor via DVI

---

### Post by anewguy on 2011-11-03
The way things work with Unity running is that the menu that shows such things as "File View Edit" etc., depending on the application, are covered by the Window title until you mouse over it - then the menu shows.  Right now this is normal.  If the top line is visible  - you should see the "power button" in the top right, for example - then that part of your resolution is fine.  The mouse-over to show the menu is normal.

I'm not sure about your Unity menu popping in from the left only partially shows.  Perhaps you could take a screen snapshot of both and post them back here so we can see more.  Use "screenshot" in the topmost unity button (you'll probably need to put it in the "search" field).  Just set it to capture the entire desktop and give it a 2 second or so delay - that way it will take the snapshot after the screenshot window closes.

Dave ;)

---

### Post by orygunjon on 2011-11-06
Definately an Nvidia driver problem.

Switched to onboard ATI graphics and problem resolved.

Uninstalled and reinstalled Nvidia driver and it didn't help.
Probable solution is blacklist "Noveau", but I don't want to go that deep into Linux.

---

### Post by bluexrider on 2011-11-06
Try the Xorg or Mesa drivers?

---

