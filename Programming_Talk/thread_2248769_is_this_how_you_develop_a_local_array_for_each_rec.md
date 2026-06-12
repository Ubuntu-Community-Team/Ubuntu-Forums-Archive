---
title: "is this how you develop a local array for each recursive invocation?"
date: 2014-10-17
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-17
Hello,
 I'm changing values by reference but would like to have an array local to a function for each recursive invocation of the function. Is this the way to do it? Just thought I'd clarify since generally changing values by reference changes the value irrespective of which function you're doing it in? 
```

#include <stdio.h>
#include <malloc.h>
#include <unistd.h>


int main(void)
{
 fun(0);


 return 0;
}


int fun(int k)
{
 int* mylocalarray;
 int i = 0;


 if(k == 5)
  return 0;


 mylocalarray = malloc(10 * sizeof(int));


 for(i=0;i<10;i++)
  *(mylocalarray + i) = k;


 fun(k+1);


 printf("At k == [%d], array contents : ",k);
 for(i=0;i<10;i++)
  printf("%d ",*(mylocalarray+i));
 printf("\n");


 free(mylocalarray);
}

```

I mean, doing as below, will change the array values across all recursive invocations.
```

#include <stdio.h>
#include <malloc.h>
#include <unistd.h>


int* mylocalarray;


int main(void)
{
 mylocalarray = malloc(10 * sizeof(int));


 fun(0);


 return 0;
}


int fun(int k)
{
 int i = 0;


 if(k == 5)
  return 0;


 for(i=0;i<10;i++)
  *(mylocalarray + i) = k;


 fun(k+1);


 printf("At k == [%d], array contents : ",k);
 for(i=0;i<10;i++)
  printf("%d ",*(mylocalarray+i));
 printf("\n");
}

```

**My question is, is the difference brought about because we're doing a malloc and free for each recursive invocation?**

Thanks.

---

### Post by ofnuts on 2014-10-17
If it's a small array only used in the function, you allocate it on the stack:
```

int array[10];

```

and there won't be no need to deallocate it before the function returns.

---

