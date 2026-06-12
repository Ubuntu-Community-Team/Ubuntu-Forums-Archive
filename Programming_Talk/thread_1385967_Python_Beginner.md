---
title: "Python Beginner"
date: 2010-01-20
forum: Programming Talk
---

### Post by beegary on 2010-01-20
I have a fair bit of experience in the world of computing, mainly hardware and windows.
I have written a few scripts before but that is as far as it goes in regards to programming.
I am a recent convert to Ubuntu.(from Windows).
 
I am trying to delve into the world of programming and am having some success with Python. I was hoping I could get some help here:
 
I have been following a few tutorials on devshed, and am planning to write a python program to do a few simple things with PDF's.
This was one of the guides that I have been using
[http://www.devshed.com/c/a/Python/Python-for-PDF-Generation/](http://www.devshed.com/c/a/Python/Python-for-PDF-Generation/)
 
If I write a Python program that utilises extra Modules that I have to download/import like reportLab and PIL is it possible to integrate these into my program? (assuming they are opensource etc)
If that is possible will they run within any OS? Will I always run into problems by programming in Linux but hoping to run in Windows?
I am playing around with Python 2.6 should I be worried about converting to 3.0 etc. Is 3.0 backwards compatible?
 
It is very likely that I have missed something or am barking up the wrong tree, what I am aiming to do is read certain values from a PDF, combine PDFs, add pages, and (if the force is with me) use the info to create a database of the PDF's.
Is this all possible using Python? Would I be better off using another language? (?Java?)
 
Sorry for the exceedingly long message, :D

---

### Post by denarced on 2010-01-20
> **beegary said:**
> If I write a Python program that utilises extra Modules that I have to download/import like reportLab and PIL is it possible to integrate these into my program? (assuming they are opensource etc)
If that is possible will they run within any OS? Will I always run into problems by programming in Linux but hoping to run in Windows?
I am playing around with Python 2.6 should I be worried about converting to 3.0 etc. Is 3.0 backwards compatible?
 

If they're opensource, sure.
As long as the system has python interpreter, everything should run smoothly on windows too. Kind of like Java.
Python 3 is not backwards compatible. The changes aren't dramatic and there is a tool for converting sourcecode from 2 to 3. The tool is name 2to3 if I remember correctly. But you should propably start learning v3 if you're just beginning 'cause 2.6 will disappear eventually.

---

### Post by beegary on 2010-01-20
>  
If they're opensource, sure.

Good! my little program would be a complete waste of time if not. So I suppose once I have the program running etc there is a way to wrap it all up including the modules of PIL/Reportlab that it depends on?
 
> Python 3 is not backwards compatible. The changes aren't dramatic and there is a tool for converting sourcecode from 2 to 3. The tool is name 2to3 if I remember correctly. But you should propably start learning v3 if you're just beginning 'cause 2.6 will disappear eventually.
 
Hmmm Reportlab is compatible with 2.6, so I think I will stick with that at the moment. Also more, free documentation is avaialable for 2.6.
 
Thank you for your reply  denarced

---

### Post by Can+~ on 2010-01-20
Btw, I hope you are taking advantage of aptitude, as most windows converted people tend to miss this great tool (and instead, they try to compile by source, scout the internet for tutorials, when everything is available in the repository)

Searching:
```
~$**apt-cache search python report lab**
python-renderpm - python low level render interface
python-reportlab - ReportLab library to create PDF documents using Python
python-reportlab-accel - C coded extension accelerator for the ReportLab Toolkit
python-reportlab-doc - Documentation for the ReportLab Python library (PDF format)
yapps2 - Yet Another Python Parser System
ipython - enhanced interactive Python shell
python-logilab-common - useful miscellaneous modules used by Logilab projects
python-pymetar - Python interface to METAR reports
python-renderpm-dbg - python low level render interface (debug extension)
python-reportlab-accel-dbg - C coded extension accelerator for the ReportLab Toolkit
python-wordaxe - German language (and other) hyphenation algorithms
skencil - Interactive vector drawing program for X11
python-apport - apport crash report handling library

~$**apt-cache search python image library**
python-gd - Python module wrapper for libgd
python-htmlgen - Python library for the generation of HTML
python-imaging - Python Imaging Library
python-imaging-dbg - Python Imaging Library (debug extension)
python-imaging-doc - Examples for the Python Imaging Library
python-imaging-tk - Python Imaging Library - ImageTk Module
python-imaging-tk-dbg - Python Imaging Library - ImageTk Module (debug extension)
python-nautilusburn - Python bindings for the Nautilus CD burner
gvb - visual simulator of 1 and 2-dimensional vibrations
python-exactimage - fast image manipulation programs (Python bindings)
python-imaging-doc-html - Documentation for the Python Imaging Library.
python-imaging-doc-pdf - Documentation for the Python Imaging Library.
python-iptcdata - Python bindings for the iptcdata library
python-nodebox-web - collection of web-related Python modules
python-opencv - Python bindings for the computer vision library
python-pyexiv2 - Python binding to Exiv2
python-qwt3d-doc - Documentation for the Python-qwt3d library
python-vipscc - image processing system good for very large images (tools)

```

Installing
```
sudo apt-get install python-imaging python-reportlab
```

Also, if you're interested in PDF generation, you should look into LaTeX:

```
sudo apt-get install texlive gedit-latex-plugin
```

LaTeX can generate beautiful documents and formulas, in fact, is what Wikipedia uses to build formulas.

---

### Post by beegary on 2010-01-21
Thank you CanPlus that is very helpful. I did use the Ubuntu software centre to try and find those modules/plugins but I suppose that sort of program extension would never be in there?
I have been using ```
sudo apt-get install
``` but I must admit I hadnt yet learnt any other commands in apt-get. 
I had downloaded PIL and ReportLab manually but luckily I had not yet run the install procedure.
 
I I also add documentation using apt-get does it always tend to get copied to the same folder as the program itself resides?
 
I have been using ghostscript as I have some experience with in on a Solaris platform, I'll check out LaTex too.

---

