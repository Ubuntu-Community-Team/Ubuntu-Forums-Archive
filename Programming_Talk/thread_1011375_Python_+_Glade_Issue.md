---
title: "Python + Glade Issue"
date: 2008-12-14
forum: Programming Talk
---

### Post by Old Marcus on 2008-12-14
Got a problem with a program I'm making. It basically has buttons which launch various programs. The menu quit button is confusing me though. How do I link it do I can close the program from it?

Code:
```
#!/usr/bin/env python

try:
	import sys
	import os
	import gtk
	import gtk.glade
except Exception, detail:
	print detail
	pass

try:
	import pygtk
	pygtk.require("2.0")
except Exception, detail:
	print detail
	pass

class mintTools:
	"""mintTools Tool"""

	def __init__(self):

		#Set the Glade file
		self.gladefile = "minttools.glade"
		self.wTree = gtk.glade.XML(self.gladefile)

		#Get the Main Window, and connect to the "destroy" event
		self.window = self.wTree.get_widget("window1")
		if (self.window):
			self.window.connect("destroy", gtk.main_quit)

		#Create our dictionary and connect it
		dic = { "on_btnAssist_clicked" : self.btnAssist_clicked,
			"on_btnBackup_clicked" : self.btnBackup_clicked,
			"on_btnInstall_clicked" : self.btnInstall_clicked,
			"on_btnNanny_clicked" : self.btnNanny_clicked,
			"on_btnUpdate_clicked" : self.btnUpdate_clicked,
			"on_btnDesktop_clicked" : self.btnDesktop_clicked,
			"on_quit1_activate" : self.quit1_activate }
		self.wTree.signal_autoconnect(dic)

	def quit1_activate(self, widget):
		gtk.main_quit

	def btnAssist_clicked(self, widget):
		os.system("/usr/bin/mintAssistant")

	def btnBackup_clicked(self, widget):
		os.system("/usr/lib/linuxmint/mintBackup/mintBackup.py")

	def btnInstall_clicked(self, widget):
		os.system("/usr/lib/linuxmint/mintInstall/frontend.py")

	def btnNanny_clicked(self, widget):
		os.system("gksu /usr/lib/linuxmint/mintNanny/mintNanny.py &")

	def btnUpdate_clicked(self, widget):
		os.system("gksu /usr/lib/linuxmint/mintUpdate/mintUpdate.py show 0 &")

	def btnDesktop_clicked(self, widget):
		os.system("/usr/lib/linuxmint/mintDesktop/mintDesktop_frontend.py")

if __name__ == "__main__":
	hwg = mintTools()
	gtk.main()

```

The menu item is labelled as 'quit1'. Also, how would I get the 'about' menu option to open an 'about' dialogue?

---

### Post by Old Marcus on 2008-12-15
Scratch the first problem, just had to add parentheses to the end of 'gtk.main_quit' so it would look like 'gtk.main_quit()'

---

