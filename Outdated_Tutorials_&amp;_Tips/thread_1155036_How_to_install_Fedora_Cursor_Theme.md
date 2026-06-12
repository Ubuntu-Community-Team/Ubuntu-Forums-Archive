---
title: "How to install Fedora Cursor Theme"
date: 2009-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by camper365 on 2009-05-10
This is a demonstration as to how to install the Fedora Cursor theme on Ubuntu with GNOME.

I have seen that a lot of people have looked at Fedora and liked the way it does the cursor. However, Ubuntu does not come with that theme. So here's how to do it:

First, go to gnome-look.org and get the files:

```
http://gnome-look.org/content/download.php?content=53266&id=1&tan=58740744
```Then unzip the archive (using either the GNOME archive manager or with this in a terminal:
```
tar -xjvf redhat-cursors.tar.bz2
```then copy all of the folders to /usr/share/icons (so there should be a Bluecurve-FC4, Bluecurve-FC6, Bluecurve-inverse-FC4, and Bluecurve-FC6 in /usr/share/icons)

You can now go to System -> Preferences -> Appearence, select your favorite theme, select customize, and go to the right tab (pointer) and select the cursor theme.
An explanation of each one is:

> Bluecurve-FC4: These are Red Hat's original Bluecurve mouse cursors, plus the 4 "drag and drop" cursors (none, ask, move, and copy) from Fedora 5 and 6. These use the hourglass instead of the running blue dot busy cursor.

Bluecurve-inverse-FC4: As above, but in white instead of black.

Bluecurve-FC6: Red Hat's theme for Fedora Core 5 and 6. Includes a new busy cursor (a blue dot running around the arrow) and a few slightly modified cursors (like the "What's this?" cursor with the question mark).

Bluecurve-inverse-FC6: As above, but in white.
(quoted from the Readme).

In order for the changes to fully take effect, you may need to restart X or your computer.


In order to undo all the changes, all you need to do is delete the Bluecurve-FC4, Bluecurve-FC6, Bluecurve-inverse-FC4, and Bluecurve-inverse-FC6 folders from the /usr/share/icons folder.


If you do not have administrative rights, but you want the cursor theme anyway, replace all instances of /usr/share/icons with ~/.icons

---

### Post by jpeddicord on 2009-05-12
Approved and thank you for your tutorial contribution! I'm not personally a fan of the Fedora cursors, but I know a lot that would find this useful.

---

