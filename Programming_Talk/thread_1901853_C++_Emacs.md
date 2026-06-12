---
title: "C++ Emacs"
date: 2011-12-29
forum: Programming Talk
---

### Post by ah535 on 2011-12-29
Hey I am trying to figure out how to do some basic C++ programming. I want to use emacs.  My file is saved as hw10.cpp.  When I try to compile it this is what I get.


ah535@ah535-laptop:~$ g++ hw10.cpp
hw10.cpp:2:21: error: isostream: No such file or directory
hw10.cpp: In function ‘int main()’:
hw10.cpp:7: error: ‘cout’ was not declared in this scope

This is my code in the emacs window.

#include <isostream>
using namespace std;

int main()
{
cout << "Hello world/n";
return 0;
}


Thanks for the help

---

### Post by Barrucadu on 2011-12-29
Emacs has nothing to do with this - it's "iostream", not "isostream".

---

### Post by dwhitney67 on 2011-12-29
Try iostream.

Also, your choice of editor will have no bearing on your ability to learn C++.  Thus I recommend that you refrain from mentioning it if you have future posts, since it is not relevant.

---

### Post by MG&amp;TL on 2011-12-29
No disrespect, but Emacs isn't for "hello world" programmers. Although I commend you for getting there. :)

---

### Post by ah535 on 2011-12-29
Thanks for the help.  That solved it.

---

### Post by F.G. on 2011-12-29
> **MG&TL said:**
> No disrespect, but Emacs isn't for "hello world" programmers. Although I commend you for getting there. :)
when i first tried to learn C i went through a tutorial which mentioned emacs.  before i got to write any code i went through trying to learn emacs. finally got a hello world program written, then had to figure out what a 'compiler' was, and where to get one (i was on windows at the time).  i'd recommend keeping it simple, and focusing on learning one thing.  
(having said that, i've been coding for a few years now, and have only just started to learn vim).

---

