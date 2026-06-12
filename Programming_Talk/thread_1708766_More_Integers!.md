---
title: "More Integers!"
date: 2011-03-17
forum: Programming Talk
---

### Post by Bakerconspiracy on 2011-03-17
So, I'm a fourth year math major, and I've had this question for a long time now... but I would finally like to know the optimal answer. So with double / long int I get a certain amount of mem space for storage of integers. How to I get more. Do I have to write a subroutine for a predefined data structure to store more digits in memory beyond what is allocated for the basic data structures? How do I got about computing something like the 200th Fibonacci number?

Thanks, mucho.

---

### Post by leg on 2011-03-17
With Java there is a BigDecimal class and some others for this purpose. Other languages will have there alternatives or yes you can write own code to manage the storage for large numbers.

---

### Post by matthew.ball on 2011-03-17
Mmm, Haskell and it's arbitrary precision... Literally took half a second to compute...

> 
fibonacciNumber 200 -> 280571172992510140037611932413038677189525


It gets a bit trickier with prime numbers though...

*Note: I have no idea if that's really the 200th Fibonacci number, but the Haskell definition I used *appears* to be correct.

---

### Post by Bakerconspiracy on 2011-03-17
Haha Haskel sounds a lot like mathematica. I'm trying to depart from languages that all already been made for me like that. Java has a bit too much overhead for my preference. But I have heard about that big decimal lib before, and now I finally will take a look at it for ideas. Thanks a bunch

---

### Post by Bakerconspiracy on 2011-03-17
Although Haskell seems great for a quick numeric analysis problem :)

---

### Post by matthew.ball on 2011-03-17
Haskell's a pretty amazing language if you're coming from a background in mathematics.

---

### Post by forrestcupp on 2011-03-17
In the old 8-bit days, we pretty much had to do what you're talking about manually. An 8-bit positive integer could only have a value of up to 65,536 values. So we would have however many bytes we needed to represent the different blocks of bits in a larger number.

It's a royal pain in the backside, and I'm glad we don't usually have to mess with that anymore.

---

