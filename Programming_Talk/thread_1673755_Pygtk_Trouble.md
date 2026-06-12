---
title: "Pygtk Trouble"
date: 2011-01-22
forum: Programming Talk
---

### Post by Mr.Macdonald on 2011-01-22
This code
[PHP]#!/usr/bin/python2.7                                                                                                                                                     

import pygtk
import gtk

class HelloWorld:
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("destroy", self.destroy)
        self.window.set_border_width(10)

        self.area = gtk.DrawingArea()
        self.area.set_size_request(500, 500)
        self.window.add(self.area)

        self.drawable = self.area.window
        print self.area.__class__
        self.gc = self.drawable.new_gc()

        self.drawable.draw_line(self.gc, 10, 10, 20, 20)

        self.area.show()
        self.window.show()

    def main(self):
        gtk.main()

    def destroy(self, widget, data=None):
        gtk.main_quit()


hello = HelloWorld()
hello.main()

[/PHP]

This Error
[PHP]Traceback (most recent call last):
  File "./ballSim", line 32, in <module>
    hello = HelloWorld()
  File "./ballSim", line 18, in __init__
    self.gc = self.drawable.new_gc()
AttributeError: 'NoneType' object has no attribute 'new_gc'
[/PHP]

EDIT:

What I want is a window to pop up with a line drawn in it

---

### Post by nvteighen on 2011-01-23
That means the window attribute hasn't been set for some reason. Maybe, because you're not creating the associated gtk.gdk.Pixmap? Have you taken look at this?: [http://www.pygtk.org/pygtk2tutorial/sec-DrawingAreaWidgetAndDrawing.html](http://www.pygtk.org/pygtk2tutorial/sec-DrawingAreaWidgetAndDrawing.html)

---

### Post by Mr.Macdonald on 2011-01-23
I got that fixed. I needed to call main and then have an event handler draw the objects.

Is there a way to force something to draw? I am trying to draw a circle, sleep and then draw another circle. Moving Ball. Ideas? I think its buffering the drawing

---

