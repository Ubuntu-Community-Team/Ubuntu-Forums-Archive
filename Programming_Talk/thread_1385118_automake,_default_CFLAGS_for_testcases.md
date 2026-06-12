---
title: "automake, default CFLAGS for testcases"
date: 2010-01-19
forum: Programming Talk
---

### Post by MadCow108 on 2010-01-19
I have a project using autotools. It has tons of testcases executed with make check.
short:
Is there a default variable, other than AM_CFLAGS, that is used by default only for testcases?

more detailed:
in the automake it looks about like this:
```

check_PROGRAMS = lots of testcases

TESTS = $(check_PROGRAMS)

TESTS_ENVIRONMENT = environment stuff

testsuite_test_gen_vector_SOURCES = \
	testsuite/test_gen_vector.c

testsuite_test_gen_vector_CFLAGS = \
        -DNO_THREADS

testsuite_test_gen_vector_LDADD = \
	-lm

testsuite_test_gen_stack_SOURCES = \
	testsuite/test_gen_stack.c

testsuite_test_gen_stack_CFLAGS = \
        -DNO_THREADS

testsuite_test_gen_stack_LDADD = \
	-lm
... lots more

```

what I am looking for is a way to avoid all these similar *_LDADD and *_CFLAGS by using some default variable

there is AM_CFLAGS which is used by default if no per target flag exists. But the tests need additional flags.
is there some kind if AM_TEST_CFLAGS/_LDADD variable which is used by default for tests?
I just can't find anything with google :/

---

### Post by MadCow108 on 2010-01-21
*bump*

---

