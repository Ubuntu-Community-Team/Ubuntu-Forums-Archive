---
title: "Gtk+ &quot;Excel&quot; Widget?"
date: 2005-02-01
forum: Programming Talk
---

### Post by JohnQ on 2005-02-01
I'm currently working on a gradebook application in C and Gtk+.  I am in the market for a nice "excel"-like spreadsheet/table/grid widget in Gtk+ > 2.0.   Does anybody have such a widget or any ideas on where I can get one or on how I might create my own?

Any input is appreciated!

John

-- The base code is written... Once I get the GUI code going I'll open the CVS and Ubuntuforums will be the first place for the announcement :-)

---

### Post by Daniel G. Taylor on 2005-02-02
I'd suggest looking at the Gnumeric source. Either they are using a library someone has made, or they have implemented just the widget you need. Either way, you should be set.

[http://www.gnome.org/projects/gnumeric/](http://www.gnome.org/projects/gnumeric/)

---

### Post by JohnQ on 2005-02-03
Thanks for your reply.  I've downloaded the source - now I just have to figure out how to remove the Gnumeric-specific code from their table widget.

---

### Post by celloandy on 2005-02-05
An easier route than wading through the Gnumeric code would be to use the GtkSheet widget provided by the GtkExtra project.  Take a glance at [http://gtkextra.sourceforge.net](http://gtkextra.sourceforge.net) for info.

Andrew

---

### Post by JohnQ on 2005-02-09
GtkSheet is a good suggestion, but the problem with GtkSheet is that it's a dead project (last release was a couple years ago) and it's for Gtk+ 1.2 which is not cool.  It also seems to use the deprecated CList widget which means it wouldn't work so well with Gtk+ 2.x.

After the exam/homework heap is cleared I'll be working with WxWidgets which seem to have a lot of potential.  My C code can be easily re-written to be C++ and WxWidgets sounds like if I am able to get it to work on Linux, it will take on the native look of MS Windows or OSX with no additional code.  That's pretty sweet!  

Thanks for the replies!

John

---

### Post by Daniel G. Taylor on 2005-02-09
I know I'm nitpicking, but you do have to remember that even though wx will give you native widgets on each platform, GNOME, Apple, etc all have their own human interface guidelines which may not agree with your particular design, making the application look a bit less native. The problem arises that the guidelines may have different rules about similar subjects, so you can have your interface truely fit in on only one platform sometimes.

That said, backend-agnostic GUI definitions and code are a good thing.

---

### Post by iwasbiggs on 2005-02-15
In the eventual future, I think gnumeric will be looking to separate their spreadsheet code into a common widget for use by all.

But for a basic cell layout, in gtk, you'd want to make a treestore (or liststore) gobject combined with a treeview widget for viewing it. Basically, your treeview widget will contain cell renderer widgets and these will interpret the data in the treestore associated with the treeview. It can be complex at first but it's not too bad.

This will make your own grid, but the calculations and advanced features are left to the programmer to implement.

---

