---
title: "Forget IDLE in Python, Python Help Doesn't Work"
date: 2008-10-29
forum: Programming Talk
---

### Post by Mitchell Rumpf on 2008-10-29
I am new to Ubuntu Linux; I had installed it on an old desktop system that had Windows XP.  I found Python (2.5) after some searching.  I trained in programming languages in college and don't have any problem with the language.  I just can't the interpreter to work properly.  I can't seem to find IDLE. My help screens are not available because the path is wrong.  This version of Python appears to be in development and does not work correctly.  When I click on Python it opens the Terminal screen and I can run Python commands interactively.  I can save a program with the text editor.  I can also copy paste programs from Text Editor to the Terminal screen to get them to run, but that seems rather odd to run these.  There has got to be a better way.  Where is IDLE?  Where are the Help files?  How do you run/execute a program from the Text Editor?

---

### Post by slavik on 2008-10-29
have you tried saving your Python code into a file with a .py ending and then running it with 'python filename.py' in terminal?

as for IDLE ... it's a rather odd issue. I'm sure you'll get a reply

Also:
```

slavik@sgoltser:~$ python --version
Python 2.5.2

```

That is the stable version of Python, 3.0 is in development, so I am not sure what you mean by the phrase "Python is in development."

---

### Post by Mitchell Rumpf on 2008-10-29
Yes, all my Python test programs have been saved with ".py extension.  I am not sure of how to do a run command at this time.  I am trying to find that information for the Terminal program and the Text Editor.

---

### Post by ghostdog74 on 2008-10-29
if you can't find IDLE , then use a different editor. I don't use IDLE myself.

---

### Post by ratmandall on 2008-10-29
> **Mitchell Rumpf said:**
> Yes, all my Python test programs have been saved with ".py extension.  I am not sure of how to do a run command at this time.  I am trying to find that information for the Terminal program and the Text Editor.

```
cd /home/$USER/somedirectory

```

```
python filename.py

```
Is that what you want?

---

### Post by gomputor on 2008-10-29
IDLE doesn't come pre-installed in Ubuntu. You can install it either
from the synaptic or from the terminal with:
```
sudo apt-get install idle
```

---

### Post by pmasiar on 2008-10-29
IDLE is part of Python on Windows, but not on Linux. One of the reason is that IDLE in Linux has that old Tk GUI which looks so '90 :-) 

Install IDLE via Synaptic, or use any other editor. Just make sure that editor has "Python mode": recognizes keywords, replaces tabs with 4 spaces. Don't mix tabs and spaces in Python! See wiki in my sig for links for Python learners.

---

### Post by The Cog on 2008-10-29
Launch python apps from the command line like this:
**python filename.py**
or if you're in a different directory:
**python /pathname/filename.py**

I suggest you use gedit to edit the files (known is nautilus as Text editor), or personally I use geany but you will have to install this - it's in the repositories.

Not sure what you mean about the help files though. I know you can do something like:
> >>> import sys
>>> help(sys)
and get a load of help text ('q' to quit).

---

### Post by Mitchell Rumpf on 2008-10-29
:)   Thanks everyone.  Answers within a very short time.  Nothing like the amount of time I spent last night trying to get the programming language to work!

I will have to dig up a Linux book to find out more about the Linux accessories.  

An answer to your question slavik: My definition of "Python is in development" is to say Python doesn't run so well in this operating system and is full of bugs; it is meant for techies and not meant for the general public.  [My opinion only]

---

### Post by slavik on 2008-10-29
what do you mean by general public? "general public" doesn't understand the difference between a reboot and a power cycle.

---

### Post by Delever on 2008-10-29
What do you mean "doesn't run so well", i find that quite unusual.

---

### Post by pmasiar on 2008-10-29
> **Mitchell Rumpf said:**
> My definition of "Python is in development" is to say Python doesn't run so well in this operating system and is full of bugs; it is meant for techies and not meant for the general public.  [My opinion only]

Python runs excellent on Linux - Google production servers are managed by Python! It is typical case of PEBKAC error. 

General public is not interested in programming. If is interested, is not general public, and has to deal with the syntax. Even if it is 2008, we still do not have HAL as we were supposed in 2001, because when you learn just a little bit more, it is really hard problem.

Then, looking at your avatar: obviously, doh! ;-)

---

### Post by Canis familiaris on 2008-10-29
You should also give gedit with its integrated Python Console a shot. Also try geany.

---

### Post by The Cog on 2008-10-29
> An answer to your question slavik: My definition of "Python is in development" is to say Python doesn't run so well in this operating system and is full of bugs; it is meant for techies and not meant for the general public. [My opinion only]

I don't understand this assertion either. I wonder what on earth you mean - to me, python seems to work very well on Linux. I certainly feel more comfortable placing my python code on Linux than I do on Windows although that may be partly influenced by the fact that I am more familiar with Linux. Can you explain what you mean?

---

### Post by go_beep_yourself on 2008-11-22
gedit is weak. try VIM or GVIM. you can learn its basics by using vimtutor.

---

