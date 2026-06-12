---
title: "Thread safe very large array"
date: 2010-02-15
forum: Programming Talk
---

### Post by night_fox on 2010-02-15
I've found this part of the forums awesome at answering my programming questions. Many thanks to everyone who's helped me. I have another few questions which stem from this one:

How would I make a very large character array safely accessible by large numbers of threads at the same time? Is there an api that does this or do I have to write my own?

Simply mutexing the whole thing isn't good enough. The threads have to be able to actually read different parts of the array at the same time.

---

### Post by howlingmadhowie on 2010-02-15
If all you want to do is read from the array then you don't have to worry about anything.  Writing is of course a different matter ...

---

### Post by night_fox on 2010-02-15
OK, that solves my problem for now, because all i want to do is read, but what if I wanted to write to another (not necessarily different) part at the same time?

---

### Post by night_fox on 2010-02-15
This sort of thing would be very useful for image processing!

---

### Post by Zugzwang on 2010-02-15
If the array has a constant length, you can lock each individual array item. Which programming language are you using?

---

### Post by night_fox on 2010-02-15
Hello Zugzwang,

I'm using c, and doing threads with glib.

Its not an array of structs, I suppose its an array of chars, and its too big to lock each char. Its length is constant, but it can't be split into constant chunks.

I'm thinking of keeping track of variable chunks, locking those, and changing them all the time.

---

### Post by howlingmadhowie on 2010-02-15
> **night_fox said:**
> OK, that solves my problem for now, because all i want to do is read, but what if I wanted to write to another (not necessarily different) part at the same time?

if it isn't a different part then things start to get complicated. what do the different threads do with the content? if one thread changes part of the array, does another thread which has already read that part need to be informed of this?  generally you can add mutexes or semaphores to ranges in the array which may prove to be more efficient than having a mutex or semaphore for each element.

the general idea would be:
```

struct { int start;
         int end;
         int id;
       } range;

range* ranges_in_use;

atomic boolean add_range(range r);
atomic boolean drop_range(range r);

atomic boolean is_in_use(int position) { // code to check
 // if the character at position is free
}

```

Forgive my pseudo C-code, it's been a while :)

---

### Post by Zugzwang on 2010-02-15
> **night_fox said:**
> 
I'm thinking of keeping track of variable chunks, locking those, and changing them all the time.

I'm not sure if I've got the same idea, but here's one:

Your character array has a size of N. You allocate M mutexes (e.g., M=32). Whenever you want to access element 0<=i<N, you lock the mutex "i MOD M", where "mod" refers to taking the modulo, which you would do with the "%" operation in C.

However, that will be very slow. It is normally better to optimize locality of your algorithm, split your array into continuous regions and have one mutex per region.

---

### Post by night_fox on 2010-02-15
We're thinking along the same lines. I'd like the thing to behave from the outside a bit like a mutex, so if the particular zone in the array is unavailable, then the locking function will block. Actually I don't know precisely what the threads will do with the content in terms of reading and writing to it at the same time, but they are independant. I wouldn't like to assume anything about what happens to the content. That way, we end up with an entirely abstract set of functions. Who knows? it might end up in glib!

```
struct ThreadSafeArrayZone {
    bool locked;
    unsigned int start;
    unsigned int length;
};

struct ThreadSafeArray
{
    char* contents;
    unsigned int length;
    
    GList* zones;
    
    /* details */
}

char* thread_safe_array_zone_lock (unsigned int index, unsigned int *zone_len, ThreadSafeArrayZone** zone);
void thread_safe_array_zone_unlock (ThreadSafeArrayZone* zone);
```

So when you create a ThreadSafeArray struct using some function with new in its name, it has one big zone in it.

 The lock function finds which zones are covered by the area given by index and zone_len, locks them, merges them, and then splits them into 1,2, or 3 zones (depending on the boundaries) , and locks one of them. It returns a pointer to the beginning of the requested zone, and replaces zone_len with the length of the zone which is only different if the zone is at the end of the array. It backpasses a pointer to a ThreadSafeArrayZone which is used to unlock the zone.

That way, the size of the zones are arbitrary, and minimised. Implementing this in a thread safe way is not easy but I think I nearly worked it out using GCond.

```
char* thread_safe_array_zone_lock (unsigned int index, unsigned int *zone_len, ThreadSafeArrayZone** zone) {
// pseudocode

    lock mutex corresponding to whole array
    do {
        determine whether the area is available
        g_cond_wait(condition);
    } while (some zones in the required area are locked);

    merge/split zones
    set zones locked to TRUE
    unlock mutex corresponding to whole array
}


void thread_safe_array_zone_unlock (ThreadSafeArrayZone* zone) {
// pseudocode

    unlock relevant condition

}
```


There would have to be several conditions. What would they have to be associated with? Only one zone is unlocked at a time, only one condition can be waited for, so this would have to represent multiple zones.

---

### Post by night_fox on 2010-02-15
[http://www.gtk.org/api/2.6/glib/glib-Threads.html#GCond](http://www.gtk.org/api/2.6/glib/glib-Threads.html#GCond)

Looking at this, if I have a system of GConds (one for each thread stuck in the zone locking function), then do I need a different mutex for each one, or can I use the one associated with the whole array?

---

### Post by MadCow108 on 2010-02-15
when your threads only modify a single char in each operation and the array size cannot grow you could theoretically write a lock free concurrent array using atomic compare and swap operations (which should be available on all modern hardware nowadays)

but if you are not very experienced in multithreaded programming, don't try it.
Lock-free datastructures are very hard to get right.


How does your array get accessed?
Of how many threads are we talking about? How well does it have to scale to higher thread numbers?

Are there many reads and few writes and not thousands of threads writing at the same time?
then probably a simple global read/write lock is enough and you don't have to bother about zoning it (which again is easy to do wrong if you're new to this kind programming).

---

### Post by night_fox on 2010-02-15
Wow, a lock free data structure really would be bleeding edge! but unfortunately I would need to access more than individual chars.

Actually, a global read write lock ...... WOULD BE ENOUGH!!!!!!
Damn my overcomplicating things! Thankyou MadCow108.

This zone thing is however, very cool so i'll probably continue.

---

### Post by night_fox on 2010-02-15
So if each thread that was waiting had a list of required zones, indexes, lengths and conditions, which could be manipulated as zones got merged and split, then the unlocking function could know what condition to give the signal on.

For efficiency, each zone could have a list of the above lists that were relevant to it. That way, the merges and splits could be done without losing information and without having to search the list of zones!

p.s.


pwnt.
:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:



p.p.s.

Whats the best way of testing? I'm thinking starting with an array of zeros, then having a giant thread pool, where the threads instructions are to complement a random area of the array, wait for a second, and complement it again. Then see if any bits are 1.

EDIT: complement it, store it, wait, then complement it again. So if the array gives two threads access at the same time, the test will fail.

---

