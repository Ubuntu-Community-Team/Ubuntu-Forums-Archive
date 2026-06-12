---
title: "Close a PyGTK top level window?"
date: 2008-05-04
forum: Programming Talk
---

### Post by ecs_pf5 on 2008-05-04
[solved]

I've been rummaging through the PyGTK reference manual at [http://library.gnome.org/devel/pygtk/unstable/index.html](http://library.gnome.org/devel/pygtk/unstable/index.html) trying to discover how to close a window I have previously opened; can't seem to find anything though.

Here is the code that opens the window (it gets fired when the user clicks a button in the program's main window): 

```

def viewhelp(self, widget, data=None):
        
    self.windowpop = gtk.Window(gtk.WINDOW_TOPLEVEL)
    self.windowpop.set_default_size(400, 200)
    self.windowpop.set_title("Help & Licensing Info")
    self.licensescroller = gtk.ScrolledWindow()
    self.licensescroller.set_policy(gtk.POLICY_NEVER, gtk.POLICY_ALWAYS)
    self.licensetextarea = gtk.TextView()
    self.licensescroller.add(self.licensetextarea)



    self.licensetextarea.get_buffer().insert_at_cursor(' License, info & help \n')
    self.licensetextarea.get_buffer().insert_at_cursor(' """""""""""""""""""" \n')
                .
                . yada
                .
    self.licensetextarea.get_buffer().insert_at_cursor('\n')
    self.licensetextarea.get_buffer().insert_at_cursor('\n')



    self.licensetextarea.set_editable(False)
    self.licensetextarea.set_cursor_visible(False)
    self.licensecontainerh = gtk.HBox(False, 5)
    self.licensecontainerh.pack_start(self.licensescroller, True, True, 5)
    self.licclose = gtk.Button("OK", None, True)
    self.licclose.connect("clicked", self.closelicense, None)
    self.licclosecontainerh = gtk.HBox(False, 5)
    self.licclosecontainerh.pack_start(self.licclose, False, False, 5)
    self.licensecontainerv = gtk.VBox(False, 5)
    self.licensecontainerv.pack_start(self.licensecontainerh, True, True, 5)
    self.licensecontainerv.pack_end(self.licclosecontainerh, False, False, 5)
    self.windowpop.add(self.licensecontainerv)
    self.licclose.grab_focus()
    self.windowpop.show_all()

```so, how would I write a button handler to close / destroy the above?

all I'm finding on search, is callbacks that do a 
```

gtk.main_quit()

```.. but I don't want to kill the entire program, just the 'help' window.

Ah.. it couldn't be as simple as

[http://library.gnome.org/devel/pygtk/stable/class-gtkwidget.html#method-gtkwidget--destroy](http://library.gnome.org/devel/pygtk/stable/class-gtkwidget.html#method-gtkwidget--destroy)

could it.. 

seems so; [solved]

---

### Post by WW on 2008-05-04
An alternative that you might consider is to create the help window once during initialization, but don't show it.  When help is requested, just call the help window's show() function, and to close the window, call the hide() function.

---

### Post by kknd on 2008-05-04
to "close" a windows, just hide it, like window.hide(). But it will still be using memory, you need to do a destroy() to free it and the child.

---

### Post by twisted_steel on 2008-05-04
One thing that tripped me up when I was trying to close windows is a problem that happens if you just try to hide a GtkDialog or a GnomeAbout box.  Since you are using a GtkWindow at the moment, you won't have this problem.  If you ever do start using one of the other types of windows, you can get crashes and callback errors printed to the screen if you don't add some additional code.

[http://eccentric.cx/misc/pygtk/pygtkfaq.html#10.13](http://eccentric.cx/misc/pygtk/pygtkfaq.html#10.13)

---

### Post by Jadd on 2008-05-05
I had a similar problem for closing a gtkWindow in a thread. Using gobject.idle_add fixed it. See this FAQ:
[http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp](http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp)

---

