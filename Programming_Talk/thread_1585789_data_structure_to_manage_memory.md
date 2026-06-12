---
title: "data structure to manage memory"
date: 2010-10-01
forum: Programming Talk
---

### Post by jamesbon on 2010-10-01
I am working on a problem (re inventing the wheel for learning)
I have a mxn matric (which is my simplified way of saying it is RAM with bytes on it)
Some of the locations on this metric is filled with some data and some places are empty.
The mxn are very big numbers in size.
I am trying to make a program so that if a system call wants to write some thing on empty locations on this mxn metric it should be able to do so without any problem.
The thing which I want to understand or logic of a data structure is what data structure do you people feel should I be maintaining so that I can allocate the requested space immediately from the above mxn matric when some system call requests for some (k) number of locations from above metrics.


The logic initially I thought was to maintain a hashtable

1bytes requested----------> location 1,location 2,location 3.........location n
2bytes requested----------> location 1,location 2,location 3.........location n
3bytes requested----------> location 1,location 2,location 3.........location n
4bytes requested----------> location 1,location 2,location 3.........location n
.
.
.
nbytes requested----------> location 1,location 2,location 3.........location n

but the problem with above logic is size of the pointers where I will be writing this problem is unsigned 64 byte.So to know location of one free byte if I am maintaining one pointer of type u64 this is not a feasible solution.
Can you people suggest me some logic,idea,algorithm for the same.

---

### Post by DanielWaterworth on 2010-10-01
you could use a pool allocator, then your address size would be smaller.

---

### Post by worksofcraft on 2010-10-01
If I understand you correctly this is essentially a "sparse matrix" that you are trying to implement. That is **most** of your matrix you expect will be empty and so you just want to store the locations that **do** hold data.

The way I would do it is with a sorted tree structure. The nodes identify address ranges and the leaves are ordinary arrays holding the data for those ranges. By keeping the tree sorted and balanced you should be able to keep the access time quite low, but it still has to hunt down the tree to find the array for any address, or to discover that the space is still vacant.

Evidently if you plan to fill most of the matrix with genuine data then the only solution is to allocate space for it all.

---

### Post by jamesbon on 2010-10-01
Ok both the suggestions were great but what is a pool allocator (just want to know)
I am curious to know more ways of achieving this.
Since I am in learning phase so any thing that any one tell me will be beneficial.
I am writing my implementation of this so I may not use any standard library or header file.

---

### Post by worksofcraft on 2010-10-01
hum... well [perhaps this explains the idea better]("http://en.wikipedia.org/wiki/B%2B_tree")

---

### Post by nvteighen on 2010-10-01
First, a tip: don't work with a huge matrix. It's useless: if your idea is right, it should work for any m, n. And starting at small values may help you test the thing more easily.

Second. If what you want is to create a rough virtual memory system, you don't need a mxn matrix, but something that **behaives like** an array of n elements. I stress the **behaives like** because that's what your interface should provide, but you may need something else to implement it. Why should the interface be "like an array", well, because there aren't two dimensions, just one: memory should be a contiguous address space, so you only have to deal with one address space :P Actually an array could be all you need...

You already see the problem is addressing, not storing... or in other words, how do I assign a way to identify a chunk of data stored in that memory. Well, you could use the array's indices... that's what memory addresses are: 0x000000 (I'm on 32-bit) is like saying my_memory[0]. So, you need a device that does what the CPU does with memory: "get an index and search in the array using that given index".

Third. Don't think about system calls because that'd be almost like creating a virtual machine that's able to emulate some platform's system calls so that "your" memory pool is used instead of the system's (well, actually it's all the system's, but you get the idea)... Think more on an abstract rough representation of what the computer does.

No, I'm not sure how I'd do this, but these are my basic intuitions about the issue. By the way, what language are you using for this?

---

### Post by DanielWaterworth on 2010-10-02
> **jamesbon said:**
> what is a pool allocator (just want to know)

A pool allocator is a memory allocator that allocates fixed sized blocks of memory. This means that you can reference a piece of memory using log 256 of the maximum number of allocations bytes. If you have a pool allocator for each matrix, which forces an upper limit on the size, this would be a small number, maybe 2 or 3 bytes. On a 32bit computer this is a saving in memory of 25-50%, on a 64bit computer, this saving is 62.5%-75% over using regular pointers.

---

### Post by jamesbon on 2010-10-02
Hmmm,
ok some one also suggested me glibc implements this via heaps.
If some one understands what I just said can you give me a link because I am not clear as where to start with.

---

