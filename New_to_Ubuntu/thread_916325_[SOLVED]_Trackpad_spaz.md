---
title: "[SOLVED] Trackpad spaz"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Crayboff on 2008-09-10
I just installed Ubuntu 8.04.01 (Hardy Heron) on my Dell Inspiron 1521. I got CompizConfig and turned on Desktop Cube, Expo and Rotating Cube. It was working perfectly. Unfortunately, literally just a couple minutes ago, I downloaded FirstClass (an email client for my school) which shouldn't mess with anything and I moved my mouse and must of touched the scroll portion of my touchpad and it switched workspaces. I checked Keyboard Shortcuts and CompizConfig, but I can't find any reason for this to be happening all of the sudden. This didn't happen before and it is getting very annoying. Is there anyway for a noob like me to stop it from switching workspaces every time i touch the scroll part of my touchpad? :confused:

---

### Post by rossjman1 on 2008-09-10
If you scroll on the desktop it automatically switches desktops, I'm not at a GNOME computer, so I don't know exactly were the option is to disable the feature.

---

### Post by Crayboff on 2008-09-10
Ah, well atleast it's not just a recent thing, but does anyone know how to disable that feature?

---

### Post by rossjman1 on 2008-09-10
Try looking in the Compiz Settings Manager.

---

### Post by Crayboff on 2008-09-10
I did, I can't find anything determining the scroll function to act as a shortcut.

---

### Post by rossjman1 on 2008-09-10
You can disable touchpad scrolling completely by going to System > Preferences > Mouse > Touchpad, but I'll look for the desktop switching setting.
Couldn't find it, but found a workaround here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150443](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150443)
> If you load compizConfig and then unselect the viewport switcher plugin, the desktop switching will start working with the mousewheel.
So, enabling the viewport switcher plugin in Compiz will override GNOME's default setting.

---

### Post by Crayboff on 2008-09-10
Oh dang, it worked. \\:D/

For future reference here is what happened:

**Problem:** When I hovered my cursor over the desktop and I touched the scroll on my touchpad, it switched workspaces.

**Solution:** Open CompizConfig and select Preferences. Click the Plugin tab and unselect auto plugin sorting. Find "vpswitch" and move it to the disabled plugin list. That worked for me. 
[COLOR="Red"]**I do not know if this will cause any backfires and I sure hope it doesn't screw up my computer in any way**[/COLOR]

:guitar:

---

### Post by Crayboff on 2008-09-10
Update: just found this site [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/175986]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/175986") which talks all about this problem.

---

