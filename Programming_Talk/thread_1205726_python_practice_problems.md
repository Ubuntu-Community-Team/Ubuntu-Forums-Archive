---
title: "python practice problems"
date: 2009-07-06
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-06
I'm learning python and picking it up pretty well, but I was wondering if their is any place I can get practice problems from, instead of just copying down code from the tutorial?

---

### Post by fr4nko on 2009-07-06
You may write a linker in python, that would be a lot of fun! :-)
It involves a lot of manipulation of binary files probably by using the bfd library. Also it requires a lot of high-level coding in order to resolve the hierarchy and cross-references and to relocate and stuff like that.

AFAIK the big limitation of the current linker is that every object file is linked entirely even if just a few functions or even no functions are used. A smart linker can effectively link only the functions that are actually used.

That could be an interesting project if you are brave enough. :-)

Anyway, to be honest, I'm not an expert and I don't know the real level of difficulty of this kind of project, be aware,

Francesco

---

### Post by c0mput3r_n3rD on 2009-07-06
Haha alright, I'm very new to Python but I'll check it out. Thanks

---

### Post by nvteighen on 2009-07-06
> **fr4nko said:**
> You may write a linker in python, that would be a lot of fun! :-)
It involves a lot of manipulation of binary files probably by using the bfd library. Also it requires a lot of high-level coding in order to resolve the hierarchy and cross-references and to relocate and stuff like that.

AFAIK the big limitation of the current linker is that every object file is linked entirely even if just a few functions or even no functions are used. A smart linker can effectively link only the functions that are actually used.

That could be an interesting project if you are brave enough. :-)

Anyway, to be honest, I'm not an expert and I don't know the real level of difficulty of this kind of project, be aware,

Francesco
It's not a bad idea, but are you sure you can "strip" down object files with Python, without recurring to C? Just wondering...

---

### Post by thornmastr on 2009-07-06
> **c0mput3r_n3rD said:**
> I'm learning python and picking it up pretty well, but I was wondering if their is any place I can get practice problems from, instead of just copying down code from the tutorial?


1.      [http://www.challenge-you.com/](http://www.challenge-you.com/)
2.      [http://projecteuler.net/index.php?section=logout](http://projecteuler.net/index.php?section=logout)
3.      [http://www.spoj.pl/problems/classical/](http://www.spoj.pl/problems/classical/)
4.      [http://codegolf.com/](http://codegolf.com/)
5.      [http://www.codechef.com/](http://www.codechef.com/)

These will certainly keep you occupied for many hours, days, weeks, etc.

Enjoy,


Robert

---

### Post by fr4nko on 2009-07-06
> **nvteighen said:**
> It's not a bad idea, but are you sure you can "strip" down object files with Python, without recurring to C? Just wondering...
To be honest, I don't know... I know that python can be perfectly fine to manipulate binary files as it is demonstrated by the [xlrd]("http://pypi.python.org/pypi/xlrd") module that handle XLS binary files at byte level. Of course the module builds higher level functions to gain some abstraction but the base is a byte-level decoding of the file. I've implemented myself a very small subset of functionalities by using PHP because I need that badly in PHP.

Anyway, if you want to handle object files is probably a good idea to use some existing library and make python binding to it but this is definitely not a beginner project...

Otherwise you can start by implementing the more simple functionalities like reading an object file (like the 'nm' command does) and then let the program grow by adding more functionalities.

If I had time enough I would love to work on this kind of project... :-)

Francesco

---

