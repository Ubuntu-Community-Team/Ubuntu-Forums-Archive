---
title: "troubles with Boost-lib for Python"
date: 2007-03-10
forum: Programming Talk
---

### Post by rudyryk on 2007-03-10
Hi!

I've got a problem with making 'bjam' work even with tutorial examples.

```

$ cd /usr/share/doc/libboost-doc/examples/libs/python/example/tutorial
$ bjam -sTOOLS=gcc

Failed to find the project root for directory '.'.
Did not find a project-root.jam file there or in any of its parent directories.
Please consult the documentation at 'http://www.boost.org'.

```

I've just installed such packages:

boost-build
libboost-dev
libboost-doc
libboost-python-dev
libboost-python1.33.1


Could you help me with further steps?

---

### Post by Game_Ender on 2007-03-12
I think that might be a problem with the bjam in that version of Boost.  You should be able to compile the examples by hand fairly easily.  You just need to link in the libpython, the Boost.Python library, then include the directories for Python.h and the Boost.Python header files.

It would go something like:
```

g++ example.cpp -o example -I/usr/include -I/usr/include/python2.5 -L/usr/lib -lpython2.4 -lboost_pyhon 

```

---

