---
title: "PyGTK no more gtk.Combo"
date: 2007-09-27
forum: Programming Talk
---

### Post by mevets on 2007-09-27
I am writing a small GUI app and following a PyGTK located here: [http://www.moeraki.com/pygtktutorial/pygtk2tutorial/index.html](http://www.moeraki.com/pygtktutorial/pygtk2tutorial/index.html)

Evidently gtk.Combo is depricated and I am supposed to use gtk.ComboBoxEntry instead gtk.Combo. My problem now is that I dont know how to use ComboBoxEntry. Can anyone tell me what arguements to pass gtkComboxEntry() on initialization and then how to put items into it?

```


#!/usr/bin/env python

# example test.py

import pygtk
pygtk.require('2.0')
import gtk

class Clock:
    # Our callback.
    # The data passed to this method is printed to stdout
    def btn(self, widget, data=None):
        print "Hello again - %s was pressed" % data

    # This callback quits the program
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False
        
    def click_cmbDay(self, widget, data=None):
    	print "i was pressed!"

    def __init__(self):

        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Alarm Clock")

        self.window.connect("delete_event", self.delete_event)

        self.window.set_border_width(10)

        vbox1 = gtk.VBox(False, 2)
        self.window.add(vbox1)
        
        cmbDay = gtk.Combo()
        days = [ "Monday", "Tuesday", "Wednesday", "Thursday",
        		 "Friday", "Saturday", "Sunday" ]
        cmbDay.set_popdown_strings(days)
        cmbDay.entry.connect("activate", self.click_cmbDay, "combobox")
        
        vbox1.pack_start(cmbDay, True, True, 0)

        self.window.show_all()

def main():
    gtk.main()
    return 0       

if __name__ == "__main__":
    Clock()
    main()


```

---

### Post by Compyx on 2007-09-27
Have you looked at the docs?
[http://www.pygtk.org/docs/pygtk/class-gtkcomboboxentry.html]("http://www.pygtk.org/docs/pygtk/class-gtkcomboboxentry.html")

---

### Post by Asday on 2009-03-03
(Apologies for the necropost)

I've read through that, and am thoroughly baffled.

Is there a way to pass a list  (["Galahad", "Blue", "The Holy Grail"] etc.) to achieve the same effect as .set_popdown_strings() ?


[SIZE="1"]Guess I should add that I necro'd, because this thread shows up with a simple Google search, so someone coming here can find an answer.[/SIZE]

---

### Post by G|N| on 2009-03-03
```


import gobject

days = gtk.ListStore(gobject.TYPE_STRING)
days.append([ "Monday", "Tuesday", "Wednesday", "Thursday",
        		 "Friday", "Saturday", "Sunday" ])
cmbDay = gtk.ComboBoxEntry(days)

```

I did not test it, but it should work

---

### Post by Asday on 2009-03-03
NameError:  gobject is not defined.

I tried gtk. and gtk.gdk., but neither worked.  Passing a "None" argument for gtk.ListStore() didn't work either.

Apart from that, it looks pretty solid.  More convoluted than combo(), but prettier, user-side.  (God lord combo()'s ugly)

EDIT:  HAHA, I'm a damn idiot.  Missed the "import gobject".

Ok, serious problem now.

```
>>> import gtk, gobject
>>> lst = ["Galahad", "Lancelot", "Not-appearing-in-this-film"]
>>> lststore = gtk.ListStore(gobject.TYPE_STRING)
>>> lststore.append(lst)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: row sequence has wrong length
>>>
```

---

### Post by G|N| on 2009-03-03
> **Asday said:**
> 
Ok, serious problem now.

```
>>> import gtk, gobject
>>> lst = ["Galahad", "Lancelot", "Not-appearing-in-this-film"]
>>> lststore = gtk.ListStore(gobject.TYPE_STRING)
>>> lststore.append(lst)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: row sequence has wrong length
>>>
```

I told you that i didn't test it :)

you could also try:
```

for i in lst:
    lststore.append([i])


```

---

### Post by imdano on 2009-03-03
Actually gtk.Combo was deprecated in favor of gtk.ComboBox, not gtk.ComboBoxEntry.  I think what you're looking for is this: [http://pygtk.org/docs/pygtk/class-gtkcombobox.html#function-gtk--combo-box-new-text](http://pygtk.org/docs/pygtk/class-gtkcombobox.html#function-gtk--combo-box-new-text)

---

### Post by Asday on 2009-03-03
Yeah, I've already said that I couldn't understand that document.

Anyway, that for loop worked.  Unfortunately, the first entry in the list, after clicking the dropdown, is blank, and when clicked, the console gets this:

```
__main__:1: GtkWarning: gtk_entry_set_text: assertion `text != NULL' failed
```

Just a warning, so nothing too scary, but the program does nothing, so any users might be all like:  "OMGWTF Y IS IT NUT WURKIN!!??!?1?1/1?1/1/!?"

(I hate users.)  =[

EDIT:  Oh yeah, and what's the point of pygtk?  I never import it anymore, 'cause it doesn't seem to help at all.  Doesn't seem to detract, either, by not importing it.

DOUBLE-EDIT:  How do you find out what the active selection is?  Say I have a button and a combobox, you change the combobox, and click the button, which prints the contents of the combobox to the console.  (Because we all know that's incredibly useful.)

---

### Post by G|N| on 2009-03-04
> **Asday said:**
> 
DOUBLE-EDIT:  How do you find out what the active selection is?  Say I have a button and a combobox, you change the combobox, and click the button, which prints the contents of the combobox to the console.  (Because we all know that's incredibly useful.)

This is an example where it prints the current item when selecting an item in the combobox
```

import gtk
import pygtk
import gobject

class Clock:

    def __init__(self):

        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Alarm Clock")

        self.window.connect("delete_event", self.delete_event)

        self.window.set_border_width(10)

        vbox1 = gtk.VBox(False, 2)
        self.window.add(vbox1)
        
        days = gtk.ListStore(gobject.TYPE_STRING)
        
        self.lst = [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday" ]    
        for i in self.lst:
            days.append([i])
        self.cmbDay = gtk.ComboBox(days)
        self.smbDay.set_active(0)
        self.cmbDay.connect("changed", self.print_selected)
        
        vbox1.pack_start(self.cmbDay, True, True, 0)

        self.window.show_all()

    # Our callback.
    # The data passed to this method is printed to stdout
    def print_selected(self, widget, data=None):
        print self.lst[self.cmbDay.get_active()]

    # This callback quits the program
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()     

if __name__ == "__main__":
    app=Clock()
    gtk.main()

```

Again this is not tested so it could contain little mistakes...
self.smbDay.get_active() returns the index from the selected item so you only have to look it up in your list.

---

### Post by Asday on 2009-03-04
Oh how I hate classes.  I've never understood them.  =P

No worries, I got what I needed to, get_active().  (^-^ )

It returns -1 if the item isn't in the list, so I'd need to filter that out, else unrecognised input will return the last item in the list.

Thanks for the help.  (^-^ )

---

