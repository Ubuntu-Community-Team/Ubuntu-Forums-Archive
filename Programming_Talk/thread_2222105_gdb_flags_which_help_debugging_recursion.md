---
title: "gdb flags which help debugging recursion ?"
date: 2014-05-05
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-05
Hello,
 I am actually not cent percent sure of what I want :) (Weird way to start off a post). But I was wondering if there are some gdb flags/options which help debugging recursion.

Since recursion involves multiple stacks(one for each call of the recursive function, where it's local variables are stored), I was wondering if there's something which tells you which stack you are currently in and allows you to see values in other stacks etc.

Thanks.

---

### Post by spjackson on 2014-05-05
> **IAMTubby said:**
> 
Since recursion involves multiple stacks(one for each call of the recursive function, where it's local variables are stored)

Recursion does not involve multiple stacks; each call stores local variables in a new **stack frame** on the same stack. This is no different from non-recursive function calls. You can use all the usual stack commands (up, down, backtrace etc.) in a recursive context as in a non-recursive context.
 
An exception to this would be if tail recursion optimization (TCO) is taking place. You might want to disable TCO, but you generally want to disable all compiler optimizations for debugging.

---

### Post by IAMTubby on 2014-05-05
> **spjackson said:**
> Recursion does not involve multiple stacks; each call stores local variables in a new **stack frame** on the same stack.
Thanks spjackson, is it possible to get debug information about the different stack frames.
For example, let me explain with the code below, please see the printf statement.

```

#include <stdio.h>


int main(void)
{
 fun(3);
}


int fun(int n)
{
 int j = 0;


 if(n == 0)
  return 1;


 for(j=0;j<5;j++)
  **printf("this will be called 5 times for each n. Can I see all the 15 j's simultaneously ? As in, I would like to see n=3's j's when the recursive function is executing at n=2\n");**


 printf("\n");


 fun(n-1);
}

```

Thanks.

---

