---
title: "Knots Problem"
date: 2007-10-17
forum: Programming Talk
---

### Post by Lster on 2007-10-17
Hi

I have a (quite?) simple question regrading a problem I found on the internet. For the actual question have a look at [http://acmicpc-live-archive.uva.es/nuevoportal/data/problem.php?p=3582](http://acmicpc-live-archive.uva.es/nuevoportal/data/problem.php?p=3582) . My question is: is there a simple formula that can compute the answer for that question? I can see how it could be done with programming but what about with a simple math formula?

I have deduced very little so far but I'm really interested.

Thanks
Lster

---

### Post by Lster on 2007-10-17
Oh and by the way, this isn't homework or anything; just fun.

---

### Post by Lster on 2007-10-17
Anyone? Any hints - or maybe it cannot be expressed as a mathematical formula? I am still attempting solving it but it is slow :)!

---

### Post by Lster on 2007-10-17
I was wrong (as I said). Post removed!

---

### Post by Lster on 2007-10-17
Well I think I've cracked it! 

...

---

### Post by wolfbone on 2007-10-17
Looks right to me. The rationale would be as follows:

If N is the number of strands, then the girl has effectively just tied them together in pairs to make k=N/2 "U"s sticking through the wall.  Let P(k) be the probability that the boy ties them together on the other side to make a continuous loop, X(k) the set of tyings that result in a continuous loop and Y(k) the set of tyings that do not (and which consists of configurations of two or more disjoint loops) .  Clearly, P(k) = |X(k)| / (|(X(k) U Y(k|) = |X(k)| / (|X(k)| + |Y(k)|) - since X(k) and Y(k) are disjoint. 

Now we can easily construct X(k+1) by inserting a single "U" into each of the continuous loop tyings in X(k) and for each of these there are 2k ways of doing so, so  that |X(k+1)| = 2k|X(k)|. 

We can construct the tyings in Y(k+1) by inserting a "U" into each tying in Y(k) - as we did for X(k) - but we also need to add the tyings that result from adjoining - rather than inserting - a single closed "U" to each of the tyings in *both* Y(k) and X(k). There are 2k|Y(k)| + |Y(k)| + |X(k)| ways of doing this so that |Y(k+1| = (2k+1)|Y(k)| + |X(k)|

So P(k+1) = 2k|X(k)| / (2k|X(k)| + (2k+1)|Y(k)| + |X(k)|)  =  2kP(k) / (2k+ 1)

---

### Post by Lster on 2007-10-18
Thanks wolfbone. :)

---

