---
title: "what is rule file in debian/rules"
date: 2010-11-19
forum: Packaging and Compiling Programs
---

### Post by c2tarun on 2010-11-19
hi friends. i just wanted to know what exactly rules file does??? and what is its role?

---

### Post by gmargo on 2010-11-20
The debian/rules file is a makefile used to create the package.

[http://www.debian.org/doc/maint-guide/ch-dreq.en.html#s-rules](http://www.debian.org/doc/maint-guide/ch-dreq.en.html#s-rules)

---

### Post by c2tarun on 2010-11-21
i was reading about packaging and found this line

[B]debuild will first check that all the build-depends packages are installed.


[/B]can anyone please tell me from where will debuild look for the list of build-depends packages needed.???

---

### Post by MadCow108 on 2010-11-21
they are listed in the debian/control file with the tag build-depends and depends

---

### Post by SevenMachines on 2010-11-22
Theres an overview of the basic debian directory files here if you need more detail

---

