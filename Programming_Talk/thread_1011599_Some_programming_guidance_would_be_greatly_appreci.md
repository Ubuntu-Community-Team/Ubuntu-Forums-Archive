---
title: "Some programming guidance would be greatly appreciated."
date: 2008-12-14
forum: Programming Talk
---

### Post by JEofVA on 2008-12-14
I've looked through a bunch of FAQs in a bunch of forums, but I haven't found an answer to my question yet.  I am hoping that someone here will be able to answer my question or at least point me in the right direction. 

I am looking for a GUI programming interface that I can use to build a standalone program that runs on a Linux laptop (currently running Ubuntu 8.04). From what I've read it seems that Python might be the correct choice of programming language. As I understand it is a fairly easy program to learn, but what I don't know is if it is practical to use it (or an application based on it) as a standalone programming environment.  What I mean is that the programs that I want to develop are just for my use, so there is no need for cross-platform concerns, or even too much user bullet-proofing, and they will most likely be running on the computer they were developed on. At a minimum the program I want to build would mainly be used to send and receive serial I/O through USB ports, processing and logging the data to a database like MySQL, and displaying the input to the screen in the form of text and graphical displays (updated at about one second intervals.) Ideally, it would be nice if the program could also capture and display video frames from a remote NTSC video source using the same program, however that would probably take too much processing power to be handled by a program that wasn't crafted from the bottom up for speed. So, I think just handling the data acquisition end of it will be sufficient. I can always use another computer and application for the video capture.

I do have some programming experience, but I'm far from a crack programmer.  Most recently I've been writing programs for the web in PHP/MySQL, however that is obviously not an appropriate language for these purposes. I've also written some simple personal applications in Basic and Pascal (Delphi 2) many years ago.   My computing background for the last 24 years has been based entirely on the various Microsoft platforms, starting from MS-DOS 2.11 right on through WinXP.  However, I'm not willing to go any farther with Microsoft and its money-grubbing minions so I am trying to defect to the Linux camp. 

As I see it, my main hurtles are going to be getting fully up to speed with the Linux OS, and conversant enough in OOP to handle whatever program I end up using to build my application. My problem is that I don't want to spend two or three months working on my project using an inappropriate development environment, only to realize that I have to start over with something else.  I'm hoping to find a Linux-based programmer with enough multi-platform programming experience to suggest the best route to follow, or at least which routes ***not*** to follow.

Thanks in advance,

Jonathan

---

### Post by mssever on 2008-12-14
I don't know whether Python can handle serial I/O through USB, but given that Python's libraries are extensive (one of the biggest advantages of Python), there's probably a module somewhere out there for Python.

While there are certainly good choices other than Python, I think Python is probably one of the better choices because

[LIST=1]
[*]It's easy to learn
[*]It has extensive library coverage, which means that you can get stuff done fast
[*]It's quite popular around here, which means that if you ask questions, they're more likely to be answered.
[/LIST]
Like I said, there are a number of other good choices, but it's hard to go wrong with Python.

---

### Post by JEofVA on 2008-12-14
> **mssever said:**
> I don't know whether Python can handle serial I/O through USB, but given that Python's libraries are extensive (one of the biggest advantages of Python), there's probably a module somewhere out there for Python.

While there are certainly good choices other than Python, I think Python is probably one of the better choices because

[LIST=1]
[*]It's easy to learn
[*]It has extensive library coverage, which means that you can get stuff done fast
[*]It's quite popular around here, which means that if you ask questions, they're more likely to be answered.
[/LIST]
Like I said, there are a number of other good choices, but it's hard to go wrong with Python.


Thanks for the fast input.  I guess one of the first things that I'll have to do is look into the Python libraries for serial I/O routines.

---

### Post by ankursethi on 2008-12-15
Found a library for serial communications : [http://pyserial.wiki.sourceforge.net/pySerial](http://pyserial.wiki.sourceforge.net/pySerial)

Here's how many people use Python -
1. Write the entire program in Python. Don't worry about performance. Remember : premature optimization is the root of all evil.
2. Use the program in a test environment with lots of sample data mimicking real world operations. Optimize the parts that are too slow.
3. Run the tests again. Find out which parts are *still* slow even after performing optimizations. Rewrite these parts in C instead of Python.

That is how high performance is achieved in dynamic languages. In fact, many parts of the Python standard library are *not* in Python, but in C. Moreover, there are many Python modules which have corresponding helper modules written in C. These helper modules do all the heavy lifting while the Python code only serves to control the helper modules. Don't worry about performance just now. Most of the time, you can get away with writing stuff in 100% Python without performance issues.

Yes, Python works very well with databases. In fact, working with databases is one of the most common uses of Python when dealing with web apps.

Python code can run unmodified on Windows, Linux and Mac OS X provided you try to make as much use of the standard library as possible (don't reinvent the wheel).

Best of luck :)

---

### Post by Sorivenul on 2008-12-15
I don't do a lot of I/O with Python, myself, but you may be interested in the "python-serial" module available in the repositories.

A link to their Wiki on SourceForge:
[http://pyserial.wiki.sourceforge.net/pySerial]("http://pyserial.wiki.sourceforge.net/pySerial")

EDIT: Beat to it.

---

### Post by pmasiar on 2008-12-15
Another +1 vote for Python.

Python is object-oriented, not object-obsessed :-) and will not force all your development into OOP straightjacket. Do parts which make sense in good old procedural style, use existing OO libraries, and add objects if you need them - or if you are lazy, squeak by by using just dictionaries instead of objects. 

And reference is just reference, so you can later change your dicts into real objects, and change only parts where you use the objects but not where you pass them around. That's the pleasure of having late binding - method presence is checked only at runtime. Python trusts you that you provide right type, and complains only when you don't, there are no nazi type compiler checks blowing your code and forcing you into contortions (AKA design patterns) to make **compiler** happy.

---

### Post by aapocketz on 2008-12-15
python is a good starting place for just about any project, its great for rapid prototyping, and for pulling together stuff that you never thought you could before.  I have used python as a hardware definition language (myHDL - like VHDL/Verilog) to reading excel files (xlrd?) and plugging values into a database.  

C/C++ is still where its at when you need something very custom or fast, but python can call C modules easily so its still a great starting point.  Python uses python libraries which must be installed somehow on the end user machine, so that is one drawback to a native compiled C program.

Beyond that how can I help?  I searched your posts for question marks and found none, so come back with specific questions, people will be happy to help you out.

---

### Post by JEofVA on 2008-12-15
Thanks for the input. I'm still too new to Python to benefit as much as I could from your reply, but I got the gist of it.  I'll be back soon enough after I get my feet wet with some tutorials and whatnot I'm sure.

---

### Post by JEofVA on 2008-12-15
> **aapocketz said:**
> python is a good starting place for just about any project, its great for rapid prototyping, and for pulling together stuff that you never thought you could before.  I have used python as a hardware definition language (myHDL - like VHDL/Verilog) to reading excel files (xlrd?) and plugging values into a database. 

It sounds like Python is exactly what I was looking for - rapid prototyping.

> **aapocketz said:**
> C/C++ is still where its at when you need something very custom or fast, but python can call C modules easily so its still a great starting point.  Python uses python libraries which must be installed somehow on the end user machine, so that is one drawback to a native compiled C program.

Beyond that how can I help?  I searched your posts for question marks and found none, so come back with specific questions, people will be happy to help you out.

I don't have any specific questions right now, I'll have to hit the books and get some Python under my fingernails before I'll  have anything specific to ask.  I guess one of my biggest concern was Python's ability to handle I/O through the USB port, but that seems to have been answered in the affirmative. My other question was whether or not there were any good IDE software packages that allowed one to flesh-out a program's GUI objects (buttons, textboxes, filehandling dialogs, etc.) so that a programmer would be free to concentrate on the logic. Something like Visual Basic, or what Delphi did for Pascal.  But, I'm getting ahead of myself.  First, I need to get the basics of Python down, then I can worry about the other.

Thanks for the input.... more, later. :)

---

### Post by mssever on 2008-12-15
> **JEofVA said:**
> My other question was whether or not there were any good IDE software packages that allowed one to flesh-out a program's GUI objects (buttons, textboxes, filehandling dialogs, etc.) so that a programmer would be free to concentrate on the logic. Something like Visual Basic, or what Delphi did for Pascal.  But, I'm getting ahead of myself.
For GUIs, check out Glade and the PyGTK module.

---

### Post by Rokurosv on 2008-12-15
I didn't know there was an serial library for python, this is awesome. I'm a Python newbie myself, haven't programmed that much with it and I don't know if I should pick it up cause Python 3 breaks backwards compatibility so I dunno if I should learn the previous versions or just jump right into 3, any suggestions?

---

### Post by mssever on 2008-12-15
> **Rokurosv said:**
> I didn't know there was an serial library for python, this is awesome. I'm a Python newbie myself, haven't programmed that much with it and I don't know if I should pick it up cause Python 3 breaks backwards compatibility so I dunno if I should learn the previous versions or just jump right into 3, any suggestions?
It will take a while for Python 3 to be widely adopted. Go ahead and use 2.6 (or even 2.5), and you won't have too much difficulty switching to 3.0 when the time comes.

---

### Post by Rokurosv on 2008-12-15
Good to know, found a Python book, a rarity here, and I thought about buying it but that was kinda holding me back.

---

