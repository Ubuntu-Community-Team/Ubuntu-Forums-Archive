---
title: "Context-Free Grammar"
date: 2009-04-05
forum: Programming Talk
---

### Post by jacobM on 2009-04-05
K, these are quite easy for me now to get a CFG for a CFL. 
But ive run into a new problem with some notation. I cannot put my finger on exactly what this notation means. 

Here it is.

L3, L*, L complement for the language

L = {a^n.b^n : n &#8805; 1} on  = {a, b}.

The CFG for this is of course quite simple. I just can'f figure out exactly what the notations mean. Does this have anything to do with closure properties?
Any help is greatly appreciated.

---

### Post by Arndt on 2009-04-05
> **jacobM said:**
> K, these are quite easy for me now to get a CFG for a CFL. 
But ive run into a new problem with some notation. I cannot put my finger on exactly what this notation means. 

Here it is.

L3, L*, L complement for the language

L = {a^n.b^n : n &#8805; 1} on  = {a, b}.

The CFG for this is of course quite simple. I just can'f figure out exactly what the notations mean. Does this have anything to do with closure properties?
Any help is greatly appreciated.

Neither can I, but where did you get it? (CFL means context-free language, I suppose.)

* is commonly used for closure, but I don't know what the 3 stands for. Maybe S[SIZE="1"]1[/SIZE]S[SIZE="1"]2[/SIZE]S[SIZE="1"]3[/SIZE], where S[SIZE="1"]1[/SIZE], S[SIZE="1"]2[/SIZE] and S[SIZE="1"]3[/SIZE] all belong to L?

(I don't know if this is programming, but why not.)

---

### Post by jacobM on 2009-04-06
I think 
L3 is (a^n b^n)(a^n b^n)(a^n b^n)
L* is (a^n b^n) and the empty set
L complement is everything other than (a^n b^n) so kinda would be (a^n b^m)

Just in case anyone was wondering and to kinda answer this post/myself :) lol.
Thanks for the reply Arndt.

---

### Post by CptPicard on 2009-04-06
I guess L3 means what you think it means (are you talking of L^3, with 3 in the exponent?), but I can't see how complement would look like that. It's more like

```

{a,b}* \ {a^nb^n : n &#8805; 1}

```

And the closure

```

{a^n.b^n : n &#8805; 1}* =

{<empty>, ab, aabb, abaabb, aabbab, aaabbb, abaaabbb, aaabbbab,
abaabbaaabbb, abaaabbbaabb, ... <all concatenated combinations of what you can generate>}

```

I can't really think of better set-representations for the two...**

---

