---
title: "segmentation fault (core dumped) pops while running a simple program in c"
date: 2015-06-24
forum: Programming Talk
---

### Post by shawon2 on 2015-06-24
Hi, I'm new to ubuntu and a beginner(not an absolute one:wink:)  in programming. I faced a problem while running a simple program in  c(finding the pairs of amicable numbers) though it didn't occure in  windows. The code is as below :

#include <stdio.h>
#include <math.h>
int fct_sum(int x) // function to add the factors of an int
{
    int y, z = 1;
    for(y = 2; y <= sqrt(x); y++) {
        if(x % y == 0) {
            z = z + x / y + y;
        }
    }
    return z;

}
int main()
{
    int x, y, a, b, size = 1000000; // only 10 ^ 6;
    int count = 0;
    char database[size];
    for(y = 2; y < size; y++) {
        database[y] = 'n';
    }
    for(y = 2; y <= sqrt(size); y++) {
        if(database[y] == 'n') {
            for(x = 2; x * y <= size; x++) {
                database[x * y] = 'y';
            }
        }
    }
    for(y = 220; y < size; y++) {
        if(database[y] == 'y') {
            a = fct_sum(y);
            b = fct_sum(a);
            if(b == y) {
                printf("%d\t%d\n", y, a);
                database[a] = 'n';
                count++;
            }
        }
    }
    printf("\nPairs counted : %d\n", count);
    return 0;
}

The code seems pretty simple yet when i run it, the output seems below :

220    284
496    496
1184    1210
2620    2924
5020    5564
6232    6368
8128    8128
10744    10856
12285    14595
17296    18416
63020    76084
66928    66992
67095    71145
69615    87633
79750    88730
100485    124155
122265    139815
122368    123152
141664    153176
142310    168730
171856    176336
176272    180848
185368    203432
196724    202444
280540    365084
308620    389924
319550    430402
356408    399592
437456    455344
469028    486178
503056    514736
522405    525915
600392    669688
609928    686072
624184    691256
635624    712216
643336    652664
667964    783556
726104    796696
802725    863835
879712    901424
898216    980984
947835    1125765
Segmentation fault (core dumped):mad:

But if i declare size as 10 ^ 5, this doesn't occure. So where is my  fault? I searched in net to find a solution to this problem but couldn't  find. In this forum the programs with this same faults were pretty  complicated but this is a childish program:razz:. So what's wrong?Please help.

---

### Post by achuthpnr on 2015-06-24
You are trying to access unallocated memory. To be precise, database[1125765] does not exist, since 1125765>size.

Also be careful about things like declaring the function first and casting the output of sqrt() etc...

---

### Post by trent.josephsen on 2015-06-24
Please use ```
 tags when posting source code. I took the liberty of running your program through "indent -kr":
[code]#include <stdio.h>
#include <math.h>                                          
int fct_sum(int x) // function to add the factors of an int
{   
    int y, z = 1; 
    for (y = 2; y <= sqrt(x); y++) {
        if (x % y == 0) { 
            z = z + x / y + y;
        }
    }
    return z;
}
              
int main(void)
{
    int x, y, a, b, size = 1000000; // only 10 ^ 6;
    int count = 0;
    char database[size];
    for (y = 2; y < size; y++) {
        database[y] = 'n';
    }
    for (y = 2; y <= sqrt(size); y++) {
        if (database[y] == 'n') {
            for (x = 2; x * y <= size; x++) {
                database[x * y] = 'y';
            }
        }
    }
    for (y = 220; y < size; y++) {
        if (database[y] == 'y') {
            a = fct_sum(y);
            b = fct_sum(a);
            if (b == y) {
                printf("%d\t%d\n", y, a);
                database[a] = 'n';
                count++;
            }
        }
    }
    printf("\nPairs counted : %d\n", count);
    return 0;
}
```
achuthpnr is correct about why your program is crashing. I'd like to note that the reason this happens with 10^6 and not 10^5 is because with 10^5, the final pair is (79750, 88730), both of which are *less* than 10^5.

I guess the prime number sieve is there to improve speed? If you're curious, it's not very effective. There are fewer than 13,000 primes under a million; that means that pre-filtering primes lets you avoid calling fct_sum at best 1.3% of the time. On my computer, your original version takes about 68.5 seconds (before crashing). I removed the sieve and just initialized all of database to 'y', then retimed it at about 72 seconds -- only 5% slower. You *can* speed it up dramatically just by removing the call to sqrt() inside fct_sum. Floating-point calculations are not just imprecise; they're typically much slower than integer calculations, and fct_sum is called many many times. Changing that test to "y*y <= x" brought my runtime (crashtime?) down to 20.9 seconds. Obviously performance is not hugely important for little programs like this, but I thought it was an interesting problem.

On a related note, your program may have a bug: fct_sum gives a wrong result when x is square. Doesn't affect the output of this particular program, which is why I said "may". I also notice that your program prints perfect numbers, which means you should either skip them (keeping to the strictest definition of "amicable number") or if not, you should also count 6 and 28, which are the perfect numbers less than 220.

---

### Post by shawon2 on 2015-06-25
Thanks a lot. Yes if I just add 
```
if(a > size) {
     continue;
}
```
the problem is solved.Yeh, i actually didn't care about the perfect numbers and forgot to skip those numbers. Thanks for the suggestions.
trent.josephsen, thanks for pointing me to such a serious problem of the function fct_sum. Yet, it doesn't affect the output but it loses it's name. I solved it adding
```
if(x / y == y) {
   z = z + x;
   continue;
}
```
is there a better way?

---

### Post by trent.josephsen on 2015-06-25
I thought of that at first, too, but doing the test every time through the loop is unnecessary when the only special case is the last value. So it's better to do that one outside the loop:
```
int fct_sum(int x) // function to add the factors of an int
{
    int y, z = 1;
    for (y = 2; y*y < x; y++) {
        if (x % y == 0) {
            z = z + x / y + y;
        }
    }
    if (y*y == x) {
        z += y;
    }
    return z;
}
```

---

### Post by shawon2 on 2015-06-25
very much right. Thanks a lot.

---

