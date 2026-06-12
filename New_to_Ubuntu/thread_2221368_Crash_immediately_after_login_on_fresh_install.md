---
title: "Crash immediately after login on fresh install"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by Doug_McCausland on 2014-05-01
I'm using an Asus EEE 1215b notebook with a fresh install of Ubuntu 12.04. When I log in as myself or as guest I immediately get a black screen followed by what looks to be a copy of the login screen, followed by flash of black, then the wallpaper.  I sometimes am told that compiz has crashed and I tell it to try to recover. I have to open a terminal session using ctl-alt T as the entire sidebar is gone. My keyboard won't even work at that point after the terminal is opened and if the screensaver engages I can't unlock as the keyboard won't work then either.  I've read about issues with nvidia drivers not playing nice with compiz, but I'm not sure how to fix this issue, or if the issue can be fixed in recovery mode, where I have a little more room to run commands before another crash. Any solutions would be helpful.  I've tried reinstalls 3 times today with no luck.  Also, let me know if you need me to get additional data.

---

### Post by Doug_McCausland on 2014-05-01
I tried several fixes including resetting unity and compiz, no dice.  What worked was going into recovery mode, opened a terminal and typed:
```
sudo apt-get install nvidia-current
```
  Rebooted and I was fixed.

---

