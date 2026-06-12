---
title: "c compiling errors"
date: 2006-10-09
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-09
here is my code for a fibonacci sequence ```
#include <stdio.h>

main()
{
        int n = 1000;
        double first = 0;
        double second = 1;
        printf (double first);
        printf ("    ");
        printf (double second);
        printf ("    ");

        while (n>0)
                {
                        double third = first + second;
                        first = second;
                        second = third;
                        printf (double third);
                        printf ("    ");
                        n--;
                }
}

```

when i compile it with gcc i get this-
```
fibiterative.c: In function ‘main’:
fibiterative.c:8: error: expected expression before ‘double’
fibiterative.c:10: error: expected expression before ‘double’
fibiterative.c:18: error: expected expression before ‘double’

```

anyone have any guesses?

---

### Post by JAwuku on 2006-10-09
Maybe the error is in the printf commands.

Instead of ```
printf (double first);
```

try ```
printf ("%f", first);
```

and do the same for the second and third printf statements.

see if that works

---

### Post by JAwuku on 2006-10-09
To see a list of printf() functions, see this posting:

[http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/printf.html](http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/printf.html)

especially the formatting identifiers such as %f

[http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/format.html](http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/format.html)

One particular variable type is the **long long** integer type, which can handle up to 64 bit integers.

I have modified the code to reflect long long integers:

```
#include <stdio.h>

main()
{
        int n = 1000;
        unsigned long long int first = 0;
        unsigned long long int second = 1;
        printf ("%llu", first);
        printf ("    ");
        printf ("%llu", second);
        printf ("    ");

        while (n>0)
                {
                        unsigned long long int third = first + second;
                        first = second;
                        second = third;
                        printf ("%llu", third);
                        printf ("    ");
                        n--;
                }
}
```

---

### Post by meng on 2006-10-09
jawuku is spot on.
I have to ask, baldy, do you think it's wise to try and learn 3 languages at once? I see you've posted on trying to achieve the same thing in python, perl and C all within the last 24 hours. I wonder if you may be better off trying to learn 1 language, master the syntax and learn the concepts, and when you have those under your belt, move on to other languages if you wish.

My concern is that you're going to be progressing very slowly while you're making these very elementary syntax errors, and increasing the risk of confusion between the languages. Just my two cents, of course it's your decision.

---

### Post by po0f on 2006-10-09
JAwuku,

Don't you have to compile programs that use the long long on 32-bit systems with -DGNU_SOURCE?  As much as we would like it, there are still people on 32-bit systems (me included).


baldy1324,

meng is correct.  You should at least learn the basic syntax of a programming language before jumping to another one.  If you need help deciding on a good first language, try [Python](http://www.python.org/).  It's a very easy to use language, has [good documentation](http://www.python.org/doc/2.4.3/), and can do everything a beginning programmer can want from a computer language.

---

### Post by JAwuku on 2006-10-09
Regarding the use of long long on 32-bit systems,

I think it is standard across the ANSI/ISO C standards.

I compiled the above on my 32-bit Mac G4 laptop which works without a problem.  version: powerpc-apple-darwin8-gcc-4.0.0 (GCC)

No reason why it shouldn't work on Linux 32-bit as well.

---

### Post by amo-ej1 on 2006-10-10
i don't see any issue on the long long issue either

```

#include <stdio.h>

int main(int argc, char **argv){
        printf("%d\n",sizeof(long long));
}

```

Which behaves as expected:

```

e@lap:/tmp$ uname -m
i686
e@lap:/tmp$ ./a.out 
8

```

---

### Post by po0f on 2006-10-10
Blar, I guess I was wrong.  I guess I just got confused when browsing the header files, specifically /usr/include/limits.h.

---

