---
title: "Best Python Wrapper"
date: 2006-12-12
forum: Programming Talk
---

### Post by mustang on 2006-12-12
Hello everyone.

Currently I am a student and as an undergraduate research project, I will be writing a simulator (for something top secret :) ) in python. This simulator will require a GUI of some sort.

I want the simulator to be cross platform---more specifically, I want it to run on linux, windows, and mac osx.

I went to the bookstore and picked up one of O'Reilly's Python books and started reading through it. Here's his take on the most popular python wrappers:

**Tkinter**
-widely used/de facto standard
-mature, well documented
-*no* changes needed for source code

**wxWidgets**
-better for sophiscated interfaces
-more complex than Tkinter
-more code needed
-less documentation
-richer set of widgets

**PyQT**
-complex but feature rich
-license issues (probably does not apply to me)

**PyGTK**
-works on OSX (provided an X server for OSX is installed)

Basically, he favors Tkinter and that's the wrapper he goes on to teach in the book. 

My question for all of you is what would be the best python wrapper for me to use? Which wrapper best finds that balance between appearance and portability? I don't mind spending a day or two porting but definitely not weeks.

The reasons I want to use Tkinter is because it looks pretty decent under windows,O'Reilly uses it in his book, and it ships with python so it is available on the lab computers here at school. On the other hand, Tkinter looks pretty aweful (from the screenshots I've seen) under linux or OSX.

But as for the other wrappers, I don't have any opinion either way.

---

### Post by gotgenes on 2006-12-12
Know your intended audience and craft it towards that. How technically savvy are they? Not at all? Tkinter looks like the only option for cross-platform, since all the others require the end-user to install the toolkit (excepting some Linux users). Are they tech-heads? Choose your favorite and go from there.

You could also abstract the interface to the GUI enough that the program is not tied to any one toolkit. That would be the ideal situation but probably more time and effort than it may be worth.

---

### Post by Wybiral on 2006-12-12
Whenever I need a GUI in python I use Tkinter. It's very simple and easy to use and looks just fine.

---

### Post by gordyt on 2006-12-13
I've found the Tkinter looks just fine under OS X.  I am using a new version of Python than that which is installed by default.

--gordy

---

