---
title: "Problems with simple PyGTK Program"
date: 2010-01-06
forum: Programming Talk
---

### Post by Tahakki on 2010-01-06
```
import pygtk, gtk
import time

on_button_clicked = None

class GTK_Main:

    def __init__(self):

	window = gtk.Window(gtk.WINDOW_TOPLEVEL)
	window.set_title("Roffle")
        window.connect("destroy", gtk.main_quit, "WM destroy")

        vbox = gtk.VBox(homogeneous=False, spacing=3)
        window.add(vbox)

	toolbar = gtk.Toolbar()
	vbox.add(toolbar)
	image = gtk.Image()
	image.set_from_file("/home/joel/Pictures/Webcam/epicfail.jpg")
	label = gtk.Label("60sec")
	toolbar.add(label)
	stop_button = gtk.Button(label="Stop", stock=None, use_underline=False)
	toolbar.add(stop_button)
	brush_button = gtk.Button(label="Choose Brush", stock=None, use_underline=False)
	toolbar.add(brush_button)
        def on_button_clicked(brush_button):
            choose.run()
	    if choose.run() == gtk.RESPONSE_OK:
    	        image.set_from_file(choose.get_filename())
	    elif choose.run() == gtk.RESPONSE_CANCEL:
    	        print 'Closed, no files selected'
	    choose.destroy()
	brush_button.connect("clicked", on_button_clicked)
	hbox = gtk.HBox(homogeneous=False, spacing=3)
	vbox.add(hbox)
	hbox.add(image)
	vert_tools = gtk.Toolbar()
	vert_tools.set_orientation(gtk.ORIENTATION_VERTICAL)
	hbox.add(vert_tools)
	choose = gtk.FileChooserDialog(title="Choose Photo", parent=None, action=gtk.FILE_CHOOSER_ACTION_OPEN, buttons=(gtk.STOCK_CANCEL,gtk.RESPONSE_CANCEL,gtk.STOCK_OPEN,gtk.RESPONSE_OK))

        window.show_all()

GTK_Main()
gtk.main()
```

This program simply opens an image. That's all so far.

Does anybody know why I have to click buttons twice in the dialog, or why it fails when opened a second time?

Thanks.

---

### Post by kostkon on 2010-01-06
Try changing it to:
```
def on_button_clicked(brush_button):
         choose_response = choose.run()
	  if choose_response == gtk.RESPONSE_OK:
    	     image.set_from_file(choose.get_filename())
	  elif choose_response == gtk.RESPONSE_CANCEL:
    	     print 'Closed, no files selected'
          choose.hide()

```
It fails because you destroy the *choose* file chooser dialog and you don't recreate it at the start of the *on_button_clicked* method. But you don't need to destroy it.

---

### Post by Tahakki on 2010-01-06
Thanks, that's solved the failing issue, but why do I still have to click the button multiple times?

---

### Post by kostkon on 2010-01-06
> **Tahakki said:**
> Thanks, that's solved the failing issue, but why do I still have to click the button multiple times?
What do you mean by that, could you be more specific?

---

### Post by Tahakki on 2010-01-06
Basically, when clicking either the 'Open' or 'Cancel' buttons in the dialog, it seems to take two clicks to activate instead of one.

By the way, how's the layout/order of this program? It seemed to me very messy, as I'm sort of learning as I go along.

---

### Post by Tahakki on 2010-01-08
Bump!

---

### Post by steeleyuk on 2010-01-08
```
import pygtk, gtk, time

class GTK_Main:
    def __init__(self):
        def on_button_clicked(brush_button):
            response = choose.run()
            if response == gtk.RESPONSE_OK:
    	        image.set_from_file(choose.get_filename())
            elif response == gtk.RESPONSE_CANCEL:
    	        print 'Closed, no files selected'
    	    choose.hide()

        window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        window.set_title("Roffle")
        
        vbox = gtk.VBox(homogeneous=False, spacing=3)
        
        toolbar = gtk.Toolbar()
        
        image = gtk.Image()
        image.set_from_file("/home/joel/Pictures/Webcam/epicfail.jpg")
        label = gtk.Label("60sec")
        
        stop_button = gtk.Button(label="Stop", stock=None, use_underline=False)
        brush_button = gtk.Button(label="Choose Brush", stock=None, use_underline=False)
        
        hbox = gtk.HBox(homogeneous=False, spacing=3)

        vert_tools = gtk.Toolbar()
        vert_tools.set_orientation(gtk.ORIENTATION_VERTICAL)
        hbox.add(vert_tools)
        
        window.add(vbox)
        vbox.add(toolbar)
        toolbar.add(label)
        toolbar.add(stop_button)
        toolbar.add(brush_button)
        vbox.add(hbox)
        hbox.add(image)

        window.connect("destroy", gtk.main_quit)
        brush_button.connect("clicked", on_button_clicked)

        window.show_all()
        
        choose = gtk.FileChooserDialog(title="Choose Photo", parent=None, action=gtk.FILE_CHOOSER_ACTION_OPEN, buttons=(gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OPEN, gtk.RESPONSE_OK))

GTK_Main()
gtk.main()
```

I've updated your code to make the dialog respond to the first click. It was simply a case of editing the function slightly.

I've moved some of the code around as well for this, but the way you set your code out is down to your own style. For example, I prefer to create my widgets in batches, i.e. create all at once, pack them, connect them, then display as above. Some people however prefer to handle the creation, packing, connecting and displaying for each widget as they go, similar to how you did it initially.

My only other suggestion would be to use the [gtk.ToolButton]("http://www.pygtk.org/docs/pygtk/class-gtktoolbutton.html") rather than placing a standard button on the toolbar. Using ToolButton allows for GNOME (or other DE) to control the size and style of the button, whether to display text or not, etc.

---

