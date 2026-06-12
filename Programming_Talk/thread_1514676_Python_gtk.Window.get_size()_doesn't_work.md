---
title: "Python gtk.Window.get_size() doesn't work"
date: 2010-06-21
forum: Programming Talk
---

### Post by Yuzem on 2010-06-21
Hello, I'm using "gtk.Window.set_default_size(1024,639)" 
My application launches with the correct size, if the user changes the window size I want to save it but "gtk.Window.get_size()" returns the default size instead of the new one.

Anyone knows how to get the current window size?
Thanks in advance.

---

### Post by simeon87 on 2010-06-21
It does work here. See the [documentation](http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--get-size) for more info - under certain conditions, it does not return the current window size (yet).

---

### Post by StephenF on 2010-06-21
This is how I do it.
```

def cb_configure_event(widget, event):
    print "Window width, height", event.width, event.height

...

window.connect("configure-event", cb_configure_event)

```

---

