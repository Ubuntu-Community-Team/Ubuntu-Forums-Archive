---
title: "Want to make a Linux Distro Downloading program. Need advice on how to do it."
date: 2006-08-05
forum: Programming Talk
---

### Post by RussianVodka on 2006-08-05
I want to make a program kind of like Steam (The program Valve uses to distribute their games).

What my program will do, is give you a list (and description) of all Linux distros, which you'll be able to download right through the program.

I'm not sure who'll actualy use it, but it's something I want to make.

So, here's my problem:

I've done similar things in the past (not too similar, but some of the basic components were similar enough so I have an idea of what I'm doing) but they've all been text based command prompt programs.

Because I know that I will be able to make a text based version of this without too many problems, it kind of makes it uninteresting.

What I want to do is make a GUI version, with cool buttons and scroll bars!

Problem is, that outside of languages like VB (which can't be used on Linux) and Gambas, I've never been able to make graphical applications. And in those languages I've never been able to make successful networking applications.

So, with C++ being my strongest language, I wan't to learn to make GUI's with it. I've tried learning the Windows API before, but I failed. So I guess I'll try to learn how to program with X Windows...

Another alternative, is to write the programs that will do all the networking things (downloading, updating, etc.)in C++, and then call them from inside the VB program.

But Gambas, sorry to say, sucks. And VB programs can't be used under Linux.

So, what do you think I should do?
Maybe I should learn a new language for this sort of thing?

Languages I know and may be able to use:
VB
C++
Java - Very Little
Shell/Bash (who knows, they may come in handy)

---

### Post by moma on 2006-08-05
wxWidgets and C++:
[http://www.wxwidgets.org/]("http://www.wxwidgets.org/")

But may I suggest Python + wxPython for GUI programming.
[http://www.wxpython.org/screenshots.php]("http://www.wxpython.org/screenshots.php")
+ [http://www.python.org]("http://www.python.org")

Try to run the wxPython samples. Search for evt. missing packages 
$ apt-cache search wxpython

---

### Post by UbuWu on 2006-08-06
Easiest way if you don't need any advanced functionality:
Bash script + zenity

---

### Post by RussianVodka on 2006-08-06
Yeah, I kind of need some advanced things... So I guess I'll be learning python.

But the Zenity thing will come in handy. I guess I'll be able to make system calls from python the same way I can from C++.

But does anyone else have any ideas for what to do?

---

