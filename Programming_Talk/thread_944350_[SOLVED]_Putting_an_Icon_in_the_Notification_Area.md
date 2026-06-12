---
title: "[SOLVED] Putting an Icon in the Notification Area"
date: 2008-10-11
forum: Programming Talk
---

### Post by Jesdisciple on 2008-10-11
The main thing missing from Sunbird for me is the MinimizeToTray addon, so I wonder what's involved in putting an icon in the Notification Area.  I plan to write a Linux version of MinimizeToTray.  (I know Kontact uses the Notification Area, but it has a bigger problem.)

Thanks!

---

### Post by cl333r on 2008-10-11
I think what you mean is also called "system tray". Google for "gtk system tray".
Here's an example I found:
[http://yettocome.blogspot.com/2007/08/gtk-system-tray-icon-example.html](http://yettocome.blogspot.com/2007/08/gtk-system-tray-icon-example.html)

---

### Post by Jesdisciple on 2008-10-11
(Please bear with the C newbie.)```
test.c:1:21: error: gtk/gtk.h: No such file or directory
```I Googled that error and found that I need to install GTK - but which package?  And should I get GTK2?

---

### Post by Sam on 2008-10-11
Have you tried [alltray](apt://alltray) ?

---

### Post by geirha on 2008-10-11
> **Jesdisciple said:**
> (Please bear with the C newbie.)```
test.c:1:21: error: gtk/gtk.h: No such file or directory
```I Googled that error and found that I need to install GTK - but which package?  And should I get GTK2?

You find header files (*.h) in -dev packages.
```
aptitude search gtk.*-dev
```

Lots of packages on that search, but you most likely need either [libgtk1.2-dev](apt://libgtk1.2-dev) or [libgtk2.0-dev](apt://libgtk2.0-dev)

---

### Post by Jesdisciple on 2008-10-11
No, I haven't heard of alltray before...  Does it work for just any program?  EDIT:  I found it and shall try it; thanks!  (Where are the instructions?)

I installed both packages and still get the error...?  :-|

---

### Post by gomputor on 2008-10-11
Do you include the gtk library when you compile it? ie
gcc `pkg-config --cflags --libs gtk+-2.0` test.c -o test

---

### Post by Jesdisciple on 2008-10-11
That does it...  Thanks much!  Now, how do I use alltray?  (I looked on SourceForge and found no instructions.)  No use doing it over if that works...

---

### Post by Sam on 2008-10-11
> **Jesdisciple said:**
> That does it...  Thanks much!  Now, how do I use alltray?  (I looked on SourceForge and found no instructions.)  No use doing it over if that works...

[Install it](apt://alltray), then open it with "Application / Accessories / AllTray", then click on any window you want in the notification area.

Otherwise, from a terminal, run```
alltray <command>
```

Read the documentation !```
alltray --help
```
or```
man alltray
```

---

### Post by Jesdisciple on 2008-10-11
Oh!  I was getting ready to respond that I want Sunbird docked on startup, but **alltray <command>** fixes that.  (And you're right; I should have thought to check the documentation.)

EDIT:  Oops, one last question...  Why doesn't the window hide when minimizing/closing?

---

### Post by Sam on 2008-10-12
> **Jesdisciple said:**
> Oops, one last question...  Why doesn't the window hide when minimizing/closing?

Sadly I don't think it's possible using alltray. You need to click on the icon in the notification area.

---

