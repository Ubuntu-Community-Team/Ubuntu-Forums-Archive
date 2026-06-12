---
title: "How to disable screensaver/screen lock on Lubuntu 18.04?"
date: 2020-01-08
forum: New to Ubuntu
---

### Post by ianmanning on 2020-01-08
How can I stop my Lubuntu 18.04 machine from locking the screen (and requiring password re-entry) after a timeout period?
I have unchecked the following in Preferences....Default Applications for LXSession:
- Power Manager
- Screen Locker
But the screen still locks after a few minutes
???

---

### Post by Dennis N on 2020-01-08
Use settings in: 
Menu > Preferences > Power Manager > Display Tab
and/or
Menu > Preferences > Power Manager > Security Tab

To stop screen blanking, sleep and timed switch off, move all three sliders in Display Tab to the far left which is the "never" setting. 
To prevent locking screen, use the Security Tab, and uncheck the "lock screen when system is going to sleep" box.

---

### Post by guiverc on 2020-01-08
Also check Preferences->Screensaver and the "Lock Screen after" check box (*to ensure it's not ticked*).

You may/may-not have xscreensaver active; if it is, it can cause locked screen  (screensaver isn't obvious if it's set to "Blank Screen Only")

---

