---
title: "What does it mean by 'invalid pointers' in C++"
date: 2007-06-19
forum: Programming Talk
---

### Post by Lina_inpas on 2007-06-19
Hihi
I just did a small programming and after compiling there was no error. 
But after I run it, it says 'free(): invalid pointer: 0x0804d0f8 ***'
I have read my codes several times, it seems there is no logical mistake.
So, normally what causes the error ' invalid pointer' when using C++?
thanks a lot.

---

### Post by Arndt on 2007-06-19
> **Lina_inpas said:**
> Hihi
I just did a small programming and after compiling there was no error. 
But after I run it, it says 'free(): invalid pointer: 0x0804d0f8 ***'
I have read my codes several times, it seems there is no logical mistake.
So, normally what causes the error ' invalid pointer' when using C++?
thanks a lot.

"free(): invalid pointer" probably means that the function 'free' was given a pointer which did not point to an allocated memory area. Even if you don't call 'free' yourself, deleting an object probably does. Either you have done 'delete' on something which was not an object, or something else has happened that has corrupted the memory structure, like writing outside an array.

I recommend using the program 'valgrind' to find the error. But if the program is very small, someone may perhaps see the error just by looking at it.

---

### Post by Lux Perpetua on 2007-06-19
If you're getting that error, then your code definitely has a bug. The semantics of that error are exactly what Arndt said. You can only free() a pointer that was returned by a previous call to malloc, calloc, or realloc. Moreover, you cannot free a pointer twice. If you violate this, *and you're lucky*, then you'll see an error. Otherwise, your program might appear to work now and puzzlingly fail later.

---

