---
title: "Problems with Gnome panel"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Surfrock66 on 2008-10-24
I've been searching all day but can't find anyone having the same problem.  I was using 8.04, and the problem is persisting in 8.10 RC 1.  It seems like all right click actions on the panels are acting funny.  I used to be able to right click anywhere on the panel and choose "add to panel," but now the only options that come up are "Help" and "About Panels."  I used to be able to right click on items in the menu and choose "add Launcher to Panel" and now right clicking just opens the program.  I used to be able to right click on the little lines next to the "Notification Area" applet, but now I can't.  I'm sort of lost as to when it started or how to fix it.  Any ideas?  If it'd be helpful for me to provide some sort of output, let me know and I can get it.

---

### Post by prematurebaby on 2008-10-24
Have you restarted?

---

### Post by taseedorf on 2008-10-24
try pressing ctrl+alt+backspace and see if reloading your window manager helps.

if not, try gconf-editor
type that at terminal

than go to apps, panel... im not sure of an exact location but poke around there....there MAY be something to fix there...

---

### Post by Surfrock66 on 2008-10-25
I've restarted the computer and the window manager several times, no luck.  I toyed around with the gconf-editor, but nothing there helped (I tried things around keybindings and stuff but it didn't work).  I've reinstalled panels in synaptic, no luck.  I'm really getting ticked off, since the upgrade I can't get the power button back or anything, I know it's in the system menu but I've been using this for a year and showing so many people how cool Ubuntu is, and I'm pissed this happened with no warning and no signals and no one seems to have had this problem before.

---

### Post by roger_1960 on 2008-10-25
Hi

Have a look in synaptic and do a search on 'panel'  There are a number of gnome-panel packages which should already be installed.  Are any broken?  Perhaps try reinstalling them.

gnome-panel
gnome-panel-data
gnome-panel-dbg

If you've already done all these, sorry!

---

### Post by Surfrock66 on 2008-10-25
I've tried re-installing all of those, no help.

Is there some output that would be useful to help diagnose this?

---

### Post by Surfrock66 on 2008-10-25
Ok, I just logged in as root and there's no problem, when I'm in root.  Is there some permission I should change?

EDIT: I ran the following code:

cd /home
sudo chown -hR ::myUsername:: ::homefolder::

and it errored on .gvfs, but seems to have taken care of everything else.  Still didn't fix it.  Root panels work, my panels don't.

---

### Post by Surfrock66 on 2008-10-28
Bump, any more ideas?  This is really killing me here.

---

