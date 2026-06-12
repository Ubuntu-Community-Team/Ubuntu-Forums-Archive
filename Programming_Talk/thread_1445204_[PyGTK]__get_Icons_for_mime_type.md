---
title: "[PyGTK]  get Icons for mime type ???"
date: 2010-04-02
forum: Programming Talk
---

### Post by baskar007 on 2010-04-02
Hi friends,
I am building a small web application, Which is require a filemanager, for that i am using gtk.IconView, But i was struck with gtk.IconTheme.load_icon().

I want to load icons for mime type of files. how can i do it with PyGtk ????

for example:
i have mime type of the file is  "image/png"
i want to load icon of image. like Nautilus.

any Idea???

---

### Post by NoBugs! on 2010-07-16
This may help, it shows a list of all the system icons and their names:
```
#!/usr/bin/env python
#based on http://www.daa.com.au/pipermail/pygtk/2003-August/005644.html

import pygtk
pygtk.require('2.0')
import gtk
import gobject

class stock_list(gtk.TreeView):
    def __init__(self):
        gtk.TreeView.__init__(self)
        self.init_model()
        self.init_view_columns()

    def init_model(self):
        store = gtk.ListStore(gtk.gdk.Pixbuf, gobject.TYPE_STRING)
        icon_theme = gtk.icon_theme_get_default()
        list = icon_theme.list_icons()
        for name in list:
                store.append((icon_theme.load_icon(name,48,0), name))
        self.set_model(store)

    def get_icon_pixbuf(self, stock):
        return self.render_icon(stock_id=getattr(gtk, stock),
                                size=gtk.ICON_SIZE_MENU,
                                detail=None)

    def init_view_columns(self):
        col = gtk.TreeViewColumn()
        col.set_title('Stock Items')
        render_pixbuf = gtk.CellRendererPixbuf()
        col.pack_start(render_pixbuf, expand=False)
        col.add_attribute(render_pixbuf, 'pixbuf', 0)
        render_text = gtk.CellRendererText()
        col.pack_start(render_text, expand=True)
        col.add_attribute(render_text, 'text', 1)
        self.append_column(col)

if __name__ == '__main__':
    w = gtk.Window()
    w.set_title('Stock Items')
    w.set_size_request(width=400, height=300)
    w.connect('destroy', gtk.mainquit)
    sw = gtk.ScrolledWindow()
    sw.add(stock_list())
    w.add(sw)
    w.show_all()
    gtk.mainloop()

```

---

