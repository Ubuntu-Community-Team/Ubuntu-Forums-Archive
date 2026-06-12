---
title: "Difference between programming in Windows and Ubuntu"
date: 2012-09-17
forum: Programming Talk
---

### Post by EnexOD on 2012-09-17
Hey one question, this might sound dumb but...:

What's the main difference between programming the Windows and in Ubuntu? In university, is it necessary to program in Ubuntu? I currently have windows and was thinking of switching but I would need to dl everything again ;;

Thanks!

---

### Post by gnometorule on 2012-09-17
The core of languages is the same. Where you encounter differences is in how i/o is treated, and how API calls are executed. Assume you learn C using K/R. Then on this level - covering all of ANSI C but not C99 - 7 out of 8 chapters pretty much translate 1-1, except things such as that the keystroke to indicate  end of file is different, and that MS VS has a steeper learning curve than gcc (what you'd probably use in Ubuntu), and needs you to add some non-standard commands so you can actually input and output. Universities are unlikely to impose Linux on you, but the 'cool kids' probably at least dual boot into it. To simply learn or do homework, both systems should be fine. Ubuntu is free, leaner, supports you with free software, but if you prefer W7, that should be fine too.

---

### Post by EnexOD on 2012-09-17
Most things like API, K/R, gcc, etc. doesn't make sense but the rest I can comprehend, thanks for the insight!

---

### Post by gnometorule on 2012-09-17
API=Application Programming Interface. When you ask your OS to execute a task, it expects you to ask in a form that it understands. This form, obviously, differs between Windows and Ubuntu.

K/R: Kernighan/Ritchie. Standard textbook to learn C, by the original author of C (and still very good).

gcc: GNU compiler collection. C is a compiled language. This means that you write your code in C, then use a program (on Ubuntu, typically gcc; on W7, typically MS Visual Studio) to compile the program for you - which means, what you have written in C is internally translated into a machine language set of byte codes the computer understands. This is what in Windows would be an executable, which you have probably seen.

Good luck!

---

### Post by EnexOD on 2012-09-18
Man.... so much information I don't know.
I've been programming for a few months now and only Python and same Java.

A long road for me in programming, looking forward for it
Hopefully looking for a job after university won't be hard

---

### Post by ibuclaw on 2012-09-18
Just bccause you're on Linux, don't mean you have to learn C. :)


Python is well supported and cross-platform. So you may find that you don't need to worry too much about differences when coding in Python.

The top of my list would be IDEs and Editors.  Typically in Windows, you'd use an IDE of some sort to code. Failing that, Notepad++.   In Linux, whilst there are some IDEs out there (Codeblocks, Geany), most people tend to use a general purpose Text Editor instead (given that syntax highlighting is supported):

- Gedit. (For people in GUI land).
- Emacs. (But real programmers don't use this).
- Vim.  (Real programmers use this).
- Nano. (Baby programmers use this).
- Butterflies. (Also found in EMACS - C-x M-c M-butterflies).

---

### Post by llanitedave on 2012-09-18
Python itself is pretty seamlessly cross-platform.  But there are some minor but tricky differences between Windows and Linux in tools such as wxPython for graphical user interfaces.  More than once I've had code that worked perfectly in Ubuntu but didn't display properly in Windows, until I mastered some other arcane commands.

---

### Post by Glencore on 2012-09-19
> **EnexOD said:**
>  only **Python **

In terms of a RAD enviroment:

Windows has Visual Studio. Ubuntu has 'quickly'.

Quickly makes it much easier to program in python code and use Glade to quickly biuld GUI front ends using the GTK+ toolkit, much like Visual Studio in that sense.

[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/) 

Nice place to start imo.

---

### Post by Tony Flury on 2012-09-19
> **ibuclaw said:**
> Just bccause you're on Linux, don't mean you have to learn C. :)


Python is well supported and cross-platform. So you may find that you don't need to worry too much about differences when coding in Python.

The top of my list would be IDEs and Editors.  Typically in Windows, you'd use an IDE of some sort to code. Failing that, Notepad++.   In Linux, whilst there are some IDEs out there (Codeblocks, Geany), most people tend to use a general purpose Text Editor instead (given that syntax highlighting is supported):

- Gedit. (For people in GUI land).
- Emacs. (But real programmers don't use this).
- Vim.  (Real programmers use this).
- Nano. (Baby programmers use this).
- Butterflies. (Also found in EMACS - C-x M-c M-butterflies).

I would add Kate to the list - althought strictly speaking it is a KDE application, I use it on Gnome. It has could multi-file project support (via sessions), flexible syntax highlighting, code folding (although occassionaly it gets it wrong on python), split screen editing etc etc.

---

### Post by snip3r8 on 2012-09-21
The difference between swearing and not swearing all day.(Not responding)

---

