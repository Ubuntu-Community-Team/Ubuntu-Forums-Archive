---
title: "C++: Rand Returns Same Int"
date: 2012-10-19
forum: Programming Talk
---

### Post by Kodeine on 2012-10-19
Salutations!

So I'm trying to get a random number but it keeps returning three. I asked in ##C++ on ubuntu.irc and they said it had to be at the very top of main(). Currently it's the second line in main() and it still happens.

```
int main() 
    {
    
    int IntNumber,IntGuesses;
    IntNumber = rand() % 10;//It can't go any higher
```

---

### Post by dwhitney67 on 2012-10-19
You have to seed the random number generator.  Typically programmers do this with a large number, such as the one returned by the time() function.

```

**srand(time(0));**
...

int randomNum = rand() % 1000;   // result is number from 0 to 999, inclusive

```


P.S.  Include <ctime> for the time() function.

---

### Post by Tony Flury on 2012-10-22
> **Kodeine said:**
> Salutations!

So I'm trying to get a random number but it keeps returning three. I asked in ##C++ on ubuntu.irc and they said it had to be at the very top of main(). Currently it's the second line in main() and it still happens.

```
int main() 
    {
    
    int IntNumber,IntGuesses;
    IntNumber = rand() % 10;//It can't go any higher
```

Whoever told you that is just plain wrong - you can geneate andom numbers at any point in your code. The reason it provides the same number is that rand() is a pseudo random number generator - i.e. it uses a formula (based on an initial value - the seed) - and that seed is always the same when a program starts. To get a different sequence - you use srand to set a new seed. Using time(0) for instance (as suggested by dwhitney67)should almost 100% ensure an different sequence each time the progam starts.

The feature of generating a known predictable "random" sequence is incredibly useful - imagine :
1) Driving a test sequence of 1000s of tests - where the set of tests is defined by one number (i.e the seed)
2) Generate a complex data set (like the landscape for a game for instance) - you just make sure you know the seed for that landscape and you can reproduce the landscape in a predicatble order, and you can generate millions of items of data from a single number.

---

