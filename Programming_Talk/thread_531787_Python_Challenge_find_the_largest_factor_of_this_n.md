---
title: "Python Challenge: find the largest factor of this number"
date: 2007-08-22
forum: Programming Talk
---

### Post by triptoe on 2007-08-22
There is a longggggg way to do this and a much easier way. I am just curious if other people do it the same way as me. 

	
Find the largest prime factor of 317584931803 and show the code.. and no cheating!

---

### Post by apetresc on 2007-08-22
Is Bash allowed? :)
```
adrian@rootbeer:~$ cat problem.sh
echo `factor 317584931803`
adrian@rootbeer:~$ ./problem.sh
317584931803: 67 829 1459 3919

```
My answer is 3919!

Out of curiosity, is this question from Project Euler?

EDIT: Oh, oops, I missed the title that says it's a "Python" challenge. Well, you can always just make os calls from Python ;)

---

### Post by triptoe on 2007-08-22
> **AdrianP said:**
> Is Bash allowed? :)
```
adrian@rootbeer:~$ cat problem.sh
echo `factor 317584931803`
adrian@rootbeer:~$ ./problem.sh
317584931803: 67 829 1459 3919

```
My answer is 3919!

Out of curiosity, is this question from Project Euler?

EDIT: Oh, oops, I missed the title that says it's a "Python" challenge. Well, you can always just make os calls from Python ;)

you are close, but none of those are the right answer.

BTW yes it is from Euler... I am doing the challenges one by one.

BTW does anyone know how to find out the length of time it takes to execute a program? Like if i wanted to see how efficient an algorithm was implemented two different ways by timing it.. how would i time it?

---

### Post by apetresc on 2007-08-22
> **triptoe said:**
> you are close, but none of those are the right answer.

Er, what? Yes it is...
```
>>> 67*829*1459*3919
317584931803L
```
They definitely multiply to the correct value, and they're definitely all prime, and I'm pretty sure the fundamental theorem of arithmetic (unique factorization) still holds for big numbers ;) What makes you think this answer is not right?

```
BTW does anyone know how to find out the length of time it takes to execute a program? Like if i wanted to see how efficient an algorithm was implemented two different ways by timing it.. how would i time it?
```
You can use the UNIX 'time' utility. Like so:
```
adrian@rootbeer:~$ time ./problem.sh
317584931803: 67 829 1459 3919

real    0m0.031s
user    0m0.012s
sys     0m0.004s
```

Do a "man time" for more details. :)

---

### Post by triptoe on 2007-08-22
> **AdrianP said:**
> Er, what? Yes it is...
```
>>> 67*829*1459*3919
317584931803L
```
They definitely multiply to the correct value, and they're definitely all prime, and I'm pretty sure the fundamental theorem of arithmetic (unique factorization) still holds for big numbers ;) What makes you think this answer is not right?

Ahh you are right i was thinking that 67 * 4740073609 = 31758491803 so 4740073609 was.. oops ... didn't notice the "prime" part :)



```
BTW does anyone know how to find out the length of time it takes to execute a program? Like if i wanted to see how efficient an algorithm was implemented two different ways by timing it.. how would i time it?
```
You can use the UNIX 'time' utility. Like so:
```
adrian@rootbeer:~$ time ./problem.sh
317584931803: 67 829 1459 3919

real    0m0.031s
user    0m0.012s
sys     0m0.004s
```

Do a "man time" for more details. :)[/QUOTE]

---

### Post by n04touchyy on 2009-11-17
i know the post is old but still

the answer is actually 317584931803 because u dont say that it has to be a prime factor u only say it has to be a factor so 317584931803x1=317584931803.

:p:p:p:p:p:p:p

---

### Post by Can+~ on 2009-11-17
> **n04touchyy said:**
> i know the post is old but still

the answer is actually 317584931803 because u dont say that it has to be a prime factor **u only say it has to be a factor** so 317584931803x1=317584931803.

:p:p:p:p:p:p:p

> Find the largest prime factor of 317584931803 and show the code.. and no cheating!

Huh? (And you're 2 years late)

---

### Post by Yarui on 2009-11-17
Edit: Wow, I didn't even notice how old this thread was until I replied.  I kind of doubt my post is needed anymore.

---

### Post by cariboo on 2009-11-17
Due to the age of the thread, it is now closed

---

