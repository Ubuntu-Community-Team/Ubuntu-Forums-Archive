---
title: "[ C++ ] Need some help with random number generation."
date: 2009-12-10
forum: Programming Talk
---

### Post by Physical Hook on 2009-12-10
The thing is that the first number will never be larger than 2999 ( tough as you can see, there's no such a limit ). Why it is so ?

```
#include <iostream>
#include <cstdlib>
#include <time.h>

using namespace std;

int main(int argc, char *argv[])
{
    srand(time(NULL));
    
    for (int i = 0; i < 10; i++)
    {
        cout << rand() << endl;
    }
    
    return 0;
}
```

```
[COLOR=Red]2948[/COLOR]
19172
8408
25010
6703
30217
12092
18255
30276
32070

```

---

### Post by dwhitney67 on 2009-12-10
This is the output I get when I run your program:
```

1392108083
67852708
1293950936
1340852862
2075467462
213616650
1171714220
1332055271
1766537957
1714784261

```
Btw, this has no bearing on the results, but when programming in C++, use <ctime>, not <time.h>

---

### Post by lisati on 2009-12-10
Possible explanation: the randomize function used is keyed to the time. Different time zones, perhaps.

---

### Post by Physical Hook on 2009-12-10
Ok, I think I still don't get the idea of srand and time(NULL). Now it'll not be larger than 4999 ( not 2999 ).
Can anybody explain what exactly srand does and what is the effect of using time(NULL) as an argument ? Have been reading all kinds of guides on random number generation but still can't get the point ..

---

### Post by lisati on 2009-12-10
> **Physical Hook said:**
> Ok, I think I still don't get the idea of srand and time(NULL). Now it'll not be larger than 4999 ( not 2999 ).
Can anybody explain what exactly srand does and what is the effect of using time(NULL) as an argument ? Have been reading all kinds of guides on random number generation but still can't get the point ..

pseudo-random-number generators, like rand(), work from a preset forumla. srand "seeds" the random number sequence, so you can control where in rand's "list" of random numbers it starts. The time function helps bring randomness into it because each occasion you run time, it will return a different value.

Wikipedia has an article on random numbers here: [http://en.wikipedia.org/wiki/Random_number_generator](http://en.wikipedia.org/wiki/Random_number_generator)

---

### Post by MadCow108 on 2009-12-10
gcc uses a linear congruential generator:
[http://en.wikipedia.org/wiki/Linear_congruential_generator](http://en.wikipedia.org/wiki/Linear_congruential_generator)
thus the first numbers will be strongly correlated if seeded repeatedly with a nonrandom source (e.g. time(NULL), your local time probably just always wraps around to some small value every time, in a few hours it may be different)
so it is essential that you only seed once in your program or else your numbers will be even less random (except you have a true random seed)

the linear congruential generator should not be used for statistical analysis or encryption.
There are better generators for these purposes, like mersenne twister available in e.g. boost

for most other applications its perfectly fine

---

### Post by Wistful on 2009-12-10
[http://ubuntuforums.org/showpost.php?p=7946267&postcount=5](http://ubuntuforums.org/showpost.php?p=7946267&postcount=5)

Please search before posting : [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php) and [http://www.google.com](http://www.google.com)

---

### Post by dwhitney67 on 2009-12-10
> **MadCow108 said:**
> ... your local time probably just always wraps around to some small value every time, in a few hours it may be different)

You lost me with this statement.  The system time, as reported when calling time(NULL), is the number of seconds since the "epoch", which is midnight of 01-Jan-1970.

If the OP has his system clock set to a date sometime during this first day of 1970, then I can understand the numbers he is getting.

Either way, if he obtains the time at this very instant using time(NULL), and repeats the exercise in a few, say 3, hours, the time will be 3*60*60, or 10800, seconds later (barring of course he didn't play with the system clock!)

---

### Post by rahilm on 2009-12-11
Try using:
```

 cout << rand() % 2999 << endl;
```

oops that is for the smaller one

---

### Post by Arndt on 2009-12-11
> **Physical Hook said:**
> The thing is that the first number will never be larger than 2999 ( tough as you can see, there's no such a limit ). Why it is so ?

```
#include <iostream>
#include <cstdlib>
#include <time.h>

using namespace std;

int main(int argc, char *argv[])
{
    srand(time(NULL));
    
    for (int i = 0; i < 10; i++)
    {
        cout << rand() << endl;
    }
    
    return 0;
}
```

```
[COLOR=Red]2948[/COLOR]
19172
8408
25010
6703
30217
12092
18255
30276
32070

```

It somehow looks like the rand() function is treated as if it returned a short int.

What is the value of the preprocessor symbol RAND_MAX?

---

### Post by MadCow108 on 2009-12-11
> **dwhitney67 said:**
> You lost me with this statement.  The system time, as reported when calling time(NULL), is the number of seconds since the "epoch", which is midnight of 01-Jan-1970.

If the OP has his system clock set to a date sometime during this first day of 1970, then I can understand the numbers he is getting.

Either way, if he obtains the time at this very instant using time(NULL), and repeats the exercise in a few, say 3, hours, the time will be 3*60*60, or 10800, seconds later (barring of course he didn't play with the system clock!)

I meant the local time plugged into to generator results in rand wrapping to small values for similar inputs.
a linear congruential generator has a modulo operation in it.
time() itself of course involves no wrapping (until 2038 at least :) )

simple example:
time gives 1000, used as seed:
rand(): (5*1000 + 2) mod 5000 = 2
now execute again one second later: 1001 is seed
(5*1001 + 2) = 7
again a small number although the generator can produce numbers up to 4999
You see the result is not even pseudorandom if you use such a predictable seed again and again
I guess something like that is happening in OP's case

I bet if he tries it now he will get a completely different range of first roll numbers due to the timestamp having changed more.

---

### Post by Physical Hook on 2009-12-11
> **MadCow108 said:**
> I meant the local time plugged into to generator results in rand wrapping to small values for similar inputs.
a linear congruential generator has a modulo operation in it.
time() itself of course involves no wrapping (until 2038 at least :) )

simple example:
time gives 1000, used as seed:
rand(): (5*1000 + 2) mod 5000 = 2
now execute again one second later: 1001 is seed
(5*1001 + 2) = 7
again a small number although the generator can produce numbers up to 4999
You see the result is not even pseudorandom if you use such a predictable seed again and again
I guess something like that is happening in OP's case

I bet if he tries it now he will get a completely different range of first roll numbers due to the timestamp having changed more.

Thank you! Finally something *human readable* :)

---

### Post by dwhitney67 on 2009-12-11
@ the OP

Did the program you originally posted generate the outputted numbers you posted??

Or did those numbers come from another similar program where perhaps you seeded the random number generator with a small number?

As you have read, there are explanations for the results you got; however none of these jive with the program you posted, unless of course your system's date is set somewhere in early 1970.

---

### Post by Physical Hook on 2009-12-11
> **dwhitney67 said:**
> @ the OP

Did the program you originally posted generate the outputted numbers you posted??

Or did those numbers come from another similar program where perhaps you seeded the random number generator with a small number?

As you have read, there are explanations for the results you got; however none of these jive with the program you posted, unless of course your system's date is set somewhere in early 1970.

I took the output right from the console ( which was like 5 seconds after I compiled it ) and I'm sure my system doesn't live in the past.
Are you talking about the fact that the numbers I got are too small ( I see you have way bigger ones there ) ?

---

### Post by dwhitney67 on 2009-12-11
> **Physical Hook said:**
> 
Are you talking about the fact that the numbers I got are too small ( I see you have way bigger ones there ) ?
Yes.

I am not at all familiar with the internals of the srand() code, and what it does with the initial seed value given.  The manpage offers some insight, similar to what MadCow108 wrote about earlier.

But it appears that one's value of RAND_MAX is important.  On my system (within /usr/include/stdlib.h), that value is 2147483647.

The current value reported by my system as the current epoch time is 1260555647.  Thus this probably explains the results I got.

P.S.  time(0), time(NULL), and "date +%s" should in theory report epoch time that is in the ballpark of each other.

---

### Post by grayrainbow on 2009-12-11
The idea of pseudo random generator is to be, well, pseudo random :)
Simply putted seed 1 doesn't exactly mean small result, there's was link in previous post about wiki page on the subject, which is 'a must read'.

Btw, if you want more realism in random numbers, best shot is to just read from /dev/random ;)

---

### Post by Physical Hook on 2009-12-11
> **dwhitney67 said:**
> Yes.

I am not at all familiar with the internals of the srand() code, and what it does with the initial seed value given.  The manpage offers some insight, similar to what MadCow108 wrote about earlier.

But it appears that one's value of RAND_MAX is important.  On my system (within /usr/include/stdlib.h), that value is 2147483647.

The current value reported by my system as the current epoch time is 1260555647.  Thus this probably explains the results I got.

P.S.  time(0), time(NULL), and "date +%s" should in theory report epoch time that is in the ballpark of each other.

Not sure what was wrong but after reinstalling g++ I finally see something more similar to what you say it should be.

```

RAND_MAX: 2147483647
TIMESTAMP: 1260558623
```

```
124906708
1730400448
886383696
951583244
1961108332
708271945
2114952830
436261318
891075609
1834231882
```

---

### Post by MadCow108 on 2009-12-11
is RAND_MAX the maximum number the standard rng can produce
it is only guaranteed by the standard that it is at least 32767 big but mostly it is 31 bit = 2147483647

you probably had an implementation where it was set/configured to the lower value.

---

