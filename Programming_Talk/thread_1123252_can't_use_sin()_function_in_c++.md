---
title: "can't use sin() function in c++"
date: 2009-04-12
forum: Programming Talk
---

### Post by darkromis on 2009-04-12
Hi, I'm new in using ubuntu and it seems that it's default compiler is not tolerant as the one that I've used in windows, I've realized that won't compile if iostream is used in the ancient manner "iostream.h" and also math.h does not have the sin() function, so I was wondering how could I use trigonometric function and also if you could recommend me a web page that has got information about c++\c programing in linux because as far as I know function widely used in windows like "getchar" or even libraries like conio are not include so I'm really pissed off :mad:

):P

thanks in advance

---

### Post by slavik on 2009-04-12
have you tried including the math library? you probably need to link against it as well.

google has all this info. ;)

---

### Post by Sinkingships7 on 2009-04-12
So just use #include <iostream>. As for math.h, follow slavik's advice. It must be linked separately.

---

### Post by Jiraiya_sama on 2009-04-12
"#include <cmath>" allows you to use sin(). Also, I presume "#include <cstdio>" pulls in getchar.

---

### Post by dribeas on 2009-04-12
> **darkromis said:**
> Hi, I'm new in using ubuntu and it seems that it's default compiler is not tolerant as the one that I've used in windows, I've realized that won't compile if iostream is used in the ancient manner "iostream.h" and also math.h does not have the sin() function

The correct includes for both of them are iostream and cmath if you are using C++. The include file math.h still exists as it is part of the C standard set of libraries, and can still be used in C++ is you wish (even if the proper include is cmath). If you include cmath, then all math functions will be defined inside the std namespace. If you include math.h they will be in the root namespace.

Unlike C, in C++ the math library does not need to be explicitly linked:

```

#include <iostream>
#include <cmath>
int main() {
   std::cout << std::sin( 1.0 ) << std::endl;
}
$ g++ -o test test.cpp
$ ./test
0.841471

```

---

### Post by darkromis on 2009-04-12
thank you all for your help :p, the c++ function is clear thanks to dribea's example. but in c I don't know how to explicit link. In orden to expose my problem better I have below exactly what I've done in Geany ide and what does the ide return to me.
[B]
(the code I'm trying to compile)[/B]
#include <stdio.h>
#include <math.h>
 
int main()
{
   double x = 3.1416/3.0;

   printf( "sin( %f ) = %f\n", x, sin(x) );
   return 0;
}

although compilation it's succesful, when I tried to build that's what it
happens:

(**The message windows **)
/tmp/cci8ouRn.o: In function `main':
seno.c: (.text+0x21): undefined reference to `sin'
collect2: ld devolvió el estado de salida 1 (Id returned output state 1)
La compilación falló. (compilation failed)

---

### Post by kknd on 2009-04-12
gcc myapp.c -o app **-lm**

---

### Post by Arndt on 2009-04-13
> **kknd said:**
> gcc myapp.c -o app **-lm**

In case you should forget, if you do "man sin", it says

```
NAME
       sin, sinf, sinl - sine function

SYNOPSIS
       #include <math.h>

       double sin(double x);
       float sinf(float x);
       long double sinl(long double x);

       Link with -lm.

```

---

### Post by slavik on 2009-04-13
I am pretty sure that cmath is the C's math library ... because of the whole 'c' being the first char, I am also very sure that this is part of the C++ standard.

---

### Post by Habbit on 2009-04-14
> **slavik said:**
> I am pretty sure that cmath is the C's math library ... because of the whole 'c' being the first char, I am also very sure that this is part of the C++ standard.

<cmath> is the C++ version of the standard C library header <math.h>. The difference between the <x.h> files and its <cx> C++ counterparts is that <cx> declare their members as `extern "C"' and within the std namespace. The latter is a matter of style, while the former prevents the C++ compiler from mangling the names of the functions in the C++ manner. Sometimes, including a standard <x.h> file in a C compiler works because they have #ifdef guards like this: ```
#ifdef __cplusplus
extern "C" {
#endif

/* C prototypes, defines, etc.  
   If included by a C++ compiler, names won't be mangled.  */
float sin(float x);  /* "sin" instead of i.e. "F3sinF1xE" */
float cos(float x);

#ifdef __cplusplus
} /* extern "C" */
#endif
```

---

### Post by dribeas on 2009-04-14
> **Habbit said:**
> <cmath> is the C++ version of the standard C library header <math.h>. The difference between the <x.h> files and its <cx> C++ counterparts is that <cx> declare their members as `extern "C"' and within the std namespace. 

And it disables most of the macros and convert them into inline functions... which is both a matter of style and usability. Most compilers I know are both C/C++ and they do have the extern "C" in math.h as well as cmath. In fact a couple of implementations of C++ <cxxxxx> libraries start with declaring a namespace and including the <xxxxx.h> library, after which some macros are undefined and the equivalent functions implemented.

---

