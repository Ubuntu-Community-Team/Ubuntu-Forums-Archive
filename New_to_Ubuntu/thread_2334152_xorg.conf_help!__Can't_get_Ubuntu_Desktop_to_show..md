---
title: "xorg.conf help!  Can't get Ubuntu Desktop to show.. &quot;Cannot Display This Video Mode&quot;"
date: 2016-08-16
forum: New to Ubuntu
---

### Post by eagletalontim on 2016-08-16
I am really needing some help if at all possible!  I can't seem to get my PowerEdge 2650 to display Ubuntu Desktop 16.04 properly.  The video card is apparently an ATI Rage 128 but I can't seem to set the xorg.conf properly to display the desktop.   I can't post the xorg.conf unless I hand type the whole thing on here :(

---

### Post by CatKiller on 2016-08-16
If you press Ctrl-Alt-F1 you'll switch to a text login. Tweak or rename your xorg.conf from there and then reboot with *sudo shutdown -r now*.

If you have another machine available, using SSH is an option, too.

---

### Post by eagletalontim on 2016-08-16
I have renamed the conf file, deleted the file, rebuilt the file, and restarted multiple times.  The best I can get is the background image and a cursor.  I think I will just give up on this server and get a NAS...

---

### Post by CatKiller on 2016-08-16
Well, that graphics card is pretty bad. You might be better with an Etch-A-Sketch.

Background image and a cursor is pretty good, actually. It means that X has started properly and the display is at the right resolution. Perhaps the problem is higher up the stack?

---

