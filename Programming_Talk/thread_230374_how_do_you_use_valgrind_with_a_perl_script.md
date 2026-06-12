---
title: "how do you use valgrind with a perl script?"
date: 2006-08-05
forum: Programming Talk
---

### Post by raspberryh on 2006-08-05
Okay, this might be a dumb question... But does anyone know how to use Valgrind with a Perl script?
I know that you can only use it on an executable. And I can't seem to find any kind of tutorial or anything online that uses a Perl script - they all use C code.
Thanks!
Heather

---

### Post by raspberryh on 2006-08-05
Nevermind! I finally found the answer. You have to type
valgrind **perl** something.pl

---

### Post by raspberryh on 2006-08-05
Nevermind I was wrong :(
That makes it debug the perl interpreter!

---

