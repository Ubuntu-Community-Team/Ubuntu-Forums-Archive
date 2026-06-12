---
title: "is it possible to profile a function c/c++"
date: 2008-12-31
forum: Programming Talk
---

### Post by monkeyking on 2008-12-31
I've got some code,
that is quite so slow.
So I compiled it with -pg.
ran it through gprof and the kprof.

And theres a single function, that is rather large,
that takes up 97% of the program.

Does anyone know I can get more elaborate info,
on where in the function it takes place.

---

### Post by mbsullivan on 2008-12-31
OProfile ([http://oprofile.sourceforge.net/about/](http://oprofile.sourceforge.net/about/)) can go down to the instruction level.

There's probably an easier option, though... OProfile requires kernel support.

Mike

PS: If you're checking out OProfile, what I think you'd be interested in is "annotated source".

---

### Post by ankursethi on 2008-12-31
I've never used it, but I hear good things about this : [http://valgrind.org/](http://valgrind.org/)

---

### Post by mbsullivan on 2008-12-31
> I've never used it, but I hear good things about this : [http://valgrind.org/](http://valgrind.org/)

Valgrind is used mainly to detect memory leaks, but it does have the ability to profile, as well.

I'm not sure if it can go down to the instruction level, though. 

One plus is that it doesn't require recompilation -- You can use it with your optimized binaries. It's definitely cool, and something that I've always meant to learn more about :)

Mike

---

### Post by dribeas on 2008-12-31
> **monkeyking said:**
> I've got some code,
that is quite so slow.
So I compiled it with -pg.
ran it through gprof and the kprof.

And theres a single function, that is rather large,
that takes up 97% of the program.

Does anyone know I can get more elaborate info,
on where in the function it takes place.

A function taking most of the execution time can be one of two things: the function is slow, or it is being called too many times. Check which is your case, and if it is being called many times whether it is necessary.

If as you stated the function is too big, then it might be the case that breaking it into smaller functions will not only improve your code but help with your profiling.

---

### Post by Bichromat on 2009-01-01
you can use gprof -l (this is L) which gives you line by line profiling.

---

