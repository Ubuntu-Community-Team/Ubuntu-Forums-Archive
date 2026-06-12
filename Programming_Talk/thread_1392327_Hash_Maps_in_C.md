---
title: "Hash Maps in C"
date: 2010-01-28
forum: Programming Talk
---

### Post by JDShu on 2010-01-28
Hey guys, does anybody know what the standard practice is for getting hash maps in C? I use the STL in C++ and Python has the dictionaries, but I can't find any agreed upon solution for C.

---

### Post by fuzZzball on 2010-01-28
A while ago I was searching for something similar, dunno if this is what you need, You can take a look though :D

[http://ubuntuforums.org/showthread.php?t=1222055]("http://ubuntuforums.org/showthread.php?t=1222055")

---

### Post by JDShu on 2010-01-28
Thanks! Its certainly not as pretty to use as hash functions in other languages, but its better than nothing.

---

### Post by MadCow108 on 2010-01-28
there is no real agreed practice, as the C standard does not contain any complex containers, nor does it set any requirements/recommendations on what a good implementation is.

glib's hash table:
[http://library.gnome.org/devel/glib/stable/glib-Hash-Tables.html](http://library.gnome.org/devel/glib/stable/glib-Hash-Tables.html)

uses tons of macros to make it reasonably easy to use, bsd license:
[http://uthash.sourceforge.net/](http://uthash.sourceforge.net/)

this one that looks quite sophisticated but I never used it. You should probably read the licesne before considering to use it.
[http://www.sunrisetel.net/software/devtools/sunrise-data-dictionary.shtml](http://www.sunrisetel.net/software/devtools/sunrise-data-dictionary.shtml)

---

### Post by JDShu on 2010-01-28
Thank you very much for answering! I guess I'll have to do some experimenting.

---

