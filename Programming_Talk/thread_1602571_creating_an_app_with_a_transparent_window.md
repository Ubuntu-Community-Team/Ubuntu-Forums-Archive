---
title: "creating an app with a transparent window"
date: 2010-10-21
forum: Programming Talk
---

### Post by Choad on 2010-10-21
Can anyone point me in the right direction here? 

I want to create a "start menu"-esque application with some similarities to the ps3's XMB

In essence, I need to be able to render accelerated 2d graphics on to a transparent surface.

Cheers.

---

### Post by johnl on 2010-10-21
Hi,

You can accomplish this with a basic gtk window using cairo. (In C, python, whatever languages have bindings for GTK and cairo)

Here's a simple python example:


```

#!/usr/bin/env python

import gtk
import cairo

class MainWindow(gtk.Window):
    __gsignals__ = {
        'expose-event': 'override'
        }

    def __init__(self):
        super(MainWindow, self).__init__()

        self.set_app_paintable(True)
        # no window border
        self.set_decorated(False)

        # see if we can do transparency
        screen = self.get_screen()
        
        alphamap = screen.get_rgba_colormap()
        rgbmap   = screen.get_rgb_colormap()

        if alphamap is not None:
            self.set_colormap(alphamap)
        else:
            self.set_colormap(rgbmap)
            print 'sorry, no alpha channel available :('
            
        self.set_size_request(300, 200)

    def do_expose_event(self, event):
        # we're going to draw on a temporary surface
        # then copy to the window surface
        # you can also draw directly on the window
        width, height = self.get_size()
        
        surface = cairo.ImageSurface(cairo.FORMAT_ARGB32, width, height)
        ctx = cairo.Context(surface)

        # background is gray and transparent
        ctx.set_source_rgba(.7, .7, .7, 0.75)
        ctx.paint()

        # red border
        ctx.set_line_width(3.0)
        ctx.rectangle(0, 0, width, height)
        ctx.set_source_rgba(1.0, 0.0, 0.0, .75)
        ctx.stroke()

        # now copy to our window surface
        dest_ctx = self.window.cairo_create()
        # only update what needs to be drawn
        dest_ctx.rectangle(event.area.x, event.area.y, 
                           event.area.width, event.area.height)
        dest_ctx.clip()
        # source operator means replace, don't draw on top of
        dest_ctx.set_operator(cairo.OPERATOR_SOURCE)
        dest_ctx.set_source_surface(surface, 0, 0)
        dest_ctx.paint()

        
if __name__ == "__main__":
    w = MainWindow()
    w.show()
    gtk.main()

```

---

### Post by worksofcraft on 2010-10-21
> **johnl said:**
> 
Here's a simple python example...


That's wierd.
It does **NOT** work on my computer.
Recently I discovered that transset has stopped work too and I don't think I changed anything except for doing automatic updates.

I posted a thread asking in anyone else had this [no-transparancy problem]("http://ubuntuforums.org/showthread.php?t=1592938") but it seems not :confused:

---

### Post by johnl on 2010-10-21
> **worksofcraft said:**
> That's wierd.
It does **NOT** work on my computer.
Recently I discovered that transset has stopped work too and I don't think I changed anything except for doing automatic updates.

I posted a thread asking in anyone else had this [no-transparancy problem]("http://ubuntuforums.org/showthread.php?t=1592938") but it seems not :confused:

Desktop effects (compiz) has to be enabled for this to work.  If you dont have them enabled you'll just see a gray window with a red border.

---

### Post by worksofcraft on 2010-10-21
> **johnl said:**
> Desktop effects (compiz) has to be enabled for this to work.  If you dont have them enabled you'll just see a gray window with a red border.

hum does the following mean anything to you?
```

$> compiz
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```
all I know is that it used to work and now it doesn't :confused:

---

### Post by johnl on 2010-10-22
```

Xlib:  extension "GLX" missing on display ":0.0".

```

means you don't have GLX, probably because your graphics driver doesn't support it.  I would post in another section with your relevant specs (graphics card, 'glxinfo', current driver, etc...) and see if someone else can figure it out.

---

### Post by Choad on 2010-10-22
> **johnl said:**
> Hi,

You can accomplish this with a basic gtk window using cairo. (In C, python, whatever languages have bindings for GTK and cairo)


Ah that's perfect! Thanks for the example too.

---

