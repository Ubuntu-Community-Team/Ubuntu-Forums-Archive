---
title: "Please help debug this C declaration [C]"
date: 2011-06-04
forum: Programming Talk
---

### Post by cdiem on 2011-06-04
I have tried playing with some Project Euler problem (decided to do it in C), but was stopped in the beginning by the rather strange Segmentation Fault:


```
#include <stdio.h>

main()
{
    unsigned long int searched_prime, max, i, j;
    max = 1000000000L;
    unsigned long int nums[max];
    printf("%s", "success");
}
```

Can you please help me debug why this prints Segmentation Fault? Is there an error with the declarations? I have ran Valgrind on it, ran it through gdb, but wasn't able to find my error. I have tried compiling it with:
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)

---

### Post by matt_symes on 2011-06-04
Hi

```
max = 1000000000L;     unsigned long int nums[max];
```

Try creating your array on the heap, using malloc or some such, and then consider what you have done to your stack ;)

Kind regards

---

### Post by cdiem on 2011-06-04
Thanks. I haven't used C so far, and it's a humbling experience after using other languages. Thanks for your help.

---

### Post by jespdj on 2011-06-05
I hope you realize how much memory this is going to take: you want to allocate a billion unsigned long values. An unsigned long is usually 64 bits (8 bytes) so that statement will allocate 8 GB memory. Do you have that much memory in your computer?

On a 32-bit system this will certainly fail (because a process is limited to a 4 GB address space), and even on a 64-bit system it is likely to fail unless you have a LOT of RAM (even if you have more than 8 GB RAM it might fail because there isn't a consecutive block of 8 GB free RAM).

---

### Post by matt_symes on 2011-06-05
Hi

> I hope you realize how much memory this is going to take

 :popcorn:

I'm hoping the OP figured that out :D

Kind regards

---

### Post by r-senior on 2011-06-05
Ooh, Euler. Not done one of those for ages. I've done quite a few in C and had the odd foray deep into my swap partition. ;)

Which problem is it?

---

### Post by cdiem on 2011-06-05
> **r-senior said:**
> Ooh, Euler. Not done one of those for ages. I've done quite a few in C and had the odd foray deep into my swap partition. ;)

Which problem is it?

It's the [problem   7]("http://projecteuler.net/index.php?section=problems&id=7"); my first try was an Euler sieve on a big array, for learning C better (hence the topic). My code was 30 lines long, but also nonworking :) I'll try to rework it to use less memory. Thanks!

---

### Post by Barrucadu on 2011-06-05
Why are you trying to allocate such a gigantic array?

---

### Post by r-senior on 2011-06-05
An Erasthones Sieve? 

Why don't you try working your way up - find the 101st prime, then the 1001st prime and so on? You'll get a feel for whether you need (a) such a large sieve and (b) whether you need long integers.

It's a good learning exercise doing Euler in C. When you look at the solutions other people have done, especially in Python and J (which is a "program" of just 7 *characters* for this problem ;)) , you'll feel that you've had to work hard but it's good learning.

It's worth putting your prime number functions into a library and looking at ways to tune them. You'll use them a lot. You'll learn how big a sieve is worthwhile and how to go beyond the sieve. Functions to test whether a number is prime, generate sequences of primes, etc.

---

### Post by cdiem on 2011-06-05
> **Barrucadu said:**
> Why are you trying to allocate such a gigantic array?

I was trying to follow the algorithm as said in [Wikipedia]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes"):
1. Create a list of consecutive integers from two to n: (2, 3, 4, ..., n)
2. ...

But I set n too high ;] 

> Why don't you try working your way up - find the 101st prime, then the 1001st prime and so on? You'll get a feel for whether you need (a) such a large sieve and (b) whether you need long integers.

It's a good learning exercise doing Euler in C. When you look at the solutions other people have done, especially in Python and J (which is a "program" of just 7 characters for this problem ) , you'll feel that you've had to work hard but it's good learning.

It's worth putting your prime number functions into a library and looking at ways to tune them. You'll use them a lot. You'll learn how big a sieve is worthwhile and how to go beyond the sieve. Functions to test whether a number is prime, generate sequences of primes, etc.
Awesome! Thanks very much!

---

### Post by r-senior on 2011-06-05
This site comes in handy for some of the Euler stuff:

[http://mathworld.wolfram.com/topics/PrimeNumbers.html](http://mathworld.wolfram.com/topics/PrimeNumbers.html)

---

### Post by cdiem on 2011-06-05
> This site comes in handy for some of the Euler stuff:

[http://mathworld.wolfram.com/topics/PrimeNumbers.html](http://mathworld.wolfram.com/topics/PrimeNumbers.html)

Awesome! I'll be checking it a lot while playing!

You were right, a much smaller array was needed. The thing I like about it is that with C it seems fast. On to the next ones :)

EDIT - removed the solution, as suggested. Thanks very much for your helping!

---

### Post by r-senior on 2011-06-05
Well done :)

(It's best not to post your solutions though).

Just a couple of tips:

1. Strictly speaking the array is true/false, so when you populate, you don't need to set nums[i] to i, only to something to indicate true.

2. Your second loop could be more efficient. But you'll find that out in due course ;)

---

### Post by matt_symes on 2011-06-05
Hi

> (It's best not to post your solutions though).

Yes. Please don't. I was thinking of having a crack at them myself :P

Kind regards

---

### Post by ziekfiguur on 2011-06-05
> **r-senior said:**
> 1. Strictly speaking the array is true/false, so when you populate, you don't need to set nums[i] to i, only to something to indicate true.


Since this is true, you could use the separate bits of every integer, so on a 32bits machine you could represent 32 numbers for every integer in the array.

---

### Post by Petrolea on 2011-06-05
Just a tip: Many Euler problems can be solved by simply brute forcing (trying all possible combinations). But it can take some time.

---

### Post by ziekfiguur on 2011-06-05
> **Petrolea said:**
> Just a tip: Many Euler problems can be solved by simply brute forcing (trying all possible combinations). But it can take some time.

The challenge of Euler is writing a program that can solve the problems in under a minute. If you just brute-force it there's no fun in it.
I'm currently at problem 72, I have solved it with python in 1 minute and 4 seconds. With C i would be able to do it faster, but i feel like that would be cheating since i didn't improve the algorithm.

---

### Post by Petrolea on 2011-06-05
> **ziekfiguur said:**
> The challenge of Euler is writing a program that can solve the problems in under a minute. If you just brute-force it there's no fun in it.
I'm currently at problem 72, I have solved it with python in 1 minute and 4 seconds. With C i would be able to do it faster, but i feel like that would be cheating since i didn't improve the algorithm.

Even making a loop to brute force can take some time on more complicated problems. Even if you try not to brute force, at the end you still end up with a loop that's trying possible combinations (can't say if this is the case in all problems since I haven't solved many).

But speeding it up is where the fun begins :D. Adding calculations to eliminate some results and make the loop run faster is the harder part of the program. 

But if you're lazy you can leave it there running through night and trying out 1.000.000 ^ 2 combinations :P

---

### Post by r-senior on 2011-06-05
> **Petrolea said:**
> Adding calculations to eliminate some results and make the loop run faster is the harder part of the program.
Finding elegant mathematical solutions and applying theorems is also part of it and that's where it starts to become less attractive if you are approaching it as a learning programmer rather than a mathematician IMO.

With some of the later problems 300+, I don't even understand the question. ;)

---

### Post by Petrolea on 2011-06-05
> **r-senior said:**
> Finding elegant mathematical solutions and applying theorems is also part of it and that's where it starts to become less attractive if you are approaching it as a learning programmer rather than a mathematician IMO.

With some of the later problems 300+, I don't even understand the question. ;)

That's where Wikipedia helps us :). It is sometimes hard to apply those long and 'weird' calculations in a program but that's the point. But later it gets kind of boring (at least for me) since it really becomes a mathematical rather than programming challenge.

---

