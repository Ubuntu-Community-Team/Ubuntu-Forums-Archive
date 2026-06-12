---
title: "error: expected ‘;’ before ‘(’ token"
date: 2012-06-11
forum: Programming Talk
---

### Post by hasanalikhattak on 2012-06-11
i m getting error
> error: expected ‘;’ before ‘(’ token
on line 121 of this code
```
u_int32_t* decode(string[8]=NULL, string[2]=NULL);
```
the code is part of this header library
[http://pastebin.com/NS8V0ByK]("http://pastebin.com/NS8V0ByK")
and the function definition is in this code at line 217
[http://pastebin.com/M9fuppa1]("http://pastebin.com/M9fuppa1")

it is kind of urgent so kindly any of you can help i will be thankful.
i am compiling on Ubuntu 12.04 32bit with gcc (Ubuntu/Linaro 4.5.3-9ubuntu1) 4.5.4

---

### Post by Majorix on 2012-06-11
Post the whole code maybe? I fail to see the error.

---

### Post by hasanalikhattak on 2012-06-11
i have posted the whole code of the header on the paste bin
[http://pastebin.com/NS8V0ByK]("http://pastebin.com/NS8V0ByK") 
and also the code for the function definition is in this code at line 217 [http://pastebin.com/M9fuppa1]("http://pastebin.com/M9fuppa1")
you can also see the whole project over [project site for Google Code]("http://code.google.com/p/ns2-neoclassic/source/detail?r=4")

---

### Post by kingtaurus on 2012-06-11
According to the compilers (clang++ and g++) that is a valid function definition. I'm assuming string is a std::string.

```

 g++ -v
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 

```

```

clang++ -v
Ubuntu clang version 3.0-6ubuntu3 (tags/RELEASE_30/final) (based on LLVM 3.0)
Target: x86_64-pc-linux-gnu
Thread model: posix

```


```

//Filename: test.cc
//clang++ test.cc -c
//g++ test.cc -c
#include <string>
#include <stdint.h>
#include <sys/types.h>

u_int32_t* decode(std::string a[8]=NULL, std::string b[2]=NULL);

```

> **hasanalikhattak said:**
> i m getting error

on line 121 of this code
```
u_int32_t* decode(string[8]=NULL, string[2]=NULL);
```
the code is part of this header library
[http://pastebin.com/NS8V0ByK]("http://pastebin.com/NS8V0ByK")
and the function definition is in this code at line 217
[http://pastebin.com/M9fuppa1]("http://pastebin.com/M9fuppa1")

it is kind of urgent so kindly any of you can help i will be thankful.
i am compiling on Ubuntu 12.04 32bit with gcc (Ubuntu/Linaro 4.5.3-9ubuntu1) 4.5.4

---

### Post by trent.josephsen on 2012-06-11
You're probably missing a semicolon on the line before that one.

That said, when you have errors, do post a compilable example and not just a line or two. Compilers can usually only guess at where you made a mistake, and they're often wrong (because they can only look at what you *wrote* and not what you *meant*).

*Edit: that seems not to be your problem after all, at least if the code you pasted is actually the code you compiled. Sorry.*

---

### Post by hasanalikhattak on 2012-06-11
the whole code is a huge project and very lengthy code. that is why i have posted on pastebin and also shared the project on google code.
> **trent.josephsen said:**
> You're probably missing a semicolon on the line before that one.

That said, when you have errors, do post a compilable example and not just a line or two. Compilers can usually only guess at where you made a mistake, and they're often wrong (because they can only look at what you *wrote* and not what you *meant*).

i am not very regular on forums so i don't know the requirements and such things. i hope you guys can be tolerable on that aspect :)

---

### Post by jim_24601 on 2012-06-11
If I saw that error on that line of code, the first thing I would do would be to check that the definition of "u_int32_t" is visible to the compiler at that point. It looks to me as if the compiler is trying to interpret it as a variable or function name and getting confused.

---

### Post by dwhitney67 on 2012-06-11
> **hasanalikhattak said:**
> i m getting error

on line 121 of this code
```
u_int32_t* decode(string[8]=NULL, string[2]=NULL);
```
...

it is kind of urgent so kindly any of you can help i will be thankful.
i am compiling on Ubuntu 12.04 32bit with gcc (Ubuntu/Linaro 4.5.3-9ubuntu1) 4.5.4

Your header file is missing an include statement for the <string> header file.  In addition, the function prototype you have above fails to note that string is declared within the std namespace.

Change your prototype to be:
```

#include <string>
...
u_int32_t* decode(**std::string**[8]=NULL, **std::string**[2]=NULL);

```
Make a similar adjustment in the cpp source file.

P.S.  I agree with Jim_24601; it would also appear that you are missing a typedef for u_int32_t.

---

