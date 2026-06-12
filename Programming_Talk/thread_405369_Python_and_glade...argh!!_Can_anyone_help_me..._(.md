---
title: "Python and glade...argh?!?! Can anyone help me... :("
date: 2007-04-09
forum: Programming Talk
---

### Post by viciouslime on 2007-04-09
I am trying to make something that will rip dvds based on quickrip. This is my first ever python project, it's just something to try and help me learn it. I have followed numerous tutorials and learnt a lot today, but one thing I can't seem to get working is setting properties of gtk elements.

For example, when I click a button, I can get the code to recognise this and display an output to the terminal, but I can't get it to move a progress bar, or display something in a status bar.

I have the following code:

```
#!/usr/bin/env python
#Various stuff from quickrip
from __future__ import generators
from time import sleep
import sys, os, re, popen2, ConfigParser, copy, threading, thread
import config   # ViciousRip global configuration


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

# ViciousRip global configuration.
import config   

__app__ = config.app
__author__ = config.author
__version__ = config.version
__date__ = config.date
__copyright__ = config.copyright
__license__ = config.license


try:
	import mmpython
except:
	print "*** FATAL ERROR: Can't import mmpython!"



class ViciousRip:
	"""ViciousRip base class, including the following methods:
	initialise	- replaces the __init__ function which is overwritten with inheritance
	loadConfig	- loads the user configuration file
	cautiousLoad	- loads a config variable in an exception clause
	findProgram	- takes a program name, returns the full path
	calcRate	- calculates a video bitrate from length, abr and file size
	calcFileSize	- calculates file size from length, abr and video bitrate
	run		- runs & handles a specified program as a new threaded pipe
	kill_pipe	- kill a spawned threaded pipe
	scanDVD		- get DVD information into data structures
			- includes several Total_ methods
	ripDVD		- rip DVD titles based on data structures
			- includes many codec-specific methods
	notify_*		- inheritable UI hooks
	"""

	def __init__(self):
		"""Replace this with your own init, but include the one line in your own"""
		self.initialise()

	def initialise(self):
		"""the 'actual' init function"""
		self.cwd = os.getcwd()
		self.state = "still"
		self.numtitles = 0
		self.titles = []
		self.configfile = os.path.join(os.path.expanduser("~"), ".viciousriprc")
		self.loadConfig()
#Set the Glade file
		#to delete hopefully: GLADE_FILE = "viciousrip2.glade"		
		#to delete hopefully: glade = gtk.glade.XML(GLADE_FILE,"statusbar1")
		self.gladefile = "viciousrip2.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile) 
#Status bar
		self.statusbar = gtk.glade.XML("viciousrip2.glade","statusbar").get_widget("statusbar")
#progressbar
		self.progressbar = gtk.glade.XML("viciousrip2.glade","progressbar").get_widget("progressbar")
#Create dictionay and connect it
		dic = { 
		"on_openiso_clicked" : self.notyetimplemented,
		"on_convert_clicked" : self.notyetimplemented,
		"on_viciousrip_destroy" : gtk.main_quit,
		"on_opendvd_clicked" : self.scanDVD }
		self.wTree.signal_autoconnect(dic)

	def notyetimplemented(self, widget):
		print "Not yet implemented!"
		context_id = self.statusbar.get_context_id("notyetimplemented")		
		self.statusbar.push(context_id, "Say something please...")
		self.progressbar.set_fraction(0.5)
		print context_id
	def loadConfig(self):
		"""Load user configuration file"""
		self.config = {}
		self.parser = ConfigParser.ConfigParser()
		if not os.path.isfile(self.configfile):
			cfg = open(self.configfile, 'w')
			self.parser.write(cfg)
			cfg.close()
		cfg = open(self.configfile, 'r')
		self.parser.readfp(cfg)
		cfg.close()

code continues...

```

Can anyone see where I'm going wrong? There must be something wrong here:

```
def notyetimplemented(self, widget):
		print "Not yet implemented!"
		context_id = self.statusbar.get_context_id("notyetimplemented")		
		self.statusbar.push(context_id, "Say something please...")
		self.progressbar.set_fraction(0.5)
		print context_id
```

But I don't know what :(

---

### Post by reacocard on 2007-04-09
> **viciouslime said:**
> I am trying to make something that will rip dvds based on quickrip. This is my first ever python project, it's just something to try and help me learn it. I have followed numerous tutorials and learnt a lot today, but one thing I can't seem to get working is setting properties of gtk elements.

For example, when I click a button, I can get the code to recognise this and display an output to the terminal, but I can't get it to move a progress bar, or display something in a status bar.

I have the following code:

```
#!/usr/bin/env python
#Various stuff from quickrip
from __future__ import generators
from time import sleep
import sys, os, re, popen2, ConfigParser, copy, threading, thread
import config   # ViciousRip global configuration


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

# ViciousRip global configuration.
import config   

__app__ = config.app
__author__ = config.author
__version__ = config.version
__date__ = config.date
__copyright__ = config.copyright
__license__ = config.license


try:
	import mmpython
except:
	print "*** FATAL ERROR: Can't import mmpython!"



class ViciousRip:
	"""ViciousRip base class, including the following methods:
	initialise	- replaces the __init__ function which is overwritten with inheritance
	loadConfig	- loads the user configuration file
	cautiousLoad	- loads a config variable in an exception clause
	findProgram	- takes a program name, returns the full path
	calcRate	- calculates a video bitrate from length, abr and file size
	calcFileSize	- calculates file size from length, abr and video bitrate
	run		- runs & handles a specified program as a new threaded pipe
	kill_pipe	- kill a spawned threaded pipe
	scanDVD		- get DVD information into data structures
			- includes several Total_ methods
	ripDVD		- rip DVD titles based on data structures
			- includes many codec-specific methods
	notify_*		- inheritable UI hooks
	"""

	def __init__(self):
		"""Replace this with your own init, but include the one line in your own"""
		self.initialise()

	def initialise(self):
		"""the 'actual' init function"""
		self.cwd = os.getcwd()
		self.state = "still"
		self.numtitles = 0
		self.titles = []
		self.configfile = os.path.join(os.path.expanduser("~"), ".viciousriprc")
		self.loadConfig()
#Set the Glade file
		#to delete hopefully: GLADE_FILE = "viciousrip2.glade"		
		#to delete hopefully: glade = gtk.glade.XML(GLADE_FILE,"statusbar1")
		self.gladefile = "viciousrip2.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile) 
#Status bar
		self.statusbar = gtk.glade.XML("viciousrip2.glade","statusbar").get_widget("statusbar")
#progressbar
		self.progressbar = gtk.glade.XML("viciousrip2.glade","progressbar").get_widget("progressbar")
#Create dictionay and connect it
		dic = { 
		"on_openiso_clicked" : self.notyetimplemented,
		"on_convert_clicked" : self.notyetimplemented,
		"on_viciousrip_destroy" : gtk.main_quit,
		"on_opendvd_clicked" : self.scanDVD }
		self.wTree.signal_autoconnect(dic)

	def notyetimplemented(self, widget):
		print "Not yet implemented!"
		context_id = self.statusbar.get_context_id("notyetimplemented")		
		self.statusbar.push(context_id, "Say something please...")
		self.progressbar.set_fraction(0.5)
		print context_id
	def loadConfig(self):
		"""Load user configuration file"""
		self.config = {}
		self.parser = ConfigParser.ConfigParser()
		if not os.path.isfile(self.configfile):
			cfg = open(self.configfile, 'w')
			self.parser.write(cfg)
			cfg.close()
		cfg = open(self.configfile, 'r')
		self.parser.readfp(cfg)
		cfg.close()

code continues...

```

Can anyone see where I'm going wrong? There must be something wrong here:

```
def notyetimplemented(self, widget):
		print "Not yet implemented!"
		context_id = self.statusbar.get_context_id("notyetimplemented")		
		self.statusbar.push(context_id, "Say something please...")
		self.progressbar.set_fraction(0.5)
		print context_id
```

But I don't know what :(

It's not the callback, the problem lies here:
```
#Status bar
		self.statusbar = gtk.glade.XML("viciousrip2.glade","statusbar").get_widget("statusbar")
#progressbar
		self.progressbar = gtk.glade.XML("viciousrip2.glade","progressbar").get_widget("progressbar")
```

it should be

```
#Status bar
		self.statusbar = self.wTree.get_widget("statusbar")
#progressbar
		self.progressbar = self.wTree.get_widget("progressbar")
```

---

### Post by viciouslime on 2007-04-09
IT WORKS!!!! Thank you so much! :) :) :)

---

