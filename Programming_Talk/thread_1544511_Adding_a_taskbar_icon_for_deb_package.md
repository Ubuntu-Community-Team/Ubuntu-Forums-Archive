---
title: "Adding a taskbar icon for deb package?"
date: 2010-08-02
forum: Programming Talk
---

### Post by Nytram on 2010-08-02
Hi all,

First let me say I'm new to Python and to program packaging.

Ok so I created a small application in Python and I've packaged it as a deb file (It's a Spanish translator called *span-gles*.)

Inside the deb is a png file which serves as an icon in the menus, and is pointed to from a .desktop file; this works OK. The problem I have is that my program doesn't have an icon in the bottom taskbar, nor does it have an image when using Alt-Tab to switch applications (it shows a blank screen with a red stop sign on it.)

How to make my icon work for these other 2 cases?

Thanks for any help.
-- 

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

### Post by Åtta on 2010-08-03
What toolkit are you using? PyGTK? PyQt?

Here's how you do it in PyGTK: [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-icon](http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-icon)

---

### Post by Nytram on 2010-08-03
I am using PyGTK thanks for the link Åtta I'll give it a try.

---

