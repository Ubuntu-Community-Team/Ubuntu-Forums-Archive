---
title: "Bad colors in firefox's video playback"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by userkwokcmscv on 2008-10-20
When video is played in firefox web browser, the colors are abnormal. Plugin is mozilla-plugin-vlc. I've also tried totem and mplayer plugins, same color error also in those.

How to fix this problem?

---

### Post by LowSky on 2008-10-20
are you using the correct video driver?

---

### Post by userkwokcmscv on 2008-10-20
> **LowSky said:**
> are you using the correct video driver?

What do you mean by correct? I use the latest GPU driver.

---

### Post by cariboo on 2008-10-20
What make and model video card are using and which driver did you install? If you have a Nvidia graphics adapter go to System-->Administration-->NVIDIA X Server Settings. If you are using an ATI card go to System-->Administration-->Hardware Drivers and report back.

Jim

---

### Post by userkwokcmscv on 2008-10-20
> **cariboo907 said:**
> What make and model video card are using and which driver did you install?
Jim

Nvidia X server config tool is found in different place than you told: Applications - System tools - Nvidia X Server Settings.

GeForce 8600M GS, driver 177.80 x86

---

### Post by userkwokcmscv on 2008-10-21
Do you know fix?

---

### Post by kahlil88 on 2008-10-21
The last time I saw videos with strange colors, it was because the system was configured to use 16-bit color instead of 32-bit. This was on a computer running Windows 98, but it couldn't hurt to double-check the color settings. Can you post a screenshot of the problem?

---

### Post by userkwokcmscv on 2008-10-21
> **kahlil88 said:**
> The last time I saw videos with strange colors, it was because the system was configured to use 16-bit color instead of 32-bit. This was on a computer running Windows 98, but it couldn't hurt to double-check the color settings. Can you post a screenshot of the problem?

GPU offers 24bit colors. Screenshot is not needed.

---

### Post by 3rdalbum on 2008-10-21
Do you get the same problem when you start VLC from the Applications menu?

It sounds to me like Nvidia still hasn't fixed the problems with their graphics drivers... sigh. In VLC, go into the Preferences and change the Video output module to something different. This should workaround the problem. Alternatively, change to the open-source nv driver; this won't give you 3D accleration, but it is relatively bug-free.

---

