---
title: "programming in linux"
date: 2010-06-18
forum: Programming Talk
---

### Post by maroofi on 2010-06-18
hi 
as you all know i am new in ubuntu and i have installed it 8 hours ago and working hard ...
i use to write c/c++ code in windows using MinGW and gcc compiler and now i wanna know if i have gcc in ubuntu as default or  i have to install it and if so where can i get it and how to install it ? 
sorry guys for these silly Q.maybe it is soon to do such a thing.(you can tell me if it is.)
(i know just a few linux command line like ls cd cp mv ...).

sorry for my poor english.

---

### Post by jmore9 on 2010-06-18
Look in the repos for most of the programming stuff.

---

### Post by MontelEdwards on 2010-06-18
GCC is installed by defualt.
You should probably still install 'build-essential' though.

---

### Post by ThesaurusRex on 2010-06-18
Test for gcc:```
gcc --version
```

---

### Post by Daniel Jorge on 2010-06-18
I use ubuntu for C programing.
Just use gcc and some text editor.
If you're a newbie use gedit or nano, if you have some time to spend learn to use vim - command line super powerfull text editor (command line integration, etc etc) - or emacs.

This should do the trick:
```
gcc -ansi -pedantic -Wall -o yourprojectname yourproject.c
```

Or if you have some more time just make a makefile.

---

### Post by QIII on 2010-06-18
If you are planning to just "write some code" for simple applications, do as suggested above -- use any text editor you like (Emacs is great because there is some configuration you can do) and gcc.

When I was a stubborn purist, that's what I did.

The world has changed.  If you want to do anything professionally, I would recommend an IDE like eclipse or Netbeans.  If you want to, you can use MonoDevelop to create cross-platform applications compatible with .NET.

---

### Post by maroofi on 2010-06-21
thx i got it but if i want to make gui in windows i can use windows API or resources(Dialog base) but how can i make gui in linux-ubuntu?

---

### Post by ad_267 on 2010-06-21
You will need to install build-essential to compile anything with GCC.

You can use either GTK or Qt to write a GUI application for Linux. There are other options but those are the two most popular. GTK is what most Gnome applications use and Qt is what KDE applications use, but GTK and Qt applications can both be used on KDE or Gnome. My preference would be to use Qt but it's up to you really. Qt is probably better suited to cross platform apps that will need to run on Windows and OSX too.

---

### Post by maroofi on 2010-06-21
thank you for reply and is this what you mean?
[http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp](http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp)

---

### Post by simeon87 on 2010-06-21
> **ad_267 said:**
> Qt is probably better suited to cross platform apps that will need to run on Windows and OSX too.

Why is that so? Gtk also runs on Windows and OS X.

---

### Post by Praveen30 on 2010-06-21
> **maroofi said:**
> hi 
as you all know i am new in ubuntu and i have installed it 8 hours ago and working hard ...
i use to write c/c++ code in windows using MinGW and gcc compiler and now i wanna know if i have gcc in ubuntu as default or i have to install it and if so where can i get it and how to install it ? 
sorry guys for these silly Q.maybe it is soon to do such a thing.(you can tell me if it is.)
(i know just a few linux command line like ls cd cp mv ...).
 
sorry for my poor english.
 
Don't worry. It is good to be a newbie because there is a plethora of knowledge waiting for you.You can learn anything at anytime,there is no process.GCC is installed by default in the ubuntu.Now how to run it?just go here--
 
 [http://fullcirclemagazine.org/issue-17/](http://fullcirclemagazine.org/issue-17/)
 
This is free to download and in pdf format and you can learn a lot of things from  this.

---

### Post by maroofi on 2010-06-21
thanks...it realy helps.

---

### Post by Barrucadu on 2010-06-21
> **simeon87 said:**
> Why is that so? Gtk also runs on Windows and OS X.

IIRC Qt uses the native toolkit to draw widgets where possible, so the program ends up interfacing better with the rest of the system.

I could be completely wrong about that, though.

---

### Post by bruno9779 on 2010-06-21
@ OP

Qt and GTK are in the repos.

Have a look at the development section of the Ubuntu Software Center

---

