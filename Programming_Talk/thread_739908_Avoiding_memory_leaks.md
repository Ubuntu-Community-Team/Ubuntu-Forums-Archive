---
title: "Avoiding memory leaks"
date: 2008-03-30
forum: Programming Talk
---

### Post by nvteighen on 2008-03-30
Hi there!
I continue playing around with C and I'm a bit confused on when memory leaks can occur and how to avoid them.

This is what I believe I know: memory leaks occur (at least in C/C++) when a pointer losses it's reference basically because of being somehow overwritten with NULL.

Question 1: Why doesn't this occur with **all variables**? (e.g. int a = 3; )
Question 2: Is it necessary to use free() at the end of main() with all pointers, no mather if allocated with malloc() or not? (I understand you must use free() in functions to avoid loss of reference by going out-of-scope)
Question 3: Are arrays also affected by this?

Thanks!

---

### Post by napsy on 2008-03-30
Or you can use a garbage collector that automatically frees any allocated memory before the program quits.

For C/C++ there's a very good garbage collector named "Hans-Boehm garbage collector" and it's easy to use.

---

### Post by pmasiar on 2008-03-30
... or use language with automatic garbage collection, like Python :-)

---

### Post by stratavarious on 2008-03-30
.

---

### Post by CptPicard on 2008-03-30
> **nvteighen said:**
> 
I continue playing around with C and I'm a bit confused on when memory leaks can occur and how to avoid them.

A memory leak occurs when you allocate something on the heap and do not release it. You avoid memory leaks by always releasing what you allocate :) (in C, using the malloc/free pair of functions, in C++, using new and delete)

> 
This is what I believe I know: memory leaks occur (at least in C/C++) when a pointer losses it's reference basically because of being somehow overwritten with NULL.

Close, but not quite. You need to in general always deallocate each pointer you get from an allocation operation; you can "lose track" of that pointer in various ways, and overwriting with NULL is just one way to do it. You have always leaked memory when you no longer can tell what the pointer value was that you need to deallocate, and have not yet done so.

> 
Question 1: Why doesn't this occur with **all variables**? (e.g. int a = 3; )

Because it is on the stack, not on the heap. Stack is always allocated and deallocated automatically. In C++ there is a pattern called RAII that makes use of this fact in managing memory allocated on the heap.

> Question 2: Is it necessary to use free() at the end of main() with all pointers, no mather if allocated with malloc() or not?

If the intention is to just quit your program, no. The OS will knows what areas of memory are in use by your program, and just reclaims them when your process terminates.

> 
Question 3: Are arrays also affected by this?


If they  are on the stack, no... if your array is malloced/new'd on the heap, yes. :)

---

### Post by nvteighen on 2008-03-30
Then, in summary, the problem with what's in the heap and not in the stack.

Thank you all for your input!

---

### Post by ruy_lopez on 2008-03-30
Use mtrace() to help avoid memory leaks.

I usually try to keep memory management local to the function which allocates the memory. So if you allocate memory inside function A, function A calls another function B which does the work. B returns to A. Before A returns, it frees the memory.

In practice this isn't always possible.

---

### Post by nvteighen on 2008-03-30
> **ruy_lopez said:**
> Use mtrace() to help avoid memory leaks.
I have been using valgrind... I'm going to try mtrace() out whenever I can. Thanks!

> I usually try to keep memory management local to the function which allocates the memory. So if you allocate memory inside function A, function A calls another function B which does the work. B returns to A. Before A returns, it frees the memory.

In practice this isn't always possible.

Interesting approach... but it requires to double the number of functions declared for a single task! If the code is long enough, you may have a real mess in there...

---

### Post by ruy_lopez on 2008-03-30
> **nvteighen said:**
> I have been using valgrind... I'm going to try mtrace() out whenever I can. Thanks!


Valgrind is also good.

> **nvteighen said:**
> 
Interesting approach... but it requires to double the number of functions declared for a single task! If the code is long enough, you may have a real mess in there...

The number of functions isn't important. The important thing is that the function takes care of its own memory allocation/deallocation. That's the point I was trying to make.

---

### Post by nvteighen on 2008-03-30
Well, for curiosity, I've been running valgrind on some common applications like Evolution, gedit, including also /bin/ls and I found they have memory leaks... 

This is memory leak for just opening Evolution and closing it after having checked mail:
```

==6813== LEAK SUMMARY:
==6813==    definitely lost: 43,990 bytes in 235 blocks.
==6813==    indirectly lost: 82,044 bytes in 4,053 blocks.
==6813==      possibly lost: 364,860 bytes in 442 blocks.
==6813==    still reachable: 4,124,576 bytes in 36,726 blocks.
==6813==         suppressed: 0 bytes in 0 blocks.

```

That add ups to 4,615,470 bytes lost until I reboot!

I suppose it must be really difficult to get track of all memory allocation instructions in such a heavy program like that, isn't it?

---

### Post by napsy on 2008-03-30
There's a high chance that the output shows incorrent information becouse gtk+ has it's own memory management functions and valgrind cannot report memory usage correctly.

---

### Post by slavik on 2008-03-30
> **nvteighen said:**
> Well, for curiosity, I've been running valgrind on some common applications like Evolution, gedit, including also /bin/ls and I found they have memory leaks... 

This is memory leak for just opening Evolution and closing it after having checked mail:
```

==6813== LEAK SUMMARY:
==6813==    definitely lost: 43,990 bytes in 235 blocks.
==6813==    indirectly lost: 82,044 bytes in 4,053 blocks.
==6813==      possibly lost: 364,860 bytes in 442 blocks.
==6813==    still reachable: 4,124,576 bytes in 36,726 blocks.
==6813==         suppressed: 0 bytes in 0 blocks.

```

That add ups to 4,615,470 bytes lost until I reboot!

I suppose it must be really difficult to get track of all memory allocation instructions in such a heavy program like that, isn't it?
Linux collects unfreed memory when application exits.

---

