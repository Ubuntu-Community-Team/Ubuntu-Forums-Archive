---
title: "Why do environment variables not show up in Makefiles?"
date: 2008-04-10
forum: Programming Talk
---

### Post by stair314 on 2008-04-10
Some of my environment variables are not showing up if I try to access them from in a makefile. For example, if I run
echo ---${MACHTYPE}--- 
in a terminal I get
---x86_64-pc-linux-gnu---

as expected. If I put the exact same line in a rule in a makefile, I get
------

I've also tried using parens instead of braces. Interestingly, other environment variables such as PATH work fine, but MACHTYPE and HOSTTYPE show up as the empty string. Does anyone know why this is happening?

---

### Post by WW on 2008-04-10
Use **export** for the variables that you want to be seen by the **make** command.  E.g.
[php]
$ cat Makefile

all:
        @echo ${MACHTYPE}

$ make

$ export MACHTYPE
$ make
x86_64-pc-linux-gnu
$ 
[/php]

---

