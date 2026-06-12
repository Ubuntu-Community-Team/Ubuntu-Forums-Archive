---
title: "gcc trunk on Hardy Heron amd64"
date: 2010-01-19
forum: Packaging and Compiling Programs
---

### Post by misha680 on 2010-01-19
Dear Sirs:

I am trying to compile gcc trunk on Hardy Heron amd64 but getting this error:

```
checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for objdir... .libs
checking for correct version of gmp.h... yes
checking for correct version of mpfr.h... buggy but acceptable
checking for the correct version of mpc.h... no
configure: error: Building GCC requires GMP 4.2+, MPFR 2.3.2+ and MPC 0.8.0+.
Try the --with-gmp, --with-mpfr and/or --with-mpc options to specify
their locations.  Source code for these libraries can be found at
their respective hosting sites as well as at
ftp://gcc.gnu.org/pub/gcc/infrastructure/.  See also
http://gcc.gnu.org/install/prerequisites.html for additional info.  If
you obtained GMP, MPFR and/or MPC from a vendor distribution package,
make sure that you have installed both the libraries and the header
files.  They may be located in separate packages.
make: *** No targets specified and no makefile found.  Stop.
make: *** No targets specified and no makefile found.  Stop.

```

Any hints?

Thank you!

Misha

---

### Post by SevenMachines on 2010-01-19
you're missing libmpc-dev but i dont think thats available in hardy. you'd need to either try installing a version from a later distribution (i think the earliest is [jaunty]("http://packages.ubuntu.com/jaunty/libmpc-dev")) or try building the package or the source for hardy

---

