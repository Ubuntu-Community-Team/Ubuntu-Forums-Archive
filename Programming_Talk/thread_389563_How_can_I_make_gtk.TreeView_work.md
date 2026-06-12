---
title: "How can I make gtk.TreeView work?"
date: 2007-03-20
forum: Programming Talk
---

### Post by reacocard on 2007-03-20
Hi, I'm fairly new to programming (about 3 months now), so go easy on me.

In python, I'm trying to use a gtk.TreeView to display a simple list with two columns, one with a string, the other with a progressbar. Here's the part that sets this up:
```
    def setup_list(self):
        self.list = gtk.ListStore(str, float)
        view = self.xml.get_widget('downloads_list')
        view.set_model(self.list)
        columns = []
        columns.append(gtk.TreeViewColumn("File", gtk.CellRendererText()))
        columns.append(gtk.TreeViewColumn("Progress", gtk.CellRendererProgress()))
        for c in columns:
            c.set_sizing(gtk.TREE_VIEW_COLUMN_AUTOSIZE)
            view.append_column(c)
        self.list.append(("Example.tar.gz", 32.56))
```

This creates the two columns just fine, but the test item added at the end there doesn't have any information. It's just a blank box and empty progressbar. How do I get this to work?

---

### Post by reacocard on 2007-03-21
bump.

Anyone? I have absolutely no idea how to do this, ANY help would be great.

---

### Post by Tomosaur on 2007-03-21
I too had some horrible problems with TreeView while writing a very tiny package management system. I managed to get around it eventually. You'll need to change this code to suit your project, obviously:

```

def set_sel_box(self):
        tree_store = gtk.TreeStore(gobject.TYPE_STRING)
        s_window = gtk.ScrolledWindow(None,None)
        cache = alpi_package_list()

        tree_view = gtk.TreeView(tree_store)
        r = gtk.CellRendererText()
        p_column = gtk.TreeViewColumn("Double click a package name to select, or expand to see description", r)
        p_column.add_attribute(r,"text",0)
        d_column = gtk.TreeViewColumn("Description")

        for item in cache.available_packages:
            iter = tree_store.append(None,[item[0]]) #Add package name
            tree_store.append(iter,[item[1]])  #Add package description

        tree_view.insert_column(p_column,0)
        tree_view.set_rules_hint(True)
        tree_view.connect("button-press-event", self.package_selected)
        s_window.add(tree_view)
        s_window.set_policy(gtk.POLICY_AUTOMATIC,gtk.POLICY_AUTOMATIC)
        self.mainbox.pack_end(s_window,True,True,5)

```


It has a tiny bug in it somewhere which I haven't bothered to fix yet, but that should at least give you an idea of how to get it working.

---

### Post by reacocard on 2007-03-21
> **Tomosaur said:**
> I too had some horrible problems with TreeView while writing a very tiny package management system. I managed to get around it eventually. You'll need to change this code to suit your project, obviously:

<snip>

It has a tiny bug in it somewhere which I haven't bothered to fix yet, but that should at least give you an idea of how to get it working.

Thanks! I didn't know you had to connect the attribute to the column like that. Here's my revised example:
```
    def setup_list(self):
        self.list = gtk.ListStore(str, float)
        view = self.xml.get_widget('downloads_list')
        view.set_model(self.list)
        columns = []
        columns.append(gtk.TreeViewColumn("File", gtk.CellRendererText(),
            text=0))
        columns.append(gtk.TreeViewColumn("Progress",
            gtk.CellRendererProgress(), value=1))
        for c in columns:
            c.set_sizing(gtk.TREE_VIEW_COLUMN_AUTOSIZE)
            view.append_column(c)

        examp = self.list.append()
        self.list.set_value(examp, 0, "Really long text string.")
        self.list.set_value(examp, 1, 50.0)
```

It's a tad less verbose than yours since I had to do the connection inside the constructor, but it works great.

Thanks again!

---

