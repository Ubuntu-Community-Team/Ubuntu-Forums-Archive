---
title: "PyGTK Glade TreeView / ListView"
date: 2012-08-06
forum: Programming Talk
---

### Post by snowz on 2012-08-06
I'm making some app with Quickly, which means I'm using Glade for the UI and Python for programming. I've inserted a TreeView with 2 columns in Glade, and now I'm stuck with adding rows to it.

How is that being done in Python?

The row cells must be empty and when clicked you can input text into those.

---

### Post by snowz on 2012-08-06
I've been experimenting around a bit and found out that if I do this

```

listview.append(row=None)

```

and add it to a button's click function, when I click it a thin "row" appears but with no content relating to the row=[COLOR="Plum"]None[/COLOR] I guess.
If I click it for multiple times, more and more "rows" begin to show up. But still, I can't do much with those.

Does **listview** actually handle the rows and **treeview** is only kind of a housing for the **listview**?

---

### Post by slavik on 2012-08-07
Treeview is very general and depends on the datastore you use. I wrote a Perl version long time ago, but the usage should be similar. Try searching for the treeview I wrote ... should be somewhere in these forums. :)

---

### Post by snowz on 2012-08-09
I've found out how to do it, following some guide.

```

# Create the store object
self.store = self.builder.get_object("liststore1")
# Put stuff into the store
self.store.append(['1st column','2nd column'])
# ^ This is an example for a 2 column list store

```This works now like it seems.

But now I've got a new problem / question.

I've created a button called "saveButton". I want the button to run a function after clicked. As I'm doing this with Python and PyGTK I first tell the app who that save button is by doing this:

```

self.saveButton = self.builder.get_object("saveButton")

```Then:
```

def on_saveButton_clicked():
         self.store.append(['123','abc'])

```This should actually do something when being clicked but it doesn't.

---

### Post by snowz on 2012-08-09
Ok, stuff just got weird. 

```

def on_saveButton_clicked():
        print 'Clicked'

```

It doesn't even print 'Clicked'.

---

### Post by oldfred on 2012-08-09
You need to connect the signals:

        # connect signals
        self.builder.connect_signals(self)

I have been trying pyqt, so I have not looked at these links for a while.
The Python GTK+ 3 Tutorial
[http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)
treeview info (older)
[http://scentric.net/tutorial/](http://scentric.net/tutorial/)
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

---

### Post by snowz on 2012-08-10
Ah damned. I had the on_button_clicked() function inside of the initialisation function, that's why it didn't work.

Thread SOLVED.

---

