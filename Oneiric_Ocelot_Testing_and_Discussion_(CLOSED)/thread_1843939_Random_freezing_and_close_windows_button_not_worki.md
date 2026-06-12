---
title: "Random freezing and close windows button not working"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-09-14
Compiz says it's crashed regularly I guess everybody is getting this. I've seen a bug report.

I'm getting random freezing where nothing responds or somethings responds. Occasionally have to ctrl alt delete then log back in.

Close button does not work randomly too. I have to say wobble a window or start another app to regain control.

Nvidia-current is active and this is a Unity 3d session I guess.

If I minimise Firefox it wont come back up I have to activate say a terminal or other app and then it will come up.

Any advice, nothing in logs

---

### Post by dino99 on 2011-09-14
i get that all the time:
log as classic, open a terminal, then freeze: need to log out
log as classic, reload metacity with a launcher, open a terminal: no freeze

---

### Post by philinux on 2011-09-14
> **dino99 said:**
> i get that all the time:
log as classic, open a terminal, then freeze: need to log out
log as classic, reload metacity with a launcher, open a terminal: no freeze

Sounds as if the compiz bug is to blame then. I forget the bug number.

---

### Post by alexvy13 on 2011-09-14
I get this too along with the launcher not showing. Didn't have this problem till the last couple of updates

---

### Post by fillmont on 2011-09-14
I have also been experiencing non-reponsive windows. I've found that "restarting" the program through the launcher restores responsiveness for a bit. 

When Unresponsive, I can click into the actual program and do things, but none of the Minimize/Maximize/Close buttons, nor the actual menu bar, seem functional.

---

### Post by mc4man on 2011-09-14
Not seeing any compiz crashes here of any consequence - there still is an occasional one that will go here - 
[https://bugs.launchpad.net/ubuntu/lucid/+source/libx11/+bug/507062](https://bugs.launchpad.net/ubuntu/lucid/+source/libx11/+bug/507062)
I'd open /var/crash and see what's in there (not a bad idea to clear that folder every once & a while, I do every day
sudo rm /var/crash/*.crash

If minimizing windows on unity (3d), then until fixed I'd suggest opening ccsm and disabling in unity plugin > switcher the 'Show minimized windows in switcher' option 
[bug here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/847967")

---

