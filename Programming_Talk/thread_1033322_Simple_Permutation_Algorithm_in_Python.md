---
title: "Simple Permutation Algorithm in Python"
date: 2009-01-07
forum: Programming Talk
---

### Post by sofiankrt on 2009-01-07
Hey!

I've been working on this problem for a few days now (I'm a student, and we have exams, no time at *all* for programming!) and I've managed to find a logical algorithm for generating all the possible permutations for a given set (a clumsy and confused one, though, but it works, I think).

1. starting from the last two elements and working your way to the left:
    i. switch the last two elements
    ii. switch the first and last letters of the last three elements
    iii. switch the last two elements
    iiii. switch the last element with the third to last...

And so on and so forth...

eg. "ABC"

Switch last two: ACB

Switch third with last: BCA

Switch last two: BAC

Third with last: CAB

Switch last two: CBA

And this generates all the possible permutations for ABC. For ABCD, you would do the same for the last three for every letter, and so on.

Kludgy, I know, but it was the only thing I could think of.

I actually wrote a *very* clumsy implementation in Python, and had problems with the syntax, something like:
[PHP]permutations += [set][/PHP]
would give a completely different answer from:
[PHP]permutations += set[/PHP]
so in a fit of rage I permanently deleted the file...

But I'm ready to write it again, if this is the simplest algorithm possible (but I doubt it).

So now I have two choices:

a. find an easier to implement and more elegant solution (if there is one, just give me a hint, I'll try to figure it out myself)
b. rewrite my clumsy implementation and try to figure out why it doesn't work

Should I just stick with my algorithm or is there a simpler one? Any tips would be greatly appreciated.

---

### Post by monkeyking on 2009-01-07
check this

[http://www.cut-the-knot.org/do_you_know/AllPerm.shtml](http://www.cut-the-knot.org/do_you_know/AllPerm.shtml)

might help

---

