---
title: "Trying to make a simple application"
date: 2008-01-13
forum: Programming Talk
---

### Post by ~LoKe on 2008-01-13
Sorry, I'm sure this is the wrong forum for my question but what I'm not sure is which would be the right one.

Basically, I'm trying to create a simple GTK app.  Very simple.  I want to be able to click on a button and have a window open that will allow me to select a file.  Then I want to be able to click another button which runs a script/commands on the file I selected.

Basically I want to add a movie and then convert it to a different format.  I realize there are many programs that do this, but I want to try making my own.

What I basically need to know is...

Which programs would I need for this?  Which language would be easiest for me to learn, and easiest to use (remember, I'm not trying to do anything complex).

I already have Glade, and I've "designed" the GUI, but I don't know how to make it "work".

Any suggestions on where I could start?

---

### Post by LaRoza on 2008-01-13
Python would be a good language, fast to learn and use.

You might find EasyGUI (and Python) have all you need.

See my wiki for information on both.

(Tcl and others could also be good at what you want, but will take longer to learn)

---

### Post by moephan on 2008-01-13
I second python. It sounds perfect for your application. There are a few tutorials floating around that help. This one is frequently cited:
[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)

Cheers, Rick

---

### Post by ~LoKe on 2008-01-14
Thanks for the links!  I managed to get though the tutorial without too much trial (as it's copy & paste), and now know how things kinda work.  However, I'm not sure where to proceed next.

I found [this](http://www.pygtk.org/pygtk2reference/class-gtkfilechooser.html) page which shows me the code I'd need to create the filechooser, but I'm not really sure how to **do** it.  Which "defs" do I need in the filechooser class in order to have a simple file selector (once that's figured out, I can add more to make it more to my liking)?

Could anyone possibly give me an example of what the class would look like for *any* kind of filechooser?  Or point me in the direction of such an example?  I'll peruse the previous links to see if I can find anything (I'm sure there'll be something, but it'll take a while to find it), but if someone could provide this or show me the way, it would save some time (and frustration :lolflag:)

Time to continue reading.

Thanks everyone!

**EDIT**: I found [this](http://www.pygtk.org/pygtk2tutorial/examples/filechooser.py).  Progress!

---

### Post by vambo on 2008-01-14
Have a look at this 
[http://www.pygtk.org/pygtk2tutorial/sec-FileSelections.html]("http://www.pygtk.org/pygtk2tutorial/sec-FileSelections.html")

---

### Post by ~LoKe on 2008-01-14
So far so good!  Is there anything particularly wrong with what I have below?  I want to make sure I'm not doing anything wrong (even though it works) just so I know better.  

```
#!/usr/bin/env python

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

class FileSelectionExample:
    # Get the selected filename and print it to the console
    def file_ok_sel(self, w):
        print "%s" % self.filew.get_filename()

    def destroy(self, widget):
        gtk.main_quit()

    def __init__(self):
        # Create a new file selection widget
        self.filew = gtk.FileSelection("File selection")

        self.filew.connect("destroy", self.destroy)
        # Connect the ok_button to file_ok_sel method
        self.filew.ok_button.connect("clicked", self.file_ok_sel)
    
        # Connect the cancel_button to destroy the widget
        self.filew.cancel_button.connect("clicked",
                                         lambda w: self.filew.destroy())
      
        self.filew.show()

def main():
    gtk.main()
    return 0


class convertGTK:
	"""Convert file application"""

	def __init__(self):
		
		#Set the Glade file
		self.gladefile = "pyconvert.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile) 
		
		#Create our dictionary and connect it
		dic = { "on_btnAddMovie_clicked" : self.btnAddMovie_clicked,
			"on_MainWindow_destroy" : gtk.main_quit }
		self.wTree.signal_autoconnect(dic)

	def btnAddMovie_clicked(self, widget):
		FileSelectionExample()

if __name__ == "__main__":
	hwg = convertGTK()
	gtk.main()
```

---

### Post by ~LoKe on 2008-01-14
Anyone?  Before I continue? :)

---

### Post by GavinZac on 2008-01-14
It seems ok to me but then I can only read so much python before my php-wired brain starts to hurt becase of the lack of brackets! :D

---

### Post by ~LoKe on 2008-01-14
> **GavinZac said:**
> It seems ok to me but then I can only read so much python before my php-wired brain starts to hurt becase of the lack of brackets! :D

I spent 10 minutes trying to figure out how to close a class, only to find that you pretty much don't.  :lolflag:

---

### Post by ~LoKe on 2008-01-14
What would you call the execution of an external command on a filename retried with the above code.  I'd like to read about it to learn, but I don't even know what to call that...process.

Any more tips? Back to the wiki!

---

### Post by pmasiar on 2008-01-14
> ... how to close a class...

It is not a bug - it is a feature. If structure of your code looks right, it is right.

For wisdom of Python (Zen), try in shell: "import this".

And if you miss braces, try "from __future__ import braces". :-)

BTW "from __future__ ..." is standard way to get features from next versions of Python, if they were backported into old versions.

---

### Post by ~LoKe on 2008-01-14
I'm just not latching onto this at all.

I've got this class:
```
class FileSelectionExample():

    # Get the selected filename and print it to the console
    def file_ok_sel(self, w):
        print "%s" % self.filew.get_filename()

    def destroy(self, widget):
        gtk.main_quit()

    def __init__(self):
        # Create a new file selection widget
        self.filew = gtk.FileSelection("File selection")

        self.filew.connect("destroy", self.destroy)
        # Connect the ok_button to file_ok_sel method
        self.filew.ok_button.connect("clicked", self.file_ok_sel)
	self.filew.ok_button.connect("clicked", lambda w: self.filew.destroy())
    
        # Connect the cancel_button to destroy the widget
        self.filew.cancel_button.connect("clicked",
                                         lambda w: self.filew.destroy())
	self.filew.show()
```
I know the money is right here:
```
    def file_ok_sel(self, w):
        print "%s" % self.filew.get_filename()
```
But how on earth do I call this from **outside** the class?

---

### Post by Vox754 on 2008-01-14
> **~LoKe said:**
> 
Basically, I'm trying to create a simple GTK app.  Very simple.  I want to be able to click on a button and have a window open that will allow me to select a file.  Then I want to be able to click another button which runs a script/commands on the file I selected.

Which language would be easiest for me to learn, and easiest to use (remember, I'm not trying to do anything complex).


Although Python and GTK is perfectly fine, for very simple interfaces a smaller toolkit library like Tk may be easier to use. Also, I think Tcl is quite easy to learn too.

Currently, Ubuntu comes installed with Tcl/Tk 8.4, so everyone can run this
```

#!/usr/bin/env wish

button .b1 -text "Open file and use a command" \
    -command {
        set filename [tk_getOpenFile]
        set Command "echo $filename"
        eval exec $Command
        set message "Executed \"$Command\""
        tk_messageBox -type ok -message $message
        puts $message
    }

pack .b1 -padx 8 -pady 8

```

You can change what this script does by changing
[php]
        set Command "mencoder $filename -options -bla -bla -bla -etcetera"
[/php]

Save it and run it.
[php]
wish MyButton.tcl
[/php]

[See this post for more info on Tcl/Tk.](http://ubuntuforums.org/showthread.php?t=333867#6)

---

### Post by ~LoKe on 2008-01-14
That's incredibly simple and you're right, easy to learn.  Now I can make a GUI for my "program" until I can sit down and learn python properly.  I'd prefer to use a GTK front end, to mesh with the rest of my desktop.

But damn, that's awesome.

Thanks for all that!

---

### Post by pmasiar on 2008-01-14
If you want **really** simple way to build GUIs, look no further than EasyGUI : [http://www.ferg.org/easygui/](http://www.ferg.org/easygui/)

---

### Post by Vox754 on 2008-01-15
> **LaRoza said:**
> 
You might find EasyGUI (and Python) have all you need.

(Tcl and others could also be good at what you want, but will take longer to learn)
> **pmasiar said:**
> If you want **really** simple way to build GUIs, look no further than EasyGUI : [http://www.ferg.org/easygui/](http://www.ferg.org/easygui/)

LaRoza mentioned EasyGUI early in the thread but nobody cared to explain it or provide an example.
I like the fact that EasyGUI is based on Tkinter, which also brings us back to Tcl/Tk.

Really, Tcl/Tk is a very simple but powerful procedural language. It's biggest disadvantage being that it's not properly designed for Object Oriented Programming with classes and methods as most people understand it nowadays. Hence they may think that is an odd or obsolete language.

Also, you don't have to switch languages to try Tk. Just use the Tkinter module for Python; this is called Python/Tk. If you are interested there is also Perl/Tk.

This program essentially does the same thing as the Tcl version.
```

#!/usr/bin/env python

from Tkinter import *
import tkFileDialog
import tkMessageBox
import os

def RunCommand():
    filename = tkFileDialog.askopenfilename()
    Command = "echo " + filename
    os.system(Command)
    message_string = "Executed: \"" + Command + "\""
    tkMessageBox.showinfo(
        type = "ok",
        message = message_string
    )
    print message_string

ROOT = Tk()

b1 = Button(ROOT, text = "Open file and use a command",
            command = RunCommand)

b1.pack(padx = "8", pady = "8")

ROOT.mainloop()

```

If you read the Tkinter documentation you'll see that it's more pythonic to wrap the code up in classes.

In fact, it's actually true what they say, you can almost immediately write GUIs in Python with Tkinter if you already know Tcl, you just need to know how to "translate" the syntax from one language to the other. In this way you can use the same documentation reference from Tcl/Tk in Python/Tk.

[Tkinter description](http://wiki.python.org/moin/TkInter).

---

### Post by pmasiar on 2008-01-15
> **Vox754 said:**
> LaRoza mentioned EasyGUI early in the thread but nobody cared to explain it or provide an example.

EasyGUI homepage I linked provides examples. Do I have to copy-paste them? I expect anyone asking for help to click on link provided and read it. Am I too demanding? :-)

---

### Post by LaRoza on 2008-01-15
> **Vox754 said:**
> LaRoza mentioned EasyGUI early in the thread but nobody cared to explain it or provide an example.
I like the fact that EasyGUI is based on Tkinter, which also brings us back to Tcl/Tk.



My wiki, which I referenced, has links to the EasyGUI homepage and tutorials.

I didn't care to explain it, or provide an example, because I shouldn't have to. 

Nobody held my hand when I started.

---

### Post by Vox754 on 2008-01-15
> **pmasiar said:**
> EasyGUI homepage I linked provides examples. Do I have to copy-paste them? I expect anyone asking for help to click on link provided and read it. **Am I too demanding?** :-)

Ha ha. Are you too demanding? Well, YES. If there is anyone too demanding in this forum, that is you pmasiar (and CptPicard, but I'll leave him alone since he hasn't showed up in this thread).
Of course, that's not a bad thing. I really appreciate the experience  (and links to interesting articles) you bring to most threads.

> **LaRoza said:**
> My wiki, which I referenced, has links to the EasyGUI homepage and tutorials.

I didn't care to explain it, or provide an example, because I shouldn't have to. 

**Nobody held my hand when I started.**
You are totally right LaRoza.
However we can never forget this is still ubuntuforums.org, a place were people are friendly, there are step-by-step guides for everything, people are commonly hand held, [and some expect others to do their homework for them ](http://ubuntuforums.org/showthread.php?t=540120) (wrong!).

I won't argue with you guys.
I'll just say this: I felt incredibly compelled to reply to this thread because of the very simple Tk command that provides the Open File dialog.
```

    tk_getOpenFile

```

---

### Post by LaRoza on 2008-01-15
> **Vox754 said:**
> 
You are totally right LaRoza.
However we can never forget this is still ubuntuforums.org, a place were people are friendly, there are step-by-step guides for everything, people are commonly hand held, [and some expect others to do their homework for them ](http://ubuntuforums.org/showthread.php?t=540120) (wrong!).


Yes, I will walk people through installations, partitioning, changing languages (for their OS), getting Flash working (when that was a "new" problem), and other things, however, programming is different.

I write programs for people sometimes, if they need the application, but I do not ever do someone's work for them. Programming requires the individual to think on their own, look things up, and make decisions. 

The links in my wiki (and the recommendations to look into EasyGUI) are enough for someone wanting help on making a program.

---

### Post by pmasiar on 2008-01-15
> **Vox754 said:**
>  If there is anyone too demanding in this forum, that is you pmasiar 

Well, that was a rhetorical questions, not asking for real answer :-)

My point is, I just wasted couple minutes of my life looking for answer and providing link. If someone cannot waste 5 minutes of his life to follow the link, tough beans. I am willing to help people who can show determination, but if someone is just a leech, I ... now I know I should let others deal with it :-) 

I am way too strongly opinionated for this forum and have hard time arguing with random fools, gaining infractions for stupid reasons once a while.

But thanks for telling me that, I would not guess that my comments might be perceived as "too demanding". 

Maybe I read too many ESR musings about hacker's ethics, and I am comparing situation today with how hard was getting into programming back in my time, when you were lucky to get 3 batch runs of your program in a week (and one run might be wrecked by failure of card reader) :-)

Youth is wasted on the young :-)

---

