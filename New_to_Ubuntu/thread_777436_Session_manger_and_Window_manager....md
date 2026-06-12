---
title: "Session manger and Window manager..."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Fatal Equinox on 2008-05-01
Hello, 

Basics:  Hardy Heron Ubuntu 8.04 via wubi, Sony Vaio VGN-AR170g Centrino duo works rather well. That is  when i don't screw things up. 

I was messing around a with the session manager a little while ago..(all i really did was check  "automatically remember  running applications when logging out") and some how disabled the window manager on startup or something.  Not quite sure myself. Anyway when i start up i only have one desktop and an x as a cursor... which is all fine(going to start compiz fusion anyway) but Firefox pops up half on and off the screen making it impossible for me to access the application tab and/or close Firefox without a force quit.

Also as a side effect(i believe it is related) my screen saver doesn't activate properly, either just goes to a black screen or is underneath a dimmed screen. 

Any insight on what exactly session manger is for would also help.  Thank you to anyone willing to help.

*Edit*  This was before the full release on the 24th.... if that helps any.

---

### Post by brownknight on 2008-05-01
> **Fatal Equinox said:**
> Hello, 

Basics:  Hardy Heron Ubuntu 8.04 via wubi, Sony Vaio VGN-AR170g Centrino duo works rather well. That is  when i don't screw things up. 

I was messing around a with the session manager a little while ago..(all i really did was check  "automatically remember  running applications when logging out") and some how disabled the window manager on startup or something.  Not quite sure myself. Anyway when i start up i only have one desktop and an x as a cursor... which is all fine(going to start compiz fusion anyway) but Firefox pops up half on and off the screen making it impossible for me to access the application tab and/or close Firefox without a force quit.

Also as a side effect(i believe it is related) my screen saver doesn't activate properly, either just goes to a black screen or is underneath a dimmed screen. 

Any insight on what exactly session manger is for would also help.  Thank you to anyone willing to help.

*Edit*  This was before the full release on the 24th.... if that helps any.

Can you go to >Systems>Preferences>Sessions? then from the session options unclick the remember session on log-out. If that's not possible, then open a terminal and type gnome-session-properties. That should open up the session GUI for you to correct.

---

### Post by Fatal Equinox on 2008-05-01
i've previously unchecked that already thinking that it should fix it, but no it still starts up that way. :-/

---

### Post by brownknight on 2008-05-01
> **Fatal Equinox said:**
> i've previously unchecked that already thinking that it should fix it, but no it still starts up that way. :-/

Ok. Then can you try looking into the sessions > startup programs. See what programs are supposed to run at startup. Firefox shouldnt be there so you can  remove or untick it so are other programs that was never there to begin with. Then you have to log-out and logback in to see the changes.

---

### Post by Fatal Equinox on 2008-05-01
> **brownknight said:**
> Ok. Then can you try looking into the sessions > startup programs. See what programs are supposed to run at startup. Firefox shouldnt be there so you can  remove or untick it so are other programs that was never there to begin with. Then you have to log-out and logback in to see the changes.

I actually don't see firefox in the startup programs field.... unless it is like within one of these:

Blue Tooth Manager - disabled
Check for new hardware drivers - enabled
Evolution Alarm Notifier - enabled
Network Manager - enabled
Power Manager - enabled
Print Queue Applet - enabled
PulseAudio Session Management - enabled  culprit maybe?
Tracker - enabled
Tracker Applet - enabled
Update Notifier - enabled
User Folder update - enabled
Visual Assistance - enabled
Volume Manager - enabled

That is the total of the startup program tab under session....

---

### Post by Fatal Equinox on 2008-05-02
any body else with advice?

---

### Post by Sand Lee on 2008-09-01
Try to get your setup as normal as possible (as it would be during a usual startup), then click the "Remember currently running applications" button again.

---

### Post by Shakaboom on 2008-09-12
I have EXACTLY the same problem, which is REALLY annoying. I already posted on the Compiz forum, but they weren't able to help me. I really hope someone here can!

---

### Post by expelledboy on 2009-04-27
I just started having this problem aswell..
Does anyone have a solution?
If not I may have to reinstall the OS!
I though only windows had to reinstalled once every 6 months :(

EDIT: well I reinstalled..

---

