---
title: "Using Fortran in Ibex"
date: 2008-11-10
forum: Programming Talk
---

### Post by MarcusAntonius on 2008-11-10
Hi everybody,

I am using Ibex and I have to compile a program which needs to link fortran with C files (at least I think so). Therefore I installed libg2c and libgfortran. In the Makefile I tried the options -lg2c or -lgfortran, but both times the linker (ld) complained that he couldn't find these libraries (in Hardy this problem never occured). So I looked into /usr/lib/ and found the files including the links (libgfortran.so.3 -> /usr/lib/libgfortran.so.3.0.0) and  (libg2c.so.0 -> libg2c.so.0.0.0) when I created the same links, but called libgfortran.so and libg2c.so ld worked without any problems.

In Hardy these links have been created automatically I think. Is this a bug or do I get something wrong?

---

### Post by MarcusAntonius on 2008-11-11
Nobody experienced this problem?

---

### Post by noway2 on 2009-03-25
I realize that your post is dated a few months back, but I just ran into a similar issue myself; where a program I was trying to install (Modnum) wanted libgfortran.so.3 and my version of GCC (4.2.4) only has .so.2.

After working on various solutions for the last 3 hours, including an unsuccessful attempt to use Alien to convert an RPM, I finally found a way forward.  I went to the debian package repository and located a package with that library.  I then modified the /etc/apt/sources.list to include one of the mirrors for this repository.  Afterwards, running the package update utility and telling it to fetch updates showed my libgfortran.so.3 as being available.

I took a chance that it would be sufficient and apparently it worked as I was then able to continue with the modnum installation and it appears to function.

A large part of my problem was that as I was coming up dry when attempting to search in google for libgfortran.so.3 as it only seemed to want to direct towards RPM repositories.  My point here is to be sure to look on the ubuntu or failing that some other debian repository as it may contain what you need.

---

