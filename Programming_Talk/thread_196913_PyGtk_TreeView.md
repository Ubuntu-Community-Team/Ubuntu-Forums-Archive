---
title: "PyGtk TreeView"
date: 2006-06-14
forum: Programming Talk
---

### Post by Wallakoala on 2006-06-14
So I am making an rss feed reader in pygtk with a friend. For displaying the feeds, we decided to use a tree-style interface. It seems like the best way to do this is using a treeview, but the only problem is that the treeview seems to be the most complex widget in all of gtk. The tutorial on the pygtk site seems to be way overkill for what we want to acheive. Does anybody know of a simple explanation/tutorial about treeviews in pygtk? Googling didn't really help this time...

Or is there a better way to do this?(without using treeview?)

---

### Post by FryerFox on 2006-06-15
The tree is the right widget. Unfortunately, it is the hardest widget to get going.

Basically, you set up a data source (for example a ListStore), then create some columns:
```

liststore = gtk.ListStore(str, str)
treeview = gtk.TreeView(liststore)

# Just text rendering for the columns
textrenderer = gtk.CellRendererText()

# Add the column to the treeview
column = gtk.TreeViewColumn(var, textrenderer, text=1)
column.set_sort_column_id(1)
treeview.append_column(column)

# Add the items to the liststore
for row in data:
   itt = liststore.append([row[0], row[1]])

```

In the simple (?) example above, we create a tree with two data columns, but only one is shown (the column created sources from the row[1]).

---

### Post by Wallakoala on 2006-06-15
Thanks, I semi-figured this out!

Attached is a shot of my program now if anybody wants to see what it looks like.

Of course I am going to add a section to the right where it will display the feed info and then eventually the descriptions of each individual entry.

Any suggestions are welcome.

---

### Post by Jefferythewind on 2010-03-30
Hi,
  I am trying to figure pygtk out as well, namely the Treeview module.  I have done a small program much like the example above, but my column is not being populated with values.  The name of the column shows up, and it seems there are a few rows generated, but the values are not visible.  Is there some kind of 'model filter' thing that I am not doing?  I noticed it in another example.

Thanks for the help.

---

### Post by SledgeHammer_999 on 2010-03-30
Don't ressurrect old threads. Create your own. Moreover plz provide some example code. Probably you're doing something wrong.

---

### Post by Jefferythewind on 2010-03-30
Alright, good idea.  It seems like i cleared that problem up anyway,

Cheers

---

