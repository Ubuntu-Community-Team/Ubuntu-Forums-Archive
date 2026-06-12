---
title: "C portability question"
date: 2011-07-14
forum: Programming Talk
---

### Post by lucasart on 2011-07-14
Hello

I define the following type:

```

typedef struct {
    unsigned fsq:6, tsq:6;
    unsigned piece:3, capture:3, promotion:3;
    unsigned ep:1, check:1;
} move_t;

```and then I want to test equality move_t variables. but i dont want to do it stupidly by comparing every element, because it has to be a fast operation (essentially i'm comparing 2 integers)

So I wrote the following function

```

static inline bool move_equal(move_t m1, move_t m2) { return *(int *)&m1 == *(int *)&m2; }

```But I really don't like this dirty hack, because whether sizeof(move_t) equals sizeof(int) is both plateform and compiler dependant.

Anyone has a better idea ?

Thank you

PS: this is plain C, not C++, despite the usage of bool (it compiles with the gcc flag -std=c99)

---

### Post by Bachstelze on 2011-07-14
memcmp(&m1, &m2, sizeof(move_t))

---

### Post by lucasart on 2011-07-14
> **Bachstelze said:**
> memcmp(&m1, &m2, sizeof(move_t))

Thanks. Actually I thought of that, but I want to be sure the memcmp function call will be removed in compiled code. Would the assembly version of this be a simple cmp instruction comparing m1 and m2 (stored in 32 bit registers) ? (I'm using gcc -O3)

---

### Post by karlson on 2011-07-14
> **lucasart said:**
> Hello

I define the following type:

```

typedef struct {
    unsigned fsq:6, tsq:6;
    unsigned piece:3, capture:3, promotion:3;
    unsigned ep:1, check:1;
} move_t;

```and then I want to test equality move_t variables. but i dont want to do it stupidly by comparing every element, because it has to be a fast operation (essentially i'm comparing 2 integers)

So I wrote the following function

```

static inline bool move_equal(move_t m1, move_t m2) { return *(int *)&m1 == *(int *)&m2; }

```But I really don't like this dirty hack, because whether sizeof(move_t) equals sizeof(int) is both plateform and compiler dependant.

Anyone has a better idea ?

Thank you

PS: this is plain C, not C++, despite the usage of bool (it compiles with the gcc flag -std=c99)

This code might have a significant problem on 64bit systems since size of the structs is by default is word aligned.

If you want to do this you might want to cast it to long instead of int.

So your second code piece should read:
```

static int move_equal(const move_t *m1, const move_t *m2) { return ((*((long *)m1)) == (*((long *)m2))); }

```

inline is a C++ keyword as far as I remember, which GCC would allow but some other compiler might not.

---

### Post by karlson on 2011-07-14
> **lucasart said:**
> Thanks. Actually I thought of that, but I want to be sure the memcmp function call will be removed in compiled code. Would the assembly version of this be a simple cmp instruction comparing m1 and m2 (stored in 32 bit registers) ? (I'm using gcc -O3)

Consider you are on a 64-bit system.  So it would be a byte by byte comparison vs. integer to integer.

---

### Post by Bachstelze on 2011-07-14
> **lucasart said:**
> Thanks. Actually I thought of that, but I want to be sure the memcmp function call will be removed in compiled code. Would the assembly version of this be a simple cmp instruction comparing m1 and m2 (stored in 32 bit registers) ? (I'm using gcc -O3)

No, but it will do it if you implement your own memcmp. ;) (Compiled in 32 bit mode because x86_64 assembly is much less readable.)

```
firas@aoba ~ % cat test.c
#include <stdbool.h>

typedef struct {
        unsigned fsq:6, tsq:6;
        unsigned piece:3, capture:3, promotion:3;
        unsigned ep:1, check:1;
} move_t;

bool move_equal(move_t *m1, move_t *m2)
{
        unsigned char *p1 = (unsigned char*) m1;
        unsigned char *p2 = (unsigned char*) m2;
        for (int i=0; i<sizeof(move_t); i++) {
                if (*p1 != *p2) {
                        return false;
                }
        }
        return true;
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -O3 -m32 -S test.c
firas@aoba ~ % cat test.s 
	.text
	.align 4,0x90
.globl _move_equal
_move_equal:
	pushl	%ebp
	movl	%esp, %ebp
	movl	8(%ebp), %eax
	movzbl	(%eax), %edx
	movl	12(%ebp), %eax
	cmpb	(%eax), %dl
	sete	%al
	movzbl	%al, %eax
	leave
	ret
	.subsections_via_symbols

```

---

### Post by lucasart on 2011-07-14
> **karlson said:**
> This code might have a significant problem on 64bit systems since size of the structs is by default is word aligned.

If you want to do this you might want to cast it to long instead of int.

So your second code piece should read:
```

static int move_equal(const move_t *m1, const move_t *m2) { return ((*((long *)m1)) == (*((long *)m2))); }

```inline is a C++ keyword as far as I remember, which GCC would allow but some other compiler might not.

I'm afraid you're mistaken. I am running a 64 plateform, and I get the following

[LIST=1]
[*]sizeof(int) = 4
[*]sizeof(long) = 8
[*]sizeof(move_t) = 4
[/LIST]
but note that this is not a golden rule for 64 bit ! On win64, I suspect results are different for 1,2. And 3 depends also on the compiler (maybe MSVC will want to do a 8 byte for better alignment reasons or whatever). So still not portable, and it doesn't work on Linux64 + gcc

As for inline, it is a perfectly valid C keyword, instroduced by the ISO standard in C99

---

### Post by lucasart on 2011-07-14
> **Bachstelze said:**
> No, but it will do it if you implement your own memcmp. ;) (Compiled in 32 bit mode because x86_64 assembly is much less readable.)

```
firas@aoba ~ % cat test.c
#include <stdbool.h>

typedef struct {
        unsigned fsq:6, tsq:6;
        unsigned piece:3, capture:3, promotion:3;
        unsigned ep:1, check:1;
} move_t;

bool move_equal(move_t *m1, move_t *m2)
{
        unsigned char *p1 = (unsigned char*) m1;
        unsigned char *p2 = (unsigned char*) m2;
        for (int i=0; i<sizeof(move_t); i++) {
                if (*p1 != *p2) {
                        return false;
                }
        }
        return true;
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -O3 -m32 -S test.c
firas@aoba ~ % cat test.s 
    .text
    .align 4,0x90
.globl _move_equal
_move_equal:
    pushl    %ebp
    movl    %esp, %ebp
    movl    8(%ebp), %eax
    movzbl    (%eax), %edx
    movl    12(%ebp), %eax
    cmpb    (%eax), %dl
    sete    %al
    movzbl    %al, %eax
    leave
    ret
    .subsections_via_symbols

```
You're *awesome*, thanks !
It is indeed a strange behaviour of the gcc optimizer. Perhaps the optimizer would (given a good compiler) even do it if i iomplement my stupid comparison like m1.fsq == m2.fsq && m1.tsq == m2.tsq and so on...
I'll have a look!

---

### Post by Bachstelze on 2011-07-14
Meh, I forgot to increment p1 and p2. :p Then the assembly will basically mimic the code, which is not really efficient.

---

### Post by Bachstelze on 2011-07-14
> **lucasart said:**
> You're *awesome*, thanks !

Not quite, as it turned out. ;)

> It is indeed a strange behaviour of the gcc optimizer. Perhaps the optimizer would (given a good compiler) even do it if i iomplement my stupid comparison like m1.fsq == m2.fsq && m1.tsq == m2.tsq and so on...
I'll have a look!

It does on x86:

```
firas@aoba ~ % cat test.c                                            
#include <stdbool.h>
#include <string.h>

typedef struct {
        unsigned fsq:6, tsq:6;
        unsigned piece:3, capture:3, promotion:3;
        unsigned ep:1, check:1;
} move_t;

bool move_equal(move_t *m1, move_t *m2)
{
        return (m1->fsq == m2->fsq &&
                m1->tsq == m2->tsq &&
                m1->piece == m2->piece &&
                m1->capture == m2->capture &&
                m1->promotion == m2->promotion &&
                m1->ep == m2->ep &&
                m1->check == m2->check);
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -O3 -m32 -S test.c
firas@aoba ~ % cat test.s                                            
	.text
	.align 4,0x90
.globl _move_equal
_move_equal:
	pushl	%ebp
	movl	%esp, %ebp
	movl	8(%ebp), %eax
	movl	(%eax), %edx
	andl	$8388607, %edx
	movl	12(%ebp), %eax
	movl	(%eax), %eax
	andl	$8388607, %eax
	cmpl	%eax, %edx
	sete	%al
	movzbl	%al, %eax
	leave
	ret
	.subsections_via_symbols

```

But see that it basically compares ints. If you are on a platform where your struct occupies e.g. 34 bits, it might not work that well.

---

### Post by lucasart on 2011-07-14
> **Bachstelze said:**
> Meh, I forgot to increment p1 and p2. :p Then the assembly will basically mimic the code, which is not really efficient.
I'd like to do it in a more readable way anyway. Is it possible to do preprocessor directives like (approximative syntax) ?

```

#include <inttypes.h>

#if sizeof(move_t)==4
static inline bool move_equal(move_t m1, move_t m2) { return *(uint32_t *)&m1 == *(uint32_t *)&m2; }
#else if sizeof(move_t)==8
static inline bool move_equal(move_t m1, move_t m2) { return *(uint32_t *)&m1 == *(uint64_t *)&m2; }
#end

```

---

### Post by lucasart on 2011-07-14
> **Bachstelze said:**
> Not quite, as it turned out. ;)



It does on x86:

```
firas@aoba ~ % cat test.c                                            
#include <stdbool.h>
#include <string.h>

typedef struct {
        unsigned fsq:6, tsq:6;
        unsigned piece:3, capture:3, promotion:3;
        unsigned ep:1, check:1;
} move_t;

bool move_equal(move_t *m1, move_t *m2)
{
        return (m1->fsq == m2->fsq &&
                m1->tsq == m2->tsq &&
                m1->piece == m2->piece &&
                m1->capture == m2->capture &&
                m1->promotion == m2->promotion &&
                m1->ep == m2->ep &&
                m1->check == m2->check);
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -O3 -m32 -S test.c
firas@aoba ~ % cat test.s                                            
    .text
    .align 4,0x90
.globl _move_equal
_move_equal:
    pushl    %ebp
    movl    %esp, %ebp
    movl    8(%ebp), %eax
    movl    (%eax), %edx
    andl    $8388607, %edx
    movl    12(%ebp), %eax
    movl    (%eax), %eax
    andl    $8388607, %eax
    cmpl    %eax, %edx
    sete    %al
    movzbl    %al, %eax
    leave
    ret
    .subsections_via_symbols

```But see that it basically compares ints. If you are on a platform where your struct occupies e.g. 34 bits, it might not work that well.
That's good to know, and one thing less to worry about. Modern compilers are much more clever than I thought!

---

### Post by karlson on 2011-07-14
> **lucasart said:**
> I'm afraid you're mistaken. I am running a 64 plateform, and I get the following

[LIST=1]
[*]sizeof(int) = 4
[*]sizeof(long) = 8
[*]sizeof(move_t) = 4
[/LIST]
but note that this is not a golden rule for 64 bit ! On win64, I suspect results are different for 1,2. And 3 depends also on the compiler (maybe MSVC will want to do a 8 byte for better alignment reasons or whatever). So still not portable, and it doesn't work on Linux64 + gcc

As for inline, it is a perfectly valid C keyword, instroduced by the ISO standard in C99

I was thinking of something else you might be able to do:

```

typedef struct {
        unsigned fsq:6, tsq:6;
        unsigned piece:3, capture:3, promotion:3;
        unsigned ep:1, check:1;
} move_t_struct;

typedef union 
{
    move_t_struct move;
    long comparator;
} move_t;


```

This way your code for assignment would pick up another level of indirection, but your comparison would be 

```

static inline bool move_equal(const move_t *m1, const move_t *m2) { return (m1->comparator == m2->comparator); }

```

This way it should be fully portable.

---

### Post by Bachstelze on 2011-07-14
Another thing I thought of is that nothing in the standard seems to guarantee that the structs will be bit-for-bit identical if all fields are equal, the "padding" between the fields may not be (this is presumably why gcc ANDs it with a mask of 8388607 in the assembly above, to keep only the relevant bits).

---

### Post by lucasart on 2011-07-15
> **karlson said:**
> I was thinking of something else you might be able to do:

```

typedef struct {
        unsigned fsq:6, tsq:6;
        unsigned piece:3, capture:3, promotion:3;
        unsigned ep:1, check:1;
} move_t_struct;

typedef union 
{
    move_t_struct move;
    long comparator;
} move_t;


```This way your code for assignment would pick up another level of indirection, but your comparison would be 

```

static inline bool move_equal(const move_t *m1, const move_t *m2) { return (m1->comparator == m2->comparator); }

```This way it should be fully portable.
It is elegant, but still not portable. The point is that if you want portability you should *never* use the long type. And I mean never ! As you can see the only types that can be used are char, short and int. Anything else is plateform and architecture dependant (even pointers can be 32 bit on some 64 bit architectures). Have a look (and this is just linux, windows is already different to that)
[http://makelinux.com/ldd3/chp-11-sect-1](http://makelinux.com/ldd3/chp-11-sect-1)

In particular if we assume x86_64 + Linux, then sizeof(long)==8, and where the useful bits of the move_t are, and what's on the extra padding bits, you can assume nothing safely.

So in the end, the best solution is simply the naive one:
```

static inline bool move_equal(move_t m1, move_t m2) {
    // NB modern compilers optimize that as a simple cmp between 32 bit registers
    return m1.fsq == m2.fsq && m1.tsq == m2.tsq
        && m1.piece == m2.piece && m1.capture == m2.capture && m2.promotion == m2.promotion
        && m1.ep == m2.ep && m1.check == m2.check;
}

```

Actually your code is not only unportable, but simply dangerous. Let's stay on  Linux x86_64:
imagine in debug mode it all works because your compiler sets all the other bits (of your 64 bit union struct) at zero
now you compile in release, with compiler optimizations, and this is not true anymore (as shown by assembly outputs in prev posts). the program is very complex recursive code, and I have no idea how I would find the bug in that case...
Imagine the nightmare !

---

### Post by karlson on 2011-07-15
> **lucasart said:**
> It is elegant, but still not portable. The point is that if you want portability you should *never* use the long type. And I mean never ! As you can see the only types that can be used are char, short and int. Anything else is plateform and architecture dependant (even pointers can be 32 bit on some 64 bit architectures). Have a look (and this is just linux, windows is already different to that)
[http://makelinux.com/ldd3/chp-11-sect-1](http://makelinux.com/ldd3/chp-11-sect-1)


So use uint64_t or uint32_t if you know that the struct will fit.

---

### Post by lucasart on 2011-07-15
> **Bachstelze said:**
> Another thing I thought of is that nothing in the standard seems to guarantee that the structs will be bit-for-bit identical if all fields are equal, the "padding" between the fields may not be (this is presumably why gcc ANDs it with a mask of 8388607 in the assembly above, to keep only the relevant bits).
good point indeed!

---

### Post by lucasart on 2011-07-15
> **karlson said:**
> So use uint64_t or uint32_t if you know that the struct will fit.
No, this is still dangerous. all the 32 bits are not used, and the unused ones, you canot assume what's on them (see pose of bachstelze)

---

### Post by Bachstelze on 2011-07-15
> **lucasart said:**
> The point is that if you want portability you should *never* use the long type. And I mean never ! As you can see the only types that can be used are char, short and int. Anything else is plateform and architecture dependant


That is not true. short and int are also platform-dependent.  The standard does not define a size for any of them, only a lower bound.  Only char is guaranteed to be 8 bits.

> 5.2.4.2.1 Sizes of integer types <limits.h>

The values given below shall be replaced by constant expressions suitable for use in #if preprocessing directives. Moreover, except for CHAR_BIT and MB_LEN_MAX, the following shall be replaced by expressions that have the same type as would an
expression that is an object of the corresponding type converted according to the integer promotions. **Their implementation-defined values shall be equal or greater in magnitude (absolute value) to those shown, with the same sign.**

---

### Post by Bachstelze on 2011-07-15
> **karlson said:**
> So use uint64_t or uint32_t if you know that the struct will fit.

Very close but not strictly portable. ;)

> 7.18.1.1 Exact-width integer types

1 The typedef name intN_t designates a signed integer type with width N, no padding bits, and a two’s complement representation. Thus, int8_t denotes a signed integer type with a width of exactly 8 bits.
2 The typedef name uintN_t designates an unsigned integer type with width N. Thus, uint24_t denotes an unsigned integer type with a width of exactly 24 bits.
3 **These types are optional.** However, if an implementation provides integer types with widths of 8, 16, 32, or 64 bits, no padding bits, and (for the signed types) that have a two’s complement representation, it shall define the corresponding typedef names.

---

### Post by Bachstelze on 2011-07-15
A good lesson to be learned from this thread I think is that you should first try the obvious way, it may very well be the only way that will always work, and trust your compiler. If it can be optimized, the compiler will do it.

---

