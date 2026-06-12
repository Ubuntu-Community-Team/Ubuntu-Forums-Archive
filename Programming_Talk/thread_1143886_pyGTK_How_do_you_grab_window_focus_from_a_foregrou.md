---
title: "pyGTK: How do you grab window focus from a foreground app?"
date: 2009-04-30
forum: Programming Talk
---

### Post by bigwave on 2009-04-30
Hi folks,

I'm building a python app using pygtk  that launches other stand-alone gnome applications and I need help understanding how to grab window focus away from the launched gnome app appearing in the foreground.

Specifically, I have an image viewer (gqview) that I call using  subprocess.Popen().

What I want to happen is this:

1) gqview launches  in full screen mode, obscuring the desktop.
2) cursor event goes to my main event loop, not gqview.
3) mouse click is handled by my main python app.
4) main program kills gqview via PID.

Question 1:  is this possible to have an app in the background retain input focus?
Question 2:  if not, is there a way to put a transparent window or frame in front of the app so I can retain input focus despite a full screen application?

Please forgive my ignorance if this is obvious -- I'm a bit of a noob to python, gnome and pygtk.

Thanks,
Dave

[PS: if there is a better forum for such a question, can someone please point me in the right direction?]

---

### Post by unutbu on 2009-04-30
Is there a compelling reason to use Popen and gqview?
If not, you might want to consider using pygtk to display images on its own:

[PHP]
#!/usr/bin/env python
import gtk
window = gtk.Window(gtk.WINDOW_TOPLEVEL)
window.connect("destroy", gtk.main_quit)
window.set_border_width(10)
image=gtk.Image()
image.set_from_file('/path/to/image.png')
window.add(image)
image.show()
window.show()
gtk.main()[/PHP]
The obvious advantage of doing it this way is your gtk.Window never loses focus.

---

### Post by bigwave on 2009-04-30
> **unutbu said:**
> Is there a compelling reason to use Popen and gqview?
If not, you might want to consider using pygtk to display images on its own:

[php]
#!/usr/bin/env python
import gtk
window = gtk.Window(gtk.WINDOW_TOPLEVEL)
window.connect("destroy", gtk.main_quit)
window.set_border_width(10)
image=gtk.Image()
image.set_from_file('/path/to/image.png')
window.add(image)
image.show()
window.show()
gtk.main()[/php]The obvious advantage of doing it this way is your gtk.Window never loses focus.

Thanks for the code snip!

I'm using the "slideshow" feature of gqview.  For now, I did not want to build my own slide-show and image management functions.  Once I get a bit more familiar with Python and oop functions I will go that route.  In the meantime I'm shunting to useful apps and bash scripts (which I know well). 

I did find the functions: gdk_pointer_grab() and gdk_keyboard_grab() 
but I don't yet understand how to reference the GDK function from within a pygtk widget/class instance. (as you can probably tell, I'm quite a noob wrt OOP and gnome) From the GDK reference:  "GTK+ initializes GDK in [gtk_init()]("file:///usr/share/gtk-doc/html/gtk/gtk-General.html#gtk-init") and so this function is not usually needed by GTK+ applications. "

-Dave

---

### Post by bigwave on 2009-05-01
> **bigwave said:**
> Thanks for the code snip!

I did find the functions: gdk_pointer_grab() and gdk_keyboard_grab() 
but I don't yet understand how to reference the GDK function from within a pygtk widget/class instance. 



Can anybody tell me if its possible to use gdk_pointer_grab() and identify a GtkWindow as the target object?  I've been trying to understand the relationship between the two but gdk_pointer_grab() expects a gdk window.  

```

        mywindow = self.window
        print "window: ",mywindow
        gtk.gdk.pointer_grab(mywindow)

```gives: 

window:  <gtk.Window object at 0x82d589c (GtkWindow at 0x83728b0)>
Traceback (most recent call last):
  File "./glui.py", line 51, in picturesButton_clicked
    gtk.gdk.pointer_grab(mywindow)
TypeError: pointer_grab() argument 1 must be gtk.gdk.Window, not gtk.Window

From the GDK and GTK+ references, it seems like the GtkWindow is related to gtk.gdk.window but I don't see a way to refer to that object.  It seems like this will only work if I'm using GDK objects -- is that true?

Thanks again,
Dave

---

