---
title: "make problem"
date: 2011-10-20
forum: Packaging and Compiling Programs
---

### Post by Seimen on 2011-10-20
When I try to make with a Makefile that worked before I get the message:

bin/sh: **g+**: not found  (**not g++)**

I checked the Makefile and also downloaded it again (it's from my university)
I reinstalled g++,make and gcc but I always get this message.

---

### Post by gmargo on 2011-10-20
You can post the Makefile here if you'd like us to take a look at it.

Failing that, get to work reading the **make(1)** man page.  Pay particular attention to the "-p" (--print-data-base) option.

Compare the difference between these two commands.  The first will give only defaults while the second takes your Makefile into account.
```

make -p -f /dev/null

make -p

```Check the outputs for "g+" and "CXX".

---

### Post by waltsullivan on 2011-10-20
And, check your environment [FONT="Courier New"]env | grep g\+[/FONT]

---

### Post by LucasCube on 2011-10-21
.. nvm

---

