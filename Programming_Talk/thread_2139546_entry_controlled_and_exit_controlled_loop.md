---
title: "entry controlled and exit controlled loop"
date: 2013-04-27
forum: Programming Talk
---

### Post by IAMTubby on 2013-04-27
Hello,
For this piece of code, I was expecting that even in the i==5 condition, the block would get executed first, which means i==5 would get printed and then condition gets checked, since do-while is an exit controlled loop. 
But the output I get is the same as that for a while loop and it prints only till i==4. 
```

#include<stdio.h>


int main(void)
{
 int i = 0;
 do
 {
  printf("i==[%d]\n",i);
  i++;
 }while(i<5);


 return 0;
}

```

I know this is a very silly question, but I'm just not able to think through, maybe I need a break. 
Thanks.

---

### Post by Vaphell on 2013-04-27
```

 do
 {
  printf("i==[%d]\n",i); [COLOR="#0000FF"]   <- 4[/COLOR]
  i++;     [COLOR="#0000FF"]<- 5[/COLOR]
 }while(i<5);  [COLOR="#0000FF"] <- 5<5[/COLOR]

```

---

### Post by IAMTubby on 2013-04-27
> **Vaphell said:**
> ```

 do
 {
  printf("i==[%d]\n",i); [COLOR=#0000FF]   <- 4[/COLOR]
  i++;     [COLOR=#0000FF]<- 5[/COLOR]
 }while(i<5);  [COLOR=#0000FF] <- 5<5[/COLOR]

```
Thank you Vaphell, so changing the position of the increment to before the printf solves it. Thank you.
But I was wondering if there is something with which I can print upto 5 using the do-while loop(exit controlled loop), but print only upto 4 using the while loop(entry controlled loop).

---

### Post by dwhitney67 on 2013-04-27
> **IAMTubby said:**
> 
But I was wondering if there is something with which I can print upto 5 using the do-while loop(exit controlled loop), but print only upto 4 using the while loop(entry controlled loop).

Yes there is.  You have already done the first; I'll leave it to you to do the latter... which is even easier to do.

Btw, try to explore the difference between pre-increment and post-increment.  The latter is often used, when in fact in most cases the pre-increment version would suffice.

---

### Post by IAMTubby on 2013-04-29
> **dwhitney67 said:**
> Yes there is.  You have already done the first; I'll leave it to you to do the latter... which is even easier to do.
dwhitney67, I tried thinking through, but I can't help but feel that do-while shows a different output from while only in a condition like this maybe,
```

i = 10;
while(i<10)
{
 printf("helloworld%d\n",i);
 i++;
}

```
*Does not give any output*

as against
```

i = 10;
do
{
 printf("helloworld%d\n",i);
 i++;
}while(i<10);

```
*Prints helloworld10*

**But I was wanting to know if there can be a code snippet where _do-while executes one more iteration of the loop as compared to while._**
Please check attached file : I feel this is not possible because once program control is **within an iteration/loop**, in both the while and do-while cases,condition is being checked for, at the same time as far as program flow is concerned.

Thanks.

---

### Post by alan9800 on 2013-04-29
> **IAMTubby said:**
> dwhitney67, I tried thinking through, but I can't help but feel that do-while shows a different output from while only in a condition like this maybe,
```

i = 10;
while(i<10)
{
 printf("helloworld%d\n",i);
 i++;
}

```
*Does not give any output*

as against
```

i = 10;
do
{
 printf("helloworld%d\n",i);
 i++;
}while(i<10);

```
*Prints helloworld10*

**But I was wanting to know if there can be a code snippet where _do-while executes one more iteration of the loop as compared to while._**
Please check attached file : I feel this is not possible because once program control is **within an iteration/loop**, in both the while and do-while cases,condition is being checked for, at the same time as far as program flow is concerned.

Thanks.change```

i = 10;
while(i<10)
{
 printf("helloworld%d\n",i);
 i++;
}
```to```

i = 10;
while([COLOR=#ff0000]i<=10[/COLOR])
{
 printf("helloworld%d\n",i);
 i++;
}
```and you'll get the output.

---

### Post by dwhitney67 on 2013-04-29
> **IAMTubby said:**
> 
**But I was wanting to know if there can be a code snippet where _do-while executes one more iteration of the loop as compared to while._**

The application will only do what you have told it to do, not necessarily what you wish it to do.  How do you expect to enter the while-loop if you setup the condition to fail before even one iteration is allowed?

A while-loop always checks the condition first, whereas a do-while loop checks the condition at the conclusion of the block of code.  You are guaranteed at least one iteration in a do-while loop; not so with a while-loop.

For example:
```

int i = 0;

do
{
    printf("You will see this once.\n");
} while (i > 0);

while (i > 0)
{
    printf("You will never see this output.\n");
}

```

---

### Post by IAMTubby on 2013-05-01
> **dwhitney67 said:**
> 
A while-loop always checks the condition first, whereas a do-while loop checks the condition at the conclusion of the block of code.  You are guaranteed at least one iteration in a do-while loop; not so with a while-loop.

Thanks for the reply,dwhitney67 :)

---

