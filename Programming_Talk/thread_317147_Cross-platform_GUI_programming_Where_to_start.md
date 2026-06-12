---
title: "Cross-platform GUI programming: Where to start?"
date: 2006-12-11
forum: Programming Talk
---

### Post by mssever on 2006-12-11
I'm in the middle of my second-ever Python project. It's a re-implementation of a Javascript time calculator (I want a desktop version). It needs to run cross-platform, so I'm thinking that Python and wxPython are the best tools for the job. (Comments?)

The interface I envision is quite simple, but I'm at a loss as to designing the GUI. I've never done GUI programming before--and it's quite different from Javascript/HTML/CSS design--so I'm at a loss as to where to begin. Is there some sort of beginner howto that deals with wxPython and simple interfaces? I've found the API, but that's a lot of reading since I don't have a clue where to begin.

Also, are there any decent GUI designers out there? I've been fighting with wxGlade, but it doesn't want to do something as simple as add a menubar to a window. It insists on creating a new window for the menubar. And the Help > Contents menu does nothing, so I guess there isn't any documentation. (Who in their right mind would implement a menu item that does nothing?)

---

### Post by Tomosaur on 2006-12-12
I personally prefer pyGTK for python GUI stuff, but I find Java Swing a lot easier to use than even that. Designing GUIs is pretty complicated, so don't expect great results instantly. Most problems stem from layout and positioning of components in my experience, and then you have the numerous difficulties involved with resizing the windows etc. The best advice I can give you is this:

Write your program first. Make sure everything works perfectly well. Do NOT mix up your GUI stuff with your actual application, get your app done first before even bothering with the GUI. A calculator is easily done like this, whereas something like Photoshop is inherently tied to its GUI. Your calculator should be fully functional before the GUI is even attempted.

Avoid feature creep. This is very tempting when writing a GUI, since you'll most likely discover pre-made stuff which makes your life easier. Don't include things which aren't necessary. You can add all of the fancy stuff later on. 

Don't remake the wheel. If you need a text-box, just use the pre-built one. Yes, you can write one yourself using basic drawing components and action events etc, but that just complicates things. GUI writing is messy and annoying, so just try to make life as easy as possible. I don't know of any decent tutorials for any GUI stuff that much more advanced than a GUI Hello World. You're much better off just playing around.

---

### Post by mssever on 2006-12-12
Does pyGTK work cross-platform? It certainly seems to be documented better than wxPython, but the majority of my users will be on Windows, and I'd rather not depend on the Win version of GTK à la GIMP. At the same time, I have zero interest in writing a native Windows app. And if I could get Mac support without extra effort, it'd be great.

My core logic has already been written, and it works from the Python shell. It wouldn't be too difficult to wrap that up in code to implement a CLI program, but I don't think I'll gain anything by that approach--though I would like to eventually read from stdin (without a GUI) for scripting purposes. That'll have to wait for a later version, though, because I'll have to parse a wide range of input formats, or it isn't worth writing.

Am I correct in understanding that writing the GUI boils down to creating widgets and writing event handlers?

EDIT: Does Java Swing provide native look and feel? And is it enough superior to justify fighting with arcane Java restrictions (verbose syntax, no operator overloading IIRC)?

---

### Post by Tomosaur on 2006-12-12
I think pyGTK will work on Windows if you install the pyGTK and GTK from [here](http://www.mapr.ucl.ac.be/~gustin/win32_ports/) for windows. However, I think the windows version of gtk is slightly behind the linux version, so you may want to stick to regular features. Since you want to avoid this route, you may want to look for something else.

The Java Swing does not use a native look and feel by default, it has it's own LAF which some despise but I actually quite like. Swing DOES have a Windows look and feel, but it doesn't work on linux (as far as I know, this may have changed), so you'll need to have two very slightly different versions if you want to use native LAF. I would be tempted to say just forget about native LAF,  but if your heart's set on it, then by all means go nuts.

Yes, GUI stuff is generally just widgets and event handlers, unless you need to introduce completely new stuff, which is normally just eye candy and unnecessary for the most part.

I would say that the easiest way of getting this done is by using the windows GTK, since your back end is already complete. The only problem is getting your users to install it. I'm assuming your program isn't very large, so the bulk of the package will probably be python and GTK, which may be pretty annoying for the end-user.

I dunno. Considering you've already written the backend, maybe you should stick with wxWidgets/wxPython. I'm sure you'll be able to figure it all out, most GUI toolkits follow the same kind of pattern. Have you tried using pydoc via the command line with one of the wx classes?

---

### Post by kinson on 2006-12-12
> **Tomosaur said:**
> 
Write your program first. Make sure everything works perfectly well. Do NOT mix up your GUI stuff with your actual application, get your app done first before even bothering with the GUI. A calculator is easily done like this, whereas something like Photoshop is inherently tied to its GUI. Your calculator should be fully functional before the GUI is even attempted.


Hi, I'm a fairly new programmer (fresh grad *bleh). I was wondering is this the norm/good practise for programming? I myself can't stand programming interfaces cause it takes up a lot of time(and is extremely irritating :P ). Is it more complicated to just code the program to work first, then later build an interface on top of it(some people say using another programming language thats easier to code interface)?

Some people quoted me examples like Synaptic is basically a front-end for apt-get. But would you have to specifically code a program to provide those interfaces during coding phase? :|

Cheers,
Kinson.

---

### Post by mkppk on 2006-12-12
kinson, as a "fresh grad" you should know that answer well: YES, this is a good idea.. kinda falls under the whole encapsulation idea. Definately keep GUI and other stuff well seperated. May take longer (in this case) to actually do it that way, but when you get into bigger apps you'll be glad you did. Makes maintainance/debugging/enhancements much easier in the long run.

---

### Post by kinson on 2006-12-12
> **mkppk said:**
> kinson, as a "fresh grad" you should know that answer well: YES, this is a good idea..

Yeah...a bit embarrasing :-#  but owells, I'm learning :D

Thanks, I'll be looking into this in the near future, its a very interesting concept to me(even though it shouldn't be, hehe :p )

Btw, would anybody know of any guides regarding this? :)

Cheers,
Kinson

---

### Post by pmasiar on 2006-12-12
> **mssever said:**
> EDIT: is java enough superior to justify fighting with arcane Java restrictions (verbose syntax, no operator overloading IIRC)?

IMHO it is not worth to use inferior language. More fun is to learn advanced tools for better language. Even if it is not easy: other people do it, you will learn, and you can be valuable contributor of important skills to other projects for language you prefer.

[http://www.py2exe.org/](http://www.py2exe.org/) should be able to pack your py progam into one executable. I.e. [http://pysvn.tigris.org/](http://pysvn.tigris.org/) does it, IICR including windows installer.

Good luck!

---

### Post by Tomosaur on 2006-12-13
> **pmasiar said:**
> IMHO it is not worth to use inferior language.

That's if you accept the idea that Java is an inferior language :P
Strongly typed, verbose code is not necessarily a bad thing, and Java is (for the most part), inherently cross-platform, rather than Python, where stuff like GUI may or may not be cross-platform depending on which particular toolkit you use.

---

### Post by samjh on 2006-12-13
> **mssever said:**
> Does Java Swing provide native look and feel? And is it enough superior to justify fighting with arcane Java restrictions (verbose syntax, no operator overloading IIRC)?

Swing provides various native look and feel (aka. LAF). It uses its own LAF called Metal, by default.  For Windows it has Windows LAF, including a Windows XP LAF.  For MacOS it has its MacOS LAF.  For GTK it has its GTK LAF.  Take note that for Windows, MacOS, and GTK LAFs, you need to be running Swing it the LAF's native environment (ie. Windows LAF only runs on Windows, etc).  You can work around that restriction, but it is illegal.

Native LAF in Swing is very good, but not perfect.  The Java Swing team is making moves to use native widget calls for each of the native LAF platforms (like what IBM/Eclipse project did with SWT), so both the "look and feel" and performance will improve.  Indeed, reports are that Java 6 Swing already benefits from improved LAF as well as performance.

As for arcane "Java restrictions", the restrictive-ness is purely relative.  Java is more restrictive than C++, but it provides limited alternatives to some of the language features that have been cut (eg. interfaces instead of multiple inheritance, object references instead of pointers, etc).  Most of those language features are not necessary anyway, and have been cut because of the over-abundance of programming errors produced by incorrect coding when using them.  As for verbose syntax, Java can be written tersely if you want to, although not as tersely as a lot of other C-like languages (C/C++, Perl, etc).  There are many other languages with weird syntactic absurdness too, like indentations in Python, and more verbose languages like Pascal and Visual Basic.

I've learnt Pascal, C, and Java in-depth; have familiarity with assembly, C++, C#, VB and VB.NET; and dabbled with many others (Perl, Ruby, Haskell, Prolog, etc).  In my scope of experience, Java sits in the middle of the restrictiveness and verbosity scale.

---

### Post by pmasiar on 2006-12-13
msserver asked:
> is java enough superior to justify fighting with arcane Java restrictions 

> **Tomosaur said:**
> That's if you accept the idea that Java is an inferior language :P

Yes, I fully agree with your suggestion that java *is* inferior :-P 

> Strongly typed, verbose code is not necessarily a bad thing, 

**Strongly typed** is not a bad thing (it is just pain and waste of time to fight type police), but **verbose code is bad**. Productivity of programmers should be measures not in lines of code produced, but in **lines of code spent**. Every line needs be maintained.

OK, Tomosaur, just admit java is new COBOL++ and learn python :-P

---

### Post by Engnome on 2006-12-13
> **kinson said:**
> 
Btw, would anybody know of any guides regarding this? :)

Cheers,
Kinson

Read the book ["The Art of Unix Programming"]("http://www.faqs.org/docs/artu/") especially the chapter "Basics of the Unix Philosophy"  It's great and not specifically related to any language/platform.

---

### Post by Tomosaur on 2006-12-13
> **pmasiar said:**
> msserver asked:




Yes, I fully agree with your suggestion that java *is* inferior :-P 



**Strongly typed** is not a bad thing (it is just pain and waste of time to fight type police), but **verbose code is bad**. Productivity of programmers should be measures not in lines of code produced, but in **lines of code spent**. Every line needs be maintained.

OK, Tomosaur, just admit java is new COBOL++ and learn python :-P

Nevar! :P

Verbose code is not inherently bad, and Java code is not inherently verbose. You're confusing 'verbose' and 'bloated'. If the source code is not directly interpreted, as in the case of scripts, then verbosity is not necessarily a bad thing. Verbose code should be easier to read and understand, and, once compiled,  its verbosity is generally irrelevant anyway. Bloated code, on the other hand, is bad, and is easily lumped in and compared (innaccurately) to verbose code. And no, every line does not need to be maintained, if you are smart enough to isolate different methods the first time round. If your method is longer than a page (of screen size), then chances are it's doing too much stuff, and can probably be seperated into a load of different methods. This means your initial development time may be longer, but your time spent maintaining the code will be much shorter (unless you're making some massive changes), which is more of a general programming guideline rather than a viable criticism of Java :P

As for python: I already use it :D

---

### Post by kinson on 2006-12-13
> **Engnome said:**
> Read the book ["The Art of Unix Programming"]("http://www.faqs.org/docs/artu/") especially the chapter "Basics of the Unix Philosophy"  It's great and not specifically related to any language/platform.

Much thanks. Just bookmarked it :) I'll have a read when I had some time :)

Cheers,
Kinson

---

### Post by Grey on 2006-12-14
I'm sorry, but I wish to throw in a question of my own here.  I might be designing a game editor at some point for an upcoming game.  That editor must be able to display 3D graphics via OpenGL, in addition to the window toolbars and such.  Much like Blender.  I know that Blender actually draws all the buttons and things with OpenGL.  I would really prefer not to do that, and use a native cross-platform toolkit for that.

And the game will NOT be open source, so I would like something with a license permissive enough to include, or at least link to the libraries.  (BSD or LGPL are very preferred).  Is SDL the tool for this job?  (I've used SDL in the past, but I don't remember if it includes functions for drawing menus).

Anyways, I am basically shopping for a toolkit that allows embedded 3D viewports, and runs on any computer, with a very permissive license.  :)

---

