---
title: "Building against different libraries."
date: 2008-09-05
forum: Programming Talk
---

### Post by loop on 2008-09-05
I'm currently developing a small application that is dependent on quite a few different libraries. The problem I'm having is that my program very rarely works on anyone else machine due to it being dependent on specific versions of libraries.
Is there a way of downloading other versions of the libraries I'm building against and use them instead of the installed ones on my development machine. i.e I can produce a binary built against glibc 2.6 and another built against glibc 2.7.
The only alternative I can think of is to build everything in statically but that just seems like overkill.

---

### Post by rnodal on 2008-09-05
The other way is to hard code the path to the libraries your application depends on shipping those libraries with your application. Note that in terms of security that is not a good idea but if your shipping a game for example then it should not be a big deal.


-r

---

