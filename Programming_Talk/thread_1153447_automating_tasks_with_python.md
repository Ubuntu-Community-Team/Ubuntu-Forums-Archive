---
title: "automating tasks with python?"
date: 2009-05-08
forum: Programming Talk
---

### Post by thehollow89 on 2009-05-08
Is it possible to create a python script to automate tasks in Ubuntu?  I'm bored and it'd give me something to do in python.

---

### Post by bapoumba on 2009-05-09
Moved to PT.

---

### Post by R Clemons on 2009-05-09
What is it you want to do?  You can execute commands from a python script if that's what you mean read this [http://groups.google.com/group/comp.lang.python/browse_thread/thread/ffdab847125f81b6?pli=1]("http://groups.google.com/group/comp.lang.python/browse_thread/thread/ffdab847125f81b6?pli=1")

---

### Post by ghostdog74 on 2009-05-09
> **R Clemons said:**
> What is it you want to do?  You can execute commands from a python script if that's what you mean read this [http://groups.google.com/group/comp.lang.python/browse_thread/thread/ffdab847125f81b6?pli=1]("http://groups.google.com/group/comp.lang.python/browse_thread/thread/ffdab847125f81b6?pli=1")

a rather funny way to go about executing shell commands. if OP needs to that ,i would recommend using the shell. Otherwise, using Python's modules is equivalent, eg using os.listdir() to do "ls" , using os.rename()  or shutil.move() to do "mv" etc

---

### Post by ad_267 on 2009-05-09
> **thehollow89 said:**
> Is it possible to create a python script to automate tasks in Ubuntu?  I'm bored and it'd give me something to do in python.

It most definitely is possible, what kind of task would you like to automate?

---

### Post by UbuKunubi on 2009-05-10
Search for XDOTOOL.
It is a command line tool, but seing as you can send calls to the command line in python, it is very easy to move the mouse, send keystrokes, and a lot more.

I personaly use use if I want to do something timeconsuming like ticking a lot of radio boxes on a webpage to delete unwanted emails.

If you want more help please post back :-)

---

