---
title: "[SOLVED] GTK Beginner - multiple top level windows"
date: 2008-05-28
forum: Programming Talk
---

### Post by anewguy on 2008-05-28
Thanks to everyone who has helped me out so far.  Please keep in mind I'm a beginner at GTK, and EXTREMELY rusty at "C" - I only remember how to do the most basic of things.

Thanks to previous answers, I now have my application with multiple top level windows (to kind of overlay one another as activated).  Right now I hide the previous window, show the new, the hide the new and show the old when going from window to the next and then back.  Is there a way to leave any "calling" windows visible but not "active" when I bring up another top level window?

Thanks in advance!  :)

---

### Post by kknd on 2008-05-28
You can set the GtkWindow to be modal. Then when you call a modal GtkWindow, the other will be visible, but not active.

[http://library.gnome.org/devel/gtk/stable/GtkWindow.html#gtk-window-set-modal](http://library.gnome.org/devel/gtk/stable/GtkWindow.html#gtk-window-set-modal)

---

