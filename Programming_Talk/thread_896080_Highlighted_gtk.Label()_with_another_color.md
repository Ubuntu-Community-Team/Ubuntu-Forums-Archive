---
title: "Highlighted gtk.Label() with another color"
date: 2008-08-20
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2008-08-20
Hi, I'm making some custom pygtk widget or I think so, this is my code>
[PHP]
#!/usr/bin/python
# -*- coding: utf-8 -*-
# file:cool_lb.py

try:
    import gtk
      import gobject
      from gtk import gdk
except:
    raise SystemExit
    

import pygtk

class cool_label(gtk.Alignment):
    def __init__(self):
        gtk.Alignment.__init__(self)
        self.tekst = gtk.Label()
        self.color1 = self.tekst.get_colormap().alloc_color("blue")
        self.color2 = self.tekst.get_colormap().alloc_color("white")

        self.tekst.set_style(self.set_color())
        self.add(self.tekst)

    def do_realize(self):
        #self.connect("motion_notify_event", self.motion_notify_event)
        # If I uncomment the connect thing I don't see the Label, else I see the Label but    
        # the code is not changing the state of the Label.
    def do_unrealize(self):
        self.window.destroy()

#    def do_expose_event(self, event):

    def motion_notify_event(self, widget, event):
        if event.is_hint:
            x, y, state = event.window.get_pointer()
            #self.tekst.set_state(gtk.STATE_PRELIGHT)
            print "1"

        else:
            x = event.x
            y = event.y
            state = event.state
            print "2"
            #self.style.set_background(self, gtk.STATE_NORMAL)
            #self.tekst.set_state(gtk.STATE_NORMAL)
        
    def get_text(self):
        return self.tekst.get_text()

    def set_text(self, text):
        self.tekst.set_text(text)
    
    def set_color(self):
        data = gtk.Label().get_style().copy()
        try:
            data.fg[gtk.STATE_NORMAL] = self.color1
            data.fg[gtk.STATE_PRELIGHT] = self.color2
            print "a"
        except:
            data.fg[gtk.STATE_NORMAL] = self.color1 % ("blue")
            data.fg[gtk.STATE_PRELIGHT] = self.color2 % ("white")
            print "b"
        return data

    def set_color1(self, color):
        self.color1 % (color)
        
    def set_color2(self, color):        
        self.color2 % (color)
[/PHP]

My goal is when I point the Label with the cursor the Label must change the color to e.g "white", when I move it back i.e STATE_NORMAL the color to be normal (blue).

Will some one help fix this terrible :) code :confused: ?

P.S> Few extra tutorials for custom pygtk widgets are welcomed :idea:.

---

