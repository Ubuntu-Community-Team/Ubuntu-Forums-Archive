---
title: "Zthread vs Boost"
date: 2008-04-21
forum: Programming Talk
---

### Post by jmartrican on 2008-04-21
So I learned ZThreads not too long ago and I thinks its awesome.  The documentation was spot on and the objects are very intuitive (IMHO).  I'm learning Boost threads now and the first problem i see is with the documentation.... why don't they just have a list of all the functions with links to the code... or maybe they do and I have not found it.

But anyways I have a project at work coming up that has threading and since I'm hearing all this talk of Boost being a prelude to any future threading standard in C++ (and ZThreads looks like it is not supported anymore) I figure I better take a serious look into using Boost over ZThreads.

Does anyone have any insight about the pros and cons of these two wonderful libraries?

---

### Post by Zdravko on 2008-04-22
I've heard Bjarne Stroustrup recommends boost::thread until C++0x is officially out.

---

### Post by dwhitney67 on 2008-04-22
I've used the Boost libraries to write multi-threaded applications, and found the libraries easy to use.  I agree with you that the documentation is not the best, unless you know exactly what you want to find.  But what I think is great about the documentation is that in many (if not all) cases, an example is provided showing the proper usage of the library discussed. 

The Boost documentation (for ver 1.35.0) is located at [http://www.boost.org/doc/libs/1_35_0](http://www.boost.org/doc/libs/1_35_0).  For the specific documentation concerning threads and supporting constructs (e.g. mutexes), the documentation is located at [http://www.boost.org/doc/libs/1_35_0/doc/html/thread.html](http://www.boost.org/doc/libs/1_35_0/doc/html/thread.html).

I would not think of Boost as a standard that will replace pthreads.  Think of it as a "wheel" that does not have to be invented again and again each time you start a new project.  The Boost libraries can also be used under Windows.

Concerning zthreads, I have personally never heard of this package/library.

---

