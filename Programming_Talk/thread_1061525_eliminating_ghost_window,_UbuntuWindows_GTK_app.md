---
title: "eliminating ghost window, Ubuntu/Windows GTK app"
date: 2009-02-05
forum: Programming Talk
---

### Post by anewguy on 2009-02-05
I have a cross-platform app in C using GTK, developed in Ubuntu.   This app also uses libusb (and in Windows, libusb for Windows).  In Ubuntu the app just shows it's normal GTK window.  In Windows, however, it opens another Window besides the normal GTK window.  In Windows, this extra Window is black except for the 2 lines or so output by the libusb routines that I have no control.  Specifically, the "found xxx busses" message.  I use gcc in both Ubuntu and Windows to compile the app.  I assume this has something to do with the libusb functions using something like stdout, which I don't use in the GTK app.

Does anyone know if there is a way in gcc, and I guess more specifically in gcc with Windows, or with the app itself, to route stdout to null so I don't get these messages?

Thanks in advance!

Dave :)

---

### Post by anewguy on 2009-02-18
Fixed the problem - someone had passed on to me that you use winmain() when using a Microsoft compiler for a windows-based app.  Some net searching for gcc and winmain() turned up the following:

for gcc, and in my case gcc for Windows, add -mwindows to the gcc line.  That's all it took - now gcc generates windows-based app so no command line window is generated.

Dave :)

---

