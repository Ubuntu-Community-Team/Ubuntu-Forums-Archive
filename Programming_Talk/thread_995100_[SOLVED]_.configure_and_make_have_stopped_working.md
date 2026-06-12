---
title: "[SOLVED] ./configure and make have stopped working"
date: 2008-11-27
forum: Programming Talk
---

### Post by Bulletbeast on 2008-11-27
In my project, I have a main dir with configure.ac and a Makefile.am pointing to two subdirs, doc/ and src/, each of which has its respective Makefile.am. I ran autotools and used to be able to do ./configure and make, but now, for some reason, a Makefile.in and a Makefile are only generated for src/.
configure.status goes:
```
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```
and make output's like this:
```
make  all-recursive
make[1]: Entering directory `/home/egasimus/Dev/dissonance/dissonance-cli'
Making all in src
make[2]: Entering directory `/home/egasimus/Dev/dissonance/dissonance-cli/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/egasimus/Dev/dissonance/dissonance-cli/src'
Making all in doc
make[2]: Entering directory `/home/egasimus/Dev/dissonance/dissonance-cli/doc'
make[2]: *** No rule to make target `all'.  Stop.
make[2]: Leaving directory `/home/egasimus/Dev/dissonance/dissonance-cli/doc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/egasimus/Dev/dissonance/dissonance-cli'
make: *** [all] Error 2
```

Any help?

---

### Post by pdwerryhouse on 2008-11-28
Does your configure.ac file have a line for doc/Makefile in its AC_OUTPUT section? And does your top level Makefile.am have doc in its SUBDIRS variable?  I'm wondering if perhaps you accidentally deleted one of them.

Otherwise, you could try running *make distclean* from the top level directory, and then configure and make again...

---

