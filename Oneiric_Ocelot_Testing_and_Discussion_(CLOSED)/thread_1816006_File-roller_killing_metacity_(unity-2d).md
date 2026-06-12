---
title: "File-roller killing metacity (unity-2d)?"
date: 2011-08-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-08-01
Please try the following running Unity 2D:

1. Create a new empty file (e.g., right click on your desktop &#8594; "Create New Document" &#8594; "Empty Document").
2. Right click on the file and choose "Compress...".
3. Now choose ".zip" and set a password under "Other Options" &#8594; "Create".
4. Right click the compressed file &#8594; "Extract Here".
5. Enter the password and click "Ok".

BOOM - the window decorations should be gone now (you can recover by Alt+Ctrl+F1, logging in, running "(DISPLAY=:0.0 metacity &)").

---

### Post by lucazade on 2011-08-01
confirmed. what a nice bug :)

---

### Post by MacUntu on 2011-08-01
Thanks! Yeah, funny thing, but having no window decorations is bad (at least for beginners that do not know about tty1).

Just sifting through the SIGABRT backtraces on LP. Will post a bug report soon.

**Bug report:**
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/819286](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/819286)

Feel free to confirm, mark yourself as affected, subscribe. :)

---

### Post by 3rdalbum on 2011-08-01
I ran into a "no window decorations" bug today, although I don't know exactly what caused it. Funnily enough, the system's still fairly usable even with no window decorations - you can still focus windows and type into them and stuff with no window decorations. In the past it always used to force me to either reboot or get them back before I could actually do anything productive, but it appears more robust now.

---

### Post by sgage on 2011-08-01
> **3rdalbum said:**
> I ran into a "no window decorations" bug today, although I don't know exactly what caused it. Funnily enough, the system's still fairly usable even with no window decorations - you can still focus windows and type into them and stuff with no window decorations. In the past it always used to force me to either reboot or get them back before I could actually do anything productive, but it appears more robust now.

Every so often I run into the same thing, but I could not possibly say what caused it, or reproduce it on demand. I usually logout/login to fix it, but the 'DISPLAY=:0.0 metacity &' gambit works, too.

---

### Post by MacUntu on 2011-08-01
> **3rdalbum said:**
> I ran into a "no window decorations" bug today, although I don't know exactly what caused it. Funnily enough, the system's still fairly usable even with no window decorations - you can still focus windows and type into them and stuff with no window decorations. In the past it always used to force me to either reboot or get them back before I could actually do anything productive, but it appears more robust now.

Doesn't work in all cases for me, e.g. for this bug I can focus things but nothing else works.

---

