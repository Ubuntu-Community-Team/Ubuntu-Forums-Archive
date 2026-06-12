---
title: "What are these languages good for?"
date: 2005-09-30
forum: Programming Talk
---

### Post by Unit #134679 on 2005-09-30
I am taking a Java class in school (infact, I'm in that class right now) and I have been learning Python since three days ago. For a while, I've wondered exactly what the hell can I do with Java and Python...especially Python. Besides programming and creating an app, I have no idea what apps I could even program with those. After I learn these languages, I have no idea what apps I could even think of creating. This is a pretty lame question, but I was just thinking about it and wanted some others opinion

---

### Post by thumper on 2005-09-30
If you like I'll give some examples of projects that I have worked on using Java and/or Python.
Java:
[LIST]
[*]Java servlet code for web applications.  Handles all of the business logic.
[*]Java applets for web sites (not so popular these days).
[*]GUI applications using Swing, used for monitoring large systems
[*]Server side java objects for handling specific business functionality, interaction with client apps using CORBA, tibco rendezvous, SOAP or XML RPC.
[/LIST]
Python:
[LIST]
[*]Many simple scripts to automate work processes, or testing
[*]Write classes to simplify testing and using of other server components.  Great to interactively test using the python interpreter.  Used fnorb for CORBA, python sybase module, python-ldap from sourceforge, tpg (toy parser generator) for writing a parser.
[*]Conversion scripts to go from one database schema to another database schema on a different server with a different database implementation (Access to PostgreSQL)
[*]Generate reports for clients through SQL to generate flat files.
[*]Script for determining dependancies between libraries and binaries.  Uses gnu binutils executables nm, readelf, c++filt.
[/LIST]
I'm sure there are many others but these are what I can think of off the top of my head...

---

### Post by Unit #134679 on 2005-09-30
[QUOTE=thumper]If you like I'll give some examples of projects that I have worked on using Java and/or Python.
Java:
[LIST]
[*]Java servlet code for web applications.  Handles all of the business logic.
[*]Java applets for web sites (not so popular these days).
[*]GUI applications using Swing, used for monitoring large systems
[*]Server side java objects for handling specific business functionality, interaction with client apps using CORBA, tibco rendezvous, SOAP or XML RPC.
[/LIST]
Python:
[LIST]
[*]Many simple scripts to automate work processes, or testing
[*]Write classes to simplify testing and using of other server components.  Great to interactively test using the python interpreter.  Used fnorb for CORBA, python sybase module, python-ldap from sourceforge, tpg (toy parser generator) for writing a parser.
[*]Conversion scripts to go from one database schema to another database schema on a different server with a different database implementation (Access to PostgreSQL)
[*]Generate reports for clients through SQL to generate flat files.
[*]Script for determining dependancies between libraries and binaries.  Uses gnu binutils executables nm, readelf, c++filt.
[/LIST]
I'm sure there are many others but these are what I can think of off the top of my head...[/QUOTE]

Ah alright. Cause I was just thinking about what exactly I could write, cause I honestly have no idea what I could do. Now thinking about it, I'm wondering if programming is really what I want to do...cause I have no idea what any (majority actually) of the stuff you said could be used for really is. I still dont know what I could really write anyways. Man, this sucks :cry:

---

### Post by Lux Perpetua on 2005-09-30
> Man, this sucksDon't worry, it probably doesn't suck as much as you think. If I'm not mistaken, a lot of Ubuntu development is done in Python (for example!). I just ran 'top' and python is listed, so something on my system is using python right now (not sure what, though). 

I don't think you should be worried just because you don't have any ideas for projects right now. If on the other hand you don't enjoy writing code, then maybe you should start looking elsewhere ;)

---

### Post by DancingSun on 2005-09-30
Well, those are just some examples of business programming.  Software programming really is a very broad field.  Both Java and Python are general programming languages and thus can be used to program just about anything, and are only really limited by the resources available (hardware, human, time).

Some programming fields are pretty boring, and some are very exciting.  What are your hobbies?  What are you interested in?  Now, many of us don't get the opportunity to work in fields that we are interested in, but following your interest is always a good way to start.  Whether you end up in a place where you can be happily programming whatever you want or not, is another topic.

---

### Post by cactus on 2005-09-30
I am a Ruby man myself, after having used the following: Java, python, C, perl, php, and a bit of C# (mono)--to varying degrees of project size.

---

### Post by DancingSun on 2005-09-30
[QUOTE=cacti]I am a Ruby man myself, after having used the following: Java, python, C, perl, php, and a bit of C# (mono)--to varying degrees of project size.[/QUOTE]
Glad to see another Ruby user here!  I'm learning Ruby myself, and it's been enjoyable so far.  Seriously, a well designed language goes a long way in making programming easier for the programmer.  When I took C classes back at school, I thought to myself "I'd never want to be a software programmer!"  Well, but here I am, doing business programming...but Ruby really makes the job easier.

---

### Post by SilentCacophony on 2005-09-30
Well, I personally never liked java for anything. My girlfriend is always playing java games online, though, (and usually complaining because of bugs... ;) ) so there is one obvious application for it.

Python and ruby are the stuff I can dig into. I've not gotten into ruby yet, but have been learning/using python for a few months now. The first and most obvious application I think of for these is simply: what do you wish that your computer could do that it's lacking? Python is a great way to glue together applications, make utility programs, make front-ends for esoteric commands, etc... I'm sure ruby is too. And they can do much more.

I came from using an Amiga computer ('89-2000) where I used to use a language called Arexx (a much improved version of rexx) and C for such functionality. I commanded my computer totally. Then I 'moved on' to Windows, and I didn't even know where to start. I never did any programming on that, as I found the lack of openness, and the cost of the tools and info prohibitive. Another wonderful thing about gnu/linux is the wealth of ready-available info and source code that you can learn from.

---

### Post by Keffin on 2005-10-01
Off the top of my head.

Programs written in Java:
Azureus (Bittorrent client)
Limewire (Gnutella client)
Large parts of OpenOffice
Eclipse (Java IDE)
Derby (relational database)
Many websites

Java has libraries to help you do just about anything at all. It also has all its own GUI stuff so you can make GUI apps that "just work" on any platform that runs Java.

Programs written in Python:
Quod Libet (Music player)
Bittorrent (guess!)
Portage (gentoos apt)
Many websites (one of the possible P's in "LAMP")
Billions of scripts that are a bit too complicated for a few lines of bash
I'm probably not doing it justice here, I don't know a huge amount about python. Ubuntu uses it for several apps I think. Update notifier?

Python also has bindings for just about any Gnome/KDE library, allowing you to write apps for either platform easily. It probably has a wxWidgets library too, which can use the native GUI stuff of either Gnome or windows.

So basically you can program pretty much anything with either. Though perhaps python lends itself better to smaller projects and Java to bigger projects. Another thing to note is that Java programs should run faster than python ones, as they are JIT compiled rather than pure interpreted. But then as python has bindings to many C libraries for the processor-intensive stuff (e.g. gstreamer for multimedia - as Quod Libet uses), this may not matter.

---

### Post by Leif on 2005-10-01
you want inspiration ? hit sourceforge or freshmeat. tons of projects, and maybe you can even find one you like enough that you join the team !

---

### Post by dcraven on 2005-10-01
Absolutely don't give up! But it can be challenging at times. There are many programs written in Python from simple to complex. I've been using it to write some of my latest projects like [this](http://newton.sf.net) and [this](http://echelon-applet.sf.net). If you are a GNOME user (probably also true with other desktops, but I can't say for sure), writing little applets and things are a breeze in Python. 
Certainly start small, choose a GUI toolkit based on the desktop you use if you want to do a GUI. Joining relevant mailing lists or asking questions in a place like this is encouraged. Be prepared for frustration because that widget that you want to use in your project is as of yet undocumented. Stick with it and you'll be amazed in a few months what you can create on a whim without the need for reference. It's great fun, and cool to see other people use and enjoy your work.
Cheers,
~djc

---

### Post by Unit #134679 on 2005-10-01
Thanks for the post guys. I enjoy writting code...I just dont enjoy having the need to fix errors, but I'm sure everyone is like that, haha. Is there a GUI toolkit based on the desktop for Python? I have one for Java, but I'm having a hard time with it in a way.

---

### Post by dcraven on 2005-10-01
[QUOTE=Unit #134679]Is there a GUI toolkit based on the desktop for Python?[/QUOTE]
There are tons of them. There is [pygtk](www.pygtk.org), [pyqt](http://www.riverbankcomputing.co.uk/pyqt/index.php) and [wxpython](http://www.wxpython.org/). My personal favourite is pygtk, but your preferences may vary. There are others too, of course.
HTH,
~djc

---

### Post by thumper on 2005-10-01
[QUOTE=Unit #134679]Thanks for the post guys. I enjoy writting code...I just dont enjoy having the need to fix errors[/QUOTE]
Unforunately unless you are a god you'll spend more time doing the later than the former.:???:

---

### Post by Unit #134679 on 2005-10-01
[QUOTE=thumper]Unforunately unless you are a god you'll spend more time doing the later than the former.:???:[/QUOTE]

Yea, I figured that. Thats why I just suck it up and take it like a man

---

### Post by Unit #134679 on 2005-10-02
[QUOTE=dcraven]There are tons of them. There is [pygtk](www.pygtk.org), [pyqt](http://www.riverbankcomputing.co.uk/pyqt/index.php) and [wxpython](http://www.wxpython.org/). My personal favourite is pygtk, but your preferences may vary. There are others too, of course.
HTH,
~djc[/QUOTE]

I'm trying wxPython and pyGTK right now. I'm liking how pyGTK comes with Glade, which is really nice...but I'm trying to figure out what to do after creating the GUI for the app. wxPython looks pretty nice too, but I'll mess with it tomorrow. I'm tryin to figure out how to open pyGTK too. Other than that, takes for the help

---

### Post by dcraven on 2005-10-02
[QUOTE=Unit #134679]I'm trying wxPython and pyGTK right now. I'm liking how pyGTK comes with Glade, which is really nice...but I'm trying to figure out what to do after creating the GUI for the app. wxPython looks pretty nice too, but I'll mess with it tomorrow. I'm tryin to figure out how to open pyGTK too. Other than that, takes for the help[/QUOTE]
Check the examples in the pygtk source distrobution tarball. If you check gnome-python out of GNOME CVS, you will get examples from pygtk, gnome-python, and gnome-python-extras. Feel free to ask me or anyone else here if you have any questions. I can be reached at [email]dcraven@myjabber.net[/email] on the Jabber network if you like. Pygtk is a very nice toolkit, and I don't mind helping others who want to take advantage of it.
Cheers,
~djc

---

### Post by Unit #134679 on 2005-10-02
I cant even get pyGTK to open I mean. I have no idea where it would be. I dont use Jabber, do you have Gmail?

---

### Post by dcraven on 2005-10-02
[QUOTE=Unit #134679]I cant even get pyGTK to open I mean. I have no idea where it would be. I dont use Jabber, do you have Gmail?[/QUOTE]
Sure. It's [email]myusernamehere@gmail.com[/email]. I'm not sure what you mean by "open". Pygtk is not a program, it's a GUI toolkit. If you mean "import", then maybe it's installed in the wrong spot, however I doubt that's the issue since I assume you used apt to install it (I hope you did anyways:)). I would suggest you start by going through the tutorial found [here](http://www.pygtk.org/pygtk2tutorial/index.html).

Cheers,
~djc

---

### Post by Unit #134679 on 2005-10-02
Ok, well, I'm using Windoze right now, sorry about that. I *did* install it, but I have no idea how to use it. I'll kick start Linux right now

EDIT: Alright its up. I gotta install it now. I added your Gmail and Jabber account to my buddylist

---

### Post by Unit #134679 on 2005-10-02
I cant get pyGTK to install

---

### Post by DancingSun on 2005-10-02
[QUOTE=Unit #134679]I cant get pyGTK to install[/QUOTE]
From Synaptic?  What's the error message?

---

### Post by Unit #134679 on 2005-10-02
[QUOTE=DancingSun]From Synaptic?  What's the error message?[/QUOTE]

I didnt find pyGTK in Synaptic. I downloaded the binary and deb file for it and tried both. I get some error with the binary about it not finding python headers. For the deb file, it says that the dependencies couldnt be met

---

### Post by DancingSun on 2005-10-02
[QUOTE=Unit #134679]I didnt find pyGTK in Synaptic. I downloaded the binary and deb file for it and tried both. I get some error with the binary about it not finding python headers. For the deb file, it says that the dependencies couldnt be met[/QUOTE]
OK, while I don't use Python, in Synaptic a package called python-gtk2 is already installed on my Ubuntu.  So if it's the same thing as pyGTK, then it should already be installed.  python-glade2 is also installed on my system, so that should be ready to use as well.

---

### Post by dcraven on 2005-10-02
Ahh yes. The lovely Debian naming scheme.. Like DancingSun said, the package is called python-gtk2. You might also want to install python-gnome2-dev and python-gnome2-extras-dev as well if you want to use GNOME specific stuff. Otherwise you won't need it.

Cheers,
~djc

---

### Post by Unit #134679 on 2005-10-03
Isnt pyGTK a GUI based editor? Or is it for created GUI and non-GUI based applications? I noticed it was installed already, but now I'm wondering how to work it in Linux and Windows (its installed on both). I created the GUI for an application in Glade but I dunno how to write the source for it.

---

### Post by DancingSun on 2005-10-03
[QUOTE=Unit #134679]Isnt pyGTK a GUI based editor? Or is it for created GUI and non-GUI based applications? I noticed it was installed already, but now I'm wondering how to work it in Linux and Windows (its installed on both). I created the GUI for an application in Glade but I dunno how to write the source for it.[/QUOTE]
GTK is a GUI toolkit. It's not a visual GUI editor, rather, it's a library that lets you contruct a GUI via code, like Swing for Java.  Glade is the visual GUI editor for GTK.  pyGTK is the Python bindings for accessing GTK functions in Python.  You'll need to read the Glade and pyGTK tutorials to learn how it works.

---

### Post by Unit #134679 on 2005-10-03
[QUOTE=DancingSun]GTK is a GUI toolkit. It's not a visual GUI editor, rather, it's a library that lets you contruct a GUI via code, like Swing for Java.  Glade is the visual GUI editor for GTK.  pyGTK is the Python bindings for accessing GTK functions in Python.  You'll need to read the Glade and pyGTK tutorials to learn how it works.[/QUOTE]

I was told that a lot of the pyGTK tutorials are outdated or bad. Have any good ones?

---

### Post by dcraven on 2005-10-04
[QUOTE=Unit #134679]I was told that a lot of the pyGTK tutorials are outdated or bad. Have any good ones?[/QUOTE]
No, I told you that many of the pygtk/glade tutorials are outdated. As in, tutorials teaching you how to use pygtk with glade. The official pygtk tutorial is very well done, current, and complete. I strongly suggest you start there. Just follow the tutorial along. 

The fact is you really don't NEED glade at all. So the pygtk tutorial is really all you need. Figure out the basics of pygtk first, then worry about glade. That's my suggestion.

~djc

---

### Post by Unit #134679 on 2005-10-04
Sorry about that. :P Sheesh. I'll look at the pyGTK tutorial then

---

### Post by Drakx on 2005-10-04
you should have it installed try this

```

#! /usr/bin/env python

# Exaple pygtk app

import pygtk
pygtk.require('2.0')
import gtk

class Base:

	def __init__(self):
	    self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
	    self.window.show()
	def main(self):
	    gtk.main()

print __name__
if __name__ == "__main__":
    base = Base()
    base.main()

```

then run some thing like this

python /path/to/base.py

post what you get when you have ran it

---

