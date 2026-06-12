---
title: "C/C++ free() question"
date: 2011-03-12
forum: Programming Talk
---

### Post by t1497f35 on 2011-03-12
Hi,
Say I got a char* string on the heap which I'll later need to free():
char ***str**;
with the value "*fruit=apple*"

Now I don't need to copy any part of the string - I just gotta check the key/value pair, so to avoid a (memory) copy I do a straightforward "split":

int index ..//holds the index of '=' in **str**
**str**[index] = 0;//split the string into key/value
char *key = **str**;
char *value = **str**[index+1];

There we go, no copy, yet I have a handy key/value pair to work with.

The question is, since I assigned a zero somewhere in the middle of the char* string, when I do **free(str)** - will it free the whole string or **only** the part till where it finds the **zero** assigned by me (somewhere) in the middle?

---

### Post by MadCow108 on 2011-03-12
it will always free all.
the memory allocator does not care what is in the memory it frees.
It has its own internal management information to keep track of allocated and freed blocks.

---

