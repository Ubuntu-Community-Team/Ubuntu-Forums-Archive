---
title: "Anyone know of fixed-length ArrayList implementation -- drops elements older than x?"
date: 2010-03-27
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-03-27
I need an indexable collection, similar to Java's ArrayList, but the idea is that I only want it to store x number of elements, where I can decide what x is.  In other words, the size of the array grows up to some number, but will not exceed that number.  If the array has hit its size limit, then adding an element will cause the element at index 0 to pop off and be forgotten.  I would implement this using a linked list, very similar to ArrayList, but before doing so, does this type of collection already exist?

I'm currently simulating this behavior by checking size on the arraylist after an insertion and deleting an element if it's larger than some number.  I figure there's a more efficient way.

---

### Post by dwhitney67 on 2010-03-27
For the simple requirements you have specified, you will not find a more efficient container than a list.  You insert at the end, and retrieve (remove) from the front.

You did not indicate which language you wanted to implement this container in.  Recently, I developed in C++ a container similar to what you describe, using of course, the STL list and a pthread mutex to ensure that it would be thread-safe.

---

### Post by Reiger on 2010-03-27
I  suggest you do not implement this via a LinkedList because you'll be fighting the underlying implementation. Rather it will be more convenient (and more efficient because you do not need to implement growth) to use an array as backing for an AbstractList.

---

### Post by CptPicard on 2010-03-27
This suggestion is somewhat memory-inefficient, but take a look at LinkedHashMap. It's both "indexable" in the sense a hash is, and retains insertion order by keeping a linked list of items.

Also, depending on what kind of indexing behaviour you actually want, in your case I would also consider the possibility of writing a "queue in an array" that wraps around the end of the array by use of the modulus operator. But, I don't really know how you expect the indexes to behave after removal of an item.

---

### Post by dwhitney67 on 2010-03-27
> **CptPicard said:**
> 
Also, depending on what kind of indexing behaviour you actually want, in your case I would also consider the possibility of writing a "queue in an array" that wraps around the end of the array by use of the modulus operator. But, I don't really know how you expect the indexes to behave after removal of an item.
This seems like the description of a circular queue.

---

### Post by lisati on 2010-03-27
> **dwhitney67 said:**
> This seems like the description of a circular queue.

+1

For some reason, when I was reading this thread, it occurred to me that popping item 0 off a list and moving the rest of the items up would be fairly straightforward in ASM if the list was stored as an array in contiguous memory and if there aren't any pointers to mess arouind with. Then for some reason the Z80 opcode "ldir" came to my recollection, possibly because I might have done something similar on one of my old machines. I haven't done any z80 programming for nearly 20 years. Hmmmm......

---

### Post by CptPicard on 2010-03-27
> **dwhitney67 said:**
> This seems like the description of a circular queue.

Yeah, except that in my mind a "circular queue" tends to be a circular linked list structure. This is more of a "circular buffer" in typical parlance IMO.

---

