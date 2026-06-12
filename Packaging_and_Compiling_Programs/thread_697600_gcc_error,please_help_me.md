---
title: "gcc error,please help me"
date: 2008-02-15
forum: Packaging and Compiling Programs
---

### Post by naffi on 2008-02-15
my code is :

#include<stdio.h>
int main(void)
{
        printf("hello world");
        return 1;
}


in terminal i get this error:

naffi@naffi-desktop:~$ gcc -c hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function &#8216;main&#8217;:
hello.c:4: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

this is my gcc:

naffi@naffi-desktop:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

anyone please help me.

---

### Post by vambo on 2008-02-15
Have you installed build-essential?

```
sudo apt-get install build-essential
```

---

### Post by piotroxp on 2008-02-15
Maybe you wish to compile it in c++ ?

then just use g++, if you haven't got it installed type:
sudo aptitude install g++

then just compile it like:
g++ [your_file].cpp -o [your_output].o

---

### Post by hod139 on 2008-02-16
> **piotroxp said:**
> Maybe you wish to compile it in c++ ?

It is C code, why would he want to compile it in C++?

```

then just use g++, if you haven't got it installed type:
sudo aptitude install g++

```
This is wrong.  To install g++ (and gcc) do (as mentioned by vambo):
```

sudo apt-get install build-essential

```

---

### Post by yetkin on 2008-02-16
not for that application but for specific differences between c89 c99 can create problems with a c compiler for example:

int main()
{
  struct aStruct a;
 a.print();
int b;                          /* ---->>> that line gives an error for standard  compilers but g++ or any c++     ---------------------------------->>> compiler works fine with that because cpp supports it. also for some ----------------------------------- >>> macros like _COMPLEX , _IMAGINARY  ... it can be better using a cpp ----------------------------------->>>compiler sometimes
                                 */
....
....
b=5;
....
return 0;
}

---

