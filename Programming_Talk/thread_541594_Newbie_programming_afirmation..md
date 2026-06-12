---
title: "Newbie programming afirmation."
date: 2007-09-03
forum: Programming Talk
---

### Post by dickohead on 2007-09-03
Hey guys/girls,

I am trying to create a GUI based backup program that sends files via FTP. I was previously considering learning C#.NET as I'd read and heard a lot of good stuff about Mono, but after reading some more OSS related articles, postings and listening to podcasts (long live FLOSS). I am now thinking that Python may be my choice language, because my only previous programming experience has been PHP and VisualBasic (blame the institutions for that one!) and I'd like it to run on Linux and Windows.

So... Will python let me build a GUI and accept a file which it can then send over FTP to wherever (a Linux server most probably)?

I have a good understanding of networking and web development, but have never programmed a *real* desktop application before - so please... be gentle! Or... if you're going to be brutal, can you please be brutally helpful?

:D

---

### Post by cdsboy on 2007-09-03
By its self python i believe you cannot make a gui with python. However, you can use libraries in addition to python to get a gui. 
Here is a website that has a tutorial on the very subject:
[http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm]("http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm")

---

### Post by daveshields on 2007-09-03
This is an amibitious project indeed. Open up Synaptic and search for "backup." You are taking on the likes of backuppc, bacula, and so forth.

This is a daunting effort for an individual, though of course it could be a good learning experience.

But if you do decide to go ahead, Python is a good choice for an implementation language.

Also, you'll want to make use of "rsync."

---

### Post by dickohead on 2007-09-03
Thanks guys!

I know that I could write a bash script to accept input and then transfer the file using ftp, but that's not nice and easy for the user, especially on windows!

I have used rsync before and quite like it as a standalone tool, so I'll keep that in mind!

Do you think there would be better languages to use, circa C#?

---

### Post by sonofusion82 on 2007-09-03
python does come with GUI library called Tkinter, however it is not very powerful.

in addition to PyGTK, there are also other GUI toolkits like wxPython, PyQt.
both GTK and Qt has pretty good qualit GUI designer tools to help with GUI since you are familiar with VB.

---

### Post by dickohead on 2007-09-03
Do these GUI tools operate much in the same that Visual Studio tools do? Drag and drop objects and assign code to actions etc? Or should I just try it and see?

Do the GUI tools translate well to windows? Or will the interface look different to other windows apps? Aka the Gimp (pre version 2) and GTK libraries?

---

### Post by nanbudh on 2007-09-03
hey!
if you are just starting out on python and wanna use this as a learning experience could i join in? I have programmed VB and VB.NET and wanna learn python but i gave up because there is no IDE which matches ease of Visual studio.NET Another thing, there is free NetBeans IDE  from Sun which is quite good for java programming. Can you consider that for developing? Though I know python is common in ubuntu and linux area.

---

### Post by Tomosaur on 2007-09-03
> **dickohead said:**
> Do these GUI tools operate much in the same that Visual Studio tools do? Drag and drop objects and assign code to actions etc? Or should I just try it and see?

Do the GUI tools translate well to windows? Or will the interface look different to other windows apps? Aka the Gimp (pre version 2) and GTK libraries?

Read this:
[http://www.linuxjournal.com/article/7421](http://www.linuxjournal.com/article/7421)

Glade sounds like the tool you need - it should allow you to visually create the GUI, and is available on Windows too - provided the Windows machine has GTK for Windows installed (which is also freely available).

---

### Post by xtacocorex on 2007-09-03
> **sonofusion82 said:**
> python does come with GUI library called Tkinter, however it is not very powerful.
I beg to differ, powerful is relative.  If you use Tkinter, you end up with very portable Python code where you don't need to install new windowing libraries.  

Tkinter can be powerful if you use it smartly.  It may not be sexy or have a lot of built in features, but it works and works well.

---

### Post by pmasiar on 2007-09-03
> **sonofusion82 said:**
> python does come with GUI library called Tkinter, however it is not very powerful.

I disagree. Tkinter is powerful enough for what you want. It might be not as "pretty" as you like, because it is focused on being cross-platform.

wxPython is focused on look "native" on each platform.

EasyGUI looks pretty, and is **very** simple to use ... but is not very powerful. It might be enough for what you want tho.

But before you start writing complicated GUI, learn basics. Wiki in my sig has many training task for Python learner. PythonChallenge.com alone should keep you busy for couple months.

Python is good choice, is easy to learn but scales well to big problems.

IDEs are not as popular in Linux as they are in Windows: most programmers will just learn one good editor and use it for all languages. Bup Python does have couple IDEs: IDLE is decent basic IDE, SPE is better one (and more complicated), or try Eric.

---

### Post by dickohead on 2007-09-03
If IDE's aren't popular on Linux how do you create the interface? Are they all XML based?

Thanks for all the info guys, this is proving to be VERY helpful!

***

I had a lok at pythonchallenge.com and have absolutely no idea how to use it... There is a screen with 238 written in it... what the hell is that?

:D

---

### Post by Tomosaur on 2007-09-03
> **dickohead said:**
> If IDE's aren't popular on Linux how do you create the interface? Are they all XML based?
With a text editor.

All the visual tools do is create the code with minimal user input. All the user has to do is drag and drop stuff to get the look they want.

WYSIWYG editors (which is what such visual design tools are) can help you cut down the time you spend on the project, but can lead to superfluous code - which can introduce multiple points of failure, can cause your software to run slower, and are something many people consider to be more trouble than they're worth.

Some GUI toolkits use an XML file to specify what should go where, while others don't. Others still use a mixture of hard-coding everything and just using XML. GTK has some XML aspects - such as when designing menu systems, but XML is just one way of doing something. Ultimately, it's up to you to decide how you design your GUI. It's well worth learning how to do it without a WYSIWYG editor, because you will learn what's going on behind the scenes, and this will help you to improve and streamline your code.

An IDE is an 'Integrated Development Environment', not a GUI design tool - but an IDE can **contain** a GUI design tool as one of its features. An IDE helps you to organise your whole project, not just the interface. Some people wouldn't do without them, others hate them - it's just a matter of personal opinion. Some employers mandate the use of an IDE, others only specify a version control system (such as Subversion - which helps many developers work on the same code-base without over-writing each others work), while others still just let the developers decide for themselves.

As for Linux and IDEs - they are popular, but Linux is organised in such a way that it is essentially an IDE itself. If the user knows his/her way around the system and understands the tools available, then there's no real reason to use an IDE unless it has some feature the developer specifically needs. IDEs like Eclipse or KDevelop are very popular - they're just not really 'necessary'. On Windows, the use of an IDE is encouraged, although you can still develop everything without one - it's just that certain aspects of Windows development are a lot easier when using say, MS Visual Studio. That, and Notepad is the worst text editor on the planet.

---

### Post by pmasiar on 2007-09-03
> **dickohead said:**
> If IDE's aren't popular on Linux how do you create the interface? 

When I compared the code generated using Eclipse and code written without IDE, even without comparing Java vs Python, I noticed that IDE helps me to generate more code easier, so you end up with more code (in Java - more verbose language, but that is beyond the point). Classic editor does not  help you write more code, but helps you to edit and refactor the code you have - as a result, you have less code with better structure.

Of course you can refactor Java, and IntelliJ was excellent in that - nicer that Eclipse, if you ask me :-), but the trend is obvious: by not letting you easily generate blobs of lookalike code, classic editors nudges you to write better code. IMHO, YMMV.

> I had a lok at pythonchallenge.com and have absolutely no idea how to use it... There is a screen with 238 written in it... what the hell is that?

Well, it is not 238, but 2 powered to 38th. With suggestion to make result to URL. And you have forums, and forum has hints per level. And there is sticky for level 0. If I give you more info I would be solving it for you. 

It is just bunch of tasks to let you explore different features of Python. This one is easy to solve in shell, using Python as calculator :-)

---

### Post by dickohead on 2007-09-04
Tomosaur - thank you very much! That has cleared a lot of stuff up for me! 
Having built websites for quite a while I understand the difference between code generated by hand and code generated by WYSIWYG tools (aka Dreamweaver).

pmasiar - I will have a look at pythonchallenge.com again when I have gotten myself started with Gedit (the editor I use for CSS, XHTML and PHP). 
I'm guessing the result of 2 to the 38th is the url for the next problem - I can now see why this will be fun :D?

You guys have helped me immensely with getting started! I installed SPE and wxGlade and had a look at the basic code generated for certain elements, so I now understand how different files are generated for different purposes, much like CSS and PHP, one does the smarts, the other makes it look good!

If there were a good-vibe rating system on these forums, you'd all be getting some serious good-karma right now!!!

:D many thanks again, and I look forward to learning python!!

---

