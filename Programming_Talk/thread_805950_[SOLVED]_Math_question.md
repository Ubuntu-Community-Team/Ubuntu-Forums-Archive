---
title: "[SOLVED] Math question"
date: 2008-05-24
forum: Programming Talk
---

### Post by achelis on 2008-05-24
Hi.

I'm looking for a way to calculate the number of different combinations from a given "set".
The set could look like this (a, a, b) which would yield the following different combinations:
(a,a,b),(a,a),(a,b),(a),(b),() = 6 different combinations

I'm pretty sure there is a formula for calculating these kinds of things, but I've been unable to find it :/ (Like if all elements are different it would be 2^n where n is the number of elements)

Hope it makes sense? and that someone can point me in the right direction :)

---

### Post by CptPicard on 2008-05-24
The number of sets in the powerset of n elements is 2^n. Think of binary numbers, and each digit signifying if something is in the particular set of the powerset or not...

In the case where you want to exclude subsets that are the same, it's probably a bit more difficult... I'll have to think of it..

---

### Post by Bichromat on 2008-05-24
A clue :
[http://en.wikipedia.org/wiki/Combinations](http://en.wikipedia.org/wiki/Combinations)

---

### Post by slavik on 2008-05-24
just to note: {a,a,b} is not a valid set, a set can only contain one instance of an item.

---

### Post by achelis on 2008-05-24
@slavik: True, but what would you call it then - a list ?

@Bichromat: Thanks, but I'm not sure that's the answer, will have to look at it some though...

@CptPicard: Yup, that's exactly what I'm trying to figure out - corrected the n² to 2^n  - thanks.

---

### Post by smartbei on 2008-05-24
In your case, the 'a' has actually 3 different possibilities, not two: There can be any of 0,1,2 'a's. The 'b' has 2 possibilities - 0, 1. This gives us 3*2=6 options. 

Therefore think of a way to enumerate over all the different pairs for two "digits", where the first digit can hold the numbers [0,1,2] and the second [0,1]. Converting this to an actual set is trivial.

---

### Post by CptPicard on 2008-05-24
> **achelis said:**
> @slavik: True, but what would you call it then - a list ?

It's a "multiset" that I think you're dealing with, and want to find the number of unique multiset subsets?

Well... consider it like this... if you've got like x a's and y b's and z c's, you can pick a's for your result in x+1 ways, b's in y+1 ways... so you can have (x+1) * (y+1) * (z+1) different unique multiset subsets of a,b,c... just multiply the amount+1 of each item you've got. It's an extension of the 2^n approach where there are *two* ways to choose one item (either it is in the set or it is not).

EDIT: damn, smartbei posted while I was typing .. too slow ;)

---

### Post by achelis on 2008-05-24
That is absolutely brilliant :) And annoyingly simply when pointed out like that. Well explained and thanks a lot!

---

### Post by smartbei on 2008-05-24
Yes, sorry about that CptPicard - You get points for the more complete answer though :D.

---

### Post by slavik on 2008-05-24
this is a problem of all combinations, and I am pretty sure there was a discussion about a very efficient way to do this ...

in a nutshell:

for i in 0 to (2^n)-1
  look at what bits are set in i and pick the elements from the list/set.

given a list of 3 items (a,b,c):
i = 0, means all bits are zero, therefore you have an empty set.
i = 1, last bit is set, pick c
i = 2 (010), pick the second item from the list
i = 3 (011), pick the second and third items from the list
i = 4 (100), pick the first item from the list
...
i = 8 (111), pick all three items from the list

Hope that makes much sense :)

---

