---
title: "[SOLVED] Compiz wont maximize windows"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by xdarkgokux on 2008-10-27
hi guys, my compiz is kinda messed up.. like when compiz is runing the windows in maximized mode dont fill the screen but metacity does..i dono how to fix this

---

### Post by Crafty Kisses on 2008-10-27
It sounds to me like your display size (i.e. the dimensions of your desktop) might not be detected/reported correctly (or perhaps it has been set incorrectly). The behavior showed in your screenshot possibly could occur if a display output were set to be in the top-left corner and at a size smaller than the full screen.

It's also possible (and perhaps easier) to open **CCSM** and change the settings in **General Options -> Display Settings**. Is the Detect Outputs option enabled? If not, try enabling it. If it is already enabled, then disable it and set the following under Outputs (by editing the default line already in the list):

```
1024x768+0+0
```

---

### Post by xdarkgokux on 2008-10-27
Hey thanks a lot for the fast reply..it turns out it was just AWN.. i set it to NOT allow maximizde windows to cover it..so that msessed it up..thx tho

---

### Post by Crafty Kisses on 2008-10-27
Oh OK good deal then man. :)

---

