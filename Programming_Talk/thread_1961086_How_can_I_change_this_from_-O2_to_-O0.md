---
title: "How can I change this from -O2 to -O0 ?"
date: 2012-04-18
forum: Programming Talk
---

### Post by forsubhi on 2012-04-18
I want to change this from  CFLAGS:--g -O2 to -O0  ?

[IMG]http://img6.imagebanana.com/img/m9i8jb1t/configure.inKate_054.png[/IMG]


I try this command 
```
./configure CFLAGS='-O0 -ggdb3 -g -O0 --g -O0' CXXFLAGS='-O0 -ggdb3 -g -O0 --g -O0'
```but nothing happens 

and is this related to debug optimisation so my code have optimisation behaviour when I debug it .

---

### Post by 11jmb on 2012-04-18
Have you tried taking -O2 out of the CFLAGS in configure.in and re-running autoconf?

It looks like the optimization is hard-coded in the configure script otherwise

---

### Post by forsubhi on 2012-04-20
I tried to do that , and after that I still have some variable with optimised out and no values available for it until I reach them again , I have Question about that 
can I have optimised out variable even though I stop optimisation? 

Note : this message ("optimized out") now appear in macro method that give me value from struct , if you want I can post the exact code that cause the problem   .

and what is difference between 

./configure CFLAGS='-O0 -ggdb3' CXXFLAGS='-O0 -ggdb3'
and 

./configure CFLAGS='-g -O0 ' CXXFLAGS='-g -O0'
and how can I know the appropriate arguments after  CFLAGS and CXXFLAGS ?

---

### Post by forsubhi on 2012-04-22
thank most of code become without optimisation , so I think thread should marked as solved even if there is some code with optimisation , 
but I want to know differences between  
./configure CFLAGS='-O0 -ggdb3' CXXFLAGS='-O0 -ggdb3'
and 

./configure CFLAGS='-g -O0 ' CXXFLAGS='-g -O0'

and where is the reference for all of them?


the command ./configure CFLAGS='-O0 -ggdb3' CXXFLAGS='-O0 -ggdb3' solve the problem .

---

### Post by 11jmb on 2012-04-23
Hmm, that's still interesting that any of your variables are optimized out in debugging mode. At the risk of patronizing, are you 100% sure that the library where the "optimized out" variables were created is the same library that you just compiled? In other words is it possible that your library is calling a function from another library that may have been compiled -O2?

As for the -ggdb3 flags question, I think that that allows for more debugging features. For example, I think that you can debug macros with -ggdb3

---

### Post by forsubhi on 2012-04-24
my project is  SphinxTrain and it is depend on sphinxbase , I think this cause the  problem , I disabled optimisation in sphinxbase , but also there is some  code that still show me , not optimized message 

is it possible to see not optimised message even if I stop optimisation ?

even though if I find the library the code that cause the problem , I can post it with all it's dependencies .

---

### Post by 11jmb on 2012-04-24
I just can't think of a reason that a variable would be "optimized out" in a library that is compiled -g -O0.

That is why I mentioned the variable possibly being a member of a dependency library that has been optimized. If an "optimized out" variable is occurring in a library that you have manually build with -O0 -g flags, then this problem is over my head.

---

