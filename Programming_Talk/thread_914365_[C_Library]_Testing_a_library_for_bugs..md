---
title: "[C Library] Testing a library for bugs."
date: 2008-09-08
forum: Programming Talk
---

### Post by British0zzy on 2008-09-08
So I've only been programming for a couple months and I decided to do something interesting with my new found knowledge of C.
I had an idea for storing values, not in 8 bit chunks, but in 3 or 5 or 14 bit chunks. I know one can do this using bitfields, but bitfields are not very dynamic. So I've gone and made a C library for creating arrays with there elements stored in n-bit chunks.
I know it isn't very practical, but I thought it was cool. It seems to be working now, but how can I be sure?
I would like some tips on how to vigorously test this library for bugs.
The source code can be found here: [http://trac.assembla.com/bitfieldarray](http://trac.assembla.com/bitfieldarray)

There are only four functions so far, but I will be adding a function for setting individual elements at an index and some others.

If you have any questions just ask in this thread. I know I've over-commented the code, but it seemed extremely confusing without it.

Comments and suggestions are greatly appreciated.

Thanks!

(btw, I don't know how to check this, but can anyone edit the repository without logging in? Can you guys even view it? Thanks for the feedback)

---

### Post by dribeas on 2008-09-09
For testing you should take general cases, then corner cases, testing the limits: BFL for a general valid size (example: 5,11,17), not allowed sizes (8,16,24,27,32), corner case sizes: 1,7,9,15,17,23. Note that the selection are the limits (smaller and larger for one byte storage, two byte storage... since your code won't allow multiples of 8, those are corner cases).

Anyway, I tried to read through your lib and there are a couple of things that are not clear to me. First, why are you limiting to 24 bit blocks? wouldn't it be more useful having a 32/64 limit? Why are multiples of 8 bits not allowed?

I believe (just from reading) that if you require a size that is multiple of 8 (for the total set of data) you will be requesting one more char, not that it is important anyway.

To keep coherence among the two init functions, if you fail to allocate the internal data buffer you should free the structure, that way the user does not need to check whether BFL_E_MEM was returned while allocating one or the other.

You could reduce the number of reallocs if you allow your buffer to be of 'not precisely the size required' which you are doing anyway when the user inits the structure with a size.

I would adhere to the same error reporting strategy in all cases. If most functions return the error code, then all of them should, get_element could receive the data holder as a parameter and return the error code, which is more natural for the user:

```

//...
unsigned long int x;
if ( BFL_get_element( bf, 5, &x ) != BFL_SUCCESS ) {
   // ... process error
};

// better than:
int error;
unsigned long int x = BFL_get_element( bf, 5, &error );
if ( error != BFL_SUCCESS ) {
   // ... process error
}

```

After all, in most cases the user will have a variable to hold the result, but does not need to have a variable for the error.

I did not try to validate your bitwise operations, I assume you have tested them and they work, else the testing should help there.

---

### Post by British0zzy on 2008-09-09
Thanks for the tips. I have changed the error reporting in the get_element function. And I have fixed the problem so that the arrays can now have 8 or 16 or 24 bit blocks.

The reason I limited the function to blocks of 24 is that I got an error in a bit operation on numbers bigger than 24. This is probably because I am doing bit operations on an 32bit integer where I need an 64bit integer.

I am thinking about separating the library into 3 or 4 versions. One would allow degrees of freedom less than or equal to 8. Another would allow degrees of freedom less than or equal to 16 and another would allow degrees of freedom less than or equal to 32 etc..
I could do this in the preprocessing stage but it may end up looking ugly.
Perhaps I should just use 64bit integers to store the values (right now I'm using chars or 8bit).

I would also like to add some buffering to the library in the future.
Let's say I end up using 64bit integers to store the values.
When filling the array, how easy would it be to realloc the array to a bigger size on a separate thread while filling already allocated parts of the array?
Do you have any tips on making the library "thread safe"?

---

### Post by dribeas on 2008-09-09
> **British0zzy said:**
> The reason I limited the function to blocks of 24 is that I got an error in a bit operation on numbers bigger than 24.

You should probably look into this as there is no reason not to use the whole 32 bits. Using bigger integers with the same algorithm will just push the limit up, but not solve the real problem.

> **British0zzy said:**
> I am thinking about separating the library into 3 or 4 versions.

Get the one version working, I don't believe that having more versions will be of any help.

> **British0zzy said:**
> I would also like to add some buffering to the library in the future. [...]
When filling the array, how easy would it be to realloc the array to a bigger size on a separate thread while filling already allocated parts of the array?
Do you have any tips on making the library "thread safe"?

Some buffering will probably speed up your operations. The most expensive part are os calls to realloc (you should profile, but that is my feeling) and reducing the number of realloc will enhance performance.

On thread safety... you should really know what you want to achieve and how you can do it. As an example, a call to realloc can move the memory chunk to a completely different position. While the OS takes care of copying data and all, if another thread was reading/writing at the same time you'll run into trouble. So you must guarantee that there is a critical region on the data. Now, you could go for a writer-multiple readers solution that will allow multiple synchronous reads (or even push it into writes that don't realloc) while only one thread doing writes (the realloc kind).

Depending on how fine you want the control on the objects and the threads you may decide to get outside synchronization (solve the data structure without thread safety and then wrap all calls in a thread safe layer) or intrusively modify the data structure.

The advantage of adding thread safety intrusively is that you have a greater control on the operations (mutex/semaphores) but at the same time you will not be able to use the lib in a single thread environment without the overhead.

I, myself, would go into a single-threaded lib, and once that is up and running, completely tested, I would analyze where and how to add thread safety, knowing that it might requite a major rewrite. But the first version, even if you rewrite it completely, won't be lost time, but experience gained.

---

### Post by British0zzy on 2008-09-10
I've uploaded an updated version of the library. It includes two user defined macros called BFL_SAFE and BFL_SIZE. BFL_SAFE turns on or off error checks, and BFL_SIZE sets the maximum degrees of freedom. The degrees of freedom now can be any number between 0 and 64 (not including either).
Is this the best way to approach this or is there a friendlier way of including these functionalities?

Concerning multithreading add_element...
Would it make sense to read the needed data and store it (at most two numbers from data); Change the stored data to its new values; While doing this call realloc and get the new pointer for the memory; And then when realloc finishes overwrite the realloced data with the stored data.

And can you get an example of a library made threadsafe (or how to make a library threadsafe). I'd just like to have a reference for the problems I should avoid.

---

### Post by dribeas on 2008-09-10
> **British0zzy said:**
> Concerning multithreading add_element...
Would it make sense to read the needed data and store it (at most two numbers from data); Change the stored data to its new values; While doing this call realloc and get the new pointer for the memory; And then when realloc finishes overwrite the realloced data with the stored data.

What do you want to achieve with this? The cost of communication between threads outweights the cost of the parallelized operation.

> **British0zzy said:**
> And can you get an example of a library made threadsafe (or how to make a library threadsafe). I'd just like to have a reference for the problems I should avoid.

It's been long since I've done serious C programming. Nowadays I am mostly doing C++ with ACE / Boost, so I cannot give you code. A thin wrapper (pseudo code) could go like:

```

struct ThreadSafeBFS
{
   BFS bfs_;
   mutex mutex_; // pthread_mutex or something in the line
};

// Init will use pthreads to init the synchronization data (mutex_), same with the rest of operations, as an example:

int TSBFS_get_element( ThreadSafeBFS * bfs, int index, unsigned int* element )
{
   // acquire mutex, check pthread docs
   int error = BFS_get_element( bfs->bfs_, index, element ); 
   // release mutex
   return error;
}

```

You'll need to dig into pthread_mutex docs for initialization, acquisition and release of the synchronization mechanism. This will be with external synchronization, which has the lowest granularity but again is what I would aim at. At least before profiling.

---

