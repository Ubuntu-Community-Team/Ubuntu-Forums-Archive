---
title: "Cannot find -lXtst"
date: 2009-05-06
forum: Packaging and Compiling Programs
---

### Post by aroby on 2009-05-06
I'm new to Ubuntu and I'm trying to find my way around.  I'm trying to compile a simple program from [http://www.cs.kent.ac.uk/~sm244/Jail.tar.gz](http://www.cs.kent.ac.uk/~sm244/Jail.tar.gz)

It needs the Xtst library.  Seems that on Ubuntu the X libraries are actually in /usr/lib rather than /usr/X11R6/lib.  So I change the Makefile to point to /usr/lib, but still can't find Xtst.  I have the following files in /usr/lib : libXtst.so.6 and libXtst.so.6.1.0.  The former is a link to the latter.

So it seems that I have the library, but I can't figure out why it can't be found.  Any ideas?

Thanks

Anthony

---

### Post by ramaboule on 2010-01-22
Just need to do install the right package. From the terminal, do:
```
$ sudo apt-get install libxtst-dev

```

---

