---
title: "[SOLVED] Changing optimization level in an unfamiliar Makefile"
date: 2008-02-12
forum: Programming Talk
---

### Post by apetresc on 2008-02-12
Hey, guys.

I'm trying to do some C development using the Eclipse CDT. I'm modifying a Makefile project that someone else wrote, and it mostly works fine (builds, runs, in Eclipse without any problems). The only issue is when I try to debug: the Makefile builds it with -O2 optimization so that when I run the debugger, things aren't quite right. Some variables have evidently been optimized out of existance, line numbers are slightly off in some places, and other oddities. The solution to this problem is obviously to set -O0 but I'm having some trouble doing that.

The Makefiles I've used in the past would specify a variable up top like ```
DEBUG="O2"
```, and then it would call ```
$CC -$DEBUG
```. This is easy to deal with. However, the Makefile I'm working with now just has lines like: ```
gnushogi_compile:
	-cd $(GNUSHOGIDIR); $(MAKE) gnushogi
```
I'm guessing that the $(MAKE) variable somehow encodes things like optimization levels, but I have no idea where I'd go to change it.

I tried Google'ing $(MAKE) but Google doesn't do special characters so it just searched for "make" and obviously that's not very productive... :)

Any help would be greatly appreciated!

---

### Post by apetresc on 2008-02-12
Oh, wow, I'm such a loser. It just calls make on the Makefile in the given subdirectory. THAT Makefile has a regular format that I'm familiar with. I just have to change *that*.

I should have noticed this an hour ago; I feel silly. Thanks anyway, guys!

---

