---
title: "How do you create an icon in the taskbar using GTK+???"
date: 2007-09-29
forum: Programming Talk
---

### Post by Fixman on 2007-09-29
How do you create an icon in the task bar using GTK+ for GNOME?

---

### Post by Compyx on 2007-09-29
Assuming you mean you want your application to have an icon next to it's name in the task bar (like for example Firefox has), this might help:
[http://library.gnome.org/devel/gtk/unstable/GtkWindow.html#gtk-window-set-icon-from-file]("http://library.gnome.org/devel/gtk/unstable/GtkWindow.html#gtk-window-set-icon-from-file")

Since you haven't provided any information on what language you're using and your problem description is somewhat vague, this is the best I can come up with.

HTH

---

### Post by Fixman on 2007-09-29
No, I mean in the right taskbar, as aMSN does

---

### Post by duff on 2007-09-29
[http://library.gnome.org/devel/gtk/2.11/GtkStatusIcon.html](http://library.gnome.org/devel/gtk/2.11/GtkStatusIcon.html)

---

### Post by MicahCarrick on 2007-09-29
I think "taskbar" is unclear. The "Notification" area is the same as "System Tray" in windows lingo. That is the area in the lower-right corner of Windows and often the upper-right corner of GNOME where running programs can have a icon (such as Gaim, Rhythmbox, etc.). 

If you want to put an icon there, you'll want to use a [GtkStatusIcon]("http://library.gnome.org/devel/gtk/2.11/GtkStatusIcon.html") to do so. More information about the standard for notification area icons is available at [FreeDesktop.org]("http://www.freedesktop.org/wiki/Specifications/systemtray-spec?action=show&redirect=Standards%2Fsystemtray-spec")

---

