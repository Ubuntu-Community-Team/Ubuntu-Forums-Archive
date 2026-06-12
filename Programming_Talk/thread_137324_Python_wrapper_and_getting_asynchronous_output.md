---
title: "Python wrapper and getting asynchronous output"
date: 2006-02-27
forum: Programming Talk
---

### Post by engla on 2006-02-27
I have some trouble with a very small wrapper project I'm doing in python. I expected this to be simple but the last day I haven't come anywhere with this, so I hope to get some pointers. And yes, I've searched quite a lot but I can't find much that touches my exact issue.

I'm trying to make a wrapper for the cli app "gnome-obex-server" that receives files via bluetooth. I want a python app that displays a window and simply updates it when a file is recieved.

The python app has to launch gnome-obex-server and then listen constantly for its output to see if something happens.

This is what gnome-obex-server's output looks like, and I want to catch it and parse it on a thread in my script: (it's strangely enough output on stderr)

```
** Message: Incoming connection from 00:15:B9:48:1D:83
** Message: Device 00:15:B9:48:1D:83 is about to send an object.
** Message: File arrived from 00:15:B9:48:1D:83
** Message: Filename 'Ulrik-0275.jpg' Length 34654
** Message: Saving to '/home/ulrik/Pictures/Mobil/Ulrik-0275 (30).jpg'
** Message: Incoming connection from 00:15:B9:48:1D:83

```

Here is the script in the current state; I've been trying lots of things though but I can't get anything to work
Notes: I'm using a thread to spawn the gnome-obex-server and listen to its output. This is neccessary as I want the UI running on the main thread. The ui is built with glade, but not at all relevant for the script.

What happens when I run the script?
First it outputs
```
Sleeping...
Trying to read file

```
I now send a file to my computer with bluetooth. It works, but nothing is output from the app. Now, if I in the interface quit the application, the following is output:
```
Win was deleted! at 1141084364.941249
Sleeping...
Trying to read file
Read file
Got things at 1141084365.084323: ** Message: Incoming connection from 00:15:B9:48:1D:83
```

So only a part of the output is caught, and somehow it's only read after the window is closed and the app is quitting...

Any help appreciated

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade
import os
import sys
from threading import Thread
import time

from subprocess import Popen, PIPE

import popen2, fcntl, select

def makeNonBlocking(fd):
    fl = fcntl.fcntl(fd, fcntl.F_GETFL)
    try:
        fcntl.fcntl(fd, fcntl.F_SETFL, fl | os.O_NDELAY)
    except AttributeError:
        fcntl.fcntl(fd, fcntl.F_SETFL, fl | fcntl.FNDELAY)



class obex_controller(Thread):
	u"""
	Wrapper around gnome-obex-server
	
	"""
	
	def __init__(self, parent): 
	 	Thread.__init__(self)
	 	cmd ="gnome-obex-server"
		self.p = Popen(cmd, shell=False, bufsize=1,
           stdout=PIPE, stderr=PIPE)
		(self.stdout,
 		self.stderr) = (self.p.stdout, self.p.stderr)
 		makeNonBlocking(self.stderr.fileno())
 		makeNonBlocking(self.stdout.fileno())
 		self.parent = parent
 		
 		
 	def join(self): 
 	 	if self.p:
 	 		os.system("kill %d" % self.p.pid)
 	 		self.p.wait()
 	 		self.p = None
 	 		
 	def run(self):
 		#self.getCommandOutput()
 		#return
 		while True:
 			if not self.p:
 				return
 			time.sleep(0.1)
			print "Sleeping..."
 			self.stderr.flush()
 			try:
 				print "Trying to read file"
				line = self.stderr.readline()
				print "Read file"
			except:
				continue
			sys.stdout.write("Got things at %lf: %s" % (time.time(),line) )
			#os.system("zenity --info --text '%s'" % line)
			sys.stdout.flush()


class main:
    def __init__(self):
        self.ui = gtk.glade.XML("btrcv.glade")
        
        dic = {"on_win_delete_event" : self.delete_win,
        		"on_open_button_clicked" : self.button,
        		"on_Öppna1_activate" : self.button,
        		"on_avsluta1_activate" : self.delete_win
               }
        self.ui.signal_autoconnect(dic)
        #ui = self.ui.get_widget("ui")
        self.win = self.ui.get_widget("win")
        self.win.set_position(gtk.WIN_POS_CENTER)
        #self.set_status("test")
        self.set_file(None) 
        
        self.controller = obex_controller(self)
        self.controller.start()
        gtk.main()
        
    def button(self, event): 
     
    	print "button!" 
      
        
    def delete_win(self, event, more=None):
		print "Win was deleted! at %lf" % time.time()
		self.quit()
		
    def quit(self,event=None):
    	self.controller.join()
        gtk.main_quit()

    def set_status(self, string):
    	label = self.ui.get_widget("label1")
    	label.set_markup("%s" % string)
    def set_file(self, f): 
    	self.file = f
    	if not self.file :
    		return
    	label = self.ui.get_widget("label2") 
    	label.set_text("%s" % self.file) 

if __name__ == '__main__':
    main()
```

---

### Post by engla on 2006-02-28
I reworked my code to the simpler and more readable thing below

This is just my Thread class, but that's the only thing that's interesting. My problem seems to be with threads; if I do
```
c = obex_controller(self)
c.run()
```
Then the code runs on the main thread and I get the desired output.

But if  I do
```
c = obex_controller(self)
c.start()
```
so that the code runs on a spawned thread (what I want), then I get no output until I kill my subprocess. 

What's the difference, and why does this happen?
```
import sys
from threading import Thread
import time

from subprocess import Popen, PIPE, STDOUT

class obex_controller(Thread):
	u"""
	Wrapper around gnome-obex-server
	
	"""
	
	def __init__(self, parent): 
	 	Thread.__init__(self)
	 	cmd ="gnome-obex-server"
		self.p = Popen(cmd, shell=True, bufsize=0,
           stdout=PIPE, stderr=STDOUT)
		self.stdout = self.p.stdout
 		self.parent = parent
 		print "Started %s with pid %d" % (cmd, self.p.pid )
 		
 		
 	def join(self): 
 	 	if self.p:
 	 		print "Killing gnome-obex-server..."
 	 		os.system("kill %d" % self.p.pid)
 	 		self.p.wait()
 	 		self.p = None
 	 		
 	def run(self):
 		while True:
 			print "Sleeping..."
 			time.sleep(0.1)
 			line = self.stdout.readline()
 			if line == "":
 				continue
			sys.stdout.write("Got things at %lf: %s\n" % (time.time(),line) )

```

---

### Post by psychicdragon on 2006-02-28
You need to call **gtk.gdk.threads_init()** somewhere in your app before the window is created.

When you need to update your Gtk Window from within the thread you need to wrap the code like this:
```
gtk.gdk.threads_enter()
...
gtk.gdk.threads_leave()
```
Some more info from the PyGtk docs:
[http://pygtk.org/pygtk2reference/gdk-functions.html#function-gdk--threads-enter](http://pygtk.org/pygtk2reference/gdk-functions.html#function-gdk--threads-enter)

---

### Post by engla on 2006-02-28
[QUOTE=psychicdragon]You need to call **gtk.gdk.threads_init()** somewhere in your app before the window is created.

When you need to update your Gtk Window from within the thread you need to wrap the code like this:
```
gtk.gdk.threads_enter()
...
gtk.gdk.threads_leave()
```
Some more info from the PyGtk docs:
[http://pygtk.org/pygtk2reference/gdk-functions.html#function-gdk--threads-enter](http://pygtk.org/pygtk2reference/gdk-functions.html#function-gdk--threads-enter)[/QUOTE]

Thanks, this is so great! That definitely works, right away.

That's why I didn't find anything and why there aren't many others asking about this -- it's a gtk/pygtk related issue that I didn't know about, and I kept searching generally in python about output and threads...
Again, thanks. Those "locking" commands seems to be just the thing I need too and now I have all the missing puzzle pieces to get my tool ready.

---

### Post by engla on 2006-02-28
Aaand..
this is alpha 1:

---

