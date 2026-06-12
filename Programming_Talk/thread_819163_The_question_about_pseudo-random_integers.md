---
title: "The question about pseudo-random integers"
date: 2008-06-05
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2008-06-05
This is my program about the random number
#include<stdio.h>
#include<time.h>
#include<stdlib.h>
int main()
{
        time_t seed;
        seed=time(NULL);
        printf("%i\n",rand());
        printf("%i\n",seed);
	return 0;
}

The "seed" will be the time of my system from January 1st,1970.
The rand() function returns a pseudo-random integer between 0 and RAND_MAX.But it always be "1804289383".
When I add a line,the "rand()" can be a random number. 
int main()
{
        time_t seed;
        seed=time(NULL);
	srand(seed);
        printf("%i\n",rand());
        printf("%i\n",seed);
	return 0;
}

I want to ask why?What does the function void srand(unsigned int seed) do?

And I also saw one sentence in man srand.That is:
"If no seed value is provided, the rand() function is automatically seeded with a value of 1."
Why not the function rand() comes a vale of 1?When can it comes the value of 1?

---

### Post by Zugzwang on 2008-06-05
Those random number generators don't really provide random numbers. In fact, they use some algorithms that provide a series of number that looks random (However, it looks like you already knew that).

A basic algorithm works as follows:
[LIST]
[*]Take the last random number generated
[*]Multiply it with some big prime number and add some big prime number
[*]Truncate the result to RAND_MAX (prime as well)
[/LIST]

I don't think that this is actually the generator used in the C libs, but it gives you a rough idea how it works. 

This algorithm always needs the last number generated. However, when running it for the first time, you don't have any. That is why there is a seed. It is used as the first number. If you only initialize the generator one, the seed can also be used to repeat a run of your program (good for debugging).

For more on pseudo-random number generators visit Wikipedia: [http://en.wikipedia.org/wiki/Pseudorandom_number_generator]("http://en.wikipedia.org/wiki/Pseudorandom_number_generator")

---

### Post by sq377 on 2008-06-05
[IMG]http://www.metasploit.com/users/hdm/tools/debian-openssl/pmeo9hcjp7aw9.jpg[/IMG]

I thought man srand explained it fairly well:
> The srand() function sets its argument as the seed for a new  sequence of pseudo-random integers to be returned by rand(). These sequences are repeatable by calling srand() with the same seed value.

It sets the seed for rand() to something other than 1.

Also, it's alot simpler just to call

srand(time(NULL));

---

### Post by AZzKikR on 2008-06-05
I am a big fan of the Mersenne Twister RNG. Perhaps it's viable for you to look into that.

---

### Post by RIchard James13 on 2008-06-05
Pseudo-Random is perhaps a misnomer. Maybe pre-selected out of order numbers or something. I use them in game programming because I know they will always be the same on every run, and I can make my game behave in the same way every time. If I want the game to alter behaviour I set the seed to the time the player presses some key. It still is not truly random but the player never sees the same game over and over again.

---

### Post by ppradeep on 2010-03-19
[I]how to use Mersenne Twister RNG 
[/I]

---

### Post by MadCow108 on 2010-03-19
understanding the standard rng is best done by looking the generating function:

x_(n+1) = (a * x_n + b) mod m
where a, b and m are constant parameters

as you see you need to provide a starting number x_0
from this number the function will generate a series of nearly uniformly distributed values between 0 and m - 1 (if the parameters are chosen correctly, for bad parameters google RANDU)
Also you see it will always generate the same series of numbers if x_0 (aka seed) is the same.

the seed is provided by the function srand.

this generator is called a linear congruentual generator, with good parameters it is good enough for most cases and it is very fast.
Only for encryption or statistical stduies you should chose a different one, like the already mentioned mersenne twister which provides very good randomness (for a pseudorandom generator) and is rather fast.
But it is comparably harder to understand how that one works.

---

