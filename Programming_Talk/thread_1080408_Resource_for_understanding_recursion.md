---
title: "Resource for understanding recursion"
date: 2009-02-25
forum: Programming Talk
---

### Post by babyhuey on 2009-02-25
Anyone know of a good resource to learn recursion? I can't seem to fully get my head around it. I can follow the flow of execution of say...recursively printing binary search tree nodes in order but it still doesn't feel concrete.

I certainly don't understand it enough to actually think in terms of recursion, such as coming up with a solution to a problem recursively.

Thanks for the help.

---

### Post by geirha on 2009-02-25
Wikipedia has a fairly comprehensive article about it. [http://en.wikipedia.org/wiki/Recursion_(computer_science)](http://en.wikipedia.org/wiki/Recursion_(computer_science))

---

### Post by nvteighen on 2009-02-25
The trick in recursion is that you just tell what to do in the limit cases and then just prepare the data for the next round if no limit case is found. If you do that in that order, you'll get something called tail-recursion, which some languages can even recognize in order to optimize the code. But, apart from that, if you stick to that method, you may have a guide on how to write a recursive process.

---

### Post by simeon87 on 2009-02-25
Also, as a general rule, when information needs to be passed down to further in the recursive process, give it as arguments to the recursive call. When information needs to be passed upwards, give it as return value (when the recursive calls have reached the base case and they need to return).

Functional programming languages are also a good way to practice your recursion skills :)

---

### Post by nvteighen on 2009-02-26
> **simeon87 said:**
> 
Functional programming languages are also a good way to practice your recursion skills :)

+1

Specially those like Scheme that lack of native looping constructs, so you use recursion everywhere :) (well, you can write a macro and implement loops, if you want... that's Lisp's magic)

---

### Post by CptPicard on 2009-02-26
Interestingly, esp. in a purely functional language you can't even have a loop, as you can't have the index variable changing...

Here's a classic paper I found, that these "FP does not exist/has no merit" guys should take a look at ...

[http://www.cs.chalmers.se/~rjmh/Papers/whyfp.html](http://www.cs.chalmers.se/~rjmh/Papers/whyfp.html)

---

### Post by soltanis on 2009-02-26
If you want a very nice understanding on recursion, I suggest you read relevant discussions from a Lisp variant (Scheme has been suggested, Common Lisp is also helpful).

[http://www.lispers.org/](http://www.lispers.org/)

There's a book linked at the bottom of that page with a pretty good explanation of recursion.

---

### Post by Paul Miller on 2009-02-27
Well, you know the old saying:
> 
To understand recursion, first you must understand recursion.

While it's intended to be humorous, there's actually some truth to it.

Have you ever taken a math class and done a proof by induction?  Recursion and induction are very, very similar.  (And, as a teacher, I find math students have as much trouble with induction as CS students seem to have with recursion.)

There are two parts to any recursive function (and, by analogy, to any proof by induction).  The first part is where you handle a small instance or set of instances of the problem explicitly.

For example, here's the start of a recursive factorial in Python.  I'm going to eventually write the whole function, but without any error checking -- just assume that the function is always called with n being a nonnegative integer.

[php]
def fact (n):
    if n == 0 or n == 1: return 1
[/php]

This function doesn't work unless n is either 0 or 1, but we'll put in the code to handle larger numbers later.

The second part of a recursive function is where, having handled all the "small" cases, you now know that if control has gotten this far, you're now in one of the "large" cases.  In our factorial example, the "large" instances would be those for which n > 1.

The goal in this case is to reduce a "large" instance to a "smaller" instance, so that eventually the problem will be reduced to one of the "small" instances you explicitly handled in the beginning.  With that in mind, here is the full code for the recursive factorial in Python:

[php]
def fact (n):
    if n == 0 or n == 1: return 1
    else               : return n * fact (n-1)
[/php]

(Note: funky formatting is to highlight the logical structure of the function.)

Now, notice how in the "large" case, yes, you're making another call to the function, but with a smaller value of the parameter.  And, eventually, no matter what the value of n is to begin with, it'll get down to n=1, where you'll return an explicit value.  Once that happens, all the recursive calls in the chain will start to return, and you'll get your answer after all n of them return.

Does that make sense?

---

### Post by ps2key on 2009-06-08
Question
I'm a programming newbie.
I "basically" understand the recursion here. What I was having trouble with was how the value of "n" was increasing back up to sum the final factorial output(answer). I was stuck because it looked like "n" would be passed as (n-1) until it meant that 1-1 would be sent to the final recursive call making "n" = 1. Since 1*1=1, the function had nothing in it that would change "n" from 1 to any other value. I think I may have finally figured it out. I thought that when the function's parameter value changed due to what was passed to it, the parameter's value would be set to match throughout the entire function code. Now I see that if the conditional if: statement is true (see code), it returns 1 to the last recursion but the value of the parameter in the if:condition fork doesn't get passed along to the else: fork because the if:condition fork ended before doing so. Therefore "n" is still = 2 from the previous recursion. Am I correct? Thank you in advance.
```
#! /usr/bin/python

def factorial(n):
    if n <= 1:
        return 1
    else:
        return = n * factorial(n-1)
        
print factorial(4)

```

---

### Post by Reiger on 2009-06-09
The trick with recursion is that you must separate 'the now' from 'the future' and 'the past'. To see this mentally unwind the function calls like so:
```

# incidentally a broken definition of factorials
def factorial(n) :
   if n <= 1 :
     return 1
   else :
     return n * factorial (n-1)

print factorial (3)

```

Becomes:

print ( factorial(3) )

Becomes : 

print ( 3 * ( factorial (2) ) )

Becomes : 

print ( 3 * ( 2 * ( factorial (1) ) ) ) 

Becomes :

print ( 3 * ( 2 * ( 1 ) ) )

Becomes :

print ( 3 * ( 2 ) )

Becomes :

print ( 6 )

---

### Post by Reiger on 2009-06-09
> **ps2key said:**
> Now I see that if the conditional if: statement is true (see code), it returns 1 to the last recursion but the value of the parameter in the if:condition fork doesn't get passed along to the else: fork because the if:condition fork ended before doing so. Therefore "n" is still = 2 from the previous recursion. Am I correct? Thank you in advance.

No. Consider the various states of the program I wrote down earlier (mentally unwinding the function calls):

We have a function call print: in this case it is passed an *integer* argument. What is the value of the integer argument? factorial(3). But print() never knows that it receives `factorial(3)' as argument: all it will ever encounter is the value (6). At the moment we are `inside print' both `this specific call to factorial' and `3' are history: no longer accessible to the pogram. This is because the arguments to a function a resolved *before* the function receives them.

When you apply the same reasoning to the non-base case factorial(2) we end up with the value `2 * factorial(1)'. `factorial(1)' is at that point not yet resolved, so we kick off a *new* call to `factorial' with argument 1 to find out. When we are in factorial(1) we do not know anything about any prior factorial call: that is _history_. Inaccessible, locked off. You cannot therefore modify something in factorial(2) when inside factorial(1) because you don't know (and never could be sure as one might call factorial(1) from elsewhere) _that_ you came from factorial(2) (and you don't have any means of accessing that information or that function call). 

On the upside of no-outside-world-information: that means you need never worry about what the variable n means to something _outside_ of your _current_ call to factorial: this is encapsulation (locking away) at its finest. 

Note that *yes* there are (sometimes useful) ways around that: it is possible for recursive functions to modify a global datastructure (think about a sorting algorithm of a tree structure) in imperative languages. (But not in pure functional languages which forbid that kind of side effect so in those cases you would return a new data structure.)

---

### Post by ps2key on 2009-06-09
Thank you very much Reiger. It makes perfect sense now.

 Also thanks to Paul Miller for his post just prior to mine. I reread it and picked up on this; 

"Once that happens, all the recursive calls in the chain will start to return, and you'll get your answer after all n of them return."

---

