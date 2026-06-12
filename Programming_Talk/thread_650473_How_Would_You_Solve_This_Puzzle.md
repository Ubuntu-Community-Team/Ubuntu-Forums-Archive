---
title: "How Would You Solve This Puzzle?"
date: 2007-12-26
forum: Programming Talk
---

### Post by Lster on 2007-12-26
Hi guys and happy Christmas :)

In a book I got for Christmas (a puzzle book... :mad:), there is this question which I cannot find an elegant solution for. The puzzle reads:

> Take a five-digit number and reverse it. Subtract the origional number from its reverse, and you are left with 33957.
What was the original number?

Well I know how I could solve it with brute force, but mathematically how would be best to approach it?

---

### Post by CptPicard on 2007-12-26
Quick back of the envelope algebra failed to produce a solution -- it may need some prime number decomposition stuff I've forgotten since taking my algebra class -- but if I were to code this, I would approach it from a constrained search angle. You do not need to "brute force" it that much really if you are smart about it. 

If the number x is the original and x' is the reverse, we have x' - x = 33957. Let's rewrite this x' = 33957 + x for convenience, it's going to be easier to deal with addition with what I've got in mind.

Now let's move on to long addition. Let a..e be the digits of the number. So:

```


 abcde
+33957
---------
 edcba

```

Now, all you need to do is start searching among the possible digits, always checking for consistency as you attach some digit some value, and backtracking if you get something inconsistent or run out of options. This may actually restrict your choices so much that you can do this on pencil and paper...

An algebraic solution would be most welcome though ;)

---

### Post by ssam on 2007-12-26
something like this?

a_1 * 10000 + a_2 * 1000+ a_3 * 100+ a_4 *10 + a_5 * 1  + 33957 = a_5 * 10000 + a_4 * 1000+ a_3 * 100+ a_2 *10 + a_1 * 1

where a_1 are integers from 0 to 9

---

### Post by Lster on 2007-12-26
I thought about a modulo solution but I wasn't able to derive a solution for anything but linking the first and last digit. You're right that I don't need to try every possible 5 digit number - some I can easily dismiss, but I can't seem to get the possibilities down to a "manageable" level!

---

### Post by Lster on 2007-12-26
> **ssam said:**
> something like this?

a_1 * 10000 + a_2 * 1000+ a_3 * 100+ a_4 *10 + a_5 * 1  + 33957 = a_5 * 10000 + a_4 * 1000+ a_3 * 100+ a_2 *10 + a_1 * 1

where a_1 are integers from 0 to 9

But then how would you solve that?

---

### Post by CptPicard on 2007-12-26
> **ssam said:**
> something like this?

a_1 * 10000 + a_2 * 1000+ a_3 * 100+ a_4 *10 + a_5 * 1  + 33957 = a_5 * 10000 + a_4 * 1000+ a_3 * 100+ a_2 *10 + a_1 * 1

where a_1 are integers from 0 to 9

This is the algebraic one I tried first, doesn't work, it's got to do with the carries in the arithmetic :)

EDIT: the solution method I proposed *is* manageable IMO. If only I had more paper handy and was... erm.. more sober ;)

So far I am working under the assumption that a=2 and e=5 and the least-significant digit addition produces a carry for the next one and the most-significant digit addition receives no carry from the previous one. Now I just would need to reproduce the possible equation pairs for the (b,d) pair of variables and check out which one of them would be satisfied... but I think I'll just leave it as an exercise and go enjoy more Xmas drinks ;)

---

### Post by wolfbone on 2007-12-26
Not sure there is an "elegant" solution.

Write it out in power terms:

10^4(a0 - a4) + 10^3(a1 - a3) + 10(a3 - a1) + a4 - a0 = 33957

9999(a0 - a4) + 990(a1 - a3) = 33957

(a2 cancels out and can be anything)

Choose a0 - a4 = 3 and a little rearrangement gives:

990(a1 - a3) = 3960

a1 - a3 = 4

Choose  a4 = 1, a3 = 0, a2 = 0

10044 

Other such reasonable  choices get other solns.

---

### Post by Lster on 2007-12-26
> the solution method I proposed *is* manageable IMO. If only I had more paper handy and was... erm.. more sober

So far I am working under the assumption that a=2 and e=5 and the least-significant digit addition produces a carry for the next one and the most-significant digit addition receives no carry from the previous one. Now I just would need to reproduce the possible equation pairs for the (b,d) pair of variables and check out which one of them would be satisfied... but I think I'll just leave it as an exercise and go enjoy more Xmas drinks

Just about. Anyway, enjoy your drinks. :)

wolfbone:

That is probably as good as it gets - very nice! :)

---

### Post by CptPicard on 2007-12-26
Ok, by elimination I got 20045. There might be other solutions too.

The point is to start at the edges first, and to first figure out that the most-significant digit addition cannot produce a carry because we remain within 5-digit numbers. Then by looking at the possibilities of the least-significant column either carrying or not and the most-significant either receiving a carry or not, we can pretty quickly deduce (at least a good assumption) a=2, e=5.

Now, the center column with variable c has the interesting property that if it does not get a carry, there are no solutions. Therefore, there must be a carry, in which case all values of c are ok! This is an interesting property and helps in figuring out the middle columns with (b,d).

For (b,d) you also set up your equation pairs with the knowledge that you're

a) getting a carry from the least-significant end
b) producing a carry to the most-significant end
c) producing a carry to the middle, c-column
d) the c-column actually has to produce a carry, with the knowledge it receives one. Look at it.

So... you solve for d = b+4. Set b=0 and notice you're done. You can just stick 0 into c as well then :)

---

### Post by wolfbone on 2007-12-26
> **Lster said:**
> 

wolfbone:

That is probably as good as it gets - very nice! :)

Glad you like it. Though there is a slight error: a0 - a4 = 3 is not a choice - it's the only possibility.

---

### Post by CptPicard on 2007-12-26
> **Lster said:**
> 
That is probably as good as it gets - very nice! :)

I would contend I actually have a search procedure that produces all solutions if one keeps looking ;)

@wb, did you you actually get your assumption for a4-a0=3 from somewhere?

---

### Post by wolfbone on 2007-12-26
> **CptPicard said:**
> There might be other solutions too.


All a0,a1,a2,a3,a4 in {0 ... 9} , a4 > 0 such that a0 - a4 = 3 and a1 - a3 = 4 are solutions.

---

### Post by wolfbone on 2007-12-26
> **CptPicard said:**
> I would contend I actually have a search procedure that produces all solutions if one keeps looking ;)

@wb, did you you actually get your assumption for a4-a0=3 from somewhere?

The only possible solutions of the diophantine, 9999x + 990y = 33957 that are also solutions to the original problem are x = 3, y = 4

---

### Post by CptPicard on 2007-12-26
Okay, thanks :)

---

### Post by Kadrus on 2007-12-26
> **Lster said:**
> Hi guys and happy Christmas :)

In a book I got for Christmas (a puzzle book... :mad:), there is this question which I cannot find an elegant solution for. The puzzle reads:



Well I know how I could solve it with brute force, but mathematically how would be best to approach it?
Euuh....I asked my friend if he could solve it..
He got 34000..
Is it correct?

---

### Post by Majorix on 2007-12-26
Which language are you working with? In VB, for example (that's what I am learning at school) there is a string function called Mid() which could chop your number into single-digit numbers, from where you can easily solve the rest. I am not sure, but I believe most other languages have a similar facility too. Just google and read the provided docs. Hope it helps.

---

### Post by wolfbone on 2007-12-26
> **Kadrus said:**
> Euuh....I asked my friend if he could solve it..
He got 34000..
Is it correct?

Well no. 43 - 34000 is negative. I got  the subtraction the wrong way round at first too.

---

### Post by CptPicard on 2007-12-26
> **Majorix said:**
> Which language are you working with?

We're working with pencil, paper and brain. ;)

If the algebraic one hadn't been so readily available, I might have tried implementing my search in some language though... :)

Really, props wb, this was enjoyable ;)

---

### Post by wolfbone on 2007-12-26
> **CptPicard said:**
> We're working with pencil, paper and brain. ;)

If the algebraic one hadn't been so readily available, I might have tried implementing my search in some language though... :)

Really, props wb, this was enjoyable ;)

Thanks :) It's rather odd that the original question suggests a single solution though... (even if I'd got which number gets subtracted from which right first time and disallowed numbers with leading zeroes ;-)

---

### Post by Lster on 2007-12-26
Well - just goes to show that Mensa ('cause it's their book!) isn't that smart - doesn't surprise me!

---

### Post by CptPicard on 2007-12-26
This reminds me of the idea that I went to CS so I didn't have to think like I would have had to in math. Let the computer do the crunching. :p

---

### Post by ghostdog74 on 2007-12-26
[Sorry to spoil the fun]("http://www.braingle.com/brainteasers/teaser.php?op=2;id=31761;comm=0").

---

### Post by wolfbone on 2007-12-27
> **ghostdog74 said:**
> [Sorry to spoil the fun]("http://www.braingle.com/brainteasers/teaser.php?op=2;id=31761;comm=0").

No need to apologise, ghostdog74. Your post is a bit too late to be a spoiler!

Edit: Also, the answer in that link, although numerically correct, is wrongly reasoned.

---

