---
title: "Beginners guide to development/distribution on Linux"
date: 2008-04-07
forum: Programming Talk
---

### Post by nami on 2008-04-07
Dear Linux Experts,

I have been searching for such a guide but have been very unsucessful.  For example, how do I do the following?

1. Create a GUI program which has a single button, which when clicked, displays a message saying "Hello World".
2. Create a Deb file so it can be distributed easily and install any missing dependencies required.
3. Add it into a repository so it can be installed and updated when updates are available.

Anyone able to help?

Thanks

---

### Post by LaRoza on 2008-04-07
> **nami said:**
> 
1. Create a GUI program which has a single button, which when clicked, displays a message saying "Hello World".
2. Create a Deb file so it can be distributed easily and install any missing dependencies required.
3. Add it into a repository so it can be installed and updated when updates are available.


0. In what langugae and toolkit?
1. See the [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)
2. See above link.

---

### Post by nami on 2008-04-07
Preferably in C++.

Thanks for the linking, looking into it now.

---

### Post by Caduceus on 2008-04-07
As far as I know, C++ GUI programming isn't all that easy. If you don't know the language already, learn it first.

---

### Post by nami on 2008-04-07
Which language would you suggest?  Python?

Just to let you know that I am a programming (not C++) so I understand programming concepts.

---

### Post by LaRoza on 2008-04-07
> **nami said:**
> Preferably in C++.

Thanks for the linking, looking into it now.

There are many GUI toolkits for C++, see my wiki for some of them (GTK, QT, and wxWidgets)

---

### Post by nami on 2008-04-07
Which toolkit would be the easiest for beginners

---

### Post by LaRoza on 2008-04-07
> **nami said:**
> Which toolkit would be the easiest for beginners

For beginners, EasyGUI (for Python) and Zenity (for Bash) are the easiest.

QT, GTK and wxWidgets are feature rich and complex. They are event driven, and QT and GTK are used to make KDE and GNOME, so they have loads of functionality.

QT is mostly used on KDE
GTK is mostly used on GNOME and Xfce
wxWidgets is meant to look native on many platforms (but will look like gtk on Linux)

EasyGUI used Tk. Tk is available for many languages. It isn't really a toolkit, but it is an easy way to add a GUI to a program if you don't have a lot of demands.

---

### Post by nami on 2008-04-07
So how about a guide which:

1. Create a GUI with a button which pops up a "Hello World" message using EasyGUI + Python
2. How do create a deb file to get needed dependencies
3. How to get your prog into the repositories

---

### Post by LaRoza on 2008-04-07
> **nami said:**
> So how about a guide which:

1. Create a GUI with a button which pops up a "Hello World" message using EasyGUI + Python
2. How do create a deb file to get needed dependencies
3. How to get your prog into the repositories

```

#!/usr/bin/python
import easygui
easygui.msgbox("Hello, world!")

```

See the links

---

### Post by nami on 2008-04-07
Thanks, I'll give it a try tonight.

---

### Post by Can+~ on 2008-04-07
pyGTK isn't all that hard either

[PHP]
#!/usr/bin/env python

import gtk

try:
	import pygtk
except ImportError:
	pass

class HelloButton():
	"""Produces a simple hello world button"""
	def __init__(self, butText="hello world"):		
		self.win	= gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.button = gtk.Button(butText)
		
		self.win.add(self.button)
		self.win.connect("destroy", self.destroy_event, None)
		self.button.connect("clicked", self.click_event, None)
		
		self.win.show_all()
	
	#A call function, so that it's easier to run the window.
	def __call__(self):
		self.gtkMain()
	
	#Gtk main loop
	def gtkMain(self):
		gtk.main()
	
	# Events
	def destroy_event(self, widget, data=None):
		gtk.main_quit()
		print "Window closed!"
	
	def click_event(self, widget, data=None):
		print "Stop clicking me!"
		

# Check if it's main
if __name__ == "__main__":
	myWindow = HelloButton()
	myWindow()[/PHP]

Produces this:
[IMG]http://img.photobucket.com/albums/v517/CanXp/Screenshot.png[/IMG]

Well.. it's long, but when you use Glade to create the XML window gets easier and shorter.

---

### Post by LaRoza on 2008-04-07
> **Can+~ said:**
> pyGTK isn't all that hard either


Compared to EasyGUI?

---

### Post by Can+~ on 2008-04-07
> **LaRoza said:**
> Compared to EasyGUI?

Still is not hard, there's just a bunch of functions like connect that you memorize and then use, but overall you can learn it quickly, and later use Glade to handle the packaging.

Although it's true, EasyGUI is, as the name implies, easy and faster than gtk on the learning curve.

---

### Post by pmasiar on 2008-04-07
Python shines again! :-)

@OP: Before you are skilled enough to make your program available and useful to others, you need to learn much more programming. Much more, so you don't ask trivial questions like first one. Think about doing your homework. Wiki in my sig has links to many training task to solve. Asking even trivial question is OK, but you have years of learning ahead of you. Good luck, and have fun!

---

### Post by nami on 2008-04-07
> **LaRoza said:**
> ```

#!/usr/bin/python
import easygui
easygui.msgbox("Hello, world!")

```

See the links

I'm guessing a little more is involved than just typing this into a text editor.

---

### Post by pmasiar on 2008-04-07
> **nami said:**
> I'm guessing a little more is involved than just typing this into a text editor.

Of course - you also need to install easyGUI. But after that, this is really all you need.

---

### Post by cmat on 2008-04-07
> **pmasiar said:**
> Of course - you also need to install easyGUI. But after that, this is really all you need.

easyGUI if I can recall is a module that accompanies your own code. It can be imported as a module into your python application without having to install it. Also pyGTK is very simple and even simpler with Glade.

---

### Post by LaRoza on 2008-04-07
> **cmat said:**
> easyGUI if I can recall is a module that accompanies your own code. It can be imported as a module into your python application without having to install it.

Yes, EasyGUI is a single Python file. You just need to download it and import it.

---

### Post by stevescripts on 2008-04-08
This thread prompted me to d/load easyGUI and tinker just a bit - seems to be
a nice wrapper around Tk (at first glance, perhaps easier than Tkinter ...)

Seems to warrant further tinkering.

---

### Post by slavik on 2008-04-08
> **pmasiar said:**
> Python shines again! :-)

@OP: Before you are skilled enough to make your program available and useful to others, you need to learn much more programming. Much more, so you don't ask trivial questions like first one. Think about doing your homework. Wiki in my sig has links to many training task to solve. Asking even trivial question is OK, but you have years of learning ahead of you. Good luck, and have fun!
Not really, Perl does everything with GTK that Python can do. One thing they both have that C and C++ cannot have is that you can put all the callbacks into a package/class and call the function to automatically connect all the callbacks. :) (don't know if Ruby has the corresponding function)

and unless you use treeview, the code becomes almost as easy and simple to write as Visual Basic (that is the only thing I like about MS VB is that you can double click on a button in the designer and it takes you to the burron's callback routine). but even after practice with treeview, it becomes very simple to use.

---

### Post by nami on 2008-04-08
So once I have created the code and downloaded the EasyGUI file, does the whole thing need to be compiled?  Or can it be run just like that?  I've not tried this yet, didn't get a chance last night...

---

### Post by LaRoza on 2008-04-08
> **nami said:**
> So once I have created the code and downloaded the EasyGUI file, does the whole thing need to be compiled?  Or can it be run just like that?  I've not tried this yet, didn't get a chance last night...

Download the easygui.py file. 

Put it in your home directory, open terminal, type "python".

Now type "import easygui".

If you don't get an error, it is loaded and ready. Then you can run the example code to see it work.

For using in scripts, it just has to be imported. I tend to keep a copy of it with the programs that will use it.

---

### Post by pmasiar on 2008-04-08
> **slavik said:**
> Not really, Perl does everything with GTK that Python can do. One thing they both have that C and C++ cannot have is that you can put all the callbacks into a package/class and call the function to automatically connect all the callbacks. :) .

That's the whole point. EasyGUI does not have confusing features like callback, events, etc. All GUI is just plain function calls, read the docs. That's why is easy, and much better for beginners than any Perl solution I am aware of. Do you know something comparably simple for Perl? Links?

---

### Post by LaRoza on 2008-04-08
> **pmasiar said:**
> That's the whole point. EasyGUI does not have confusing features like callback, events, etc. All GUI is just plain function calls, read the docs. That's why is easy, and much better for beginners than any Perl solution I am aware of. Do you know something comparably simple for Perl? Links?

EasyGUI is just Tkinter, so it would be relatively easy to make an equivalent for Perl. 

Now that I think about it, it seems like an interesting project....

---

### Post by pmasiar on 2008-04-08
> **LaRoza said:**
> EasyGUI is just Tkinter, so it would be relatively easy to make an equivalent for Perl. 

Obviously. Writing clone of something is much simpler - someone solved hard questions about API design.

Real question is, why Perl community never bothered to do it? This is exactly what I like in Python community: if you do something common, there should be one obvious way to do it right. What can be more common than simple GUI frontend for simple app?

---

### Post by LaRoza on 2008-04-08
> **pmasiar said:**
> 
Real question is, why Perl community never bothered to do it? This is exactly what I like in Python community: if you do something common, there should be one obvious way to do it right. What can be more common than simple GUI frontend for simple app?

I don't know why they didn't. Perhaps I'll try (although I don't know Perl, how hard can it be now that the work is already done?)

---

### Post by slavik on 2008-04-08
> **pmasiar said:**
> That's the whole point. EasyGUI does not have confusing features like callback, events, etc. All GUI is just plain function calls, read the docs. That's why is easy, and much better for beginners than any Perl solution I am aware of. Do you know something comparably simple for Perl? Links?

just function calls? so you mean callbacks ...
but when should those calls be made? when the mouse moves over a button, when the mouse is pressing the button, when the mouse leaves the button?

what is your issue with Perl again?

---

### Post by stevescripts on 2008-04-08
Seeing as how we have mentioned tkinter a few times, I feel we may be remiss in not
providing the OP with a simple tkinter example ... so, here is one 

```

#!/usr/bin/python

from Tkinter import *

import tkMessageBox

root = Tk()

root.title("Hello")

def mycommand():
	tkMessageBox.showinfo("Hello", "Hello World!")

b = Button(root, text="Push ME!", padx=32 ,command=mycommand )

b.pack()

root.resizable(0, 0)

root.mainloop()

```

Using easyGUI is, in this case, obviously simpler.

Realizing that Python has a great deal of the mindshare here,
(not without good reason, I hasten to add ;) )

I would be remiss, as a tcl/tk advocate, to not include a simple
tcl/Tk example for the OP to peruse:
```

#! /usr/bin/tclsh
package require Tk

pack [button .b -text "Push ME!" -command {mycommand} -padx 32]

proc mycommand {} {
	tk_messageBox -title "Hello" -message "Hello World!" -type ok
}

wm title . "Hello"

```

Again, no compilation required .  Just save it, and chmod +x.

RubyTk and PerlTk scripts quite similar.

I have nothing against other GUI toolkits, BTW.

Hope this is somewhat informative to sombody.

Steve
PS - I also agree with LaRoza and pmasiar about wondering
why none of the Perl folks have done something similar to easyGUI for PerlTk ...

---

### Post by pmasiar on 2008-04-08
> **slavik said:**
> just function calls? so you mean callbacks ...

No, I mean function calls. Please check docs, it's couple screens long.

> what is your issue with Perl again?

My issue is why Perl community never created the clone which LaRoza might do. Are simple solutions worth doing?

---

