---
title: "Avoiding Allocation"
date: 2009-03-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-03-29
I am working on writing my own programming language (Lisp), and in the process I began to look at some languages allocation usage.

scm never allocates
python allocates a lot

for each language I did an equivalant task.


How would a language avoid allocation?
Should I avoid allocation?
Is allocation slow?

---

### Post by CptPicard on 2009-03-29
> **Mr.Macdonald said:**
> 
scm never allocates

Err... what?

Yes, it does. Lisps typically manage allocation through garbage-collected cons pairs.

---

### Post by Mr.Macdonald on 2009-03-29
I ran scm under valgrind and here is the closing message, (opening was huge!)
```
> (define (mult a b)
> (* a b (+ a b)))
#<unspecified>
> (mult 3 4)
84
> (quit)
;EXIT
==20021== 
==20021== ERROR SUMMARY: 1725 errors from 62 contexts (suppressed: 29 from 1)
==20021== malloc/free: in use at exit: 0 bytes in 0 blocks.
==20021== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==20021== For counts of detected errors, rerun with: -v
==20021== All heap blocks were freed -- no leaks are possible.

```

maybe the errors include allocations?

---

### Post by nvteighen on 2009-03-29
Valgrind is not infallible... It's useless with threaded applications and other sort of programs.

---

### Post by jimi_hendrix on 2009-03-29
i was messing around in python and got:

```

==10520== LEAK SUMMARY:
==10520==    definitely lost: 0 bytes in 0 blocks.
==10520==      possibly lost: 5,714 bytes in 117 blocks.
==10520==    still reachable: 2,299,780 bytes in 2,820 blocks.
==10520==         suppressed: 0 bytes in 0 blocks.

```

---

### Post by Mr.Macdonald on 2009-03-29
So, Lisp is just multi threaded (as it should be).

Then I won't worry about allocation (for the most part).

---

### Post by CptPicard on 2009-03-29
I don't know about valgrind, but the idea that Scheme doesn't allocate on the heap is certainly nonsensical, and threading should not have anything to do with it. Write something with "cons" in it (create lists or what have you) and the cons pair certainly goes on the garbage-collected heap. Same with lambdas' closures; you just can't keep the Scheme environment frames on the call stack as they live longer than the call they are created in.

Try actually implementing a Scheme without malloc and you'll quickly see what I mean.

Another point to notice that in this specific case, your very trivial example actually can be compiled into just a normal call that just uses stack.

---

### Post by monkeyking on 2009-03-29
> **nvteighen said:**
> Valgrind is not infallible... It's useless with threaded applications and other sort of programs.

I've never used valgrind for threaded applications.
But I think you can use it.(pthread)
It however doesn't use the standard linux schedular,
just a simple roundrobin one.

It also has a racecondition checker called helgrind,
which I've never used either.

---

