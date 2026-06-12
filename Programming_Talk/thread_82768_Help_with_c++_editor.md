---
title: "Help with c++ editor"
date: 2005-10-27
forum: Programming Talk
---

### Post by nidron on 2005-10-27
Hi!
I'm learning c++ and thinking about making a GUI program. I wan't it to be able to work under both Ubuntu and Windows. What editor should I use? How to install it? What other things do I need to install to make it work?

/Thanks :p

---

### Post by thumper on 2005-10-27
You will be able to make a C++ program compilable on both windows and linux, but the same binary won't work on both.

You need to write your GUI code using one of the cross platform libraries like QT or gtk.

---

### Post by darth_vector on 2005-10-27
you can use any editor you like. in ubuntu you can use vi, vim, emacs, pico, red nedit, gedit, ... of these at least vim and nedit are installed by default.

in windows you can use notepad, wordpad, ...

---

### Post by toojays on 2005-10-27
I have found wxWidgets to be a good toolkit to use across Windows and GNU/Linux.

You can setup the mingw compiler on your Ubuntu box to make Windows binaries from the comfort of your GNU operating system. Alternatively you can install Emacs on Windows, and install Cygwin or MSYS to get the GNU tools on Windows. Or you can use a Free Windows IDE like Dev-C++.

---

### Post by JOKe on 2005-10-27
hello : 
wxWidget is VERYYYYYYYYYYYYYYYYYYYYYYYYYYYYY not easy :+)


if you want a easy to use good editor and if you want to make fast GUI apps wich work on windows and Linux 

use QT.
thats all
QT-designer i think was the ide.

---

### Post by nidron on 2005-10-27
Thanks all! I think I will check out QT... :smile:

---

