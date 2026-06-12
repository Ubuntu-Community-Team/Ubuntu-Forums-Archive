---
title: "Good C/C++ setup for beginners..."
date: 2005-11-01
forum: Programming Talk
---

### Post by Noah0504 on 2005-11-01
Okay, so I'm in the process of removing Windows from my life.  Don't get me wrong, I like Windows, and it has been pretty good to me over the years, I just think Linux is the way to go.

Anyway, a few years back I bought C for Dummies and tried to teach myself to program.  Well, let's just say I eventually gave up and moved onto BASIC, where I had more luck.  Now, I want to go back and learn C++.  I was wondering what a good setup would be for Ubuntu.  I'm sure there are already several compilers available, but I want to know about a good IDE to use and how to go about setting everything up.

Thanks.

---

### Post by 23meg on 2005-11-01
You should look into Anjuta and Eclipse. If you use KDE or wouldn't mind installing the KDE libraries you may also want to look into KDevelop.

---

### Post by Susana on 2005-11-01
gcc/g++ + gdb + eclipse + cdt plugin + valgrind + gprof

If you know how to use gdb and vim/emacs than you probably don't need eclipse, if you don't eclipse has a debuger that runs on top of gdb and makes it quite simple (if you never used a debuger USE IT!).

valgrind will help you with memory issues, it tells you when you are writing outside the memory you allocated, how many mallocs/frees you made, etc

gprof tells you where you should optimize you programs, the last time i searched wasn't in ubuntu repos, but if you look for profiling tools there may be others that are good as well

---

### Post by thumper on 2005-11-01
I'd say it is best to start with a simple editor (pick one of your choice) and the command line.

Move on to an IDE once you understand the basics of compiling and makefiles.

Otherwise you just end up knowing the IDE and moving to something else becomes a real pain in the arse.

---

### Post by Susana on 2005-11-01
[QUOTE=thumper]I'd say it is best to start with a simple editor (pick one of your choice) and the command line.
[/QUOTE]

Presuming you will know where your mistakes are right away is a mistake by itself. Presuming you won't make mistakes is even a greater mistake. Seeing people fill their code with printfs for debuging is just the saddest thing (they tend to hit their heads against a wall very quickly :p).

So, if you choose to start with only an editor and command line i'd recommend at least gdb+ddd and valgrind.

I don't think you should learn gdb alone right now because C++ is already hard enough and if you put extra effort to learn gdb and a good editor you won't concentrate enough on the language.

PS: i think that eclipse also needs you to make a makefile in order to compile C/C++ but i'm not sure

---

### Post by ctcecil on 2005-11-01
I also agree, with experiance, starting with the VIM or gedit editors will be the best way to go. It teaches you good ethics and helps you understand what your doing a whole lot better. After that you can just use simple gcc to compile it.

g++ myhelloworld.cpp -o myhelloworld

(it's good to start off with tips)

---

### Post by DJ_Max on 2005-11-01
[QUOTE=ctcecil]I also agree, with experiance, starting with the VIM or gedit editors will be the best way to go. It teaches you good ethics and helps you understand what your doing a whole lot better. After that you can just use simple gcc to compile it.

g++ myhelloworld.cpp -o myhelloworld

(it's good to start off with tips)[/QUOTE]
Ditto. Besides, as a beginner, an IDE will just get in the way, as I doubt you'll be writting 1,000 line scripts starting out.

---

