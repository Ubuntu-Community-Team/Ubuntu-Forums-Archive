---
title: "Critical. TreeView don't show elements!"
date: 2013-01-22
forum: Programming Talk
---

### Post by bogdannix on 2013-01-22
I use GTK and Python to develop an application.
I want to load TreeView elements(1 column) from SQLite3 database.
But something go wrong(without any error)! :(
Here is a whole code:
```

#!/usr/bin/python
import sys
import sqlite3 as sqlite
from gi.repository import Gtk
from gi.repository import Notify
	
def notify(notifer, text, notificationtype=""):
	Notify.init("Application")
	notification = Notify.Notification.new (notifer, text, notificationtype)
	notification.show ()
	
def get_object(gtkname):
	builder = Gtk.Builder()
	builder.add_from_file("main.ui")
	return builder.get_object(gtkname)
	
def base_connect(basefile):
	return sqlite.connect(basefile)

class Handler:
	
	def main_destroy(self, *args):
		Gtk.main_quit(*args)
    
	def hardwaretool_clicked(self, widget):
		baselist = get_object("subjectlist")
		baselist.clear()
		base = base_connect("subjectbase")
		with base:
			cur = base.cursor()
			cur.execute("SELECT * FROM sub")
			while True:
				row = cur.fetchone()
				if row == None:
					break
				iter = baselist.append()
				print "row ", row[0]
				baselist.set(iter, 0, row[0])
			cur.close()
		
	def gamestool_clicked(self, widget):
		print("gamestool clicked!!!!! =)")

	def appstool_clicked(self, widget):
		print("appstool clicked!!!!! =)")
		
	def fixtool_clicked(self, widget):
		notify("Charmix","Fix Applied", "dialog-ok")
		
	def brokenfixtool_clicked(self, widget):
		notify("Charmix","Broken Fix Report Sended", "dialog-error")
		
	def sendfixtool_clicked(self, widget):
		notify("Charmix","Fix Sended", "dialog-information")

class CharmixMain:
     
	def __init__(self):
    
		builder = Gtk.Builder()
		builder.add_from_file("main.ui")
		
		self.window = builder.get_object("main")
		
		self.subject = builder.get_object("subjectlist")
		self.problem = builder.get_object("problemlist")
		
		self.toolbar = builder.get_object("toolbar")
		self.hardwaretool = builder.get_object("hardwaretool")
		self.gamestool = builder.get_object("gamestool")
		self.appstool = builder.get_object("appstool")
		self.fixtool = builder.get_object("fixtool")
		self.brokenfixtool = builder.get_object("brokenfixtool")
		self.sendfixtool = builder.get_object("sendfixtool")
		
		builder.connect_signals(Handler())
		
		context = self.toolbar.get_style_context()
		context.add_class(Gtk.STYLE_CLASS_PRIMARY_TOOLBAR)
		
if __name__ == "__main__":
	Charmix = CharmixMain()
	Charmix.window.show()
	Gtk.main()


```

I'm interested in this part (not working normally):
```

def hardwaretool_clicked(self, widget):
		baselist = get_object("subjectlist")
		baselist.clear()
		base = base_connect("subjectbase")
		with base:
			cur = base.cursor()
			cur.execute("SELECT * FROM sub")
			while True:
				row = cur.fetchone()
				if row == None:
					break
				iter = baselist.append()
				print "row ", row[0]
				baselist.set(iter, 0, row[0])
			cur.close()

```

TreeView(subjecttree) don't display anything but ```
print "row ", row[0]
``` works fine and display all the strings.

Please, help me. 
Maybe i need to repaint TreeView or thomething like that?
How can I get it?
:|

---

