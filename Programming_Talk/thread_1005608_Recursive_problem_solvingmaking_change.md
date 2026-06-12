---
title: "Recursive problem solving/making change"
date: 2008-12-08
forum: Programming Talk
---

### Post by luke77 on 2008-12-08
Hi guys,

I'm trying to solve problems recursively and it is very frustrating. My goal is to develop a program that, given a set of coin values (like 100,25,10,5,1) and an amount of money, outputs all possible change combinations that can be used to make change. Not the number of possible combinations, but the actual combinations themselves.

So anyways, it seems like this problem lends itself to recursive processes, so I need to develop a base case and then a set of methods to reduce larger cases to this base case. I'm having trouble with this design, because I am not used to thinking in recursion. 

The function should look something like:

```
makeChange(amount,coins):

coinVal = coins[0]
otherCoins=coins[1:]

if amount<coinVal:
return makeChange(amount,otherCoins)

if amount = coinval:
return [coinVal]
```

Then, as the "else" clause handling everything else, I could say:```


else: 
return ([coinVal] + makeChange((amount-coinVal),coins))
```

Now, this function would sort of begin to address the problem I really want to solve, but it only makes "optimal" change for a given value. I need to find every single combination. I *could *create a list of combinations, and then when a combination is generated test to see whether it is in the list, and if not change some parameter and call the function again, but this seems overly complicated and I'm not sure how I would implement it.

So, I'm stumped. I can express the solution in plain English: "If the amount of money is greater than or equal to the largest coin, subtract the amount of the largest coin from the total, then run the test using the adjusted total and the same set of coins. If the total is less than the largest coin, remove the largest coin and test with the adjusted list of coins." This is the problem that my current function solves (I think).

Then, in plain English, the rest of the solution: "For each coin in the solution set, generate all possible combinations of change that can make up this value". In other words, if my total is 30 cents, the "best" answer is (25,5). Then, we can reduce 25 to (10,10,5),(10,10,1,1,1,1,1),(10,5,5,5),etc....and for each of these new combinations of 25, we can also create the "5" in the original solution with either (5) or (1,1,1,1,1). Clearly for larger values it gets exponentially more complicated. But even this does not address all solutions, because what if we did not use a quarter in the original solution, and instead used (10,10,10)? Simply coming up with the optimal solution and then reducing it would not come up with this solution. 

You get the point. I am sure I am overthinking this, but I am pretty frustrated. Can someone suggest how I should be thinking about this in simpler terms?

Also, to step back from this problem; in larger terms, how do you "think about" more complicated recursive problems like this? This problem is not that complex and I'm having trouble coming up with a plan to solve it. Clearly I need to have a different framework to address these problems.



Thanks for any advice.

---

### Post by pp. on 2008-12-08
Don't look too far for a solution. Think about how you would solve the problem using ***pencil and paper***. 

Let's say your that [10, 5, 2, 1] was list of your denominations. Let's say that you wanted to list all possible ways to change an amount of 10.

In order to make sure that you hit on each combination, but on each only once, you'd need  an orderly way of enumerating all combinations. An obvious way would consist of starting with the largest coin wich does not exceed the wanted sum.

So you start with the largest coin, enumerate all the possible ways to change the rest (the original sum minus the largest coin). 

Once you have exhausted all combinations which include the largest coin, you use the second largest coin and enumerate all the possible ways to change the rest again. This time, the largest coin used for the rest can not be larger than the one used 'before' the rest.

That would yield a list like

10
5, 5
5, 2, 2, 1
5. 2, 1, 1, 1
5, 1, ...

---

### Post by dribeas on 2008-12-08
While the solution provided is correct and good for learning, if you plan on using the code above, you should consider that there are some partial results that will get calculated many times. You could consider using [memoization]("http://en.wikipedia.org/wiki/Memoization") as a way of avoiding the repeated calculations.

---

### Post by nvteighen on 2008-12-08
Recursion is about splitting a problem in smaller parts and applying the same solution to solve those parts. It's a "take and pass" mechanism: select something from somewhere, analyze... if it works, take the item and return. If further splitting is needed, we pass stuff to another round.

Basically, a correctly written recursive process should never lead to more complexity in the arguments passed, but to less. If you see you're passing more complex stuff, you may be mistaken... or even using a recursion where there is none.

---

### Post by luke77 on 2008-12-08
> **pp. said:**
> Don't look too far for a solution. Think about how you would solve the problem using ***pencil and paper***. 

Let's say your that [10, 5, 2, 1] was list of your denominations. Let's say that you wanted to list all possible ways to change an amount of 10.

In order to make sure that you hit on each combination, but on each only once, you'd need  an orderly way of enumerating all combinations. An obvious way would consist of starting with the largest coin wich does not exceed the wanted sum.

So you start with the largest coin, enumerate all the possible ways to change the rest (the original sum minus the largest coin). 

Once you have exhausted all combinations which include the largest coin, you use the second largest coin and enumerate all the possible ways to change the rest again. This time, the largest coin used for the rest can not be larger than the one used 'before' the rest.

That would yield a list like

10
5, 5
5, 2, 2, 1
5. 2, 1, 1, 1
5, 1, ...

Thanks for the responses. Okay, this makes sense, and actually this is how I was thinking about things before I confused myself. If think my problem lies in changing the "Plain English" into an algorythm. Here's my attempt to translate what you wrote:
```

makeChange (total,coins):

coinVal = coins[0]
tail=coins[1:]

if tail==[]:
return 

if total<coinVal:
return makeChange(total,tail)

else:
return [coinVal] + (makeChange (total-coinVal,coins))
```

This is essentially what I wrote previously, except I'm leaving out the line: 

```
if amount = coinval:
return [coinVal]
```

Am I correct so far?

I'm reading back over what I wrote originally and I realize I was thinking incorrectly when I said that this method wouldn't cover stuff like making change for 30 c with (10,10,10). But still, this solution does not do anything but compute the "optimal" solution. So I'm not really translating what you wrote into code. I need a way to save the optimal solution, and then move on to compute additional solutions. IOW, using your example of changing 10 with [10, 5, 2, 1], my function would just return [10]. How do I move from returning only the ideal solution to returning every solution?

Thanks again.

---

### Post by pp. on 2008-12-09
The solution you are thinking of generates just one list of coins for any given value, as you observed yourself.

You have correctly identified that you just take one coin and then recursively solve the problem for the remaining amount.

But there's a "second dimension" in your problem: after picking a coin for one amount (and finding all combinations of coins for the remaining amount) you should repeat the procedure with the next coin. In the example above, that would be '10' at first, then '5' (for the first coin) plus all combinations yielding the remainder of 5.

You can do the second dimension either as an iteration or as a recursion, but choosing to do it as a recursion might further confuse you.

I carefully abstain from commenting on your code. Did you try to solve some sample problems using pencil, paper and an adequate supply of coins?

---

### Post by luke77 on 2008-12-09
> **pp. said:**
> The solution you are thinking of generates just one list of coins for any given value, as you observed yourself.

You have correctly identified that you just take one coin and then recursively solve the problem for the remaining amount.

But there's a "second dimension" in your problem: after picking a coin for one amount (and finding all combinations of coins for the remaining amount) you should repeat the procedure with the next coin. In the example above, that would be '10' at first, then '5' (for the first coin) plus all combinations yielding the remainder of 5.

You can do the second dimension either as an iteration or as a recursion, but choosing to do it as a recursion might further confuse you.

I carefully abstain from commenting on your code. Did you try to solve some sample problems using pencil, paper and an adequate supply of coins?


Thanks. I understand the solution conceptually; my problem is that I can't figure out how to implement it. For instance, if I try doing the second dimension iteratively as you suggest, this is the code I came up with:

```
b=[10,5,2,1] 
cnt=0
for i in range(len(b)):
    print makeChange(10,b[cnt:]))
    cnt+=1

```

This solves using the complete set, then the complete set minus the largest coin, then minus the first two coins, etc. But the solution is still incorrect: it computes only the "optimal" solution for each set. So here are the solutions using this code:
```

[10]
[5, 5]
[2, 2, 2, 2, 2]
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
```

It excludes nonideal solutions like [5,2,2,1], [5,2,1,1,1], etc. There is some step that I am leaving out that must account for these possibilities, but I cannot figure out what it is. My problem isn't understanding what the solutions are; it is in translating into code.

---

### Post by dribeas on 2008-12-09
> **luke77 said:**
> So here are the solutions using this code:
```

[10]
[5, 5]
[2, 2, 2, 2, 2]
[1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
```

It excludes nonideal solutions like [5,2,2,1], [5,2,1,1,1], etc. There is some step that I am leaving out that must account for these possibilities, but I cannot figure out what it is. My problem isn't understanding what the solutions are; it is in translating into code.

You are quite a step ahead. You only need to figure now how to finish getting to all solutions. Consider that to provide all the solutions you want to try first with as many possible coins of the higher value. Then You could use just one less coin of that higher value and try to solve the problem of finding the change for the amount pending (this time without using any other higher valued coin for that part of the result.

That is: first try with as many of the highest value: 10: [10]; then use one less of that value and try with as many of the second largest value 5: [5, 5], then with one less of the second largest value and try to find all solutions for the remainder: [ 5, ... ], where ... are all possible solutions to giving 5 worth of change with just 2's and 1's.

---

### Post by luke77 on 2008-12-09
> **dribeas said:**
> You are quite a step ahead. You only need to figure now how to finish getting to all solutions. Consider that to provide all the solutions you want to try first with as many possible coins of the higher value. Then You could use just one less coin of that higher value and try to solve the problem of finding the change for the amount pending (this time without using any other higher valued coin for that part of the result.

That is: first try with as many of the highest value: 10: [10]; then use one less of that value and try with as many of the second largest value 5: [5, 5], then with one less of the second largest value and try to find all solutions for the remainder: [ 5, ... ], where ... are all possible solutions to giving 5 worth of change with just 2's and 1's.

This makes perfect sense; I just don't know how to implement it. I can intuitively think, "OK, I want to use one less of the highest value and find solutions for the remainder", but I can't figure out how to code it, because the code needs to repeat this for each "next smaller" value. This suggests a recursive process, but I am stuck...

---

### Post by pp. on 2008-12-09
OK, let's reduce the problem.

First step: Given the list of denominations (different coin values) in a given currency, e.g.: [100, 50, 20, 10, 5, 2, 1]

Note that each value occurs exactly once because it's just a list of coin types.

Starting with the full list, print a series of lists of decreasing lengths, where each list is the same as the preceding one but without the largest (first) value.

The result ought to look something like:
[100, 50, 20, 10, 5, 2, 1]
[50, 20, 10, 5, 2, 1]
...(omitted, through)..
[2,1]
[1]

Write a program which produces that "list of lists", using a recursive algorithm or procedure.

---

### Post by luke77 on 2008-12-09
OK. To print all combos:
```

def changeCombos(coinlst):
    if coinlst==[]:
        return []
    print coinlst
    return changeCombos(coinlst[1:])
```

or to return a list of combos:
```

def changeCombos(coinlst):
    if coinlst==[]:
        return []
    
    return [coinlst] + changeCombos(coinlst[1:])
```

Correct?

---

### Post by pp. on 2008-12-10
[QUOTE=luke77;6339532]OK. To print all combos:
```

def changeCombos(coinlst):
    if coinlst==[]:
        return []
    print coinlst
    return changeCombos(coinlst[1:])
```

Now we're getting someplace.

Criticism (i.e. things that I think could be improved). Please understand that these are just tips of the trade which will be of value for your own education. They do not prevent the function from working.

The function should have but one place where it returns to the caller. Thats not all that important in such a short bit of code. Its importance grows with the length of the code.

I don't think that the function should return anything at all. That's beyond the spec, and in a later phase of development or maintenance you might start to wonder where and why the return value might be used.

The name of the function ("changeCombo") is a bit misleading at this point in time. However, as you presently will add that task to your function, we'll let it stand.

EDIT: Did you try and run that program? If not, I'd suggest to do so.

---

### Post by mssever on 2008-12-10
> **pp. said:**
> I don't think that the function should return anything at all.
Point of clarification: All Python functions return an object. If you don't provide an explicit return object, they implicitly return None.

---

### Post by luke77 on 2008-12-10
OK, so a better function might look like this:
```

def changeCombos(coinlst):
    if coinlst==[]:
        return []
    print coinlst
    changeCombos(coinlst[1:])
```

---

### Post by pp. on 2008-12-10
> **mssever said:**
> Point of clarification: All Python functions return an object. If you don't provide an explicit return object, they implicitly return None.

Thanks for the clarification. In that case, I think it's better to return NONE instead of some computed value, if only because you won't dare at a later time changing the result of the function without carefully perusing all clients of the function.

> **luke77 said:**
> OK, so a better function might look like this:
```

def changeCombos(coinlst):
    if coinlst==[]:
        return []
    print coinlst
    changeCombos(coinlst[1:])
```

Yes, or even

```
def printCoinLists(coinList):
    if !(coinList==[])
        print coinList
    printCoinLists(coinList[1:])
```

(not sure about the condition in the if statement as I don't know any Python at all)

---

### Post by luke77 on 2008-12-10
How does this help though? My original problem still exists: I still am only generating "ideal" solutions; this function wouldn't generate, for instance, the solution [10,10,10], or [10,10,1,1,1,1,1,1,1,1,1,1] to make change for 30 cents. I'm not sure how I would link this into the problem that I am addressing.

---

### Post by nvteighen on 2008-12-10
If I've been following this correctly, you may have this conceptual issue: you're destroying the "coins" list at each recursion (well, recursions are destructive...) and therefore, you can't check all possibilities. And you get the ideal ones just because you have a sorted list; try using an unsorted coins list and you'll surely get some weird result.

I had, some time ago, a problem with a similar structure: a recursion where some data has to remain constant through each new recursion... the langauge was C, so I could use a "static" variable which is actually a sort of low-level trick related to how programs are loaded into memory... 

In Python you don't have that and the temptation to use a global variable is big... Maybe, wrapping the recursion into a local function (function declared inside another) and declaring that coins list outside of it you get a kind of "global" variable... Then, you just make copies of that list inside the recursion when needed and, if exhausted, you can get the whole thing again.

The reasonale behind this is because while I was doing this in Scheme (a Lisp dialect that favors the use of recursion) I needed something called "closure"... it's a funny way to construct functions on the fly. In Python you have a limited-hidden way to write such, which is the local function (the other is the explicit lambda closure, but in Python it is annoyingly limited to one line of code).

---

### Post by dribeas on 2008-12-10
> **luke77 said:**
> How does this help though? My original problem still exists: I still am only generating "ideal" solutions; this function wouldn't generate, for instance, the solution [10,10,10], or [10,10,1,1,1,1,1,1,1,1,1,1] to make change for 30 cents. I'm not sure how I would link this into the problem that I am addressing.

We can keep going around the problem for a while or we can try to hit it right on. First with a mixed iterative + recursive approach and then, left as exercise you can try to translate it to a purely recursive approach.

Input:
value: value to return
coins: coin denominations not yet used (initially all denominations ordered)
solution: list of coins selected for the partial solution (initially an empty list)

With those inputs, you take the higher valued coin (denomination1) and divide the value to return by the coin denomination. All solutions will have a number of coins from that denomination from 0 to n, being n = value / denomination1.

Now, if you choose n - highest valued coins, then you have to solve a subproblem: return value-(n * denomination1) worth of change with the subset of denominations that does not include denomination1. In each recursive call, you have to add the coins used to the partial solution.

Example: 
value = 5
denominations = [ 10, 5, 2, 1 ] 
solution = []

```

change( 5, [ 10, 5, 2, 1 ], [] ):
  division 5 / 10 = 0 (integer division), thus no 10's
  change( 5, [ 5, 2, 1 ], [] ):
    division is 1, we can use either 1 or no 5 coins.
    change( 0, [ 2, 1 ], [ 5 ] ): 
      value is 0, stop condition 1, we have a solution: [5]
    change( 5, [ 2, 1 ], [] ):
      division is 2, we can use 0, 1 or 2 coins of face value 2
      change( 1, [ 1 ], [ 2, 2 ] ):
        division is 1 [*]
        change( 0, [], [ 2, 2, 1 ] ):
          value is 0, stop condition 1, we have a solution [2, 2, 1]
        change( 1, [], [ 2, 2 ] ): using 0 coins of value 1
          value is not 0, but denominations is empty: stop condition: this is no solution
      change( 3, [ 1 ], [ 2 ] ):
        division is 3:  we can use 0, 1, 2 or 3 coins of face value 1

```

The different levels of indentation imply recursion, while lines at the same level represent iteration. At the point marked with [*] you could use a special branch in your code to detect that there is just one coin and thus the only solution is providing full change with just that one denomination. Else, you can use the proposed method of recurring with an empty set of denominations, that is marked as error if the value to return is not zero.

Implementing this should be straight forward in your language of choice.

---

### Post by pp. on 2008-12-10
You might want to remember the verbal solution I gave in some earlier post. Part of that solution consisted of producing a sorted list of change combinations, starting with the largest possible coin, and then proceeding to the smaller change.

I'd suggest now to write a solution to another subset of your problem.

Given: a list of denominations or coin values "valueList", e.g. [100, 50, 20, 10, 5, 2, 1], same as in last part.
Given an amount to change, which is a positive integer, call it "amount".

Since we want to generate all possible combinations of coins which can express the chosen amount, we will at first produce a list of all possible values for just the first coin in each combination.

For the valueList given above and an amount of 9, the output would be printed as
[5]
[2]
[1]

Write a function which does exactly that.

After writing and debugging that function, try and find where you have to expand the specification to obtain a more complete solution to your original problem.

---

### Post by luke77 on 2008-12-10
I feel like I'm getting close but I'm not there yet. I read dribeas' latest post and wrote the following :

```
def makeChange (value,denominations,solution):

    if denominations==[]: #No coins left, return []
        return []
    if value==0: #Change has been made, return []
        return []

    firstCoin = denominations[0]
    tail=denominations[1:]
    
    n = value / firstCoin

     
    if n<1: #The first coin is larger than the value, so try with the next largest coin

        makeChange(value,tail,solution)
    
#if n is greater than 1, try making change with the total minus 
#the maximum number of the first coin that can be used, and all #remaining coins. Add the number of the first coin used to the #solution (?)
#Then, make change WITHOUT using the first coin.


    return makeChange((value - (n * firstCoin)),tail, solution+[firstCoin*n])      +  makeChange(value ,tail, solution)
```


This looks pretty ugly and is not quite correct; I am trying to follow the "rules" you set out but am missing something.

While writing this post, I read pp.'s post and after thinking about it thought that I had found my problem, but I haven't. To solve pp.'s simpler problem:

```
def firstVals(value,valueList):

if valueList==[]:
return []
first = valueList[0]
print first

firstVals(value-first,valueList)
```


This does break the problem up into a simpler solution, and I can see what you guys are suggesting. It's incredibly frustrating because I know what I want to do, I just have not been able to actually implement it. 

Using pp.'s example, it's pretty simple to see that the solution is:

"To make all combinations, use the first value of the valueList that is smaller than the value, then make all combinations using that value and (total-value). ALSO, make all combinations NOT using the value."

I thought that that is what I was writing, I just am not getting correct results...

Thanks again for the help; sorry I'm not "getting it" so far...

---

### Post by dribeas on 2008-12-11
First, forget about returning anything, just for the sake of it. Provide the solution to the screen with a print statement.

```

def makeChange (value,denominations,solution):
    if value==0: # first, if solution is valid print tit and return
        print "Found solution: ", solution
        return
    if denominations==[]: # this is not a valid solution
        return

    firstCoin = denominations[0]
    tail = denominations[1:]

    n = value / firstCoin

    for ix in range( 0, n ):
        i = n - ix      # I'm sure python has better constructs for this
        partial = solution[:]   # Calculate partial (possible) solution
        partial.append( [ firstCoin, i ] )
        makeChange( value - (i*firstCoin), tail, partial )
    makeChange( value, tail, solution )

```

The description of the code:

First you check the end conditions: 
value == 0, we have a solution: print it; no more denominations then thats no solution [*]

Then extract the current denomination and calculate the remainder denominations and how many coins of that denomination can be used at most in a solution.

Now we can solve a smaller problems. Calling i the number of coins of the current denomination to use, our subproblem is calculating the change we must provide if we use that number of coins. Each subproblem cannot use the current denomination (we have excluded it from the list) and the change to provide depends on the value not yet returned. With each recursive call we add a pair [denomination, number_coins] to the current partial solution.


[*] This check can be pushed to the caller. Once you hit the lower denomination value (last one in the list) you can divide the value against the denomination. If there is no remainder you must use that many coins. If there is a remainder the problem cannot be solved and you need to backtrack and choose a different set of coins for the other denominations. Note that with this list of denominations (last value is the unit) there will never be a remainder.

---

### Post by luke77 on 2008-12-11
Thank you, this works exactly as it should. I modified one line to make it easier to read (for me):
```

partial.append( [firstCoin]* i )
```

instead of:

```
partial.append( [ firstCoin, i ] )
```

Is there a good way to think about problems such as these to make them more clear or easier to solve, or is it simply a matter of working lots of problems until you get it? Even reading though this code, if I attempt to follow the progression of the problem, I start confusing myself after about the third or fourth recursive call, even using a fairly simple set of coins.

---

### Post by pp. on 2008-12-11
> **luke77 said:**
> Is there a good way to think about problems such as these to make them more clear or easier to solve, or is it simply a matter of working lots of problems until you get it? Even reading though this code, if I attempt to follow the progression of the problem, I start confusing myself after about the third or fourth recursive call, even using a fairly simple set of coins.

There are several things you can "condition" yourself to do.

(1) I'd be willing to place a (very small) bet that you ignored my suggestion to actually solve a few cases using pencil and paper. I was very earnest in suggesting that, as you can gain quite a few insights into the problem you want your program to solve.

(2) I've already suggested this in another place: you are trying to understand the problem in 'procedural' terms. That means that you describe steps your program is to take in such and such circumstance, and the you try to follow your program for a number of such steps. No wonder you become confused.

I find it much easier to just think in terms of the desired results without - at first - bothering to think about any steps to be taken in order to produce that result.

Let's apply this kind of thinking to the money changing procedure. Perhaps you want to refer back to some of my explanations earlier in this thread for alternate descriptions of the same stuff.

First, I observe that (typically) the valid combinations of change for a given amount come in "groups". All combinations in one group have the same largest coin. Since we want to list the combinations (solutions) sorted by the largest coin in the solution, and in descending order, we can give a first coarse description of the result to be produced by the procedure:

The resulting set is 
[LIST]
[*]first a group of all combinations containing the largest denomination in the list of values, 
[*]followed by the resulting set of all combinations giving the same amount but consisting of denominations without the largest value.
[/LIST]

I think that cumbersome definition is not all that hard to arrive at. It does, however, show quite clearly where the recursion comes into play.

It also has a slight problem when we want to implement it as a computer program: we didn't specify when or how the computer should recognize that the work is done.

Hence, we have to think of a clever terminating case. Obviously, if we have no coins, we can not change any amount (with the exception of zero cents). 

So far, we have solved the one problem your first attempts did not address: we have created a mechanism which ought to produce all solutions and not just the first one.

In similar fashion, we can proceed to describe the groups mentioned above in terms of combinations and/or individual coins.

A "group" is a number of solutions for the list of values V where 
the [LIST]
[*]first value of the solution is the largest value in V and 
[*]the rest of the solution is the amount to be changed minus the largest value in V. [/list]

I have left a few ragged edges since I don't believe in handing out complete solutions.

---

### Post by dribeas on 2008-12-11
First things first: you must follow **pp** advice. A professor of mine used to say that if you cannot provide a solution with pen an paper, if you cannot determine the process with just pen and paper, there is no possible way of automating/programming a solution.
In none of my algorithm classes have I used a computer, all problems were solved with pen and paper, and moreover, pseudo-code was used just as a compact way of expressing ideas. Most of the work was done in plain writting describing what you do and proving that it is correct (correct, complete, terminating or some subset of the three)

In general, for recursive problems you have two parts: the stop condition and the recursive call. 

Stop conditions are situations where you already have an answer or you know that you will not find it in this search path, so that you must backtrack.

The recursion is all about reducing your problem to a smaller problem that is exactly equivalent to the problem you have at hand. At this point it sometimes helps 'believing' in your solution. Much like a proof by induction: you assume that your algorithm is already working perfectly all the smaller problems.

Once you have the recursion step defined you know you have a solution. The last step is tweaking the interface so that you can inject/extract the solution for further use.

Your original problem is not trivial, so don't worry if that problem did not just pop to mind.

Now, going back to the problem (forgetting about the solutions themselves and just focusing on the rationale). Your problem has two inputs: value, denominations, so you can get to a first approach to a solution:

```

def change( value, denominations ):
   # stop conditions
   # recursive solution to smaller problems

```

Stop conditions are easy in your problem: if value is 0 it is a solution, if value != 0 and there are no denominations then no solution can be found.

```

def change( value, denominations ):
   if ( value == 0 ):
      #found it
      print "Found solution" 
      return
   if ( denominations == [] ):
      print "No solution"
      return
   # recursive solution to smaller problems

```

You must try to reduce the problem into something that hits the stop conditions. That can be achieved by reducing value or by reducing the denominations list and using the current denomination to actually reduce value.

Now its time to reduce the problem. You select your higher denomination, and what can you do with it? The set of solutions will contain a number of coins of your current denomination, how many? Any number from 0 to floor( value/denomination ), each one of those options actually reducing your original problem to a different problem, so you must test all those options:

If you select no coins of this denomination your subproblem is finding the same value as inputed but with a smaller set of denominations (check here that you always get closer to the stop conditions, else you are not really reducing the problem but changing it). If your algorithm is correct you can assume that the recursive step will work its way perfectly and return.

If you select 1 coin of the current denomination your subproblem will be finding change for (value-denomination[0]) with the set of (denominations[1:]).

Now you can prove that your algorithm's correctness:

- You only consider a solution if your remainder value has gone down to 0, else you backtrack

You can prove that it is complete:

- At each step of recursion, all solutions will use 0..(value/denomination[0]) coins of denomination[0] value. Using less coins is impossible, using more will give more change than required.

And finally you can prove that the algorithm is terminating:

- In each recursion step the problem is reduced, the list of denominations is strictly smaller and thus will hit either the first or second stop conditions at one time or another.

The very last step of your algorithm is really providing the solution you have found. Here experience (and requirements) help.

---

### Post by luke77 on 2008-12-12
This is very helpful, thanks.

---

### Post by Barbas06 on 2008-12-22
Hey guys sorry,  for the bump here but I'm trying to find an algorithm that uses Dynamic Programming to solve this problem and i'm kind of stuck. Also i didn't quite understand the recursive algorithm that is used/proposed by the guys here, any help?
Thanks!

---

### Post by namegame on 2008-12-22
> **Barbas06 said:**
> Hey guys sorry,  for the bump here but I'm trying to find an algorithm that uses Dynamic Programming to solve this problem and i'm kind of stuck. Also i didn't quite understand the recursive algorithm that is used/proposed by the guys here, any help?
Thanks!

You'd be better off making a new post.

---

