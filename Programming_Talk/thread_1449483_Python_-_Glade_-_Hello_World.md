---
title: "Python - Glade - Hello World"
date: 2010-04-07
forum: Programming Talk
---

### Post by WillFerrellLuva on 2010-04-07
Im trying to get create a simple hello world gui with glade and python, but keep getting the following error:
```

Traceback (most recent call last):
  File "/home/chris/Code/Python/Projects/test.py", line 17, in <module>
    hwg = HellowWorldGTK()
  File "/home/chris/Code/Python/Projects/test.py", line 9, in __init__
    self.wTree = gtk.glade.XML("test.glade")
RuntimeError: could not create GladeXML object

```

here is test.py:
```

#!/usr/bin/env python
import pygtk
import gtk
import gtk.glade

class HellowWorldGTK:
    """This is a Hello World GTK application"""
    def __init__(self):
        self.wTree = gtk.glade.XML("test.glade")
        dic = {	"on_mainWindow_destroy": (gtk.main_quit), "on_close_destroy": (gtk.main_quit)}
        self.wTree.signal_autoconnect(dic)
        self.win = self.wTree.get_widget("mainWindow")
        self.win.show()
       
    
if __name__ == "__main__":
    hwg = HellowWorldGTK()
    gtk.main()

```

and test.glade:
```

<?xml version="1.0"?>
<interface>
  <!-- interface-requires gtk+ 2.10 -->
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="mainWindow">
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <property name="orientation">vertical</property>
        <child>
          <object class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Hello World!</property>
          </object>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkButton" id="close">
            <property name="label">gtk-close</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="use_stock">True</property>
            <signal name="destroy" handler="on_close_destroy"/>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```

Any help would be greatly appreciated.

---

### Post by n0dix on 2010-04-07
Are you sure your version pygtk is correct?
I find the following example in Internet:
```

#!/usr/bin/env python

import sys
try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
except:
	sys.exit(1)

class HellowWorldGTK:
	"""This is an Hello World GTK application"""

	def __init__(self):
		
		#Set the Glade file
		self.gladefile = "pyhelloworld.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile) 
		
		#Create our dictionay and connect it
		dic = { "on_btnHelloWorld_clicked" : self.btnHelloWorld_clicked,
			"on_MainWindow_destroy" : gtk.main_quit }
		self.wTree.signal_autoconnect(dic)

	def btnHelloWorld_clicked(self, widget):
		print "Hello World!"


if __name__ == "__main__":
	hwg = HellowWorldGTK()
	gtk.main()

```
Here's the [link]("http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm").

---

### Post by WillFerrellLuva on 2010-04-07
still get the error with the import exception statements.  Will check out that link again though.

---

### Post by oldfred on 2010-04-08
Are you using glade2? Glade3 uses builder.

[http://ubuntuforums.org/showthread.php?t=1440503](http://ubuntuforums.org/showthread.php?t=1440503)

---

### Post by WillFerrellLuva on 2010-04-08
Yeah I have glade 3.  I had to change a setting from gtkbuilder to libglade and then the glade files would open.  tyvm for the help

---

