---
title: "[C++] std::vector - traverse by index or by iterator?"
date: 2010-03-11
forum: Programming Talk
---

### Post by kahumba on 2010-03-11
Hi,
which approach should I use if I just need to traverse the whole vector? Are there any performance implications or so..?

---

### Post by schauerlich on 2010-03-11
Correct me if I'm wrong, but accessing by index should be quicker - it's just pointer arithmetic with some range checking. However, iterators have some overhead as they have to be created, and work out the "magic" of incrementing. I'd imagine for vectors the overhead is pretty negligible, though, especially compared to other more complex containers. You also have the flexibility to switch the vector out for some other data structure at a later time and leave much of your code the same.

---

### Post by krazyd on 2010-03-11
I'm not sure of the performance differences, but i'm sure that any speed disadvantages of iterators would be minimal.

The iterator is preferred for genericity. See here for some good explanations:
[http://stackoverflow.com/questions/131241/why-use-iterators-instead-of-array-indices](http://stackoverflow.com/questions/131241/why-use-iterators-instead-of-array-indices)

also:
[http://stackoverflow.com/questions/178934/iterators-why-use-them](http://stackoverflow.com/questions/178934/iterators-why-use-them)

---

### Post by Simon17 on 2010-03-11
The performance differences are so small, that you shouldn't worry about it.

And normally, indexing an std::vector doesn't do range checking. If you want that, you need at().

---

### Post by kahumba on 2010-03-11
Thanks all,
as I understand it, using at() would be slightly faster but no one would notice it anyway.

---

### Post by MadCow108 on 2010-03-12
at will be slightly slower than [] as it does range checking. But this is negligible.

Iterators will be near just as fast as indexing as the iterator of a vector is just an encapsulated pointer.
An optimizing compiler can reduce this back to a raw pointer making speed (almost) identical.

---

### Post by pbrane on 2010-03-12
For a discussion of time for std::vector access see:
[http://www.cppreference.com/wiki/]("http://www.cppreference.com/wiki/")
There you can look up the *[]* operators or the *at()* function or iterators. The discriptions usually tell you about what time they run in. *[]* runs in constant time, for instance.

---

### Post by schauerlich on 2010-03-12
> **pbrane said:**
> For a discussion of time for std::vector access see:
[http://www.cppreference.com/wiki/]("http://www.cppreference.com/wiki/")
There you can look up the *[]* operators or the *at()* function or iterators. The discriptions usually tell you about what time they run in. *[]* runs in constant time, for instance.

Well, they're both constant time - that doesn't mean one isn't a faster constant time than the other.

---

### Post by dribeas on 2010-03-12
First of all, the difference does not matter at all, and more over before actually meassuring whether you need to optimize or not.

Iterators depend on the implementation, in particular they can range from a raw pointer (.begin() can give a raw pointer to the first element, .end() a raw pointer one beyond the end of the last element) to quite complex things (by default VS has checked iterators that verify that the vector has not undertaken an operation that invalidates the iterator.

The difference between a fast iterator and indirect access through the position is negligible (with the fast iterator being marginally faster). In most cases the cost of accessing the data element (even if it is in a cache line already) will be much higher than the difference.

You should settle for the most readable and maintainable implementation (iterators). Depending on the STL library you use you might even get the advantage of a slow implementation!!! That means that in a debug build it will flag errors.

---

### Post by krazyd on 2010-03-13
> **kahumba said:**
> Thanks all,
as I understand it, using at() would be slightly faster but no one would notice it anyway.

> Please remember the rules of Optimization Club:

   1. The first rule of Optimization Club is, you do not Optimize.
   2. The second rule of Optimization Club is, you do not Optimize without measuring.
   3. If your app is running faster than the underlying transport protocol, the optimization is over.
   4. One factor at a time.
   5. No marketroids, no marketroid schedules.
   6. Testing will go on as long as it has to.
   7. If this is your first night at Optimization Club, you have to write a test case.

;)

[Source](http://stackoverflow.com/questions/177122/how-can-i-speed-up-my-perl-program)

---

