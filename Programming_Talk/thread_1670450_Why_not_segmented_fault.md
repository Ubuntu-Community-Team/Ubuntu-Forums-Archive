---
title: "Why not segmented fault?"
date: 2011-01-18
forum: Programming Talk
---

### Post by c2tarun on 2011-01-18
```

#include<stdio.h>

void main()
{
int a[5];
int i;
for(i=0;i<5;i++)
    a[i]=0;
printf("%d ",a[7]);
}

```

in the above program. I allocated only 5 memory spaces for the array. On printing the 7th element I am getting the garbage value. Even when I tried to edit the value of a[7] then also it compiled perfectly and printed the edited value. I think compiler should give a SEGMENTATION FAULT on this. Can anyone please explain me this strange behavior.
Thanks

---

### Post by worksofcraft on 2011-01-18
> **c2tarun said:**
> ```

#include<stdio.h>

void main()
{
int a[5];
int i;
for(i=0;i<5;i++)
    a[i]=0;
printf("%d ",a[7]);
}

```

in the above program. I allocated only 5 memory spaces for the array. On printing the 7th element I am getting the garbage value. Even when I tried to edit the value of a[7] then also it compiled perfectly and printed the edited value. I think compiler should give a SEGMENTATION FAULT on this. Can anyone please explain me this strange behavior.
Thanks

No, segmentation fault means that the memory management hardware detected an attempt to access memory outside what has been allocated to your application.

Local variables are stored on the stack which has loads of space incase you need more variables later on... so chances are there is plenty left beyond your array that is still allocated for your application.

p.s. infact you might be able to access variable "i" as were it a[5]

---

### Post by c2tarun on 2011-01-18
> **worksofcraft said:**
> No, segmentation fault means that the memory management hardware detected an attempt to access memory outside what has been allocated to your application.

Local variables are stored on the stack which has loads of space incase you need more variables later on... so chances are there is plenty left beyond your array that is still allocated for your application.

p.s. infact you might be able to access variable "i" as were it a[5]


Thanks

---

### Post by Tony Flury on 2011-01-19
Also even if you declared such a small array on the heap (eg as a global), the chances are that the OS has allocated a reasonable chunk of memory for your programs data it is more efficient to allocate a programme memory in reasonable size chunks, so stepping outside the array may well not cause a seg fault, as you will still be inside the allocated memory for your program.

---

### Post by Arndt on 2011-01-19
> **c2tarun said:**
> ```

#include<stdio.h>

void main()
{
int a[5];
int i;
for(i=0;i<5;i++)
    a[i]=0;
printf("%d ",a[7]);
}

```

in the above program. I allocated only 5 memory spaces for the array. On printing the 7th element I am getting the garbage value. Even when I tried to edit the value of a[7] then also it compiled perfectly and printed the edited value. I think compiler should give a SEGMENTATION FAULT on this. Can anyone please explain me this strange behavior.
Thanks

Others have explained the reason, but I'll add that the compiler will not detect the problem - it's at runtime that a segmentation fault or other problems may appear.

---

