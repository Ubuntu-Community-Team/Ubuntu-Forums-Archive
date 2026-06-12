---
title: "C: Stack vs Heap. What are they? Why do they exist?"
date: 2010-10-20
forum: Programming Talk
---

### Post by Pithikos on 2010-10-20
So continuing with learning some C I came across stack and heap memory. I understand that they are two main parts of the memory to store data. In fact dynamic memory allocation is happening in the heap and function parameters and variables are stored in the stack. 

My questions:

[LIST]
[*]Why can't there be ONE BIG place for everything to be stored instead of having two places?
[*]In hardware terms is stack different than heap? I read somewhere that stack is smaller and faster than heap. That means it sits somewhere else right?
[*]Is stack the cache of the RAM?
[/LIST]
I searched around quite a bit but noone says anything more than "stack is for that" and "heap is for that". Noone explains WHY it is like that. Some people even encourage you to not care about it and just program. But I want to know what the heck I am doing when I program so was hoping some more experienced soul could help a bit with my questions :)

---

### Post by Arndt on 2010-10-20
> **Pithikos said:**
> So continuing with learning some C I came across stack and heap memory. I understand that they are two main parts of the memory to store data. In fact dynamic memory allocation is happening in the heap and function parameters and variables are stored in the stack. 

My questions:

[LIST]
[*]Why can't there be ONE BIG place for everything to be stored instead of having two places?
[*]In hardware terms is stack different than heap? I read somewhere that stack is smaller and faster than heap. That means it sits somewhere else right?
[*]Is stack the cache of the RAM?
[/LIST]
I searched around quite a bit but noone says anything more than "stack is for that" and "heap is for that". Noone explains WHY it is like that. Some people even encourage you to not care about it and just program. But I want to know what the heck I am doing when I program so was hoping some more experienced soul could help a bit with my questions :)

What's special with the stack is that it grows and shrinks, usually because when a function call is made, the place to return to, and the current local variables must be stored there, and can then be restored.

Since pushing and popping on a stack turned out to be a popular operation, most processor architectures incorporated some special instruction to do just that (in the sixties/seventies). I am not so familiar with architectures where the stack and heap memory are handled entirely separately. One idea is to cache the last part of the stack (or the whole stack) in faster memory, since you know it will soon be used again.

Often, the operating system sets things up for your program, and the usual pattern is to have the stack somewhat limited, in some environments very very limited. This is often not a big problem, unless you try to program recursive functions using the ordinary stack - then you will have to set up a stack of your own in the heap instead.

---

### Post by StephenF on 2010-10-20
The heap on the other hand is like checking a book out of library except these books are read/write and may have random stuff in them already which needs to be ignored.

---

### Post by worksofcraft on 2010-10-20
They are two different ways of managing computer memory.

- Stack memory as always allocated and then deallocated on a first in last out basis: The next available stack address is always known and there need never be any unused gaps.

Obtaining memory from the stack is as easy as moving the stack pointer register by the amount that you need and releasing that memory again you simply move it the other direction by the same amount. The compiler knows at compile time the address of any data here relative to the stack pointer register so accessing it has little overhead.

Stack is well suited to nested function calls: Each time you enter a function the stack pointer moves to reserve space for it's local variables and when you return from the function it simply moves back again releasing that memory in a single instruction. 

- Heap memory is allocated as and when you need it and can be released back to the system when ever you want. That means it has to keep a record of all the bits that are in use and all the bits that are not.
The heap can become "fragmented" with gaps of unused bits being released in between used bits. It can't simply shuffle things about to keep the unused space contiguous because then addresses and memory pointers would change and the program could lose track of them.

Thus when you ask to allocate a certain size of heap memory it has to hunt through it's unused area looking for a chunk that is big enough. With heap memory something needs to determine when it is no longer in use and that either has to be done by the programmer, or by software called "garbage collection".

Doing explicit heap memory management is a nuisance to the programmer and can have bugs known as "memory leak". Also garbage collectors can get it wrong sometimes failing to recognize when items on the heap are no longer used, thus effectively also a kind of "memory leak".

Some languages like Python and Java as you suggest do everything on the heap, but others like C allow you the choice.

p.s. The processor always has to have a stack defined because that is how it remembers where to return from function calls and also where it saves and restores things when an interrupt occurs, regardless what language you program in, but for your data you don't have to use it.

---

### Post by psusi on 2010-10-20
> **Pithikos said:**
> 
[*]Why can't there be ONE BIG place for everything to be stored instead of having two places?

Because they fundamentally perform different functions.  The stack grows and shrinks as one unit.  The heap allocates and frees different chunks at different times.  The stack only needs a single pointer to its current top.  The heap needs more book keeping.

> **Pithikos said:**
> [*]In hardware terms is stack different than heap? I read somewhere that stack is smaller and faster than heap. That means it sits somewhere else right?

There is no physical difference; they are both in ram.  The stack is just allocated when the program starts up, and the heap allocates more space from the OS as needed.

The processor has a special register to keep track of the stack, called the stack pointer.  Whenever you make a function call, the processor call instruction pushes the return address onto the stack so that the function can return when it is finished.  Other registers may be pushed onto the stack as well during the execution of the function if their contents need to be retained for a while, but the register is needed for some other operation.  Later when the saved value is needed, it is poped back off the stack.  C also allocates local variables on the stack by moving the stack pointer when the function starts, and moving it back before returning.  Push and pop are implemented as single machine instructions that load/store to/from the current stack pointer location, then increment/decrement the stack pointer.

The heap is where malloc/free/new/delete allocate and return memory to.

---

### Post by schauerlich on 2010-10-20
Basically: The stack is where a program "starts". Every program gets a stack, and unless you tell it otherwise, that's the only memory you'll use. Every time you call a function, you're using the stack for your bookkeeping. For instance, once you're done with the current function, where should your program go next? That type of stuff is recorded on the stack. The stack is also faster because the hardware itself keeps track of where the stack is, instead of having to read in a pointer from memory and then dereferencing it. In C, unless you specifically use malloc, just about all of your data will be placed on the stack (excluding globals and static local variables).

The heap, however, is usually used for "big" things, or things that don't have a known size when you're writing the program. The OS is in charge of who gets what memory, and every time you use malloc, you're asking the OS for more. This memory comes from "the heap", which is just an area of memory "somewhere else" that the OS maintains. When you use malloc, the OS goes off, finds some free memory in the heap, and gives you a pointer to it.

Now, why is the heap usually saved for big things? The OS is also in charge of how big your stack will be when the program starts, and it's usually pretty stingy (around 10mb). For small applications, this will be fine. But can you imagine firefox trying to work in only 10mb RAM? And that 10mb includes all of the bookkeeping from every function call. It just won't work. So, since keeping everything on the stack is faster (no calls to malloc and free), most small things go there, whereas big things that won't fit on the stack are thrown on the heap. 

Another common usage of the heap is for things for which the size is not known at compile time. Say you want to keep track of data structures based on what's read from read from a file: how much memory should you allocate? Well, it depends on how man entries are in the file... but that could change. Sure, you can try to guess and allocate way more space than is necessary, but that's wasteful and the file might STILL be bigger. So instead, you can learn the size of the file at run time, and use that number to ask the OS for more memory on the heap. Now you have exactly as much memory as you need, and you don't have to worry about your buffer not being big enough. (assuming someone doesn't give you a file bigger than all your RAM, in which case they're just annoying).

So, to sum it up: the stack is small, fast, and static. The heap is big, slightly slower and flexible.

---

### Post by psusi on 2010-10-20
> **worksofcraft said:**
> 
Some languages like Python and Java as you suggest do everything on the heap, but others like C allow you the choice.


Not quite.  All *objects* are allocated on the heap, but the local variable that points to the object is still on the stack.

---

### Post by psusi on 2010-10-20
> **schauerlich said:**
> In C, unless you specifically use malloc, all of your data will be placed on the stack.

Except for globals.  And static locals.

---

### Post by schauerlich on 2010-10-20
> **psusi said:**
> Except for globals.  And static locals.

Fixed. :)

---

### Post by CptPicard on 2010-10-20
> **worksofcraft said:**
> 
Some languages like Python and Java as you suggest do everything on the heap, but others like C allow you the choice.

In Java, primitives and and object references are on the stack. Actual object data is on the heap.

In higher level languages like Python in general, the "choice" is irrelevant as the language just is not defined in a way where the difference would be meaningful -- as long as the scoping rules hold, it does not matter where the data actually resides in memory.

This is actually not all that different from languages like C or even the CPU stack-manipulation instructions; they just simply enforce (or help enforce) certain scoping rules by making use of appropriate regions of the memory.

---

### Post by worksofcraft on 2010-10-20
> **psusi said:**
> Not quite.  All *objects* are allocated on the heap, but the local variable that points to the object is still on the stack.

AFIK the programmer cannot create pointer types in neither Python, nor Java.

> **CptPicard said:**
> In Java, primitives and and object references are on the stack. Actual object data is on the heap...


I suspect you are referring to low level internal implementation details?

Conceptually all the data that you, the programmer, define in Python or Java is allocated from and returned to a single memory pool. Scoping rules may allow this to be optimized in certain circumstances by the compiler. Whether it does or doesn't and under what circumstances said optimization takes place is not specified and implementation dependent and not really helping explain the topic IMHO.

---

### Post by psusi on 2010-10-20
> **worksofcraft said:**
> AFIK the programmer cannot create pointer types in neither Python, nor Java.

It calls them references and limits what you can do with them, but they are really pointers.

> **worksofcraft said:**
> 
I suspect you are referring to low level internal implementation details?

Yes.

---

### Post by unknownPoster on 2010-10-20
> **worksofcraft said:**
> AFIK the programmer cannot create pointer types in neither Python, nor Java.


EDIT: Psusi beat me to it.

---

### Post by worksofcraft on 2010-10-20
> **unknownPoster said:**
> In Java, any reference to a simple type is by value. However, any reference to an Object is a pointer.

Well actually in some systems all references and pointers are implemented as indexes in a run time system pointer table.
This table is under control of the memory management system. The purpose of this is so that the heap can be reorganized to keep free space in the memory pool contiguous.
Such implementation and optimization details don't help clarify the principle IMO.

---

### Post by drdos2006 on 2010-10-20
Maybe a piece of programming may help the poster.

This is how the heap is memory is used.
```
 
const 	long 	int MEM_POINTERS 	= 	     1000	;
long    int     * mem_pointers[MEM_POINTERS]	;
int	ARRAY_WIDTH = 10	;
/*------------------------------ ADD_MEM ---------*/
void add_mem()
{
	    int j			; //temporary int

	mem_pointers[max_records] = new long int[CNT_ARRAY]		; //find last record number and add

	if ( mem_pointers[max_records] == NULL )
	{
        	cout << "Error.. Mem_pointers[max_records] is NULL.. \n"	;
		exit(1)					;
	}
	else
	{
	for ( j = 0 ; j < ARRAY_WIDTH ; j++ ) mem_pointers[max_records][j] = var[j] ; // the variable array numbers
	}
}

```

The compiler allocates 1000 times 10 of heap memory places for the program to run in.
The stack is usually run in faster cache RAM which is part of the CPU.
Heap is storage RAM for allocation of data, the operating system normally takes care of memory allocation and the compiler uses the OS.

Hope that helps.

regards

---

### Post by psusi on 2010-10-20
> **drdos2006 said:**
> 
The stack is usually run in faster cache RAM which is part of the CPU.


No, it isn't.  RAM is ram; the processor caches it all equally and does not know or care which parts are used for the stack or heap.

---

### Post by nvteighen on 2010-10-21
The reason why they exist is because a computer always needs to know how big your data is beforehand or otherwise, it won't be able to calculate how much memory is to be used.

Compile-time known variables are the easy part: the code itself tells the computer how big stuff is. But the issue is dynamic memory, data whose size isn't known until created... for that kind of data, the computer will need a fixed-length pointer variable that should be correctly set where that data will be allocated at runtime (malloc).

Now, from what I've observed (I may be wrong), stack vs. heap is actually an abstraction offered by the C and the OS, not Assembly. What you get from the OS is a size-fixed chunk of memory for your program... And what you get from Assembly is the ability to allocate stuff wherever you like, even outside the space reserved for your program, although you probably will crash your program if you don't use the stack pointer or the kernel to get a valid memory address (there comes the OS's protection system... DOS hadn't any...). The "popping" stack effect is a consequence of the so-called "C calling convention", which allows you to organize that "size-fixed chunk of memory" into a stack data structure and pop out stuff that won't be used.

So, the heap is only accessable through the OS, as it requires allocating memory outside the space normally reserved for a program. That's why you need a syscall (sbrk, IIRC) or the C Std. Library to do it.

> **worksofcraft said:**
> AFIK the programmer cannot create pointer types in neither Python, nor Java.


No, the only language of that abstraction level that I know that can do that is Perl... (using the \ operator as C's & operator to allocate a memory address to a scalar $).

---

### Post by psusi on 2010-10-21
> **nvteighen said:**
> 
Now, from what I've observed (I may be wrong), stack vs. heap is actually an abstraction offered by the C and the OS, not Assembly.

The stack is there in assembly.  The hardware requires it for use when calling functions and handling interrupts, and provides push/pop instructions that use it for register spilling.  You don't have to pass arguments or store locals there like C does, but it is convenient to do so.

---

### Post by maximinus_uk on 2010-10-21
> **psusi said:**
> The stack is there in assembly.  The hardware requires it for use when calling functions and handling interrupts, and provides push/pop instructions that use it for register spilling.  You don't have to pass arguments or store locals there like C does, but it is convenient to do so.

You are right (but of course, you can put the stack where you like by setting the stack pointer), a stack is internal to most (all?) CPU's but the heap is part of the way that C works.

The heap comes from the languages equivalent to C's malloc() call., which needs to find extra free memory.

Basically, in almost all languages you'll never have to worry about stack / heap differences, and even then only when mixing assembly with the language. Even the stack is reasonably trivial: although it became more common in the mid-80's for CPU's to give more functionality to it by adding extra CPU instructions (I first met these on the Motorola 68000 after programming on the Z80), most assembly coders didn't need to use them. I never did.

On 1980's / 1990's machines, normally the stack started at the bottom of the free memory (which could be quite high - maybe above 16k! - since often the ROM took up the first addressable part of memory) and went upwards, whereas the heap started at the top of memory and went downwards. Again though, this was only a language issue - there is no malloc() call in assembly and thus no heap.

Nowadays I use languages where I don't need to remember this kind of thing, but sometimes I miss the 8-bit days when you could fit the whole computer system in your head :)

---

### Post by CptPicard on 2010-10-21
> **worksofcraft said:**
> 
I suspect you are referring to low level internal implementation details?

Yes, because there was a claim about those that was incorrect. Primitive types, including object references that are in local scopes on the call stack are on the stack. Rest is on the heap.

> 
Conceptually all the data that you, the programmer, define in Python or Java is allocated from and returned to a single memory pool. 

If you *want* to make the distinction between heap and stack allocation as it happens in, say, C, then no, Java does not behave the same way as Python does -- in Python everything really is on the heap (although call stack scope management is driven through the underlying C stack of the interpreter).

I guess I could then just as well say that everything in any language is conceptually allocated from the same memory pool -- the RAM. It's just that the scoping is managed differently in implementation, whether it is the C stack or a system of linked "environment frames" as in Scheme...

---

### Post by mimiteto on 2010-10-21
I wanna thank all of you for the great discussion you've made on such unclear matter!
THANK ALL OF YOU

---

### Post by nvteighen on 2010-10-21
> **psusi said:**
> The stack is there in assembly.  The hardware requires it for use when calling functions and handling interrupts, and provides push/pop instructions that use it for register spilling.  You don't have to pass arguments or store locals there like C does, but it is convenient to do so.

Oh, yeah, I'm stupid... of course there's pop/push... :P

Thanks for your insight!

---

### Post by Pithikos on 2010-10-21
I don't know assembly so some comments were a bit hard to understand. After all it's my second month in university.
I think anyway that I got a better intuition of what the stack and heap are and what they do. At least I know now that both are just different places in the same physical memory and that they are kept apart from each other for some convenient reasons.

A bonus question for getting so many replies :mrgreen::
**How can all RAM addresses start from 0000 and end at FFFF?** Shouldn't the memory size be a factor for the amount of addresses a RAM has?

---

### Post by psusi on 2010-10-21
> **Pithikos said:**
> 
A bonus question for getting so many replies :mrgreen::
**How can all RAM addresses start from 0000 and end at FFFF?** Shouldn't the memory size be a factor for the amount of addresses a RAM has?

They don't, and of course.

---

### Post by worksofcraft on 2010-10-21
> **Pithikos said:**
> 
A bonus question for getting so many replies :mrgreen::
**How can all RAM addresses start from 0000 and end at FFFF?** Shouldn't the memory size be a factor for the amount of addresses a RAM has?

lol - well the adresses do have a quite a few more bits in them these days and so on a 32 bit system you will find they go all the way up to FFFFFFFF (hex) and on on a 64 bit system it's... well twice as many eF's

The addresses and pointers that your applications use are however NOT actual physical memory addresses. They are translated from virtual address space to physical address space by a memory management unit (MMU). The MMU helps to separate address space of applications and kernel so that you can't "peek" and "poke" kernel memory, or that of other applications.

Virtual address space can be larger than the available memory. One of the functions of your Linux "swap partition" is to hold data for virtual addresses when there isn't any physical memory space for it. If you try to address such a location an interrupt is generated and the processor swaps the desired memory image to or from disk...

---

### Post by saulgoode on 2010-10-21
One distinction between stack and heap is that heap allocations can be shared between threads whereas stack memory is always intended to be local to a particular thread (each thread has its own stack and it would be foolhardy for another thread to attempt to access data on that stack).

---

