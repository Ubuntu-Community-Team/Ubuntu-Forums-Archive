---
title: "after &quot;apt-get install build-essential&quot; gcc cannot find stdlibc++"
date: 2009-03-02
forum: Programming Talk
---

### Post by Brad- on 2009-03-02
I've just installed the new EasyPeasy on my EeePC.
I did this to get a Ubuntu base, which I thought would make coding easier on the little machine. I apt-got build-essential and everything seems to be operating fine, except for one glitch, so far.

gcc cannot link a c++ program, specifically cannot find iostream references. I know libstdc++ is installed because I can find the file in /usr/lib/gcc/...
The odd thing is that g++ can compile and link my hello.cxx.
I know it is a linking problem because when I use gcc -o I get an object file, but when I then try ld on it I get the same complaints about undefined references. I tried "ld hello.o --library=stdc++" and it replied "cannot find -lstdc++". Again, g++ gives me a working a.out.

Also, I had this same behavior on ASUS's Xandros, which ships with EeePC.
I was able to apt-get build-essential and had exactly the same behavior. Which was one reason I went to Ubuntu, but clearly the version of Linux was not the problem.

---

### Post by dwhitney67 on 2009-03-02
Why are you using 'gcc' and not 'g++' to compile/link your C++ application?

P.S.  g++ == gcc -lstdc++

---

### Post by Brad- on 2009-03-02
> **dwhitney67 said:**
> 
P.S.  g++ == gcc -lstdc++

okay thx ... the one thing I didn't try.
I'm back to linux after 6 yrs, so guess I forgot a couple things.

---

