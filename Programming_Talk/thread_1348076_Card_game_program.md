---
title: "Card game program"
date: 2009-12-06
forum: Programming Talk
---

### Post by DanielJackins on 2009-12-06
Hello,

I'm trying to make a program which simulates a 3-card poker game. I've got most of it working (ie. dealing both of the players their hands) and just need to implement some way of determining which is the winning hand. The hands are, in order, a straight flush, three of a kind, a straight, a flush, a pair, and high card. How would I implement that? I can't really think of anything but a lot of if statements with long complicated conditionals.

Thanks for any help :)

---

### Post by Zugzwang on 2009-12-07
> **DanielJackins said:**
> I'm trying to make a program which simulates a 3-card poker game. I've got most of it working (ie. dealing both of the players their hands) and just need to implement some way of determining which is the winning hand. The hands are, in order, a straight flush, three of a kind, a straight, a flush, a pair, and high card. How would I implement that? I can't really think of anything but a lot of if statements with long complicated conditionals.


Yeah, that's basically the "standard" way of doing it. However, you can also do it OOP-like: Create an abstract class "HandType" with some some function that takes a hand and computes the value wrt. the type of hand. For example, a "Flush" would return "0" if the hand given is no flush and 1-4 otherwise (depending on whether you have spades, clubs, etc.).

Then derive a couple of sub-classes from "HandType", one for each "hand type". Instantiate them once in your program and add them to a list. Then you can see which hand is winning by computing for each hand the highest-index matching hand-type from the list. If two hands are equal wrt. the index, you can use the value to determine the winner. This way, all of these "hand types" are separated into individual classes, making it look a little bit nicer (but non-OOP programmers might disagree on this).

---

### Post by TennTux on 2009-12-07
I agree with Zugzwang for the most part.

Though I might suggest that the return from each hand type check be either 0 if the hand is not of that type, or the sum of two numbers if it is. The first, high order, number would represent the type of hand and the second would represent the high card for that hand, used to decide on ties. For example [Straight Flush]=4000; [Three of a Kind]=3000; [Straight]=2000; [Flush]=1000; [High Card]=0. Thus 3003 would be 3 threes, while 3007 would be 3 sevens. This allows you to compute a value for each player and then compare the values for the largest number.

Since a pair does not seem to be an option you will not run into the case where each player has the same pair for example [4 4 5] and [4 4 8] this would mean that the answer would need to be the sum of three numbers with Hand Type(High Value) High Card for Hand Type(Mid Value) and High Card not part of Hand Type(Low Value).

> **Zugzwang said:**
> ... with some some function that takes a hand and computes the value wrt. the type of hand. For example, a "Flush" would return "0" if the hand given is no flush and 1-4 otherwise (depending on whether you have spades, clubs, etc.).


And as for the OOP vs Algorithmic ;)
> **Zugzwang said:**
> 
However, you can also do it OOP-like: Create an abstract class "HandType" with some some function that takes a hand and computes the value...

...making it look a little bit nicer (but non-OOP programmers might disagree on this). 


While I would probably use the OOP method myself, it could be done cleanly and simply by having a function for each test rather than a class with a method.

---

### Post by nvteighen on 2009-12-07
I would definitely go for a procedural solution. Given a hand, return a heuristic value. I don't see any benefit from making this OOP-way... maybe just the syntactic fancy of having "hand.value()" (which we could still argue it is procedural programming under a OOP-syntax...).

---

