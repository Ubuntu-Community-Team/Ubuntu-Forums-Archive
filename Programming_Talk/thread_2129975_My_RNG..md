---
title: "My RNG."
date: 2013-03-27
forum: Programming Talk
---

### Post by EmanresuusernamE on 2013-03-27
I'm pretty much just a vaporware writer right now, and I was writing a game about a month ago and decided: I need a Random Number Generator.  I was going to start with rand() and saw mixed reviews on how well it did creating random numbers.  After researching some more, they all have their own various issues that I didn't like.  I also saw that creating an RNG was really difficult to do, but I decided to try and write one anyway.  It's pretty much in an alpha stage right now and the results it is returning look pretty random to me.  I've made images that look like random static to me and they pretty much look like the top image of this website: [http://boallen.com/random-numbers.html]("http://boallen.com/random-numbers.html")

Does anyone know of a good way to test the results from an RNG?  I've tried Dieharder and it passed all of the tests, but I read somewhere that bad RNGs can also pass all of the tests in Dieharder.  I've also used a tester from the NIST, but I'm not fully sure how to use it yet, (or where it puts the results).  Are there any other tests out there that I can run in parallel to these three tests, (Visual, Dieharder and NIST)?

Thanks.

---

### Post by ofnuts on 2013-03-28
[http://en.wikipedia.org/wiki/Pseudorandom_number_generator#BSI_evaluation_criteria](http://en.wikipedia.org/wiki/Pseudorandom_number_generator#BSI_evaluation_criteria)

IMHO, the chances that you come up with a PRNG that is better than existing ones are quite small..

---

### Post by trent.josephsen on 2013-03-28
What properties of existing PRNGs didn't you like?

Realistically, for games and most things short of cryptography, even a weak PRNG is normally random enough. Even visually obvious patterns like odd, even, odd, even... won't be obvious in a game that shuffles cards or has monsters drop random loot. And few implementations of rand() generate such an obvious pattern.

But as far as I know the only real test of quality is to provide the source and see how long it takes for someone to find an exploit. This is why [cryptographically secure PRNGs](http://en.wikipedia.org/wiki/CSPRNG) are proven by reduction to a mathematical problem that is known "difficult" to solve. In particular, the Blum-Micali algorithm mentioned on that page depends on the difficulty of the discrete logarithm problem, which is hard to solve using conventional methods, but may in the future be solvable in much less time using Shor's algorithm on a quantum computer. (True randomness, like you get from a hardware RNG, is actually impossible -- not just difficult -- to crack.)

---

### Post by EmanresuusernamE on 2013-03-30
> **ofnuts said:**
> IMHO, the chances that you come up with a PRNG that is better than existing ones are quite small..Look, if I wanted to listen to trolls, I would have gone to 4chan or some place similar.

> **trent.josephsen said:**
> What properties of existing PRNGs didn't you like?

Realistically, for games and most things short of cryptography, even a weak PRNG is normally random enough. Even visually obvious patterns like odd, even, odd, even... won't be obvious in a game that shuffles cards or has monsters drop random loot. And few implementations of rand() generate such an obvious pattern.

But as far as I know the only real test of quality is to provide the source and see how long it takes for someone to find an exploit. This is why [cryptographically secure PRNGs](http://en.wikipedia.org/wiki/CSPRNG) are proven by reduction to a mathematical problem that is known "difficult" to solve. In particular, the Blum-Micali algorithm mentioned on that page depends on the difficulty of the discrete logarithm problem, which is hard to solve using conventional methods, but may in the future be solvable in much less time using Shor's algorithm on a quantum computer. (True randomness, like you get from a hardware RNG, is actually impossible -- not just difficult -- to crack.)While I don't really know a good deal about all of the PRNGs out ther, with most PRNGs you give it a seed and then you start using it for random numbers.  After looking at some of their code, they also use hard coded numbers to change the value of the random numbers being returned.  With my RNG, you will be able to seed it with the same thing over and over again and you won't get the same results from it when you set its options correctly.  This is one of the things I wanted, so it isn't a flaw.  And yes, there will be a way to make it where you give it a seed and a predictable stream will come out of it.

Realistically I play a lot of games and I tend to notice patterns more often than I'd like to see.

True randomness from a hardware RNG?  I find that hard to believe. A few sites agree with me, hardware RNGs all suffer from the same issue: Their components can all fail over time.  It is very difficult to tell if a hardware RNG is actually working properly or not and then there's also the fact that outside forces can also affect the results that are coming from the RNG.  I could very well be completely wrong about this, but if you have an audio HRNG and you put something like a fan next to it, could that not cause it to start showing a pattern?

---

### Post by ofnuts on 2013-03-30
> **EmanresuusernamE said:**
> Look, if I wanted to listen to trolls, I would have gone to 4chan or some place similar.
I'm not trolling, I'm realistic. If rand() were so bad and if $random_programmer could come up with  a better PRNG in a matter of months it would have been replaced eons ago. And I'm not dismissing the possibility that you could be the next Turing/Dijkstra/Von Neumann (I said "quite small").

---

### Post by trent.josephsen on 2013-03-30
> **EmanresuusernamE said:**
> With my RNG, you will be able to seed it with the same thing over and over again and you won't get the same results from it when you set its options correctly.
That would be adding to the entropy pool, not seeding. A seed by definition contains all the information necessary to recreate a sequence of numbers.

> Realistically I play a lot of games and I tend to notice patterns more often than I'd like to see.
Patterns in games tend to come from poor game design, not poor quality of randomness. (That is, when the pattern isn't just imagined to begin with.) NetHack uses plain old rand() and I've never heard of anyone successfully exploiting that.

> True randomness from a hardware RNG?  I find that hard to believe. A few sites agree with me, hardware RNGs all suffer from the same issue: Their components can all fail over time.  It is very difficult to tell if a hardware RNG is actually working properly or not and then there's also the fact that outside forces can also affect the results that are coming from the RNG.  I could very well be completely wrong about this, but if you have an audio HRNG and you put something like a fan next to it, could that not cause it to start showing a pattern?
You're right, hardware RNGs are not perfect. But they are the only source of true randomness. Computer programs are by nature deterministic. The output of a PRNG does not exhibit randomness because if you can recreate the state of the machine you can always predict with 100% certainty what number it will output next. They work because of how difficult it is to deduce the state of the machine.

You say "It is very difficult to tell if a hardware RNG is actually working properly"; that is an understatement. It is impossible to tell if a HRNG is working properly, because any sequence of numbers could just as well be random (= working properly) or non-random (= fan interfering with the microphone). That's why real HRNGs only generate a few bits of entropy for many thousands of bits of data collected; you might not be able to get rid of the periodic noise (fan humming), but you can mix it with aperiodic noise (air turbulence, jitter, cat knocks the fan off the shelf) until you're *pretty sure* any exploitable source of non-randomness is gone.

(There are sources of entropy in computer hardware, too. You can time keypresses and mouse jitter and stuff like that, which is how /dev/random works. *(edit -- this is not exactly right, /dev/random is actually just a throttled version of /dev/urandom. See MadCow's link.)* You can inject this entropy periodically into a PRNG, so as to foil anyone trying to guess the state; that is how /dev/urandom works and the principle behind CSPRNGs.)

I've gone on long enough.

---

### Post by MadCow108 on 2013-03-31
here  is an interesting article about hardware random number generators and how they work in linux:
[http://lwn.net/Articles/525204/](http://lwn.net/Articles/525204/)

there are measures in place to ensure the generator is not flawed, but as always when dealing with random numbers, nothing is certain.

---

