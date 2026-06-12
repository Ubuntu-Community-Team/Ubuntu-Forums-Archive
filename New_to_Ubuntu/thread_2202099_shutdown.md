---
title: "shutdown"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by trav9595 on 2014-01-27
I played around with some unrelated settings and now my shutdown doesnt work correctly. It delays and stalls for a minute before it shuts down.
Anyone know a script or something to repair it or better a desktop button that does a 1 clik shutdown fast on the desktop.  xfce..

---

### Post by DuckHook on 2014-01-27
Your delay would seem to be the result of the settings you played with. Only you know what those were. It is likely that if you reverse those changes, it would get you back to your original state. Otherwise, I'm aware of no magic wand in Linux or Ubuntu that can reverse unknown changes. If this is really bugging you and you don't remember what settings you changed, then backing up your data and reinstalling is always a relatively easy option in Linux.

FWIW, I always keep a detailed log of changes that I make to settings and config files in Linux. It is easy if you get into the habit. Just create a simple text file on your desktop called "system_changes" and manually update it every time you make a change. This way, you can always reverse what you do.

---

### Post by trav9595 on 2014-01-27
anyone got a script for a shutdown button?

---

### Post by whitesmith on 2014-01-27
My part:```
shutdown -H now
```Your part: Create a launcher for this code snippet.

---

### Post by trav9595 on 2014-01-30
That code doesnt work. gee what a surprise. Anyone else know launcher code for shutdown that does work. Preferable all the code to make a launcher 
and place it on the desktop that bypasses the idle problem and just shuts down the stupid computer.

---

