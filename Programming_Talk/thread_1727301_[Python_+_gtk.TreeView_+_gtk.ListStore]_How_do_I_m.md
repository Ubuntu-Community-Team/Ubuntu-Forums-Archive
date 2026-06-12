---
title: "[Python + gtk.TreeView + gtk.ListStore] How do I make this fast enough?"
date: 2011-04-12
forum: Programming Talk
---

### Post by simeon87 on 2011-04-12
I'm having a problem with making a piece of Python + GTK code fast enough. It's a gtk.TreeView with a gtk.ListStore which has 100,000 rows and that's really making it slow. The code below takes 800 milliseconds on my computer. I must say that 100,000 is unlikely to occur in real life but 50,000 is likely to occur so I'm stress-testing with a large number of rows.

I'm not concerned with the time to load the window but the time it takes when you press the button.

I've tried many things, including:

- freeze_child_notify and thaw_child_notify on the TreeView.
- Unsetting / setting the model before and after model changes.
- Fixed widths and heights for columns, rows and cellrenderers.
- Using multiple TreeViews and multiple ListStores to split the data and then to remove / pack_start the appropriate ScrolledWindow with the TreeView when needed.
- Custom model as subclass of gtk.GenericTreeModel but then you have to deal with the overhead of calling on_iter_next thousands of times.
- Using the gtk.TreeModel.foreach function but that's also slow due to calling a function for 100,000 times.

I have reduced the problem to the following code. To see the problem, click the button and then look at the time the profiler shows.

```
import gtk
import pstats
import cProfile

class FastWindow(gtk.Window):
    def __init__(self):
        super(FastWindow, self).__init__()
        self.set_size_request(800, 600)
        self.connect('destroy', gtk.main_quit)
        
        store = gtk.ListStore(str, str, bool)
        for i in xrange(100000):
            store.append(("A", "B", True))
        self.tree = gtk.TreeView(store)
        cell = gtk.CellRendererText()
        column = gtk.TreeViewColumn("")
        column.pack_start(cell, False)
        column.set_attributes(cell, text=0)
        self.tree.append_column(column)

        swindow = gtk.ScrolledWindow(None, None)
        swindow.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        swindow.add(self.tree)
        swindow.set_size_request(192, -1)
        button = gtk.Button("Click me")
        button.connect('pressed', self.on_pressed)
        
        vbox = gtk.VBox(False, 0)
        vbox.pack_start(swindow, True, True, 0)
        vbox.pack_start(button, False, False, 0)
        self.add(vbox)
        
    def on_pressed(self, button):
        cProfile.runctx('self.update()', globals(), locals(), filename='fooprof')
        p = pstats.Stats('fooprof')
        p.sort_stats('time').print_stats(20)
        
    def update(self):
        store = self.tree.get_model()
        for row in store:
            row[0] = "TEST"

if __name__ == "__main__":
    window = FastWindow()
    window.show_all()
    gtk.main()
```

Does anyone here have an idea what I could do to make it faster? I'm pretty much running out of options. Thanks in advance, it would be much appreciated!

---

### Post by StephenF on 2011-04-13
You could...
[LIST]Convert the program to C just to check the slowness isn't down to the Python interpreter.
[/LIST]
[LIST]Create an index of the data.
[INDENT]The form of the index would depend on your data. This could be displayed in a gtk.TreeView + TreeStore. Objects A..Z with subobjects a..z for choosing the first two letters, or maybe a paper dictionary approach with anl..apr, apo..ast, and so on, aiming for a maximum of 1000 rows of data, or divide it up by time, date.

The data display to appear alongside gets the data subset upon user request from the index.
[/INDENT]
[/LIST]

---

### Post by SledgeHammer_999 on 2011-04-13
I know little python, but I suppose the function that takes 800milliseconds to execute is the update(), right?

If yes, you should try this:
1. Get a copy of the treestore.
2. Remove the treestore from the Treeview
3. Edit the treestore
4. Add the treestore to the Treeview.

EDIT: oops sorry, I saw now that you mentioned this on your OP.

---

### Post by simeon87 on 2011-04-13
> **StephenF said:**
> You could...
[LIST]Convert the program to C just to check the slowness isn't down to the Python interpreter.
[/LIST]
[LIST]Create an index of the data.
[INDENT]The form of the index would depend on your data. This could be displayed in a gtk.TreeView + TreeStore. Objects A..Z with subobjects a..z for choosing the first two letters, or maybe a paper dictionary approach with anl..apr, apo..ast, and so on, aiming for a maximum of 1000 rows of data, or divide it up by time, date.

The data display to appear alongside gets the data subset upon user request from the index.
[/INDENT]
[/LIST]

1. I could try that. Based on what I've read on the web more people are having trouble with speed issues with GTK TreeView so it may also be something with TreeView itself.

2. I'll have to think about that. The data is a wordlist, such as /usr/share/dict/words so I'm not sure if an index would make things more efficient. I do have tree data structures in C for efficiently retrieving a word from this wordlist but I'll have to see if I can use that to make the TreeView faster. Thanks for your thoughts.

> **SledgeHammer_999 said:**
> I know little python, but I suppose the function that takes 800milliseconds to execute is the update(), right?

If yes, you should try this:
1. Get a copy of the treestore.
2. Remove the treestore from the Treeview
3. Edit the treestore
4. Add the treestore to the Treeview.

EDIT: oops sorry, I saw now that you mentioned this on your OP.

Yes, I've tried that and just iterating over the thousands of values is slow. The update function currently doesn't do anything else and that alone is already too slow. Thanks for giving this problem some thought though.

---

