---
title: "Bizarre realloc error in C (invalid next size)"
date: 2011-03-08
forum: Programming Talk
---

### Post by Colgax on 2011-03-08
Hi everybody!

I'm having a strange problem in a code I wrote today.

For now, the only thing it is supposed to do is read x strings using malloc and realloc, but after writing the fourth string and pressing enter, it gives me the following error:

```
*** glibc detected *** ./a.out: realloc(): invalid next size
```I've been searching for the answer on google for more than one hour, but I don't see why is this error happening, and why it just happens after the fourth loop.

Anyway, here is my code:

```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    char **words=NULL;
    void *words_alt=NULL;
    char c, new_line=1;
    int chars=0, strings=0;

    words=malloc(sizeof(*words));

    words[strings]=malloc(sizeof(*words[strings]));

    if (words==NULL || words[strings]==NULL)
    {
        puts("Memory allocation error... Bleh!");

        return 1;
    }

    words[0][0]='\0';

    for(;;)
    {
        c=getchar();

        if (c=='\n' && new_line)
        {
            break;
        }

        if (c!=' ')
        {
            if (c==',' || c==';' || c=='.' || c=='\n')
            {
                if (!new_line)
                {
                    new_line=1;

                    chars=0;

                    strings++;

                    puts("Error?");

                    words_alt=realloc(words, sizeof(*words));

                    if (words_alt==NULL)
                    {
                        puts("Memory allocation error... Bleh!");

                        return 2;
                    }

                    puts("Nope! YAY\n");

                    words=words_alt;;

                    words[strings]=malloc(sizeof(*words[strings]));

                    if (words[strings]==NULL)
                    {
                        puts("Memory allocation error... Bleh!");

                        return 3;
                    }

                    words[strings][0]='\0';
                }
            }
            else
            {
                new_line=0;

                words[strings][chars]=c;

                chars++;

                words_alt=realloc(words[strings], sizeof(*words[strings]));

                if (words_alt==NULL)
                {
                    puts("Memory allocation error... Bleh!");

                    return 4;
                }

                words[strings]=words_alt;

                words[strings][chars]='\0';
            }
        }
    }

    return 0;
}
```I haven't finished writing it yet, but I wanted to solve this problem before moving on...

Thanks for the attention! =D

EDIT: Oh, I forgot to mention that the realloc that gives me the error message is the one before the 'return 2'. It prints "Error?" but doesn't print "Nope! YAY\n".

---

### Post by Tony Flury on 2011-03-09
> **Colgax said:**
> Hi everybody!

I'm having a strange problem in a code I wrote today.

For now, the only thing it is supposed to do is read x strings using malloc and realloc, but after writing the fourth string and pressing enter, it gives me the following error:

```
*** glibc detected *** ./a.out: realloc(): invalid next size
```I've been searching for the answer on google for more than one hour, but I don't see why is this error happening, and why it just happens after the fourth loop.

************* CODE removed ***************

EDIT: Oh, I forgot to mention that the realloc that gives me the error message is the one before the 'return 2'. It prints "Error?" but doesn't print "Nope! YAY\n".

I can't exactly see what the problem is, but my guess is that somewhere you are stomping over either the start or the end of an existing malloced area - and thus destroying bits of the linked list that malloc/realloc uses to keep track of memory.

your mallocs/reallocs look odd - sizeof(*words) - what do you expect that to do ?

---

### Post by MadCow108 on 2011-03-09
use valgrind to find the problem.
and as flury said your allocs are off
e.g. this one in the loop:
```
words_alt=realloc(words, sizeof(*words));
words_alt=realloc(words[strings], sizeof(*words[strings]));
words=words_alt;
```
will not grow your memory as the size is a compile time constant (1, 4 or 8 ).

---

### Post by Colgax on 2011-03-09
When I was writing the code, I used numbers instead of using these sizeof's.

Since the error was "invalid next size", changing the "size" could fix it, but I was wrong =P

I'll give it a try with this valgrind.

---

### Post by Arndt on 2011-03-09
> **Colgax said:**
> When I was writing the code, I used numbers instead of using these sizeof's.

Since the error was "invalid next size", changing the "size" could fix it, but I was wrong =P

I'll give it a try with this valgrind.

You may find abort() and/or __LINE__ useful in your error handling. Returning a different number for each possible error is not bad in itself, but may be impractical. Making the error messages different from each other may also be a good idea.

---

### Post by Colgax on 2011-03-09
valgrind didn't help so much.

Anything that I try to do with the  variable "words", it tells me that it's an invalid write or read, but on valgrind it works till the 10th string.

I've tried to modify the code  and even create 2 other that do the same thing with other methods, and  now valgrind is telling me that "the impossible happened; killed by  fatal signal"

I'm starting to think about using normal arrays or  just writing the strings on a external temporary file instead of using  the memory.

---

### Post by Arndt on 2011-03-09
> **Colgax said:**
> valgrind didn't help so much.

Anything that I try to do with the  variable "words", it tells me that it's an invalid write or read, but on valgrind it works till the 10th string.

I've tried to modify the code  and even create 2 other that do the same thing with other methods, and  now valgrind is telling me that "the impossible happened; killed by  fatal signal"

I'm starting to think about using normal arrays or  just writing the strings on a external temporary file instead of using  the memory.

Since your original code was a kind of false trail, since you had arguments to sizeof that couldn't be correct, you had better show us the program as it looks now.

---

### Post by Colgax on 2011-03-09
> **Arndt said:**
> Since your original code was a kind of false trail, since you had arguments to sizeof that couldn't be correct, you had better show us the program as it looks now.

Right now it's like this:

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    char **words=NULL;
    char c, new_line=1;
    int chars=0, strings=0;

    words=malloc(8);

    words[strings]=malloc(1);

    if (words==NULL || words[strings]==NULL)
    {
        puts("Error 1");

        return 1;
    }

    words[0][0]='\0';

    for(;;)
    {
        c=getchar();

        if (c=='\n' && new_line)
        {
            break;
        }

        if (c!=' ')
        {
            if (c==',' || c==';' || c=='.' || c=='\n')
            {
                if (!new_line)
                {
                    new_line=1;

                    chars=0;

                    strings++;

                    printf("\n\nRealloc 2 - %d\n", __LINE__);

                    words=realloc(words, strings*8);

                    if (words==NULL)
                    {
                        puts("Error 2");

                        return 2;
                    }

                    puts("---Realloc 2 end---\n\n");
                    
                    printf("\n\nMalloc 3 - %d\n", __LINE__);

                    words[strings]=malloc(1);
                    
                    puts("---");

                    if (words[strings]==NULL)
                    {
                        puts("Error 3");

                        return 3;
                    }
                    
                    puts("---Malloc 3 end---\n\n");
                    
                    //printf("\n\n%lu - %x\n\n", sizeof(words[strings]), words[strings]);

                    //words[strings][0]='\0';
                }
            }
            else
            {
                new_line=0;

                printf("%d %d - %c (%x)\n", strings, chars, c, &words[strings][chars]);

                printf("\n\nRalloc 4 - %d\n", __LINE__);

                words[strings]=realloc(words[strings], chars+1);

                if (words[strings]==NULL)
                {
                    puts("Error 4");

                    return 4;
                }
                
                puts("---Realloc 4 end---\n\n");
                
                words[strings][chars]=c;

                chars++;

                //words[strings][chars]='\0';
            }
        }
    }
    
    puts(words[1]);

    return 0;
}
```Right now it's "working" if I run with valgrind, but it gives me the following error on the "Malloc 3" 

```
Malloc 3 - 57
==9378== Invalid write of size 8
==9378==    at 0x400791: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378==  Address 0x51b11d8 is 0 bytes after a block of size 8 alloc'd
==9378==    at 0x4C28254: realloc (vg_replace_malloc.c:525)
==9378==    by 0x400736: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378== 
---
==9378== Invalid read of size 8
==9378==    at 0x4007AB: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378==  Address 0x51b11d8 is 0 bytes after a block of size 8 alloc'd
==9378==    at 0x4C28254: realloc (vg_replace_malloc.c:525)
==9378==    by 0x400736: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378== 
---Malloc 3 end---
```If I just run it without valgrind, the same message from before shows up:

```
*** glibc detected *** ./a.out: realloc(): invalid next size
```Something else that I noticed is that, running on valgrind, the puts near the end of the code prints "Segmentation Fault", but running normaly, it prints the correct string.

---

### Post by Arndt on 2011-03-09
> **Colgax said:**
> Right now it's like this:

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    char **words=NULL;
    char c, new_line=1;
    int chars=0, strings=0;

    words=malloc(8);

    words[strings]=malloc(1);

    if (words==NULL || words[strings]==NULL)
    {
        puts("Error 1");

        return 1;
    }

    words[0][0]='\0';

    for(;;)
    {
        c=getchar();

        if (c=='\n' && new_line)
        {
            break;
        }

        if (c!=' ')
        {
            if (c==',' || c==';' || c=='.' || c=='\n')
            {
                if (!new_line)
                {
                    new_line=1;

                    chars=0;

                    strings++;

                    printf("\n\nRealloc 2 - %d\n", __LINE__);

                    words=realloc(words, strings*8);

                    if (words==NULL)
                    {
                        puts("Error 2");

                        return 2;
                    }

                    puts("---Realloc 2 end---\n\n");
                    
                    printf("\n\nMalloc 3 - %d\n", __LINE__);

                    words[strings]=malloc(1);
                    
                    puts("---");

                    if (words[strings]==NULL)
                    {
                        puts("Error 3");

                        return 3;
                    }
                    
                    puts("---Malloc 3 end---\n\n");
                    
                    //printf("\n\n%lu - %x\n\n", sizeof(words[strings]), words[strings]);

                    //words[strings][0]='\0';
                }
            }
            else
            {
                new_line=0;

                printf("%d %d - %c (%x)\n", strings, chars, c, &words[strings][chars]);

                printf("\n\nRalloc 4 - %d\n", __LINE__);

                words[strings]=realloc(words[strings], chars+1);

                if (words[strings]==NULL)
                {
                    puts("Error 4");

                    return 4;
                }
                
                puts("---Realloc 4 end---\n\n");
                
                words[strings][chars]=c;

                chars++;

                //words[strings][chars]='\0';
            }
        }
    }
    
    puts(words[1]);

    return 0;
}
```Right now it's "working" if I run with valgrind, but it gives me the following error on the "Malloc 3" 

```
Malloc 3 - 57
==9378== Invalid write of size 8
==9378==    at 0x400791: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378==  Address 0x51b11d8 is 0 bytes after a block of size 8 alloc'd
==9378==    at 0x4C28254: realloc (vg_replace_malloc.c:525)
==9378==    by 0x400736: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378== 
---
==9378== Invalid read of size 8
==9378==    at 0x4007AB: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378==  Address 0x51b11d8 is 0 bytes after a block of size 8 alloc'd
==9378==    at 0x4C28254: realloc (vg_replace_malloc.c:525)
==9378==    by 0x400736: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378== 
---Malloc 3 end---
```If I just run it without valgrind, the same message from before shows up:

```
*** glibc detected *** ./a.out: realloc(): invalid next size
```Something else that I noticed is that, running on valgrind, the puts near the end of the code prints "Segmentation Fault", but running normaly, it prints the correct string.

Allocating 1 byte for a char * is not really good. It may work in practice, since the 1 is likely to get rounded up to 8 or 16, but valgrind still catches it, as it should.

I suggest you use a sizeof of the appropriate type in all malloc calls, multiplied of course with how many you want.

---

### Post by MadCow108 on 2011-03-09
> **Colgax said:**
> Right now it's like this:
Right now it's "working" if I run with valgrind, but it gives me the following error on the "Malloc 3" 

```
Malloc 3 - 57
==9378== Invalid write of size 8
==9378==    at 0x400791: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378==  Address 0x51b11d8 is 0 bytes after a block of size 8 alloc'd
==9378==    at 0x4C28254: realloc (vg_replace_malloc.c:525)
==9378==    by 0x400736: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378== 
---
==9378== Invalid read of size 8
==9378==    at 0x4007AB: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378==  Address 0x51b11d8 is 0 bytes after a block of size 8 alloc'd
==9378==    at 0x4C28254: realloc (vg_replace_malloc.c:525)
==9378==    by 0x400736: main (in /media/sda3/Users/Douglas/Documents/My Programs/Fit in lines)
==9378== 
---Malloc 3 end---
```If I just run it without valgrind, the same message from before shows up:

```
*** glibc detected *** ./a.out: realloc(): invalid next size
```Something else that I noticed is that, running on valgrind, the puts near the end of the code prints "Segmentation Fault", but running normaly, it prints the correct string.

hint: compile with debug symbols (-g) and the line number will be included in the valgrind report thus you don't need all these printfs

---

