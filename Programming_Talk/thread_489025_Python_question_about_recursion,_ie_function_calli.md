---
title: "Python question about recursion, ie function calling itself"
date: 2007-06-30
forum: Programming Talk
---

### Post by BeardlessForeigner on 2007-06-30
I've been messing with Python a bit for the past week now, and last night I started doing some of the problems from ProjectEuler.net. For problem 3 I wanted a function that would find the greatest prime factor of a number, and instead of trying to use while loops, I tried an iterative method used commonly in Structure and Interpretations of Computer Programs, which uses the Scheme variant of Lisp. My problem is I don't understand why my function should be limited by the Python recursion cap, or really how recursion works with Python. The fact that a recursion limit applies seems to indicate my function isn't iterative in the way my intuition says it would be. I have very little programming experience, basically a week of Python and a bit of reading SICP chap 1.

First, my Python code:
```

"""The prime factors of 13195 are 5, 7, 13 and 29.
What is the largest prime factor of the number 317584931803?"""

import sys
sys.setrecursionlimit(5000)

def gpf_helper(number, dvs):
	if number <= dvs:
		return number
	elif number % dvs == 0:
		return gpf_helper(number / dvs, dvs)
	else:
		return gpf_helper(number, dvs + 1)

def gpf(x):
	return gpf_helper(x, 2)

print "This program finds the greatest prime factor of a number."
number = input("Pick a number: ")
print "The greatest prime factor of %s is %s." % (number, gpf(number))

```

This works fine, but I have to up the recursion limit alot to do large numbers. I don't understand why though. The program runs very quickly, even for the large number 317584931803. What I want/expect from the bit of Scheme I've seen is for gpf_helper to be evaluated to gpf_helper with new arguments, a completely new function not inside of the original (and hence an iterative process). This wouldn't be limited by recursion levels at all. Is there a way to do this, or can anyone point me somewhere that discusses the recursion limit in Python?

I also translated the program into Scheme, although its more primitive since i only know a few basic functions. It merely returns the correct values for the two calls to gpf I put in and doesnt prompt the user:
```

(define (gpf_helper number dvs)
  (cond ((= number dvs) number)
	((= (remainder number dvs) 0)
	 (gpf_helper (/ number dvs)
		     dvs))
	(else (gpf_helper number
			  (+ dvs 1)))))

(define (gpf x)
  (gpf_helper x 2))

(gpf 13195)
(gpf 317584931803)

```

Thanks for any help! The long post should show how much fun/interest my programming exploits have so far given me!

---

### Post by Dancingwllamas on 2007-06-30
Good question.

When recursing with functions, the processor stores the function calls in a stack (basically, think of it as a storage box) until the end case is reached. Each time the function calls itself, a new call is placed onto the stack. For larger numbers, the function has to call itself more times in order to reach the end case. If your limit is set too low, the "box" is too small to contain all the function calls, so it never reaches the end case. Even though you can raise the limit in Python, there is a certain level where the processor runs out of storage space for the function calls.

Iterative solutions (like for loops) work differently because the processor does not need to store the function calls inside a stack. With for loops, you are typically writing stuff that takes up less space than function call information to your RAM which is a much larger storage space.

Hope this makes sense.

---

### Post by BeardlessForeigner on 2007-07-01
Yea, that makes sense. What got me wondering was that I sort of expected it would work as in Scheme, since with Scheme the code I wrote is iterative and does not in fact take up more and more memory storing all the calls within calls, but instead (gpf_helper 10 2) evaluates to (gpf_helper 5 2) which evaluates to 5. Is it generally thought better to just use loops for this stuff in Python?

---

### Post by Dancingwllamas on 2007-07-01
It's usually better to use loops in most programming languages (in my experience).  I haven't really done much with having computers calculate roots of numbers, so I have no idea if it is a situation where recursion is "better."

Recursion is really nice for situations when it makes the code very elegant. One example is traversing a binary search tree - you can make the traversing function just a few lines. Just remember to estimate how deep your recursion is going to go - if it is going to be huge for some of your planned workloads, you may need to go with an iterative solution to ensure you don't fill up your runtime stack despite how elegant the recursive algorithm is.

---

### Post by olejorgen on 2007-07-01
What you are asking is wheter python has "tail recursion"*. I do not belive it has, but I might be wrong.

*What makes schemes iterative recursion efficient

---

