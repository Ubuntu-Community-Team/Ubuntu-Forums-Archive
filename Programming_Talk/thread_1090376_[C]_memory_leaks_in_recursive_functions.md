---
title: "[C] memory leaks in recursive functions"
date: 2009-03-08
forum: Programming Talk
---

### Post by hey_ram on 2009-03-08
hi all,

i had been trying some examples from k&r. i am facing problems in ex 4-13. the problem statement is this:

Write a recursive version of the function reverse(s) , which reverses the string s in place.

i wrote the following code:

[PHP]
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

char *reverse(char *src, int len);

int main(int argc, char *argv[])
{
    char *src, *dest, ch; 
    int i = 0;

    src = (char *)malloc(1*sizeof(char));
    dest = (char *)malloc(1*sizeof(char));

    fprintf(stdout, "\nEnter a string:");
    while( (ch = getchar()) != '\n')
    {   
        src = (char *)realloc(src, (i + 1)*sizeof(char));
        *(src + i++) = ch; 
    }   
    *(src + i) = '\0';

    dest = reverse(src, strlen(src));

    fprintf(stdout, "\n%s, after reversing => %s\n", src, dest);

    free(src);
    free(dest);
 return 0;
}

char *reverse(char *src, int len)
{
    static char *dest;
    static int i = 0, j = 0;

    while(j >= 0)
    {
        if( i == 0 )
        {
            dest = (char *)malloc(1*sizeof(char));
            j = len - 1;
        }
        dest = (char *)realloc(dest, (i + 1)*sizeof(char));
        *(dest + i++) = *(src + j--);
        dest = reverse(src, j);
    }
    *(dest + i + 1) = '\0';

    return dest;
}
[/PHP]

with the following valgrind report:

>  valgrind --tool=memcheck --leak-check=yes ./h
==10448== Memcheck, a memory error detector.
==10448== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==10448== Using LibVEX rev 1804, a library for dynamic binary translation.
==10448== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==10448== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==10448== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==10448== For more details, rerun with: -v
==10448== 

Enter a string:google mail
==10448== Invalid write of size 1
==10448==    at 0x804856F: main (reverse_recursive.c:23)
==10448==  Address 0x418c2ab is 0 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048545: main (reverse_recursive.c:20)
==10448== 
==10448== Invalid read of size 1
==10448==    at 0x40239E3: strlen (mc_replace_strmem.c:242)
==10448==    by 0x804857C: main (reverse_recursive.c:25)
==10448==  Address 0x418c2ab is 0 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048545: main (reverse_recursive.c:20)
==10448== 
==10448== Invalid write of size 1
==10448==    at 0x804868F: reverse (reverse_recursive.c:51)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==  Address 0x418c52c is 1 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048621: reverse (reverse_recursive.c:47)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448== 
==10448== Invalid write of size 1
==10448==    at 0x804868F: reverse (reverse_recursive.c:51)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804858B: main (reverse_recursive.c:25)
==10448==  Address 0x418c52c is 1 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048621: reverse (reverse_recursive.c:47)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448== 
==10448== Invalid write of size 1
==10448==    at 0x804868F: reverse (reverse_recursive.c:51)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804858B: main (reverse_recursive.c:25)
==10448==  Address 0x418c52c is 1 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048621: reverse (reverse_recursive.c:47)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448== 
==10448== Invalid write of size 1
==10448==    at 0x804868F: reverse (reverse_recursive.c:51)
==10448==    by 0x804858B: main (reverse_recursive.c:25)
==10448==  Address 0x418c52c is 1 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048621: reverse (reverse_recursive.c:47)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)
==10448==    by 0x804866B: reverse (reverse_recursive.c:49)

==10448== 
==10448== Invalid read of size 1
==10448==    at 0x40239E3: strlen (mc_replace_strmem.c:242)
==10448==    by 0x407D811: vfprintf (in /lib/tls/i686/cmov/libc-2.7.so)
==10448==    by 0x4083321: fprintf (in /lib/tls/i686/cmov/libc-2.7.so)
==10448==    by 0x80485B2: main (reverse_recursive.c:27)
==10448==  Address 0x418c2ab is 0 bytes after a block of size 11 alloc'd
==10448==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==10448==    by 0x8048545: main (reverse_recursive.c:20)
google mail, after reversing => liam elgoog
==10448== 
==10448== ERROR SUMMARY: 16 errors from 7 contexts (suppressed: 11 from 1)
==10448== malloc/free: in use at exit: 1 bytes in 1 blocks.
==10448== malloc/free: 25 allocs, 24 frees, 135 bytes allocated.
==10448== For counts of detected errors, rerun with: -v
==10448== searching for pointers to 1 not-freed blocks.
==10448== checked 64,396 bytes.
==10448== 
==10448== 
==10448== 1 bytes in 1 blocks are definitely lost in loss record 1 of 1
==10448==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==10448==    by 0x8048506: main (reverse_recursive.c:15)
==10448== 
==10448== LEAK SUMMARY:
==10448==    definitely lost: 1 bytes in 1 blocks.
==10448==      possibly lost: 0 bytes in 0 blocks.
==10448==    still reachable: 0 bytes in 0 blocks.
==10448==         suppressed: 0 bytes in 0 blocks.


my questions are:
1. in the question, it says that the string needs to be replaced "in place". what does that mean exactly? does that mean i cannot return a char pointer (string) from the function, and that the original string needs to be altered?

2. is this program really a recursive function? i am struggling with recursive functions, and am not able to convince myself if this is one.

3. please help me find and plug the leak. i think it arises because i declare the destination string as static. but i have tried various combinations of free's and alloc's and the leak still seems to persist.

4. should i be bothered about the "invalid read" and "invalid write" operations?

thanks!

---

### Post by monkeyking on 2009-03-08
You should fix the errors before fixing the leak.

Without having looked to much at yourcode I think you need to malloc+1, such that \0 fits.

But I really haven't looked to deeply :)

---

### Post by hey_ram on 2009-03-08
the program works fine. the output is correct. however, these invalud reads and writes are generated when i run it with valgrind. that is what i want to know, whether i should be happy with the program running like a charm or should i be bothered about it...

---

### Post by dwhitney67 on 2009-03-08
The one character leak you have is from the initial allocation for space for dest in the main() function.  This allocation is not necessary, since allocation for dest will be taken care of in reverse().

By the way, here's an improvement on your code, with the hopes of reducing the number of allocations.
```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>


char* reverse(const char *src, const int len);

int main(int argc, char *argv[])
{
    char* src  = malloc(1);
    char* dest = 0;
    char  ch;
    int   i = 0;

    fprintf(stdout, "\nEnter a string: ");
    while( (ch = getchar()) != '\n')
    {   
        *(src + i++) = ch; 

        src = realloc(src, (i + 1) * sizeof(char));
    }   
    *(src + i) = '\0';

    dest = reverse(src, strlen(src));

    fprintf(stdout, "\n%s, after reversing => %s\n", src, dest);

    free(src);
    free(dest);
    return 0;
}

char* reverse(const char *src, const int len)
{
    static char* dest;
    static int   i = 0;
    static int   j = 0;

    if (i == 0)
    {
      dest = malloc(len + 1);
      j = len -1;
    }

    while (j >= 0)
    {
        *(dest + i++) = *(src + j--);

        dest = reverse(src, j);
    }

    if (i == len)
    {
        *(dest + i + 1) = '\0';
    }

    return dest;
}

```

---

### Post by winch on 2009-03-08
There are a few issues I can see.

In main() this malloc is lost.

dest = (char *)malloc(1*sizeof(char));

As later on dest is replaced by the return from reverse()

dest = reverse(src, strlen(src));

In addition to that try to keep memory management as simple as possible. The reverse function should eventually return a string the same length as src. No need to realloc for every character when you know how long the string is.

```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>

char *reverse(char *src, int len);

int main(int argc, char *argv[])
{
    char *src, *dest, ch; 
    int i = 0;

    src = (char *)malloc(1*sizeof(char));

    fprintf(stdout, "\nEnter a string:");
    while( (ch = getchar()) != '\n')
    {   
        src = (char *)realloc(src, (i + 1)*sizeof(char));
        *(src + i++) = ch; 
    }
    *(src + i) = '\0';

    dest = reverse(src, strlen(src));

    fprintf(stdout, "\n%s, after reversing => %s\n", src, dest);

    free(src);
    free(dest);
 return 0;
}

char *reverse(char *src, int len)
{
    static char *dest = NULL;
    static int i = 0, j = 0;
    
    if (dest == NULL)
    {
        dest = (char *)malloc((strlen(src)+1)*sizeof(char));
    }

    while(j >= 0)
    {
        if( i == 0 )
        {
            j = len - 1;
        }
        *(dest + i++) = *(src + j--);
        dest = reverse(src, j);
    }
    *(dest + i + 1) = '\0';

    return dest;
}  

```

---

### Post by monkeyking on 2009-03-08
> **hey_ram said:**
> the program works fine. the output is correct. however, these invalud reads and writes are generated when i run it with valgrind. that is what i want to know, whether i should be happy with the program running like a charm or should i be bothered about it...

You're program should not have invalid read/writes.
It should only happen if you are using some optimized libraries.

Just because a program doesn't crash and give correct results,
it doesn't mean that it actually works.

You can run it 1000times and then the 1001 it will crash.

---

### Post by hey_ram on 2009-03-09
got it..

i made the following changes:
1. removed the malloc from main.
2. instead of a realloc every time, i now have just one malloc at the beginning of the function definition.

but some questions remain:
1. should i be bothered about invalid read and write?

thanx winch and dwhitney67 for your help!

---

