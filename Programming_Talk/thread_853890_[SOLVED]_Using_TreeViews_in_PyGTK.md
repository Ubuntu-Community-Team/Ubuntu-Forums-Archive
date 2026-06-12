---
title: "[SOLVED] Using TreeViews in PyGTK"
date: 2008-07-09
forum: Programming Talk
---

### Post by mssever on 2008-07-09
I'm a newbie to GUI programming, and I'm amazed at how incredibly complicated GTK is. I'm using Glade 3, so that's one hurdle out of the way, but Glade can't set up a proper TreeView. I've been working on this for three days and still haven't gotten past prepopulating the window with initial values, let alone writing signal handlers to make the GUI useful. I'm about to pull my hair out. ](*,)

All I need is a list with a single column; no headings, no sorting--nothing fancy at all. Simple, right? It seems that in order to handle what should take one or two lines of code involves dozens of different classes, none of which is useful on its own, and each requiring thourough knowledge to be used. So the API docs are useless to me because they don't give sufficient information without reading up on 20,000 classes (plus or minus a few :)). And the PyGTK tutorial manages to give lots of detail without being helpful; how can I remember or understand what I'm reading when I can't write working code? And I can't write working code without reading too much to remember all at once. Grr.

Sorry for the rant. Now to my problem. I'm trying to add rows to the aforementioned list. In my GUI class's __init__() method, I have this code: [php]self.inputs['email_to_treeview'] = builder.get_object('email_to_treeview') # builder is an instance of gtk.Builder
self.inputs['email_to'] = gtk.ListStore(gobject.TYPE_STRING)
self.inputs['email_to_treeview'].set_model(self.inputs['email_to'])[/php]In my main class, where I'm initializing everything prior to displaying the window, I have the following: [php]for i in current['email_to']: # current['email_to'] is a list of strings to display
    print i # this is just to prove that the correct data is going in
    self.app.inputs['email_to'].append(row=(i,)) # self.app.inputs['email_to'] is the ListStore created earlier[/php]I expected this code to add the proper rows to the TreeView. But when I run my code, the TreeView is as blank as ever. What's wrong with my code? Or even better, can I make Glade 3 do the heavy lifting for me?

---

### Post by mssever on 2008-07-09
bump

---

### Post by thornmastr on 2008-07-09
Consider posting this to the python users news group. This might help

[http://mail.python.org/mailman/listinfo/python-list](http://mail.python.org/mailman/listinfo/python-list)


Robert

---

### Post by mssever on 2008-07-09
> **thornmastr said:**
> Consider posting this to the python users news group.
Thanks. I'll do that as a last resort, though, because I hate mailing lists. I hope someone here is able to help, given that Python is very popular here.

---

### Post by Can+~ on 2008-07-09
I've also noticed that TreeViews are incredibly complicated in Gtk, you need at least 5 different widgets:

-Store widget: it stores the data, pretty much a glorified list.
-TreeView widget: Displays everything
-CellRenderer: The object that draws cells on a list, text, bitmap, other widgets...
-Column: A column.

Therefore, mixing all that:

[PHP]treeview = thexml.get_widget("treeview1") # Get the treeview widget (thexml = the glade file)
treecol = gtk.TreeViewColumn("Title") # Define the column
treerend = gtk.CellRendererText() # The Cellrenderer
treestore = gtk.ListStore(str) # List store, storing a single string (a TreeStore also available).

# Append some stuff to it
treestore.append(["Hello"])
treestore.append(["Another Row!"])

# EDIT: Forgot this one :D
treeview.set_model(treestore)

# Pack start the cellrenderer to the column.
treecol.pack_start(treerend, False)

treecol.add_attribute(treerend, "text", 0)[/PHP]

---

### Post by mssever on 2008-07-10
Can+~:

Thanks for your help. Unfortunately, things still aren't working. Using your code as a starting point, I wrote the following function, in the hopes that I'll never have to mess with treeview internals for a simple list again:
[php]def make_list(treeview, column_names, column_types):
    """Converts an empty TreeView into a simple list widget.
    
    Arguments:
        treeview: the treeview widget to alter
        column_names: a tuple-like object containing the column names
        column_types: a tuple-like object containing the column types
        Both column_names and column_types must be the same length
    
    Returns:
        The ListStore instance that you can use to alter the TreeView's contents.
    """
    if len(column_names) != len(column_types):
        raise ArgumentError, "Column name and type mismatch"
    for i in xrange(len(column_names)):
        col = gtk.TreeViewColumn(column_names[i], gtk.CellRendererText(), text=i)
        col.expand = True
        treeview.append_column(col)
    list_store = gtk.ListStore(*column_types)
    treeview.set_model(list_store) # Your code didn't include this, but I believe that it's necessary, right?
    return list_store[/php]I'm initializing my TreeView like this: [php]self.inputs['email_to_treeview'] = builder.get_object('email_to_treeview')
self.inputs['email_to'] = gtktrees.make_list(self.inputs['email_to_treeview'], ('E-mail address',), (gobject.TYPE_STRING,))[/php]And in another class, I'm adding items like this: [php]for address in current['email_to']:
    self.app.inputs['email_to'].append((address,))[/php]current['email_to'] is a list containing 3 e-mail addresses, but the widget is as blank as ever. Somehow, I'm still not doing something right. But what?

---

### Post by af20001 on 2008-07-11
When I was looking into the treeview I worked through [this]("http://www.learningpython.com/2007/02/17/pylan-a-gtd-todo-application-written-in-python-and-pygtk-part-one/") example at learningpython.com.

Not sure if that is the best or only way of doing it, but I was able to get a working example running based on that.

---

### Post by mssever on 2008-07-18
After a PM conversation with Can+~, I finally found the problem: I have to call ```
tree_view_column.set_sizing(gtk.TREE_VIEW_COLUMN_FIXED)
``` on each column.

I have several questions now:

[LIST=1]
[*]In [this thread]("http://www.gtkforums.com/viewtopic.php?t=1507"), I wrote some test code that works without requiring gtk.TreeViewColumn#set_sizing(). Why does that test code work that way while my program is different?
[*]I got this error before fixing my code: ```
/home/.../lib/gtktrees.py:47: GtkWarning: gtk_tree_view_insert_column: assertion `gtk_tree_view_column_get_sizing (column) == GTK_TREE_VIEW_COLUMN_FIXED' failed
  treeview.append_column(col)
```I initially ignored it because: a) It's labeled a warning, not an error; b) a number of programs I use regularly spew out GTK warnings about such-and-such assertion failing, without any apparent consequences; c) I expected to get an exception if something was truly wrong. Is it a bug in PyGTK that this didn't raise an exception?
[*]On the subject of exceptions, why on earth does PyGTK swallow all exceptions? Imagine the following scenario: The user is editing a file of some type. He/she uses the save command, but writing the file fails for some reason. Furthermore, the programmer didn't catch that exception, so PyGTK "helpfully" does so. The user makes major changes, planning on being able to revert to the saved version if something goes wrong, oblivious to the error that just occurred. PyGTK had tried to print a backtrace to stderr, but since the app was started from the menu, the user never saw the error.

Obviously, in this scenario, the app contains a major bug. But the user won't necessarily find out about it until too late. This is why uncaught exceptions are fatal, outside PyGTK's world. As a compromise, shouldn't uncaught exceptions at least result in an automatic error dialog? They should be in-your-face obvious.
[/LIST]

---

### Post by Can+~ on 2008-07-18
Also, we managed to produce a little widget connector:

[PHP]# Written by Can+~@ubuntuforums. Modified by Scott Severance.
# Last edit: Friday 18-June-08 | 22:27:08

import sys
import gtk

class EasyList:
    def __init__(self, treeview, columns, coltypes):
        """EasyList(gtktreeview, titles, types) -> EasyList object
        
        Creates a new instance of the class EasyList that
        handles the content of a gtktreeview easier than
        the gtk method.
        
        Arguments:
            treeview : The gtk treeview widget to be used.
            columns : A tuple of column titles ("title1", "title2", ...)
            coltypes : Types of column (str, str, int...)
        
        Comments:
            Everything is treated as fundamental types in EasyList."""
                
        if len(columns) != len(coltypes) or len(columns) == 0:
            raise ValueError, "columns and coltypes should be equal in size."
        
        self.treeview = treeview
        self.store = gtk.ListStore(*coltypes)
        self.cellr = gtk.CellRendererText()
        
        for count,column in zip(xrange(len(columns)), columns):
            current = gtk.TreeViewColumn(column, self.cellr)
            current.add_attribute(self.cellr, "text", count)
            self.treeview.append_column(current)
        
        self.treeview.set_model(self.store)
    
    def append_row(self, data):
        if type(data) is not list and type(data) is not tuple:
            data = (data,)
        self.store.append(data)

#Usage example
if __name__ == "__main__":
    import gtk.glade
    xml = gtk.glade.XML("%s/glade/widget.glade" % sys.path[0])
    win = xml.get_widget("window1")
    
    gtklist = EasyList(xml.get_widget("treeview"), ("Name", "Age"), (str, int))
    gtklist.append_row(("John", 21))
    gtklist.append_row(("Susan", 17))
    
    win.connect("destroy", gtk.main_quit, None)
    win.show_all()
    gtk.main()  [/PHP]

It may need that additional "tree_view_column.set_sizing(gtk.TREE_VIEW_COLUMN_FIXED)"

---

