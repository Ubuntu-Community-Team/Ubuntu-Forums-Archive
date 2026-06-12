---
title: "Memory Management Help"
date: 2010-11-17
forum: Programming Talk
---

### Post by racrbilly67 on 2010-11-17
Hello,

I am working on writing a version of malloc(), realloc(), and free() for a class project. We are having a contest to see if we can create an algorithm that is faster and more efficient than the libc version. My question really is what is an efficient data structure that we can use to keep track of our lists of alloc'd and free'd memory chunks. Currently we are using a doubly linked list with head and tail pointers utilizing a first fit method. And we are still very slow when we have 400,000 alloc() and realloc() calls. Does anyone have any ideas or some place I could go read and try and figure out how to make ours faster/more efficient? Other things I have heard of are to try "binning" the lists by creating different groups of sizes, also using a circular linked list and trying best fit over first fit. Any suggestions?

We are programming in C, in case this matters.

Thanks for the help guys!

---

### Post by worksofcraft on 2010-11-17
> **racrbilly67 said:**
> Hello,

I am working on writing a version of malloc(), realloc(), and free() for a class project. We are having a contest to see if we can create an algorithm that is faster and more efficient than the libc version...


As long as there is a large contiguous free store to carve up you won't have many problems, but once your heap is all fragmented it gets complicated.

My initial thought is to keep two indexes to the free heap: One sorted on size and the other on address. That way you can quickly pick an existing block of the correct size and also quickly spot when adjacent blocks are free so you can merge them back together. For efficient indexing and allocation you can use a balanced binary tree structure and hopefully you can find convenient tried and tested functions to manage these in C. The free blocks themselves can contain pointers back to their indexes.

Do keep in mind though that the system heap has advantage of using virtual memory management hardware in the kernel ;)

---

### Post by Arndt on 2010-11-17
> **racrbilly67 said:**
> Hello,

I am working on writing a version of malloc(), realloc(), and free() for a class project. We are having a contest to see if we can create an algorithm that is faster and more efficient than the libc version. My question really is what is an efficient data structure that we can use to keep track of our lists of alloc'd and free'd memory chunks. Currently we are using a doubly linked list with head and tail pointers utilizing a first fit method. And we are still very slow when we have 400,000 alloc() and realloc() calls. Does anyone have any ideas or some place I could go read and try and figure out how to make ours faster/more efficient? Other things I have heard of are to try "binning" the lists by creating different groups of sizes, also using a circular linked list and trying best fit over first fit. Any suggestions?

We are programming in C, in case this matters.

Thanks for the help guys!

What are your memory management primitives? Are you given a big area of memory, or do you for example use brk/sbrk yourselves?

Remember that different allocation schemes are good for different things. Yours may be better than libc in some respects, but worse in others. For example lots of small allocation of same-sized blocks, versus a very mixed scenario, with many frees.

---

### Post by dwhitney67 on 2010-11-17
> **racrbilly67 said:**
> Other things I have heard of are to try "binning" the lists by creating different groups of sizes, also using a circular linked list and trying best fit over first fit. 

This approach was used on a embedded s/w project I supported 8 years ago.  In lieu of the circular linked list, a (message) queue was used to store the available blocks of memory for each group (pool) of available data block sizes.

Whereas this approach seems practical, it is by no means a trivial endeavor.  You would have to implement the API to substitute malloc() and free(), and you would have to define a structure-type to define a memory block; this structure would contain information about which pool the block originated from, as well as whether there are additional blocks associated with it (eg. when one allocates an array).  The callee requesting the block(s) of memory should never "see" this ancillary data; they should only have a reference to the block(s) of memory they are permitted to use.

With embedded systems, surprises are not welcome.  Thus it is typical to employ a memory manager which must be used to obtain available memory.  This prevents one module with a runaway desire to continue allocating more and more memory from bringing down the entire system.

P.S.  I was not directly involved with how the Memory Manager was designed on the project I referred to above; thus my recollection of how it was designed/implement may not be entirely accurate.

---

