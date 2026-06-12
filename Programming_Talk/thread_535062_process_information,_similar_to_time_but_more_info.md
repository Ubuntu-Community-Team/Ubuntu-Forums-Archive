---
title: "process information, similar to time but more info"
date: 2007-08-26
forum: Programming Talk
---

### Post by slavik on 2007-08-26
was wondering if anyone know of something like time but that could also display maximum memory usage and such. like time but with memory.

does valgrind do this?

---

### Post by Wybiral on 2007-08-26
Valgrind is great for finding leaking, but simple "gprof" is good for profiling most Linux Code.

I constantly use the two together when needed.

---

### Post by slavik on 2007-08-26
I am looking for something that will work for interpreted code (shell scripts, perl, python, etc.) gprof works on compiled stuff (with -g) if I am correct.

---

### Post by Compyx on 2007-08-26
A quick google search for "perl profiling" and "python profiling" came up with these links:

[Devel:: DProf]("http://search.cpan.org/~ilyaz/DProf-19990108/DProf.pm") (the space after the :: shouldn't be there, but without it I got a smiley)
[http://docs.python.org/lib/profile.html]("http://docs.python.org/lib/profile.html")

---

### Post by slavik on 2007-08-26
but I am looking for something that works the same way that time does, except also gather max memory usage.

---

