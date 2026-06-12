---
title: "&quot;Memory Pool&quot;"
date: 2008-08-13
forum: Programming Talk
---

### Post by lordhaworth on 2008-08-13
Heya

Question: programming using pointers, arrays etc uses up memory from a "memory pool" --> a chunk of available memory that is used up as arrays etc are allocated memory. Will the size of this pool be determined by the kernel (I dont know much about this) or will it be all that the computer has available?

I obviously dont plan on messing around with the kernel, and I never write programs that require more memory than I have (well not yet anyway). I was just wondering if it would be possible (for like massive simulatons) to do a sort of kernel compile time memory allocation so that absolutely everything possible could be immediately dedicated to the running of the simulation?

This is really just out of curiosity - and hopefully ill learn a bit more about the deeper workings of my computer when Im programming.

Cheers

Tom

---

### Post by nvteighen on 2008-08-13
The stack is a fixed amount of memory determined by the kernel, though you can modify it running the ulimit command (please, read the man page before. ulimit can change lots of other things too). By default, in my system it is around 8 MB. Enough for data stored in stack.

The heap, dynamic memory, is also determined by the kernel, but its size can be modified at runtime by a system call. So, when you do a malloc()/new (I assume you're on C or C++ because of the kind of your question) and there's no more memory on heap, the system will resize it for you... of course, until there's no memory available in your system.

---

### Post by lordhaworth on 2008-08-13
Ahh ok so the dynamic allocation just uses up everything eventually and not just a portion given by the kernel.

Thanks very much for your response!

---

### Post by dwhitney67 on 2008-08-13
> **lordhaworth said:**
> Ahh ok so the dynamic allocation just uses up everything eventually and not just a portion given by the kernel.

Thanks very much for your response!
Your application could potentially use all the memory that is _available_.  Note that other applications that are running, including the kernel, are already using some of your system's memory.

When an application starts demanding more memory than there is available, idle applications could have some (if not all) of their memory contents relegated to the swap space.

Obviously an application that requests more memory space than is available will fail to get such memory allocated; in practice, the application needs to handle this situation "gracefully".  Other developers may share a different opinion.  These opinions are not what matter here; what matters is that you understand how the system doles out memory that is allocated.

---

### Post by Lster on 2008-08-13
I think this section in Wikipedia might be useful to you:

[http://en.wikipedia.org/wiki/Malloc#The_glibc_allocator](http://en.wikipedia.org/wiki/Malloc#The_glibc_allocator)

---

### Post by lordhaworth on 2008-08-13
thanks everyone, this is pretty new to me so ill go away and read up a bit. Ive never really worried about what makes the programs i write work - might be worth a look though!

---

### Post by pmasiar on 2008-08-13
Wikipedia has the answers: [http://en.wikipedia.org/wiki/Dynamic_memory_allocation](http://en.wikipedia.org/wiki/Dynamic_memory_allocation) [http://en.wikipedia.org/wiki/Stack-based_memory_allocation](http://en.wikipedia.org/wiki/Stack-based_memory_allocation)

Also, if even swap space is not enough, there is another trick: use direct memory mapping of data tables to files on disk (basically extending swap file with custom datafiles), which allowed incredibly fast swapping of the data in and out.

[http://en.wikipedia.org/wiki/Main_memory_database](http://en.wikipedia.org/wiki/Main_memory_database)

---

