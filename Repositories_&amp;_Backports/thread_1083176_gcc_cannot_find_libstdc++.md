---
title: "gcc cannot find libstdc++"
date: 2009-02-28
forum: Repositories &amp; Backports
---

### Post by Brad- on 2009-02-28
I've just installed the new EasyPeasy on my EeePC.
I did this to get a Ubuntu base, which I thought would make coding easier on the little machine. I apt-got build-essential and everything seems to be operating fine, except for one glitch, so far.

gcc cannot link a c++ program, specifically cannot find iostream references. I know libstdc++ is installed because I can find the file in /usr/lib/gcc/...
The odd thing is that g++ can compile and link my hello.cxx.
I know it is a linking problem because when I use gcc -o I get an object file, but when I then try ld on it I get the same complaints about undefined references. I tried "ld hello.o --library=stdc++" and it replied "cannot find -lstdc++". Again, g++ gives me a working a.out.

Also, I had this same behavior on ASUS's Xandros, which ships with EeePC.
I was able to apt-get build-essential and had exactly the same behavior. Which was one reason I went to Ubuntu, but clearly the version of Linux was not the problem.

---

### Post by WW on 2009-03-01
I don't have an answer, just another question:  if the program is written in C++, and g++ works, why do you want to use gcc?



P.S. You'll probably get more responses if you ask this question in the "Programming Talk" subforum.

---

### Post by Brad- on 2009-03-02
> **WW said:**
> I don't have an answer, just another question:  if the program is written in C++, and g++ works, why do you want to use gcc?

Simply because gcc is suppose too work with C++ programs.
If I could not build c++ at all I'd be urgently hunting for a solution, but as is I guess this is more of a bug report re: build-essential.
But I'm accustomed to using gcc for everything.

> **WW said:**
> 
P.S. You'll probably get more responses if you ask this question in the "Programming Talk" subforum.
thank you, I'm back to Linux again after 6 yrs and not familiar with good discussion groups these days

---

