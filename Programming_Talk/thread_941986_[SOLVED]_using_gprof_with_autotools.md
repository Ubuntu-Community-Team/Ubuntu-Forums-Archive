---
title: "[SOLVED] using gprof with autotools"
date: 2008-10-08
forum: Programming Talk
---

### Post by Sydius on 2008-10-08
I tried to set up autotools for my project, and it has been working well enough so far.  I don't really understand it entirely, though, and frankly, I find the whole system to be nearly as complex as the actual programming for the project.  I'm at a level of understanding where it is still difficult to articulate questions in a way that gets at what it is I actually want to know.

At any rate, I'd like to be able to use gprof, and that means adding the -pg flag to compilation.  I would like to do this via a configuration option (is that wise?) and so I assume I need to do something to my configure.ac file and my makefile.am.

Here are those two files (there are other Makefile.am files, but this is the only one relating to source code):

[http://code.google.com/p/odysi/source/browse/trunk/configure.ac#](http://code.google.com/p/odysi/source/browse/trunk/configure.ac#)
[http://code.google.com/p/odysi/source/browse/trunk/build/Makefile.am#](http://code.google.com/p/odysi/source/browse/trunk/build/Makefile.am#)

So... two questions:

1. Is it a good idea to add a configuration option to enable profiling? (If not, then what is the best way to handle this?)

2. How do I add it as an option?

I know I could just add the -pg option to the makfile.am, but then it wouldn't be configurable.

Sorry if I sound like a newb, but I am one. :confused:

---

### Post by pdwerryhouse on 2008-10-08
You can set it in your CFLAGS environment variable before running configure:

```
CFLAGS=-pg ./configure
```

Probably not worth the trouble of adding it as an option.

---

### Post by Sydius on 2008-10-08
Oh, I didn't realize I could do that.  Thanks!  Seems so simple and silly... I guess I was making it much more complicated than it needed to be.

---

