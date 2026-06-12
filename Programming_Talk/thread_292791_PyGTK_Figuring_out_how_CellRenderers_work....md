---
title: "PyGTK: Figuring out how CellRenderers work..."
date: 2006-11-04
forum: Programming Talk
---

### Post by JohnSilver on 2006-11-04
Hi

I'm trying to incorporate a combobox widget in my treeview, but I can't get it to display. I've messed around with it for a few hours now and it's driving me crazy. Anyway I have prepared a small sample program which illustrates my problem.

The program creates a window and adds a treeview widget to it. Then it adds five different types of colums (text, toggle, progress, spin, pixbuf, combobox).. The spin and combobox widget won't display. What is it that I'm not getting?

```

#!/usr/bin/env python
import sys

try:
    import pygtk
    pygtk.require("2.0")
except:
    pass

try:
    import gtk
except:
    sys.exit(1)
    
class CellRendererExample:
    """ Main class of the application. """
    
    def __init__(self):
        # Create window and connect its destroy signal.        
        window = gtk.Window()
        window.connect("destroy", gtk.main_quit)
        
        # Create and add a treeview widget to the window.
        self.treeview = gtk.TreeView()
        window.add(self.treeview)
        
        # Add a columns to treeview.
        columns = []
        
        # Text column
        columns.append( gtk.TreeViewColumn("Text column",
                                           gtk.CellRendererText(),
                                           text=0) )
        
        # Toggle column
        columns.append( gtk.TreeViewColumn("Toggle column",
                                           gtk.CellRendererToggle(),
                                           active=1) )
        
        # Progress column
        columns.append( gtk.TreeViewColumn("Progress column",
                                           gtk.CellRendererProgress(),
                                           value=2) )
        
        
        # Spin column
        cellspin = gtk.CellRendererSpin()
        
        self.adjustment = gtk.Adjustment(0, 0, 100, 1)
        
        cellspin.set_property("adjustment", self.adjustment)
        
        column = gtk.TreeViewColumn("Spin column", cellspin)
        
        column.set_cell_data_func(cellspin, self.set_value)        
        
        columns.append(column)
        
        # Pixbuf column
        cellpixbuf = gtk.CellRendererPixbuf()
        
        column = gtk.TreeViewColumn("Pixbuf column", cellpixbuf)
        
        column.set_cell_data_func(cellpixbuf, self.set_pixbuf)     
        
        columns.append(column)
        
        # Combobox column
        cellcombo = gtk.CellRendererCombo()
        
        model = gtk.ListStore(str)
        
        for item in ["item 1","item 2","item 3"]:
            model.append([item])
        
        cellcombo.set_property("model", model)
        
        column = gtk.TreeViewColumn("Combo column", cellcombo)
        
        column.add_attribute(cellcombo, "text-column", 5)
        
        columns.append(column)
        
        # Append columns to treeview
        for column in columns:
            self.treeview.append_column(column)        
        
        # Create liststore.
        liststore = gtk.ListStore(str, bool, int, int, str, int)
        
        # Append a couple of rows.
        liststore.append(["Some text", True, 50, 20, gtk.STOCK_OPEN, 0])
        liststore.append(["More text", False, 75, 30, gtk.STOCK_NEW, 1])
        
        # Set model.
        self.treeview.set_model(liststore)
        
        window.show_all()
        
    def set_pixbuf(self, column, cell, model, iter):
        stock = model.get_value(iter, 4)
        pixbuf = self.treeview.render_icon(stock, gtk.ICON_SIZE_MENU, None)
        cell.set_property("pixbuf", pixbuf)
        
    def set_value(self, column, cell, model, iter):
        value = model.get_value(iter, 3)        
        self.adjustment.set_value(value)
        cell.set_property("adjustment", self.adjustment)
        print value
        
    def main(self):
        gtk.main()

if __name__ == "__main__":
    cre = CellRendererExample()
    cre.main()


```

---

### Post by nosami on 2006-12-20
I just encountered the same problem with a CellRendererSpin control and found this post via google.

It's probably too late for you now but I had to add

```

cellspin.set_property("editable", True)


```

and even then, the spin control is only visible when you put the cell into "Edit" mode by selecting the row and then clicking inside the cell that you want to edit.

I'm thinking about converting my app to use [GtkGrid]("http://www.sicem.biz/personal/lgs/projects/gtkgrid/view_project") instead of GtkTree. It looks very similar except it's always in the edit state.

---

