---
title: "Problem with Euler problem 5"
date: 2008-10-12
forum: Programming Talk
---

### Post by sofiankrt on 2008-10-12
I've been trying to solve it since yesterday, and all I have come up with is:
```
from sys import *

def smallest_mutliple(limit):
	num = 1

	div = 1
	
	while div <= limit:
		div = 1
		while num % div  == 0:
			if div == limit:
				print num
				exit()
			else:
				div = div + 1
		while not(num % div == 0):
			num += 1

smallest_mutliple(10)


```

which works perfectly if the limit is ten, but spews out a cryptic error message for 20. Please don't tell me the answer, just some tips.

I appreciate any help. Thanks.

---

### Post by leg on 2008-10-12
If it is working for 10 but not twenty think about the size of the type you are using. I can tell you that the answer has 9 digits so if that won't fit into the type it will go wrong.

Also look into how the lowest common multiple is calculated using the greatest common divisor.

---

### Post by sofiankrt on 2008-10-12
Thanks!

Still doesn't work though. Here's what I did:
```
from sys import *

def smallest_mutliple(limit):
	num = 1
	
	long(num)

	div = 1
	
	long(div)
	
	while div <= limit:
		div = 1
		while num % div  == 0:
			if div == limit:
				print num
				exit()
			else:
				div += 1
		else:
			num += 1

smallest_mutliple(20)
```

Same result. 

Here's the error message:
```
Traceback (most recent call last):
  File "C:\Users\Sofian\bin\euler\euler4.py", line 25, in <module>
    smallest_mutliple(20)
  File "C:\Users\Sofian\bin\euler\euler4.py", line 16, in smallest_mutliple
    while num % div  == 0:
KeyboardInterrupt
```

---

### Post by sofiankrt on 2008-10-12
OMG! I can't believe how dumb I am! I just didn't give the computer enough time to "compute" it!

Anyway, I got the correct answer. Thanks. Code:

```
from sys import *

def smallest_mutliple(limit):
	num = 1

	div = 1
	
	while div <= limit:
		div = 1
		while num % div  == 0:
			if div == limit:
				print num
				exit()
			else:
				div += 1
		else:
			num += 1

smallest_mutliple(20)
```

---

### Post by meanburrito920 on 2008-10-12
Just as a reminder, applying long() to your variables does not change the value of that variable, it generates a new variable of type long with the value of the parameter. so instead of 

long(num)

you would want

num = long(num)

---

### Post by y-lee on 2008-10-12
> **sofiankrt said:**
> OMG! I can't believe how dumb I am! I just didn't give the computer enough time to "compute" it!



You can speed this code up *a lot* by thinking about it a little bit and applying what you already know. From the Project Euler Web site:

> 2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.

What is the smallest number that is evenly divisible by all of the numbers from 1 to 20?


So we know the result for 10 is 2520, why not use that knowledge:

[PHP]import sys

def smallest_mutliple(limit):
    if limit > 10 :
        num = inc = 2520
        divs = 11
    else:
        num = divs = inc = 1
        
    div = divs
    while div <= limit:
        div = divs
        while num % div  == 0:
            if div == limit:
                print num
                sys.exit()
            else:
                div += 1
        else:
            num += inc

smallest_mutliple(20)   [/PHP] 

That makes a big difference doesn't it. If you don't understand it think about it some.

But the best way to do it is to use some math know how:

[PHP]def gcd(a,b):
    while b:
        a, b = b, a % b
    return a 
    
print reduce(lambda a,b: a*b/gcd(a,b), range(1,21)) [/PHP]

:lolflag:

Edit: This is python Code btw :)

---

### Post by Sinkingships7 on 2008-10-12
I remember doing this problem a long time ago in C. This is the solution I came up with, showing only to help the OP think of a different way to do it:

```
[color=#408080][i]/* Project Euler: Problem 5
 * 
 * 2520 is the smallest number that can be divided by each 
 * of the numbers from 1 to 10 without any remainder.
 * What is the smallest number that is evenly divisible by all of the numbers from 1 to 20?
 */[/i][/color]
[color=#BC7A00]
#include <stdio.h>
[/color]
[color=#B00040]int[/color] main(){
    [color=#B00040]int[/color] check [color=#666666]=[/color] [color=#666666]1[/color];
    [color=#B00040]int[/color] x;
    [color=#008000]**for**[/color] (x [color=#666666]=[/color] [color=#666666]1[/color]; x [color=#666666]<=[/color] [color=#666666]20[/color]; x[color=#666666]++[/color]){
        [color=#008000]**if**[/color] (check [color=#666666]%[/color] x [color=#666666]!=[/color] [color=#666666]0[/color]){
            check[color=#666666]++[/color];
            x [color=#666666]=[/color] [color=#666666]0[/color];
            [color=#008000]**continue**[/color];
        }
    }
    printf([color=#BA2121]"%i"[/color], check);
    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---

### Post by pp. on 2008-10-12
> **y-lee said:**
> 
Edit: This is python Code btw :)

Yes, anyone can see that.

---

### Post by y-lee on 2008-10-12
> **pp. said:**
> [QUOTE=y-lee;5954008]Edit: This is python Code btw :)

Yes, anyone can see that.[/QUOTE]

:lolflag:

I would think so but someone ask me in IRC why I used PHP instead of perl. Well considering I don't know perl or php for that matter, I decided I would clarify :)

---

### Post by pp. on 2008-10-12
[off_topic]

> **y-lee said:**
> I would think so but someone ask me in IRC why I used PHP instead of perl. Well considering I don't know perl or php for that matter, I decided I would clarify :)

I replied to your comment the way I did because just a little while ago I mistook some code by LaRoza for a couple of spreadsheet functions when she actually wrote them as Python code snippets.

The person asking you for your reason to code PHP can in part understood because the code boxes are clearly labelled as *PHP code*.

[/off_topic]

---

### Post by Reiger on 2008-10-12
You can speed up code a lot further by:
-Realise that the number is divisible by *every* number in the range 1-20 (inclusive) any number in the range 1-10 (inclusive) is a factor of at least one number in the range 11-20 (inclusive). 

So we have the cases:
11, 13, 17,19 are primes.
20 covers any multiple of 5,10,20.
18,16,14 cover the multiples of 2,3,4,6,7,8,9.
Everything is divisible by 1, so that's irrelevant.

```

lcm20=head $ filter check [2520..]
check= \x -> and $ map (x `isDivisbleBy`) [11,13,14,16,17,18,19,20]
isDivisbleBy= \x y -> x `mod` y == 0

```

---

### Post by sofiankrt on 2008-10-13
Thanks!

So what you're basically doing (meanburrito) is, eliminating the test for numbers from 1 to 10, and instead of incrementing by one for numbers non-divisible by a number that's greater than 10 you increment by 2520, because anything less than that will not be divisible by one of the numbers from 1 to 10. Am I right?

I don't get the second approach.

---

### Post by y-lee on 2008-10-13
> **sofiankrt said:**
> Thanks!

So what you're basically doing (meanburrito) is, eliminating the test for numbers from 1 to 10, and instead of incrementing by one for numbers non-divisible by a number that's greater than 10 you increment by 2520, because anything less than that will not be divisible by one of the numbers from 1 to 10. Am I right?

I don't get the second approach.

I believe you are referring to [my post]("http://ubuntuforums.org/showpost.php?p=5954008&postcount=6") :) And indeed you are right in your analysis of my first program, I saw your post and thought it was an interesting problem. However your code ran *far* too slow for me and I like you was too impatient to wait on it. So i thought about how to speed it it up. In fact I rewrote it and below is my version of your brute force approach as I optimized it:

```
def test(result, limit, start):
    for num in range(start, limit +1):
        if result % num !=0:
            return False
    return True
 
def euler5(limit):
    result = 2520
    if limit > 10:
        start = 11
        inc = result
    else:
        start = inc = 1
    while True:
        if not test(result, limit, start): result += inc
        else: return result

print euler5(20)
```

Now my second approach:

```

def gcd(a,b):
    while b:
        a, b = b, a % b
    return a 
    
print reduce(lambda a,b: a*b/gcd(a,b), range(1,21))
```

does look a little mysterious, but it is the result of me trying to incorporate functional programming into the python I write. I will have to admit I am not particularly used to  that style of programming :)

But anyway my first version of this is perhaps a bit less mysterious:

```
def euler5_func(limit):
    return reduce(lcm, range(1, limit+1))   

# Euclidean gcd algorithm
#   returns Greatest Common Divisor of a and b
def gcd(a,b):
    while b:
        a, b = b, a % b
    return a 
    
# Lowest Common Multiple of a and b
#   returns the smallest number that is a multiple of both a and b.    
def lcm(a,b):
    return (a * b) / gcd(a,b)
    
print euler5_func(20)
```

First I make use of the fact the [least common multiple]("http://en.wikipedia.org/wiki/Least_common_multiple") of a and b can be expressed in terms of the greatest common divisor  of a, and b, namely lcm(a,b) = a*b/gcd(a,b). Now a very clever recursive algorithm to calculate the gcd of two numbers is well know and appears in [Euclid's Elements]("http://en.wikipedia.org/wiki/Euclid%27s_Elements") around 300 BC (Proposition 2, book 7).  Hence it is called the [Euclidean algorithm]("http://en.wikipedia.org/wiki/Euclidean_algorithm").

Now lets analysis the problem and start simple Consider only the case of finding the lowest number evenly divisible by the numbers 1 to 2, that is simply lcm(1,2) which is 2 .

Ok fine so far, now consider the case of [1,2,3] lcm of this list must be a multiple of lcm(1,2) since this list contains(1,2), hence we have lcm([1,2,3]) = lcm(lcm(1,2),3), if I may abuse my notation here a bit. hence lcm([1,2,3]) = lcm(2,3) = 6

and so for the case of the lcm of [1,2,3,4]

lcm(1,2,3,4) = lcm(lcm(lcm(1,2),3),4)
             = lcm(lcm(2,3),4)
             = lcm(6,4)
             = 12.
                    
By now I think you get the idea. In functional programming this is known as a [fold]("http://en.wikipedia.org/wiki/Fold_(higher-order_function)") and in python it is implemented by the reduce statement. And so the lcm([1,2,3, ..., 20]) in python becomes:

```
reduce(lcm, range(1, 21))
```

and by replacing lcm with a lambda because really it is almost too simple to implement, we end up with my second program:

```
def gcd(a,b):
    while b:
        a, b = b, a % b
    return a 
    
print reduce(lambda a,b: a*b/gcd(a,b), range(1,21))
```

Perhaps I could have optimized this yet a bit more but it seemed simple enough and I didn't want to further obscure the logic. But the lesson of all this analysis is that often programmers start coding before they think clearly about the problem and this leads to terrible inefficient code if not sloppy and unreadable code. In a commercial setting perhaps it makes economic sense, code some times produced sloppily and terrible inefficient in an hour verses think about it and research the problem for three days and then code it in 20 minutes. :guitar: 

I code for fun and not money so I don't care, I like my code to be pretty :)

And Reiger, pretty clever :) But pardon my ignorance, what language is this? Haskell? 

> **Reiger said:**
> You can speed up code a lot further by:

```

lcm20=head $ filter check [2520..]
check= \x -> and $ map (x `isDivisbleBy`) [11,13,14,16,17,18,19,20]
isDivisbleBy= \x y -> x `mod` y == 0

```

---

### Post by Reiger on 2008-10-13
Yup it's Haskell.

EDIT: And you can optimise by replacing ```
[2520..]
``` with: ```
iterate (+2520) 2520
```

In GHCi:
```

*Euler5> lcm20
232792560
(0.34 secs, 28080116 bytes)

```

EDIT: And implementing your code in Haskell is way faster:
```

*Euler5> foldl (\x y-> (x*y `div`) $ gcd x y) 1 [1..20]
232792560
(0.01 secs, 1049572 bytes)

```

And you can get slightly more peformance from reducing the list of factors to [11,12,13,14,16,17,18,19,20], as well as forcing foldl to be strict. (foldl).

```

*Euler5> foldl (\x y-> (x*y `div`) $! gcd x y) 1 [11,12,13,14,16,17,18,19,20]
232792560
(0.01 secs, 1573988 bytes)

```

---

### Post by y-lee on 2008-10-13
> **Reiger said:**
> Yup it's Haskell.

Cool :) Haskell is on my list of things to learn if i can get a grip on functional programming in python as well as grok what prolog is all about. I started coded some in prolog  a few days ago and it is sorta alien to my way of thinking about code. :lolflag:

---

### Post by pp. on 2008-10-13
> **y-lee said:**
> I started coded some in prolog  a few days ago and it is sorta alien to my way of thinking about code. 

Do not think of Prolog code as 'code' but of assertions. That way, many problems simply fall apart at their most natural boundaries or interfaces.

Well, there are a few properties of the language which spoil the fun. For one, the sequence of the assertions might matter (which would not apply to predicate calculus, I believe). Then, there's the 'cut' which controls backtracking. Lastly, of course, there are any predicates which have side effects.

In my experience, the greatest part of a Prolog project can indeed consist of merely listing assertions.

---

