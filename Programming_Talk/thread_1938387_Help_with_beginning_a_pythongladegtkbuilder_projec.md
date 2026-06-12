---
title: "Help with beginning a python/glade/gtkbuilder project please!"
date: 2012-03-09
forum: Programming Talk
---

### Post by jondecker76 on 2012-03-09
Hello

I have many years of programming experience, though I'm new to glade, python and gtkbuilder.  I'm trying to do some simple tests working towards completing a gimp plugin for my wife's photography business.  While I normally research and learn on my own, I can't find any decent examples anywhere using python glade and gtkbuilder together.  Here is a simple example where I want to display a simple messageDialog.  I have no problem defining it in glade, nor getting it to show up on the screen.. However, I can't for the life of me figure out how to set the text or secondary text of the dialog - so it just sits there blank :(

What am I doing wrong?
```

#! /usr/bin/env python

#import gimpplugin
import time

# UI Includes
import sys

try:
	import gtk

except:
	sys.exit(1)
import pygtk # Do I even need pygtk, or is the gtk import above enough??

# Logging stuff...
import logging
logger = logging.getLogger('myapp')
hdlr = logging.FileHandler('test.log',mode="wb")
formatter = logging.Formatter('%(asctime)s %(levelname)s %(message)s')
hdlr.setFormatter(formatter)
logger.addHandler(hdlr) 
logger.setLevel(logging.INFO)

#UI Class
class UI():
	def __init__(self):
		self.gladefile = "DPplugin.glade"  
		self.builder=gtk.Builder()
		self.builder.add_from_file(self.gladefile)
		self.builder.connect_signals(self)
		return

	def InfoDialog(self,title,message):
		self.infoMessageDialog=self.builder.get_object("infoMessageDialog")
		self.infoMessageDialog.text=title ###<- WHY WONT THIS WORK??
		self.infoMessageDialog.show_all()
		return

#class myplugin(gimpplugin.plugin):
class myplugin():
	def init(self):
		# initialisation routines
		# called when gimp starts.
		logger.info('Plugin initializing...')
		# Set the glade file
		self.UI=UI()

		return
	def quit(self):
		# clean up routines
		# called when gimp exits (normally).
		logger.info('Plugin deinitializing...')

		self.UI.InfoDialog(self,"hi")
		# Needed by all GTK programs
		gtk.main()
		time.sleep(10)
		return
	def query(self):
		# called to find what functionality the plugin provides.
		#gimp.install_procedure("procname", ...)
		
		return

	# note that this method name matches the first arg of
	# gimp.install_procedure
	#def procname(self, arg1, ...):
	def procname(self):
		# do what ever this plugin should do
		return

blah=myplugin()
blah.init()
blah.quit()


```


Please ignore the messy code, I'm just trying some simple tests to learn some things...


thanks for any help!

---

### Post by r-senior on 2012-03-09
I feel your pain, I'm playing with Python and GTK3 at the moment and there's a lot of reading between the lines to be done.

Perhaps the first thing to point out is that using PyGTK (which is what the import gtk does) means you are using GTK+, not the latest GTK3. That might be the best choice for a GIMP plugin, I don't know. But it's worth looking into.

For PyGTK, this is a good tutorial (but no Glade)

[http://zetcode.com/tutorials/pygtktutorial/](http://zetcode.com/tutorials/pygtktutorial/)

For GKT3 with Python:

[http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)

The latter has a very small example of using Glade.

I'd suggest looking at some of these tutorial examples without Glade to start with because the same layout principles are applied with Glade, albeit graphically. Understanding boxes, grids, actions, action groups, how dialogs work, etc. is all worthwhile, as is the general code structure and use of subclasses.

A simple message dialog is not really worth doing in Glade because the constructor pretty much gives everything you need:

[http://zetcode.com/tutorials/pygtktutorial/dialogs/](http://zetcode.com/tutorials/pygtktutorial/dialogs/)

Something I tend to do with Glade is create the top-level windows in code and use the Glade file to layout the content - maybe getting a grid or box from the Glade file rather than a window or dialog. I don't know if that's the way it's suppose to be done.

---

### Post by oldfred on 2012-03-09
I have not used GTK3, yet. And have been experimenting with qt lately. 

But I have to connect builder objects you want to refer to, to my python object like this:

```
        self.window1 = self.builder.get_object("window1")
        self.label1 = self.builder.get_object("label1")
        self.treeview = self.builder.get_object("treeview1")
        self.label2 = self.builder.get_object("label2")

```

Then use the window

```
    def main(self):
        #self.window.maximize()
        self.window1.show()
        gtk.main()

```

builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

---

