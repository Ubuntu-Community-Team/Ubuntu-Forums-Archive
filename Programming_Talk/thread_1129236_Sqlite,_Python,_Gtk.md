---
title: "Sqlite, Python, Gtk"
date: 2009-04-18
forum: Programming Talk
---

### Post by matmatmat on 2009-04-18
```

# -*- coding: utf-8 -*-
import sys
import gtk
import sqlite
  
class Cataloger:
 
    def on_window_destroy(self, widget, data=None):
        gtk.main_quit()

    def on_add(self, widget, data=None):
	con = sqlite.connect('history.db')
	cur = con.cursor()
	self.namev = self.name.get_text()
	self.categoryv = self.category.get_active_text()
	self.priorityv = self.priority.get_active_text() 
	self.mediav = self.media.get_active_text()
	self.wherev = self.where.get_text()
	try:
	    cur.execute('insert into catalog(name, category, priority, media, location) values ("' + self.namev + '", "' + self.categoryv + '", ' + self.priorityv + ', "' + self.mediav + '", "' + self.wherev + '")')
            cur.execute('select * from catalog')
	    print cur.fetchone()

	except:
	    cur.execute('create table catalog(name TEXT, category TEXT, priority INT, media TEXT, location TEXT)') 
            cur.execute('insert into catalog(name, category, priority, media, location) values ("' + self.namev + '", "' + self.categoryv + '", ' + self.priorityv + ', "' + self.mediav + '", "' + self.wherev + '")')
	    cur.execute('select * from catalog')
	    print cur.fetchone()

    def __init__(self):
    
        builder = gtk.Builder()
        builder.add_from_file("history_file_cataloger.xml") 
        self.window = builder.get_object("window1")
	self.name = builder.get_object("inname")
	self.category =  builder.get_object("incategory")
	self.priority = builder.get_object("inpriority")
	self.media = builder.get_object("inmedia")
	self.where = builder.get_object("inwhere")
        builder.connect_signals(self)       
    
if __name__ == "__main__":
    win = Cataloger()
    win.window.show()
    gtk.main()

```
When run I get:
```

matio@ubuntu:~/Documents$ python history_file_cataloger.py 
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')
('a', 'Buildings', 1, 'Video', 'a')

```
(I've entered all that - kept clicking add, not from the select * from catalog)
when i look in the db file there isn't anything!
Glade file:
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Sat Apr 18 18:00:49 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <signal name="destroy_event" handler="on_window_destroy"/>
    <child>
      <widget class="GtkNotebook" id="notebook1">
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <child>
          <widget class="GtkTable" id="table2">
            <property name="visible">True</property>
            <property name="n_rows">6</property>
            <property name="n_columns">2</property>
            <child>
              <widget class="GtkEntry" id="inwhere">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">4</property>
                <property name="bottom_attach">5</property>
              </packing>
            </child>
            <child>
              <widget class="GtkComboBox" id="inmedia">
                <property name="visible">True</property>
                <property name="items" translatable="yes">Video
Text
Picture
Other</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">3</property>
                <property name="bottom_attach">4</property>
              </packing>
            </child>
            <child>
              <widget class="GtkComboBox" id="inpriority">
                <property name="visible">True</property>
                <property name="items" translatable="yes">1
2
3</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">2</property>
                <property name="bottom_attach">3</property>
              </packing>
            </child>
            <child>
              <widget class="GtkComboBox" id="incategory">
                <property name="visible">True</property>
                <property name="items" translatable="yes">Buildings
Date opened
Discipline
Uniform
Teaching Methods
Staff</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkEntry" id="inname">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkLabel" id="where">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Where?</property>
              </widget>
              <packing>
                <property name="top_attach">4</property>
                <property name="bottom_attach">5</property>
              </packing>
            </child>
            <child>
              <widget class="GtkLabel" id="media">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Media</property>
              </widget>
              <packing>
                <property name="top_attach">3</property>
                <property name="bottom_attach">4</property>
              </packing>
            </child>
            <child>
              <widget class="GtkLabel" id="priority">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Priority
(1 - High, 2 - Low)</property>
              </widget>
              <packing>
                <property name="top_attach">2</property>
                <property name="bottom_attach">3</property>
              </packing>
            </child>
            <child>
              <widget class="GtkLabel" id="category">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Category</property>
              </widget>
              <packing>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkLabel" id="name">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Name</property>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="add">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Add</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_add"/>
              </widget>
              <packing>
                <property name="top_attach">5</property>
                <property name="bottom_attach">6</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="quit">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Quit</property>
                <property name="response_id">0</property>
                <signal name="pressed" handler="on_window_destroy"/>
                <signal name="clicked" handler="on_window_destroy"/>
              </widget>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">5</property>
                <property name="bottom_attach">6</property>
              </packing>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkLabel" id="insert">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Insert</property>
          </widget>
          <packing>
            <property name="type">tab</property>
            <property name="tab_fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="GtkVBox" id="vbox2">
            <property name="visible">True</property>
            <child>
              <widget class="GtkTextView" id="txtquery">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkHBox" id="hbox1">
                <property name="visible">True</property>
                <child>
                  <widget class="GtkLabel" id="labelquery">
                    <property name="visible">True</property>
                    <property name="label" translatable="yes">Query:</property>
                  </widget>
                </child>
                <child>
                  <widget class="GtkEntry" id="inquery">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                  </widget>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="btnquery">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Query</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_query"/>
              </widget>
              <packing>
                <property name="position">2</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkLabel" id="query">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Query</property>
          </widget>
          <packing>
            <property name="type">tab</property>
            <property name="position">1</property>
            <property name="tab_fill">False</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

---

### Post by matmatmat on 2009-04-20
bump

---

### Post by dandaman0061 on 2009-04-20
First of all... you might want to ask the question directly before posting the code, and stating the outcome.

Assuming you want your data to be persistent in the db:
It doesn't look like you are committing your data.  You need to put a cur.commit() either in the on_add function or whereever it seems most logical.

Another tip: if you're using sqlite version 3+, import sqlite3 instead of 'sqlite'.  I believe this is the standard.

[http://docs.python.org/library/sqlite3.html]("http://docs.python.org/library/sqlite3.html")

---

### Post by matmatmat on 2009-04-21
Thanks for the reply, I now have this code it isn't writing into the table but there is data in the history.db file and there is a 'u' character:
```

import sys
import gtk
import sqlite3 as sqlite
  
class Cataloger:
 
    def on_window_destroy(self, widget, data=None):
        gtk.main_quit()

    def on_add(self, widget, data=None):
	con = sqlite.connect('history.db')
	cur = con.cursor()

	self.namev = self.name.get_text()
	self.categoryv = self.category.get_active_text()
	self.priorityv = self.priority.get_active_text() 
	self.mediav = self.media.get_active_text()
	self.wherev = self.where.get_text()

	try:
	    cur.execute('insert into catalog(name, category, priority, media, location) values ("' + self.namev + '", "' + self.categoryv + '", ' + self.priorityv + ', "' + self.mediav + '", "' + self.wherev + '")')
	    con.commit()
            cur.execute('select * from catalog')
            print cur.fetchone()
	
	except:
	    try: 
		cur.execute('CREATE TABLE catalog(name TEXT, category TEXT, priority INT, media TEXT, location TEXT)') 
	    	con.commit()
	    except:
		print
	    cur.execute('insert into catalog(name, category, priority, media, location) values ("' + self.namev + '", "' + self.categoryv + '", ' + self.priorityv + ', "' + self.mediav + '", "' + self.wherev + '")')
	    con.commit()
	    cur.execute('select * from catalog')
	    print cur.fetchone()

    def __init__(self):
    
        builder = gtk.Builder()
        builder.add_from_file("history_file_cataloger.xml") 
        self.window = builder.get_object("window1")
	self.name = builder.get_object("inname")
	self.category =  builder.get_object("incategory")
	self.priority = builder.get_object("inpriority")
	self.media = builder.get_object("inmedia")
	self.where = builder.get_object("inwhere")
        builder.connect_signals(self)       
    
if __name__ == "__main__":
    win = Cataloger()
    win.window.show()
    gtk.main()


```

```

matio@ubuntu:~/Documents$ python history_file_cataloger.py 
(u'1', u'Buildings', 1, u'Video', u'1')
(u'1', u'Buildings', 1, u'Video', u'1')

```
(entered the same thing twice)

---

