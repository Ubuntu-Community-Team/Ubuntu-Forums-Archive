---
title: "Python readability"
date: 2010-08-18
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-18
Starting to learn Python here.
I set myself task of making a program that counts down in audio, 5, 4, 3, 2, 1 and then says "go".
First things first and I findout how to do timers and play sounds!

Thus I now have this little Python script that goes "ding" 5 times every minute on the minute... but I'm thinking my code looks really illegible and messy and the word "self" seems to appear far too often for my liking... so I was kind of hoping that some Python Gurus might give me a few pointers please [-o<

Note: all you need is a "ding.wav" file to run this code and a Ctrl-C to stop it.
```

#!/usr/bin/python
import gtk
import gobject
import pygst
pygst.require("0.10")
import gst

repeat = 60 # repeat every 60 seconds
warn = 5 # give 5 seconds warning

class countdown(gobject.GObject):
	def __init__(self):
		# Create GStreamer malarkey
		self.pipeline = gst.Pipeline("ping_pipe")

		self.filesrc = gst.element_factory_make("filesrc", "source")
		self.pipeline.add(self.filesrc)
		self.filesrc.set_property("location", "ding.wav")

		self.decode = gst.element_factory_make("decodebin", "decode")
		self.decode.connect("new-decoded-pad", self.OnDynamicPad)
		self.pipeline.add(self.decode)

		self.filesrc.link(self.decode)

		self.convert = gst.element_factory_make("audioconvert", "convert")
		self.pipeline.add(self.convert)

		self.sink = gst.element_factory_make("alsasink", "sink")
		self.pipeline.add(self.sink)

		self.convert.link(self.sink)

		# the timer malarkey
		self.count = 0
		self.start()

	def start(self):
		self.count = self.count - 1 # count down warnings
		if self.count > 0:
			return True # that was just a warning
		else:
			self.count = warn # reload for next
			# Compute time to wait
			secs_to_go = repeat - (warn + int(gobject.get_current_time()))%60
			print 'wait = ', secs_to_go
			gobject.timeout_add(secs_to_go * 1000, self.delay)
			return False

	def delay(self):
		gobject.timeout_add(1000, self.tick)
		return False
		
	def tick(self):
		self.pipeline.set_state(gst.STATE_READY)
		self.pipeline.set_state(gst.STATE_PLAYING)
		print 'time tick', self.count
		return self.start()

	def OnDynamicPad(self, dbin, pad, islast):
		print "OnDynamicPad Called!"
		pad.link(self.convert.get_pad("sink"))

c = countdown()
gtk.main()

```

Thanks in advance :)

---

### Post by StephenF on 2010-08-18
If you don't intend to add a graphical user interface at a later stage I would remove the 'import gtk' statement and replace the gtk.main() with...
```

context = gobject.main_context_default()
while 1:
        context.iteration()

```
Hopefully it still works, otherwise disregard.

Your code is kind of big for what it does until you consider that you have right there an entire media player. All sample rates and file formats are taken care of. If you need more features you just have to access them. If all you wanted was a ding sound then yes, it's bloated as gstreamer is big and there are simpler ways of handling audio but gstreamer is not pushing the audio through the Python layer as far as I know, which allows it to run at C(++) speed. The gstreamer libraries are almost certainly shared and loaded ahead of time in any case, so forget they take up any room and just consider the CPU load which I suspect is minimal.

Edit: Ignore the above code. This is better.
```

loop = gobject.MainLoop()
loop.run()

```

---

### Post by worksofcraft on 2010-08-18
Thanks for that StephenF :)
I actually am adding a GUI just simply because I want to learn how to do that from Python too and it seems to be nice and easy using Glade just like I did in C.

You make a good about the benefits of gstreamer and it definitely seems the way to go. I'm not quite sure how to connect signals for when one file stops playing at the moment.

Now when it comes to code structure I'm want to split up the functionality of timer, gui and gstreamer into separate classes. Not sure if I should multiply inherit from them all into my app or if it would be better practice to create an instance of each.

I'm still a bit concerned with having to write 'self' everywhere... In C++ the use of 'this' (current object equivalent to Python 'self') is implicit for object members, but in Python the members don't even exist until I assign something to them :shock:

---

### Post by worksofcraft on 2010-08-18
Some languages are 'free format'. They claim you can lay things out whatever way you want, but in the next sentence they impose conventions: So it's like "You are allowed to put as many statements on one line as you like, but our coding standards say it has to be no more than one!" and similar for indentations and lining up braces etcetera, so what attracted me to Python is that the layout is actually significant and provides information to the interpreter.

Thus I was a bit surprised to read a number of recommended Python coding practices stating that you had to use 4 spaces for each level of indent and that tabs were anathema! The reason apparently that 4 is a good compromise between legibility and line length.

Now if there is one thing I really hate it's counting spaces... specially cuz I can't see them! I don't see a need to "compromise" because gedit lets me set the number of spaces between tab stops. With a few clicks I can change it whatever way I want :)

Thus, I decided to ignore recommendations and use ONLY tabs for indentation :D Perhaps I'll learn the hard way then, and have to use 'sed' to replace all those tabs :shock:

Anyone else got views on Python tabs and spaces?

---

### Post by oldfred on 2010-08-18
I use geany and in at least two places I had to tell it to default to spaces and then when I hit tab it puts in spaces. 

Sometimes when I copy code from one place to another the indent is wrong and I have trouble finding it as it is hidden. I end up deleting a lot of spaces and reseting to fix it but that is the only issue I have had.

---

### Post by GenBattle on 2010-08-18
The whole anti-tab anathema is because of the inconsistency of tab spacing between editors; some read a tab as 8 spaces, some as 4, some as 5, etc.

Me, i still use tabs :-P

---

### Post by Bachstelze on 2010-08-18
> **GenBattle said:**
> The whole anti-tab anathema is because of the inconsistency of tab spacing between editors; some read a tab as 8 spaces, some as 4, some as 5, etc.

Not to mention that most editors let the user define the "width" of a tab, and that using tabs require you to only indent your code in 8 characters increment (or 4 or whatever you set your tab width to).

---

### Post by worksofcraft on 2010-08-18
lol, kewl

May I take it you guys approve of using tab indents too then ;)

---

### Post by nvteighen on 2010-08-19
I don't remember how I set Emacs up, whether to use tab = 8 spaces, tab = 4 spaces or tab = tab :p

About self:

It's annoying but it's a great idea: it makes OOP consistent with the idea that a procedure (i.e. a method in this case) should only know about what it gets from the argument list. If you avoid globals, you'll appreciate how clear your code gets when following that rule.

Btw, if you don't like the word 'self', you could name it however you like, because the instance is passed to the method's first argument regardless of how that argument is named. Some people prefer to follow the C++ tradition and name it 'this'.

---

### Post by worksofcraft on 2010-08-19
> **nvteighen said:**
> 
... Some people prefer to follow the C++ tradition and name it 'this'.

Yes having conventions does help with intelligibility. The problem starts when different people use different conventions.
I once adopted convention to name "don't care" parameters "_" like they do in Prolog, but I've been learning gettext package that uses _ to mean "translate to user's locale" and Python uses _ to identify the most recent result!

Now there appear to be all sorts of conventions about capitalising letters in identifiers of objects, in their class names and in their method names. In human language we often capitalise the first letter of identifiers as in 'Fred, Sally and Chris are people.' Yet some programming conventions might have them write 'People fred, sally, chris;' capitalising the type and not the identifiers.

'this' is indeed a good name for the object that a method is working on, although grammatically I think it's probably the 'subject' and not the 'object'... That reminds me of a convention to always identifying the result that one intends to return from a function as 'That' (as opposed to 'this'), but then 'That' was usually the 'object' and not the 'subject') and perhaps 'this' should be called 'pThis' according to popular Hungarian notation conventions :confused:

One thing that IMO would make Python even better is if it actually *enforced* more consistent conventions and preferably adopted ones that are established already in other programming languages.

I'm not sure now whether to start using your suggestion of calling 'self', 'this' it does make sense, but as an initial reaction to the language, I would have preferred being forced to identify the occasional *global* variable as being outside an implicit current context and dispense with the ubiquitous 'self' identifiers.

---

### Post by worksofcraft on 2010-08-20
I was studying gstreamer and atm I am on the tutorial [http://pygstdocs.berlios.de/pygst-tutorial/capabilities.html](http://pygstdocs.berlios.de/pygst-tutorial/capabilities.html) Examples are all written in Python.

One thing that struck me is that each one ends up being a single instance of one complex big object that has a gui and all the other bits bolted in.
 
It seems a prime case for multiple inheritance and polymorphism: Encapsulating independent functionality in separate classes and importing the earlier examples for further derivation with just a few lines of extra functionality.

While I'm having a go at that does anyone have views on how effective object oriented technology actually is in Python?

----
update:
I split the "big object" from example 2.1 of that tutorial into a separate Gui class and a GStreamer class, that were both inherited by an Audio-Player application class. Then it was very very easy to import that into another Python script where with one extra method and an extra bit for the constructor a Video-Player class could be derived.

Thus object oriented application of Python looks very promising :)

---

### Post by CptPicard on 2010-08-21
> **worksofcraft said:**
> I would have preferred being forced to identify the occasional *global* variable as being outside an implicit current context and dispense with the ubiquitous 'self' identifiers.

Well, you do have to identify them exactly like that, with the "global" keyword.

If the "self" wasn't there, then we would really lose consistency in the rather loose association there is between objects and functions in Python... we'd have to somehow deal with the issue that sometimes the function may be attached to an object as a method, and sometimes it may be standalone, and the self/this may actually just be something that was passed in.

---

### Post by worksofcraft on 2010-08-22
> **CptPicard said:**
> Well, you do have to identify them exactly like that, with the "global" keyword.

If the "self" wasn't there, then we would really lose consistency in the rather loose association there is between objects and functions in Python... we'd have to somehow deal with the issue that sometimes the function may be attached to an object as a method, and sometimes it may be standalone, and the self/this may actually just be something that was passed in.

Yes good point. Just defining a variable outside of other classes and functions makes them global, but when reading the code inside a function it isn't immediately obvious that we aren't dealing with a local variable. I noticed Google recommend a convention naming Globals in all capital letters, so I'll adopt that standard now.

Now another practical aspect of Python as a language is the way variables just get introduced without any kind of declarations. Only minutes ago I found an unpredictable bug where I had obtained a value from the gui, did some calculations and then was comparing it for equality...

```

    warnings = self.adjustment.get_value()
    ...
    if warnings == 1:
        ...

```

... by MY oversight 'warnings' is going to be a floating point number in which calculations can produce tiny errors. Thus comparing it for equality is really dumb. Other languages would have warned me about type mismatch or even cast float to int which was exactly what I really wanted in this case ;)

---

