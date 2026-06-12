---
title: "How to generate random 0 and 1 ,also want to generate numbers within a range"
date: 2010-11-26
forum: Programming Talk
---

### Post by fasoulas on 2010-11-26
How can i use rand() in c++ in order to generate numbers between 180 and 245 ,but every time generate a bigger number than the previous one?

I also want to know how can i generate only 0 and 1 in order to use them as boolean true or false??

---

### Post by Tony Flury on 2010-11-26
> **fasoulas said:**
> How can i use rand() in c++ in order to generate numbers between 180 and 245 ,but every time generate a bigger number than the previous one

Um - that isn't random then - and the most numbers you will generate will be 65 before you can't go further.

If you want to do it - the psuedocode will be something like this : 
```

Start = 180
End = 245
Number = 0
While Number < End
   Number = IntRand(End-Start)+ Start
   print Number
   Start = Number+1

```
I am assuming the IntRand( n ) produces an integer between 0 and n

> 
I also want to know how can i generate only 0 and 1 in order to use them as boolean true or false??
I would do this by producing a number between 0 and 7 (for instance), and then do a modulo 2 - so 0,2,4,6 produce a 0 result, and 1,3,5, 7 produce a 1 result.

Your main challenge is to be able to create a random number between 0 and n - i.e. the IntRand function about - assuming that the normal rand gives a number between 0 and 1 (including 0 but not 1) - I think the answer is 

```

Define IntRand( integer n )
   return (int)((n+1) * rand() + 0.5)

```
I think that should work : 

rand() => number from 0 to 0.9999999999
*n => number from 0 to to (n-1) + 0.999999999
+ 0.5 => number from 0.5 to n + 0.4999999999
int => number from 0 to n

---

### Post by Arndt on 2010-11-26
> **fasoulas said:**
> How can i use rand() in c++ in order to generate numbers between 180 and 245 ,but every time generate a bigger number than the previous one?

I also want to know how can i generate only 0 and 1 in order to use them as boolean true or false??

First produce a random number r between 0 and 1: ((double) rand()) / RAND_MAX.

Keep track of which is the minimum number you can accept (call it m, it starts out as 180), and then do (int) (r * (246-m) + 180). I'm assuming that 245 is included.

For 0 or 1, do (int) (2*r). Do not do rand() % 2, because that may have atrocious behaviour (be 1 every second time, for example - completely predictable).

There are better random number generators than 'rand', too, which don't have its problems.

---

### Post by lucasart on 2010-11-26
> **fasoulas said:**
> How can i use rand() in c++ in order to generate numbers between 180 and 245 ,but every time generate a bigger number than the previous one?

I also want to know how can i generate only 0 and 1 in order to use them as boolean true or false??

First, rand() has values between 0 and 32767 so there might be a "granularity effect" which isn't great. Here's a somewhat better rand() with a period of 2^64. In fact rand() is very implementation specific, so it's best to write your own, at least you know what you're doing.
```

typedef unsigned long long U64;

inline U64 rand64()
{
    static U64 seed = 0ULL;
    return seed = seed * 6364136223846793005ULL + 1442695040888963407ULL;
}

```The second point (0 or 1) is trivial: just do
```

rand64() & 1

```As for the first one, it's very simple, just loop and keep the bounds. Of course the upper bound may be reached in which case the sequence will be stationary at the upper bound and not random  anymore...

Of course you can also generate double values within [0,1] interval by doing
```

double(rand64()) / 0xFFFFFFFFFFFFFFFFULL

```

---

### Post by Arndt on 2010-11-27
> **lucasart said:**
> First, rand() has values between 0 and 32767 so there might be a "granularity effect" which isn't great. Here's a somewhat better rand() with a period of 2^64. In fact rand() is very implementation specific, so it's best to write your own, at least you know what you're doing.
```

typedef unsigned long long U64;

inline U64 rand64()
{
    static U64 seed = 0ULL;
    return seed = seed * 6364136223846793005ULL + 1442695040888963407ULL;
}

```The second point (0 or 1) is trivial: just do
```

rand64() & 1

```

Did you read my post? Your generator suffers from precisely that problem: you will get 0,1,0,1,0,1,0,1, etc.

---

### Post by MadCow108 on 2010-11-27
> **lucasart said:**
> First, rand() has values between 0 and 32767 so there might be a "granularity effect" which isn't great. Here's a somewhat better rand() with a period of 2^64. In fact rand() is very implementation specific, so it's best to write your own, at least you know what you're doing.

very very bad idea.

Unless you know exactly what you are doing you are going to screw up badly.
random generators are not trivial. Even the simple ones (like rand() aka linear congruential). Just see the RANDU fiasko.

---

### Post by nvteighen on 2010-11-27
> **lucasart said:**
> First, rand() has values between 0 and 32767 so there might be a "granularity effect" which isn't great. Here's a somewhat better rand() with a period of 2^64. In fact rand() is very implementation specific, so it's best to write your own, at least you know what you're doing.
```

typedef unsigned long long U64;

inline U64 rand64()
{
    static U64 seed = 0ULL;
    return seed = seed * 6364136223846793005ULL + 1442695040888963407ULL;
}

```The second point (0 or 1) is trivial: just do
```

rand64() & 1

```As for the first one, it's very simple, just loop and keep the bounds. Of course the upper bound may be reached in which case the sequence will be stationary at the upper bound and not random  anymore...

Of course you can also generate double values within [0,1] interval by doing
```

double(rand64()) / 0xFFFFFFFFFFFFFFFFULL

```

No, this is so wrong for so many reasons...

1) A static variable in an inline function sounds pointless to me... 
2) It's impossible to get truly random numbers from constants.
3) Nice unsigned long long integer overflows.

---

