---
title: "Multi-language debugging"
date: 2008-05-05
forum: Programming Talk
---

### Post by blowguy on 2008-05-05
Hi all,

I wonder if there is a tool which would help me with easily debugging large projects which consists of both - Perl and C++ code.

---

### Post by dwhitney67 on 2008-05-05
I doubt you will find one.  Did the developer(s) create unit tests for each of the components that were ultimately integrated together to form the large project?  A good project will mandate that this be done; on others where short-cuts are sought, then this is usually not done.  Ask yourself which approach is better!

For debugging C++ code, ensure that the "-g" option is passed to the compiler, and that preferably any optimization flags are not used.  Then to debug, use the "gdb", or better yet, the front-end application to gdb called "ddd".
```

$ g++ -g MyApp.cpp -o MyApp
$ ddd MyApp &

```

To get ddd:
```

$ sudo apt-get install ddd

```

---

