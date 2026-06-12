---
title: "Making a deb from python distutils project"
date: 2008-05-10
forum: Packaging and Compiling Programs
---

### Post by Jadd on 2008-05-10
I've spent an entire afternoon researching this and I'm still confused. I've got a python project, which after some research, I can put into a tarball using distutils' or setuptools' setup.py sdist, and install using setup.py install. I can also make a python egg. How can I make a .deb package now?
I can't understand python central, python support, CDBS. All the help I find seems to require you know C, which I don't.
Any ideas?

---

### Post by jazee on 2008-05-12
Does any body know of a way to do this. I'm looking for the same thing. I wish to package up a simple Library into a .deb package. but the only solutions I can find are very vague and/or out of date. Setuptools says they support it but they don't seem to have much documentation on how to do this with going though a lot of trial and error.

If anyone can point me in the direction of how to do this or has an example your help will be much appreciated.

---

### Post by jazee on 2008-05-13
Ok I tried this tutorial out ([https://help.ubuntu.com/community/PythonRecipes/DebianPackage](https://help.ubuntu.com/community/PythonRecipes/DebianPackage)) and it seems to work. But how would I do the same thing to support both python 2.4 and 2.5. 

Right now I have to set my path to /usr/lib/python2.5/site-packages/ to get it to work. Is there a shared folder that I'm not seeing in the PYTHONPATH or do I need to script out in the deb file creation of links to the library?

---

### Post by Jadd on 2008-05-13
Thanks for that link, I got a working deb made thanks to that tutorial. Unfortunately, that tutorial doesn't follow the Ubuntu Packaging Guidelines. One of my questions is: is it important that I insure that the .pyc files are compiled?

---

### Post by jazee on 2008-05-13
Thats the other question I've been having. Do pyc's need to be included. Becuase when you do the distutils "python setup.py install" it builds and saves those in the site-packages folder as well.

---

### Post by Jadd on 2008-05-13
I just went through the [Complete Ubuntu Packaging Guide](https://wiki.ubuntu.com/PackagingGuide/Complete) on the wiki and I have a few questions. Bear in mind I don't know C, and I want to make a package for a python program. Open the guide and follow along, these are just my comments on the bits I didn't understand:
Packaging:[LIST]
[*]Prerequisites:[LIST]
[*]make? why should I need to know what make is? Isn't this only for compiling C programs?
[*]./configure ? again, why should I need to know about this, I've never seen a python program use it[/LIST]
[*]Getting Started:[LIST]
[*]Binary and source packages: I don't really need to make that distinction, do I? I want to distribute an open-source python program, and python code can be executed.
[*]Tools: build-essential: I don't need this for python programs, do I?
[*]Pbuilder: what are .dsc files?[/LIST]
[*]Basic packaging:[LIST]
[*]Why do we need debhelper in Build-Depends in control?
[*]What's ${shlibs:Depends}
[*]Do I need to have separate source and binary sections in the control file?
[*]The rules file is confusing, what do I really need for a python package?[/LIST]
[*]CDBS: do I need this? What does the example actually do?
[*]Skipped patches and shared libraries and KDE sections
[/LIST]

If someone could explain this to me I'd really appreciate it. :)

---

### Post by Jadd on 2008-05-21
bump

---

### Post by Jadd on 2008-06-03
bump

---

### Post by Jadd on 2008-06-04
> **jazee said:**
> Thats the other question I've been having. Do pyc's need to be included. Becuase when you do the distutils "python setup.py install" it builds and saves those in the site-packages folder as well.
I've been studying wine-door's debian package and it incloded some .pyc files, but not for every .py file, so I've concluded it doesn't really matter.
This webpage also helped me:
[Compiling python code](http://effbot.org/zone/python-compile.htm)

---

### Post by Vadi on 2008-06-04
There's a program called Debian Package Maker that's easier to figure out than these thousands of pages of confusing manuals (yes, I gave up myself. No wonder there's such a backlog of apps needing packaging in ubuntu).

[https://launchpad.net/debianpackagemaker](https://launchpad.net/debianpackagemaker)

And there's also another one too: [https://launchpad.net/debcreator](https://launchpad.net/debcreator)

---

