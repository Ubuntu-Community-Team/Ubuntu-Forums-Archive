---
title: "HOWTO Easiest Xgl/Compiz setup yet"
date: 2006-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by dyssident on 2006-07-22
I found [this tutorial]("http://tazforum.thetazzone.com/viewtopic.php?t=2189") at the Taz Forum. I followed the instructions and had Xgl/Compiz working like a charm in about 5 minutes.

Only one correction: when I first logged in to Xgl, the window manager aparently wasnt running. I went back go the default Gnome desktop and ran

```
compiz --replace gconf & 
```

I logged back into Xgl and it worked perfectly. 

Only 8MB more ram is consumed, and there is very little noticeable slowdown when manipulating windows even on my bottom of the line laptop.

For refrence, heres my system:
Toshiba Satellite M55-S1001
1.6 GHz Celeron M / 192 MB Ram
ATI Radeon Xpress 200M 32MB

---

