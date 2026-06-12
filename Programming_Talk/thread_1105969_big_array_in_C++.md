---
title: "big array in C++"
date: 2009-03-25
forum: Programming Talk
---

### Post by flylehe on 2009-03-25
Hi,
I am now considering creating a big array, like 3.61696e+08 elements, where each element is also an array of 24*24 integers. I guess it is impossible in terms of memory, so I'd like to know how to do memory planning when writing C++ code. Here is what I've learned so far.Please correct me if I am wrong.

1. firstly notice that the index can only be integer type, so the number of elements could not be greater than the maximum value of  long long unsigned integer;

2. secondly "a n-bit OS will not allow you to allocate more than 2^n bytes". This is what I learned from somewhere in the internet. Why is it?

3. Finally the memory of my code cannot exceeds the amount of RAM plus swap size. IN bash, how can I get the size of RAM and swap?

Some other questions:

1. Is there something handy that could tell how much memory my code would use? If it exists, does it require running the code or not?

2. If I try to avoid large sized array in cost of computational time, are multiple thread and parallel programming good way to accelerate the program running? 

Thanks a lot!

---

### Post by dwhitney67 on 2009-03-25
> **flylehe said:**
> Hi,
I am now considering creating a big array, like 3.61696e+08 elements, where each element is also an array of 24*24 integers. ...

Please tell us why you would contemplate such a thing?  Are you attempting to create an inventory of each of the stars in the heavens, or perhaps keep a record for each grain of sand at all of the beaches in the world?

---

### Post by flylehe on 2009-03-25
Dear dwhitney67,
In my case, it would be great if it is possible to create all possible images of 24 by 24 with 4 non-overlapping boxes within its central 15 * 15 region. Hope this could meet your curiosity. 
Could you answer my questions please? Thanks!

---

### Post by dwhitney67 on 2009-03-25
Then create the images as needed, but do not attempt to store each and every one of them.  I cannot imagine any application that would need to hold such vast amount of data in memory.  Perhaps you can create individual images, and store them in a database or a file... but even then, it seems overkill.

---

### Post by flylehe on 2009-03-25
By "store them in a database or a file... but even then, it seems overkill", you mean the file or database is too big to read? By the way, I totally agree with you not to store but to create each image only when needed.

Could you please also look at my original questions:

> 
I'd like to know how to do memory planning when writing C++ code. Here is what I've learned so far.Please correct me if I am wrong.

1. firstly notice that the index can only be integer type, so the number of elements could not be greater than the maximum value of long long unsigned integer;

2. secondly "a n-bit OS will not allow you to allocate more than 2^n bytes". This is what I learned from somewhere in the internet. Why is it?

3. Finally the memory of my code cannot exceeds the amount of RAM plus swap size. IN bash, how can I get the size of RAM and swap?

Some other questions:

1. Is there something handy that could tell how much memory my code would use? If it exists, does it require running the code or not?

2. If I try to avoid large sized array in cost of computational time, are multiple thread and parallel programming good way to accelerate the program running?

Thanks a lot!


---

### Post by cabalas on 2009-03-25
> **flylehe said:**
> Hi,
2. secondly "a n-bit OS will not allow you to allocate more than 2^n bytes". This is what I learned from somewhere in the internet. Why is it?


It can only allocate 2^n bytes because it can only memory addresses of n bits which leaves it with an upper limit on the memory any architecture can handle.  There are ways around this, I believe the i686 kernel can address more than 4 gigs of memory - can't say I know how off the top of my head though.

---

### Post by flylehe on 2009-03-25
So it is "2^n bytes"  not "2^n element-type size" because the memory address is only in terms of bytes?
I am not sure it is coincident that for 64-bit OS, 2^64 = 1.8446744073709552e+19, which is the same as the maximum value of a long long unsigned int can take. This seems to be equivalent to the first point in my original post that "the number of elements could not be greater than the maximum value of long long unsigned integer". But for 32-bit OS, 2^32 =  4294967296.0 while the maximun value of a long long unsigned int can still take as big value as 1.8446744073709552e+19. So the two points are likely not the same, but are similar in that both have something to do with the memory addressing?

---

### Post by kjohansen on 2009-03-25
EDIT: I know see that you said get, not set...

> **flylehe said:**
> 
3. Finally the memory of my code cannot exceeds the amount of RAM plus swap size. IN bash, how can I get the size of RAM and swap?


you can never set the size of RAM.  The amount of RAM you have is the amount that is installed.  You can change the SWAP size since it is a parititon on your harddirve, but that cannot be done through bash.  You would need to use a partition editor.

---

### Post by kjohansen on 2009-03-25
> **flylehe said:**
> 
2. If I try to avoid large sized array in cost of computational time, are multiple thread and parallel programming good way to accelerate the program running? 
Thanks a lot!

Parallel solutions are not universal, they are very specific to what you are trying to do.

If there are dependencies among your data then parallel solutions may not be that great because of the communication need..  If the elements are independent of each other then parallel solutions will have a greater return.  

But if they are independent of each other there is no reason to have an array allocated to hold them all at one time as dwhitney mentioned, you should rather process them in batches.

---

### Post by cabalas on 2009-03-25
> **flylehe said:**
> So it is "2^n bytes"  not "2^n element-type size" because the memory address is only in terms of bytes?
I am not sure it is coincident that for 64-bit OS, 2^64 = 1.8446744073709552e+19, which is the same as the maximum value of a long long unsigned int can take. This seems to be equivalent to the first point in my original post that "the number of elements could not be greater than the maximum value of long long unsigned integer". But for 32-bit OS, 2^32 =  4294967296.0 while the maximun value of a long long unsigned int can still take as big value as 1.8446744073709552e+19. So the two points are likely not the same, but are similar in that both have something to do with the memory addressing?

To the best of my knowledge type sizes do not have something to do with memory address. It depends on the architecture and OS on how big certain types are (which is pretty much everything except a char).  This can even be different between different 32 bit cpu architectures as some might define an int as 2 bytes while others might define it as 4.

Now it's been a while since I did all this theory back in uni, so some points might be a little off as my memory is fuzzy - so please someone who knows better correct me where I'm wrong.

---

### Post by Can+~ on 2009-03-25
> **flylehe said:**
> Hi,
2. secondly "a n-bit OS will not allow you to allocate more than 2^n bytes". This is what I learned from somewhere in the internet. Why is it?

Pointers are numbers too, your average pointer on 32-bit is 4 bytes long, therefore, you can only address memory between 0 and (2^32)-1, which almost 3~4 [MB] of memory.

> **flylehe said:**
> 1. Is there something handy that could tell how much memory my code would use? If it exists, does it require running the code or not?

Yeah, a calculator: (24*24) * 4 (size of an int in 32-bit) * 3.61696e+08 = 833347584000 [Bytes] = 776.115 [GB]

> **flylehe said:**
> 2. If I try to avoid large sized array in cost of computational time, are multiple thread and parallel programming good way to accelerate the program running?

Depends on the algorithm in question. As for having to transverse that vast amount of memory you mentioned, I think you should rethink your solution.

*edit: Now that I read the whole post and the problem. Hard disks exist for a reason, to avoid having to store that insane amounts of data in memory.

Work your algorithm to create the image and buffer it to the hard disk as needed, in that case, no amount of multi threading will help you out, since you'll have the bottleneck at the hard disk writing speed.

People come with every crazy idea...

---

### Post by flylehe on 2009-03-25
Again, thanks a lot to all of you for these valuable info and advice!

Please excuse me for putting my problem in a simplified way. Given a test image, I have to compute some value between the test image and each template image and then sum the values up over 3.61696e+08 template images, which takes my office's cluster 20 minutes. 

Furthermore I am asked to do this for 10000 test images. As you can see the processing for each test image is independent, so I believe multiple thread programming might be able to help me to get the results as fast as possible.

There are 3.61696e+08 intermediate values, each of which is for each template image, that are repeatedly used by all test images. But it is a pity that I don't have a way to store pre-computed 3.61696e+08 such values.

If you have some other advice, please don't hesitate to post here. Thanks!

Can+~:
1.By "buffer it to the hard disk", do you mean writing it to a file in the hard disk? Stored with all those images, the file would be very large and extremely slow to read.
2. 2^32 = 4.294967296e9 bytes. Is it really only "3~4 [MB] of memory"?
3. the memory my code would use will not only include the array, but also other variables and functions. If the codes are long and in multiple files, it will be handy if some gadget can do the space computation for human being.

kjohansen:
I meant what is the bash command to tell how much are the sizes of RAM and swap in a system?

Thanks!

---

### Post by Can+~ on 2009-03-25
> **flylehe said:**
> Please excuse me for putting my problem in a simplified way. Given a test image, I have to compute some value between the test image and each template image and then sum the values up over 3.61696e+08 template images, which takes my office's cluster 20 minutes.

Oh well, never thought you would have access to a cluster.
 
> **flylehe said:**
> 2. 2^32 = 4.294967296**e**9 bytes. Is it really only "3~4 [MB] of memory"?

4294967296 [B] = 4194304 [KB] = 4096 [MB] = 4 [GB]

Seriously, is not that hard math, consider each byte on your memory going from 0 to 2^32-1. Of course, in 64 bit architecture this is far more. And I guess your cluster is all 64-bit.

> But for 32-bit OS, 2^32 = 4294967296.0 while the maximun value of a long long unsigned int can still take as big value as 1.8446744073709552e+19.

long long int, even on 32 bit architecture use 8 bytes.

[http://en.wikipedia.org/wiki/Integer_(computer_science](http://en.wikipedia.org/wiki/Integer_(computer_science))

---

### Post by JohnLM_the_Ghost on 2009-03-26
> **flylehe said:**
> Given a test image, I have to compute some value between the test image and each template image and then sum the values up over 3.61696e+08 template images, which takes my office's cluster 20 minutes. 

Furthermore I am asked to do this for 10000 test images. As you can see the processing for each test image is independent, so I believe multiple thread programming might be able to help me to get the results as fast as possible.

Hmm depending where you intend to put the resulting data... it might or might not be smart to use threads.
If it is intended to be written on hard drive, the speed gain would be quite minimal, cause writing would make a bottleneck.

So where do you keep those template images? If they are on hard drive, you should stream them to a FIFO list or similar data-type, so only needed ones are kept within memory. (array will also do I you code it right and avoid overflows)

And yes... I'm wondering what is the actual purpose of this program? I know I tend to put huge amounts of data in memory, but whew... yours is a giant!

---

### Post by lisati on 2009-03-26
> **flylehe said:**
> Hi,


2. secondly "a n-bit OS will not allow you to allocate more than 2^n bytes". This is what I learned from somewhere in the internet. Why is it?



The OS will use n **b**inary dig**its** to form a numerical address for any particular memory location. The largest possible (unsigned) number you can hold in n bits is 2^n-1

Hope this explanation makes sense.

---

### Post by Simian Man on 2009-03-26
Even if you had enough memory, you would never be able to allocate that much memory without modifying libc (malloc has a limit that is much lower than this) and likely the kernel as well.  Considering that you had to ask how much data 32 bits can address, I'd say you have little chance succeeding in that.

Rethink your algorithm such that you can recompute images as you need them or, if you must store them, store them on disk and cache a subset in memory as you need them.

---

### Post by quip on 2009-03-26
> **flylehe said:**
> Hi,
I am now considering creating a big array, like 3.61696e+08 elements, where each element is also an array of 24*24 integers. I guess it is impossible in terms of memory, so I'd like to know how to do memory planning when writing C++ code. Here is what I've learned so far.Please correct me if I am wrong.

1. firstly notice that the index can only be integer type, so the number of elements could not be greater than the maximum value of  long long unsigned integer;

2. secondly "a n-bit OS will not allow you to allocate more than 2^n bytes". This is what I learned from somewhere in the internet. Why is it?

3. Finally the memory of my code cannot exceeds the amount of RAM plus swap size. IN bash, how can I get the size of RAM and swap?

Some other questions:

1. Is there something handy that could tell how much memory my code would use? If it exists, does it require running the code or not?

2. If I try to avoid large sized array in cost of computational time, are multiple thread and parallel programming good way to accelerate the program running? 

Thanks a lot!

1.  Well, yes, but you could always play tricks, like starting with one huge array that doesn't contain a primitive type, but pointers to other huge arrays, each of which contains the primitives.  Doing this for just one level then increases your storage to huge_array * huge_array items.  But this gets unwieldly in a hurry, so you really need to make sure you are storing only what you need, as others mentioned.

2.  As mentioned, cpus are referenced by the number of bits they can process at one time, which includes addresses.  For a 32 bit machine, this is 2^32 (starting with 0, it becomes 2^32-1).  64 bit is 2^64.

3.  Pretty much, in practice anyway.  Computers use virtual memory in the program; this can exceed the amount of physical RAM (and I think the swap?).  Hardware in your computer brings in parts of the program when needed, and swaps out unneeded.  I don't know if the compiler (or OS) checks to see if a program wants to possibly address more memory than you have in RAM + swap.  I would guess not, but I'm not sure.  Either way, it's not something you want to start doing unless you know what you're doing.

Other:

1.  How much it _would_ use?  I doubt it.  This depends on how much memory your program needs; the OS doesn't allocate all of the memory your program possibly could need when it starts; it allocates what it thinks you will need in the near future.  Once you need more, it brings it in, and swaps something out (from the program or another) that currently seems unneeded.  There are several algorithms out there to do this (page replacement)--FIFO, LRU, etc...

2.  Again, as mentioned, your bottleneck is much more likely to come from I/O than CPU.  Multi-threading and the like will only significantly speed up CPU-intensive tasks.  If your program uses small amounts of CPU time, then it doesn't really matter, since the tasks are all going to be waiting on I/O instead.

Hope that helps a bit...

---

### Post by JohnLM_the_Ghost on 2009-03-26
> **quip said:**
> 3.  Pretty much, in practice anyway.  Computers use virtual memory in the program; this can exceed the amount of physical RAM (and I think the swap?).  Hardware in your computer brings in parts of the program when needed, and swaps out unneeded.  I don't know if the compiler (or OS) checks to see if a program wants to possibly address more memory than you have in RAM + swap.  I would guess not, but I'm not sure.  Either way, it's not something you want to start doing unless you know what you're doing.

Nope you can't have more memory allocated than RAM+swap.
Virtual memory is an abstract memory space assigned to that particular program, so it does not need to know internals of memory management outside the program. But in basics it is that same memory as RAM and swap. You can't go over that!

---

### Post by quip on 2009-03-26
> **JohnLM_the_Ghost said:**
> Nope you can't have more memory allocated than RAM+swap.
Virtual memory is an abstract memory space assigned to that particular program, so it does not need to know internals of memory management outside the program. But in basics it is that same memory as RAM and swap. You can't go over that!

I thought it was clear that I was speaking of the total amount of virtual memory (2^32 for a 32 bit machine), which the OP was asking about.

You most certainly can have a 32 bit machine with, say, 512 MB of RAM and 1 GB of swap.  1 + .5 = 1.5GB < 4.0 GB

Virtual memory is _not_ the same as RAM and swap.  The OS takes the request for a page of memory, looks to see if it is in memory already, and if not, brings it in.  If you have already taken up all your RAM, it swaps out a page when it does so.

When it brings it in, it goes to a page table.  This structure maps different logical memory blocks (pages) to physical ones (frames).  In fact, your program does not even need to be stored contiguously in physical memory.

---

### Post by flylehe on 2009-03-26
Thanks for all of you giving me advice! You are really help me learn a lot!

Currently my huge number of template images are generated synthetically by my code and not necessarily to be stored in hard disk unless it can give some benefits. Probably I will consider FIFO if I am asked to deal with huge number of real images, although I am not sure about the whole page replacement algorithm thing.

One thing that I just realized might reduce time is to change my loop order. Originally I used:
```

for each test image i
  sum[i]=0;
  for each template image j
    generate the template image j
    some intermediate value of the template image j used in the following computation
    sum[i] += some value between the test image i and the template image j
  end
end

```
There are some operations repeated for all test images, so I changed it to:
```

for each test image i
  sum[i]=0;
end
for each template image j
  generate the template image j
  some intermediate value of the template image j used in the following computation
  for each test image i
    sum[i] += some value between the test image i and the template image j
  end
end

```
I was hoping this change would save me a lot of time, however the time benefit is virtually unobservable.

I perhaps have to resort to multiple thread programming. I've been studying how to use POSIX library. My office cluster has 8 CPUs, each of which has one core. I was wondering how many threads to create would get approximately best time performance on my cluster? Is it the same number of CPUs? If I am using multiple thread library like POSIX, will the library take care of which thread run on which CPU or do I have to specify this in my code?

---

### Post by JohnLM_the_Ghost on 2009-03-26
> **flylehe said:**
> Currently my huge number of template images are generated synthetically by my code and not necessarily to be stored in hard disk unless it can give some benefits.

Well from your algorithm it looks like you don't need to keep template longer than comparison and I assume those can be generated quite fast. So you just do comparing... then generate new one and continue.

I guess you have to worry only where to keep sum[] data... and image data.

But if I understand right there is nothing really that need that huge amount of memory space.

---

### Post by Can+~ on 2009-03-26
> **JohnLM_the_Ghost said:**
> Well from your algorithm it looks like you don't need to keep template longer than comparison and I assume those can be generated quite fast. So you just do comparing... then generate new one and continue.

That's a good point, does the data need to be compared completely between all of them?

So far this thread has been a massive waste of time, you throw too little information per post. What's going on? What are this templates? What's the objective? How do you compare them?

---

### Post by Delever on 2009-03-27
Lets look at this problem from another point of view:

With such huge collection of generated images, your next image is so random it does not even matter anymore. Unless your algorithm which generates 24x24 images requires lots of time (i doubt it), why not simply generate new image every time you need one, and dispose it after that? 

However I fear that in such case cluster will no longer be necessary, so that might not be very impressive when documented.

---

### Post by JohnLM_the_Ghost on 2009-03-27
Also one note about the threads... if there is no directly dependent data between processed images, it may be even wiser to make it single-threaded.

And run 8 copies of it on the cluster if you wish (and if possible).

That way you will have much less headache on actual implementation and program will be more portable.
Remember: "The simplest working implementation will always prevail!"

Of course there is a bit of overhead having 8 processes, but compared to required memory space it is negligible.

---

### Post by jpkotta on 2009-03-27
I'm not exactly sure what you're doing, but is it possible to decompose all of your template images into some basis set, and then perform your computations on linear combinations of the basis images?  If your operations are linear (in the linear vector space sense), you can perform your operations on just the basis images and then combine the results.

---

### Post by monkeyking on 2009-03-29
I didn't really read all the posts very intensively,
But if you want to allocate huge amounts of data you are limited by the size_t unsigned integral type,
which on my system is a unsigned long int, thats 8 bytes.

If you need to store alot of data, consider try compressing the data.

I'm doing some genetics stuff, and when I really need to allocate data. I'm packing my data using bitpattens in char arrays.

good luck

---

