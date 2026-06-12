---
title: "Qt under Gnome."
date: 2007-12-11
forum: Programming Talk
---

### Post by fargoth on 2007-12-11
I know Qt, and i like the way it's designed.
but i prefer Gnome on my machine... my question is... will my program be less useful under Gnome if i choose to use Qt over Gtk?
What are the drawbacks (if any, apart from having to install Qt runtime) of choosing Qt if my main DE is Gnome?

---

### Post by kknd on 2007-12-14
will my program be less useful under Gnome if i choose to use Qt over Gtk?

If it doesn't use kdelibs, it does the same under GNOME or KDE. But people will search for GTK apps first, since a Qt app will have a different look and feel and will require  more libs loaded at runtime.

What are the drawbacks (if any, apart from having to install Qt runtime) of choosing Qt if my main DE is Gnome?

A different look and feel and a a higher memory consumption. Maybe some options like toolbar text positioning and so will also don't work.

---

### Post by rbprogrammer on 2007-12-15
i had the same question a few months and, here is the thread that i eventually answered my own problem.  check the bottom on what i installed.  then every QT program will run the same as if it were to run on a KDE, maybe even windows if the QT libraries were installed on the windows environment.

[http://ubuntuforums.org/showthread.php?t=593183](http://ubuntuforums.org/showthread.php?t=593183)

---

