---
title: "a question about makefile"
date: 2009-08-19
forum: Packaging and Compiling Programs
---

### Post by bzhao on 2009-08-19
today I met a makefile having a line like:
TMP ?= /tmp

What does the "?" mean here.

Thanks indeed

---

### Post by zarthon on 2009-08-20
From:
[http://www.gnu.org/software/make/manual/html_node/Flavors.html#Flavors](http://www.gnu.org/software/make/manual/html_node/Flavors.html#Flavors)



There is another assignment operator for variables, `?='. This is called a conditional variable assignment operator, because it only has an effect if the variable is not yet defined. This statement:

     FOO ?= bar

is exactly equivalent to this (see The origin Function):

     ifeq ($(origin FOO), undefined)
       FOO = bar
     endif

---

### Post by bzhao on 2009-08-22
thank you for providing the link, which is good.

---

