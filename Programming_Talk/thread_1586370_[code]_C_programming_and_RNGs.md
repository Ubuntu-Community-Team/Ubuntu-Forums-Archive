---
title: "[code] C programming and RNGs"
date: 2010-10-01
forum: Programming Talk
---

### Post by nair on 2010-10-01
#include <stdio.h>

int main ()
{[INDENT]      int number;
     int i;
     int run;

     printf("How many numbers?\n");
     scanf("%d", &number);
[/INDENT][INDENT][INDENT]      for(run=0;run<number;run++){

       srand(time(NULL));
       i=rand() % 100;

       printf("%d\n",i);
[/INDENT][/INDENT][INDENT]      }
[/INDENT]}

**********

I want to make some code that takes the input of the user (How many numbers? = number) and generates that number of random numbers (between 0-99).    And I want it to output a different random number each time the 'for loop' executes.  So, if the user inputs number = 5, it will output 5 random numbers that will be different from one another (usually).  Currently, this 'for loop' generates the same 5 numbers with an input of number = 5 because it is seeded using time.  Since the 'for loop' executes 5 times at the same instant, it has the same seed every time, and thus it repeats the same random number 5 times in the output.

I think there are a few ways to fix this code to do what I want it to do.  One way would be to seed it differently, not using time--or using something in addition to time--so that it would be different if the 'for loop' were run multiple times in the same second.  Maybe you can base the time on milliseconds or nanoseconds?  I have no idea.  Another way would be to develop some sort of more complicated random number generator that isn't exclusively based on built-in functions of the C language.  Anyone know what my options are or how to implement them?

---

### Post by schauerlich on 2010-10-01
Just move the call to srand outside your for loop. It only needs to be done once.

---

### Post by nair on 2010-10-01
That works great!

I heard a rumor or saw something on the net that said lower numbers are slightly more favored than higher numbers when using rand and srand (seeded to time).  Is there truth to this, and if there is, can this slight favoring be manipulated somehow?

I'm also curious how to seed this particular RNG to something else besides time, if anyone knows how to do that.

---

### Post by unknownPoster on 2010-10-02
> **nair said:**
> 
I'm also curious how to seed this particular RNG to something else besides time, if anyone knows how to do that.

srand accepts any unsigned int as an argument. As such you can seed it with any integer. In GUI applications, I've used the coordinates of the mouse pointer as my seed. I've also used the process ID as the seed.

The possibilities of seeds is limitless to be honest.

---

### Post by schauerlich on 2010-10-02
> **unknownPoster said:**
> The possibilities of seeds is limitless to be honest.

Well, 2^(8*sizeof(unsigned int)). :)

---

### Post by nair on 2010-10-02
Well, what about the way rand works?  Could rand be skewed somehow in how it works, no matter what the seed is?

Also, is it possible to use multiple seeds in one RNG?

---

### Post by unknownPoster on 2010-10-02
> **schauerlich said:**
> Well, 2^(8*sizeof(unsigned int)). :)

Yes, of course. I meant to say that the number of ways to determine your seed is probably limitless.

> **nair said:**
> Well, what about the way rand works?  Could rand be skewed somehow in how it works, no matter what the seed is?


Well that can be considered one of the classic problems of computer science. It is almost impossible to generate a truly random number quickly, as such most random number generators are considered "pseudo-random". Most random number generators I have seen are formulaic in approach. In order to increase the randomness of output we choose to seed it with "random" data from the environment such as system time, process id, pointer coordinates, etc.

As such I would assume you could make the argument that srand() and rand() are skewed to some extent in that their results are determined by a set algorithm/formula, but I would argue the the effect is negligible in majority of applications.

> 
Also, is it possible to use multiple seeds in one RNG?

You could reseed the RNG with a different value later in the function/code.

As far as the computer science theory I discussed above, I'm just a Senior studying Computer Science, so my understanding of it could be completely wrong. There are many more experienced people here that may be able to correct me or add information.

---

### Post by schauerlich on 2010-10-02
> **unknownPoster said:**
> Yes, of course. I meant to say that the number of ways to determine your seed is probably limitless.

I know, just being snarky. :)

---

### Post by MadCow108 on 2010-10-02
> **nair said:**
> I heard a rumor or saw something on the net that said lower numbers are slightly more favored than higher numbers when using rand and srand (seeded to time).  Is there truth to this, and if there is, can this slight favoring be manipulated somehow?

The lower order bits of rand (=linear congruential generator) have a lower period than the higher bits (depending on parameters of the generator)
But unless you are doing cryptography or statistical analysis this seldom matters.
You could also just decide to use just the higher bits of the output.

if you need a good and fast generator suitable for monte carlo work use e.g. mersenne twister (implemented e.g. in gsl or boost)

---

### Post by nair on 2010-10-02
So, in the example like this one where there are 100 possible values of a random number, 0 through 99, what are the 'lower bits' and 'higher bits'?  If the 'lower bits' are being favored over 'higher bits', would this mean that (using rand to generate random numbers) 0 is more likely than 99?  I'm not familiar with the 'bit' terminology in this context.

Assume we don't know what the seed is, or even that the seed is changing.

Also, if there are some tools out there for testing random number generators, I'd be very interested in experimenting with them.  It seems like it would be fairly easy to test a RNG with some tool or stats program.  Just give it the list of possible values, like 0-99, and then give it some example output generated by the RNG/psuedo-RNG.  Anyone know of a good tool for testing the randomness of randomly generated output?

---

### Post by MadCow108 on 2010-10-02
lower order bits depends on implementation and machine but usually means smaller numbers.

but they are still quite uniformly distributed, just the period may be smaller than for the higher bits.
the period of a rng is the number of numbers you can extract from it before it begins repeating again with the same pattern.

you can easily illustrate the most important concepts by implementing a linear congruential generator yourself (x = (a*x +b) mod m).
just choose some bad parameters and you can create one with very low periods.

donald knuth's bible volume 2 has an chapter on random numbers and their tests.
google should also bring up tons of possibilities
you should also find something here:
[http://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator](http://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator)

---

### Post by nair on 2010-10-03
> **MadCow108 said:**
> lower order bits depends on implementation and machine but usually means smaller numbers.

but they are still quite uniformly distributed, just the period may be smaller than for the higher bits.
the period of a rng is the number of numbers you can extract from it before it begins repeating again with the same pattern.

you can easily illustrate the most important concepts by implementing a linear congruential generator yourself (x = (a*x +b) mod m).
just choose some bad parameters and you can create one with very low periods.

donald knuth's bible volume 2 has an chapter on random numbers and their tests.
google should also bring up tons of possibilities
you should also find something here:
[http://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator](http://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator)

That is all very helpful information.  I'm new to programming, so that is all pretty new to me.   I'll be doing more research on all of those topics you mentioned.   Thank you for all of that.

I've just realized another question I have about 'rand'.  If the code says:

x = rand % 10

I understand that it generates a random number with a range of 0-9.  I was curious if you can change the range after the % to omit certain numbers from the range (ex. go from 0-9 and then 15-20, affectively omitting 10-14).  I was thinking of something that would look something like:

x = rand % 10, 6 + 15

Obviously I made that syntax up--it doesn't compile.  But I haven't found anything online to suggest that this is possible using basic syntax on one line of code.  I'm sure it's possible through some means though.

---

### Post by spjackson on 2010-10-03
> **nair said:**
> I've just realized another question I have about 'rand'.  If the code says:

x = rand % 10

I understand that it generates a random number with a range of 0-9.  I was curious if you can change the range after the % to omit certain numbers from the range (ex. go from 0-9 and then 15-20, affectively omitting 10-14).  I was thinking of something that would look something like:

x = rand % 10, 6 + 15

Obviously I made that syntax up--it doesn't compile.  But I haven't found anything online to suggest that this is possible using basic syntax on one line of code.  I'm sure it's possible through some means though.
rand() returns a value in the range 0..RAND_MAX.

A common way to map that large range onto a smaller range is to use the modulus operator %, as per your example. Note that this does not affect the range of rand(), it simply maps the result onto a smaller range.

There isn't a direct way to ask the modulus operator to map to a discontinuous domain. However, there a few approaches to what you want to do:
```

a)
    int myrand = rand() % 16;
    if (myrand > 9) {
        myrand += 5;
    }

b)
    const int domain_size = 16;
    int domain[domain_size] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 15, 16, 17, 18, 19, 20 };

    int myrand = domain[rand() % domain_size];

c)
    // use switch

```

---

