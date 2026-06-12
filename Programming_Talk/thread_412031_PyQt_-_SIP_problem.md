---
title: "PyQt - SIP problem"
date: 2007-04-17
forum: Programming Talk
---

### Post by kikapu on 2007-04-17
Hi to all,

i strangle to make a "copy" of my development environment that i have to an XP box so i can eventually focus on Linux and of course Ubuntu.
So, i am using 6.1. I installed Java1.5, Eclipse, PyDev, Python2.5 and last night i managed to install Qt Open Source Edition. (i said "managed" because my knowledge in Linux is very limited)

Then i was about to install PyQt (Python bindings of Qt) and i thought that when i finish and just run a .py (that contains Qt code) in Linux that i have made in WIndows, ok, it is time for my party to begin.

But PyQt refused to install because i had to install SIP at first.
Ok i said, i downloaded SIP and try to install it.

i write to the console the command: /usr/bin/python25 configure.py
which run just fine,
But when i run "make", a whole lot of errors come to me. Errors like:

siplib.c:3412: error: ‘PyExc_IndexError’ undeclared (first use in this function)
siplib.c: At top level:
siplib.c:3424: error: expected declaration specifiers or ‘...’ before ‘PyObject’
siplib.c: In function ‘createType’:
siplib.c:3426: error: ‘PyObject’ undeclared (first use in this function)


or

siplib.c:3412: error: ‘PyExc_IndexError’ undeclared (first use in this function)
siplib.c: At top level:
siplib.c:3424: error: expected declaration specifiers or ‘...’ before ‘PyObject’
siplib.c: In function ‘createType’:
siplib.c:3426: error: ‘PyObject’ undeclared (first use in this function)



Anyway, i am a small step behind for my dream to come true :popcorn: 
Does anyone knows about this problem and can help with it ??
If so, he just earned an invitation to my afterward party !

---

### Post by bep on 2007-04-21
You need the python-2.5-dev package (or something, look it up in Synaptic) to get this one to build.

---

### Post by pmasiar on 2007-04-21
I don't use Qt and cannot help you directly, but I can suggest possibly simpler way of solving "GUI for Python" problem.

Try SPE (Stani's Python Editor) and wxPython. SPE is *much* simpler than eclipse, but still pretty decent Python editor - and some things are missing in eclipse, like print with line numbers (can you believe that? bug reported since 2002), or background (paper) color for some syntax elements (impossible in eclipse). wx-based GUI looks "native" in every platform.

Of course if you require Qt and Eclipse and nothing else, it will not work. :-(

---

### Post by kikapu on 2007-04-22
> **bep said:**
> You need the python-2.5-dev package (or something, look it up in Synaptic) to get this one to build.

Xmmm..i found that already...the hard way! I have searhced the net and found nothing so a few days ago i sent an email to the SIP programmers and told me that.
I went to Synaptic, check the dev packages and now i enjoy a Wt/PyQt experience!Thanks anyway.

@pmasiar : i know about wxPython but i chose to work with Qt/PyQt/Eclipse/pydev. Thanks for the suggestion!

---

