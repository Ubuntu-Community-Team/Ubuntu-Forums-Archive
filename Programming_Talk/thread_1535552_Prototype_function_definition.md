---
title: "Prototype function definition"
date: 2010-07-21
forum: Programming Talk
---

### Post by grk.jkb on 2010-07-21
Hi, i am using a tool developed in C and i use "make all" command to run. But the following error occur:

cc -O -DUNIX -DBSD -g -I/home/English/morph-1.5/hash -I/usr/include/X11/Xaw  -c -w -o lib/bcopy.o /home/English/morph-1.5/hash/bcopy.c
/home/English/morph-1.5/hash/bcopy.c: In function ‘bcopy’:
/usr/include/bits/string3.h:90: error: old-style parameter declarations in prototyped function definition
make: *** [lib/bcopy.o] Error 1

and the program is given below

#if defined(LIBC_SCCS) && !defined(lint)
static char sccsid[] = "@(#)bcopy.c    5.7 (Berkeley) 5/16/90";
#endif /* LIBC_SCCS and not lint */

#include <string.h>
#include <sys/types.h>

/*
 * sizeof(word) MUST BE A POWER OF TWO
 * SO THAT wmask BELOW IS ALL ONES
 */
typedef    int word;        /* "word" used for optimal copy speed */

#define    wsize    sizeof(word)
#define    wmask    (wsize - 1)

/*
 * Copy a block of memory, handling overlap.
 * This is the routine that actually implements
 * (the portable versions of) bcopy, memcpy, and memmove.
 */
void bcopy(const void *src0, void *dst0, size_t length)
//void bcopy( src0, dst0, length)
    char *dst0;
    char *src0;
    register size_t length;    
{
    register char *dst = dst0;
    register char *src = src0;
    register size_t t;

    if (length == 0 || dst == src)        /* nothing to do */
        return;

    /*
     * Macros: loop-t-times; and loop-t-times, t>0
     */
#define    TLOOP(s) if (t) TLOOP1(s)
#define    TLOOP1(s) do { s; } while (--t)

    if ((unsigned long)dst < (unsigned long)src) {
        /*
         * Copy forward.
         */
        t = (int)src;    /* only need low bits */
        if ((t | (int)dst) & wmask) {
            /*
             * Try to align operands.  This cannot be done
             * unless the low bits match.
             */
            if ((t ^ (int)dst) & wmask || length < wsize)
                t = length;
            else
                t = wsize - (t & wmask);
            length -= t;
            TLOOP1(*dst++ = *src++);
        }
        /*
         * Copy whole words, then mop up any trailing bytes.
         */
        t = length / wsize;
        TLOOP(*(word *)dst = *(word *)src; src += wsize; dst += wsize);
        t = length & wmask;
        TLOOP(*dst++ = *src++);
    } else {
        /*
         * Copy backwards.  Otherwise essentially the same.
         * Alignment works as before, except that it takes
         * (t&wmask) bytes to align, not wsize-(t&wmask).
         */
        src += length;
        dst += length;
        t = (int)src;
        if ((t | (int)dst) & wmask) {
            if ((t ^ (int)dst) & wmask || length <= wsize)
                t = length;
            else
                t &= wmask;
            length -= t;
            TLOOP1(*--dst = *--src);
        }
        t = length / wsize;
        TLOOP(src -= wsize; dst -= wsize; *(word *)dst = *(word *)src);
        t = length & wmask;
        TLOOP(*--dst = *--src);
    }
    return;
}

---

### Post by lisati on 2010-07-21
Moved to "Programming Talk"

---

### Post by Compyx on 2010-07-21
> **grk.jkb said:**
> Hi, i am using a tool developed in C and i use "make all" command to run. But the following error occur:

cc -O -DUNIX -DBSD -g -I/home/English/morph-1.5/hash -I/usr/include/X11/Xaw  -c -w -o lib/bcopy.o /home/English/morph-1.5/hash/bcopy.c
/home/English/morph-1.5/hash/bcopy.c: In function ‘bcopy’:
/usr/include/bits/string3.h:90: error: old-style parameter declarations in prototyped function definition
make: *** [lib/bcopy.o] Error 1

```

void bcopy(const void *src0, void *dst0, size_t length)
//void bcopy( src0, dst0, length)
    char *dst0;
    char *src0;
    register size_t length;    
{

```


That's were the error is occuring, like the message said, old-style (pre-ANSI) parameter declarations mixed with prototyped (ANSI) function definition.
Two quick solutions here: either remove the prototyped definition and uncomment the old-style definition:
```

//void bcopy(const void *src0, void *dst0, size_t length)
void bcopy( src0, dst0, length)
    char *dst0;
    char *src0;
    register size_t length;    
{

```

or use the new-style prototyped function defintion:
```

void bcopy(const void *src0, void *dst0, size_t length)
/* void bcopy( src0, dst0, length)
    char *dst0;
    char *src0;
    register size_t length;    
*/
{

```

I would go for the prototyped function definition, unless you need portability to old systems without an ANSI/ISO-C compliant compiler.

Another way is this:
```

#ifdef __STDC__
void bcopy(const void *src0, void *dst0, size_t length)
#else
void bcopy( src0, dst0, length)
    char *dst0;
    char *src0;
    register size_t length;    
#endif
{

```
This will pick the prototyped version for ANSI/ISO-C compliant compilers and the old definition syntax for pre-ANSI/ISO compilers.

Additional nitpick: C++-style comments (//) are accepted in C99 and GNU-C, but illegal in C90, so if you want maximum portability you should avoid those.


Hope this helps.

---

