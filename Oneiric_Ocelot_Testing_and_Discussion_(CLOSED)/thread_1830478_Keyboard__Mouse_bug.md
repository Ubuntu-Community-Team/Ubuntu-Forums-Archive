---
title: "Keyboard / Mouse bug?"
date: 2011-08-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by RJ12 on 2011-08-21
So, one of my favorite features about GNOME/Ubuntu is that when I'm typing, it disables my Trackpad and when I stop, it enables it again. But for some reason, the threshold seems like it's been turned up big time. So when I'm typing I have to wait about 4 seconds for it to enable again. This is getting really annoying. What package would I file a bug as, or am I just missing a setting to change. In Ubuntu 11.04 and below, it's been perfect. I suspect it has something to do with GNOME 3?

---

### Post by ventrical on 2011-08-21
Yep !! I got it too. I opened LibreOffice .. started typing and tried to move mouse on track pad and it froze right up !

---

### Post by mc4man on 2011-08-21
The default 'lock' time has been upped from 0.5 sec to 2 sec.
It's unlikely this will be changed so - 
Build gnome-settings-daemon source and change back
Turn off the touchpad lock in mouse settings
Get used to it
Hope someone ppa's a reverted g-s-d

If curious - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763)

---

### Post by RJ12 on 2011-08-21
This is stupid! Who changed it?! It was seamless when it was at .5, I didn't notice it at all, and now it's very noticeable, lets hope someone fixes it, or as the poster above me said, someone make a PPA. Which if isn't hard enough to make (with the fixed gnome-settings-daemon package), I would be happy to do it. But I have never really done anything like that, and probably would be a little challenging to me...

EDIT: So it's C... I have little experience with C, but I can change a variable. Although I can't find the variable...

P.S thats a lot of code!

---

### Post by mc4man on 2011-08-21
the edit is simple - currently
```
--- gnome-settings-daemon-3.1.5.orig/plugins/mouse/gsd-mouse-manager.c
+++ gnome-settings-daemon-3.1.5/plugins/mouse/gsd-mouse-manager.c
@@ -533,7 +533,7 @@ set_disable_w_typing (GsdMouseManager *m
 
                 args[0] = "syndaemon";
                 args[1] = "-i";
-                args[2] = "2.0";
+                args[2] = "0.5";
                 args[3] = "-K";
                 args[4] = "-R";
                 args[5] = NULL;

```

---

### Post by RJ12 on 2011-08-21
> **mc4man said:**
> the edit is simple - currently
```
--- gnome-settings-daemon-3.1.5.orig/plugins/mouse/gsd-mouse-manager.c
+++ gnome-settings-daemon-3.1.5/plugins/mouse/gsd-mouse-manager.c
@@ -533,7 +533,7 @@ set_disable_w_typing (GsdMouseManager *m
 
                 args[0] = "syndaemon";
                 args[1] = "-i";
-                args[2] = "2.0";
+                args[2] = "0.5";
                 args[3] = "-K";
                 args[4] = "-R";
                 args[5] = NULL;

```


Which argument would I change?... Nvm...

---

### Post by mc4man on 2011-08-22
You won't need to build - as of the new g-s-d the time has been reverted

> gnome-settings-daemon (3.1.5-0ubuntu3) oneiric; urgency=low

  * debian/gnome-settings-daemon.gsettings-override:
    - Enable GConf bridge plugin by default 
  * debian/patches/10_smaller_syndaemon_timeout.patch:
    - Use a smaller timeout for syndaemon (LP: #801763)

---

### Post by ricsi-pontaz on 2011-08-22
Great news! This is very annoying.

---

### Post by mc4man on 2011-08-22
Was an interesting change - the 1st. attempt to build the new g-s-d that failed earlier wasn't patched, the re-attempt did (that build also failed but the new g-s-d should be coming soon

---

### Post by ventrical on 2011-08-22
> **mc4man said:**
> Was an interesting change - the 1st. attempt to build the new g-s-d that failed earlier wasn't patched, the re-attempt did (that build also failed but the new g-s-d should be coming soon


Thanks for staying at this one.

---

### Post by mc4man on 2011-08-24
You should see a new g-s-d available today that has the shorter time(0.5

---

### Post by ventrical on 2011-08-24
Much better .. thanks !

---

