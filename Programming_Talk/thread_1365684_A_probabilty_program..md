---
title: "A probabilty program."
date: 2009-12-27
forum: Programming Talk
---

### Post by rahilm on 2009-12-27
Hi,
I have been reading Frederick Mosteller's Fifty Challenging Problems in Probabilty and i came across this problem.
> On the average, how many times a die must be thrown until one gets a  6?sure, the answer is 6. But i wanted to verify (my knowledge of C). I wrote up this program:
```

/*Average number of throws for a dice to show 6*/
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define NO 1000000
int throw()
{
    int i,j=0;
    for(i=1;j!=6;i++)
        j=rand()%6+1;
    return i;
}
int main()
{
    int i,sum=0;
    srand((unsigned)time(NULL));
    for(i=0;i<NO;i++)
        sum+=throw();
    printf("%f",(float)sum/NO);
    return 0;
}


```What i find uncomfortable, is that almost everytime, the answer is close to 7 and not 6.
i tried it 5 times to get:
```

7.006066
6.997382
7.003007
6.996360
7.012870

```So my question is , is it correct? is the random number generator supposed to give results according to probability theory (in this case it doesn't)? I tried many more probablity problems, they all agreed to theory. I hate probability, and this is the only way to make it interesting for me.

---

### Post by Some Penguin on 2009-12-27
> **rahilm said:**
> Hi,
I have been reading Frederick Mosteller's Fifty Challenging Problems in Probabilty and i came across this problem.
sure, the answer is 6. But i wanted to verify (my knowledge of C). I wrote up this program:
[code]
int throw()
{
    int i,j=0;
    for(i=1;j!=6;i++)
        j=rand()%6+1;
    return i;
}



The order of execution in a for loop is:

1.  Initial clause.  (In this case, setting i = 1).
2.  Second clause -- Test condition (j != 6 ?)
   2a.  Test passes: 
          Execute loop body.
          Execute third clause (i++)
          Return to step 2 (re-evaluate test condition).
   2b.  Test fails:
          Terminate immediately without executing body or third clause.


Consider what happens with your code if it rolls 6 on the very first time. What value does i start with before you make even a single roll, and what value does it end up with when you return?

---

### Post by rahilm on 2009-12-27
> **Some Penguin said:**
> 
Consider what happens with your code if it rolls 6 on the very first time. What value does i start with before you make even a single roll, and what value does it end up with when you return?
Ahaa!!!Gotcha!!This is the improved code
```

/*Average number of throws for a dice to show 6*/
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define NO 1000000
int throw()
{
    int i,j=0;
    for(i=1;1;i++)
    {
        j=rand()%6+1;
        if(j==6)
            break;
    }
    return i;
}
int main()
{
    int i,sum=0;
    srand((unsigned)time(NULL));
    for(i=0;i<NO;i++)
        sum+=throw();
    printf("%f",(float)sum/NO);
    return 0;
}

```

Its working now:here are 5 outputs.
```
5.996133
6.002068
5.997853
5.990558
6.008882
```

Lesson learnt:You should not mess with chance.
Thnx Some Penguin

---

### Post by Can+~ on 2009-12-27
```
plot(dbinom(1, 1:36, 1/6), type='o')
```

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-7.png[/IMG]

The probability peaks in 6 actually (Binomial distribution, varying the size of the sample), it lowers later because you probably already achieved the success event in the previous attempts.

---

### Post by mali2297 on 2009-12-28
> **Can+~ said:**
> ```
plot(dbinom(1, 1:36, 1/6), type='o')
```

The probability peaks in 6 actually (Binomial distribution, varying the size of the sample), it lowers later because you probably already achieved the success event in the previous attempts.

If you want to plot the distribution of the number of throws until you get the first six, the relevant R code is
```

plot(1:36,dgeom(0:35, 1/6), type='o')

```
*dgeom(i-1,1/6)* uses the probability function of a geometric distribution to calculate the probability that the first six will come in the *i*th throw. In the plot, you can observe that the peak is not at the average 6 but at 1. (Sorry, but I cannot give you a screenshot.)

---

### Post by CptPicard on 2009-12-28
Actually, nevermind ;)

---

