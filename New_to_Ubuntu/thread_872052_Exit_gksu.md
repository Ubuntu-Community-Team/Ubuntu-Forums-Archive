---
title: "Exit gksu?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Contrarian on 2008-07-27
I created a launcher on my desktop "gksu nautilus" so I can bring up nautilus with SU rights.

First, how can I set the default password so I don't get prompted? F security, if somebody accesses this PC then I've got bigger problems, like home intruders.

Second, I notice it changes my screen to some wierd flaming background.  Why does it do this? I don't want my background changed.  It took me long enough to figure out what was causing it.  At least put something in the lower right corner indicating you're now in SU mode.

When I exit nautilus, I still seem to have super user rights.  My desktop is that of the root.  I really just want that one nautilus instance to have SU rights. How can I set it up so it's just that window or when I exit at least return me to regular user rights.

C

---

### Post by northern lights on 2008-07-27
It's not really "exiting gksu" what you want to do.

The problem here is that nautilus is not just a filemanager, but also draws the gnome desktop.

You have several options.

You could simply use a different filemanager when it needs to be ran as root. xfce's thunar or kde's konqueror would do.

If you want to stick to nautilus, run ```
gksu gconf-editor
```
navigate to /apps/nautilus/preferences/ and uncheck 'Show Desktop'. Exit gconf-editor and do not change anything else, this is the root user's preferences. You can now run 'gksu nautilus' on your desktop.

On a side note: Why would you need to run your filemanager as root? How often do you have to move/copy/delete files from the root file system?
Anyway, I'd strongly advise against using this instance as your permanent filemanager or leaving it open over longer periods even.

---

### Post by Tim Sharitt on 2008-07-27
Try changing the launcher to 
```
gksu nautilus --no-desktop
```
to see if that fixes the problems with the desktop.

---

### Post by northern lights on 2008-07-27
> **Tim Sharitt said:**
> ```
gksu nautilus --no-desktop
```good flag! n1.

---

