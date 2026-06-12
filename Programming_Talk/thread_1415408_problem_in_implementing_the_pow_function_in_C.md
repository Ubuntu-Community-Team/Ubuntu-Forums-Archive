---
title: "problem in implementing the pow function in C"
date: 2010-02-24
forum: Programming Talk
---

### Post by sri2887 on 2010-02-24
Hello frnds,
I'm having a probelm while using the pow() function in my C program. 
when i compile it, it says:
 undefined reference to `pow'
even this simple code does not work:

#include<stdio.h>
#include<math.h>
int main(int argc, char *argv[])
{
   double m=2,n=5;    
   printf("2^5 = %lf\n",pow(m,n));
   return 0;
}

Awaiting your help
Thnx

---

### Post by pbrane on 2010-02-24
Your code seems fine. Did you compile it with
```

gcc -o myapp myapp.c **-lm**

```

You need to link with the math library, **-lm**

---

### Post by sri2887 on 2010-02-24
Thank you so much..i did not know this
now it works just fine:)

---

### Post by not_a_phd on 2010-02-24
Interesting. I have never had to explicitly include the math library with an -lm flag when compiling programs with gcc (or g++). Is there something in the configuration of gcc that allows me to compile programs with math routines and link to the math library by default. 

I see that he doesn't have to explicitly link to the stdio library. What is the difference?

---

### Post by dwhitney67 on 2010-02-24
gcc requires that you specify the -lm when using the math library functions.  g++ does not.

I don't know why it is so.

---

### Post by not_a_phd on 2010-02-24
More weirdness - gcc does not require the -lm flag for sin, cos, asin, and other math.h functions. But, it absolutely does require it for the pow function.

---

### Post by dwhitney67 on 2010-02-24
> **not_a_phd said:**
> More weirdness - gcc does not require the -lm flag for sin, cos, asin, and other math.h functions. But, it absolutely does require it for the pow function.

Compile the following with /usr/bin/gcc; do NOT use any alias you may have setup for gcc:

sin.c:
```

#include <math.h>
#include <stdio.h>

int main()
{
   double rads = 1.0;
   double res  = sin(rads);
   printf("res = %g\n", res);
   return 0;
}

```
```

/usr/bin/gcc sin.c
/tmp/cc4L7end.o: In function `main':
sin.c:(.text+0x17): undefined reference to `sin'
collect2: ld returned 1 exit status

```

---

### Post by not_a_phd on 2010-02-24
Did what you said on UNR Karmic Koala, and it compiled just fine. On my machine, /usr/bin/gcc is a link to /usr/bin/gcc-4.4. When I compile with this executable, it works just fine. 

I won't look the gift horse in the mouth on my box, but will be aware of the issue if I run into it down the road.

---

### Post by pbrane on 2010-02-25
This link attempts to explain why you need to link with libm in C but not in C++,
[http://stackoverflow.com/questions/1033898/why-do-you-have-to-link-the-math-library-in-c]("http://stackoverflow.com/questions/1033898/why-do-you-have-to-link-the-math-library-in-c")
Some of it makes sense.

---

