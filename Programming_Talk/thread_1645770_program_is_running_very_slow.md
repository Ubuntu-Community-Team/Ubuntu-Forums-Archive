---
title: "program is running very slow"
date: 2010-12-15
forum: Programming Talk
---

### Post by c2tarun on 2010-12-15
here is the problem I was solving [http://www.codechef.com/problems/COINS/](http://www.codechef.com/problems/COINS/)


my program:
[php]
#include<stdio.h>
#define MAX(X,Y) X>Y?X:Y

long int check(int n)
{
    long int m[3];
    while(n>11)
    {
        m[0]=check(n/2);
        m[1]=check(n/3);
        m[2]=check(n/4);
        return (m[0]+m[1]+m[2]);
    }
    return n;
}

int main(void)
{
    long int m[3];
    long int n;
    long int sol;
    while(scanf("%ld",&n) != -1)
    {
        m[0]=check(n);
//        m[1]=check(n);
//        m[2]=check(n);
        sol=MAX(m[0],n);
        printf("%ld\n",sol);
    }
}
[/php]here is one solution posted by someone else: [http://www.codechef.com/viewplaintext/28717](http://www.codechef.com/viewplaintext/28717)


here working logic of both the programs are same (mine logic is very little bit different but that is not in terms of number of steps both the program have same number of steps), but my program is running very slow and the other program is damn fast :( why so?

if anyone want to check the speed run both the program and give the input  745745845
output will the  745745845 only

---

### Post by XPeter on 2010-12-15
The reason why the other program is faster is because it uses a large array (almost 10 MB) to save the result of getNoOfCoins for each input. So if the result is already calculated it just uses that value and does not have to call getNoOfCoins recursively. This saves a lot of computations.

For the input 745745845 your program calls check 735615673 times. The other program for the same input calls getNoOfCoins 17110 times. As you can see it is a huge difference.

---

### Post by c2tarun on 2010-12-15
> **XPeter said:**
> The reason why the other program is faster is because it uses a large array (almost 10 MB) to save the result of getNoOfCoins for each input. So if the result is already calculated it just uses that value and does not have to call getNoOfCoins recursively. This saves a lot of computations.

For the input 745745845 your program calls check 735615673 times. The other program for the same input calls getNoOfCoins 17110 times. As you can see it is a huge difference.

Thanks a lot :)
I didn't notic it.

---

