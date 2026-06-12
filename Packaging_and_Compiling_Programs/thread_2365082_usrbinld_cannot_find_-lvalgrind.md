---
title: "/usr/bin/ld: cannot find -lvalgrind"
date: 2017-07-02
forum: Packaging and Compiling Programs
---

### Post by Adrian_Oneasca on 2017-07-02
Hello there, I am trying to compile a application using GCC5, and I am getting the following error message from make:
```

/usr/bin/ld: cannot find -lvalgrind
collect2: error: ld returned 1 exit status

```
I have already installed "valgrind" via:
```
sudo apt-get install valgrind
```
But it doesn't seem to do the trick.

---

### Post by spjackson on 2017-07-04
The valgrind package does not include a library libvalgrind.a or libvalgrind.so. What is it that you are trying to build that requires such a library?

---

