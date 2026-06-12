---
title: "make gtk.Notebook behave like Firefox"
date: 2010-05-07
forum: Programming Talk
---

### Post by Rockiger on 2010-05-07
Hello, 
I am new to PyGTK-Development. I try to make gtk.Notebook behave like Firefox, but couldn't find a solution on the internet.
Is there a way to change the shortcuts for turning the pages of gtk.notebook. I would like to  use <ctrl>+<tab> for turning a page forward instead of <ctrl>+<alt>+<PageDown>. Is there a way to do this?

Kind regards,

Marco

---

### Post by steeleyuk on 2010-05-07
You'll need to write your own method to increment the page number when CTRL+Tab is detected.

It shouldn't be very difficult. You could use an Eventbox to catch the CTRL+Tab key combination, and then retrieve the number of pages in the Notebook. When the number of pages is equal to the currently selected page and CTRL+Tab is pressed, return the user to page 0.

Thats the theory anyway.

---

### Post by Rockiger on 2010-05-07
Thanks for the reply. This is what I have done so far:

```
class Notebook(gtk.Notebook):
    """The Notebook class
    """
    __gsignals__ = dict(
         forwardpage = (gobject.SIGNAL_RUN_LAST | gobject.SIGNAL_ACTION, None,  ()),
         	        )

    def __init__(self, mainAppWin):
        """
        """
        ...
        
        
        gtk.binding_entry_add_signal(self, gtk.keysyms.Tab,gtk.gdk.CONTROL_MASK, 'forwardpage')
        self.connect('forwardpage', self.onForwardPage)
        
        ...

```

The problem is, that <ctrl>+<tab> is predefined for "unfocus" if <tab> alone is not working. That means it is kind of blocked - how do I remove this behavior?

---

### Post by steeleyuk on 2010-05-07
OK, here's a probably really rough version of Ctrl+Tabbing through Notebook tabs. I stole/borrowed the event code [from Marco Islas]("http://www.islascruz.org/html/index.php?Blog/SingleView/id/Pygtk%3A-About-keyboard-accelerators").

It seems to work fine. This most likely isn't the best way to do it, though someone else might be able to help with any refinement. I've also added in the ability to shift tabs backwards as well using Ctrl+Shift+Tab.

```
#!/usr/bin/env python

import gtk

def catch_event(window, event):
    keyval = event.keyval
    name = gtk.gdk.keyval_name(keyval)
    mod = gtk.accelerator_get_label(keyval, event.state)

    if mod == "Ctrl+Mod2+Tab":
        if notebook.get_n_pages() == notebook.get_current_page() + 1:
            notebook.set_current_page(0)
        else:
            notebook.next_page()
    elif mod == "Shift+Ctrl+Mod2+ISO Left Tab":
        if notebook.get_current_page() == 0:
            notebook.set_current_page(notebook.get_n_pages() - 1)
        else:
            notebook.prev_page()
    

window = gtk.Window()
window.set_default_size(300, 200)

notebook = gtk.Notebook()
for page in range(5):
    box = gtk.VBox()
    label = gtk.Label("Page %s" % page)
    notebook.append_page(box, label)

window.connect("key-press-event", catch_event)
window.connect("destroy", lambda w: gtk.main_quit())

window.add(notebook)

window.show_all()

gtk.main()
```

---

### Post by Rockiger on 2010-05-08
Ok, thank you very much.

I will try this, tomorrow.

---

### Post by Rockiger on 2010-05-11
I found a solution to the problem:

1. I remove the <ctrl>+<tab> shortcut from the gtk.TextView - so this is not interrupting anymore
2. I set the <ctrl>+<tab> for my gtk.Notebook 

```
class Notebook(gtk.Notebook):
    """The Notebook class
    """
    ### New signal for pressing <ctrl>+<tab>
    __gsignals__ = dict(
         forwardpage = (gobject.SIGNAL_RUN_LAST | gobject.SIGNAL_ACTION, None,  ())
	        )
    

    def __init__(self, mainAppWin):
        ### remove <ctrl>+<tab> from gtk.TextView 
	gtk.binding_entry_remove (gtk.TextView, gtk.keysyms.Tab, gtk.gdk.CONTROL_MASK)

        # Make <ctrl>+<tab> emmit a signal called 'forwardpage'
        gtk.binding_entry_add_signal(self, gtk.keysyms.Tab,gtk.gdk.CONTROL_MASK, 'forwardpage')

        # connect signal to method
        self.connect('forwardpage', self.onForwardPage)
        
        
        self.show()
        

    def onForwardPage(self, war):
        self.next_page()     # go on page forward
```

Hope this is useful for others.

Cheers,
Marco

---

