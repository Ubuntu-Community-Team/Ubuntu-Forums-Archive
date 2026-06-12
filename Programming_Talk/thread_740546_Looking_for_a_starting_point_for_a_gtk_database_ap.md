---
title: "Looking for a starting point for a gtk database app"
date: 2008-03-30
forum: Programming Talk
---

### Post by zombiepig on 2008-03-30
I'm wanting to make a very basic little database app for tracking repair jobs at my workplace. I'd like to do this in gtk/python/sqlite, but don't see the point in starting from scratch. Does anyone know any well-coded basic little database apps out there I could use as a starting point?

(I realize I could easily do this in a spreadsheet/etc, but I'm trying to extend my programming knowledge!)

---

### Post by tempest on 2008-03-30
If you are looking for an actual database and graphical client you could use mysql-server as the database and the mysql-query-browser application to query the database. If you are looking for something along the lines of a MS Access database you could use the   openoffice.org-base application. It is similar to access but uses a slightly different query language.

---

### Post by Can+~ on 2008-03-30
I made one, pretty simple, it just displays the content of one, and adds new rows:

[PHP]#!/usr/bin/env python

import gtk
import gtk.glade
import sqlite3

class mainWindow():
	def add_event(self, widget, data=None):
		"""Event executed when user presses the 'add' button.
		Appends value of self.entry to the treestore"""
		
		val = self.entry.get_text().strip()
		if (val != ""):
			self.store.append((val, val))
		
	def save_event(self, widget, data=None):
		"""Event executed when user presses the 'save' button.
		Truncates (clears) table and iterates the treestore and inserts it.
		When iteration is complete it commits the content."""
		
		try:
			self.curs.execute("""delete from coldata""")
			for i in self.store:
				self.curs.execute("""insert into coldata values (?, ?)""", i)
			self.conn.commit()
			print "values saved!"
		except sqlite3.OperationalError:
			print "OMFG ERROR"
	
	def select_event(self, widget, data=None):
		iter = widget.get_selection().get_selected()

	
	def destroy_event(self, widget, data=None):
		gtk.main_quit()
		return False
	
	def loadTable(self, treestr):
		self.conn = sqlite3.connect("sqlcols")
		self.curs = self.conn.cursor()
		
		try:
			self.curs.execute("""select * from coldata""")
			
			print "Table exists. Loading..."
			
			for row in self.curs:
				treestr.append(row)
				
				
		except sqlite3.OperationalError:
			print "Table does not exist, creating it."
			self.curs.execute("""create table coldata (name text, data text)""")
			self.curs.execute("""insert into coldata values ('Test', 'zzzz')""") # Sample rows
			self.curs.execute("""insert into coldata values ('Roflpie', 'waffles')""") #Another one
			self.conn.commit()
	
	def __init__(self):
		self.xml = gtk.glade.XML("colview.glade")
		self.win = self.xml.get_widget("window1")
		self.cview = self.xml.get_widget("treeview1")
		self.store = gtk.ListStore(str, str)
		self.entry = self.xml.get_widget("entry1")
		
		#self.asdf = gtk.TreeRowReference.copy()
		
		self.loadTable(self.store)		
		self.cview.set_model(self.store)
		
		self.cellr = gtk.CellRendererText()
		self.colls = [gtk.TreeViewColumn("Name"), gtk.TreeViewColumn("Value")]
		self.colls[0].pack_start(self.cellr)
		self.colls[1].pack_start(self.cellr)
		
		self.cview.append_column(self.colls[0])
		self.cview.append_column(self.colls[1])
		self.colls[0].add_attribute(self.cellr, "text", 0)
		self.colls[1].add_attribute(self.cellr, "text", 1)
		
		self.win.connect("delete_event", self.destroy_event)
		self.__signals__ = { \
			"save_event" : self.save_event, \
			"add_event" : self.add_event, \
			"select_event" : self.select_event }
			
		self.xml.signal_autoconnect(self.__signals__)
		
		self.win.show_all()
	
	def gtk_main(self):
		gtk.main()
		
if __name__ == "__main__":
	a = mainWindow()
	a.gtk_main()
[/PHP]

It's old, it's probably not optimal, but it's something. I attached the file with an example table, and the glade file.

---

### Post by pmasiar on 2008-03-30
Looks like it is multi-user app? Better than doing desktop, consider web-based app. Deployment and upgrades are easier (you just change server), all runs in browser. But of course browser-based apps are not as dynamic and user friendly as desktop, although you can do lot of cool tricks with AJAX.

Django or TurboGears are very flexible web app frameworks, I prefer TG. It includes development server (CherryPy, you can use it also for light production, if you have like max 5-10 page hits per minute, you will be fine). Follow tutorial, you will have your own web app (a wiki) running within hour, including installation.

SQLite is fine for this kind of app, no reason to struggle with full blown database server as MySQL until you have real hard requirements for performance - and then I would consider PostgreSQL too, because it has more flexible embedded languages (including Python in triggers - how cool is that! :-) )

If you need desktop GUI, EasyGUI is good simple start.

---

### Post by jjgauthi on 2008-03-30
Question about SQLite, how would I go about installing it?

Thanks in advance.

---

### Post by mssever on 2008-03-30
> **jjgauthi said:**
> Question about SQLite, how would I go about installing it?
```
sudo aptitude install sqlite3
```

---

### Post by pmasiar on 2008-03-30
Python 2.5 comes with sqlite and pysqlite installed.

---

