---
title: "GtkRcStyle Lookup?"
date: 2008-11-17
forum: Programming Talk
---

### Post by arloth on 2008-11-17
Is there a way to lookup styles in a RC file? I have a program in which I need to change the color of a label widget depending on if a file is present or not.  Once I have the style I can use gtk_widget_modify_style to change the color as needed.  For example, I would want to lookup the "file_absent" style, and then modify an existing widget with that style.

I guess you could say, I'm looking for the equivalent of XGetDefault for GTK+, if there is such a thing?  Or should I just make the Xlib call?  It would seem rather silly to even try to use an rc file at that point.

---

