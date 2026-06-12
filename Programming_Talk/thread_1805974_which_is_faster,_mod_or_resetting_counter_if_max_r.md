---
title: "which is faster, mod or resetting counter if max reached"
date: 2011-07-16
forum: Programming Talk
---

### Post by jmartrican on 2011-07-16
Hello,

Which do you think is faster...

ver-1
```

object[++someCounter mod someMaxValue].doSomething();

```

or

ver-2
```

if (++someCounter >= someMaxValue) {
    someCounter = 0;
}
object[someCounter].doSomething();

```

Assume someCounter will grow into the tens of thousands in ver-1.  I know ver-1 looks more elegant and that's what I am doing now, but I was concerned about doing mod on larger numbers.  I mean tens of thousands is not even that large.  The someMaxValue will be small, like no greater than 5.  So maybe you will see something like 100000 mod 5 in worst case scenario.

I am being lazy... I should run tests and maybe I will but wanted to see what you guys thought.


thanks
jose

---

### Post by NovaAesa on 2011-07-16
Your version one will have a bug because someCounter will eventually overflow and wrap around (unless you are checking for this somewhere else or using a language supporting arbitrarily large ints).

If I was to hazard a guess which would be faster, I would say version 1. There are no branches, so this allows better instruction pipelining in the CPU. If it's a bottle neck in your program though, I would test both cases.

---

### Post by cipherboy_loc on 2011-07-16
The version one may be faster if you do the following:

```

int counter = 0;
int max = 422;
newvalue = 0;
while (someCondition) {
  counter = (counter + 1) % max;
  newvalue += numbers[counter];
}


```

---

### Post by jmartrican on 2011-07-17
NovaAesa,
Thanks for the response man, i didnt notice that glaring bug.


cipherboy_loc,
Pretty slick man, never thought about making my counter equal to the outcome of the mod.... its so simple too.  I think I got my solution.


thanks
jose

---

### Post by ziekfiguur on 2011-07-17
Though NovaAesa is right that the first one is better because of pipelining, an assignment is a **lot** faster that the division needed to compute the mod. So, if your language supports a ternary operator that would probably be even better than cipherboys solution.

---

### Post by jmartrican on 2011-07-17
ziekfiguur,

The lang is javafx.  

So its possible to do...
```

counter = if (counter >= max) 0 else (counter + 1);

```

This has 1 boolean expression, one assignment, one addition (most of the time), anything else?.

Where as this one...
```

counter = (counter + 1) mod max;

```
has an assignment, an addition, and a mod.

Yeah i see your point.  If it really boils down to which is faster the boolean expression over the mod than I presume the boolean expression wins out.

thanks
jose

---

### Post by ziekfiguur on 2011-07-17
I don't know about javafx, but in normal java you would have to use:
```
counter = (counter >= max) ? 0 : (counter + 1);
```
and not use an if statement as that will result in a pipelining delay.

---

### Post by jmartrican on 2011-07-17
In javafx you have to have that IF there.  I do not know how it is compiled... I'm hoping the compiler knows what's going on and compiles efficiently.

Javafx 2.0 just came out and its now more of a library than its own scripting language.  But i'm still on version 1.3 for my current project, which is its own language.  Its pretty cool BTW.

---

### Post by ve4cib on 2011-07-17
Generally-speaking, using the if-statement will result in faster code.  But the difference is not terribly noticeable.

The reasoning behind this is that the mod is only ever necessary once; when you roll around from the end back to the beginning of the range.  So if you're looping through an array of 100,000 items, 99,999 times you will be doing an unnecessary modulo operation, eating up 99,999 * n clock cycles.

The if-statement approach requires checking the condition (usually only 1 clock cycle), and a branch (1 or 2 clock cycles).  Once through every loop you'll add in another few cycles to do the assignment.

Determining which is ultimately faster depends on the CPU and what operations it supports.  If the CPU doesn't support division (common on a lot of RISC processors) then division is implemented as a series of shits and subtractions, eating up many, many clock cycles, versus the 3-4 for the branching version.

---

