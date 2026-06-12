---
title: "Java Implementation of Unsigned (without using BigInteger or Big Decimal)"
date: 2009-10-08
forum: Programming Talk
---

### Post by nova47 on 2009-10-08
For one of my classes I am supposed to write an implementation of unsigned in Java without using either the BigInteger or BigDecimal classes. The challenge is as follows:

--------------------------------------------------------------

A natural number is a number greater than or equal to 0. Java does not provide a primitive type that corresponds to natural numbers: only boolean and char are unsigned and neither provides very many distinct values (2 in the case of boolean and 65,536 in the case of char).

Your task is to implement a class that supports arbitrary-sized natural numbers (that is, limited only by memory availability for the JVM, not by some constant limit defined a priori by your class). This class is similar, at least in intent, to the Natural component from the Resolve/C++ component catalog.

Note that Java does provide, as part of the standard libraries, various implementations of arbitrary-sized numbers (e.g., BigInteger and BigDecimal). For the purpose of this lab, however, you are asked not to use the these classes in your own solution. 

--------------------------------------------------------------

I'm not looking to cheat but does anyone have any ideas on how to approach the problem? I'm just looking for a point in the right direction. I feel like this is a bit manipulation problem but I don't know how.

---

### Post by shadylookin on 2009-10-09
Well since most of java is open source. So whenever a professor says don't use class X in the assignment I would go look up that class and see how they did it for ideas. [http://www.docjar.com/projects/openjdk-7-java.html](http://www.docjar.com/projects/openjdk-7-java.html)

---

### Post by nova47 on 2009-10-10
I figured it out. I realized I was over complicating the assignment. When I read on all I had to do was provide three methods increment, decrement, and toString. I didn't actually have to be able to perform arithmatic on the object so I just ended up going with an ArrayList of chars.

---

