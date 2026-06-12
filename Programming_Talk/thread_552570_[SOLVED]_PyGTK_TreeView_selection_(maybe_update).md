---
title: "[SOLVED] PyGTK TreeView selection (maybe update)?"
date: 2007-09-16
forum: Programming Talk
---

### Post by Wybiral on 2007-09-16
I'm pretty new to GTK in general, and a recent project of mine requires a "playlist" that the users can select objects from (like a media player). I decided to use the TreeView widget as it seems the most natural for this type of thing. The objects will be sortable by the users (I can already do that) and will play sequentially if not interrupted by the user clicking (I can do that as well).

Where I'm running into problems is that the selected one is a different color (in the code below it's blue) but when you select a new one it doesn't automatically update the old ones color (you have to mouse over it or something to force it).

Obviously that's not the effect I'm going for... So does anyone know a way I can force an update on an individual cell (even the whole list if I have to)? I've been looking through the documentation and haven't had any luck. I think I just need a way to get the cell from an iterator, but I can't find any functionality that supports this.

Here's a small example of what I mean (select one, then select another... Notice how it stays blue, then mouse-over the old one to update it).

```

import pygtk, gtk, gobject, thread

class DInterface:
    def __init__(self):
        # Create Window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Playlist test")
        self.window.set_default_size(640, 480)
        self.window.connect("destroy", gtk.main_quit)

        # Create Playlist
        self.playlist = gtk.TreeView()
        self.playlist.connect("row-activated", self.playlist_select_row)
        self.playlist_model = gtk.ListStore(gobject.TYPE_STRING)
        self.playlist.set_model(self.playlist_model)
        self.playlist_renderer = gtk.CellRendererText()
        self.playlist_column = gtk.TreeViewColumn("Playlist", self.playlist_renderer, text=0)
        self.playlist.append_column(self.playlist_column)
        self.playlist_column.set_cell_data_func(self.playlist_renderer, self.playlist_cell_func)
        self.window.add(self.playlist)
        self.window.show_all()

        # Fill list, set selected
        for i in xrange(11):
            self.playlist_model.set(self.playlist_model.append(), 0, str(2**i))
        self.playlist_selected = self.playlist_model.get_iter_root()

    # Playlist cell_data_func
    def playlist_cell_func(self, column, cell, model, iter):
        a = self.playlist_model.get_value(self.playlist_selected, 0)
        b = self.playlist_model.get_value(iter, 0)
        if a == b:
            cell.set_property("cell-background", "#aaaaff")
        else:
            cell.set_property("cell-background", "#ffffff")

    # Change selected row
    def playlist_select_row(self, treeview, path, column):
        self.playlist_selected = self.playlist_model.get_iter(path)

interface = DInterface()
gtk.gdk.threads_init()
gtk.main()

```

---

### Post by Wybiral on 2007-09-17
Bump. I'd really like to figure this out. If anyone knows how to force an update on a widget, or any other way to solve this, that would be really helpful.

---

### Post by xtacocorex on 2007-09-17
Hey, sorry that you haven't gotten help Wybiral.  From my research in pyGTK, the TreeView is one of the harder widgets to use.

Don't know if this will help: [http://library.gnome.org/devel/gtk-faq/stable/x602.html](http://library.gnome.org/devel/gtk-faq/stable/x602.html)
or this:
[http://ubuntuforums.org/showthread.php?t=323435](http://ubuntuforums.org/showthread.php?t=323435)

Have you run across this: [http://www.mail-archive.com/gtkmm-list@gnome.org/msg08236.html](http://www.mail-archive.com/gtkmm-list@gnome.org/msg08236.html)

I haven't read through them thoroughly, just googled quick to see if it'd help. The last one seems promisable though.

---

### Post by Wybiral on 2007-09-17
> **xtacocorex said:**
> 
...
Have you run across this: [http://www.mail-archive.com/gtkmm-list@gnome.org/msg08236.html](http://www.mail-archive.com/gtkmm-list@gnome.org/msg08236.html)
...


AH HAH! That did it. I need to use "queue_draw" to force the widget to redraw when I change it. Thanks man.

---

### Post by xtacocorex on 2007-09-17
Excellent, glad my googling skills helped out.

---

