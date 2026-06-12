---
title: "Where to start?"
date: 2007-01-04
forum: Programming Talk
---

### Post by azkehmm on 2007-01-04
This has propably been asked a few times before, but I seem to be unable to find the answer. Apologies in advance, if I'm punishing a dead horse :)

 Having used computers for gaming and work since I was 8, I figured out, after starting to use Linux, that I have close to no idea about how to build my own software. This annoys me, as i can build stuff in all my other hobbies. So, I figured it was time to learn it now. I've looked at numerous guides and tutorials but they all lack what I find most important in a tutorial, a product. So, now I have decided that I want to create two small programs to use when I'm playing D&D. 
 First one is a diceroller, the second is a character creator (since I can find neither of these for linux :)). If it isn't too difficult, I'd like to make both with a Gnome GUI. So, the question is:
 Bearing in mind that I have basically no programming experience, except for some very basic HTML and a little macro-writing in WoW and SWG, what languages would be well suited for these tasks? 

Thanks in advance.

---

### Post by welshboy on 2007-01-04
I've just started to learn python, having programmed (badly) in Java for the last few years.

It comes free with linux, and there's some excellent tutorials out there.  One I would strongly recommend to get you going is:

[http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

I'm using this to learn python myself, and I've found it very useful.  Python's syntax IMHO is similar to C, so once you've got to grips with Python, then it opens the door to other programming languages.

Hope that tidbit helps :D

---

### Post by kidders on 2007-01-04
Hi there,

If you really have _no_ programming experience, I would suggest sticking to scripting languages like perl, php, etc., and a web-based or text-based UI. Everyone loves python (I just haven't gotten around to learning it yet), but you might also like to give that a try.

In terms of difficulty, your next step up might be something like java, followed by the traditional "real" languages like C/C++, etc. These are actual *programming* languages (rather than just scripting engines), but it would take quite a bit of effort to go from zero to Gnome-based UIs with them.

Since the apps you're describing are quite basic, I would be inclined to suggest staying with what you're already familiar with, and using PHP to make little web-based things for yourself. When you have the time, you could work on replicating them in other languages.

**Edit:** Yikes @ welshboy... yet another person singing the praises of python! I really must learn it!

---

### Post by welshboy on 2007-01-04
> **kidders said:**
> 
**Edit:** Yikes @ welshboy... yet another person singing the praises of python! I really must learn it!

I've only been learning Python for fun!!  At the moment I'm frantically trying to learn J2EE and C to try and find a job as a programmer.  I did learn it at university, but that was four years ago!  But Python is a nice little hobby programming language.  (for me anyways)

;)

---

### Post by stimpsonjcat on 2007-01-04
> **welshboy said:**
> [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

I've used the same text to dive into programming myself and highly recommend it. It was written by CS teachers and the examples are very good. I'm confident you'll be able to create a command line dice roller after having read it. GUIs and other advanced topics (like databases, threads etc) are not covered though.

For GUI stuff you'll have to learn one of the GUI toolkits -- Tkinter (probably the easiest), wxWindows, qt, Gtk / Glade. I think that you should start with a command line version first though.

---

### Post by studiesrule on 2007-01-04
I agree that ThinkCSpy must be the best start off text for Python. Python is a very good language to understand the nuances of programming, because it's very straightforward. It also does a lot for you. The interpreter allows you to just type in commands into the shell, and explore the language very quickly (as opposed to compiler languages where you have to make a small program to do it).

However, C++ isn't too difficult either. The general learning curve for any programming language is a one time thing. If you learn any language, then another langauge isn't very hard to learn. So IMHO, learn python first, then emmigrate to C++ (I like C++ much more than C). I don't know java, so I can't say anything about that.

wxWidgets has a python port, and is pretty great. It has a very good tutorial, but it's for C++ ( [wxWidgets Book]("http://www.phptr.com/content/images/0131473816/downloads/0131473816_book.pdf"). It takes quite some time to get into it though (took me a week approx. to get a grip and make something) . I think the wxPython site has a lot of information too.

---

### Post by pmasiar on 2007-01-04
>  Bearing in mind that I have basically no programming experience, ... what languages would be well suited for these tasks? 

You are right, we beat that horse couple times and it is almost dead - but maybe it is Rocky, always raises again and continues to struggle :-)

Some pointers - all from last week only:
[LIST]
[*][What Is the Most Suitable Programming Language for a Beginner?]("http://ubuntuforums.org/showthread.php?t=233405") (with poll, winner: python)
[*][Assembly as first language?]("http://ubuntuforums.org/showthread.php?t=330796") (consensus: not)
[*][How to learn Python?]("http://ubuntuforums.org/showthread.php?t=329984")
[*][Python or Ruby?]("http://ubuntuforums.org/showthread.php?t=308831") (slight preference to python)
[*][What is the best language for a newbie to learn?]("http://ubuntuforums.org/showthread.php?t=327239") (with 10 more threads linked)
[*][some really esoteric programming language if you want a challenge]("http://ubuntuforums.org/showpost.php?p=1947492&postcount=22")
[*][ A programming language to start with]("http://ubuntuforums.org/showthread.php?t=326971")
[*][Why Python?]("http://ubuntuforums.org/showthread.php?t=251282")
[*][6 more links to selecting a language]("http://ubuntuforums.org/showpost.php?p=1900222&postcount=6")
[/LIST]

**How to start, which book to use?**
My pet projets is a wiki to help non-programmers [learn programming]("http://learnpydia.pbwiki.com/HowToStart") by learning python. That page has:
[LIST]
[*]instant hacking - get the feeling without reading any boring pages
[*]two online books with basics (no object oriented programming to get you confused)
[*]links to lessons about data structures
[*]programming tasts to solve - some simple, some more complicated, but not too much
[/LIST]


> **azkehmm said:**
>  I've looked at numerous guides and tutorials but they all lack what I find most important in a tutorial, a product. So, now I have decided that I want to create two small programs to use when I'm playing D&D. 
 First one is a diceroller, the second is a character creator (since I can find neither of these for linux :)).

[LIST]
[*]diceroller - random number generator, standard library function in all languages known to man (or at least to me :p )
[*]character creator: very custom. You may want to look at [WorldForge]("http://en.wikipedia.org/wiki/Worldforge"), thay do that for living.
[/LIST]

For games, you may want to look at [Game Maker]("http://en.wikipedia.org/wiki/Game_maker")

---

### Post by lnostdal on 2007-01-04
> **kidders said:**
> followed by the traditional "real" languages like C/C++, etc. These are actual *programming* languages (rather than just scripting engines)

gawd; i cringe when i read things like this .. C/C++ are not goals to strive for; they are a necessary evil that are less and less viable as there are better alternatives for most things now..   

the "whole world" (*shrug* i must sink to this level of argumentation because it seems people do not have the ability to have independent opinions that differ from the majority) is finally starting to move away from the "Windows C API"-world where there was focus on C/C++

* python
* lisp (many implementations are compiled to native code)
* java (jit-compiled to native code)
* ruby
* ..etc..

..there are many alternatives that are more suitable 99% of the time.. C (ignore the hybrid called C++) is handy to know, just like low-level stuff in general is handy to know - but there are better means to an end now

---

### Post by Wybiral on 2007-01-04
> **lnostdal said:**
> gawd; i cringe when i read things like this .. C/C++ are not goals to strive for; they are a necessary evil that are less and less viable as there are better alternatives for most things now..   

the "whole world" (*shrug* i must sink to this level of argumentation because it seems people do not have the ability to have independent opinions that differ from the majority) is finally starting to move away from the "Windows C API"-world where there was focus on C/C++

* python
* lisp (many implementations are compiled to native code)
* java (jit-compiled to native code)
* ruby
* ..etc..

..there are many alternatives that are more suitable 99% of the time.. C (ignore the hybrid called C++) is handy to know, just like low-level stuff in general is handy to know - but there are better means to an end now

C didn't come from windows and it has and probably always will be involved with linux, do some research... There's nothing "evil" about C++, I use it daily and it doesn't make me cringe. People with experience with C++ don't usually have a problem with it, it's the people who don't know it who often complain (I'm not saying you don't know C++, just that it seems to work like that). 

I don't think C++ is exactly the epitome of programming languages, but it's: strong, readable, fast, and versatile. It is a mix of procedural + OO and allows the programmer to choose from both. It's just an enhanced version of C, it can still be used like C...

Using just the standard library I've been able to write remarkably similar looking C++ code to python code, despite what people think, C++ does not take that long to program in. People who think that often don't know much about the STL and how to use it properly (you need to know the same stuff about python too).

Suggesting lisp to a beginner? Are you mad? CL is good for math and AI, but show me a full-fledged program written in lisp. Not to mention how unstandardized lisp is. It sounds like you just have a C++ grudge... "(ignore the hybrid called C++)"

---

### Post by Lord Illidan on 2007-01-04
Um, python is all very well for learning and basic GUIs and stuff, but when you get really heavy duty like:

Operating System kernels
3D video games, etc, then C++/C are the way to go.

---

### Post by Wybiral on 2007-01-04
You can write 3d video games in python...

---

