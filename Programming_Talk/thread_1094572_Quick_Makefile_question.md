---
title: "Quick Makefile question"
date: 2009-03-12
forum: Programming Talk
---

### Post by ranthal on 2009-03-12
Hey all,

In a makefile I want to grab the output of a shell command and assign it to a macro, how do I do this?

The specifics are that I want to find the openssl binary (i.e. command line would run "which openssl") and assign it to the macro OPENSSL.

I feel like this is a really straightforward thing, my brain is just running on empty right now ](*,).  Thanks!

---

### Post by monkeyking on 2009-03-12
backtick the argument something like

[PHP]

ubuntu=pre

all : test

test : Makefile
        echo ${ubuntu}
[/PHP]

use it like

[PHP]make
echo pre
pre
[/PHP]
and then

[PHP]
make ubuntu=`which openssl`
echo /usr/bin/openssl
/usr/bin/openssl
[/PHP]

This is a general trick in shells not just Makefiles

hope it helps

---

### Post by ranthal on 2009-03-12
Sure did, thanks a bunch.

---

