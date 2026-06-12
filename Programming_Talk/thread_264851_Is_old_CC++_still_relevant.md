---
title: "Is old C/C++ still relevant?"
date: 2006-09-25
forum: Programming Talk
---

### Post by elpuerco on 2006-09-25
I learned C/C++ back in the early '90s and stopped around '95 - '96.

I have a number of books which aided me at the time, some if not all were for Borland C++ running under Windows.

Would these still be relevant in relearning C/C++ in KDevelop, (once I get it working that is:confused: ).

Or should I be trying to locate a up to date C++ guide of the generic variety?

---

### Post by Jessehk on 2006-09-25
I'm a C++ beginner, so this should be taken with a grain of salt. 

Recent additions include namespaces, exceptions, templates, the STL, and the boost library. Furthermore, I think there have been several changes to the standard since then (like using iostream instead of iostream.h)

If you are going to use C++ (not really recommended unless you need low-level, or speed-dependant code), I would recommend picking up a more modern book.

---

### Post by thumper on 2006-09-25
C++ became an ISO standard in 1998 (or was that 1997?).  Either way what you learned in the early 90s *will* be out of date.

Pick up a book like Accelerated C++ by Koenig and Moo.

After that go for: Exceptional C++ and More Exceptional C++ by Herb Sutter, Effective C++ and More Effective C++ by Scott Meyers, The C++ standard library by Josuttis.

---

### Post by elpuerco on 2006-09-25
> If you are going to use C++ (not really recommended unless you need low-level, or speed-dependant code), I would recommend picking up a more modern book.
Reply With Quote

Ah crap!  'not really recommended'!!!  ](*,) 

I have just got KDevelop installed and I think correctly, have been informed I can use QTDesigner rather that KDevDesigner so was on my way to start to look at C++ again!

I want to write 'simple' GUI interface programs to start off with, you know the sort of baby applets for personal use and fun, a DB frontend, a text editor..just for educational experimenting and fun.

So previously I was offered python, but having no IDE for it scared me off.

OK, begging question here.....

Is python the one I need and can I create apps with KDevelop and QTDesigner with it?  ](*,)

---

### Post by tbrownaw on 2006-09-25
> **Jessehk said:**
> If you are going to use C++ (not really recommended unless you need low-level, or speed-dependant code),
Or unless you want to be able to, y'know, actually do useful stuff without fighting the language...

---

### Post by tbrownaw on 2006-09-25
> **elpuerco said:**
> Ah crap!  'not really recommended'!!!  ](*,) 
[SNIP]
OK, begging question here.....

Is python the one I need and can I create apps with KDevelop and QTDesigner with it?  ](*,)

The "not really recommended" is entirely subject to debate. Python does seem to be popular in Ubuntu-land and I know there are GTK bindings for it (pygtk), but I don't know about QT bindings (there probably are, just I don't know what they're called).

I personally like staying with something where I actually get type safety and a compiler that yells at me if I give something the wrong kind of argument (ie, not python. C++ is good.).

---

### Post by IYY on 2006-09-25
Gnome apps are often coded in good old C.

---

### Post by elpuerco on 2006-09-26
:) Thnx for the feedback :) 

After spending way too long fighting trying to get KDevelop configured so I can actually access the manuals, failing to get KDevDesigner to access the manauls and then being confused as to whether I should be using KDevelop & KDevDesigner or Kdevelop & QTDesigner without even beginnig to start to relearn a single line of code I installed Boa Constructor.

This is more like it as I installed it.  It is ready to go with the environment all set and user guide, help etc all ready to view.

The result...

I spent an hour last night starting to learn the Boa IDE and and hour learning the start of python.

So for now I shall see how I get on with pyhton as I know jack about it at present but it might be a refreshing educational experiment for me.

I remember hardly anything of C++ as it has been 11 years since I did anything in it so now I have an IDE that will allow me to learn the language (python) rather than struggle to get the manuals to work I will see how it goes.

I guess I will figure out soon enough if it is the right decision.

The type safety and compiler issue did raise my eyebrows a bit but I will see how it goes.....;)

---

### Post by Gotterdammerung on 2006-09-26
> **Jessehk said:**
> Recent additions include namespaces, exceptions, templates, the STL, and the boost library. 

These are really not new. These are old C++ defs.

C/C++ is "the language". The rest is user interface.

---

### Post by thumper on 2006-09-27
Using templates as a meta-programming language however is still new, and used extensively by boost.

The language isn't C/C++, just C++.  C is an entirely different language.

---

### Post by tseliot on 2006-09-27
> **tbrownaw said:**
> The "not really recommended" is entirely subject to debate. Python does seem to be popular in Ubuntu-land and I know there are GTK bindings for it (pygtk), but I don't know about QT bindings (there probably are, just I don't know what they're called).
It's PyQT

---

### Post by ephie on 2006-09-27
Hello guys!

Does someone know how to get Qt4 working under Ubuntu!

I just can't seem to get the last *make* going when compiling my hello.cpp file

Thanks for your response!

---

### Post by tseliot on 2006-09-27
> **ephie said:**
> Hello guys!

Does someone know how to get Qt4 working under Ubuntu!

I just can't seem to get the last *make* going when compiling my hello.cpp file

Thanks for your response!

Someone else already posted about QT4 and I don't know if it can be installed on Dapper without breaking things.

Edgy has (also) QT4 and PyQT4. I suggest you to wait for it.

---

### Post by elpuerco on 2006-09-29
When I was trying to get KDeveloper and QTDesigner to work I removed QT3 and tried to install QT4 and my system got trashed.

However a restore from image got me working back in under 5 minutes :) 

I thought I had done something wrong but now I see from this thread I had not...

ever learning :D

---

### Post by elpuerco on 2006-09-29
Huh!

back to searching for a suitable IDE once more after spending 3 days on BOA only to find that the oddities and crashes were not me but actually a flaky IDE.

How did I come to this conclusion?  Well the things that happened to me whilst using it just happen to be in this interesting review!

[http://spyced.blogspot.com/2005/09/review-of-6-python-ides.html](http://spyced.blogspot.com/2005/09/review-of-6-python-ides.html)

So my journey starts all over again ](*,) 

Python or C++ ...... ??? ..... will I ever find out :confused:

---

### Post by moephan on 2006-09-30
For your purposes, definately Python. It will be way more fun and productive. C++ is still relevant and important, but for the programs you describe, it isn't really appropriate.

I think Python is easy to use without an IDE.

Cheers, Rick

---

### Post by elpuerco on 2006-09-30
Well the reason I like the idea of an IDE is the help it provides to you in developing your applications, speaking from a MS defector that is.

I see that there is python, wxpython, widgets wxwidgets etc so lots to get my head around.

I am still yet to really learn a single line of python of any flavour which is a shame!  In MS I would have installed the VB.NET suite and spent the last week leanring to program.

So far I have wasted a week for no output and nothing learned.

I spent all last night trying to install python2.5 with no joy which is a bummer.  I have the tarball but am unsure if I should use this to install in on my Kubuntu setup.

see:
 
[http://www.ubuntuforums.org/showthread.php?t=268218](http://www.ubuntuforums.org/showthread.php?t=268218)

---

### Post by moephan on 2006-09-30
Paul,

1. Are you sure you don't have Python installed already? If you open a terminal and enter the command "python", you should get to an interactive python session. I don't think Ubuntu really works without Python installed.

2. I totally understand your perspectives on IDEs. I rely on Microsoft programming for pretty much 100% of my income. Visual Studio is a fantastically productive environment for writing code on the Windows platform. However, Linux is a different platform. In some ways it is more simple and strait forward.

I emailed you a document that might help you get started. Here's also are some links if you haven't seen them yet:

Dive into Python to get you rolling:
[http://diveintopython.org/](http://diveintopython.org/)

Python tutorial:
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

The Python language reference:
[http://docs.python.org/ref/ref.html](http://docs.python.org/ref/ref.html)

The Python class library:
[http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)

the pyGtk tutorial:
[http://www.moeraki.com/pygtkreference/pygtk2tutorial/](http://www.moeraki.com/pygtkreference/pygtk2tutorial/)


Cheers, Rick

---

### Post by elpuerco on 2006-10-01
Hi Rick,

I have the document, thanks I will see how it goes.

I do have Python installed but was trying to install 2.5 which I have now done.

I have started reading the doc and see that I should first spend an hour or so reading thru some of the links you provide here so will do that...

watch this space :D

---

### Post by argie on 2006-10-01
> **elpuerco said:**
> 
So previously I was offered python, but having no IDE for it scared me off.

Python does have an IDE, Idle. It's quite nice, but for some reason the syntax highlighting doesn't kick in until the script is saved once on the Linux version.

---

### Post by po0f on 2006-10-01
When doing Python development, I usually have two terminals and a web browser open.  One terminal for Vim, one for Python's interactive interpreter, and the web browser for docs.  If you're uncomfortable with Vim, substitute Gedit for the terminal with Vim.  When working with Python, I feel that an IDE gets in the way.  Granted, I haven't written any programs in Python, just at most scripts with around 150 lines or so.

---

### Post by christhemonkey on 2006-10-01
I usually have one terminal with two tabs,
one for executing my script with python, the other for running the interpreter help("search terms") is your friend :p
I also have a gedit open to edit my script.

---

### Post by elpuerco on 2006-10-02
Moephan,  I know have my system restored to python 2.4 and am trying the code as follows:

```

#!/usr/bin/env python

import pygtk

pygtk.require('2.0')

import gtk

class GUI_Form:

 def __init__(self):
  self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
  self.window.set_title("Finally, a GUI")
  self.window.show()

 def main(self):
  gtk.main()

if __name__ == "__main__":
 frm=Form()
 frm.main()

```

I saved it into a file called window.py and then changed the permissions thus chmod 755 window.py

Now when I try to run it like this ./window.py

I get this error?

Traceback (most recent call last):
  File "./window.py", line 20, in ?
    frm=Form()
NameError: name 'Form' is not defined


any ideas?

---

### Post by elpuerco on 2006-10-02
frm = GUI_Form() not frm = Form()

---

### Post by moephan on 2006-10-02
Does this mean that you got it working? (sorry about the type btw).

Cheers, Rick

---

### Post by elpuerco on 2006-10-02
yeah, i got the window one to work....kool :) 

The textbox_window.py gives me this tho

Traceback (most recent call last):
  File "./textbox_window.py", line 29, in ?
    frm=Form()
  File "./textbox_window.py", line 15, in __init__
    self.window.connect("state_changed", self.statechange)
AttributeError: Form instance has no attribute 'statechange'

---

### Post by Arndt on 2006-10-05
> **elpuerco said:**
> I learned C/C++ back in the early '90s and stopped around '95 - '96.

I have a number of books which aided me at the time, some if not all were for Borland C++ running under Windows.

Would these still be relevant in relearning C/C++ in KDevelop, (once I get it working that is:confused: ).


If you mean "C and C++", rather than the imaginary language C/C++, one thing worth knowing about C is that there is a relatively new standard C99. As with earlier versions, not enough time has passed to make it universal, but you're likely to encounter code relying on the new features.

And which are they? These seem to be two good pages:
[http://www.kuro5hin.org/story/2001/2/23/194544/139](http://www.kuro5hin.org/story/2001/2/23/194544/139)
[http://gcc.gnu.org/c99status.html](http://gcc.gnu.org/c99status.html)

---

### Post by elpuerco on 2006-10-05
Well after much ado I think I have finally found my way thanks to help from various forums;) 

I am using Glade to create the GUI and gedit to create the python code to use the GUI.

I am currently working through the PyGTK documentation which to start with is showing me the way to create and manipulate the window with nothing more than gedit.

So at last I can concentrate on learning the language and hopefully start creating some app soon:D

---

### Post by moephan on 2006-10-07
Great! Soon you'll be able to check back in on this forum and help other people get started with python + gtk!

Cheers, Rick

---

### Post by slimdog360 on 2006-10-08
c# is still used a hell of a lot in embedded programming. That and assembly.

---

### Post by elpuerco on 2006-10-09
been out of it for too many years!  I heard way back in the mid '90s when I was using assembly that it was dying out due to changes in PC systems?

I used to look at the assembler demos from the Finish etc gurus showing their stuff, but wouldn't know where to find them now if they still exist?

I was under the impression it was all DirectX etc these days?

---

