---
title: "Programmer new to Ubuntu"
date: 2007-08-31
forum: Programming Talk
---

### Post by subferno on 2007-08-31
I am a software developer on Windows. I code in java through Eclipse/RAD. I use VB.NET in Visual Studio once in awhile.I am a programmer for two years and I mainly code business logic and algorithms. I don't create the front end or GUI. Therefore I am not familiar with what tools correlate between Windows and Ubuntu. 

My questions:
1) Is there a primary/popular programming  language used for applications in Ubuntu?

2) Visual Studio or VB.Net has an IDE that allows drag and drop of components to develop graphical user interfaces. Same applies to Java for NetBeans or Eclipse via Swing(?). Is there such an IDE for Ubuntu?

Thanks

---

### Post by slavik on 2007-08-31
1. No, but the favorites seem to be C and Python. There are many others that are used (Perl, C++, Java, C#, Tcl to name a few)

2. Glade (strictly GUI design) Anjuta 2.x and Kdevelop have built in GUI builders also. (Anjuta uses Glade as a module, don't know much about Kdevelop)

---

### Post by pmasiar on 2007-09-01
> **subferno said:**
> 1) Is there a primary/popular programming  language used for applications in Ubuntu?

no, there are no "preferred" languages for Linux. But of course most project prefer one language. IIRC Qt is in C++, but Gnome in C, etc.

Ubuntu uses Python for all internal development, but integrates 10-20k "upstream" projects developed in whatever language project prefers.

For libraries and "low-level" (fuzzy term BTW)  system tools, C is preferred.

When developing applications, many people prefer productivity gain resulting from dynamically typed language, like Python, Ruby, Perl. Unix philosophy is "set of smart sharp tools used together" instead of one single universal solution. This paradigm is used in all areas, including programming. Small sharp tools to accomplish each task - and if it is not sharp enough, you have sources to make it better. 

BTW if you insist on Java, you can use Eclipse on Linux too. But until you tried dynamic language you don't know what are you missing. And java is deliberately incompatible with all Linux tools, stands as separate world (or platform). Exactly like C#.NET.

Warning: **after** you try it, Java will feel like a big, dull tool. :-)

> 2) Visual Studio or VB.Net has an IDE that allows drag and drop of components to develop graphical user interfaces. Same applies to Java for NetBeans or Eclipse via Swing(?). Is there such an IDE for Ubuntu?

IDE - depends obviously for which language. Python has couple: SPE, Eric, and the simple IDLE are free, about half a dozen (Komodo, WingWare etc) are commercial. But you will find that many programmers just use Emacs or Vim: because they are optimized after decades of constant use, and customizable to handle every new language you will ever need, way before there are IDEs for it.

So don't be surprised, when you ask for "silver bullet", we will tell you: it depends what you want to do... :-)

So, tell us: what you want to do?

---

### Post by subferno on 2007-09-01
Thanks for the responses.

Like I said in my initial post, I have been programming business logic for years and I would like to branch out and create something useful for my own daily tasks. I am sure there are already programs written for what I want. I just feel like a newbie programmer who wants to do fun creative things :) and get a better understanding of how Ubuntu works.

---

### Post by pmasiar on 2007-09-01
> **subferno said:**
> get a better understanding of how Ubuntu works.

Ubuntu is just yet another GNU/Linux distribution (the best one of course - but distro). It is not a single product.

Big part of Ubuntu is integrating and releasing many projects done "upstream", most of them coming via debian. If you want to learn generic GNU/Linux, pick a project you like, say FreeCiv, Midnight Commander, KDE, and start hacking.

If you want to learn how Ubuntu is different from other distributions, you can join developer team (google ubuntu MOTU) and help with packaging. They have orientation and training for new recruits after each release.

---

### Post by ashvala on 2007-09-01
Well... Anjunta is a great software....
Just install and see.... It rocks
(if you use gnome) for KDE
Kdevolop

---

### Post by daveshields on 2007-09-01
In a word, Python.

Yes, Java is great for the enterprise, but you'll have fun learning Python, lots more fun that you had with Java.

I spent a few years whilst at IBM Research working on Java, mostly  with Philippe Charles  to design and implement Jikes, a javac replacement that wound up being IBM's first open-source project. You can even take it for a spin on Ubuntu:

 $ apt-get install jikes

Jikes is not up to date with the latest  language changes, but it is *damn* fast. (By the way, the Java parser in Eclipse uses the JikesPG parser-generator  that was released as part of the Jikes project.)

No apt-get is needed for Python. It's ready and waiting.

---

### Post by daveshields on 2007-09-01
Subferno,

By the way, as a fellow software developer (40+ years and counting) welcome to Linux-land, courtesy of Ubuntu.

I must admit I envy you, as you are about to encounter programming at the highest level for the first time . That's what open-source is all about-- it's just the scientific model applied to programming.

Have fun. I know you will.

---

