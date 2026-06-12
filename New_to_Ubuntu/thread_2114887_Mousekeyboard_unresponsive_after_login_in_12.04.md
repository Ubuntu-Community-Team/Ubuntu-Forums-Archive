---
title: "Mouse/keyboard unresponsive after login in 12.04"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by cuatro on 2013-02-11
After successfully logging in, I can't input anything using my keyboard and while I can move the mouse, I can't select anything with it. Logging in as a guest has the same problem. Both the keyboard and mouse work after booting in recovery mode, but not in a normal Ubuntu boot, so I don't believe it's a hardware problem. I have been running Ubuntu since August and haven't had this problem until today.

I dual boot Ubuntu 12.04 with Windows 7 on an Asus N53 laptop.

Suggestions?

---

### Post by MiantCub on 2013-02-11
I've also experienced a problem with the touch-pad, tap-to-click turned back on, and the option to turn it off has disappeared from the mouse and touch-pad menu.

---

### Post by U202E on 2013-02-11
You can login, right? So you're mouse+keyboard work at the login screen.
quite strange...

some possible solutions:
ctrl+alt+f1 -> login there with the cli -> sudo apt-get install --reinstall lightdm unity
if nothing works: sudo apt-get install gdm/kdm =try another login manager.

there was something like a hardware+sound+video test in the settings or so, maybe you would like to try that.

---

