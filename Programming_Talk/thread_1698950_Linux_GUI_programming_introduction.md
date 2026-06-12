---
title: "Linux GUI programming introduction"
date: 2011-03-03
forum: Programming Talk
---

### Post by Learning Linux 2011 on 2011-03-03
Hi,

I am new to Linux.

What do people here really use to program Linux GUI applications?  

Is there an IDE that people commonly use?  Hypothetically if I just wanted a "Hello" program in C that opens a plain window, what would you use for that?  There's probably more than one, but is there one that is more popular and/or more widely used?

I have programmed before, but I'm just not familiar with Linux GUI programming.

Can someone just give me a very quick rundown?

Thanks in advance

---

### Post by foxmuldr on 2011-03-03
> **Learning Linux 2011 said:**
> Hi,

I am new to Linux.

What do people here really use to program Linux GUI applications?  

Is there an IDE that people commonly use?  Hypothetically if I just wanted a "Hello" program in C that opens a plain window, what would you use for that?  There's probably more than one, but is there one that is more popular and/or more widely used?

I have programmed before, but I'm just not familiar with Linux GUI programming.

Can someone just give me a very quick rundown?

Thanks in advance

I use Codelite, which supports C and C++ in a Qt GUI environment.

- Rick C. Hodgin

---

### Post by norseman-has-a-laptop on 2011-03-10
i mainly use python and c

---

### Post by Simian Man on 2011-03-10
Nothing is even close to "standard" with Linux programming.  Not the language, not the toolkit, not the IDE, nothing.  C#, GTK#, Monodevelop is a good choice if you ask me.  But the next 10 responses to this thread will likely have 10 different suggestions :).

---

### Post by Hippytaff on 2011-03-10
[Quickly]("http://http://en.wikipedia.org/wiki/Quickly_%28software%29") - because I'm learning

---

### Post by kuifje09 on 2011-03-10
option 4,  I use GAMBAS.  a kind like basic.
Nice environment, but not very version consistent.
So for serious work, I would not recoment it. At least not now.

I do realy miss a dev-env.  like Visual C or Borland C

---

### Post by Hippytaff on 2011-03-10
deleted

---

### Post by cgroza on 2011-03-10
If you are in python or C++, wxPython,  wxWidgets(C++) is a nice toolkit to work with. Or you can use GTK which is the native for GNOME.

---

### Post by LemursDontExist on 2011-03-10
For gui development python seems like the obvious choice.  Unless performance is critical, it will allow for very rapid development and clean readable code.  I could see an argument for Ruby or C#, but personally, I find Python preferable.  Ruby is not quite as well supported by third party modules, and using C# seems like a strange choice for linux development since it was developed by Microsoft for windows programming.

As far as IDE goes, I favor lightweight, and often just use gedit, but that's just a stylistic preference.  For larger projects I tend to use Geany which is a little more feature rich, but is still more properly an editor than an IDE.  I feel that in an interpreted langauge, the need for an IDE is much less than in a compiled language.  Any IDE involves a learning curve, and for python I think it's just not worth the trouble.

You have a few options for your gui toolkit - I like gtk because it integrates most naturally with the vanilla Ubuntu install, is reasonably easy to learn, but still quite flexible, and is cross platform in case you want to port whatever you write.  Qt and Wxpython are also pretty reasonable choices though. 

If you just want a gui 'Hello World,' I recommend Bash scripting and Zenity.  You can have a working script in 3 minutes.  10 if you've never done bash scripting before.

---

### Post by charileb000 on 2011-03-21
anybody tried [http://www.kdevelop.org/](http://www.kdevelop.org/)
though its probably for KDE...

---

### Post by might and power on 2011-03-21
gui programming is a lot less smooth than it is on windows. the best framework is nokia Qt libraries which is cross platform. If you dont mind programming in c++ its definitely the best option. 


other than that there is wx widgets and gtk. they are ok. but basically you wont get anything close to the productivity you get with visual studio on windows. Linux is not as advanced as windows in what you see is what you get designers and such.

---

### Post by JupiterV2 on 2011-03-21
GTK+ is native to C with bindings for Python, C++, etc. Qt is native to C++ with bindings for other languages. wxWidgets is also native to C++ with bindings for other languages.

I prefer the native gnome look, so I tend to choose GTK+.

Python is a good choice if you want rapid development. I personally use C but for no other reason than I like to make my life difficult.

---

### Post by stchman on 2011-03-21
Nobody giving Java any love?

You can develop GUIs in Java that will run on Windows and OS X.  Once you're done, you have a nice neat .jar file.

I use Netbeans as it includes the GUI development stuff.

---

### Post by rg4w on 2011-03-21
[LiveCode]("http://www.runrev.com/")

---

### Post by camelinahat on 2011-03-22
Personally I've been using Vala (which is for GTK+/Gnome libraries and uses GLib as a foundation). I liked it because it compiles to C source-code and executables. Running natively giving a bit of a performance boost over intepreted languages like Python/Perl or over managed languages like C#/Java. However it has a higher level syntax very similar to C#.

<edit>
Additionally you can use Glade for a GUI builder, or Mono-develop with a vala plugin for a full IDE
</edit>

---

### Post by bouncingwilf on 2011-03-22
I use Codeblocks with GTK+ & C ( occasionally gtkmm & C++) but would have found it easier to set up this system with a little more documentation.

Knowing which compiler & linker flags to add to Codeblocks defaults is far from intuitive ( or maybe I'm just too old and past it)

Bouncingwilf

---

### Post by BuffaloX on 2011-03-22
Nothing comes even close to Lazarus for easy fast efficient nice GUI programming on Linux.

[http://www.lazarus.freepascal.org/]("http://www.lazarus.freepascal.org/")

It's based on Delphi Pascal, and supports OOP, it's powerful flexible easy to read IMO, and very very fast.

The Ubuntu and Debian installers are quick and easy, but they make the examples hard to find, and adding new components a chore, you should only use repository or .deb versions to get a quick taste of what Lazarus is, then make a proper install if you decide to really use it.

---

### Post by deathadder on 2011-03-22
I tend to do my GUI stuff in GTK using either C++ or Python. 

At the moment I'm using Java though because of need a cross platform GUI.

---

### Post by LemursDontExist on 2011-03-22
> **deathadder said:**
> I tend to do my GUI stuff in GTK using either C++ or Python. 

At the moment I'm using Java though because of need a cross platform GUI.

Have you tried the python/gtk cross platform?  I've had no trouble running applications I wrote in Linux under windows that way. You do need to install python and gtk, but using py2exe you can construct an executable that bundles everything you need for distribution.

---

### Post by deathadder on 2011-03-23
> **LemursDontExist said:**
> Have you tried the python/gtk cross platform?  I've had no trouble running applications I wrote in Linux under windows that way. You do need to install python and gtk, but using py2exe you can construct an executable that bundles everything you need for distribution.
I've wanted to, I've just always had other constraints that meant it was Java I had to use. When I get some more time for my own coding I'll be using Python / GTK a lot more. :D

---

### Post by jesuisbenjamin on 2011-05-21
Have you tried Gtk+3 and Python using PyGObject? I've found so little documentation and the little I found didn't work -- it drives me insane.

---

### Post by simeon87 on 2011-05-21
> **jesuisbenjamin said:**
> Have you tried Gtk+3 and Python using PyGObject? I've found so little documentation and the little I found didn't work -- it drives me insane.

Is there any reason why you want GTK+3? It's new but there's a lot more documentation for GTK+2, see [here](http://www.pygtk.org/docs/pygtk/) for example. Python + GTK+2 works pretty well for me.

---

### Post by jesuisbenjamin on 2011-05-21
> **simeon87 said:**
> Is there any reason why you want GTK+3? It's new but there's a lot more documentation for GTK+2, see [here](http://www.pygtk.org/docs/pygtk/) for example. Python + GTK+2 works pretty well for me.

Well PyGtk is going to "die out along with GTK+2" from what i read. I'm new to Gui and don't want to learn something that's going to be obsolete by the time i master it.
Besides GTK+3 supposedly has better theming/skinning options which is what i am looking for.
But please let me know if i'm wrong :)

---

### Post by simeon87 on 2011-05-21
> **jesuisbenjamin said:**
> Well PyGtk is going to "die out along with GTK+2" from what i read. I'm new to Gui and don't want to learn something that's going to be obsolete by the time i master it.
Besides GTK+3 supposedly has better theming/skinning options which is what i am looking for.
But please let me know if i'm wrong :)

Hmm, you're right that PyGObject is the future according to the [latest PyGTK news](http://www.pygtk.org/). There is a directory with examples and demos (see [PyGObject](http://live.gnome.org/PyGObject) page). In that case I have some reading to do to port from PyGTK to PyGObject.

---

### Post by jesuisbenjamin on 2011-05-21
> **simeon87 said:**
> Hmm, you're right that PyGObject is the future according to the [latest PyGTK news](http://www.pygtk.org/). There is a directory with examples and demos (see [PyGObject](http://live.gnome.org/PyGObject) page). In that case I have some reading to do to port from PyGTK to PyGObject.

Yes. I'm not sure whether i have the gi.repository installed properly or not. But i couldn't run simple examples [like this one]("http://www.micahcarrick.com/gtk3-python-hello-world.html"). Also i couldn't find the demos on my computer (shouldn't they be installed with PyGObject?)

EDIT: couldn't git clone demo so i used wget:
```
wget -r -np -nH &#8211;cut-dirs=4 http://git.gnome.org/browse/pygobject/plain/demos/gtk-demo/

```
Not all demos work in my case.

EDIT 2: out of frustration and persistence I just started a [blog with notes on Gtk+3 and Python]("http://gtk3lab.blogspot.com/") (PyGI) which I intend to append as I find out more on badly documented PyGI. I'm a complete novice, so that blog will be written from that perspective, unless any of the senior programmers are willing to help adding tips, tutorial and documentation for PyGI. That would be really cool thanks.

---

### Post by AgentZ86 on 2011-05-22
Hi
I'm new to computer science and just finished learning some basics in python and now moving to gui tookkits subjects.

I'm currently using python2.6 and wanted to know which may be best for learning.

It's just a hobby and I'm not concerned about relearning another gui but I was considering WxPython ? 
Looks like I have WxPython by default in Maverick ? 
Is there any real problem with this?

I need advise on where I should start. I don't mind relearning another later I just want a place to start that will be simple and the video lessons I found online are using WxPython

Can I use WxPython on linux ? 
There is all these on the list hard to choose?

[http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming)

I'm so new I just need some more input to decide where to start

Thanks everyone

---

### Post by jesuisbenjamin on 2011-05-22
> **AgentZ86 said:**
> Hi
I'm new to computer science and just finished learning some basics in python and now moving to gui tookkits subjects.

I'm currently using python2.6 and wanted to know which may be best for learning.

It's just a hobby and I'm not concerned about relearning another gui but I was considering WxPython ? 

Is there any real problem with this?

I need advise on where I should start. I don't mind relearning another later I just want a place to start that will be simple and the video lessons I found online are using WxPython

Can I use WxPython on linux ? 

There is all these on the list hard to choose?

[http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming)

Thanks everyone

If you want a taste of Wx with Python try out [http://zetcode.com/wxpython/](http://zetcode.com/wxpython/)
it's a good start. You'll find other GUI tutorials there too, you may need to ask yourself what you want to achieve in order to help your decision. Good luck. :)

---

### Post by %hMa@?b&lt;C on 2011-05-24
QTcreator is great.  It reminds me much of the Visual Studio for creating the forms, and then it is easy to write callback functions.  I've used it only with C++, but there are other languages that you can use with it I think.

---

### Post by AgentZ86 on 2011-05-25
Thanks all for the response

I guess I need to redefine my question.
I want to learn and become fluent in python is a given.
Yet after some study, I feel I'm missing something.
I get the python tutorials, and I also jumped into wxpython
But I guess my question is where does it end ?

Am I ready to jump in and start programming? Do I know enough about python and syntax ? Is it time to learn and pick from the libraries out there to start creating a program ? 

I guess my question is at what point are you ready to make decisions about what you need to know ? What is the typical direction or is there a spike in direction depending on what a person wants to accomplish in their program ?

IE:
I read how to think like a computer scientist
Then I watch a bunch of Youtube vids, and other vids about python, and tutorials on the python site; and also now wxpython, pygame, pysears etc. and more

I mean once you get the python and basics syntax topics down, is it just now time to find the tools you need and start building something ?
Or is there something more I should know before I dive in ?
I want to make sure I have what I need before getting off track.

So the question is sort of difficult without knowing what I should or shouldn't know for starters.

I hope this makes sense.

Thanks all

---

### Post by teachop on 2011-05-25
> **jeffc313 said:**
> QTcreator is great.
I second this...  Qt Creator is very plesant to work in, and the resulting Qt applications look very natural wherever they execute, including Ubuntu .  Good stuff, it is my go to IDE for Linux or Windows GUI utilities.  I hope the Nokia thrashing doesn't hurt Qt...

---

### Post by Blackbug on 2011-05-26
I just want to add one query to this post..
How should I decide on choosing language for GUI developement.
 
I am c++ programmer but do know python. Should I choose python or c++ for my applications GUI interface? on which basis should i decide this?
 
and also, if i choose python ( i guess since its more easy to implement than c++ ), how should i connect my core c++ (algorithms and logic) part with python gui interface?

---

### Post by simeon87 on 2011-05-26
> **Blackbug said:**
> I just want to add one query to this post..
How should I decide on choosing language for GUI developement.
 
I am c++ programmer but do know python. Should I choose python or c++ for my applications GUI interface? on which basis should i decide this?
 
and also, if i choose python ( i guess since its more easy to implement than c++ ), how should i connect my core c++ (algorithms and logic) part with python gui interface?

If you have your code algorithms in C++ then you could also opt to write the GUI in C++. You can call C or C++ from Python by writing extensions so it's indeed possible to access the core logic in C++ from Python.

For many applications, writing the GUI in Python is quick and easy which would take many lines in C or C++. It just depends on the type of application. For a 3D video game it may not be worth it (you might as well do everything in C++ there) but for a desktop applications that just computes and shows values then a GUI in Python is very well possible.

---

### Post by Blackbug on 2011-05-26
your advise seems to be correct.
for desktop applications gui with python and logic part in c++ seems to be nice option
 
thanks

---

