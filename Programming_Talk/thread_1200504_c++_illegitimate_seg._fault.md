---
title: "c++ illegitimate seg. fault"
date: 2009-06-30
forum: Programming Talk
---

### Post by sidious1741 on 2009-06-30
So before I run a program like...

```
int main ()
{
	int a[400000];
	int b[400000];
	int c[400000];
	int d[400000];
	int e[400000];
	//int f[400000];
 	system("free");
	return 0;
}
```

I typed free in the terminal to see how muce space I have which says...

```
             total       used       free     shared    buffers     cached
Mem:       1018324     566952     451372          0      21348     238816
-/+ buffers/cache:     306788     711536
Swap:      2980016          0    2980016
```

and the program ( system("free"); ) returns

```
             total       used       free     shared    buffers     cached
Mem:       1018324     566912     451412          0      21360     238760
-/+ buffers/cache:     306792     711532
Swap:      2980016          0    2980016
```

So I should have enough free space for...

```
int main ()
{
	int a[400000];
	int b[400000];
	int c[400000];
	int d[400000];
	int e[400000];
	int f[400000];
 	system("free");
	return 0;
}
```

but I get a segmentation fault.  Any Ideas?

---

### Post by Victor Liu on 2009-06-30
All those large arrays you define go on the stack. Maybe you're running out of stack space?

Edit: See [http://ubuntuforums.org/showthread.php?t=680535]("http://ubuntuforums.org/showthread.php?t=680535")

---

### Post by lisati on 2009-06-30
That does seem rather a lot of memory for a program to need all at once.

Perhaps someone else might have a better idea of what's going on but I suspect that part of the problem could be that there are other processes that together with your program are testing your system's ability to allocate sufficient resources.

EDIT: (afterthought) don't forget that an int is usually more than one byte.....

---

### Post by Zugzwang on 2009-06-30
@OP: "Victor Liu" is right. You run out of stack space. Since Linux does not distinguish between "regular" segmentation faults and running out of stack space (which I think is really a pity. Even Windows does that!), you get a segfault instead of a "out of stack space" message.

Type "ulimit -s" on your terminal before running your program. It shows you the amount of stack space in megabytes. Try for example "ulimit -s 16384" for increasing this value.

---

### Post by sidious1741 on 2009-06-30
[http://ubuntuforums.org/showthread.php?t=680535](http://ubuntuforums.org/showthread.php?t=680535) says to look at malloc and Zugzwang says to use ulimit.  I understand a little better about the stack but...
Why does c++ use "stack space"?
I'd like to understand how malloc or ulimit works Instead of using them blindly.  (I didnt understand man ulimit)

---

### Post by soltanis on 2009-06-30
Automatic variables (i.e. the ones you declared in the main function) are declared on the "stack," which while formally is not defined by C to be anything, is basically where your architecture allocates the space for those variables.

So basically, if you need some space to put large amounts of data, your best bet is the heap, basically a big pool of memory that you can grab parts of. This memory is dynamically allocated to your program by malloc (see man 2 malloc), which returns a pointer to the start of the memory segment it allocates for you (or otherwise NULL indicating an error).

You can access the memory you set aside like you would access an array. For example:

```

#include <stdio.h>
#include <stdlib.h>

int main()
{
        int *pmem, i;

        if (!(pmem = malloc(sizeof(int) * 40000))) {
                perror("malloc");
                return 1;
        }

        for (i = 0; i < 40000; i++) {
                pmem[i] = i;
                printf("%d\n", pmem[i]);
                /* *(pmem + i) <=> pmem[i] by virtue of pointer/array similarity */
        }

        free(pmem); /* good practice -- free memory after use */
        return 0;
}

```

---

### Post by stroyan on 2009-06-30
Variables declared within functions (without the "static" attribute) are allocated when a function is called and released when a function completes.
If a function is called recursively from within the first use of the function then another set of the same variables is allocated.
That is most effectively handled by a stack of memory locations.
The memory used for each function's variables is pushed onto the end of the stack when the function starts and popped off of the stack when the function finishes.
But most variables are allcoated by the C style malloc and free functions or c++ style new and delete builtins.
Both those will create memory that can be freed in arbitrary order, unlike a stack.
For c++ you should get into a habit of using new and delete.
They include the action of calling constructor and destructor functions when creating and deleting instances of class variables.
Malloc and free don't do constructors and destructors.
There are other more sophisticated container types in the standard template library that build upon the new and delete mechanism.
Here is an example using new and delete.

```

#include <stdlib.h>
int main ()
{
	int *a = new(int[400000]);
	int *b = new(int[400000]);
	int *c = new(int[400000]);
	int *d = new(int[400000]);
	int *e = new(int[400000]);
	int *f = new(int[400000]);

	system("free");
	delete[] a;
	delete[] b;
	delete[] c;
	delete[] d;
	delete[] e;
	delete[] f;
	return 0;
}

```

---

### Post by sidious1741 on 2009-06-30
So when you use new that data does not go on the stack right?  And I got malloc now but I'd still like to be more clear on what ulimit does.

---

### Post by sidious1741 on 2009-06-30
This might have been confusing to some who have read my first post but I meant that I get the segfault when I uncomment the array f.

---

### Post by Mirge on 2009-06-30
[http://www.gotw.ca/gotw/009.htm](http://www.gotw.ca/gotw/009.htm)

This may help your understanding

---

### Post by stroyan on 2009-06-30
New and delete, like malloc and free, use the "heap" or "data" area.
There can be more complexity to that in some implementations.
The simplest implementation of a heap area uses brk or sbrk system calls to set a single range of allocated memory.
That single area is then used to handle allocations.
Memory released by free or delete remain allocated to a process but are noted in user-space data structures as available for reuse by later malloc or free calls.
Some implementations actually use mmap to handle really large allocations so that freeing them can cause an immediate release back to the OS with an munmap system call.

The ulimit values set and reported by shells can limit the maximum stack size, the maximum data segment size, and the maximum total virtual memory size.  Ulimit is implemented with getrlimit and setrlimit system calls.

Stack limits can be much more complicated than just the ulimit value.
A program using threading will have a separate stack area for each thread.
The limit on stack size can be set to different values for different threads.  The stack size limit of the original thread in a process is usually higher than the default limit for additional threads.

---

### Post by sidious1741 on 2009-07-01
> **Mirge said:**
> [http://www.gotw.ca/gotw/009.htm](http://www.gotw.ca/gotw/009.htm)

This may help your understanding

That does very much.  Now It make sense why there are so many initializer commands in c++.  I don't know much more that the basics.

---

### Post by sidious1741 on 2009-07-01
So is there a way to get more stack space?  I know I use a lot of memory but for what I'm doing I don't need much more.  The only reason that I ask is because [http://www.gotw.ca/gotw/009.htm](http://www.gotw.ca/gotw/009.htm) says

"The stack stores automatic variables. Typically
allocation is much faster than for dynamic
storage (heap or free store) because a memory
allocation involves only pointer increment
rather than more complex management."

---

### Post by nvteighen on 2009-07-01
Hmm... You usually would never need such amount of stack space... Your design is probably bad. For example, why do you need that space? Wouldn't it better to adjust it during runtime?

---

### Post by fr4nko on 2009-07-01
> **sidious1741 said:**
> This might have been confusing to some who have read my first post but I meant that I get the segfault when I uncomment the array f.
I believe that since you are depassing the limits of the stack the behaviour of your program becames unpredictable. I will not spend so much time on that. If you want to allocate a lot of memory your should use the heap-allocated memory, as suggested, either with malloc or with the new[] operator in C++. You should also check if the call to malloc fails or, in C++, if new throw an exception.

For informations, here the man page of ulimit:
> [FONT=Verdana][FONT=Courier New]**ulimit**

  User limits - limit the use of system-wide resources.
 Syntax
      ulimit [-acdfHlmnpsStuv] [limit]

Options

   -S   Change and report the soft limit associated with a resource. 
   -H   Change and report the hard limit associated with a resource. 

   -a   All current limits are reported. 
   -c   The maximum size of core files created. 
   -d   The maximum size of a process's data segment. 
   -f   The maximum size of files created by the shell(default option) 
   -l   The maximum size that may be locked into memory. 
   -m   The maximum resident set size. 
   -n   The maximum number of open file descriptors. 
   -p   The pipe buffer size. 
   -s   The maximum stack size. 
   -t   The maximum amount of cpu time in seconds. 
   -u   The maximum number of processes available to a single user. 
   -v   The maximum amount of virtual memory available to the process.  ulimit provides control over the resources available to the shell and to processes started by it, on systems that allow such control. [/FONT]
[/FONT][FONT=Verdana]and here the results of ulimit -a on my system
> [FONT=Courier New]core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
**stack size              (kbytes, -s) 8192**
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited[/FONT][/FONT]>      
So the stack size is limited by default to 8 Mb.

Francesco

---

### Post by fr4nko on 2009-07-01
> **sidious1741 said:**
> So is there a way to get more stack space?  I know I use a lot of memory but for what I'm doing I don't need much more.  The only reason that I ask is because [http://www.gotw.ca/gotw/009.htm](http://www.gotw.ca/gotw/009.htm) says

"The stack stores automatic variables. Typically
allocation is much faster than for dynamic
storage (heap or free store) because a memory
allocation involves only pointer increment
rather than more complex management."
That's ok, but usage of automatic variables should be limited to variables or arrays of small size. If you allocate a lot of memory on the stack you can get a stack overflow and your program will crash. You should also keep in mind that automatic variable are valid only withing the scope of the function or the block where they are declared. You cannot return references to automatically allocated variables because their lifes does not go beyond the life of the activation stack of the function.

Francesco

---

### Post by curvedinfinity on 2009-07-01
Stack space is very fast because the sizes of all of the data are set at compile time and the memory is preallocated. Those are also the downsides -- sizes can't be changed at allocation-time and there is a limited amount of memory. :D

If you need something bigger or dynamic-er, you need to use the heap. That's what it is there for. Its slower because the OS has to worry about memory management (fragmentation is the biggest issue), but much more flexibile.

On the security front, tons of application vulnerabilities stem from "stack overflow" attacks. These involve writing into an array in the stack at an index that is past the array's bounds. The goal of the attack is to write to a spot that is executable code, and replace the actual code with some code that will take control away from the application. If you use the heap instead, you are preventing this kind of attack.

Speed-critical applications will often make their own memory managers to circumvent the OS's slow memory manager. They will preallocate a bunch of heap memory, and then divy it out in chunks to the application. I've done this in the past when I'm going to make tons of the same kind of data -- in my case, a particle system. Its much harder to do (and less advantageous), if you have different sizes of data that you want to allocate.

I happen to have the source right here for a simple memory manager:

MemoryBlock.h
```

#ifndef _MEMORYBLOCK_H
#define _MEMORYBLOCK_H

class MemoryBlock
{
	struct Segment
	{
		void *start;
	};

	void *start;
	unsigned int segmentSize;
	Segment *firstFree;
public:
	MemoryBlock(unsigned int _segmentSize = 4, unsigned int _numSegments = 256, void *startAddress = 0);
	~MemoryBlock(void);
	
	void Create(unsigned int _segmentSize, unsigned int _numSegments = 256, void *startAddress = 0);
	void Destroy(void);
	void *Allocate(int size = 0);
	void Deallocate(void *vp);
	void *GetStart(void);
};
#endif

```

MemoryBlock.cpp
```

#include "MemoryBlock.h"

#include <stdlib.h>
#include <memory.h>

MemoryBlock::MemoryBlock(unsigned int _segmentSize, unsigned int _numSegments, void *validStart)
{
	start = 0;
	if(_segmentSize)
	{
		Create(_segmentSize, _numSegments, validStart);
	}
}
	
MemoryBlock::~MemoryBlock(void)
{
	Destroy();
}

void MemoryBlock::Create(unsigned int _segmentSize, unsigned int _numSegments, void *validStart)
{
	if(start) Destroy();
	
	segmentSize = _segmentSize;
	
	if(validStart) start = validStart;
	else start = malloc(_segmentSize*_numSegments);
	memset(start, 0, _segmentSize * _numSegments);
		
	firstFree = (Segment *)start;
	
	Segment **thisFree = &firstFree;
	for(int i=0; i<_numSegments; i++)
	{
		(*thisFree)->start = (*((char**)thisFree)+_segmentSize);
			thisFree = (Segment **)&(*thisFree)->start;
	}
	*thisFree = 0;
}
	
void MemoryBlock::Destroy(void)
{
	if(start) free(start);
	start = 0;
}
	
void *MemoryBlock::Allocate(unsigned int size)
{
	if(size>segmentSize || !firstFree) return 0;
	Segment *thisFree = firstFree;
	firstFree = (Segment *)thisFree->start;
	return &thisFree->start;
}
	
void MemoryBlock::Deallocate(void *vp)
{
	((Segment *)vp)->start = firstFree;
	firstFree = (Segment *)vp;
}

void *MemoryBlock::GetStart(void)
{
	return start;
}

```

... It treats free segments as a linked list (using their memory as the list nodes).

---

### Post by smartbei on 2009-07-01
> **curvedinfinity said:**
> Stack space is very fast because the sizes of all of the data are set at compile time and the memory is preallocated. Those are also the downsides -- sizes can't be changed at allocation-time and there is a limited amount of memory. :D

Just to clarify, data on the stack is allocated instantly, while data on the heap may take longer. Once it is allocated there is no performance difference.

> **curvedinfinity said:**
> 
On the security front, tons of application vulnerabilities stem from "stack overflow" attacks. These involve writing into an array in the stack at an index that is past the array's bounds. The goal of the attack is to write to a spot that is executable code, and replace the actual code with some code that will take control away from the application. If you use the heap instead, you are preventing this kind of attack.

This is generally false. There is normally no executable code in the stack. Instead, the goal of the overflow is to overwrite the return address of a function, so that when the function returns, execution will jump to wherever the attacker wants (possibly into part of the data on the stack that is under the attacker's control). Note that there are simple ways to defend against this type of attack, and allocating on the heap isn't one of them - there are security vulnerabilities that are heap-based as well.

---

### Post by sidious1741 on 2009-07-01
Thank you all so much.  You've helped me out quite a bit.  This is kinda off topic but I'm really interested in security...

> **smartbei said:**
> This is generally false. There is normally no executable code in the stack. Instead, the goal of the overflow is to overwrite the return address of a function, so that when the function returns, execution will jump to wherever the attacker wants (possibly into part of the data on the stack that is under the attacker's control). Note that there are simple ways to defend against this type of attack, and allocating on the heap isn't one of them - there are security vulnerabilities that are heap-based as well.

Where do you learn something like that and what can I read to learn something like that?

---

### Post by nvteighen on 2009-07-02
Wikipedia is great on programming articles. It is one of the topics in which is pretty accurate and informative.

---

### Post by merc64 on 2009-07-02
I think this is the definitive guide:
[http://www.phrack.org/issues.html?issue=49&id=14&mode=txt](http://www.phrack.org/issues.html?issue=49&id=14&mode=txt) ("Smashing the Stack for Fun and Profit")

---

