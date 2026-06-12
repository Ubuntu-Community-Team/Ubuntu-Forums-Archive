---
title: "BUILDING GUIs"
date: 2006-08-22
forum: Programming Talk
---

### Post by TheForkOfJustice on 2006-08-22
I require assistance making a database management program similar in style to the rather nice KDE Control Panel (to look professional and compete with nice-looking proprietary software).

I need code and/or a VERY SIMPLE GUI-creating program. Bindings can be added later by someone more experienced.

My end goal is a program that will take any info I enter (text fields, checkboxes, radio buttons, etc) into the nice GUI (easily reconfigurable to my needs, including the addition of tabs) and save and store the data in an open-format XML spreadsheet (like the OpenOffice format), to be recallable by a call number (or last name, first name, DOB, Date tests taken).

I'm beginning to learn how to use OpenOffice.org Base to construct a rough GUI for a database, but since it's chore I would really love the community's input before I spend too much time inefficiently.

It would be great if the XML spreadsheets would be strongly encrypted when stored (locally or network drive) and decrypted when recalled. That's vital for v1.0, so help finding code or programs that do just this would we very welcome.

All of this is for the 3rd Party 'Medical Ubuntu' project. Specifically, the clinical lab software that stores patient info and test results.

Thank you all for any help you can offer.

---

### Post by Warbo on 2006-08-23
Please pay no attention to this if they are too simple for what you want, but you did put easy in capitals :)

Anyway, the easiest way to make QT GUIs I have found is Gambas (pretty much everything QT/KDE likes to use C++, so as far as I can tell you either have really simple Gambas or pretty advanced C++)

For GTK obviously Glade and Gazpacho are the easiest ways of making GUIs, and if you program in Python then there is a script called GladeGen here [http://www.linuxjournal.com/article/7421](http://www.linuxjournal.com/article/7421) which will set up a Python program for your .glade file which is ready to run, but with blank functions for each handler. 

Both are good for rapid application development and prototyping, and it would be relatively easy to make professional-looking applications with them. The real test is in the background, and Gambas shouldn't really be used for such an application, but Python might be a good choice. Personally I would seperate out the GUI from the engine, that way you aren't forced to use a certain language for the engine just because it is easy to make a GUI in, and similarly you will not end up with a buggy GUI because the language you chose for the engine is directed to backend work. Anyway, that is my 2 cents, so make of it what you will.

---

### Post by TheForkOfJustice on 2006-08-23
Good info.

About python though, anyone got some wikis or readmes or other programs that will help me easily understand what I'm doing :p

Any other tips for using Gambas/Glade/Gazpacho/Gladegen are very welcome.

I would especially like to know how to compile python since I have a program on my windows partition that I cannot figure out how to work. With no EXE file easily visible its a pain figuring out how the hell to start the damn thing. I find Java to be just as confusing.

---

### Post by TheForkOfJustice on 2006-08-23
Oh, an issue that came up: what if this were GNOME and not KDE?

Does gnomes use a different language to make its GUIs?

If so, what simple GUI make do I need?

===

Something Else:

From my first post would anyone consider using OpenOffice Base (or any part of OpenOffice for that matter) especially useful for the task at hand?

---

### Post by UbuWu on 2006-08-23
You can use python for both gnome and kde. The difference is the GUI toolkits they use, kde uses Qt, gnome uses GTK (Glade builds gtk gui's).

For storing the data, maybe sqlite could be useful, it has good python bindings.

---

### Post by TheForkOfJustice on 2006-08-23
Concerning sqlite: is there a program out there that will help me manage sqlite?

Is is a type of code like python? Explain it to me a little.

---

### Post by Warbo on 2006-08-23
Python is an interpreted language. That means that instead of instructing the computer what to do, it instructs a program (the interpreter) instead. Interpreted laguages like Python are good because a) the language can be incredibly flexible, as long as the interpreter still understands it, so an almost English-like syntax can be used (in fact, there are interpreted languages which understand some English!) b) since you are instructing a program instead of a machine, the exact same instructions will work on any platform that the interpreter runs on (Python runs on loads of OSs and machines, including Windows, Linux and MacOS on PC, 64bit PC and PowerPC) c) because the program doesn't need compiling you can just open it up in a text editor and see instant results.

Python itself has been extended by loads of "bindings", which mean that a Python program can use GTK (GNOME's toolkit), QT (KDE's toolkit), SQLite (a simplified database system) and loads more. Because many of these bindings are written in languages like C, and it is the bindings which do most of the hard work, Python programs do not run much slower than their non-interpreted counterparts.

If you want to get into Python then there are loads of great resources out there. I would recommend you get to grips with how Python programs are written and executed using something like [http://www.diveintopython.org](http://www.diveintopython.org) and then learn about the different bindings (for example, the GTK bindings are called PyGTK).

Since I don't use QT personally, and have never tried SQLite (other than my Amarok playlist :) ) I can only really offer advice on GTK, so here goes...

To use Glade or Gazpacho I would really just recommend you try running them and play around (one thing to note is that GTK objects can only store 1 "widget" [button, label, etc.] so you should make heavy use of containers like table widgets, which split the window up and allow you to use more than one object. Gazpacho puts these containers into their own catagory which is nice).

Once you have made a GUI in Glade or Gazpacho you should add handlers to the events which you want to use (for example "on_button_release") then save the file as "something.glade" (yes, even if you are using Gazpacho), then give GladeGen that file, along with the name of your program and the name of it's first "class" (a class is to do with object oriented programming, and is a large section of code). For example you might do "python GladeGen.py MyProgram.glade MyProgram MyClass", you will then get a file "MyProgram.py" which is already set up to run, you just have to tell each handler to do what you want (each handler will have an empty section of code in the MyProgram.py file, just waiting for you to put some instructions in).

I am really not experienced at programming, but I managed to make a pretty good game engine in Python in 2 days, then added a GUI to it in half an hour with GladeGen.

---

