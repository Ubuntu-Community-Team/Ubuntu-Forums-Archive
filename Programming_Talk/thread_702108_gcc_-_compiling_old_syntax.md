---
title: "gcc - compiling old syntax"
date: 2008-02-19
forum: Programming Talk
---

### Post by Nine on 2008-02-19
Hello, I'm helping a friend here by trying to compile a *very* old mud application from 1990 that has some pretty outdated syntax. Is there a way instead of fixing all the source files to do a 'make' that will compile outdated C?

---

### Post by lnostdal on 2008-02-20
probably not - it depends really

1990 .. this was maybe written for, what -- MS DOS 5.5 using a Borland compiler perhaps?

do you have a link to the source?

---

### Post by Nine on 2008-02-20
[http://www.hypercube.org/tess/rom/download/Rom24b6.tar.gz](http://www.hypercube.org/tess/rom/download/Rom24b6.tar.gz)

That's the source code. From what I can gather, it was written for a UNIX like platform and was, at the time of this release, being developed on Linux.

---

### Post by lnostdal on 2008-02-20
ah .. that code badly needs some love

try this as a temporary solution though:

```

cd src
mv Makefile.linux Makefile
sudo aptitude install gcc-2.95

```

now change the first line in Makefile to read:

```

CC      = gcc-2.95

```

..then start make and it will compile and link a file *rom*

---

### Post by lnostdal on 2008-02-20
btw.
```

cd ../area
../src/rom

```

..then in a different terminal

```

telnet localhost 4000

```

..and it's up

---

### Post by Nine on 2008-02-20
Thanks, I'll try this out when I get home from work. I appreciate the help.

IT WORKS!

---

