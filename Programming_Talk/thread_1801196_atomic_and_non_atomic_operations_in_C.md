---
title: "atomic and non atomic operations in C"
date: 2011-07-10
forum: Programming Talk
---

### Post by jamesbon on 2011-07-10
I am trying to understand atomic and non atomic operations.With respect to Operating System and also with respect to C.
As per the wikipedia page [here]("http://en.wikipedia.org/wiki/Atomicity_(programming)")
Consider a simple counter which different processes can increment.
**Non-atomic**
The naive, non-atomic implementation:
reads the value in the memory location;
adds one to the value;
writes the new value back into the memory location.
Now, imagine two processes are running incrementing a single, shared memory location:
the first process reads the value in memory location;
the first process adds one to the value;
but before it can write the new value back to the memory location it is suspended, and the second process is allowed to run:
the second process reads the value in memory location, the same value that the first process read;
the second process adds one to the value;
the second process writes the new value into the memory location.



How can the above operation be made an atmoic operation.
My understanding of atomic operation is that any thing which executes without interruption is atomic.
So for example 
```
int b=1000;
  b+=1000;
```

Should be an atomic operation as per my understanding because both the instructions executed without an interruption,how ever I learned from some one that in C there is nothing known as atomic operation so above both statements are non atomic.
So what I want to understand is what is atomicity is different when it comes to programming languages than the Operating Systems?

---

### Post by ve4cib on 2011-07-10
In order to prevent the situation you describe you need to use a mechanism that will block one process from accessing the shared memory while the other is using.  Fortunately such mechanisms exist and are pretty well documented.

Try looking up the terms "mutex" and "semaphore."  Those will get you started.

---

### Post by Npl on 2011-07-10
there currently is nothing in C/C++ that allows you to guarantee atomic operation, next versions of those standards will define it. It will look like this:
```
atomic_int b = ATOMIC_VAR_INIT(1000);
atomic_exchange(&b, b + 1000);

```

If you want to guarantee atomic ops today you need assembly or libraries which have system and compiler specific code. That said, current compiler versions generally will use atomic ops if you mark a integer variable volatile, but this is their own definition - and not regulated by the standard.

---

### Post by MadCow108 on 2011-07-10
gcc provides atomic add operations:
```

int a = 5;
__sync_add_and_fetch(&a, 5);

```
[http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Atomic-Builtins.html](http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Atomic-Builtins.html)
all other compilers do to.

pretty much all modern processors support most of these operations on the hardware level by disabling memory access during the operation.
It is slower than non-atomic addition but faster than operating system locking.

---

### Post by resander on 2011-07-10
b = 1000 is atomic if there is a 'move constant into memory location' hardware instruction. Most CPUs nowadays have this instruction.

Older computers may not and need instructions like:

   ldconst reg, constant    -- load constant into register
   streg   memaddr, reg     -- store register content to memory address

which is not atomic.
However, the compiler(-writer) could (but probably wouldn't) wrap the two instructions above between turn-interrupt off&on instructions to make the sequence atomic.

So atomicity for C depends on the operation, instruction set and possibly choices made by the compiler designer.

The operations of an operating system are more complex and atomicity when needed is implemented by semaphores, critical sections etc. Same is true for filing systems and database systems that may also provide higher-level locks to prevent double-update problems etc.

---

