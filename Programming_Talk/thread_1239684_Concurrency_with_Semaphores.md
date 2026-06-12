---
title: "Concurrency with Semaphores"
date: 2009-08-13
forum: Programming Talk
---

### Post by matthew.ball on 2009-08-13
Hey,

I'm looking into how concurrency works, and everything I have seen points towards Semaphores, though I'm not quite sure I can fully appreciate what a Semaphore is, let alone what one does.

Just wondering if anyone has any useful documentation? Any papers or anything? I have read the wiki pages, but yeah still asking questions.

---

### Post by Cenoforums on 2009-08-15
Concurrency is quite the academic topic. You're probably better off having a quick read on a book about Operating Systems. I think they're a couple on google. It's not that hard.

Last October I wrote a short essay on the linux implementation of spinlocks and semaphores, analysing the actual (assembly) code. I can show you if you're curious, but if you're still trying to grasp the concept itself...

---

### Post by soltanis on 2009-08-15
Very quickly, a semaphore is basically like a little counter variable that concurrent processes all have access to. Incrementing/decrementing it is an atomic operation (concurrent processes can't mess each other up by trying to modify the semaphore at the same time). The simplest semaphores are just counters set to a certain value:

```

int semaphore = 5;

```

If you wanted to access a resource, you would decrement the semaphore, indicating that the resource is in use:

```

void access_resource(void) {
         entry:
         if (semaphore > 0) semaphore--;
         else goto entry;
}

access_resource();

```

(As you can see, my use of goto precludes this from being actually useful code).

If the semaphore has reached a count of zero, the function above would wait indefinitely until it was greater than zero again. Freeing a resource is done by incrementing the semaphore:

```

void free_resource(void) {
        semaphore++;
}

free_resource();

```

This is a very simplified look at semaphores. Note that first of all, my code implements no sort of concurrency control, the biggest point being that in the middle of the access_resource function, the process might have execution time taken away from it; in other words, it would pass the if condition but not get to actually decrementing the semaphore, in which case we have a problem, because the process has access to the semaphore, but another process that might've been pre-empted from having access to the resource will still be able to pass the conditional check -- a race condition.

Additionally, most semaphores implement queues on a first come, first serve basis; this implementation is a stupid spin-lock (whoever is lucky enough to get the process time first gets the resource first).

Look at

[http://en.wikipedia.org/wiki/Semaphore_(programming](http://en.wikipedia.org/wiki/Semaphore_(programming))

For a more in-depth discussion.

---

### Post by lisati on 2009-08-15
The term "semaphore" in the context of concurrency, is like the [flag]("http://en.wikipedia.org/wiki/Flag_semaphore") from which it gets its name. It's a method of communicating between different processes which might want, for example, to share resources. 

Example: Suppose you have multiple processes which want to read and update a file (maybe you're working on an online booking system for a travel agent). When the semaphore variable is set to one value, it can mean something like "the file is not being used", and when set to another value, it can mean "wait a while, the file is being updated and the contents might not be reliable".

EDIT: Have a look here: [http://en.wikipedia.org/wiki/Semaphore_(programming](http://en.wikipedia.org/wiki/Semaphore_(programming))

---

### Post by dwhitney67 on 2009-08-15
soltanis and lisati provided good examples.

I used a semaphore in an interrupt handler that I configured within a device driver for a VME board that provided timing to the system.  If the IRIG-B time signal coming into the board is lost, then the interrupt handler would increment the semaphore by one.  Otherwise, if the signal is available, then the semaphore is reset to zero.

When/if the semaphore count reached 5, then this would indicate to the system to acquire timing from the main CPU board.  The main CPU board relied on a chip-set, which in turn relied on crystals (which degrade over the years) to provide the timing to the system.  The main CPU board was not considered precise enough for day-to-day activities, but usable in cases where the system had lost its primary time source.

When developing concurrent applications, another similar entity, called a mutex, can be used.  There are different types of mutexes, but the most commonly used type of mutex behaves in a "ping-pong" fashion.  This is similar to a semaphore being set to a one, and then back to a zero.

---

### Post by matthew.ball on 2009-08-15
> **soltanis said:**
> Very quickly, a semaphore is basically like a little counter variable that concurrent processes all have access to. Incrementing/decrementing it is an atomic operation (concurrent processes can't mess each other up by trying to modify the semaphore at the same time). The simplest semaphores are just counters set to a certain value:

```

int semaphore = 5;

```

If you wanted to access a resource, you would decrement the semaphore, indicating that the resource is in use:

```

void access_resource(void) {
         entry:
         if (semaphore > 0) semaphore--;
         else goto entry;
}

access_resource();

```

(As you can see, my use of goto precludes this from being actually useful code).

If the semaphore has reached a count of zero, the function above would wait indefinitely until it was greater than zero again. Freeing a resource is done by incrementing the semaphore:

```

void free_resource(void) {
        semaphore++;
}

free_resource();

```

This is a very simplified look at semaphores. Note that first of all, my code implements no sort of concurrency control, the biggest point being that in the middle of the access_resource function, the process might have execution time taken away from it; in other words, it would pass the if condition but not get to actually decrementing the semaphore, in which case we have a problem, because the process has access to the semaphore, but another process that might've been pre-empted from having access to the resource will still be able to pass the conditional check -- a race condition.

Additionally, most semaphores implement queues on a first come, first serve basis; this implementation is a stupid spin-lock (whoever is lucky enough to get the process time first gets the resource first).

Look at

[http://en.wikipedia.org/wiki/Semaphore_(programming](http://en.wikipedia.org/wiki/Semaphore_(programming))

For a more in-depth discussion.
Thank you. Great explanation.

I think what I was looking for, was somebody explicitly mentioning the fact that increment/decrement operations are atomic, I suppose we can therefore guarantee they will execute when they appear, as opposed to compound instructions which may execute over a few cycles.

I am actually very interested in Operating System, design and implementation, and I have noticed concurrency is rather important.

---

### Post by soltanis on 2009-08-16
> **matthew.ball said:**
> 
I am actually very interested in Operating System, design and implementation, and I have noticed concurrency is rather important.

This is a pretty important mechanism for operating systems to consider, yes.

---

