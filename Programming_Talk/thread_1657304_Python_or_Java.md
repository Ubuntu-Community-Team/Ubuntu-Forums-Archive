---
title: "Python or Java?"
date: 2011-01-01
forum: Programming Talk
---

### Post by Red Kelly on 2011-01-01
Gday I'm new to programing but have an idea for a music player was wondering what laungage I should use to create a frontend for the player? 

It wont need to play music just look pritty and send comands to server, like a remote app. 

I ask about pythin or java as I hear they are a little bit less of a steep learning curve but I am open to any suggestion.

Thanks

---

### Post by Red Kelly on 2011-01-01
Think I'll go with Python.

---

### Post by PaulM1985 on 2011-01-01
What language is the server going to be written in?

I think either language would be ok.  I think most people on this forum would recommend Python.  I personally prefer Java.

Both Python and Java have good user interface capabilities.  In Netbeans, a Java Integrated Desktop Environment (IDE, which is something that helps you develop your programs), there is a designer that allows you to drag and drop user interface components onto a panel. This makes it easy to create user interfaces quickly.  I am not sure if there is an equivalent for Python.

Whatever you choose, I am sure there will be plenty of people on this forum to help you out if you get into problems.

Paul

---

### Post by MadCow108 on 2011-01-01
there are also good gui builders for the many gui toolkits python supports, like QtBuilder, GtkBuilder (glade), Boa Constructor (wxWidgets), ...

---

### Post by trent.josephsen on 2011-01-01
> **Red Kelly said:**
> I'm new to programing

Python

---

### Post by Nytram on 2011-01-01
If you want it to be cross-platform I'd go with Java. If not, then I think Python would be easier to learn and develop for.

---

### Post by MadCow108 on 2011-01-01
python is cross plattform too
at least as long as you don't use unix specific features, but the same holds true for java

---

### Post by Nytram on 2011-01-01
> **MadCow108 said:**
> python is cross plattform too

I know it is.

But how many users will install Python AND the graphics toolkit (assuming you don't use Tkinter) just to run your program?

The JRE is already installed on most PCs, so nothing to download and install.

---

### Post by juancarlospaco on 2011-01-02
Python or Jython

---

### Post by Red Kelly on 2011-01-02
Thanks guys
Python it is. 

> **PaulM1985 said:**
> What language is the server going to be written in? 
No idea. I was thinking I'd pinch a copy of an open source player and change it around to do what I wonted, but that is a long way off. I just wont a project so I can start to learn.

---

### Post by idi0tf0wl on 2011-01-02
JavaFX actually makes for a really nice toolkit for transferring an idea to a GUI. And seeing as it works completely with any Java you or someone else might have lying around, it makes things that much nicer. Especially if you're new to programming, you might want to head for the Java family of languages for your learning endeavors.

Cheers, guy!

---

### Post by ssam on 2011-01-02
just a quick check on the original idea. are you aware of MPD and xmms2? are you planning to write a client for those, or start from scratch?

---

### Post by Red Kelly on 2011-01-02
> **ssam said:**
> just a quick check on the original idea. are you aware of MPD and xmms2? are you planning to write a client for those, or start from scratch?
No I wasn't thanks for them tho, I only had a brief google for something like those.

I know I'm doing this a bit backwords, building a front and not knowing what or how it is going to connect to the back. But I just wonted to have a ruf goal/project to keep me motivated.  Just the books get a bit mundain and boring. 
So I was going to follow the books and do this.

---

### Post by Shin_Gouki2501 on 2011-01-02
I know you already have "settled" with Python but i suggest you go with "scala" instead. 
[www.scala-lang.org](www.scala-lang.org)
It runs also on the JVM ( like java), you can use all java libraries if you want. But at the same time its statically typed and concise as Python.

In general JVM GUI Programs have a "noticeable" startup time, but IMHO its the same for python apps. I really like wikipad but it starts a little slow. So choose and happy coding :)

---

### Post by Red Kelly on 2011-01-03
Thanks Shin_Gouki I'd never herd of scala before. So probably for that reason I'll give it a miss. I like the sound of it though maybe I'll learn that next. (I have a lot I wont to learn just need the time)
Think I've got my head around "Hallo World" so Mark Zuckerberg look out!

---

### Post by worksofcraft on 2011-01-03
When I was learning about programming gstreamer with Python one of the first test programs I wrote was this one to play a track of someone else's website.

It is very simple gui to start and stop a pre programmed sound track. I just tested it works fine on my computer still, but was written for Python 2.x (not for 3) and you do need to import from gst module (gstreamer).

Hopefully it gets you started with some sounds :)
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
			self.get_ready()

	def get_ready(self):
			self.player.set_state(gst.STATE_NULL)
			self.button.set_label("Start")
						
	def on_message(self, bus, message):
		t = message.type
		if t == gst.MESSAGE_EOS:
			self.get_ready()
		elif t == gst.MESSAGE_ERROR:
			err, debug = message.parse_error()
			print "Error: %s" % err, debug
			self.get_ready()

GTK_Main()
gtk.gdk.threads_init()
gtk.main()

```

---

### Post by Shin_Gouki2501 on 2011-01-03
> **Red Kelly said:**
> Thanks Shin_Gouki I'd never herd of scala before. So probably for that reason I'll give it a miss. I like the sound of it though maybe I'll learn that next. (I have a lot I wont to learn just need the time)
Think I've got my head around "Hallo World" so Mark Zuckerberg look out!

I miss a lot of things to, and I wont a lot of things too
but for real:
if you *really* want to learn you can read up here:
[http://scala-programming-language.1934581.n4.nabble.com/](http://scala-programming-language.1934581.n4.nabble.com/)
This is the scala mailing list, a lot of people write and read there among them: Russ Paielli
He had an "Air Traffic Control" Application which he converted from Pyhton to Scala. On that path he gained a lot of insight. Maybe he should write a Scala for Python Programmers.

Well its up to you.

regards

---

