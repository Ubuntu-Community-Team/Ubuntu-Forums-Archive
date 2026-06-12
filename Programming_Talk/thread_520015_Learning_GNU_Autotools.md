---
title: "Learning GNU Autotools"
date: 2007-08-07
forum: Programming Talk
---

### Post by nrwilk on 2007-08-07
I've been working on a C++ project using ncurses, and I'm getting tired of issuing the same ultra-long g++ command over and over.

So, I decided to start learning GNU's autotools.  I found what was supposed to be a beginner's tutorial, and it seemed dated.  The program that they use is a hello world program which has no outside dependencies.  I need at least ncurses to build it, and I can't find a tutorial which will describe the process to an intermediate programmer, including dependency checks.  Everything seems to be for the beginner or a huge tome full of information that I don't need.

Does anyone have a suggestion for an up-to-date intermediate tutorial?  Or, any other suggestions?  How do most people learn to use autotools?

Thanks a lot for any help! :)

---

### Post by vambo on 2007-08-07
Not up to snuff on auto tools. However thoroughly recommend this

[http://www.oreilly.com/catalog/make2/]("http://www.oreilly.com/catalog/make2/")

I know it's not free, but to me it's worth the money. Even if it does appear to be rather long in the tooth.

---

### Post by hod139 on 2007-08-07
Autotools is a monster with a crazy language syntax.  I prefer using [cmake]("http://www.cmake.org/HTML/Index.html").  It is much simpler and intelligent.  Another option is [scons]("http://www.scons.org/"), which uses python for the scripting language.  I suggest you learn one of those two over autotools.

---

### Post by samjh on 2007-08-07
Here's a tutorial I found useful:
[http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/autotools.html](http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/autotools.html)

---

### Post by nrwilk on 2007-08-07
> **hod139 said:**
> Autotools is a monster with a crazy language syntax.  I prefer using [cmake]("http://www.cmake.org/HTML/Index.html").  It is much simpler and intelligent.  Another option is [scons]("http://www.scons.org/"), which uses python for the scripting language.  I suggest you learn one of those two over autotools.

Thanks a lot!  I'll look into cmake and scons.

> **samjh said:**
> Here's a tutorial I found useful:
[http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/autotools.html](http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/autotools.html)

Great!  This is the first tutorial that I've seen where the versions of automake and autoconf are anywhere close to the versions I have!

---

### Post by spookware on 2007-08-07
Thank you for that tutorial link. That was very helpfull.

---

### Post by nrwilk on 2007-08-08
> **spookware said:**
> Thank you for that tutorial link. That was very helpfull.

Word.  I have fully functioning configure and make files for my project now.  Thank you!  that tutorial was the best one I've seen so far.  And, it's up-to-date too. 8-)

Thanks again!

---

### Post by samjh on 2007-08-08
> **nrwilk said:**
> Word.  I have fully functioning configure and make files for my project now.  Thank you!  that tutorial was the best one I've seen so far.  And, it's up-to-date too. 8-)

Thanks again!

Any time!  I scratched my head against Autotools so much that I was about to give up learning it until I found that tutorial.  So I was compelled to post it. :)

---

