---
title: "Synaptic on Drake vs. Fiesty"
date: 2007-10-03
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2007-10-03
With the Drake version of Ubuntu, I could search in Synaptic-Advanced window for "python" and thus get a reference to all the python-dev, -- things for development. As I built up a package using ./configure over and over I would download additional packages from Synaptic -- for instance something like ./jpeg-imaging-dev.

Fiesty Synaptic does not search as deep. Fiesty's Synaptic has not Advanced search. The necessary libraries I am able to find for download, I find by searching these Ubuntu Forums.

Where do I find out the apt-get packages I'm looking for to do development or custom modules???

I go to python.org, I can get a source-package.tar.gz, -- PIL in this instance -- but then I can get hung up doing the build process because I don't have a dev library for OpenGL, imaging-jpeg, etc. etc. etc.

---

### Post by pmasiar on 2007-10-03
is this question about synaptic, or about python packages?

---

### Post by Unterseeboot_234 on 2007-10-03
Good question pmasiar... for example, right now:

I need python2.5-dev libs plus the supporting packages to make the PIL module for the jpeg imaging. I should end up with advanced Tkinter widgets when I'm done. 

apt-get is too specific. Synaptic, on Drake-Synaptic, would fetch reference for all things python on a search. My question then, in Fiesty. How do I get python2.5-dev without having to declare something like: apt-get install python2.5.1.2.4_development ??? or, where can I go to consider which package downloads?

thanks

---

### Post by Soybean on 2007-10-03
When I open Synaptic on my Feisty system, hit the search button, and enter "python," one of the results is "python2.5-dev". Are you saying that's not the case for you? 

Um... this might help:
```
aptitude search python
```
Of course, you can replace "python" there with whatever you happen to be looking for.

---

### Post by tgalati4 on 2007-10-03
I assume that you selected "Source Code" repositories in Feisty.  I think the development modules are only available when source code repositositories are selected.

---

### Post by Unterseeboot_234 on 2007-10-03
Look at my attached screen shot. From Fiesty -Synaptic's Preferences, I can not have a checkmark for Sources. 

Drake-Synaptic let me add all kinds of repositories. I learned today that Fiesty moved the Advanced Search (what used to be Menu Applications =>Add/Remove - Synaptic => Advanced Search in Drake), is now over under (Fiesty) Menu System => Administration => Synaptic Package Manager. The Fiesty Synaptic over under System menu behaves like I'm used to. I use Debian website to see the names of the dependencies that make their debs, jump into Ubuntu's advanced search to see if we've got it and tell either Synaptic or aptitude to download it. Works pretty good. I'm posting this, hopes it helps somebody else.

Python's PIL still won't setup.py install into Python2.5 site-package. But now I'm confident this is a Python add-on problem and not a Ubuntu thing. I can write to the Python-imaging mail list. I can't display a jpeg picture with Python Tkinter. No problems connecting the C++ image libs with Python.

Linux means freedom, as in choice. Linux means pragmatic instead of theoretical, something the other OS crowd can't understand.

Thanks forum!!!

---

