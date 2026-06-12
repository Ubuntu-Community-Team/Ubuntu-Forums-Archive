---
title: "Is STL sort() Function Thread Safe?"
date: 2012-05-22
forum: Programming Talk
---

### Post by DBQ on 2012-05-22
Hi everybody.

Does anybody know if the sort()thread safe?

By this I mean: can I safely call instances of this function on distinct containers from different threads?

Here is my g++ info:

```

Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)

```

Thank you very much!

EDIT: The reason I ask this question is because I am debugging a multi-threaded program. So far, the sort() function can be a possible culprit

---

### Post by CptPicard on 2012-05-22
As long as the containers really are distinct, then you should be fine. There is no reason why different calls to sort would share some background state that is separate from the container.

That said, make sure your assumption holds and you're not dealing with some container implementation that shares storage behind the scenes.

---

### Post by kingtaurus on 2012-05-24
> **CptPicard said:**
> As long as the containers really are distinct, then you should be fine. There is no reason why different calls to sort would share some background state that is separate from the container.

That said, make sure your assumption holds and you're not dealing with some container implementation that shares storage behind the scenes.

STL sort is **not thread safe** (unless you lock the container). In case you are wondering why it is not thread safe:
(1) if iterators become invalidated (std::vector<>, std::deque<>, and other containers can have function calls invalidate the iterator). For example, push_back can invalidate iterators (it can causes the location of data associated with the std::vector change).
(2) if you can guarantee that other threads will not modify the contents of std::vector, std::deque while sort is being performed then it might be thread safe.

Cheers,

---

### Post by CptPicard on 2012-05-24
> **kingtaurus said:**
> STL sort is **not thread safe** (unless you lock the container). In case you are wondering why it is not thread safe:

Yes, but I read the question as the containers really being distinct for each thread, so there really shouldn't be any state external to the container (let's include iterators in container state) that would make sort non-thread-safe.

---

### Post by kingtaurus on 2012-05-24
> **CptPicard said:**
> Yes, but I read the question as the containers really being distinct for each thread, so there really shouldn't be any state external to the container (let's include iterators in container state) that would make sort non-thread-safe.
The original post made no promise of anything more than threads would call std::sort on different containers (I felt that situations like the following could occur: thread 'a' might call std::sort on container_a and the push_back the first element onto container b; whereas thread 'b' might call std::sort on container_b);

I agree that **if** you can make guarantees about the state of container (including iterators); and that no other thread will modify the data stored within it, it should be thread safe.

However I felt that I should clarify the issue relating to threads accessing the container but not modifying. Any values 'handled' by these threads should be considered suspect (between the initial call to std::sort(...) and its completion.

DBQ: Consider adding a mutex before any interaction with a container by any thread (see boost::thread);

---

