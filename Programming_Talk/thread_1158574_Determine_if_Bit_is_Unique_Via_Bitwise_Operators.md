---
title: "Determine if Bit is Unique Via Bitwise Operators"
date: 2009-05-13
forum: Programming Talk
---

### Post by corngeek on 2009-05-13
Hi.

My question: Given a set of equal sized bitstrings, can you determine if, for each place in the string, there's a single 1 amaongst the bitstrings? (for all you extremely intelligent people who can't be bothered to read my explanation below)

I'm working on a Sudoku AI, implemented in Java (although the binary operations will be universal) As an academic exercise, I decided to implement the solving utilizing bitstrings. Each empty square has an integer that represents the possibilities for that square as a bitstring (ie, 100001100 means that it can be a 9, 4, or 3). This makes it easy to toggle a certain value without searching through an ArrayList or such and squeezes out a few seconds of efficiency. 

The current test I'm working on is what I call "deduction" (as compared to "exhaustion", in which there's only one possible value). If a square is the only one in a column/row/subsquare that contains a particular bit, that must be what the value for that tile is. My problem is determining if a bit is unique within a set of bitstrings. 

For example, if a row has empty squares with the following bitstrings:
100001100
110010101
110001000

I would want it to return 000010101 (all of the unique values, ie, numbers that have only one possibility). That would then be ANDed with each square to see if it has the needed bit and set the value of the tile accordingly.

I've played around for a few days, and the only thing I can come up with is an iterative approach. While this would work and would be efficient, I would like to implement this with bitwise operations (I thought about it, now I have to do it, or it will keep me up at nights ;) ) I hope that's clear enough...

What do you guys think? Given a set of equal sized bitstrings, can you determine if, there exists a single 1 in each place value across the set?

Thanks.

---

### Post by Can+~ on 2009-05-13
**+**: OR
**·**: AND

Truth Table:
n | A | B | C | F(A,B,C)
0 | 0 | 0 | 0 | 0
[COLOR="#CC0000"]1 | 0 | 0 | 1 | 1[/COLOR]
[COLOR="#CC0000"]2 | 0 | 1 | 0 | 1[/COLOR]
3 | 0 | 1 | 1 | 0
[COLOR="#CC0000"]4 | 1 | 0 | 0 | 1[/COLOR]
5 | 1 | 0 | 1 | 0
6 | 1 | 1 | 0 | 0
7 | 1 | 1 | 1 | 0

Canonical Form:
[IMG]http://img.photobucket.com/albums/v517/CanXp/canonical.png[/IMG]

There's your solution, it's pretty much a redefinition of XOR for 3 variables. (Damn, I should reinstall LaTeX*)

Now you can play with bitwise operators, or, as you can see, all single values are powers of two.

A simple test of "Power of two" can be done with:

00100000 (n)
00011111 (n-1) &
00000000

!(n & (n-1)) will be true if a number is a power of two (aka. it has a single 1 bit on it)

If you could rearrange your strings to form vertical strings like:

00000**0**01
10110**1**01
00000**0**01

Another way to get to the same solution, but less practical.


*edit: latexified

---

### Post by corngeek on 2009-05-14
Gotcha. It seems so simple now...

I was assuming XOR was a fundamental operation and didn't even think to break it into ANDs and ORs. Silly me.

I really like the second solution, as I was doing the same thing horizontally for the first test, but as you said, it would be less practical to arrange.

Alright, thanks. I might be able to sleep at night now...

---

