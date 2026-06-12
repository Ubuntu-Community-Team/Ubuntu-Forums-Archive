---
title: "Large Data?&gt; in C++"
date: 2008-11-08
forum: Programming Talk
---

### Post by xdeathwishx on 2008-11-08
I want to do matrix algebra on very large data, which will not fit in memory.  I've heard Lapack++ is good for performing matrix operations, but I don't know if it supports large data sets.

For example, what would I have to do to invert a matrix that is 30GB?

I'm not necessarily looking for an exact answer (unless you know), but if you could give me an idea of what one calls such a process, or where I should look to find out this type of information, it would be very helpful.

Thanks.

---

### Post by pp. on 2008-11-08
Is it conceivable that you're thinking of a ***matrix transposition***? There ought to be a large body of literature about that, starting with the wikipedia.

---

### Post by CptPicard on 2008-11-08
The inverse and transpose of matrix are two different things, surely you know..?

---

### Post by xdeathwishx on 2008-11-08
Nope.  I'm not talking about any type of matrix algebra in particular.  I already know linear algebra, what I don't know is how to do it with huge datasets.  This is just a general question of how to work with large data that doesn't fit into memory.

I'm mainly interested in developing applications that can compute statistics on very large datasets.  The type of matrix operation is not significant, only how to do it without reading the entire dataset into memory (as packages like LAPACK++ require you to do).

I've come across one template library called STXXL, but I'm struggling to figure out how to use it, and wether or not it can be used in combination with LAPACK or something of that sort.

I don't think its possible because LAPACK would have its own matrix objects (I think), which are probably collections of std::vector rather than stxxl::vector.

Maybe somebody can tell me if theres a better solution??

---

### Post by slavik on 2008-11-08
could you tell us how the matrix is stored? is it plain text?

you could potentially do something like the following:
if "file" contains a matrix where each number is separated by space and a newline between each number, eg:
```

1 2 3 4 5
1 2 3 4 5
1 2 3 4 5

```

you could then do the following:
```

split -l 1 file pieces; sed -i 's/\s/\n/g' pieces*; paste -d' ' pieces* > file2

```

file2 will then contain
```

1 1 1
2 2 2
3 3 3
4 4 4
5 5 5

```

then you can read a row from each matrix and multiply stuffs :)

---

### Post by xdeathwishx on 2008-11-08
I don't see how what you just posted has anything to do with what I was asking?

---

### Post by slavik on 2008-11-08
if you need to multiply two large matrices, you can transpose the second matrix and make multiplication require less memory :) (not only that, but the code is simpler).

---

### Post by ad_267 on 2008-11-08
I'm not sure if this will help but you could look at ScaLAPACK. It's in Fortran and I don't think there's a C++ interface yet. It provides LAPACK routines using distributed memory methods. I know this sort of thing must have been done before but I don't have any experience with it myself, I've only used LAPACK in C.

---

### Post by WW on 2008-11-08
Adding to what ad_267 said, [ScaLAPACK](http://www.netlib.org/scalapack/slug/) allows for the storage of "out-of-core" matrices, meaning the matrices are stored on disk.  I've never used it (or even ScaLAPACK), so I couldn't help you with it.

---

### Post by Cracauer on 2008-11-08
mmap the whole thing, even if bigger than RAM and let the virtual memory system take care of the caching.

If you can a seek/read/write interface picking blocks from the data on the fly is better, for multithreaded programs in particular.

---

### Post by xdeathwishx on 2008-11-09
> **Cracauer said:**
> mmap the whole thing, even if bigger than RAM and let the virtual memory system take care of the caching.

If you can a seek/read/write interface picking blocks from the data on the fly is better, for multithreaded programs in particular.

This was basically what I was looking for.  Thanks a lot.

---

### Post by dribeas on 2008-11-09
> **Cracauer said:**
> mmap the whole thing, even if bigger than RAM and let the virtual memory system take care of the caching.

If you can a seek/read/write interface picking blocks from the data on the fly is better, for multithreaded programs in particular.

Question: Will it really map the file even if it is bigger than the available memory + swaps? Won't it produce an ENOMEM error? 

Just curiosity, I don't really know. In any case, it should be clear that this will never work on a 32 bit architecture, where the 33GB file is bigger than the memory address space available to the process (4GB). For 32 bit architecture you will have to manually work on pieces of the matrix and integrate the result.

---

### Post by Tony Flury on 2008-11-09
> **Cracauer said:**
> mmap the whole thing, even if bigger than RAM and let the virtual memory system take care of the caching.


If the OP really has 30GB of data like he claims on a reasonably speced system, then even Virtual memory will choke. Total memory (RAM and Virtual) is normally only around 4 * RAM (SWAP is approx 3 *RAM normally)

---

### Post by Cracauer on 2008-11-09
> **dribeas said:**
> Question: Will it really map the file even if it is bigger than the available memory + swaps? Won't it produce an ENOMEM error? 

Just curiosity, I don't really know. In any case, it should be clear that this will never work on a 32 bit architecture, where the 33GB file is bigger than the memory address space available to the process (4GB). For 32 bit architecture you will have to manually work on pieces of the matrix and integrate the result.

The input file(s) will be mapped readonly and don't require any backing by physical memory (RAM or paging space).

For the output file(s) you should probably organize workflow in a way that you can write it linearly and use write(2).

However, if you want to mosh around in an read-write mapped file that's no problem either. You have to create that file before mapping anyway and then this file is the backing space. No swapspace required.

A 64 bit version is of course required if you have files larger than 2 GB unless you go hand-picking with seek/read/write.

---

### Post by Cracauer on 2008-11-09
> **Tony Flury said:**
> If the OP really has 30GB of data like he claims on a reasonably speced system, then even Virtual memory will choke. Total memory (RAM and Virtual) is normally only around 4 * RAM (SWAP is approx 3 *RAM normally)

No, people mmap files much larger than RAM all the time.

Whether it brings down your system or not is only dependent on what access pattern your program shows. Obviously, in a situation like this you really want a smart program.

---

### Post by Tony Flury on 2008-11-09
> **Cracauer said:**
> No, people mmap files much larger than RAM all the time.

Whether it brings down your system or not is only dependent on what access pattern your program shows. Obviously, in a situation like this you really want a smart program.

Thank you for the reply.

Yes you can mmap larger than RAM, that after all is the point of virtual memory, but I was actually talking about RAM and SWAP combined - so can you really mmap a file far bigger then both RAM and virtual memory combined (which is what the OP asked - I guess 50GB is bigger than most peoples RAM+VM)? A cursory glance at the mmap info suggests that you are still limited to the total memory - i.e. RAM + virtual - after all the total address space of any process is limited to the total of RAM + VM, and the only way of dealing with a bigger file would be to use mmap to grab effectively a window into that file - and process that.

---

### Post by pp. on 2008-11-09
Loosely speaking, amount(real RAM)+amount(SWAP space)=amount(virtual RAM).

It's usually not a good idea to run a single application which exceeds available real RAM by a factor or even an order of magnitude. Virtual RAM typically is put to good use when the working set of your application fits into real RAM. That is often the case when running several applications. It is rarely the case with one huge application.

The crux of the matter is that the application is not usually aware of being run in swapped RAM, hence it does not attempt to access the data in RAM in a sequence which economizes on swapping (reading and writing junks of RAM contents).

For doing work with largish matrices I would look for a library or application which is designed to work on large matrices in a piecemeal fashion.

Matrix transposition is a fine example of an operation which can be done in such a way.

Also,it might be worthwile to scrutinize the format in which the matrix data is presented. A very good way to ruin performance might be variable length comma separated ascii fields.

---

### Post by Cracauer on 2008-11-09
> **Tony Flury said:**
> Thank you for the reply.

Yes you can mmap larger than RAM, that after all is the point of virtual memory, but I was actually talking about RAM and SWAP combined - so can you really mmap a file far bigger then both RAM and virtual memory combined (which is what the OP asked - I guess 50GB is bigger than most peoples RAM+VM)? A cursory glance at the mmap info suggests that you are still limited to the total memory - i.e. RAM + virtual - after all the total address space of any process is limited to the total of RAM + VM, and the only way of dealing with a bigger file would be to use mmap to grab effectively a window into that file - and process that.

No, that's not correct. As long as there is file backing for the memory you need neither RAM nor swap.

Data in RAM from a readonly mapped file is never moved to swap whent he OS needs memory. It is just dropped from RAM, then reloaded later from the original location.

Likewise, if you have a preallocated read-write mapped file and you use MAP_SHARED for mmap flags, then data that belong there is never moved to swapspace. It's moved to the destination in the file.

You only need swapspace for memory mapping that are anonymous (including memory from sbrk like certain malloc areads) and those that are read-write and use MAP_PRIVATE in mmap flags.

This will all work find, even if you have 1 TB of file space, 1 GB of RAM and no swapspace. You can map just fine.

Whether it will trash your system entirely depends on the algorithm and the access pattern of your program. It might or might not work fine.

---

### Post by caonima on 2008-11-09
Maybe you should look at blockwise inversion of matrix.

---

### Post by gnusci on 2008-11-09
I think you better look for better matrix operations, you can save hardware requirements and time ;)

[http://www.iop.org/EJ/abstract/0305-4470/18/9/018](http://www.iop.org/EJ/abstract/0305-4470/18/9/018)

---

### Post by hod139 on 2008-11-10
Use of [FONT=Comic Sans MS][FONT=Comic Sans MS]randomized  and approximation algorithms is common for exactly this situation, when you have very large matrices.  For an example of some matrix operations on very large data-sets:
[/FONT][/FONT] [Fast Monte Carlo 	Algorithms for Matrices I: Approximating Matrix Multiplication]("http://www.cs.rpi.edu/%7Edrinep/matrixI_SICOMP.pdf")
 [Fast Monte Carlo 	Algorithms for Matrices II: Computing a Low Rank Approximation to a Matrix]("http://www.cs.rpi.edu/%7Edrinep/matrixII_SICOMP.pdf")
 [Fast Monte Carlo 	Algorithms for Matrices III: Computing a Compressed Approximate	Matrix Decomposition]("http://www.cs.rpi.edu/%7Edrinep/matrixIII_SICOMP.pdf")

Petros Drineas is very well know and respected in the area of randomize and approximation algorithms, and the 3 above papers are from him.  You can visit his website for many more papers if you are interested in more details.

---

