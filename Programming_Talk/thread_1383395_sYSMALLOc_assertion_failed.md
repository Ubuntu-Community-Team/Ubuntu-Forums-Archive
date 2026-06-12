---
title: "sYSMALLOc assertion failed"
date: 2010-01-17
forum: Programming Talk
---

### Post by tom66 on 2010-01-17
I have a program which relies on malloc, calloc and realloc to allocate data; it is written in C. 

However when I try to run it, the third calloc ALWAYS fails. The bug still happens when using malloc.

It is allocating space for nodes and routes on a map.

I get a bizarre sYSMALLOc assertion failure:

```

Calloc 1 * 8 bytes.
34689 nodes, 7803 ways.
Calloc 8 * 34689 bytes.
Calloc 8 * 7803 bytes.
a.out: malloc.c:3074: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted

```

(I am running on 64-bit; it is allocating 8 bytes for a pointer to a struct, times the number of ways.) 

I have some functions, named chk_malloc, chk_calloc, and chk_realloc. These allocate memory, but they check for NULL pointers, and abort if they couldn't allocate the memory. In this case, m/c/realloc never return; they die on an assertion error.

```


void *chk_malloc(size_t size)
{
    printf("Malloc %ld bytes.\n", size);
    void *ptr = malloc(size);
    if(!ptr) {
        fprintf(stderr, "Failed to malloc %ld bytes. Aborting.\n", size);
        exit(1);
    }
    return ptr;
}

void *chk_calloc(size_t size, size_t count)
{
    printf("Calloc %ld * %ld bytes.\n", size, count);
    void *ptr = calloc(size, count);
    if(!ptr) {
        fprintf(stderr, "Failed to calloc %ld bytes. Aborting.\n", size * count);
        exit(1);
    }
    return ptr;
}

void *chk_realloc(void *ptr, size_t size)
{
    printf("Realloc %p to %ld bytes.\n", ptr, size);
    void *new_ptr = realloc(ptr, size);
    if(!new_ptr) {
        fprintf(stderr, "Failed to realloc %p to %ld bytes. Aborting.\n", ptr, size);
        exit(1);
    }
    return new_ptr;
}

```

The weirdest part of this, is that it only started recently. Before, it was happily allocating the memory. Could it be some system change? Or is there a known bug?

---

### Post by tom66 on 2010-01-17
Here's something interesting. From advice on the 'net, I set $MALLOC_CHECK_ to 1. This means if it detects a problem, it prints a warning, but continues anyway. Now I get a warning:

```

*** glibc detected *** ./a.out: malloc: top chunk is corrupt: 0x0000000001e2f270 ***

```

But it doesn't crash. Still, this looks like a fairly major bug. What does it mean, top chunk corrupt?

---

### Post by MadCow108 on 2010-01-17
have you run it through valgrind to see if your corrupting something?

crashes in malloc are usually do to something overwriting some memory malloc uses internally

---

### Post by tom66 on 2010-01-17
Valgrind tells me I've got lots of invalid reads and writes. Ah well, back to understanding pointers I guess.

---

