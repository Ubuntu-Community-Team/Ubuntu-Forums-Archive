---
title: "Help understanding some python syntax"
date: 2007-05-25
forum: Programming Talk
---

### Post by kevinlyfellow on 2007-05-25
Sorry about having to post on a forum for this, but I have no clue how else to find an answer.  

Anyways, the question.  What does n /= x mean and what does x += x % 2 + 1 mean?  I'm unfamiliar with /= and += and I don't know where to find the info.

---

### Post by tac-tics on 2007-05-25
> Sorry about having to post on a forum for this, but I have no clue how else to find an answer.

This seems like a good enough place. You can also try:

[http://groups.google.com/group/comp.lang.python/topics](http://groups.google.com/group/comp.lang.python/topics)

For help in Python


> Anyways, the question. What does n /= x mean and what does x += x % 2 + 1 mean? I'm unfamiliar with /= and += and I don't know where to find the info.

+=, -=, /=, *=, %= are common shorthands in Python, Java, C, and many, many other languages.

They are simply abbreviations, defined as follows:

x += a  ==========> x = x + a
x /= a ==========> x = x % a

So
x /= 2, for example, simply halves the value of the variable x.
x += 1, increments the value of variable x by one (in Java and C, you can do x++ for this but not in Python).
x *= x, squares the value of the variable x.

The difference between x + a and x += b is that the first simply __returns__ the value of x + a and the second actually stores that returned value in the variable x. Very handy from time to time.

---

### Post by kevinlyfellow on 2007-05-25
thanks very much :-)

---

### Post by Billy the Kid on 2007-05-25
In Python,  "/=" means that the number in front of the operator divided by the number after the operator, equals the variable after the operator.

n = n / x

For example: 
a = 36
b = 12
a /= b
# a is equal to 3 

In answer to your second question, x is equal to it's current value and the sum of x % (modulus) 2 + 1

 Hope that helps

---

### Post by kevinlyfellow on 2007-05-26
> **Billy the Kid said:**
> In Python,  "/=" means that the number in front of the operator divided by the number after the operator, equals the variable after the operator.

n = n / x

For example: 
a = 36
b = 12
a /= b
# a is equal to 3 

In answer to your second question, x is equal to it's current value and the sum of x % (modulus) 2 + 1

 Hope that helps

Tac-tics  already deconfused me (I caught his error i /= x is the same as i = i/x not i = i % x), but thanks for the effort.  I've made quite a bit of progress today! :-)

---

