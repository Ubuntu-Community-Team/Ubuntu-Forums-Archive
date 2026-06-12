---
title: "[SOLVED] Event Handling PyGTK Program With Gladefile"
date: 2008-02-25
forum: Programming Talk
---

### Post by Glaxed on 2008-02-25
Hello, I am having a big roadblock with PyGTK.
I used Glade(3) Interface Designer to make a nice Gladefile, and I am able to see the GUI finally (what a headache, the gladefile didn't have the "visible" property for the main window =p).
I have a File Chooser Widget, but the documentation I found was fuzzy about actually getting a file location... This is what I have, excluding the gladefile.
```

#!/usr/bin/env python
try:
 	import pygtk, sys, os, time, gtk, gtk.glade
  	pygtk.require("2.0")
except:
	print "Missing essential Python modules."; break

class ReadBin:
	def __init__(self):
		self.widgets = gtk.glade.XML("Main.glade", "Window")
		EVT = {
			"on_Frame_destroy" : gtk.main_quit,
                        # here is where i am confused 
			"on_doFile" : self.doFile
		}
		self.widgets.signal_autoconnect(EVT)

	def doFile(self, widget):
		print 1, 2, 3
		fn = self.get_filename()
		print fn

ReadBin()
gtk.main()

```

My glade file has the 'file-activated' signal, with the 'doFile' handler. Nothing happens when I pick a file, though.
Any help is greatly appreciated!

---

### Post by Glaxed on 2008-02-26
I understand that lots of people manually (in-source) construct widgets and bind them to events, and I've tried it too, it's just that using Glade seems very convenient, and I'd love to get it working...
This is essentially a bump (sorry), because I have no new information. But I've been combing Python and C docs for gtk and still cant get this to workl...

edit: nvm, check this out, any problems
[xml]
<widget class="GtkFileChooserWidget" id="File">
  <property name="visible">True</property>
  <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK</property>
  <signal name="file-activated" handler="doFile"/>
[/xml]
It looks to me that the chosen events dont activate the file-activated signal on user file selection.... Hmm..

---

### Post by Glaxed on 2008-02-26
```

#!/usr/bin/env python
try:
 	import pygtk, sys, os, time, gtk, gtk.glade
  	pygtk.require("2.0")
except:
	print "Missing essential Python modules."; break

class ReadBin:
	def __init__(self):
		xml = gtk.glade.XML("Main.glade")
		self.window = xml.get_widget("Window")
		self.box = xml.get_widget("Box")
		self.view = xml.get_widget("View")
		self.file = xml.get_widget("File")
		self.text = xml.get_widget("Text")
		self.name = xml.get_widget("Name")
		self.file.connect("file_activated", self.doFile)
		self.window.show()

	def doFile(self, widget):
		fn = self.file.get_filename()
		print fn

ReadBin()
gtk.main()

```
Solved!

---

