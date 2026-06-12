---
title: "pygtk FileChooserButton: messy selecting directory"
date: 2011-03-10
forum: Programming Talk
---

### Post by wwwookie on 2011-03-10
Hi,

I've been using the python gtk.FileChooserButton widget to select files as part of a gui I'm writing, and everything works fine. However, when I try to use the same widget to select directories, I get a combobox that I didn't ask for with all my nautilus bookmarks in it and 'other' at the bottom of the list. If I select 'other', I then get to the filechooser window I originally wanted.

Here's a miniature example to show what I mean.

```
import pygtk
pygtk.require('2.0')
import gtk

class Base:

    def delete_event(self, widget, event, data = None):
        return False
 
    def destroy(self, widget, data = None):
        gtk.main_quit()

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)
        self.window.set_border_width(10)

        # this is the bit I'm talking about
        button=gtk.FileChooserButton('Select Directory')
        button.set_action(gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER)       

        self.window.add(button)
        button.show()
        self.window.show()

    def main(self):
        gtk.main()

if __name__ == "__main__":
     base = Base()
     base.main()
```Is there anyway I can disable this combobox and go straight to the filechooser? It seems there should be a way, it's easy in bash:-
```
 zenity --file-selection --directory

```Please tell me I'm doing something wrong and there's a really easy fix!

---

### Post by wwwookie on 2011-03-11
Hi again,

I slept on it and found the (admittedly easy) solution before breakfast.
The unexpected combobox when looking for directories only seems to be a feature of gtk.FileChooserButton. With gtk.FileChooserDialog you go straight to the dialog window.

In the exapmle below, I've made my own button, and put the dialog in a callback.

```
import pygtk
pygtk.require('2.0')
import gtk

class Base:

    def delete_event(self, widget, event, data = None):
        return False
 
    def destroy(self, widget, data = None):
        gtk.main_quit()

    def callback(self, widget, data = None):
        filechooser = gtk.FileChooserDialog('Select Directory', self.window, gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER, ('Cancel', 1, 'Open', 2))
        ans = filechooser.run()
        if ans == 2:        
            filechooser.destroy()
            # put "acts on selected directory routine" here
        else: 
            filechooser.destroy()

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)
        self.window.set_border_width(10)

        button = gtk.Button('Select Directory')
        button.connect('clicked', self.callback)
        self.window.add(button)
        button.show()

        self.window.show()

    def main(self):
        gtk.main()

if __name__ == "__main__":
     base = Base()
     base.main()

```All the best

---

