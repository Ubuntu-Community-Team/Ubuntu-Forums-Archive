---
title: "Python.GTK Filelister"
date: 2009-10-13
forum: Programming Talk
---

### Post by DThurman on 2009-10-13
I am hoping there are some really good Python/GTK programmers
here!  This is the first time I am posting in regards to programming.

To make a long story short, basically I am trying to
create a specific Filelister application that supports
a tree view of directories/files which includes the black
expand/close actionable event.

The application works as expected if I set the argument,
recurse=True in the dir_walk() method, but unfortunately
it recurses all the way though from the default path setting
down, which can take a very long time to complete.  This is
obviously very inefficient.

What I am attempting to do, is obtain the directories/files
at one-level deep, and through an "expand" event, to trigger
a call to obtain the branches depending on directory selected.

[edit1]
I added modification to open_file() method codeblock by adding
additional parameter, parent=iter, to dir_walk method(), and it
seems to work only for the root-tree and not that of its branches.
[/edit1]

[edit2]
I discovered that I was not getting the absolute pathnames
from file_open() method.  Not sure how to grab the entire
pathname starting from the root-tree... so I guess I will
have to keep trying...

Added a debug statement in file_open() method
just after the filename assignment.
[/edit2]

I am seeking pointers/advice, and here is the code
provided below:

```

#!/usr/bin/env python

import os, stat, time
import pygtk
pygtk.require('2.0')
import gtk

class FileLister:

    # Close the window and quit
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def __init__(self, dname=None):
        
        # Create a new window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("FileLister")
        self.window.set_size_request(400, 300)
        self.window.connect("delete_event", self.delete_event)

        # Create TreeStore File List
        self.treestore = gtk.TreeStore(str, gtk.gdk.Pixbuf, int, bool)
        
        # Obtain the list of files
        self.dname = os.path.expanduser('~/Desktop/')
        self.dir_walk(self.dname)

        # Create TreeViewColumn1
        self.tvcolumn1 = gtk.TreeViewColumn('File')
        # Allow sorting on the column
#        self.tvcolumn1.set_sort_column_id(0)
        # Create a column cell to display text
        self.tvcolumn1_cell_text = gtk.CellRendererText()
        # Create a column cell to display an image
        self.tvcolumn1_cell_img = gtk.CellRendererPixbuf()
        # Add the cells to the column
        self.tvcolumn1.pack_start(self.tvcolumn1_cell_img, False)
        self.tvcolumn1.pack_start(self.tvcolumn1_cell_text, True)
        # Bind the text cell to column 0 of the tree's model
        self.tvcolumn1.add_attribute(self.tvcolumn1_cell_text, "text", 0)
        # Bind the image cell to column 1 of the tree's model
        self.tvcolumn1.add_attribute(self.tvcolumn1_cell_img, "pixbuf", 1)

        # Create TreeViewColumn2
        self.tvcolumn2 = gtk.TreeViewColumn('Size')
        self.tvcolumn2_cell_text = gtk.CellRendererText()
        self.tvcolumn2.pack_start(self.tvcolumn2_cell_text)
        self.tvcolumn2.add_attribute(self.tvcolumn2_cell_text, "text", 2)

        # Create the TreeView and set our data store as the model
        self.treeview = gtk.TreeView(self.treestore)
        # Make the treeview searchable
#        self.treeview.set_search_column(0)
        # Allow treeview drag and drop reordering of rows
#        self.treeview.set_reorderable(True)

        # Append the columns to the TreeView
        self.treeview.append_column(self.tvcolumn1)
        self.treeview.append_column(self.tvcolumn2)

        # Folder open event
        self.treeview.connect('row-activated', self.open_file)

        # Add scrolled Window
        self.scrolledwindow = gtk.ScrolledWindow()
        self.scrolledwindow.add(self.treeview)

        # Add scrolled window and show
        self.window.add(self.scrolledwindow)
        self.window.show_all()

    # Obtain the directory listing
    def dir_walk(self, dname, parent=None, recurse=False):
        ''' (1) If recurse=True, this can take a very long time
            (2) Symlinks are followed - need to disable this.
        '''
        for f in os.listdir(dname):
            filename = os.path.join(dname, f)
            self.debug("File: "+filename)
            try:
                fdata = os.stat(filename)
            except:
                self.debug("File: <error>"+filename)
                continue
            is_folder = stat.S_ISDIR(fdata.st_mode)
            img = gtk.icon_theme_get_default().load_icon(
                    "folder" if is_folder else "document",
                    gtk.ICON_SIZE_MENU, 0)
            try:
                ts = self.treestore.append(parent, [f,img,fdata.st_size, is_folder])
            except:
                self.debug("File: <error>"+filename)
                continue
            if is_folder & recurse:
                self.dir_walk(filename, ts)
        return self.treestore

    def open_file(self, treeview, path, column):
        ''' UNDER DEVELOPMENT - DOES NOT WORK RIGHT '''
        model = treeview.get_model()
        iter = model.get_iter(path)
        filename = os.path.join(self.dname, model.get_value(iter, 0))
        ''' (1) filename is not an absolute path, so
                it will break in the branches of of the
                root-tree
        '''
        self.debug("File: "+filename)
        ''' Added parent, but this only works for top level '''
        ts = self.dir_walk(filename, parent=iter)
        treeview.set_model(ts)
        return

    def debug(self, string):
        print 'DEBUG: %s' % string

def main():
    gtk.main()

if __name__ == "__main__":
    myApp = FileLister()
    main()

```

---

