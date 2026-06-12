---
title: "My prime number generator"
date: 2008-08-23
forum: Programming Talk
---

### Post by artir on 2008-08-23
After some hours of coding (I've recently started to learn python), I attempted to make a prime number finder. It works, but maybe it can be further improved to make is faster:

[PHP]
#!/usr/bin/python
numbers=[]
primes=[]
marcadoesdivi=0

#Count up to...
hasta=999

#Move forward one number and check...

for go in range(1,hasta+1):
    
  numbers.append(go)
  
  #Try to divide the number by all the numbers before that one but one and zero

  for check in range(2,len(numbers)):
      
      #Check if the division give us 0
      
      isprime=go%(check)
      
      #If the check phails, set a var 1. A number must pass all the checks
      
      if isprime == 0:
          marcadoesdivi=1
          
   #If the number passes the check, do this:
          
  if marcadoesdivi == 0:
             primes.append(go)
             marcadoesdivi=0
             print go
             
 #Set the prime checking var to 0 again           
  marcadoesdivi=0
   [/PHP]

I want to know what can be done to this code to make it run faster.
Thanks

---

### Post by Majorix on 2008-08-23
> **artir said:**
> After some hours of coding (I've recently started to learn python), I attempted to make a prime number finder. It works, but maybe it can be further improved to **make is faster**:
I want to know what can be done to this code to **make it run faster**.

If speed is what you want, you are better off with another language.

---

### Post by shankhs on 2008-08-23
Your algorithm is Theta(n^2)( if you dont know anything about Theta notaation then go through [http://www.cprogramming.com/tutorial/computersciencetheory/algorithmicefficiency1.html](http://www.cprogramming.com/tutorial/computersciencetheory/algorithmicefficiency1.html))

Further more check this:
[http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)

This algo generates prime in O((nlogn)(loglogn)).

---

### Post by Erdaron on 2008-08-23
From just the algorithm point of view...

When you're checking if x is divisible by smaller numbers, you should only check using primes smaller than the square root of x. Otherwise you're checking whether x is divisible by 2 and 4 - if it's not divisible by 2, it is definitely not divisible by 4.

Also, every time you get a new prime, you should eliminate its multiples from the list of all numbers.

There are existing algorithms, such as [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") that will rather efficiently look for primes. (Although I understand that it's more exciting to come up with our own method than implementing something someone else had thought up.)

---

### Post by Reiger on 2008-08-23
If you want to do the goold ol' Sieve you're better off with Haskell.
```

module Prime where

primes (x:xs) = x : ( primes (filter (`isRelativePrimeTo` x) xs) )
primes  x	  = x

isRelativePrimeTo = \x y -> x `mod` y /= 0

```

Call the **primes** function like so (where '>' stands for the prompt): ```
> primes [2..]
```

Or: ```
> primes [2..k]
``` Where k is any Integer >= 2.

So, unless Python has Lazy Evaluation you must either restrict yourself to finite lists (the [2..k] example) or accept a bit of a drop in performance. (This Haskell code got me at 14207 in less than a second.)

---

