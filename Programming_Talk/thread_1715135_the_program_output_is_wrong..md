---
title: "the program output is wrong."
date: 2011-03-26
forum: Programming Talk
---

### Post by lester b on 2011-03-26
Good day to all!

My code apparently does not work on Ubuntu but works on Windows. I tried to use Kubuntu but with the same effect.

Here is the dumb don version of the code:

```


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define stringOf(expr) (#expr)

void *xmalloc(size_t size)
{
    void *ptr = malloc(size);
    if(ptr==NULL)
    {
        perror("");
        exit(EXIT_FAILURE);
    }
    return ptr;
}

void *xrealloc(void *ptr, size_t size)
{
    void *temp = realloc(ptr, size);
    if(temp==NULL)
    {
        perror("");
        exit(EXIT_FAILURE);
    }
    return temp;
}

char *cpy(const char *source)
{
    char *dest = malloc(sizeof(*dest));
    char *temp = NULL;
    int iter = 0;
    int size = 1;

    while(source[iter]!='\0')
    {
        if(iter==size-2)
        {
            size<<=1;
            temp = xrealloc(dest,sizeof(*dest)*size);
            dest = temp;
        }

        dest[iter] = source[iter];
        iter++;

    }
    dest[iter]='\0';
    temp = xmalloc(sizeof(*temp)*iter);
    strcpy(temp, dest);
    free(dest);
    dest = temp;
    return dest;
}

int main(void)
{
    int dimen[] = {3,4, 5};
    int *intPtr = xmalloc(sizeof(*intPtr));
    int *copyOfDimen = xmalloc(sizeof(*copyOfDimen)*3);
    char *s = stringOf(const char *const);
    char *copyOfS = cpy(s);

    for(*intPtr=0;*intPtr<3; (*intPtr)++)
    {
        copyOfDimen[*intPtr] = dimen[*intPtr];
    }
    printf("%s %d\n", s, strlen(s));
    printf("%s %d\n",copyOfS,strlen(copyOfS));

    return 0;
}


```

Here is the supposed output:
```

const char *const 17
const char *const 17

```

Here is the actual output:
```

const char *const 17
const char * 13

```

I thought there was something wrong on the compiler so I installed gcc-4.5 and compile the program with it but the problem still persist. On Windows, I used Mingw gcc-4.5 to compile and run the program and the problem somehow vanished.

When I debug the program, I found out that malloc somehow modify copyOfS from the 13th index.

My compile command is "gcc -Wall -Wextra -pedantic -g" and my OS version is 10.10 if that helps.

---

### Post by GeneralZod on 2011-03-26
> **lester b said:**
> 
```


char *cpy(const char *source)
{
    char *dest = malloc(sizeof(*dest));
    char *temp = NULL;
    int iter = 0;
    int size = 1;

    while(source[iter]!='\0')
    {
        if(iter==size-2)
        {

```


Well, have you tried debugging it, at all? Here's a hint: How many times will the condition "if(iter==size-2)" be true?

---

### Post by MadCow108 on 2011-03-26
also your malloc before the (quite useless) strcpy is wrong

the two bugs mentioned are detected by valgrind:
```

==12791== Invalid write of size 1
==12791==    at 0x4007F0: cpy (test.c:44)
==12791== Invalid read of size 1
==12791==    at 0x4C2987A: __GI_strcpy (mc_replace_strmem.c:313)
==12791==    by 0x400835: cpy (test.c:50)

```
use his tool first on every non-trivial problem

---

### Post by lester b on 2011-03-26
> **GeneralZod said:**
> Well, have you tried debugging it, at all? Here's a hint: How many times will the condition "if(iter==size-2)" be true?

Well, that solves the problem. I didn't notice that during the first test on the condition, the value is false. I just concentrate on malloc changing the value pointed by copyOfS. 

Sorry for wasting your time. Next time, I read the code thoroughly. But thanks for the help.

> **MadCow108 said:**
> also your malloc before the (quite useless) strcpy is wrong

the two bugs mentioned are detected by valgrind:
```

==12791== Invalid write of size 1
==12791==    at 0x4007F0: cpy (test.c:44)
==12791== Invalid read of size 1
==12791==    at 0x4C2987A: __GI_strcpy (mc_replace_strmem.c:313)
==12791==    by 0x400835: cpy (test.c:50)

```
use his tool first on every non-trivial problem

I add the malloc there because I noticed that after the program loops out and call malloc, it change the content of dest. 

Thanks for recommending valgrind. It gonna be quite useful to me. Also, sorry for wasting your time on this trivial problem.

:P

---

