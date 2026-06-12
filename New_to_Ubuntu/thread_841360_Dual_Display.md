---
title: "Dual Display"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by dinomite89 on 2008-06-26
Okay,

Ive read a few threads on this subject but not really understood them,

Because i dual boot between vista (x64) and Ubuntu (8.04) i will explain my problem,

When in vista i have dual display set up as following,

A ViewSonic 28" (1900x1200) LCD on my left and an ACER 19" (1280x1024) display on my left, i was running UltraMon and had a task bar setup to span across the screen 2 different wallpapers,

If i boot straight to Linux with out changing anything after the loading bar both monitors flash out of range, i have to unplug the 19" to boot up.

Is it possible to use 2 monitors in this configuration, and is there a Linux version of UltraMon For the task bar setup?

---

### Post by fatality_uk on 2008-06-27
If you know the refresh rates and rex for both screens, go into System->Preferences->Screen resolution in Ubuntu and you can set the relevant information there for both screens. It should auto detect, but there is a detect displays button there.

---

### Post by benste on 2008-06-27
if you've got a nvidia card use
nvidia-settings

there you can "create" a new xorg.conf
including xinerama configuration for the two monitors

---

### Post by bodhi.zazen on 2008-06-27
run nvidia-settings as root to save you changes :

```
gksu nvidia-settings
```

---

