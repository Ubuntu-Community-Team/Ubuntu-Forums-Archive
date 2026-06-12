---
title: "Question about a C assignment I have"
date: 2009-11-21
forum: Programming Talk
---

### Post by ownaginatious on 2009-11-21
I'm currently in a class were we're learning C, and I'm having trouble understanding an instruction on my assignment. I know this is a weird place to be bringing a homework question, but it's  one of the few sites I'm registered on with a programming forum that's actually active.

Anyway, I was hoping someone here could potentially explain a part of it to me. The assignment is [here.]("http://hygelac.cas.mcmaster.ca/courses/SE-2S03-09/assignments/assign5.pdf")

The part I don't understand is 3 b).

Now, would that mean something along the lines of the following?:

```

typedef struct {
   vector seq[MAX_SEQ_LENGTH];
   int size;
} vec_store;

```

I actually got the whole thing working with that, but now looking back the 'pointer' part of the instruction is throwing me off.

Any help or insight would be greatly appreciated.

Thanks!

---

### Post by Arndt on 2009-11-21
> **ownaginatious said:**
> I'm currently in a class were we're learning C, and I'm having trouble understanding an instruction on my assignment. I know this is a weird place to be bringing a homework question, but it's  one of the few sites I'm registered on with a programming forum that's actually active.

Anyway, I was hoping someone here could potentially explain a part of it to me. The assignment is [here.]("http://hygelac.cas.mcmaster.ca/courses/SE-2S03-09/assignments/assign5.pdf")

The part I don't understand is 3 b).

Now, would that mean something along the lines of the following?:

```

typedef struct {
   vector seq[MAX_SEQ_LENGTH];
   int size;
} vec_store;

```

I actually got the whole thing working with that, but now looking back the 'pointer' part of the instruction is throwing me off.



What does your code for 3c, make_vec_store, look like?

(I see they are using TeX - that's nice.)

---

### Post by MadCow108 on 2009-11-21
its really not quite clear what they want.
I see four simple possibilities:
1. the one you made, the constructor is now trivial, no real deletion possible (just reordering beyond size)
2. use heap allocated memory, constructor uses malloc, now you have a pointer in your struct, real deletion now possible but expensive (needs reallocation and reordering of memory)
3. use stack array of pointers to vectors, this now allows deletion of heap vectors without reallocation but still needs reordering
4. use heap allocated memory of pointers to vectors, like 3. plus you can shrink the data size by reallocating it if necessary

I recommend doing them all and learn how the internals of the member functions change with the different possibilities.

---

### Post by PmDematagoda on 2009-11-21
No homework questions here please. Thread closed.

---

