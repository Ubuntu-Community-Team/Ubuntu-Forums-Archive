---
title: "python tk"
date: 2012-04-13
forum: Programming Talk
---

### Post by Jacobonbuntu on 2012-04-13
Hi people, probably a stupid question, 
but:
just installed 12.04 beta2 to do some testing....
I expected python tk to be installed by default, but not. is there something wrong with my installation??

---

### Post by PeterP24 on 2012-04-13
Hi,

I have a year old Ubuntu installation and I don't remember if it came with Tkinter installed or not. Have you searched using Synaptic Package Manager to see if python-tk package is installed? I don't think it is something wrong with your installation - maybe python-tk isn't included by default ...

---

### Post by memilanuk on 2012-04-14
For whatever reason, the Ubuntu developers take it upon themselves to break up the python packages further - if you want tk, you have to install the python-tk package (or python3-tk), if you want IDLE, you have to install the idle-python2.6 package, etc.  Given that IDLE uses tkinter, if you install the idle package, it should pull in python, tkinter, and whatever else it needs.

---

### Post by Jacobonbuntu on 2012-04-14
hmmm, now you mention it, I might have installed it in the passed, but always thought it was standard, along with python (think it should be)
thanks for replying,
have a good time!
Jacob

---

### Post by memilanuk on 2012-04-14
In general I don't like it when they split up packages from the upstream vendors or developers... but I'm guessing the logic is something along the lines of this:  Linux in general uses python a *lot* for system level programs and scripts, even in the CLI-only 'server' version - which has no need for tkinter, so why burden installs un-necessarily if its not needed.  There are plenty of python programs that use tkinter that will pull it in as dependency as needed if the user installs them.  Probably the only time it becomes an issue is when someone has a new system and wants to try *developing* python w/ tkinter programs, and it hasn't been pulled in yet.

Not saying I like it, but I can (kinda) understand the reasoning...

---

