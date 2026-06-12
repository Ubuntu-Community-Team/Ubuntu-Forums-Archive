---
title: "auto-size window with gtkmozembed"
date: 2008-04-30
forum: Programming Talk
---

### Post by Tar-Get on 2008-04-30
```
#!/usr/bin/python 
import os, sys, gtk, gtkmozembed, PIL.Image 

class Take_screenshot: 
    def __init__(self, parent = None):        
        self.parent = gtk.Window(gtk.WINDOW_TOPLEVEL) 
        # Initialize mozembed 
        self.moz = gtkmozembed.MozEmbed() 
        self.moz.show() 
        print self.parent.get_allocation().height    # returns 1 
        #self.moz.set_resize_mode(gtk.RESIZE_PARENT)    # tested if this changed something 
        #self.parent.set_resize_mode(gtk.RESIZE_PARENT)    # tested if this changed something 
        self.parent.add(self.moz) 
        self.moz.load_url('http://www.google.com')        
        self.parent.show_all() 
        # Connect signals 
        self.moz.connect('net_stop', self.prepare_screenshot) 
        self.moz.connect('size-request', self.set_size) 
        self.moz.connect('size-allocate', self.set_size) 
    
    def prepare_screenshot(self, data = None):    # 'Page loaded' 
        sys.stdout.flush() 
        gtk.timeout_add(1000, self.create_screenshot) 
        #print gtk.Requisition(self.moz).height # Doesn't work (abstract widget => requisition with connect('size-request')) 
    
    def set_size(self, width, height): 
        print 'width: %d   height: %d'% (height.width, height.height) 
        #print height # the height-parameter is a gtkmozembed object 

    def create_screenshot(self): 
        (x, y, width, height, depth) = self.moz.window.get_geometry() 
        pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, False, 8, width, height) 
        pixbuf.get_from_drawable(self.moz.window, self.moz.get_colormap(), 0, 0, 0, 0, width, height) 
        pixbuf.save('screenshot.png', 'png')    # 'Write screenshot.png' 
        gtk.main_quit() 
        
Take_screenshot() 
gtk.main()
```


this is a screenshot-script that uses the gtkmozembed widget.
Does someone know how I can resize the window to the gtkmozembed-widget its size? (I want a screenshot of the full webpage)
the size-request signal returns (0, 0) and the get_allocation doesn't return the widget's size either.

---

### Post by LaRoza on 2008-04-30
Please use code tags. (The sticky has a guide for posting code to make things easier)

---

### Post by JamesUser on 2008-04-30
Maybe this is what you are looking for.

[http://www.pygtk.org/docs/pygtk/class-gtkwidget.html#method-gtkwidget--size-request](http://www.pygtk.org/docs/pygtk/class-gtkwidget.html#method-gtkwidget--size-request)

---

### Post by Tar-Get on 2008-04-30
> **JamesUser said:**
> Maybe this is what you are looking for.

[http://www.pygtk.org/docs/pygtk/class-gtkwidget.html#method-gtkwidget--size-request](http://www.pygtk.org/docs/pygtk/class-gtkwidget.html#method-gtkwidget--size-request)

the function get_size_request(self.moz) returns (-1, -1)  :s
I've also tried the connect('size-request') event, which also returns (-1, -1)

---

