---
title: "Setting button height and width in python with gtk2"
date: 2010-07-23
forum: Programming Talk
---

### Post by The Midnight Coder on 2010-07-23
Hi.

I just started with pygtk and I cant seem to get the button to a certain height and width. I tried set_size_request but it doesn't seem to work. Can anybody help me with this?

This is my __init__ function:

```

	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("MyApp1")
		self.window.set_size_request(400,400)
		self.window.connect("delete_event",self.delete_event)
		
		self.box1 = gtk.HBox()
		
		self.quit_button = gtk.Button("Quit",gtk.STOCK_CLOSE)
		self.quit_button.set_size_request(20,20)
		self.quit_button.set_tooltip_text("Close this window")
		self.quit_button.connect("clicked",self.manual_quit)
		
		self.box1.pack_start(self.quit_button)
		
		self.window.add(self.box1)
		self.box1.show()
		self.quit_button.show()
		
		self.window.show()

```

---

### Post by nvteighen on 2010-07-23
What one usually does is to set the box's height and width and then tell that box how to distribute space among its contained widgets...

---

### Post by StephenF on 2010-07-23
You are using the default packing options which is for filling and expansion of widgets to fit the available space.
```

import gtk

class App(object):
	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("MyApp1")
		self.window.set_size_request(400,400)
		self.window.connect("delete_event",gtk.main_quit)
		
		self.box0 = gtk.VBox()
		self.box1 = gtk.HBox()
		self.box0.pack_start(self.box1, fill=False)
		self.box1.show()
		
		self.quit_button = gtk.Button("Quit",gtk.STOCK_CLOSE)
		self.quit_button.set_size_request(20,20)
		self.quit_button.set_tooltip_text("Close this window")
		self.quit_button.connect("clicked",gtk.main_quit)
		
		self.box1.pack_start(self.quit_button, fill=False)
		
		self.window.add(self.box0)
		self.box0.show()
		self.quit_button.show()
		
		self.window.show()
		
a = App()
gtk.main()

```
The size 20x20 is considerably smaller than the label text on the button. Removal of this yields a button that fits the size of its text.

---

### Post by The Midnight Coder on 2010-07-26
Thanks :) I had read up on the packing options but had forgotten about the fill, padding and expansion options :oops:

---

