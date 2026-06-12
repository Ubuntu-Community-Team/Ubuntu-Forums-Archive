---
title: "Any pygtk python programmers out there?"
date: 2006-11-04
forum: Programming Talk
---

### Post by pachjo on 2006-11-04
I am trying to get to grips with treeviews in pygtk/gtk and am stuck on setting the alignment of the columns.

No matter what I try I cannot change the alignment](*,)  

Here is the code I found on the web which I am using to change different lines to see the effect and thus learn how they work.  However I added the line 	self.cell1.set_property('alignment', pango.ALIGN_CENTER) and it makes no difference.  I have tried right align too with no joy!

Can anyone help me please?

```

def __init__(self):

        # Create a new window

        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)

        self.window.set_title("TreeViewColumn Example")

        self.window.set_size_request(400, 200)

        self.window.connect("delete_event", self.delete_event)

        # create a liststore with one string column to use as the model

        self.liststore = gtk.ListStore(str, str, str, 'gboolean')

        # create the TreeView using liststore

        self.treeview = gtk.TreeView(self.liststore)

        # create the TreeViewColumns to display the data

        self.tvcolumn = gtk.TreeViewColumn('Pixbuf and Text')

        self.tvcolumn1 = gtk.TreeViewColumn('Text Only')

        # add a row with text and a stock item - color strings for

        # the background

        self.liststore.append(['Open', gtk.STOCK_OPEN, 'Open a File', True])

        self.liststore.append(['New', gtk.STOCK_NEW, 'New File', True])

        self.liststore.append(['Print', gtk.STOCK_PRINT, 'Print File', False])

        # add columns to treeview

        self.treeview.append_column(self.tvcolumn)

        self.treeview.append_column(self.tvcolumn1)

        # create a CellRenderers to render the data

        self.cellpb = gtk.CellRendererPixbuf()

        self.cell = gtk.CellRendererText()

        self.cell1 = gtk.CellRendererText()

        # set background color property

        self.cellpb.set_property('cell-background', 'yellow')

        self.cell.set_property('cell-background', 'cyan')

        self.cell1.set_property('cell-background', 'pink')

	self.cell1.set_property('alignment', pango.ALIGN_CENTER)

        # add the cells to the columns - 2 in the first

        self.tvcolumn.pack_start(self.cellpb, False)

        self.tvcolumn.pack_start(self.cell, True)

        self.tvcolumn1.pack_start(self.cell1, True)

        # set the cell attributes to the appropriate liststore column

        # GTK+ 2.0 doesn't support the "stock_id" property

        if gtk.gtk_version[1] < 2:

            self.tvcolumn.set_cell_data_func(self.cellpb, self.make_pb)

        else:

            self.tvcolumn.set_attributes(self.cellpb, stock_id=1)

        self.tvcolumn.set_attributes(self.cell, text=0)

        self.tvcolumn1.set_attributes(self.cell1, text=2,

                                      cell_background_set=3)

        # make treeview searchable

        self.treeview.set_search_column(0)

        # Allow sorting on the column

        self.tvcolumn.set_sort_column_id(0)

        # Allow drag and drop reordering of rows

        self.treeview.set_reorderable(True)

        self.window.add(self.treeview)

        self.window.show_all()


```

---

