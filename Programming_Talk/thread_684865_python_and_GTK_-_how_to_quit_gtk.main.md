---
title: "python and GTK - how to quit gtk.main"
date: 2008-02-01
forum: Programming Talk
---

### Post by Harvs on 2008-02-01
Hi

I'm just starting out with python and writing my first GUI with GTK and Glade.

I'm getting to understand the basics, but have hit a problem which I just can't understand why it won't work.

Here's the basic code:

```
    

#!/usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk
import gtk.glade


class Maths:

	def __init__(self):
		self.wTree = gtk.glade.XML('mathsglade.glade')
		dic = { "on_window1_destroy" : self.exit , "on_button1_clicked" : self.exit}
		self.wTree.signal_autoconnect(dic)
		self.win = self.wTree.get_widget("window1")
		self.win.show()

	def exit(self, widget):
		print "trying to quit....."
		gtk.main_quit
		

x = Maths()
gtk.main()


```

The problem is that it won't quit. I've got the quit button linked to the handler properly as it prints the "trying to quit..." message in the terminal. But the GUI window just sits there and won't go away!!

I'm obviously doing something wrong - but can't see what it is!

Any thoughts?

---

### Post by RIchard James13 on 2008-02-01
When you call gtk.main_quit outside of the dic line you need to write
gtk.main_quit()
not
gtk.main_quit

---

### Post by RIchard James13 on 2008-02-01
Also you should not need the self.win.show() if your window is not showing after loading it go back into the glade designer and select the top level window, go to the common tab and you will find the toggle visible is set to no. Set it to yes and re-save your glade file.

---

### Post by Harvs on 2008-02-03
Thanks Richard - made both changes (and updated the glade file to set to visible). Works just as I want now - cheers!

---

