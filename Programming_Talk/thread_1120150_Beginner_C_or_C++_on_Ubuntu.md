---
title: "Beginner C or C++ on Ubuntu"
date: 2009-04-08
forum: Programming Talk
---

### Post by accLinux on 2009-04-08
I really want to learn c or c++, because a lot of programs for windows and Linux are written using c. Where is the best place to start, and what online tutorials and/or books would you recommend? I learn a lot working with programs others made, and would like to work with the tremulous source code. How do you compile it and where are the graphics at? Also, is Urban terror source code available? I've programmed in Visual Basic, also some Assembly and Basic using micro-controllers, the BS2 and Picaxe's. Any help or suggestions I'd really like.:p

---

### Post by Shpongle on 2009-04-08
ubuntu 's full cicle magazine teaches you c step by step in each isssue and web development. once you learn c the youll pick cpp up handy enough. i learned c last year in college and im currently finishing up my cpp course at the moment. also theres loads of c/cpp ebooks you can download in torrents, also theres plenty of help here in the forums

---

### Post by Firestom on 2009-04-08
On cplusplus you have a good beginners tutorial for C/C++: [http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")

Once you're done with this tutorial, you should look around with google to find other stuff you might have missed out and find tutorials with 3rd-party libraries (SDL, SFML, Qt, OpenGL) to practice what you have seen (always good to practice) and learn using them not by a tutorial, but by reading the API references. Then, as you start making projects, you'll look for other libraries and so on...

Then read a book on C/C++, doesn't care which one, but they explain more deeply how the language really works and the "why of the how" of some coding. Then well, it's up to you!

---

### Post by benj1 on 2009-04-08
> **Firestom said:**
> On cplusplus you have a good beginners tutorial for C/C++: [http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")

+1 for [www.cplusplus.com/doc/tutorial/]("www.cplusplus.com/doc/tutorial") 
thats where i started just remember:

```
apt-get install build-essential
```

or you won't be able to compile anything

---

### Post by benj1 on 2009-04-08
oh and 'thinking in c++' vol 1 & 2 by bruce eckle (google it).
are good follow ons, slightly more advanced but good as a reference

---

### Post by TheBuzzSaw on 2009-04-08
> **accLinux said:**
> I really want to learn c or c++, because a lot of programs for windows and Linux are written using c. Where is the best place to start, and what online tutorials and/or books would you recommend? I learn a lot working with programs others made, and would like to work with the tremulous source code. How do you compile it and where are the graphics at? Also, is Urban terror source code available? I've programmed in Visual Basic, also some Assembly and Basic using micro-controllers, the BS2 and Picaxe's. Any help or suggestions I'd really like.:p

Make sure you obtain the g++ package. ;)

---

### Post by soltanis on 2009-04-08
```

sudo apt-get install gcc g++ automake build-essential linux-kernel-headers

```

GEdit is a pretty good starting editor, works well with C or C++, as you move on you might want to go with a big IDE (Eclipse is good here) or with a lightweight editor + command line (this is the favored way).

Since you already know a little about programming and computers, it seems, I suggest you actually go pick up a copy of The C Programming Language/The C++ Programming Language, as those books are targeted at those who already understand basic programming concepts. The C text is actually very good, especially in the way it explains pointers which are just about the single most important concept in C (well, not single, but anyway).

---

### Post by benj1 on 2009-04-08
> **soltanis said:**
> ```

sudo apt-get install gcc g++ automake build-essential linux-kernel-headers

```

GEdit is a pretty good starting editor, works well with C or C++, as you move on you might want to go with a big IDE (Eclipse is good here) or with a lightweight editor + command line (this is the favored way).

Since you already know a little about programming and computers, it seems, I suggest you actually go pick up a copy of The C Programming Language/The C++ Programming Language, as those books are targeted at those who already understand basic programming concepts. The C text is actually very good, especially in the way it explains pointers which are just about the single most important concept in C (well, not single, but anyway).

build-essential depends on the rest of those anyway.
on a side note according to synaptic i don't have build essential, even though i know i installed it, and have been happily compiling for the past few months ????

---

### Post by accLinux on 2009-04-08
> **soltanis said:**
> ```

sudo apt-get install gcc g++ automake build-essential linux-kernel-headers

```

GEdit is a pretty good starting editor, works well with C or C++, as you move on you might want to go with a big IDE (Eclipse is good here) or with a lightweight editor + command line (this is the favored way).

Since you already know a little about programming and computers, it seems, I suggest you actually go pick up a copy of The C Programming Language/The C++ Programming Language, as those books are targeted at those who already understand basic programming concepts. The C text is actually very good, especially in the way it explains pointers which are just about the single most important concept in C (well, not single, but anyway).
When I try that code I get:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
g++ is already the newest version.
build-essential is already the newest version.
Package linux-kernel-headers is a virtual package provided by:
  linux-libc-dev 2.6.27-11.31
You should explicitly select one to install.
E: Package linux-kernel-headers has no installation candidate



I'd like to use an IDE for starting, than maybe just text editor + command line later.

---

### Post by FrankT-Qc on 2009-04-08
You also want to learn how a linker works... Wikipedia

---

### Post by slavik on 2009-04-08
There are two stickies at the top of this forum. They have links to good information. Please make sure to read them.

---

### Post by soltanis on 2009-04-08
Leave out the kernel headers, install eclipse. It's a good IDE. Netbeans is decent too though its mostly targeted at Java and its C/C++ support isnt all that good.

---

### Post by sqlpython on 2009-04-09
I have used Cforge and Eclipse for C++ IDE  programming.
I have switched to Netbeans 6.5. Netbeans is plenty flexible enough as it is powerful enough. The one big Plus for netbeans is as with Cforge and Eclipse, Netbeans is cross platform but more importantly it is more stable then the other two At This Time.

---

### Post by benj1 on 2009-04-09
> **sqlpython said:**
> I have used Cforge and Eclipse for C++ IDE  programming.
I have switched to Netbeans 6.5. Netbeans is plenty flexible enough as it is powerful enough. The one big Plus for netbeans is as with Cforge and Eclipse, Netbeans is cross platform but more importantly it is more stable then the other two At This Time.

geany, nice small an light IDE, havent had any problems with it

---

### Post by Firestom on 2009-04-09
When you're looking into a more powerful IDE, you should try Code::Blocks. It has powerful functions like it's debugger and allows you to control just about everything that is needed in your project.

---

### Post by Shpongle on 2009-04-09
i use gedit to write compile & run my progs , using scripts to compile and run

heres the link with the scripts

[http://ubuntuforums.org/showthread.php?t=1073795](http://ubuntuforums.org/showthread.php?t=1073795)

---

### Post by accLinux on 2009-04-09
Ok. Thanks Guys. I'll start learning C!!! Where is the full source code for tremulous, or other apps that I'd learn from??? And how do I modify them???

---

### Post by jpmelos on 2009-04-09
If you have the money available, I heavily recommend Deitel's books for both C and C++. Everything you need to know on the topics of semantics and standard libraries and code organization standards are there. For non-standard libraries, they have their own documentation.

---

### Post by accLinux on 2009-04-28
Thanks Guys. I'm currently using netbeans 6.5.1 as my c/c++ IDE.

---

### Post by Shpongle on 2009-04-30
good to hear! :D

---

### Post by Abu Sajid on 2009-05-01
> **benj1 said:**
> oh and 'thinking in c++' vol 1 & 2 by bruce eckle (google it).
are good follow ons, slightly more advanced but good as a reference

This book is great. It can be download on Bruce Eckel's site ([http://mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html)) along with the code.

---

### Post by wsonar on 2009-05-01
There's a ton of IDE's in the add/remove/programming

but I'm still more comfortable using gedit and g++
haven't got into anything big yet

I am going through teach yourselff c++ on linux it's been taking me quite a wihle but show's how to use G++ and later there is a weekk that is just specific to linux

---

