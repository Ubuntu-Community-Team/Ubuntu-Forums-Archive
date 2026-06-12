---
title: "what's a good language for writing gui applications?"
date: 2008-03-02
forum: Programming Talk
---

### Post by provisional_idiot on 2008-03-02
looking for something like visual basic, only open source

thanks

---

### Post by Can+~ on 2008-03-02
Well, all depends on you want to do:

Build applications that work in both Gnome and Windows?
What language you already now?

The most Visual-Basic thing I can think of is Python/C with Glade, or WXwidgets with STE, I personally use PyGTK+Glade combo. Mono uses C#, but I don't know if it has the drag and drop kind of interface, as I never installed it.

---

### Post by provisional_idiot on 2008-03-02
i only want to work with GNOME... don't really have much experience programming gui's, but i do know c++ pretty well and I d be willing to learn python, or any language, as long as it makes the constructing a gui interface easy

---

### Post by Can+~ on 2008-03-02
Glade Interface Designer (3).

[IMG]http://img.photobucket.com/albums/v517/CanXp/1.jpg[/IMG]

```
sudo apt-get glade-3
```

Glade makes interfaces and stores them on plain ol' XML. Later, you can decide what language to use, I went for python,

The thing is that, with python or C, you can go ahead and make interfaces directly from a text file like:

```
import pygtk
import gtk

class mainWindow:
	def myFunc(self, widget, data=None):
		self.x += 1
		print "%d: invoked by %s" % (self.x, widget)
	
	def destroy(self, widget, data=None):
		gtk.main_quit()
	
	def __init__(self):
		self.x = 1
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.mybutton = gtk.Button("w0000000000000000000t")
		self.window.connect("delete_event", self.destroy)
		hid = self.mybutton.connect("clicked", self.myFunc, None)
		
		self.window.add(self.mybutton)
		
		self.mybutton.show()
		self.window.show()

	def main(self):
		gtk.main()
	


print __name__
if (__name__ == "__main__"):
	mwin = mainWindow()
	mwin.main()
```

Or load the XML (which is way easier) and connect the respective signals.

```
import gtk
import gtk.glade

class mainWindow:
	#-----------Events------------
	def event_destroy(self, widget, data=None):
		gtk.main_quit()
		return False
	
	def event_add(self, widget, data=None):
		self.entry.set_text("W00t")
	
	#-----------Constructor------------
	def __init__(self):
		#Load Glade
		self.gladeRef = "test01.glade"
		self.wTree = gtk.glade.XML(self.gladeRef)
		self.window = self.wTree.get_widget("MainWindow")
		self.entry = self.wTree.get_widget("emain")

		#Signals
		self.window.connect("delete_event", self.event_destroy)
		signals = { \
		"event_destroy" : self.event_destroy, \
		"event_add" : self.event_add }
		
		self.wTree.signal_autoconnect(signals)
		
		#Show All
		self.window.show_all()

	#-----------Main loop------------
	def main(self):
		gtk.main()

if (__name__ == "__main__"):
	mwin = mainWindow()
	mwin.main()
else:
	print "Error: Not main."

```


I personally think that learning PyGTK first, and later moving to glade it's the best way to learn how packing works.

---

### Post by stratavarious on 2008-03-02
.

---

### Post by RafG on 2008-03-02
> **Can+~ said:**
> Mono uses C#, but I don't know if it has the drag and drop kind of interface, as I never installed it.

[MonoDevelop]("http://www.monodevelop.com") has an [integrated GUI designer]("http://www.monodevelop.com/Image:Stetic-in-monodevelop.png").

---

