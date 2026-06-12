---
title: "problem with a simple program using realloc"
date: 2008-08-09
forum: Programming Talk
---

### Post by kboy on 2008-08-09
Hi, I'm pretty new to the programming world.
i've tried to build a simple program that to read numbers into a dynamically allocated array, and then print the entire array.

here is the code:

```
#include <stdio.h>
#include <stdlib.h>

void processOutOfMemory();


int main()               //reads numbers until -1 is entered.
{
    int *num, *newNum;
    int currNum, i, arrSize;

    printf("Please enter numbers one by one:\n");

    arrSize = 1;
    num = malloc(sizeof(int));
    if(num == NULL)
        processOutOfMemory();

    for(i = 0; scanf("%d", &currNum), currNum != -1; i++, arrSize++)
    {
        num[i] = currNum;
        newNum = realloc(num, arrSize * sizeof(int));

        if(newNum == NULL)
            processOutOfMemory();
        else
            num = newNum;
    }

    printf("Your numbers are: ");    //printing the array
    for(i = 0; i < arrSize; i++)
        printf("%d ", num[i]);

    return 0;
}


void processOutOfMemory()
{
    printf("out of memory\n");
    exit(1);
}

```



when i start the program, i start to enter the numbers one by one.
when i reach the 4th number the program stops with a bunch of error messages:


```
Please enter numbers one by one:
5
6
9
4
*** glibc detected *** ./hello: realloc(): invalid next size: 0x09dee008 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d2f803]
/lib/tls/i686/cmov/libc.so.6(realloc+0x10b)[0xb7d3175b]
./hello[0x8048530]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cd8450]
./hello[0x8048461]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:06 327239     /home/fibo/Projects/hello/bin/Debug/hello
08049000-0804a000 rw-p 00000000 08:06 327239     /home/fibo/Projects/hello/bin/Debug/hello
09dee000-09e0f000 rw-p 09dee000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7cc1000-b7cc2000 rw-p b7cc1000 00:00 0 
b7cc2000-b7e0b000 r-xp 00000000 08:05 894266     /lib/tls/i686/cmov/libc-2.7.so
b7e0b000-b7e0c000 r--p 00149000 08:05 894266     /lib/tls/i686/cmov/libc-2.7.so
b7e0c000-b7e0e000 rw-p 0014a000 08:05 894266     /lib/tls/i686/cmov/libc-2.7.so
b7e0e000-b7e11000 rw-p b7e0e000 00:00 0 
b7e11000-b7e1b000 r-xp 00000000 08:05 876608     /lib/libgcc_s.so.1
b7e1b000-b7e1c000 rw-p 0000a000 08:05 876608     /lib/libgcc_s.so.1
b7e1c000-b7e1d000 rw-p b7e1c000 00:00 0 
b7e1d000-b7e40000 r-xp 00000000 08:05 894274     /lib/tls/i686/cmov/libm-2.7.so
b7e40000-b7e42000 rw-p 00023000 08:05 894274     /lib/tls/i686/cmov/libm-2.7.so
b7e42000-b7f2a000 r-xp 00000000 08:05 229837     /usr/lib/libstdc++.so.6.0.9
b7f2a000-b7f2d000 r--p 000e8000 08:05 229837     /usr/lib/libstdc++.so.6.0.9
b7f2d000-b7f2f000 rw-p 000eb000 08:05 229837     /usr/lib/libstdc++.so.6.0.9
b7f2f000-b7f35000 rw-p b7f2f000 00:00 0 
b7f45000-b7f49000 rw-p b7f45000 00:00 0 
b7f49000-b7f4a000 r-xp b7f49000 00:00 0          [vdso]
b7f4a000-b7f64000 r-xp 00000000 08:05 876563     /lib/ld-2.7.so
b7f64000-b7f66000 rw-p 00019000 08:05 876563     /lib/ld-2.7.so
bf950000-bf965000 rw-p bffeb000 00:00 0          [stack]
Aborted

```


i need some help to solve this or an alternative solution to the program.
thanks!

---

### Post by nvteighen on 2008-08-09
You first allocated num with malloc(), with arrSize = 1. OK. Then, you entered the loop, realloc'ed... with arrSize still being 1 (so, you didn't make the array grow!), because the (i++, arrSize++) part in the loop is executed only **after the for-loop had finished**. So, in summary: you were always one step behind the real size you needed... you were dancing on the dangerous moods of undefined behaivor, writing to memory not really allocated by you... and then reading them crashed the whole thing... heap corruption and libc complaining.

Why did you do that, because of a mistake: you never initialized num. So, you were forced to malloc() it first, before the loop, force arrSize to be 1 (completely unpractical; always start counting by 0... it's the convention!) and couldn't take advantage of a subtle feature of realloc(): if the pointer is NULL, realloc() turns itself into malloc()! (and, if size is 0, realloc() acts like free()).

Ah, and you forgot to free() your memory.

Also, I replaced all your C++ style comments (//) into pure C style comments (/* */)... Just to preserve language purity ;) (use what you want, of course). And also did a tweak that may help you when moving further in C (scoping variables and restrict them to the loop they work).

But, anyways, it seems you are very comfortable with pointers. If you're a programming newbie in general, you have understood them, not something most people in your situation (for some strange reason...) achieve.

[PHP]
#include <stdio.h>
#include <stdlib.h>

void processOutOfMemory(void);


int main(void)
{
    printf("Please enter numbers one by one:\n");
    
    int *num = NULL; /* ALWAYS initialize pointers!! If you don't have the value
                      * yet, use NULL (or 0, it's just a matter of style). */
    
    /* More style issues: I like to declare things as nearest as possible to its
     * use instead of having them all at the beginning; newer C standards allow 
     * this. */
    int i;
    int arrSize = 0;
    int currNum = 0;
    for(i = 0; scanf("%d", &currNum), currNum != -1; i++)
    {
        int *newNum = realloc(num, ++arrSize * sizeof(int));
        /* realloc() acts as malloc() if source pointer (the first parameter) is
         * NULL. Now you see why we have to initialize pointers? :) So, the 
         * malloc() you had in your code was useless. And you might ask why I
         * declare the buffer pointer here: just because it won't be used 
         * outside the loop. */ 

        if(newNum == NULL)
            processOutOfMemory();
        else
        {
            num = newNum;
            num[i] = currNum; /* Moved here: we are sure if everything is fine
                               * only if the code has reached this line. */
        }
    }
    
    /* newNum dies here (RIP). Try to access it and it you won't be able; in 
     * larger programs, scoping variables properly can be really helpful. */

    printf("Your numbers are: ");    /* Printing the array. */
    for(i = 0; i < arrSize; i++)
        printf("%d ", num[i]);
        
    free(num); /* ALWAYS free() your dynamically allocated memory!!! 
                * As you passed all memory addresses from newNum to num, you 
                * have to free() num, not newNum. */

    return 0;
}


void processOutOfMemory(void)
{
    printf("out of memory\n");
    exit(1);
}
[/PHP]

---

### Post by Bachstelze on 2008-08-09
[font="Courier New"]realloc[/font] *always* returns a [FONT="Courier New"]void[/FONT] pointer, regardless of the pointer type you gave it in input. Therefore, in this case, you must conver it into an [FONT="Courier New"]int[/FONT] pointer before you can use it. For example, replace

```
newNum = realloc(num, arrSize * sizeof(int));
```

with

```
newNum = (int*) realloc(num, arrSize * sizeof(int));
```

And yes, there is also an indices mistake. Here's my version:

[PHP]#include <stdio.h>          
#include <stdlib.h>         

void processOutOfMemory();


int main()               //reads numbers until -1 is entered.
{                                                            
    int *num = NULL, *newNum = NULL;                         
    int n = 0, arrSize = 0;                                  
    int i;                                                   

    printf("Please enter numbers one by one:\n");

    while(1)
    {       
        scanf("%d", &n);
        if(n == -1)     
            break;      

        arrSize += 1;
        newNum = realloc(num, arrSize * sizeof(int));

        if(newNum == NULL)
            processOutOfMemory();
        else                     
        {                        
            num = (int*) newNum; 
            num[arrSize - 1] = n;
        }                        
    }                            

    printf("Your numbers are: ");    //printing the array
    for(i = 0; i < arrSize; i++)                         
        printf("%d ", num[i]);                           

    free(num);
    return 0;
}            


void processOutOfMemory()
{                        
    printf("out of memory\n");
    exit(1);                  
}                           [/PHP]

---

### Post by kboy on 2008-08-09
thanks for replies! :)

---

### Post by nvteighen on 2008-08-09
> **HymnToLife said:**
> 

```
newNum = realloc(num, arrSize * sizeof(int));
```

with

```
newNum = (int*) realloc(num, arrSize * sizeof(int));
```


Uhm... yes. It's not quite necessary in modern compilers, as you're storing the (void *) pointer into an (int *), with no dereferencing at all. Data types in C are just length offsets when **accessing** memory and the length is already set by the target variable. The problem would be if you declared newNum as (void *). Then, of course, you have to cast it whenever you use it.

But, as programming languages are languages, are there's tradition involved in language usage, you'll usually see the cast written before realloc(), malloc() and calloc() (off-topic: I usually prefer calloc() over malloc(), it initializes memory to zero and has a nicer syntax). Even myself write it always as HymntoLife pointed.

> Here's my version:

[PHP](...) [/PHP]


Nice one, showing a bit more structured programming. A loop takes care of all input, and just "breaks" when -1 enters. That solves lots of headaches

---

