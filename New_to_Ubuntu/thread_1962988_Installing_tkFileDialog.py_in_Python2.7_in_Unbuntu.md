---
title: "Installing tkFileDialog.py in Python2.7 in Unbuntu 11.10"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by phkahn on 2012-04-21
I have numerous routines written in Python running under windows that  call tkFileDialog.py. I am trying to port those programs to Python2.7  running on Ubuntu 11.10 and I realize that I need to install the package  containing tkFileDialog.py .  I checked inside /usr/lib/python2.7 and  found a directory called lib-tk that contains tkFIleDialog.py and the  compiled version tkFileDialog.pyc . I think I just need to install the  modules in lib-tk in Python 2.7.

This is what I have tried so far...

philip@philip-System-Product-Name:/$ sudo apt-get install /usr/lib/python2.7/lib-tk/tkFileDialog.py

and this was the response...

[sudo] password for philip:

I then entered my user password and then the console responded...

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package /usr/lib/python2.7/lib-tk
E: Couldn't find any package by regex '/usr/lib/python2.7/lib-tk'

Given  that the console said that it was finished reading package lists I do  not see why it couldn't locate package /usr/lib/python2.7/lib-tk . Any  help would be most appreciated.

I think that I may need to install all of the modules in /usr/lib/python2.7/lib-tk not just tkFileDialog.py .  If this is so, would the command I should use be:

$ sudo apt-get install /usr/lib/python2.7/lib-tk *

?

---

