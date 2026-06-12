---
title: "Help building first python glade app. Mostly working."
date: 2007-07-07
forum: Programming Talk
---

### Post by notamonopoly on 2007-07-07
Background:
So a few days ago I decided to learn python, as it seems to come highly recommended. I wrote a simple program to automate the conversion of files from flash to avi using mencoder. It worked well but lacked a gui so I used glade for that and learned how to connect the two. I wanted to output the status of the conversion in the gui and also provide an way to stop it if needed. To accomplish this I created a thread. It worked, except that the output would stop part way through. I made some changes to fix that and now it hangs without an error.

Where I am:
After spending many hours on this, I'm finally ready to get some help. If someone has the time to look at the code, I've included both the toAvi.py code, followed by the toavi.glade code.

Please keep in mind that I started this to learn and would appreciate advice and/or examples on how to improve my current logic, as I believe that I went wrong somewhere, and how to make it more efficient.

Many thanks in advance

toAvi.py
===========================
```

#!/usr/bin/env python

# Imports
import sys, time, threading, Queue
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

# To determine Mime Types
import gnomevfs
# Call external apps
import subprocess

# Make thread safe
gtk.gdk.threads_init()


class GuiPart:
	"""
		Class: GuiPart
		Create the GUI and connect functions to events	
	"""
	# Initialize class
	# queue - ThreadedClient.queue
	# command - ThreadedClient.endApplication()
	# command2 - ThreadedClient.requestConversion()
	# command3 - ThreadedClient.stopRequest

	def __init__(self, queue, command, command2, command3):
		self.queue = queue
		self.endCommand = command
		self.requestConversion = command2
		self.stopRequest = command3
		
		#Create Gui using the glade file
		self.gladefile = "toavi.glade"  
		self.wTree = gtk.glade.XML(self.gladefile)

		#Create dictionay and connect it
		dic = { "on_filechooserbutton1_selection_changed" : self.on_filechooserbutton1_selection_changed,
			"on_mainWindow_destroy" : self.stopApplication,
			"on_button1_clicked" : self.on_button1_clicked,
			"on_button2_clicked" : self.on_button2_clicked}
		self.wTree.signal_autoconnect(dic)
	
	# User selects file
	def on_filechooserbutton1_selection_changed(self, widget):
		lbl = self.wTree.get_widget("label1")
		txt = self.wTree.get_widget("entry1")
		fc = self.wTree.get_widget("filechooserbutton1")
		filename = fc.get_filename().split('/')[-1]
		txt.set_text(filename)
		
	# User chooses convert	
	def on_button1_clicked(self, widget):
		fc = self.wTree.get_widget("filechooserbutton1")
		full = fc.get_filename()
		type = gnomevfs.get_mime_type(full)

		path = fc.get_current_folder()
		fileName = full.split('/')[-1]
		ext = fileName.split('.')[-1]
			
		if type == "application/x-flash-video":
			self.convertToAvi(path, fileName)
		else:			
			print type
			print
			print "Only looking for Flash files right now"
	
	# Conversion Function
	def convertToAvi(self, path, fileName):
		self.requestConversion(path, fileName)
	
	# Stop Execution
	def on_button2_clicked(self, widget):
		print "STOP"
		self.stopRequest()
	
	# Check the queue
	def processIncoming(self):
		# Handle all the messages currently in the queue (if any).
		while self.queue.qsize():
			try:
				msg = self.queue.get(0)
				# Make sure that we can still connect to the gui
				if self.wTree.get_widget("entry1"):
					txt = self.wTree.get_widget("entry1")
					txt.set_text(str(msg))
			except Queue.Empty:
				print "QUEUE IS EMPTY"
				pass

	# Close App
	def stopApplication(self, widget):
		gtk.main_quit
		self.endCommand()
		sys.exit(1)
		
class ThreadedClient:
	"""
	Class: ThreadedClient
	Create the thread	
	"""
	def __init__(self):
		# Create the queue
		self.queue = Queue.Queue()

		# Set up the GUI part
		self.gui=GuiPart(self.queue, self.endApplication, self.requestConversion, self.stopRequest)		

		# Set up the thread to do asynchronous I/O
		# More can be made if necessary
		self.running = 1
		self.thread1 = threading.Thread(target=self.workerThread1)
		self.thread1.start()
		
		# Start the periodic call in the GUI to check if the queue contains anything
		self.periodicCall()

	def periodicCall(self):
		#time.sleep(0.1)
		self.gui.processIncoming()
		if not self.running:
			sys.exit(1)
		
		
	def endApplication(self):
		self.running = 0

	def requestConversion(self, path, fileName):
		self.stop_request = False
		self.oldPath = path + "/" + fileName
		self.newPath = path + "/" + fileName + ".avi"
		self.cmd = "mencoder"
		self.args = " -oac copy -ovc lavc -o " + self.newPath + " " + self.oldPath
		self.proc = subprocess.Popen(self.cmd + self.args,
							shell=True,
							universal_newlines=True,
							stdin=subprocess.PIPE,
							stdout=subprocess.PIPE,
							)

	def stopRequest(self):
		self.stop_request = True
		time.sleep(0.2)
		try:
			os.kill(self.proc.pid, signal.SIGKILL)
		except:
			pass
			print "Process is not running"

	def workerThread1(self):
		"""
		Asynchronous I/O.
		"""
		while self.running:
			try: 
				if self.proc.poll() == None:
					if self.stop_request == False:
						self.output = self.proc.stdout.readline()
						print "line: ", repr(self.output)
						self.msg = self.output
						self.queue.put(self.msg)
						self.periodicCall()
					else:
						print "Stop Requested"
						pass
				else:
					if self.proc.stdout:
						self.output = self.proc.stdout.readline()
						print "line: ", repr(self.output)
					print "Finished!"
					pass
			except:
				pass
	
		"""		
		# Testing
		while self.running:
			msg = "Testing Message"

			self.queue.put(msg)
			self.periodicCall()
		"""

def main():
	client = ThreadedClient()
	gtk.main()

if __name__ == "__main__":
	main()

```


toavi.glade
===============================

```
<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>
<requires lib="gnome"/>

<widget class="GtkWindow" id="mainWindow">
  <property name="visible">True</property>
  <property name="title" translatable="yes">toAvi</property>
  <property name="type">GTK_WINDOW_TOPLEVEL</property>
  <property name="window_position">GTK_WIN_POS_NONE</property>
  <property name="modal">False</property>
  <property name="resizable">True</property>
  <property name="destroy_with_parent">False</property>
  <property name="decorated">True</property>
  <property name="skip_taskbar_hint">False</property>
  <property name="skip_pager_hint">False</property>
  <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
  <property name="gravity">GDK_GRAVITY_NORTH_WEST</property>
  <property name="focus_on_map">True</property>
  <property name="urgency_hint">False</property>
  <signal name="destroy" handler="on_mainWindow_destroy" last_modification_time="Thu, 05 Jul 2007 06:52:59 GMT"/>

  <child>
    <widget class="GtkVBox" id="vbox1">
      <property name="visible">True</property>
      <property name="homogeneous">False</property>
      <property name="spacing">0</property>

      <child>
	<widget class="GtkLabel" id="label1">
	  <property name="visible">True</property>
	  <property name="label" translatable="yes">Please choose a file to convert</property>
	  <property name="use_underline">False</property>
	  <property name="use_markup">False</property>
	  <property name="justify">GTK_JUSTIFY_LEFT</property>
	  <property name="wrap">False</property>
	  <property name="selectable">False</property>
	  <property name="xalign">0.5</property>
	  <property name="yalign">0.5</property>
	  <property name="xpad">0</property>
	  <property name="ypad">0</property>
	  <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
	  <property name="width_chars">-1</property>
	  <property name="single_line_mode">False</property>
	  <property name="angle">0</property>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>

      <child>
	<widget class="GtkFileChooserButton" id="filechooserbutton1">
	  <property name="visible">True</property>
	  <property name="title" translatable="yes">Select A File To Convert</property>
	  <property name="action">GTK_FILE_CHOOSER_ACTION_OPEN</property>
	  <property name="local_only">True</property>
	  <property name="show_hidden">False</property>
	  <property name="do_overwrite_confirmation">False</property>
	  <property name="width_chars">-1</property>
	  <signal name="file_activated" handler="on_filechooserbutton1_file_activated" last_modification_time="Thu, 05 Jul 2007 06:45:58 GMT"/>
	  <signal name="selection_changed" handler="on_filechooserbutton1_selection_changed" last_modification_time="Thu, 05 Jul 2007 06:55:03 GMT"/>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>

      <child>
	<widget class="GtkButton" id="button1">
	  <property name="visible">True</property>
	  <property name="can_focus">True</property>
	  <property name="label" translatable="yes">Convert</property>
	  <property name="use_underline">True</property>
	  <property name="relief">GTK_RELIEF_NORMAL</property>
	  <property name="focus_on_click">True</property>
	  <signal name="clicked" handler="on_button1_clicked" last_modification_time="Thu, 05 Jul 2007 06:46:04 GMT"/>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>

      <child>
	<widget class="GtkEntry" id="entry1">
	  <property name="height_request">193</property>
	  <property name="visible">True</property>
	  <property name="can_focus">True</property>
	  <property name="editable">True</property>
	  <property name="visibility">True</property>
	  <property name="max_length">0</property>
	  <property name="text" translatable="yes"></property>
	  <property name="has_frame">True</property>
	  <property name="invisible_char">&#9679;</property>
	  <property name="activates_default">False</property>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>

      <child>
	<widget class="GtkButton" id="button2">
	  <property name="visible">True</property>
	  <property name="can_focus">True</property>
	  <property name="label" translatable="yes">Stop</property>
	  <property name="use_underline">True</property>
	  <property name="relief">GTK_RELIEF_NORMAL</property>
	  <property name="focus_on_click">True</property>
	  <signal name="clicked" handler="on_button2_clicked" last_modification_time="Sat, 07 Jul 2007 01:50:04 GMT"/>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>
    </widget>
  </child>
</widget>

</glade-interface>
```

---

### Post by notamonopoly on 2007-07-10
Well I finally got it working and in the process learned a lot about threading and gtk. I ended up ditching glade and coding everything. The gui isn't pretty and the app does not validate much before converting the file but it's a good start and I'm rather happy with it.

Things to figure out:
1) Why the process ID returned by popen is not valid. To stop the conversion prematurely I use os.kill with pid+1. It is consistently 1 less than it should be.
2) A more accurate way of getting the percentage completed.

I've included the new code below so if you want to try it just start the app, choose a file (flash format), click convert and wait. If you get impatient, click stop and it should kill the conversion.

If anyone uses this code please post any improvements you make to it back here so everyone can benefit, especially me, I'm still learning :)

```

#!/usr/bin/env python
#Imports
import threading
import time, sys
import gtk
import Queue, subprocess
import gnomevfs

gtk.gdk.threads_init()

class readOutput(threading.Thread):
	"""This class reads the stdout data from the subprocess"""
	
	#Thread event, stops the thread if it is set.
	stopthread = threading.Event()
	
	def run(self):
		"""Run method, this is the code that runs while thread is alive."""
		
		#Importing objects from global scope
		global progressbar 
		global queue
		global proc
		#While the stopthread event isn't set, the thread keeps going on
		while not self.stopthread.isSet() :
			# Acquiring the gtk global mutex
			gtk.gdk.threads_enter()
			#Check if the subprocess exists
			#This thread is started before the subprocess is executed so if proc doesn't exist yet, keep checking
			if proc != None:
				#If there is still output being generated
				if proc.poll() == None:
					#Read the output and send it to the queue
					output = proc.stdout.readline()
					queue.put(output)
				else:
					#If the subprocess has stopped, check if there is still data in stdout
					output = proc.stdout.readline()
					while output != "":
						queue.put(output)
						output = proc.stdout.readline()
					#If there is no more data, stop reading	
					self.stop()
			# Releasing the gtk global mutex		
			gtk.gdk.threads_leave()
			
	def stop(self):
		"""Stop method, sets the event to terminate the thread's main loop"""
		self.stopthread.set()

class setStatus(threading.Thread):
	"""This class displays the current status of the subprocess in the gui"""
	
	def __init__(self):
		
		#Importing objects from global scope
		global results 
		global queue
		global progressbar
		global ro
		
		#initialize
		percent = 0
		results.set_text("Please select a file")

		#Thread event, stops the thread if it is set.
		self.stopthread = threading.Event()
		
		threading.Thread.__init__ ( self )
	
	def run(self):
		"""Run method, this is the code that runs while thread is alive."""
			
		#While the stopthread event isn't set, the thread keeps going on
		while not self.stopthread.isSet() :
			# Acquiring the gtk global mutex
			gtk.gdk.threads_enter()
			# Check the que and get the data
			if queue.qsize():
				output = queue.get(0)
				# Parsing the mencoder output to get the percentage complete
				pos1 = output.find("(")
				pos2 = output.find(")")

				if pos1 != -1 and pos2 != -1:
					percent = output[pos1+1:pos2-1]

					if percent.strip().isdigit():
						percent = float(percent)/100

				if output != None and output != "":
					#Display output in gui
					results.set_text(str(output))
					try:
						#Attempt to update the progressbar
						progressbar.set_fraction(percent)
					except:
						pass
			else:
				#If the queue is empty and no more data is being sent, stop the thread
				if not ro.isAlive():
					self.stop()
			# Releasing the gtk global mutex		
			gtk.gdk.threads_leave()
			
	def stop(self):
		"""Stop method, sets the event to terminate the thread's main loop"""
		self.stopthread.set()


def convert():
	global proc
	full = fileChoose.get_filename()
	print gnomevfs.get_mime_type(full)
	
	if full != None:
		if gnomevfs.get_mime_type(full) != None:
			path = fileChoose.get_current_folder()
			fileName = full.split('/')[-1]
			cmd = "mencoder"
			args = " -oac copy -ovc lavc -o '" + path + "/" + fileName + ".avi'" + " '" + full + "'"
			ro.start()
			proc = subprocess.Popen(cmd + args,
							shell=True,
							universal_newlines=True,
							stdin=subprocess.PIPE,
							stdout=subprocess.PIPE
							)
			ss.start()

def on_buttonStart_clicked(button):
	convert()
	
def on_buttonEnd_clicked(button):
	global proc
	try:
		import os, signal
		os.kill(proc.pid + 1, signal.SIGKILL)
		os.waitpid(-1, os.WNOHANG)
	except Exception, inst:
		print "Unable to kill process"

def main_quit(obj):
	"""main_quit function, it stops the thread and the gtk's main loop"""
	#Importing objects from global scope
	global ro
	global ss
	#Stopping the thread and the gtk's main loop
	ro.stop()
	ss.stop()

	gtk.main_quit()
	#sys.exit(1)

#Gui
window = gtk.Window()
vbox = gtk.VBox()
window.add(vbox)

window = gtk.Window()
vbox = gtk.VBox()
window.add(vbox)
label = gtk.Label()
vbox.pack_start(label)
fileChoose = gtk.FileChooserButton("File Select")
fileChoose.set_current_folder('/home')
vbox.pack_start(fileChoose)
buttonStart = gtk.Button("Start Conversion")
vbox.pack_start(buttonStart)
buttonEnd = gtk.Button("STOP")
vbox.pack_start(buttonEnd)
results = gtk.Entry()
vbox.pack_start(results)
progressbar = gtk.ProgressBar()
vbox.pack_start(progressbar)

window.show_all()

queue = Queue.Queue()
proc = None
pid = None

#Connecting the gui events to functions
window.connect('destroy', main_quit)

buttonStart.connect("clicked", on_buttonStart_clicked)
buttonEnd.connect("clicked", on_buttonEnd_clicked)

#Threads
ro = readOutput()
ss = setStatus()

gtk.main()

```

---

### Post by ButteBlues on 2007-07-10
In the GUI portion, you defined "window" and "vbox" twice.

---

### Post by notamonopoly on 2007-07-10
Thanks, I missed that.

---

### Post by 3togo on 2008-02-05
I found your program very intriguing but I think it could be simpler.

"popen" itself is a thread so u don't need to create another thread to run the popen thread. Instead, a simple while loop to first read stdout and then to update the progressbar is suffice.

:)

---

