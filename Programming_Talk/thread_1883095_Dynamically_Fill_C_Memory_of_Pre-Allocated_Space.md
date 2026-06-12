---
title: "Dynamically Fill C Memory of Pre-Allocated Space"
date: 2011-11-18
forum: Programming Talk
---

### Post by JCoster on 2011-11-18
Hi,
My background is originally Java but am starting to get a bit onto C now...
I want to pre-allocate a continuous block of space for 1000 integers in memory.  I then want to go through a while loop and populate this integers with random data by using the offset in memory.  I can't use an array for this as in practice the number of integers I wish to store is much higher.  
Here is what I have so far, however, I can't work out where I'm going wrong...

```

int memorySpace = malloc(1000 * sizeof(int));

int i;
for (i=0;i<1000;i++)
{
   // get the address of the memory space, and add space for the next int
   int *offset = &memorySpace + (sizeof(int)*i);

   offset = *some_random_int*;
}

```

Thanks for help in advance.
JC

---

### Post by karlson on 2011-11-18
> **JCoster said:**
> Hi,
My background is originally Java but am starting to get a bit onto C now...
I want to pre-allocate a continuous block of space for 1000 integers in memory.  I then want to go through a while loop and populate this integers with random data by using the offset in memory.  I can't use an array for this as in practice the number of integers I wish to store is much higher.  
Here is what I have so far, however, I can't work out where I'm going wrong...

```

int memorySpace = malloc(1000 * sizeof(int));

int i;
for (i=0;i<1000;i++)
{
   // get the address of the memory space, and add space for the next int
   int *offset = &memorySpace + (sizeof(int)*i);

   offset = *some_random_int*;
}

```

Thanks for help in advance.
JC

Multiple issues with the code, which can be made simpler like this:
```

int *memorySpace = (int *)malloc(1000 * sizeof(int));

int i;
for (i=0;i<1000;i++)
{
    memorySpace* = [i]random_int*;
}

```

If you insist on using pointers to do this then it should be done like this:
```

void *memorySpace = malloc(1000 * sizeof(int));

int i;
for (i=0;i<1000;i++)
{
    int *dest =(int *)(memorySpace + (i * sizeof(int)));
    *dest = *random_int*;
}

```

I think this should make it clearer.

---

### Post by 3Miro on 2011-11-18
+1 to karlson. His first method is the technically correct way to do this. The second method is good to understand how pointers work, although direct assignment to a pointer from int should be avoided.

---

### Post by Bachstelze on 2011-11-18
> **karlson said:**
> 
If you insist on using pointers to do this then it should be done like this:
```

void *memorySpace = malloc(1000 * sizeof(int));

int i;
for (i=0;i<1000;i++)
{
    int *dest =(int *)(memorySpace + (i * sizeof(int)));
    *dest = *random_int*;
}

```

I think this should make it clearer.

Line 6 should be:

```
    int *dest =(int *)(memorySpace + i);
```

Another approach is

```

int *p = malloc(1000*sizeof(int));
int *sp = p;

for (int i=0; i<1000; i++) {
    *sp = random();
    sp++;
}
```

It is good because the processor does not have to compute the address from the base pointer all the time. Of course, with such simple code, most compilers will optimize karlson's code to this, but in more complicated situations, the compiler might not always "figure out" the optimization.

*EDIT:* Also you need to read about pointer arithmetic. Incrementing a pointer by n increments the actual address by n times the size of the pointed type.

---

### Post by karlson on 2011-11-18
> **Bachstelze said:**
> Line 6 should be:

```
    int *dest =(int *)(memorySpace + i);
```


If memorySpace was an int * then you'd be correct.

> 
*EDIT:* Also you need to read about pointer arithmetic. Incrementing a pointer by n increments the actual address by n times the size of the pointed type.

+1.

---

### Post by Bachstelze on 2011-11-18
> **karlson said:**
> If memorySpace was an int * then you'd be correct.

True. But for my defense, you can't do pointer arithmetic on a void* (because void has no size). ;)

---

### Post by karlson on 2011-11-18
> **Bachstelze said:**
> True. But for my defense, you can't do pointer arithmetic on a void* (because void has no size). ;)

+1 on that. :)

---

### Post by JCoster on 2011-11-20
Great, thanks a lot for all your help- really appreciate it!  Will read up a little more on pointer arithmetic- was getting stuck on when I can increment it and when I need to add a specific value to it.

Cheers

---

