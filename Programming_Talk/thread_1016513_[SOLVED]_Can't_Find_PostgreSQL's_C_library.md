---
title: "[SOLVED] Can't Find PostgreSQL's C library ???"
date: 2008-12-20
forum: Programming Talk
---

### Post by rich1939 on 2008-12-20
I installed **PostgreSQL v8.3**, but I can't find the C library. The documentation says that it's called "**pq**" or maybe "**libpq**", and when I execute "**pg_config --libdir**" it reports "**/usr/lib**", but there's no PostgreSQL library that I can recognize there.

I've tried "find", but it only finds directories named "libpq" and they only have the ".h" header files in them.

My program complied, but I can't link it. Do I have to download the library from somewhere...and if so, how?

---

### Post by slavik on 2008-12-20
did you add the flags for the linker? as in -lpq or whatever it has to be?
Have you tried looking for a tutorial that shows the linker flags?

---

### Post by rich1939 on 2008-12-20
bump

I located a file in /**usr/lib** called **libpq.a**, but when I used that in my compile command: **gcc -o test test.o -L/usr/lib -llibpq.a**, I get a message "**/usr/bin/ld can't find -llibpq.a**!

There are two other entries in /usr/lib that match **libpq*** and they are **libpq.so** and **libpq.so.5**, but they are both links and neither one is acceptable to the linker.

Any ideas?

---

### Post by slavik on 2008-12-20
try using -lpq

---

### Post by rich1939 on 2008-12-20
> **slavik said:**
> try using -lpq

**YOU'RE RIGHT!**

I had searched for the "pq" library, but couldn't find it, so I also looked for "libpq", etc. The latter weren't acceptable to the linker.

I finally took a leap of faith and followed your suggestion to use **-lpq** and it linked and ran just fine, with no errors.

For others who might want to key-in the "libpq Example Program 1", I first used the commands: **pg_config --includedir** and **pg_config --libdir** to locate the **libpq-fe.h** header file and the location of the **pq** library. The commands I used to compile and link the program were as follows:

```

gcc -c testlibpq.c -I/usr/include/postgresql
gcc -o testlibpq testlibpq.o -L/usr/lib -lpq

```

If the locations of your header file and/or library are different from these using the **pg_config** commands, then use your results.

Thanks again for your very helpful response. I love these forums!

---

### Post by westmdflounder on 2009-02-07
This would typically work as a one liner:

gcc -lpq -I/usr/include/postgresql testlibpq.c -o testlibpq

---

