---
title: "C++ Undefined reference error"
date: 2015-05-12
forum: Programming Talk
---

### Post by alrod on 2015-05-12
I know that there are a lot of questions about undefined reference out there, but I couldn't find any that is like my case, probably because I am new to C++.

I am developing a little project structured like this:
- uses SNAP library (... /usr/include/Snap-2.3/snap-core/Snap.o -I../include -I/usr/include/Snap-2.3/snap-core -I/usr/include/Snap-2.3/glib-core)
- uses Nauty & Traces library (../nauty25r9/nauty.a -I../nauty25r9/)
- Project own files are:
  > *main.cpp* (includes *GraphData.hpp*)
  > *GraphData.hpp*
  > *GraphData.cpp* (includes *GraphData.hpp*)

So, in *GraphData* I have a namespace **GD** in which I defined a class *GraphList* which is created with a custom type *T* (*template <typename T>*).

In *main.cpp* I call ```
GD::GraphList<int>* kSubgraphs = new GD::GraphList<int>;
```, which causes the error: ```
main.cpp:(.text+0x41): undefined reference to `GD::GraphList<int>::GraphList()'
```, yet in *main.cpp* I call another function defined in *GraphData*, also in namespace **GD**, and it doesn't cause errors.

I am compiling the whole project directly in terminal, without Make or CMake and I don't intend to use any of them, here is the whole commmand:
```
g++ -o ../Kavosh main.cpp GraphData.cpp /usr/include/Snap-2.3/snap-core/Snap.o ../nauty25r9/nauty.a -std=gnu++11 -I../include -I/usr/include/Snap-2.3/snap-core -I/usr/include/Snap-2.3/glib-core -I../nauty25r9/
```

As far as I know, the error I pointed, is a Linker Error, so I though that I may need an object to link to the file, so I compiled *GraphData.cpp* to produce an object *GraphData.o* and then compiled *main.cpp* adding the object, but it didn't work, it produced a lot of strange errors about reallocations having an index of invalid symbol.

What am I doing wrong? Probably it may be a dumb mistake, because I only know the basics of C/C++.

Thanks for your time, Rodrigo.

---

### Post by alrod on 2015-05-12
I already found the error, I can't use templates in .cpp files. So I converted GraphData.cpp to GraphData.tpp and included it at the end of GraphData.hpp.

---

