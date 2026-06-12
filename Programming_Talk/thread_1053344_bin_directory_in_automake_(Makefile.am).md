---
title: "bin directory in automake (Makefile.am)"
date: 2009-01-28
forum: Programming Talk
---

### Post by nitro_n2o on 2009-01-28
Hi all,

Im trying to build a project using GNU autotools and automake.. I have the current directory structure
src
docs
man

However, I would like to specify a bin/ directory so that when i type make "make" the default action is put the binaries in bin/ 

how can i do that?

Thx

---

### Post by cabalas on 2009-01-28
You specify where the files go in Makefile.am (generally Makefile.am in the src directory)  I would suggest reading through this tutorial, it's the one I used to learn the autotools and I found it very clear and easy to follow.

[http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/](http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/)

Some small parts might be out of date by now, but should be easy to figure out what you should change them to.

---

