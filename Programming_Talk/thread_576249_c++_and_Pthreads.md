---
title: "c++ and Pthreads"
date: 2007-10-15
forum: Programming Talk
---

### Post by Rij on 2007-10-15
Is using pthreads with C++ a bad idea?

---

### Post by KaeseEs on 2007-10-15
There's nothing wrong with using PThreads with C++.  In fact, it is probably the best threading implementation available for C++, being efficient, relatively easy to use, full-featured, and cross-platform.

---

### Post by Rij on 2007-10-15
Thanks.

---

### Post by dwhitney67 on 2007-10-15
I second KaeseEs opinion, however before you go polluting your code with pthread implementations, consider using the [Boost libraries]("http://www.boost.org/") for your needs.

If you still insist on writing your own pthread implementations, then I suggest that you write wrapper-classes around the necessary pthread components you need so that the draconian interface is "hidden" from the application code.

---

