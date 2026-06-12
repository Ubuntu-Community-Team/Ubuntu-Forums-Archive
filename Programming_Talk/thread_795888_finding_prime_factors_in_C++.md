---
title: "finding prime factors in C++"
date: 2008-05-15
forum: Programming Talk
---

### Post by StrikerZeroX on 2008-05-15
Hi everyone,

I am trying to write a C++ program that can determine the greatest prime factor of a number. I can figure out how to do this with a number that is small enough to fit in the int variable type. The problem is the assignment calls for me to find the prime factors of an integer that will not fit into the int variable type.

So I tried to make it a double type. This is when I found out that you can't modular a double. Does anyone know another way to find factors with out modular, or is there a way to modular a double?

Thanks in advance.

---

### Post by WW on 2008-05-15
> **StrikerZeroX said:**
>  The problem is the assignment calls for ...
Is this [homework](http://ubuntuforums.org/showthread.php?t=795888)?

> **StrikerZeroX said:**
> 
So I tried to make it a double type. 

This probably won't work.  The **double** data type has only a finite number of digits of precision.  For example, on my computer, this code shows that 10^33 and 10^33+1 are "the same":

**doubletest.cpp**
```

#include <iostream>

int main(int argc, char *argv[])
    {
    double x,y;
    
    x = 1.0e33;
    y = x + 1.0;
    if (x == y)
        std::cout << "They are equal!\n";
    return 0;
    }

```

For very large integers in C++, take a look at the [CLN library](http://www.ginac.de/CLN/).

---

### Post by Can+~ on 2008-05-15
And a [FONT="Courier New"][COLOR="RoyalBlue"]long long unsigned int[/COLOR][/FONT] doesn't cut it?

8 bytes = 8*8 bits

And it really looks like homework

---

### Post by JupiterV2 on 2008-05-15
> **StrikerZeroX said:**
> Hi everyone,

I am trying to write a C++ program that can determine the greatest prime factor of a number. I can figure out how to do this with a number that is small enough to fit in the int variable type. The problem is the assignment calls for me to find the prime factors of an integer that will not fit into the int variable type.

This sounds exactly like problem #3 on [Project Euler]("http://projecteuler.net/index.php?section=problems&id=3").

The 'long double' variable should be large enough to hold a value of ~15 digits. A 'double' variable may be large enough too.

---

### Post by StrikerZeroX on 2008-05-16
It is a homework assignment...It is exactly like Problem 3 on Project Euler. The only thing different is the number. I always thought my professor was lazy...

---

### Post by Npl on 2008-05-16
how big is the number? if it fits in 64 bit, just use a 64-bit integer (int64_t or long long). doubles dont cut it, they arent exact.

If its bigger than 64 bit (or arbitrary size) then you will have to define a class that can deal with bigger numbers and use that.

---

### Post by josaphat on 2010-05-26
Hm... It seems to me using 64 bit int (long long) is VERY slow. Would this be true or is it just a problem with the way you implement?

Edit: also, the number is 600851475143

---

### Post by lostinxlation on 2010-05-27
> **josaphat said:**
> Hm... It seems to me using 64 bit int (long long) is VERY slow. Would this be true or is it just a problem with the way you implement?
 
Edit: also, the number is 600851475143
Imagine you have a calculator that can do the arithmetic operation only on 1 digit numbers, and you are trying to do 33 divided by 3. A lot of operations and storing are required, and it will be slower.

---

### Post by ssam on 2010-05-27
> **josaphat said:**
> Hm... It seems to me using 64 bit int (long long) is VERY slow. Would this be true or is it just a problem with the way you implement?

Edit: also, the number is 600851475143

do you have a 64bit computer/OS

---

### Post by Ty Meador on 2011-07-03
there is a floating point modulus operator, it is contained int <cmath.h> or <math.h> (though this is an older c header file, so i would recommend you use <cmath>) just use
fmod(number, divisor);

---

### Post by Tony Flury on 2011-07-03
> 
there is a floating point modulus operator, it is contained int <cmath.h> or <math.h> (though this is an older c header file, so i would recommend you use <cmath>) just use
fmod(number, divisor); 


The OP is trying to find prime factors of a large integer - the one thing he can't use is a floating point library. As already mentioned floating point arithmetic simply is not precise enough for large integers.

---

### Post by zobayer1 on 2011-07-03
> **JupiterV2 said:**
> This sounds exactly like problem #3 on [Project Euler]("http://projecteuler.net/index.php?section=problems&id=3").

The 'long double' variable should be large enough to hold a value of ~15  digits. A 'double' variable may be large enough too.
64 bit ints are quite sufficient, they can hold upto 20 digits. (i.e. long long int or __int64)

> **josaphat said:**
> Hm... It seems to me using 64 bit int (long  long) is VERY slow. Would this be true or is it just a problem with the  way you implement?

Edit: also, the number is 600851475143
If it seems slow, then your algorithm is slow..
I have solved it years ago, this is my source code, try it... 
```

#include <cstdio>
#include <vector>
using namespace std;

#define MAX 777924
#define LMT 882
#define u64 unsigned long long
#define ifC(x) (flag[x>>6]&(1<<((x>>1)&31)))
#define isC(x) (flag[x>>6]|=(1<<((x>>1)&31)))

int flag[MAX>>6];
int primes[62314];
int total;

inline u64 sq(u64 n) { return n * n; }

void sieve() {
    int i, j, k;
    primes[0] = 2, total = 1;
    for(i=3; i<LMT; i+=2) if(!ifC(i)) for(j=i*i, k=i<<1; j<MAX; j+=k) isC(j);
    for(i=3; i<MAX; i+=2) if(!ifC(i)) primes[total++] = i;
}

void factorize(u64 n, vector< u64 > &V) {
    for(int i=0; i<total && sq(primes[i]) <= n; i++) {
        if(n%primes[i]==0) {
            V.push_back(primes[i]);
            while(n%primes[i]==0) n /= primes[i];
        }
    }
    if(n > 1) V.push_back(n);
}

int main() {
    sieve();
    vector< u64 > factors;
    factorize(600851475143ULL, factors);
    printf("%llu\n", factors[factors.size()-1]);
    return 0;
}
```QUITE FAST. Before blaming properties of a language, try to analyze the complexity of your algorithm. And always leave out doubles and long doubles whenever possible, handling those may need some extra care...

---

### Post by Iowan on 2011-07-03
Thread has been dormant for over a year.

---

