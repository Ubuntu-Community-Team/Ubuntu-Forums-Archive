---
title: "Are thread stacks virtual?"
date: 2009-10-14
forum: Programming Talk
---

### Post by resander on 2009-10-14
I am new to threads and have been googling a bit to find out about sizes of thread stacks. Someone wrote that pthread_attr_setstacksize only allocates space in virtual memory with no physical behind it. Is this really so?

I want to put an application on a server using sockets with multi threading using one thread for each connection. There would be one procedure 'listener' for each connection run by/in a thread. Each connection needs workspace and the code snippet  below gets that workspace by a simple array declaration on entry to the procedure. The workspace stays for as long as the procedure is active (carryon is true) and is automatically returned on exit. 

```

bool carryon = true ;
void listener ( )
   {
   char workspace [ 500000 ] ;   // allocated on thread stack

   while ( carryon )
      {
      waitforclientmessage() ;
      actonmessage ( workspace ) ;   // pass workspace to handler 
      }
   }

```

There will be delays when actonmessage is running if the kernel has to map in missing physical memory. How significant would these be? Would they be only for the for the first client message, i.e. would the kernel leave the physical memory alone once allocated to the thread stack?

Would allocating memory by char * space = new char[ 500000 ] behave differently?

Which way is best or fastest?

---

### Post by napsy on 2009-10-14
I think posix threads come with 8MB of stack size. If you're running out of stack space, then your algorith should be reworked to use heap allocation.

Usually stack allocation is faster but limited. All programs use virtual addressing. In this way they always see the "whole memory".

---

### Post by dwhitney67 on 2009-10-14
> **resander said:**
> ... Each connection needs workspace ...
If you say so.  But you have not provided any detail for why this is so.

Perhaps you could reconsider your approach to the design such that you would not have to have a ~500K array per client.

---

### Post by resander on 2009-10-14
The app is a special-purpose database + report generator that would run on a server to allow ultra-thin clients to obtain datasheets about products, request product comparisons and more detailed product information stored in the database.

The volume sent back to clients can be quite large and having workspace for each connection makes marshalling data back to the client easier and faster, besides there is a need to keep a connection state to be able to transfer in parts, retransmit etc. I am not sure yet, but having about 20KB will probably be enough. 500KB was just for the forum question.

I am still not sure whether to allocate space on the thread stack by char stackspace[20000] or ask for space from the heap by char * heapspace = new char[20000] or whether it matters.

Which of the following two is likely to be faster?

  memset ( stackspace , 0 , 20000 ) or memset ( heapspace , 0 , 20000 )

If there is unallocated physical memory, a 'hole', in the virtual space of stackspace/heapspace, hardware will suspend memset instruction and the kernel will need to find physical memory to plug the hole. Dont't know how long it will take for memset to be resumed, but it may well be the performance of the memset has been ruined. The more holes the worse it will get. The memset above is just a single operation that affects all locations in the space. Any other operations with operands in the space would suffer in the same way.     

Which space would have less holes of unallocated memory in it. Heap or stack space? I think heapspace should have fewer, because new char[] somehow seems like a stronger, more urgent and definite request for memory than getting 8MB thread stack without asking for it. But the kernel may not see it like that!

---

### Post by dwhitney67 on 2009-10-14
If I were you, I would be more concerned about getting the server to work rather than burden yourself with whether stack memory or heap memory is better.

Personally, when I initialize stack memory, I use:
```

char stack[20000] = {0};

```
It is my understanding that the "new" operator initializes the allocated memory to zero, thus obviating the need to even use memset(); but I may be wrong on this.

---

### Post by resander on 2009-10-15
I am going to use stack allocation. 

Issuing memset(space,0,size) upfront before entering the server loop* will cause the entire size range to be mapped to physical memory, so there should be less or no memory mappings/unmappings when client is served. 

*server loop is only for the forum question. The real code uses socket listen and accepts.

---

### Post by dwhitney67 on 2009-10-15
> **resander said:**
> ...
Issuing memset(space,0,size) upfront before entering the server loop* will cause the entire size range to be mapped to physical memory...

Where did you obtain this info?

Here's the link to the man-page for memset():  [http://linux.die.net/man/3/memset](http://linux.die.net/man/3/memset)

---

### Post by resander on 2009-10-16
The compiler and linker produce a simple, linear virtual address space. 
When a program is running a memory management unit (MMU) hardware component translates virtual addresses to addreseses in physical memory. The virtual space is divided into segments 4KB or larger and the kernel+MMU ensure there is physical memory for segments as required by a program. For example, if a=1; is executed and variable a has virtual address 12345, then the MMU would detect if there is no physical memory for 12345 and generate a page-fault interrupt. The OS kernel handles this interrupt and has to find physical memory. If there is no free memory the kernel has to get it which may require the contents of the memory to be saved on disk first so it can be restored. So, a single memory reference to virtual memory can lead to a slow disk access. If there is too much of this the system could spend most of its time swapping and doing very little work.

The default thread virtual stack space is 8MB. My guess is that the first segment of the stack is mapped to physical memory and the rest is left unmapped. The MMU+kernel would spring to life when the program makes a memory reference in the unmapped address range. With

```

  char space [ 20000 ];
  memset ( space, 0 , 20000 );

```

then memset makes 20000 memory references to space, space+1, space+2...
On completion the whole virtual address range would be mapped to physical memory.

---

