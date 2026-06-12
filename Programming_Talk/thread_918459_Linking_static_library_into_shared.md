---
title: "Linking static library into shared"
date: 2008-09-12
forum: Programming Talk
---

### Post by amauk on 2008-09-12
Hi all,

Is it safe to link a static library (static library is -fPIC'd) into a shared library?

gcc is throwing a warning, saying this may not be portable

I'm trying to hack up a shared library into more manageable chunks within my IDE, with different sections compiled separately then linked together to form a single .so

thanks
Tony

---

### Post by rnodal on 2008-09-14
Are trying to turn a static library into a shared one? Or linking a static library into an existing shared library?

-r

---

### Post by amauk on 2008-09-14
linking a static library into an existing shared library

it's ok though
I've sorted it

---

### Post by nvteighen on 2008-09-14
Are you building a shared library with a static library? Well, if so, just know that one of the most important shared libraries in a GNU/Linux system is built that way (/lib/ld-2.7.so), as it cannot depend on any shared library to be run... because it happens to be the linker library that allows shared libraries to work! :p

So, it shouldn't give any trouble, as long the static library is on PIC format.

---

