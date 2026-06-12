---
title: "cpp help"
date: 2010-11-28
forum: Programming Talk
---

### Post by awaistoor on 2010-11-28
hello everyone .. 
im new here so just need some help about c programming
ok im using ubuntu 10.04 n i have installed gcc as well as g++ .. i have also installed build-essential package n have compiled a simple hello world program in c++
my questions are:
1. where can i see the header files of gcc
2. can i include graphics in my program using gcc (as i have done my all c programming in turbo c)
3. someone tell me a compiler of c++ on which i can work on.
thanx :)
Awais Toor

---

### Post by GregBrannon on 2010-11-28
> 3. someone tell me a compiler of c++ on which i can work on.
thanx 

g++ is the compiler.

You may be asking for Integrated Development Environment recommendations.  If so, please review the many threads in this forum that have previously discussed this topic.

---

### Post by lucasart on 2010-11-28
> **awaistoor said:**
> hello everyone .. 
im new here so just need some help about c programming
ok im using ubuntu 10.04 n i have installed gcc as well as g++ .. i have also installed build-essential package n have compiled a simple hello world program in c++
my questions are:
1. where can i see the header files of gcc
2. can i include graphics in my program using gcc (as i have done my all c programming in turbo c)
3. someone tell me a compiler of c++ on which i can work on.
thanx :)
Awais Toor

1.
```

locate vector.h

```and you'll have your answer

2. graphics are not within the C or C++ language itself. You can only draw something on a window, create buttons etc. This is called GTK, and you should be looking at GTK tutorials. GTK is of course free software written in C, so you can use it in C or C++ (which ever language you prefer).


3. g++.

Also an IDE should make it easier for you. I personally like CodeLite, but there are certainly many other good ones. I believe the real hardcore linux fans are using VIM or Emacs, and these are extremely powerful, but also difficult to begin with... up to you ;)

---

### Post by awaistoor on 2010-11-29
thanx ...

---

