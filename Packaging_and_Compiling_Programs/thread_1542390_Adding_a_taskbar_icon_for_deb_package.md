---
title: "Adding a taskbar icon for deb package?"
date: 2010-07-30
forum: Packaging and Compiling Programs
---

### Post by Nytram on 2010-07-30
Hi all,

First let me say I'm new to Python and to program packaging.

Ok so I created a small application in Python and I've packaged it as a deb file (It's a Spanish translator called *span-gles*.)

Inside the deb is a png file which serves as an icon in the menus, and is pointed to from a .desktop file; this works OK. The problem I have is that my program doesn't have an icon in the bottom taskbar, nor does it have an image when using Alt-Tab to switch applications (it shows a blank screen with a red stop sign on it.)

How to make my icon work for these other 2 cases?

Thanks for any help.
-

Additional information:

Current location of icon:
```
/usr/share/pixmaps/span-gles.png
```

Location of desktop file:
```
/usr/share/applications/span-gles.desktop
```

---

### Post by Nytram on 2010-08-03
Solved after re-posting into the Programmer forum.

For the solution see:

[http://ubuntuforums.org/showthread.php?t=1544511]("http://ubuntuforums.org/showthread.php?t=1544511")

---

