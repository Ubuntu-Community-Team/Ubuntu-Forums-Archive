---
title: "Problem Installing Python Site-Packages/Modules"
date: 2009-09-05
forum: Programming Talk
---

### Post by hatros on 2009-09-05
I've been having trouble with a few python programs on my jaunty system. It seems like I have more than one version of python installed, and when I try to install something like PYGAME it installs into one of the older python folders/distributions.

/usr/local/lib/ has 3 python folders:
python2.5, python2.6, and python3.0
The first 2 are pretty much empty, and python3.0 is full of .py files and whatnot.. so I assume its the active version on my system.

I installed python-pygame, with apt-get but then when I run the python interpreter and try "import pygame" it says no module found. I checked in /usr/local/lib/python3.0/site-packages to see if it was there, but it wasn't. In fact that folder is almost empty.

I looked around some more and finally found pygame here instead:
/usr/lib/python2.5/site-packages/pygame

And when I look in /usr/lib/python2.5/site-packages/
it is full of packages.

So my question is.. what's going on? how do I get python to install into the most current distribution folder? .. I've had a variety of other strange problems with python programs. I feel like this is all related.

I've tried just moving pygame from /usr/lib/python2.5/site-packages/pygame to /usr/local/lib/python3.0/site-packages/pygame, but obviously that's not enough, because then I just get other module loading errors when running the python interpretor and importing pygame.

Why do my packages install to a older version of python? I'm confused.

---

### Post by nipunreddevil on 2009-09-05
I installed all with synaptic and never faced a problem

---

### Post by hatros on 2009-09-05
I've tried that.. although I figured it wouldbe the same as using apt-get. It just installs into:
/usr/lib/python2.5/site-packages/pygame

And this is my pythonpath according to sys.path:
['', '/usr/local/lib/python30.zip', '/usr/local/lib/python3.0', '/usr/local/lib/python3.0/plat-linux2', '/usr/local/lib/python3.0/lib-dynload', '/home/hup/.local/lib/python3.0/site-packages', '/usr/local/lib/python3.0/site-packages']


Anyone have any ideas why pygame is installing to /usr/lib/python2.5/site-packages/pygame ? doesn't it or shouldn't it use something from the python path for installation?

---

### Post by nipunreddevil on 2009-09-05
i read somewhere that there is some way in which using synaptic you could ensure which version of dependency you want to install for.don't remember it though

---

### Post by unutbu on 2009-09-05
Some system applications which use python will break if run under python3.0. 
There are also many python modules (like pygame and numpy/scipy) which have not yet been ported to python3.0. Because of all these problems, python2.x is still the default "main" python used by Ubuntu. 

I suggest you uninstall all the python installations you have in /usr/local.
Then, as nipunreddevil suggests, just use the python packages in the official Ubuntu repositories.
```

$(which python) --version
```
should return something of the form```

Python 2.x.x
```

---

### Post by hatros on 2009-09-05
Ah, ok. That makes sense then. PYGAME is installing to its supported python version.. 

And that python3.0 I installed is likely breaking some other python applications I've been having trouble with.

My problem now is.. how do I get rid of python3.0? Its not selected in Synaptec. apt-get says its not installed. I also tried dpkg -autoremove python3 which removed a few things.. but python3 still loads when I type "python" into the terminal window.

All I can think of now is to delete the python3 libs and uninstall everything python and re-install. That'll suck.. because it will also remove everything dependent on python, right?

---

### Post by hatros on 2009-09-05
I uninstalled python.. that was fun. That killed my GUI, so I re-install python and then ubuntu-desktop ubuntu-minimal ubuntu-standard

Python still wouldn't work though, or at least the interpreter wouldn't work. So I ended up going to /usr/local/bin and deleting:
2to3 python3.0 python3.0-config pydoc python-config idle smtpd.py
and then the python3.0 dir from /usr/local/lib

and now I'm back to python2.6 and pygame installs fine.

Thanks for giving me the clues I needed!

*and as a bonus quodlibet and sudoku among other apps all work again too.

---

