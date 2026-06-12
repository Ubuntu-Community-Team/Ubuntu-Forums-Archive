---
title: "python: ImportError: No module named whrandom"
date: 2007-09-26
forum: Programming Talk
---

### Post by BertP on 2007-09-26
Hi
  I am not trying to program.  I am just trying to follow along  on the installation-by-terminal-commands  example in the book "Ubuntu For Non-Geeks"

The book tells me to run the newly downloaded program,,,   but it doesn't run, instead it kicks out the following error messages.

Can anyone help?

-----
Traceback (most recent call last):
  File "LocalApps/pywings/pywings.py", line 86, in <module>
    import pywings_interface_tkinter
  File "/home/bert/LocalApps/pywings/pywings_interface_tkinter.py", line 42, in <module>
    import string, sys, os, copy, time, whrandom
ImportError: No module named whrandom

---

### Post by BertP on 2007-09-26
oops forgot to subscribe

---

### Post by pointone on 2007-09-26
According to [the official Python documentation]("http://www.python.org/doc/2.4/lib/module-whrandom.html"), whrandom is depreciated, and you should use the random module instead. My guess is that whrandom is not installed on your machine.

---

### Post by BertP on 2007-09-26
Thanks for the help!
Soooo  I am guessing  that you would advise that I  either learn Python or skip to the next section of the book ;)

---

### Post by pmasiar on 2007-09-27
what book do you use? Look like something targetting Python 1.5 or other long obsolete version.

Wiki in my sig has links to free online books, for beginners and experienced programmers.

---

