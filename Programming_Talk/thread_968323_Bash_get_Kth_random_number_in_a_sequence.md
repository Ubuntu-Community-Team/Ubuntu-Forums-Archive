---
title: "Bash get Kth random number in a sequence"
date: 2008-11-02
forum: Programming Talk
---

### Post by DBQ on 2008-11-02
Hi everybody.  I am using the bash's $RANDOM magic variable.  I seed it in the beginning (ie RANDOM=1234), and use it to get numbers in a sequence.  Say I would like get a kth number in a sequence.  Is there a way to accomplish this without looping through all the previous numbers?

---

### Post by stylishpants on 2008-11-02
No, once you seed RANDOM, you have to get all k numbers to see the kth.  Random number generators in general are deliberately designed to work this way.

Since you are getting your random numbers in a specific order anyway, you could cheat and capture a bunch of them in advance, for easy reference.

---

