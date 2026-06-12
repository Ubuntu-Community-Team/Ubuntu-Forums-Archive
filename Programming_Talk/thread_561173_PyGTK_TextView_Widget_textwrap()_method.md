---
title: "PyGTK TextView Widget textwrap() method"
date: 2007-09-27
forum: Programming Talk
---

### Post by petit.padavoine on 2007-09-27
Hi.

This sample PyGTK application should display a text file in word wrap mode, in a TextView widget with scrollbars: 

```

! /usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

class HelloWorld:

   def delete_event(self, widget, event, data=None):
      return False

   def destroy(self, widget, data=None):
      gtk.main_quit()

   def __init__(self):
      self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
      self.window.connect("delete_event", self.delete_event)
      self.window.connect("destroy", self.destroy)
      self.window.set_border_width(10)

      self.texteditorsw = gtk.ScrolledWindow()
      self.texteditorsw.set_policy(gtk.POLICY_AUTOMATIC,gtk.POLICY_AUTOMATIC)
      self.texteditor = gtk.TextView(buffer=None)
      self.textbuffer = self.texteditor.get_buffer()
      self.file = open("/home/padavoine/programming/python/tkinter/stufftodo", 'r')
      self.contents = self.file.read()
      self.file.close()
      self.texteditor.set_wrap_mode(gtk.WRAP_WORD)
      self.textbuffer.set_text(self.contents)
      self.texteditor.set_editable(True)
      self.texteditor.set_justification(gtk.JUSTIFY_LEFT)

      self.texteditorsw.add(self.texteditor)
       
      self.window.add(self.texteditorsw)

      self.texteditorsw.show()
      self.texteditor.show()
      self.window.show()


   def main(self):
      gtk.main()

if __name__ == "__main__":
   hello = HelloWorld()
   hello.main()

```

However, the text is not wrapped...
Any ideas?

I posted this on a specific python forum and the only answer I got was to switch to wxPyton...

---

### Post by petit.padavoine on 2007-09-27
Bump.

---

### Post by tseliot on 2007-09-28
Try to resize (reduce) the window and see how it works. It works well here.

Maybe you should set the the size of the window in the code.

---

### Post by petit.padavoine on 2007-09-30
Basically what happens is that I start with a minuscule textbox.
As I type into the textbox, the textbox grows larger to fit the text on one line.
I can't shrink it back manually, because the window isn't growing, only the textbox.

I just get a longer and longer textbox, which I can scroll through with the scrollbar, but the window keeps its original size.

Resizing the window or setting the size in the code have no effect.

---

### Post by petit.padavoine on 2007-10-03
Bump.

---

### Post by Jhongy on 2009-07-02
This is an old thread, but in case anyone else finds this via Google (as I did), then the solution is to pack the scrolledwindow into a container which doesn't resize, and get it to occupy the available space in the container. For example, just pack_start it into a VBox.

J

---

