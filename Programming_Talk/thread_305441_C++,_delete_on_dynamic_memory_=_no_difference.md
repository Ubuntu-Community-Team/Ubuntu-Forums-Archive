---
title: "C++, delete on dynamic memory = no difference"
date: 2006-11-23
forum: Programming Talk
---

### Post by Freddd on 2006-11-23
Hey,
I have made a simple linked list program to test how to use dynamic memory allocation with C++. My test program does the following:

1. Creates 1 million new nodes, when I tell it to do so..
2. deletes all nodes, when I tell it to do so..

I use the System Monitor in Ubuntu (Edgy) to check the amount of resident memory used by my program.

The program uses 836.0 KiB when I startup the application. It uses 16.1 MiB when I have created my 1 million nodes. But why does my application use the same amount of memory when I delete all my dynamic allocated nodes? I have compiled and tested the same application in Windows where this problem doesn't occur.

I have also performed these test on a program using dynamic arrays. Believe it or not but here I can see the difference of amount of memory used when doing a delete on all my nodes created with new.

I have attached my source file, in case it would be helpful.

The person helping me to sort out this confusion deserves a big golden star!

---

### Post by Freddd on 2006-11-24
Anyone?

---

### Post by Arndt on 2006-11-24
> **Freddd said:**
> Hey,
I have made a simple linked list program to test how to use dynamic memory allocation with C++. My test program does the following:

1. Creates 1 million new nodes, when I tell it to do so..
2. deletes all nodes, when I tell it to do so..

I use the System Monitor in Ubuntu (Edgy) to check the amount of resident memory used by my program.

The program uses 836.0 KiB when I startup the application. It uses 16.1 MiB when I have created my 1 million nodes. But why does my application use the same amount of memory when I delete all my dynamic allocated nodes? I have compiled and tested the same application in Windows where this problem doesn't occur.

I have also performed these test on a program using dynamic arrays. Believe it or not but here I can see the difference of amount of memory used when doing a delete on all my nodes created with new.

I have attached my source file, in case it would be helpful.

The person helping me to sort out this confusion deserves a big golden star!

The classical way of doing memory allocation in Unix is to find out where the limit of available space is, and then tell the system to raise it by the amount you want (the system calls are called brk and sbrk). The memory allocation functions of the language you're using do this and then create an appropriate structure (list, array or whatever) and sends it to you.

To give back memory to the system would be by lowering the limit again, with the same system calls. In practice, this is never done, because of two reasons:

1) Usually, a number of allocation calls are been made from the user's code, some structures freed again, etc. so that you might give back a big block if it wasn't for one chunk in the middle of it that's still used, and the added complexity of keeping track of when you can lower the limit isn't worth it;

2) It's unusual for a program to at an early point allocate a lot of memory, and later use only a tiny portion, so it makes sense to assume that if memory is freed by your program, it will be worth keeping the allocated memory around to reuse later. The rare exceptions exist, of course. 

3) Even when the memory was given back to the system by brk/sbrk, it wouldn't actually be made available to other programs. Only the bookkeeping value of where the limit is would be changed. I don't know if this is the case in Linux, but it used to be in most older Unix systems.


A more modern way of allocation could make use of the system call mmap, which doesn't require the new block of memory to be adjacent to any old one. I don't know how much it is used in modern allocators.

If your application is not just a test program, but one of the exceptions to my point 2, maybe you can: A) do whatever calculation it is that takes so much space in a separate process and write its result to a file, then exit it and start the other small process to do the remaining calculation; B) Forget the problem - 16M is not that much, and if the memory really isn't used, it will be paged out so it won't bother other processes, unless swap memory is really low; C) Scenario A, but let the processes communicate in real time, and restart the first process whenever it gets too large.

---

### Post by Freddd on 2006-11-24
Thanks for this great explanation :)
Do you know why this isn't the case for int arrays? 

> I have also performed these test on a program using dynamic int arrays. Believe it or not but here I can see the difference of amount of memory used when doing a delete on my array created with new.

---

### Post by Arndt on 2006-11-24
> **Freddd said:**
> Thanks for this great explanation :)
Do you know why this isn't the case for int arrays?

I missed that part before. No, I don't have an explanation for that.

---

