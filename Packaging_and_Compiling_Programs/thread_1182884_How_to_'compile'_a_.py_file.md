---
title: "How to 'compile' a .py file?"
date: 2009-06-09
forum: Packaging and Compiling Programs
---

### Post by LiamWilson on 2009-06-09
Hey, I've made a (Rather Nifty, I think) app that I would like to compile into a stand-alone app for either Windows or Linux, or both.

I'm running Jaunty, with both Python 2.6 and Python 3.0 installed. The .py file I have is called 'area.py'. Does anyone know any tools or apps, or anything, I can use to turn it into a stand alone EXE or Linux executable?

---

### Post by eilios on 2009-06-12
> **LiamWilson said:**
> Hey, I've made a (Rather Nifty, I think) app that I would like to compile into a stand-alone app for either Windows or Linux, or both.
 
I'm running Jaunty, with both Python 2.6 and Python 3.0 installed. The .py file I have is called 'area.py'. Does anyone know any tools or apps, or anything, I can use to turn it into a stand alone EXE or Linux executable?
To make it a linux executable just make it a .so and chmod it, for a windows executable use py2exe.

---

### Post by LiamWilson on 2009-06-13
Aah, how would I go about making it a .so file and chmod-ing it?

---

### Post by SOULRiDER on 2009-06-19
AFAIK python cant be compiled, its always interpreted.

---

### Post by curvedinfinity on 2009-06-20
He wants is an application that will embed the python interpreter and the python source in a binary. As far as I'm aware, such a thing doesn't exist for Linux because most linux systems have such good package management software.

---

### Post by RainCT on 2009-06-20
Have a look at cx-freeze (a [package for it is available in Karmic](http://packages.ubuntu.com/karmic/cx-freeze)), it should be able to create an executable for GNU/Linux.

But, why would you want to ship an executable? ".py" files are much prefered.

---

### Post by dyfet on 2009-06-20
It probably helps to understand that there is a bytecode compiled form of Python, the .pyc file.  This is to .py what a Java .class file is to a .java source; it is the format created and recognized internally by the python runtime engine when a python "source" file is loaded and parsed.   

Python class files are most useful for imported libraries.  If you look at /usr/lib/python2.6, you will see the normal modules for python are distributed in compiled class form, .pyc.  And in dist-packages, you may see both .py and .pyc files.  Having .pyc means when an "import" statement is processed, the python source for the library module does not have to be parsed and converted into class files each and every time.

I would imagine "py2exe" type wrapper scripts simply embed some stub code and a .pyc class file directly into an executable script, which means faster startup since the script does not have to be parsed, but is NOT a machine code translated executable of the python source itself.

---

### Post by LiamWilson on 2009-06-21
Just a quick Update guys, I managed to make it an exectuble by adding ```
#!/usr/lib/python
``` as the 1st line, and then running ```
chmod a+x /path/to/file
``` Then when I run it, I can run it in a terminal, or view the contents. Very Handy :) Thanks for the replies guys. :D

---

