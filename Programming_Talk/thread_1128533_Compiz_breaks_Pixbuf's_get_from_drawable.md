---
title: "Compiz breaks Pixbuf's get_from_drawable"
date: 2009-04-17
forum: Programming Talk
---

### Post by Flimm on 2009-04-17
I'm trying to save a screenshot of a window which contains a preview of a metacity theme. I use the metacity module to generate the preview and Pixbuf's save and get_from_drawable methods to save the .png file. For some reason, it only works when I've disabled compiz by running:
```
metacity --replace
```
I get the first attached image. When compiz is running, I get the second image.
Anybody got any ideas why? Is there a better way to save a preview of a metacity theme? Thanks.

Here's the code:
```
#!/usr/bin/env python
# released into the public domain

import metacity
import gtk
import gtk.gdk
import gobject
import sys, os
import time
gobject.threads_init()

class Base:
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("destroy", self.destroy_event)
        self.window.show_all()
        
    def destroy_event(self, widget):
        gtk.main_quit()
        sys.exit(0)
        return False


def main():
    theme_preview = metacity.Preview()
    viewport = gtk.Viewport()
    theme_preview.add(viewport)
    theme = metacity.theme_load("Human")
    theme_preview.set_theme(theme)
    theme_preview.set_title("Testing123")
    
    base = Base()
        
    base.window.add(theme_preview)
    theme_preview.realize()
    theme_preview.show()
    
    
    def take_screenshot():
        w = theme_preview.window
        root = gtk.gdk.get_default_root_window()
        sz = w.get_size()
        pb = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB,1,8,sz[0],sz[1])
        pb = pb.get_from_drawable(w,root.get_colormap(),0,0,0,0,sz[0],sz[1])
        if pb is not None:
            pb.save(os.path.expanduser("~/pb.png"),"png")
            print "saved"
        else:
            print "eror"
        gtk.main_quit()
        sys.exit(0)
    
    gobject.timeout_add(1000,take_screenshot)
    gtk.main()
    
if __name__ == "__main__":
    main()
```

---

### Post by days_of_ruin on 2009-04-17
You could try to figure out how the gnome appearances program does it.
But its written in c so its hard to figure out.

---

### Post by Flimm on 2009-04-18
Do you know, I have already taken a look at that, but my knowledge of Python and Java wasn't good enough to be able to understand it sufficiently.
The metacity theme code was inspired by your project, [Metacity Themer](https://launchpad.net/mct), thank you for opening its source. :)
BTW, could anyone confirm that they get similar results? Maybe I've got a bad graphics driver or something.

---

### Post by days_of_ruin on 2009-04-18
> **Flimm said:**
> Do you know, I have already taken a look at that, but my knowledge of Python and Java wasn't good enough to be able to understand it sufficiently.
The metacity theme code was inspired by your project, [Metacity Themer](https://launchpad.net/mct), thank you for opening its source. :)
BTW, could anyone confirm that they get similar results? Maybe I've got a bad graphics driver or something.

I don't think you want to be using this method anyway because:
> gtk.gdk.Pixbuf.get_from_drawable

    def get_from_drawable(src, cmap, src_x, src_y, dest_x, dest_y, width, height)

src :
	the source gtk.gdk.Drawable.

cmap :
	a colormap if src doesn't have one set.

src_x :
	the X coordinate within drawable.

src_y :
	the Y coordinate within drawable.

dest_x :
	the X coordinate in the pixbuf.

dest_y :
	the Y coordinate in the pixbuf.

width :
	the width in pixels of the region to get.

height :
	the height in pixels of the region to get.

Returns :
	the pixbuf or None on error

The get_from_drawable() method transfers image data from the gtk.gdk.Drawable specified by src and converts it to an RGB(A) representation inside a gtk.gdk.Pixbuf. In other words, copies image data from a server-side drawable to a client-side RGB(A) buffer. This allows you to efficiently read individual pixels on the client side. If src has no colormap (the gtk.gdk.Drawable.get_colormap() method returns None), then a suitable colormap must be specified as cmap. Typically a gtk.gdk.Window or a pixmap created by passing a gtk.gdk.Window to gtk.gdk.Pixmap() will already have a colormap associated with it. If src has a colormap, the cmap argument will be ignored. If src is a bitmap (1 bit per pixel pixmap), then a colormap is not required; pixels with a value of 1 are assumed to be white, and pixels with a value of 0 are assumed to be black. For taking screenshots, the gtk.gdk.colormap_get_system() function returns the correct colormap to use.

If src is a pixmap, then the requested source rectangle must be completely contained within the pixmap, otherwise the function will return None. For pixmaps only (not for windows) passing -1 for width or height is allowed to mean the full width or height of the pixmap. If src is a window, and the window is off the screen, then there is no image data in the obscured/offscreen regions to be placed in the pixbuf. The contents of portions of the pixbuf corresponding to the offscreen region are undefined.

**If the window you're obtaining data from is partially obscured by other windows, then the contents of the pixbuf areas corresponding to the obscured regions are undefined. If the target drawable is not mapped (typically because it's iconified/minimized or not on the current workspace), None will be returned**. If memory can't be allocated for the return value, None will be returned instead. (In short, there are several ways this method can fail, and if it fails it returns None; so check the return value.)

This method calls the gtk.gdk.Drawable.get_image() method internally and converts the resulting image to a gtk.gdk.Pixbuf, so the documentation for the gtk.gdk.Drawable.get_image() method may also be helpful.

---

### Post by Flimm on 2009-05-02
Thanks for the pointer. Funnily enough, the code seems to work fine on a Hardy machine, even when the window is partially obscured.
Does anyone know a reliable way to get a preview of a metacity theme? Help deciphering the C code from gnome appearance would be appreciated.

---

### Post by Flimm on 2009-06-24
I've found the solution: use get_snapshot()

[php]#!/usr/bin/env python
# released into the public domain

import metacity
import gtk
import gtk.gdk
import gobject
import sys, os
import time
gobject.threads_init()

class Base:
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("destroy", self.destroy_event)
        self.window.show_all()
        
    def destroy_event(self, widget):
        gtk.main_quit()
        sys.exit(0)
        return False


def main():
    theme_preview = metacity.Preview()
    viewport = gtk.Viewport()
    theme_preview.add(viewport)
    theme = metacity.theme_load("Human")
    theme_preview.set_theme(theme)
    theme_preview.set_title("Testing123")
    
    base = Base()
        
    base.window.add(theme_preview)
    theme_preview.realize()
    theme_preview.show()
    
    
    def take_screenshot():
        w = theme_preview.window
        root = gtk.gdk.get_default_root_window()
        sz = w.get_size()
        pb = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB,1,8,sz[0],sz[1])
        ## This line was deleted: #pb = pb.get_from_drawable(w,root.get_colormap(),0,0,0,0,sz[0],sz[1])
        # The following two lines were added:
        pm = theme_preview.get_snapshot(None)
        pb = pb.get_from_drawable(pm, pm.get_colormap(), 0,0,0,0,sz[0],sz[1])
        if pb is not None:
            pb.save(os.path.expanduser("~/pb.png"),"png")
            print "saved"
        else:
            print "eror"
        gtk.main_quit()
        sys.exit(0)
    
    gobject.timeout_add(1000,take_screenshot)
    gtk.main()
    
if __name__ == "__main__":
    main()[/php]

---

