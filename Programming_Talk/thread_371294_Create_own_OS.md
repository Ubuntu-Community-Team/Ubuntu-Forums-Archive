---
title: "Create own OS"
date: 2007-02-26
forum: Programming Talk
---

### Post by carteris21 on 2007-02-26
Hello, 
    may someone has or know where could be found examples of simple OS(it could be wrote in various languages C\C++, Java...). It's my University task :). Thanks.

---

### Post by Wybiral on 2007-02-26
Look at post #6 here: [http://ubuntuforums.org/showthread.php?t=364974](http://ubuntuforums.org/showthread.php?t=364974)

You wont be able to use Java... And probably not much C++ either, C and assembly will probably be all you'll need.

EDIT:

Oh, looks like you need source code for an existing OS? Guess what... You're using it!!! (Linux is open source)

---

### Post by lnostdal on 2007-02-26
Here's one written in Common Lisp: [http://common-lisp.net/project/movitz/](http://common-lisp.net/project/movitz/) (hey cool; another Norwegian Lisper ... :) )

Note that while assembly is needed, an OS is more than just the stuff that must be written in assembly. If someone asked I'd say "Linux is written in C" even if they use both C and asm .. in the same sense Movitz is written in Common Lisp.

---

### Post by Tenicus on 2007-02-26
It depends on what you mean.
There is LFS(Linux from Scratch)

---

### Post by justin whitaker on 2007-02-26
> **carteris21 said:**
> Hello, 
    may someone has or know where could be found examples of simple OS(it could be wrote in various languages C\C++, Java...). It's my University task :). Thanks.

Great sources for alternative and research OS projects are:

[OSNews]("http://www.osnews.com/index.php")
[OSDEV Community]("http://www.osdcom.info/component/option,com_frontpage/Itemid,1/")
[FreshMeat]("http://freshmeat.net/browse/144/")

---

### Post by j_g on 2007-02-26
Here's a list of numerous operating systems with links to appropriate web pages. Some have source, some don't. In particular, you may be interested in looking at Minix. It seems to be rather functional, but not nearly the codebase size of Linux.

[http://en.wikipedia.org/wiki/List_of_operating_systems](http://en.wikipedia.org/wiki/List_of_operating_systems)

---

### Post by Wybiral on 2007-02-26
Oh, if size is a matter, a minute or so on google can lead you to a number of "Hello world!" operating systems. Or does it have to have a certain level of functionality?

---

### Post by lloyd mcclendon on 2007-02-26
you may want to take a look at nachos [http://www.cs.washington.edu/homes/tom/nachos/](http://www.cs.washington.edu/homes/tom/nachos/) , it's pretty academic.  when i was in college we had to fill in the missing pieces and write some extensions.  i would say that was more rewarding than writing an entire OS from scratch

---

### Post by daniel of sarnia on 2007-02-26
Someone told me that if you want to have a simple OS to understand how OS's are made with something you can hack on and improve, just start playing with Linux kernel .01 or .1 I forget which one he said. It's only about 10 000 lines of code, I'm told. 

I'm pretty sure it's all, or mostly in C.

---

### Post by pmasiar on 2007-02-27
[http://en.wikipedia.org/wiki/Minix](http://en.wikipedia.org/wiki/Minix) is used for years for teaching how (unix-like) OS works, and was "father" of Linux. It is open source (BSD) and books are available explaining it.

---

### Post by carteris21 on 2007-02-27
Thanks :). Would be quite much work.

---

### Post by clouserw on 2007-02-28
One of my classes used [NachOS]("http://en.wikipedia.org/wiki/Not_Another_Completely_Heuristic_Operating_System").  It's written in java.

---

