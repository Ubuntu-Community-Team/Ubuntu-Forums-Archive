---
title: "Programming language - simple GUI"
date: 2009-06-12
forum: Programming Talk
---

### Post by MadnessRed on 2009-06-12
Hi, I have been programming with php for a while, and I am fairly good with it, though I don't know classes yet.

I am looking for a programming language, that has a fairly easy implmentation of a gui. PHP's gui was very easy as you just print (or echo) in html, and I was kind of hopefing for a desktop language that lets you do omething slight differnt, rather than having the gui and the programming completely sepparate which is what qt seemed to have.

I would also like a gui that works windows and linux if possible,

---

### Post by nvteighen on 2009-06-12
> **MadnessRed said:**
> Hi, I have been programming with php for a while, and I am fairly good with it, though I don't know classes yet.

I am looking for a programming language, that has a fairly easy implmentation of a gui. PHP's gui was very easy as you just print (or echo) in html, and I was kind of hopefing for a desktop language that lets you do omething slight differnt, rather than having the gui and the programming completely sepparate which is what qt seemed to have.

I would also like a gui that works windows and linux if possible,
Python.

Other high level languages apply to this too, but Python has great support for cross-platform GUI toolkits like Qt, GTK+ or wxWidgets.

---

### Post by fr4nko on 2009-06-12
> **nvteighen said:**
> Python.

Other high level languages apply to this too, but Python has great support for cross-platform GUI toolkits like Qt, GTK+ or wxWidgets.
I agree, Python can be a very good choice. Otherwise you have more complex C++ toolkits like Qt, FOX, fltk or, in C, GTK+. Fltk can be a good choice because it is very simple and lightweight but it does not have all the features of the most complete toolkits.

Another alternative is Java. I'm not an expert of Java but I think that GUI programming in Java is not easy and I don't recommend you this programming language. It is nevertheless true that with Java you can create very nice and full-featured user interfaces and the responsiveness is very good. The problem is the huge memory footprint and the starting time.

I hope that helps but be aware, GUI programming is never very easy. With python is a lot simpler but this is at the expense of the performance (responsiveness, memory usage, time to initialize, etc.).

Francesco

---

### Post by blackxored on 2009-06-12
Python/Glade.
Python/wxWidgets
Java/Swing

---

### Post by lykwydchykyn on 2009-06-12
I also started with php and html, and I can tell you right now that transitioning to writing client-side stuff with a GUI toolkit is going to take some adjustment.  

My php code was predominantly procedural, whereas every GUI toolkit I've seen is object-oriented.  So if you haven't done any object-oriented programming, that's the first thing you want to understand.

As far as which toolkit, I'd recommend walking through a beginner's tutorial on several of them before settling on one.  TK, Qt, Gtk, and Wxwidgets are all cross-platform, so that's not really an issue.

The biggest difference, from a programmer's perspective, that I see between them is how they each do event handling (that is, how you make user actions actually do something).  I eventually gravitated to Qt on the basis of its event handling system because it made the most sense to me.  But that said, Qt is probably not the easiest toolkit to learn, especially if you're trying to learn it on Python or some other non-C++ language (Qt is heavily C++ oriented, and the documentation for it in other languages is lacking -- so I have to usually refer to the C++ documentation and translate it to Python with a bit of guesswork).

---

### Post by MadnessRed on 2009-06-12
i have recently started trying python again, last time i tried I gave up coz I couldn't work out how to compile it :/ though it was a compilable language, I know now that you don't compile it, (or do you), but I can do basic programs. Will try and learn it a bit, more, any suggestions about good tutorials, or should I just go for google and se which ones look good.

---

### Post by Can+~ on 2009-06-12
> **MadnessRed said:**
> i have recently started trying python again, last time i tried I gave up coz I couldn't work out how to compile it :/ though it was a compilable language, I know now that you don't compile it, (or do you), but I can do basic programs. Will try and learn it a bit, more, any suggestions about good tutorials, or should I just go for google and se which ones look good.

It's interpreted actually, but it's compiled into .pyc for speed.

```
python myscript.py
```

and you're set.

For tutorials, the pydoc's tutorial is pretty good actually:
[http://docs.python.org/](http://docs.python.org/)

---

### Post by MadnessRed on 2009-06-12
> **Can+~ said:**
> It's interpreted actually, but it's compiled into .pyc for speed.

```
python myscript.py
```

and you're set.

For tutorials, the pydoc's tutorial is pretty good actually:
[http://docs.python.org/](http://docs.python.org/)

I have been doing the
[PHP]#!/usr/bin/python [/PHP]
I find it a bit easier, is there any adantages between the two?

pw: I found easy gui, it seem very easy but I don't like it, its a bit blocky, GTK is the gui that gnome uses by default, I mean go to system >  preferenes > appearence, that box is gtk?

---

### Post by lykwydchykyn on 2009-06-12
Well, you might start with tkinter; it's probably the easiest and most straightforward.  Downside is that it looks awful and (IMHO) the event handling probably doesn't scale well.  I went through this tutorial a while back and it helped:
[http://www.pythonware.com/library/tkinter/introduction/](http://www.pythonware.com/library/tkinter/introduction/)

For GTK, I went through this tutorial and got a lot out of it:
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

Downside is that the tutorial is four years old and some stuff may be outdated.  I was doing ok with GTK until I got into the bit about menu building and saw that I had to make an xml file just to do a menu.

For pyQt, I haven't found a really good online free tutorial.  I ended up buying a book on it which got me started.  Unfortunately if you search for "pyqt tutorial" you end up with a lot of Qt3 stuff, which is different enough from Qt4 to make it not really useful.  About the only one I've found is this:
[http://www.zetcode.com/tutorials/pyqt4/](http://www.zetcode.com/tutorials/pyqt4/)
And it's not very complete.  

I never got far with wxwidgets, and that was years ago so I won't suggest anything there.

---

### Post by blackxored on 2009-06-12
Of course, most times you will have to use OOP. 
You should consider getting used to it before anything. I haven't ever adopted php because of this. 
With python the transition will be more transparent than with another language, because python itself doesn't force and OO paradigm, contrary to Ruby or Java or C#. Give it a try. Tk is fairly easy to learn. Gtk has a little step learning courve that could be simplified using glade and python bindings (that's the one I've used most). Other toolkits are available, but since I haven't used them, I won't give comments, such as PyQT, wxWidgets and the like. Yes, I know I've missed wxWidgets, but when I use Python GUIs I mostly do gnome developement. Otherwise, I use Django in  web, and some command line frameworks the other time.

---

### Post by Can+~ on 2009-06-12
> **MadnessRed said:**
> I have been doing the
[PHP]#!/usr/bin/python [/PHP]
I find it a bit easier, is there any adantages between the two?

Both do the same thing, but just install geany or any IDE and hit the execute button.

---

### Post by fr4nko on 2009-06-12
> **Can+~ said:**
> It's interpreted actually, but it's compiled into .pyc for speed.
I believe that the compiled python code does not run faster than just executing the scripting. The difference is only during the loading time, which is actually faster with compiled code but the execution time is just the same.

You can look[COLOR=Blue] [here]("http://docs.python.org/tutorial/modules.html#compiled-python-files") [/COLOR]to have a more authoritative source of information.

Francesco

---

### Post by Can+~ on 2009-06-12
> **fr4nko said:**
> I believe that the compiled python code does not run faster than just executing the scripting. The difference is only during the loading time, which is actually faster with compiled code but the execution time is just the same.

You can look[COLOR=Blue] [here]("http://docs.python.org/tutorial/modules.html#compiled-python-files") [/COLOR]to have a more authoritative source of information.

Francesco

I meant faster, as not having to recompile each time. Actually, python checks for the .pyc first, if not available or outdated, go for the .py and generate the .pyc

---

### Post by ranthal on 2009-06-12
> **MadnessRed said:**
> I have been doing the
[PHP]#!/usr/bin/python [/PHP]
I find it a bit easier, is there any adantages between the two?

I believe #! is Linux specific so for the OP this wouldn't be applicable but given that this is a forum based around Linux I prefer the using #! to keep it consistent with other bash scripts.

So that's a
+1 for Python/PyQt

Scripting languages are simple and easy to run and test.  If you haven't worked with scripting before ti takes a little bit of adjusting to the idea that it's more forgiving (sometimes to a fault) than compiler-based languages like C, but I'd recommend the O'Reilly book on Python and PyQt (just torrent them) and you can be writing simple scripts by the end of the day.

---

### Post by pokerbirch on 2009-06-12
At the risk of being heckled, bullied and laughed at, i'm going to say Gambas. The syntax is very similar to Visual Basic 6, so a bit old fashioned looking. The GUI builder is a very likable drag n' drop style which hides the boilerplate code but gives you full control when you need it. Some of the components are a bit limited, but the language is growing nicely: [http://gambasdoc.org/help/comp](http://gambasdoc.org/help/comp)

---

### Post by nvteighen on 2009-06-12
> **MadnessRed said:**
> I have been doing the
[PHP]#!/usr/bin/python [/PHP]
I find it a bit easier, is there any adantages between the two?

Well... the difference is that using the shebang (#!) will allow you to set execution permission to the script and run it just using ./ as it were a binary executable and not calling the interpreter explicitly. This is not Python-specific, but true for almost all scripting languages.

> **blackxored said:**
> Of course, most times you will have to use OOP. 
You should consider getting used to it before anything. I haven't ever adopted php because of this. 
With python the transition will be more transparent than with another language, because python itself doesn't force and OO paradigm, contrary to Ruby or Java or C#. Give it a try. Tk is fairly easy to learn. Gtk has a little step learning courve that could be simplified using glade and python bindings (that's the one I've used most). Other toolkits are available, but since I haven't used them, I won't give comments, such as PyQT, wxWidgets and the like. Yes, I know I've missed wxWidgets, but when I use Python GUIs I mostly do gnome developement. Otherwise, I use Django in  web, and some command line frameworks the other time.

It's curious... because Python does force you to OOP but it allows you to hide it :)

But yes, GUI is usually OOP. Why? Because OOP is the best paradigm for such a task where you have to make windows, mice and text boxes (among others) interact with eachother... It's natural. And sometimes you'll have to build your own classes to extend the toolkit's basic functionality.

> **pokerbirch said:**
> At the risk of being heckled, bullied and laughed at, i'm going to say Gambas. The syntax is very similar to Visual Basic 6, so a bit old fashioned looking. The GUI builder is a very likable drag n' drop style which hides the boilerplate code but gives you full control when you need it. Some of the components are a bit limited, but the language is growing nicely: [http://gambasdoc.org/help/comp](http://gambasdoc.org/help/comp)

Gambas and VB have a major issue. They make you adapt your code to the GUI... instead of adapting the GUI to the underlying code. It inverts the priorities... The GUI should be just another possible interface for interacting with a function library... If you can't make your program change its interface without affecting how the inner code works, then your design is bad. Separate interface from implementation, always! Not that you can't do that in Gambas or VB, the issue is that it's much difficult to do it properly in them than as I described above. (The "right thing" in VB would be to never code implementation in the Forms' code, but in Modules or even Class Modules compiled into a .DLL...).

---

### Post by MadnessRed on 2009-06-12
wow, a lot of responces, well tkinter is what easygui is based on, and it looks terrible, sorry. I tried GTK, and I read a tutorial and this is my current app.
(I will try the tutorial in the post now.)

For want of something to do its has a play and pause button for starting and stopping banshee, I know its pointless as there is already and button on the keyboard which does that far more efficiently but it was something to make.



[PHP]#!/usr/bin/python

#Basic GTK Aplication

# Import GTK libraries
import pygtk
import gtk

# Import any other libraries
import os

#Start GTK class
class GTKApp(gtk.Window):
	
	#All of own functions
	def banshee_play(self, widget, data=None):
		os.system('banshee --play')
	
	def banshee_pause(self, widget, data=None):
		os.system('banshee --pause')
	
	#Main function/body ect
	def __init__(self):
		#Startthe gtk app, or do something
		super(GTKApp, self).__init__()
		
		#Set the title, window size and position
		self.set_title("Banshee Play/Pause")
		self.set_size_request(190, 75)
		self.set_position(gtk.WIN_POS_CENTER)
		
		#Add make play pause buttons
		button_play = gtk.Button(stock=gtk.STOCK_MEDIA_PLAY)
		button_pause = gtk.Button(stock=gtk.STOCK_MEDIA_PAUSE)
		
		#And when buttons are clicked
		button_play.connect("clicked", self.banshee_play, None)
		button_pause.connect("clicked", self.banshee_pause, None)
		
		# Make a fixed widget to hold hte buttons
		fixed = gtk.Fixed()

		# Add the buttons
		fixed.put(button_play, 20, 30)
		fixed.put(button_pause, 100, 30)
		
		# On window close, exit program
		self.connect("destroy", gtk.main_quit)
		
		# Add the fixed widget and show all.
		self.add(fixed)
		self.show_all()

#And run the program
GTKApp()
gtk.main()[/PHP]

Also is there an equivelent to shell_exec() from php?

> >>> title = os.system('banshee --query-title')
title: Viva La Vida
>>> title
0


I think, (I may be wrong, this is mostly guessing) that the function banshee --query-title
is something like
print "title: "+title
return 0

so its returning 0 which python is reading but the title is being printed), so can I do somethign like shell_exec and get the printed output of a function?

I will also try and get it to only have 1 button play or pause and then it detects weather music is playing or not as to which is shown.

---

### Post by lykwydchykyn on 2009-06-12
> **MadnessRed said:**
> 

Also is there an equivelent to shell_exec() from php?



I think, (I may be wrong, this is mostly guessing) that the function banshee --query-title
is something like
print "title: "+title
return 0

so its returning 0 which python is reading but the title is being printed), so can I do somethign like shell_exec and get the printed output of a function?

I will also try and get it to only have 1 button play or pause and then it detects weather music is playing or not as to which is shown.

used to be os.popen, but that's being deprecated.  I think now you want to use:
[http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

---

### Post by MadnessRed on 2009-06-13
> **lykwydchykyn said:**
> used to be os.popen, but that's being deprecated.  I think now you want to use:
[http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

doesn't seem to work for me, any tutorials on how to use it?

---

