---
title: "nvidia-settings unable to save resolution setting to xorg.conf"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by neoMAX on 2008-04-26
Each time I change the settings for my dual monitors, nvidia-settings does not save. It says "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'." I don't know how to save this setting on my own.

What I'm trying to do is save it such that on startup, I have both monitors spanning my desktop, each monitor has a resolution of 1280x1024

:confused::confused::confused:

---

### Post by sisco311 on 2008-04-26
press Alt+F2 and type:
```
gksu nvidia-settings
```
to run nvidia-settings as super user

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by neoMAX on 2008-04-26
Well I'll be damned. Thank you!

---

