---
title: "[C++] Dynamically Linked Executable Larger than Static"
date: 2010-05-08
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-05-08
I have used the tutorials from the following pages:
[http://ehuss.com/shared/](http://ehuss.com/shared/)
[http://www.network-theory.co.uk/docs/gccintro/gccintro_25.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_25.html)
[http://www.adp-gmbh.ch/cpp/gcc/create_lib.html](http://www.adp-gmbh.ch/cpp/gcc/create_lib.html)

So I create my shared and static libraries in the source directory:
```
g++ -fPIC -c libtesting.cpp
g++ -shared libtesting.o -o libtesting.so
rm libtesting.o
g++ -c libtesting.cpp
ar rcs libtesting.a libtesting.o
```

Then I compile an executable with a dynamic link to libtesting.so:
```
g++ test.cpp /home/user/C++/test/libtesting.so -o dyntest
```

I also compile an executable with the static library:
```
g++ test.cpp /home/user/C++/test/libtesting.a -o statictest
```

Maybe I'm not understanding something, but I thought that using a dynamically linked library was supposed to make the executable smaller.  dyntest is 13.4kb and statictest is 9.4kb.  There must be something that I don't understand.  Would someone like to enlighten me as to why the statically linked executable is larger?

---

### Post by dodle on 2010-05-09
I was doing something wrong, I don't know what, but now my statically linked file is 9.4kb and the dynamically linked is 9.3kb :).

---

