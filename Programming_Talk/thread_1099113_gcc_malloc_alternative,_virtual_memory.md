---
title: "gcc malloc alternative, virtual memory"
date: 2009-03-17
forum: Programming Talk
---

### Post by Belerophon on 2009-03-17
Hi.

Malloc allocates memory in the heap, right?

The thing is that this has some limitations in size, so I was wondering if there is some alternative so that I could allocate memory that automatically grows into the virtual memory space when needed. Something compatible with gcc... 

Thanks.

---

### Post by slavik on 2009-03-17
err, what?

malloc() does do anything. malloc() is a system which allows you to ask the kernel for memory. the kernel will use all the virtual memory and the vm.overcommit_memory settings to determine what you get.

NOTE: the kernel meaning Linux 2.6 kernel.

---

### Post by soltanis on 2009-03-17
malloc asks the system for more memory when the heap runs out of space. It's up to the system as to where that memory comes from. But malloc manages the details for you, so there's no need to worry about it (unless of course you don't free it or otherwise mess up managing the memory once its given to you).

---

### Post by the_unforgiven on 2009-03-18
Take a look at this:
[http://en.wikipedia.org/wiki/Malloc#Implementations](http://en.wikipedia.org/wiki/Malloc#Implementations)

---

### Post by Belerophon on 2009-03-18
Ok...

then, let me explain a practical case:
I need do allocate space for a matriz, of nxn:
```
malloc(n * n * sizeof(double))
```

The thing is that for "small" n (10000 for example) this works perfectly...but for 50000 I get "segmentation fault"...

Why is this, and how can I resolve?

---

### Post by jfbilodeau on 2009-03-18
> **Belerophon said:**
> Ok...

then, let me explain a practical case:
I need do allocate space for a matriz, of nxn:
```
malloc(n * n * sizeof(double))
```

The thing is that for "small" n (10000 for example) this works perfectly...but for 50000 I get "segmentation fault"...

Why is this, and how can I resolve?

Do you check for NULL? The 'small' matrix that you are requesting (50000 * 50000 * 8) seems huge to me. There may not be a way to fit a matrix this large in memory, no matter what technique you use.

With an array that size, you may have to cache some of it on disk.

---

### Post by kpatz on 2009-03-18
10000 x 10000 x 8(the size of a double) = 763 megabytes.

50000 x 50000 x 8 = 19,073 megabytes!!

Do you have 20 gigabytes of total virtual memory (RAM + swap)?  Also, unless you're running a 64-bit OS and compiler, you're going to run into a 4 gigabyte size limit on pretty much everything.

---

### Post by WitchCraft on 2009-03-18
For Debian-based distros, use the apt-cache search command to locate a recent linux-image package for a kernel for a 686 processor if you want support for more than 4 gigabytes. 

If you want support for up to 64 gigabytes, look for a kernel that ends with 686-bigmem. 
These kernels will enable support for 64GB. The generic kernel is for only 4GB. 

aptitude install linux-image-2.6-686-bigmem
 That&#8217;s it now you need to reboot your system and you will be able to use up to 64GB of RAM.


But I suppose you don't have more than 4 GB RAM...


THERE'S NO WAY FOR SUCH A MATRIX TO FIT INTO 4 GB OF MEMORY!
And your have a 20 GB matrix.

If you have 4 GB of RAM, you need an appx. 16 GB swap parition + ONE additional gig for the system.
So your swap partition is probably too tiny...
The system can only page until the swap partition is full...

> 
The problem exists because 32-bit Linux kernels are designed to access only 1GB of RAM by default. The workaround for this limitation is vaguely reminiscent of the virtual memory solution once used by DOS, with a high memory area of virtual memory being constantly mapped to physical addresses. This high memory can be enabled for up to 4GB by one kernel parameter, or up to 64GB on a Pentium Pro or higher processor with another parameter. However, since these parameters have not been needed on most machines until recently, the standard kernels in many distributions have not enabled them.

Increasingly, many distributions are enabling high memory for 4GB. Ubuntu default kernels have been enabling this process at least since version 6.10, and so have Fedora 7's. By contrast, Debian's default 486 kernels do not. Few distros, if any, enable 64GB by default.

To check whether your kernel is configured to use all your RAM, enter the command free -m. This command gives you the total amount of unused RAM on your system, as well as the size of your swap file, in megabytes. If the total memory is 885, then no high memory is enabled on your system (the rest of the first gigabyte is reserved by the kernel for its own purposes). Similarly, if the result shows over 1 gigabyte but less than 4GB when you know you have more, then the 4GB parameter is enabled, but not the 64GB one. In either case, you will need to add a new kernel to take full advantage of your RAM.


PS: You should consider redesigning your program:
Breaking up the matrix in several smaller ones, load the first into memory and process the it, save the result to disk and unload the first matrix, load and process the next part, etc...
.

---

### Post by lensman3 on 2009-03-19
You might go look in 80286 code from the late '80s.  There were lots of virtual memory systems written that would allocate array on disk then page the current page into memory.  80286/8086 would only allocate 64k of memory.

The syntax is function calls to retrieve and store a value.  The one we used had about 20 pages at once in memory with the Least-Recently-Used being paged out when a value that was on disk had to be accessed.  

You could also go buy a 64 bit machine and use it!

---

### Post by movieman on 2009-03-19
You could also look at mmap(); if you're running 64-bit Linux you may be able to map a 20GB file into your address space and use that to hold the matrix. Though performance would suck unless you try hard to keep accesses close together so you're not permanently paging data in and out.

---

### Post by kjohansen on 2009-03-19
what matrix operations are you trying to perform?

as mentioned earlier you could break it up and do parts of the computation and then save it.

Matrix multiplication, matrix vector multiplication and many others can be easily split among sub blocks.

---

### Post by Belerophon on 2009-03-20
You are all obviously right...it was a stupid question.:oops:
I was dealing with huge numbers, I just didn't took the time to look at the numbers....
Sorry.

Anyway, I did not know that malloc reserved memory from ram and swap when needed. So my stupid question made me learn something anyway...lol

Thank you.

---

### Post by Can+~ on 2009-03-20
But what thing would ever need 50.000^2 double values?

At that point you don't need more space or splitting, you should look if you really need all that space and if that data representation is actually the best one.

I guess you were just messing with malloc, right?

---

### Post by Belerophon on 2009-03-20
Not messing with malloc...
It's a project to learn OpenMP, make some performance tests...we're using the matrix multiplication as test case...

---

### Post by WitchCraft on 2009-03-22
> **Can+~ said:**
> But what thing would ever need 50.000^2 double values?

At that point you don't need more space or splitting, you should look if you really need all that space and if that data representation is actually the best one.

I guess you were just messing with malloc, right?

You need that much space if you are writing a (real) search engine for the internet.
(When you need to compute the eigenvectors of [hughe] probability matrices.)

Also for translation programs (probability table for EVERY word in that language)

---

