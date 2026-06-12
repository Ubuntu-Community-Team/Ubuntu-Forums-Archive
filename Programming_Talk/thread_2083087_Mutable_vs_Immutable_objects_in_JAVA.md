---
title: "Mutable vs Immutable objects in JAVA"
date: 2012-11-11
forum: Programming Talk
---

### Post by vikkyhacks on 2012-11-11
1. What is the difference between mutable and immutable objects in Java ?

2. How do I if an Object is mutable or immutable ?

3. An Integer array mutable or immutable ???

---

### Post by dwhitney67 on 2012-11-11
Answers...

1.  [http://lmgtfy.com/?q=java+immutable+mutable+objects](http://lmgtfy.com/?q=java+immutable+mutable+objects)


2.  Usually the documentation for that object will tell you; in other cases the object is declared as "final".  A common immutable object is String; once you initialize a String, it's contents cannot be changed.  You can morph it into a different style of String, but the original String is still intact.

3.  An Integer array is mutable; you can create entries within the array, and you can modify them.  I suggest you write a small application to test this hypothesis.  An ArrayList is also mutable.

---

