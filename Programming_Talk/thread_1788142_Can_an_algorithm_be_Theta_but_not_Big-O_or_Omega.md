---
title: "Can an algorithm be Theta but not Big-O or Omega?"
date: 2011-06-22
forum: Programming Talk
---

### Post by The111 on 2011-06-22
I'm not sure if there's a better sub-forum to put this question in.

I am new to computer science and programming in general, and I just recently learned about Big-O, Omega, and Theta, but I think I have a decent grasp on them (though I'd be happy to be proved wrong too).  I understand that an algorithm can be Big O and Omega, but not Theta.  For example if something is O(N) and Omega(1), then there is no Theta.

However, I ran into something recently where it is being claimed that a function is Theta(1), but is not Big O or Omega.  Does this make any sense?  Theta means there is are TWO constant factors to multiply by a certain  function, ONE factor gives upper bound function and other ONE factor  gives lower bound function.  Right?

Big O means there is a constant factor to give upper bound (already established above as ONE of the TWO).

Omega means there is a constant factor to give lower bound (already established above as ONE of the TWO).

In  essence it seems like we are saying that a thing is both A and B, but  neither A nor B.  Logically that doesn't make sense... if something is  Theta it seems to me it has to be both Big O and Omega also (though the  opposite is not true).

I welcome the thoughts of the more experienced in these matters. :popcorn:

---

### Post by simeon87 on 2011-06-22
> **The111 said:**
> if something is  Theta it seems to me it has to be both Big O and Omega also (though the  opposite is not true).

That is also what I think.

---

### Post by NovaAesa on 2011-06-22
If f(n) is in &#920;(1) then this implies it's also in &#927;(1) and &#937;(1).

---

### Post by Barrucadu on 2011-06-22
> **The111 said:**
> However, I ran into something recently where it is being claimed that a function is Theta(1), but is not Big O or Omega.  Does this make any sense?  Theta means there is are TWO constant factors to multiply by a certain  function, ONE factor gives upper bound function and other ONE factor  gives lower bound function.  Right?

Let's start with some formal definitions of Big Oh and Big Omega:

```
f(n) &#8712; O(g(n)) &#8660; &#8707;k > 0, n&#8320; &#8704;n > n&#8320; |f(n)| &#10877; |k×g(n)|
f(n) &#8712; &#937;(g(n)) &#8660; &#8707;k > 0, n&#8320; &#8704;n > n&#8320; |f(n)| &#10878; |k×g(n)|
```

So Big Oh can be thought of as "*f* grows no faster than *g*", and Big Omega can be thought of as "*f* grows no slower than *g*". Big Theta can be defined as follows:

```
f(n) &#8712; &#920;(g(n)) &#8660; &#8707;k&#8321; > 0, k&#8322; > 0, n&#8320; &#8704;n > n&#8320; |f(n)| &#10877; |k&#8321;×g(n)| &#8743; |f(n)| &#10878; |k&#8322;×g(n)|
```

So Big Theta can be thought of as "*f* grows exactly as fast as *g*".

Now, hopefully it's not too difficult to see from those definitions that if f(n) &#8712; &#920;(g(n)) holds, then so do f(n) &#8712; O(g(n)) and f(n) &#8712; &#937;(g(n)). That is:

```
f(n) &#8712; &#920;(g(n)) &#8660; f(n) &#8712; O(g(n)) &#8743; f(n) &#8712; &#937;(g(n))
```

In summary, that claim is totally wrong, it's impossible for that to be the case. If you worked through the logic assuming that claim was correct, you would derive a contradiction.

---

### Post by The111 on 2011-06-22
> **Barrucadu said:**
> Let's start with some formal definitions of Big Oh and Big Omega:
Sadly, I am not too familiar with the formal definition or all the symbols involved.  What course of study would I undertake to understand that math and those symbols?  I'm guessing it's discrete math... I've actually started reading a big book on that but haven't got very far yet.

I have an aero engineering background and all the math that goes along with it, but am new to comp sci.  I've only received a brief informal definition of the Big O concept in a data structures class I'm taking to jump into the comp sci world.

Thanks.

> **Barrucadu said:**
> In summary, that claim is totally wrong, it's impossible for that to be the case.
The claim is coming from a college professor. :(

---

### Post by simeon87 on 2011-06-22
> **The111 said:**
> The claim is coming from a college professor. :(

Is that really what the professor said? It sounds unlikely that he / she would make such a basic mistake. Despite all the formal symbols above, the intuitive concepts are quite obvious. Is it possible that you have interpreted a claim incorrectly? That's okay, it seems your understanding was right all along.

---

### Post by The111 on 2011-06-22
> **simeon87 said:**
> Is that really what the professor said? It sounds unlikely that he / she would make such a basic mistake. Despite all the formal symbols above, the intuitive concepts are quite obvious. Is it possible that you have interpreted a claim incorrectly? That's okay, it seems your understanding was right all along.
On an exam it was asked that I give Big O, Theta, and Omega for a certain programming operation (flipping a specific single bit in a bitmap).  My answer was:
O(1), Omega(1), and Theta(1)

The professor crossed off my O and Omega answers and said the correct answer was Theta only.

Not much room for interpretation there.  I do not mean to throw this (anonymous) prof under the bus, but I did want to make sure my logic was sound before I discussed it further with him.  Thanks for the input.

---

### Post by schauerlich on 2011-06-22
> **The111 said:**
> The professor crossed off my O and Omega answers and said the correct answer was Theta only.

Perhaps he thought that the Big-O and Big-Omega specifications were redundant?

---

### Post by simeon87 on 2011-06-22
> **schauerlich said:**
> Perhaps he thought that the Big-O and Big-Omega specifications were redundant?

Could be. Theta(1) implies O(1) and Omega(1). In that case the question should have been phrased differently though as the question now asks for all three of them.

---

### Post by Arndt on 2011-06-22
> **The111 said:**
> Sadly, I am not too familiar with the formal definition or all the symbols involved.  What course of study would I undertake to understand that math and those symbols?  I'm guessing it's discrete math... I've actually started reading a big book on that but haven't got very far yet.



[http://en.wikipedia.org/wiki/First-order_logic](http://en.wikipedia.org/wiki/First-order_logic) and
[http://en.wikipedia.org/wiki/Set_theory](http://en.wikipedia.org/wiki/Set_theory) cover the unknown symbols, I think.

There may be better elementary expositions, of course. Discrete mathematics uses sets a lot, and if theorems are proved, => and <=> will be in there too.

---

### Post by The111 on 2011-06-23
> **schauerlich said:**
> Perhaps he thought that the Big-O and Big-Omega specifications were redundant?
His latest statement to me, in response to my argument as presented in the original post:

[I]theta is approximately the same
thus no separate upper/lower bound[/I]

---

### Post by slavik on 2011-06-23
if you make a venn diagram, theta is the cross section.
big O is one circle, big omega is the other.
little o is the circle without theta, little omega same the other way

saying something is both big O and big omega doesn't make sense if it's theta, since theta is an intersection, not both.

---

### Post by The111 on 2011-06-23
> **slavik said:**
> if you make a venn diagram, theta is the cross section.
big O is one circle, big omega is the other.
little o is the circle without theta, little omega same the other way

saying something is both big O and big omega doesn't make sense if it's theta, since theta is an intersection, not both.
How can you have an intersection of two circles, without two circles?

---

### Post by NovaAesa on 2011-06-23
> **The111 said:**
> His latest statement to me, in response to my argument as presented in the original post:

[I]theta is approximately the same
thus no separate upper/lower bound[/I]

Your professor is wrong, simply put. There is a lower and upper bound, they are both constant bounds.

---

