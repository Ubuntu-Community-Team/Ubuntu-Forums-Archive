---
title: "A challange I found -- how would you do it?"
date: 2010-12-04
forum: Programming Talk
---

### Post by DBQ on 2010-12-04
Hi everybody. I was surfing for fun programming challenges, and I found one, which was actually a question of logic (it seems that this was an interview question at some point too).

1. Everyone Loves All Lovers
2. Romeo Loves Juliet

Therefore, prove (i.e. 1 AND 2 => 3)
3. I Love You

Here is how I do it: 

I assume that anything that loves is a lover. Let L represent the set of all lovers. Everybody, loves people in L. Since Romeo "loves" he is in L. From here, we know that everybody loves Romeo. If this is the case, then everybody is a lover, is in L, and hence, everyone loves everyone else. From this since "I" and "You" are part of "everyone", then I love you.

What do you think?  Anybody got other solutions?

---

### Post by roccivic on 2010-12-06
Mathematically this argument is a fallacy (e.g: not true).

Let:
a = "Everyone Loves All Lovers"
b = "Romeo Loves Juliet"
c = "I Love You"

This yield the argument:
(a and b) implies c

A valid argument is a tautology (e.g.: it simplifies into "true"), but the above argument simplifies into:
(c or not(a)) or not(b)

Therefore it is false.

---

### Post by Neovos on 2010-12-06
> **roccivic said:**
> A valid argument is a tautology (e.g.: it simplifies into "true")

not all valid arguments are tautologies. A valid argument is one where the conclusion is valid under at least one interpretation. A tautology is true under ALL interpretations (that is, it's negation cannot be valid ever). 

true statement --> all U.S. presidents were (are) older then 35
false statement --> all men over 35 are U.S. presidents
tautology --> all men over 35 are either presidents or not

I say the original phrase is true and heres why:

Everyone refers to the set of all people. If "everyone loves all lovers", then that alone is sufficient and necessary to say that "I love you" because both you and I are in the set of all people, and if the set of all people love lovers, then both you and I love lovers as well.

To say as well that "Romeo Loves Juliet", is another condition that is true and also sufficient and necessary to "everyone loves all lovers" by the same reasoning. And since "Romeo Loves Juliet" is not a contradiction to "Everyone loves all lovers," then conditions A and B being true both imply that C is true as well. 

It is not a tautology however because if:

a = "Everyone Loves All Lovers"
b = "Romeo Loves Juliet"
c = "I Love You"

the negation is then:

not(a) = "Everyone does not love all lovers"
not(b) = "Romeo does not love Juliet"
not(c) = "I do not love you"

The above relationship, not(a) and not(b) therefore not(c) is true by the same token that I argued before. Thus it's not a tautology.


I spent too much time on this....

---

### Post by dwhitney67 on 2010-12-06
The Capulets do not love Romeo, and in this day and age, they would also despise Juliet for what she has done.

Btw, here's a challenge... how many cats live in your country?  Seriously!  Do the math...

---

### Post by StephenF on 2010-12-07
A barely avoidable intuitive leap.

d) Everyone that loves is also a lover.

I'm not liking how poorly defined everyone is but assume it to include fictional as characters as well as the reader and writer and that it be the universal set.

---

