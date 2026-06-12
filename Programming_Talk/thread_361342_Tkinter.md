---
title: "Tkinter"
date: 2007-02-14
forum: Programming Talk
---

### Post by SuperCow56 on 2007-02-14
I am using Ubuntu 6.06 and I need to know how to get Tkinter working. Do I have to download it? Or is it already part of the python package that came with Ubuntu.

---

### Post by lnostdal on 2007-02-14
this page mentions some tests you can do to determine whether tkinter is installed: [http://wiki.python.org/moin/TkInter](http://wiki.python.org/moin/TkInter)

(first hit on google btw. :P)

---

### Post by kthakore on 2007-02-14
the tkinter module is a part of the python package. This website has more info [http://www.pythonware.com/library/tkinter/introduction/]("http://www.pythonware.com/library/tkinter/introduction/")

---

### Post by WW on 2007-02-14
Install the package **python-tk**.  For example, in a terminal:
>  $ sudo apt-get install python-tk

---

### Post by riley468 on 2007-12-31
I am using Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) on 
Ubuntu 7.10 (Gutsy Gibbon) and have tried to import Tkinter at the Python prompt:

 >>> import Tkinter 

with the following result: 

ImportError: No module named _tkinter, please install the python-tk package.
 
I followed the intstructions in the thread and entered the following at the shell prompt: 

sudo apt-get install python-tk 
 
with the following result: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.5
E: Package python-tk has no installation candidate

Can anyone help me? What should I do now?

Thanks in advance...and a happy new year to all.

---

### Post by jphaberman on 2008-03-08
@riley468: I am experiencing the same issue.  Were you able to resolve it?

---

### Post by riley468 on 2008-03-11
Look in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you have a check mark on all th repos except the last one, Source code and the CDROM at the bottom window. If you need to add them in, then you must press the Refresh button. Now, see if you can find that package again in synaptic with the Search option.

---

