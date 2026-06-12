---
title: "what do =&gt; mean in haskell?"
date: 2011-11-11
forum: Programming Talk
---

### Post by william2011 on 2011-11-11
what do => mean in haskell?
 
instance (Coarbitrary a, Arbitrary b) => Arbitrary (a -> b) where
arbitrary = promote (a -> coarbitrary a arbitrary)

---

### Post by Bachstelze on 2011-11-11
[http://en.wikibooks.org/wiki/Haskell/Classes_and_types](http://en.wikibooks.org/wiki/Haskell/Classes_and_types)

---

### Post by simeon87 on 2011-11-11
Short answer: it enforces constraints on what a and b can be. This is useful if you want your function to accept certain types but not all.

Long answer: read link above.

---

### Post by cgroza on 2011-11-11
It gives a hint to the type checker that the types a b must have an instance of the a some class available.
For example, if you want to write a comparison function, your function may need types that have an Eq instance.

This kind of constraints are usually necessary only when the type checker does not have enough information to infer one.

---

### Post by schauerlich on 2011-11-11
If you're familiar with Java interfaces, it's kind of like saying whatever type you have must implement a certain interface.

---

