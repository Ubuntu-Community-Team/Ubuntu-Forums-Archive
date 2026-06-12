---
title: "Cant run .py files in terminal."
date: 2010-12-01
forum: Programming Talk
---

### Post by Zavie A. on 2010-12-01
So, I started messing around with Python 2.6.5 the other day, to see if I could teach myself how to use it. It seemed to be going pretty well until I got to this part. 

I wrote a simple script:

> >>> a=2
>>> b=3
>>> a=2*a
>>> b=3*b
>>> c=a+b
>>> print c

Then I attempt to run it in the terminal and this happens:

> zavire@zavire-laptop:~$ cd /home/zavire/Programming/PracticeScripts
zavire@zavire-laptop:~/Programming/PracticeScripts$ python newscript.py
  File "newscript.py", line 1
    >>> a=2
     ^
SyntaxError: invalid syntax
zavire@zavire-laptop:~/Programming/PracticeScripts$ 

Can anyone tell me what I'm doing wrong? :/

---

### Post by Arndt on 2010-12-01
> **Zavie A. said:**
> So, I started messing around with Python 2.6.5 the other day, to see if I could teach myself how to use it. It seemed to be going pretty well until I got to this part. 

I wrote a simple script:



Then I attempt to run it in the terminal and this happens:



Can anyone tell me what I'm doing wrong? :/

You should not enter >>> as input to Python. You don't do that in the interactive case either - it's Python saying that to you, to show it's expecting input.

So just remove all the >>> in the file.

---

### Post by Zavie A. on 2010-12-01
Beauuuttyyyy.
Thanks man!

One more question. IDLE seems to save those '>>>' things into my file automatically, so I had to go back with a text editor and remove them manually.
Is there any way of saving the .py file so those don't appear? 
or do I have to remove them manually every time? :/

---

### Post by Vaphell on 2010-12-01
well, you can simply edit the file with gedit all the time and not bother with idle?
you don't have to use anything special to run it - mark it as an executable, add shebang at the top (#!/usr/bin/env python) and run it from terminal with ./filename.py

---

### Post by oldfred on 2010-12-01
I just use geany, which you can install from synaptic.

You input a file, once saved as a .py it knows it is python and you can run it right there. You do have to set some default parameters to get it to know you are editing python like using spaces not tabs.

---

