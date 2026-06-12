---
title: "New to Linux programming"
date: 2012-05-26
forum: Programming Talk
---

### Post by kirkkaf on 2012-05-26
Dear all,


I have just downloaded the new version of linux and it is truly a beautyfully designed OS.

I am interested in programming on the Linux OS, for both Linux & Windows what programming language do you recommend?

Thanks alot.

---

### Post by snowz on 2012-05-26
Python

[http://www.python.org/](http://www.python.org/)
[http://docs.python.org/](http://docs.python.org/)
[http://www.tutorialspoint.com/python/index.htm](http://www.tutorialspoint.com/python/index.htm)

---

### Post by kirkkaf on 2012-05-26
> **snowz said:**
> Python

[http://www.python.org/](http://www.python.org/)
[http://docs.python.org/](http://docs.python.org/)
[http://www.tutorialspoint.com/python/index.htm](http://www.tutorialspoint.com/python/index.htm)

Thank you for the extremely quick reply! Is there any reason you would recommend Python?

Thanks.

---

### Post by trent.josephsen on 2012-05-26
Everybody recommends Python. It has a simple, readable syntax that is easy to pick up. It accommodates a number of programming styles, and learning it requires very little prior knowledge. It is well-designed with all the control structures and data structures you need to know about as a beginner, but it also supports advanced constructs like lambdas and list comprehensions. Python is high-level compared to something like C, C++, or even Java, abstracting away much of the implementation detail which can bog down a new programmer. It has a large standard library so you can do a lot of stuff with it that other languages simply don't support out of the box. Finally, Python is installed on most Linuxes and many Unixes by default, available for every common platform (and some uncommon ones), and in fact a pretty popular choice for real projects (some high-profile examples being BitTorrent, Dropbox, Mercurial, and Portage) -- so you know learning Python isn't merely an academic exercise.

What's not to like? :D

---

### Post by snowz on 2012-05-26
> **trent.josephsen said:**
> everybody recommends python. It has a simple, readable syntax that is easy to pick up. It accommodates a number of programming styles, and learning it requires very little prior knowledge. It is well-designed with all the control structures and data structures you need to know about as a beginner, but it also supports advanced constructs like lambdas and list comprehensions. Python is high-level compared to something like c, c++, or even java, abstracting away much of the implementation detail which can bog down a new programmer. It has a large standard library so you can do a lot of stuff with it that other languages simply don't support out of the box. Finally, python is installed on most linuxes and many unixes by default, available for every common platform (and some uncommon ones), and in fact a pretty popular choice for real projects (some high-profile examples being bittorrent, dropbox, mercurial, and portage) -- so you know learning python isn't merely an academic exercise.

What's not to like? :d

+1 :)

---

### Post by CryptAck on 2012-05-26
> **trent.josephsen said:**
> Everybody recommends Python. It has a simple, readable syntax that is easy to pick up. It accommodates a number of programming styles, and learning it requires very little prior knowledge. It is well-designed with all the control structures and data structures you need to know about as a beginner, but it also supports advanced constructs like lambdas and list comprehensions. Python is high-level compared to something like C, C++, or even Java, abstracting away much of the implementation detail which can bog down a new programmer. It has a large standard library so you can do a lot of stuff with it that other languages simply don't support out of the box. Finally, Python is installed on most Linuxes and many Unixes by default, available for every common platform (and some uncommon ones), and in fact a pretty popular choice for real projects (some high-profile examples being BitTorrent, Dropbox, Mercurial, and Portage) -- so you know learning Python isn't merely an academic exercise.

What's not to like? :D

I agree that it's a great language.

Some may find Google's Python Course helpful: [http://code.google.com/edu/languages/google-python-class/](http://code.google.com/edu/languages/google-python-class/)

The *only* thing not to like that comes to mind right now is speed. But for most tasks this shouldn't be a problem. :)

[http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python3&lang2=gcc](http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python3&lang2=gcc)

---

### Post by kostkon on 2012-05-26
You can also check [this site]("http://developer.ubuntu.com/"), specific to Ubuntu.

---

### Post by gnusci on 2012-05-26
Python or Java.

---

### Post by na5h on 2012-05-28
It also depends on what types of applications you intend to develop.
Java is quite nice if you're into object-oriented programming and portability...and if you wish to develop Android apps!

---

### Post by kirkkaf on 2012-05-28
> **kostkon said:**
> You can also check [this site]("http://developer.ubuntu.com/"), specific to Ubuntu.

This link is great learning resource, thanks alot.

---

### Post by trent.josephsen on 2012-05-28
The thing I don't like about Java is that it's designed for enterprise-scale projects. When you choose a language for your 1,000,000-line open source project that will be worked on by dozens or hundreds of people in-house and attract international attention, you evaluate languages with an eye towards mitigating the damage that *mediocre* programmers can do to your codebase. When you're learning on your own, you want something with a small core and consistent semantics. Java's just big, clunky and sometimes confusing.

Another way to put this is that the *way* you program when you're learning to program is *not* the way Java is designed to be used. Sure, you *can* write a simple bookkeeping program or something in Java, but the syntactic and semantic features of Java that are supposed to help will probably only get in the way. Python, in spite of its mantra "There should be one-- and preferably only one --obvious way to do it", is quite tolerant of naive programming, and will likewise require less refactoring if you later rework the design.

And that's why I never recommend Java to new programmers. Just my 2 cents.

---

### Post by Ecomarsho on 2012-05-28
Hm! what's not to like?
 
I have often thought of taking some time to learn a better language for programs myself.
It would be kinda handy if I can translate some of my JavaScript progs into a free-standing programming language, and so to make progs that will run on any computer.
 
There seems to be alot to learn in Python, but maybe that's just my impression.  I tried a few progs in C and, with the help of library books and my old Solaris manual, got it to echo "Hello World", but that is very far from what I'd call a proper program.
 
I was hoping to get a GUI by downloading alot of JDK and associated packages, but now they seem to have just disappeared into my computer, with no GUI, and no observable effect on the computer (running Ubuntu 10.04).
 
The fastest way to learn enough, I was thinking, should be to get some prog with a GUI which also displays code, and work to and fro between the two with some books etc for reference.
 
But now what?

---

