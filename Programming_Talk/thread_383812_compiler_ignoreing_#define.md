---
title: "compiler ignoreing #define"
date: 2007-03-13
forum: Programming Talk
---

### Post by Mars8082686 on 2007-03-13
When I was compiling my program the linker kept throwing me errors saying that I defined funtions/variables multiple times. I have #ifndef FILE_H  #define FILE_H on all my headers. (where file equals the name of the file). Is there a flag I have to enable in order for the G++ compiler to accept those commands?
when I take the include "main.h" out of the main, it will link, but with it in, it wont.

---

### Post by Mr. C. on 2007-03-13
The answer is no, you don't need to enable options for the macro preprocessor to work.

Break down your program to the smallest possible test case, to help you find what is going wrong.

FILE_H may be defined in one of the system includes; if so, use something that won't collide with the existing namespace (eg. MYPROG_FILE_H)

MrC

---

### Post by Mars8082686 on 2007-03-13
> **Mr. C. said:**
> The answer is no, you don't need to enable options for the macro preprocessor to work.

Break down your program to the smallest possible test case, to help you find what is going wrong.

FILE_H may be defined in one of the system includes; if so, use something that won't collide with the existing namespace (eg. MYPROG_FILE_H)

MrC
I wrote a simple program to test this.... I don't know how to make it any simpilier... heres the code
```

//test.h
#ifndef test_h
#define test_h
class test
{
    public:
	test();
	int value;
};
#endif


```
```

//test.cpp
#include "test.h"
#include "main.h"
test::test()
{
    value = 3*q;
}

```
```

//main.h
#ifndef main_h
#define main_h
int q = 3;
#endif

```
```

//main.cpp
#include <iostream>
#include "test.h"
#include "main.h"
int main()
{
    test kitten;
    std::cout<<"q";
    std::cout<<kitten.value;
}

```

And I still get a linking error... am I doing something wrong?

---

### Post by Mr. C. on 2007-03-13
You are including all your include files into both .cpp files.

Each file is compiled separately, and the preprocessor is run on each separately.

So you have main.cpp including the definition of your test class and q, and you have test.cpp doing the same thing.  You can't link them because q is defined twice.

MrC

---

### Post by lnostdal on 2007-03-13
hm, no .. the core of the problem is that he is both declaring and defining the symbol q in the header

```

//main.h
#ifndef main_h
#define main_h
extern int q; // declaration _only_
#endif

```

```

//main.cpp
#include <iostream>
#include "test.h"
#include "main.h"

int q = 3; // the definition of the symbol `q' goes here

int main()
{
    test kitten;
    std::cout<<"q";
    std::cout<<kitten.value;
}

```

..any file including `main.h' can now refer to the single q defined in main.cpp  (a good habit is naming your headers .hpp also btw.)

---

### Post by Mr. C. on 2007-03-13
Yes, this too.

It was common practice for many to do this:

```

$ cat main.c
#include "globs.h"

main () {
    printf ("C is %d\n", c);
}

$ cat globs.h 
#ifndef globs
#define globs
int c = 1;
extern int c;
#endif
```

Which compiles and works just fine.  As soon as you get a second compilation unit, it will fail.

Good catch,
MrC

---

### Post by Mars8082686 on 2007-03-13
Thank you for your help... now everything works :D

---

