---
title: "recursive use of Make"
date: 2010-09-29
forum: Packaging and Compiling Programs
---

### Post by LeeBruce on 2010-09-29
Hello,
before submitting a bug I would like to be sure...

My setup: Ubuntu 9.04, GNU Make 3.81.

I have two makefiles in the same folder (.../tmp/makefile/), really simple, with the first that recursively calls the second.
The global dependency graph is as follows:

```

mainTarget
  |--> p1 --> pp1
  |--> p2 --> pp2

```Here are the files:
Makefile
```

mainTarget : p1 p2
    touch mainTarget

p1 : phony
p2 : phony

phony :
    $(MAKE) -f Makefile2 all
.PHONY : phony

```Makefile2
```

all : p1 p2

p1 : pp1
    touch $@
p2 : pp2
    touch $@

pp1 :
    touch $@
pp2 :
    touch $@

```From the shell I touch either pp1 or pp2 to make them newer and test if make is working properly.
Touch pp2 gives me what I expect:
```

> touch pp2
> make
make -f Makefile2 all
make[1]: Entering directory `... /tmp/makefile'
touch p2
make[1]: Leaving directory `... /tmp/makefile'
touch mainTarget

```That is, p2 and so mainTarget get 'rebuilt'.

But if I touch pp1:
```

> touch pp1
> make
make -f Makefile2 all
make[1]: Entering directory `... /tmp/makefile'
touch p1
make[1]: Leaving directory `... /tmp/makefile'

```p1 is updated but mainTarget is not!!
And I've also discovered that if I exchange p1 and p2 in the prerequisites list of mainTarget (p2 p1 instead of p1 p2) it behaves the other way round, i.e. it works only with pp1.

Does anybody know why this happens?
Is it a bug of make or it is the expected behavior?

Many thanks

---

### Post by LeeBruce on 2010-10-04
bump..:(
Does anybody know why this happens?
Can you reproduce the same problem?

cheers

---

