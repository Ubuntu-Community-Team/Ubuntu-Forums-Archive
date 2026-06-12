---
title: "Make functions"
date: 2010-08-18
forum: Programming Talk
---

### Post by Essence on 2010-08-18
I have a quick question about make functions.
I am wondering what I am doing wrong in attempting to define a multi-line variable.

For example, if I have the following makefile:
```

simple1 = echo Testing simple 1

define simple2 =
echo Testing simple 2
endef

test:
    @$(call simple1)
    @$(call simple2)

```Then I would expect the folowing:
```

make test

Testing simple1
Testing simple2

```However I never get the multi-line function to work. I only ever get the first print ("Testing simple1") and not the second. I figure I am missing something here, but can not see what. Any help would be appreciated, thanks.

---

### Post by dwhitney67 on 2010-08-18
You do not require the equal sign following the function name.

Try something like:
```

define simple2
echo Test simple2
endef

```

---

### Post by Essence on 2010-08-18
Thanks! That does seem to solve my problem.
I am left with one question: Why does the GNU 'make' guide ([http://www.gnu.org/software/make/manual/make.html#Multi_002dLine](http://www.gnu.org/software/make/manual/make.html#Multi_002dLine)) tell me to use the equal sign, while the code requires me to not use one in order to function?

---

### Post by dwhitney67 on 2010-08-18
A typo perhaps?

---

