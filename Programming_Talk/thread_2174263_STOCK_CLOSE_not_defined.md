---
title: "STOCK_CLOSE not defined?"
date: 2013-09-13
forum: Programming Talk
---

### Post by JKyleOKC on 2013-09-13
I'm creating a small weather applet based on the "textview-basic" example from the pygtk manual, and attempting to create its "Close" button using the STOCK_CLOSE definition as shown in several of the other examples. In every case, I get an error message that STOCK_CLOSE is not defined. What am I missing?

Here's the entire applet script, in its working condition. If I replace ("Close") with (stock=STOCK_CLOSE), as copied and pasted from other examples, I get the fatal error when running in the interpreter. ```
#!/usr/bin/env python

# example textview-basic.py

import pygtk
pygtk.require('2.0')
import gtk
import weather

class wxokc:
    def close_application(self, widget):
        gtk.main_quit()

    def __init__(self):
        window = gtk.Window(gtk.WINDOW_TOPLEVEL)
	window.set_default_size(585, 275)
        window.set_resizable(True)  
        window.connect("destroy", self.close_application)
        window.set_title("Weather at Will Rogers")
        window.set_border_width(2)

        box1 = gtk.VBox(False, 0)
        window.add(box1)
        box1.show()

        box2 = gtk.VBox(False, 10)
        box2.set_border_width(5)
        box1.pack_start(box2, True, True, 0)
        box2.show()

        sw = gtk.ScrolledWindow()
        sw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        textview = gtk.TextView()
        textbuffer = textview.get_buffer()
	textview.set_editable(False)
	textview.set_cursor_visible(False)
        sw.add(textview)
        sw.show()
        textview.show()
        box2.pack_start(sw)

        string = weather.get_metar(id="KOKC")
        textbuffer.set_text(string)

        [COLOR="#FF0000"]**button = gtk.Button("Close")**[/COLOR]
        button.connect("clicked", self.close_application)
        button.set_flags(gtk.CAN_DEFAULT)

        # Create an alignment object
        align = gtk.Alignment(1.0, 1.0, 0, 0)
        box2.pack_end(align, False, False, 2)
	align.add(button)

        button.show()
        align.show()
        window.show()

def main():
    gtk.main()
    return 0       

if __name__ == "__main__":
    wxokc()
    main()

```EDIT: You may have to install the "weather-util" package to have the "weather" module in place! I just ran the applet in another system, without the weather package, and got such an error message.

---

### Post by Bachstelze on 2013-09-13
Try gtk.STOCK_CLOSE. ;)

---

### Post by JKyleOKC on 2013-09-13
I thought I had tried that when copying and pasting from another example in the manual, but perhaps it was cached -- because making the change just now fixed it! Many thanks for prompting me to try again!

---

