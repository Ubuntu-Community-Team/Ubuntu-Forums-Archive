---
title: "pygtk comboboxes"
date: 2008-10-04
forum: Programming Talk
---

### Post by kuzniarpawel on 2008-10-04
I'm in a middle of creating my first python+pygtk program. Recently I'm encountered a problem, while trying to use comboboxes. I'm trying to fill a combobox with two values for each row. Bellow is the code sample. My problem is whenever I add a new entry to db, stazbox should be refreshed, so I run stazbox_fill(). With each run my combobox grows, duplicating values from the second column, for each row. 

So on a first run I receive a combobox with data:

X1, Y1
X2, Y2
X3, Y3

and after second run

X1, Y1, Y1
X2, Y2, Y2
X3, Y3, Y3
X4, Y4, Y4

So where is the problem?

[INDENT]
  def stazbox_fill(self):
[INDENT]
    stazlist = gtk.ListStore(gobject.TYPE_STRING, gobject.TYPE_STRING)
    self.stazbox = self.wTree.get_widget("staz-box")
    self.addstazlistcolumn()
    self.stazbox.set_model(stazlist)
    for x in stazdic.keys():
[INDENT]
      stazlist.insert(x, row=(stazdic[x][0], stazdic[x][1]))
[/INDENT]
    self.stazbox.set_active(0)
[/INDENT]

  def addstazlistcolumn(self):
[INDENT]
    cell = gtk.CellRendererText()
    self.stazbox.pack_start(cell, True)
    self.stazbox.set_attributes(cell, text=0)
    self.stazbox.set_attributes(cell, text=1)
[/INDENT]
[/INDENT]

---

### Post by gomputor on 2008-10-04
To refresh it you must first clear it.
Didn't have the time to test it, but you can try it.
[PHP]def stazbox_fill(self):
    self.stazbox = self.wTree.get_widget("staz-box")

    model = self.stazbox.get_model()
    if model != None:
        self.stazbox.set_model(None)
        self.stazbox.clear()

    stazlist = gtk.ListStore(str, str)
    self.addstazlistcolumn()
    self.stazbox.set_model(stazlist)
    for x in stazdic.keys():
        stazlist.insert(x, row=(stazdic[x][0], stazdic[x][1]))

    self.stazbox.set_active(0)[/PHP]
And a question: Why you have the [COLOR="DarkOrange"]self.stazbox = self.wTree.get_widget("staz-box")[/COLOR]
inside your [COLOR="Olive"]stazbox_fill[/COLOR] method and not inside the [COLOR="DarkOrange"]__init__[/COLOR] of your App Class? Declare it once
and let your methods use it, you don't have to declare it every time you call the [COLOR="Olive"]stazbox_fill[/COLOR] method.

---

### Post by kuzniarpawel on 2008-10-04
thx a lot, now it works fine

Surely, I moved declarations to __init__ :)

---

