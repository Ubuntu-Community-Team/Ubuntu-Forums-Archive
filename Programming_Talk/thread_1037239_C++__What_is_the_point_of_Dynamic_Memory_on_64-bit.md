---
title: "C++  What is the point of Dynamic Memory on 64-bit Systems?"
date: 2009-01-11
forum: Programming Talk
---

### Post by u-slayer on 2009-01-11
I've been reading up on dynamic memory allocation with vectors and so on in C++. It all sounds very slick, only allocating the memory you need at run time, but I've been testing it on my 64-bit machine and all of these fancy tricks have a significant performance penalty. What's so wrong with doing something like

```
double * x = new double[4294967295];
```

and then only using the portion of the array you actually need?

64-bit Machines have a (virtually) endless supply of Virtual Ram and the above is much faster to allocate, access and modify.

---

### Post by Reiger on 2009-01-11
Where is virtual RAM taken from? A 64bit machine with 2GB of *real* RAM is and remains a machine with 2GB of RAM. The only thing which has changed, assuming there is a 64bit OS at work is the _theoretical capability_ to work with more than 4GB of RAM. But you got to have that RAM in the first place in order for your machine to work with it; anything you don't have must come from pagefile/swap which means the harddisk. And a harrdisk operates at a much lower Read/Write speeds than RAM does, not to mention seek times.

Plus an allocated array is an allocated array which (excepting shared memory) is memory not available to other processes. Even if you only use 64bytes of the N allocated, the OS got to take all N into account (make sure that it *is* loaded before read/write calls *can* be made.)

---

### Post by jimi_hendrix on 2009-01-11
dont make arrays that big?!?!

---

### Post by slavik on 2009-01-11
there are two problems with this.

1. as already stated a 2GB RAM system still has only 2GB of RAM. If you allocate 4GB, where will the other 2GB come from if the swap is only 1GB?
2. malloc() on Linux by default will never fails, but when you try to use the memory you allocated, you will run out of it and something will have to be killed.

---

### Post by kavon89 on 2009-01-11
> **slavik said:**
> 2. malloc() on **Linux by default will never fails**, but when you try to use the memory you allocated, you will run out of it and something will have to be killed.

I spent two minutes laughing at this... welcome to my signature :D

---

### Post by u-slayer on 2009-01-11
> **Reiger said:**
> Plus an allocated array is an allocated array which (excepting shared memory) is memory not available to other processes. Even if you only use 64bytes of the N allocated, the OS got to take all N into account (make sure that it *is* loaded before read/write calls *can* be made.)

Example:
```
	double * test[100];
	for ( int x = 0; x < 100; x++ )
	{
		test[x] = new double[(int)(4e9 / 8)];	//4 Gigs Virtual
		
		for ( int y= 0; y < 10e6/8; y++ )		//Fill in 10 Megs of Real Ram
			test[x][y] = (double)y;
	}
	
	cin.get();
```

This program uses 400 GB of virtual Ram and 1 GB of real ram. No swapping no paging no kidding.


Try it. There's a reason it's called "virtual" ram. (It doesn't really exist)

---

### Post by u-slayer on 2009-01-11
> **jimi_hendrix said:**
> dont make arrays that big?!?!

Why not? No seriously, I want to know.

> **slavik said:**
> ... , but when you try to use the memory you allocated, you will run out of it and something will have to be killed.

That's why you have to keep track of how much you have used and how much Real ram you still have available. It's still a lot easier ( and infinitely less cpu expensive ) than using vectors which have to copy themselves every time they expand. 

In the above example, if you need to "expand" any one array simply write values to it at a higher subscript, just keep track of what you're doing so you don't run out of real ram.

---

### Post by Cracauer on 2009-01-11
They keyword to google here is "overcommit".

You can turn this off, BTW.

> **slavik said:**
> there are two problems with this.

1. as already stated a 2GB RAM system still has only 2GB of RAM. If you allocate 4GB, where will the other 2GB come from if the swap is only 1GB?


With overcommit that's not a problem since the actual allocation of a physical page happens when the page is referenced. In this situation the programming "style" the OP proposes is perfectly valid.

Useless of course since you can't really say what a good maximum size is unless you specify every array to be max_int - in which case you fail because you run out of virtual memory, even of 64 bits. But let's leave that aside.

In C++ it's problematic since many constructors written by wimps initialize the fields.

> **slavik said:**
>  2. malloc() on Linux by default will never fails, but when you try to use the memory you allocated, you will run out of it and something will have to be killed.

It will never fail for running out of physical memory (RAM + swap). But it will fail when you run out of virtual memory.

I don't think the virtual address map of a Linux/amd64 process with current processors is actually 64 bits, but I'm too lazy to check.

---

### Post by jimi_hendrix on 2009-01-11
> **u-slayer said:**
> Why not? No seriously, I want to know.

if why malloc more than you need?...

its like:

i know...the string the user inputs might be really long! ill malloc 2 gigs for a char array just in case...

---

### Post by u-slayer on 2009-01-11
> **Cracauer said:**
> 
I don't think the virtual address map of a Linux/amd64 process with current processors is actually 64 bits, but I'm too lazy to check.

Wikipedia seems to think [128 TB]("http://en.wikipedia.org/wiki/X86-64#Linux") is the limit.

I've benchmarked it and overcommiting seems to work just as fast as normal arrays. I was expecting there to be problems with memory fragmentation and other Black Box Hardware stuff I don't really understand, but so far I'm not seeing it. I don't know why anyone would ever want to use vectors.

---

### Post by u-slayer on 2009-01-11
> **jimi_hendrix said:**
> i know...the string the user inputs might be really long! ill malloc 2 gigs for a char array just in case...

I know it sounds crazy doesn't it.:lolflag:

 But if you know that you're code is going to use a 64-bit platform, I am still waiting for a downside.):P

---

### Post by dribeas on 2009-01-11
> **u-slayer said:**
> I've been reading up on dynamic memory allocation with vectors and so on in C++. It all sounds very slick, only allocating the memory you need at run time, but I've been testing it on my 64-bit machine and all of these fancy tricks have a significant performance penalty. What's so wrong with doing something like

```
double * x = new double[4294967295];
```

and then only using the portion of the array you actually need?

64-bit Machines have a (virtually) endless supply of Virtual Ram and the above is much faster to allocate, access and modify.

You can ask the std::vector to allocate (reserve) as much memory as you want, no need to fall back to raw arrays. Of course, if you allocate for 2^32 doubles chances are the vector will never grow.

Now, from a program design standpoint, it does not make sense in as much as you don't request a long long to hold a small integer. Now, as you said requesting infinite memory will not fail, and as it was mentioned before linux kernels allow you to allocate more memory than you actually have. Now, you have just bought a dependency on the operating system. If at some time you want to port  your program to another operating system you might just find out that suddenly it won't work any more and you will have a hard time determining what the real limits in your code are to tighten them up.

While it works, it is one of those things that are often considered as 'code smell'. It works, but being careless can bite you back at some later time.

My advice would be using vectors in C++ (plain arrays in C), and if you do have an estimate of how much space will be used, then provide that info to the container using reserve:

```

// expect around 10000 elements:
std::vector<Type> v;
v.reserve( 10000 );

```

Note that the method will reallocate space, and that implies the invalidation of all previous iterators into that container. With this approach you will minimize the number of times memory is acquired.

I don't really see what you are referring in your last sentence with access and modify in 'faster to allocate, access and modify'. You are limiting allocations but access is just as simple or complex as if you had used a vector and I just don't see where 'modify' fits.

---

### Post by slavik on 2009-01-11
> **kavon89 said:**
> I spent two minutes laughing at this... welcome to my signature :D
You're taking my words out of context. Please add that malloc() by default never fails. Also, please fix the grammar mistake for the quote. :)

[http://www.mjmwired.net/kernel/Documentation/vm/overcommit-accounting](http://www.mjmwired.net/kernel/Documentation/vm/overcommit-accounting)

I've also kicked in OOM on my system time and time again by running the below code:
```

slavik@slavik-desktop:~/code/c_cpp$ cat overcommit.c; gcc -o overcommit overcommit.c; cat /proc/meminfo | grep -i memtotal; sysctl vm.overcommit_memory; valgrind ./overcommit
/*
 *      overcommit.c
 *      
 *      Copyright 2009 Vyacheslav Goltser <slavikg@gmail.com>
 *      
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *      
 */


#include <stdio.h>
#include <malloc.h>

int main(int argc, char** argv)
{
	unsigned char* a[1024*10];
	int i = 0;
	// ~10,000 blocks
	for (; i < 1024*10; i++) {
		a[i] = (unsigned char*)malloc(1024*1024); // allocate 1MB per block
	}
	
	return 0;
}
MemTotal:      8183676 kB
vm.overcommit_memory = 0
==25811== Memcheck, a memory error detector.
==25811== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==25811== Using LibVEX rev 1854, a library for dynamic binary translation.
==25811== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==25811== Using valgrind-3.3.1-Debian, a dynamic binary instrumentation framework.
==25811== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==25811== For more details, rerun with: -v
==25811== 
==25811== 
==25811== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 8 from 1)
==25811== malloc/free: in use at exit: 10,737,418,240 bytes in 10,240 blocks.
==25811== malloc/free: 10,240 allocs, 0 frees, 10,737,418,240 bytes allocated.
==25811== For counts of detected errors, rerun with: -v
==25811== searching for pointers to 10,240 not-freed blocks.
==25811== checked 69,072 bytes.
==25811== 
==25811== LEAK SUMMARY:
==25811==    definitely lost: 10,727,981,056 bytes in 10,231 blocks.
==25811==      possibly lost: 9,437,184 bytes in 9 blocks.
==25811==    still reachable: 0 bytes in 0 blocks.
==25811==         suppressed: 0 bytes in 0 blocks.
==25811== Rerun with --leak-check=full to see details of leaked memory.

```

EDIT:
```

slavik@slavik-desktop:~/code/c_cpp$ top | head

top - 21:11:03 up 1 day,  5:42,  5 users,  load average: 0.14, 0.16, 0.14
Tasks: 183 total,   1 running, 182 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.8%us,  0.4%sy,  0.0%ni, 96.3%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8183676k total,  2481600k used,  5702076k free,   308160k buffers
Swap:        0k total,        0k used,        0k free,   437388k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                             
 7103 root      20   0  648m  62m 6488 S    2  0.8   9:05.32 Xorg                                                
    1 root      20   0  4024  196   60 S    0  0.0   0:01.12 init                                                
    2 root      15  -5     0    0    0 S    0  0.0   0:00.02 kthreadd                                            

slavik@slavik-desktop:~/code/c_cpp$ uname -a
Linux slavik-desktop 2.6.27-11-generic #1 SMP Thu Jan 8 08:38:38 UTC 2009 x86_64 GNU/Linux

```

Please tell me why malloc() gave me 10GB of memory on a system with 8GB of real RAM and no swap.

EDIT2: Here is what happens when vm.overcommit_memory is set to 2. Please note that malloc was only able to get about 1.5GB of memory, versus 10GB as before. Also note that any memory that malloc says "is yours", you program has no idea whether or not it is really available and has no way of knowing unless you start interrogating the /proc filesystem and/or related system calls in which case, what is the point of malloc returning NULL if you are checking how much free memory is really left. But then what happens if there really isn't any memory and you call malloc to get what isn't available?

```

slavik@slavik-desktop:~/code/c_cpp$ cat overcommit.c; echo; gcc -o overcommit overcommit.c; cat /proc/meminfo | grep -i memtotal; echo; sysctl vm.overcommit_memory; echo; valgrind ./overcommit; echo; uname -a; echo; top -b -n 1 | head -5
/*
 *      overcommit.c
 *      
 *      Copyright 2009 Vyacheslav Goltser <slavikg@gmail.com>
 *      
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *      
 */


#include <stdio.h>
#include <malloc.h>

int main(int argc, char** argv)
{
	unsigned char* a[1024*10];
	int i = 0;
	// ~10,000 blocks
	for (; i < 1024*10; i++) {
		a[i] = (unsigned char*)malloc(1024*1024); // allocate 1MB per block
	}
	
	return 0;
}

MemTotal:      8183676 kB

vm.overcommit_memory = 2

==27008== Memcheck, a memory error detector.
==27008== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==27008== Using LibVEX rev 1854, a library for dynamic binary translation.
==27008== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==27008== Using valgrind-3.3.1-Debian, a dynamic binary instrumentation framework.
==27008== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==27008== For more details, rerun with: -v
==27008== 
==27008== 
==27008== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 8 from 1)
==27008== malloc/free: in use at exit: 1,531,969,536 bytes in 1,461 blocks.
==27008== malloc/free: 10,240 allocs, 0 frees, 1,531,969,536 bytes allocated.
==27008== For counts of detected errors, rerun with: -v
==27008== searching for pointers to 1,461 not-freed blocks.
==27008== checked 69,104 bytes.
==27008== 
==27008== LEAK SUMMARY:
==27008==    definitely lost: 1,526,726,656 bytes in 1,456 blocks.
==27008==      possibly lost: 5,242,880 bytes in 5 blocks.
==27008==    still reachable: 0 bytes in 0 blocks.
==27008==         suppressed: 0 bytes in 0 blocks.
==27008== Rerun with --leak-check=full to see details of leaked memory.

Linux slavik-desktop 2.6.27-11-generic #1 SMP Thu Jan 8 08:38:38 UTC 2009 x86_64 GNU/Linux

top - 21:25:38 up 1 day,  5:56,  5 users,  load average: 0.32, 0.36, 0.26
Tasks: 183 total,   3 running, 180 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.9%us,  0.4%sy,  0.0%ni, 96.3%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8183676k total,  2301504k used,  5882172k free,   310800k buffers
Swap:        0k total,        0k used,        0k free,   476520k cached


```

---

### Post by Cracauer on 2009-01-11
> **u-slayer said:**
> Wikipedia seems to think [128 TB]("http://en.wikipedia.org/wiki/X86-64#Linux") is the limit.

I've benchmarked it and overcommiting seems to work just as fast as normal arrays. I was expecting there to be problems with memory fragmentation and other Black Box Hardware stuff I don't really understand, but so far I'm not seeing it. I don't know why anyone would ever want to use vectors.

Well, strictly speaking, the "style" proposed here might actually help against heap fragmentation in very long-lived programs. (still not a practical programming style)

Once a malloc implementation is out of it's depth things get ugly. There's a reason why copying GCs sometimes have their advantages.

Of course a malloc implementation could also just overcommit the hell out of everything, mmap a lot and let the VM system sort out fragmentation.

---

### Post by slavik on 2009-01-12
This is also worth taking a look at.

[http://en.wikipedia.org/wiki/Translation_lookaside_buffer](http://en.wikipedia.org/wiki/Translation_lookaside_buffer)

---

