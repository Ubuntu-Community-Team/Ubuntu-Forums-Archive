---
title: "Python/Glade example program wont display anything"
date: 2009-08-19
forum: Programming Talk
---

### Post by AFarris01 on 2009-08-19
Hey everybody! I'm trying to break into GUI programming w/ Python, and I'm having issues.

I've been trying to follow this tutorial:[http://handhelds.org/~nelson/pyglade/pyglade-tutorial](http://handhelds.org/~nelson/pyglade/pyglade-tutorial) to figure out how to mash python and Glade together to make a nice GUI program, but I can't get the example program to work right. I searched around for a few hours, got it to finally execute w/o errors, but no display ever comes up. Here's my current python code (glade file is attached):
```

#!/usr/bin/env python

import gtk, gtk.glade

# From example: wrapper class for widget event handlers
class GladeHandlers:
    pass

#wrapper class for the widget tree
class WidgetsWrapper:
    def __init__(self):
        self.widgets = gtk.glade.XML ('pyglade2.glade', "root_window")
        self.widgets.signal_autoconnect(GladeHandlers.__dict__)
    # From Example: Adds the ability to do: widgets['widget_name'].action()
    # for the 'GladeHandelers class
    def __getitem__(self, key):
        return self.widgets.get_widget(key)

# assign the widget tree
widgets = WidgetsWrapper()

# start GTK
gtk.main()


```
At this point, the tutorial claims that a window should pop up, but of course for me, the python code runs w/o error, but a window never appears.

Anybody with some python/Glade experience be able to help?*id greatly appreciate it. :)

---

### Post by days_of_ruin on 2009-08-19
That tutorial is outdated, it uses libglade with is deprecated.
Check out this tutorial: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

You need to get the gtk.Window and then call its method "show_all()".

---

### Post by AFarris01 on 2009-08-19
Thanks for that! It looks promising. I had actually been trying to build a calculator following a different tutorial, but I've since lost it.

Additionally, that example appears to be using gtkbuilder, rather than glade...is that correct?

I kind of figured out that the tutorial was outdated, but the one feature I really liked about it was the technique of using the 2 separate classes to control the event handlers, and with the ```
self.widgets.signal_autoconnect(GladeHandlers.__dict__) 
```
line. Is this still possible to accomplish with the newer versions of glade, or is this now accomplished with somethig similar to the ```
builder.connect_signals(self)
``` line from the micah carrick example (where i would probably replace 'self' with the desired object containing handler bindings)?

---

### Post by days_of_ruin on 2009-08-19
> **AFarris01 said:**
> Thanks for that! It looks promising. I had actually been trying to build a calculator following a different tutorial, but I've since lost it.

Additionally, that example appears to be using gtkbuilder, rather than glade...is that correct?

Yes, gtk.glade is libglade which is deprecated (It will be removed from the gtk library in the future and is only still in for compatibility).

> **AFarris01 said:**
> 
I kind of figured out that the tutorial was outdated, but the one feature I really liked about it was the technique of using the 2 separate classes to control the event handlers, and with the ```
self.widgets.signal_autoconnect(GladeHandlers.__dict__) 
```
line. Is this still possible to accomplish with the newer versions of glade, or is this now accomplished with somethig similar to the ```
builder.connect_signals(self)
``` line from the micah carrick example (where i would probably replace 'self' with the desired object containing handler bindings)?

Is there really any reason to have the handlers in a different class?

---

### Post by AFarris01 on 2009-08-20
> **days_of_ruin said:**
> 
Is there really any reason to have the handlers in a different class?

The main reason I wanted this was so I could try to take as much of the 'generic' code as possible, place it in its own file, then just 'import' it into my new projects, so all I'd have to do is implement the handler class with whatever handlers are required for the current project.... That's the idea anyway.

---

