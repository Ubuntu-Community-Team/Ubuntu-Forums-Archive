---
title: "IDE with /usr/include/c++ autocomplete"
date: 2008-05-29
forum: Programming Talk
---

### Post by Redscare on 2008-05-29
This is a relatively simple question, and it is mainly one of aesthetics, but is there an IDE that can provide autocomplete the files found under /usr/include/c++, such as iostream, apart from the IDE Eclipse? So if i go ```
std::c
``` and press control+enter I get options such as cin and cout, and if I type in ```
std::cin.
``` I get options such as get(). 
Thanks in advance

---

### Post by geirha on 2008-05-29
Eclipse apparently has code completion for c++. Haven't tried it myself though.

[http://www.eclipse.org/downloads/moreinfo/c.php](http://www.eclipse.org/downloads/moreinfo/c.php)
> The Eclipse IDE for C/C++ Developers runs on top of the Eclipse Platform. The Eclipse IDE for C/C++ Developersprovides advanced functionality for C/C++ developers, including an editor (with syntax highlighting, and **code completion**), launcher, debugger, search engine and makefile generator.

---

### Post by Redscare on 2008-05-29
Oh yeah, sorry I forgot to mention that I was doing this in search of an alternative to Eclipse:)

---

### Post by dempl_dempl on 2008-05-29
(1) Kdevelop.  

When it comes to C++ ,  it beats the Eclipse.

It has source completion too ( only it has couple of options to be checked in the **project options** ).

(2)Anjuta is also nice. :)

(3)**Code::blocks** is ok, but bit buggy too ( from my experience )  . 



Btw, if some moderator sees this thread, they will probably shut it down, becuase this kind of thread emerges every second day :) .

Cheers!

---

### Post by Redscare on 2008-05-30
Anjuta doesn't complete the standard C++ libraries does it?
Also if I recall Kdevelop doesn't either?

---

### Post by irrdev on 2008-05-31
Code::Blocks seems to do the best job of all Linux IDEs, IMO. It isn't perfect, but it at least its code-completion works 99% of the time with the C++ STL. I have had disappointing experiences with both Kdevelop and Anjuta, although the former seems to be the better choice of the two. As for Eclipse, it it a Java IDE first and foremost; it is rather apparent that C++ support is only an addon. ;)

---

### Post by WW on 2008-05-31
> **dempl_dempl said:**
> 
Btw, if some moderator sees this thread, they will probably shut it down, becuase this kind of thread emerges every second day :) .

Not necessarily.  Unlike the usual "Which IDE is best?" threads, the question here is a very specific one about code completion of the standard library.

---

