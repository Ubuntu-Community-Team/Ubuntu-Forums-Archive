---
title: "Random number generation in repeated simulations"
date: 2007-03-20
forum: Programming Talk
---

### Post by WebDrake on 2007-03-20
I'm writing some code for simulations which will repeat the same process (but with different starting conditions) many times over.  This is serial code, not parallel.

I'm wondering about the use of random numbers in these simulations.  Should I just set up one random number generator and let it run all the way through, or is it preferable to start with a different seed for each simulation (e.g. by generating a sequence of seeds with another random number generator, as one might for parallel simulations)?

Thanks,

     -- Joe

---

### Post by LotsOfPhil on 2007-03-20
The usual way it is done is to seed the random number generator with the time in milliseconds, or something.

If you run your code and then generate on more random number to be the seed for the next run, that will work too. The only thing is that if you start with the same seed, you'll get the same sequence of numbers every time you run it. I would use the clock.

Make sure you use a small increment of time. If your code takes less than a second to run and you seed with seconds, you'll get repeats.

---

### Post by Ubuntist on 2007-03-20
It's very handy for debugging purposes to use the same seed every time.

---

### Post by Mirrorball on 2007-03-20
Use one random number generator for each run and **save the seed** with the results because you might need it to replicate the simulation later.

---

### Post by Mr. C. on 2007-03-20
man urandom
man random

MrC

---

### Post by WebDrake on 2007-03-21
Thanks to all for replies. :KS

I think I probably wasn't clear enough in stating what I was interested in.  Obviously I use separate seeds each time I run the program, usually taking the time for this, and save the seed when I exit.

The problem is this.  Each simulation has the (rough) form,
```

for i = 1 to N
        PLAY_GAME(i)
endfor

average over results of the GAMES

```

The question is, do I generate one seed for one rng and let it go all the way through---with each GAME picking up the "random" sequence where the last left off---or is it better to generate a separate seed for each GAME inside the for loop?

That is,
```

seed_rng(newseed)
for i = 1 to N
        PLAY_GAME(i)
endfor

```

or,
```

for i=1 to N
        seed_rng(a different seed each time round)
        PLAY_GAME(i)
endfor

```

I would normally do the former but started wondering if that would build in correlations between runs.

---

### Post by Ubuntist on 2007-03-21
Use the first.

---

### Post by Mirrorball on 2007-03-21
I would generate only one seed too. You will always get the same sequence of simulations for each seed, which is simpler for debugging and if you ever need to run it again.

---

### Post by WebDrake on 2007-03-21
> **Mirrorball said:**
> I would generate only one seed too. You will always get the same sequence of simulations for each seed, which is simpler for debugging and if you ever need to run it again.

Actually, that's not as big a problem as it might seem because there are ways to deal with that, for example by having a "master" rng which generates seeds for the "local" ones inside the loop (good so long as the master rng uses a different algorithm).  Or you can use seed, seed+1, seed+2 .... which is easier for debugging.

---

### Post by Mirrorball on 2007-03-21
Then the seeds are just another pseudorandom number, why bother changing it?

---

### Post by WebDrake on 2007-03-22
> **Mirrorball said:**
> Then the seeds are just another pseudorandom number, why bother changing it?

I just started wondering after investigating a bit the use of threads.  If in the above pseudocode PLAY_GAME() spawns a thread, then you *have* to have separate seeds for each one.  I wondered whether there might be an advantage to doing this in general in order to avoid correlations, but I agree with you, probably not.

---

