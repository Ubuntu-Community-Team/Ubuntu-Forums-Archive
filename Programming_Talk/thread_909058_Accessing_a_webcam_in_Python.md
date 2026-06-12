---
title: "Accessing a webcam in Python"
date: 2008-09-03
forum: Programming Talk
---

### Post by JoshHendo on 2008-09-03
Hi Everyone,

I am just looking for a simple way to access a webcam from within python (in Ubuntu of course). Basically, I want to be able to access the webcam, take a still from it, store it on disk and close the connection to the webcam. I am currently not using any GUI.

Any help would be greatly appreciated.

Thanks, Josh.

---

### Post by kknd on 2008-09-03
You can use gstreamer.

---

### Post by Zugzwang on 2008-09-03
The simplest way is to use some command line tool to do this task for you. For example, you can use mencoder to capture a picture or video.

[http://mydebian.blogdns.org/?p=120]("http://mydebian.blogdns.org/?p=120")

Using gstreamer is almost guaranteed to be more complicated. You can also call mencoder from your Python program if you want to.

---

### Post by themusicwave on 2008-09-03
> **Zugzwang said:**
> The simplest way is to use some command line tool to do this task for you. For example, you can use mencoder to capture a picture or video.

[http://mydebian.blogdns.org/?p=120]("http://mydebian.blogdns.org/?p=120")

Using gstreamer is almost guaranteed to be more complicated. You can also call mencoder from your Python program if you want to.

That is pretty cool!  Once I finishing painting, sanding, and otherwise remodeling my house maybe I will setup a camera.  Kinda a poor mans security system.

---

### Post by LaRoza on 2008-09-03
> **themusicwave said:**
> That is pretty cool!  Once I finishing painting, sanding, and otherwise remodeling my house maybe I will setup a camera.  Kinda a poor mans security system.

Search the repos from "motion" it is a motion activated features rich yet very light webcam software :-)

---

### Post by JoshHendo on 2008-09-03
> **Zugzwang said:**
> The simplest way is to use some command line tool to do this task for you. For example, you can use mencoder to capture a picture or video.

[http://mydebian.blogdns.org/?p=120]("http://mydebian.blogdns.org/?p=120")

Using gstreamer is almost guaranteed to be more complicated. You can also call mencoder from your Python program if you want to.
Works great. Thanks. What I am doing currently is using popen to run the command... is there a better way to do this (I am sure there is).

Also, how can I specify the output of the jpegs? My program is similar to motion in the sense that it is a security program, so I want to store all the jpegs in a certain folder, not just where the person is running the script from in the terminal.

Thanks, Josh.

---

### Post by Zugzwang on 2008-09-04
> **JoshHendo said:**
> 
Also, how can I specify the output of the jpegs? My program is similar to motion in the sense that it is a security program, so I want to store all the jpegs in a certain folder, not just where the person is running the script from in the terminal.


You could chdir() to that directory before running mencoder *or* tell mencoder where to put the files. Just look into mencoder's 4000-lines-or-so man page. Will the somewhere there. :-)

---

### Post by edajai on 2009-04-17
Using gstreamer(pygst) and pygtk

```

 #!/usr/bin/env python

import sys, os
import pygtk, gtk, gobject
import pygst
pygst.require("0.10")
import gst

class GTK_Main:

	def __init__(self):
		window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		window.set_title("Webcam-Viewer")
		window.set_default_size(500, 400)
		window.connect("destroy", gtk.main_quit, "WM destroy")
		vbox = gtk.VBox()
		window.add(vbox)
		self.movie_window = gtk.DrawingArea()
		vbox.add(self.movie_window)
		hbox = gtk.HBox()
		vbox.pack_start(hbox, False)

		hbox.set_border_width(10)
		hbox.pack_start(gtk.Label())
		self.button = gtk.Button("Start")
		self.button.connect("clicked", self.start_stop)
		hbox.pack_start(self.button, False)
		self.button2 = gtk.Button("Quit")
		self.button2.connect("clicked", self.exit)
		hbox.pack_start(self.button2, False)
		hbox.add(gtk.Label())

		window.show_all()

		# Set up the gstreamer pipepile
		self.player = gst.parse_launch ("v4l2src  !  autovideosink")

		bus = self.player.get_bus()
		bus.add_signal_watch()
		bus.enable_sync_message_emission()
		bus.connect('message', self.on_message)
		bus.connect('sync-message::element', self.on_sync_message)

	def start_stop(self, w):
		if self.button.get_label() == "Start":
			self.button.set_label("Stop")
			self.player.set_state(gst.STATE_PLAYING)
		else:
			self.player.set_state(gst.STATE_NULL)
			self.button.set_label("Start")

	def exit(self, widget, data=None):
		gtk.main_quit()

	def on_message(self, bus, message):
		t = message.type
		if t == gst.MESSAGE_EOS:
			self.player.set_state(gst.STATE_NULL)
			self.button.set_label("Start")
		elif t == gst.MESSAGE_ERROR:
			err, debug = message.parse_error()
			print "Error: %s" % err, debug
			self.player.set_state(gst.STATE_NULL)
			self.button.set_label("Start")

	def on_sync_message(self, bus, message):
		if message.structure is None:
			return
		message_name = message.structure.get_name()
		if message_name == 'prepare-xwindow-id':
			# Assign the viewport
			imagesink = message.src
			imagesink.set_property('force-aspect-ratio', True)
			imagesink.set_xwindow_id(self.movie_window.window.xid)

GTK_Main()
gtk.gdk.threads_init()
gtk.main()

```

source:[http://www.ndeschildre.net/2008/04/04/python-power/]("http://www.ndeschildre.net/2008/04/04/python-power/")

---

### Post by idlecool on 2010-11-04
hey! thanks for the code. its works..

---

