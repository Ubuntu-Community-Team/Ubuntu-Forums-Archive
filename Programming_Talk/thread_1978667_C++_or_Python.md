---
title: "C++ or Python?"
date: 2012-05-12
forum: Programming Talk
---

### Post by MiXor on 2012-05-12
Hello everyone!

I'm looking for insights about what language to use to create an application that would take signal from the microphone, analyse its spectrum, generate sounds, etc... I'm ok in C, know little about C++, and nothing about Python!
Thanks for your help!
:KS

Aline

---

### Post by lisati on 2012-05-12
*Thread moved to **[Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")**.*

---

### Post by markbl on 2012-05-12
I have been programming in C/C++ extensively for 25+ years. My recommendation is python .. (!)

I now use python everywhere I possibly can, and then C++/C only where I absolutely have to.

---

### Post by MiXor on 2012-05-12
I'm willing to be bitten by the snake, if I'm given a good reason to... :D
What did you like about Python/loathe about C++?
Oh, by the way, apologies about posting on the wrong forum... Thanks to the moderators for keeping things tidy!
:KS

Aline

---

### Post by markbl on 2012-05-12
I don't loathe C/C++. It is just that Python is a step forward in the technology of programming languages. You are programming at a higher abstraction level, so it is just much easier, quicker, and far less can bite you. There is also enormous standard and 3rd party library support, with the same api across all platforms.

I produce better quality, portable, more capable code, quicker. And I enjoy it more.

---

### Post by MiXor on 2012-05-12
What sort of programs do you write?  (I hope I'm not being nosy there :P)

---

### Post by markbl on 2012-05-12
All sorts of stuff. I do a lot of legacy code for old large systems. Most of that is in C/C++ as that is what the original system was built in. I do a lot of shell programming there also, but use python where I can now.

All web stuff I do in python. Gui apps I do in python, e.g with wxpython, which overlays wxwidgets (written in C++). That is a good example, to a user wxpython looks just like any other wxwidgets apps, and essentially same speed, just quicker and easier to write.

I use python even for apps reading writing binary data, to files or devices etc where you may tradionally think C/C++ would be more suitable. But python can convert binary data in a one-liner (with array or struct modules) and then you can work with the binary data in higher level python lists/dicts etc. Then just convert to binary, in another one-liner, when you output. Much easier.

Python is a practical and pragmatic language, unlike C++ which IMHO was hijacked many years ago by academics touting template meta-programming etc. That stuff is sometimes cute and interesting but damn complicated and not often appropriate to the real world. I could go on ...

---

### Post by MiXor on 2012-05-12
I read that python only checks the code at runtime. Hasn't that made things tricky for debugging?

---

### Post by 11jmb on 2012-05-12
on the contrary, it makes debugging large projects easier, because you don't have to re-build every time. Python interpreters sometimes don't have as good of error messages as some C compilers, but I find that debugging is a breeze in Python. (also, you're forced to write more readable code in Python, so errors are sometimes easier to find). Furthermore, I find that I have less bugs in the first place with Python, and I have way more experience with C :)

---

### Post by 11jmb on 2012-05-12
> **Shadius said:**
> Hey guys, ):P

Where would a beginner with absolutely no knowledge of programming language begin their journey into the programming world? It's very interesting to me. :)

This question is very interesting to a lot of people on this board :) I recommend a quick thread search, because this has been discussed many times.

Do you have a particular project or problem space towards which you would like to apply programming knowledge? or just a general interest?

---

### Post by Shadius on 2012-05-12
> **11jmb said:**
> This question is very interesting to a lot of people on this board :) I recommend a quick thread search, because this has been discussed many times.

Do you have a particular project or problem space towards which you would like to apply programming knowledge? or just a general interest?

I don't have a particular project or problem right now, but I am studying Computer Information Systems aimed toward the Software side of things, but my school also offers the Programming track as well. It's more of a general curiosity to see what I can learn and do with programming. I find it really interesting putting in codes and then getting an output. I like the whole idea of doing things in the Terminal rather than using the GUI. I'm just wondering what programming language should a beginner try to start with first? There's so many it gets confusing! I wouldn't say I have zero experience with programming languages, because I did take a Visual Basic class which peaked my interest even more. :) Then I found this thread! :guitar:

---

### Post by woxuxow on 2012-05-12
that is depends on what you want to do

---

### Post by 11jmb on 2012-05-12
Give Python a try. I don't think that there's a language that will get beginners up and running faster. This is important because you will be able to acquire lots of general programming skills that can be applied to many different domains.

---

### Post by Shadius on 2012-05-12
> **11jmb said:**
> Give Python a try. I don't think that there's a language that will get beginners up and running faster. This is important because you will be able to acquire lots of general programming skills that can be applied to many different domains.

Great! I want to start off with the fundamentals and build off of that. Is there something I'm supposed to download to try Python?

---

### Post by 11jmb on 2012-05-12
@OP: is it fair to assume you are using Linux? the answer to the microphone question can differ between operating systems.

As for the signal processing, you can use numpy for just about everything you would ever need. Post specific questions if you need help. In general, you should have a compelling reason to develop in C (i.e. running this code on a device or heavy processing on live signals) in lieu of languages like Python, IMO, because of how much faster you can develop. Place a high value on your time :)

---

### Post by 11jmb on 2012-05-12
> **Shadius said:**
> Great! I want to start off with the fundamentals and build off of that. Is there something I'm supposed to download to try Python?

Have you read the sticky? Good stuff there :)

If you are using Ubuntu (a fair assumption on this board, right?) Python should already be installed.

For beginners, I recommend just editing your scripts in your favorite text editor, and executing them with the command line. IDE's are great development tools for experienced programmers, but they are not good learning tools.

---

### Post by Shadius on 2012-05-12
> **11jmb said:**
> Have you read the sticky? Good stuff there :)

If you are using Ubuntu (a fair assumption on this board, right?) Python should already be installed.

For beginners, I recommend just editing your scripts in your favorite text editor, and executing them with the command line. IDE's are great development tools for experienced programmers, but they are not good learning tools.

Didn't notice the sticky. Will check it out. Yes, I am on Ubuntu, so I will check out Python now. :) Thank you for your help, and I must apologize for getting off topic from the original poster's topic.

---

### Post by MiXor on 2012-05-12
Hey Shadius, no worries about veering off the original topic, that kind of like what happens face to face anyway :)
I'm new to Python too, and this: [http://code.google.com/edu/languages/google-python-class/index.html](http://code.google.com/edu/languages/google-python-class/index.html) seems like a good place to start if you know a little bit about programming.

---

### Post by MiXor on 2012-05-12
> **11jmb said:**
> @OP: is it fair to assume you are using Linux? the answer to the microphone question can differ between operating systems.

As for the signal processing, you can use numpy for just about everything you would ever need. Post specific questions if you need help. In general, you should have a compelling reason to develop in C (i.e. running this code on a device or heavy processing on live signals) in lieu of languages like Python, IMO, because of how much faster you can develop. Place a high value on your time :)

I have no other good reason to program in C than the fact that I use it at work to acquire and generate signals from data acquisition cards. 
NumPy looks like a brilliant piece of work. +1 for Python... :)

I am indeed using Linux. In a nutshell, the idea is to make a little application that explains for ex. what a note is, why if a piano and a violin play an A, it can be the same A but we do recognize the piano and the violin, or how scale temperament works... Fun science stuff!

By any chance, would you know how to retrieve the signal from a microphone and stick it into an array?..

Close to be bitten by the Snake... :)

Aline

---

### Post by pauljwells on 2012-05-12
I would agree with recommending Python for a beginner. Like markbl, Python is my default choice for anything I'm writing for myself. Even if later on I decide to rewrite the bottlenecks in something lower-level (one of the  'Cs' or more often, Fortran using the amazing f2py wrapper included with numpy), writing it in Python first lets you sort out your structure and algorithms so that you have a working, if slow, application against which to check the compiled language code. I would also agree with wxPython for GUI writing. A great place to start is the online book 'Dive into Python' which used to be in the repos and might be still. For wx the 'bible' is 'wxPython in Action' by Robin Dunn (who wrote the code). Gedit or Idle are fine as editors to start with. Once you get into bigger projects then eclipse with pydev is the way to go, or if you are on Windows, the excellent pyscripter.
Lastly, don't believe the naysayers who will tell you that Python is too slow. For most things is it more than fast enough, it has many high level structures that do a lot with just one line and run at 'C' speed. (list comprehensions, for example). It is easy to write parallel code using pp and it is easy to link compiled code using f2py, or (a little harder) swig.
Have fun!

---

### Post by pauljwells on 2012-05-12
Stackoverflow is a great place to find answers to many programming queries. This link might answer your question regarding capturing the microphone input. A great beauty of Python is that you will almost always find a library that someone else has already written that does more or less what you want. It's like programming in 'Lego' ;-)

[http://stackoverflow.com/questions/1936828/how-get-sound-input-from-microphone-in-python-and-process-it-on-the-fly]("http://stackoverflow.com/questions/1936828/how-get-sound-input-from-microphone-in-python-and-process-it-on-the-fly")

---

### Post by MiXor on 2012-05-13
Hadn't thought of stackoverflow, good thinking. Thanks for the link!

ok, I've been overwhelmingly convinced to use Python.

---

### Post by The Cog on 2012-05-13
> **MiXor said:**
> I read that python only checks the code at runtime. Hasn't that made things tricky for debugging?

It means that you cannot skimp on testing, because errors that in some languages would be picked up by the compiler only show up later during testing. For example:
```
# try to concatenate 'str' and 'int' objects:
a = "foo"
b = 99
c = a + b

# mis-spell a variable name:
myValues = [3, 5, 7, 11, 13]
average = float(sum(myValues)) / len(myvalues)

```
I have seen a program called pylint that can scan a python program and pick up a lot of these errors in much the way a compiler would.

---

### Post by MiXor on 2012-05-13
> **The Cog said:**
> It means that you cannot skimp on testing, because errors that in some languages would be picked up by the compiler only show up later during testing.

Yes, I got that, and I do make lots of typos when I write!! Hence my question... 

> **The Cog said:**
> I have seen a program called pylint that can scan a python program and pick up a lot of these errors in much the way a compiler would.

I'll definitely check that out in due time! (Where Python is concerned I am now at the 'very beginner' stage, barely beyond hello world :P )

---

### Post by memilanuk on 2012-05-14
It takes a bit more setup to get rolling, but Eclipse + PyDev has excellent code completion - better than most 'free' editors/IDEs I've tried - along with checking your code against PEP8 (python coding standard) for things like unused (or unresolved) imports, syntax, formatting, naming conventions, etc. and has pylint in there too.  You have to set up house according to their 'project' structure for the tools to know where to look and how things are supposed to relate, but so far I'm amazed at how slick it is overall.  I'm just a dabbler, doing this stuff now and again for fun so I always thought an IDE was gross overkill for my needs.  Probably still is, as I know I'm only scratching the surface of what it can and will do for me... but code-completion + code-checking at least makes me *feel* like I'm learning more, faster :lolflag:  Other IDEs like Spyder, Eric, Komodo Edit, Wing 101, SPE, etc. have varying degrees of the above features, so feel free to test away.  The biggest selling point on Eclipse + PyDev for me is code completion, not just for the language (python has a lot of built-in functions) but also for import modules - once you start importing GUI tool kits that saves you a ton of typing in a hurry!

YMMV,

Monte

---

### Post by MiXor on 2012-05-15
@memilanuk/Monte :)

I'll have a go at it once I get more fluent! So far gedit has been enough.
Incidentally, talking about GUIs, what do you know of handy modules and graphical interface objects for making a friendly interactive interface showing mostly graphs and pictures? 
Thanks!!

Aline

---

### Post by memilanuk on 2012-05-15
so far I'm liking PyQt4, using QT4 Designer to design the UI, then pyuic4 to convert the .ui (xml) file to a python module that can be imported (which is where having an IDE or editor that can do code-completion based on imports) into your main program file.

zetcode.com has tutorials on a variety of GUI toolkits for python... pyqt, pyside, tkinter, gtk, wxpython - good ones to walk thru and see which appeals to you.

---

### Post by Darkblood on 2012-05-15
Is programming a hobby to you? If so i would recommend python.
You still have to research to see what kind of libraries (if any) are there for python and C++ to help you doing your application.

---

### Post by MiXor on 2012-05-16
> **memilanuk said:**
> so far I'm liking PyQt4, using QT4 Designer to design the UI, then pyuic4 to convert the .ui (xml) file to a python module that can be imported (which is where having an IDE or editor that can do code-completion based on imports) into your main program file.

zetcode.com has tutorials on a variety of GUI toolkits for python... pyqt, pyside, tkinter, gtk, wxpython - good ones to walk thru and see which appeals to you.
Could I possibly have a little snippet of the sort of thing you can do with it?

---

### Post by diesch on 2012-05-16
> **MiXor said:**
> 
Incidentally, talking about GUIs, what do you know of handy modules and graphical interface objects for making a friendly interactive interface showing mostly graphs and pictures? 


Have a look at [Matplotlib](http://matplotlib.sourceforge.net/)

---

### Post by MiXor on 2012-05-18
Matplotlib looks really neat, might even come in handy for work...:biggrin:
*added to favourites* ;)

---

### Post by memilanuk on 2012-05-18
> **MiXor said:**
> Could I possibly have a little snippet of the sort of thing you can do with it?

...not quite sure what you're asking for here.  Are you talking beyond what they show in the demos listed on zetcode.com, or...?

Something else that might be of interest to you if matplotlib sparked your interest... spyder is an IDE that works with numpy, scipy, PyQt4 and ipython (Interactive Python).  It has pyflakes (a slightly lighter/faster code analysis module than pylint), rope (for code completion), etc.

For that matter, just plain ipython ([www.ipython.org](www.ipython.org)) may work for you... the demos on their site for interactive cells for graphs (using matplotlib) and web-enabled 'notebooks' look pretty dang impressive.  Not really the direction I'm headed in right now, but still impressive.

The above combination (spyder, ipython, pyflakes, matplotlib, numpy, scipy, etc.) is supposed to make a decent challenger to things like Mathematica...

---

### Post by MiXor on 2012-05-18
> **memilanuk said:**
> ...not quite sure what you're asking for here.  Are you talking beyond what they show in the demos listed on zetcode.com, or...?

I'm just generally curious to see what people do, so I meant (I hope I'm not being rude there) what you personally built. It's always a great way to find out how you could be doing things differently. I'm lucky you found my question unclear, I had never heard of zetcode before. Lots of good stuff in there..

I've marked this thread as "solved" -though "solved" isn't quite the right term- and started a new thread because now my questions are related to GUI making. Who knows, it might make things easier for the next Python beginner :) 
Perhaps catch you in next thread?

---

