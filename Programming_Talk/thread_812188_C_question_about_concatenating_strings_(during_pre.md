---
title: "C question about concatenating strings (during preprocessing)"
date: 2008-05-29
forum: Programming Talk
---

### Post by robheus on 2008-05-29
For a programming project in C I want to be able to concatenate two strings, but not sure if the gcc preprocessor is accepting the syntax.
Basically the idea is this (Example 1):
```

//Example 1
#include <stdio.h>
#define String1    "One string "
#define String2    "and another string"

char concatenated_string= String1 String2;
int main(void)
{ printf("%s\n", concatenated_string); }

```

The compiler will complain about the '"' however (non-matching or not-closed quotes), however, the code below (Example 2) compiles fine and runs:

```

//Example 2
#include <stdio.h>
int main(void)
{ printf("%s\n", "Hello," "world!\n" ); }

```

What does the official C grammar tell about these constructs? I believe that it said that concatenating strings are fine, and the compiler concatenates the strings at compile time.

The reason I need this is because I want to be able to put the value of some defined number into a string at compile time.

The idea is to be able to construct strings like this (Example 3):
```

//Example 3
#define A_VALUE    1234
#define QUOTE      "

char a_string="A string $" QUOTE A_VALUE QUOTE ;

```

But that won't compile, although it seems basically to fulfill the C grammar specs...

Any ideas???

Edit:

Not sure, but perhaps the C compiler is happier with a construct like this?
(Example 4)
```

//Example 4
char string[] = "String1" \
                "String2";

```

---

### Post by stylishpants on 2008-05-29
In the first code example you provide, the type of 'concatenated_string is 'char', when it should be 'char*'.
I fixed that, and found that the first code example compiled and ran without errors.

```
fhanson@fhanson:/tmp$ cat test.c
//Example 1
#include <stdio.h>
#define String1    "One string "
#define String2    "and another string"

char* concatenated_string= String1 String2;
int main(void)
{ printf("%s\n", concatenated_string); }
fhanson@fhanson:/tmp$ gcc test.c

fhanson@fhanson:/tmp$ ./a.out
One string and another string

fhanson@fhanson:/tmp$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
fhanson@fhanson:/tmp$ 

```

---

### Post by Joeb454 on 2008-05-29
Pointers can be very awkward sometimes in C. The amount of times I've read through my code (many times) to find I'd missed a * :p

---

### Post by robheus on 2008-05-30
> **stylishpants said:**
> In the first code example you provide, the type of 'concatenated_string is 'char', when it should be 'char*'.
I fixed that, and found that the first code example compiled and ran without errors.

```
fhanson@fhanson:/tmp$ cat test.c
//Example 1
#include <stdio.h>
#define String1    "One string "
#define String2    "and another string"

char* concatenated_string= String1 String2;
int main(void)
{ printf("%s\n", concatenated_string); }
fhanson@fhanson:/tmp$ gcc test.c

fhanson@fhanson:/tmp$ ./a.out
One string and another string

fhanson@fhanson:/tmp$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
fhanson@fhanson:/tmp$ 

```

Thx for the fix of '*'.
By the language spec it should compile Ok, but why doesn't Example 3 which -after preprocessing - results in the same source??

---

### Post by Verminox on 2008-05-31
What about something along the lines of:

```
#define A_VALUE 2

char a_string[20];
sprintf(a_string,"A String $%d",A_VALUE);

printf("%s",a_string); // A String $2
```

---

### Post by robheus on 2008-05-31
> **Verminox said:**
> What about something along the lines of:

```
#define A_VALUE 2

char a_string[20];
sprintf(a_string,"A String $%d",A_VALUE);

printf("%s",a_string); // A String $2
```

Of course that works, but only at runtime. I was aiming at assembling strings of (static/constant) data at compile time using the preprocessor....

---

### Post by Verminox on 2008-06-01
You can still concatenate strings using preprocessing...

```
#define H "Hello "
#define W "World!"
#define HW H W

printf(HW); // Prints "Hello World!"
```

The only trouble will be converting an int to a string, because there is no standard way of doing that at run-time even, let alone during pre-processing.

If you could define your A_VALUE to be "2" instead of just 2, then you shouldn't have problems.  If you want to use it as an integer for some other calculations you can use atoi.

```
#define A_VALUE "2"
#define A_VALUE_I atoi(A_VALUE)
```

---

