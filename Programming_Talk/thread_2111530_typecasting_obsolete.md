---
title: "typecasting obsolete"
date: 2013-02-02
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-02
Hello,
I understand that typecasting is obsolete now. I was trying to google for scenarios under which explicit typecasting like [b]char* ptr;
ptr = (char*)malloc(200 * sizeof(char))[/b] can cause errors and stumbled upon this link [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1047673478&id=1043284351](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1047673478&id=1043284351) .

The link says that it becomes dangerous only if your stdlib.h file is missing. 
So I wrote the following simple program and compiled as **gcc -nostdlib main.c**. But it gives me an error saying that malloc and printf are undefined. **My question is, if stdlib.h is not present, it gives such a strong error which makes it easy to understand what is going wrong, I wanted something where the program doesn't build/doesn't run as expected only because we have done the explicit typecasting**.

```

#include <stdio.h>

int main(void)
{
 char* str;

 str =(char*) malloc(200 * sizeof(char));
 strcpy(str,"hello world ");
 printf("\nstr == [%s]",str);

 return 0;
}

```

Error
```
$ gcc -nostdlib main.c
main.c: In function âmainâ:
main.c:7: warning: incompatible implicit declaration of built-in function âmallocâ
main.c:8: warning: incompatible implicit declaration of built-in function âstrcpyâ
/usr/local/bin/ld: warning: cannot find entry symbol _start; defaulting to 08048074
/tmp/cccxsB0F.o: In function `main':
main.c:(.text+0x19): undefined reference to `malloc'
main.c:(.text+0x4a): undefined reference to `printf'
collect2: ld returned 1 exit status

```
Thanks.

---

### Post by Bachstelze on 2013-02-02
First, the word "typecast" does not exist in C. The proper word is "cast", and it is certainly not obsolete in general. What you are referring to is the special case of casting the return value of malloc(). This is indeed unnecessary.

You are missing a header file in your code.

---

### Post by r-senior on 2013-02-02
If you use the -nostdlib during compilation, gcc does not link against the library and you get the linker error. That's not what the FAQ is talking about.

The FAQ says that if you cast the result of malloc to the wrong type and you forget the #include you could end up with an obscure bug. (You'd have to disable or ignore default compiler warnings too).

If you did all that, you'd deserve an obscure bug.

So, as a minimum, always compile with -Wall, always include the correct headers and always run any program that allocates dynamic memory through something like valgrind.

---

### Post by IAMTubby on 2013-02-02
> **Bachstelze said:**
> First, the word "typecast" does not exist in C. The proper word is "cast", and it is certainly not obsolete in general. What you are referring to is the special case of casting the return value of malloc(). This is indeed unnecessary.

You are missing a header file in your code.
Thanks Bachstelze, yes I added stdlib.h, but built my code with gcc -nostdlib so that I get an error.
From what I read in the article I mentioned, I was hoping that I would get an error on building with -nostdlib only on doing casting , but as it turns out, I will get an error with and without the cast because malloc and printf come under stdlib.h.

This was my naive way of trying to see an error on casting the return value of malloc. 
Thanks for correcting my terms, shall remember them .

---

### Post by dwhitney67 on 2013-02-02
Try compiling your code with the -w option (that's lowercase w).  This will suppress all warnings.

Since malloc() is not defined, the compiler will assume it returns an int, which is typically 4-bytes long on a 32-bit PC.  When you convert this return value to a char*, everything should work fine.

Try this on a 64-bit PC, and your luck will not be so good.

P.S.  Addresses (pointers) on a 64-bit PC are 8 bytes long.

---

### Post by IAMTubby on 2013-02-02
> **dwhitney67 said:**
> Try compiling your code with the -w option (that's lowercase w).  This will suppress all warnings.

Since malloc() is not defined, the compiler will assume it returns an int, which is typically 4-bytes long on a 32-bit PC.  When you convert this return value to a char*, everything should work fine.

Try this on a 64-bit PC, and your luck will not be so good.

P.S.  Addresses (pointers) on a 64-bit PC are 8 bytes long.
dwhitney, I understand what you said. So, to see variable output, I have to do the following on a 64-bit OS, correct ?
_Run code_
```

#include <stdio.h>
**make sure that #include <stdlib.h> is not there**
#include <string.h>

int main(void)
{
 char* str;
 str = (char*)malloc(200 * sizeof(char));
 strcpy(str,"hello world");

 printf("\nstr == [%s]",str);

 printf("\nsize of a pointer == [%d]",sizeof(void*));

 return 0;
}

```

_Build as:_
**gcc -w main.c**

Is that correct ? I currently don't have access to a 64-bit systen, shall try out in a few hours and get back to you.

---

### Post by dwhitney67 on 2013-02-02
> **IAMTubby said:**
> 
I currently don't have access to a 64-bit systen, ...

I do, and my theory is not playing out as I expected.  In other words, what I stated earlier apparently is bogus.

The rule of thumb is to use -Wall when compiling your code.  If some "bug" in the compiler allows for sloppy coding, then so be it.

---

### Post by IAMTubby on 2013-02-02
> **dwhitney67 said:**
> I do, and my theory is not playing out as I expected.  In other words, what I stated earlier apparently is bogus.

The rule of thumb is to use -Wall when compiling your code.  If some "bug" in the compiler allows for sloppy coding, then so be it.
alright :)

---

### Post by Bachstelze on 2013-02-02
I have finally read the article (better late than never). What it mentions is irrelevant with all modern compilers that I know of: if you do not include the header, they will warn you anyway.

---

### Post by trent.josephsen on 2013-02-02
Going back to your original question a little bit...

Casts are almost never necessary, and when you find yourself writing one it should cause you to stop and think a bit. In particular, malloc() is guaranteed to return a void * that is correctly aligned for any purpose, so the implicit conversion from void * to <whatever> * will always work losslessly on any conforming C implementation. A cast is therefore unnecessary, and the *only possible reason* for including it is to suppress a warning -- which is a warning you *wouldn't want to suppress*, even if it's not very likely to happen.

Casts still pop up from time to time. Since conversions are usually implicit, casts are primarily useful to make implicit conversions explicit, in order to suppress a compiler warning when you know that *you are right and the compiler is wrong*. This is why casts should not be used willy-nilly; they *always* suppress a potential compiler warning, and when using one you must accept the consequences of disabling that particular warning.

---

### Post by Bachstelze on 2013-02-02
> **trent.josephsen said:**
> 
Casts are almost never necessary,

While I agree with this, I feel compelled to provide an example where a cast is necessary. Say you want to write a function that returns a 64-bit bitfield with the rightmost n bits set to 1, and all others to 0. One way is (I put it all in main for simplicity):

```
firas@wakaba ~ % cat test.c 
#include <stdint.h>
#include <stdio.h>

int main(void)
{
    int n = 1;
    uint64_t a = (~0) >> (64-n);
    uint64_t b = (uint64_t)(~0) >> (64-n);
    printf("%lu %lu\n", a, b);
}
firas@wakaba ~ % gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@wakaba ~ % ./test 
18446744073709551615 1

```

---

### Post by trent.josephsen on 2013-02-02
Quite right, but I find myself confused by why the correct version works, on a machine where int is 32 bits. Shouldn't ~0, converted to uint64_t, be 00000000ffffffff?

Edit -- never mind, I see it's because of sign-extension when converting from signed to unsigned. /facepalm

---

### Post by Bachstelze on 2013-02-02
EDIT: Yes, sign extension. More precisely, ~0 is -1 as an int so when you convert it to uint64_t you get 2^64-1...

---

### Post by steeldriver on 2013-02-02
possibly slightly OT but what about making the constant 0 explicitly unsigned long with UL? is that different / more / less acceptable? 

```
$ cat test.c 
#include <stdint.h>
#include <stdio.h>

int main(void)
{
    int n = 1;
    uint64_t a = (~0) >> (64-n);
    uint64_t b = (~0[COLOR=Red]UL[/COLOR]) >> (64-n);
    printf("%lu %lu\n", a, b);
}
$ gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
$ ./test
18446744073709551615 1
$ 
```

---

### Post by Bachstelze on 2013-02-02
> **steeldriver said:**
> possibly slightly OT but what about making the constant 0 explicitly unsigned long with UL? is that different / more / less acceptable? 

unsigned long is not guaranteed to be 64 bits. On x86 it is 32 bits.

---

### Post by Bachstelze on 2013-02-02
But!

```
firas@wakaba ~ % cat test.c 
#include <stdint.h>
#include <stdio.h>

int main(void)
{
    int n = 1;
    uint64_t a = (~0) >> (64-n);
    uint64_t b = (~0UL) >> (64-n);
    printf("%llu %llu\n", a, b);
}
firas@wakaba ~ % gcc -m32 -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@wakaba ~ % ./test 
18446744073709551615 1

```

So does UL work after all? Let's try something else, another way to do the same thing:

```
firas@wakaba ~ % cat test.c 
#include <stdint.h>
#include <stdio.h>

int main(void)
{
    int n = 35;
    uint64_t a = (1 << n) - 1;
    uint64_t b = (1UL << n) - 1;
    uint64_t c = ((uint64_t)1 << n) - 1;
    printf("%llu %llu %llu\n", a, b, c);
}
firas@wakaba ~ % gcc -m32 -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@wakaba ~ % ./test 
7 7 34359738367

```

Hmmmmmm, It seems that UL only works when ~ is involved...

---

### Post by steeldriver on 2013-02-02
... but ULL does apparently...? 

```
$ cat test.c
#include <stdint.h>
#include <stdio.h>

int main(void)
{
    int n = 35;
    uint64_t a = (1 << n) - 1;
    uint64_t b = (1**ULL** << n) - 1;
    uint64_t c = ((uint64_t)1 << n) - 1;
    printf("%llu %llu %llu\n", a, b, c);
}
$ gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
$ ./test
7 34359738367 34359738367
$
```OK going to stop messing now...

---

### Post by Bachstelze on 2013-02-02
Technically it does, but it's unreliable. Who knows what unsigned long long will be all machines present and future? I'm still trying to make sense of why it works with ~ and not without...

---

### Post by trent.josephsen on 2013-02-02
UL alone works for me without -m32, so that's not an apples-to-apples comparison. I can't test both because I'm not on a multilib system.

---

### Post by Bachstelze on 2013-02-02
> **trent.josephsen said:**
> UL alone works for me without -m32, so that's not an apples-to-apples comparison. I can't test both because I'm not on a multilib system.

UL will work on 64 but not on 32. ULL will work on both but might not work on other more obscure archs. AFAIK the only way to mke sure it's 64 bits is to cast to uint64_t: that's what it's for. (And that was basically my original point, all the subsequent mess was unintentional. :p)

---

### Post by steeldriver on 2013-02-02
> **Bachstelze said:**
> ([...] all the subsequent mess was unintentional. :p)

... and largely my fault - sorry

---

### Post by Bachstelze on 2013-02-02
> **steeldriver said:**
> ... and largely my fault - sorry

Not at all, it gave me one new thing to learn about C!

---

