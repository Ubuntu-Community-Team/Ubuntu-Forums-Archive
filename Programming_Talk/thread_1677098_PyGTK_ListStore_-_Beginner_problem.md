---
title: "PyGTK ListStore - Beginner problem"
date: 2011-01-28
forum: Programming Talk
---

### Post by jorrieboy on 2011-01-28
I've recently started working in PyGTK, and I have a problem with getting the selected item from a ListStore. This is the code:
```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk, gobject

import datetime
import sys
import re

file_location = '/home/joris/Dropbox/calendar.txt'


def openTxtDict():
  txt = open(file_location, 'r')
  txt_dict = {}
  for tmpline in txt:
    line = tmpline.split('|') # Convert to list, and remove the newline at the end 
    if line[3] != 'none':
      line[3] = datetime.datetime.strptime(line[3],"%Y-%m-%d") # Convert date string to date
    if line[4] != 'none':
      line[4] = int(line[4]) # Convert priority string to int
    #line[5] = datetime.datetime.strptime(line[5],"%Y-%m-%d") # Convert date string to date
    txt_dict[line[0]] = line
  return txt_dict





class MainWindow:
  # Create the list of "messages"
  def createList(self):
    # Create a new scrolled window, with scrollbars only if needed
    scrolled_window = gtk.ScrolledWindow()
    scrolled_window.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)

    model = gtk.ListStore(gobject.TYPE_STRING)
    self.tree_view = gtk.TreeView(model)
    scrolled_window.add_with_viewport (self.tree_view)
    self.tree_view.show()

    # Add some item messages to the window
    self.txt_dict = openTxtDict()
    for key in self.txt_dict:
      name = self.txt_dict[key]
      item = name[0]
      iter = model.append()
      model.set(iter, 0, item)

    cell = gtk.CellRendererText()
    column = gtk.TreeViewColumn("Items", cell, text=0)
    self.tree_view.append_column(column)

    return scrolled_window
   
  def getSelected(self):
    model, iter = self.tree_view.get_selection().get_selected()
    entry = model.get(iter, 0)
    #entry = model.get_value(iter, 0)
    return entry


  def insertText(self, buffer):
    pass
   
  # Create the area with the item's information
  def createInfo(self):
    frame = gtk.Frame(self.getSelected())
    
    return frame
   
  def __init__(self):
    window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    window.set_title("pyCalendar")
    window.connect("destroy", lambda w: gtk.main_quit())
    window.set_border_width(3)
    window.set_size_request(450, 400)

    # create a vpaned widget and add it to our toplevel window
    hpaned = gtk.HPaned()
    window.add(hpaned)
    hpaned.show()

    # Now create the contents of the two halves of the window
    list = self.createList()
    hpaned.add1(list)
    list.show()

    item_info = self.createInfo()
    hpaned.add2(item_info)
    item_info.show()
    window.show()

def main():
  gtk.main()
  return 0

if __name__ == "__main__":
  MainWindow()
  main()
```The error I get when I run this program is:
  File "./MainWindow.py", line 100, in <module>
    MainWindow()
  File "./MainWindow.py", line 90, in __init__
    item_info = self.createInfo()
  File "./MainWindow.py", line 69, in createInfo
    frame = gtk.Frame(self.getSelected())
  File "./MainWindow.py", line 59, in getSelected
    entry = model.get(iter, 0)
TypeError: iter must be a GtkTreeIter

Does anyone has a solution for this problem?

---

### Post by StephenF on 2011-01-28
Since nobody else has calender.txt there is no way to properly test this program.

---

### Post by jorrieboy on 2011-01-28
This is what is in the calendar.txt file

Toekomstdossier|Toekomstdossier af!|toekomstdossier, opleiding|2011-03-15|3|2011-01-18 
Toekomstdossier 20|20 uur besteed aan toekomstdossier|toekomstdossier, opleiding|2011-01-28|3|2011-01-18 
test|test|test|2010-01-01|3|2011-01-18 
Frans|dit is een test voor frans|frans, frans|2011-01-01|3

It's a calendar application, and i've chosen to save all the items in this file on dropbox, so it's synced on my home and my school computer (for your information: it's in Duch)

---

### Post by StephenF on 2011-01-28
It fails because nothing is selected which would result in iter=None.
```

def getSelected(self):
    model, iter = self.tree_view.get_selection().get_selected()
    if iter is None:
        return model[0][0]
    else:
        return model.get_value(iter, 0)

```

---

### Post by jorrieboy on 2011-01-28
It works, but does anyone also know how to update the gtk frame every time when you select an other item?

---

### Post by StephenF on 2011-01-28
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

