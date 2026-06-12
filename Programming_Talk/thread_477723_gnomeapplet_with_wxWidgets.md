---
title: "gnomeapplet with wxWidgets ?"
date: 2007-06-18
forum: Programming Talk
---

### Post by info2 on 2007-06-18
Hi,

i started coding something in wxWidgets. Now i want to create a little gnome applet using wx, too.
I googled around but all i find are examples using pygtk.

I found this ( using gtk ) and i understand whyt it is doing:

```
#!/usr/bin/env python
import pygtk
pygtk.require('2.0')

import gtk
import gnomeapplet
import gobject

def background_show(applet):
    print "background: ", applet.get_background()

def sample_factory(applet, iid):
    print "Creating new applet instance"
    label = gtk.Label("Success!")
    applet.add(label)
    applet.show_all()
    gobject.timeout_add(1000, background_show, applet)
    return True

gnomeapplet.bonobo_factory("OAFIID:GNOME_PythonAppletSample_Factory", 
                           gnomeapplet.Applet.__gtype__, 
                           "hello", "0", sample_factory)
```

I understand how it works and it just works but i really like to do something easy like that with wxwidgets.

I hope somebody knows a howto or can give me a code skeleton.

Thanks in advance.

---

