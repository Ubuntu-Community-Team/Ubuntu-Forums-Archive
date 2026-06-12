---
title: "PyGTK and gnome-screensaver?"
date: 2010-12-30
forum: Programming Talk
---

### Post by Tahakki on 2010-12-30
Simple enough question, really - is there a way to turn a PyGTK program into screensaver with gnome-screensaver?

---

### Post by Tahakki on 2011-01-03
Bump!

---

### Post by LemursDontExist on 2011-02-08
Hi Tahakki,

You can, in fact, make a gnome screensaver using pygtk.  You have to create a custom gtk window which uses os.environ['XSCREENSAVER_WINDOW'] as the handle for its gdk window.  Here's the code I used that worked:

```
class GsThemeWindow(gtk.Window):
    __gtype_name__ = 'GsThemeWindow'
    
    def __init__(self):
        super(GsThemeWindow, self).__init__()
        self.connect("destroy", gtk.main_quit)

    def do_realize(self):
        ident = os.environ.get('XSCREENSAVER_WINDOW')
        if not ident is None:
            self.window = gtk.gdk.window_foreign_new(int(ident, 16))
            self.window.set_events(gtk.gdk.EXPOSURE_MASK |
                                   gtk.gdk.STRUCTURE_MASK)
            x, y, w, h, depth = self.window.get_geometry()
            self.size_allocate(gtk.gdk.Rectangle(x, y, w, h))
            self.set_default_size(w, h)
            self.set_decorated(False)
        else:
            self.window = gtk.gdk.Window(
                self.get_parent_window(),
                width=self.allocation.width,
                height=self.allocation.height,
                window_type=gtk.gdk.WINDOW_TOPLEVEL,
                wclass=gtk.gdk.INPUT_OUTPUT,
                event_mask=self.get_events() | gtk.gdk.EXPOSURE_MASK)
        self.window.set_user_data(self)
        self.style.attach(self.window)
        self.set_flags(self.flags() | gtk.REALIZED)
```

The else block is so that you can run the program in a normal window for testing, etc.

If you use a GsThemeWindow as your main application window, everything should work.  You will also need to create a .desktop file - I suggest modifying one of the ones in /usr/share/applications/screensavers/.

Anyway, I spent hours trying to figure this out, so I hope this saves you some time!  Let me know if you have any other questions!

---

