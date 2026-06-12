---
title: "C++ linking"
date: 2009-05-19
forum: Programming Talk
---

### Post by Alcareru on 2009-05-19
Hi once again!

I'm experiencing some difficulties trying to link some libraries to my application. I compile my app with g++ and on linking time it is all happy and finds the libraries I want to include, but when I try to run the application it says it can't find them. How is that possible?

If it matters the library is libmyodc3-3.51.27 that I compiled myself.
A simple line that compiles the application is:
g++ sql_interface.cpp -L/usr/local/odbc/lib/ -lmyodbc3 -o app.bin
and then running the app.bin results in:
error while loading shared libraries: libmyodbc3-3.51.27.so: cannot open shared object file: No such file or directory.

---

### Post by Arndt on 2009-05-19
> **Alcareru said:**
> Hi once again!

I'm experiencing some difficulties trying to link some libraries to my application. I compile my app with g++ and on linking time it is all happy and finds the libraries I want to include, but when I try to run the application it says it can't find them. How is that possible?

If it matters the library is libmyodc3-3.51.27 that I compiled myself.
A simple line that compiles the application is:
g++ sql_interface.cpp -L/usr/local/odbc/lib/ -lmyodbc3 -o app.bin
and then running the app.bin results in:
error while loading shared libraries: libmyodbc3-3.51.27.so: cannot open shared object file: No such file or directory.

When you say "then runnning", do you run it from the very shell where you linked it, or in another shell, or even on another computer? You need a value for the environment LD_LIBRARY_PATH in order to find the shared libraries at runtime. You can use the program 'ldd' to see whether the libraries will be found, before running the program.

---

### Post by Alcareru on 2009-05-19
> **Arndt said:**
> You need a value for the environment LD_LIBRARY_PATH in order to find the shared libraries at runtime.
Ah thanks. It seems I had misunderstood some parts of the linking process. :) Now it works.

---

