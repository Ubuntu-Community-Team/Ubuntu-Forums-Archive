---
title: "a very wierd stack overflow!! (Haskell)"
date: 2008-12-01
forum: Programming Talk
---

### Post by amityak on 2008-12-01
so the next question refers to Haskell, but i'm sure many of you could see directly the problem which I don't see. 

the task is to sum up all [amicable numbers]("http://en.wikipedia.org/wiki/Amicable_number") up to 10,000 [(click for wikipedia link)]("http://en.wikipedia.org/wiki/Amicable_number")
amicable numbers: a pair of numbers m & n such that d(n)=m && d(m)=n
where d(x) = gives the sum of all real dividers of x (without x)

i hope it was clear, but even if not its not so important.
because i've defined a function to check with a number if it has an amice and it runs pretty well:

```

hasAmice :: Int -> Bool
hasAmice n	|n == howMany(howMany(n)) = True
		|otherwise = False	

```
it uses the howMany function which gives for a number the sum of its dividers, for example howMany(220)=284 , howMany(284)=220

the howMany function is defined as following, together with divCounter:

```

howMany :: Int -> Int
howMany 1 = 1
howMany n   |n<1 || mod n 1 /=0 = error "Only whole positive numbers please."
            |otherwise = divCounter n n 0                          	
			                                               	

divCounter :: Int -> Int -> Int -> Int               	
divCounter n m c	| m==0 = c               	
			| m==n = divCounter n (m-1) c
			| (mod n m == 0) = divCounter n (m-1) (c+m)
			| otherwise = divCounter n (m-1) c

```

until here everything works quite well, here are some examples from my console:

```

*Main> howMany 220
284
*Main> howMany 1
1
*Main> howMany 0
*** Exception: Only whole positive numbers please.
*Main> howMany 10000
14211
*Main> howMany 100000
146078
*Main> 

```

but now when i want to wrap it all together and sum all the amicables till 10,000 it gets all messy. I've defined the following function:

```

sumAmice :: Int -> Int
sumAmice n	|n==1 = 0
		|hasAmice n = n + sumAmice n-1
		|otherwise = sumAmice n-1

```

which works for values like 0 or 1, but from 2 on gives stack overflow:

```

*Main> sumAmice 1
0
*Main> sumAmice 0
*** Exception: Only whole positive numbers please.
*Main> sumAmice 2
*** Exception: stack overflow

```

this is very funny because sumAmice calles only hasAmice, which works okay, and itself. how come already from the value of 2 it starts to work exponentially????

any ideas?
ill be grateful for every tip or link or something about something i might have been missing here.

Many thanks ,

Amít

---

### Post by Alasdair on 2008-12-01
It's an operator precedence issue, you need brackets around the n-1 arguments to the sumAmice function calls, like so:
```
sumAmice :: Int -> Int
sumAmice n	
    | n == 1 = 0
    | hasAmice n = n + sumAmice (n-1)
    | otherwise = sumAmice (n-1)

```

> *Main> sumAmice 2
0
-- As an example:
*Main> (*2) 1+1
3
*Main> (*2) (1+1)
4


---

### Post by amityak on 2008-12-02
yeah, it works now... still a bit slow but i just have to improve my algorithm

Cheers!!

---

