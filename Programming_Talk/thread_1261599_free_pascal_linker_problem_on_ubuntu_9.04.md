---
title: "free pascal linker problem on ubuntu 9.04"
date: 2009-09-08
forum: Programming Talk
---

### Post by rollyar on 2009-09-08
I have a problem when compiling a library, but not with a program.
I searched about this problem, but can not find a clear solution. 
The error is as follows:
...
"Error: Can't call the linker, switching to external linking"
...

the command line is:  

fpc tbudf.dpr -Sh -S2 -Sd -TLINUX -Op3

Thank you very much.

---

### Post by jmaebe on 2009-09-10
The problem is explained here: [http://www.freepascal.org/faq.var#unix-ld219](http://www.freepascal.org/faq.var#unix-ld219)

In short: ld 219 and 2.19.1 have a bug that causes it to crash when linking FPC programs. This bug has been fixed in the mean time, however there is no new binutils release yet. I don't know whether Ubuntu already provides a patched version of that package.

If not, your only choice is probably to downgrade to binutils 2.18.50 (if that's possible), or to compile binutils yourself from cvs.

---

