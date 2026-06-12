---
title: "[SOLVED] Is Floyd's cycle detection algorithm fool proof?"
date: 2008-07-21
forum: Programming Talk
---

### Post by MdaG on 2008-07-21
I'm tring to implement Floyds cycle detection algorithm and it seems to work fine for "most" sequences, but I've detected that there are some that it cannot do correctly.

ex.) 1/23 = 0.04347826086956521739130434782608695652173913043478... = 0.(0434782608695652173913) meaning that the number within the parenthesis loop infinitely.

However when I use [Floyd's algorithm]("http://en.wikipedia.org/wiki/Cycle_detection#cite_note-0") it gives the answer 1/23 = 0.(04347826).

Now I'm pretty sure it's just me that hasn't implemented this correctly, but as other sequences are detected just fine I might need some help finding out where my error lie.

Running my code yields the following output:
```
1/2 = 0.5
1/3 = 0.(3) lambda = 1 mu = 0
1/4 = 0.25
1/5 = 0.2
1/6 = 0.1(6) lambda = 1 mu = 1
1/7 = 0.(142857) lambda = 6 mu = 0
1/8 = 0.125
1/9 = 0.(1) lambda = 1 mu = 0
1/10 = 0.1
1/11 = 0.(09) lambda = 2 mu = 0
1/12 = 0.08(3) lambda = 1 mu = 2
1/13 = 0.(076923) lambda = 6 mu = 0
1/14 = 0.0(714285) lambda = 6 mu = 1
1/15 = 0.0(6) lambda = 1 mu = 1
1/16 = 0.0625
1/17 = 0.(0588235294117647) lambda = 16 mu = 0
1/18 = 0.0(5) lambda = 1 mu = 1
1/19 = 0.(052631578947368421) lambda = 18 mu = 0
1/20 = 0.05
1/21 = 0.(047619) lambda = 6 mu = 0
1/22 = 0.0(45) lambda = 2 mu = 1
Error! Algorithm contains at least one bug!
1/23 could not be calculated.
```


Here's my python implementation:
```
#! /usr/bin/env python

from decimal import *

def getRecurringCycle(x):  # Using Floyd's cycle detection algorithm
   # Only proceed if there are enough decimal numbers to actually find a large cycle
   if len(x) > 100:
      # The main phase of the algorithm, finding a repetition x_nu = x_2nu
      # The hare moves twice as quickly as the turtle
      turtle, hare = 1, 2
      while x[turtle] != x[hare]:
         turtle = turtle + 1
         hare = hare + 2

      # Find the position of the first repetition of length nu
      # The hare and turtle move at the same speeds
      mu = 0
      turtle, hare = 0, turtle
      while x[turtle] != x[hare]:
         turtle = turtle + 1
         hare = hare + 1
         mu = mu + 1

      # Find the length of the shortest cycle starting from x_mu
      # The hare moves while the turtle stays still
      lam = 1
      hare = turtle + 1
      while x[turtle] != x[hare]:
        hare = hare + 1
        lam += 1

      # Verify that the obtained mu and lambda does indeed describe a cycle
      if verifyCycle(x, lam, mu) == False:
         print 'Error! Algorithm contains at least one bug!'
         return -1, -1
      
      return lam, mu
   else:
      return 0, 0


def verifyCycle(x, lam, mu):
   # Verify that the calculated cycle is indeed correct
   for i in range(lam):
      if x[mu + i] != x[mu + lam + i]:
         return False
      if lam == 1:   # As a precaution...
         for i in range(10):  # 10 is arbitrary...
            if x[mu + i] != x[mu + i + 1]:
               return False
   return True

   
def printResult(a, d, lam, mu):
   # Print the result on a form that's easily readable
   if (lam > 0) or (mu > 0):
      number = '1/' + str(d) + ' = 0.'
      for i in range(2, mu + 2):
         number = number + a[i]
      number = number + '('
      for i in range(mu + 2, mu + lam + 2):
         number = number + a[i]
      number = number + ')' + ' lambda = ' + str(lam) + ' mu = ' + str(mu)
   elif (lam == -1) or (mu == -1):
      number = '1/' + str(d) + ' could not be calculated.'
   else:
      number = '1/' + str(d) + ' = ' + str(Decimal(1) / Decimal(d))
   print number
   
   
if __name__ == "__main__":
   getcontext().prec = 1000
   for d in range(2, 24):
      a = str(Decimal(1) / Decimal(d))
      x = []
      for i in range(2, len(a)):
         x.append(int(a[i]))
      lam, mu = getRecurringCycle(x)
      printResult(a, d, lam, mu)
```

---

### Post by dribeas on 2008-07-21
From the output either the implementation of the algorithm or else the verification is incorrect. Exec them separatedly and check by hand, that is get results from the algorithm applied to 1/23 (without verification) and verify by hand.

I don't know enough python, but you may want to check the precision of the real number implementation, just in case you don't have enough precision to determine the correct result (print the result of 1/23 and check that it has enough decimals.

---

### Post by WW on 2008-07-21
Floyd's algorithm (as described in the wikipedia article) is not applicable to the problem of finding a cycle of digits in a decimal expansion.  The algorithm assumes that from any given "node", there is only one possible next node.  So if, for example, 0 is followed by 4 at some point in the pattern, 0 is *always* followed by 4.  This is not true for a decimal expansion of a rational number.

---

### Post by MdaG on 2008-07-21
> **dribeas said:**
> From the output either the implementation of the algorithm or else the verification is incorrect. Exec them separatedly and check by hand, that is get results from the algorithm applied to 1/23 (without verification) and verify by hand.

I don't know enough python, but you may want to check the precision of the real number implementation, just in case you don't have enough precision to determine the correct result (print the result of 1/23 and check that it has enough decimals.

I'm using the Decimal data type so the precision is "infinite" (well actually it's 1000 decimals since I've set the precision to that.).
And removing the verification I get the result described in my original post which isn't the correct one.

> **WW said:**
> Floyd's algorithm (as described in the wikipedia article) is not applicable to the problem of finding a cycle of digits in a decimal expansion.  The algorithm assumes that from any given "node", there is only one possible next node.  So if, for example, 0 is followed by 4 at some point in the pattern, 0 is *always* followed by 4.  This is not true for a decimal expansion of a rational number.

Thank you. That explains it. :)
Is there a better suited known algorithm for my problem?
Otherwise I'll just have to figure one out myself.

EDIT:
Rewrote an algorithm that seems to work. The verification algorithm is ugly however and not fool proof.
```
#! /usr/bin/env python

from decimal import *

def Floyd(x):  # Using Floyd's cycle detection algorithm
   # Only proceed if there are enough decimal numbers to actually find a large cycle
   if len(x) > 100:
      # The main phase of the algorithm, finding a repetition x_nu = x_2nu
      # The hare moves twice as quickly as the turtle
      turtle, hare = 1, 2
      while x[turtle] != x[hare]:
         turtle = turtle + 1
         hare = hare + 2

      # Find the position of the first repetition of length nu
      # The hare and turtle move at the same speeds
      mu = 0
      turtle, hare = 0, turtle
      while x[turtle] != x[hare]:
         turtle = turtle + 1
         hare = hare + 1
         mu = mu + 1

      # Find the length of the shortest cycle starting from x_mu
      # The hare moves while the turtle stays still
      lam = 1
      hare = turtle + 1
      while x[turtle] != x[hare]:
        hare = hare + 1
        lam += 1

      # Verify that the obtained mu and lambda does indeed describe a cycle
      if verifyCycle(x, mu, lam) == True:
         return mu, lam
      else:
         return -1, -1
   else:
      return 0, 0


def getRecurringCycle(x):
   # Only proceed if there are enough decimal numbers to actually find a large cycle
   maxLength = len(x)
   if maxLength > 100:
      mu, lam = Floyd(x)   # Try finding a cycle using Floyd's algorithm
      if (mu != -1) and (lam != -1):
         return mu, lam
      else:                # Otherwise try a brute force approach
         mu = 0
         lam = 1
         sequenceFound = False
         while not sequenceFound:
            while (mu + lam < maxLength) and x[mu] != x[mu + lam]:
               lam += 1
            if verifyCycle(x, mu, lam) == True:
               sequenceFound = True
            elif lam < maxLength:
               lam += 1
            else:
               mu += 1
               lam = 1

         return mu, lam
   else:
      return 0, 0


def verifyCycle(x, mu, lam):
   # Verify that the calculated cycle is indeed correct
   # This algorithm is not fool proof
   if (2 * lam + mu) < len(x):
      for j in range(len(x) / lam):
         for i in range(lam):
            if x[mu + i] != x[mu + lam + i]:
               return False
      if lam < 10:   # As a precaution...
         for i in range(10):  # 10 is arbitrary...
            if x[mu + i] != x[mu + i + 1]:
               return False
      return True
   else:
      return False

   
def printResult(a, d, mu, lam):
   # Print the result on a form that's easily readable
   if (lam > 0) or (mu > 0):
      number = '1/' + str(d) + ' = 0.'
      for i in range(2, mu + 2):
         number = number + a[i]
      number = number + '('
      for i in range(mu + 2, mu + lam + 2):
         number = number + a[i]
      number = number + ')' + ' lambda = ' + str(lam) + ' mu = ' + str(mu)
   elif (lam == -1) or (mu == -1):
      number = '1/' + str(d) + ' could not be calculated.'
   else:
      number = '1/' + str(d) + ' = ' + str(Decimal(1) / Decimal(d))
   print number
   
   
if __name__ == "__main__":
   getcontext().prec = 2000
   for d in range(2, 1000):
      a = str(Decimal(1) / Decimal(d))
      x = []
      for i in range(2, len(a)):
         x.append(int(a[i]))
      mu, lam = getRecurringCycle(x)
      printResult(a, d, mu, lam)
```

---

