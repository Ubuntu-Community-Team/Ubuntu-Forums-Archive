---
title: "[PyGtk] GtkEntry, how to use?"
date: 2008-09-28
forum: Programming Talk
---

### Post by dodle on 2008-09-28
I've been trying to build a basic calculator to practice programming in python.  I'm using Glade as well.  My problem (at the moment) is that I have only figured out how to use text in a GtkEntry.[PHP]# When button 1 pressed
gtk.entry.insert_text("1")[/PHP]For a calculator I need to use a digit don't I?  Can I do this with a GtkEntry, or is there a different widget that I need to use?

---

### Post by meastp on 2008-09-28
Look here:
[http://www.pygtk.org/docs/pygtk/class-gtkentry.html](http://www.pygtk.org/docs/pygtk/class-gtkentry.html)

Of course you can use it as input for a calculator. Then you just have to convert the numbers to integers with int( '89079' ) afterwards.

---

