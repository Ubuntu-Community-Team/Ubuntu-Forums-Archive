---
title: "Compiler problem"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by andymic on 2008-07-01
Hi,
I am trying to compile some stuff.

When I do a ./configure I get an error as follows:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output... configure: error: C++ compiler cannot create executables

Anybody have an idea what's wrong?

TIA

---

### Post by sdennie on 2008-07-01
Try running:

```

sudo apt-get install build-essential

```

That will install the major things needed for building software.

---

### Post by andymic on 2008-07-01
Vor

Thanks man.

That got me passed 1st base  :-)

Now I gotta fix a few other niggles.

You're a star !!

---

### Post by sdennie on 2008-07-01
A useful trick to use if you are compiling a newer version of something that is already in the Ubuntu repos is to use:

```

sudo apt-get build-dep name_of_package

```

That will download everything that was needed to build the Ubuntu version of the package and save you a lot of time tracking down dependencies.

---

