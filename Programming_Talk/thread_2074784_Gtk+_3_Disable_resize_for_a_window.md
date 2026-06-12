---
title: "Gtk+ 3 Disable resize for a window ?"
date: 2012-10-22
forum: Programming Talk
---

### Post by myromance123 on 2012-10-22
Hi there.
I have been trying to set Gtk+ 3 to stop the user from resizing the window.
Initially I thought I had to use gtk_window_set_has_resize_grip(False) but that didn't do anything. The window is still resizable.

```
#!/usr/env/python

from gi.repository import Gtk

class BasicWindow(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title="No Resize")

        self.set_has_resize_grip(False)

        table = Gtk.Table(3, 1, True)
        self.add(table)

        label_info = Gtk.Label("This window cannot be resized")
        table.attach(label_info, 0, 1, 1, 2)

win = BasicWindow()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()

```

I've been scouring the Gtk+ 3 documentation, but I can't seem to find out how to do this. I am using Python with Gtk+ 3 on Ubuntu 12.10 with IDLE 2.7. Is this possible? Am I doing something wrong?

Any help would greatly be appreciated!

---

### Post by bird1500 on 2012-10-22
Afaik, the compositor, not X11 decides if a window can be resized, so it's probably not possible to make it work under any compositor (Mutter, Compiz..). E.g. X11 might set a location for a window but ultimately the compositor might just place it at the center of the screen. But maybe I'm wrong, maybe your case doesn't fall under this assumption.

---

### Post by myromance123 on 2012-10-23
What I wonder is how did OutRec do it?
Its a small window which cannot be resized or maximized. This is what I want to achieve. Is it really impossible to make a window with a permanent height and width?

---

### Post by bird1500 on 2012-10-23
I'm using Gtkmm (gtk with C++) and to achieve it I do in a Gtk::Window subclass:

property_resizable() = false;

And it works fine (that is, there's no resize grips) if called before or after the Gtk::Window shows up.

Same result when using set_resizable(false);

PS: Using Ubuntu 12.04 with the Unity desktop.

---

### Post by myromance123 on 2012-10-23
Thanks bird1500, 
```

Same result when using set_resizable(false);
```
works great.
I also found this via searching the Gtk+ 3 documentation using the keyword "resize".
That got me this:
[[COLOR="RoyalBlue"]http://developer.gnome.org/gtk-faq/stable/x662.html[/COLOR]]("http://developer.gnome.org/gtk-faq/stable/x662.html")

Basically, we use gtk_window_set_resizable( boolean ) which in python looks something like (assuming self is for the main window):
```
 self.set_resizable( False )
```

So, implementing like this:
```
#!/usr/env/python

from gi.repository import Gtk

class BasicWindow(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title="No Resize")

        # This single line below stops the user from resizing.
        self.set_resizable(False)

        table = Gtk.Table(3, 1, True)
        self.add(table)

        label_info = Gtk.Label("This window cannot be resized")
        table.attach(label_info, 0, 1, 1, 2)

win = BasicWindow()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()
```

Now the user is unable to resize the window, and it will stay in its current width and height! :)
Thanks for all the help, and may this help someone else later on.

---

