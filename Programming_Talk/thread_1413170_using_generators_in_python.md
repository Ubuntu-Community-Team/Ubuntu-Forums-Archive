---
title: "using generators in python"
date: 2010-02-22
forum: Programming Talk
---

### Post by astrakhan on 2010-02-22
here is a beginner's question. the following is supposed to generate prime numbers:

```

def primes(p=2):
    while True:
        for n in range(2,p):
            if p % n == 0:
                p += 1
                primes(p)
        z = p
        p += 1
        yield z

```

it works but also lets some non-primes through, look:
2 3 5 7 11 13 17 19 23 **27** 29 31 **35** 37 41 43 47 53 59 61 67 71 73 79 83 **87** 89 **95** 97
thanks
why? why it lets 35 though but it filters out 15? confused…

---

### Post by ssam on 2010-02-22
your algorithm seems a bit odd. you should not need to recurse (have the generator call its self).

try:
start p at 2
set is_prime to true
loop from 2 to p
if you find a factor, set is_prime to false
after that loop yield p if is_prime is still true
then increment p

then you can try to make it faster by breaking out of the inner loop as soon as you find a factor, or by only check against previously found primes.

---

### Post by astrakhan on 2010-02-22
thanks, still very much learning  :D

```

def primes(p=2):
    while True:
        flag = 1
        for n in range(2,p/2):
            if p % n == 0:
                flag = 0
                break
        if flag == 1:
            yield p
        p += 1

```

...that'll do for now, got too much homework!

---

