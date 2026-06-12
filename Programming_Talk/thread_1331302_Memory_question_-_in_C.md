---
title: "Memory question - in C"
date: 2009-11-19
forum: Programming Talk
---

### Post by Gorgamel on 2009-11-19
In a project to write my own malloc, I have looked at others code.
In some I have seen that they are fetching an pointer and adding the page size to that (the size you get from getpagesize()).

What does this do?
Will this be pointing to the next memory block?

---

### Post by MindSz on 2009-11-19
It points to the next element in the array.

So if you have an array of elements of size m, then the nth element will be addressed as base_ptr+(n*m)

---

### Post by Tony Flury on 2009-11-19
> **MindSz said:**
> It points to the next element in the array.

So if you have an array of elements of size m, then the nth element will be addressed as base_ptr+(n*m)

I think what I am bout to say is correct : 

If your pointer is of the right type then base_ptr+n will work, as the compiler works out the pointer arithemtic - doing n*m will get the wrong answer.

Doing n*m, should get the right answer in most implementations if your pointer is "void *", but you are then making assumptions that your elements are stored contigously with no padding or alignment issues, and I am not sure that is guaranteed by the standard.

---

### Post by Habbit on 2009-11-19
> **Tony Flury said:**
> Doing n*m, should get the right answer in most implementations if your pointer is "void *" (...)
Pointer arithmetic on a void* is forbidden, because void names no type. If you want to add n _bytes_, you need to use a char*.

---

### Post by meson2439 on 2009-11-20
I usually just avoid pointer arithmetic. It looks neat but conceptually doesn't seem very stable, especially for codes that took hours to run. There are many things that can go wrong during that time. Use malloc and realloc instead to change array size. But since the assignment asked you to write your own malloc, I guess you have no choice. In practice, avoid them especially for very large arrays ( >100kB is normal for most number crunching ) but for small arrays, they are quite safe.

---

### Post by Arndt on 2009-11-20
> **meson2439 said:**
> I usually just avoid pointer arithmetic. It looks neat but conceptually doesn't seem very stable, especially for codes that took hours to run. There are many things that can go wrong during that time. Use malloc and realloc instead to change array size. But since the assignment asked you to write your own malloc, I guess you have no choice. In practice, avoid them especially for very large arrays ( >100kB is normal for most number crunching ) but for small arrays, they are quite safe.

How do you relate execution time to whether pointer arithmetic is safe? And what is it about pointer arithmetic that isn't safe?

---

### Post by meson2439 on 2009-11-20
> How do you relate execution time to whether pointer arithmetic is safe? And what is it about pointer arithmetic that isn't safe?

Let's consider that we have to access the pointers a few million times and along the way, we create new pointers for our various results. Let's consider our initial data use 200MB of memory from our PC 1GB. Don't you think that in such cases the chances of memory leak increases with longer running time since you happen to allocate and reallocate data more often than we could free. 

Although, I have to admit that those fears are mostly paranoia because with good programming practice it should not be a problem. However, trudging through the code in search of errors is very hard work. Even more dangerous, if you didn't notice that your variables had been modified in the first place (large numbers are common in the code). Thus a few bad experience are enough to make me avoid them if possible. I'm even suspicious of arrays, thus  I tend to design my code to use more scalar values. 

Sorry for the unrelated rant.

---

### Post by ApEkV2 on 2009-11-21
> **meson2439 said:**
> 
Sorry for the unrelated rant.

I can't believe it's not butter.

---

