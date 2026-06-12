---
title: "Problem compiling C++ code in console."
date: 2013-01-21
forum: New to Ubuntu
---

### Post by nevthinking on 2013-01-21
Hi!
I'm a newbie in Ubuntu and I'm trying to run my C++ code using the console. I used the header file conio.h like I did when I used turbo C++ IDE in Windows, and I ran the code in console using g++ filename.cpp. I have installed the build-essentials package previously, but still I get the message that "conio.h file : No such file or directory".
Please help.

---

### Post by Tank Jr on 2013-01-21
Are you sure you need that header?
It may be that some headers are particular to Windows/Turbo C.
See what functions you need from there.

I use C++ on Linux and don't require the  conio.h file

---

### Post by Nr90 on 2013-01-21
It's not a linux library.
Have a look here:
[http://stackoverflow.com/questions/8792317/why-cant-i-find-conio-h-on-linux](http://stackoverflow.com/questions/8792317/why-cant-i-find-conio-h-on-linux)

---

### Post by nevthinking on 2013-01-21
> **Tank Jr said:**
> Are you sure you need that header?
It may be that some headers are particular to Windows/Turbo C.
See what functions you need from there.

I use C++ on Linux and don't require the  conio.h file
Thanks, I had no idea that the header files will differ for C in Ubuntu and Windows.

---

### Post by nevthinking on 2013-01-21
How do I install the ncurses library? I ran a search in the Synaptic package manager and I received numerous results, which is quite confusing..

---

### Post by Warren Hill on 2013-01-21
conio is a DOS/Windows header file not part of the unix standard library.

Take a look here for possible replacements

[http://stackoverflow.com/questions/3627975/replacement-for-conio-h-in-linux](http://stackoverflow.com/questions/3627975/replacement-for-conio-h-in-linux)

If you are still struggling then you can always post code here and we can take a look.

---

### Post by squakie on 2013-01-21
If you are going to continue to use C and/or C++, I would highly recommend you not waste time with ncurses (we used curses on Unix boxes in the early 90's) and instead try something like GTK for controlling a true GUI.  You don't need to build pseudo GUI apps using the old terminal sequences any more nor run them in a terminal.  GTK also allows cross-platform development as there is a GTK package for Windows as well.

I know there are other tools for doing GUI's as well - QT, Python, Java, etc..  Since Java and Python are different languages from C/C++,  you would have to decide if you want to tackle a new language (though they are structured OO languages like C++).

I done some cross platform development (same program source compiles and runs on both Linux or Windows) using GTK myself.  It's actually fairly simple if you just install the devhelp package as well so you can look up the calls.

---

