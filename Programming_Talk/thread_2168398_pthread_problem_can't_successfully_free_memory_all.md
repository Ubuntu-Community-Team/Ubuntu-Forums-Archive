---
title: "pthread problem: can't successfully free memory allocated in a thread"
date: 2013-08-17
forum: Programming Talk
---

### Post by mark allyn on 2013-08-17
Hello everyone,
I am trying to teach myself pthreads and have run into a problem freeing memory allocated in a thread.   In the present instance I am passing a struct to the thread create call as the parameter.  Here's the code:

```

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

typedef struct {
    int dat1;
    int dat2;
    } sdata;
    
void * func (void * x);

int main ( void ){

pthread_t threadID;
sdata d1
sdata *e1;
d1.dat1 = 1;
d1.dat2 = 2;
void * exit_status;


pthread_create(&threadID, NULL, func, &d1);

pthread_join(threadID, &exit_status);
e1=(sdata *)exit_status;

printf("Here's the modified struct first field: %d\n", e1->dat1);
printf("And here's the modified struct second field: %d\n", e1->dat2);
free(exit_status);
return 0;
}

void * func(void * x)
{
sdata * buffer = (sdata *)malloc(sizeof(sdata));
buffer = (sdata *)x;

buffer -> dat1 = 4*(buffer -> dat1);
buffer -> dat2 = 5*(buffer -> dat2);

return (void *)buffer;
} 
```

The program successfully creates and executes the thread and returns the correct answers in the struct, but then crashes (sigbrt) when the free(exit_status) call is executed.  I can't figure out what is going on.

Thanks for any help.

Regards,
Mark Allyn

---

### Post by spjackson on 2013-08-17
> **mark allyn said:**
> 
```

void * func(void * x)
{
sdata * buffer = (sdata *)malloc(sizeof(sdata));
buffer = (sdata *)x;

buffer -> dat1 = 4*(buffer -> dat1);
buffer -> dat2 = 5*(buffer -> dat2);

return (void *)buffer;
} 
```

First you store the address returned by malloc in the variable buffer. Then you throw away that address and set buffer to the address which has been passed in via x. So you are not returning the allocated address from the function.

I think you may mean this instead.
```

* buffer = * (sdata *)x;

```
if I've understood your intent correctly.

---

### Post by mark allyn on 2013-08-17
Good evening spjackson:

I'll try it.  I'll let you know.

Mark

---

### Post by mark allyn on 2013-08-17
Good evening, spjackson,

Yup.  Your fix worked.  Valgrind reports no leaks and the program exits without a complaint.  What I was thinking was that in the thread the first statement (malloc) would do the allocation and that the second statement would assign the x address to the newly created pointer.  It made infinite sense at the time....

Appreciated greatly.

Mark Allyn

---

### Post by dwhitney67 on 2013-08-18
> **mark allyn said:**
>  What I was thinking was that in the thread the first statement (malloc) would do the allocation and that the second statement would assign the x address to the newly created pointer.

Pointers are typically not allocated; however, typically the region of memory (on the heap) that they point to generally are.  This is not to say that all pointers must point to allocated memory; they could also point to something declared on the stack.  In cases such as the latter, there's no need to allocate any memory.  Anyhow, as spjackson was trying to tell you earlier, with the simple assignment, you were ultimately attempting to free memory that was declared on the stack.
```

sdata myStackBuffer;

sdata* ptr1 = &myStackBuffer;    // points to area on the stack

sdata* ptr2 = malloc(sizeof(sdata));    // points to area of memory in the heap

...

free(ptr2);

```

---

