---
title: "Music Player(Mp3, wav, etc)"
date: 2010-08-18
forum: Programming Talk
---

### Post by Black Mage on 2010-08-18
Hey everyone,

I am developing a site that is going to be able to play music but I need a good web music player. Can anyone give suggestions of one that can play mp3 and possibly other music formats such as wavs, aiff, etc

---

### Post by worksofcraft on 2010-08-19
I don't know much about playing music off the web, but per chance I'm learning all about gstreamer that lets you make your own audio/video stream players by plugging different modules together.
I suspect it has modules that source from a TCP/IP port, but haven't progressed far enough to know.

The tutorial I'm learning atm is:
[http://pygstdocs.berlios.de/pygst-tutorial/playbin.html](http://pygstdocs.berlios.de/pygst-tutorial/playbin.html)
You might want to have a look if anything there does what you want.

update: With a few minor changes like where it says "file://" make it say "http://" and then example script plays off the web. So basically it lets Python programmers brew their own players (both audio and video) without even using a web browser.

---

### Post by dv3500ea on 2010-08-19
You can do this in HTML:
```

<audio controls="controls">
  <source src="song.ogg" type="audio/ogg" />
  <source src="song.mp3" type="audio/mpeg" />
  <source src="song.wav" type="audio/wav" />
  You are using an old or out of date web browser.
  <a href="song.ogg" >Click here for the audio file.</a>
</audio>

```

---

### Post by worksofcraft on 2010-08-19
Well whatever, just in case anyone want to see how epic gstreamer is, copy this code, paste in a text file, chmod +x on it and then run it to hear Blind Willie's l33t guitar streaming to you over the internet ;)

```

#!/usr/bin/env python
import pygtk, gtk, gobject
import pygst
pygst.require("0.10")
import gst

class GTK_Main:
	
	def __init__(self):
		window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		window.set_title("Blind Willie")
		window.set_default_size(200, -1)
		window.connect("destroy", gtk.main_quit, "WM destroy")
		self.button = gtk.Button("Start")
		self.button.connect("clicked", self.start_stop)
		window.add(self.button)
		window.show_all()
		
		self.player = gst.element_factory_make("playbin2", "player")
		bus = self.player.get_bus()
		bus.add_signal_watch()
		bus.connect("message", self.on_message)
		
	def start_stop(self, w):
		if self.button.get_label() == "Start":
			self.button.set_label("Stop")
			self.player.set_property("uri", "http://www.robtowns.com/music/blind_willie.mp3")
			self.player.set_state(gst.STATE_PLAYING)
		else:
			self.player.set_state(gst.STATE_NULL)
			self.button.set_label("Start")
						
	def on_message(self, bus, message):
		t = message.type
		if t == gst.MESSAGE_EOS:
			self.player.set_state(gst.STATE_NULL)
			self.button.set_label("Start")
		elif t == gst.MESSAGE_ERROR:
			self.player.set_state(gst.STATE_NULL)
			err, debug = message.parse_error()
			print "Error: %s" % err, debug
			self.button.set_label("Start")

GTK_Main()
gtk.gdk.threads_init()
gtk.main()

```

Ka Pai (enjoy)

---

