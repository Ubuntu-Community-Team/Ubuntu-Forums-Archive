---
title: "Advice on how to develop system programming skills"
date: 2006-08-20
forum: Programming Talk
---

### Post by pez on 2006-08-20
Hi fellow Ubuntu users,

I'm looking to develop system programming skills. My aim is to be proeficient to contribute code to the Ubuntu development project and Linux kernel.

I am learning C at the moment but I was wondering what books or steps I should take next to reach my goal?

---

### Post by baldy1324 on 2006-08-20
WOW want to contribute to kernel :). well what i would recommend is not to try to contribute to kernel b/c that uses code that interacts with your hardware and is not easy at all - and very picky about code. as with helping out with ubuntu
ubuntu has people called package maintainers that maintain packages of software and make debian packages out of the origional author (upstream author)'s code. sometimes there are packaging errors done by the maintainers which cause bugs and sometimes every distro has the same bugs b/c the problem is in the upstream source. if you wanted to submit code you would be submitting to upstream authors (since they are the only ones who edit and control what is in the actualy code (not ubuntu). and i love gnome (hate kde's overload) but don't learn C if you are knew to programming (it's a step BACKWORDS). my recommendation learn something easy and modern-python is arguably the easiest programmming language so drop c and learn python. also in linux if you want to make graphical programs you have to learn gui toolkits (interact with code to create graphical interfaces). i think the easiest is wxPython which is the python bindings for wxWidgets (one of the most easy but complete gui toolkits). and a lot of third-party gnome programs (alacarte menu editor and lots of others) are starting to use python.
this may sound like over kill but it is easy, do three things
1. research python tutorial - [http://docs.python.org/tut/](http://docs.python.org/tut/)
2. wxPython to make guis in python - [http://wiki.wxpython.org/index.cgi/How_to_Learn_wxPython](http://wiki.wxpython.org/index.cgi/How_to_Learn_wxPython)
3. DROP C!!!

if you think im crazy i have spent 2 years programming in c++ and abandoned it for python and wxPython and have created some nifty little programs with it.
hope that helped.

---

### Post by Revert on 2006-08-20
My thoughts would be that you need focus a lot on learning how the kernel works before you attempt to contribute to it.  To this end, you might look into the book Understanding the Linux Kernel by O'reilly.  There're probably a number of tutorials and information sites online, too.

Note that I'm interested in kernel hacking, but haven't ever done any myself, so take what I say with a grain of salt. ;)

---

### Post by LordHunter317 on 2006-08-20
If you have no previous kernel-level experience, then you need to learn the following things:[list][*]Some dialect of assembly.  Find a good text that focuses on that.[*]Operating systems from an academic perspective.  Get a textbook on that.[*]Then, worry about practical contributions.[/list]If your path is specific hardware drivers, then you can skip step 2.

---

### Post by kwalo on 2006-08-23
[http://www.ubuntuforums.org/showthread.php?t=8682](http://www.ubuntuforums.org/showthread.php?t=8682)
There you'll find whole lot of references.

The thread is long, so I'll repeat myself:"The C Programming Language" by B.W. Kerringhan & D.M.Ritchie is the book you're looking for.

---

### Post by LordHunter317 on 2006-08-23
Not really, no.

Knowledge of C, while important, isn't the most critical thing.

---

