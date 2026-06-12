---
title: "HUGE wine issue (pun intended)"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by taith on 2008-07-02
hey everyone

when i open up my wine config, or any wine based programs... everything is HUGE

i'll attach a picture so you can see what i mean

i have tried reinstall/complete reinstall... neither has made any effect

---

### Post by someonestolemyname on 2008-07-18
Hmm... Wine settings seem screwed. Try "apt-get remove wine --purge" and reinstall. Or, w/o uninstalling, just 'rm -rf ~/.wine'. Either should (hopefully) fix your problem

---

### Post by Dark_Stang on 2008-07-18
Go into the wine configuration, click the graphics tab, and check what your screen resolution is set at. Adjust the slider accordingly. If that's set at 96 dpi, let us know.

---

