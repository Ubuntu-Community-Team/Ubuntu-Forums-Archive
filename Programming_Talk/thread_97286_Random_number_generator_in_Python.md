---
title: "Random number generator in Python?"
date: 2005-11-30
forum: Programming Talk
---

### Post by erik-the-red on 2005-11-30
How would I write a random number generator in Python?

Is it even possible to make a truly random number generator?

---

### Post by Sutekh on 2005-11-30
You can find lots of information on random number generators in Python just using Google.

Keep in mind that most computational random number generators are called *pseudo*-random number generators, because they usually rely on a deterministic algorithm.  For most purposes this should be adequate.

The "truest" random number generators need to use a completely unpredictable process, some use things like atmospheric noise and radioactive sources.  If you want a "true" random number generator, you could give it a try.  In the space eng department at my uni, they were using static from unused radio frequencies to generate random numbers, but that would be quite a project.

**Edit:** Indeed this is actually implemented by the people at [http://www.random.org/]("http://www.random.org/"), who used radio static.  They also have a page where they can generate a large quantity of random numbers for your use.  Check it out.

---

### Post by erik-the-red on 2005-11-30
Thanks!

---

### Post by Sutekh on 2005-11-30
No problem.  Hey, let me know how you go.  I'm just getting into Python (with desklets) and would be interested to see how it goes.  Good Luck.

---

### Post by gord on 2005-11-30
```

import random
print random.random()

```

[linky :) ](http://docs.python.org/lib/module-random.html)

---

### Post by erik-the-red on 2005-12-02
Thanks, gord. Here is my final code:

```

import random
print random.randrange(1,226,1)

```

Works like a charm.

---

### Post by julemel on 2009-05-15
hi, this is a follow on question from the random numbers.
i want to generate random numbers to use in a monte carlo simulation. but the model script is in pcraster. i have the model running 100 times in python but need to generate random numbers to use in the model for each run. 
can anyone help???

---

