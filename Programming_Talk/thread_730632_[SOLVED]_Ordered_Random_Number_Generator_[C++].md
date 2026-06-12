---
title: "[SOLVED] Ordered Random Number Generator [C++]"
date: 2008-03-21
forum: Programming Talk
---

### Post by moinster on 2008-03-21
Good Morning everyone...

I am just wondering if there is a way to randomly generate numbers, lets say 0-9, in an ordered set.  Like {3,4,6,2,1,9,7,0,5,8}.

I was thinking something like using an IF statement were if x = 1 and it tried to generate 1 again it would say no you cant do that, generate another number that is not 1.

If anyone knows what I'm trying to say - awesome.
If you don't, that is fine.  It was something that just popped into my head.

moin

---

### Post by CptPicard on 2008-03-21
The issue with that algorithm is that it's n^2 in time. A better way to do it is to first generate your numbers in (any) order (0,1,2...9) and then shuffle that vector. This is actually a typical homework assignment as it is easy to get wrong.. ;)

[http://en.wikipedia.org/wiki/Shuffling#Shuffling_algorithms](http://en.wikipedia.org/wiki/Shuffling#Shuffling_algorithms)

---

### Post by moinster on 2008-03-21
Hahah no really it's not homework.  In my c++ class we are doing fstream's.  I was trying to make a program that would help me count cards faster in blackjack.

I want it so cards don't show up twice and mess with the count.  I only want 52 different cards, not 4 Kings of Hearts.

If you understand, yay.  But it was just something I randomly thought of.

---

### Post by Wybiral on 2008-03-21
Then you fill a vector with all 52 cards and use the Fisher-Yates / Knuth shuffle that CptPicard linked to (don't worry it's simple).

---

### Post by CptPicard on 2008-03-21
Wyb, you've been up all evening and it's apparently quite late there ... go to bed ;)

---

### Post by Wybiral on 2008-03-21
> **CptPicard said:**
> Wyb, you've been up all evening and it's apparently quite late there ... go to bed ;)

lol, it's true. But I have this magical ability to skip about one night of sleep each week and still function. There's a threshold you have to reach, but after that it's like you never even needed to sleep.

---

### Post by CptPicard on 2008-03-21
I'm good at that, as well. I am currently about 24hrs up and counting. :)

---

### Post by LaRoza on 2008-03-21
I too haven't slept :-)

Will tonight, most likely.

(Must be a programmer thing)

---

### Post by CptPicard on 2008-03-21
One of my professors had this posted outside his office:

> 
Computare neccesse est, dormire non est neccesse


I'm not a Latinist but I get the point :)

---

### Post by Wybiral on 2008-03-21
Insomnia and absentmindedness seem to be very common traits amongst our type.

---

### Post by LaRoza on 2008-03-21
> **Wybiral said:**
> Insomnia and absentmindedness seem to be very common traits amongst our type.

[img]http://hackles.org/strips/cartoon20.png[/img]

---

### Post by moinster on 2008-03-22
Thank you so much for the help

---

