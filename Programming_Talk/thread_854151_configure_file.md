---
title: "configure file"
date: 2008-07-09
forum: Programming Talk
---

### Post by rba1988 on 2008-07-09
Hi I'm starting to develop for Linux and use the C/C++ programming language for development. I'm used to installing programs from source via a configure file and the make tool. Can anyone direct me to any reference or explain the process for making the configure file and how to generate make files? Thanks.

---

### Post by escapee on 2008-07-09
[http://crasseux.com/books/ctutorial/Writing-a-makefile.html#Writing%20a%20makefile]("http://crasseux.com/books/ctutorial/Writing-a-makefile.html#Writing%20a%20makefile") is a pretty good reference on learning about makefiles.  I can't seem to remember where I found a good one on the configure files.  I'd Google that one.

---

### Post by WW on 2008-07-09
The reference manual to look at is the one for [autoconf](http://www.gnu.org/software/autoconf/manual/index.html).  However, that can be a bit overwhelming.  Despite some childish profanity, [this tutorial](http://mij.oltrelinux.com/devel/autoconf-automake/) looks like it covers the basic sequence for setting up a configure script fairly well.

You don't have to be a Makefile guru to get started with this, but you should at least know what a Makefile is, and how macros are defined and used in a Makefile before diving into autoconf, automake, and the other related tools.

---

### Post by odyniec on 2008-07-09
There's a comprehensive tutorial on Autotools (in the form of a set of slides) at [http://www.lrde.epita.fr/~adl/autotools.html]("http://www.lrde.epita.fr/~adl/autotools.html").

---

### Post by rba1988 on 2008-07-09
thanks guys. I appreciate the help.:)

---

