---
title: "Randomizing Your Application (with RNGs)"
date: 2010-09-19
forum: Programming Talk
---

### Post by nair on 2010-09-19
Forgive me if this is a nab question, but I know nothing about random number generators or designing applications.

Let's say you want to design an application that is going to have several different features within it that will have some sort of random element associated with them.  Maybe you've got some settings that you want to randomize, maybe you've got some features of the AI that you want to randomize, maybe you've got some color schemes or other aesthetic features that you want to randomize.

From an overall design point-of-view, which of the following two approaches generally makes more sense:

(1) Build a centralized random number generator which generates actual numbers or letters--something similar to a license key--which is extremely complex and random, but is not actually useful in isolation.  Then plug the random values created by this RNG into the different features of the application that need to be randomized.  These features do not have to be numbers-based.  Again, maybe you want to randomize the AI or a list of names or some series of events, etc.  In other words, take a number (which was generated randomly) and use it to randomize something or some feature that is not necessarily a number.

(2) Build a separate random number generator for each individual component of an application which you want to randomize.  You might have to make 5 or 10 or 50 RNGs (I'm calling them RNGs but they might not have to deal with numbers at all) which are unique and are geared towards a specific feature and purpose.  You are not having to create some individually useless random number first in order to get anything done--maybe this saves a step.

I'm not sure if these two approaches are all that different or would have that much impact on your design either way.  I could be making something out of nothing here, but again, I emphasize my ignorance regarding this topic.

---

### Post by Wybiral on 2010-09-19
You generate a random number, with a sufficient RNG, and apply that to your problem. If you need to randomly sort a list, you'd use some random shuffle algorithm (Fisher-Yates, for instance) which utilizes the random numbers generated from the RNG. For AI, there may be some actions performed based on the outcome of that RNG. For random text/strings you'd just convert the numbers to characters. I don't know of any cases where a generic random integer or floating point couldn't be applied to randomize the situation.

A proper random number generator will work in these cases. And most languages are equipped with a sufficient RNG, so implementing one is rarely an issue in day-to-day development.

Other than that, I'm not sure what you mean by "having to create some individually useless random number first in order to get anything done"

---

### Post by nair on 2010-09-19
Say you have a list of five strings: Apple, Orange, Banana, Grape, Pear.

I can set up my application to just give me a random one of those strings...in which I will receive a value like 'Pear' for example.  I want a random value on that list, and that is what I receive, pretty simple.

Or I can setup my application to give me some really long, complex random number...but I don't really want a long random number ultimately, I want a value in that list to be provided to me randomly.  So then I have to take that long, complex random number...give it back to the application, essentially saying "hey, here is your random number--now give me one of the five strings based on this number".

In either case, all I really wanted was  Apple, Orange, Banana, Grape, or Pear, provided to me randomly.  That long, complex number has no use other than to randomize the values on my list, and I was wondering if using an approach involving this long, complex number would either be beneficial (like it might provide a more robust level of randomness) or would just provide an extra, somewhat useless step in the process.  Maybe it is just as easy using out-of-the-box programming language functions, like rand() in the C language for example, to create very randomized data--and you don't need to code some random number directly into every feature of an application that you want to be randomized.

---

### Post by schauerlich on 2010-09-19
With rand(), you can use modulo to only get random numbers in a certain range.

[http://www.cplusplus.com/reference/clibrary/cstdlib/rand/](http://www.cplusplus.com/reference/clibrary/cstdlib/rand/)

```
( value % 100 ) is in the range 0 to 99
( value % 100 + 1 ) is in the range 1 to 100
( value % 30 + 1985 ) is in the range 1985 to 2014
```

If you know the length of the array, you can use rand() % length_of_array to get a random index, and then get an element. Higher level languages usually provide a way to get a random element from their standard containers, ie python's random.choice(some_seq)

---

### Post by nair on 2010-09-19
The information in the link states that lower numbers are slightly more likely than higher numbers, meaning that the distribution of random numbers will not be even if this code (in the example) is used.

What are some possibilities for getting a psuedo RNG to have evenly distributed outcomes in the C language?  Should rand() be avoided or just used some other way?

---

### Post by schauerlich on 2010-09-19
Unless you're doing cryptography or something, rand() will probably be sufficiently random.

EDIT: of course, make sure to seed it with something like the system time. See [srand()](http://www.cplusplus.com/reference/clibrary/cstdlib/srand/)

---

### Post by MadCow108 on 2010-09-19
gsl provides a wide range of random number generators for C:
[http://www.gnu.org/software/gsl/manual/html_node/Random-Number-Generation.html](http://www.gnu.org/software/gsl/manual/html_node/Random-Number-Generation.html)

mersenne twister is usually a good choice if you need good pseudorandom numbers with good performance.

But mostly the linear congruential generator provided by rand() is enough

---

### Post by Some Penguin on 2010-09-20
Or if you're running an on [online poker site]("http://www.cigital.com/papers/download/developer_gambling.php") or other business where there's profit in finding flaws in your PRNG.

Normally, 'tho, things like reproducibility and platform-independence are more important.  The first is useful for test cases (seeding your PRNG so that your test case behavior /should/ be stable until you break something else), while the latter is something to pay attention to for anything that assumes that multiple machines will be in sync (such as, say, multiplayer RTSes).

---

