---
title: "Problem with a simple program in C using math.h"
date: 2012-06-20
forum: Programming Talk
---

### Post by jander on 2012-06-20
Hey,

I can't compile this simple program:

[INDENT]
#include <stdio.h>
#include <math.h>

int main() {
[INDENT]        float v = 3.14;

        printf("%f\n", sin(v));
        return 0;
[/INDENT]}
[/INDENT]

This is what I get:

[B]$ gcc -Wall -lm teste02.c 
/tmp/ccMBiHrv.o: In function `main':
teste02.c:(.text+0x1a): undefined reference to `sin'
collect2: ld returned 1 exit status[/B]

So I made a simple test:

[INDENT]
#include <stdio.h>
#include <math.h>

int main() {
[INDENT]        //float v = 3.14;

        printf("%f\n", sin(**3.14**));
        return 0;[/INDENT]
}
[/INDENT]

And surprise! It runs just fine!

Well, why can't I use a variable to funcion *sin*?

I really hope my question is not THAT stupid! :p

Info:

gcc --version
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright © 2011 Free Software Foundation, Inc.

Ubuntu 12.04

Thansk for any help.

Jander

---

### Post by Simian Man on 2012-06-20
You need to pass "-lm" to gcc to link with the math libraries.

Edit: Sorry, I see that you did.  This program works for me.  Do you have the full C standard library installed?

---

### Post by jim_24601 on 2012-06-20
Instead of

```
gcc -Wall -lm teste02.c
```

try

```
gcc -Wall teste02.c -lm
```

gcc can be quite fussy about the order of its command-line arguments, particularly when linking. Generally speaking, put libraries last, and libm last of all.

---

### Post by steeldriver on 2012-06-20
Agreed - my guess is it works in the 2nd case because gcc treats sin(3.14) as sin(double x) and finds a definition for that elsewhere (built-in or stdlib?); but when you explicitly call sin(float x) it needs libm, and fails because it's linked in the wrong order.

---

### Post by xb12x on 2012-06-20
Try
gcc -Wall teste02.c -lm

instead of
gcc -Wall -lm teste02.c

Whoops: jim_24601 beat me to it.

---

### Post by jim_24601 on 2012-06-20
Interesting. Compare

```
jim@bank-monument:/tmp$ cat test.c
#include <stdio.h>
#include <math.h>

int main() {

    float v = 3.14;

    printf("%f\n", sin(v));
    return 0;

}
jim@bank-monument:/tmp$ gcc -Wall -o test test.c -lm
jim@bank-monument:/tmp$ ldd test
	linux-vdso.so.1 =>  (0x00007fff07910000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f65ea558000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f65ea19b000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f65ea875000)

```

with

```
jim@bank-monument:/tmp$ cat test2.c
#include <stdio.h>
#include <math.h>

int main() {

//    float v = 3.14;

    printf("%f\n", sin(3.14));
    return 0;

}
jim@bank-monument:/tmp$ gcc -Wall -o test2 test2.c -lm
jim@bank-monument:/tmp$ ldd test2
	linux-vdso.so.1 =>  (0x00007fff7d1ff000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f9b24e03000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f9b251e3000)

```

Spot the difference? Looks like gcc is doing some sneaky optimisation and not bothering to link in the code for sin() if it's called with a constant.

---

### Post by jander on 2012-06-25
> **jim_24601 said:**
> Instead of

```
gcc -Wall -lm teste02.c
```

try

```
gcc -Wall teste02.c -lm
```

gcc can be quite fussy about the order of its command-line arguments, particularly when linking. Generally speaking, put libraries last, and libm last of all.

That really did the trick for me. :D

Funny. This was the very first time I had trouble with the order of the arguments to gcc...

Thanks jim, xb12x and everybody for the attention.

---

### Post by Simian Man on 2012-06-25
Odd, it works for me either way.  I'm using Fedora, I wonder if this is a bug in Ubuntu's gcc or if it's using an old version.

---

### Post by Sirveyor on 2013-02-03
I know this thread is a bit old but I was having the same issue with my Ubuntu system. I was using 'make' to compile my code and apparently make did not link the math.h library. Using gcc with the -lm did the trick. 

Does anyone know why the make utility did not link the math.h library?
I used the make utility on a different system to compile the code and it linked the math library as I expected.

If it is not blatantly  apparent I am new to Ubuntu.

---

### Post by Bachstelze on 2013-02-03
make only does what the Makefile tells it to do. If the Makefile was written using the wrong flag order, you will get the same error.

---

### Post by r-senior on 2013-02-03
Make has implicit rules that mean it knows how to do common transformations, e.g. a .c file into a .o file. These implicit rules don't link any other libraries though.

[http://www.gnu.org/software/make/manual/html_node/Implicit-Rules.html#Implicit-Rules](http://www.gnu.org/software/make/manual/html_node/Implicit-Rules.html#Implicit-Rules)

If you want make to link a specific library, you have to write that into a Makefile, i.e. you have to do more than use the implicit rules. Sometimes this means writing rules by hand, other times you can tap into the implicit rules by defining variables like LDLIBS to inject extra flags.

If you make a Makefile in the same directory as your source file containing just this line ...

```
LDLIBS=-lm
```

... you should be able to use make to build a program that uses the math library:

```
$ cat simple.c
#include <stdio.h>
#include <math.h>

int main() 
{
    double pi = 3.142;
    printf("%f\n", sin(pi));
    return 0;
}
$ cat Makefile
LDLIBS=-lm
$ make simple
[COLOR="Red"]cc     simple.c  -lm -o simple[/COLOR]
$ rm Makefile simple
$ make simple
[COLOR="red"]cc     simple.c   -o simple[/COLOR]
/tmp/cc4mAdV3.o: In function `main':
simple.c:(.text+0x1a): undefined reference to `sin'
collect2: error: ld returned 1 exit status
make: *** [simple] Error 1

```

Notice how the program fails to compile when I delete that Makefile because the commands produced by make (highlighted in red) are different.

---

