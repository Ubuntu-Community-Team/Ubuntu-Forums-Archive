---
title: "Help with this equation/program"
date: 2010-06-18
forum: Programming Talk
---

### Post by makuab on 2010-06-18
Im trying to make a program that calculates the amount of time required to get a certain skill to a certain level.

I looked for the formula to determine the amount of XP needed for a given level.

[img]http://images.wikia.com/wikitex/images/c/ce/cea/0c35159ec08535e346288841cce731.png[/img]

Im new to python and programming in general, can an equation like this even be used in python?

I dont understand this formula, can someone explain it?

from [http://runescape.wikia.com/wiki/Skills](http://runescape.wikia.com/wiki/Skills)

---

### Post by simeon87 on 2010-06-18
That's a summation, see [Summation](http://en.wikipedia.org/wiki/Summation) for what this notation means. After that, you can implement it in Python with a for loop.

---

### Post by StephenF on 2010-06-18
```

def xp_for_level(lev):
    return sum(n / 4 + 75 * 2 ** (n / 7) for n in range(1, lev))

```
You know about functions yet, right?

---

### Post by makuab on 2010-06-18
I dont understand functions at all

---

### Post by simeon87 on 2010-06-18
> **makuab said:**
> I dont understand functions at all

Just let us know if you have questions.

---

### Post by DanielWaterworth on 2010-06-18
> **makuab said:**
> I dont understand functions at all

Try this. Open up a python shell, (by typing 'python' in a terminal) and copy in the following:
```
def xp_for_level(lev):
    return sum(n / 4 + 75 * 2 ** (n / 7) for n in range(1, lev))
```Then type:
```
xp_for_level(10)
```And it'll print out the xp for whatever level you put in place of 10.

---

