---
title: "WriteFile() function in linux"
date: 2007-08-15
forum: Programming Talk
---

### Post by nonoykevin on 2007-08-15
Hey there!

I had a project that needs porting process. From win32 to C++ in linux platform. my problem is i haven't find yet the equivalent WriteFile() function in linux. can somebody gave me hint on this?

Thanks!

---

### Post by slavik on 2007-08-15
you can open a file as a stream in C++ ... and then just operator>>() into it ...

---

### Post by nonoykevin on 2007-08-15
ok thanks a lot!

another thing, is there also an equivalent ResetEvent() function in linux?

---

### Post by PaulFr on 2007-08-16
Just my 0.02 of your local currency: :-)

The following suggestions are for C (not C++):

1. The answer depends on your specific requirements: If performance is critical, you may want to take a look at **[http://www.kegel.com/c10k.html](http://www.kegel.com/c10k.html)** for a description of various ways to handle events and I/O on Unix with a focus on scaling to a high number of connections. See the I/O frameworks sections for some libraries that can help keep your code portable across the various flavors of Unix.

2. Two Ubuntu packaged libraries that provide you event notifications are **libevent-dev** and **liboop-dev** referenced in I/O frameworks of above page.

3. One of the most valuable books for Unix programming (system and network) is Rich Stevens' books (**[http://www.kohala.com/start](http://www.kohala.com/start)**). It may be worth it for you to review that first.

Of course, for C++, the iostreams library is always available for writing to files. Good luck !

---

