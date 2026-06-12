---
title: "python understanding"
date: 2007-09-29
forum: Programming Talk
---

### Post by miki85 on 2007-09-29
hi, i am an X-wannabe xp user...
I'm trying to leave it and move to Linux (Ubuntu seems pretty good for my needs)...

i used to program in visual basic for the last 8 or so years and it suited my needs in xp and all other Microsoft's platforms.

i want to learn a new language that will work in Linux and from what i saw in other peoples questions... python is the recommended one for my needs ... TCP-IP connections and other regular programs (all with GUI ... correct me if this is not the one i need and if you think that c\c#\... will be better for making simple TCP chat (for example) with GUI and not spending a week and a half doing it (when you're experienced) 

i have a few questions...

i used to have same ver of python as in linux on my xp and it was like this terminal... i can built a set of commands and in the end it will run them... but i cant compile at least from the minor experience that i had with it...
can i compile programs ? with GUI and run them on comp where no python is installed ?

and will python applications will run on winxp ?

---

### Post by sonofusion82 on 2007-09-29
the standard python is an interpreted language that does not compile to binary executable. you can run python programs that are saved as python scripts (.py)
on windows, there is a tool called py2exe that will 'compile' your python scripts into windows exe so that they can run without the python interpreter.
on platform portability, like c/c++, if you carefully select the libraries that you used, your python programs can easily run on most major platforms that python supports.
on GUI, there are many flavors for GUI toolkits around. i personally like PyQt but there are also PyGTK, wxPython and tkinter that you should check out. :-)

---

### Post by Compyx on 2007-09-29
As stated by sonofusion82, Python is an interpreted language, so you'll need the interpreter to run Python scripts. You can 'compile' Python with a variety of tools, but that would make you application non-portable.

If you want a portable GUI solution, you should probably look into wxPython, those are Python bindings to wxWidgets, a GUI-toolkit that aims to provide a native look and feel on the platform it's running on.

I suggest you read the stickies at the top of this subforum, especially the one for Windows programmers. You should also read the tutorials at [http://www.python.org]("http://www.python.org"), specifically Guido' van Rossum's introductory tutorial is a good one. Another good read on Python is [Dive into Python]("http://diveintopython.org/index.html").

---

### Post by pmasiar on 2007-09-29
Python is rather flexible, but for every library you use check availability - some are not cross-platform. Python is good choice.

twisted is very flexible framework for chats, web servers etc.

Don't worry about compiling for speed until you have performance problems - and then, profile your app to see which part is the bottleneck, and recode **that part only** as C library.

---

